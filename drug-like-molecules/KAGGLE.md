# Drug-Like Molecules - ChEMBL Physicochemistry

**Subtitle:** 40,000 bioactive molecules with clinical phase, SMILES & drug properties

**Tags:** `tabular`, `chemistry`, `biology`

**Dataset File:** `chembl_molecules.csv` (40,000 rows, 53 columns, 18.7 MB)

**Provenance & Source:** ChEMBL Database API (ebi.ac.uk/chembl)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### 40,000 molecules from the ChEMBL drug-discovery database

ChEMBL is the European Bioinformatics Institute's manually curated database of bioactive molecules
with drug-like properties. This extract contains **40,000 molecules** with **53 parameters**,
combining ChEMBL's curation with computed physicochemical properties.

- **Identity and modality** — ChEMBL ID, preferred name, molecule type, structure type, ATC codes.
- **Clinical status** — maximum phase, first approval year, indication class, black-box warning,
  first-in-class, prodrug, natural-product and availability flags.
- **Administration** — oral, parenteral and topical flags.
- **Structure** — canonical SMILES, standard InChI and InChIKey.
- **Physicochemistry** — molecular weight (free base and full), ALogP, H-bond donors/acceptors, polar
  surface area, rotatable bonds, aromatic rings, heavy atoms, QED, natural-product likeness and the
  Lipinski rule-of-five violation count.
- **Derived** — approved/clinical/small-molecule/biologic flags, Ro5 pass, MW/logP/QED bands,
  property completeness and SMILES length.

**471 molecules are approved drugs (phase 4)** and **39,289 are small molecules**, so the
file spans everything from preclinical tool compounds to marketed medicines.

## 🧾 Columns (53)

`chembl_id`, `pref_name`, `molecule_type`, `max_phase`, `first_approval`, `indication_class`, `oral`, `parenteral`, `topical`, `black_box_warning`, `natural_product`, `first_in_class`, `chirality`, `prodrug`, `inorganic_flag`, `polymer_flag`, `availability_type`, `atc_classifications`, `canonical_smiles`, `standard_inchi`, `standard_inchi_key`, `mw_freebase`, `full_mwt`, `alogp`, `hba`, `hbd`, `psa`, `rtb`, `ro3_pass`, `num_ro5_violations`, `qed_weighted`, `aromatic_rings`, `heavy_atoms`, `np_likeness_score`, `full_molformula`, `atc_count`, `property_count`, `property_completeness_pct`, `is_approved`, `is_clinical`, `is_preclinical`, `is_small_molecule`, `is_biologic`, `has_black_box_warning`, `is_withdrawn`, `is_oral`, `passes_ro5`, `mw_band`, `logp_band`, `qed_band`, `smiles_length`, `heavy_atom_fraction_of_mw`, `has_structure`

## 💡 Ideas for using this data

1. **Drug-likeness** — QED and Ro5 violations for approved vs preclinical compounds.
2. **Property cliffs** — molecular weight vs ALogP, coloured by approval status.
3. **Modality shift** — small molecules vs biologics over approval year.
4. **Black-box warnings** — which indication classes carry the most warnings?
5. **Oral druggability** — oral vs parenteral compounds across property space.
6. **Natural products** — do natural-product-like molecules have different property profiles?
7. **Chemical similarity** — cluster by InChIKey/Murcko scaffold (external toolkit) or SMILES length.
8. **ATC taxonomy** — map molecules to therapeutic areas and compare size and phase.
9. **Predicting approval** — train a classifier on computed properties (beware selection bias).

## 📁 Files

| File | What it is |
|---|---|
| `chembl_molecules.csv` | 40,000 molecules x 53 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`chemistry`, `drug-discovery`, `chembl`, `molecules`, `pharmacology`, `bioinformatics`, `smiles`

## 🔗 Provenance

- **Source:** **ChEMBL API**, `https://www.ebi.ac.uk/chembl/api/data/molecule.json`,
  paginated 1,000 records at a time.
- **Scope:** the first 40,000 molecule records in ChEMBL's default ordering, not a random or
  approved-only sample.
- **Processing:** nested `molecule_properties`, `molecule_structures` and `atc_classifications`
  flattened; derived bands, flags and completeness measures added.
- **Snapshot date:** 22 November 2026 (ChEMBL release current at that date).

## 🔄 Update frequency

**Several times a year.** ChEMBL publishes roughly quarterly releases.

## ⚠️ Caveats

- This is the first 40,000 records by ChEMBL ID, not a representative sample of the database.
- Computed properties are absent for many biologics and older records; blanks are not zero.
- `max_phase` reflects the highest phase recorded, which may be stale for discontinued drugs.
- SMILES/InChI strings are large and can make the CSV heavy to load unfiltered.
- ChEMBL includes compounds that never became drugs; 'approved' is a minority class.
- Property values are calculated (ALogP, QED), not measured.
- Some molecules are salts or mixtures, so `full_mwt` differs from `mw_freebase`.

