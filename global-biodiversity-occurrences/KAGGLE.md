# Global Biodiversity Occurrences

**Subtitle:** 100,000 GBIF records with taxonomy, coordinates, dates & quality flags

**Tags:** `biology`, `biodiversity`, `ecology`, `nature`, `species`, `gbif`, `geospatial`, `conservation`, `environment`, `tabular`

**Dataset File:** `occurrences.csv` (102,000 rows, 79 columns, 91.0 MB)

---

## 📖 Description

### A worldwide sample of biodiversity records

**102,000 occurrence records** of living organisms, pulled from **GBIF** — the Global Biodiversity
Information Facility, which aggregates observations from museums, herbaria, research institutes and
citizen-science platforms. The sample spans **20 countries**,
**2,109 families** and **18,797 species**, with **79 parameters** per record.

Each row is one recorded occurrence:
- **Taxonomy** — scientific name with authorship, the GBIF-backbone accepted name, rank, and the full
  kingdom → phylum → class → order → family → genus → species chain plus taxon keys.
- **Place** — decimal coordinates, coordinate uncertainty, country and country code, state/province,
  locality, elevation, depth, water body, island group, continent and geodetic datum.
- **Time** — year, month, day, full event date and the last-interpreted timestamp.
- **Record provenance** — basis of record, institution and collection codes, catalogue number, recorder
  and identifier, individual count, sex, life stage, establishment means, dataset and publishing
  organisation, licence, media type and protocol.
- **Quality** — GBIF's issue-flag list, plus flags for missing coordinates, elevation, depth and date parts.
- **Derived** — hemisphere, absolute latitude, marine/elevation/coordinate flags, date completeness,
  record age, uncertainty band, record-type group, specimen/observation/fossil flags, issue count, media
  count, taxonomic depth, species-level flag, and the country's continent, region and sub-region.

Because records were sampled by country rather than by taxon, the file is a broad cross-section of how
biodiversity data actually looks upstream: uneven, geographically biased, and full of quality flags that
are themselves worth studying.

## 🧾 Columns (79)

`key`, `scientificName`, `acceptedScientificName`, `taxonRank`, `kingdom`, `phylum`, `class`, `order`, `family`, `genus`, `species`, `speciesKey`, `taxonKey`, `acceptedTaxonKey`, `country`, `countryCode`, `stateProvince`, `locality`, `decimalLatitude`, `decimalLongitude`, `coordinateUncertaintyInMeters`, `elevation`, `depth`, `year`, `month`, `day`, `eventDate`, `basisOfRecord`, `institutionCode`, `collectionCode`, `catalogNumber`, `recordedBy`, `identifiedBy`, `individualCount`, `sex`, `lifeStage`, `occurrenceStatus`, `establishmentMeans`, `datasetKey`, `datasetName`, `publishingOrgKey`, `license`, `issues`, `mediaType`, `protocol`, `continent`, `waterBody`, `islandGroup`, `typeStatus`, `lastInterpreted`, `geodeticDatum`, `higherClassification`, `occurrenceID`, `taxonConceptID`, `hemisphere`, `abs_latitude`, `is_marine`, `has_coordinates`, `has_elevation`, `has_depth`, `date_completeness`, `record_age_years`, `uncertainty_class`, `basis_group`, `is_specimen`, `is_human_observation`, `is_machine_observation`, `is_fossil`, `n_issues`, `has_issues`, `issues_list`, `n_media`, `taxon_depth`, `is_species_level`, `country_name`, `continent_name`, `region`, `subregion`, `latitude_band`

## 💡 Ideas for using this data

1. **Species richness by latitude** — records per band of `abs_latitude`; reproduce the latitudinal diversity gradient.
2. **Data bias** — which countries, taxa and decades dominate? Compare `basis_group` shares across regions.
3. **Quality analysis** — `n_issues` distributions by publisher, country and basis of record.
4. **Marine vs terrestrial** — compare depth and elevation coverage and taxonomic composition.
5. **Temporal coverage** — records per year since 1990; spot the digitisation waves.
6. **Taxonomic composition** — kingdom and family frequency, and how much of each is species-level identified.
7. **Geospatial clustering** — DBSCAN over coordinates to find biodiversity hotspots (and the cities where observers live).
8. **Sampling-effort model** — predict record density from country features; residual hotspots are true sampling gaps.
9. **Text** — `recordedBy` and `locality` fields support name-entity and place-name extraction.

## 📁 Files

| File | What it is |
|---|---|
| `occurrences.csv` | 102,000 occurrence records x 79 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: diversity gradient, sampling bias, quality flags. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`biology`, `biodiversity`, `ecology`, `nature`, `species`, `gbif`, `geospatial`, `conservation`, `environment`, `tabular`

