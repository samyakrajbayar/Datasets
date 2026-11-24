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
pretty_name: "Global Clinical Trials Registry"
tags:
- tabular
- health
- medicine
---

# Global Clinical Trials Registry

**Subtitle:** 10,000 ClinicalTrials.gov studies with design, sponsors, eligibility & outcomes

**Tags:** `health`, `medicine`, `research`, `tabular`

**Dataset File:** `clinical_trials.csv` (10,003 rows, 81 columns, 9.2 MB)

**Provenance & Source:** ClinicalTrials.gov Modernized REST API (National Library of Medicine)

**Expected Update Frequency:** `monthly`

---

## 📖 Description

### The world's clinical trial registry, flattened for analysis

ClinicalTrials.gov is the largest trial registry on earth. This snapshot takes
**10,000 study records** (the most recently updated ones) and flattens the registration
document into **81 tidy columns** — one row per trial.

What each row carries:
- **Identity** — NCT number, brief and official title, acronym, sponsor protocol id,
  submitting organisation and its class, secondary identifiers.
- **Status and dates** — overall and last-known status, why a trial stopped, start,
  primary-completion and completion dates, first-posted, last-updated and results-posted dates.
- **Design** — study type, phase (raw list plus a cleaned label), allocation, intervention
  model, masking, primary purpose, number of arms, enrollment count and type.
- **Conditions and interventions** — full condition and keyword lists, intervention names
  and types, arm-group count.
- **Outcomes** — primary outcome measures and counts, secondary and other outcome counts.
- **Eligibility** — sex, minimum and maximum age, standard age groups, healthy-volunteer flag,
  sampling method.
- **Geography and sponsorship** — every country with a site, site and facility counts,
  US-site flag, lead sponsor and class, collaborator list.
- **Oversight and sharing** — FDA drug/device regulation flags, data-monitoring-committee flag,
  individual-patient-data sharing statement, reference count.
- **Derived features** — planned duration in days, start year, age bounds in years,
  pediatric/adult/senior flags, industry/academic sponsor flags, enrollment size band,
  randomised/blinded flags, update lag and title/abstract lengths.

**0 trials (0.0%)** are industry-sponsored and **1,354** have posted results,
so the file supports both registry science and meta-research on reporting bias.

## 🧾 Columns (81)

`nct_id`, `brief_title`, `official_title`, `acronym`, `org_study_id`, `secondary_id_count`, `organization`, `organization_class`, `study_type`, `overall_status`, `last_known_status`, `why_stopped`, `phase`, `phase_clean`, `lead_sponsor`, `lead_sponsor_class`, `collaborator_count`, `collaborators`, `enrollment_count`, `enrollment_type`, `start_date`, `primary_completion_date`, `completion_date`, `first_posted`, `last_update_posted`, `results_first_posted`, `has_results`, `condition_count`, `conditions`, `keywords`, `intervention_count`, `interventions`, `intervention_types`, `arm_group_count`, `primary_outcome_count`, `primary_outcome_measures`, `secondary_outcome_count`, `other_outcome_count`, `sex`, `minimum_age`, `maximum_age`, `healthy_volunteers`, `std_ages`, `sampling_method`, `primary_purpose`, `allocation`, `intervention_model`, `observational_model`, `masking`, `site_count`, `country_count`, `countries`, `has_us_site`, `facility_count`, `has_dmc`, `is_fda_regulated_drug`, `is_fda_regulated_device`, `ipd_sharing`, `reference_count`, `brief_summary_length`, `detailed_description_length`, `is_interventional`, `is_observational`, `is_industry_sponsored`, `is_academic_sponsored`, `is_network_sponsored`, `start_year`, `planned_duration_days`, `days_since_last_update`, `days_to_first_post`, `min_age_years`, `max_age_years`, `is_pediatric`, `is_older_adult`, `is_randomized`, `is_blinded`, `enrollment_band`, `title_length`, `condition_count_clean`, `is_oncology`, `accepts_healthy_volunteers`

## 💡 Ideas for using this data

1. **Trial geography** — map site countries; which conditions are studied where, and which countries are under-represented?
2. **Sponsor landscape** — industry vs academic vs NIH share over time, and how design choices differ between them.
3. **Reporting bias** — compare `has_results` and `results_first_posted` against `completion_date`; how long do results take, and which sponsors never post?
4. **Phase pipeline** — phase distribution by condition and start year; where does the pipeline thin out?
5. **Enrollment reality** — distribution of `enrollment_count` by phase and sponsor class; find implausibly small or huge trials.
6. **Design choices** — randomised vs single-arm, blinded vs open-label, and how they correlate with phase and condition.
7. **Stopped trials** — text-mine `why_stopped` for failure reasons (futility, slow accrual, safety).
8. **Pediatric gap** — share of trials with `is_pediatric` by condition; compare with disease burden.
9. **Text classification** — predict study type or phase from the title and brief summary.
10. **Duration modelling** — regress `planned_duration_days` on phase, sponsor class and condition area.

