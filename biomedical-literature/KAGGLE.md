# Biomedical Literature 2024-2025

**Subtitle:** 40,000 open-access articles with authors, abstracts, MeSH terms & citations

**Tags:** `tabular`, `science`, `health`

**Dataset File:** `europepmc_articles.csv` (40,037 rows, 49 columns, 96.0 MB)

**Provenance & Source:** Europe PMC REST API (europepmc.org)

**Expected Update Frequency:** `monthly`

---

## 📖 Description

### 40,000 open-access biomedical articles

Europe PMC aggregates PubMed, PubMed Central, preprints and patents. This extract pulls
**40,000 open-access articles published in 2024–2025** with **49 parameters** each.

- **Bibliographic identity** — Europe PMC id, source, PMID, PMCID, DOI, title, journal, ISSN/eISSN,
  volume, issue and publication dates.
- **Authorship** — author string, parsed author count, first and last author, first affiliation.
- **Content** — abstract (truncated), author keywords, MeSH descriptors, indexed chemicals.
- **Funding and licensing** — grant count and agencies, licence, language.
- **Access** — open-access flag, in-PMC, PDF, supplementary files, references and text-mined terms.
- **Impact** — citation counts and citation bands.
- **Derived** — abstract/title lengths, review and clinical-trial flags, DOI presence, keyword/MeSH/
  author counts and a recency flag.

**40,000 records are open access**, **5,582 are reviews**, and the sample spans
**1,722 journals** — a bibliometric corpus for text mining, citation analysis and research
policy work.

## 🧾 Columns (49)

`id`, `source`, `pmid`, `pmcid`, `doi`, `title`, `author_string`, `author_count`, `first_author`, `last_author`, `first_affiliation`, `journal_title`, `issn`, `essn`, `volume`, `issue`, `pub_year`, `pub_month`, `pub_type`, `is_review`, `is_clinical_trial`, `is_open_access`, `in_pmc`, `has_pdf`, `has_suppl`, `has_references`, `has_text_mined_terms`, `cited_by_count`, `citation_count`, `abstract`, `abstract_length`, `abstract_word_count`, `title_length`, `keyword_count`, `keywords`, `mesh_count`, `mesh_terms`, `chemical_count`, `grant_count`, `grant_agencies`, `language`, `license`, `first_publication_date`, `electronic_publication_date`, `full_text_url`, `has_doi`, `has_abstract`, `citation_band`, `is_recent`

## 💡 Ideas for using this data

1. **Topic modelling** — cluster abstracts to map the 2024–2025 biomedical research landscape.
2. **Citation drivers** — what predicts citations: journal, author count, MeSH terms, open access?
3. **Author productivity** — distribution of papers per author and per affiliation.
4. **Funding landscape** — grant agencies and their output by topic.
5. **Journal analysis** — output and citation profiles of the largest journals.
6. **MeSH co-occurrence** — build a disease–method network from MeSH descriptors.
7. **Review vs primary research** — how do abstracts and citation patterns differ?
8. **Text classification** — predict review status or clinical-trial status from the abstract.
9. **Open-access effect** — compare citations for OA vs non-OA records in the same journal.

## 📁 Files

| File | What it is |
|---|---|
| `europepmc_articles.csv` | 40,000 articles x 49 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`biomedical`, `literature`, `europe-pmc`, `pubmed`, `text-mining`, `bibliometrics`, `science`

## 🔗 Provenance

- **Source:** **Europe PMC REST API**,
  `https://www.ebi.ac.uk/europepmc/webservices/rest/search?resultType=core&format=json`.
- **Query:** `OPEN_ACCESS:y AND (PUB_YEAR:2024 OR PUB_YEAR:2025)`, cursor-paginated 1,000 records at
  a time until 40,000 records were collected.
- **Processing:** nested author, journal, MeSH, keyword, chemical, grant and full-text objects
  flattened; counts, flags and bands derived; abstracts truncated at 2,500 characters.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Daily.** Europe PMC indexes new articles continuously.

