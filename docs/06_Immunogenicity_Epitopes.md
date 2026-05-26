# Immunogenicity & Epitopes

Immunogenicity prediction was a dedicated track at PEGS 2026. The field is maturing rapidly: T cell epitope prediction is established; B cell epitope prediction is actively improving; and the challenge of modeling clinical ADA outcomes from molecular features is an open problem.

---

## Talks

### Guilhem Richard (EpiVax) — *Harnessing Human and Machine Intelligence for Next-Generation Immunogenicity Risk Prediction*
- EpiVax is the industry leader in in silico immunogenicity risk assessment. 13M+ sequences analyzed, serves 18 of the top 20 pharma companies, 230+ publications.
- Core technology: two-step prediction — (1) peptide–HLA binding (EpiMatrix), (2) pMHC–TCR interaction (JanusMatrix, predicts tolerance vs. foreignness).
- Updates presented:
  - **JanusMatrix 2.1:** improved prediction of epitope tolerance (self vs. foreign by T cells).
  - **ADA 2.2 model:** updated anti-drug antibody prediction.
- Platform: **ISPRI Toolkit** (Interactive Screening and Protein Reengineering Interface) — industry-leading, FDA-aligned, supports deimmunization workflows.
- Emphasis on **regulatory-ready methodologies** — aligned with FDA expectations and New Approach Methodologies (NAMs) guidance.

### Daniel Leventhal (Tactyl Consulting) — *Defining the Data Behind the Models: Interpreting Clinical Immunogenicity Measures for AI/ML Risk Assessment*
- Focus on **clinical immunogenicity data quality** — the ground truth for all immunogenicity models.
- Framework: immunogenicity system has molecular features (drug product), clinical features (dose, route, duration), and patient features (HLA typing, pre-existing ADA, immune history).
- **Critical gaps:** which components are relevant? How to weight features? How to connect features into a system-level model?
- **Immunogenicity Database Collaborative (IDC):** initiative to build high-quality, standardized clinical ADA datasets for training/validating AI models.
- Key message: "High quality, ground truth data is key for developing and validating in silico models." Most current models are limited by data quality, not model architecture.

### Mojtaba Haghighatlari / Sophie Tourdot (Pfizer) — *From HLA Class II Peptide Presentation to Immunogenicity Screening with HLAIIPred*
- **HLAIIPred:** Pfizer's in-house ML model for predicting HLA class II peptide presentation (a key step in T cell-mediated ADA response).
- Why HLA-II modeling is hard: three gene loci (DR, DQ, DP), thousands of alleles, each patient has multiple allotypes, peptide binding groove is open-ended (8–26 AA epitopes), only positive (presented) examples in training data.
- HLAIIPred addresses: allele-specific binding prediction, 9-mer core identification, handling polyallelic data.
- Use case: immunogenicity screening of therapeutic antibodies during development.

### Lora Hamuro (Clinical Pharmacology) — *Advanced Modeling of Immunogenicity for a Biotherapeutic Combination*
- Covered in [Structure Prediction page](03_Structure_Prediction.md); also relevant here.
- Modeling ADA risk for combination biologics — synergistic immune activation with Nivolumab + Ipilimumab as the canonical example.

### Will Thrift (gCS CBM/AI4DD) — *Improving Antibody Immunogenicity Risk Assessment with B Cell Epitope Prediction*
- **B cell epitope (BCE) prediction** is maturing: Discotope 3 uses structure-informed ESM-IF embeddings + relative solvent accessibility + AF2 pLDDT to train XGBoost.
- Dataset: 582 antibody-antigen complexes, 1466 antigen chains, ~27k BCE residues, ~300k total residues.
- New model: **RoBep** (region-oriented deep learning, Xu et al., *Bioinformatics* 2026) — argues that region-aware inductive bias is beneficial.
- Built a **BCE risk pipeline** for clinical immunogenicity assessment: structure prediction → BCE prediction → patch identification → self-patch exclusion → risk metric.
- Key finding: adding BCE prediction to T cell epitope assessment may yield additional predictive power for clinical ADA outcomes (~40% of biotherapeutics have efficacy reduced by immunogenicity).