## 📁 Files

| File | What it is |
|---|---|
| `clinical_trials.csv` | 10,000 clinical trial registrations x 81 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: status mix, sponsors, phases, reporting lag. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`clinical-trials`, `health`, `medicine`, `research`, `pharmaceutical`, `medical-research`, `tabular`, `public-health`, `biology`, `statistics`

## 🔗 Provenance

- **Source:** U.S. National Library of Medicine, **ClinicalTrials.gov API v2**
  (`https://clinicaltrials.gov/api/v2/studies`), JSON format, 10 pages of 1,000 records.
- **Selection:** the API's default ordering (last update, newest first), so this is a
  *recent-activity sample* of the registry rather than its full 500,000+ record history.
- **Flattening:** nested `protocolSection` modules were flattened field by field; list-valued
  fields (conditions, countries, interventions, collaborators, outcome measures) are joined
  with semicolons.
- **Derived columns:** duration, start year, ages in years, pediatric/adult/senior flags,
  sponsor class flags, enrollment bands, randomised/blinded flags, update lag, text lengths.
- **Snapshot date:** 21 November 2026.

## 🔄 Update frequency

**Daily upstream.** ClinicalTrials.gov updates continuously; re-run `scripts/21_clinical_trials.py` to take a fresh snapshot.

## ⚠️ Caveats

- This is a sample of the 10,000 most recently updated studies, not the full registry — treat it as a recent cross-section.
- Registration quality varies enormously: some records are missing enrollment, dates, or outcome measures entirely.
- `enrollment_count` is *planned* enrollment (`enrollment_type` says actual or anticipated).
- Countries come from listed site locations; multi-country trials with sparse site lists under-count.
- Free-text fields (`why_stopped`, titles, summaries) are multilingual and inconsistently formatted.
- The registry includes observational studies and expanded-access records; filter on `study_type` for interventional-only analysis.
- No patient-level data is present; only aggregate registration metadata.

## 📜 Licence

