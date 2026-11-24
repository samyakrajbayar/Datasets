# Space Weather Time Series — X-Ray Flux, Kp and F10.7

**Subtitle:** 20,148 minute-resolution solar X-ray, geomagnetic Kp and F10.7 observations from NOAA SWPC.

---

## 📖 Description

### 20,148 minutes of solar and geomagnetic activity

NOAA's Space Weather Prediction Center publishes GOES X-ray flux, the planetary K-index and the
F10.7 radio flux. This dataset joins the three into one minute-resolution table of **20,148 rows** and
**22 parameters**.

- **Solar X-rays** — long-channel flux, observed and electron flux, satellite id and flare class.
- **Geomagnetic field** — Kp index, estimated Kp and Kp label for the same minute.
- **Solar radio** — daily F10.7 flux, the classic solar-activity proxy.
- **Derived** — A/B/C/M/X classes, detailed class magnitude, flare/storm/active/quiet flags, flux to
  F10.7 ratio, hour, minute, day of year and a scaled flux column.

The window contains **1,982 minutes at C-class or above** and **0 minutes with Kp ≥ 5**;
peak flux reaches **2.40e-05 W/m²**. It is a compact time series for space-weather forecasting,
power-grid risk and satellite-operations analytics.

## 🧾 Columns (22)

`timestamp`, `satellite`, `xray_flux`, `observed_flux`, `electron_flux`, `xray_class`, `xray_class_detailed`, `kp_index`, `estimated_kp`, `kp_label`, `f107_flux`, `is_flare`, `is_m_class`, `is_x_class`, `is_storm`, `is_geomagnetic_active`, `is_quiet`, `flux_ratio_f107`, `hour`, `minute`, `day_of_year`, `modified_flux`

## 💡 Ideas for using this data

1. **Flare detection** — classify flares from the flux time series.
2. **Storm onset** — Kp response to X-ray flares.
3. **Solar cycle** — F10.7 as a solar-activity proxy.
4. **Forecasting** — predict Kp from the preceding X-ray flux.
5. **Diurnal patterns** — observation coverage by hour.
6. **Anomaly detection** — sudden flux jumps.
7. **Cross-correlation** — flare-to-storm lag analysis.
8. **Dashboard** — live space-weather monitoring.

## 📁 Files

| File | What it is |
|---|---|
| `space_weather.csv` | 20,148 minutes x 22 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`space-weather`, `solar`, `noaa`, `geophysics`, `time-series`, `astronomy`

## 🔗 Provenance

- **Source:** **NOAA SWPC** JSON products: GOES primary X-ray flux (7-day, falling back to
  1-day), planetary K-index (1-minute) and F10.7 cm flux.
- **Processing:** the three series joined on UTC minute; flare classes, storm flags and time features
  derived.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Real time.** SWPC refreshes each product every minute to daily.

## ⚠️ Caveats

- X-ray rows are minute averages from a single GOES satellite; gaps exist during eclipses.
- Kp is a planetary 3-hour index interpolated here to minute resolution by SWPC.
- F10.7 is a daily value repeated across the day.
- Flux calibrations change; `observed_flux` differs from the operational product.
- The feed window is about seven days, so this is a short time series.

## 📜 Licence

U.S. Government work (NOAA SWPC), public domain.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
