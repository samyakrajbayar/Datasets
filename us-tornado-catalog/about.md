U.S. Tornado Catalog 1950–2024

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

55 columns; one row per recorded tornado (multi-state tracks appear as separate segments).