Public domain — U.S. National Library of Medicine. ClinicalTrials.gov data is downloadable and reusable without restriction; cite NLM as the source.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `nct_id` | `string` | ClinicalTrials.gov identifier (NCT number). |
| 2 | `brief_title` | `string` | Short public title of the study. |
| 3 | `official_title` | `string` | Full scientific title, when supplied. |
| 4 | `acronym` | `string` | Study acronym, when supplied. |
| 5 | `org_study_id` | `string` | Sponsor's own protocol identifier. |
| 6 | `secondary_id_count` | `number` | Number of secondary identifiers (other registries, grants). |
| 7 | `organization` | `string` | Organisation that submitted the registration. |
| 8 | `organization_class` | `string` | Class of the submitting organisation (e.g. INDUSTRY, NIH). |
| 9 | `study_type` | `string` | Interventional, Observational or Expanded Access. |
| 10 | `overall_status` | `string` | Current recruitment/conduct status. |
| 11 | `last_known_status` | `string` | Last status before the study was withdrawn or unknown. |
| 12 | `why_stopped` | `string` | Free-text reason the study stopped, when given. |
| 13 | `phase` | `string` | Raw phase list as registered (semicolon-joined). |
| 14 | `phase_clean` | `string` | Phase collapsed to a single label, Early Phase 1 / Phase 1 / Phase 2 / Phase 3 / Phase 4 / Not applicable. |
| 15 | `lead_sponsor` | `string` | Primary sponsoring organisation. |
| 16 | `lead_sponsor_class` | `string` | Sponsor type: Industry, Academic, NIH, Network, Other. |
| 17 | `collaborator_count` | `number` | Number of collaborating organisations. |
| 18 | `collaborators` | `string` | Collaborating organisations (semicolon-joined). |
| 19 | `enrollment_count` | `number` | Planned or actual enrollment, as registered. |
| 20 | `enrollment_type` | `string` | Whether enrollment_count is ANTICIPATED or ACTUAL. |
| 21 | `start_date` | `string` | Study start date (ISO). |
| 22 | `primary_completion_date` | `string` | Date primary outcome data collection is expected to finish. |
| 23 | `completion_date` | `string` | Study completion date (ISO). |
| 24 | `first_posted` | `date` | Date the record first appeared on ClinicalTrials.gov. |
| 25 | `last_update_posted` | `date` | Date of the most recent record update. |
| 26 | `results_first_posted` | `date` | Date results were first posted, if any. |
| 27 | `has_results` | `boolean` | true when summary results are posted. |
| 28 | `condition_count` | `number` | Number of registered conditions. |
| 29 | `conditions` | `string` | Registered conditions (semicolon-joined). |
| 30 | `keywords` | `string` | Free-text keywords. |
| 31 | `intervention_count` | `number` | Number of interventions. |
| 32 | `interventions` | `string` | Intervention names (semicolon-joined). |
| 33 | `intervention_types` | `string` | Distinct intervention types: DRUG, DEVICE, BIOLOGICAL, BEHAVIORAL, ... |
| 34 | `arm_group_count` | `number` | Number of study arms/groups. |
| 35 | `primary_outcome_count` | `number` | Number of primary outcome measures. |
| 36 | `primary_outcome_measures` | `string` | Primary outcome measure names (semicolon-joined). |
| 37 | `secondary_outcome_count` | `number` | Number of secondary outcome measures. |
| 38 | `other_outcome_count` | `number` | Number of other outcome measures. |
| 39 | `sex` | `string` | Eligible sex: ALL, FEMALE, MALE. |
| 40 | `minimum_age` | `string` | Minimum eligible age as registered (e.g. '18 Years'). |
| 41 | `maximum_age` | `string` | Maximum eligible age as registered. |
| 42 | `healthy_volunteers` | `boolean` | true when healthy volunteers are accepted. |
| 43 | `std_ages` | `string` | Standard age groups: CHILD, ADULT, OLDER_ADULT. |
| 44 | `sampling_method` | `string` | Probability vs non-probability sampling (observational studies). |
| 45 | `primary_purpose` | `string` | Treatment, Prevention, Diagnostic, Screening, Supportive Care, ... |
| 46 | `allocation` | `string` | Randomized vs non-randomized. |
| 47 | `intervention_model` | `string` | Parallel, Crossover, Sequential, Factorial, Single Group. |
| 48 | `observational_model` | `string` | Cohort, Case-Control, Cross-Sectional, ... |
| 49 | `masking` | `string` | None, Single, Double, Triple, Quadruple. |
| 50 | `site_count` | `number` | Number of listed site locations. |
| 51 | `country_count` | `number` | Number of distinct countries with a listed site. |
| 52 | `countries` | `string` | Countries with a listed site (semicolon-joined). |
| 53 | `has_us_site` | `boolean` | true when at least one site is in the United States. |
| 54 | `facility_count` | `number` | Number of distinct facility names. |
| 55 | `has_dmc` | `boolean` | true when a data monitoring committee is declared. |
| 56 | `is_fda_regulated_drug` | `boolean` | true when the study involves an FDA-regulated drug. |
| 57 | `is_fda_regulated_device` | `boolean` | true when the study involves an FDA-regulated device. |
| 58 | `ipd_sharing` | `string` | Individual participant data sharing statement (Yes/No/Undecided). |
| 59 | `reference_count` | `number` | Number of publication references attached to the record. |
| 60 | `brief_summary_length` | `number` | Characters in the brief summary. |
| 61 | `detailed_description_length` | `number` | Characters in the detailed description. |
| 62 | `is_interventional` | `boolean` | true for interventional studies. |
| 63 | `is_observational` | `boolean` | true for observational studies. |
| 64 | `is_industry_sponsored` | `boolean` | true when the lead sponsor class is Industry. |
| 65 | `is_academic_sponsored` | `boolean` | true when the lead sponsor is academic/university. |
| 66 | `is_network_sponsored` | `boolean` | true when the lead sponsor is a clinical network. |
| 67 | `start_year` | `number` | Calendar year of the start date. |
| 68 | `planned_duration_days` | `number` | Completion date minus start date, in days. |
| 69 | `days_since_last_update` | `number` | Days between the last update and the snapshot date (2026-11-21). |
| 70 | `days_to_first_post` | `number` | Days between study start and first registration posting. |
| 71 | `min_age_years` | `number` | Minimum age converted to years (months/weeks/days divided accordingly). |
| 72 | `max_age_years` | `number` | Maximum age converted to years. |
| 73 | `is_pediatric` | `boolean` | true when the minimum age is below 18. |
| 74 | `is_older_adult` | `boolean` | true when the maximum age is 65 or below. |
| 75 | `is_randomized` | `boolean` | true when allocation is Randomized. |
| 76 | `is_blinded` | `boolean` | true when any masking is declared. |
| 77 | `enrollment_band` | `string` | Enrollment size band from <50 to 5,000+. |
| 78 | `title_length` | `number` | Characters in the brief title. |
| 79 | `condition_count_clean` | `number` | Number of registered conditions (recounted during flattening). |
| 80 | `is_oncology` | `boolean` | true when a condition mentions cancer, neoplasm or tumour. |
| 81 | `accepts_healthy_volunteers` | `boolean` | true when healthy volunteers are accepted. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
