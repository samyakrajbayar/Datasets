---
license: cc-by-4.0
task_categories:
- tabular
tags:
- tabular
pretty_name: "Chicago Crime Incidents"
---

# Chicago Crime Incidents

**Subtitle:** 200,000 recent Chicago crimes with type, block location & arrest status

**Tags:** `tabular`, `crime`, `chicago`

**Dataset File:** `chicago_crimes.csv` (200,000 rows, 40 columns, 59.6 MB)

**Provenance & Source:** City of Chicago Open Data Portal (data.cityofchicago.org)

**Expected Update Frequency:** `monthly`

---

## 📖 Description

### 200,000 recent Chicago crime incidents

The City of Chicago publishes every reported crime with a block-level location, IUCR/FBI codes and
arrest status. This dataset contains the **200,000 most recent incidents** with **40 parameters**.

- **Incident** — id, case number, date/time, IUCR code, primary type, description, FBI code and the
  derived FBI category and coarse crime band.
- **Location** — block address, location description, beat, district, ward, community area,
  State Plane coordinates and latitude/longitude.
- **Outcome** — arrest and domestic flags.
- **Derived** — violent/property/drug/public-order and theft flags, firearm mention, night and weekend
  flags, hour/month/weekday, year-month, location and text-length measures.

**69,249 incidents are violent**, **10,411 mention a firearm**, and **30,919**
(15.5%) resulted in an arrest. The block-level geography supports hot-spot mapping
without exposing exact addresses.

## 🧾 Columns (40)

`id`, `case_number`, `date`, `block`, `iucr`, `primary_type`, `description`, `location_description`, `arrest`, `domestic`, `beat`, `district`, `ward`, `community_area`, `fbi_code`, `x_coordinate`, `y_coordinate`, `year`, `updated_on`, `latitude`, `longitude`, `fbi_category`, `crime_category`, `is_violent`, `is_property`, `is_drug`, `is_public_order`, `is_theft`, `is_firearm`, `is_arrest`, `is_domestic`, `hour`, `month`, `day_of_week`, `is_weekend`, `has_location`, `block_length`, `description_length`, `is_night`, `year_month`

## 💡 Ideas for using this data

1. **Hot-spot mapping** — hex-bin the coordinates and compare violent vs property crime.
2. **Temporal patterns** — hour-of-week heatmaps by crime category.
3. **Arrest propensity** — which crime types and districts clear cases by arrest?
4. **Firearm incidents** — spatial and temporal clustering of firearm mentions.
5. **District comparison** — crime mix and arrest rates across the 22 police districts.
6. **Seasonality** — monthly counts by category over the sample window.
7. **Location type** — street vs residence vs commercial mix by crime type.
8. **Forecasting** — build a weekly district-level count model.
9. **Equity analysis** — join community areas to census data (external) and test enforcement patterns.

## 📁 Files

| File | What it is |
|---|---|
| `chicago_crimes.csv` | 200,000 crime incidents x 40 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`crime`, `chicago`, `open-data`, `urban`, `geospatial`, `public-safety`, `socrata`

## 🔗 Provenance

- **Source:** **City of Chicago Open Data Portal**, Crimes 2001 to present,
  `https://data.cityofchicago.org/resource/ijzp-q8t2.json` (Socrata).
- **Scope:** the 200,000 most recent incidents by `date`, five pages of 40,000.
- **Processing:** timestamps parsed, crime and FBI categories mapped, temporal and text features
  derived; no addresses below block level are included upstream.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Daily.** The Chicago data portal updates the crime dataset continuously.

## ⚠️ Caveats

- This is a recency sample, not the full 2001-present history.
- Crime data reflects reports to police, not actual crime incidence.
- Records can be reclassified or updated after initial publication.
- Coordinates are block-level and occasionally missing or rounded.
- The `year` column follows the source and may differ from the parsed date year at year boundaries.
- Firearm flag is a keyword match on the description and will miss some cases.
- Arrest does not imply conviction.

## 📜 Licence

City of Chicago Open Data is licensed CC BY 4.0 — attribution required.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `id` | `number` | Incident record identifier. |
| 2 | `case_number` | `string` | Chicago Police Department case number. |
| 3 | `date` | `datetime` | Incident date and time (local). |
| 4 | `block` | `string` | Block-level address (hundred-block, not an exact address). |
| 5 | `iucr` | `string` | Illinois Uniform Crime Reporting code. |
| 6 | `primary_type` | `string` | Primary crime type. |
| 7 | `description` | `string` | Secondary description / subtype. |
| 8 | `location_description` | `string` | Location type (street, residence, apartment, ...). |
| 9 | `arrest` | `boolean` | true when an arrest was made. |
| 10 | `domestic` | `boolean` | true when the incident was domestic. |
| 11 | `beat` | `number` | Police beat. |
| 12 | `district` | `number` | Police district. |
| 13 | `ward` | `number` | City ward. |
| 14 | `community_area` | `number` | Community area number. |
| 15 | `fbi_code` | `string` | FBI crime code. |
| 16 | `x_coordinate` | `number` | State plane X coordinate. |
| 17 | `y_coordinate` | `number` | State plane Y coordinate. |
| 18 | `year` | `number` | Year reported in the source. |
| 19 | `updated_on` | `datetime` | Last update timestamp of the record. |
| 20 | `latitude` | `number` | Latitude (WGS84). |
| 21 | `longitude` | `number` | Longitude (WGS84). |
| 22 | `fbi_category` | `string` | Human-readable FBI crime category. |
| 23 | `crime_category` | `string` | Derived Violent / Property / Drug / Public order / Other band. |
| 24 | `is_violent` | `boolean` | true for violent crime types. |
| 25 | `is_property` | `boolean` | true for property crime types. |
| 26 | `is_drug` | `boolean` | true for narcotics offences. |
| 27 | `is_public_order` | `boolean` | true for public-order offences. |
| 28 | `is_theft` | `boolean` | true for theft/larceny. |
| 29 | `is_firearm` | `boolean` | true when the description mentions a firearm/handgun. |
| 30 | `is_arrest` | `boolean` | true when arrest is true. |
| 31 | `is_domestic` | `boolean` | true when domestic is true. |
| 32 | `hour` | `number` | Hour of day (0-23). |
| 33 | `month` | `number` | Month number. |
| 34 | `day_of_week` | `string` | Weekday name. |
| 35 | `is_weekend` | `boolean` | true for Saturday/Sunday. |
| 36 | `has_location` | `boolean` | true when latitude and longitude are present. |
| 37 | `block_length` | `number` | Characters in the block address. |
| 38 | `description_length` | `number` | Characters in the secondary description. |
| 39 | `is_night` | `boolean` | true for incidents between 20:00 and 05:59. |
| 40 | `year_month` | `string` | Year-month string for monthly aggregation. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
