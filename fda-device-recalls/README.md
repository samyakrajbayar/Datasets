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
pretty_name: "FDA Medical Device Recalls"
tags:
- tabular
- health
- medicine
---

# FDA Medical Device Recalls

**Subtitle:** 25,000 device recalls with classifications, firms, failure modes, dates and 510(k) links.

---

## 📖 Description

### 25,000 FDA medical-device recalls

The openFDA device enforcement endpoint publishes recalls of medical devices, from infusion pumps to
implants and diagnostic software. This dataset contains **25,000 recalls** and **51 parameters**.

- **Recall** — number, event id, classification, status, voluntary/mandated and notification method.
- **Firm** — name, address, city, state, country, postal code.
- **Product** — description, quantity, code information and distribution pattern.
- **Dates and lags** — initiation, classification, report and termination dates with lag and duration
  in days.
- **Derived** — class ranks and flags, status flags, openFDA/510(k) linkage, text lengths and failure
  keywords (software, battery, sterility, labelling, component, packaging, material).

**2,263 recalls are Class I**, **1,303 involve software or firmware** and **446
involve batteries** — a concrete view of device-safety failure modes and regulatory response times.

## 🧾 Columns (51)

`recall_number`, `event_id`, `recalling_firm`, `city`, `state`, `country`, `postal_code`, `address_1`, `address_2`, `product_type`, `classification`, `class_rank`, `status`, `voluntary_mandated`, `initial_firm_notification`, `distribution_pattern`, `product_description`, `product_quantity`, `reason_for_recall`, `code_info`, `more_code_info`, `recall_initiation_date`, `center_classification_date`, `report_date`, `termination_date`, `initiation_year`, `initiation_month`, `classification_lag_days`, `report_lag_days`, `recall_duration_days`, `is_class_i`, `is_class_ii`, `is_class_iii`, `is_ongoing`, `is_completed`, `is_terminated`, `is_voluntary`, `has_termination`, `has_openfda`, `openfda_key_count`, `k_number_count`, `reason_length`, `description_length`, `mentions_software`, `mentions_battery`, `mentions_sterility`, `mentions_labeling`, `mentions_component`, `mentions_packaging`, `mentions_material`, `is_device`

## 💡 Ideas for using this data

1. **Failure modes** — software vs hardware vs labelling recalls.
2. **Class I drivers** — root causes of the most serious recalls.
3. **Firm concentration** — manufacturers with repeated recalls.
4. **Response time** — classification and termination lags.
5. **Device categories** — text clustering of product descriptions.
6. **Trends** — recall volume by year and month.
7. **510(k) linkage** — recalls by clearance pathway.
8. **Geographic spread** — firm locations and distribution reach.

## 📁 Files

| File | What it is |
|---|---|
| `device_recalls.csv` | 25,000 recalls x 51 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`fda`, `medical-devices`, `recalls`, `openfda`, `patient-safety`, `healthcare`

## 🔗 Provenance

- **Source:** **openFDA** device enforcement API (`/device/enforcement.json`), 1,000
  records per request.
- **Sampling:** the first 25,000 records returned (API pagination cap), deduplicated by recall number.
- **Processing:** openFDA identifiers summarised; date arithmetic, flags and keyword features derived;
  long text truncated.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Weekly.** openFDA publishes a new enforcement report each week.

## ⚠️ Caveats

- Pagination is capped, so the file is a large sample rather than the full history.
- Classification and status can be revised after publication.
- Keyword flags are simple substring matches on free-text reasons.
- 510(k) links are only present when openFDA supplies them.
- Recall quantities are free text and not normalised to units.

## 📜 Licence

U.S. Government work (FDA openFDA), public domain.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
