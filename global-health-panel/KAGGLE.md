# Global Health Panel 2000-2025

**Subtitle:** WHO health panel across countries: mortality, disease, spending and access

**Tags:** `health`, `public-health`, `who`, `global`, `epidemiology`, `demography`, `economics`, `time-series`, `tabular`, `social-science`

**Dataset File:** `who_health_panel.csv` (5,914 rows, 41 columns, 1.4 MB)

---

## 📖 Description

### 25 years of global health, one row per country per year

A wide panel assembled from the **WHO Global Health Observatory** — the World Health Organization's
open data warehouse — covering **230 countries** from **2000 to 2025** in
**5,914 country-year rows** with **41 parameters**.

Each row carries 21 health indicators plus national context:
- **Mortality and longevity** — life expectancy, healthy life expectancy, under-5, neonatal, infant and
  maternal mortality.
- **Disease burden** — age-standardised obesity and diabetes prevalence, tuberculosis incidence, suicide
  rate and road-traffic death rate.
- **Health system** — medical doctors, nursing and midwifery personnel and hospital beds per 10,000
  people, current health expenditure as a share of GDP, and DTP3 and measles immunisation coverage.
- **Access** — safely managed sanitation, basic drinking-water coverage, skilled birth attendance and
  alcohol consumption.
- **Context** — country name, ISO-3 code, continent, UN region/sub-region, WHO region, population and GDP
  per capita.
- **Derived** — years lived in poor health (life expectancy minus healthy life expectancy), health spend
  per person, per-1,000 staffing and bed densities, indicator coverage, decade, and life-expectancy,
  child-mortality and health-spending bands.

Not every country reports every indicator in every year — the coverage columns make that explicit, so
missingness can be modelled rather than silently dropped.

## 🧾 Columns (41)

`country_code`, `country_name`, `year`, `continent`, `region`, `subregion`, `who_region`, `population`, `gdp_per_capita_usd`, `life_expectancy`, `healthy_life_expectancy`, `under5_mortality_per_1000`, `neonatal_mortality_per_1000`, `infant_mortality_per_1000`, `maternal_mortality_per_100k`, `obesity_pct`, `diabetes_pct`, `doctors_per_10k`, `nurses_per_10k`, `hospital_beds_per_10k`, `health_spend_pct_gdp`, `suicide_rate_per_100k`, `road_death_rate_per_100k`, `tb_incidence_per_100k`, `dtp3_coverage_pct`, `measles_coverage_pct`, `sanitation_pct`, `drinking_water_pct`, `alcohol_litres_per_capita`, `skilled_birth_pct`, `health_adjusted_years_lost`, `health_spend_per_capita_usd`, `doctors_per_1000`, `nurses_per_1000`, `hospital_beds_per_1000`, `n_indicators_reported`, `indicator_coverage_pct`, `decade`, `life_expectancy_band`, `child_mortality_class`, `health_spend_class`

## 💡 Ideas for using this data

1. **Life expectancy vs health spending** — the classic curve; identify outliers above and below it.
2. **Child mortality decline** — animated or small-multiple time series by region since 2000.
3. **Years lived in poor health** — `health_adjusted_years_lost` by country and income level.
4. **Workforce density** — doctors and nurses per 1,000 versus under-5 mortality.
5. **Panel regression** — fixed-effects model of life expectancy on spending, staffing and sanitation.
6. **Missingness** — which indicators and countries are sparse, and does that bias global averages?
7. **Clustering** — group countries into health-system archetypes from the indicator vector.
8. **Forecasting** — predict 2030 life expectancy per country with a per-country time-series model.
9. **Inequality** — Gini or ratio of top-to-bottom decile life expectancy across countries per year.

## 📁 Files

| File | What it is |
|---|---|
| `who_health_panel.csv` | 5,914 country-year rows x 41 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: life expectancy, spending, workforce, missingness. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`health`, `public-health`, `who`, `global`, `epidemiology`, `demography`, `economics`, `time-series`, `tabular`, `social-science`

## 🔗 Provenance

- **Source:** **WHO Global Health Observatory OData API**, `https://ghoapi.azureedge.net/api`.
- **Indicators:** 21 codes selected automatically from the WHO indicator catalogue by name
  matching, then fetched with `$filter=TimeDim ge 2000 and SpatialDimType eq 'COUNTRY'`.
  The exact code used for each column is listed in the collection log below.
- **Indicator codes used:** `WHOSIS_000001`, `WHOSIS_000002`, `MDG_0000000007`, `WHOSIS_000003`, `MDG_0000000001`, `MDG_0000000026`, `NCD_BMI_30A`, `NCD_DIABETES_TREATMENT_AGESTD`, `HWF_0005`, `HWF_0007`, `WHS6_102`, `GHED_CHEGDP_SHA2011`, `MH_12`, `RS_198`, `MDG_0000000020`, `WHS4_100`, `MCV2`, `WSH_SANITATION_SAFELY_MANAGED`, `WSH_WATER_BASIC`, `SA_0000001746`, `MDG_0000000025`.
- **Transformation:** long indicator rows pivoted into a wide country-year panel; sex-split indicators
  resolved to both-sexes values; derived ratios and bands computed.
