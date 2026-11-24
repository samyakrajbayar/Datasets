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
pretty_name: "Steam Games Market"
tags:
- tabular
- games
- video games
---

# Steam Games Market

**Subtitle:** 20,000 Steam games with owner estimates, reviews, playtime and pricing

**Tags:** `video-games`, `pricing`, `entertainment`, `tabular`

**Dataset File:** `steam_games.csv` (2,488 rows, 41 columns, 621.5 KB)

**Provenance & Source:** Steam Storefront API & SteamSpy Community API

**Expected Update Frequency:** `quarterly`

---

## 📖 Description

### The Steam catalogue as a market dataset

SteamSpy publishes an estimate of every game on Steam: ownership bands, review counts, playtime,
price and concurrency. This snapshot covers **2,488 games** with **41 parameters** per title.

Columns cover:
- **Identity** — app id, title, developer, publisher, and how many titles in the file that
  developer and publisher have.
- **Reviews** — positive, negative and total review counts, the positive ratio, a review band,
  user score and SteamSpy's score rank.
- **Audience** — estimated owner range with its bounds and midpoint, plus review and concurrency
  rates per estimated owner.
- **Engagement** — average and median lifetime playtime (minutes and hours), two-week playtime,
  the median/average ratio and playtime per owner.
- **Commerce** — current and initial price, discount percentage and amount, a price band,
  free-to-play and discount flags, peak concurrent users.
- **Title features** — length, word count, sequel heuristic, leading "The".

**304 titles (12.2%)** are free to play. Owner figures are SteamSpy's own
interval estimates, not Valve disclosures, which makes the dataset a good exercise in working with
banded, uncertain quantities.

## 🧾 Columns (41)

`appid`, `name`, `developer`, `publisher`, `score_rank`, `positive_reviews`, `negative_reviews`, `total_reviews`, `review_ratio_pct`, `userscore`, `owners_range`, `owners_min`, `owners_max`, `owners_mid`, `average_playtime_minutes`, `average_playtime_hours`, `median_playtime_minutes`, `median_playtime_hours`, `average_2weeks_minutes`, `median_2weeks_minutes`, `price_cents`, `price_usd`, `initial_price_usd`, `discount_pct`, `discount_usd`, `ccu`, `is_free`, `is_discounted`, `has_score_rank`, `publisher_game_count`, `developer_game_count`, `name_length`, `name_word_count`, `is_sequel`, `review_band`, `price_band`, `engagement_ratio`, `playtime_per_owner_minutes`, `ccu_per_owner_pct`, `review_per_owner_pct`, `name_starts_with_the`

## 💡 Ideas for using this data

1. **Price and reception** — does price correlate with review ratio once you control for genre size?
2. **Free-to-play economics** — compare owner estimates, review counts and concurrency for free vs paid titles.
3. **Engagement tails** — median/average playtime ratio as a proxy for how top-heavy a game's audience is.
4. **Publisher portfolios** — which publishers have the most titles, and do their games cluster in quality bands?
5. **Review propensity** — reviews per owner varies widely; model it and use it to improve owner estimates.
6. **Title conventions** — sequel and 'The' heuristics versus commercial performance.
7. **Discount behaviour** — discount depth by price band and age proxy (`appid` order).
8. **Long-tail analysis** — log-log distribution of owners and reviews; fit a power law.
9. **Recommendation baseline** — build a content-free popularity ranker and measure precision against review counts.

## 📁 Files

| File | What it is |
|---|---|
| `steam_games.csv` | 2,488 Steam games x 41 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: pricing, reviews, owners, engagement. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`gaming`, `steam`, `video-games`, `market-analysis`, `entertainment`, `pricing`, `reviews`, `tabular`, `consumer`, `economics`

## 🔗 Provenance

- **Source:** **SteamSpy** public API (`https://steamspy.com/api.php?request=all&page=N`),
  pages 0–19, retrieved at one request per second.
- **Upstream:** SteamSpy derives ownership bands and playtime from Steam profiles and the public
  store API; review and price fields come from Steam itself.
- **Processing:** 20 pages of 1,000 app records were merged by app id (duplicates overwritten),
  owners strings were parsed into bounds and a midpoint, prices converted from cents.
- **Derived columns:** review totals and ratios, owner statistics, playtime conversions, price bands,
  discount flags, publisher/developer catalogue sizes, engagement ratios, title features.
- **Snapshot date:** 21 November 2026.

