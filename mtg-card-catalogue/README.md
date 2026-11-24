---
license: cc-by-4.0
task_categories:
- tabular
tags:
- tabular
pretty_name: 'Magic: The Gathering Card Catalogue'
---

# Magic: The Gathering Card Catalogue

**Subtitle:** 39,412 unique MTG cards with mana, types, rules text, legalities & prices

**Tags:** `tabular`, `games`

**Dataset File:** `mtg_cards.csv` (70,290 rows, 79 columns, 50.7 MB)

**Provenance & Source:** Scryfall Bulk Data API (scryfall.com)

**Expected Update Frequency:** `monthly`

---

## 📖 Description

### The complete Magic: The Gathering oracle catalogue

Scryfall's `oracle_cards` bulk file is the canonical list of unique Magic cards. This dataset contains
**39,412 cards across 594 sets** with **79 parameters** each.

- **Identity** — Scryfall and oracle ids, name, language, layout, set code/name/type, collector number,
  rarity, artist and release date.
- **Printing** — border, frame, frame effects, security stamp, finishes, games, digital/promo/reprint/
  variation/reserved flags, full-art, textless, booster and story-spotlight flags, image status.
- **Game text** — mana cost and converted cost, type line, oracle text, power, toughness, loyalty,
  colours, colour identity, colour indicator, keywords and produced mana.
- **Legalities and prices** — full format legality map, USD/USD-foil/EUR/MTGO prices, EDHREC and Penny
  ranks, Scryfall and rulings URLs.
- **Derived** — colour count and colourfulness, parsed power/toughness, CMC band, card-type flags,
  Commander/Standard/Modern legality, price presence, set age and rarity rank.

**20,424 cards are creatures** and **33,303** have a listed USD price — a complete base
table for metagame, market and card-design analysis.

## 🧾 Columns (79)

`card_id`, `oracle_id`, `name`, `lang`, `layout`, `released_at`, `set_code`, `set_name`, `set_type`, `collector_number`, `rarity`, `artist`, `border_color`, `frame`, `frame_effects`, `security_stamp`, `finishes`, `games`, `digital`, `promo`, `reprint`, `variation`, `reserved`, `full_art`, `textless`, `booster`, `story_spotlight`, `highres_image`, `image_status`, `mana_cost`, `cmc`, `type_line`, `oracle_text`, `power`, `toughness`, `loyalty`, `colors`, `color_identity`, `color_indicator`, `keywords`, `produced_mana`, `legalities`, `price_usd`, `price_usd_foil`, `price_eur`, `price_tix`, `edhrec_rank`, `penny_rank`, `card_back_id`, `illustration_id`, `scryfall_uri`, `prints_search_uri`, `rulings_uri`, `face_count`, `oracle_text_length`, `keyword_count`, `color_count`, `is_colorless`, `is_multicolor`, `is_monocolor`, `power_num`, `toughness_num`, `cmc_band`, `is_creature`, `is_land`, `is_instant`, `is_sorcery`, `is_artifact`, `is_enchantment`, `is_planeswalker`, `is_battle`, `is_legendary`, `is_commander_legal`, `is_standard_legal`, `is_modern_legal`, `has_price`, `set_age_years`, `collector_number_int`, `rarity_rank`

## 💡 Ideas for using this data

1. **Card design over time** — mana cost, power/toughness and keyword usage by release year.
2. **Colour pie** — mechanics and keywords by colour identity.
3. **Market analysis** — price distribution by rarity, set age and format legality.
4. **Power creep** — creature stats vs mana cost across eras.
5. **Format staples** — Commander/Modern legality vs EDHREC rank.
6. **Text mining** — keyword and rules-text co-occurrence networks.
7. **Set composition** — rarity and card-type mix across sets.
8. **Reserved list** — the reserved cards and their price profile.
9. **Price prediction** — model USD price from rarity, age, legality and EDHREC rank.

## 📁 Files

| File | What it is |
|---|---|
| `mtg_cards.csv` | 39,412 cards x 79 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`magic-the-gathering`, `cards`, `games`, `scryfall`, `catalogue`, `prices`, `text`

## 🔗 Provenance

- **Source:** **Scryfall bulk data**, `https://api.scryfall.com/bulk-data`, using the
  `oracle_cards` JSONL archive (one JSON object per line).
- **Scope:** every unique oracle card in Scryfall at snapshot time.
- **Processing:** JSONL parsed, nested legalities/prices/finishes flattened, card-type and colour flags,
  parsed stats and rarity ranks derived.
- **Snapshot date:** 22 November 2026 (bulk file dated 2026-11-22).

## 🔄 Update frequency

**Daily.** Scryfall regenerates the bulk files every day.

## ⚠️ Caveats

- Prices are Scryfall's daily snapshots and fluctuate; they are not a transaction record.
- Oracle text uses Scryfall's wording, which can differ from printed text.
- Multi-face cards are one row with `face_count` > 1; per-face detail is not expanded.
- Legalities are stored as a single key:value string, not one column per format.
- Power/toughness can be non-numeric (`*`, `1+*`), so parsed values may be blank.
- Digital-only printings and promos are included; filter `digital`/`promo` for paper analysis.
- Bulk data is refreshed daily, so counts and prices will differ from other snapshots.

## 📜 Licence

