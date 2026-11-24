# Podcast Catalogue

**Subtitle:** 2,997 podcasts with genres, feeds, episode counts and release metadata

**Tags:** `tabular`, `podcasts`, `audio`

**Dataset File:** `podcasts.csv` (2,997 rows, 47 columns, 2.2 MB)

**Provenance & Source:** Apple iTunes Search API (itunes.apple.com)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### 2,997 podcasts from the iTunes catalogue

Apple's iTunes Search API exposes podcast metadata without a key. This dataset queries 15 podcast
topics across four storefronts and deduplicates the results, yielding **2,997 podcasts** with
**47 parameters**.

- **Identity** — collection and track ids, title, censored title, publisher, iTunes and publisher URLs.
- **Distribution** — RSS feed URL, episode count, artwork, price and currency, store country.
- **Classification** — primary genre, genre ids and full genre list, explicitness and content advisory.
- **Latest episode** — release date, duration in milliseconds and minutes, episode URL.
- **Derived** — release year and age, genre count, explicit/free/feed/artwork flags, price and
  episode-count bands, episodes per year, title length and ten topic flags.

**2,997 podcasts are free**, **2,979** expose an RSS feed, and results span **4**
storefronts — a cross-section of the podcasting market for media and audio research.

## 🧾 Columns (47)

`collection_id`, `track_id`, `artist_name`, `collection_name`, `censored_name`, `feed_url`, `track_count`, `artwork_url`, `collection_price`, `currency`, `country`, `release_date`, `primary_genre`, `genre_ids`, `genres`, `explicitness`, `content_advisory`, `kind`, `wrapper_type`, `view_url`, `artist_view_url`, `track_view_url`, `track_time_millis`, `track_duration_minutes`, `query`, `store_country`, `release_year`, `age_days`, `genre_count`, `is_explicit`, `is_free`, `price_band`, `has_feed`, `has_artwork`, `episode_count_band`, `episodes_per_year`, `name_length`, `is_comedy`, `is_news`, `is_true_crime`, `is_business`, `is_technology`, `is_health`, `is_sports`, `is_education`, `is_fiction`, `is_kids`

## 💡 Ideas for using this data

1. **Genre landscape** — podcast supply and episode counts by genre.
2. **Pricing** — paid vs free podcasts and what predicts a price.
3. **Longevity** — release recency and episode counts as activity signals.
4. **Episode cadence** — episodes per year by genre.
5. **Feed availability** — podcasts without a public RSS feed.
6. **Topic overlap** — co-occurrence of genres.
7. **Title analysis** — naming patterns across genres and countries.
8. **Artwork** — the artwork URLs support image classification.
9. **Market comparison** — the same podcast across US/UK/CA/AU storefronts.

## 📁 Files

| File | What it is |
|---|---|
| `podcasts.csv` | 2,997 podcasts x 47 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`podcasts`, `audio`, `itunes`, `media`, `catalogue`, `genres`, `rss`

## 🔗 Provenance

- **Source:** **iTunes Search API**, `https://itunes.apple.com/search?entity=podcast`, no key
  required.
- **Scope:** the top 200 results for each of 15 podcast search terms in four storefronts
  (US, UK, Canada, Australia), deduplicated by collection id.
- **Processing:** flat result records normalised; release dates, durations and prices parsed; genre,
  price, episode and recency features derived.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Continuous.** The iTunes catalogue changes as podcasts publish and update.

## ⚠️ Caveats

- The sample is query- and storefront-stratified, not a complete podcast census.
- Episode counts are those reported by the feed at indexing time.
- Prices are storefront-specific and often zero for free podcasts.
- Release date refers to the latest indexed episode, not the podcast's start date.
- Genre labels are Apple's, not a controlled vocabulary.
- Apple rate-limits the API; the collector sleeps between requests.
- Some podcasts appear in multiple storefronts with different ids.

## 📜 Licence

Apple iTunes Search metadata is provided for informational use; podcasts remain with their publishers.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `collection_id` | `number` | iTunes podcast collection id. |
| 2 | `track_id` | `number` | iTunes track id. |
| 3 | `artist_name` | `string` | Publisher / artist name. |
| 4 | `collection_name` | `string` | Podcast title. |
| 5 | `censored_name` | `string` | Censored podcast title. |
| 6 | `feed_url` | `string` | RSS feed URL. |
| 7 | `track_count` | `number` | Number of episodes in the feed. |
| 8 | `artwork_url` | `string` | Artwork URL (600 px). |
| 9 | `collection_price` | `number` | Collection price. |
| 10 | `currency` | `string` | Price currency. |
| 11 | `country` | `string` | iTunes store country. |
| 12 | `release_date` | `date` | Release date of the latest episode (ISO). |
| 13 | `primary_genre` | `string` | Primary genre. |
| 14 | `genre_ids` | `string` | iTunes genre ids. |
| 15 | `genres` | `string` | All genres (semicolon-joined). |
| 16 | `explicitness` | `string` | Explicit-content rating. |
| 17 | `content_advisory` | `string` | Content advisory rating. |
| 18 | `kind` | `string` | Result kind. |
| 19 | `wrapper_type` | `string` | Wrapper type. |
| 20 | `view_url` | `string` | iTunes page URL. |
| 21 | `artist_view_url` | `string` | Publisher page URL. |
| 22 | `track_view_url` | `string` | Latest episode URL. |
| 23 | `track_time_millis` | `number` | Latest episode duration in ms. |
| 24 | `track_duration_minutes` | `number` | Latest episode duration in minutes. |
| 25 | `query` | `string` | Search term that surfaced the podcast. |
| 26 | `store_country` | `string` | Store country of the query. |
| 27 | `release_year` | `number` | Release year. |
| 28 | `age_days` | `number` | Days since release at 2026-11-22. |
| 29 | `genre_count` | `number` | Number of genres. |
| 30 | `is_explicit` | `boolean` | true when marked explicit. |
| 31 | `is_free` | `boolean` | true when the collection price is zero. |
| 32 | `price_band` | `string` | Price band. |
| 33 | `has_feed` | `boolean` | true when an RSS feed URL exists. |
| 34 | `has_artwork` | `boolean` | true when artwork exists. |
| 35 | `episode_count_band` | `string` | Episode-count band. |
| 36 | `episodes_per_year` | `number` | Episodes divided by podcast age in years. |
| 37 | `name_length` | `number` | Characters in the title. |
| 38 | `is_comedy` | `boolean` | true for comedy podcasts. |
| 39 | `is_news` | `boolean` | true for news podcasts. |
| 40 | `is_true_crime` | `boolean` | true for true-crime podcasts. |
| 41 | `is_business` | `boolean` | true for business podcasts. |
| 42 | `is_technology` | `boolean` | true for technology podcasts. |
| 43 | `is_health` | `boolean` | true for health podcasts. |
| 44 | `is_sports` | `boolean` | true for sports podcasts. |
| 45 | `is_education` | `boolean` | true for education podcasts. |
| 46 | `is_fiction` | `boolean` | true for fiction/drama podcasts. |
| 47 | `is_kids` | `boolean` | true for kids/family podcasts. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
