---
license: cc-by-4.0
task_categories:
- tabular
tags:
- tabular
pretty_name: "Global Cosmetics & Personal Care"
---

# Global Cosmetics & Personal Care

**Subtitle:** 3,913 beauty products with ingredients, brands, packaging & Eco-Scores

**Tags:** `tabular`, `health`, `consumer`

**Dataset File:** `cosmetics.csv` (4,498 rows, 56 columns, 2.8 MB)

**Provenance & Source:** Open Beauty Facts Database (openbeautyfacts.org)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### 10,000 cosmetics and personal-care products

Open Beauty Facts is the cosmetics sibling of Open Food Facts: a crowd-sourced database of
ingredients and labels. This dataset samples **3,913 products** across 20 categories with
**56 parameters** each.

- **Identity** — barcode, name, generic name, brands, categories and category group, quantity and
  product weight.
- **Market** — countries and country tags, stores, origins, manufacturing places.
- **Packaging and labels** — packaging tags, certifications, allergens, additives, ingredient text and
  counts.
- **Scores** — Eco-Score grade/score and NOVA group.
- **Derived** — brand/category/country/label/allergen/additive/origin counts, vegan/organic/natural/
  hypoallergenic/paraben-free/sulfate-free flags, image and score availability, name and ingredient
  lengths.

**1,411 distinct brands**, **137 organic-labelled products** and **303 vegan-labelled
products** are included. The ingredient lists and claims support formulation, greenwashing and
consumer-label research.

## 🧾 Columns (56)

`code`, `product_name`, `generic_name`, `brands`, `brand_count`, `categories`, `categories_tags`, `category_count`, `category_group`, `countries`, `countries_tags`, `country_count`, `quantity`, `product_quantity_g`, `packaging`, `packaging_tags`, `packaging_count`, `labels`, `labels_tags`, `label_count`, `allergens`, `allergens_tags`, `allergen_count`, `additives_tags`, `additive_count`, `ingredients_text`, `ingredient_count`, `image_url`, `image_front_url`, `ecoscore_grade`, `ecoscore_score`, `nova_group`, `manufacturing_places`, `stores`, `origins`, `origins_tags`, `origin_count`, `lang`, `conservation_conditions`, `warning`, `period_after_opening`, `emb_codes`, `link`, `obsolete`, `is_vegan`, `is_organic`, `is_natural`, `is_hypoallergenic`, `is_paraben_free`, `is_sulfate_free`, `has_ecoscore`, `has_nova`, `is_ultra_processed`, `has_image`, `name_length`, `ingredients_text_length`

## 💡 Ideas for using this data

1. **Ingredient analysis** — most common ingredients by category.
2. **Green claims** — organic/natural/vegan claims vs Eco-Score.
3. **Category comparison** — ingredient complexity in hair vs skin vs makeup.
4. **Brand landscape** — brand concentration and product counts.
5. **Packaging** — packaging types by category and country.
6. **Allergens** — allergen prevalence in cosmetics.
7. **Label text mining** — claims and warnings across categories.
8. **Country differences** — formulation and labelling by market.
9. **Image dataset** — `image_front_url` supports packaging-image classification.

## 📁 Files

| File | What it is |
|---|---|
| `cosmetics.csv` | 3,913 products x 56 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`cosmetics`, `beauty`, `ingredients`, `open-beauty-facts`, `labels`, `consumer`, `health`

## 🔗 Provenance

- **Source:** **Open Beauty Facts** search API v2
  (`https://world.openbeautyfacts.org/api/v2/search`), category queries.
- **Sampling:** the first five pages of 100 products in each of 20 cosmetics categories, deduplicated
  by barcode — a category-stratified sample.
- **Processing:** nested category/country/label/packaging/origin tag arrays flattened; counts, diet and
  claim flags, category groups and text lengths derived.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Continuous upstream; snapshot here.** Volunteers edit the database daily.

## ⚠️ Caveats

- Crowd-sourced data: coverage and accuracy vary strongly by country and brand.
- The category-stratified sample is not representative of the whole database.
- Ingredient text is truncated at 1,000 characters.
- Eco-Score and NOVA are present for only a minority of products.
- `product_quantity_g` is parsed from free text and fails for non-gram units.
- Some products are discontinued or duplicated in the database.
- The main `.org` host was intermittently unavailable; a mirror was used where needed.