## ⚠️ Caveats

- Only open-access records with a 2024 or 2025 publication year are included.
- The 40,000 records follow Europe PMC's default relevance ordering, not a random sample.
- Citation counts differ between sources and lag behind publication.
- Abstracts are truncated at 2,500 characters; the full text is not included.
- MeSH indexing is incomplete for very recent articles and preprints.
- Author affiliations are often only available for the first author.
- Journal titles are free text and may appear with variants.

## 📜 Licence

Europe PMC content carries per-record licences; open-access records are mostly CC BY.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `id` | `number` | Europe PMC record identifier. |
| 2 | `source` | `string` | Source database (MED, PMC, PPR, ...). |
| 3 | `pmid` | `number` | PubMed identifier. |
| 4 | `pmcid` | `string` | PubMed Central identifier. |
| 5 | `doi` | `string` | Digital Object Identifier. |
| 6 | `title` | `string` | Article title. |
| 7 | `author_string` | `string` | Author list as a single string. |
| 8 | `author_count` | `number` | Number of authors parsed from the structured author list. |
| 9 | `first_author` | `string` | First author's full name. |
| 10 | `last_author` | `string` | Last author's full name. |
| 11 | `first_affiliation` | `string` | Affiliation of the first author. |
| 12 | `journal_title` | `string` | Journal title. |
| 13 | `issn` | `string` | Print ISSN. |
| 14 | `essn` | `string` | Electronic ISSN. |
| 15 | `volume` | `number` | Journal volume. |
| 16 | `issue` | `string` | Journal issue. |
| 17 | `pub_year` | `number` | Publication year. |
| 18 | `pub_month` | `number` | Publication month. |
| 19 | `pub_type` | `string` | Publication type string(s). |
| 20 | `is_review` | `boolean` | true when the publication type includes a review. |
| 21 | `is_clinical_trial` | `boolean` | true when tagged as a clinical trial. |
| 22 | `is_open_access` | `boolean` | true when the record is open access. |
| 23 | `in_pmc` | `boolean` | true when full text is in PubMed Central. |
| 24 | `has_pdf` | `boolean` | true when a PDF is available. |
| 25 | `has_suppl` | `boolean` | true when supplementary files exist. |
| 26 | `has_references` | `boolean` | true when references are indexed. |
| 27 | `has_text_mined_terms` | `boolean` | true when text-mined terms are available. |
| 28 | `cited_by_count` | `number` | Number of citations recorded by Europe PMC. |
| 29 | `citation_count` | `number` | Citation count from the source record. |
| 30 | `abstract` | `string` | Abstract text (truncated to 2,500 characters). |
| 31 | `abstract_length` | `number` | Characters in the stored abstract. |
| 32 | `abstract_word_count` | `number` | Words in the stored abstract. |
| 33 | `title_length` | `number` | Characters in the title. |
| 34 | `keyword_count` | `number` | Number of author keywords. |
| 35 | `keywords` | `string` | Author keywords (semicolon-joined). |
| 36 | `mesh_count` | `number` | Number of MeSH headings. |
| 37 | `mesh_terms` | `string` | MeSH descriptor names (semicolon-joined). |
| 38 | `chemical_count` | `number` | Number of indexed chemicals. |
| 39 | `grant_count` | `number` | Number of funding grants. |
| 40 | `grant_agencies` | `string` | Funding agency names. |
| 41 | `language` | `string` | Language of the article. |
| 42 | `license` | `string` | Licence reported for the article. |
| 43 | `first_publication_date` | `date` | First publication date. |
| 44 | `electronic_publication_date` | `date` | Electronic publication date. |
| 45 | `full_text_url` | `string` | First full-text URL. |
| 46 | `has_doi` | `boolean` | true when a DOI is present. |
| 47 | `has_abstract` | `boolean` | true when an abstract is present. |
| 48 | `citation_band` | `string` | Citation-count band. |
| 49 | `is_recent` | `boolean` | true for 2025 publications. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
