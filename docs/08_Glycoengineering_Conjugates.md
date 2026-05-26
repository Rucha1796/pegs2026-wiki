# Glycoengineering & Antibody Conjugates

Glycoengineering — modifying the sugar structures on antibodies and glycoproteins — and antibody conjugation (ADCs) were featured in dedicated talks at PEGS 2026. Both areas leverage precise molecular engineering to improve therapeutic specificity and efficacy.

---

## Talks

### Hans H. Wandall (University of Copenhagen) — *Clean Cancer Targets for Better Therapeutics: GO's Glyco-mAbs*
- **Core concept:** Cancer cells express proteins with **truncated O-glycans** (Tn antigens) on their surface; normal cells have elongated O-glycans. This creates a tumor-specific antigen space.
- **GO (GlycoOnco) mAbs:** antibodies that recognize the combination of a protein + truncated O-glycan (glycopeptide epitope) — inherently tumor-specific.
- Why this matters:
  - Classical cancer targets (e.g., HER2, EGFR) are expressed in normal tissues → on-target, off-tumor toxicity.
  - Tn-O-glycans are tumor-specific: expressed broadly in epithelial tumors, absent in normal tissue, stable across cancer stages, increased in metastases.
  - Overlap (~50%) with PDL1 — potential combination opportunities.
  - >15,000 possible glycoprotein targets in the Tn-target universe.
- Platform enables: ADCs, bispecifics, targeted degraders, IO therapies, radiopharmaceuticals, T cell engagers (TCBs), CAR-T.
- Approach: O-glycoproteomic data + crystal structure data → antigen design → MS/MS confirmation.

### Jamie Spangler (Johns Hopkins) — *Facile Antibody Conjugate Production by Interfacing Protein Engineering with Metabolic Glycoengineering*
- Problem with current conjugation methods: NHS chemistry labels all primary amines (not site-specific); thiol chemistry disrupts disulfides; enzymatic remodeling requires expensive drug-enzyme preparation.
- Solution: **hijacking N-linked glycosylation** for site-specific conjugation using azido-functionalized sugar analogs.
- Process: cells incorporate azido-sugars metabolically → antibody is expressed with azido groups at glycosylation sites → click chemistry conjugates payload site-specifically.
- Limitation of natural IgG1: only one glycan site (N297), buried between Fc heavy chains — suboptimal for conjugation.
- Innovation: engineering **additional Fc glycosylation sites** that are surface-exposed → better conjugation efficiency and DAR homogeneity.
- Reference: Dammen-Brower et al., *Front. Chem.* 2022.

### Haisun Zhu (IPI) — *Evaluating Codon Optimization Strategies for Mammalian Glycoprotein Production*
- Focus on **antigen production for antibody discovery** — high throughput expression of glycoproteins in mammalian cells.
- In 2025: 221 unique genes expressed, 500+ expression constructs, 3,075 confirmed antibodies.
- Key variables: codon optimization strategy, expression vector design, production cell line (Expi293).
- Open-source expression vector developed by IPI and validated through Addgene DataHub.
- Platform integration: Beckman liquid handler + Illumina MiSeq + SONY sorter + Carterra SPR + AKTA Purifier.

---

## Key Themes

- **Tumor-specific glycopeptide epitopes are an underexplored target class** — combining protein and glycan recognition creates an exquisite selectivity filter.
- **Site-specific conjugation is critical for next-generation ADCs** — heterogeneous DAR is a major challenge for ADC safety and efficacy; metabolic glycoengineering offers a clean solution.
- **Glycoprotein production quality affects downstream antibody discovery** — codon optimization and vector design directly impact expression yield and glycoform homogeneity.
- **Fc engineering for conjugation** — moving beyond N297 opens new surface-exposed sites for site-specific payload attachment.

---

## Glycobiology Glossary

| Term | Meaning |
|------|---------|
| O-glycan | Sugar attached to serine/threonine; typically truncated in cancer (Tn antigen) |
| N-glycan | Sugar attached to asparagine (e.g., N297 on IgG Fc); site of standard antibody glycosylation |
| Tn antigen | Truncated O-glycan (GalNAc-Ser/Thr); tumor-associated, not expressed in normal tissue |
| DAR | Drug-to-antibody ratio; homogeneous DAR is critical for ADC performance |
| ADC | Antibody-drug conjugate; linker + cytotoxic payload attached to antibody |
| Fc | Crystallizable fragment of IgG; mediates effector functions and FcRn-mediated half-life |
| ADCC | Antibody-dependent cellular cytotoxicity; enhanced by afucosylation of Fc glycan |
