---
annotations_creators:
- no-annotation
language:
- en
license: cc0-1.0
multilinguality:
- monolingual
size_categories:
- 10K<n<100K
source_datasets:
- original
task_categories:
- tabular-classification
task_ids: []
pretty_name: "PubChem Compound Property Table"
tags:
- tabular
- chemistry
- science
---

# PubChem Compound Property Table

**Subtitle:** 60,000 compounds with molecular descriptors, Lipinski rules, stereochemistry and element composition.

---

## 📖 Description

### 60,000 PubChem compounds with computed chemistry

PubChem is the world's largest open chemistry database. This dataset pulls the computed property
table for **60,000 compounds** (CIDs 1–60,000) and expands it to **45 parameters**.

- **Identity** — CID, IUPAC name, InChIKey, molecular formula, canonical and isomeric SMILES.
- **Mass and size** — average, exact and monoisotopic mass, heavy atoms, covalent units, complexity.
- **Drug-likeness** — XLogP, TPSA, hydrogen-bond donors/acceptors, rotatable bonds, Lipinski
  violations and pass flag.
- **Stereochemistry** — atom and bond stereocentre counts, defined vs undefined centres, definition
  ratio.
- **Composition** — carbon, nitrogen, oxygen, sulfur and halogen counts parsed from the formula,
  hetero-atom total and element bands.

**49,648 compounds pass all four Lipinski rules** and **20,965 contain at least one
stereocentre**. The table supports QSAR modelling, scaffold analysis, descriptor benchmarking and
chemical-space exploration without any cheminformatics toolkit.

## 🧾 Columns (45)

`cid`, `molecular_formula`, `molecular_weight`, `exact_mass`, `monoisotopic_mass`, `xlogp`, `tpsa`, `complexity`, `charge`, `heavy_atom_count`, `h_bond_donors`, `h_bond_acceptors`, `rotatable_bonds`, `covalent_unit_count`, `atom_stereo_count`, `defined_atom_stereo`, `undefined_atom_stereo`, `bond_stereo_count`, `defined_bond_stereo`, `undefined_bond_stereo`, `canonical_smiles`, `isomeric_smiles`, `inchi_key`, `iupac_name`, `halogen_atoms`, `carbon_atoms`, `nitrogen_atoms`, `oxygen_atoms`, `sulfur_atoms`, `ring_flag`, `rule_of_five_violations`, `lipinski_pass`, `has_stereo`, `stereo_defined_ratio`, `is_fragment`, `is_large_molecule`, `mass_band`, `logp_band`, `tpsa_band`, `heavy_atom_band`, `hetero_atom_count`, `has_smiles`, `has_iupac_name`, `has_xlogp`, `formula_length`

## 💡 Ideas for using this data

1. **Drug-likeness** — Lipinski violations vs molecular size and polarity.
2. **Chemical space** — MW vs XLogP density map.
3. **Element composition** — halogen and hetero-atom distributions.
4. **Stereochemistry** — how often stereocentres are left undefined.
5. **Descriptor benchmarking** — TPSA and complexity distributions by mass band.
6. **Fragment libraries** — the sub-250 Da subset.
7. **Formula mining** — most common molecular formulas and hetero-atom patterns.
8. **Clustering** — fingerprint-free clustering on TPSA, logP and complexity.
9. **ML targets** — train a logP or solubility model from 2D descriptors.

## 📁 Files

| File | What it is |
|---|---|
| `pubchem_compounds.csv` | 60,000 compounds x 45 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`chemistry`, `pubchem`, `cheminformatics`, `molecular-descriptors`, `drug-discovery`

## 🔗 Provenance

- **Source:** **PubChem PUG REST** property table
  (`https://pubchem.ncbi.nlm.nih.gov/rest/pug/compound/cid/property/.../JSON`).
- **Sampling:** every CID from 1 to 60,000, requested in batches of 1,000 by POST; CIDs without
  a record are absent.
- **Processing:** 23 computed properties retrieved; element counts, rule-of-five violations, bands
  and availability flags derived.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Continuous upstream; snapshot here.** PubChem is updated weekly.

## ⚠️ Caveats

- CIDs are not a random sample of chemical space: low CIDs skew to small, early-deposited molecules.
- XLogP3 is a prediction, not an experimental measurement.
- Element counts are parsed from formula strings and ignore isotopes and charges.
- PubChem records change; CIDs are stable but properties are recomputed over time.
- No bioactivity, toxicity or assay data is included — properties only.

## 📜 Licence

PubChem data is public domain (U.S. National Library of Medicine).

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
