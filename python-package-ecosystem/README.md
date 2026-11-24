---
annotations_creators:
- no-annotation
language:
- en
license: cc-by-4.0
multilinguality:
- monolingual
size_categories:
- 10K<n<100K
source_datasets:
- original
task_categories:
- tabular-classification
task_ids: []
pretty_name: "Python Package Ecosystem"
tags:
- tabular
- programming
- software
---

# Python Package Ecosystem

**Subtitle:** 4,999 top PyPI packages with downloads, licenses, dependencies & releases

**Tags:** `python`, `software`, `open-source`, `tabular`

**Dataset File:** `pypi_packages.csv` (23,010 rows, 47 columns, 3.4 MB)

**Provenance & Source:** PyPI JSON API & BigQuery PyPI Public Dataset

**Expected Update Frequency:** `annually`

---

## 📖 Description

### The Python package ecosystem, ranked by real downloads

PyPI serves millions of package downloads a day and publishes the numbers. This dataset combines the
**top 4,999 projects by 30-day downloads** with each project's full PyPI metadata.

Per package you get **47 parameters**:
- **Reach** — download rank and count for the last 30 days, share of the ecosystem's downloads,
  download concentration implied by the ranks.
- **Identity** — name, summary, author, canonical URL, home page, project URLs (docs / source /
  changelog), keywords.
- **Licensing** — raw licence string plus a normalised class (MIT, Apache, GPL, BSD, MPL, LGPL,
  public domain, Creative Commons, other, unknown).
- **Compatibility** — `requires_python`, supported Python versions from classifiers, Python-3-only
  flag, wheel and sdist availability, file sizes, yanked files.
- **Dependencies** — runtime dependency count (extras excluded), extras entries, a has-dependencies flag.
- **Release history** — version count, first and latest release dates, total and yanked file counts,
  age, days since last release, releases per year, cadence and maturity bands.
- **Packaging hygiene** — classifier and topic counts, development status, project-URL completeness,
  pre-release flag.

The top 10 projects alone account for **11.1%** of all downloads in the file,
which makes download concentration, release cadence and dependency counts directly comparable.

## 🧾 Columns (47)

`rank`, `project`, `monthly_downloads`, `download_share_pct`, `latest_version`, `summary`, `author`, `license`, `license_class`, `requires_python`, `home_page`, `project_url`, `package_url`, `keywords`, `development_status`, `classifier_count`, `topic_count`, `python_versions_supported`, `python_version_count`, `requires_dist_count`, `dependency_count`, `release_count`, `total_file_count`, `yanked_file_count`, `first_release`, `latest_release`, `latest_upload`, `latest_size_bytes`, `summary_length`, `has_wheel`, `has_sdist`, `has_homepage`, `has_docs_url`, `has_source_url`, `has_changelog`, `project_url_count`, `is_prerelease`, `python3_only`, `name_length`, `is_single_word`, `major_version`, `age_days`, `days_since_release`, `releases_per_year`, `release_cadence`, `maturity`, `has_dependencies`

## 💡 Ideas for using this data

1. **Download concentration** — Lorenz curve and Gini of `monthly_downloads`; the long tail is extreme.
2. **Maintenance risk** — find widely used packages with long `days_since_release` or an inactive status.
3. **Licence landscape** — licence class by download volume; how much of the ecosystem is permissively licensed?
4. **Dependency weight** — packages with the most runtime dependencies versus their download share.
5. **Release cadence** — cadence band versus rank; do the most-downloaded packages ship more or less often?
6. **Packaging quality** — wheels, sdists and project URLs as a quality score, then check whether quality predicts downloads.
7. **Python version adoption** — `python_versions_supported` over the ecosystem; who still lists 3.6?
8. **Name economics** — name length and single-word names versus downloads (short names are scarce).
9. **Supply-chain graph starter** — join `requires_dist_count` with per-package dependency lists fetched from PyPI for a network analysis.

## 📁 Files

| File | What it is |
|---|---|
| `pypi_packages.csv` | 4,999 packages x 47 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: concentration, licences, cadence, dependencies. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`python`, `pypi`, `software`, `open-source`, `packages`, `programming`, `developer-tools`, `supply-chain`, `tabular`, `web-scraping`

## 🔗 Provenance

- **Sources:** (1) the **top PyPI packages** list maintained by Hugo van Kemenade
  (`hugovk.dev/top-pypi-packages/`), a 30-day rolling download ranking built from the official
  PyPI download logs; (2) the **PyPI JSON API** (`https://pypi.org/pypi/<project>/json`) for each
  project's metadata, classifiers, dependencies and release files.
- **Coverage:** the 5,000 highest-ranked projects at snapshot time.
- **Processing:** list and per-package metadata were joined on project name; release dates and file
  counts were derived from the `releases`/`urls` objects; licences normalised into classes.
- **Derived columns:** download share, licence class, version counts, dependency counts, age,
  days since release, releases per year, cadence and maturity bands, URL completeness flags.
