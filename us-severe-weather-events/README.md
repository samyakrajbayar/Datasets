---
license: cc0-1.0
task_categories:
- tabular
tags:
- tabular
pretty_name: "U.S. Severe Weather Events 2000-2026"
---

# U.S. Severe Weather Events 2000-2026

**Subtitle:** 1.65M storm events with casualties, damage, paths and impact features

**Tags:** `tabular`, `weather`, `climate`

**Dataset File:** `severe_weather_events.csv` (1,657,168 rows, 72 columns, 522.9 MB)

**Provenance & Source:** NOAA Storm Events Database (ncdc.noaa.gov)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### 26 years of severe weather, one row per event

NOAA's Storm Events database is the official record of U.S. weather damage, compiled from Weather
Forecast Office reports. This extract contains **1,657,168 events from 2000 to 2026**, each with
**72 parameters**, including the raw report and a set of derived impact measures.

- **Identity and place** — event and episode IDs, state and FIPS, county/zone, Weather Forecast
  Office, start/end timestamps and time zone, start and end coordinates, nearest place names.
- **Hazard** — event type and coarse family, magnitude and units, F/EF tornado rating, path length
  and width, flood cause, storm category, reporting source.
- **Impact** — direct and indirect deaths and injuries, property and crop damage, total damage,
  log damage, damage per casualty, fatality and injury flags.
- **Derived context** — duration in hours, great-circle path length, path area, season, day of year,
  hour of day and time-of-day band, decade, Census region, narrative lengths.

**12,207 events were fatal** and **47,425 were tornadoes**. Damage totals exceed
**$594 billion** (nominal dollars), which makes the file suitable for
catastrophe modelling, climate trends and emergency-management analysis.

## 🧾 Columns (72)

`event_id`, `episode_id`, `state`, `state_fips`, `year`, `month`, `month_name`, `event_type`, `cz_type`, `cz_fips`, `cz_name`, `wfo`, `begin_datetime`, `cz_timezone`, `end_datetime`, `injuries_direct`, `injuries_indirect`, `deaths_direct`, `deaths_indirect`, `damage_property`, `damage_crops`, `source`, `magnitude`, `magnitude_type`, `flood_cause`, `category`, `tor_f_scale`, `tor_length`, `tor_width`, `tor_other_wfo`, `tor_other_cz_state`, `tor_other_cz_fips`, `tor_other_cz_name`, `begin_range`, `begin_azimuth`, `begin_location`, `end_range`, `end_azimuth`, `end_location`, `begin_lat`, `begin_lon`, `end_lat`, `end_lon`, `episode_narrative_len`, `event_narrative_len`, `data_source`, `duration_hours`, `total_deaths`, `total_injuries`, `total_casualties`, `damage_total_usd`, `log10_damage_total`, `is_fatal`, `has_injuries`, `state_region`, `season`, `day_of_year`, `begin_hour`, `time_of_day`, `path_length_km`, `path_width_m`, `path_area_sqkm`, `decade`, `is_tornado`, `is_flood`, `is_winter`, `is_heat`, `is_wind`, `has_magnitude`, `damage_per_casualty_usd`, `narrative_total_len`, `event_type_group`

## 💡 Ideas for using this data

1. **Fatality drivers** — which event types and regions kill most often per event, and how has that changed since 2000?
2. **Damage concentration** — plot the Lorenz curve of damage; a handful of episodes usually dominate the total.
3. **Tornado climatology** — path length, width and EF rating by state, season and decade.
4. **Seasonal shift** — heat and flood events by month; is the severe-weather season moving?
5. **Warning performance proxy** — compare narrative length and reporting source with casualties.
6. **Geospatial hot spots** — hex-bin the start coordinates and cluster event types.
7. **Economic loss regression** — predict log damage from event type, region, magnitude and path size.
8. **Compound episodes** — group by `episode_id` to study multi-hazard systems.
9. **Narrative NLP** — the episode and event narratives support topic modelling and named-entity extraction.

