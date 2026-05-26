# Analytical Characterization

A dedicated track at PEGS 2026 covered **ML and Digital Integration in Biotherapeutic Analytics** — automation of LC-MS workflows, analytical method performance monitoring, host cell protein detection, and biophysical characterization tools.

---

## Talks

### David Bush (Roche) — *LC-MS Automation for All Seasons*
- Roche's strategy for **end-to-end LC-MS automation** across the research-development continuum.
- Teams: Cambridge (US) + Basel (Switzerland) — cross-site collaboration with automation, mass spec, and IT experts.
- Automation goals:
  - **Productivity:** reduce turnaround time, eliminate menial tasks, shift scientists to higher-value work.
  - **Data Quality:** stricter protocol adherence, fewer manual errors, more data points per study.
  - **Data Integrity:** ALCOA+ compliance, automatic results federation.
  - **AI Readiness:** automatically populate AI-legible databases with federated results.
- mAb discovery and development workflow: hit screening → profiling → lead development → CMC development — MS analytics at every stage.
- Covers biophysical, physiochemical, and MS analytics from hit screening to lead development.

### Yi Han (Bristol Myers Squibb) — *Enabling Analytical Excellence: The Impact of Digital Integration in Clinical Method Performance*
- **Method Performance Monitoring (MPM):** track analytical method quality across the full method lifecycle (development → validation → ongoing monitoring).
- Analytical methods: relative potency (bioassay/ELISA), process impurities (ProA, HCP, DNA), separation methods (CGE, SEC, iCE).
- Three lifecycle stages: Stage 1 (Method Development: define ATP), Stage 2 (Method Validation: confirm performance), Stage 3 (Method Performance Monitoring: ensure performance maintained).
- BMS built an **MPM Automation Workflow** and **MPM Dashboard** — automated monitoring with real-time visualization of method trends, alerts for drift, and use cases for root cause analysis.

### Leo (Lei) Wang (Takeda) — *Peak Exclusion-Driven Deep-Field LC-MS/MS for Enhanced Host Cell Protein Detection*
- **Host Cell Proteins (HCPs):** process-related impurities from CHO, E. coli, or other expression hosts that co-purify with biologic drug substance (DS). HCPs are a Critical Quality Attribute (CQA).
- Problem: conventional top-N DDA (data-dependent acquisition) reaches a depth ceiling — high-abundance peptides dominate, low-abundance HCPs are missed.
- Solution: **AcquireX deep-field acquisition** — automatic exclusion lists built from earlier runs, enabling detection of progressively deeper (lower-abundance) HCPs.
- Results: deeper and higher-confidence HCP identification vs. standard DDA; benchmarked on NISTmAb and 4 commercial mAb standards.

### Leo (Lei) Wang / Takeda — *PEGS2026 AcquireX LW2*
- A second Takeda talk (possibly from the same group) covering **AcquireX** implementation details — workflow, results, and validation across different expression systems.

### Zahid Khan — *The Role of Analytical Ultracentrifugation (AUC) in Characterizing the Complexity of Diverse Modalities*
- **AUC (Analytical Ultracentrifugation):** biophysical technique separating macromolecules by hydrodynamic and thermodynamic properties (sedimentation + diffusion).
- Unique advantages: analysis in native state, large MW range (10²–10⁸ Da), non-destructive, no matrix interactions (unlike chromatography).
- Core technique: **SV-AUC (Sedimentation Velocity AUC)** — differentiates soluble species by size, shape, and relative abundance.
- Applications across modalities: mAbs, vaccines (VLPs, polysaccharides), multicomponent systems, proteins/peptides, ADCs, oligonucleotides.
- Key message: AUC solves problems that chromatography and imaging cannot — heterogeneous populations distorted by matrix interactions (SEC) or labeling (DLS) are resolved cleanly.

---

## Key Themes

- **Automation enables AI readiness.** Without automated data federation into structured, AI-legible databases, ML models cannot be trained or deployed at scale.
- **Method performance monitoring is undervalued.** Analytical methods drift over time; MPM dashboards with automated alerts are critical for GMP compliance.
- **HCP detection depth matters.** Trace HCPs can cause immunogenicity or degradation of the drug product — deep-field LC-MS/MS is essential for comprehensive characterization.
- **AUC is a gold standard for soluble aggregates.** For modalities where SEC is confounded by matrix interactions (e.g., aggregation under high-concentration conditions), AUC provides definitive results.
- **Digital integration enables continuous improvement.** MPM data feeds back into method development, closing the loop.

---

## Analytical Methods Quick Reference

| Method | Measures | Typical Use in Biologics |
|--------|---------|--------------------------|
| SEC-HPLC | Monomer %, HMW/LMW aggregates | Release testing, stability |
| iCE (Imaged Capillary Electrophoresis) | Charge variants (acidic/basic peaks) | Release testing |
| CGE | Purity (non-reduced/reduced) | Release testing |
| SV-AUC | Soluble aggregates, size distribution | Development, investigational |
| LC-MS/MS (DDA) | Peptide mapping, sequence confirmation, HCPs | Development, characterization |
| AcquireX (deep-field DDA) | Deep HCP detection | Development, process validation |
| SPR/BLI | Binding kinetics (Kd, kon, koff) | Hit characterization, developability |
| DSF/DSC | Thermal stability (Tm) | Formulation, developability |
| DLS | Hydrodynamic size, aggregation | Early screening |
| ELISA | HCP quantification (total), ADA detection | Release, clinical monitoring |
