# Protein Language Models (pLMs)

Protein language models were a central theme across multiple talks at PEGS 2026. Key questions: which models are actually better, how should training data be composed, and what do they know about antibody function?

---

## Talks

### Victor Greiff (University of Oslo / IMPRINT) — *Training Data Composition Determines ML Generalization and Biological Rule Discovery*
- Core finding: **training data composition is the most important variable** in ML for adaptive immune receptors — more important than model architecture.
- Demonstrated that antigen-specific datasets occupy **distinct regions** of the immune receptor embedding space (Vicinity Score metric quantifies enrichment).
- Critical result: **PLMs are generally not better than simple edit-distance-based baselines** for clustering antigen-specific antibodies.
- Ran a public Kaggle competition (immune repertoire classification, with Sandve/UiO and Yaari/Yale). Only **10% of participants beat a very simple baseline.** Accepted as Registered Report in *Nature Methods.*
- Key takeaway: be skeptical of model complexity; always benchmark against simple baselines.

### Koji Tsuda (University of Tokyo / NIMS / RIKEN) — *Benchmarking Language Models for Antibody and Nanobody Tasks*
- Introduced two benchmark suites:
  - **NbBench** (Zhang & Tsuda, *Mach. Learn. Sci. Tech.*, 2025): 8 tasks across 9 datasets for encoder-type models (BERT-style). Evaluated 11 models — general protein LMs, antibody-specific LMs, nanobody-specific LMs. Tasks: variable region classification, CDR infilling, antigen-nanobody binding prediction, paratope prediction, thermostability, polyreactivity, nanobody type classification, phage display affinity.
  - **Ab-VS-Bench** (Zhang & Tsuda, bioRxiv 2025): benchmarks for decoder-type models (GPT-style).
- Key message: the field needs rigorous benchmarks. Domain-specific finetuning doesn't always help (echoes AbBiBench finding #2).

### Clare Gillis (OPIG) / Valentin Stanev (AstraZeneca) / Mani Jain (Amgen) — *In silico and ML Tools for Antibody Design and Developability Predictions*
Three-part talk:
1. **OPIG Tools** (Clare Gillis): Overview of Oxford Protein Informatics Group databases and tools (see [Computational Tools page](09_Computational_Tools_Databases.md)).
2. **ML for Developability Predictions** (Valentin Stanev, AstraZeneca): Using pLMs to predict developability properties at AstraZeneca scale.
3. **Federated Fine-Tuning of Protein Language Models for Biologics Property Prediction** (Mani Jain, Amgen): Federated learning approach to train pLMs across organizations without sharing proprietary data.

### Aviv Spinner (The ALIGN Foundation) — *GROQ-seq: Addressing Protein Function Prediction*
- Built **GROQ-seq** (Growth-based Quantitative Sequencing): a high-throughput, generalizable, and reproducible platform for measuring protein fitness.
- Deep mutational scanning on 5 protein landscapes + profiling a protein family across the tree of life.
- Datasets: T7RNAP (34,651 seqs), DAMP/LMSF RamR and LacI (16k–44k seqs each).
- Goal: benchmark ML models against each other on calibrated, quantitative fitness measurements.
- Key theme: experimental platforms that generate clean, quantitative data are essential for training and validating pLMs.

---

## Key Themes

- **Benchmarking is essential and underused.** NbBench and GROQ-seq both address the same problem: the field lacks standardized, quantitative evaluation.
- **Simple baselines are strong.** Both Greiff and AbBiBench showed that simple methods (edit distance, global structure models) often match or beat complex pLMs.
- **Antibody-specific finetuning can degrade performance** — a counterintuitive finding from multiple benchmarks.
- **Training data composition matters more than architecture.** This is the headline finding from Greiff's lab.
- **Federated learning** is emerging as a way to train better models across pharma companies without data sharing.

---

## Key Models Referenced

| Model | Type | Notes |
|-------|------|-------|
| ESM2 / ESM-IF | Encoder / Inverse folding | Meta's general protein LM; widely used for embeddings and feature extraction |
| AbLang / AbLang2 | Antibody-specific encoder | Oxford OPIG; trained on OAS antibody sequences |
| TCRLang-paired | TCR-specific encoder | OPIG; for paired TCR sequences |
| p-IgGen / LICHEN | Decoder | OPIG; antibody sequence generation |
| IgFold | Structure prediction | Johns Hopkins (Jeff Gray lab) |

---

## AIDD4B Training Course — Protein Language Models Module
**Instructor:** David Nannemann (Rosetta Commons Foundation / Rosetta Design Group)

### Model Comparison

| Model | Training Data | Token Spacing | Use Case |
|-------|--------------|--------------|----------|
| **ESM-2** | General protein sequences (UniRef) | No spaces | General protein embeddings; standard for biologics |
| **ProtBERT** | General protein sequences | Space between residues | General protein embeddings (older baseline) |
| **IgBERT** | Antibody sequences (OAS) | Space between residues; heavy+light combined with `[SEP]` | Antibody-specific tasks |
| **AMPLIFY** | General sequences, optimized training | — | Better compute efficiency; emerging alternative to ESM-2 |

**Tokenization note:** ESM-2 uses `<mask>` for masked tokens; BERT-style models use `[MASK]`. IgBERT expects heavy and light chain combined as a single sequence separated by `[SEP]` — input format matters.

### Interpreting pLM Outputs

**Logits and probabilities:**
- Raw model outputs are **logits** — unnormalized scores for each amino acid at each position
- Convert to probabilities via **softmax**: `P(aa | context) = softmax(logits)`
- **Fitness estimate:** `log P(mutant) − log P(wild-type)` — positive = model predicts mutation is tolerated; negative = likely deleterious

**Hidden state layers:**
| Layer range | Information encoded |
|------------|-------------------|
| Early (1–5) | Amino acid chemistry, local interactions |
| Middle (6–15) | Secondary structure (helices, sheets) |
| Late (16–30) | Tertiary structure, functional relationships |

For most downstream tasks, **late-layer embeddings** (or averaged across all layers) perform best.

**Perplexity and Shannon entropy:**
- **Perplexity < 10** = good sequence fit; **> 20** = problematic (model is uncertain)
- **Shannon entropy < 2 bits** = model is confident about which residues are allowed at that position

### Failure Modes

| Scenario | Why pLMs struggle |
|----------|-----------------|
| Intrinsically disordered regions (IDRs) | No single correct structure; sequence-structure relationship breaks down |
| Membrane proteins | Underrepresented in training data |
| Signal peptides | Cleaved post-translation; model sees artifact sequence |
| Low-complexity regions | Repetitive sequence carries little information |
| Rare protein families | Low representation in training corpus |
| Post-translational modifications | pLMs trained on sequence only; glycosylation, phosphorylation not captured |

### Practical Guidelines for Biologics

**DO:**
- Use pLM embeddings as features for downstream regression/classification models (developability, affinity)
- Compare multiple models on your specific task before committing
- Always benchmark against simple baselines (edit distance, physicochemical descriptors)
- Use late-layer or averaged embeddings for most tasks

**DON'T:**
- Assume antibody-specific finetuning always outperforms general models — benchmarks (NbBench, AbBiBench) show this is not reliable
- Use perplexity alone as a proxy for binding affinity
- Ignore training data composition — it affects generalization more than model architecture (Greiff Lab)

### Antibody Triaging with pLMs
For antibody developability triaging, a practical framework combining pLM scores with biophysical flags is described in:
- **Sweet-Jones & Martin, *mAbs* 2025** — systematic evaluation of pLM-based approaches for antibody triaging and developability prediction