## 🔗 Provenance

- **Source:** **GBIF occurrence API**, `https://api.gbif.org/v1/occurrence/search`.
- **Query:** `hasCoordinate=true`, `occurrenceStatus=PRESENT`, `year=1990,2025`, sampled across 20
  countries at 5,000 records each (300 per page, offset paging).
- **What GBIF is:** an intergovernmental network that indexes occurrence records published by museums,
  herbaria, research institutes and citizen-science programmes; each record keeps its publisher's licence.
- **Transformation:** selected fields flattened to columns, lists (issues, media) normalised, and 25 derived
  columns added. Country context joined from the World Bank-backed countries table in this repository.
- **Snapshot date:** 20 November 2026.

## 🔄 Update frequency

**Never (static snapshot).** GBIF grows continuously; re-run `scripts/17_biodiversity.py` for a fresh sample.

## ⚠️ Caveats

- This is a **country-stratified sample**, not the full GBIF index (which holds well over a billion records).
- Sampling effort is wildly uneven: a handful of species and regions dominate because they are heavily observed.
- Records reflect where people and institutions collect, not where biodiversity is greatest.
- Each record carries its publisher's licence (`license` column); check it before redistribution of subsets.
- `occurrenceStatus=PRESENT` excludes absence records, so the file cannot be used for presence/absence modelling as-is.
- Coordinate uncertainty is often missing or large; `uncertainty_class` buckets what is reported.

## 📜 Licence

