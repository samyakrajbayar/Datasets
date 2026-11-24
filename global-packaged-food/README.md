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
pretty_name: "Global Packaged Food"
tags:
- tabular
- health
- food
---

# Global Packaged Food

**Subtitle:** 16,091 grocery products with Nutri-Score, NOVA, nutrients and additives

**Tags:** `food`, `nutrition`, `health`, `tabular`

**Dataset File:** `food_products.csv` (18,638 rows, 67 columns, 15.6 MB)

**Provenance & Source:** Open Food Facts Database (openfoodfacts.org)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### Packaged food, label by label

Open Food Facts is a crowd-sourced database of barcoded food products from around the world. This
snapshot samples **16,091 products** across 36 grocery categories and extracts
**67 parameters** per product, from the ingredient list to the Nutri-Score.

Columns span:
- **Product identity** — barcode, name, generic name, brands, categories and category tags, quantity,
  serving size, packaging and packaging tags.
- **Where and how it is sold** — countries and country tags, stores, manufacturing places, origins,
  label and certification tags.
- **Ingredients** — ingredient text and count, allergen count, additive tags and count, palm-oil flag.
- **Nutrition per 100 g** — energy, fat, saturated fat, carbohydrates, sugars, added sugars, fibre,
  protein, salt and sodium.
- **Scores** — Nutri-Score grade and score, Eco-Score grade and score, NOVA processing group, plus
  derived ultra-processed / processed / unprocessed flags.
- **Derived nutrition** — energy shares from sugar, fat and protein; high-sugar, high-salt, high-fat,
  high-fibre and high-protein flags; nutrition completeness percentage.
- **Diet flags** — organic, vegan, vegetarian, gluten-free, beverage and snack indicators.

**7,257 products (45.1%)** are NOVA group 4 (ultra-processed) and **16,090**
have a Nutri-Score, so the file supports both nutrition science and label-regulation analysis.

## 🧾 Columns (67)

`code`, `product_name`, `generic_name`, `brands`, `brand_count`, `categories`, `categories_tags`, `category_count`, `countries`, `countries_tags`, `country_count`, `quantity`, `product_quantity_g`, `serving_size`, `packaging`, `packaging_tags`, `labels`, `labels_tags`, `allergens`, `allergen_count`, `additives_tags`, `additive_count`, `ingredients_text`, `ingredient_count`, `image_url`, `nutriscore_grade`, `nutriscore_score`, `ecoscore_grade`, `ecoscore_score`, `nova_group`, `manufacturing_places`, `stores`, `origins`, `lang`, `energy_kcal_100g`, `fat_100g`, `saturated_fat_100g`, `carbohydrates_100g`, `sugars_100g`, `added_sugars_100g`, `fiber_100g`, `proteins_100g`, `salt_100g`, `sodium_100g`, `is_ultra_processed`, `is_processed`, `is_unprocessed`, `has_nutriscore`, `has_ecoscore`, `is_organic`, `is_vegan`, `is_vegetarian`, `is_gluten_free`, `contains_palm_oil`, `is_beverage`, `is_snack`, `sugar_energy_pct`, `fat_energy_pct`, `protein_energy_pct`, `is_high_sugar`, `is_high_salt`, `is_high_fat`, `is_high_fiber`, `is_high_protein`, `nutrition_fields_present`, `nutrition_completeness_pct`, `label_count`

## 💡 Ideas for using this data

1. **Nutri-Score versus NOVA** — do ultra-processed products always score badly? Cross-tabulate the two systems.
2. **Sugar in disguise** — sugar energy share by category; find products where sugar provides most of the calories.
3. **Category nutrition profiles** — median sugar/salt/fat per category, with confidence intervals.
4. **Additive load** — which categories carry the most E-numbers, and does additive count predict Nutri-Score?
5. **Label claims** — organic, vegan and gluten-free prevalence by country and category.
6. **Country comparison** — average Nutri-Score by country tag; is the same product formulated differently?
7. **Front-of-pack images** — the `image_url` column makes this a ready-made image-classification manifest.
8. **Missingness** — nutrition completeness varies by category and country; quantify the bias before modelling.
9. **Ingredient text NLP** — extract ingredient names and build a co-occurrence network of the food supply.

