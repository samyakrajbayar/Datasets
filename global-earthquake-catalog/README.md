---
annotations_creators:
- no-annotation
language:
- en
license: cc0-1.0
multilinguality:
- monolingual
size_categories:
- 10K<n<100K
source_datasets:
- original
task_categories:
- tabular-classification
task_ids: []
pretty_name: "Global Earthquake Catalog 2015-2026: 337K Events"
tags:
- tabular
- geography
- science
---

# Global Earthquake Catalog 2015–2026 — 337,247 Events, 34 Parameters

**Subtitle:** A decade of worldwide seismicity (M ≥ 2.5) with hypocentre geometry, magnitude scales, station counts, PAGER alerts, tsunami flags and significance scores.

---

## 📖 Description

This is a clean, single-file extract of the **USGS ANSS Comprehensive Catalog** covering **1 January 2015 → 19 November 2026**, filtered to magnitude 2.5 and above. That yields **337,247 earthquakes** — enough for time-series work, spatial statistics and genuine machine-learning experiments, while staying small enough to load in a laptop dataframe (94 MB).

Unlike the raw GeoJSON feeds scattered around the web, every field here is already parsed from the nested `properties` object into its own column, with derived temporal and geophysical features added:

- **Time features** — UTC timestamp, date, year, month, day, hour, weekday, and the last update time.
- **Hypocentre geometry** — latitude, longitude, depth in km, plus a `depth_class` band (shallow < 70 km, intermediate < 300 km, deep ≥ 300 km).
- **Magnitude** — preferred magnitude, the magnitude scale (`magType`: ml, mb, mww, md, …), and a descriptive `magnitude_class` (minor → great).
- **Solution quality** — `n_stations`, `azimuthal_gap_deg`, `min_distance_deg`, `rms_residual`. These are exactly the features you need if you want to predict magnitude reliability.
- **Impact** — `tsunami_flag`, DYFI `felt_reports`, `cdi`, `mmi`, PAGER `alert_level`, and the USGS `significance` score.
- **Provenance** — contributing `network`, event `type` (earthquake, quarry blast, explosion, ice quake…), review status, source count and list, event page URL.

## 🧾 Columns (34)

`event_id`, `time_utc`, `date`, `year`, `month`, `day`, `hour`, `weekday`, `updated_utc`, `place`, `country_region`, `latitude`, `longitude`, `depth_km`, `depth_class`, `magnitude`, `magnitude_type`, `magnitude_class`, `n_stations`, `azimuthal_gap_deg`, `min_distance_deg`, `rms_residual`, `network`, `event_type`, `review_status`, `tsunami_flag`, `felt_reports`, `cdi`, `mmi`, `alert_level`, `significance`, `n_sources`, `sources`, `url`

Full descriptions in `data_dictionary.csv`.

## 💡 Ideas for using this data

1. **Seismic hotspot mapping** — hexbin or kernel-density maps of epicentres; identify the Ring of Fire and mid-ocean ridges.
2. **Gutenberg–Richter law** — fit the magnitude–frequency distribution and estimate b-values per region.
3. **Aftershock sequences** — detect mainshock/aftershock clusters with spatial-temporal windows (e.g. the 2023 Türkiye–Syria sequence).
4. **Magnitude prediction** — regress `magnitude` on depth, station geometry and location features.
5. **Alert-level classification** — predict PAGER `alert_level` from magnitude, depth and population proxies (imbalanced classification).
6. **Tsunami risk screening** — which magnitude/depth combinations actually trigger `tsunami_flag`?
7. **Data quality study** — how do `n_stations` and `azimuthal_gap_deg` relate to review status and magnitude uncertainty?

## ⚠️ Caveats

- Only events of M ≥ 2.5 are included; completeness varies strongly by region and over time because global station coverage improved over the decade.
- `felt_reports`, `cdi`, `mmi` and `alert_level` are mostly populated for significant events; blanks are normal.
- `place` is a free-text human description, not a normalised gazetteer — `country_region` is a convenience extraction of its last component.
- Depths are reported relative to sea level and can be negative for some events.

## 🔗 Provenance & licence

- Source: U.S. Geological Survey, ANSS Comprehensive Earthquake Catalog (ComCat) FDSN event service — public domain (U.S. Government work).
- Query: `minmagnitude=2.5`, 2015-01-01 → 2026-11-19, all event types.
- Snapshot: November 2026. 337,247 rows × 34 columns.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
