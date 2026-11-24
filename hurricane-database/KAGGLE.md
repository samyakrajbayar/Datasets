# Hurricane Database 1851-2024

**Subtitle:** Atlantic and Pacific cyclone tracks with intensity, pressure and wind radii

**Tags:** `weather`, `climate`, `time-series`, `tabular`

**Dataset File:** `hurricanes.csv` (55,230 rows, 57 columns, 14.3 MB)

**Provenance & Source:** NOAA National Hurricane Center HURDAT2 Database

**Expected Update Frequency:** `annually`

---

## 📖 Description

### 170 years of Atlantic and eastern Pacific cyclone tracks

HURDAT2 is the official best-track archive maintained by the NOAA National Hurricane Center:
every six hours of every tropical cyclone since 1851, with position, intensity, central pressure
and (from 2004) the full wind-radius structure.

This snapshot has **55,230 waypoints** from **1,991 storms** across **174 seasons
(1851–2024)** and **57 parameters** per row:

- **Track** — storm id, basin, season, storm number and name, timestamp, latitude and longitude,
  landfall/minimum-pressure/maximum-wind record flags.
- **Intensity** — maximum sustained wind in knots, km/h and mph, central pressure, Saffir-Simpson
  category as label and number, hurricane and major-hurricane flags.
- **Structure** — the 34, 50 and 64 kt wind radii in all four quadrants (48 radius values across
  the file), radius of maximum wind, and a flag for whether the storm has structure data.
- **Motion** — bearing, speed and compass direction since the previous waypoint, plus 6-hourly
  wind and pressure tendencies.
- **Storm summaries** — peak wind, minimum pressure, peak category, duration, active days,
  waypoint count and Accumulated Cyclone Energy, repeated on every row for easy grouping.
- **Time features** — decade, waypoint index, first/last waypoint flags.

3,345 waypoints (6.1%) are at major-hurricane intensity. Because the file mixes
1851 ship reports with satellite-era fixes, it is a natural laboratory for data-quality work as well
as for climate-trend analysis.

## 🧾 Columns (57)

`storm_id`, `basin`, `basin_code`, `storm_number`, `storm_name`, `storm_year`, `record_time_utc`, `iso_date`, `hour_utc`, `record_identifier`, `status`, `status_label`, `latitude`, `longitude`, `max_wind_kt`, `max_wind_kmh`, `max_wind_mph`, `min_pressure_mb`, `category`, `category_num`, `is_hurricane`, `is_major`, `is_named`, `lat_hemisphere`, `lon_hemisphere`, `distance_to_equator_km`, `movement_bearing_deg`, `movement_speed_kmh`, `movement_direction`, `wind_change_kt`, `pressure_change_mb`, `storm_max_wind_kt`, `storm_min_pressure_mb`, `storm_peak_category`, `storm_duration_days`, `storm_record_count`, `storm_active_days`, `storm_ace`, `storm_sequence_in_year`, `decade`, `waypoint_index`, `is_first_point`, `is_last_point`, `radius_34_kt_ne`, `radius_34_kt_se`, `radius_34_kt_sw`, `radius_34_kt_nw`, `radius_50_kt_ne`, `radius_50_kt_se`, `radius_50_kt_sw`, `radius_50_kt_nw`, `radius_64_kt_ne`, `radius_64_kt_se`, `radius_64_kt_sw`, `radius_64_kt_nw`, `max_wind_radius_nm`, `has_wind_radii`

## 💡 Ideas for using this data

1. **Climate trends** — annual ACE, major-hurricane days and peak intensity by decade; how much of the trend is observation quality?
2. **Rapid intensification** — find 24-hour wind increases above 30 kt and ask where and when they happen.
3. **Track maps** — plot all tracks coloured by category, or density-map genesis points.
4. **Landfall climatology** — use `record_identifier == 'L'` to study US Gulf/Atlantic landfalls by decade and state.
5. **Size structure** — wind radii are only available post-2004; model storm size from intensity and latitude.
6. **Translation speed** — are storms slowing down? Regress `movement_speed_kmh` on year and latitude.
7. **Pressure–wind relationship** — fit wind as a function of pressure, basin and latitude; find outliers.
8. **Seasonality** — genesis and peak-timing distributions, and how El Niño years shift the eastern Pacific.
9. **Forecast benchmark** — use the 6-hourly series as ground truth for simple persistence/trend baselines.

