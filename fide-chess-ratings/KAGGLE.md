# FIDE Chess Ratings

**Subtitle:** 573,475 FIDE-rated players with classical ratings, titles & federations

**Tags:** `tabular`, `games`, `sports`

**Dataset File:** `fide_players.csv` (573,475 rows, 34 columns, 94.6 MB)

**Provenance & Source:** FIDE Standard Rating List (ratings.fide.com)

**Expected Update Frequency:** `monthly`

---

## 📖 Description

### Every FIDE-rated chess player

FIDE publishes its standard rating list as XML each month. This dataset contains **573,475 players
from 208 federations**, with **34 parameters** each.

- **Identity** — FIDE id, name, country, sex, open/women's/organiser/online titles.
- **Rating** — classical rating, rated games, K-factor and derived rating bands.
- **Demographics** — birth year, age in 2026, junior/veteran flags.
- **Status** — rated, titled, active, inactive-flag and title-category flags.
- **Derived** — name length/word count and rating per rated game.

**573,475 players have a published rating** and **1,904 are grandmasters**. The list supports
rating-distribution, title-pathway and national-federation analysis.

## 🧾 Columns (34)

`fide_id`, `name`, `country`, `sex`, `title`, `woman_title`, `organiser_title`, `foa_title`, `rating`, `games`, `k_factor`, `birth_year`, `flag`, `age`, `rating_band`, `is_rated`, `is_titled`, `is_grandmaster`, `is_international_master`, `is_fide_master`, `is_candidate_master`, `is_woman_grandmaster`, `is_woman_master`, `is_active`, `is_male`, `is_female`, `has_birth_year`, `is_junior`, `is_veteran`, `is_inactive_flag`, `k_factor_band`, `name_length`, `name_word_count`, `rating_per_game`

## 💡 Ideas for using this data

1. **Rating distribution** — the long tail of club players vs the elite.
2. **Country strength** — players, GMs and mean rating by federation.
3. **Age curves** — rating vs age, and the peak rating age.
4. **Title pathways** — how many players reach each title, by country and sex.
5. **Activity** — rated games vs rating and inactivity flags.
6. **Gender gaps** — participation and rating distributions.
7. **Name analysis** — naming conventions and country-specific name structures.
8. **K-factor** — K-factor distribution by age and rating.
9. **Elite table** — build a top-100 board with title and age context.

## 📁 Files

| File | What it is |
|---|---|
| `fide_players.csv` | 573,475 players x 34 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`chess`, `fide`, `ratings`, `sports`, `players`, `rankings`, `demographics`

## 🔗 Provenance

- **Source:** **FIDE standard rating list**,
  `https://ratings.fide.com/download/standard_rating_list_xml.zip` (monthly download).
- **Scope:** every player on the standard (classical) list at snapshot time.
- **Processing:** XML streamed with `iterparse`, fields normalised, title/age/activity flags and
  rating bands derived.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Monthly.** FIDE publishes new standard rating lists at the start of each month.

## ⚠️ Caveats

- The list covers classical ratings only; rapid and blitz lists are separate downloads.
- Birth year is optional and missing for many players.
- Country codes are FIDE/IOC codes, which differ from ISO for some federations.
- Ratings and game counts change every month.
- The `flag` field's meaning is not fully documented; `i` is treated as inactive.
- Name order and diacritics follow FIDE's formatting.
- Unrated players may appear with a rating of 0.

## 📜 Licence

FIDE rating lists are published for public information; FIDE retains the rights.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `fide_id` | `number` | FIDE player identifier. |
| 2 | `name` | `string` | Player name (last name first). |
| 3 | `country` | `string` | FIDE country code. |
| 4 | `sex` | `string` | M or F. |
| 5 | `title` | `string` | Open title (GM, IM, FM, CM). |
| 6 | `woman_title` | `string` | Women's title (WGM, WIM, WFM, WCM). |
| 7 | `organiser_title` | `string` | Organiser title. |
| 8 | `foa_title` | `string` | FIDE Online Arena title. |
| 9 | `rating` | `number` | Standard classical rating. |
| 10 | `games` | `number` | Rated games in the period. |
| 11 | `k_factor` | `number` | FIDE K-factor. |
| 12 | `birth_year` | `number` | Year of birth. |
| 13 | `flag` | `string` | FIDE flag field (i = inactive). |
| 14 | `age` | `number` | Age in 2026. |
| 15 | `rating_band` | `string` | Rating band. |
| 16 | `is_rated` | `boolean` | true when the rating is positive. |
| 17 | `is_titled` | `boolean` | true when the player holds any title. |
| 18 | `is_grandmaster` | `boolean` | true for GMs. |
| 19 | `is_international_master` | `boolean` | true for IMs. |
| 20 | `is_fide_master` | `boolean` | true for FMs. |
| 21 | `is_candidate_master` | `boolean` | true for CMs. |
| 22 | `is_woman_grandmaster` | `boolean` | true for WGMs. |
| 23 | `is_woman_master` | `boolean` | true for WIM/WFM/WCM. |
| 24 | `is_active` | `boolean` | true when rated games > 0. |
| 25 | `is_male` | `boolean` | true when sex is M. |
| 26 | `is_female` | `boolean` | true when sex is F. |
| 27 | `has_birth_year` | `boolean` | true when a birth year is listed. |
| 28 | `is_junior` | `boolean` | true when aged 20 or under. |
| 29 | `is_veteran` | `boolean` | true when aged 60 or over. |
| 30 | `is_inactive_flag` | `boolean` | true when the FIDE inactive flag is set. |
| 31 | `k_factor_band` | `string` | K-factor band. |
| 32 | `name_length` | `number` | Characters in the name. |
| 33 | `name_word_count` | `number` | Words in the name. |
| 34 | `rating_per_game` | `number` | Rating divided by rated games. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
