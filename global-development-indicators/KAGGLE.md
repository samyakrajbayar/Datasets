# Global Development Indicators 1960-2025

**Subtitle:** 14,322 country-years across 55 World Bank development indicators

**Tags:** `tabular`, `economics`, `countries`

**Dataset File:** `development_indicators.csv` (14,322 rows, 79 columns, 5.9 MB)

**Provenance & Source:** World Bank World Development Indicators (data.worldbank.org)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### 66 years of development, 55 indicators, one panel

The World Bank's World Development Indicators are the standard cross-country macro dataset. This
extract pivots **55 indicators** into a wide country-year panel: **14,322 rows** for
**217 countries from 1960 to 2025**, with **79 parameters**.

- **Economy** — GDP (current and constant), GDP per capita, growth, manufacturing/agriculture/services
  shares, trade, FDI, government debt, tax revenue and expenditure.
- **People** — population, growth, age structure, density, urban share, birth/death rates, fertility,
  life expectancy by sex and infant mortality.
- **Health** — health spending (% GDP and per capita), beds, physicians, measles immunisation, maternal
  mortality, TB and HIV incidence.
- **Education** — primary/secondary/tertiary enrolment, education spending and adult literacy.
- **Environment and infrastructure** — forest and agricultural land, cereal yield, freshwater
  withdrawal, electricity access, energy use per capita, renewable share, internet and mobile uptake.
- **Inequality and labour** — Gini, poverty headcount, unemployment, participation and employment ratio.
- **Derived** — log GDP, urban/rural population, dependency ratios, life-expectancy gap, access gaps,
  health spend per person-day, income-group flags and per-row completeness.

Missing values are left blank rather than imputed, so the completeness columns show exactly how much
of each country-year is observed.

## 🧾 Columns (79)

`iso3`, `country_name`, `country_iso2`, `year`, `region`, `income_level`, `lending_type`, `capital_city`, `latitude`, `longitude`, `population_total`, `population_growth_pct`, `population_0_14_pct`, `population_15_64_pct`, `population_65plus_pct`, `life_expectancy_years`, `life_expectancy_female_years`, `life_expectancy_male_years`, `infant_mortality_per_1000`, `fertility_rate`, `birth_rate_per_1000`, `death_rate_per_1000`, `urban_population_pct`, `population_density_per_km2`, `gdp_current_usd`, `gdp_per_capita_usd`, `gdp_growth_pct`, `gdp_constant_2015_usd`, `manufacturing_value_added_pct`, `agriculture_value_added_pct`, `services_value_added_pct`, `exports_gdp_pct`, `imports_gdp_pct`, `trade_gdp_pct`, `fdi_inflow_usd`, `central_govt_debt_pct`, `tax_revenue_pct`, `govt_expense_pct`, `gini_index`, `poverty_2_15_per_day_pct`, `unemployment_pct`, `labour_force_participation_pct`, `employment_ratio_pct`, `primary_enrolment_pct`, `secondary_enrolment_pct`, `tertiary_enrolment_pct`, `education_spend_pct`, `literacy_rate_pct`, `health_spend_pct`, `health_spend_per_capita_usd`, `hospital_beds_per_1000`, `physicians_per_1000`, `measles_immunisation_pct`, `maternal_mortality_per_100k`, `tuberculosis_per_100k`, `hiv_incidence_per_1000`, `forest_area_pct`, `agricultural_land_pct`, `cereal_yield_kg_per_ha`, `freshwater_withdrawal_pct`, `electricity_access_pct`, `energy_use_per_capita_kg`, `renewable_energy_pct`, `internet_users_pct`, `mobile_subscriptions_per_100`, `urban_population`, `rural_population_pct`, `log10_gdp`, `log10_gdp_per_capita`, `youth_dependency_ratio`, `old_age_dependency_ratio`, `life_expectancy_gap_years`, `electricity_access_gap_pct`, `internet_nonusers_pct`, `health_spend_per_person_day_usd`, `is_high_income`, `is_low_income`, `indicators_present`, `indicator_completeness_pct`

## 💡 Ideas for using this data

1. **Development trajectories** — plot GDP per capita vs life expectancy by decade, coloured by region.
2. **Convergence** — do poorer countries grow faster? Regress growth on initial income.
3. **Structural transformation** — manufacturing share vs income, and where countries peak.
4. **Health spending efficiency** — life expectancy per health dollar by income group.
5. **Education and growth** — enrolment in 1990 vs GDP per capita in 2020.
6. **Missing data** — visualise completeness by indicator and region; a ready-made missingness study.
7. **Gender gaps** — female-male life expectancy and literacy gaps over time.
8. **Resource dependence** — forest loss vs agricultural expansion and cereal yield.
9. **Digital divide** — internet and mobile adoption curves by income group.
10. **Panel forecasting** — build a country-year model with lagged features.

