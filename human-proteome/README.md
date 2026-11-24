---
license: cc-by-4.0
task_categories:
- tabular
tags:
- tabular
pretty_name: "Human Proteome - Reviewed Annotations"
---

# Human Proteome - Reviewed Annotations

**Subtitle:** 20,429 curated human proteins with sequences, domains & gene symbols

**Tags:** `tabular`, `biology`, `science`

**Dataset File:** `human_proteins.csv` (20,429 rows, 60 columns, 47.4 MB)

**Provenance & Source:** UniProtKB Swiss-Prot Database (uniprot.org)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### The curated human proteome

UniProtKB/Swiss-Prot is the manually reviewed protein knowledge base. This extract contains
**20,429 reviewed human proteins** with **60 parameters**, including the full sequence and
every major annotation layer.

- **Identity** — accession, entry name, protein name, gene names, organism, sequence length and mass,
  sequence version and the full amino-acid sequence.
- **Function** — curated function text, catalytic activity, cofactor, pathway, subunit and
  pharmaceutical-use annotations.
- **Localisation** — subcellular location text plus secreted, membrane, nuclear and mitochondrial flags.
- **Structure and interactions** — domain features, binding and active sites, disulfide bonds,
  modified residues and PDB identifiers.
- **Disease and variation** — disease associations, natural variants and caution notes.
- **Ontology** — GO term IDs, UniProt keywords and their counts.
- **Derived** — enzyme class, length band, mass per residue, annotation lengths and per-protein counts.

**4,616 proteins are enzymes**, **8,969 have at least one PDB structure**, and
**5,350** carry a disease association — enough to support structural bioinformatics, function
prediction and drug-target exploration.

## 🧾 Columns (60)

`accession`, `entry_name`, `protein_name`, `gene_names`, `organism`, `length`, `mass_da`, `sequence_version`, `ec_number`, `function`, `domains`, `go_ids`, `keywords`, `subcellular_location`, `involvement_in_disease`, `pdb_ids`, `sequence_similarity`, `binding_sites`, `active_sites`, `sequence`, `catalytic_activity`, `cofactor`, `subunit`, `pathway`, `pharmaceutical_use`, `tissue_specificity`, `signal_peptide`, `transit_peptide`, `chains`, `disulfide_bonds`, `variants`, `modified_residues`, `caution`, `gene_count`, `function_length`, `domain_count`, `go_term_count`, `pdb_structure_count`, `keyword_count`, `subcellular_location_count`, `binding_site_count`, `active_site_count`, `variant_count`, `disulfide_count`, `modified_residue_count`, `is_enzyme`, `ec_class`, `has_structure`, `has_signal_peptide`, `has_transit_peptide`, `has_disease_association`, `is_transmembrane`, `is_secreted`, `is_membrane_protein`, `is_nuclear`, `is_mitochondrial`, `has_caution`, `mass_per_residue_da`, `length_band`, `is_reviewed`

## 💡 Ideas for using this data

1. **Enzyme vs non-enzyme** — compare length, mass and domain counts between EC-annotated and other proteins.
2. **Structure coverage** — which protein families lack experimental structures?
3. **Localisation prediction** — build a classifier from sequence-derived features (length, mass, keywords).
4. **Disease proteome** — enrichment of GO terms and keywords among disease-associated proteins.
5. **Domain architecture** — parse the domain features to find recurrent multi-domain combinations.
6. **Sequence composition** — amino-acid frequencies by localisation class.
7. **Annotation quality** — protein entries with many variants and caution notes.
8. **Network analysis** — build a protein-protein graph from the subunit annotations.
9. **Text mining** — the function and disease fields are a rich corpus for biomedical NLP.

## 📁 Files

| File | What it is |
|---|---|
| `human_proteins.csv` | 20,429 proteins x 60 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`biology`, `proteomics`, `uniprot`, `bioinformatics`, `proteins`, `genomics`, `health`

## 🔗 Provenance

- **Source:** **UniProtKB REST API**, stream endpoint
  `https://rest.uniprot.org/uniprotkb/stream?query=reviewed:true+AND+organism_id:9606`.
- **Scope:** all reviewed (Swiss-Prot) entries for Homo sapiens, 33 returned fields including the
  complete sequence.
- **Processing:** TSV flattened to one row per protein; counts, flags, enzyme class and length bands
  derived; long free-text fields truncated only where noted.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Every eight weeks.** UniProt releases a new version on a regular cadence.

## ⚠️ Caveats

- Only reviewed entries are included; unreviewed TrEMBL records (the majority) are excluded.
- Annotation depth varies enormously between well-studied and newly added proteins.
- Function and disease text is truncated at 2,000 / 1,500 characters.
- Feature fields are semicolon-joined strings; their internal structure is positional and not normalised.
- Isoforms are not separate rows — one row per canonical entry.
- Mass is the computed mass of the canonical sequence, not a measured value.