## 📁 Files

| File | What it is |
|---|---|
| `hurricanes.csv` | 55,230 six-hourly cyclone waypoints x 57 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: tracks, categories, ACE by decade. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`hurricanes`, `weather`, `climate`, `meteorology`, `natural-disasters`, `geospatial`, `time-series`, `noaa`, `environment`, `tabular`

## 🔗 Provenance

- **Source:** NOAA National Hurricane Center / Atlantic Oceanographic and Meteorological Laboratory,
  **HURDAT2** best-track database, file `hurdat2-1851-2024-040425.txt`
  (`https://www.nhc.noaa.gov/data/hurdat/`).
- **Contents:** all North Atlantic (AL) and eastern/central Pacific (EP/CP) tropical cyclones,
  1851–2024, at 6-hourly resolution.
- **Parsing:** the fixed HURDAT2 layout was parsed directly: storm headers, then comma-separated
  waypoint records with 21 fields, including the 12 quadrant wind radii and radius of maximum wind.
- **Derived columns:** unit conversions, Saffir-Simpson category, motion vector, 6-hourly tendencies,
  storm-level aggregates (peak intensity, ACE, duration), decade and sequence flags.
- **Snapshot date:** 21 November 2026 (2024 season is the latest in this release).

## 🔄 Update frequency

**Annual.** NOAA publishes a revised HURDAT2 file after each season (usually spring); re-run `scripts/22_hurricanes.py` to refresh.

## ⚠️ Caveats

- Pre-1950 tracks rely on ship observations and are far less complete; intensity before the satellite era is smoothed and often underestimated.
- Wind radii (34/50/64 kt quadrants) only exist from 2004 onward; `has_wind_radii` marks availability.
- Pressure is missing (-999 in the source, blank here) for many early or weak systems.
- ACE uses the 6-hourly maximum wind; 3-hourly special waypoints are not present in HURDAT2.
- `record_identifier` flags are sparse and occasionally inconsistent with the surrounding track.
- The file stops at the 2024 season; storms from 2025–2026 are not included in this release.
- Longitude is signed (west negative), unlike the source's 'W' suffix notation.

## 📜 Licence

