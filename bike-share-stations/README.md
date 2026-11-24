---
annotations_creators:
- no-annotation
language:
- en
license: cc-by-4.0
multilinguality:
- monolingual
size_categories:
- 10K<n<100K
source_datasets:
- original
task_categories:
- tabular-classification
task_ids: []
pretty_name: "Bike-Share Station Network - North America"
tags:
- tabular
- geography
---

# Bike-Share Station Network — North America

**Subtitle:** 7,167 stations across 7 bike-share systems with docks, location, station type and rental access.

---

## 📖 Description

### 7,167 bike-share stations in 7 North American systems

General Bikeshare Feed Specification (GBFS) feeds publish every dock of a bike-share system. This
dataset merges **7 systems across 7 cities** into one table of **7,167 stations** with
**33 parameters**.

- **System** — operator, city, country and station identifiers.
- **Location** — latitude, longitude, hemisphere bands, address and region.
- **Capacity and type** — docks, capacity band, classic/electric station type and kiosk presence.
- **Access** — rental methods, key/credit-card/phone/transit-card/account support, app and web
  rental links.
- **Derived** — method counts, availability flags, electric surcharge waiver, name length.

The stations represent **137,285 docking points** in total. The table supports network
accessibility analysis, dock-capacity planning and cross-city comparison of bike-share design.

## 🧾 Columns (33)

`system`, `city`, `country`, `operator`, `station_id`, `external_id`, `name`, `short_name`, `lat`, `lon`, `region_id`, `capacity`, `station_type`, `has_kiosk`, `address`, `rental_methods`, `rental_method_count`, `accepts_key`, `accepts_creditcard`, `accepts_phone`, `accepts_transit_card`, `accepts_accountnumber`, `has_android_app`, `has_ios_app`, `has_web_rental`, `electric_surcharge_waiver`, `has_external_id`, `has_region`, `capacity_band`, `name_length`, `is_charging`, `lat_band`, `lon_band`

## 💡 Ideas for using this data

1. **Accessibility** — station density and coverage by city.
2. **Capacity planning** — dock distribution and undersized stations.
3. **Equity** — station locations vs neighbourhood demographics (external join).
4. **System design** — kiosk and payment-method differences across operators.
5. **Electric bikes** — station types and surcharge policies.
6. **Network graphs** — nearest-neighbour clustering of stations.
7. **Maps** — station maps per city.
8. **Cross-city benchmarking** — capacity per station by operator.

## 📁 Files

| File | What it is |
|---|---|
| `bike_share_stations.csv` | 7,167 stations x 33 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`bike-share`, `mobility`, `gbfs`, `transport`, `cities`, `geospatial`

## 🔗 Provenance

- **Source:** **GBFS** `station_information.json` feeds published by each operator
  (Lyft, Bicycle Transit Systems, B-cycle, BIXI, Serco).
- **Processing:** systems fetched independently, station records concatenated with system/city/
  country labels, rental methods split into flags and distance-free derived fields added.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Real time.** GBFS feeds refresh station inventories continuously.

## ⚠️ Caveats

- Station inventories change daily; this is a single snapshot.
- Some systems were unreachable from this network and are absent.
- Fields vary by operator: B-cycle feeds omit capacity and kiosk data.
- `capacity` counts docks, not available bikes.
- Licences differ by feed; check each operator before redistribution.

## 📜 Licence

GBFS feeds are published by each operator under open licences (mostly CC BY 4.0); attribution to the operators.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
