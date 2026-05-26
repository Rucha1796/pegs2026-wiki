# AI/ML for Biologic Design

**The overarching theme of PEGS 2026** — AI has crossed from proof-of-concept into production. Multiple industry talks focused on scaling validated methods across portfolios, building connected data infrastructure, and closing the gap between dry-lab models and wet-lab reality.

---

## Talks

### Melody Shahsavarian (Eli Lilly) — *Democratizing Data and AI for Biotherapeutics Research*
- Eli Lilly's Digital Transformation Team (40+ scientists and technologists) built a **connected digital platform** that unifies wet-lab experimental data and dry-lab ML models.
- Previously: isolated data ecosystems with manual handoff between experimentalists and data scientists.
- Now: shared platform where wetlab scientists access ML models directly; models retrain on new data automatically.
- Key enabler: **harmonized processes, data standards, and ontologies** across the organization.
- MAKE capability: 10s of plates/week expressed. TEST capability: 10,000s of data points per molecule.
- Wet/dry lab synergy enables: developability models, diversity/clustering algorithms, binding affinity models, generative design, structure-based design.

### Prashanth Vishwanath (Takeda) — *From Proof-of-Concept to Proof-of-Productivity and Scale*
- Key message: **"AI in Biologics is at an inflection point."** The question is no longer whether it works — it's how fast we can scale across the portfolio.
- Three-phase framing: (1) Validated PoC, (2) The productivity gap — what breaks at scale, (3) The scaling platform.
- **Case study:** Fc-fusion protein with poor expression and aggregation. Rational optimization failed (one property at a time, scaffold could not meet multi-parameter requirements). Generative redesign (2 DMTA cycles) preserved function while substantially improving yield and aggregation.
- Two paths forward: **more PoCs** (one-off wins, no reusable infrastructure) vs. **a compounding platform** (each program makes the next faster; failure data is an asset).
- Takeda's bet: build the compounding platform.

### Andrew C R Martin (University College London) — *Application of AI to Developability Screening: A Skeptic's View*
- Critical assessment of generative AI for antibody design. Key points:
  - "You still need to test the Abs. Mice and phage display are very good at it."
  - Several 2023–2025 papers making **questionable claims** — most "designed" antibodies still require large libraries or yeast display for affinity maturation.
  - More convincing recent examples: Germinal (Gao 2025, 4–22% nanomolar binders from 43–101 designs per target), Chai Discovery (2025, ≥1 binder for 50% of 52 targets, 18.3 pM–200 nM).
- **Where AI is genuinely useful NOW:** Triaging and developability — epitope prediction, affinity ranking, developability flags (hydrophobic clusters, MHC binding, PTM sites, CDR-H3 length, isoelectric point, thermostability, germline pairing).
- Tool: **WALLE** — combines protein language models (ESM2) and graph neural networks for structure-based affinity ranking.
- Tool: **abYsis** — all data-driven, no generative AI, used at UCL for developability.

---

## Key Themes

- **Data connectivity beats model sophistication.** Lilly and Takeda both found that unifying data infrastructure delivered more value than any single ML model.
- **Skepticism is healthy.** The field is awash with papers overstating results; critical evaluation of experimental controls and benchmarks matters.
- **Generative AI for antibody design is getting real** — but best results still require some experimental iteration (10–100 designs, not millions).
- **Multi-parameter optimization** is the hard problem. Rational optimization solves one property at a time; generative redesign can jointly optimize multiple objectives.

---

## Tools & Methods Mentioned

| Tool | Description |
|------|-------------|
| WALLE / WALLE-Affinity | pLM + GNN for antibody affinity ranking |
| abYsis | Data-driven antibody analysis (UCL, no generative AI) |
| Germinal | Dual-objective generative AI (pLM + AlphaFold-Multimer) for antibody design |
| Chai Discovery | All-atom generative AI for antibody/nanobody design |
| DMTA cycle | Design-Make-Test-Analyze cycle for iterative protein optimization |

