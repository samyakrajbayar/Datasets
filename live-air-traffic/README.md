---
annotations_creators:
- no-annotation
language:
- en
license: cc-by-sa-4.0
multilinguality:
- monolingual
size_categories:
- 10K<n<100K
source_datasets:
- original
task_categories:
- tabular-classification
task_ids: []
pretty_name: "Live Air Traffic Snapshot - Global Aircraft States"
tags:
- tabular
- geography
---

# Live Air Traffic Snapshot — Global Aircraft States

**Subtitle:** 8,636 aircraft with positions, altitudes, speeds, vertical rates and emitter categories from OpenSky.

---

## 📖 Description

### 8,636 aircraft tracked in one live snapshot

The OpenSky Network aggregates ADS-B, MLAT and FLARM receivers worldwide. This dataset is a single
snapshot of every aircraft the network could see, expanded to **38 parameters**.

- **Identity** — ICAO24 address, callsign, origin country and callsign prefix.
- **Position** — latitude, longitude, hemisphere, position source and fix ages.
- **Flight state** — barometric and geometric altitude, ground speed, track, vertical rate, squawk
  and on-ground flag.
- **Derived** — altitude/speed bands in feet, km/h, knots and feet per minute, climb/descent flags,
  emergency-squawk flag, sensor counts and emitter category labels.

Aircraft from **109 countries** are visible, **7,623 of them airborne** at snapshot
time. The table is a cross-section of global aviation for spatial analysis, trajectory
reconstruction and live-dashboard projects.

## 🧾 Columns (38)

`icao24`, `callsign`, `origin_country`, `time_position`, `last_contact`, `longitude`, `latitude`, `baro_altitude_m`, `on_ground`, `velocity_ms`, `true_track`, `vertical_rate_ms`, `sensors`, `geo_altitude_m`, `squawk`, `spi`, `position_source`, `category`, `category_label`, `altitude_ft`, `geo_altitude_ft`, `speed_kmh`, `speed_knots`, `vertical_rate_fpm`, `age_seconds`, `position_age_seconds`, `has_position`, `is_climbing`, `is_descending`, `is_moving`, `is_ground`, `altitude_band`, `speed_band`, `hemisphere`, `callsign_prefix`, `callsign_length`, `is_emergency_squawk`, `sensor_count`

## 💡 Ideas for using this data

1. **Traffic density** — aircraft per country and per altitude band.
2. **Altitude profile** — cruise-level distribution by aircraft category.
3. **Climb and descent** — vertical-rate patterns near major airports.
4. **Callsign decoding** — airline prefixes and their traffic share.
5. **Position freshness** — receiver coverage by region (position age).
6. **Emergency squawks** — screening for 7500/7600/7700 codes.
7. **Map visualisation** — plot every aircraft on a world map.
8. **Anomaly detection** — unusual speeds or altitudes for the category.

## 📁 Files

| File | What it is |
|---|---|
| `aircraft_states.csv` | 8,636 aircraft x 38 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`aviation`, `ads-b`, `opensky`, `flight-tracking`, `geospatial`, `live-data`

## 🔗 Provenance

- **Source:** **OpenSky Network** anonymous REST API (`/api/states/all`).
- **Processing:** one live snapshot; the 18-element state arrays expanded into named columns, units
  converted, bands and flags derived.
- **Snapshot date:** 24 November 2026 (single moment, UTC).

## 🔄 Update frequency

**Real time.** A new snapshot can be pulled from OpenSky at any moment.

## ⚠️ Caveats

- This is a single snapshot, not a time series; repeat collection is required for trajectories.
- Coverage depends on volunteer receivers and is dense over Europe and North America, sparse elsewhere.
- Anonymous API access is rate-limited and may be unavailable at peak times.
- Callsigns and positions are broadcast by aircraft and can be missing or erroneous.
- `on_ground` values are read literally from the feed and are sometimes wrong.
- Military and privacy-filtered aircraft may be absent.

## 📜 Licence

OpenSky Network data, CC BY-SA 4.0 — attribution required.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