## 🔄 Update frequency

**Continuous upstream; snapshot here.** SteamSpy refreshes daily. Re-run `scripts/24_steam_games.py` for a new snapshot.

## ⚠️ Caveats

- Ownership is an estimate published as a range; `owners_mid` is a convenience midpoint, not a measurement.
- SteamSpy's `all` listing is popularity-ordered and capped here at 20 pages (20,000 slots), so very obscure titles may be missing.
- Playtime and concurrency figures lag and are sampled from public profiles, which skew toward engaged players.
- Prices are USD and reflect the moment of capture; regional pricing is not included.
- `userscore` and `score_rank` are empty for many titles — SteamSpy only fills them above review thresholds.
- The sequel heuristic is a string match, not a curated franchise table.
- No genre or tag columns are present because SteamSpy's bulk listing does not expose them.

## 📜 Licence

SteamSpy data is published for public use; Steam store metadata belongs to Valve and the respective publishers. Included for non-commercial research with attribution.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `appid` | `number` | Steam application id. |
| 2 | `name` | `string` | Game title as listed on Steam. |
| 3 | `developer` | `string` | Developer studio. |
| 4 | `publisher` | `string` | Publisher. |
| 5 | `score_rank` | `number` | SteamSpy's proprietary ranking score (empty for most titles). |
| 6 | `positive_reviews` | `number` | Number of positive user reviews. |
| 7 | `negative_reviews` | `number` | Number of negative user reviews. |
| 8 | `total_reviews` | `number` | Positive plus negative reviews. |
| 9 | `review_ratio_pct` | `number` | Share of reviews that are positive, in percent. |
| 10 | `userscore` | `number` | Metacritic-style user score (0-100) where available. |
| 11 | `owners_range` | `string` | Estimated owner range as published (e.g. '200,000 .. 500,000'). |
| 12 | `owners_min` | `number` | Lower bound of the owner range. |
| 13 | `owners_max` | `number` | Upper bound of the owner range. |
| 14 | `owners_mid` | `number` | Midpoint of the owner range, used as an estimate. |
| 15 | `average_playtime_minutes` | `number` | Average total playtime in minutes, all players. |
| 16 | `average_playtime_hours` | `number` | Average total playtime in hours. |
| 17 | `median_playtime_minutes` | `number` | Median total playtime in minutes. |
| 18 | `median_playtime_hours` | `number` | Median total playtime in hours. |
| 19 | `average_2weeks_minutes` | `number` | Average playtime in the last two weeks, minutes. |
| 20 | `median_2weeks_minutes` | `number` | Median playtime in the last two weeks, minutes. |
| 21 | `price_cents` | `number` | Current price in US cents. |
| 22 | `price_usd` | `number` | Current price in US dollars. |
| 23 | `initial_price_usd` | `number` | Pre-discount price in US dollars. |
| 24 | `discount_pct` | `number` | Current discount percentage. |
| 25 | `discount_usd` | `number` | Absolute discount in US dollars. |
| 26 | `ccu` | `number` | Peak concurrent users recorded by SteamSpy. |
| 27 | `is_free` | `boolean` | true when the game is free to play. |
| 28 | `is_discounted` | `boolean` | true when a discount is active. |
| 29 | `has_score_rank` | `boolean` | true when SteamSpy assigns a score rank. |
| 30 | `publisher_game_count` | `number` | Number of games in this file from the same publisher. |
| 31 | `developer_game_count` | `number` | Number of games in this file from the same developer. |
| 32 | `name_length` | `number` | Characters in the title. |
| 33 | `name_word_count` | `number` | Words in the title. |
| 34 | `is_sequel` | `boolean` | Heuristic flag for numbered or colon-titled sequels. |
| 35 | `review_band` | `string` | Review-count band from <100 to 100k+. |
| 36 | `price_band` | `string` | Price band: Free, Budget, Mid, Premium, AAA. |
| 37 | `engagement_ratio` | `number` | Median playtime divided by average playtime — how top-heavy engagement is. |
| 38 | `playtime_per_owner_minutes` | `number` | Average playtime divided by estimated owners. |
| 39 | `ccu_per_owner_pct` | `number` | Peak concurrent users as a percentage of estimated owners. |
| 40 | `review_per_owner_pct` | `number` | Reviews as a percentage of estimated owners (review propensity). |
| 41 | `name_starts_with_the` | `boolean` | true when the title begins with 'The '. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