## 📁 Files

| File | What it is |
|---|---|
| `development_indicators.csv` | 14,322 country-years x 79 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`world-bank`, `development`, `economics`, `health`, `education`, `panel-data`, `countries`, `sustainability`

## 🔗 Provenance

- **Source:** **World Bank World Development Indicators** API v2,
  `https://api.worldbank.org/v2/country/all/indicator/<CODE>?format=json&per_page=20000&date=1960:2025`.
- **Indicator set:** the 55 codes listed in `scripts/34_development.py`, chosen across economy, health,
  education, environment, infrastructure and inequality.
- **Country filter:** the World Bank country endpoint was used to drop regional and income aggregates
  (`region.id = NA`), leaving sovereign countries and territories.
- **Processing:** long indicator series pivoted to one row per country-year; derived ratios and flags
  computed only where the inputs exist.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Annual (with frequent revisions).** The World Bank updates WDI several times a year.

## ⚠️ Caveats

- Coverage is very uneven: 1960s rows are sparse, and some indicators start in the 1990s or 2000s.
- World Bank estimates are modelled and revised; values can change between vintages.
- GDP is in current US$ unless the column says constant; cross-year comparisons need the constant series.
- Aggregate regions were removed, but territories (e.g. small islands) remain.
- Poverty and Gini series have long gaps and changing survey methodologies.
- Blank cells mean 'not reported', not zero.
- The panel stops at 2025 because 2026 reporting is incomplete.

## 📜 Licence

