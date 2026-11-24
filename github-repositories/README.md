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
pretty_name: "Most-Starred GitHub Repositories"
tags:
- tabular
- programming
- software
---

# Most-Starred GitHub Repositories

**Subtitle:** 1,000 repositories above 10,000 stars with languages, licences, topics and activity metrics.

---

## 📖 Description

### 1,000 most-starred GitHub repositories

GitHub's search API reports several thousand public repositories above 10,000 stars but only
exposes the first 1,000 results. This dataset contains **all 1,000 of them** with
**50 parameters**.

- **Repository** — id, name, owner and owner type, description, homepage and default branch.
- **Activity** — stars, forks, watchers, open issues, size, creation/update/push timestamps.
- **Metadata** — primary language, licence, topics, archived/fork/template/visibility flags and
  feature switches (issues, wiki, pages, discussions).
- **Derived** — age, days since push, stars per day, forks and issues per star, size in MB, licence/
  topic/description flags, language flags, org/active/stale flags and star bands.

The set carries **71,749,189 stars** across **43 languages**, with **29 archived**
projects — a snapshot of what the open-source world considers important.

## 🧾 Columns (50)

`repo_id`, `name`, `full_name`, `owner`, `owner_type`, `description`, `homepage`, `language`, `license`, `stars`, `forks`, `watchers`, `open_issues`, `size_kb`, `created_at`, `updated_at`, `pushed_at`, `topics`, `topic_count`, `fork`, `archived`, `is_template`, `has_issues`, `has_wiki`, `has_pages`, `has_discussions`, `default_branch`, `visibility`, `age_days`, `days_since_push`, `stars_per_day`, `forks_per_star`, `issues_per_star`, `size_mb`, `has_license`, `has_topics`, `has_description`, `is_archived`, `is_fork`, `is_org_owned`, `is_active`, `is_stale`, `is_python`, `is_javascript`, `is_go`, `is_rust`, `is_cpp`, `star_band`, `description_length`, `name_length`

## 💡 Ideas for using this data

1. **Language popularity** — stars and repos per language.
2. **Growth** — stars per day for young vs old projects.
3. **Maintenance** — archived and stale repository share.
4. **Licensing** — licence mix by language and owner type.
5. **Community** — issues and forks relative to stars.
6. **Topics** — topic co-occurrence networks.
7. **Organisations** — which orgs own the most top repos.
8. **Project size** — repo size vs stars.

## 📁 Files

| File | What it is |
|---|---|
| `github_repositories.csv` | 1,000 repositories x 50 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`github`, `open-source`, `software`, `repositories`, `developer-tools`

## 🔗 Provenance

- **Source:** **GitHub REST search API**
  (`/search/repositories?q=stars:>10000`), sorted by stars.
- **Sampling:** all results above 10,000 stars, 100 per page.
- **Processing:** owner, licence and topic objects flattened; age, rates and flags derived.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Real time.** Stars and activity change continuously.

## ⚠️ Caveats

- Star counts are a popularity signal, not a quality measure.
- Unauthenticated search is rate-limited, so collection is throttled.
- Repositories below 10,000 stars are excluded.
- Sizes are Git object sizes, not working-tree sizes.
- Archived and fork status can change after extraction.

## 📜 Licence

Public GitHub repository metadata; individual repository licences apply.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
