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
pretty_name: "Nobel Prize Laureates 1901-2026"
tags:
- tabular
- science
- history
---

# Nobel Prize Laureates 1901-2026

**Subtitle:** Every Nobel Prize with laureate demographics, affiliations and prize citations

**Tags:** `history`, `science`, `education`, `research`, `society`, `awards`, `nobel`, `gender`, `tabular`, `social-science`

**Dataset File:** `nobel_laureates.csv` (1,085 rows, 46 columns, 488.0 KB)

---

## 📖 Description

### Every Nobel Prize ever awarded, one row per laureate

Straight from the Nobel Foundation's open API: **1,085 rows** covering the 126 award years from
1901 to 2026, describing **1,005 individual laureates** and **31 organisational
laureates** through **46 parameters**.

Each row is one laureate receiving one prize (a shared prize therefore produces several rows sharing the
same `prize_year`/`category`), and includes:
- **The prize** — year, category and full official name, announcement date, prize amount in SEK, the
  inflation-adjusted amount and how many laureates shared it.
- **The laureate** — API id, person/organisation type, known name, full name, given and family name,
  gender, organisation name and the fraction of the prize received.
- **The citation** — the motivation text explaining the award.
- **Life and place** — birth date, city, country at the time and present-day country, continent of birth,
  death date and city, all affiliations with their cities and countries.
- **Derived measures** — age at award, birth and death year, lifespan, posthumous and shared-prize flags,
  share of the prize in percent, prize value per laureate, value of the laureate's own portion (raw and
  inflation-adjusted), decade, century, category group and years since the award.

Years in which a prize was not awarded appear as a single row with `laureate_type = none`, so the file can
be used directly for time-series work without silently dropping years.

## 🧾 Columns (46)

`prize_year`, `category`, `category_full_name`, `date_awarded`, `prize_amount_sek`, `prize_amount_adjusted_sek`, `n_laureates`, `laureate_id`, `laureate_type`, `known_name`, `full_name`, `given_name`, `family_name`, `gender`, `org_name`, `portion`, `motivation`, `birth_date`, `birth_city`, `birth_country`, `birth_country_now`, `birth_continent`, `death_date`, `death_city`, `death_country_now`, `affiliation_count`, `first_affiliation`, `first_affiliation_city`, `first_affiliation_country`, `affiliations_all`, `age_at_award`, `birth_year`, `death_year`, `lifespan_years`, `is_posthumous`, `is_shared`, `share_of_prize_pct`, `prize_amount_per_laureate_sek`, `value_of_portion_sek`, `value_of_portion_adjusted_sek`, `decade`, `category_group`, `birth_decade`, `is_organisation`, `century`, `years_since_award`

## 💡 Ideas for using this data

1. **Laureate demographics** — gender, birth continent and birth decade over 125 years of prizes.
2. **Age at award** — distribution by category; physicists tend to be younger than literature laureates.
3. **Institutional dominance** — which affiliations and countries produce the most laureates?
4. **Shared prizes** — how the fraction of shared awards and the number of co-laureates evolved.
5. **Prize value** — real (inflation-adjusted) prize amount per laureate over time.
6. **Posthumous awards** — the rare cases and the rules that followed them.
7. **Text mining** — the `motivation` field is clean prose; extract topics or build a citation-keyword trend.
8. **Geography of science** — map birthplaces and affiliations; measure the rise of the United States and Asia.
9. **Family names** — surname diversity among laureates, or name-origin inference.

## 📁 Files

| File | What it is |
|---|---|
| `nobel_laureates.csv` | 1,085 laureate-prize rows x 46 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: demographics, age at award, prize value. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`history`, `science`, `education`, `research`, `society`, `awards`, `nobel`, `gender`, `tabular`, `social-science`

## 🔗 Provenance

- **Source:** **Nobel Prize open data API v2.1**, `https://api.nobelprize.org/2.1/nobelPrizes`,
  published by the Nobel Foundation (nobelprize.org).
- **Query:** all prizes, sorted ascending by year, `limit=1000` (covers the entire award history).
- **Transformation:** prize records exploded to one row per laureate, nested birth/death/affiliation objects
  flattened, and 16 derived columns added.
- **Snapshot date:** 20 November 2026.

## 🔄 Update frequency

**Annual.** New laureates are announced each October; re-run `scripts/16_nobel.py` after the announcement to extend the file.

## ⚠️ Caveats

