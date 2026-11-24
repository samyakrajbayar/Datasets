# Research Data DOIs - DataCite

**Subtitle:** 40,000 research outputs with creators, types, funding and usage metrics

**Tags:** `tabular`, `science`, `research`

**Dataset File:** `datacite_dois.csv` (168,892 rows, 59 columns, 51.9 MB)

**Provenance & Source:** DataCite REST API (api.datacite.org)

**Expected Update Frequency:** `monthly`

---

## 📖 Description

### 40,000 research-data DOIs

DataCite is the global DOI registration agency for research data, software, samples and other
non-article outputs. This dataset contains **40,000 DOIs** with **59 parameters** each.

- **Identity** — DOI, title, publisher, publication year, resource type (free text and controlled).
- **People** — creator count, first creator, creator names and affiliations, contributor count and
  ORCID coverage.
- **Description** — subjects, primary description, language and version.
- **Rights and links** — rights statements, landing page and content URL, active state.
- **Impact metrics** — views, downloads, references, citations, parts and related records.
- **Funding and geography** — funder names, geo-locations with coordinates, dates, sizes and formats.
- **Derived** — dataset/software/text/image/preprint flags, ORCID presence, year bands and counts.

**8,262 records are datasets**, **4,401 are software**, and **17,244**
(43.1%) have at least one creator ORCID — a view of the research-data ecosystem
through its persistent identifiers.

## 🧾 Columns (59)

`doi`, `title`, `publisher`, `publication_year`, `resource_type`, `resource_type_general`, `creator_count`, `first_creator`, `creator_names`, `creator_affiliations`, `contributor_count`, `subject_count`, `subjects`, `description_count`, `description`, `language`, `version`, `rights_count`, `rights`, `url`, `content_url`, `is_active`, `state`, `view_count`, `download_count`, `reference_count`, `citation_count`, `part_count`, `part_of_count`, `related_count`, `funding_count`, `funder_names`, `geo_count`, `geo_place`, `geo_lat`, `geo_lon`, `date_count`, `dates`, `size_count`, `sizes`, `format_count`, `formats`, `identifier_count`, `orcid_count`, `title_length`, `description_length`, `has_orcid`, `has_description`, `has_funding`, `has_geo`, `has_related`, `has_rights`, `is_dataset`, `is_software`, `is_text`, `is_image`, `is_preprint`, `year_band`, `decade`

## 💡 Ideas for using this data

1. **Repository landscape** — which publishers/repositories mint the most DOIs?
2. **Type mix** — datasets vs software vs text over publication year.
3. **FAIR metadata** — ORCID, rights, funding and geo coverage by repository.
4. **Citation advantage** — do records with richer metadata get more views/downloads?
5. **Geography** — map geo-located records and compare with funder countries.
6. **Funding networks** — funders and their output types.
7. **Software citation** — how software DOIs differ from dataset DOIs.
8. **Title and description NLP** — topic-model research outputs across disciplines.
9. **Metadata completeness** — build a repository scorecard from the derived coverage flags.

## 📁 Files

| File | What it is |
|---|---|
| `datacite_dois.csv` | 40,000 DOIs x 59 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`datacite`, `doi`, `research-data`, `open-science`, `metadata`, `repositories`, `bibliometrics`

## 🔗 Provenance

- **Source:** **DataCite REST API**, `https://api.datacite.org/dois`,
  paginated 1,000 records per page.
- **Scope:** the first 40,000 DOI records returned by the default API ordering.
- **Processing:** nested creators, contributors, subjects, descriptions, rights, funding, geo-locations,
  dates, sizes and formats flattened; coverage flags and year bands derived.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Continuous.** DataCite registers DOIs throughout the day.

## ⚠️ Caveats

- This is the first 40,000 records by API ordering, not a random or complete census.
- Metadata quality varies widely between repositories; many fields are optional.
- View and download counts are repository-reported and not comparable across all members.
- Descriptions may contain HTML and are truncated at 1,500 characters.
- Resource types are free text in `resource_type`, so use the controlled general type for grouping.
- Geo-locations are optional and often absent for non-spatial data.
- Publication year is the DOI registration year for some records, not the data collection year.

