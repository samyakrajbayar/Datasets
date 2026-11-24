# Global City Climate 2015–2025 — 192,864 City-Days, 40 Variables

**Subtitle:** Eleven years of daily weather and climate for 48 major cities worldwide, with temperature, humidity, rainfall, wind, soil moisture, radiation and derived climate flags from NASA POWER.

---

## 📖 Description

This is a **long-format daily climate panel**: 48 cities × 4,018 days each = **192,864 rows**, with **40 columns**. It was built for time-series analysis, climate-trend work and any ML task that benefits from weather context (energy demand, agriculture, retail, health, tourism).

The 48 cities were chosen for global spread and contrast — megacities in Asia (Tokyo, Delhi, Shanghai, Dhaka, Mumbai, Beijing, Jakarta, Seoul, Bangkok), the Americas (New York, Los Angeles, Chicago, Mexico City, São Paulo, Rio, Buenos Aires, Toronto, Bogotá, Lima), Africa and the Middle East (Cairo, Lagos, Nairobi, Johannesburg, Kinshasa, Tehran, Istanbul, Dubai), and Europe/Oceania (London, Paris, Berlin, Madrid, Moscow, Sydney, Singapore) — including extreme cases such as **Reykjavik and Anchorage** so the model has genuinely cold climates to learn from.

**Measured daily parameters (20, NASA POWER):**
`T2M`, `T2M_MAX`, `T2M_MIN`, `T2MDEW`, `T2MWET`, `T2M_RANGE`, `TS`, `RH2M`, `QV2M`, `PRECTOTCORR`, `EVLAND`, `GWETROOT`, `GWETTOP`, `WS2M`, `WS10M`, `WD2M`, `PS`, `CLOUD_AMT`, `ALLSKY_SFC_SW_DWN`, `ALLSKY_KT`

**Derived features:**
`temperature_range_c`, `rain_day`, `extreme_heat` (max ≥ 35 °C), `extreme_cold` (min ≤ −10 °C), `wind_class` (calm → strong), `sunshine_class` (cloudy / mixed / sunny from the clearness index), and `aridity_index` (evaporation ÷ precipitation).

**Time keys:** date, year, month, day, day of year, hemisphere-aware `season`, and weekday — so you can slice by monsoon, heating season or weekend without extra work.

## 🧾 Columns (40)

`city`, `country`, `iso2`, `latitude`, `longitude`, `elevation_m`, `date`, `year`, `month`, `day`, `day_of_year`, `season`, `weekday`, `T2M`, `T2M_MAX`, `T2M_MIN`, `T2MDEW`, `T2MWET`, `T2M_RANGE`, `TS`, `RH2M`, `QV2M`, `PRECTOTCORR`, `EVLAND`, `GWETROOT`, `GWETTOP`, `WS2M`, `WS10M`, `WD2M`, `PS`, `CLOUD_AMT`, `ALLSKY_SFC_SW_DWN`, `ALLSKY_KT`, `temperature_range_c`, `rain_day`, `extreme_heat`, `extreme_cold`, `wind_class`, `sunshine_class`, `aridity_index`

## 💡 Ideas for using this data

1. **Climate trends** — 11-year warming slopes per city; compare tropical vs temperate cities and coastal vs continental.
2. **Heatwave detection** — rolling percentiles of `T2M_MAX` to find extreme-heat episodes; count `extreme_heat` days per year.
3. **Rainfall seasonality** — monsoon curves for Mumbai/Dhaka vs Mediterranean winter rain in Madrid.
4. **Forecasting benchmark** — predict next-day temperature or rainfall with lags, calendar features and neighbouring cities.
5. **Humidity and comfort** — dew point and wet-bulb temperature as heat-stress indicators.
6. **Solar energy potential** — `ALLSKY_SFC_SW_DWN` and clearness index by city and month.
7. **Soil and evaporation** — root-zone wetness and aridity index as drought proxies.
8. **Weather → demand** — join with your own energy, sales or mobility data using `city` + `date`.

## ⚠️ Caveats

- Values are **NASA POWER reanalysis/model grid cells** for the requested coordinates, not station observations. Expect small offsets versus a city's official weather station.
- Missing values were cleaned to blanks (the API's −999 sentinel).
- `PRECTOTCORR` is bias-corrected precipitation; trace amounts are common, hence the 0.1 mm threshold for `rain_day`.
- Some cities are coastal and the grid cell may fall partly over water, which smooths temperature extremes.
- Covers 2015-01-01 → 2025-12-31 only.

## 🔗 Provenance & licence

- Source: NASA POWER (Prediction Of Worldwide Energy Resources) Daily API, community `RE`, NOAA GEOS-5 / MERRA-2 based — publicly available, no key required.
- Snapshot: November 2026. 48 cities, 192,864 rows × 40 columns.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
