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
pretty_name: "Near-Earth Asteroids"
tags:
- tabular
- space
- science
---

# Near-Earth Asteroids

**Subtitle:** 43,000 NEOs with orbital elements, MOID, delta-v, diameter and spectral type

**Tags:** `astronomy`, `physics`, `science`, `tabular`

**Dataset File:** `near_earth_asteroids.csv` (43,367 rows, 60 columns, 16.9 MB)

**Provenance & Source:** NASA JPL Solar System Dynamics (SSD) Small-Body Database API

**Expected Update Frequency:** `quarterly`

---

## 📖 Description

### Every known near-Earth asteroid, with full orbital elements

NASA/JPL's Small-Body Database is the authoritative catalogue of Solar System objects. This dataset
is a complete query of its **near-Earth object** subset: **43,367 asteroids** with **60 parameters** each.

Columns cover:
- **Identity** — SPK id, full name, proper name, permanent/provisional designation, discovery number.
- **Dynamics** — semi-major axis, eccentricity, perihelion and aphelion, inclination, node, argument of
  perihelion, mean anomaly, epoch, time of perihelion, period in days and years, mean motion,
  and a derived orbit class (Atira / Aten / Apollo / Amor).
- **Hazard metrics** — Earth MOID in AU, km and lunar distances, the standard
  potentially-hazardous flag, Earth- and Mars-crossing flags, and the Tisserand parameter.
- **Orbit quality** — observation arc, first and last observation dates, RMS residual,
  condition code, orbit producer and a two-body flag.
- **Physical properties** — absolute magnitude H, measured diameter, a size estimate from H for the
  majority without a measured diameter, albedo, rotation period, SMASSII and Tholen spectral types.
- **Derived features** — diameter and inclination classes, retrograde, near-circular and
  high-eccentricity flags, name features and data-completeness flags.

**24,643 objects** are Apollo-class and **23,447** meet the MOID-based potentially-hazardous
criterion. Diameter is missing for most objects, which makes the H-to-size estimate a useful,
explicitly documented imputation rather than a hidden one.

## 🧾 Columns (60)

`spkid`, `full_name`, `name`, `pdes`, `orbit_class`, `orbit_class_description`, `is_potentially_hazardous`, `absolute_magnitude_h`, `diameter_km`, `diameter_class`, `albedo`, `rotation_period_hours`, `spectral_type_smb`, `spectral_type_tholen`, `epoch_jd`, `semi_major_axis_au`, `eccentricity`, `perihelion_au`, `aphelion_au`, `inclination_deg`, `longitude_ascending_node_deg`, `argument_perihelion_deg`, `mean_anomaly_deg`, `time_of_perihelion_jd`, `orbital_period_days`, `orbital_period_years`, `mean_motion_deg_per_day`, `earth_moid_au`, `earth_moid_km`, `earth_moid_lunar_distances`, `earth_moid_ld_api`, `tisserand_parameter_jupiter`, `observation_arc_days`, `first_observation`, `last_observation`, `orbit_rms_arcsec`, `orbit_condition_code`, `orbit_producer`, `is_two_body_orbit`, `gm_km3_s2`, `extent`, `is_apollo`, `is_aten`, `is_amor`, `is_atira`, `is_earth_crossing`, `crosses_mars_orbit`, `is_retrograde`, `is_near_circular`, `is_high_eccentricity`, `inclination_class`, `size_estimate_m`, `has_diameter`, `has_albedo`, `has_spectral_type`, `has_rotation_period`, `name_length`, `has_proper_name`, `discovery_number`, `h_magnitude_size_m`

## 💡 Ideas for using this data

