# U.S. Tornado Catalog 1950-2024

**Subtitle:** Every recorded US tornado with coordinates, path size, F/EF scale & damage

**Tags:** `weather`, `climate`, `time-series`, `tabular`

**Dataset File:** `tornadoes.csv` (71,813 rows, 55 columns, 18.3 MB)

**Provenance & Source:** NOAA Storm Prediction Center (SPC) Tornado Database

**Expected Update Frequency:** `annually`

---

## 📖 Description

### Every recorded U.S. tornado, 1950–2024

The NOAA Storm Prediction Center's tornado database is the canonical record of U.S. tornadoes:
**71,813 events** with start and end coordinates, path dimensions, F/EF magnitude, casualties and
damage estimates. This file keeps all 29 source fields and adds **26
derived parameters** for a total of **55 columns**.

Each row includes:
- **Identity and timing** — year, month, day, full date, local start time and time-zone code,
  decade, month name, meteorological season, day-of-year, hour band.
- **Location** — state code and FIPS, full state name, region, start/end latitude and longitude,
  track midpoint and compass bearing.
- **Magnitude** — raw F/EF value, the scale in force that year, a label such as `EF4`,
  significant (2+) and violent (4+) flags.
- **Path** — length in miles, width in yards, computed area in square miles, length-to-width ratio.
- **Impact** — injuries, fatalities, casualties, property and crop damage in unadjusted millions,
  a damage band, fatalities/injuries per mile, killer and injurious flags, crop-loss flag.
- **Legacy codes** — the original SPC F1–F4 and FC fields, preserved for reproducibility.

**22,517 events** are from the EF era (2007+), and the file spans the shift from the original
Fujita scale to the Enhanced Fujita scale — a built-in discontinuity that makes trend analysis
genuinely interesting.

## 🧾 Columns (55)

`om`, `yr`, `mo`, `dy`, `date`, `time`, `tz`, `st`, `stf`, `stn`, `mag`, `inj`, `fat`, `loss`, `closs`, `slat`, `slon`, `elat`, `elon`, `len`, `wid`, `ns`, `sn`, `sg`, `f1`, `f2`, `f3`, `f4`, `fc`, `state_name`, `region`, `decade`, `month_name`, `season`, `day_of_year`, `hour_local`, `time_of_day`, `scale`, `magnitude_label`, `is_violent`, `is_significant`, `path_area_sq_miles`, `midpoint_lat`, `midpoint_lon`, `path_bearing_deg`, `path_direction`, `is_killer`, `is_injurious`, `fatalities_per_mile`, `injuries_per_mile`, `casualties`, `damage_class`, `has_crop_loss`, `length_width_ratio`, `record_seq`

## 💡 Ideas for using this data

1. **Tornado Alley is moving?** — spatial density by decade; compare the classic Plains hotspot with the Southeast.
2. **Rating drift** — how the F-to-EF transition in 2007 changed the distribution of ratings, and how to correct for it.
3. **Casualty modelling** — predict fatalities from path length, width, magnitude and time of day.
4. **Night-time risk** — `time_of_day` versus casualties; are overnight tornadoes deadlier per unit of damage?
5. **Damage curves** — property loss as a function of magnitude and path area.
6. **Seasonality** — day-of-year density plots by region; find the Southeast's winter secondary season.
7. **Track geometry** — distribution of path bearings and length/width ratios; do long-track events cluster?
8. **Outbreak detection** — group by date and state to find the biggest tornado outbreaks since 1950.
9. **Reporting bias** — annual counts before/after NEXRAD (1990s); how many weak tornadoes were simply missed?

## 📁 Files

| File | What it is |
|---|---|
| `tornadoes.csv` | 71,813 tornadoes x 55 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: trends, geography, casualties, ratings. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`tornado`, `weather`, `natural-disasters`, `climate`, `meteorology`, `usa`, `geospatial`, `time-series`, `tabular`, `risk-analysis`

## 🔗 Provenance

- **Source:** NOAA Storm Prediction Center, **SPC Severe Weather Database**,
  file `1950-2024_actual_tornadoes.csv` (`https://www.spc.noaa.gov/wcm/`).
- **Upstream curation:** SPC compiles local storm reports and NWS damage surveys; the file is the
  standard research extract used in climatology and actuarial work.
- **Processing:** every one of the 29 source columns is preserved; coordinates are kept as decimals;
  dates and times are parsed for derived features.
- **Derived columns:** state name, region, decade, season, day-of-year, hour band, magnitude label,
  significant/violent flags, path area, midpoint, bearing, casualty rates, damage band, ratio.
- **Snapshot date:** 21 November 2026.

## 🔄 Update frequency

**Annual.** SPC updates the database when each year's surveys are finalised (usually spring); re-run `scripts/23_tornadoes.py`.

## ⚠️ Caveats

