# Global Power Plant Inventory

**Subtitle:** Worldwide power plants with fuel type, capacity, generation history & location

**Tags:** `energy`, `climate`, `environment`, `geospatial`, `electricity`, `renewable-energy`, `sustainability`, `infrastructure`, `tabular`, `economics`

**Dataset File:** `power_plants.csv` (34,936 rows, 52 columns, 15.3 MB)

---

## 📖 Description

### Every large power plant on Earth, mapped and characterised

The WRI Global Power Plant Database is the most complete open inventory of the world's power stations.
This snapshot contains **34,936 plants** in **167 countries** with
**52 parameters** each, enriched with country-level context and derived engineering features.

Each row covers:
- **Identity and location** — plant name, WRI id, country code and name, latitude and longitude,
  geolocation provenance and the WEPP cross-reference.
- **Technology** — primary fuel plus up to three secondary fuels, a coarse fuel group (Renewable /
  Fossil / Nuclear / Storage / Other) and a renewable flag. **24,794 plants (71.0%)**
  are renewable-primary.
- **Capacity** — nameplate capacity in MW, the year that capacity refers to, a capacity band, the plant's
  share of its country's and the world's capacity in this file, and capacity per person in its country.
- **Generation** — reported net generation for 2013–2019, an observed mean capacity factor, the latest
  reported year and a flag for whether the plant reports generation at all.
- **Ownership and provenance** — owner, data source, record URL, commissioning year and plant age.
- **Country context** — continent, UN region and sub-region, GDP per capita and a latitude/climate band.

The file mixes capacity-complete records with generation-sparse ones, which is exactly the kind of
real-world incompleteness that makes for good data-cleaning and imputation practice.

## 🧾 Columns (52)

`country`, `country_long`, `name`, `gppd_idnr`, `capacity_mw`, `latitude`, `longitude`, `primary_fuel`, `other_fuel1`, `other_fuel2`, `other_fuel3`, `commissioning_year`, `owner`, `source`, `url`, `geolocation_source`, `wepp_id`, `year_of_capacity_data`, `generation_gwh_2013`, `generation_gwh_2014`, `generation_gwh_2015`, `generation_gwh_2016`, `generation_gwh_2017`, `generation_gwh_2018`, `generation_gwh_2019`, `generation_data_source`, `estimated_generation_gwh_2013`, `estimated_generation_gwh_2014`, `estimated_generation_gwh_2015`, `estimated_generation_gwh_2016`, `estimated_generation_gwh_2017`, `estimated_generation_note_2013`, `estimated_generation_note_2014`, `estimated_generation_note_2015`, `estimated_generation_note_2016`, `estimated_generation_note_2017`, `continent`, `region`, `subregion`, `fuel_group`, `is_renewable`, `plant_age_years`, `capacity_class`, `capacity_share_country_pct`, `capacity_share_global_pct`, `capacity_per_capita_w`, `mean_capacity_factor_pct`, `latest_generation_gwh`, `latest_generation_year`, `has_generation_data`, `gdp_per_capita_usd`, `grid_zone_class`

## 💡 Ideas for using this data

1. **Energy transition map** — capacity by fuel group and country; which grids are already low-carbon?
2. **Plant ageing** — age distribution by fuel; how old is the world's coal fleet versus its solar fleet?
3. **Capacity factor reality check** — compare observed `mean_capacity_factor_pct` across fuels (nuclear vs solar vs wind).
4. **Concentration** — Gini or HHI of plant capacity within each country using `capacity_share_country_pct`.
5. **Per-capita capacity** — `capacity_per_capita_w` versus GDP per capita; find outliers.
6. **Geospatial clustering** — DBSCAN on latitude/longitude to find industrial clusters and co-located plants.
7. **Missingness analysis** — which countries and fuels report generation data, and does that bias any conclusion?
8. **Regression** — predict capacity from fuel, age and country features; or predict whether generation is reported.
9. **Renewable vs fossil siting** — latitude and climate band distributions by fuel group.

## 📁 Files

| File | What it is |
|---|---|
| `power_plants.csv` | 34,936 power plants x 52 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: fuel mix, capacity factors, ageing fleet. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`energy`, `climate`, `environment`, `geospatial`, `electricity`, `renewable-energy`, `sustainability`, `infrastructure`, `tabular`, `economics`

## 🔗 Provenance

- **Source:** World Resources Institute **Global Power Plant Database v1.3.0**, distributed as
  `global_power_plant_database.csv` in the `wri/global-power-plant-database` GitHub repository.
- **Upstream compilation:** WRI aggregated national registers, company disclosures and OpenStreetMap-style
  sources; each record carries its own `source` and `url`, which are preserved here.
- **Enrichment:** country attributes (continent, UN region/sub-region, population, GDP per capita) joined
  from the World Bank-backed `countries-of-the-world` table in this repository.
- **Derived columns:** fuel group, renewable flag, plant age, capacity bands, country/world capacity shares,
  per-capita capacity, observed capacity factor, latest generation year and latitude band.
- **Snapshot date:** 20 November 2026.

## 🔄 Update frequency

**Never (static snapshot).** WRI publishes roughly annual releases; re-run `scripts/13_power_plants.py` when a new version appears.

## ⚠️ Caveats

