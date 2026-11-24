# Most-Cited Scholarly Works Since 2015

**Subtitle:** Crossref bibliometric snapshot of top-cited articles & open-access metadata

**Tags:** `academia`, `research`, `scientometrics`, `publishing`, `bibliometrics`, `citation-analysis`, `science`, `nlp`, `tabular`, `education`

**Dataset File:** `crossref_works.csv` (6,585 rows, 53 columns, 3.9 MB)

---

## 📖 Description

### The 6,000 most-cited journal articles published since 2015

A bibliometric snapshot pulled live from **Crossref**, the DOI registration agency that holds metadata for
over 150 million scholarly works. This file contains the **6,000 journal articles from 2015 onwards with the
highest Crossref cited-by counts**, resolved at snapshot time, with **53 parameters** per work.

Each row describes one paper:
- **Bibliographic identity** — DOI, title, subtitle, journal and abbreviated journal, publisher, volume,
  issue, pages, publication year/month/day and the full issued date.
- **Authorship** — author and editor counts, first and last author names, distinct affiliation count,
  first affiliation, single-author flag and a team-size band.
- **Impact** — Crossref citation count, citations per year, work age and a citation band.
- **Funding and openness** — number of funders, funder names, number of licences, licence URLs and an
  open-access flag.
- **Content** — a discipline label inferred from journal-title keywords, abstract presence and length,
  title length, full-text link count, references count and the DOI resolver URL.

Because the sample is defined by citation rank, it is a natural benchmark for **citation prediction,
team-size effects, open-access advantage and journal prestige** — and, equally, a clear example of
survivorship bias.

## 🧾 Columns (53)

`doi`, `title`, `subtitle`, `journal`, `journal_abbrev`, `publisher`, `type`, `published_year`, `published_month`, `published_day`, `published_date`, `created_date`, `n_authors`, `n_editors`, `first_author`, `first_author_given`, `last_author`, `n_affiliations`, `first_affiliation`, `n_funders`, `funder_names`, `citations`, `citations_per_year`, `year_since_publication`, `n_subjects`, `subjects`, `n_issn`, `issn`, `is_open_access`, `license_urls`, `volume`, `issue`, `pages`, `n_links`, `n_references`, `has_abstract`, `abstract_length`, `title_length`, `article_number`, `publisher_location`, `doi_prefix`, `group_title`, `deposited_date`, `indexed_date`, `print_year`, `online_year`, `url`, `decade`, `is_single_author`, `team_size_class`, `citation_class`, `field`, `field_basis`

## 💡 Ideas for using this data

1. **Open-access advantage** — compare citation rates for works with and without a registered licence, controlling for age and field.
2. **Team size vs impact** — boxplot citations by `team_size_class`; test whether large teams dominate the top of the distribution.
3. **Journal prestige** — rank journals by mean citations per article and by publication volume.
4. **Citation decay** — plot `citations_per_year` against `published_year` to see how the most-cited set ages.
5. **Field mix** — `field` frequency by year; which disciplines generate the most highly cited work?
6. **Abstract effect** — does `has_abstract` / `abstract_length` correlate with citations?
7. **Funding** — share of top-cited work with funder metadata, by publisher and by decade.
8. **Regression** — predict log citations from authors, affiliations, openness, field and age.
9. **Text mining** — titles are clean UTF-8; cluster them or build a keyword extractor.

## 📁 Files

| File | What it is |
|---|---|
| `crossref_works.csv` | 6,000 highly cited journal articles x 53 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: citation distributions, open access, team size. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block for the Kaggle web form. |

## 🏷️ Tags

`academia`, `research`, `scientometrics`, `publishing`, `bibliometrics`, `citation-analysis`, `science`, `nlp`, `tabular`, `education`

## 🔗 Provenance

- **Source:** Crossref REST API, `https://api.crossref.org/works`.
- **Query:** `filter=from-pub-date:2015-01-01,type:journal-article`, `sort=is-referenced-by-count`,
  `order=desc`, cursor deep-paging, 200 records per page.
- **Records:** the top-cited slice of the Crossref corpus from 2015 onward (see row count above), not a
  random sample.
- **Transformation:** nested JSON (authors, funders, licences, subjects) flattened to one row per work;
  16 derived columns computed from the raw fields.
- **Snapshot date:** 20 November 2026. Citation counts change daily upstream.

## 🔄 Update frequency

**Never (static snapshot).** Citation counts move daily upstream; re-run `scripts/12_crossref.py` to refresh.

## ⚠️ Caveats