- **Snapshot date:** 21 November 2026.

## 🔄 Update frequency

**Monthly.** The download ranking is a rolling 30-day window; re-run `scripts/25_pypi_ecosystem.py` for a fresh snapshot.

## ⚠️ Caveats

- Download counts include CI, mirrors and bots, so they measure installs rather than users.
- The ranking covers only the top 5,000 projects; the long tail (hundreds of thousands of packages) is absent.
- `author` and `summary` are free text and inconsistently filled.
- `license` is often a full licence sentence or 'UNKNOWN'; use `license_class` for grouping.
- Release dates come from file upload timestamps, which can be re-uploads rather than original publication.
- Dependency counts use `requires_dist` and exclude environment markers beyond extras.
- 5,000 API calls were made politely; a handful of packages may be missing if PyPI errored.

## 📜 Licence

Package metadata is published by PyPI and the respective authors; the download ranking is published by Hugo van Kemenade. Mixed open-source licences — check each package's `license` field.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `rank` | `number` | Rank in the 30-day download list (1 = most downloaded). |
| 2 | `project` | `string` | Package name on PyPI. |
| 3 | `monthly_downloads` | `number` | Downloads in the last 30 days (PyPI download statistics). |
| 4 | `download_share_pct` | `number` | Share of the total downloads of all packages in this file. |
| 5 | `latest_version` | `string` | Latest version on PyPI at snapshot time. |
| 6 | `summary` | `string` | One-line package description. |
| 7 | `author` | `string` | Author field as published. |
| 8 | `license` | `string` | Licence string or classifier as published. |
| 9 | `license_class` | `string` | Licence normalised into MIT, Apache, GPL, BSD, MPL, LGPL, Public domain, Creative Commons, Other, Unknown. |
| 10 | `requires_python` | `string` | PEP 440 Python version specifier. |
| 11 | `home_page` | `string` | Legacy home page URL. |
| 12 | `project_url` | `string` | Legacy project URL. |
| 13 | `package_url` | `string` | Canonical PyPI project URL. |
| 14 | `keywords` | `string` | Comma-separated keywords as published. |
| 15 | `development_status` | `string` | Development status from the trove classifiers. |
| 16 | `classifier_count` | `number` | Number of trove classifiers. |
| 17 | `topic_count` | `number` | Number of 'Topic ::' classifiers. |
| 18 | `python_versions_supported` | `string` | Python versions named in the classifiers (semicolon-joined). |
| 19 | `python_version_count` | `number` | Number of named Python versions. |
| 20 | `requires_dist_count` | `number` | Raw number of entries in requires_dist, including extras. |
| 21 | `dependency_count` | `number` | Number of runtime dependencies, excluding extras. |
| 22 | `release_count` | `number` | Number of uploaded versions. |
| 23 | `total_file_count` | `number` | Number of distribution files across all versions. |
| 24 | `yanked_file_count` | `number` | Number of yanked files. |
| 25 | `first_release` | `date` | Date of the earliest uploaded file (ISO). |
| 26 | `latest_release` | `date` | Date of the most recent uploaded file (ISO). |
| 27 | `latest_upload` | `date` | Upload date of the current version. |
| 28 | `latest_size_bytes` | `number` | Size of the largest distribution file for the current version. |
| 29 | `summary_length` | `number` | Characters in the summary. |
| 30 | `has_wheel` | `boolean` | true when a wheel is published for the current version. |
| 31 | `has_sdist` | `boolean` | true when a source distribution is published. |
| 32 | `has_homepage` | `boolean` | true when a home page is declared. |
| 33 | `has_docs_url` | `boolean` | true when a documentation URL appears in project_urls. |
| 34 | `has_source_url` | `boolean` | true when a source/repository URL appears in project_urls. |
| 35 | `has_changelog` | `boolean` | true when a changelog URL appears in project_urls. |
| 36 | `project_url_count` | `number` | Number of project URLs declared. |
| 37 | `is_prerelease` | `boolean` | true when the latest version looks like a pre-release. |
| 38 | `python3_only` | `boolean` | true when requires_python allows Python 3 but not Python 2. |
| 39 | `name_length` | `number` | Characters in the project name. |
| 40 | `is_single_word` | `boolean` | true when the name has no spaces. |
| 41 | `major_version` | `number` | Major component of the latest version. |
| 42 | `age_days` | `number` | Days between the first release and the snapshot date. |
| 43 | `days_since_release` | `number` | Days since the most recent release. |
| 44 | `releases_per_year` | `number` | Average number of releases per year since the first release. |
| 45 | `release_cadence` | `string` | Release cadence band: Dormant, Slow, Regular, Rapid, Very rapid. |
| 46 | `maturity` | `string` | Maturity band from major version and age. |
| 47 | `has_dependencies` | `boolean` | true when the package declares runtime dependencies. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
