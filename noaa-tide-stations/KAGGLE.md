# NOAA Tide & Current Station Network

**Subtitle:** 3,707 U.S. coastal stations with capabilities, coordinates & metadata

**Tags:** `tabular`, `oceanography`, `climate`

**Dataset File:** `noaa_stations.csv` (3,707 rows, 40 columns, 752.5 KB)

**Provenance & Source:** NOAA CO-OPS Metadata API (tidesandcurrents.noaa.gov)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### The U.S. tide, current and weather station network

NOAA's Center for Operational Oceanographic Products and Services operates a national network of
coastal and Great Lakes stations. This dataset contains **3,707 stations** across
**35 states/territories**, with **40 parameters** each.

- **Identity** — station id, name, state, territory, Census region, type, reference id.
- **Position and time** — latitude, longitude, time zone, UTC offset and local time meridian.
- **Codes** — SHEF code, port code, affiliations and the metadata API URL.
- **Capabilities** — product count and product names, tide prediction, currents, meteorology,
  water level, storm surge, observed water level and harmonic constituent flags.
- **Derived** — coordinate bands, hemisphere, coastal/territory flags, name lengths and a product
  completeness percentage.

**0 stations publish tide predictions** and **0 publish meteorological data**. The
capability columns make it easy to map where each type of observation is available along the U.S.
coastline, Great Lakes and territories.

## 🧾 Columns (40)

`station_id`, `name`, `state`, `country`, `state_region`, `latitude`, `longitude`, `type`, `timezone`, `timezone_offset`, `time_meridian`, `reference_id`, `shef_code`, `port_code`, `affiliations`, `station_url`, `has_shef`, `has_port_code`, `has_affiliations`, `product_count`, `products`, `disclaimer_count`, `notice_count`, `has_disclaimer`, `has_notice`, `is_tide_station`, `is_current_station`, `is_met_station`, `is_water_level_station`, `has_storm_surge`, `has_observed_water_level`, `has_harmonic_constituents`, `latitude_band`, `longitude_band`, `hemisphere`, `is_coastal_us`, `is_territory`, `name_length`, `name_word_count`, `product_completeness`

## 💡 Ideas for using this data

1. **Network coverage** — station density by state and coastline segment.
2. **Capability gaps** — stretches of coast with water-level but no meteorological data.
3. **Products** — which product combinations are standard, and which stations are unusual?
4. **Reference network** — map reference stations and their subordinate stations.
5. **Territories** — compare station capabilities in territories vs the mainland.
6. **Map making** — plot the network with capability colours.
7. **Time zones** — station distribution across time zones and meridians.
8. **Data availability** — build a manifest of downloadable products per station.
9. **Metadata quality** — missing SHEF/port codes by region.

## 📁 Files

| File | What it is |
|---|---|
| `noaa_stations.csv` | 3,707 stations x 40 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`noaa`, `tides`, `oceanography`, `stations`, `coastal`, `geospatial`, `infrastructure`

## 🔗 Provenance

- **Source:** **NOAA CO-OPS Metadata API**,
  `https://api.tidesandcurrents.noaa.gov/mdapi/prod/webapi/stations.json`.
- **Scope:** every station returned by the metadata endpoint (tide, current, met and water-level
  stations).
- **Processing:** station records flattened, product names extracted from their URLs, capability and
  geography flags derived.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**As stations change.** NOAA updates the metadata API when stations are added or retired.

## ⚠️ Caveats

- The metadata API describes stations, not the observations themselves.
- Capability flags reflect the products published in the metadata at snapshot time.
- Station ids are strings and can have leading zeros.
- Coordinates are station locations, not necessarily the exact sensor position.
- Only U.S. stations and territories are covered.
- Some fields (port code, affiliations, SHEF) are absent for many stations.
- Product completeness uses 12 as an arbitrary denominator, for comparison only.

## 📜 Licence

U.S. Government work (NOAA) — public domain.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `station_id` | `string` | NOAA station identifier. |
| 2 | `name` | `string` | Station name. |
| 3 | `state` | `string` | Two-letter state/territory code. |
| 4 | `country` | `string` | Territory name for non-state stations. |
| 5 | `state_region` | `string` | U.S. Census region. |
| 6 | `latitude` | `number` | Latitude (decimal degrees). |
| 7 | `longitude` | `number` | Longitude (decimal degrees). |
| 8 | `type` | `string` | Station type code (S = tide/water level, etc.). |
| 9 | `timezone` | `string` | Time zone name. |
| 10 | `timezone_offset` | `number` | Offset from UTC in hours. |
| 11 | `time_meridian` | `number` | Local time meridian. |
| 12 | `reference_id` | `number` | NOAA reference station id. |
| 13 | `shef_code` | `string` | SHEF location code. |
| 14 | `port_code` | `string` | Port code used by marine services. |
| 15 | `affiliations` | `string` | Partner affiliations. |
| 16 | `station_url` | `string` | Metadata API URL for the station. |
| 17 | `has_shef` | `boolean` | true when a SHEF code exists. |
| 18 | `has_port_code` | `boolean` | true when a port code exists. |
| 19 | `has_affiliations` | `boolean` | true when affiliations are listed. |
| 20 | `product_count` | `number` | Number of data products offered. |
| 21 | `products` | `string` | Product names (semicolon-joined). |
| 22 | `disclaimer_count` | `number` | Number of disclaimers. |
| 23 | `notice_count` | `number` | Number of active notices. |
| 24 | `has_disclaimer` | `boolean` | true when a disclaimer exists. |
| 25 | `has_notice` | `boolean` | true when a notice exists. |
| 26 | `is_tide_station` | `boolean` | true when tide predictions are offered. |
| 27 | `is_current_station` | `boolean` | true when current data are offered. |
| 28 | `is_met_station` | `boolean` | true when meteorological data are offered. |
| 29 | `is_water_level_station` | `boolean` | true when water-level data are offered. |
| 30 | `has_storm_surge` | `boolean` | true when storm-surge data are offered. |
| 31 | `has_observed_water_level` | `boolean` | true when observed water levels are available. |
| 32 | `has_harmonic_constituents` | `boolean` | true when harmonic constituents are published. |
| 33 | `latitude_band` | `string` | 5-degree latitude band. |
| 34 | `longitude_band` | `string` | 10-degree longitude band. |
| 35 | `hemisphere` | `string` | N/S + E/W hemisphere pair. |
| 36 | `is_coastal_us` | `boolean` | true for U.S. coastal states. |
| 37 | `is_territory` | `boolean` | true for U.S. territories and freely associated states. |
| 38 | `name_length` | `number` | Characters in the station name. |
| 39 | `name_word_count` | `number` | Words in the station name. |
| 40 | `product_completeness` | `number` | product_count as a percentage of 12. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
