---
license: other
task_categories:
- tabular
tags:
- tabular
pretty_name: "MLB Player Seasons 2015-2025"
---

# MLB Player Seasons 2015-2025

**Subtitle:** 20,318 player-season rows with batting, pitching and fielding stats

**Tags:** `tabular`, `sports`, `baseball`

**Dataset File:** `mlb_player_seasons.csv` (20,318 rows, 88 columns, 5.8 MB)

**Provenance & Source:** MLB StatsAPI (statsapi.mlb.com)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### MLB player seasons, 2015–2025

The MLB StatsAPI exposes season totals for every player. This dataset contains **20,318 player-season
rows** across **11 seasons**, with **88 parameters** — every statistic returned by the
API plus identity and derived rate fields.

- **Identity** — player id/name, team and league ids/names, season, position and group.
- **Hitting stats** — games, plate appearances, at-bats, runs, hits, doubles, triples, home runs, RBI,
  walks, strikeouts, stolen bases, average, OBP, slugging, OPS, BABIP and more (blank for pitchers).
- **Pitching stats** — wins, losses, ERA, innings, strikeouts, saves, WHIP, home runs allowed, hit
  batters and more (blank for batters).
- **Derived** — pitcher/batter flags, extra-base hits, strikeout/walk/HR rates, isolated power,
  decimal innings, OPS and ERA bands, and qualification flags.

**11,350 batting rows** and **8,968 pitching rows** make this a complete two-way
player-season table for sabermetrics and fantasy analysis.

## 🧾 Columns (88)

`player_id`, `player_name`, `team_id`, `team_name`, `league_id`, `league_name`, `season`, `group`, `position`, `is_pitcher`, `is_batter`, `age`, `air_outs`, `at_bats`, `at_bats_per_home_run`, `avg`, `babip`, `balks`, `base_on_balls`, `batters_faced`, `blown_saves`, `catchers_interference`, `caught_stealing`, `caught_stealing_percentage`, `complete_games`, `doubles`, `earned_runs`, `era`, `games_finished`, `games_pitched`, `games_played`, `games_started`, `ground_into_double_play`, `ground_outs`, `ground_outs_to_airouts`, `hit_batsmen`, `hit_by_pitch`, `hits`, `hits_per9_inn`, `holds`, `home_runs`, `home_runs_per9`, `inherited_runners`, `inherited_runners_scored`, `innings_pitched`, `intentional_walks`, `left_on_base`, `losses`, `number_of_pitches`, `obp`, `ops`, `outs`, `pickoffs`, `pitches_per_inning`, `plate_appearances`, `rbi`, `runs`, `runs_scored_per9`, `sac_bunts`, `sac_flies`, `save_opportunities`, `saves`, `shutouts`, `slg`, `stolen_base_percentage`, `stolen_bases`, `strike_outs`, `strike_percentage`, `strikeout_walk_ratio`, `strikeouts_per9_inn`, `strikes`, `total_bases`, `triples`, `walks_per9_inn`, `whip`, `wild_pitches`, `win_percentage`, `wins`, `extra_base_hits`, `strikeout_rate`, `walk_rate`, `home_run_rate`, `slg_minus_avg`, `innings_pitched_decimal`, `ops_band`, `era_band`, `is_qualified_batter`, `is_qualified_pitcher`

## 💡 Ideas for using this data

1. **Two-way players** — find players with meaningful batting and pitching rows.
2. **Aging curves** — performance by age, separately for batters and pitchers.
3. **Power vs contact** — home-run rate vs strikeout rate.
4. **Team production** — aggregate team offence and pitching by season.
5. **Breakout seasons** — largest year-over-year improvements.
6. **Qualification effects** — how rate stats change when minimums are applied.
7. **Position scarcity** — offensive output by position.
8. **ERA vs WHIP** — pitcher profiles and outliers.
9. **Forecasting** — predict next-season OPS or ERA from prior seasons.

## 📁 Files

| File | What it is |
|---|---|
| `mlb_player_seasons.csv` | 20,318 player-seasons x 88 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`baseball`, `mlb`, `sports`, `statistics`, `players`, `sabermetrics`, `seasons`

## 🔗 Provenance