## 📜 Licence

ChEMBL data is licensed CC BY-SA 4.0 — attribution and share-alike apply.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `chembl_id` | `string` | ChEMBL molecule identifier. |
| 2 | `pref_name` | `string` | Preferred compound name. |
| 3 | `molecule_type` | `string` | Small molecule, protein, antibody, oligosaccharide, ... |
| 4 | `max_phase` | `number` | Highest clinical phase reached (4 = approved). |
| 5 | `first_approval` | `number` | Year of first approval, where approved. |
| 6 | `indication_class` | `number` | Therapeutic indication class. |
| 7 | `oral` | `boolean` | true when the molecule is orally administered. |
| 8 | `parenteral` | `boolean` | true when parenterally administered. |
| 9 | `topical` | `boolean` | true when topically administered. |
| 10 | `black_box_warning` | `number` | 1 when a black-box warning applies. |
| 11 | `natural_product` | `number` | 1 when the compound is a natural product. |
| 12 | `first_in_class` | `number` | 1 when flagged as first in class. |
| 13 | `chirality` | `number` | Chirality flag (-1 unknown, 0 achiral, 1 chiral, 2 racemic). |
| 14 | `prodrug` | `number` | 1 when the compound is a prodrug. |
| 15 | `inorganic_flag` | `number` | 1 when inorganic. |
| 16 | `polymer_flag` | `number` | 1 when a polymer. |
| 17 | `availability_type` | `number` | Prescription / over-the-counter availability code. |
| 18 | `atc_classifications` | `string` | ATC codes assigned to the molecule. |
| 19 | `canonical_smiles` | `string` | Canonical SMILES structure string. |
| 20 | `standard_inchi` | `string` | Standard InChI identifier. |
| 21 | `standard_inchi_key` | `string` | Standard InChIKey (27 characters). |
| 22 | `mw_freebase` | `number` | Molecular weight of the free base (Da). |
| 23 | `full_mwt` | `number` | Molecular weight including salts (Da). |
| 24 | `alogp` | `number` | Calculated ALogP lipophilicity. |
| 25 | `hba` | `number` | Hydrogen-bond acceptors. |
| 26 | `hbd` | `number` | Hydrogen-bond donors. |
| 27 | `psa` | `number` | Polar surface area (A^2). |
| 28 | `rtb` | `number` | Rotatable bonds. |
| 29 | `ro3_pass` | `string` | Lipinski rule-of-three pass flag (Y/N). |
| 30 | `num_ro5_violations` | `number` | Number of Lipinski rule-of-five violations. |
| 31 | `qed_weighted` | `number` | QED drug-likeness score (0-1). |
| 32 | `aromatic_rings` | `number` | Number of aromatic rings. |
| 33 | `heavy_atoms` | `number` | Number of heavy (non-hydrogen) atoms. |
| 34 | `np_likeness_score` | `number` | Natural-product likeness score. |
| 35 | `full_molformula` | `string` | Molecular formula including salts. |
| 36 | `atc_count` | `number` | Number of ATC codes. |
| 37 | `property_count` | `number` | How many of the 12 core computed properties are present. |
| 38 | `property_completeness_pct` | `number` | property_count as a percentage of 12. |
| 39 | `is_approved` | `boolean` | true when max_phase is 4. |
| 40 | `is_clinical` | `boolean` | true when the molecule reached phase 1 or later. |
| 41 | `is_preclinical` | `boolean` | true when max_phase is below 1 or unknown. |
| 42 | `is_small_molecule` | `boolean` | true when molecule_type is Small molecule. |
| 43 | `is_biologic` | `boolean` | true for protein/antibody/oligonucleotide modalities. |
| 44 | `has_black_box_warning` | `boolean` | true when black_box_warning is 1. |
| 45 | `is_withdrawn` | `boolean` | true when the withdrawn flag is set. |
| 46 | `is_oral` | `boolean` | true when oral administration is flagged. |
| 47 | `passes_ro5` | `boolean` | true when num_ro5_violations is 0. |
| 48 | `mw_band` | `string` | Molecular-weight band (Da). |
| 49 | `logp_band` | `string` | ALogP band. |
| 50 | `qed_band` | `string` | QED drug-likeness band. |
| 51 | `smiles_length` | `number` | Characters in the SMILES string. |
| 52 | `heavy_atom_fraction_of_mw` | `number` | Heavy atoms divided by molecular weight. |
| 53 | `has_structure` | `boolean` | true when a SMILES string exists. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
