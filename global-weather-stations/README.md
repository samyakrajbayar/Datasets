---
license: cc0-1.0
task_categories:
- tabular
tags:
- tabular
pretty_name: "Global Weather Station Network"
---

# Global Weather Station Network

**Subtitle:** 133,041 GHCN-Daily stations with coordinates, elevation & network data

**Tags:** `tabular`, `weather`, `climate`

**Dataset File:** `weather_stations.csv` (133,041 rows, 35 columns, 28.0 MB)

**Provenance & Source:** NOAA NCEI GHCN-Daily Database (noaa.gov)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### The global weather-station network

NOAA's Global Historical Climatology Network – Daily (GHCN-Daily) aggregates station observations
worldwide. This dataset combines its **133,041 stations** across **218 countries** with the
inventory of what each station measures, giving **35 parameters**.

- **Identity** — station id, name, country code and name, U.S. state, GSN/HCN flags and WMO id.
- **Position** — latitude, longitude, elevation, hemisphere and coordinate bands.
- **Measurement inventory** — element codes and count, first and last year, record length, and
  precipitation/temperature/snow/wind availability flags.
- **Derived** — active-in-2025 and long-record flags, station age, high-elevation and coastal-lowland
  flags, name and country coverage.

**43,689 stations have data reaching 2025** and **985** belong to the Global Surface Network.
The file is a ready-made station metadata table for any GHCN-Daily analysis or climate-data pipeline.

## 🧾 Columns (35)

`station_id`, `name`, `latitude`, `longitude`, `elevation_m`, `state`, `country_code`, `country_name`, `gsn_flag`, `hcn_flag`, `wmo_id`, `hemisphere`, `latitude_band`, `longitude_band`, `is_us`, `has_state`, `has_wmo`, `is_gsn`, `is_hcn`, `name_length`, `name_word_count`, `element_count`, `elements`, `first_year`, `last_year`, `record_years`, `is_active_2025`, `is_long_record`, `has_precipitation`, `has_temperature`, `has_snow`, `has_wind`, `station_age`, `is_high_elevation`, `is_coastal_lowland`

## 💡 Ideas for using this data

1. **Network coverage** — station density by country and latitude band.
2. **Record length** — which regions have long, continuous climate records?
3. **Measurement gaps** — stations with temperature but no precipitation, and vice versa.
4. **Elevation bias** — high-elevation stations are sparse; quantify the gap.
5. **Active vs retired** — map stations that stopped reporting.
6. **GSN/HCN** — reference-network coverage by country.
7. **Climate analysis prep** — join this metadata to GHCN-Daily observations.
8. **Station naming** — name patterns and duplicate names.
9. **Country comparison** — stations per country vs land area (external join).

## 📁 Files

| File | What it is |
|---|---|
| `weather_stations.csv` | 133,041 stations x 35 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`weather`, `climate`, `noaa`, `ghcn`, `stations`, `geospatial`, `infrastructure`

## 🔗 Provenance

- **Source:** **NOAA NCEI GHCN-Daily** metadata files,
  `ghcnd-stations.txt`, `ghcnd-countries.txt` and `ghcnd-inventory.txt` under
  `https://www.ncei.noaa.gov/pub/data/ghcn/daily/`.
- **Processing:** fixed-width station records parsed, country names joined, inventory aggregated to one
  row per station (element set, first and last year), derived flags and bands added.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Daily.** GHCN-Daily and its metadata files are refreshed each day.

## ⚠️ Caveats

- Station metadata describes the station, not the observations; no daily values are included.
- Inventory years describe data availability in GHCN-Daily, not the station's operational life.
- The country code is a GHCN/FIPS-style prefix and may differ from ISO codes.
- Elevation is station elevation, not necessarily representative of the surrounding area.
- Some stations have no inventory entry and therefore blank element/year fields.
- GSN/HCN flags are network memberships that change slowly.
- Station names and coordinates contain historical inconsistencies.

## 📜 Licence

U.S. Government work (NOAA/NCEI) — public domain.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `station_id` | `string` | GHCN station identifier (first two characters are the country code). |
| 2 | `name` | `string` | Station name. |
| 3 | `latitude` | `number` | Latitude (decimal degrees). |
| 4 | `longitude` | `number` | Longitude (decimal degrees). |
| 5 | `elevation_m` | `number` | Elevation in metres. |
| 6 | `state` | `string` | Two-letter state code (U.S. stations only). |
| 7 | `country_code` | `string` | FIPS-like country code from the station id prefix. |
| 8 | `country_name` | `string` | Country name from the GHCN country list. |
| 9 | `gsn_flag` | `string` | Global Surface Network flag. |
| 10 | `hcn_flag` | `string` | U.S. Historical Climatology Network flag. |
| 11 | `wmo_id` | `number` | WMO station number, where assigned. |
| 12 | `hemisphere` | `string` | N/S + E/W hemisphere pair. |
| 13 | `latitude_band` | `string` | 10-degree latitude band. |
| 14 | `longitude_band` | `string` | 15-degree longitude band. |
| 15 | `is_us` | `boolean` | true for U.S. stations. |
| 16 | `has_state` | `boolean` | true when a state code is present. |
| 17 | `has_wmo` | `boolean` | true when a WMO id is present. |
| 18 | `is_gsn` | `boolean` | true for GSN stations. |
| 19 | `is_hcn` | `boolean` | true for HCN stations. |
| 20 | `name_length` | `number` | Characters in the station name. |
| 21 | `name_word_count` | `number` | Words in the station name. |
| 22 | `element_count` | `number` | Number of distinct daily elements measured. |
| 23 | `elements` | `string` | Element codes measured (semicolon-joined). |
| 24 | `first_year` | `number` | First year with data in the inventory. |
| 25 | `last_year` | `number` | Last year with data in the inventory. |
| 26 | `record_years` | `number` | last_year - first_year + 1. |
| 27 | `is_active_2025` | `boolean` | true when data reach 2025 or later. |
| 28 | `is_long_record` | `boolean` | true for records of 50 years or more. |
| 29 | `has_precipitation` | `boolean` | true when PRCP is measured. |
| 30 | `has_temperature` | `boolean` | true when TMAX or TMIN is measured. |
| 31 | `has_snow` | `boolean` | true when SNOW or SNWD is measured. |
| 32 | `has_wind` | `boolean` | true when AWND is measured. |
| 33 | `station_age` | `number` | Years since the first inventory year. |
| 34 | `is_high_elevation` | `boolean` | true above 2,000 m. |
| 35 | `is_coastal_lowland` | `boolean` | true below 10 m elevation. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
