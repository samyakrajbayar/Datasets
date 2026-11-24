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
pretty_name: "Art Institute of Chicago Collection"
tags:
- tabular
- arts and entertainment
---

# Art Institute of Chicago Collection

**Subtitle:** 12,000 museum objects with materials, dates, style, subjects & color statistics

**Tags:** `art`, `history`, `visual-arts`, `tabular`

**Dataset File:** `artworks.csv` (20,965 rows, 62 columns, 6.8 MB)

**Provenance & Source:** Art Institute of Chicago Public API (api.artic.edu)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### 12,000 objects from the Art Institute of Chicago

The Art Institute publishes its collection through a free API, including curatorial metadata that most
museums keep internal: classification, style, theme, subject tags, provenance text and even computed
image colour statistics.

This snapshot has **12,000 objects** and **62 parameters**:
- **Identity** — id, title, accession number, reference API link, fiscal year.
- **Creation** — display date, start and end years, derived century, decade, object age, place of origin.
- **Materials** — medium text, a normalised medium class, dimensions, classification and artwork type.
- **Curation** — department, style(s), themes, subject tags, tag count, description and provenance lengths.
- **Artist** — id, name, display string, attribution flags.
- **Rights and access** — public-domain flag, copyright notice, zoomability, educational and multimedia
  resource flags, alternate images, documents, audio.
- **Imaging** — thumbnail presence and pixel dimensions, aspect ratio, colourfulness, dominant colour
  hue/saturation/lightness and its pixel population.
- **Display** — gallery title and coordinates when the object is on view.

**50.5%** of the objects are public domain and many ship with a thumbnail URL pattern
(`https://www.artic.edu/iiif/2/<image_id>/full/843,/0/default.jpg`), so the file doubles as an
image-classification manifest.

## 🧾 Columns (62)

`id`, `title`, `main_reference_number`, `date_display`, `date_start`, `date_end`, `place_of_origin`, `medium_display`, `medium_class`, `dimensions`, `credit_line`, `classification_title`, `classification_titles`, `department_title`, `department_id`, `artwork_type_title`, `style_title`, `style_titles`, `theme_titles`, `subject_titles`, `artist_id`, `artist_title`, `artist_display`, `is_public_domain`, `is_boosted`, `colorfulness`, `color_hue`, `color_saturation`, `color_lightness`, `color_population`, `has_thumbnail`, `thumbnail_width`, `thumbnail_height`, `latitude`, `longitude`, `gallery_title`, `fiscal_year`, `copyright_notice`, `alt_image_count`, `document_count`, `sound_count`, `has_educational_resources`, `has_multimedia_resources`, `is_zoomable`, `max_zoom_window_size`, `description_length`, `provenance_text_length`, `api_link`, `century`, `creation_year`, `creation_decade`, `object_age_years`, `has_artist`, `is_anonymous`, `is_on_view`, `image_aspect_ratio`, `title_length`, `tag_count`, `is_painting`, `is_print`, `is_photograph`, `is_sculpture`

## 💡 Ideas for using this data

1. **Collection composition** — department, classification and medium mix; what does a encyclopaedic museum actually hold?
2. **Acquisition history** — `fiscal_year` and credit lines over time; when did the collection grow fastest?
3. **Colour analysis** — dominant hue and colourfulness by century, department and medium; is the art getting brighter?
4. **Public domain strategy** — public-domain share by department and artist death date (from `artist_display`).
5. **Artist concentration** — works per artist, and how many artists have exactly one object.
6. **Style timeline** — style labels by creation decade; trace the rise and fall of movements.
7. **Subject tags** — co-occurrence network of subject titles (portraits, landscapes, animals).
8. **Image manifest** — build a download list from `thumbnail` ids and train a classifier on medium or century.
9. **Provenance research** — length and content of provenance text as a proxy for documentation quality.

## 📁 Files

| File | What it is |
|---|---|
| `artworks.csv` | 12,000 artworks x 62 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: departments, dates, colour, artists. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`art`, `museum`, `culture`, `image-metadata`, `history`, `collection`, `public-domain`, `tabular`, `visual-arts`, `humanities`

## 🔗 Provenance

- **Source:** **Art Institute of Chicago API v1** (`https://api.artic.edu/api/v1/artworks`),
  pages 1–120 at 100 objects per page, with an explicit field list to keep payloads small.
- **Upstream:** the museum's public collection API, which exposes curatorial catalogue data and
  IIIF image derivatives.
- **Processing:** objects flattened to one row each; list fields (classifications, styles, themes,
  subjects, images, documents) joined with semicolons and counted; colour statistics extracted from
  the API's computed dominant-colour object.
- **Derived columns:** century, decade, object age, attribution and on-view flags, medium normalisation,
  aspect ratio, tag counts, object-type flags.
- **Snapshot date:** 21 November 2026.

## 🔄 Update frequency

**Continuous upstream; snapshot here.** The museum API changes as cataloguing improves. Re-run `scripts/26_artworks.py` for a new snapshot.

## ⚠️ Caveats

