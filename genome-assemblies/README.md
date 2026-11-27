---
annotations_creators:
- no-annotation
language:
- en
license: cc0-1.0
multilinguality:
- monolingual
size_categories:
- 10K<n<1M
source_datasets:
- original
task_categories:
- tabular-classification
task_ids: []
pretty_name: "NCBI RefSeq Sequenced Genomes"
tags:
- tabular
- science
---

# NCBI RefSeq Sequenced Genomes


## ⭐ Upvote & Support
If you find this dataset useful for your research, machine learning projects, or data visualization, please consider giving it an **Upvote**! Your support helps make open data more accessible to the community.


# Sequenced Genomes — NCBI RefSeq Assembly Catalogue

**Subtitle:** 576,154 genome assemblies with taxonomy, size, GC content, contiguity, gene counts and annotation.

---

## 📖 Description

### 576,154 sequenced genomes from NCBI RefSeq

NCBI's RefSeq assembly summary lists every genome assembly in the reference sequence collection.
This dataset contains **576,154 assemblies** (latest versions with a reported genome size) and
**62 parameters** — one of the widest genomics catalogues available.

- **Identity** — RefSeq accession, assembly name, organism, species, genus, taxonomy ids,
  strain or isolate, submitter and BioProject/BioSample accessions.
- **Assembly** — level (complete, chromosome, scaffold, contig), release type, representation,
  ploidy, release date and decade, paired GenBank assembly and FTP path.
- **Size and composition** — genome size in base pairs and megabases, ungapped size, GC percent,
  replicons, scaffolds, contigs and scaffolds per contig.
- **Annotation** — annotation provider, release name and date, total, protein-coding and
  non-coding gene counts, coding share, gene density and linked PubMed records.
- **Flags** — reference, representative, complete, chromosome-level, animal, plant, bacteria,
  fungi, virus and human markers.

**86,191 assemblies are complete genomes**, **9,184**
are chromosome-level and **575,414** carry gene annotations. The largest groups
are bacteria (554,612), viral (15,865), archaea (3,220), fungi (674), vertebrate other (622).

## 🧾 Columns (62)

`assembly_accession`, `assembly_name`, `organism_name`, `species`, `genus`, `taxid`, `species_taxid`, `infraspecific_name`, `isolate`, `refseq_category`, `version_status`, `assembly_level`, `release_type`, `genome_rep`, `assembly_type`, `group`, `seq_rel_date`, `seq_rel_year`, `seq_rel_month`, `asm_submitter`, `annotation_provider`, `annotation_name`, `annotation_date`, `annotation_year`, `genome_size_bp`, `genome_size_mb`, `genome_size_ungapped_mb`, `gc_percent`, `replicon_count`, `scaffold_count`, `contig_count`, `scaffolds_per_contig`, `total_gene_count`, `protein_coding_gene_count`, `non_coding_gene_count`, `protein_coding_share`, `genes_per_mb`, `pubmed_id`, `pubmed_count`, `bioproject`, `biosample`, `paired_asm_comp`, `has_paired_asm`, `excluded_from_refseq`, `relation_to_type_material`, `asm_not_live_date`, `ftp_path`, `is_reference`, `is_representative`, `is_complete_genome`, `is_chromosome_level`, `is_scaffold_level`, `is_contig_level`, `has_annotation`, `has_pubmed`, `is_animal`, `is_plant`, `is_bacteria`, `is_fungi`, `is_virus`, `is_human`, `release_decade`

## 💡 Ideas for using this data

1. **Genome size** — the distribution across animals, plants, bacteria and fungi.
2. **Assembly quality** — contiguity and completeness by release year.
3. **Annotation** — gene density vs genome size and GC content.
4. **Taxonomy** — which genera have the most sequenced assemblies.
5. **Sequencing boom** — assemblies per year and per decade.
6. **Reference genomes** — what fraction of species have a reference assembly.
7. **GC content** — variation across organism groups.
8. **Publication link** — assemblies with vs without a paper.

## 📁 Files

| File | What it is |
|---|---|
| `genome_assemblies.csv` | 576,154 assemblies x 62 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`genomics`, `bioinformatics`, `biology`, `ncbi`, `dna`, `science`, `taxonomy`

## 🔗 Provenance

- **Source:** **NCBI RefSeq assembly summary**
  (`assembly_summary_refseq.txt`, `ftp.ncbi.nlm.nih.gov/genomes/ASSEMBLY_REPORTS/`).
- **Processing:** the 38-column tab-separated summary was streamed and parsed; assemblies without
  a reported genome size were dropped; 23 fields were derived (species, genus, sizes in Mb,
  contiguity, gene density, flags).
- **Snapshot date:** 27 November 2026.

## 🔄 Update frequency

**Monthly.** NCBI refreshes the assembly summary continuously.

## ⚠️ Caveats

- Only RefSeq (GCF) assemblies are included; GenBank-only (GCA) assemblies are not listed.
- Assemblies without a reported genome size are excluded.
- Gene counts exist only where an NCBI annotation has been run.
- The file is a single snapshot; suppressed assemblies may disappear from later snapshots.
- Genome size is the assembly length, not the true biological genome size.
- Organism names are free text from submitters and are not fully normalised.

## 📜 Licence

NCBI RefSeq data — US government work, public domain.