Mixed: each record is published under its own licence (CC0, CC BY or CC BY-NC), recorded in the `license` column. GBIF itself asks for attribution to GBIF and to the publishing institution. Check the per-record licence before any commercial use.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `key` | `number` | GBIF occurrence identifier. |
| 2 | `scientificName` | `string` | Full scientific name as recorded, including authorship. |
| 3 | `acceptedScientificName` | `string` | Name with authorship, matched to the GBIF backbone taxonomy. |
| 4 | `taxonRank` | `string` | Rank of the identified taxon (SPECIES, GENUS, FAMILY...). |
| 5 | `kingdom` | `string` | Kingdom of the record. |
| 6 | `phylum` | `string` | Phylum of the record. |
| 7 | `class` | `string` | Class of the record. |
| 8 | `order` | `string` | Order of the record. |
| 9 | `family` | `string` | Family of the record. |
| 10 | `genus` | `string` | Genus of the record. |
| 11 | `species` | `string` | Species binomial. |
| 12 | `speciesKey` | `number` | GBIF occurrence field `speciesKey` (see the GBIF occurrence schema). |
| 13 | `taxonKey` | `number` | GBIF occurrence field `taxonKey` (see the GBIF occurrence schema). |
| 14 | `acceptedTaxonKey` | `number` | GBIF occurrence field `acceptedTaxonKey` (see the GBIF occurrence schema). |
| 15 | `country` | `string` | Country name as supplied by the publisher. |
| 16 | `countryCode` | `string` | ISO-3166 alpha-2 country code of the record. |
| 17 | `stateProvince` | `string` | GBIF occurrence field `stateProvince` (see the GBIF occurrence schema). |
| 18 | `locality` | `string` | GBIF occurrence field `locality` (see the GBIF occurrence schema). |
| 19 | `decimalLatitude` | `number` | Latitude in decimal degrees (WGS84). |
| 20 | `decimalLongitude` | `number` | Longitude in decimal degrees (WGS84). |
| 21 | `coordinateUncertaintyInMeters` | `number` | Reported uncertainty of the coordinates, in metres. |
| 22 | `elevation` | `string` | Elevation above sea level in metres. |
| 23 | `depth` | `string` | Depth below sea level in metres. |
| 24 | `year` | `number` | Year of the observation. |
| 25 | `month` | `number` | Month of the observation. |
| 26 | `day` | `number` | Day of the observation. |
| 27 | `eventDate` | `datetime` | Full event date as recorded. |
| 28 | `basisOfRecord` | `string` | How the record was made (PRESERVED_SPECIMEN, HUMAN_OBSERVATION...). |
| 29 | `institutionCode` | `string` | GBIF occurrence field `institutionCode` (see the GBIF occurrence schema). |
| 30 | `collectionCode` | `string` | GBIF occurrence field `collectionCode` (see the GBIF occurrence schema). |
| 31 | `catalogNumber` | `string` | GBIF occurrence field `catalogNumber` (see the GBIF occurrence schema). |
| 32 | `recordedBy` | `string` | GBIF occurrence field `recordedBy` (see the GBIF occurrence schema). |
| 33 | `identifiedBy` | `string` | GBIF occurrence field `identifiedBy` (see the GBIF occurrence schema). |
| 34 | `individualCount` | `number` | Number of individuals recorded. |
| 35 | `sex` | `string` | GBIF occurrence field `sex` (see the GBIF occurrence schema). |
| 36 | `lifeStage` | `string` | GBIF occurrence field `lifeStage` (see the GBIF occurrence schema). |
| 37 | `occurrenceStatus` | `string` | GBIF occurrence field `occurrenceStatus` (see the GBIF occurrence schema). |
| 38 | `establishmentMeans` | `string` | GBIF occurrence field `establishmentMeans` (see the GBIF occurrence schema). |
| 39 | `datasetKey` | `string` | GBIF occurrence field `datasetKey` (see the GBIF occurrence schema). |
| 40 | `datasetName` | `string` | Name of the publishing dataset. |
| 41 | `publishingOrgKey` | `string` | GBIF occurrence field `publishingOrgKey` (see the GBIF occurrence schema). |
| 42 | `license` | `string` | Licence under which the record is published. |
| 43 | `issues` | `string` | GBIF data-quality issue flags attached to the record. |
| 44 | `mediaType` | `string` | Media types attached to the record. |
| 45 | `protocol` | `string` | GBIF occurrence field `protocol` (see the GBIF occurrence schema). |
| 46 | `continent` | `string` | GBIF occurrence field `continent` (see the GBIF occurrence schema). |
| 47 | `waterBody` | `string` | GBIF occurrence field `waterBody` (see the GBIF occurrence schema). |
| 48 | `islandGroup` | `string` | GBIF occurrence field `islandGroup` (see the GBIF occurrence schema). |
| 49 | `typeStatus` | `string` | GBIF occurrence field `typeStatus` (see the GBIF occurrence schema). |
| 50 | `lastInterpreted` | `datetime` | Timestamp of GBIF's last interpretation of the record. |
| 51 | `geodeticDatum` | `string` | GBIF occurrence field `geodeticDatum` (see the GBIF occurrence schema). |
| 52 | `higherClassification` | `string` | Higher taxonomy string, pipe-separated. |
| 53 | `occurrenceID` | `string` | GBIF occurrence field `occurrenceID` (see the GBIF occurrence schema). |
| 54 | `taxonConceptID` | `string` | GBIF occurrence field `taxonConceptID` (see the GBIF occurrence schema). |
| 55 | `hemisphere` | `string` | Northern or Southern hemisphere. |
| 56 | `abs_latitude` | `number` | Absolute latitude, useful for species-richness gradients. |
| 57 | `is_marine` | `boolean` | true when a water body or a depth value is recorded. |
| 58 | `has_coordinates` | `boolean` | true when decimal latitude and longitude are present. |
| 59 | `has_elevation` | `boolean` | true when an elevation value is recorded. |
| 60 | `has_depth` | `boolean` | true when a depth value is recorded. |
| 61 | `date_completeness` | `string` | Whether only the year, the year and month, or a full date is known. |
| 62 | `record_age_years` | `number` | Years between the observation year and the snapshot year. |
| 63 | `uncertainty_class` | `string` | Coordinate-uncertainty band in metres. |
| 64 | `basis_group` | `string` | Coarse record type: specimen, observation, machine observation, fossil, other. |
| 65 | `is_specimen` | `boolean` | true for preserved or living specimen records. |
| 66 | `is_human_observation` | `boolean` | true for human observation records. |
| 67 | `is_machine_observation` | `boolean` | true for sensor/camera records. |
| 68 | `is_fossil` | `boolean` | true for fossil specimen records. |
| 69 | `n_issues` | `number` | Number of data-quality flags GBIF attached to the record. |
| 70 | `has_issues` | `boolean` | true when GBIF flagged at least one quality issue. |
| 71 | `issues_list` | `string` | Semicolon-separated GBIF quality issue flags. |
| 72 | `n_media` | `number` | Number of media items attached to the record. |
| 73 | `taxon_depth` | `number` | Number of taxonomic ranks filled in (kingdom to species), 0-7. |
| 74 | `is_species_level` | `boolean` | true when the record is identified to species rank. |
| 75 | `country_name` | `string` | Country name from the GBIF country dimension. |
| 76 | `continent_name` | `string` | Continent of the recording country. |
| 77 | `region` | `string` | UN macro-region of the recording country. |
| 78 | `subregion` | `string` | UN sub-region of the recording country. |
| 79 | `latitude_band` | `string` | Absolute-latitude band. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
