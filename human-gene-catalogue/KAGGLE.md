# Human Gene Catalogue — HGNC Complete Set

**Subtitle:** 45,470 approved human gene loci with nomenclature, cytogenetics and 30+ database cross-references.

---

## 📖 Description

### 45,470 human genes from the HGNC complete set

The HUGO Gene Nomenclature Committee is the authority that assigns every approved human gene
symbol. Its complete set is the reference table behind nearly every human-genetics pipeline. This
dataset contains **45,470 loci** and **73 parameters**, one row per HGNC record.

- **Identity** — HGNC id, approved symbol and name, locus group and type, status, cytogenetic
  location split into chromosome and band.
- **Nomenclature history** — aliases, previous symbols and names, symbol/name change dates, approval
  and modification dates.
- **Cross-references** — Entrez, Ensembl, Vega, UCSC, ENA, RefSeq, CCDS, UniProt, MGD, RGD, OMIM,
  miRBase, Orphanet, IUPHAR, lncRNA databases, MANE Select and GenCC.
- **Grouping and literature** — gene groups with ids, linked PubMed records and counts.
- **Derived** — coding/pseudogene/non-coding flags, cross-reference availability, alias and PubMed
  counts, symbol/name lengths and alias density.

**19,299 protein-coding genes** and **17,577 genes with an OMIM entry** are included across
**2,004 distinct gene groups** — a base table for genomics, text mining and gene-set enrichment.

## 🧾 Columns (73)

`hgnc_id`, `symbol`, `name`, `locus_group`, `locus_type`, `status`, `location`, `chromosome`, `cytoband`, `alias_symbol`, `alias_count`, `alias_name`, `prev_symbol`, `prev_symbol_count`, `prev_name`, `gene_group`, `gene_group_id`, `gene_group_count`, `date_approved_reserved`, `date_symbol_changed`, `date_name_changed`, `date_modified`, `entrez_id`, `ensembl_gene_id`, `vega_id`, `ucsc_id`, `ena`, `refseq_accession`, `ccds_id`, `uniprot_ids`, `pubmed_id`, `pubmed_count`, `mgd_id`, `rgd_id`, `lsdb`, `cosmic`, `omim_id`, `mirbase`, `homeodb`, `snornabase`, `bioparadigms_slc`, `orphanet`, `pseudogene_org`, `horde_id`, `merops`, `imgt`, `iuphar`, `kznf_gene_catalog`, `mamit_trnadb`, `cd`, `lncrnadb`, `enzyme_id`, `intermediate_filament_db`, `rna_central_id`, `lncipedia`, `gtrnadb`, `agr`, `mane_select`, `gencc`, `is_protein_coding`, `is_pseudogene`, `is_non_coding`, `is_approved`, `has_ensembl`, `has_uniprot`, `has_omim`, `has_refseq`, `has_ccds`, `has_mane_select`, `has_gene_group`, `symbol_length`, `name_length`, `alias_density`

## 💡 Ideas for using this data

1. **Gene density** — genes per chromosome and cytoband.
2. **Nomenclature churn** — symbol changes over time by locus type.
3. **Gene families** — largest HGNC gene groups and their chromosomal clustering.
4. **Cross-reference completeness** — which databases cover which locus types.
5. **Literature attention** — PubMed records per gene and per family.
6. **Pseudogene landscape** — pseudogene families and their parent genes.
7. **Non-coding RNA catalogue** — lncRNA and snoRNA counts by chromosome.
8. **Alias ambiguity** — genes with many aliases as a text-mining hazard.
9. **OMIM disease coverage** — protein-coding genes with Mendelian phenotypes.

## 📁 Files

| File | What it is |
|---|---|
| `hgnc_genes.csv` | 45,470 genes x 73 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`genomics`, `hgnc`, `genes`, `bioinformatics`, `human-genetics`, `biology`

## 🔗 Provenance

- **Source:** **HGNC complete set** (`hgnc_complete_set.txt`), published by the HUGO Gene
  Nomenclature Committee and hosted on Google Cloud Storage.
- **Processing:** tab-separated file parsed as-is; pipe-separated multi-value fields retained;
  cytogenetic location split into chromosome and band; counts and boolean availability flags derived.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Monthly.** HGNC republishes the complete set as nomenclature changes.

## ⚠️ Caveats

- HGNC is a nomenclature authority: it lists genes, not variants or expression values.
- Cytogenetic locations are approximate and some entries have no location.
- Multi-value fields (aliases, PubMed ids, groups) are pipe-separated strings, not arrays.
- Withdrawn entries are included and flagged by `status`.
- Identifiers change upstream; joins should use `hgnc_id` rather than symbols.

## 📜 Licence

CC0 1.0 public-domain dedication — HUGO Gene Nomenclature Committee.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
