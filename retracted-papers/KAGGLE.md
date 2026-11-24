# Retracted Research Papers — Retraction Watch

**Subtitle:** 74,000 retractions, corrections and expressions of concern with reasons, lags, journals and authors.

---

## 📖 Description

### 74,000 retracted or corrected research papers

The Retraction Watch database, distributed through Crossref, records every retraction, correction and
expression of concern in the scholarly literature. This dataset contains **74,000 records** with
**60 parameters**.

- **Paper** — record id, title, subject, article type, original DOI and PubMed id.
- **People and places** — authors, institutions, journal, publisher and country.
- **Retraction** — date, DOI, PubMed id, nature of the notice and the full reason text.
- **Derived** — years, months and quarters, publication-to-retraction lag in days and years, nature
  flags, 13 reason-keyword flags, paywall/DOI/URL flags, subject flags, text lengths and lag bands.

**6,548 records cite plagiarism** and **11,360 cite duplication**, while **44,991
retractions date from 2020 or later**. The file is the standard reference for research-integrity,
meta-science and bibliometrics work.

## 🧾 Columns (60)

`record_id`, `title`, `subject`, `institution`, `journal`, `publisher`, `country`, `country_count`, `author`, `author_count`, `urls`, `article_type`, `retraction_date`, `retraction_year`, `retraction_month`, `retraction_quarter`, `retraction_doi`, `retraction_pubmed_id`, `original_paper_date`, `original_year`, `original_month`, `original_doi`, `original_pubmed_id`, `lag_days`, `lag_years`, `retraction_nature`, `reason`, `reason_length`, `paywalled`, `notes`, `notes_length`, `is_retraction`, `is_correction`, `is_expression_of_concern`, `is_reinstatement`, `mentions_plagiarism`, `mentions_duplication`, `mentions_data_issues`, `mentions_fabrication`, `mentions_error`, `mentions_authorship`, `mentions_peer_review`, `mentions_ethics`, `mentions_consent`, `mentions_conflict`, `mentions_reproducibility`, `mentions_image`, `is_paywalled`, `has_notes`, `has_doi`, `has_urls`, `is_clinical_trial`, `is_cancer_paper`, `is_engineering`, `is_social_science`, `subject_length`, `title_length`, `is_recent`, `retraction_decade`, `lag_band`

## 💡 Ideas for using this data

1. **Reasons** — plagiarism vs duplication vs data problems over time.
2. **Lag** — how long retracted papers stay in the literature.
3. **Journals** — venues with the most retractions.
4. **Countries** — retraction rates by author country.
5. **Subjects** — which fields retract most.
6. **Text mining** — reason and notes narratives.
7. **Trend** — retractions per year and decade.
8. **Corrections vs retractions** — notice-type mix.

## 📁 Files

| File | What it is |
|---|---|
| `retractions.csv` | 74,000 records x 60 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`research-integrity`, `retractions`, `bibliometrics`, `science`, `meta-science`, `academia`

## 🔗 Provenance

- **Source:** **Retraction Watch Database**, distributed by Crossref
  (`retraction_watch.csv` from the crossref/retraction-watch-data repository).
- **Processing:** 20 source columns retained; dates parsed, lags, notice-type and reason-keyword
  flags derived; long text truncated.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Monthly.** Retraction Watch and Crossref publish updates regularly.

## ⚠️ Caveats

- Retraction Watch is a curated database; coverage before 2000 is incomplete.
- Reason text is free-form and keyword flags are simple substring matches.
- One record can cover several papers or a correction rather than a retraction.
- Author and institution fields are as supplied and are not normalised.
- Dates are notice dates, not the date a paper was formally withdrawn.

## 📜 Licence

Retraction Watch Database, distributed by Crossref under CC BY 4.0.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
