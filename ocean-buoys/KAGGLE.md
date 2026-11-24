# NOAA Ocean Buoy Network — Stations and Live Observations

**Subtitle:** 1,357 buoys and platforms with positions, sensors, winds, waves, temperatures and pressure.

---

## 📖 Description

### 1,357 ocean buoys and platforms with live observations

The National Data Buoy Center operates the U.S. network of moored buoys, fixed platforms and coastal
stations. This dataset merges the **station registry** with each station's **latest realtime
observation**, giving **1,357 rows** and **49 parameters**.

- **Station** — id, name, owner, programme, platform type, position, elevation, sensor capabilities
  and DART/tsunami flags.
- **Meteorology** — wind direction, speed and gusts, air and water temperature, dew point, pressure
  and its tendency, visibility.
- **Oceanography** — significant wave height, dominant and average wave periods, wave direction and
  tide.
- **Derived** — metric/imperial conversions, wind chill, air-water temperature gap, observation age,
  freshness flags, wind and wave bands, hemisphere and platform flags.

**255 stations reported within the last two hours**, making this a usable live picture of
sea state, winds and water temperature across the Atlantic, Pacific and Gulf.

## 🧾 Columns (49)

`station_id`, `name`, `owner`, `lat`, `lon`, `elev`, `program`, `type`, `has_met`, `has_currents`, `has_waterquality`, `has_dart`, `obs_time`, `wind_dir_deg`, `wind_speed_ms`, `gust_ms`, `wave_height_m`, `dominant_period_s`, `average_period_s`, `wave_dir_deg`, `pressure_hpa`, `air_temp_c`, `water_temp_c`, `dewpoint_c`, `visibility_nmi`, `pressure_tendency_hpa`, `tide_m`, `wind_speed_kmh`, `gust_kmh`, `wave_height_ft`, `pressure_inhg`, `air_temp_f`, `water_temp_f`, `dewpoint_f`, `air_water_temp_gap`, `wind_chill_c`, `obs_age_hours`, `has_obs`, `is_recent`, `is_stale`, `has_wave_data`, `has_pressure`, `has_wind`, `has_water_temp`, `wind_band`, `wave_band`, `hemisphere`, `is_buoy`, `is_fixed_platform`

## 💡 Ideas for using this data

1. **Sea state** — wave-height distribution by basin.
2. **Wind patterns** — wind speed and direction roses by region.
3. **Air-sea interaction** — air-water temperature gaps.
4. **Storm detection** — low pressure and high wind events.
5. **Data freshness** — sensor outages across the network.
6. **Seasonality** — water temperature by latitude (repeat collection).
7. **Wave period** — swell vs wind-sea regimes.
8. **Map** — live buoy dashboard.

## 📁 Files

| File | What it is |
|---|---|
| `ndbc_buoys.csv` | 1,357 stations x 49 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`oceanography`, `noaa`, `buoys`, `weather`, `marine`, `live-data`

## 🔗 Provenance

- **Source:** **NOAA NDBC** active station XML (`activestations.xml`) and realtime2
  observation files (`/data/realtime2/<station>.txt`).
- **Processing:** registry parsed from XML; the most recent row of each station's observation file
  read and joined; units converted and derived features added.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Real time.** NDBC observations update every 10 minutes to hourly.

## ⚠️ Caveats

- Each station contributes one row (its latest observation), not a time series.
- Sensors differ by station: `MM` means missing and becomes blank.
- Some stations are inactive and return no observation file.
- Realtime data are preliminary and have not passed NOAA quality control.
- Wind chill is computed only for winds above 4.8 km/h and temperatures below 10 C by convention.

## 📜 Licence

U.S. Government work (NOAA NDBC), public domain.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
