# arXiv Preprints

**Subtitle:** 18,226 recent arXiv papers with abstracts, authors, categories and dates

**Tags:** `research`, `papers`, `nlp`, `tabular`

**Dataset File:** `arxiv_papers.csv` (18,226 rows, 43 columns, 33.4 MB)

**Provenance & Source:** arXiv Open Access Metadata Ingestion API (OAI-PMH & export.arxiv.org)

**Expected Update Frequency:** `monthly`

---

## 📖 Description

### A cross-section of arXiv, the world's preprint server

arXiv hosts close to three million preprints in physics, mathematics, computer science, quantitative
biology, economics and electrical engineering. This snapshot samples the **most recent
18,226 papers** across 12 major categories and flattens each Atom record into **43 parameters**.

Each row includes:
- **Identity** — arXiv id with version, base id, title, abstract, abstract page and PDF URLs.
- **Authorship** — ordered author list, author count, affiliations and distinct affiliation count,
  single-author and large-collaboration flags, abstract length per author.
- **Classification** — primary category, all cross-listed categories, category count, top-level archive.
- **Publication state** — comment, journal reference, DOI, and flags for whether the paper has been
  published, mentions code, or states a page count.
- **Dates** — first submission and latest version timestamps, date/year/month/weekday, revision count,
  days to latest version, age at snapshot.
- **Title and abstract features** — word and character counts, colon-in-title, short-title flag.

**8,241 papers (45.2%)** come from computer-science categories. The abstracts are included
verbatim, which makes the file usable for topic modelling, citation-free summarisation and
research-metadata prediction.

## 🧾 Columns (43)

`arxiv_id`, `base_id`, `version`, `title`, `abstract`, `authors`, `author_count`, `affiliations`, `affiliation_count`, `primary_category`, `categories`, `category_count`, `comment`, `journal_ref`, `doi`, `published`, `updated`, `abs_url`, `pdf_url`, `primary_group`, `published_date`, `published_year`, `published_month`, `published_weekday`, `days_to_latest_version`, `revision_count`, `title_words`, `title_length`, `abstract_words`, `abstract_length`, `has_journal_ref`, `has_doi`, `has_comment`, `mentions_code`, `mentions_pages`, `is_cross_listed`, `is_short_title`, `abstract_per_author`, `is_single_author`, `large_collaboration`, `title_has_colon`, `age_days`, `is_recent_30d`

## 💡 Ideas for using this data

1. **Topic modelling** — LDA or BERTopic over abstracts; compare the topical map of cs, physics and math.
2. **Title conventions** — colon usage, length and 'A ... for ...' patterns by archive and year.
3. **Authorship** — author-count distribution by field; find the boundary between normal collaborations and mega-author papers.
4. **Preprint-to-journal** — which categories actually get a `journal_ref` or DOI, and how quickly?
5. **Version churn** — revision count and days-to-latest-version as a proxy for how much papers change after posting.
6. **Code availability** — text-mine comments for GitHub links; estimate reproducibility signals by category.
7. **Abstract readability** — sentence length and jargon density across fields.
8. **Classification** — train a classifier to predict the primary category from the title and abstract.
9. **Submission rhythm** — weekday and month patterns; when do researchers post?

## 📁 Files

| File | What it is |
|---|---|
| `arxiv_papers.csv` | 18,226 preprints x 43 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: categories, authors, text lengths, dates. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`arxiv`, `research`, `papers`, `science`, `machine-learning`, `physics`, `bibliometrics`, `nlp`, `tabular`, `academia`

## 🔗 Provenance

- **Source:** **arXiv export API** (`https://export.arxiv.org/api/query`), Atom XML,
  sorted by submission date descending, 1,000 records per request.
- **Sampling:** the most recent records in 12 categories (cs.LG, cs.CV, cs.CL, cs.AI, stat.ML,
  quant-ph, astro-ph.GA, cond-mat.mtrl-sci, math.OC, eess.SY, q-bio.NC, econ.EM), 1,000–2,200 each.
- **Processing:** Atom entries parsed with `xml.etree`, whitespace normalised in titles and abstracts,
  duplicate versions collapsed to the newest record per base id.
- **Derived columns:** date parts, revision count, text lengths, authorship features, publication and
  code flags, age at snapshot.
