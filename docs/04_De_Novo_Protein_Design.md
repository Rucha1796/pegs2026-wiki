# De Novo Protein Design

One of the most exciting and contested areas at PEGS 2026. RFDiffusion and BindCraft represent the current state of the art; several groups showed genuine new biology from computationally designed proteins. Key tension: impressive results in published papers vs. difficulty of generalizing to new targets.

---

## Talks

### Rohith Krishna (David Baker Lab, University of Washington) — *Designing Biochemical Function with AI*
- Presented the full RFDiffusion → ProteinMPNN → RoseTTAFold pipeline for generative protein design.
- Key framing: like image generation ("I want a protein with C2 symmetry with a catalytic triad where the substrate leaving group points outward").
- **RFD3** (next generation): opens new possibilities beyond what's accessible through engineering native proteins — custom enzymes, new structural classes.
- Demonstrated design of:
  - Custom scaffolds
  - Antibody CDR design (with Jasper Butcher and Saman Salike)
  - **Building a composable programming language for structure-based protein design** — combining soft constraints (preferences) and hard constraints (fixed residues, symmetry).
  - Partial diffusion for **refining early hits** — noise existing designs and re-diffuse to improve them without restarting from scratch.
- Impact: RFDiffusion (Watson et al., *Nature* 2023), RFD3 (Krishna et al., *Science* 2024), RFantibody.

### Lennart Nickel (LPDI, EPFL, Correia Lab) — *Accurate Protein-Binder Design Using BindCraft*
- BindCraft uses **AlphaFold2 hallucination** (ColabDesign by Sergey Ovchinnikov) to design protein binders via gradient-based optimization.
- Loss function optimizes: interface pLDDT, interface pTM, inter/intramolecular pAE, contact count, helicity, radius of gyration.
- **State before deep learning:** ~100,000–10,000,000 proteins designed in silico per target; ~1,000–100,000 tested to get 1 binder.
- BindCraft dramatically reduces the experimental burden.
- Benchmarked against diverse targets: cellular receptors (Visterra), claudins, allergens, nucleases.
- Published: Pacesa & Nickel & Schellhaas et al., *Nature* (2025).

### Ariel Tennenhouse (Fleishman Lab) — *Computational Design of Antibody Repertoires*
- Developed **CADAbRe** (Combinatorial Assembly and Design of Antibody Repertoires): strategy for designing developable, structurally diverse antibody repertoires.
- Two sub-methods:
  - **CUMAb** (Computational hUMan AntiBody design): selects stable combinations of antibody frameworks without compromising humanness or affinity.
  - **LAffAb** (Libraries of high-Affinity Antibodies): designs stable combinations of CDR mutations to optimize affinity and stability.
- Scale challenge: "We need to design hundreds of millions to billions of antibodies." Context: Lipsh-Sokolik (Science, 2023) designed 1M enzyme variants; Weinstein (Nature Comm, 2023) designed 10M GFP variants.
- Key innovation: **polar epitope targeting** — natural antibodies target polar epitopes through germline-encoded (GRAB) motifs and complex CDR loops; de novo design has historically been limited to hydrophobic epitopes.
- Preprint: Tennenhouse, bioRxiv 2025.

### Manu Ben-Johny (Columbia University) — *De Novo Design of Synthetic Ion Channel Modulators*
- **ELIXIR** (Engineered Late-current Inhibitor X by Inactivation-gate Release): de novo designed peptide to inhibit pathological late sodium current (INaL) in cardiac and neurological disorders.
- Designed using protein design hallucination (Roney & Ovchinnikov, *Phys. Rev. Lett.* 2022).
- ELIXIR is a generalizable INaL inhibitor, selective for "pathogenic" INaL over physiological INaL.
- Applications: Long QT syndrome, Brugada syndrome, Dravet epilepsy, Timothy syndrome.
- Demonstrates that de novo design can reach **ion channel biology** — a target class historically inaccessible to protein design.

### Gian Marco Visani (University of Washington) — *Mapping the TCR-pMHC Specificity Landscape via De Novo Peptide Design*
- Designing peptides that activate specific T cells — inverse problem to the usual T cell epitope prediction.
- Uses computational design to map TCR specificity landscape; important for cancer immunotherapy (neoantigen design) and autoimmune tolerance.

---

## Key Themes

- **The design-test cycle is shortening dramatically.** AlphaFold2-based filtering can eliminate most failed designs before synthesis.
- **Partial diffusion** (noising + re-diffusing existing designs) is a powerful refinement strategy.
- **Polar epitopes remain hard.** The field has made progress on hydrophobic interfaces; polar epitopes require new strategies (CADAbRe, GRAB motifs).
- **Scale is everything.** Designs at 100M+ scale are becoming feasible computationally; the experimental bottleneck shifts to high-throughput screening.
- **Antibody design is getting closer.** RFantibody and Chai Discovery 2025 represent milestone results. Still requires some experimental iteration.

---

## Tools & Methods

| Tool | Description |
|------|-------------|
| RFDiffusion / RFD3 | Diffusion model for de novo protein backbone generation (Baker Lab) |
| ProteinMPNN | Sequence design for generated backbones |
| BindCraft | AF2 hallucination-based binder design (Correia Lab, EPFL) |
| CADAbRe / CUMAb / LAffAb | Antibody repertoire design (Fleishman Lab) |
| ColabDesign | Open-source hallucination framework by Sergey Ovchinnikov |
| RFantibody | RFDiffusion for antibody design |
| Chai-1 / Chai Discovery | All-atom generative model (Chai Discovery, 2025) |