## 📁 Files

| File | What it is |
|---|---|
| `severe_weather_events.csv` | 1,657,168 storm events x 72 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`weather`, `noaa`, `climate`, `tornado`, `flood`, `disaster`, `united-states`, `geospatial`, `tabular`

## 🔗 Provenance

- **Source:** **NOAA National Centers for Environmental Information (NCEI)**, Storm Events
  database, `https://www.ncei.noaa.gov/pub/data/swdi/stormevents/csvfiles/`.
- **Files:** `StormEvents_details-ftp_v1.0_d{year}_c*.csv.gz` for 2000-2026 (the latest revision of
  each year's file was used) and the matching locations files where present.
- **Processing:** fixed column mapping, damage strings (`K`/`M`/`B`) parsed to dollars, timestamps
  parsed from `DD-MON-YY HH:MM:SS`, start-to-end great-circle distance computed, all other derived
  columns documented in the dictionary.
- **Snapshot date:** 22 November 2026 (2026 file is partial through November).

## 🔄 Update frequency

**Annual.** NCEI republishes each year's file after post-storm surveys are finalised; the current year's file grows through the season.

## ⚠️ Caveats

- Damage figures are nominal dollars as reported at the time, not inflation-adjusted.
- The 2026 file is incomplete: it covers events processed up to November 2026.
- Reporting practices and database schema change over 26 years; early-2000s records are sparser.
- Casualty and damage numbers are estimates from local officials and can be revised upstream.
- Storm Events is a U.S. only database; it does not cover territories uniformly.
- Events with no reported coordinates have blank latitude/longitude and derived path fields.
- The `magnitude` column mixes units (knots, inches, EF rating) — always read `magnitude_type`.

## 📜 Licence

U.S. Government work (NOAA/NCEI) — public domain in the United States.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `event_id` | `number` | Unique event identifier within the Storm Events database. |
| 2 | `episode_id` | `number` | Identifier of the episode (weather system) the event belongs to. |
| 3 | `state` | `string` | Two-letter state postal code. |
| 4 | `state_fips` | `number` | FIPS code of the state. |
| 5 | `year` | `number` | Year the event began. |
| 6 | `month` | `number` | Month number (1-12). |
| 7 | `month_name` | `string` | Month name. |
| 8 | `event_type` | `string` | NOAA event type (Tornado, Hail, Flash Flood, Excessive Heat, ...). |
| 9 | `cz_type` | `string` | Whether the county/zone code is a county (C) or forecast zone (Z). |
| 10 | `cz_fips` | `number` | County or zone FIPS code. |
| 11 | `cz_name` | `string` | County or forecast-zone name. |
| 12 | `wfo` | `string` | Weather Forecast Office that logged the event. |
| 13 | `begin_datetime` | `datetime` | Event start, local time (ISO format). |
| 14 | `cz_timezone` | `string` | Time zone of the county/zone. |
| 15 | `end_datetime` | `datetime` | Event end, local time (ISO format). |
| 16 | `injuries_direct` | `number` | Direct injuries attributed to the event. |
| 17 | `injuries_indirect` | `number` | Indirect injuries (e.g. clean-up accidents). |
| 18 | `deaths_direct` | `number` | Direct fatalities. |
| 19 | `deaths_indirect` | `number` | Indirect fatalities. |
| 20 | `damage_property` | `string` | Property damage as reported (e.g. 10.00K). |
| 21 | `damage_crops` | `string` | Crop damage as reported (e.g. 1.50M). |
| 22 | `source` | `string` | Reporting source (law enforcement, trained spotter, ASOS, ...). |
| 23 | `magnitude` | `number` | Magnitude value; units depend on event type (kt, inches, EF scale...). |
| 24 | `magnitude_type` | `string` | Unit/type of the magnitude value. |
| 25 | `flood_cause` | `number` | Cause of a flood event, where given. |
| 26 | `category` | `number` | Storm category (e.g. hurricane category), where given. |
| 27 | `tor_f_scale` | `number` | Tornado F/EF rating. |
| 28 | `tor_length` | `number` | Tornado path length in miles as reported. |
| 29 | `tor_width` | `number` | Tornado path width in yards as reported. |
| 30 | `tor_other_wfo` | `number` | Secondary WFO for a tornado crossing office boundaries. |
| 31 | `tor_other_cz_state` | `number` | State of the secondary county/zone. |
| 32 | `tor_other_cz_fips` | `number` | FIPS of the secondary county/zone. |
| 33 | `tor_other_cz_name` | `string` | Name of the secondary county/zone. |
| 34 | `begin_range` | `number` | Distance from the beginning location reference point (miles). |
| 35 | `begin_azimuth` | `string` | Compass direction from the reference point to the start. |
| 36 | `begin_location` | `string` | Nearest place name to the event start. |
| 37 | `end_range` | `number` | Distance from the ending location reference point (miles). |
| 38 | `end_azimuth` | `string` | Compass direction from the reference point to the end. |
| 39 | `end_location` | `string` | Nearest place name to the event end. |
| 40 | `begin_lat` | `number` | Start latitude (decimal degrees). |
| 41 | `begin_lon` | `number` | Start longitude (decimal degrees). |
| 42 | `end_lat` | `number` | End latitude (decimal degrees). |
| 43 | `end_lon` | `number` | End longitude (decimal degrees). |
| 44 | `episode_narrative_len` | `number` | Characters in the episode narrative. |
| 45 | `event_narrative_len` | `number` | Characters in the event narrative. |
| 46 | `data_source` | `string` | Post-processing source of the record. |
| 47 | `duration_hours` | `number` | End minus start in hours (derived from the timestamps). |
| 48 | `total_deaths` | `number` | Direct + indirect deaths. |
| 49 | `total_injuries` | `number` | Direct + indirect injuries. |
| 50 | `total_casualties` | `number` | Deaths + injuries. |
| 51 | `damage_total_usd` | `number` | Property + crop damage in current US dollars. |
| 52 | `log10_damage_total` | `number` | log10(1 + damage_total_usd), for skewed damage models. |
| 53 | `is_fatal` | `boolean` | true when the event killed at least one person. |
| 54 | `has_injuries` | `boolean` | true when at least one injury was recorded. |
| 55 | `state_region` | `number` | U.S. Census region of the state. |
| 56 | `season` | `string` | Meteorological season of the start date. |
| 57 | `day_of_year` | `number` | Day of year of the event start (1-366). |
| 58 | `begin_hour` | `number` | Hour of day the event began (local time). |
| 59 | `time_of_day` | `string` | Overnight / Morning / Afternoon / Evening band. |
| 60 | `path_length_km` | `number` | Great-circle start-to-end distance in km, or reported tornado length converted. |
| 61 | `path_width_m` | `number` | Tornado width converted from yards to metres. |
| 62 | `path_area_sqkm` | `number` | Path length x width in square kilometres. |
| 63 | `decade` | `number` | Decade of the event year (2000, 2010, 2020, ...). |
| 64 | `is_tornado` | `boolean` | true for tornado and funnel-cloud events. |
| 65 | `is_flood` | `boolean` | true for flash flood, flood and heavy rain events. |
| 66 | `is_winter` | `boolean` | true for winter storm, blizzard, ice storm and cold events. |
| 67 | `is_heat` | `boolean` | true for heat and excessive heat events. |
| 68 | `is_wind` | `boolean` | true for thunderstorm wind, high wind and strong wind events. |
| 69 | `has_magnitude` | `boolean` | true when a magnitude value is present. |
| 70 | `damage_per_casualty_usd` | `number` | Damage total divided by casualties. |
| 71 | `narrative_total_len` | `number` | Combined length of the episode and event narratives. |
| 72 | `event_type_group` | `string` | Coarse event family used for grouping. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
