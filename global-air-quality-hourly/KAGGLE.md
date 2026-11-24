# Global Air Quality 2024 — 263,520 Hourly Records Across 30 Cities

**Subtitle:** A full year of hourly pollutants, aerosol optical depth, UV and both European and US air-quality indices for the world's most polluted and cleanest major cities.

---

## 📖 Description

Air pollution is one of the largest environmental health risks worldwide, yet hourly, multi-city, multi-pollutant data is surprisingly hard to assemble. This dataset is a whole calendar year (**1 January – 31 December 2024**) of **hourly** observations for **30 major cities**, giving you **263,520 rows** with **39 columns**.

Cities were chosen to span the pollution spectrum: Delhi, Lahore, Dhaka, Beijing, Mumbai, Cairo, Jakarta, Tehran, Kolkata, Shanghai, Karachi, Lagos, Mexico City, São Paulo, Bangkok, Istanbul, Seoul and Tokyo on one side; London, Paris, Berlin, Madrid, New York, Los Angeles, Chicago, Toronto, Sydney, Nairobi, Johannesburg and Buenos Aires on the other.

**What's measured, per city-hour:**

- **Particulates** — PM10, PM2.5, Saharan dust
- **Gases** — carbon monoxide, nitrogen dioxide, sulphur dioxide, ozone, ammonia
- **Optical/atmospheric** — aerosol optical depth at 550 nm, surface UV index and clear-sky UV index
- **Indices** — European AQI plus five sub-indices (PM2.5, PM10, NO₂, O₃, SO₂) and the US AQI plus five sub-indices
- **Derived flags** — `aqi_band` (good → extremely poor), `is_who_pm25_exceeded` (above the WHO 2021 24-hour guideline of 15 µg/m³), `is_weekend`
- **Time keys** — UTC timestamp, date, year, month, day, hour, weekday

All values come from the CAMS European/global atmospheric composition model served through Open-Meteo's air-quality API, so they are model-grid values rather than single roadside sensors — consistent across cities and time, which is what you want for comparison and forecasting.

## 🧾 Columns (39)

`city`, `country`, `iso2`, `latitude`, `longitude`, `elevation_m`, `timestamp_utc`, `date`, `year`, `month`, `day`, `hour`, `weekday`, `pm10`, `pm2_5`, `carbon_monoxide`, `nitrogen_dioxide`, `sulphur_dioxide`, `ozone`, `dust`, `ammonia`, `aerosol_optical_depth`, `uv_index`, `uv_index_clear_sky`, `european_aqi`, `european_aqi_pm2_5`, `european_aqi_pm10`, `european_aqi_nitrogen_dioxide`, `european_aqi_ozone`, `european_aqi_sulphur_dioxide`, `us_aqi`, `us_aqi_pm2_5`, `us_aqi_pm10`, `us_aqi_nitrogen_dioxide`, `us_aqi_ozone`, `us_aqi_sulphur_dioxide`, `aqi_band`, `is_who_pm25_exceeded`, `is_weekend`

## 💡 Ideas for using this data

1. **Diurnal and weekly cycles** — rush-hour peaks in NO₂ versus afternoon ozone production, and the weekend effect.
2. **City benchmarking** — rank cities by annual mean PM2.5 and by hours above WHO guidelines.
3. **Forecasting** — build an hourly AQI forecaster with lag features (SARIMA, gradient boosting, or a small LSTM).
4. **Pollution source fingerprinting** — NO₂/PM2.5 ratio separates traffic from dust-driven pollution; dust spikes show up as PM10 ≫ PM2.5.
5. **Seasonality and meteorology** — winter inversions in Delhi/Beijing versus summer ozone in Madrid.
6. **UV and aerosol** — how does aerosol optical depth suppress surface UV?
7. **Classification** — predict `aqi_band` or `is_who_pm25_exceeded` from pollutant concentrations, then compare with the official index thresholds.

## ⚠️ Caveats

- Values are **modelled grid-cell concentrations**, not sensor readings; absolute levels can differ from ground stations.
- Some pollutants (notably ammonia and dust) are only meaningful in certain regions and may be near-zero elsewhere.
- Timestamps are UTC; local-time analysis needs a timezone offset per city.
- Cities are a curated sample, not a random or population-weighted sample of the world.

## 🔗 Provenance & licence

- Source: Open-Meteo Air Quality API (CAMS global/European atmospheric composition forecasts) — free for non-commercial use with attribution.
- Snapshot pulled November 2026 for calendar year 2024. 263,520 rows × 39 columns.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
