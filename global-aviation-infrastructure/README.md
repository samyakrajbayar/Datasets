---
license: cc0-1.0
task_categories:
- tabular
tags:
- tabular
pretty_name: "Global Aviation Infrastructure"
---

# Global Aviation Infrastructure

**Subtitle:** 86,377 airports with runway, radio-navigation & country parameters

**Tags:** `tabular`, `aviation`, `transport`

**Dataset File:** `airports.csv` (86,377 rows, 57 columns, 23.2 MB)

**Provenance & Source:** OurAirports Public Data (ourairports.com)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### The world's airports, runways and radio infrastructure

OurAirports is a community-maintained global aeronautical database. This extract joins its four
public tables into **86,377 airports** across **247 countries/territories**, with
**57 parameters** per airport.

- **Identity** — internal id, ident, airport type, name, IATA/ICAO/GPS/local codes, municipality,
  ISO country and region, continent, coordinates and elevation.
- **Country context** — country name, World Bank region and subregion, hemisphere and coordinate bands.
- **Runways** — count, longest/total/average length, widest runway, paved vs unpaved vs closed,
  lighted count and the set of surface types.
- **Radio and navigation** — frequency count and types, highest frequency, navaid count and types.
- **Service flags** — scheduled service, large/medium/small airport, heliport, seaplane base, has
  runway / frequency / navaid, website and Wikipedia availability.

**1,174 large airports** and **4,336 airports with scheduled service** are included;
**9,053** carry an IATA code. The runway and navaid joins turn a simple directory into an
infrastructure dataset suitable for network analysis, accessibility studies and aviation economics.

## 🧾 Columns (57)

`id`, `ident`, `type`, `name`, `latitude_deg`, `longitude_deg`, `elevation_ft`, `continent`, `iso_country`, `iso_region`, `municipality`, `scheduled_service`, `icao_code`, `iata_code`, `gps_code`, `local_code`, `home_link`, `wikipedia_link`, `keywords`, `country_name`, `country_region`, `country_subregion`, `elevation_m`, `hemisphere`, `latitude_band`, `longitude_band`, `is_large_airport`, `is_medium_airport`, `is_small_airport`, `is_heliport`, `is_seaplane_base`, `has_iata`, `has_icao`, `has_scheduled_service`, `has_home_link`, `has_wikipedia_link`, `name_length`, `keyword_count`, `runway_count`, `paved_runway_count`, `unpaved_runway_count`, `lighted_runway_count`, `closed_runway_count`, `longest_runway_ft`, `longest_runway_m`, `total_runway_length_ft`, `avg_runway_length_ft`, `max_runway_width_ft`, `runway_surface_types`, `frequency_count`, `frequency_types`, `max_frequency_mhz`, `navaid_count`, `navaid_types`, `has_runway`, `has_frequency`, `has_navaid`

## 💡 Ideas for using this data

1. **Hub ranking** — rank airports by runway capacity, scheduled service and navaid density.
2. **Island and remote access** — find countries whose airports have no paved runway.
3. **Runway length vs traffic** — do long runways predict scheduled service, or the reverse?
4. **Airport density** — airports per million people by country (join the countries dataset).
5. **Surface mix** — unpaved share by region; which regions still depend on grass/gravel strips?
6. **Navigation infrastructure gaps** — airports with runways but no navaids or frequencies.
7. **Coordinate quality** — missing or suspicious coordinates by country and airport type.
8. **Heliport geography** — where heliports cluster relative to large airports.
9. **Map making** — the latitude/longitude columns support point maps and hex-bin density plots.

## 📁 Files

| File | What it is |
|---|---|
| `airports.csv` | 86,377 airports x 57 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`aviation`, `airports`, `infrastructure`, `transport`, `geospatial`, `ourairports`

## 🔗 Provenance

- **Source:** **OurAirports** public data files,
  `https://davidmegginson.github.io/ourairports-data/` (`airports.csv`, `runways.csv`,
  `frequencies.csv`, `navaids.csv`), maintained by David Megginson and contributors.
- **Join:** runways, frequencies and navaids are aggregated to one row per airport (by airport id for
  runways/frequencies and by associated airport ident for navaids).
- **Enrichment:** country names and World Bank regions joined from the pack's countries dataset;
  elevations converted to metres; coordinate bands and service flags derived.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Continuous upstream; snapshot here.** OurAirports updates its files daily.

## ⚠️ Caveats

- OurAirports is community-maintained: small airports and heliports are inconsistently complete.
- Runway and frequency tables change slowly and may lag official AIP publications.
- `scheduled_service` reflects the last contributor update, not a live timetable.
- Some closed airports remain in the file with `type = closed`.
- Navaids are joined by `associated_airport` ident, which is missing for some aids.
- Coordinates are WGS84 but a small number of records are approximate.
- No passenger or movement statistics are included — this is infrastructure, not traffic.