## 📁 Files

| File | What it is |
|---|---|
| `food_products.csv` | 16,091 food products x 67 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: Nutri-Score, nutrients, categories, labels. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`food`, `nutrition`, `health`, `open-food-facts`, `groceries`, `diet`, `nutriscore`, `tabular`, `consumer`, `europe`

## 🔗 Provenance

- **Source:** **Open Food Facts** search API v2
  (`https://world.openfoodfacts.org/api/v2/search`), category queries with an explicit field list.
- **Sampling:** the first five pages of 100 products in each of 36 grocery categories, deduplicated by
  barcode — a category-stratified sample, not a random sample of the 3-million-product database.
- **Upstream:** crowd-sourced labels, ingredient lists and nutrition tables, with Nutri-Score,
  Eco-Score and NOVA values computed by Open Food Facts where enough data exists.
- **Derived columns:** brand/category/country/allergen/additive counts, diet and processing flags,
  energy shares, nutrient-threshold flags, nutrition completeness.
- **Snapshot date:** 21 November 2026.

## 🔄 Update frequency

**Continuous upstream; snapshot here.** Open Food Facts is edited daily by volunteers. Re-run `scripts/29_food.py` for a new sample.

## ⚠️ Caveats

- Crowd-sourced data: values are only as good as the volunteer who entered them, and coverage is heavily European.
- Nutrition values are per 100 g as declared; missing values are left blank rather than imputed.
- Nutri-Score and NOVA are only present for a minority of products and use different algorithms over time.
- `product_quantity_g` is parsed from a free-text field and fails for multi-packs and non-gram units.
- The sample is category-stratified (five pages per category), so it is not representative of the whole database.
- Ingredient text is truncated at 800 characters in this extract.
- Some records are duplicates or retired products that remain in the database.

## 📜 Licence

