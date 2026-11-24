Hurricane Database 1851–2024

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

57 columns; one row per six-hourly storm waypoint.
