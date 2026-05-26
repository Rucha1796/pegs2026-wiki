# Nanobodies & VHH (Single Domain Antibodies)

Nanobodies — the variable domain of camelid heavy-chain-only antibodies (VHH) — featured prominently at PEGS 2026, from commercialization stories to developability profiling and benchmarking.

---

## Talks

### Benedikte Serruys (Sanofi / Ablynx) — *From Conception to Commercialization: Cablivi® NANOBODY® Compound*
- The story of **Cablivi® (caplacizumab)** — the world's first approved NANOBODY® therapeutic (2018, for acquired thrombotic thrombocytopenic purpura, aTTP).
- Origin: 1989, Prof. Raymond Hamers at VUB (Brussels) discovered that dromedaries have heavy-chain-only antibodies with a fully functional variable domain (VHH).
- VHH properties: 12–15 kDa (vs. 150 kDa full IgG), small and robust, easily linked in tandem, nanomolar–picomolar affinities, can target cryptic/challenging epitopes, sequence homology comparable to humanized/human mAbs, microbial manufacturing.
- Ablynx's journey: from discovery to acquisition by Sanofi; built a leading NANOBODY® platform.
- Lessons for drug developers: small format, easy reformatting, novel epitope access, and manufacturing advantages are real clinical differentiators.

### Gilad Kaplan (AstraZeneca) — *Lessons Learned from Biophysical Profiling of Clinical Stage Single Domain Antibodies*
- (Also covered in [Developability page](05_Antibody_Developability.md))
- Analyzed developability properties of AstraZeneca's **clinical-stage sdAb/VHH panel**.
- Key question: do early developability flags predict manufacturing problems in clinic?
- Properties assessed: yield, monomer content, reversible self-association, non-specific binding, low pH stability.
- Key finding: VHH developability assessment needs its own validated panel — mAb panels are not fully transferable. Some flags predict downstream issues; others do not.

### Koji Tsuda (University of Tokyo) — *Benchmarking Language Models for Antibody and Nanobody Tasks* (NbBench)
- (Also covered in [Protein Language Models page](02_Protein_Language_Models.md))
- **NbBench** — dedicated nanobody benchmark suite with 8 tasks:
  - Variable region classification (FR vs. CDR1/2/3)
  - CDR infilling (masked CDR reconstruction)
  - Antigen-nanobody binding prediction (SARS-CoV-2 and human IL-6 antigens)
  - Paratope prediction
  - Thermostability prediction
  - Polyreactivity prediction
  - Nanobody type classification (VHH, VNAR, VH, Vλ, Vκ)
  - Phage display affinity (against galectin-3)
- Compared general protein LMs, antibody-specific LMs, and nanobody-specific LMs.
- Key finding: domain-specific finetuning doesn't always outperform general LMs.

---

## VHH Properties vs. Conventional Antibodies

| Property | VHH (Nanobody) | mAb (IgG) |
|----------|---------------|-----------|
| Molecular weight | ~12–15 kDa | ~150 kDa |
| Epitope access | Cryptic/concave sites (enzymes, GPCRs) | Typically flat/convex surfaces |
| Stability | High thermal & chemical stability | Moderate |
| Manufacturing | Microbial (E. coli, yeast) | Mammalian cells (CHO) |
| Half-life | Short (without Fc) | Long (~21 days with Fc) |
| Formatting | Easy multivalent, bispecific formatting | More complex engineering required |
| Humanization | High sequence homology to human VH3 | Requires CDR grafting |
| Administered routes | IV, SC, inhaled, topical | Primarily IV or SC |

---

## Key Themes

- **Nanobodies are now clinically validated** — Cablivi proved the concept; multiple others in late-stage development.
- **Developability needs its own VHH-specific panel** — mAb panels are insufficient for sdAb characterization.
- **Benchmarking for VHH is in early stages** — NbBench is a first effort; more work needed.
- **Epitope access is a major advantage** — VHHs can bind GPCR active sites, enzyme active sites, and other cavities inaccessible to conventional Abs.
- **Manufacturing via microbial systems** is a cost advantage but requires careful attention to glycosylation and disulfide formation.

---

## Relevant OPIG Databases

From the OPIG Tools talk (Clare Gillis):
- **SAbDab:** 21,099 Fv structures + 2,032 nanobody structures
- **Thera-SAbDab:** 1,133 therapeutic sequences + structures  
- **Gordon et al. (2024):** 4,913 nanobody sequences (OPIG nanobody database)