## 📜 Licence

OurAirports data is released into the public domain (CC0).

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `id` | `number` | OurAirports internal airport identifier. |
| 2 | `ident` | `string` | Stable identifier (usually the ICAO code or local code). |
| 3 | `type` | `string` | Airport type: large_airport, medium_airport, small_airport, heliport, seaplane_base, closed. |
| 4 | `name` | `string` | Airport name. |
| 5 | `latitude_deg` | `number` | Latitude in decimal degrees (WGS84). |
| 6 | `longitude_deg` | `number` | Longitude in decimal degrees (WGS84). |
| 7 | `elevation_ft` | `number` | Elevation above sea level in feet. |
| 8 | `continent` | `string` | Continent code (AF, AN, AS, EU, NA, OC, SA). |
| 9 | `iso_country` | `string` | ISO 3166-1 alpha-2 country code. |
| 10 | `iso_region` | `string` | ISO 3166-2 subdivision code. |
| 11 | `municipality` | `string` | City or town served. |
| 12 | `scheduled_service` | `string` | yes/no — whether scheduled commercial service exists. |
| 13 | `icao_code` | `string` | ICAO airport code. |
| 14 | `iata_code` | `string` | IATA airport code. |
| 15 | `gps_code` | `string` | GPS/ICAO code used in navigation databases. |
| 16 | `local_code` | `string` | Local national identifier. |
| 17 | `home_link` | `string` | Official website. |
| 18 | `wikipedia_link` | `string` | Wikipedia article. |
| 19 | `keywords` | `string` | Comma-separated alternative names. |
| 20 | `country_name` | `string` | Country common name (joined from the countries dataset). |
| 21 | `country_region` | `number` | World Bank region of the country. |
| 22 | `country_subregion` | `number` | World Bank subregion. |
| 23 | `elevation_m` | `number` | Elevation in metres. |
| 24 | `hemisphere` | `string` | N/S + E/W hemisphere pair. |
| 25 | `latitude_band` | `string` | 10-degree latitude band label. |
| 26 | `longitude_band` | `string` | 15-degree longitude band label. |
| 27 | `is_large_airport` | `boolean` | true for large_airport records. |
| 28 | `is_medium_airport` | `boolean` | true for medium_airport records. |
| 29 | `is_small_airport` | `boolean` | true for small_airport records. |
| 30 | `is_heliport` | `boolean` | true for heliports. |
| 31 | `is_seaplane_base` | `boolean` | true for seaplane bases. |
| 32 | `has_iata` | `boolean` | true when an IATA code is present. |
| 33 | `has_icao` | `boolean` | true when an ICAO code is present. |
| 34 | `has_scheduled_service` | `boolean` | true when scheduled_service is yes. |
| 35 | `has_home_link` | `boolean` | true when a website is listed. |
| 36 | `has_wikipedia_link` | `boolean` | true when a Wikipedia article is listed. |
| 37 | `name_length` | `number` | Characters in the airport name. |
| 38 | `keyword_count` | `number` | Number of alternative names. |
| 39 | `runway_count` | `number` | Number of runway records (including closed). |
| 40 | `paved_runway_count` | `number` | Runways with an asphalt/concrete surface. |
| 41 | `unpaved_runway_count` | `number` | Open runways without a paved surface. |
| 42 | `lighted_runway_count` | `number` | Runways flagged as lighted. |
| 43 | `closed_runway_count` | `number` | Runways flagged as closed. |
| 44 | `longest_runway_ft` | `number` | Longest runway length in feet. |
| 45 | `longest_runway_m` | `number` | Longest runway length in metres. |
| 46 | `total_runway_length_ft` | `number` | Sum of all runway lengths in feet. |
| 47 | `avg_runway_length_ft` | `number` | Mean runway length in feet. |
| 48 | `max_runway_width_ft` | `number` | Widest runway in feet. |
| 49 | `runway_surface_types` | `string` | Distinct runway surface strings. |
| 50 | `frequency_count` | `number` | Number of radio frequencies assigned. |
| 51 | `frequency_types` | `string` | Distinct frequency types (TWR, GND, ATIS, ...). |
| 52 | `max_frequency_mhz` | `number` | Highest assigned frequency in MHz. |
| 53 | `navaid_count` | `number` | Navigational aids associated with the airport. |
| 54 | `navaid_types` | `string` | Distinct navaid types. |
| 55 | `has_runway` | `boolean` | true when at least one runway is recorded. |
| 56 | `has_frequency` | `boolean` | true when at least one frequency is recorded. |
| 57 | `has_navaid` | `boolean` | true when at least one navaid is associated. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
