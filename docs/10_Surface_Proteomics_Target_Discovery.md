# Surface Proteomics & Target Discovery

Target discovery and surface proteomics talks at PEGS 2026 explored new approaches to finding tumor-specific antigens — moving beyond classical targets toward conformational, context-dependent, and glycan-modified surface proteins.

---

## Talks

### Neal Goodwin (Immuto Scientific) — *Illuminating the Disease Surfaceome: Exploiting Conformational Targets for First-in-Class Cancer Therapies*
- **The "me too" problem:** 80% of assets fail in clinic, often due to on-target but off-disease activity. Average of 9 assets per target in oncology.
- Current targets overlap heavily with healthy tissues → toxicity limits dose and therapeutic window.
- **Key insight:** disease is inherently non-native. Pathology creates a divergent microenvironment (hypoxia, second messenger signaling, lactate generation) → diseased cells adopt distinct morphologies → surface proteins adopt distinct **conformations**.
- **Surface Protein Conformations (SPCs):** novel structural targets that:
  - Are invisible to standard target discovery approaches (which measure quantity, not conformation)
  - Have exceptional specificity (pathologic vs. healthy conformation)
  - Widen the therapeutic index dramatically
- **Case study:** Mutant KRAS^G12V affects the tumor cell surfaceome — not just quantitative protein differences but **structural (conformational) surfaceome effects**.
- Immuto Scientific's platform: screens for antibodies that bind conformational epitopes present only in diseased cells.
- Opportunity: first-in-class cancer therapies targeting conformational targets not accessible to current discovery approaches.

### Zinaida Good (Stanford University) — *Artificial Intelligence Systems to Advance Engineered T-Cell Immunotherapy Designs*
- 9 FDA-approved CAR-T/T-cell therapies since 2017 (7 for blood cancers, 2 for solid tumors in 2024; 2 more expected in 2026).
- Problem: T cell therapies have curative potential but only in some patients. Insufficient understanding of resistance mechanisms; preclinical models don't represent patient biology.
- **Good Lab approach:** learn from patient data + model mechanisms of resistance → more effective T cell therapy designs.
- Center for Cancer Cell Therapy at Stanford: multi-omics (scRNA-seq, flow cytometry, TCR sequencing, proteomics) from patient samples.
- AI systems: model the complex cell-cell interactions and signaling states that determine CAR-T efficacy or failure.
- Key datasets: Phase 3 axi-cel vs. HDT-ASCT (ZUMA-7, *NEJM* 2022), TIL vs. ipilimumab for melanoma (Rohaan *NEJM* 2022).

### Nicolle Serrano SantoDomingo (Roche) — *Labelling and Isolating Surface Proteins Using Immunoprecipitation Coupled to Mass-Spectrometry (IP-MS)*
- Context: **CAR-T cell characterization** — understanding what proteins are on the surface of manufactured CAR-T cells.
- Problem: plasmid splicing during lentiviral vector (LVV) production can create a splice variant of the CAR scFv. Questions: (1) Can we detect the splice variant? (2) Is it on the cell surface? (3) Can we quantify it? (4) Do co-eluting surface proteins affect CAR-T efficacy?
- **IP-MS method:** immunoprecipitation of CAR + cell surface proteins, followed by mass spectrometry identification and quantification.
- Results: detected and quantified splice variant at cell surface; identified co-eluting surface proteins that may affect CAR-T function.
- Significance: quality control method for CAR-T manufacturing; identifies potential sources of product heterogeneity.

### Hongyoon Choi (Seoul National University Hospital / Portrai, Inc.) — *Beyond SSTR and PSMA: Human Data-Driven Discovery and in silico Design of Next-Generation Radiopharmaceutical Therapies*
- **Theranostics:** use same molecular target for both imaging (Ga-68) and therapy (Lu-177) — "we treat what we see."
- Current standard targets: SSTR (somatostatin receptor) and PSMA (prostate-specific membrane antigen).
- Portrai platform: human multi-omics data (omics + AI) to identify new radiopharmaceutical targets.
- Target biology: iodine uptake system, tumor metabolism, cancer-specific targets from imaging data.
- Next generation RPT target discovery moves from empirical to **data-driven and in silico design**.

### Timothy Craig (Pfizer) — *Membrane Protein Production Supporting Drug Discovery*
- Focus on **GPCR production** for DNA Encoded Library (DEL) screening.
- DEL is a conformational selection technique — requires proteins in their native conformational state (allosteric states matter for hit identification).
- Novel membrane mimetics: **SMALP** (styrene maleic acid lipid particles) and **Peptidisc** for stabilizing GPCRs in solution without detergents.
- Allosteric nanobodies used to lock GPCRs in defined conformational states for DEL screening.
- Key message: the right protein preparation is critical for finding the right drug hits.

---

## Key Themes

- **Conformation is the new frontier for target discovery.** Conformational epitopes distinguish diseased from healthy cells — a specificity advantage that standard approaches miss.
- **CAR-T biology is complex and poorly understood.** AI systems modeling patient-level data are needed to predict which patients respond and why.
- **Membrane protein production is a major bottleneck.** GPCRs require specialized stabilization methods (nanobodies, SMALP, Peptidisc) for drug discovery campaigns.
- **Radiopharmaceuticals are expanding.** Data-driven target discovery is opening new radiopharmaceutical opportunities beyond SSTR and PSMA.
- **CAR-T quality control is critical.** IP-MS methods can detect product heterogeneity (splice variants, surface protein composition) that affects therapeutic function.

---

## Tools & Methods

| Tool/Method | Application |
|-------------|-------------|
| IP-MS | Immunoprecipitation-mass spectrometry for surface protein characterization |
| DEL (DNA Encoded Library) | Hit ID for membrane proteins, especially GPCRs |
| SMALP | Styrene maleic acid lipid particles — membrane protein solubilization |
| Peptidisc | Amphipathic peptide belt for membrane protein stabilization |
| Allosteric nanobodies | Lock GPCRs in defined conformational states |
| Portrai platform | Omics + AI for radiopharmaceutical target discovery |
| SPC (Surface Protein Conformation) | Immuto's conformational target discovery approach |