## 📜 Licence

Open Database License (ODbL 1.0) — Open Beauty Facts contributors.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `code` | `number` | Product barcode (EAN/UPC). |
| 2 | `product_name` | `string` | Product name. |
| 3 | `generic_name` | `string` | Generic product name. |
| 4 | `brands` | `string` | Brand(s), comma-separated. |
| 5 | `brand_count` | `number` | Number of brands listed. |
| 6 | `categories` | `string` | Category path. |
| 7 | `categories_tags` | `string` | Normalised category tags. |
| 8 | `category_count` | `number` | Number of category tags. |
| 9 | `category_group` | `string` | Coarse product group. |
| 10 | `countries` | `string` | Countries where the product is sold. |
| 11 | `countries_tags` | `string` | Normalised country tags. |
| 12 | `country_count` | `number` | Number of countries. |
| 13 | `quantity` | `string` | Net quantity as printed. |
| 14 | `product_quantity_g` | `number` | Net quantity parsed to grams where possible. |
| 15 | `packaging` | `string` | Packaging description. |
| 16 | `packaging_tags` | `string` | Normalised packaging tags. |
| 17 | `packaging_count` | `number` | Number of packaging tags. |
| 18 | `labels` | `string` | Labels and certifications. |
| 19 | `labels_tags` | `string` | Normalised label tags. |
| 20 | `label_count` | `number` | Number of label tags. |
| 21 | `allergens` | `string` | Allergens as printed. |
| 22 | `allergens_tags` | `string` | Normalised allergen tags. |
| 23 | `allergen_count` | `number` | Number of allergens. |
| 24 | `additives_tags` | `string` | Additive tags. |
| 25 | `additive_count` | `number` | Number of additives. |
| 26 | `ingredients_text` | `string` | Ingredient list (truncated to 1,000 characters). |
| 27 | `ingredient_count` | `number` | Comma-separated ingredient count. |
| 28 | `image_url` | `string` | Product image URL. |
| 29 | `image_front_url` | `string` | Front-of-pack image URL. |
| 30 | `ecoscore_grade` | `string` | Eco-Score letter, where computed. |
| 31 | `ecoscore_score` | `number` | Eco-Score numeric score. |
| 32 | `nova_group` | `number` | NOVA processing group. |
| 33 | `manufacturing_places` | `string` | Manufacturing locations. |
| 34 | `stores` | `string` | Retailers listed. |
| 35 | `origins` | `string` | Country of origin as declared. |
| 36 | `origins_tags` | `string` | Normalised origin tags. |
| 37 | `origin_count` | `number` | Number of origin tags. |
| 38 | `lang` | `string` | Record language. |
| 39 | `conservation_conditions` | `string` | Storage conditions. |
| 40 | `warning` | `number` | Safety warning text. |
| 41 | `period_after_opening` | `number` | Period after opening. |
| 42 | `emb_codes` | `string` | European manufacturer codes. |
| 43 | `link` | `string` | Product page URL. |
| 44 | `obsolete` | `boolean` | true when the product is marked obsolete. |
| 45 | `is_vegan` | `boolean` | true when a vegan label is present. |
| 46 | `is_organic` | `boolean` | true when an organic label is present. |
| 47 | `is_natural` | `boolean` | true when a natural label is present. |
| 48 | `is_hypoallergenic` | `boolean` | true when a hypoallergenic label is present. |
| 49 | `is_paraben_free` | `boolean` | true when a paraben-free claim is present. |
| 50 | `is_sulfate_free` | `boolean` | true when a sulfate-free claim is present. |
| 51 | `has_ecoscore` | `boolean` | true when an Eco-Score exists. |
| 52 | `has_nova` | `boolean` | true when a NOVA group exists. |
| 53 | `is_ultra_processed` | `boolean` | true when NOVA group is 4. |
| 54 | `has_image` | `boolean` | true when an image URL exists. |
| 55 | `name_length` | `number` | Characters in the product name. |
| 56 | `ingredients_text_length` | `number` | Characters in the stored ingredient list. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