World Bank Open Data is licensed CC BY 4.0 — attribution required.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `iso3` | `string` | World Bank / ISO 3166-1 alpha-3 country code. |
| 2 | `country_name` | `string` | Country name as used by the World Bank. |
| 3 | `country_iso2` | `string` | ISO 3166-1 alpha-2 code. |
| 4 | `year` | `number` | Calendar year of the observation. |
| 5 | `region` | `string` | World Bank region. |
| 6 | `income_level` | `string` | World Bank income group (High, Upper middle, Lower middle, Low). |
| 7 | `lending_type` | `string` | World Bank lending category. |
| 8 | `capital_city` | `string` | Capital city. |
| 9 | `latitude` | `number` | Country centroid latitude. |
| 10 | `longitude` | `number` | Country centroid longitude. |
| 11 | `population_total` | `number` | Total population. |
| 12 | `population_growth_pct` | `number` | Annual population growth rate (%). |
| 13 | `population_0_14_pct` | `number` | Population aged 0-14 (% of total). |
| 14 | `population_15_64_pct` | `number` | Population aged 15-64 (% of total). |
| 15 | `population_65plus_pct` | `number` | Population aged 65+ (% of total). |
| 16 | `life_expectancy_years` | `number` | Life expectancy at birth, total (years). |
| 17 | `life_expectancy_female_years` | `number` | Life expectancy at birth, female (years). |
| 18 | `life_expectancy_male_years` | `number` | Life expectancy at birth, male (years). |
| 19 | `infant_mortality_per_1000` | `number` | Infant mortality per 1,000 live births. |
| 20 | `fertility_rate` | `number` | Fertility rate, total births per woman. |
| 21 | `birth_rate_per_1000` | `number` | Crude birth rate per 1,000 people. |
| 22 | `death_rate_per_1000` | `number` | Crude death rate per 1,000 people. |
| 23 | `urban_population_pct` | `number` | Urban population (% of total). |
| 24 | `population_density_per_km2` | `number` | Population density (people per sq. km). |
| 25 | `gdp_current_usd` | `number` | GDP at current prices (US$). |
| 26 | `gdp_per_capita_usd` | `number` | GDP per capita (current US$). |
| 27 | `gdp_growth_pct` | `number` | GDP growth (annual %). |
| 28 | `gdp_constant_2015_usd` | `number` | GDP at constant 2015 prices (US$). |
| 29 | `manufacturing_value_added_pct` | `number` | Manufacturing value added (% of GDP). |
| 30 | `agriculture_value_added_pct` | `number` | Agriculture value added (% of GDP). |
| 31 | `services_value_added_pct` | `number` | Services value added (% of GDP). |
| 32 | `exports_gdp_pct` | `number` | Exports of goods and services (% of GDP). |
| 33 | `imports_gdp_pct` | `number` | Imports of goods and services (% of GDP). |
| 34 | `trade_gdp_pct` | `number` | Trade (% of GDP). |
| 35 | `fdi_inflow_usd` | `number` | Foreign direct investment, net inflows (US$). |
| 36 | `central_govt_debt_pct` | `number` | Central government debt (% of GDP). |
| 37 | `tax_revenue_pct` | `number` | Tax revenue (% of GDP). |
| 38 | `govt_expense_pct` | `number` | Expense (% of GDP). |
| 39 | `gini_index` | `number` | Gini index (0-100). |
| 40 | `poverty_2_15_per_day_pct` | `number` | Poverty headcount at $2.15/day (2017 PPP, %). |
| 41 | `unemployment_pct` | `number` | Unemployment, total (% of labour force). |
| 42 | `labour_force_participation_pct` | `number` | Labour force participation rate (%). |
| 43 | `employment_ratio_pct` | `number` | Employment to population ratio (%). |
| 44 | `primary_enrolment_pct` | `number` | School enrolment, primary (% gross). |
| 45 | `secondary_enrolment_pct` | `number` | School enrolment, secondary (% gross). |
| 46 | `tertiary_enrolment_pct` | `number` | School enrolment, tertiary (% gross). |
| 47 | `education_spend_pct` | `number` | Government expenditure on education (% of GDP). |
| 48 | `literacy_rate_pct` | `number` | Adult literacy rate (% of people aged 15+). |
| 49 | `health_spend_pct` | `number` | Current health expenditure (% of GDP). |
| 50 | `health_spend_per_capita_usd` | `number` | Current health expenditure per capita (US$). |
| 51 | `hospital_beds_per_1000` | `number` | Hospital beds per 1,000 people. |
| 52 | `physicians_per_1000` | `number` | Physicians per 1,000 people. |
| 53 | `measles_immunisation_pct` | `number` | Immunisation, measles (% of children 12-23 months). |
| 54 | `maternal_mortality_per_100k` | `number` | Maternal mortality ratio per 100,000 live births. |
| 55 | `tuberculosis_per_100k` | `number` | Incidence of tuberculosis per 100,000 people. |
| 56 | `hiv_incidence_per_1000` | `number` | HIV incidence per 1,000 uninfected population. |
| 57 | `forest_area_pct` | `number` | Forest area (% of land area). |
| 58 | `agricultural_land_pct` | `number` | Agricultural land (% of land area). |
| 59 | `cereal_yield_kg_per_ha` | `number` | Cereal yield (kg per hectare). |
| 60 | `freshwater_withdrawal_pct` | `number` | Annual freshwater withdrawals (% of internal resources). |
| 61 | `electricity_access_pct` | `number` | Access to electricity (% of population). |
| 62 | `energy_use_per_capita_kg` | `number` | Energy use per capita (kg of oil equivalent). |
| 63 | `renewable_energy_pct` | `number` | Renewable energy consumption (% of final energy). |
| 64 | `internet_users_pct` | `number` | Individuals using the Internet (% of population). |
| 65 | `mobile_subscriptions_per_100` | `number` | Mobile cellular subscriptions per 100 people. |
| 66 | `urban_population` | `number` | Urban population (population x urban share). |
| 67 | `rural_population_pct` | `number` | 100 - urban population share. |
| 68 | `log10_gdp` | `number` | log10 of GDP in current US$. |
| 69 | `log10_gdp_per_capita` | `number` | log10 of GDP per capita. |
| 70 | `youth_dependency_ratio` | `number` | Population 0-14 / population 15-64 x 100. |
| 71 | `old_age_dependency_ratio` | `number` | Population 65+ / population 15-64 x 100. |
| 72 | `life_expectancy_gap_years` | `number` | Female minus male life expectancy. |
| 73 | `electricity_access_gap_pct` | `number` | 100 - electricity access share. |
| 74 | `internet_nonusers_pct` | `number` | 100 - internet user share. |
| 75 | `health_spend_per_person_day_usd` | `number` | Health spend per capita divided by 365. |
| 76 | `is_high_income` | `boolean` | true for World Bank high-income countries. |
| 77 | `is_low_income` | `boolean` | true for World Bank low-income countries. |
| 78 | `indicators_present` | `number` | How many of the 55 indicators are non-null for this row. |
| 79 | `indicator_completeness_pct` | `number` | indicators_present as a percentage of 55. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
