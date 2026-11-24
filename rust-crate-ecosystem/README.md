---
license: cc-by-4.0
task_categories:
- tabular
tags:
- tabular
pretty_name: "Rust Crate Ecosystem"
---

# Rust Crate Ecosystem

**Subtitle:** 20,000 crates with downloads, versions, metadata and maintenance stats

**Tags:** `tabular`, `software`, `rust`

**Dataset File:** `rust_crates.csv` (22,404 rows, 44 columns, 7.0 MB)

**Provenance & Source:** crates.io API & Database Dumps (crates.io)

**Expected Update Frequency:** `monthly`

---

## 📖 Description

### 30,000 Rust crates

crates.io is the Rust package registry. This dataset contains the **20,000 most-downloaded crates**
with **44 parameters** each.

- **Identity** — name, creation and update dates, all-time and recent downloads, version count,
  newest/max stable/default versions and yanked flag.
- **Metadata** — description, homepage, documentation, repository, keywords and categories.
- **Derived** — description length, keyword/category counts, link and description flags, pre-release
  and 0.x flags, name features, age, downloads per day, versions per year and domain flags
  (async, CLI, WASM, embedded, proc-macro, serialization).

**10,110 crates have more than a million downloads** and **19,452** link to a source
repository — a snapshot of the Rust open-source supply chain.

## 🧾 Columns (44)

`name`, `created_at`, `updated_at`, `downloads`, `recent_downloads`, `recent_share_pct`, `num_versions`, `max_version`, `newest_version`, `max_stable_version`, `default_version`, `yanked`, `description`, `description_length`, `homepage`, `documentation`, `repository`, `keywords`, `categories`, `keyword_count`, `category_count`, `has_homepage`, `has_documentation`, `has_repository`, `has_description`, `is_prerelease`, `is_major_zero`, `name_length`, `name_has_underscore`, `age_days`, `days_since_update`, `downloads_per_day`, `recent_downloads_per_day`, `versions_per_year`, `is_popular`, `download_band`, `is_async`, `is_cli`, `is_wasm`, `is_embedded`, `is_proc_macro`, `is_serialization`, `created_year`, `updated_year`

## 💡 Ideas for using this data

1. **Adoption curves** — downloads vs age, and which crates are still growing.
2. **Maintenance** — days since update vs popularity; find abandoned dependencies.
3. **Naming conventions** — underscores vs hyphens, length and prefix patterns.
4. **Ecosystem layers** — async vs CLI vs embedded vs WASM crates by download band.
5. **Documentation quality** — repository/documentation/homepage coverage by category.
6. **Version churn** — versions per year and 0.x maturity.
7. **Category network** — co-occurrence of categories and keywords.
8. **Dependency risk** — popular crates with stale updates or yanked versions.
9. **Supply chain** — build a crate metadata table for SBOM research.

## 📁 Files

| File | What it is |
|---|---|
| `rust_crates.csv` | 20,000 crates x 44 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`rust`, `crates`, `packages`, `software`, `open-source`, `supply-chain`, `developer-tools`

## 🔗 Provenance

- **Source:** **crates.io API**, `https://crates.io/api/v1/crates?sort=downloads`,
  100 crates per page.
- **Scope:** the 30,000 most-downloaded crates at snapshot time.
- **Processing:** list records flattened; keywords and categories joined; age, download-rate, naming
  and domain flags derived.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Continuous.** New crates and versions are published daily.

## ⚠️ Caveats

- Downloads are cumulative and not de-duplicated by user or CI.
- The crates.io API does not expose licence or dependency data in the list endpoint.
- Domain flags are keyword heuristics on the description and keywords.
- A yanked crate can still have many historical downloads.
- Version strings are not strictly semver-normalised.
- Recent downloads cover a 90-day window, so the rate is approximate.
- This is a popularity-ranked sample, not a random sample of all crates.

## 📜 Licence

crate metadata is provided by crates.io under CC BY 4.0; each crate keeps its own licence.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `name` | `string` | Crate name. |
| 2 | `created_at` | `date` | First publication date. |
| 3 | `updated_at` | `date` | Last update date. |
| 4 | `downloads` | `number` | All-time downloads. |
| 5 | `recent_downloads` | `number` | Downloads in the last 90 days. |
| 6 | `recent_share_pct` | `number` | recent_downloads as a percentage of all-time downloads. |
| 7 | `num_versions` | `number` | Number of published versions. |
| 8 | `max_version` | `string` | Highest published version. |
| 9 | `newest_version` | `string` | Newest published version. |
| 10 | `max_stable_version` | `string` | Highest non-prerelease version. |
| 11 | `default_version` | `string` | Default version shown by crates.io. |
| 12 | `yanked` | `boolean` | true when the crate is yanked. |
| 13 | `description` | `string` | Crate description. |
| 14 | `description_length` | `number` | Characters in the description. |
| 15 | `homepage` | `string` | Project homepage. |
| 16 | `documentation` | `string` | Documentation URL. |
| 17 | `repository` | `string` | Source repository URL. |
| 18 | `keywords` | `number` | Keywords (semicolon-joined). |
| 19 | `categories` | `number` | Categories (semicolon-joined). |
| 20 | `keyword_count` | `number` | Number of keywords. |
| 21 | `category_count` | `number` | Number of categories. |
| 22 | `has_homepage` | `boolean` | true when a homepage is listed. |
| 23 | `has_documentation` | `boolean` | true when documentation is listed. |
| 24 | `has_repository` | `boolean` | true when a repository is listed. |
| 25 | `has_description` | `boolean` | true when a description exists. |
| 26 | `is_prerelease` | `boolean` | true when the newest version is a pre-release. |
| 27 | `is_major_zero` | `boolean` | true when the newest version is 0.x. |
| 28 | `name_length` | `number` | Characters in the crate name. |
| 29 | `name_has_underscore` | `boolean` | true when the name contains an underscore. |
| 30 | `age_days` | `number` | Days since first publication. |
| 31 | `days_since_update` | `number` | Days since the last update. |
| 32 | `downloads_per_day` | `number` | All-time downloads divided by age in days. |
| 33 | `recent_downloads_per_day` | `number` | Recent downloads divided by 90. |
| 34 | `versions_per_year` | `number` | Versions published per year of age. |
| 35 | `is_popular` | `boolean` | true when all-time downloads exceed one million. |
| 36 | `download_band` | `string` | All-time download band. |
| 37 | `is_async` | `boolean` | true when the description or keywords mention async/tokio. |
| 38 | `is_cli` | `boolean` | true when the description or keywords mention CLI/command line. |
| 39 | `is_wasm` | `boolean` | true when the description or keywords mention wasm/webassembly. |
| 40 | `is_embedded` | `boolean` | true when the description or keywords mention embedded/no_std. |
| 41 | `is_proc_macro` | `boolean` | true when the description or keywords mention proc-macro. |
| 42 | `is_serialization` | `boolean` | true when the description or keywords mention serde/serialization. |
| 43 | `created_year` | `number` | Year of first publication. |
| 44 | `updated_year` | `number` | Year of last update. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
