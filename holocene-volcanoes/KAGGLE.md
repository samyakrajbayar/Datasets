# Holocene Volcanoes of the World

**Subtitle:** Global Holocene volcanoes with eruption history, morphology and coordinates

**Tags:** `geology`, `volcanoes`, `earth-science`, `natural-hazards`, `geospatial`, `environment`, `disaster`, `science`, `tabular`, `clustering`

**Dataset File:** `volcanoes.csv` (1,221 rows, 38 columns, 1.9 MB)

---

## 📖 Description

### Every volcano active in the Holocene

The Smithsonian Institution's **Global Volcanism Program** maintains the definitive catalogue of the
world's volcanoes. This dataset exports its Holocene layer as a flat table: **1,209 volcanoes** with
**38 parameters** each, covering eruptive history, morphology, tectonics, location and
photography.

Each row contains:
- **Identity** — GVP volcano number (a stable 6-digit id) and name.
- **Morphology** — primary volcano type, broader landform and dominant rock type.
- **Eruption history** — last eruption year (negative for BCE), a CE/BCE display string, decade,
  recency class, years since the last eruption, the evidence category for the Holocene date and a dated flag.
- **Tectonics and geology** — tectonic setting, subduction-zone flag, geologic epoch and a full-text
  geological summary.
- **Geography** — latitude, longitude, summit elevation, country and ISO-3 code, volcanic region and
  sub-region, continent, UN sub-region, hemisphere, latitude band and elevation band.
- **Media** — link, caption and photographer credit for the primary photograph, plus a photo flag.

**579 volcanoes have erupted since 1500** and **360 have no dated eruption at all** — a spread
that makes the file useful for hazard ranking, spatial statistics and text analysis of the summaries.

## 🧾 Columns (38)

`volcano_number`, `volcano_name`, `primary_volcano_type`, `volcanic_landform`, `last_eruption_year`, `country`, `region`, `subregion`, `latitude`, `longitude`, `elevation_m`, `tectonic_setting`, `geologic_epoch`, `evidence_category`, `major_rock_type`, `geological_summary`, `primary_photo_link`, `primary_photo_caption`, `primary_photo_credit`, `country_cca3`, `continent`, `un_region`, `hemisphere`, `abs_latitude`, `latitude_band`, `elevation_band`, `volcano_type_group`, `is_subduction_zone`, `is_holocene_dated`, `eruption_year_display`, `years_since_last_eruption`, `last_eruption_decade`, `eruption_recency_class`, `is_historical_eruption`, `is_undated`, `summary_length`, `has_photo`, `name_word_count`

## 💡 Ideas for using this data

1. **Ring of Fire** — map volcanoes by longitude/hemisphere and confirm the Pacific arc structure.
2. **Elevation vs latitude** — do high volcanoes cluster in the tropics and subtropics?
3. **Hazard ranking** — combine recency, elevation, population proximity (join with the cities dataset) and type.
4. **Volcano morphology** — type frequency by tectonic setting; stratovolcanoes versus shields.
5. **Submarine volcanism** — negative elevations and their spatial distribution.
6. **Spatial clustering** — DBSCAN over coordinates to recover volcanic arcs without using the region labels.
7. **Text analysis** — `geological_summary` is several sentences of expert prose; extract rock types, ages and hazard words.
8. **Dating quality** — how the `evidence_category` mix differs between regions.
9. **Country exposure** — volcanoes per country and per unit area, joined to population.

## 📁 Files

| File | What it is |
|---|---|
| `volcanoes.csv` | 1,209 volcanoes x 38 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: Ring of Fire map, elevation, eruption recency. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`geology`, `volcanoes`, `earth-science`, `natural-hazards`, `geospatial`, `environment`, `disaster`, `science`, `tabular`, `clustering`

## 🔗 Provenance

- **Source:** **Smithsonian Institution Global Volcanism Program**, `Volcanoes of the World`
  database, served as a WFS layer from `webservices.volcano.si.edu`
  (`GVP-VOTW:Smithsonian_VOTW_Holocene_Volcanoes`).
- **Query:** single GeoJSON feature collection request, no filtering.
- **Transformation:** GVP property names renamed to snake_case, coordinates taken from the geometry-verified
  latitude/longitude properties, and 21 derived columns added.
- **Context join:** country ISO-3, continent and UN region from the World Bank-backed countries table in
  this repository.