## 📜 Licence

UniProt data is licensed CC BY 4.0 — cite UniProt and the source databases.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `accession` | `string` | UniProtKB primary accession. |
| 2 | `entry_name` | `string` | UniProt entry name (e.g. MOTSC_HUMAN). |
| 3 | `protein_name` | `string` | Recommended protein name, with synonyms. |
| 4 | `gene_names` | `string` | Gene name(s) mapped to the entry. |
| 5 | `organism` | `string` | Source organism (Homo sapiens). |
| 6 | `length` | `number` | Protein sequence length in amino acids. |
| 7 | `mass_da` | `number` | Computed molecular mass in daltons. |
| 8 | `sequence_version` | `number` | UniProt sequence version. |
| 9 | `ec_number` | `string` | Enzyme Commission number(s), where assigned. |
| 10 | `function` | `string` | Curated function annotation (truncated to 2,000 characters). |
| 11 | `domains` | `string` | Domain boundaries from the feature table. |
| 12 | `go_ids` | `string` | Gene Ontology term IDs (semicolon-joined). |
| 13 | `keywords` | `number` | UniProt keyword annotations (semicolon-joined). |
| 14 | `subcellular_location` | `string` | Curated subcellular location text. |
| 15 | `involvement_in_disease` | `string` | Disease association text (truncated to 1,500 characters). |
| 16 | `pdb_ids` | `string` | PDB structure identifiers. |
| 17 | `sequence_similarity` | `string` | Sequence similarity family annotation. |
| 18 | `binding_sites` | `string` | Binding-site features. |
| 19 | `active_sites` | `string` | Active-site features. |
| 20 | `sequence` | `string` | Full amino-acid sequence. |
| 21 | `catalytic_activity` | `number` | Catalytic activity annotation. |
| 22 | `cofactor` | `number` | Cofactor annotation. |
| 23 | `subunit` | `number` | Subunit / complex composition. |
| 24 | `pathway` | `number` | Pathway annotation. |
| 25 | `pharmaceutical_use` | `number` | Pharmaceutical use annotation. |
| 26 | `tissue_specificity` | `number` | Tissue expression specificity. |
| 27 | `signal_peptide` | `number` | Signal peptide feature. |
| 28 | `transit_peptide` | `number` | Transit peptide feature. |
| 29 | `chains` | `number` | Chain features. |
| 30 | `disulfide_bonds` | `number` | Disulfide bond features. |
| 31 | `variants` | `number` | Natural variant features. |
| 32 | `modified_residues` | `number` | Post-translational modification features. |
| 33 | `caution` | `number` | Caution / annotation warning text. |
| 34 | `gene_count` | `number` | Number of gene names listed. |
| 35 | `function_length` | `number` | Characters in the function annotation. |
| 36 | `domain_count` | `number` | Number of domain features. |
| 37 | `go_term_count` | `number` | Number of GO terms. |
| 38 | `pdb_structure_count` | `number` | Number of PDB structures. |
| 39 | `keyword_count` | `number` | Number of UniProt keywords. |
| 40 | `subcellular_location_count` | `number` | Number of subcellular location terms. |
| 41 | `binding_site_count` | `number` | Number of binding-site features. |
| 42 | `active_site_count` | `number` | Number of active-site features. |
| 43 | `variant_count` | `number` | Number of natural variants. |
| 44 | `disulfide_count` | `number` | Number of disulfide bonds. |
| 45 | `modified_residue_count` | `number` | Number of modified residues. |
| 46 | `is_enzyme` | `boolean` | true when an EC number is assigned. |
| 47 | `ec_class` | `number` | First digit of the EC number (enzyme class). |
| 48 | `has_structure` | `boolean` | true when at least one PDB structure exists. |
| 49 | `has_signal_peptide` | `boolean` | true when a signal peptide is annotated. |
| 50 | `has_transit_peptide` | `boolean` | true when a transit peptide is annotated. |
| 51 | `has_disease_association` | `boolean` | true when a disease association is annotated. |
| 52 | `is_transmembrane` | `boolean` | true when the keyword Transmembrane is present. |
| 53 | `is_secreted` | `boolean` | true when the location mentions secreted. |
| 54 | `is_membrane_protein` | `boolean` | true when the location mentions membrane. |
| 55 | `is_nuclear` | `boolean` | true when the location mentions nucleus. |
| 56 | `is_mitochondrial` | `boolean` | true when the location mentions mitochondria. |
| 57 | `has_caution` | `boolean` | true when a caution annotation exists. |
| 58 | `mass_per_residue_da` | `number` | Mass divided by sequence length. |
| 59 | `length_band` | `string` | Protein length band (aa). |
| 60 | `is_reviewed` | `boolean` | true — the query restricts to reviewed Swiss-Prot entries. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