- Crossref cited-by counts are **not** the same as Scopus or Web of Science counts and are typically lower.
- Only works whose publishers deposit reference metadata have citation counts, so coverage is uneven by field and publisher.
- Names are split into `first_author` / `last_author` only; full author lists are not included.
- The sample is citation-ranked, so it is heavily survivorship-biased and dominated by medicine and physics.
- Affiliations come from free-text publisher deposits and are inconsistent in spelling.
- `is_open_access` only reflects a registered licence, not whether the PDF is actually free to read.
- `field` is inferred from journal-title keywords, and about 29% of journals match no rule and are labelled `Other`; treat it as a coarse grouping, not a taxonomy.

## 📜 Licence

Crossref metadata is openly available under the Crossref Terms of Use; individual abstracts and titles remain © their publishers and authors. Attribution to Crossref and the original publishers is required.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `doi` | `string` | Digital Object Identifier — the unique, resolvable id of the work. |
| 2 | `title` | `string` | Work title as deposited at Crossref. |
| 3 | `subtitle` | `string` | Subtitle, when the deposit includes one. |
| 4 | `journal` | `string` | Container (journal) title. |
| 5 | `journal_abbrev` | `string` | Abbreviated journal title as registered by the publisher. |
| 6 | `publisher` | `string` | Publishing organisation that deposited the DOI. |
| 7 | `type` | `string` | Crossref work type; all rows here are `journal-article`. |
| 8 | `published_year` | `number` | Year of the issued (publication) date. |
| 9 | `published_month` | `number` | Month of the issued date. |
| 10 | `published_day` | `number` | Day of the issued date. |
| 11 | `published_date` | `string` | Full issued date as YYYY-M-D. |
| 12 | `created_date` | `datetime` | Timestamp when the DOI record was first created at Crossref. |
| 13 | `n_authors` | `number` | Number of authors in the deposited author list. |
| 14 | `n_editors` | `number` | Number of editors. |
| 15 | `first_author` | `string` | Family name of the first author. |
| 16 | `first_author_given` | `string` | Given name of the first author. |
| 17 | `last_author` | `string` | Family name of the last author (often the senior/PI author). |
| 18 | `n_affiliations` | `number` | Number of distinct institutional affiliations across all authors. |
| 19 | `first_affiliation` | `string` | Affiliation of the first author who reported one. |
| 20 | `n_funders` | `number` | Number of funding records attached to the work. |
| 21 | `funder_names` | `string` | Semicolon-separated funder names. |
| 22 | `citations` | `number` | Crossref cited-by count at snapshot time. |
| 23 | `citations_per_year` | `number` | Citations divided by years since publication. |
| 24 | `year_since_publication` | `number` | Age of the work in years at snapshot time. |
| 25 | `n_subjects` | `number` | Derived field. |
| 26 | `subjects` | `number` | Derived field. |
| 27 | `n_issn` | `number` | Number of ISSNs registered for the journal. |
| 28 | `issn` | `string` | First ISSN of the journal. |
| 29 | `is_open_access` | `boolean` | true when at least one licence is registered for the work. |
| 30 | `license_urls` | `string` | Semicolon-separated licence URLs. |
| 31 | `volume` | `string` | Journal volume. |
| 32 | `issue` | `string` | Journal issue. |
| 33 | `pages` | `string` | Page range or article number. |
| 34 | `n_links` | `number` | Number of full-text/resource links in the record. |
| 35 | `n_references` | `number` | Number of references the publisher deposited for the work. |
| 36 | `has_abstract` | `boolean` | true when the deposit carries an abstract. |
| 37 | `abstract_length` | `number` | Length of the abstract text in characters. |
| 38 | `title_length` | `number` | Title length in characters. |
| 39 | `article_number` | `string` | Article number for journals that number articles instead of pages. |
| 40 | `publisher_location` | `number` | Registered location of the publisher. |
| 41 | `doi_prefix` | `number` | DOI prefix, which identifies the registration agency member (usually the publisher). |
| 42 | `group_title` | `number` | Group or collection title, where deposited. |
| 43 | `deposited_date` | `datetime` | Timestamp of the last metadata deposit. |
| 44 | `indexed_date` | `datetime` | Timestamp when Crossref last indexed the record. |
| 45 | `print_year` | `number` | Year of the print publication date, when distinct. |
| 46 | `online_year` | `number` | Year of the online publication date, when distinct. |
| 47 | `url` | `string` | Canonical DOI resolver URL. |
| 48 | `decade` | `string` | Publication decade. |
| 49 | `is_single_author` | `boolean` | true when the work has exactly one author. |
| 50 | `team_size_class` | `string` | Author-count band: Solo, Small (2-5), Medium (6-20), Large (>20). |
| 51 | `citation_class` | `string` | Citation band: Mega (10k+), High (1k-10k), Notable (100-1k), Low (<100). |
| 52 | `field` | `string` | Discipline inferred from journal-title keywords (heuristic, see `field_basis`). |
| 53 | `field_basis` | `string` | How the field was assigned; always `journal title keywords` here. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
