# IMDb Title Catalogue 1990-2026

**Subtitle:** 147,195 films and series with genres, runtime, average rating and votes

**Tags:** `tabular`, `movies`, `entertainment`

**Dataset File:** `imdb_titles.csv` (147,195 rows, 39 columns, 34.4 MB)

**Provenance & Source:** IMDb Non-Commercial Datasets (datasets.imdbws.com)

**Expected Update Frequency:** `monthly`

---

## 📖 Description

### 300,000 IMDb titles with ratings

IMDb publishes its title metadata as open TSV files. This dataset joins `title.basics` to
`title.ratings` and keeps **147,195 films and series released since 1990** with at least 100 votes,
giving **39 parameters** per title.

- **Identity** — IMDb id, title type, primary and original title, adult flag, start and end year.
- **Production** — runtime and genres.
- **Ratings** — average rating and vote count.
- **Derived** — decade, age, runtime band, genre count and eight genre flags, movie/series flags,
  title length and word count, rating and vote bands, highly-rated and popular flags, votes per year,
  a Bayesian-shrunk rating and a rating x log-votes score.

**107,537 are feature films**, **10,090 rate 8.0 or higher**, and the mean rating in the sample is
**6.09**. The file supports film-industry, genre and audience-reception analysis.

## 🧾 Columns (39)

`tconst`, `title_type`, `primary_title`, `original_title`, `is_adult`, `start_year`, `end_year`, `runtime_minutes`, `genres`, `average_rating`, `num_votes`, `decade`, `age_years`, `is_adult_film`, `runtime_band`, `genre_count`, `is_drama`, `is_comedy`, `is_documentary`, `is_action`, `is_horror`, `is_thriller`, `is_romance`, `is_scifi`, `is_animation`, `is_movie`, `is_series`, `title_length`, `title_word_count`, `same_title`, `rating_band`, `votes_band`, `is_highly_rated`, `is_popular`, `votes_per_year`, `bayesian_rating`, `has_runtime`, `is_ongoing`, `rating_votes_product`

## 💡 Ideas for using this data

1. **Genre economics** — ratings and vote counts by genre combination.
2. **Runtime trends** — how film length has changed since 1990.
3. **Ratings over time** — are newer titles rated differently, or just voted on more?
4. **Series vs films** — reception and longevity differences.
5. **Bayesian ranking** — build a robust top-1000 using the shrunk rating.
6. **Title linguistics** — word count, punctuation and title patterns vs rating.
7. **Vote dynamics** — votes per year as a proxy for ongoing popularity.
8. **Genre co-occurrence** — network of genre combinations.
9. **Recommendation features** — a clean title-level feature table for recommender models.

## 📁 Files

| File | What it is |
|---|---|
| `imdb_titles.csv` | 147,195 titles x 39 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`imdb`, `movies`, `film`, `ratings`, `entertainment`, `genres`, `recommendation`

## 🔗 Provenance

- **Source:** **IMDb public datasets**, `https://datasets.imdbws.com/title.basics.tsv.gz`
  and `title.ratings.tsv.gz` (non-commercial use).
- **Scope:** titles released from 1990 onward, of type movie/tvSeries/tvMiniSeries, with at least 100
  votes; the first 300,000 matching rows in `tconst` order.
- **Processing:** ratings joined by `tconst`, genres split, runtime and year parsed, derived bands,
  flags and a Bayesian rating computed.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Daily.** IMDb regenerates the public datasets each day.

## ⚠️ Caveats

- IMDb datasets are for personal and non-commercial use; check IMDb's terms before redistribution.
- Only titles with at least 100 votes and a 1990+ start year are included.
- The 300,000 rows follow `tconst` order, which correlates with release date, not popularity.
- Ratings and vote counts are a snapshot and change continuously.
- Runtime is missing for some series and unreleased titles.
- Genres are a fixed vocabulary; many titles have several.
- The Bayesian rating uses a fixed prior (m = 5,000, global mean 7.0), not IMDb's own weighting.

## 📜 Licence

IMDb datasets are provided for personal, non-commercial use only; see IMDb's terms.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `tconst` | `string` | IMDb title identifier. |
| 2 | `title_type` | `string` | movie, tvSeries or tvMiniSeries. |
| 3 | `primary_title` | `string` | Primary title. |
| 4 | `original_title` | `string` | Original-language title. |
| 5 | `is_adult` | `number` | true for adult titles. |
| 6 | `start_year` | `number` | Release / start year. |
| 7 | `end_year` | `number` | End year for series. |
| 8 | `runtime_minutes` | `number` | Runtime in minutes. |
| 9 | `genres` | `string` | Genres (comma-separated). |
| 10 | `average_rating` | `number` | IMDb weighted average rating (1-10). |
| 11 | `num_votes` | `number` | Number of votes. |
| 12 | `decade` | `number` | Start-year decade. |
| 13 | `age_years` | `number` | Years since release at 2026. |
| 14 | `is_adult_film` | `boolean` | true when flagged adult. |
| 15 | `runtime_band` | `string` | Runtime band. |
| 16 | `genre_count` | `number` | Number of genres. |
| 17 | `is_drama` | `boolean` | true when Drama is a genre. |
| 18 | `is_comedy` | `boolean` | true when Comedy is a genre. |
| 19 | `is_documentary` | `boolean` | true when Documentary is a genre. |
| 20 | `is_action` | `boolean` | true when Action is a genre. |
| 21 | `is_horror` | `boolean` | true when Horror is a genre. |
| 22 | `is_thriller` | `boolean` | true when Thriller is a genre. |
| 23 | `is_romance` | `boolean` | true when Romance is a genre. |
| 24 | `is_scifi` | `boolean` | true when Sci-Fi is a genre. |
| 25 | `is_animation` | `boolean` | true when Animation is a genre. |
| 26 | `is_movie` | `boolean` | true for feature films. |
| 27 | `is_series` | `boolean` | true for series. |
| 28 | `title_length` | `number` | Characters in the primary title. |
| 29 | `title_word_count` | `number` | Words in the primary title. |
| 30 | `same_title` | `boolean` | true when primary and original titles match. |
| 31 | `rating_band` | `string` | Rating band. |
| 32 | `votes_band` | `string` | Vote-count band. |
| 33 | `is_highly_rated` | `boolean` | true when rating is 8.0 or higher. |
| 34 | `is_popular` | `boolean` | true when votes are 10,000 or more. |
| 35 | `votes_per_year` | `number` | Votes divided by age in years. |
| 36 | `bayesian_rating` | `number` | Rating shrunk toward the global mean (m = 5,000 votes). |
| 37 | `has_runtime` | `boolean` | true when a runtime is listed. |
| 38 | `is_ongoing` | `boolean` | true when a series has no end year. |
| 39 | `rating_votes_product` | `number` | Rating x log10(votes), a simple popularity-weighted score. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
