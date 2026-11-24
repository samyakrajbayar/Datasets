# FDA Drug Recalls - Enforcement Reports

**Subtitle:** 18,166 drug recalls with classification, firm, reason & distribution

**Tags:** `tabular`, `health`, `medicine`

**Dataset File:** `fda_drug_recalls.csv` (18,166 rows, 55 columns, 12.5 MB)

**Provenance & Source:** openFDA Drug Enforcement API (open.fda.gov)

**Expected Update Frequency:** `quarterly`

---

## 📖 Description

### 18,000 FDA drug recalls, enriched

openFDA publishes the FDA's enforcement reports — every drug recall with its classification, firm,
distribution and reason. This dataset contains **18,166 recall records** with **55 parameters**.

- **Recall identity** — recall number, event id, classification, status, product type, voluntary vs
  mandated, initial notification method.
- **Firm** — name, address, city, state, country, postal code.
- **Product and reason** — product description, reason for recall, quantity, distribution pattern.
- **Dates** — initiation, center classification, report and termination dates, plus processing lags and
  total recall duration.
- **openFDA product link** — brand/generic name, manufacturer, NDC, route, substance, application
  number and SPL id where FDA matched the recall to a product record.
- **Derived** — class and status flags, nationwide/international flags, reason category, text lengths
  and parsed quantity.

**1,753 recalls are Class I** (reasonable probability of serious harm) and **14,842 have been
terminated**. Recalls come from **1,686 distinct firms**, making this a firm-level operations and
supply-chain dataset as well as a regulatory one.

## 🧾 Columns (55)

`recall_number`, `event_id`, `classification`, `status`, `product_type`, `recalling_firm`, `address_1`, `address_2`, `city`, `state`, `country`, `postal_code`, `voluntary_mandated`, `initial_firm_notification`, `distribution_pattern`, `product_description`, `reason_for_recall`, `product_quantity`, `recall_initiation_date`, `center_classification_date`, `report_date`, `termination_date`, `openfda_brand_name`, `openfda_generic_name`, `openfda_manufacturer_name`, `openfda_product_ndc`, `openfda_route`, `openfda_substance_name`, `openfda_application_number`, `openfda_spl_id`, `openfda_count`, `year`, `quarter`, `month`, `days_initiation_to_classification`, `days_classification_to_report`, `days_initiation_to_termination`, `recall_duration_days`, `is_class_i`, `is_class_ii`, `is_class_iii`, `is_ongoing`, `is_completed`, `is_terminated`, `is_voluntary`, `is_mandated`, `is_nationwide`, `is_international`, `reason_category`, `distribution_word_count`, `product_description_len`, `reason_len`, `quantity_numeric`, `has_openfda`, `firm_state`

## 💡 Ideas for using this data

1. **Recall severity** — what distinguishes Class I from Class III recalls: product, reason, firm?
2. **Reason taxonomy** — contamination vs potency vs labelling over time.
3. **Firm concentration** — which firms recall most often, and does size predict severity?
4. **Processing speed** — days from initiation to classification and to termination.
5. **Geographic pattern** — recalls by firm state and distribution reach.
6. **Product classes** — which dosage forms and routes are recalled most?
7. **NLP on reasons** — topic-model the reason text and compare with the derived categories.
8. **Time series** — monthly recall counts and the effect of major regulatory events.
9. **OpenFDA linkage** — join to drug labels or NDC directories for product-level enrichment.

## 📁 Files

| File | What it is |
|---|---|
| `fda_drug_recalls.csv` | 18,166 recall records x 55 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`fda`, `recalls`, `pharmaceuticals`, `openfda`, `regulation`, `supply-chain`, `health`

## 🔗 Provenance

- **Source:** **openFDA drug enforcement** API,
  `https://api.fda.gov/drug/enforcement.json?limit=1000&skip=N`.
- **Scope:** all enforcement reports available at snapshot time (the API caps `skip` at 25,000).
- **Processing:** nested `openfda` object flattened, dates parsed from `YYYYMMDD`, processing lags and
  duration computed, reason categories derived by keyword matching.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Weekly.** openFDA refreshes the enforcement endpoint as new reports are published.

## ⚠️ Caveats

- openFDA data is unvalidated and explicitly not for clinical decision-making.
- Dates are as published; ongoing recalls have no termination date and use a fixed reference date.
- `recall_duration_days` for ongoing recalls is truncated at the snapshot date.
- Reason categories are keyword heuristics, not an official taxonomy.
- Distribution and quantity fields are free text and inconsistently formatted.
- The API caps pagination at 25,000 records; this extract stops there.
- Recall records can be updated or removed upstream between snapshots.

