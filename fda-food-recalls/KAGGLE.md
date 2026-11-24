# FDA Food & Supplement Recalls

**Subtitle:** 25,000 food recalls with classifications, firms, distribution, dates and hazard keywords.

---

## 📖 Description

### 25,000 FDA food and supplement recalls

openFDA's enforcement endpoint publishes every food, beverage and dietary-supplement recall that
appears in FDA's weekly Enforcement Report. This dataset contains **25,000 recalls** and
**50 parameters**.

- **Recall** — recall number, event id, classification, status, voluntary/mandated and notification
  method.
- **Firm** — name, address, city, state, country and postal code.
- **Product** — type, description, quantity, code/lot information and distribution pattern.
- **Dates and lags** — initiation, classification, report and termination dates plus classification,
  reporting and total duration in days.
- **Derived** — class ranks and flags, ongoing/completed/terminated flags, openFDA availability,
  text lengths and reason keywords (undeclared allergen, Listeria, Salmonella, foreign material,
  labelling).

**10,983 recalls are Class I** (serious harm), **5,407 cite undeclared allergens** and
**6,276 mention Listeria** — a direct measure of food-safety risk in the U.S. supply chain.

## 🧾 Columns (50)

`recall_number`, `event_id`, `recalling_firm`, `city`, `state`, `country`, `postal_code`, `address_1`, `address_2`, `product_type`, `classification`, `class_rank`, `status`, `voluntary_mandated`, `initial_firm_notification`, `distribution_pattern`, `product_description`, `product_quantity`, `reason_for_recall`, `code_info`, `more_code_info`, `recall_initiation_date`, `center_classification_date`, `report_date`, `termination_date`, `initiation_year`, `initiation_month`, `classification_lag_days`, `report_lag_days`, `recall_duration_days`, `is_class_i`, `is_class_ii`, `is_class_iii`, `is_ongoing`, `is_completed`, `is_terminated`, `is_voluntary`, `has_termination`, `has_openfda`, `openfda_key_count`, `reason_length`, `description_length`, `distribution_length`, `mentions_undeclared_allergen`, `mentions_listeria`, `mentions_salmonella`, `mentions_foreign_material`, `mentions_labeling`, `is_food`, `is_drug`

## 💡 Ideas for using this data

1. **Recurring firms** — firms with repeated recalls.
2. **Hazard mix** — allergen vs pathogen vs foreign-material reasons.
3. **Recall speed** — classification and termination lags.
4. **Class I drivers** — what distinguishes the most serious recalls.
5. **Geography** — recalls by state and firm location.
6. **Product categories** — text clustering of product descriptions.
7. **Trend** — recalls per month and year.
8. **Supply chain** — distribution patterns and reach.

## 📁 Files

| File | What it is |
|---|---|
| `food_recalls.csv` | 25,000 recalls x 50 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`fda`, `food-safety`, `recalls`, `openfda`, `supply-chain`, `public-health`

## 🔗 Provenance

- **Source:** **openFDA** food enforcement API (`/food/enforcement.json`), 1,000 records
  per request.
- **Sampling:** the first 25,000 records returned by the API (pagination cap), deduplicated by recall
  number.
- **Processing:** nested openFDA data summarised; date arithmetic, class flags and reason keywords
  derived; long text truncated.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Weekly.** openFDA publishes a new enforcement report each week.

## ⚠️ Caveats

- The API pagination cap means this is not the complete recall history.
- Status and dates are as published and can be updated later.
- Reason text is free-form; keyword flags are simple substring matches.
- Distribution patterns are descriptive text, not structured geography.
- Recalls of imported products may list a foreign firm address.

## 📜 Licence

U.S. Government work (FDA openFDA), public domain.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
