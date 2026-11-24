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
pretty_name: "Countries of the World 2026 & Macro Indicators"
tags:
- tabular
- economics
- geography
---

# Countries of the World 2026 — Geography, Politics and 18 Macro Indicators

**Subtitle:** 250 countries and territories with borders, currencies, languages, area, and the latest World Bank development indicators joined in one analysis-ready file.

---

## 📖 Description

Most country datasets give you names, capitals and a population figure. This one gives you **52 columns** covering physical geography, political structure and socio-economic development, already joined — no API keys, no merge steps.

**Geography & identity (33 columns).** ISO alpha-2/alpha-3/numeric codes, IOC code, common and official names, sovereignty status, UN membership and UN regional group, continent and sub-region, capital city with coordinates, total area in km², landlocked flag, the full list of bordering countries plus a border count, centroid coordinates, flag emoji, top-level domain, international dialling prefix and suffixes, currencies (codes, names, symbols), official languages and a language count, English demonyms, and alternative-spelling counts.

**Development indicators (18 columns, World Bank).** Population, population growth, GDP, GDP per capita, GDP growth, life expectancy, fertility rate, urban population share, internet users, mobile subscriptions per 100 people, adult literacy, unemployment, inflation, CO₂ emissions per capita, forest cover, infant mortality, health spending and education spending. Each row carries `indicator_year`, the most recent year for which that country reported.

Derived features worth noting: `n_borders` (a simple connectivity measure), `language_count` (linguistic diversity proxy), and the ratio fields you can build between the macro columns.

## 🧾 Column groups

- **Codes**: `cca2`, `cca3`, `ccn3`, `cioc`
- **Names**: `name_common`, `name_official`, `demonym_male`, `demonym_female`, `alt_spellings_count`
- **Politics**: `independent`, `un_member`, `un_regional_group`, `status`
- **Geography**: `region`, `subregion`, `capital`, `capital_lat`, `capital_lng`, `area_km2`, `landlocked`, `borders`, `n_borders`, `lat`, `lng`
- **Culture/infra**: `languages`, `language_count`, `currency_codes`, `currency_names`, `currency_symbols`, `flag_emoji`, `tld`, `idd_root`, `idd_suffixes`
- **Economy & society**: `population`, `population_growth_pct`, `gdp_usd`, `gdp_per_capita_usd`, `gdp_growth_pct`, `inflation_pct`, `unemployment_pct`, `life_expectancy_years`, `fertility_rate`, `infant_mortality_per_1000`, `urban_population_pct`, `internet_users_pct`, `mobile_subs_per_100`, `literacy_rate_pct`, `co2_per_capita_tonnes`, `forest_area_pct`, `health_spend_pct_gdp`, `education_spend_pct_gdp`, `indicator_year`

A machine-readable dictionary is included as `data_dictionary.csv`.

## 💡 Ideas for using this data

1. **Development clustering** — k-means on the normalised indicators to recover income/development tiers, then map them.
2. **Regression** — what explains life expectancy or GDP per capita: internet penetration, urbanisation, health spend, forest cover?
3. **Landlocked penalty** — compare GDP per capita and inflation for landlocked vs coastal states.
4. **Border network analysis** — build a country adjacency graph from `borders` and compute centrality.
5. **Choropleth dashboard** — join `cca3` to any ISO-3 map (Plotly, GeoPandas, Tableau).
6. **Language diversity vs development** — does `language_count` correlate with any socio-economic indicator?

## ⚠️ Caveats

- 250 rows include dependencies, territories and disputed entities, not just sovereign states. Filter on `independent` / `un_member` for country-level work.
- **35 entities have no population value** (mostly small dependencies the World Bank does not report separately); treat their blanks as missing, not zero.
- Indicator years differ by country (see `indicator_year`); this is a "latest available" snapshot, not a single-year panel.
- Areas are total area (land + inland water) in km².

## 🔗 Provenance & licence

- Country attributes: `mledoze/countries` open dataset (ODbL), the upstream source of the REST Countries project.
- Indicators: World Bank Open Data API (CC BY 4.0).
- Snapshot: November 2026. 250 rows × 52 columns.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