Scryfall data is provided for community use; Magic: The Gathering is a Wizards of the Coast property.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `card_id` | `string` | Scryfall card id for this printing. |
| 2 | `oracle_id` | `string` | Oracle id shared by all printings of the card. |
| 3 | `name` | `string` | Card name. |
| 4 | `lang` | `string` | Card language. |
| 5 | `layout` | `string` | Card layout (normal, transform, split, ...). |
| 6 | `released_at` | `date` | Set release date. |
| 7 | `set_code` | `string` | Set code. |
| 8 | `set_name` | `string` | Set name. |
| 9 | `set_type` | `string` | Set type (core, expansion, commander, promo, ...). |
| 10 | `collector_number` | `string` | Collector number within the set. |
| 11 | `rarity` | `string` | Rarity (common, uncommon, rare, mythic, special, bonus). |
| 12 | `artist` | `string` | Illustrator. |
| 13 | `border_color` | `string` | Border colour. |
| 14 | `frame` | `number` | Frame version. |
| 15 | `frame_effects` | `string` | Frame effects. |
| 16 | `security_stamp` | `string` | Security stamp, where printed. |
| 17 | `finishes` | `string` | Available finishes (nonfoil, foil, etched). |
| 18 | `games` | `string` | Games the card is available in (paper, mtgo, arena). |
| 19 | `digital` | `boolean` | true for digital-only printings. |
| 20 | `promo` | `boolean` | true for promotional printings. |
| 21 | `reprint` | `boolean` | true when the card is a reprint. |
| 22 | `variation` | `boolean` | true for alternate-art variations. |
| 23 | `reserved` | `boolean` | true when the card is on the Reserved List. |
| 24 | `full_art` | `boolean` | true for full-art cards. |
| 25 | `textless` | `boolean` | true for textless cards. |
| 26 | `booster` | `boolean` | true when the card appears in boosters. |
| 27 | `story_spotlight` | `boolean` | true for story spotlight cards. |
| 28 | `highres_image` | `boolean` | true when a high-resolution image exists. |
| 29 | `image_status` | `string` | Image availability status. |
| 30 | `mana_cost` | `string` | Mana cost string. |
| 31 | `cmc` | `number` | Converted mana cost. |
| 32 | `type_line` | `string` | Full type line. |
| 33 | `oracle_text` | `string` | Oracle rules text. |
| 34 | `power` | `string` | Power (creatures). |
| 35 | `toughness` | `string` | Toughness (creatures). |
| 36 | `loyalty` | `string` | Starting loyalty (planeswalkers). |
| 37 | `colors` | `string` | Colours (WUBRG). |
| 38 | `color_identity` | `string` | Colour identity. |
| 39 | `color_indicator` | `string` | Colour indicator for colourless-frame cards. |
| 40 | `keywords` | `string` | Keyword abilities. |
| 41 | `produced_mana` | `string` | Mana the card can produce. |
| 42 | `legalities` | `string` | Format legality as key:value pairs. |
| 43 | `price_usd` | `number` | USD price (non-foil). |
| 44 | `price_usd_foil` | `number` | USD price (foil). |
| 45 | `price_eur` | `number` | EUR price. |
| 46 | `price_tix` | `number` | MTGO ticket price. |
| 47 | `edhrec_rank` | `number` | EDHREC popularity rank. |
| 48 | `penny_rank` | `number` | Penny Dreadful rank. |
| 49 | `card_back_id` | `string` | Scryfall id of the card back. |
| 50 | `illustration_id` | `string` | Illustration id. |
| 51 | `scryfall_uri` | `string` | Scryfall page URL. |
| 52 | `prints_search_uri` | `string` | URL of all printings. |
| 53 | `rulings_uri` | `string` | URL of rulings. |
| 54 | `face_count` | `number` | Number of card faces. |
| 55 | `oracle_text_length` | `number` | Characters in the oracle text. |
| 56 | `keyword_count` | `number` | Number of keyword abilities. |
| 57 | `color_count` | `number` | Number of colours. |
| 58 | `is_colorless` | `boolean` | true when the card has no colours. |
| 59 | `is_multicolor` | `boolean` | true when the card has two or more colours. |
| 60 | `is_monocolor` | `boolean` | true when the card has exactly one colour. |
| 61 | `power_num` | `number` | Power parsed to a number, where possible. |
| 62 | `toughness_num` | `number` | Toughness parsed to a number, where possible. |
| 63 | `cmc_band` | `number` | Converted-mana-cost band. |
| 64 | `is_creature` | `boolean` | true when the type line contains Creature. |
| 65 | `is_land` | `boolean` | true when the type line contains Land. |
| 66 | `is_instant` | `boolean` | true when the type line contains Instant. |
| 67 | `is_sorcery` | `boolean` | true when the type line contains Sorcery. |
| 68 | `is_artifact` | `boolean` | true when the type line contains Artifact. |
| 69 | `is_enchantment` | `boolean` | true when the type line contains Enchantment. |
| 70 | `is_planeswalker` | `boolean` | true when the type line contains Planeswalker. |
| 71 | `is_battle` | `boolean` | true when the type line contains Battle. |
| 72 | `is_legendary` | `boolean` | true when the type line contains Legendary. |
| 73 | `is_commander_legal` | `boolean` | true when legal in Commander. |
| 74 | `is_standard_legal` | `boolean` | true when legal in Standard. |
| 75 | `is_modern_legal` | `boolean` | true when legal in Modern. |
| 76 | `has_price` | `boolean` | true when a USD price is listed. |
| 77 | `set_age_years` | `number` | Years since the set released. |
| 78 | `collector_number_int` | `number` | Collector number parsed to an integer, where numeric. |
| 79 | `rarity_rank` | `number` | Ordinal rarity rank (common=1 ... mythic=4). |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
