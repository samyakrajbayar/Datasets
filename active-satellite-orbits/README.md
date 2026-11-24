---
license: cc-by-4.0
task_categories:
- tabular
tags:
- tabular
pretty_name: "Active Satellite Orbits"
---

# Active Satellite Orbits

**Subtitle:** 12,901 satellites with full orbital mechanics, geometry & constellation labels

**Tags:** `space`, `satellites`, `astronomy`, `orbital-mechanics`, `engineering`, `geospatial`, `telecommunications`, `science`, `tabular`, `clustering`

**Dataset File:** `satellites.csv` (12,901 rows, 41 columns, 4.0 MB)

---

## 📖 Description

### Everything currently in orbit, with its orbital mechanics worked out

A snapshot of the **CelesTrak** general-perturbations catalogue, derived from US Space Force tracking
data: **12,901 satellites** described by **41 parameters**, including the full set of orbital
elements plus the geometry analysts usually have to compute themselves.

Each row contains:
- **Identity** — object name, international designator (whose prefix is the launch year),
  NORAD catalogue number and the general-perturbations record id.
- **Orbital elements** — epoch, mean motion, eccentricity, inclination, right ascension of the ascending
  node, argument of perigee, mean anomaly, B* drag term and its derivatives, element set number and
  revolution count at epoch.
- **Geometry** — semi-major axis, period, perigee and apogee (computed from mean motion and
  eccentricity) and mean altitude above the Earth's surface.
- **Derived mechanics** — orbital regime (LEO/MEO/GEO/HEO), geostationary and geosynchronous flags,
  sun-synchronous, polar and retrograde flags, mean orbital speed from the vis-viva equation,
  revolutions per day, and inclination and altitude bands.
- **Fleet structure** — an inferred constellation label (Starlink, OneWeb, Planet, Iridium, GPS, ...),
  operator group, number of catalogue objects in that constellation, launch year and satellite age.

**12,199 objects are in low Earth orbit**, **396 are geostationary**, and the largest constellations
in the file are Starlink (11,206), OneWeb (651), BeiDou (56), GPS (32), Galileo (32) — a direct measurement of the
mega-constellation era.

## 🧾 Columns (41)

`object_name`, `object_id`, `norad_cat_id`, `epoch`, `mean_motion`, `eccentricity`, `inclination`, `ra_of_asc_node`, `arg_of_pericenter`, `mean_anomaly`, `ephemeris_type`, `classification_type`, `element_set_no`, `rev_at_epoch`, `bstar`, `mean_motion_dot`, `mean_motion_ddot`, `semimajor_axis`, `period`, `apoapsis`, `periapsis`, `mean_altitude_km`, `perigee_altitude_km`, `apogee_altitude_km`, `orbital_regime`, `is_geostationary`, `is_geosynchronous`, `is_sun_synchronous`, `is_polar`, `is_retrograde`, `constellation`, `operator_group`, `launch_year`, `satellite_age_years`, `orbit_speed_kms`, `revolutions_per_day`, `inclination_band`, `altitude_band`, `is_leo`, `n_same_constellation`, `source_group`

## 💡 Ideas for using this data

1. **Mega-constellation shells** — Starlink altitude versus inclination clusters; count satellites per orbital shell.
2. **Orbital regimes** — LEO/MEO/GEO/HEO counts, and which operators use each.
3. **Launch waves** — satellites per launch year; visualise the post-2019 explosion.
4. **Sun-synchronous imaging fleet** — who operates polar-orbiting Earth-observation satellites?
5. **Decay risk** — age distribution and B* drag values for objects in low, decaying orbits.
6. **Operator concentration** — HHI over inferred operators and constellations.
7. **Geometry** — inclination against altitude exposes the shell structure of the catalogue.
8. **Anomaly detection** — flag objects whose period or eccentricity is inconsistent with their constellation.
9. **Classification** — predict object type (payload vs rocket body) from the orbit alone.

## 📁 Files

| File | What it is |
|---|---|
| `satellites.csv` | 12,901 satellites x 41 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: constellation shells, regimes, launch waves. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`space`, `satellites`, `astronomy`, `orbital-mechanics`, `engineering`, `geospatial`, `telecommunications`, `science`, `tabular`, `clustering`

## 🔗 Provenance

- **Source:** **CelesTrak** GP data, `https://celestrak.org/NORAD/elements/gp.php`, union of the
  Starlink, OneWeb, GEO, GNSS, weather, science, space-station, CubeSat, military, engineering, radar
  and amateur groups; duplicates removed by NORAD catalogue number. Where CelesTrak rate-limits a
  group file, its supplemental GP file or a name query supplies the same records.
- **Upstream:** orbital elements originate from the US Space Force 18th Space Defense Squadron and are
  redistributed by CelesTrak as general-perturbations records.
- **Transformation:** GP JSON reshaped to named columns. Semi-major axis, period, apogee, perigee and
  mean altitude are computed from mean motion and eccentricity; speed uses the vis-viva equation;
  regime, sun-synchronous, polar and band flags are derived; constellation and operator labels are
  inferred from object names.