- **Snapshot date:** 20 November 2026.

## 🔄 Update frequency

**Rarely.** The GVP revises the catalogue a few times a year as eruptions are dated and new volcanoes are added; re-run `scripts/19_volcanoes.py` annually at most.

## ⚠️ Caveats

- `last_eruption_year` is negative for BCE dates and empty when the eruption is undated; it is not a usable continuous variable without care.
- The Holocene window is ~11,700 years, so 'last eruption' spans a huge range of dating precision.
- Submarine volcanoes have negative summit elevations.
- The `geological_summary` field contains embedded newlines and long prose; parse it as text, not as CSV-safe short values.
- Country names follow GVP conventions and a few do not map cleanly to ISO-3 codes.
- Photos are credited individually — the `primary_photo_credit` column must be preserved if images are reused.

## 📜 Licence

Smithsonian Institution Global Volcanism Program data are free to use for non-commercial research and education with attribution to the GVP and to individual photographers for images.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `volcano_number` | `number` | Smithsonian Global Volcanism Program volcano number. |
| 2 | `volcano_name` | `string` | Volcano name. |
| 3 | `primary_volcano_type` | `string` | Primary morphological type (Stratovolcano(es), Shield, Caldera...). |
| 4 | `volcanic_landform` | `string` | Broader landform classification. |
| 5 | `last_eruption_year` | `number` | Year of the last known eruption; negative values are BCE, empty means undated. |
| 6 | `country` | `string` | Country as recorded by the GVP. |
| 7 | `region` | `string` | Volcanic region. |
| 8 | `subregion` | `string` | Volcanic sub-region (usually the specific arc). |
| 9 | `latitude` | `number` | Latitude in decimal degrees. |
| 10 | `longitude` | `number` | Longitude in decimal degrees. |
| 11 | `elevation_m` | `number` | Summit elevation in metres (negative for submarine volcanoes). |
| 12 | `tectonic_setting` | `string` | Tectonic setting of the volcano. |
| 13 | `geologic_epoch` | `string` | Geologic epoch of the volcano's formation. |
| 14 | `evidence_category` | `string` | How the Holocene age of the last eruption is evidenced. |
| 15 | `major_rock_type` | `string` | Dominant rock type(s). |
| 16 | `geological_summary` | `string` | Free-text geological summary from the GVP. |
| 17 | `primary_photo_link` | `string` | URL of the primary photograph. |
| 18 | `primary_photo_caption` | `string` | Caption of the primary photograph. |
| 19 | `primary_photo_credit` | `string` | Photographer credit for the primary photograph. |
| 20 | `country_cca3` | `string` | ISO-3166 alpha-3 code of the volcano's country. |
| 21 | `continent` | `string` | Continent of the volcano's country. |
| 22 | `un_region` | `string` | UN macro-region of the country. |
| 23 | `hemisphere` | `string` | Northern or Southern hemisphere. |
| 24 | `abs_latitude` | `number` | Absolute latitude, for latitude-band analysis. |
| 25 | `latitude_band` | `string` | 10-degree latitude band. |
| 26 | `elevation_band` | `string` | Elevation band from submarine to high-Andean. |
| 27 | `volcano_type_group` | `string` | Coarse type: Stratovolcano, Shield, Caldera, Complex, Cone, Fissure, Submarine, Other. |
| 28 | `is_subduction_zone` | `boolean` | true when the tectonic setting involves subduction. |
| 29 | `is_holocene_dated` | `boolean` | true when the last eruption is dated rather than only inferred. |
| 30 | `eruption_year_display` | `string` | Last eruption year rendered as CE or BCE. |
| 31 | `years_since_last_eruption` | `number` | Years between the last eruption and 2026 (negative is impossible; empty if undated). |
| 32 | `last_eruption_decade` | `string` | Decade of the last eruption. |
| 33 | `eruption_recency_class` | `string` | Historical (since 1500), Holocene (10k years), Pleistocene, or undated. |
| 34 | `is_historical_eruption` | `boolean` | true when the last eruption is documented history (year >= 1500). |
| 35 | `is_undated` | `boolean` | true when no last-eruption year is recorded. |
| 36 | `summary_length` | `number` | Length of the geological summary text in characters. |
| 37 | `has_photo` | `boolean` | true when a primary photograph is linked. |
| 38 | `name_word_count` | `number` | Number of words in the volcano name. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
