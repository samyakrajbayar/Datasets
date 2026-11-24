---
annotations_creators:
- no-annotation
language:
- en
license: other
multilinguality:
- monolingual
size_categories:
- 10K<n<100K
source_datasets:
- original
task_categories:
- tabular-classification
task_ids: []
pretty_name: "UNESCO World Heritage List"
tags:
- tabular
- history
- geography
---

# UNESCO World Heritage List

**Subtitle:** 1,273 World Heritage sites with criteria, states parties, regions, coordinates and danger status.

---

## 📖 Description

### 1,273 UNESCO World Heritage sites

The World Heritage List names the cultural and natural properties of outstanding universal value.
This dataset parses the official XML export into **1,273 sites** with **46 parameters**.

- **Identity** — id, unique number, site name, dossier and URLs.
- **Geography** — states parties with counts, ISO codes, UNESCO region and region flags, location and
  parsed coordinates.
- **Heritage values** — category, criteria text and count, year inscribed, extensions and
  transnational/danger flags.
- **Content** — cleaned justification and short description with lengths.
- **Derived** — age, decade, state/region/criteria/extension counts and category flags.

The list covers **174 states parties**, **51 transnational properties** and
**54 sites on the in-danger list** — a compact base for heritage, tourism and conservation
research.

## 🧾 Columns (46)

`id_number`, `unique_number`, `site`, `dossier`, `http_url`, `image_url`, `iso_code`, `iso_count`, `states`, `state_count`, `regions`, `region_count`, `category`, `criteria_txt`, `criteria_count`, `criteria`, `date_inscribed`, `inscription_year`, `age_years`, `extension`, `extension_count`, `secondary_dates`, `danger`, `transnational`, `location`, `justification`, `short_description`, `description_length`, `latitude`, `longitude`, `has_geolocation`, `is_in_danger`, `is_transnational`, `is_cultural`, `is_natural`, `is_mixed`, `has_criteria`, `has_extension`, `has_image`, `inscription_decade`, `name_length`, `region_africa`, `region_asia`, `region_europe`, `region_americas`, `region_arab`

## 💡 Ideas for using this data

1. **Geography** — sites per country and region.
2. **Criteria** — which criteria combinations dominate.
3. **Danger list** — risk factors and regional patterns.
4. **Transnational** — cooperation networks between states.
5. **Inscription history** — sites added per decade.
6. **Tourism** — join visitor numbers (external).
7. **Text mining** — description language by category and region.
8. **Maps** — geolocated heritage map.

## 📁 Files

| File | What it is |
|---|---|
| `world_heritage_sites.csv` | 1,273 sites x 46 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`unesco`, `heritage`, `culture`, `conservation`, `geography`, `tourism`

## 🔗 Provenance

- **Source:** **UNESCO World Heritage Centre** XML export
  (`https://whc.unesco.org/en/list/xml/`).
- **Processing:** XML rows flattened, HTML stripped from text fields, coordinates, criteria and
  region flags derived.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Annual.** The List is revised at each World Heritage Committee session.

## ⚠️ Caveats

- Coordinates are only present for some properties and are often a representative point.
- Descriptions are truncated at 1,500 characters.
- The danger flag reflects the list at extraction time.
- Transnational properties list several states parties and are counted once.
- Criteria are roman numerals whose meaning is defined by the Operational Guidelines.

## 📜 Licence

UNESCO World Heritage data; cite the UNESCO World Heritage Centre.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
