---
annotations_creators:
- no-annotation
language:
- en
license: cc0-1.0
multilinguality:
- monolingual
size_categories:
- 10K<n<1M
source_datasets:
- original
task_categories:
- tabular-classification
task_ids: []
pretty_name: "US Public Schools NCES Directory"
tags:
- tabular
- education
---

# US Public Schools NCES Directory


## ⭐ Upvote & Support
If you find this dataset useful for your research, machine learning projects, or data visualization, please consider giving it an **Upvote**! Your support helps make open data more accessible to the community.


# US Public Schools — NCES Common Core of Data Directory

**Subtitle:** 102,268 K-12 public schools with enrolment, staff, poverty, locale and district geography.

---

## 📖 Description

### 102,268 US public schools (NCES Common Core of Data)

The Urban Institute's Education Data Portal republishes the federal Common Core of Data. This
dataset is the **2022-23 school directory**: every public elementary, middle and
high school in the United States and its territories, with **102,268 schools** and
**65 parameters**.

- **Identity** — NCES school id, state and district ids, name, district name and school code.
- **Location** — street, city, state, ZIP, county FIPS, CBSA, CSA, latitude and longitude,
  plus the NCES urban-centric locale code and description (city / suburb / town / rural).
- **School** — level, type, status, lowest and highest grade, grade span, charter, magnet,
  virtual, shared-time, Title I, schoolwide Title I and Bureau of Indian Education flags.
- **Students and staff** — enrolment, FTE teachers, student-teacher ratio, free and reduced-price
  lunch counts and percentages, direct certification, Community Eligibility Provision counts and
  lunch programme code.
- **Politics and derived** — state legislative districts, congressional district, phone and
  coordinate flags, enrolment bands.

The file covers **56 states and territories** with **49,620,679 enrolled students**;
**99,528 schools are open**, **8,288 are charter schools**, and the mean student-teacher
ratio is **15.9**.

## 🧾 Columns (65)

`ncessch`, `school_id`, `school_name`, `leaid`, `lea_name`, `state_leaid`, `seasch`, `year`, `state_fips`, `state`, `state_abbr`, `county_code`, `county_fips`, `cbsa`, `csa`, `urban_centric_locale`, `locale_desc`, `locale_type`, `street_location`, `city_location`, `state_location`, `zip_location`, `phone`, `latitude`, `longitude`, `school_level`, `school_level_desc`, `school_type`, `school_type_desc`, `school_status`, `school_status_desc`, `lowest_grade_offered`, `highest_grade_offered`, `grade_span`, `grade_span_size`, `is_charter`, `is_magnet`, `is_virtual`, `is_shared_time`, `is_title_i`, `is_title_i_schoolwide`, `is_bie_school`, `enrollment`, `teachers_fte`, `student_teacher_ratio`, `free_lunch`, `reduced_price_lunch`, `free_or_reduced_price_lunch`, `free_lunch_pct`, `reduced_lunch_pct`, `free_or_reduced_lunch_pct`, `direct_certification`, `direct_certification_pct`, `elem_cedp`, `middle_cedp`, `high_cedp`, `ungrade_cedp`, `lunch_program`, `state_leg_district_lower`, `state_leg_district_upper`, `congress_district_id`, `has_phone`, `has_coordinates`, `is_open`, `enrollment_band`

## 💡 Ideas for using this data

1. **Funding equity** — free-lunch share vs student-teacher ratio by state.
2. **Charter schools** — where they are and how large they are.
3. **Locale** — city, suburb, town and rural schools compared.
4. **Grade spans** — which configurations are most common.
5. **Map** — plot every school by latitude and longitude.
6. **Districts** — largest districts and their school counts.
7. **Virtual schools** — growth and geography.
8. **Title I** — poverty concentration and school size.

## 📁 Files

| File | What it is |
|---|---|
| `us_public_schools.csv` | 102,268 schools x 65 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`education`, `schools`, `united-states`, `k12`, `geography`, `public-data`, `society`

## 🔗 Provenance

- **Source:** **Urban Institute Education Data Portal**, endpoint
  `educationdata.urban.org/api/v1/schools/ccd/directory/2022/` (NCES Common Core of Data).
- **Processing:** all pages of the 2022 directory were read; 50 API fields were flattened, state
  and locale codes decoded, grade spans, ratios, lunch percentages and flags derived.
- **Snapshot date:** 27 November 2026.

## 🔄 Update frequency

**Annually.** NCES publishes a new school directory each school year.

## ⚠️ Caveats

- One school year only; the directory is not a time series.
- Enrolment, teacher and lunch figures are as reported by state agencies and can be missing.
- Charter, magnet and Title I flags are 1/0 in the source and may be blank for some states.
- Closed schools remain in the directory for the year they operated.
- Territories and tribal schools have less complete data than the 50 states.
- Counts are not adjusted for the Community Eligibility Provision when comparing lunch shares.

## 📜 Licence

NCES Common Core of Data via the Urban Institute Education Data Portal, public domain.