1. **Hazard ranking** — combine MOID, H and delta-v into your own risk score and compare with the official PHA flag.
2. **Orbit families** — cluster the six orbital elements to recover dynamical groups and resonances.
3. **Size distribution** — cumulative size-frequency distribution; fit a power law and check where survey completeness drops.
4. **Discovery completeness** — `has_diameter`, `has_albedo` and `has_spectral_type` versus size; which objects are still uncharacterised?
5. **Orbit quality** — condition code and arc length versus object size; how well do we really know the small ones?
6. **Comet or asteroid?** — use the Tisserand parameter to separate dormant comets from asteroidal orbits.
7. **Aten vs Apollo** — how do the two Earth-crossing classes differ in period, inclination and size?
8. **Rotation and size** — rotation period versus diameter; find the spin barrier around 2.2 hours.
9. **Spectral types** — compositional mix by orbit class and size.
10. **Close-approach candidates** — filter MOID < 0.01 AU and rank by H for a watchlist.

## 📁 Files

| File | What it is |
|---|---|
| `near_earth_asteroids.csv` | 43,367 near-Earth asteroids x 60 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: orbit classes, sizes, hazard metrics. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`astronomy`, `space`, `asteroids`, `solar-system`, `nasa`, `orbital-mechanics`, `planetary-science`, `tabular`, `physics`, `risk-analysis`

## 🔗 Provenance

- **Source:** **NASA/JPL Small-Body Database (SBDB) Query API**,
  `https://ssd-api.jpl.nasa.gov/sbdb_query.api` with `sb-group=neo` and an explicit field list.
- **Upstream curation:** JPL's Solar System Dynamics group, which maintains the definitive orbit
  solutions and physical-property compilations for small bodies.
- **Coverage:** the full near-Earth object subset returned by the API at query time
  (43,000+ objects, including numbered and provisional designations).
- **Derived columns:** orbit class, aphelion, Earth MOID in km and lunar distances, crossing and
  hazard flags, size and inclination bands, H-based size estimate, completeness flags, discovery number.
- **Snapshot date:** 21 November 2026.

## 🔄 Update frequency

**Daily upstream.** JPL refreshes orbits as new observations arrive; re-run `scripts/27_asteroids.py` for a fresh snapshot.

## ⚠️ Caveats

- `is_potentially_hazardous` follows the MOID < 0.05 AU convention and does not consider object size.
- Diameter is missing for most objects; `h_magnitude_size_m` assumes a fixed 0.14 albedo and is an estimate only.
- Orbital elements are osculating values at a single epoch and drift over time; do not mix epochs.
- The API's `dv` is the minimum delta-v from Earth, computed under simplifying assumptions.
- Spectral types are available for a small minority and come from two different classification systems.
- `crosses_mars_orbit` is a coarse geometric test, not a collision assessment.
- New objects are discovered continuously, so counts differ between snapshots.

## 📜 Licence