- Coverage is best for plants above ~1 MW; small distributed generation (rooftop solar, small hydro) is largely absent.
- Generation is only reported for a minority of plants and only for 2013–2019; `mean_capacity_factor_pct` is therefore not a global average.
- `commissioning_year` is sometimes a decade estimate, so `plant_age_years` is approximate.
- Coordinates are rounded to four decimals in the upstream file and occasionally point to a corporate office rather than the plant.
- Capacity figures are nameplate, not derated or seasonal.
- The country join uses ISO-3 codes; a handful of territories have no World Bank population/GDP and leave those columns empty.

## 📜 Licence

Creative Commons Attribution 4.0 (CC BY 4.0) — World Resources Institute. Attribution to WRI and to the per-record `source` is required.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `country` | `string` | ISO-3166 alpha-3 country code of the plant. |
| 2 | `country_long` | `string` | Country name in long form. |
| 3 | `name` | `string` | Plant name as recorded in the database. |
| 4 | `gppd_idnr` | `string` | Unique WRI Global Power Plant Database identifier. |
| 5 | `capacity_mw` | `number` | Generating capacity in megawatts. |
| 6 | `latitude` | `number` | Plant latitude in decimal degrees. |
| 7 | `longitude` | `number` | Plant longitude in decimal degrees. |
| 8 | `primary_fuel` | `string` | Main fuel or energy source. |
| 9 | `other_fuel1` | `string` | Secondary fuel, if any. |
| 10 | `other_fuel2` | `string` | Third fuel, if any. |
| 11 | `other_fuel3` | `string` | Fourth fuel, if any. |
| 12 | `commissioning_year` | `number` | Year the plant (or its first unit) started operating. |
| 13 | `owner` | `string` | Owner or operator as recorded. |
| 14 | `source` | `string` | Source of the plant record. |
| 15 | `url` | `string` | Source URL for the record. |
| 16 | `geolocation_source` | `string` | How the coordinates were obtained. |
| 17 | `wepp_id` | `number` | World Electric Power Plants database cross-reference. |
| 18 | `year_of_capacity_data` | `number` | Year the capacity figure refers to. |
| 19 | `generation_gwh_2013` | `number` | Reported net generation in 2013 (GWh), where available. |
| 20 | `generation_gwh_2014` | `number` | Reported net generation in 2014 (GWh), where available. |
| 21 | `generation_gwh_2015` | `number` | Reported net generation in 2015 (GWh), where available. |
| 22 | `generation_gwh_2016` | `number` | Reported net generation in 2016 (GWh), where available. |
| 23 | `generation_gwh_2017` | `number` | Reported net generation in 2017 (GWh), where available. |
| 24 | `generation_gwh_2018` | `number` | Reported net generation in 2018 (GWh), where available. |
| 25 | `generation_gwh_2019` | `string` | Reported net generation in 2019 (GWh), where available. |
| 26 | `generation_data_source` | `string` | Derived field. |
| 27 | `estimated_generation_gwh_2013` | `number` | Derived field. |
| 28 | `estimated_generation_gwh_2014` | `number` | Derived field. |
| 29 | `estimated_generation_gwh_2015` | `number` | Derived field. |
| 30 | `estimated_generation_gwh_2016` | `number` | Derived field. |
| 31 | `estimated_generation_gwh_2017` | `number` | Derived field. |
| 32 | `estimated_generation_note_2013` | `string` | Derived field. |
| 33 | `estimated_generation_note_2014` | `string` | Derived field. |
| 34 | `estimated_generation_note_2015` | `string` | Derived field. |
| 35 | `estimated_generation_note_2016` | `string` | Derived field. |
| 36 | `estimated_generation_note_2017` | `string` | Derived field. |
| 37 | `continent` | `string` | Continent of the plant's country (joined from the countries dataset). |
| 38 | `region` | `string` | UN macro-region of the plant's country. |
| 39 | `subregion` | `string` | UN sub-region of the plant's country. |
| 40 | `fuel_group` | `string` | Coarse fuel class: Renewable, Fossil, Nuclear, Storage or Other. |
| 41 | `is_renewable` | `boolean` | true when the primary fuel is a renewable source. |
| 42 | `plant_age_years` | `number` | Years since commissioning at snapshot time. |
| 43 | `capacity_class` | `string` | Capacity band from <1 MW to 10 GW+. |
| 44 | `capacity_share_country_pct` | `number` | Plant capacity as a percentage of all plants in its country in this file. |
| 45 | `capacity_share_global_pct` | `number` | Plant capacity as a percentage of total capacity in this file. |
| 46 | `capacity_per_capita_w` | `number` | Plant capacity divided by country population (watts per person). |
| 47 | `mean_capacity_factor_pct` | `number` | Mean of generation / (capacity x 8760 h) over the years with data, in percent — an observed capacity factor, not a design value. |
| 48 | `latest_generation_gwh` | `number` | Most recent non-empty annual generation value. |
| 49 | `latest_generation_year` | `number` | Year of that most recent generation value. |
| 50 | `has_generation_data` | `boolean` | true when at least one annual generation value is present. |
| 51 | `gdp_per_capita_usd` | `number` | Country GDP per capita from the countries dataset. |
| 52 | `grid_zone_class` | `string` | Latitude band of the plant (Tropical, Subtropical, Temperate, High latitude). |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