Public domain — NOAA / National Weather Service. Best-track data is a work of the U.S. Government and free of copyright; attribution is requested.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `storm_id` | `string` | HURDAT2 storm identifier (basin + number + year, e.g. AL011851). |
| 2 | `basin` | `string` | Basin name: North Atlantic, Eastern Pacific or Central Pacific. |
| 3 | `basin_code` | `string` | Two-letter basin code (AL, EP, CP). |
| 4 | `storm_number` | `number` | Storm number within its season. |
| 5 | `storm_name` | `string` | Storm name, or UNNAMED for pre-naming-era systems. |
| 6 | `storm_year` | `number` | Season year. |
| 7 | `record_time_utc` | `datetime` | Observation timestamp in UTC (ISO). |
| 8 | `iso_date` | `number` | Date of the observation (YYYYMMDD, as in the source). |
| 9 | `hour_utc` | `number` | Synoptic hour of the observation (0, 6, 12, 18). |
| 10 | `record_identifier` | `string` | Landfall (L), minimum pressure (P) or maximum wind (W) marker. |
| 11 | `status` | `string` | Two-letter status code (HU, TS, TD, EX, SS, SD, LO, ...). |
| 12 | `status_label` | `string` | Expanded status label. |
| 13 | `latitude` | `number` | Storm centre latitude in degrees (north positive). |
| 14 | `longitude` | `number` | Storm centre longitude in degrees (east positive, so western hemisphere is negative). |
| 15 | `max_wind_kt` | `number` | Maximum sustained wind in knots (1-minute average). |
| 16 | `max_wind_kmh` | `number` | Maximum sustained wind converted to km/h. |
| 17 | `max_wind_mph` | `number` | Maximum sustained wind converted to mph. |
| 18 | `min_pressure_mb` | `number` | Central pressure in millibars. |
| 19 | `category` | `string` | Saffir-Simpson category label at this point. |
| 20 | `category_num` | `number` | Saffir-Simpson category as a number (0 for TS, -1 for depression). |
| 21 | `is_hurricane` | `boolean` | true when sustained wind is at least 64 kt. |
| 22 | `is_major` | `boolean` | true when sustained wind is at least 96 kt (Category 3+). |
| 23 | `is_named` | `boolean` | true when the storm has a name rather than UNNAMED. |
| 24 | `lat_hemisphere` | `string` | N or S. |
| 25 | `lon_hemisphere` | `string` | E or W. |
| 26 | `distance_to_equator_km` | `number` | Absolute latitude converted to km. |
| 27 | `movement_bearing_deg` | `number` | Bearing of motion since the previous waypoint, in degrees. |
| 28 | `movement_speed_kmh` | `number` | Translation speed since the previous waypoint, in km/h. |
| 29 | `movement_direction` | `string` | Compass direction of motion (N, NE, E, ...). |
| 30 | `wind_change_kt` | `number` | Change in maximum wind since the previous waypoint (kt). |
| 31 | `pressure_change_mb` | `number` | Change in central pressure since the previous waypoint (mb). |
| 32 | `storm_max_wind_kt` | `number` | Peak sustained wind over the whole storm. |
| 33 | `storm_min_pressure_mb` | `number` | Lowest central pressure over the whole storm. |
| 34 | `storm_peak_category` | `string` | Peak Saffir-Simpson category over the whole storm. |
| 35 | `storm_duration_days` | `number` | Time between the first and last waypoint, in days. |
| 36 | `storm_record_count` | `number` | Number of 6-hourly waypoints in the storm. |
| 37 | `storm_active_days` | `number` | Number of distinct calendar dates with a waypoint. |
| 38 | `storm_ace` | `number` | Accumulated Cyclone Energy in 10^4 kt^2 (sum of squared winds / 10^4). |
| 39 | `storm_sequence_in_year` | `number` | Storm number within the season. |
| 40 | `decade` | `number` | Decade of the season year. |
| 41 | `waypoint_index` | `number` | Position of this waypoint within the storm track (1-based). |
| 42 | `is_first_point` | `boolean` | true for the first waypoint of the storm. |
| 43 | `is_last_point` | `boolean` | true for the last waypoint of the storm. |
| 44 | `radius_34_kt_ne` | `number` | Radius of 34 KT NE winds in nautical miles (quadrant NE/SE/SW/NW). |
| 45 | `radius_34_kt_se` | `number` | Radius of 34 KT SE winds in nautical miles (quadrant NE/SE/SW/NW). |
| 46 | `radius_34_kt_sw` | `number` | Radius of 34 KT SW winds in nautical miles (quadrant NE/SE/SW/NW). |
| 47 | `radius_34_kt_nw` | `number` | Radius of 34 KT NW winds in nautical miles (quadrant NE/SE/SW/NW). |
| 48 | `radius_50_kt_ne` | `number` | Radius of 50 KT NE winds in nautical miles (quadrant NE/SE/SW/NW). |
| 49 | `radius_50_kt_se` | `number` | Radius of 50 KT SE winds in nautical miles (quadrant NE/SE/SW/NW). |
| 50 | `radius_50_kt_sw` | `number` | Radius of 50 KT SW winds in nautical miles (quadrant NE/SE/SW/NW). |
| 51 | `radius_50_kt_nw` | `number` | Radius of 50 KT NW winds in nautical miles (quadrant NE/SE/SW/NW). |
| 52 | `radius_64_kt_ne` | `number` | Radius of 64 KT NE winds in nautical miles (quadrant NE/SE/SW/NW). |
| 53 | `radius_64_kt_se` | `number` | Radius of 64 KT SE winds in nautical miles (quadrant NE/SE/SW/NW). |
| 54 | `radius_64_kt_sw` | `number` | Radius of 64 KT SW winds in nautical miles (quadrant NE/SE/SW/NW). |
| 55 | `radius_64_kt_nw` | `number` | Radius of 64 KT NW winds in nautical miles (quadrant NE/SE/SW/NW). |
| 56 | `max_wind_radius_nm` | `number` | Radius of maximum wind in nautical miles, when reported. |
| 57 | `has_wind_radii` | `boolean` | true when any quadrant wind radius is reported (post-2004 records). |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