## 📜 Licence

U.S. Government work (FDA/openFDA) — public domain.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `recall_number` | `string` | FDA recall number. |
| 2 | `event_id` | `number` | FDA enforcement event identifier. |
| 3 | `classification` | `string` | Class I (serious harm), II (temporary harm) or III (unlikely harm). |
| 4 | `status` | `string` | Ongoing, completed or terminated. |
| 5 | `product_type` | `string` | Product type reported by FDA. |
| 6 | `recalling_firm` | `string` | Firm that initiated the recall. |
| 7 | `address_1` | `string` | Firm street address. |
| 8 | `address_2` | `string` | Firm address line 2. |
| 9 | `city` | `string` | Firm city. |
| 10 | `state` | `string` | Firm state. |
| 11 | `country` | `string` | Firm country. |
| 12 | `postal_code` | `string` | Firm postal code. |
| 13 | `voluntary_mandated` | `string` | Whether the recall was voluntary or mandated. |
| 14 | `initial_firm_notification` | `string` | How the firm notified customers. |
| 15 | `distribution_pattern` | `string` | Free-text description of where the product went. |
| 16 | `product_description` | `string` | Product description from the enforcement report. |
| 17 | `reason_for_recall` | `string` | Stated reason for the recall. |
| 18 | `product_quantity` | `string` | Quantity recalled, as reported. |
| 19 | `recall_initiation_date` | `date` | Date the recall began (ISO). |
| 20 | `center_classification_date` | `date` | Date FDA assigned the classification (ISO). |
| 21 | `report_date` | `date` | Date the enforcement report was published (ISO). |
| 22 | `termination_date` | `date` | Date the recall was terminated (ISO). |
| 23 | `openfda_brand_name` | `string` | Brand name from the openFDA product record. |
| 24 | `openfda_generic_name` | `string` | Generic name from the openFDA product record. |
| 25 | `openfda_manufacturer_name` | `string` | Manufacturer from the openFDA product record. |
| 26 | `openfda_product_ndc` | `string` | NDC code from the openFDA product record. |
| 27 | `openfda_route` | `string` | Route of administration. |
| 28 | `openfda_substance_name` | `string` | Active substance name(s). |
| 29 | `openfda_application_number` | `string` | NDA/ANDA application number. |
| 30 | `openfda_spl_id` | `string` | Structured Product Labeling identifier. |
| 31 | `openfda_count` | `number` | Number of openFDA product records attached. |
| 32 | `year` | `number` | Year of the recall initiation date. |
| 33 | `quarter` | `number` | Quarter of the recall initiation date. |
| 34 | `month` | `number` | Month of the recall initiation date. |
| 35 | `days_initiation_to_classification` | `number` | Classification date minus initiation date. |
| 36 | `days_classification_to_report` | `number` | Report date minus classification date. |
| 37 | `days_initiation_to_termination` | `number` | Termination date minus initiation date. |
| 38 | `recall_duration_days` | `number` | Initiation to termination, or initiation to 2026-11-22 if ongoing. |
| 39 | `is_class_i` | `boolean` | true for Class I recalls. |
| 40 | `is_class_ii` | `boolean` | true for Class II recalls. |
| 41 | `is_class_iii` | `boolean` | true for Class III recalls. |
| 42 | `is_ongoing` | `boolean` | true when status is Ongoing. |
| 43 | `is_completed` | `boolean` | true when status is Completed. |
| 44 | `is_terminated` | `boolean` | true when status is Terminated. |
| 45 | `is_voluntary` | `boolean` | true when the recall was voluntary. |
| 46 | `is_mandated` | `boolean` | true when the recall was mandated. |
| 47 | `is_nationwide` | `boolean` | true when the distribution pattern says nationwide. |
| 48 | `is_international` | `boolean` | true when the distribution pattern mentions international/foreign. |
| 49 | `reason_category` | `string` | Derived reason category from keyword matching. |
| 50 | `distribution_word_count` | `number` | Words in the distribution pattern. |
| 51 | `product_description_len` | `number` | Characters in the product description. |
| 52 | `reason_len` | `number` | Characters in the reason text. |
| 53 | `quantity_numeric` | `number` | First number parsed from product_quantity. |
| 54 | `has_openfda` | `boolean` | true when an openFDA product record is attached. |
| 55 | `firm_state` | `string` | Recalling firm state (same as `state`, kept for clarity). |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
