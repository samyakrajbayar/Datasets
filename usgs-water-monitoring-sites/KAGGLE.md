# USGS Water-Monitoring Site Inventory

**Subtitle:** 41,000 stream gauges, wells, lakes and springs with geography, hydrologic units and site attributes.

---

## 📖 Description

### 41,000 USGS water-monitoring sites

The USGS National Water Information System tracks stream gauges, wells, lakes and springs across the
United States and its territories. This dataset pages the modern OGC API into a table of **41,000
sites** with **57 parameters**.

- **Identity** — site number, name, agency, site type and status.
- **Geography** — state, county, country, HUC hydrologic units, latitude, longitude, altitude and
  time zone.
- **Site characteristics** — drainage area, well depth and construction fields where reported.
- **Derived** — stream/groundwater/lake/spring/estuary flags, coordinates availability, altitude in
  feet, HUC region and subregion, hemisphere and drainage area in square miles.

**5,455 sites are streams or rivers** and **33,628 are wells**, spread over **2
states and territories** — the reference inventory for hydrology, drought and water-quality work.

## 🧾 Columns (57)

`agency_code`, `agency_name`, `altitude`, `altitude_accuracy`, `altitude_method_code`, `altitude_method_name`, `aquifer_code`, `aquifer_type_code`, `basin_code`, `construction_date`, `contributing_drainage_area`, `country_code`, `country_name`, `county_code`, `county_name`, `depth_source_code`, `district_code`, `drainage_area`, `hole_constructed_depth`, `horizontal_position_method_code`, `horizontal_position_method_name`, `horizontal_positional_accuracy`, `horizontal_positional_accuracy_code`, `hydrologic_unit_code`, `id`, `latitude`, `longitude`, `minor_civil_division_code`, `monitoring_location_name`, `monitoring_location_number`, `national_aquifer_code`, `original_horizontal_datum`, `original_horizontal_datum_name`, `revision_created`, `revision_modified`, `revision_note`, `site_type`, `site_type_code`, `state_code`, `state_name`, `time_zone_abbreviation`, `uses_daylight_savings`, `vertical_datum`, `vertical_datum_name`, `well_constructed_depth`, `is_stream`, `is_groundwater`, `is_lake`, `is_spring`, `is_estuary`, `has_coordinates`, `altitude_ft`, `huc2`, `huc4`, `is_active`, `latitude_band`, `drainage_area_sqmi`

## 💡 Ideas for using this data

1. **Network coverage** — gauges per state and HUC region.
2. **Site types** — streams vs wells vs lakes by region.
3. **Elevation** — altitude distribution and basin gradients.
4. **Drainage areas** — largest basins and their gauge density.
5. **Map** — site map coloured by type.
6. **Join hub** — attach streamflow or water-quality time series by site number.
7. **Data gaps** — states with sparse monitoring.
8. **HUC analysis** — sites per hydrologic subregion.

## 📁 Files

| File | What it is |
|---|---|
| `usgs_sites.csv` | 41,000 sites x 57 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`hydrology`, `usgs`, `water`, `streamflow`, `geospatial`, `environment`

## 🔗 Provenance

- **Source:** **USGS Water Data OGC API**
  (`/collections/monitoring-locations/items`), the modern replacement for NWIS site services.
- **Sampling:** the first 100,000 monitoring locations, paged 1,000 at a time.
- **Processing:** GeoJSON properties flattened, coordinates lifted from geometry, site-type flags,
  HUC codes and unit conversions derived.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Continuous upstream; snapshot here.** Sites are added and retired regularly.

## ⚠️ Caveats

- Only the first 100,000 sites are included; the full inventory is larger.
- Field availability varies widely between site types and states.
- Coordinates are as published; some sites are approximate.
- No measurements (flow, level, quality) are included — this is the site inventory.
- Site numbers are the join key to USGS time-series services.

## 📜 Licence

U.S. Government work (USGS), public domain.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