- **Snapshot date:** 21 November 2026.

## 🔄 Update frequency

**Continuous upstream; snapshot here.** arXiv receives thousands of submissions a day. Re-run `scripts/28_arxiv.py` for a new slice.

## ⚠️ Caveats

- This is a recent cross-section, not the full arXiv corpus; older and less active categories are under-represented.
- Only 12 categories were sampled, so category-level comparisons reflect the chosen slice.
- The API returns at most 1,000 records per request and throttles aggressively; requests were spaced 3 s apart.
- Abstracts are author-supplied and sometimes contain LaTeX macros rather than plain prose.
- `affiliations` are frequently missing because arXiv does not require them.
- `journal_ref` and `doi` are optional and manually entered, so absence does not mean unpublished.
- Duplicates across categories were collapsed by base id, keeping the most recent version.

## 📜 Licence

arXiv metadata is distributed under CC0 by Cornell University; abstracts remain the property of their authors. Attribution to arXiv is requested.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `arxiv_id` | `string` | arXiv identifier including version (e.g. 2511.01234v1). |
| 2 | `base_id` | `number` | arXiv identifier without the version suffix. |
| 3 | `version` | `number` | Version number of the posting. |
| 4 | `title` | `string` | Paper title, whitespace-normalised. |
| 5 | `abstract` | `string` | Full abstract text. |
| 6 | `authors` | `string` | Author names in order, semicolon-joined. |
| 7 | `author_count` | `number` | Number of authors. |
| 8 | `affiliations` | `string` | Author affiliations as supplied, semicolon-joined. |
| 9 | `affiliation_count` | `number` | Distinct affiliations listed. |
| 10 | `primary_category` | `string` | Primary arXiv category. |
| 11 | `categories` | `string` | All cross-listed categories. |
| 12 | `category_count` | `number` | Number of categories. |
| 13 | `comment` | `string` | Author comment field (page count, accepted-at, code links). |
| 14 | `journal_ref` | `string` | Journal reference, when the paper was published. |
| 15 | `doi` | `string` | DOI, when supplied. |
| 16 | `published` | `datetime` | First submission timestamp (UTC). |
| 17 | `updated` | `datetime` | Latest version timestamp (UTC). |
| 18 | `abs_url` | `string` | Abstract page URL. |
| 19 | `pdf_url` | `string` | PDF URL. |
| 20 | `primary_group` | `string` | Top-level archive of the primary category (cs, math, physics, ...). |
| 21 | `published_date` | `date` | Date part of the first submission. |
| 22 | `published_year` | `number` | Year of first submission. |
| 23 | `published_month` | `number` | Month of first submission (1-12). |
| 24 | `published_weekday` | `string` | Weekday of first submission. |
| 25 | `days_to_latest_version` | `number` | Days between first submission and latest version. |
| 26 | `revision_count` | `number` | Number of versions implied by the version suffix. |
| 27 | `title_words` | `number` | Word count of the title. |
| 28 | `title_length` | `number` | Characters in the title. |
| 29 | `abstract_words` | `number` | Word count of the abstract. |
| 30 | `abstract_length` | `number` | Characters in the abstract. |
| 31 | `has_journal_ref` | `boolean` | true when a journal reference is supplied. |
| 32 | `has_doi` | `boolean` | true when a DOI is supplied. |
| 33 | `has_comment` | `boolean` | true when the comment field is filled. |
| 34 | `mentions_code` | `boolean` | true when the comment mentions code, GitHub or a URL. |
| 35 | `mentions_pages` | `boolean` | true when the comment states a page count. |
| 36 | `is_cross_listed` | `boolean` | true when more than one category is assigned. |
| 37 | `is_short_title` | `boolean` | true when the title is under 60 characters. |
| 38 | `abstract_per_author` | `number` | Abstract words per author. |
| 39 | `is_single_author` | `boolean` | true for single-author papers. |
| 40 | `large_collaboration` | `boolean` | true when the paper has 20 or more authors. |
| 41 | `title_has_colon` | `boolean` | true when the title contains a colon. |
| 42 | `age_days` | `number` | Days between first submission and the snapshot date. |
| 43 | `is_recent_30d` | `boolean` | true when submitted within 30 days of the snapshot. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