---

## AIDD4B Training Course — De Novo Design & Pipelining Module
**Instructor:** David Nannemann (Rosetta Commons Foundation / Rosetta Design Group)

### The Classic De Novo Design Pipeline

```
RFDiffusion → ProteinMPNN → AlphaFold2 (self-consistency check)
```

| Step | Tool | What happens |
|------|------|-------------|
| 1. Backbone generation | RFDiffusion | Generates 3D backbone conditioned on target hotspot residues |
| 2. Sequence design | ProteinMPNN | Designs amino acid sequence to fold onto that backbone |
| 3. Self-consistency | AlphaFold2 | Predicts structure of the designed sequence — if it matches the RFDiffusion backbone (RMSD < 2Å, usually 0.5–1.5Å), design is considered self-consistent |

### RFDiffusion: Contig Syntax

The contig string defines which parts of the design are variable (hallucinated) vs. fixed (from input structure):

```
5-15/A10-25/30-40/0 B1-100
```

| Token | Meaning |
|-------|---------|
| `5-15` | Variable length hallucinated segment (5–15 residues) |
| `A10-25` | Fixed residues 10–25 from chain A of input PDB |
| `30-40` | Another hallucinated segment |
| `/0 ` | Chain break (space after zero separates chains) |
| `B1-100` | Full chain B (e.g., antigen) — fixed |

Hotspot residues (target interface residues to design against) specified separately as `B5,B12,B37`.

### ProteinMPNN Variants

| Variant | Optimized for |
|---------|--------------|
| Vanilla ProteinMPNN | General backbone-to-sequence design |
| SolubleMPNN | Improved solubility; avoids hydrophobic burial |
| AntibodyMPNN | Antibody CDR design (respects framework/CDR distinction) |
| ThermoMPNN | Thermostability-focused design |

### BindCraft: 4-Step Pipeline

BindCraft (Pacesa, Nickel, Schellhaas et al., *Nature* 2025) combines AF2 hallucination with ProteinMPNN:

**Step 1 — AF2 Hallucination (ColabDesign)**
- Gradient descent on the AF2 loss function to generate a binder sequence+structure simultaneously
- Optimizes: interface pLDDT, interface pTM, inter/intramolecular pAE, contact count, helicity, radius of gyration
- Applies clash checking at every step; discards trajectories with zero clashes early

**Step 2 — ProteinMPNN for non-interface residues**
- Holds the binding interface fixed from step 1
- Redesigns all non-interface residues with ProteinMPNN for better solubility and foldability
- Why: ColabDesign produces good binding sites but can produce sticky/insoluble proteins; ProteinMPNN fixes the non-binding scaffold

**Step 3 — Multi-metric Filtering**

| Metric | Filter threshold | What it measures |
|--------|-----------------|-----------------|
| pLDDT | > 0.7 | Per-residue confidence (whole binder) |
| pTM | > 0.7 | Overall model accuracy |
| i_pTM | high | Interface-specific predicted TM score |
| pAE | low | Predicted aligned error (whole complex) |
| i_pAE / ipSAE_min | low | Interface-specific PAE |
| LIS | — | Local Interface Score (interface quality) |
| pDockQ | > 0.23 | Docking quality score |
| Interface dG | negative | Predicted binding free energy |
| dG/dSASA ratio | — | Binding efficiency relative to buried surface area |
| Shape complementarity | high | Geometric fit of binder to target surface |
| H-bonds at interface | high count | Polar contacts across interface |

**Step 4 — Self-consistency Check**
- Run ProteinMPNN on the designed complex → get designed sequence
- Run AlphaFold2 on that sequence alone (binder only) and in complex
- Designed structure must match both the complex prediction AND the binder-only prediction (RMSD < 2Å)
- This filters out designs that only "look good" in the context of the target

**Why BindCraft works:**
- ColabDesign (hallucination) = excellent at finding binding sites; poor at producing stable scaffolds
- ProteinMPNN = excellent at designing stable, soluble sequences; limited to a given backbone
- Combining them gives you both: a good binding site AND a stable protein

**Practical tips:**
- Hydrophobic binding sites are easier to design against than polar ones
- Provide multiple input structures for the target (different conformations)
- Trim the target to the relevant domain — do not feed in the whole protein

### Antibody-Specific De Novo Pipelines

| Pipeline | Lab/Company | Approach | Hit rate / Best affinity |
|---------|------------|---------|------------------------|
| **RFantibody** | Baker Lab (IPD/UW) + MIT license | RFDiffusion adapted for antibody CDR hallucination | Published 2024 |
| **JAM** | Nabla Bio | — | — |
| **Chai-2** | Chai Discovery | All-atom generative; ≥1 binder for >50% of 52 targets | 18.3 pM – ~200 nM; MIT license |
| **IgGM** | Tencent | — | 7/60 targets; MIT license |
| **Germinal** | Arc Institute / Hie Lab | Dual-objective pLM + AF-Multimer | 4–22% nanomolar binders per target (43–101 designs); MIT |
| **mBER** | Manifold Bio | — | 0.02–8% median hit rate; MIT |

**General take:** Most pipelines achieve hits on 10–50% of targets, with affinities in the nanomolar range — meaningful but not yet routine without wet-lab follow-up.
