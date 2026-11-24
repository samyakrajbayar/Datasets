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
pretty_name: "U.S. Hospital Quality - CMS Star Ratings"
tags:
- tabular
- health
- medicine
---

# U.S. Hospital Quality — CMS Star Ratings

**Subtitle:** 5,435 hospitals with overall ratings, mortality measure profiles, ownership and emergency services.

---

## 📖 Description

### 5,435 U.S. hospitals with CMS quality ratings

CMS Hospital Compare publishes the official star ratings and measure counts for every hospital that
reports to Medicare. This dataset contains **5,435 facilities** across **56 states** with
**53 parameters**.

- **Facility** — CCN, name, address, county, state, ZIP and phone.
- **Classification** — hospital type, ownership and emergency-services status.
- **Quality** — overall star rating, mortality measure counts (better, no different, worse) and their
  footnotes.
- **Derived** — ownership groups and flags, acute-care/emergency/birthing flags, rating bands,
  measure coverage, better/worse ratios, net measure score, high-rated and unrated flags, and each
  hospital's share of its state's facilities.

**3,166 hospitals carry an overall rating** and **4,501 provide emergency services** —
the base table for hospital-quality, access and ownership research.

## 🧾 Columns (53)

`facility_id`, `facility_name`, `address`, `citytown`, `state`, `zip_code`, `countyparish`, `telephone_number`, `hospital_type`, `hospital_ownership`, `emergency_services`, `meets_criteria_for_birthing_friendly_designation`, `hospital_overall_rating`, `hospital_overall_rating_footnote`, `mort_group_measure_count`, `count_of_facility_mort_measures`, `count_of_mort_measures_better`, `count_of_mort_measures_no_different`, `count_of_mort_measures_worse`, `mort_group_footnote`, `safety_group_measure_count`, `count_of_facility_safety_measures`, `count_of_safety_measures_better`, `count_of_safety_measures_no_different`, `count_of_safety_measures_worse`, `safety_group_footnote`, `readm_group_measure_count`, `count_of_facility_readm_measures`, `count_of_readm_measures_better`, `count_of_readm_measures_no_different`, `count_of_readm_measures_worse`, `readm_group_footnote`, `pt_exp_group_measure_count`, `count_of_facility_pt_exp_measures`, `pt_exp_group_footnote`, `te_group_measure_count`, `count_of_facility_te_measures`, `te_group_footnote`, `ownership_group`, `is_for_profit`, `is_nonprofit`, `is_government`, `is_acute_care`, `has_emergency`, `has_birthing`, `rating_band`, `measure_coverage`, `better_ratio`, `worse_ratio`, `net_measure_score`, `is_high_rated`, `is_unrated`, `state_hospital_share`

## 💡 Ideas for using this data

1. **Ownership and quality** — star ratings by ownership group.
2. **Geographic variation** — state-level rating distributions.
3. **Emergency access** — hospitals without emergency departments.
4. **Measure mix** — better vs worse measure profiles.
5. **Rural access** — facility density by county (join Census data).
6. **Type comparison** — acute vs critical-access vs specialty hospitals.
7. **Rating prediction** — structural features vs overall rating.
8. **Map** — hospital locations and ratings.

## 📁 Files

| File | What it is |
|---|---|
| `hospitals.csv` | 5,435 hospitals x 53 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`healthcare`, `hospitals`, `cms`, `quality`, `united-states`, `public-health`

## 🔗 Provenance

- **Source:** **CMS Provider Data Catalog**, dataset `xubh-q36u`
  ("Hospital General Information"), queried through the datastore API.
- **Processing:** all hospitals paged 1,000 at a time; ownership, rating, measure and geography
  features derived.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Quarterly.** CMS refreshes Hospital Compare data quarterly.

## ⚠️ Caveats

- Star ratings exist only for hospitals that report enough measures.
- Mortality counts refer to the mortality measure group only, not all quality measures.
- Hospital type strings vary and are grouped by keyword.
- Facilities close, merge and change ownership; this is a quarterly snapshot.
- Ratings are not risk-adjusted for case mix in this table.

## 📜 Licence

U.S. Government work (CMS), public domain.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