### Morten Nielsen (DTU) — *B Cell Epitope Predictions: Can We Benefit from Immune-Receptor Data?*
- Director of the NielsenLab IML research group at DTU, which develops many of the field's core prediction tools.
- Tools from this lab: **NetMHCpan** (HLA-I), **NetMHCIIpan** (HLA-II), **NetTCR**, **Bepipred** (B cell linear epitope prediction), **Discotope** (conformational B cell epitopes), **AbEpiTope**, **BepiPocket/DiscoPocket**.
- New work: leveraging paired antibody-antigen structural data to improve conformational BCE prediction.
- Key challenge: linear BCE prediction (Bepipred) is relatively mature; conformational BCE prediction (Discotope) is harder and still improving.

### Brunno Rocha (Novartis) — *IGMotifFinder: Improving Preclinical in silico Immunogenicity Assessment via Integration of Pathogen Similarity Analysis*
- Novel approach: integrate **pathogen sequence similarity** into immunogenicity assessment.
- Hypothesis: sequences similar to pathogens may be perceived as more foreign by the immune system.
- **IGMotifFinder pipeline:** HLA class II binding hotspot prediction (PSSM) → de-immunization via randomization → MAPPs assay confirmation.
- Advantage of early in silico profiling: high-quality candidate material not available in early development; in vitro assays are expensive and slow.
- Context of use drives the depth of profiling: IRA questionnaire → in silico → in vitro → clinical.

### Rita Martello (EMD Serono) — *A Streamlined Preclinical Workflow to Assess the Immunogenicity Risk of Biotherapeutics*
- Full preclinical-to-clinical immunogenicity workflow at Merck KGaA / EMD Serono.
- Adaptive testing strategy: risk-based triaging — only candidates with high immunogenicity risk proceed to expensive in vitro assays (MAPPs, T cell activation assays).
- Key tools: in silico T cell epitope analysis → MAPPs assay → T cell activation/proliferation assays → ADA detection in clinical.
- Caveats: "Immunogenicity in animals is not predictive of clinical immunogenicity."

### Xiaobin Zhang (Takeda) — *Mapping the Anti-Drug Antibody Binding Site on Multidomain Biotherapeutics*
- Focused on **ADA epitope mapping** for complex multi-domain biotherapeutics (case study: TAK-186).
- Combined in silico (MHC-TCR modeling) and in vitro tools to characterize which domains of a bispecific are immunogenic.
- Key factors for immune response: AA sequence foreignness, T/B epitope content, glycosylation, aggregation, dose, route, frequency, patient HLA typing, pre-existing ADA.

---

## Key Themes

- **T cell epitope prediction is mature; B cell epitope prediction is catching up.** Discotope 3 and RoBep represent the current state of the art.
- **Clinical data quality is the main bottleneck.** The IDC is a community response to this problem.
- **De-immunization is now a routine workflow** — but requires high-quality in vitro confirmation (MAPPs assay).
- **Combination biologics create new immunogenicity risks** that require system-level (not molecule-level) modeling.
- **HLA diversity** makes HLA-II prediction especially challenging — thousands of alleles, polyallelic data, open-ended peptide binding groove.

---

## Key Tools

| Tool | Function |
|------|---------|
| EpiMatrix | HLA-I and HLA-II peptide binding prediction (EpiVax) |
| JanusMatrix 2.1 | Epitope tolerance prediction — self vs. foreign (EpiVax) |
| ISPRI Toolkit | Integrated immunogenicity screening platform (EpiVax) |
| NetMHCpan / NetMHCIIpan | HLA binding prediction (DTU) |
| Bepipred | Linear B cell epitope prediction (DTU) |
| Discotope 3 | Conformational B cell epitope prediction (DTU, uses ESM-IF + AF2) |
| RoBep | Region-oriented BCE prediction (Xu et al. 2026) |
| MAPPs assay | In vitro: MHC-associated peptide proteomics — confirms in silico HLA-II predictions |
| HLAIIPred | Pfizer's in-house HLA-II peptide presentation model |
| IGMotifFinder | Novartis: pathogen similarity-integrated immunogenicity assessment |
| IEDB | Immune Epitope Database — public resource for T and B cell epitopes |