- F-scale (1950–2006) and EF-scale (2007+) ratings are not strictly comparable; the `scale` column marks the break.
- Damage (`loss`, `closs`) is in unadjusted historical dollars — do not compare across decades without deflating.
- Weak tornadoes were under-reported before the NEXRAD era, so the apparent upward trend in counts is largely observational.
- Time is local clock time and 00:00 is used when unknown, which conflates midnight events with missing data.
- Path length and width are survey estimates and are rounded (length to 0.1 mi, width to 1 yd).
- Multi-state and multi-segment tornadoes appear as several rows linked by `sn`/`sg`.
- The file covers U.S. tornadoes only, including Puerto Rico and territories where reported.

## 📜 Licence

Public domain — NOAA Storm Prediction Center (U.S. Government work).

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `om` | `number` | Sequential record number in the SPC database. |
| 2 | `yr` | `number` | Year of the tornado. |
| 3 | `mo` | `number` | Month (1-12). |
| 4 | `dy` | `number` | Day of month. |
| 5 | `date` | `date` | Local calendar date (YYYY-MM-DD). |
| 6 | `time` | `string` | Local start time (HH:MM:SS); 00:00 when unknown. |
| 7 | `tz` | `number` | Time-zone code used by the source. |
| 8 | `st` | `string` | Two-letter state code. |
| 9 | `stf` | `number` | State FIPS code. |
| 10 | `stn` | `number` | Station number in the source. |
| 11 | `mag` | `number` | F-scale (1950-2006) or EF-scale (2007+) magnitude, 0-5. |
| 12 | `inj` | `number` | Number of injuries. |
| 13 | `fat` | `number` | Number of fatalities. |
| 14 | `loss` | `number` | Property damage in millions of US dollars, unadjusted. |
| 15 | `closs` | `number` | Crop damage in millions of US dollars, unadjusted. |
| 16 | `slat` | `number` | Start latitude (degrees). |
| 17 | `slon` | `number` | Start longitude (degrees). |
| 18 | `elat` | `number` | End latitude (degrees). |
| 19 | `elon` | `number` | End longitude (degrees). |
| 20 | `len` | `number` | Path length in miles. |
| 21 | `wid` | `number` | Path width in yards. |
| 22 | `ns` | `number` | Number of states affected (1 or 2). |
| 23 | `sn` | `number` | State number for multi-state tracks. |
| 24 | `sg` | `number` | Segment number for multi-segment tracks. |
| 25 | `f1` | `number` | F-scale injury code (legacy field). |
| 26 | `f2` | `number` | F-scale fatality code (legacy field). |
| 27 | `f3` | `number` | F-scale loss code (legacy field). |
| 28 | `f4` | `number` | F-scale crop-loss code (legacy field). |
| 29 | `fc` | `number` | Flood/other code (legacy field). |
| 30 | `state_name` | `string` | Full state name. |
| 31 | `region` | `string` | Census-style region: Northeast, Midwest, South or West. |
| 32 | `decade` | `number` | Decade of the year. |
| 33 | `month_name` | `string` | Month name. |
| 34 | `season` | `string` | Meteorological season (DJF, MAM, JJA, SON). |
| 35 | `day_of_year` | `number` | Day number within the year (1-366). |
| 36 | `hour_local` | `number` | Start hour in local time, 0-23. |
| 37 | `time_of_day` | `string` | Hour band: Overnight, Morning, Afternoon, Evening. |
| 38 | `scale` | `string` | Magnitude scale in force that year: F (through 2006) or EF (2007+). |
| 39 | `magnitude_label` | `string` | Scale plus rating, e.g. EF4 or F2. |
| 40 | `is_violent` | `boolean` | true for F4/EF4 and stronger. |
| 41 | `is_significant` | `boolean` | true for F2/EF2 and stronger. |
| 42 | `path_area_sq_miles` | `number` | Path length x width, converted to square miles. |
| 43 | `midpoint_lat` | `number` | Latitude midway between start and end. |
| 44 | `midpoint_lon` | `number` | Longitude midway between start and end. |
| 45 | `path_bearing_deg` | `number` | Initial bearing from start to end, in degrees. |
| 46 | `path_direction` | `string` | Compass direction of the track. |
| 47 | `is_killer` | `boolean` | true when at least one fatality was reported. |
| 48 | `is_injurious` | `boolean` | true when at least one injury was reported. |
| 49 | `fatalities_per_mile` | `number` | Fatalities divided by path length. |
| 50 | `injuries_per_mile` | `number` | Injuries divided by path length. |
| 51 | `casualties` | `number` | Fatalities plus injuries. |
| 52 | `damage_class` | `string` | Property-damage band in the source's unadjusted millions of dollars. |
| 53 | `has_crop_loss` | `boolean` | true when crop damage was reported. |
| 54 | `length_width_ratio` | `number` | Path length in yards divided by width — how elongated the track is. |
| 55 | `record_seq` | `number` | Row number in the filtered file. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