- This is the first 12,000 records in API order, not a random or complete sample of the ~120,000-object collection.
- `date_start`/`date_end` are cataloguer estimates and can be negative (BCE) or missing.
- `dimensions` is free text with mixed units; it was deliberately not parsed into numbers.
- Thumbnail URLs are not included directly — reconstruct them from the object's image id via the documented IIIF pattern.
- Colour statistics describe the museum's photograph, not the physical object.
- Some fields (gallery, coordinates) are only populated for objects currently on view.
- Rights vary by object; `is_public_domain` reflects the museum's own determination.

## 📜 Licence

Metadata is published under CC0 by the Art Institute of Chicago; images carry their own rights statements. Attribution to the museum is requested.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `id` | `number` | Art Institute of Chicago artwork id. |
| 2 | `title` | `string` | Object title. |
| 3 | `main_reference_number` | `string` | Museum accession number. |
| 4 | `date_display` | `string` | Date as displayed in the gallery. |
| 5 | `date_start` | `number` | Earliest year of creation (negative = BCE). |
| 6 | `date_end` | `number` | Latest year of creation. |
| 7 | `place_of_origin` | `string` | Place of origin as catalogued. |
| 8 | `medium_display` | `string` | Materials and technique, free text. |
| 9 | `medium_class` | `string` | Materials normalised into painting, print, sculpture, photograph, drawing, etc. |
| 10 | `dimensions` | `string` | Dimensions as catalogued (free text). |
| 11 | `credit_line` | `string` | Acquisition credit line. |
| 12 | `classification_title` | `string` | Primary classification (painting, print, sculpture, ...). |
| 13 | `classification_titles` | `string` | All classifications assigned. |
| 14 | `department_title` | `string` | Curatorial department. |
| 15 | `department_id` | `string` | Curatorial department id. |
| 16 | `artwork_type_title` | `string` | Object type. |
| 17 | `style_title` | `string` | Primary style or period. |
| 18 | `style_titles` | `string` | All styles and periods assigned. |
| 19 | `theme_titles` | `string` | Themes assigned by the museum. |
| 20 | `subject_titles` | `string` | Subject tags assigned by the museum. |
| 21 | `artist_id` | `number` | Artist id (empty for unknown makers). |
| 22 | `artist_title` | `string` | Artist name. |
| 23 | `artist_display` | `string` | Artist name with nationality and dates. |
| 24 | `is_public_domain` | `boolean` | true when the work is in the public domain. |
| 25 | `is_boosted` | `boolean` | true when the museum promotes the object. |
| 26 | `colorfulness` | `number` | Computed colourfulness score of the image. |
| 27 | `color_hue` | `number` | Dominant hue (0-360). |
| 28 | `color_saturation` | `number` | Dominant colour saturation (0-1). |
| 29 | `color_lightness` | `number` | Dominant colour lightness (0-1). |
| 30 | `color_population` | `number` | Share of pixels in the dominant colour cluster. |
| 31 | `has_thumbnail` | `boolean` | true when a thumbnail image is available. |
| 32 | `thumbnail_width` | `number` | Thumbnail width in pixels. |
| 33 | `thumbnail_height` | `number` | Thumbnail height in pixels. |
| 34 | `latitude` | `number` | Gallery latitude, when the object is on view. |
| 35 | `longitude` | `number` | Gallery longitude, when the object is on view. |
| 36 | `gallery_title` | `string` | Gallery where the object is displayed. |
| 37 | `fiscal_year` | `number` | Fiscal year the record was last touched. |
| 38 | `copyright_notice` | `string` | Copyright statement, when applicable. |
| 39 | `alt_image_count` | `number` | Number of alternative images. |
| 40 | `document_count` | `number` | Number of attached documents. |
| 41 | `sound_count` | `number` | Number of audio files. |
| 42 | `has_educational_resources` | `boolean` | true when educational resources exist. |
| 43 | `has_multimedia_resources` | `boolean` | true when multimedia resources exist. |
| 44 | `is_zoomable` | `boolean` | true when a deep-zoom image is available. |
| 45 | `max_zoom_window_size` | `number` | Maximum zoom window size. |
| 46 | `description_length` | `number` | Characters in the catalogue description. |
| 47 | `provenance_text_length` | `number` | Characters in the provenance text. |
| 48 | `api_link` | `string` | Canonical API URL for the object. |
| 49 | `century` | `string` | Creation century derived from date_start. |
| 50 | `creation_year` | `number` | Preferred creation year (date_start, else date_end). |
| 51 | `creation_decade` | `number` | Decade of creation. |
| 52 | `object_age_years` | `number` | Years between creation and 2026. |
| 53 | `has_artist` | `boolean` | true when an artist is attributed. |
| 54 | `is_anonymous` | `boolean` | true when no artist is attributed. |
| 55 | `is_on_view` | `boolean` | true when a gallery is assigned. |
| 56 | `image_aspect_ratio` | `number` | Thumbnail width divided by height. |
| 57 | `title_length` | `number` | Characters in the title. |
| 58 | `tag_count` | `number` | Style + theme + subject tag count. |
| 59 | `is_painting` | `boolean` | true when the classification is painting. |
| 60 | `is_print` | `boolean` | true when the classification is print. |
| 61 | `is_photograph` | `boolean` | true when the medium is photographic. |
| 62 | `is_sculpture` | `boolean` | true when the object is sculpture. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