Public domain — NASA/JPL-Caltech. Data is produced by a U.S. Government laboratory and is free to use with attribution to JPL/NASA.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `spkid` | `number` | JPL SPK object identifier. |
| 2 | `full_name` | `string` | Full designation, e.g. '433 Eros (A898 PA)'. |
| 3 | `name` | `string` | Proper name, when one has been assigned. |
| 4 | `pdes` | `number` | Permanent designation (number or provisional designation). |
| 5 | `orbit_class` | `string` | Dynamical class: Atira, Aten, Apollo or Amor. |
| 6 | `orbit_class_description` | `string` | Human-readable definition of the orbit class. |
| 7 | `is_potentially_hazardous` | `boolean` | true when Earth MOID is below 0.05 AU (the standard PHA criterion, size not considered). |
| 8 | `absolute_magnitude_h` | `number` | Absolute magnitude H — a proxy for size. |
| 9 | `diameter_km` | `number` | Mean diameter in km, where measured or modelled. |
| 10 | `diameter_class` | `string` | Size band from <100 m to 10 km+. |
| 11 | `albedo` | `number` | Geometric albedo, where known. |
| 12 | `rotation_period_hours` | `number` | Rotation period in hours. |
| 13 | `spectral_type_smb` | `string` | SMASSII spectral type. |
| 14 | `spectral_type_tholen` | `string` | Tholen spectral type. |
| 15 | `epoch_jd` | `number` | Epoch of the osculating elements (Julian date). |
| 16 | `semi_major_axis_au` | `number` | Orbital semi-major axis in AU. |
| 17 | `eccentricity` | `number` | Orbital eccentricity. |
| 18 | `perihelion_au` | `number` | Perihelion distance in AU. |
| 19 | `aphelion_au` | `number` | Aphelion distance computed as a x (1 + e). |
| 20 | `inclination_deg` | `number` | Orbital inclination in degrees. |
| 21 | `longitude_ascending_node_deg` | `number` | Longitude of the ascending node, degrees. |
| 22 | `argument_perihelion_deg` | `number` | Argument of perihelion, degrees. |
| 23 | `mean_anomaly_deg` | `number` | Mean anomaly at epoch, degrees. |
| 24 | `time_of_perihelion_jd` | `number` | Time of perihelion passage (Julian date). |
| 25 | `orbital_period_days` | `number` | Orbital period in days. |
| 26 | `orbital_period_years` | `number` | Orbital period in Julian years. |
| 27 | `mean_motion_deg_per_day` | `number` | Mean motion in degrees per day. |
| 28 | `earth_moid_au` | `number` | Minimum orbit intersection distance with Earth, in AU. |
| 29 | `earth_moid_km` | `number` | Earth MOID converted to km. |
| 30 | `earth_moid_lunar_distances` | `number` | Earth MOID expressed in lunar distances. |
| 31 | `earth_moid_ld_api` | `number` | Earth MOID in lunar distances as returned by JPL (redundant cross-check). |
| 32 | `tisserand_parameter_jupiter` | `number` | Tisserand parameter with respect to Jupiter — separates asteroids from comets. |
| 33 | `observation_arc_days` | `number` | Length of the observation arc used in the orbit solution, in days. |
| 34 | `first_observation` | `date` | Date of the first observation used in the orbit fit. |
| 35 | `last_observation` | `date` | Date of the last observation used in the orbit fit. |
| 36 | `orbit_rms_arcsec` | `number` | RMS residual of the orbit fit, in arcseconds. |
| 37 | `orbit_condition_code` | `number` | Orbit condition code (0 = excellent, 9 = highly uncertain). |
| 38 | `orbit_producer` | `string` | Organisation that produced the orbit solution. |
| 39 | `is_two_body_orbit` | `boolean` | true when the orbit is a simple two-body solution. |
| 40 | `gm_km3_s2` | `number` | Gravitational parameter, when known. |
| 41 | `extent` | `string` | Object extent/shape description. |
| 42 | `is_apollo` | `boolean` | true for Apollo-class asteroids. |
| 43 | `is_aten` | `boolean` | true for Aten-class asteroids. |
| 44 | `is_amor` | `boolean` | true for Amor-class asteroids. |
| 45 | `is_atira` | `boolean` | true for Atira-class (interior to Earth's orbit) asteroids. |
| 46 | `is_earth_crossing` | `boolean` | true when perihelion is inside 1.017 AU. |
| 47 | `crosses_mars_orbit` | `boolean` | true when the orbit spans the Martian semi-major axis. |
| 48 | `is_retrograde` | `boolean` | true when inclination exceeds 90 degrees. |
| 49 | `is_near_circular` | `boolean` | true when eccentricity is below 0.1. |
| 50 | `is_high_eccentricity` | `boolean` | true when eccentricity exceeds 0.6. |
| 51 | `inclination_class` | `string` | Inclination band: low, moderate, high, retrograde. |
| 52 | `size_estimate_m` | `number` | Diameter converted to metres. |
| 53 | `has_diameter` | `boolean` | true when a diameter is published. |
| 54 | `has_albedo` | `boolean` | true when an albedo is published. |
| 55 | `has_spectral_type` | `boolean` | true when a spectral type is published. |
| 56 | `has_rotation_period` | `boolean` | true when a rotation period is published. |
| 57 | `name_length` | `number` | Characters in the full name. |
| 58 | `has_proper_name` | `boolean` | true when the object has a proper name rather than only a designation. |
| 59 | `discovery_number` | `number` | Asteroid number parsed from the permanent designation, when present. |
| 60 | `h_magnitude_size_m` | `number` | Diameter estimated from H assuming a 0.14 albedo, only when no measured diameter exists. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
