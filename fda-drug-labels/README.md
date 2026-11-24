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
pretty_name: "FDA Drug Labels - SPL Section Corpus"
tags:
- tabular
- health
- medicine
---

# FDA Drug Labels — SPL Section Corpus

**Subtitle:** 25,000 drug labels with product identity, pharmacologic classes and 22 section-coverage measures.

---

## 📖 Description

### 25,000 FDA drug labels with full section coverage

The openFDA drug label endpoint exposes the Structured Product Labeling (SPL) documents that accompany
every FDA-regulated drug. This dataset contains **25,000 labels** and **78 parameters**.

- **Product identity** — set id, label id, version, effective date, brand, generic, manufacturer,
  NDCs, UNII, RxCUI and pharmacologic classes.
- **Classification** — product type, routes and substance names with counts.
- **Label content** — presence and length of 22 sections: indications, warnings, dosage, contraindications,
  adverse reactions, interactions, use in pregnancy, storage, description and more.
- **Derived** — section coverage, OTC/prescription/biological/vaccine and generic flags, label age,
  total text length and route bands.

**4,993 labels are over-the-counter** and **3,593 are prescription** products. The section
lengths and coverage make this a strong corpus for pharmacovigilance NLP and label-quality research.

## 🧾 Columns (78)

`set_id`, `label_id`, `version`, `effective_time`, `effective_year`, `effective_month`, `brand_name`, `generic_name`, `manufacturer_name`, `product_ndc`, `package_ndc`, `product_type`, `route`, `route_count`, `substance_name`, `substance_count`, `unii`, `rxcui`, `pharm_class_epc`, `pharm_class_moa`, `brand_count`, `has_openfda`, `active_ingredient_length`, `has_active_ingredient`, `inactive_ingredient_length`, `has_inactive_ingredient`, `purpose_length`, `has_purpose`, `indications_and_usage_length`, `has_indications_and_usage`, `warnings_length`, `has_warnings`, `dosage_and_administration_length`, `has_dosage_and_administration`, `contraindications_length`, `has_contraindications`, `adverse_reactions_length`, `has_adverse_reactions`, `drug_interactions_length`, `has_drug_interactions`, `pregnancy_or_breast_feeding_length`, `has_pregnancy_or_breast_feeding`, `stop_use_length`, `has_stop_use`, `do_not_use_length`, `has_do_not_use`, `storage_and_handling_length`, `has_storage_and_handling`, `keep_out_of_reach_of_children_length`, `has_keep_out_of_reach_of_children`, `questions_length`, `has_questions`, `package_label_principal_display_panel_length`, `has_package_label_principal_display_panel`, `spl_product_data_elements_length`, `has_spl_product_data_elements`, `geriatric_use_length`, `has_geriatric_use`, `pediatric_use_length`, `has_pediatric_use`, `overdosage_length`, `has_overdosage`, `description_length`, `has_description`, `clinical_pharmacology_length`, `has_clinical_pharmacology`, `section_coverage`, `section_coverage_ratio`, `is_otc`, `is_prescription`, `is_biological`, `is_vaccine`, `is_generic`, `has_dosage`, `label_age_years`, `is_recent_label`, `total_text_length`, `route_band`

## 💡 Ideas for using this data

1. **Label completeness** — which product classes have thin labels.
2. **Warning text** — NLP of boxed warnings and contraindications.
3. **OTC vs Rx** — language and section differences.
4. **Pharmacologic classes** — MoA/EPC distribution.
5. **Label churn** — version counts and effective-date recency.
6. **Generic vs brand** — labelling differences.
7. **Named entity recognition** — drugs, conditions and dosages.
8. **Search engine** — build a label retrieval demo.

## 📁 Files

| File | What it is |
|---|---|
| `drug_labels.csv` | 25,000 labels x 78 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`fda`, `drug-labels`, `pharmacology`, `openfda`, `nlp`, `healthcare`

## 🔗 Provenance

- **Source:** **openFDA** drug label API (`/drug/label.json`), 1,000 records per request.
- **Sampling:** the first 25,000 labels returned by the API (API skip limit), deduplicated by SPL set id.
- **Processing:** openFDA nested arrays flattened to names and counts; 22 label sections measured for
  presence and length; classification flags derived.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Continuous upstream; snapshot here.** openFDA ingests new labels daily.

## ⚠️ Caveats

- The API caps pagination, so this is the first 25,000 labels, not the full set.
- Label text is measured, not stored, to keep the file small.
- Section names follow SPL conventions and are not present for every product.
- Labels are updated continuously; effective dates span decades.
- Only FDA-regulated products with SPL labels are included.

## 📜 Licence

U.S. Government work (FDA openFDA), public domain.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
