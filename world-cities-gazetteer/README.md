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
pretty_name: "World Cities Gazetteer"
tags:
- tabular
- geography
---

# World Cities Gazetteer

**Subtitle:** 34,248 cities above 15,000 people with admin divisions and national statistics

**Tags:** `cities`, `urbanization`, `geography`, `population`, `geospatial`, `demography`, `world`, `geonames`, `tabular`, `clustering`

**Dataset File:** `cities.csv` (34,248 rows, 43 columns, 14.6 MB)

---

## 📖 Description

### Every city on Earth with more than 15,000 people

A gazetteer of **34,248 cities** in **244 countries** and territories, exported from
GeoNames and enriched with national statistics, administrative names and derived urban features —
**43 parameters per city**.

Each row gives:
- **Identity** — GeoNames id, name, ASCII name, full alternative-name list, feature class and feature code.
- **Location** — latitude and longitude, elevation from records and from a digital elevation model, IANA
  time zone and the last modification date.
- **Administration** — ISO country code, alternate country codes for border towns, and the codes and
  resolved name for the first-level administrative division, plus second-, third- and fourth-level codes.
- **Status** — whether the city is the national capital (**241 capitals**), a first-level
  administrative capital, or an ordinary populated place.
- **Population** — city population, a population band, the city's share of its country's population and
  its rank within that country.
- **National context** — country name, continent, UN region and sub-region, total population, area,
  population density, urbanisation rate and GDP per capita.
- **Geometry and language** — hemisphere, latitude band, elevation band, distance to the capital,
  alternative-name count, name length and a diacritics flag.

The alternative-name count is a surprisingly good proxy for international prominence, and the
capital-distance column lets you measure how primate a country's urban system is.

## 🧾 Columns (43)

`geonameid`, `name`, `asciiname`, `alternatenames`, `latitude`, `longitude`, `feature_class`, `feature_code`, `country_code`, `cc2`, `admin1_code`, `admin2_code`, `admin3_code`, `admin4_code`, `population`, `elevation_m`, `dem_m`, `timezone`, `modification_date`, `country_name`, `continent`, `region`, `subregion`, `admin1_name`, `is_capital`, `is_admin_capital`, `hemisphere`, `latitude_band`, `population_class`, `population_share_country_pct`, `country_urban_pct`, `country_population`, `country_area_km2`, `country_pop_density_per_km2`, `city_rank_in_country`, `alt_names_count`, `name_length`, `has_diacritics`, `distance_to_capital_km`, `timezone_region`, `utc_offset_hours`, `elevation_band`, `gdp_per_capita_usd`

## 💡 Ideas for using this data

1. **Urban hierarchy** — Zipf's law: rank versus population within each country.
2. **Primacy** — share of the largest city in national population, and how far the second city lags.
3. **Megacity map** — plot all cities over 5 million with a population-weighted scatter.
4. **Coastal vs inland** — with elevation and distance-to-capital, classify settlement patterns.
5. **Name linguistics** — diacritics, name length and alternative-name counts by region.
6. **Capital effect** — does distance to the capital predict a city's population rank?
7. **Country clustering** — build an urban profile per country (mean city size, primacy, density) and cluster.
8. **Geospatial** — DBSCAN/HDBSCAN over coordinates to recover metropolitan agglomerations that GeoNames lists as separate cities.
9. **Regression** — predict city population from country and geography features.

## 📁 Files

| File | What it is |
|---|---|
| `cities.csv` | 34,248 cities x 43 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: Zipf's law, primacy, megacity map. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`cities`, `urbanization`, `geography`, `population`, `geospatial`, `demography`, `world`, `geonames`, `tabular`, `clustering`

## 🔗 Provenance

- **Primary source:** **GeoNames** `cities15000.zip` — all populated places with a population above
  15,000 (or capitals), `download.geonames.org/export/dump/`.
- **Administrative names:** GeoNames `admin1CodesASCII.txt`, joined on `country_code.admin1_code`.
- **Enrichment:** country name, continent, UN region/sub-region, population, area, urbanisation rate and
  GDP per capita joined from the World Bank-backed `countries-of-the-world` table in this repository.
- **Transformation:** TSV to CSV, alternative names normalised from commas to semicolons, plus 24 derived
  columns (population bands and shares, capital flags, distance to capital, elevation bands and more).
- **Snapshot date:** 20 November 2026.

## 🔄 Update frequency

