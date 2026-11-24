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
pretty_name: "World University Directory: 10,272 Institutions"
tags:
- tabular
- education
---

# World University Directory — 10,272 Institutions Across 200+ Countries

**Subtitle:** A cleaned, feature-rich registry of universities worldwide with domains, websites, regions and per-country counts.

---

## 📖 Description

Every university outreach, recruitment or research-collaboration project starts with the same boring problem: getting a usable list of institutions. This dataset is that list, already cleaned and enriched.

It contains **10,272 higher-education institutions** from the openly licensed [Hipolabs Universities registry](https://github.com/Hipo/university-domains-list), the same source that powers countless "list of universities by country" tools. On top of the raw records I've added derived features that make the file immediately analysable:

- **Geography** — continent-level `region` and `subregion` joined from ISO country codes, so you can group by continent without a second lookup table.
- **Web footprint** — number of domains and official web pages per institution, plus the primary domain and website, which makes it easy to check `.edu`/`.ac.uk`/`.edu.au` patterns or measure how many institutions share hosting providers.
- **Name features** — name length, word count, and a `is_duplicate_name` flag for institutions that appear in several countries (e.g. campuses of the same network).
- **Country density** — `country_university_count` gives an instant measure of how crowded a country's higher-education market is.

Coverage is strongest for the United States, India, Indonesia, the Philippines and Europe; small states and some African countries are sparser. That imbalance is itself an interesting analytical topic.

## 🧾 Columns (17)

| Column | Type | Notes |
|---|---|---|
| `name` | string | Institution name |
| `country` | string | Country name |
| `alpha_two_code` | string | ISO 3166-1 alpha-2 |
| `state_province` | string | Mostly filled for US/Canada |
| `primary_domain`, `n_domains`, `domains` | string/int/list | Email & institutional domains |
| `primary_website`, `n_web_pages`, `web_pages` | string/int/list | Official pages |
| `region`, `subregion` | string | Derived from ISO code |
| `name_length`, `name_word_count` | int | Text features |
| `has_state` | bool | State/province present |
| `country_university_count` | int | Institutions in same country |
| `is_duplicate_name` | bool | Shared normalised name |

A full machine-readable dictionary ships as `data_dictionary.csv`.

## 💡 Ideas for using this data

1. **Country/region ranking** of institution counts and normalise by population (join with a country dataset).
2. **Domain-suffix analysis** — how higher-education naming conventions differ across countries.
3. **Duplicate/campus network detection** — find university systems with many same-named campuses.
4. **NLP on institution names** — topic modelling of "Institute of Technology" vs "University of…" patterns.
5. **Contact-list generation** for legitimate academic outreach (respect anti-spam rules).

## 🔗 Provenance & licence

- Source: Hipolabs `universities` list (public domain / CC0-style open data), fetched via `universities.hipolabs.com`.
- Region/subregion enrichment: ISO country metadata (mledoze/countries, ODbL).
- Snapshot: November 2026. 10,272 rows × 17 columns.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
