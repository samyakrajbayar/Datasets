# U.S. Nursing Homes — Ownership, Capacity and CMS Ratings

**Subtitle:** 14,686 certified nursing homes with star ratings, ownership, chains, beds and occupancy.

---

## 📖 Description

### 14,686 U.S. nursing homes with quality ratings

The CMS Provider Data Catalog publishes every Medicare- and Medicaid-certified nursing home with its
star ratings, ownership, capacity and inspection flags. This dataset contains **14,686 providers** and
**117 parameters**.

- **Provider** — CCN, name, address, county, state, ZIP, phone, provider type and legal business name.
- **Ownership** — ownership type, chain name and id.
- **Capacity** — certified beds, average daily residents and their footnotes.
- **Quality** — overall, health-inspection, quality-measure, staffing, long-stay and short-stay star
  ratings, plus CMS abuse and special-focus flags where supplied.
- **Derived** — ownership group, for-profit/non-profit/government flags, chain flag, occupancy rate,
  bed and resident bands, rating mean and high/low-rated flags, tenure years and state bed share.

The file covers **1,567,009 certified beds**, **10,227 chain-affiliated homes** and
**14,560 homes with at least one star rating** — a complete market map for elder-care research.

## 🧾 Columns (117)

`cms_certification_number_ccn`, `provider_name`, `provider_address`, `citytown`, `state`, `zip_code`, `telephone_number`, `provider_ssa_county_code`, `countyparish`, `urban`, `ownership_type`, `number_of_certified_beds`, `average_number_of_residents_per_day`, `average_number_of_residents_per_day_footnote`, `provider_type`, `provider_resides_in_hospital`, `legal_business_name`, `date_first_approved_to_provide_medicare_and_medicaid_services`, `chain_name`, `chain_id`, `number_of_facilities_in_chain`, `chain_average_overall_5star_rating`, `chain_average_health_inspection_rating`, `chain_average_staffing_rating`, `chain_average_qm_rating`, `continuing_care_retirement_community`, `special_focus_status`, `abuse_icon`, `high_performing_icon`, `most_recent_health_inspection_more_than_2_years_ago`, `provider_changed_ownership_in_last_12_months`, `with_a_resident_and_family_council`, `automatic_sprinkler_systems_in_all_required_areas`, `overall_rating`, `overall_rating_footnote`, `health_inspection_rating`, `health_inspection_rating_footnote`, `qm_rating`, `qm_rating_footnote`, `longstay_qm_rating`, `longstay_qm_rating_footnote`, `shortstay_qm_rating`, `shortstay_qm_rating_footnote`, `staffing_rating`, `staffing_rating_footnote`, `reported_staffing_footnote`, `physical_therapist_staffing_footnote`, `reported_nurse_aide_staffing_hours_per_resident_per_day`, `reported_lpn_staffing_hours_per_resident_per_day`, `reported_rn_staffing_hours_per_resident_per_day`, `reported_licensed_staffing_hours_per_resident_per_day`, `reported_total_nurse_staffing_hours_per_resident_per_day`, `total_number_of_nurse_staff_hours_per_resident_per_day_on_t_4a14`, `registered_nurse_hours_per_resident_per_day_on_the_weekend`, `reported_physical_therapist_staffing_hours_per_resident_per_day`, `total_nursing_staff_turnover`, `total_nursing_staff_turnover_footnote`, `registered_nurse_turnover`, `registered_nurse_turnover_footnote`, `number_of_administrators_who_have_left_the_nursing_home`, `administrator_turnover_footnote`, `nursing_casemix_index`, `nursing_casemix_index_ratio`, `casemix_nurse_aide_staffing_hours_per_resident_per_day`, `casemix_lpn_staffing_hours_per_resident_per_day`, `casemix_rn_staffing_hours_per_resident_per_day`, `casemix_total_nurse_staffing_hours_per_resident_per_day`, `casemix_weekend_total_nurse_staffing_hours_per_resident_per_day`, `adjusted_nurse_aide_staffing_hours_per_resident_per_day`, `adjusted_lpn_staffing_hours_per_resident_per_day`, `adjusted_rn_staffing_hours_per_resident_per_day`, `adjusted_total_nurse_staffing_hours_per_resident_per_day`, `adjusted_weekend_total_nurse_staffing_hours_per_resident_per_day`, `rating_cycle_1_standard_survey_health_date`, `rating_cycle_1_standard_survey_footnote`, `rating_cycle_1_total_number_of_health_deficiencies`, `rating_cycle_1_number_of_standard_health_deficiencies`, `rating_cycle_1_number_of_complaint_health_deficiencies`, `rating_cycle_1_health_deficiency_score`, `rating_cycle_1_number_of_health_revisits`, `rating_cycle_1_health_revisit_score`, `rating_cycle_1_total_health_score`, `rating_cycle_2_standard_health_survey_date`, `rating_cycle_2_standard_survey_footnote`, `rating_cycle_23_total_number_of_health_deficiencies`, `rating_cycle_2_number_of_standard_health_deficiencies`, `rating_cycle_23_number_of_complaint_health_deficiencies`, `rating_cycle_23_health_deficiency_score`, `rating_cycle_23_number_of_health_revisits`, `rating_cycle_23_health_revisit_score`, `rating_cycle_23_total_health_score`, `total_weighted_health_survey_score`, `number_of_citations_from_infection_control_inspections`, `number_of_fines`, `total_amount_of_fines_in_dollars`, `number_of_payment_denials`, `total_number_of_penalties`, `location`, `latitude`, `longitude`, `geocoding_footnote`, `processing_date`, `ownership_group`, `is_for_profit`, `is_nonprofit`, `is_government`, `is_chain`, `occupancy_rate`, `bed_band`, `resident_band`, `has_rating`, `rating_mean`, `is_high_rated`, `is_low_rated`, `has_abuse_flag`, `tenure_years`, `state_rank_beds`

## 💡 Ideas for using this data

1. **Quality vs ownership** — star ratings by for-profit/non-profit/government.
2. **Chain effects** — do chain homes rate differently?
3. **Occupancy** — census vs beds and its relation to ratings.
4. **Geography** — state-level quality and capacity comparisons.
5. **Staffing** — staffing stars against quality measures.
6. **Abuse flags** — prevalence and correlates.
7. **Market concentration** — chain share by state.
8. **Prediction** — model the overall rating from structural features.

## 📁 Files

| File | What it is |
|---|---|
| `nursing_homes.csv` | 14,686 providers x 117 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`healthcare`, `nursing-homes`, `cms`, `elder-care`, `quality`, `united-states`

## 🔗 Provenance

- **Source:** **CMS Provider Data Catalog**, dataset `4pq5-n9py`
  ("Provider Information"), queried through the datastore API.
- **Processing:** all providers paged 1,000 at a time; ownership groups, occupancy, rating summaries
  and bands derived; state bed shares computed across the file.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Quarterly.** CMS refreshes provider information and ratings each quarter.

## ⚠️ Caveats

- Ratings are CMS composites and should be read with their footnotes.
- Resident census is a daily average, not a point-in-time count.
- Some fields (abuse icon, special-focus status) are only populated for flagged homes.
- Ownership classifications are simplified into three groups for analysis.
- Facilities change ownership and ratings quarterly; this is a snapshot.

## 📜 Licence

U.S. Government work (CMS), public domain.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
