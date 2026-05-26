# Structure Prediction

Structure prediction tools — led by AlphaFold2 — are now foundational infrastructure for biologics design. PEGS 2026 featured talks using these tools for antibody design, binder engineering, and HDX/biophysical modeling.

---

## Talks

### Lora Hamuro (Clinical Pharmacology, Oncology & Cell Therapy) — *Advanced Modeling of Immunogenicity for a Biotherapeutic Combination*
- Focused on immunogenicity modeling for **combination biologics** (now standard in oncology — Nivolumab + Ipilimumab, Trastuzumab + Pertuzumab, etc.).
- Used structural modeling to understand how co-administered biologics might interact to increase ADA risk through synergistic immune activation.
- Case study: Nivolumab + Ipilimumab — complementary PD-1 and CTLA-4 blockade can amplify immune responses, potentially increasing risk of anti-drug antibodies.
- Key takeaway: immunogenicity assessment for combinations requires modeling the **system**, not just individual molecules.

### Yoshitomo Hamuro (PEGS, Advanced Modeling Techniques Session) — *Advanced Modeling Techniques for Biologics*
- Focused on **Hydrogen-Deuterium Exchange Mass Spectrometry (HDX-MS)** modeling combined with computational structure prediction.
- HDX-MS provides residue-level structural dynamics data; combining with AlphaFold2 structures enables better prediction of aggregation-prone regions and epitope mapping.
- Showed that structure prediction models are now accurate enough to use as input for HDX interpretation, reducing need for experimental crystallography in early-stage projects.

---

## AIDD4B Training Course — Structure Prediction Module
**Instructor:** David Nannemann (Rosetta Commons Foundation / Rosetta Design Group)

This was a hands-on training session covering how to use and interpret structure prediction tools in biologics design workflows.

**Key conceptual distinction taught:**

| Concept | Input | Output | Goal | Example Tools |
|---------|-------|--------|------|---------------|
| Structure Modeling | Sequence | 3D structure | Predict structure | AlphaFold2, Boltz-2, ImmuneBuilder |
| Structure-based Design | Structure | Sequence | Design from fold | ProteinMPNN, ColabDesign |

**Structure prediction output metrics explained:**

| Metric | Units | Range | Good Value | What it measures |
|--------|-------|-------|------------|-----------------|
| RMSD | Å | >0 | <1.2 Å (excellent) | Average atom distance after superposition |
| pLDDT | — | 0–1 | >0.90 | Per-residue confidence score |
| GDT | % | 0–100 | >95 | Global structural similarity |
| pTM | — | 0–1 | >0.70 | Predicted overall model accuracy |
| PAE (Predicted Aligned Error) | — | low = good | Low off-diagonal | Confidence in relative residue placement |

**Key practical takeaways from the course:**
- **MSA quality matters:** A deep multiple sequence alignment (MSA) produces higher-quality predictions. MSA sub-sampling can bias outputs toward alternative conformations.
- **De novo designed proteins** are often well-predicted without an MSA — a useful diagnostic for checking design quality.
- **PAE (off-diagonal blocks)** is the key metric for assessing protein-protein interfaces — low inter-chain PAE indicates confident interface prediction.
- **Boltz-2 YAML format** supports protein, DNA, RNA, small molecules (SMILES or CCD), cyclic peptides, and post-translational modifications — enabling fully integrated protein-ligand docking.
- Practical tip: when modeling a protein-protein complex (e.g., PD1:PDL1), use "paired_unpaired" MSA generation to capture evolutionarily correlated mutations at the interface.
- **ImmuneBuilder** installation on Google Colab is unreliable; local installation is more robust.

---

## Key Tools Covered

| Tool | Input | Output | Notes |
|------|-------|--------|-------|
| **AlphaFold2** | Sequence | 3D structure | Gold standard; pLDDT and PAE scores used for design filtering |
| **AlphaFold-Multimer** | Multiple sequences | Complex structure | Used for antibody-antigen complex modeling |
| **Boltz-2** | Sequence + small molecule | Complex structure | New; supports protein-small molecule docking directly |
| **ImmuneBuilder** | Ab/Nb sequence | Ab/Nb structure | Specialized for antibody and nanobody structure prediction; faster than AF2 for immune molecules |
| **IgFold** | Ab sequence | Ab structure | Johns Hopkins; fast antibody-specific structure prediction |
| **ColabFold** | Sequence | Structure | Open-access AF2 via MMseqs2 MSA; widely used in academia |

---

## Key Themes

- **Structure prediction is now a commodity input** to design pipelines (RFDiffusion, BindCraft, WALLE all use AF2 predictions as a starting point or filter).
- **pLDDT and PAE scores** from AlphaFold2 are widely used as proxies for confidence, but they are **insufficient as standalone proxies for binding affinity** (AbBiBench finding #3).
- **Boltz-2** is an emerging tool for integrated protein-small molecule design — relevant for ADCs and targeted degraders.
- **ImmuneBuilder** provides fast, specialized structure prediction for antibodies and nanobodies, enabling high-throughput structural analysis.
