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
pretty_name: "U.S. Federal Contract Awards - FY2025-FY2026"
tags:
- tabular
- economics
---

# U.S. Federal Contract Awards — FY2025–FY2026

**Subtitle:** 29,998 contract awards with amounts, agencies, recipients, NAICS/PSC codes and durations.

---

## 📖 Description

### 29,998 U.S. federal contract awards (FY2025–FY2026)

USAspending publishes every federal award. This dataset takes the **29,998 largest contract awards**
from October 2024 to September 2026, with **31 parameters** each.

- **Award** — PIID, amount, type, description and period of performance.
- **Recipient** — name and USAspending recipient id.
- **Agency** — awarding agency, sub-agency and slug, with defense/health flags.
- **Classification** — NAICS code and sector, PSC code, place of performance.
- **Derived** — duration in days, start/end year and month, amount bands, multi-year and large-award
  flags, amount per day, description length and keyword flags.

The sample covers **$4,808.2 billion** in obligations across **47 agencies** and
**6,572 recipients** — enough for procurement, industrial-policy and contractor-concentration
research.

## 🧾 Columns (31)

`award_id`, `recipient_name`, `recipient_id`, `award_amount`, `awarding_agency`, `awarding_sub_agency`, `agency_slug`, `award_type`, `start_date`, `end_date`, `duration_days`, `naics_code`, `naics_sector`, `psc_code`, `place_state`, `place_country`, `description`, `description_length`, `amount_band`, `is_multiyear`, `is_large_award`, `start_year`, `start_month`, `end_year`, `is_positive_amount`, `amount_per_day`, `description_has_software`, `description_has_services`, `description_has_construction`, `is_defense`, `is_health`

## 💡 Ideas for using this data

1. **Contractor concentration** — top recipients and their agency mix.
2. **Agency spending** — obligations by agency and NAICS sector.
3. **Geographic distribution** — awards by place-of-performance state.
4. **Contract size** — amount distributions and multi-year awards.
5. **Industrial policy** — defense vs civilian spending mix.
6. **Text mining** — description keywords and service categories.
7. **Time patterns** — fiscal year-end spending spikes.
8. **Rate analysis** — amount per day as an intensity measure.
9. **Network** — agency-recipient bipartite graph.

## 📁 Files

| File | What it is |
|---|---|
| `federal_awards.csv` | 29,998 awards x 31 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`government-spending`, `procurement`, `usaspending`, `contracts`, `public-finance`, `economics`

## 🔗 Provenance

- **Source:** **USAspending.gov** award search API
  (`/api/v2/search/spending_by_award/`), contract award types A–D.
- **Sampling:** the 29,998 largest awards by amount for FY2025–FY2026 (1 Oct 2024 – 30 Sep 2026),
  collected page by page in descending amount order.
- **Processing:** fields expanded, dates parsed, duration and keyword features derived.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Daily.** USAspending ingests new awards continuously.

## ⚠️ Caveats

- This is the top of the amount distribution, not a random or complete sample of awards.
- Award amounts are obligations, not outlays, and can be modified later.
- Award descriptions are free text and truncated at 500 characters.
- Place of performance is often blank for contracts.
- Recipient identities are as reported and are not deduplicated across subsidiaries.
- Only contract award types A–D are included; grants and IDVs are excluded.

## 📜 Licence

USAspending.gov data is U.S. Government public domain.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