**Never (static snapshot).** GeoNames updates daily upstream; this file is frozen at the snapshot date. Re-run `scripts/15_cities.py` for a refresh.

## ⚠️ Caveats

- Population figures come from national censuses of varying years; comparability across countries is approximate.
- GeoNames is crowd-edited, so a few coordinates and populations are stale or wrong.
- `utc_offset_hours` is left empty by design — the offset must be derived from the IANA zone with a tz database.
- The file is a list of individual populated places, not metropolitan areas; suburbs appear separately.
- Coverage below 15,000 inhabitants is intentionally absent; small towns and villages are not included.
- `elevation_m` is sparse while `dem_m` is dense — use `dem_m` for analysis and treat `elevation_m` as a quality check.

## 📜 Licence

Creative Commons Attribution 4.0 (CC BY 4.0) — GeoNames. Attribution to GeoNames is required for any redistribution or derived publication.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `geonameid` | `number` | GeoNames numeric identifier. |
| 2 | `name` | `string` | City name (UTF-8). |
| 3 | `asciiname` | `string` | ASCII transliteration of the name. |
| 4 | `alternatenames` | `string` | Semicolon-separated alternative names (comma-separated upstream, normalised here). |
| 5 | `latitude` | `number` | Latitude in decimal degrees. |
| 6 | `longitude` | `number` | Longitude in decimal degrees. |
| 7 | `feature_class` | `string` | GeoNames feature class; P for populated places. |
| 8 | `feature_code` | `string` | GeoNames feature code (PPLC national capital, PPLA1 seat of a first-order division, PPL town...). |
| 9 | `country_code` | `string` | ISO-3166 alpha-2 country code. |
| 10 | `cc2` | `string` | Alternate country codes for places near a border. |
| 11 | `admin1_code` | `string` | First-level administrative division code. |
| 12 | `admin2_code` | `string` | Second-level administrative division code. |
| 13 | `admin3_code` | `string` | Third-level administrative division code. |
| 14 | `admin4_code` | `string` | Fourth-level administrative division code. |
| 15 | `population` | `number` | City population. |
| 16 | `elevation_m` | `number` | Elevation in metres as recorded (often empty). |
| 17 | `dem_m` | `number` | Digital elevation model value in metres. |
| 18 | `timezone` | `string` | IANA time-zone name. |
| 19 | `modification_date` | `date` | Date the GeoNames record was last modified. |
| 20 | `country_name` | `string` | Country common name (joined by ISO-3 code). |
| 21 | `continent` | `string` | Continent of the country. |
| 22 | `region` | `string` | UN macro-region of the country. |
| 23 | `subregion` | `string` | UN sub-region of the country. |
| 24 | `admin1_name` | `string` | Name of the first-level administrative division (state/province/region). |
| 25 | `is_capital` | `boolean` | true when the city is the national capital (GeoNames feature code PPLC). |
| 26 | `is_admin_capital` | `boolean` | true when the city is the capital of a first-level division (PPLA family). |
| 27 | `hemisphere` | `string` | Northern or Southern hemisphere. |
| 28 | `latitude_band` | `string` | Climate-style latitude band. |
| 29 | `population_class` | `string` | Population band from small town to megacity. |
| 30 | `population_share_country_pct` | `number` | City population as a percentage of its country's population. |
| 31 | `country_urban_pct` | `number` | Urbanisation rate of the country (World Bank). |
| 32 | `country_population` | `number` | Country population (World Bank). |
| 33 | `country_area_km2` | `number` | Country area in square kilometres. |
| 34 | `country_pop_density_per_km2` | `number` | Country population density. |
| 35 | `city_rank_in_country` | `number` | Rank of the city by population within its country in this file. |
| 36 | `alt_names_count` | `number` | Number of alternative names recorded (a proxy for international prominence). |
| 37 | `name_length` | `number` | Length of the primary name in characters. |
| 38 | `has_diacritics` | `boolean` | true when the primary name contains non-ASCII characters. |
| 39 | `distance_to_capital_km` | `number` | Great-circle distance to the country's capital city. |
| 40 | `timezone_region` | `string` | Geographic prefix of the IANA time zone (e.g. Europe, America, Asia). |
| 41 | `utc_offset_hours` | `number` | Standard UTC offset implied by the time zone, from the country capital. |
| 42 | `elevation_band` | `string` | Terrain band from sea level to high plateau. |
| 43 | `gdp_per_capita_usd` | `number` | Country GDP per capita (World Bank). |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
