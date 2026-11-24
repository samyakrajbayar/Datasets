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
pretty_name: "Hugging Face Model Hub Catalogue"
tags:
- tabular
- programming
- computer science
---

# Hugging Face Model Hub Catalogue

**Subtitle:** 20,000 open models with tasks, libraries, downloads, likes, licences and provenance tags.

---

## 📖 Description

### 20,000 models from the Hugging Face Hub

Hugging Face hosts the largest open model registry. This dataset pages the model API and captures
**20,000 repositories** with **43 parameters** each.

- **Repository** — id, author, SHA, creation and update timestamps, file count and privacy/gating.
- **Popularity** — downloads, likes, trending score, downloads per day and likes per 1,000 downloads.
- **Task and library** — pipeline tag, library name, full tag list and derived task flags.
- **Provenance** — licence, dataset tags and base-model tags.
- **Derived** — tag counts, age and update recency, model-family flags, download/like bands and
  organisation flag.

The sample spans **54 pipeline tasks** and **4,472 authors**, with **2,645,129,388
downloads** in the last 30 days — a map of the open-model ecosystem for trend and adoption analysis.

## 🧾 Columns (43)

`model_id`, `author`, `sha`, `created_at`, `last_modified`, `downloads`, `likes`, `trending_score`, `pipeline_tag`, `library_name`, `tags`, `tag_count`, `license`, `dataset_count`, `base_model_count`, `gated`, `private`, `file_count`, `age_days`, `days_since_update`, `downloads_per_day`, `likes_per_1k_downloads`, `is_gated`, `is_private`, `has_license`, `has_dataset`, `has_base_model`, `is_text_generation`, `is_text_classification`, `is_image_generation`, `is_speech`, `is_embedding`, `is_recent`, `is_stale`, `is_llama_family`, `is_mistral_family`, `is_qwen_family`, `is_diffusers`, `download_band`, `likes_band`, `tag_to_download_ratio`, `model_id_length`, `is_org_model`

## 💡 Ideas for using this data

1. **Task landscape** — models and downloads by pipeline tag.
2. **Popularity dynamics** — downloads vs likes and age.
3. **Fine-tuning chains** — base-model tags and family concentration.
4. **Licensing** — licence mix across tasks and authors.
5. **Organisations** — which namespaces dominate each task.
6. **Freshness** — model churn and stale repositories.
7. **Gating** — gated model prevalence by family.
8. **Trending** — trending score vs raw downloads.

## 📁 Files

| File | What it is |
|---|---|
| `hf_models.csv` | 20,000 models x 43 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`machine-learning`, `hugging-face`, `models`, `nlp`, `open-source`, `ai`

## 🔗 Provenance

- **Source:** **Hugging Face Hub API** (`https://huggingface.co/api/models`), full
  model records, sorted by downloads.
- **Sampling:** cursor pagination following the API `Link` header, up to 20,000 unique models.
- **Processing:** tags parsed for licences, datasets and base models; counts, rates, bands and task
  flags derived.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Real time.** The Hub API reflects new models and download counts continuously.

## ⚠️ Caveats

- Downloads are 30-day counts and can be inflated by CI pipelines.
- The sample is ordered by downloads, so newer long-tail models are underrepresented.
- Tags are user-supplied and inconsistent.
- Model sizes and parameter counts are not included in the listing payload.
- Gated and private models can change visibility at any time.

## 📜 Licence

Model metadata is published by the Hugging Face Hub; individual model licences vary.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