- Country names for birthplaces are given both as historical (`birth_country`) and present-day (`birth_country_now`) entities; use the latter for maps.
- Some early laureates have no recorded birth date, so `age_at_award` is empty for them.
- Organisational laureates (mostly Peace) have no gender, birth data or age.
- `prize_amount_sek` changes meaning over time — compare using `prize_amount_adjusted_sek`.
- Shared prizes produce multiple rows with the same `prize_year` and `category`; count prizes with `nunique` on year+category, not with `len`.
- The Nobel Foundation records gender as a binary field, which limits analysis to that categorisation.

## 📜 Licence

The Nobel Prize API is published by the Nobel Foundation for public use (CC0-style open data). Nobel Prize, Nobel Laureate and the Nobel medal are registered trademarks of the Nobel Foundation; this dataset is an independent compilation and is not endorsed by it.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `prize_year` | `number` | Year the prize was awarded. |
| 2 | `category` | `string` | Nobel category (Physics, Chemistry, Medicine, Literature, Peace, Economic Sciences). |
| 3 | `category_full_name` | `string` | Full official name of the prize. |
| 4 | `date_awarded` | `date` | Date the prize was announced/awarded. |
| 5 | `prize_amount_sek` | `number` | Prize amount in Swedish kronor at the time of the award. |
| 6 | `prize_amount_adjusted_sek` | `number` | Prize amount adjusted to a common price level (SEK). |
| 7 | `n_laureates` | `number` | Number of laureates sharing this prize. |
| 8 | `laureate_id` | `number` | Nobel Prize API laureate identifier. |
| 9 | `laureate_type` | `string` | person, organisation, or none when the prize was not awarded. |
| 10 | `known_name` | `string` | Name the laureate is generally known by. |
| 11 | `full_name` | `string` | Full name as recorded by the Nobel Foundation. |
| 12 | `given_name` | `string` | Given name(s). |
| 13 | `family_name` | `string` | Family name. |
| 14 | `gender` | `string` | male or female (as recorded); empty for organisations. |
| 15 | `org_name` | `string` | Organisation name, for prizes awarded to institutions. |
| 16 | `portion` | `number` | Fraction of the prize received (1 = the whole prize). |
| 17 | `motivation` | `string` | Citation explaining why the prize was awarded. |
| 18 | `birth_date` | `date` | Laureate date of birth. |
| 19 | `birth_city` | `string` | City of birth. |
| 20 | `birth_country` | `string` | Country of birth (as it was at the time). |
| 21 | `birth_country_now` | `string` | Present-day country of the birthplace. |
| 22 | `birth_continent` | `string` | Continent of the birthplace (supplied by the Nobel API). |
| 23 | `death_date` | `date` | Date of death, where applicable. |
| 24 | `death_city` | `string` | City of death. |
| 25 | `death_country_now` | `string` | Present-day country of death. |
| 26 | `affiliation_count` | `number` | Number of affiliations recorded at the time of the award. |
| 27 | `first_affiliation` | `string` | First affiliation listed. |
| 28 | `first_affiliation_city` | `string` | City of that affiliation. |
| 29 | `first_affiliation_country` | `string` | Country of that affiliation. |
| 30 | `affiliations_all` | `string` | Semicolon-separated list of all affiliations. |
| 31 | `age_at_award` | `number` | Laureate age in years at the award date (persons only). |
| 32 | `birth_year` | `number` | Year of birth. |
| 33 | `death_year` | `number` | Year of death. |
| 34 | `lifespan_years` | `number` | Age at death, or age at snapshot for living laureates. |
| 35 | `is_posthumous` | `boolean` | true when the prize was awarded after the laureate's death. |
| 36 | `is_shared` | `boolean` | true when the prize was split between two or more laureates. |
| 37 | `share_of_prize_pct` | `number` | Portion of the prize received, in percent. |
| 38 | `prize_amount_per_laureate_sek` | `number` | Prize amount divided by the number of laureates. |
| 39 | `value_of_portion_sek` | `number` | Prize amount multiplied by the laureate's portion. |
| 40 | `value_of_portion_adjusted_sek` | `number` | Inflation-adjusted value of that portion. |
| 41 | `decade` | `string` | Award decade. |
| 42 | `category_group` | `string` | Coarse category grouping used for comparisons. |
| 43 | `birth_decade` | `string` | Decade of birth. |
| 44 | `is_organisation` | `boolean` | true when the laureate is an institution rather than a person. |
| 45 | `century` | `string` | Century of the award. |
| 46 | `years_since_award` | `number` | Years between the award and the snapshot date. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
