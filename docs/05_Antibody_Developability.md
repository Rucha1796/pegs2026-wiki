# Antibody Developability

Developability — the set of biophysical, manufacturability, and safety properties that determine whether a biologic can become a drug — was one of the largest tracks at PEGS 2026. Talks covered automation, high-concentration formulations, bispecifics, AI applications, and roundtable discussions.

---

## Talks

### Maniraj Bhagawati (Roche, pRED) — *Engineering Success: High-Throughput Developability for Next-Generation Biotherapeutics*
- **HCLF (High Concentration Liquid Formulations)** are increasingly important for subcutaneous administration and patient centricity (self-injection at home).
- Critical quality parameters: **viscosity** (manufacturability, syringability), **aggregation** (shelf life, patient safety), **turbidity** (product quality).
- Roche is developing increasingly complex molecular formats: DutaFab, Brainshuttle, 1+1 bispecifics, 2+1 bispecifics, masked bispecifics, contorsbodies, IgG.
- HT developability workflow at Roche: CS-SINS score for early self-interaction assessment; early developability flags guide candidate selection.
- Key challenge: extending standard HT assays to complex molecular formats (bispecifics, fusion proteins) where properties are not simply additive.

### Andrew Dippel (AstraZeneca, Gaithersburg) — *Scaling Developability: Automating HT Assays for Early Developability Assessment*
- AstraZeneca Biologics Engineering: 397 FTE, global organization, 3 sites (Cambridge, Gaithersburg, Boston).
- **ATLAS** (Automated High-Throughput Laboratory for Antibody Screening): semi-automated HT developability panel.
- Four-part talk: (1) Analytics & Developability at AZ, (2) Optimizing automation-friendly HT assay panel, (3) Semi-automation implementation, (4) ATLAS system overview.
- Core focus: making developability assays **automation-compatible** — reducing dead volume, standardizing plate formats, enabling downstream AI readiness.
- Both Dippel (automation) and Kaplan (clinical stage data) presented from AstraZeneca — coordinated multi-speaker session.

### Gilad Kaplan (AstraZeneca) — *Lessons Learned from Comprehensive Biophysical Profiling of Clinical Stage Single Domain Antibodies*
- Analyzed developability flags for **clinical-stage single domain antibodies (sdAbs/VHH)** at AstraZeneca.
- Key question: **Do early developability flags for sdAbs translate into downstream manufacturing issues?**
- Profiled properties: yield, monomer content, reversible self-association, non-specific binding, solution properties, low pH viral hold compatibility.
- Findings: some early flags are predictive of manufacturing issues; others are not — the relationship is not always linear.
- Emphasizes the need for **clinical-stage datasets** to train and validate developability models for sdAbs specifically.

### Jan Paulo Zaragoza (Merck & Co.) — *From Automation to Visualization: Robotic Sample Preparation, HT Developability Analysis, and Dashboards*
- Discovery Biologics at Merck: mAbs, multispecific Abs, engineered fusion proteins, small format Abs (VHH), multivalent Abs, ADCs, cytokines, enzymes.
- End-to-end workflow: **Sequence Design → DNA Inventory → DNA Vectors Prep → Express Protein → Purify Protein → Sample Prep → Vialing → Test → Process**.
- Automation reduces turnaround time, improves data quality, ensures data integrity, enables AI readiness by federating results into AI-legible databases.
- Dashboarding: data visualization tools to present HT developability results across large molecule panels.

### Deborah Moshinsky — *Interpreting Biophysical Data in Antibody Evaluation: From Binding to Biological Relevance* (Roundtable)
- Core observation: **High affinity does not always predict biological performance** — epitope accessibility, receptor density, cell state, PTMs, avidity, assay architecture all matter.
- Discussion topics: Which biophysical metrics are most predictive? What are the limits of SPR/BLI? When can SPR replace downstream assays? Can sufficiently large datasets support predictive AI/ML models for this?

---

## Key Themes

- **Automation is prerequisite** — HT developability is only possible with end-to-end automation from sample prep to data visualization. ATLAS (AZ), Merck's robotic workflow, and IPI's platform are industry examples.
- **Early flags need clinical validation** — many developability assays have not been validated against clinical outcomes. The AZ clinical sdAb dataset is a step toward closing this gap.
- **Complex formats need tailored developability** — bispecifics and fusion proteins cannot simply reuse mAb developability panels; assay development is needed for each new format.
- **AI for developability is useful but needs the right benchmarks** — Martin's skeptic talk highlighted that many claimed AI advances have not been rigorously validated.

---

## Key Assays Mentioned

| Assay | Measures |
|-------|---------|
| CS-SINS | Self-interaction, colloidal stability (cross-interaction chromatography variant) |
| SEC | Monomer content, HMW/LMW aggregates |
| DLS | Hydrodynamic radius, aggregation |
| HIC | Hydrophobicity |
| PSR / BVP | Polyspecificity / Baculovirus particle reactivity (non-specific binding) |
| RSA | Reversible self-association |
| AC-SINS | Self-interaction |
| Viscosity | High-concentration viscosity |
| DSF/DSC | Thermostability |