Open Database License (ODbL 1.0) — Open Food Facts contributors. Share-alike and attribution apply to derived databases.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `code` | `number` | Open Food Facts barcode (EAN/UPC). |
| 2 | `product_name` | `string` | Product name as entered. |
| 3 | `generic_name` | `string` | Generic product name. |
| 4 | `brands` | `string` | Brand(s), comma-separated. |
| 5 | `brand_count` | `number` | Number of brands listed. |
| 6 | `categories` | `string` | Human-readable category path. |
| 7 | `categories_tags` | `string` | Normalised category tags (semicolon-joined). |
| 8 | `category_count` | `number` | Number of category tags. |
| 9 | `countries` | `string` | Countries where the product is sold. |
| 10 | `countries_tags` | `string` | Normalised country tags. |
| 11 | `country_count` | `number` | Number of countries. |
| 12 | `quantity` | `string` | Net quantity as printed (free text). |
| 13 | `product_quantity_g` | `number` | Net quantity parsed to grams where possible. |
| 14 | `serving_size` | `string` | Serving size as printed. |
| 15 | `packaging` | `string` | Packaging description. |
| 16 | `packaging_tags` | `string` | Normalised packaging tags. |
| 17 | `labels` | `string` | Labels and certifications as printed. |
| 18 | `labels_tags` | `string` | Normalised label tags. |
| 19 | `allergens` | `string` | Allergens as printed. |
| 20 | `allergen_count` | `number` | Number of allergen tags. |
| 21 | `additives_tags` | `string` | Normalised additive tags (E-numbers). |
| 22 | `additive_count` | `number` | Number of additives. |
| 23 | `ingredients_text` | `string` | Ingredient list (truncated to 800 characters). |
| 24 | `ingredient_count` | `number` | Comma-separated ingredient count. |
| 25 | `image_url` | `string` | Front-of-pack image URL. |
| 26 | `nutriscore_grade` | `string` | Nutri-Score letter (a-e), where computed. |
| 27 | `nutriscore_score` | `number` | Nutri-Score numeric score (lower is better). |
| 28 | `ecoscore_grade` | `string` | Eco-Score letter (a-e), where computed. |
| 29 | `ecoscore_score` | `number` | Eco-Score numeric score. |
| 30 | `nova_group` | `number` | NOVA processing group 1-4. |
| 31 | `manufacturing_places` | `string` | Manufacturing locations as declared. |
| 32 | `stores` | `string` | Retail chains listed. |
| 33 | `origins` | `string` | Country of origin as declared. |
| 34 | `lang` | `string` | Language of the record. |
| 35 | `energy_kcal_100g` | `number` | Energy per 100 g in kcal. |
| 36 | `fat_100g` | `number` | Fat per 100 g (g). |
| 37 | `saturated_fat_100g` | `number` | Saturated fat per 100 g (g). |
| 38 | `carbohydrates_100g` | `number` | Carbohydrates per 100 g (g). |
| 39 | `sugars_100g` | `number` | Sugars per 100 g (g). |
| 40 | `added_sugars_100g` | `number` | Added sugars per 100 g (g), where declared. |
| 41 | `fiber_100g` | `number` | Fibre per 100 g (g). |
| 42 | `proteins_100g` | `number` | Protein per 100 g (g). |
| 43 | `salt_100g` | `number` | Salt per 100 g (g). |
| 44 | `sodium_100g` | `number` | Sodium per 100 g (g). |
| 45 | `is_ultra_processed` | `boolean` | true when NOVA group is 4. |
| 46 | `is_processed` | `boolean` | true when NOVA group is 3. |
| 47 | `is_unprocessed` | `boolean` | true when NOVA group is 1. |
| 48 | `has_nutriscore` | `boolean` | true when a Nutri-Score grade exists. |
| 49 | `has_ecoscore` | `boolean` | true when an Eco-Score grade exists. |
| 50 | `is_organic` | `boolean` | true when an organic label is present. |
| 51 | `is_vegan` | `boolean` | true when a vegan label is present. |
| 52 | `is_vegetarian` | `boolean` | true when a vegetarian label is present. |
| 53 | `is_gluten_free` | `boolean` | true when a gluten-free label is present. |
| 54 | `contains_palm_oil` | `boolean` | true when the ingredients mention palm oil. |
| 55 | `is_beverage` | `boolean` | true when the category indicates a drink. |
| 56 | `is_snack` | `boolean` | true when the category indicates a snack or biscuit. |
| 57 | `sugar_energy_pct` | `number` | Share of energy from sugars (sugars x 4 / kcal x 100). |
| 58 | `fat_energy_pct` | `number` | Share of energy from fat (fat x 9 / kcal x 100). |
| 59 | `protein_energy_pct` | `number` | Share of energy from protein (protein x 4 / kcal x 100). |
| 60 | `is_high_sugar` | `boolean` | true when sugars exceed 22.5 g/100 g. |
| 61 | `is_high_salt` | `boolean` | true when salt exceeds 1.5 g/100 g. |
| 62 | `is_high_fat` | `boolean` | true when fat exceeds 17.5 g/100 g. |
| 63 | `is_high_fiber` | `boolean` | true when fibre exceeds 6 g/100 g. |
| 64 | `is_high_protein` | `boolean` | true when protein exceeds 20 g/100 g. |
| 65 | `nutrition_fields_present` | `number` | How many of the ten core nutrient fields are filled. |
| 66 | `nutrition_completeness_pct` | `number` | Nutrition fields present as a percentage of ten. |
| 67 | `label_count` | `number` | Number of label tags. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