---

## NRC ML for Biologics Training Course
**Instructors:** Mélanie Gaudreault & Yumeng Wei (National Research Council Canada)

A two-day intensive course covering machine learning foundations as applied to biologics discovery. Key sessions: Data to Discovery, Structure Prediction, Affinity Prediction (Day 1); Generative Modeling, Developability & Immunogenicity (Day 2).

### ML Algorithm Landscape

| Algorithm | Strengths | Typical use in biologics |
|-----------|-----------|------------------------|
| **K-Nearest Neighbors (KNN)** | Interpretable, no training required | Sequence similarity clustering, hit retrieval |
| **Support Vector Machines (SVM)** | Effective in high-dimensional spaces | Developability classification |
| **Decision Trees / Random Forest** | Interpretable, handles mixed features | Immunogenicity risk flags |
| **Neural Networks (deep learning)** | Learns complex patterns from large data | pLM fine-tuning, structure prediction |
| **Bayesian methods** | Principled uncertainty estimates | Active learning, small-data affinity models |

### Protein Representation for ML

| Representation | Type | Examples | Strengths |
|---------------|------|---------|-----------|
| One-hot encoding | 1D | Binary position matrix | Simple, exact |
| Word embeddings | 1D | pLM embeddings (ESM-2) | Captures evolutionary context |
| Z-scales / physicochemical | 1D | Charge, hydrophobicity, size per position | Interpretable features |
| BLOSUM substitution matrix | 1D | Evolutionary substitution frequencies | Classic baseline |
| 2D projections | 2D | UMAP, t-SNE of embedding space | Visualization, clustering |
| Voxel grid / 3D | 3D | 3D CNN on structure | Captures spatial context; computationally expensive |

### FAIR Data Principles for ML Readiness

A foundational requirement for building useful ML datasets in biologics:

| Principle | Meaning | Why it matters |
|-----------|---------|---------------|
| **Findable** | Data is labeled, indexed, discoverable | Cannot train on data you cannot locate |
| **Accessible** | Data can be retrieved via standard protocols | Wet/dry lab integration requires accessible databases |
| **Interoperable** | Data uses standardized formats and ontologies | Enables cross-organization or cross-project ML |
| **Reusable** | Data has clear provenance, license, metadata | Future models can build on existing datasets |

Both Eli Lilly (Shahsavarian) and AstraZeneca (Dippel) cited FAIR compliance as a prerequisite for AI readiness.

### Affinity Prediction

**mCSM-Ab** (web server: biosig.lab.unimelb.edu.au/mcsm_ab):
- Predicts change in antibody-antigen binding affinity upon mutation (ΔΔG)
- Uses graph-based signatures encoding local atomic environment
- Useful for: ranking mutations before synthesis, flagging affinity-destabilizing variants

**SIE Scoring Function** (Solvated Interaction Energy):
```
ΔG = α(E_vdw + b·E_ele + b·E_RF + γ·DSA) + C
```
- vdW: van der Waals contacts at interface
- E_ele: electrostatics
- E_RF: reaction field (solvation)
- DSA: desolvation penalty (buried surface area)

**Training/Validation/Test splits:**
- Standard: 60–80% training, 10–20% validation, held-out test set
- For small datasets: **k-fold cross-validation** (k=5 or 10) avoids wasting data
- Always use sequence-based splits (not random) to prevent data leakage via homologous sequences

### Useful Web Servers (from course)

| Server | What it predicts | URL |
|--------|----------------|-----|
| mCSM-Ab | Antibody affinity upon mutation (ΔΔG) | biosig.lab.unimelb.edu.au/mcsm_ab |
| mCSM-Stability | Protein stability upon mutation | — |
| Aggrescan | Aggregation-prone regions | — |
| IEDB | Immune epitope database + prediction tools | iedb.org |
