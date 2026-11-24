# World Postal Code Directory

**Subtitle:** 1,835,923 postal codes in 124 countries with coordinates & hierarchy

**Tags:** `tabular`, `geography`, `world`

**Dataset File:** `postal_codes.csv` (1,835,923 rows, 29 columns, 271.3 MB)

**Provenance & Source:** GeoNames Postal Code Database (geonames.org)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### Postal codes as a geographic index

GeoNames' `allCountries` postal code export is one of the few open, global postal-code lists.
This dataset contains **1,835,923 postal-code records in 124 countries**, with **29 parameters**
per record and duplicates removed on country + code + place + admin1.

- **Address hierarchy** — country, postal code, place name, admin1/admin2/admin3 names and codes,
  plus an `admin_depth` count.
- **Geography** — latitude/longitude, hemisphere, 10-degree latitude band, 15-degree longitude band and
  a 9-character geohash.
- **Code shape** — length, numeric flag, two-character prefix, first character.
- **Quality** — GeoNames accuracy code and label, plus admin2/admin3 presence flags.
- **Country context** — country name, World Bank region and subregion.

**1,128,319 codes are purely numeric**, while the rest use letters or mixed formats. The
file supports geocoding, delivery-zone analysis, regional segmentation and postal-format research.

## 🧾 Columns (29)

`country_code`, `postal_code`, `place_name`, `admin1_name`, `admin1_code`, `admin2_name`, `admin2_code`, `admin3_name`, `admin3_code`, `latitude`, `longitude`, `accuracy`, `country_name`, `country_region`, `country_subregion`, `postal_length`, `is_numeric_postal`, `postal_prefix`, `postal_first_char`, `hemisphere`, `latitude_band`, `longitude_band`, `accuracy_label`, `has_admin2`, `has_admin3`, `admin_depth`, `place_word_count`, `place_name_length`, `geohash`

## 💡 Ideas for using this data

1. **Postal formats** — cluster countries by code length and character mix.
2. **Geocoding** — join to any address table on country + postal code; measure match rates.
3. **Population proxies** — count codes per admin1 area as a proxy for settlement density.
4. **Spatial clustering** — geohash prefixes make it easy to bin codes into map tiles.
5. **Prefix hierarchies** — check whether the first one or two characters map cleanly to regions.
6. **Data quality** — compare GeoNames accuracy classes across countries.
7. **Missing middle** — countries with no admin2 data; what does that imply for address matching?
8. **Place-name NLP** — tokenise place names to find common suffixes (ville, stad, burg, -pur).
9. **Map visualisation** — plot all coordinates coloured by region (use a sample for speed).

## 📁 Files

| File | What it is |
|---|---|
| `postal_codes.csv` | 1,835,923 postal records x 29 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`postal-codes`, `geography`, `geocoding`, `geonames`, `addresses`, `world`, `tabular`

## 🔗 Provenance

- **Source:** **GeoNames** postal code export,
  `https://download.geonames.org/export/zip/allCountries.zip` (creative commons attribution).
- **Format:** tab-separated, 12 fields per line: country code, postal code, place name, admin1
  name/code, admin2 name/code, admin3 name/code, latitude, longitude, accuracy.
- **Processing:** exact duplicates removed, country names and World Bank regions joined, bands,
  code-shape fields and geohashes derived.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Daily upstream; snapshot here.** GeoNames refreshes the postal export regularly.

## ⚠️ Caveats

- Postal code systems differ wildly: some countries have none, others map one code to many places.
- Coordinates are place centroids, not rooftop locations; accuracy varies by country.
- GeoNames is community-maintained and coverage is uneven outside Europe and North America.
- Duplicate removal is on country + code + place + admin1, so genuinely repeated codes remain.
- Codes are formatted as nationally used; no normalisation (spaces, hyphens) is applied.
- Row order follows the upstream file (country, then code), not any ranking.
- This file is large; notebook cells should sample or filter before plotting.

## 📜 Licence

GeoNames data is licensed CC BY 4.0 — attribution to GeoNames is required.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `country_code` | `string` | ISO 3166-1 alpha-2 country code. |
| 2 | `postal_code` | `string` | Postal code as used nationally (may contain letters, spaces or hyphens). |
| 3 | `place_name` | `string` | Primary place name for the code. |
| 4 | `admin1_name` | `string` | First-level administrative division (state, region, province). |
| 5 | `admin1_code` | `number` | GeoNames code for the first-level division. |
| 6 | `admin2_name` | `string` | Second-level division (county, district). |
| 7 | `admin2_code` | `number` | GeoNames code for the second-level division. |
| 8 | `admin3_name` | `string` | Third-level division (municipality, commune). |
| 9 | `admin3_code` | `number` | GeoNames code for the third-level division. |
| 10 | `latitude` | `number` | Latitude of the place centroid (decimal degrees). |
| 11 | `longitude` | `number` | Longitude of the place centroid (decimal degrees). |
| 12 | `accuracy` | `number` | GeoNames accuracy code: 1 estimated, 4 region/state, 6 admin2 centroid. |
| 13 | `country_name` | `string` | Country common name. |
| 14 | `country_region` | `number` | World Bank region. |
| 15 | `country_subregion` | `number` | World Bank subregion. |
| 16 | `postal_length` | `number` | Number of characters in the postal code. |
| 17 | `is_numeric_postal` | `boolean` | true when the code contains only digits. |
| 18 | `postal_prefix` | `string` | First two characters of the postal code (sorting/region prefix). |
| 19 | `postal_first_char` | `string` | First character of the postal code. |
| 20 | `hemisphere` | `string` | N/S + E/W hemisphere pair. |
| 21 | `latitude_band` | `string` | 10-degree latitude band. |
| 22 | `longitude_band` | `string` | 15-degree longitude band. |
| 23 | `accuracy_label` | `string` | Human-readable accuracy class. |
| 24 | `has_admin2` | `boolean` | true when a second-level division is recorded. |
| 25 | `has_admin3` | `boolean` | true when a third-level division is recorded. |
| 26 | `admin_depth` | `number` | Number of administrative levels present (1-3 plus country). |
| 27 | `place_word_count` | `number` | Words in the place name. |
| 28 | `place_name_length` | `number` | Characters in the place name. |
| 29 | `geohash` | `string` | 9-character geohash of the coordinates (spatial joins, binning). |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
