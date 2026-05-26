# Computational Tools & Databases

PEGS 2026 featured a dedicated session on computational tools and databases for antibody design and developability. The OPIG group presented a comprehensive overview, and several talks introduced new benchmarking platforms.

---

## Talks

### Clare Gillis (Oxford Protein Informatics Group) — *OPIG Tools: In silico and ML Tools for Antibody Design and Developability Predictions*

#### OPIG Databases

| Database | Type | Size (Apr 2026) |
|----------|------|-----------------|
| **SAbDab** | Adaptive immune receptor structures | 21,099 Fv structures |
| **Nb-SAbDab** | Nanobody structures | 2,032 structures |
| **OAS** (Observed Antibody Space) | Ab sequence repertoires | 2.4B unpaired, 3M paired sequences |
| **OAS-Nb** | Nanobody sequences | 6.9M sequences (2.1M non-redundant) |
| **IGHV** (IMGT-based) | TCR structures | 634 structures |
| **CoV-AbDab** | Covid antibody sequences + structures | 176,894 Ab sequences |
| **Thera-SAbDab** | Clinical/therapeutic antibodies | 1,133 therapeutics |
| **Nanobody-SAbDab** | Nanobody therapeutics | 4,913 sequences |

#### OPIG Tools

| Tool | Function |
|------|---------|
| **ANARCI / ANARCII** | Antibody, nanobody, and TCR numbering (Dunbar 2016; Greenshields-Watson 2025) |
| **AbLang / AbLang2** | Antibody language model for sequence analysis (Olsen 2022, 2024) |
| **TCRLang-paired** | TCR language model (Raybould 2024) |
| **p-IgGen** | Antibody sequence generation |
| **LICHEN** | Antibody light chain sequence generation (Capel 2025) |
| **KA-Search** | Rapid/exhaustive search of antibody sequence databases (Olsen 2023) |

All tools available at: `github.com/oxpig` and `opig.stats.ox.ac.uk/resources`

### Xinyan Zhao et al. — *AbBiBench: A Framework for Antibody Affinity Maturation and Design*
- **AbBiBench:** a new evaluation framework for antibody affinity maturation and design models.
- Addresses a critical gap: **existing metrics (structural RMSD, amino acid recovery) do not correlate with biological binding affinity.**
- AbBiBench evaluates based on **quality of antibody-antigen interface** and correlation with experimental binding affinity.
- **Three key findings:**
  1. **Global structure modeling outperforms local structure modeling** — context matters.
  2. **Antibody-specific finetuning can yield marginal gains or even degrade performance** — generalist models are competitive.
  3. **Confidence scores from structure prediction (pLDDT, pTM) are insufficient as standalone proxies for binding affinity.**
- **SimBinder-IF:** top-performing model from the benchmark — combines inverse folding (ESM-IF) with preference optimization (DPO/SPO).
- Method: Direct Preference Optimization (DPO) / Simple Preference Optimization (SPO) using strong vs. weak binder pairs.

### Tim Whitehead (University of Colorado Boulder) — *Unbiased Deep Screening of Antibody-Antigen Interactions*
- Premise: "AI can solve biophysical problems… given enough experimental measurements."
- Goal: for arbitrary biomolecular surface, discover antibody binders and quantitatively predict their affinities.
- Requirements: quantitative Kd measurements, scalable, representative of human Fab format.
- **MAGMA-seq** (Multiple Antigens, Multiple Antibodies): integrates Fab display (Golden Gate assembly), coupled VH/VL sequencing across ~2 kb, and Kd determination from sequencing data (Kinney, eLife 2016).
- Technical challenges: (1) Fab display with Golden Gate assembly, (2) resolving coupled VH and VL mutations across 2 kb, (3) determining monovalent Kds from sequencing data.
- Dataset scale: 200–500 mutational data points per Ab-Ag complex; >10,000 Ab-Ag complexes needed for AI.
- Recent publications: Kirby et al. *PNAS* 2025; Petersen & Kirby et al. *Nature Comms* 2024.

### Ashty Karim (Northwestern University) — *Design-driven Optimization of Low-Cost High-Yielding Cell-Free Protein Synthesis*
- **Cell-free gene expression (CFE)** systems: protein synthesis in cell lysate without live cells.
- Advantages: >1 g/L protein in ~4 hours, uses plasmid or linear DNA (LETs), open system for engineering.
- Historical context: Eduard Buchner (1907 Nobel), Nirenberg & Matthaei (first codon, 1961), Zubay (S30 extract protocol, 1973).
- Focus on **metabolic optimization** — slow-metabolizing sugars and polyphosphate-based metabolism for higher yields.
- Application: rapid protein testing platform for antibody discovery and engineering.

---

## Key Themes

- **OPIG is the go-to open-source toolbox** for antibody bioinformatics — ANARCI for numbering, AbLang for LM representations, KA-Search for database queries.
- **Benchmarking is the bottleneck** — AbBiBench, NbBench, GROQ-seq, and MAGMA-seq all address the lack of rigorous, biologically meaningful evaluation frameworks.
- **Experimental data at scale is essential** — MAGMA-seq targets >10,000 quantitative Ab-Ag interactions for AI training.
- **Cell-free protein synthesis** offers a rapid, scalable platform for early protein testing without full mammalian expression campaigns.

---

## Reproducibility Notes

- AbBiBench code and data: available on GitHub (Zhao et al.)
- OPIG tools: all open-source at `github.com/oxpig`
- MAGMA-seq: method available; dataset being scaled up
- NRC ML for Biologics course materials: `mm.nrc.ca/static/NRC-PEGS26.pdf`; web servers: mCSM-Ab (affinity), mCSM-Stability, Aggrescan (aggregation), IEDB (immunogenicity)
