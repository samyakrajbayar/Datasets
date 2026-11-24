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
pretty_name: "Chicago Food Inspections 2023-2026"
tags:
- tabular
- health
---

# Chicago Food Inspections 2023–2026

**Subtitle:** 71,290 food-establishment inspections with outcomes, violation text, risk classes and locations.

---

## 📖 Description

### 71,290 Chicago food-establishment inspections since 2023

The City of Chicago publishes every food inspection, the outcome and the violation text. This
dataset covers inspections since January 2023 with **71,290 records** and **39 parameters**.

- **Establishment** — DBA and AKA names, licence, facility type and derived facility group, risk
  class and address.
- **Inspection** — id, date, type, result and full violation text (truncated).
- **Violations** — numbered violation count, text length and violation band.
- **Derived** — pass/fail/conditional flags, complaint/canvass/re-inspection flags, year, month,
  quarter, weekday, coordinates and coordinate block, name length.

**46,512 inspections passed**, **13,344 failed** and **11,696 were complaint-driven**.
The violation text makes this a ready-made NLP corpus for food-safety risk modelling.

## 🧾 Columns (39)

`inspection_id`, `dba_name`, `aka_name`, `license_number`, `facility_type`, `facility_group`, `risk`, `risk_rank`, `address`, `city`, `state`, `zip`, `latitude`, `longitude`, `inspection_date`, `inspection_type`, `results`, `violations`, `violation_count`, `violation_text_length`, `inspection_year`, `inspection_month`, `inspection_quarter`, `inspection_weekday`, `is_pass`, `is_fail`, `is_conditional`, `is_out_of_business`, `is_no_entry`, `is_complaint`, `is_canvass`, `is_reinspection`, `is_license_inspection`, `has_location`, `has_violations`, `violation_band`, `name_length`, `is_chain_name`, `geo_block`

## 💡 Ideas for using this data

1. **Failure prediction** — which establishments and inspection types fail.
2. **Violation NLP** — topic modelling of violation text.
3. **Risk classes** — outcomes by risk level and facility type.
4. **Chains vs independents** — failure rates by name.
5. **Seasonality** — inspections and failures by month.
6. **Geography** — failure hotspots by ZIP and coordinate block.
7. **Complaint efficiency** — complaint inspections vs routine canvass.
8. **Repeat offenders** — licences with repeated failures.

## 📁 Files

| File | What it is |
|---|---|
| `chicago_food_inspections.csv` | 71,290 inspections x 39 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`food-safety`, `inspections`, `chicago`, `public-health`, `nlp`, `open-data`

## 🔗 Provenance

- **Source:** **City of Chicago Open Data Portal**, dataset `4ijn-s7e5`
  ("Food Inspections"), Socrata SoQL query.
- **Sampling:** all inspections dated after 1 January 2023, newest first.
- **Processing:** Socrata metadata columns dropped; violation items counted from the text; outcome,
  inspection-type, date and facility features derived.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Daily.** Chicago publishes new inspection records continuously.

## ⚠️ Caveats

- Results reflect city records at extraction time and can be amended later.
- Violation counts are parsed from numbered text items and can undercount.
- Coordinates come from address geocoding and some records lack them.
- Facility group is a keyword mapping of free-text facility types.
- Only inspections after 2023 are included.

## 📜 Licence

City of Chicago open data, public domain dedication.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
