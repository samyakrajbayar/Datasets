---
license: cc-by-4.0
task_categories:
- tabular
tags:
- tabular
pretty_name: "Formula 1 Race Results 1950-2026"
---

# Formula 1 Race Results 1950-2026

**Subtitle:** 26,335 driver-race results with grid, finish, points & constructor data

**Tags:** `tabular`, `sports`, `racing`

**Dataset File:** `f1_results.csv` (26,335 rows, 42 columns, 6.9 MB)

**Provenance & Source:** Jolpica F1 API (Ergast-compatible)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### Every Formula 1 race result, 1950–2026

The Jolpica API mirrors the Ergast Formula 1 database. This dataset expands **26,335 driver-race
results** across **77 seasons**, **820 drivers**, every circuit and constructor, with
**42 parameters** per result.

- **Race** — season, round, Grand Prix name, date and time, circuit id/name, locality, country and
  coordinates.
- **Driver** — id, code, permanent number, name, nationality.
- **Constructor** — id, name and nationality.
- **Result** — grid, finishing position and text, classification order, points, laps, status, total
  time, fastest-lap rank/time/speed.
- **Derived** — win/podium/points/finish/pole flags, grid delta, points per lap, finishing band,
  decade and (where a birth date is available) driver age.

**1,173 race wins** are included. The table supports driver and constructor comparisons, circuit
analysis, reliability studies and historical trends going back to the first world championship.

## 🧾 Columns (42)

`season`, `round`, `race_name`, `race_date`, `race_time`, `circuit_id`, `circuit_name`, `locality`, `country`, `latitude`, `longitude`, `driver_id`, `driver_code`, `permanent_number`, `first_name`, `last_name`, `driver_nationality`, `constructor_id`, `constructor_name`, `constructor_nationality`, `grid`, `position`, `position_text`, `position_order`, `points`, `laps`, `status`, `finish_time_millis`, `finish_time`, `fastest_lap_rank`, `fastest_lap_time`, `fastest_lap_speed_kph`, `is_win`, `is_podium`, `is_points_finish`, `is_finished`, `is_pole`, `grid_delta`, `points_per_lap`, `position_band`, `driver_age_at_race`, `decade`

## 💡 Ideas for using this data

1. **Driver rankings** — wins, podiums and points per start, adjusted for era.
2. **Constructor dominance** — team performance by decade.
3. **Grid to finish** — which circuits produce the most overtaking?
4. **Reliability** — retirement causes by era and team.
5. **Home advantage** — driver performance in their home country.
6. **Circuit characteristics** — fastest-lap speeds and race times by circuit.
7. **Points systems** — normalise points across the many scoring regimes.
8. **Teammate battles** — compare drivers within the same constructor-season.
9. **Age curves** — performance vs age for drivers with known birth dates.

## 📁 Files

| File | What it is |
|---|---|
| `f1_results.csv` | 26,335 results x 42 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`formula-1`, `motorsport`, `racing`, `sports`, `results`, `historical`, `drivers`

## 🔗 Provenance

- **Source:** **Jolpica F1 API** (Ergast-compatible),
  `https://api.jolpi.ca/ergast/f1/results.json`, paginated 1,000 results at a time.
- **Scope:** every result in the database from the 1950 season through the 2026 season to date.
- **Processing:** nested race, circuit, driver, constructor, time and fastest-lap objects flattened;
  win/podium/finish/pole flags, grid delta and rates derived.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**After each Grand Prix.** Jolpica updates results during race weekends.

## ⚠️ Caveats

- Older races have less complete data (no fastest-lap speed, no grid in some early events).
- The points system changed many times; raw points are not comparable across eras.
- `grid = 0` means a pit-lane start, not pole position.
- Status strings are free text and change over time.
- Driver birth dates are not included by this endpoint, so age is usually blank.
- The 2026 season is partial at the snapshot date.
- Jolpica is a community mirror of Ergast; occasional gaps are possible.

## 📜 Licence

Ergast/Jolpica data is open; Formula 1 trademarks belong to their owners.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `season` | `number` | Championship season. |
| 2 | `round` | `number` | Round number within the season. |
| 3 | `race_name` | `string` | Grand Prix name. |
| 4 | `race_date` | `date` | Race date. |
| 5 | `race_time` | `string` | Scheduled start time (UTC), where published. |
| 6 | `circuit_id` | `string` | Circuit identifier. |
| 7 | `circuit_name` | `string` | Circuit name. |
| 8 | `locality` | `string` | Circuit locality. |
| 9 | `country` | `string` | Circuit country. |
| 10 | `latitude` | `number` | Circuit latitude. |
| 11 | `longitude` | `number` | Circuit longitude. |
| 12 | `driver_id` | `string` | Driver identifier. |
| 13 | `driver_code` | `string` | Three-letter driver code. |
| 14 | `permanent_number` | `number` | Permanent driver number (modern era). |
| 15 | `first_name` | `string` | Driver first name. |
| 16 | `last_name` | `string` | Driver last name. |
| 17 | `driver_nationality` | `string` | Driver nationality. |
| 18 | `constructor_id` | `string` | Constructor identifier. |
| 19 | `constructor_name` | `string` | Constructor name. |
| 20 | `constructor_nationality` | `string` | Constructor nationality. |
| 21 | `grid` | `number` | Starting grid position (0 = pit lane). |
| 22 | `position` | `number` | Finishing position, where classified. |
| 23 | `position_text` | `string` | Finishing position as text (R = retired, D = disqualified, ...). |
| 24 | `position_order` | `number` | Official classification order. |
| 25 | `points` | `number` | Championship points scored. |
| 26 | `laps` | `number` | Laps completed. |
| 27 | `status` | `string` | Finish status (Finished, Accident, Engine, ...). |
| 28 | `finish_time_millis` | `number` | Total race time in milliseconds. |
| 29 | `finish_time` | `string` | Total race time as text. |
| 30 | `fastest_lap_rank` | `number` | Rank of the driver's fastest lap. |
| 31 | `fastest_lap_time` | `string` | Driver's fastest lap time. |
| 32 | `fastest_lap_speed_kph` | `number` | Driver's fastest lap average speed. |
| 33 | `is_win` | `boolean` | true for a race win. |
| 34 | `is_podium` | `boolean` | true for a top-three finish. |
| 35 | `is_points_finish` | `boolean` | true when points were scored. |
| 36 | `is_finished` | `boolean` | true when the car was classified as finished. |
| 37 | `is_pole` | `boolean` | true when starting from first on the grid. |
| 38 | `grid_delta` | `number` | Grid position minus finishing position (positive = gained places). |
| 39 | `points_per_lap` | `number` | Points divided by laps completed. |
| 40 | `position_band` | `string` | Finishing-position band. |
| 41 | `driver_age_at_race` | `number` | Driver age at the race date, where birth date is known. |
| 42 | `decade` | `number` | Season decade. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