- **Snapshot date:** 20 November 2026.

## 🔄 Update frequency

**Daily upstream (this file is a single snapshot).** CelesTrak refreshes element sets roughly every two hours; re-run `scripts/20_satellites.py` for a current catalogue.

## ⚠️ Caveats

- Orbital elements are a snapshot at their individual epochs, not a common instant; positions drift within days.
- The catalogue is built from CelesTrak's constellation and operational groups rather than the aggregate `active` file, so objects outside those groups are not included.
- Constellation and operator labels are **inferred from name prefixes** and are heuristic, not authoritative.
- The GP feed does not carry launch site, launching state, radar cross-section or decay dates, so those columns are omitted rather than left empty.
- Launch year is parsed from the international designator, so objects catalogued before designators were standardised have no launch year.
- Semi-major axis and altitudes assume a spherical Earth of radius 6,378.137 km.

## 📜 Licence

CelesTrak data are provided free of charge for research and educational use; attribution to CelesTrak and the US Space Force is expected. The upstream provider gives no warranty of accuracy.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `object_name` | `string` | Satellite name as catalogued by CelesTrak / US Space Force. |
| 2 | `object_id` | `string` | International designator (launch year-number-piece). |
| 3 | `norad_cat_id` | `number` | NORAD catalogue number. |
| 4 | `epoch` | `datetime` | Epoch of the orbital elements. |
| 5 | `mean_motion` | `number` | Mean motion in revolutions per day. |
| 6 | `eccentricity` | `number` | Orbital eccentricity (0 = circular). |
| 7 | `inclination` | `number` | Orbital inclination in degrees. |
| 8 | `ra_of_asc_node` | `number` | Right ascension of the ascending node (degrees). |
| 9 | `arg_of_pericenter` | `number` | Argument of perigee (degrees). |
| 10 | `mean_anomaly` | `number` | Mean anomaly at epoch (degrees). |
| 11 | `ephemeris_type` | `number` | Ephemeris type code used by the propagator. |
| 12 | `classification_type` | `string` | U (unclassified), C (classified) or S (secret). |
| 13 | `element_set_no` | `number` | Element set number, incremented with each new orbit fit. |
| 14 | `rev_at_epoch` | `number` | Revolution count at epoch. |
| 15 | `bstar` | `number` | B* drag term (1/Earth radii). |
| 16 | `mean_motion_dot` | `number` | First derivative of mean motion divided by two (rev/day^2). |
| 17 | `mean_motion_ddot` | `number` | Second derivative of mean motion divided by six (rev/day^3). |
| 18 | `semimajor_axis` | `number` | Semi-major axis in kilometres, computed from the mean motion. |
| 19 | `period` | `number` | Orbital period in minutes, computed as 1440 / mean motion. |
| 20 | `apoapsis` | `number` | Apogee altitude above the Earth's surface (km), computed as a(1+e) - R_earth. |
| 21 | `periapsis` | `number` | Perigee altitude above the Earth's surface (km), computed as a(1-e) - R_earth. |
| 22 | `mean_altitude_km` | `number` | Semi-major axis minus the Earth's equatorial radius. |
| 23 | `perigee_altitude_km` | `number` | Perigee altitude above the Earth's surface. |
| 24 | `apogee_altitude_km` | `number` | Apogee altitude above the Earth's surface. |
| 25 | `orbital_regime` | `string` | LEO, MEO, GEO or HEO, derived from period and eccentricity. |
| 26 | `is_geostationary` | `boolean` | true when the period is ~24 h and the orbit is near-circular and equatorial. |
| 27 | `is_geosynchronous` | `boolean` | true when the orbital period is close to one sidereal day. |
| 28 | `is_sun_synchronous` | `boolean` | true for near-polar, sun-synchronous orbits (~96-102 deg inclination, 400-1100 km). |
| 29 | `is_polar` | `boolean` | true when the inclination is within 10 degrees of 90. |
| 30 | `is_retrograde` | `boolean` | true when the inclination exceeds 90 degrees. |
| 31 | `constellation` | `string` | Commercial or institutional constellation inferred from the object name. |
| 32 | `operator_group` | `string` | Operator/owner inferred from the object name prefix. |
| 33 | `launch_year` | `number` | Year of launch. |
| 34 | `satellite_age_years` | `number` | Years since launch at the snapshot date. |
| 35 | `orbit_speed_kms` | `number` | Mean orbital speed from the vis-viva equation. |
| 36 | `revolutions_per_day` | `number` | Mean motion in revolutions per day. |
| 37 | `inclination_band` | `string` | Inclination band label. |
| 38 | `altitude_band` | `string` | Altitude band from very low LEO to beyond GEO. |
| 39 | `is_leo` | `boolean` | true for low Earth orbit objects (period < 128 minutes and eccentricity < 0.25). |
| 40 | `n_same_constellation` | `number` | Number of catalogue objects sharing the same inferred constellation. |
| 41 | `source_group` | `string` | CelesTrak group file the object was retrieved from. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