## 📜 Licence

DataCite metadata is released under CC0 1.0; individual records may carry other licences.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `doi` | `string` | DOI of the research output. |
| 2 | `title` | `string` | Primary title. |
| 3 | `publisher` | `string` | Data repository or publisher. |
| 4 | `publication_year` | `number` | Year of publication. |
| 5 | `resource_type` | `string` | Free-text resource type. |
| 6 | `resource_type_general` | `string` | Controlled resource type (Dataset, Software, Text, ...). |
| 7 | `creator_count` | `number` | Number of creators. |
| 8 | `first_creator` | `string` | First creator's name. |
| 9 | `creator_names` | `string` | All creator names (semicolon-joined). |
| 10 | `creator_affiliations` | `string` | Distinct creator affiliations. |
| 11 | `contributor_count` | `number` | Number of contributors. |
| 12 | `subject_count` | `number` | Number of subject keywords. |
| 13 | `subjects` | `string` | Subject keywords (semicolon-joined). |
| 14 | `description_count` | `number` | Number of descriptions. |
| 15 | `description` | `string` | Primary description (truncated to 1,500 characters). |
| 16 | `language` | `string` | Language code. |
| 17 | `version` | `string` | Version string. |
| 18 | `rights_count` | `number` | Number of rights statements. |
| 19 | `rights` | `string` | Rights/licence statements (semicolon-joined). |
| 20 | `url` | `string` | Landing-page URL. |
| 21 | `content_url` | `string` | Direct content URL, where given. |
| 22 | `is_active` | `boolean` | true when the DOI is active. |
| 23 | `state` | `string` | DOI state (findable, registered, ...). |
| 24 | `view_count` | `number` | DataCite view count. |
| 25 | `download_count` | `number` | DataCite download count. |
| 26 | `reference_count` | `number` | Number of references. |
| 27 | `citation_count` | `number` | Number of citations. |
| 28 | `part_count` | `number` | Number of parts. |
| 29 | `part_of_count` | `number` | Number of parent records. |
| 30 | `related_count` | `number` | Number of related identifiers. |
| 31 | `funding_count` | `number` | Number of funding references. |
| 32 | `funder_names` | `string` | Funder names (semicolon-joined). |
| 33 | `geo_count` | `number` | Number of geo-locations. |
| 34 | `geo_place` | `string` | First geo-location place name. |
| 35 | `geo_lat` | `number` | First geo-location latitude. |
| 36 | `geo_lon` | `number` | First geo-location longitude. |
| 37 | `date_count` | `number` | Number of dates. |
| 38 | `dates` | `string` | Date values (semicolon-joined). |
| 39 | `size_count` | `number` | Number of sizes. |
| 40 | `sizes` | `string` | Size values (semicolon-joined). |
| 41 | `format_count` | `number` | Number of formats. |
| 42 | `formats` | `string` | Format values (semicolon-joined). |
| 43 | `identifier_count` | `number` | Number of alternative identifiers. |
| 44 | `orcid_count` | `number` | Number of ORCID identifiers among creators. |
| 45 | `title_length` | `number` | Characters in the title. |
| 46 | `description_length` | `number` | Characters in the stored description. |
| 47 | `has_orcid` | `boolean` | true when at least one creator has an ORCID. |
| 48 | `has_description` | `boolean` | true when a description exists. |
| 49 | `has_funding` | `boolean` | true when funding references exist. |
| 50 | `has_geo` | `boolean` | true when a geo-location exists. |
| 51 | `has_related` | `boolean` | true when related identifiers exist. |
| 52 | `has_rights` | `boolean` | true when a rights statement exists. |
| 53 | `is_dataset` | `boolean` | true for resource_type_general Dataset. |
| 54 | `is_software` | `boolean` | true for Software. |
| 55 | `is_text` | `boolean` | true for Text/JournalArticle. |
| 56 | `is_image` | `boolean` | true for Image. |
| 57 | `is_preprint` | `boolean` | true when the type or title suggests a preprint. |
| 58 | `year_band` | `string` | Publication year band. |
| 59 | `decade` | `number` | Publication decade. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