- **Source:** **MLB StatsAPI**,
  `https://statsapi.mlb.com/api/v1/stats?stats=season&group={group}&season={year}&sportId=1`.
- **Scope:** all players with a season total in 2015–2025, for both hitting and pitching.
- **Processing:** every stat key retained and snake-cased; player/team/league/position identity joined;
  rate, band and qualification fields derived.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Daily during the season.** StatsAPI updates statistics after each game.

## ⚠️ Caveats

- Stats are regular-season totals only; postseason is a separate endpoint.
- Players traded mid-season appear once per team in some responses, so rows are team-specific.
- Rate stats are not park- or league-adjusted.
- Innings pitched uses baseball notation (outs) and is converted to decimal for analysis.
- Very small sample sizes (few plate appearances) produce extreme rate stats.
- The API can revise statistics after the season.
- Column names follow the API's stat keys, snake-cased.

## 📜 Licence

MLB data is provided by MLB Advanced Media for public informational use.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `player_id` | `number` | MLB person identifier. |
| 2 | `player_name` | `string` | Player full name. |
| 3 | `team_id` | `number` | Team identifier. |
| 4 | `team_name` | `string` | Team name. |
| 5 | `league_id` | `number` | League identifier. |
| 6 | `league_name` | `string` | League name. |
| 7 | `season` | `number` | Season year. |
| 8 | `group` | `string` | hitting or pitching. |
| 9 | `position` | `string` | Position abbreviation. |
| 10 | `is_pitcher` | `boolean` | true for pitching rows. |
| 11 | `is_batter` | `boolean` | true for hitting rows. |
| 12 | `age` | `number` | MLB StatsAPI field or derived metric. |
| 13 | `air_outs` | `number` | MLB StatsAPI field or derived metric. |
| 14 | `at_bats` | `number` | MLB StatsAPI field or derived metric. |
| 15 | `at_bats_per_home_run` | `string` | MLB StatsAPI field or derived metric. |
| 16 | `avg` | `number` | MLB StatsAPI field or derived metric. |
| 17 | `babip` | `string` | MLB StatsAPI field or derived metric. |
| 18 | `balks` | `number` | MLB StatsAPI field or derived metric. |
| 19 | `base_on_balls` | `number` | MLB StatsAPI field or derived metric. |
| 20 | `batters_faced` | `number` | MLB StatsAPI field or derived metric. |
| 21 | `blown_saves` | `number` | MLB StatsAPI field or derived metric. |
| 22 | `catchers_interference` | `number` | MLB StatsAPI field or derived metric. |
| 23 | `caught_stealing` | `number` | MLB StatsAPI field or derived metric. |
| 24 | `caught_stealing_percentage` | `string` | MLB StatsAPI field or derived metric. |
| 25 | `complete_games` | `number` | MLB StatsAPI field or derived metric. |
| 26 | `doubles` | `number` | MLB StatsAPI field or derived metric. |
| 27 | `earned_runs` | `number` | MLB StatsAPI field or derived metric. |
| 28 | `era` | `number` | MLB StatsAPI field or derived metric. |
| 29 | `games_finished` | `number` | MLB StatsAPI field or derived metric. |
| 30 | `games_pitched` | `number` | MLB StatsAPI field or derived metric. |
| 31 | `games_played` | `number` | MLB StatsAPI field or derived metric. |
| 32 | `games_started` | `number` | MLB StatsAPI field or derived metric. |
| 33 | `ground_into_double_play` | `number` | MLB StatsAPI field or derived metric. |
| 34 | `ground_outs` | `number` | MLB StatsAPI field or derived metric. |
| 35 | `ground_outs_to_airouts` | `string` | MLB StatsAPI field or derived metric. |
| 36 | `hit_batsmen` | `number` | MLB StatsAPI field or derived metric. |
| 37 | `hit_by_pitch` | `number` | MLB StatsAPI field or derived metric. |
| 38 | `hits` | `number` | MLB StatsAPI field or derived metric. |
| 39 | `hits_per9_inn` | `number` | MLB StatsAPI field or derived metric. |
| 40 | `holds` | `number` | MLB StatsAPI field or derived metric. |
| 41 | `home_runs` | `number` | MLB StatsAPI field or derived metric. |
| 42 | `home_runs_per9` | `number` | MLB StatsAPI field or derived metric. |
| 43 | `inherited_runners` | `number` | MLB StatsAPI field or derived metric. |
| 44 | `inherited_runners_scored` | `number` | MLB StatsAPI field or derived metric. |
| 45 | `innings_pitched` | `number` | MLB StatsAPI field or derived metric. |
| 46 | `intentional_walks` | `number` | MLB StatsAPI field or derived metric. |
| 47 | `left_on_base` | `number` | MLB StatsAPI field or derived metric. |
| 48 | `losses` | `number` | MLB StatsAPI field or derived metric. |
| 49 | `number_of_pitches` | `number` | MLB StatsAPI field or derived metric. |
| 50 | `obp` | `number` | MLB StatsAPI field or derived metric. |
| 51 | `ops` | `number` | MLB StatsAPI field or derived metric. |
| 52 | `outs` | `number` | MLB StatsAPI field or derived metric. |
| 53 | `pickoffs` | `number` | MLB StatsAPI field or derived metric. |
| 54 | `pitches_per_inning` | `number` | MLB StatsAPI field or derived metric. |
| 55 | `plate_appearances` | `number` | MLB StatsAPI field or derived metric. |
| 56 | `rbi` | `number` | MLB StatsAPI field or derived metric. |
| 57 | `runs` | `number` | MLB StatsAPI field or derived metric. |
| 58 | `runs_scored_per9` | `number` | MLB StatsAPI field or derived metric. |
| 59 | `sac_bunts` | `number` | MLB StatsAPI field or derived metric. |
| 60 | `sac_flies` | `number` | MLB StatsAPI field or derived metric. |
| 61 | `save_opportunities` | `number` | MLB StatsAPI field or derived metric. |
| 62 | `saves` | `number` | MLB StatsAPI field or derived metric. |
| 63 | `shutouts` | `number` | MLB StatsAPI field or derived metric. |
| 64 | `slg` | `number` | MLB StatsAPI field or derived metric. |
| 65 | `stolen_base_percentage` | `string` | MLB StatsAPI field or derived metric. |
| 66 | `stolen_bases` | `number` | MLB StatsAPI field or derived metric. |
| 67 | `strike_outs` | `number` | MLB StatsAPI field or derived metric. |
| 68 | `strike_percentage` | `number` | MLB StatsAPI field or derived metric. |
| 69 | `strikeout_walk_ratio` | `string` | MLB StatsAPI field or derived metric. |
| 70 | `strikeouts_per9_inn` | `number` | MLB StatsAPI field or derived metric. |
| 71 | `strikes` | `number` | MLB StatsAPI field or derived metric. |
| 72 | `total_bases` | `number` | MLB StatsAPI field or derived metric. |
| 73 | `triples` | `number` | MLB StatsAPI field or derived metric. |
| 74 | `walks_per9_inn` | `number` | MLB StatsAPI field or derived metric. |
| 75 | `whip` | `number` | MLB StatsAPI field or derived metric. |
| 76 | `wild_pitches` | `number` | MLB StatsAPI field or derived metric. |
| 77 | `win_percentage` | `string` | MLB StatsAPI field or derived metric. |
| 78 | `wins` | `number` | MLB StatsAPI field or derived metric. |
| 79 | `extra_base_hits` | `number` | Doubles + triples + 2 x home runs. |
| 80 | `strikeout_rate` | `number` | Strikeouts per plate appearance (batters) or per batter faced (pitchers). |
| 81 | `walk_rate` | `number` | Walks per plate appearance or batter faced. |
| 82 | `home_run_rate` | `number` | Home runs per plate appearance. |
| 83 | `slg_minus_avg` | `number` | Slugging percentage minus batting average (isolated power). |
| 84 | `innings_pitched_decimal` | `number` | Innings pitched converted to decimal (outs / 3). |
| 85 | `ops_band` | `string` | OPS band for batters. |
| 86 | `era_band` | `string` | ERA band for pitchers. |
| 87 | `is_qualified_batter` | `boolean` | true when the batter had 300+ plate appearances. |
| 88 | `is_qualified_pitcher` | `boolean` | true when the pitcher threw 100+ innings. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