- **Context join:** continent, region, sub-region, population and GDP per capita from the World
  Bank-backed `countries-of-the-world` table in this repository.
- **Snapshot date:** 20 November 2026.

## 🔄 Update frequency

**Annual.** WHO refreshes the Global Health Observatory roughly once a year (typically with a one-to-two-year lag). Re-run `scripts/18_who_health.py` to extend the panel.

## ⚠️ Caveats

- WHO estimates are modelled for many countries and years; they are not raw registry counts.
- Coverage is uneven — health-workforce and expenditure series are often missing before 2005.
- Some indicators are age-standardised and others are crude rates; the data dictionary notes which.
- WHO revises historical estimates between releases, so values can differ from older publications.
- Indicators whose WHO name did not match the keyword list were left out; see the log for the exact selection.
- Country codes follow WHO/UN usage, so a few territories are absent from the World Bank join.

## 📜 Licence

Creative Commons Attribution-NonCommercial-ShareAlike 3.0 IGO (CC BY-NC-SA 3.0 IGO) — World Health Organization. Attribution to WHO is required; commercial use is restricted by the upstream licence.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `country_code` | `string` | ISO-3166 alpha-3 country code. |
| 2 | `country_name` | `string` | Country name from the WHO country dimension. |
| 3 | `year` | `number` | Year of the observation. |
| 4 | `continent` | `string` | Continent of the country. |
| 5 | `region` | `string` | UN macro-region of the country. |
| 6 | `subregion` | `string` | UN sub-region of the country. |
| 7 | `who_region` | `string` | WHO administrative region code (AFR, AMR, EMR, EUR, SEAR, WPR). |
| 8 | `population` | `number` | Country population (World Bank). |
| 9 | `gdp_per_capita_usd` | `number` | Country GDP per capita (World Bank). |
| 10 | `life_expectancy` | `number` | Life expectancy at birth, both sexes (years). |
| 11 | `healthy_life_expectancy` | `number` | Healthy life expectancy at birth, both sexes (years). |
| 12 | `under5_mortality_per_1000` | `number` | Probability of dying before age 5, per 1,000 live births. |
| 13 | `neonatal_mortality_per_1000` | `number` | Neonatal deaths per 1,000 live births. |
| 14 | `infant_mortality_per_1000` | `number` | Infant deaths per 1,000 live births. |
| 15 | `maternal_mortality_per_100k` | `number` | Maternal deaths per 100,000 live births. |
| 16 | `obesity_pct` | `number` | Age-standardised prevalence of obesity among adults (%). |
| 17 | `diabetes_pct` | `number` | Age-standardised prevalence of diabetes among adults (%). |
| 18 | `doctors_per_10k` | `number` | Medical doctors per 10,000 population. |
| 19 | `nurses_per_10k` | `number` | Nursing and midwifery personnel per 10,000 population. |
| 20 | `hospital_beds_per_10k` | `number` | Hospital beds per 10,000 population. |
| 21 | `health_spend_pct_gdp` | `number` | Current health expenditure as a share of GDP (%). |
| 22 | `suicide_rate_per_100k` | `number` | Suicide mortality rate per 100,000 population. |
| 23 | `road_death_rate_per_100k` | `number` | Estimated road traffic death rate per 100,000 population. |
| 24 | `tb_incidence_per_100k` | `number` | Tuberculosis incidence per 100,000 population. |
| 25 | `dtp3_coverage_pct` | `number` | DTP3 immunisation coverage among 1-year-olds (%). |
| 26 | `measles_coverage_pct` | `number` | Measles-containing vaccine first-dose coverage (%). |
| 27 | `sanitation_pct` | `number` | Population using safely managed sanitation services (%). |
| 28 | `drinking_water_pct` | `number` | Population using at least basic drinking-water services (%). |
| 29 | `alcohol_litres_per_capita` | `number` | Total alcohol consumption per capita, litres of pure alcohol. |
| 30 | `skilled_birth_pct` | `number` | Births attended by skilled health personnel (%). |
| 31 | `health_adjusted_years_lost` | `number` | Life expectancy minus healthy life expectancy: years lived in poor health. |
| 32 | `health_spend_per_capita_usd` | `number` | Health expenditure per person implied by spend share of GDP and GDP per capita. |
| 33 | `doctors_per_1000` | `number` | Medical doctors per 1,000 population. |
| 34 | `nurses_per_1000` | `number` | Nursing and midwifery personnel per 1,000 population. |
| 35 | `hospital_beds_per_1000` | `number` | Hospital beds per 1,000 population. |
| 36 | `n_indicators_reported` | `number` | How many of the tracked indicators have a value in this country-year. |
| 37 | `indicator_coverage_pct` | `number` | Share of the tracked indicators reported, in percent. |
| 38 | `decade` | `string` | Decade of the observation year. |
| 39 | `life_expectancy_band` | `string` | Life-expectancy band from <55 to 80+ years. |
| 40 | `child_mortality_class` | `string` | Under-5 mortality band from Very low to Very high. |
| 41 | `health_spend_class` | `string` | Health-spending band as a share of GDP. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
