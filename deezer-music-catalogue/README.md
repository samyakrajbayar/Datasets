---
license: other
task_categories:
- tabular
tags:
- tabular
pretty_name: "Deezer Music Catalogue Sample"
---

# Deezer Music Catalogue Sample

**Subtitle:** 14,654 tracks with artist, album, duration, popularity & genre queries

**Tags:** `tabular`, `music`, `audio`

**Dataset File:** `deezer_tracks.csv` (14,654 rows, 31 columns, 8.3 MB)

**Provenance & Source:** Deezer Public API (api.deezer.com)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### 20,000 tracks from the Deezer catalogue

Deezer's public search API exposes track metadata without a key. This dataset contains
**14,654 unique tracks** from **9,098 artists** and **11,306 albums**, with
**31 parameters** per track.

- **Track** — id, title, short title, version suffix, duration, popularity rank, explicit flags,
  preview URL and cover art.
- **Artist** — id, name and image URL.
- **Album** — id, title and cover URL.
- **Provenance** — the search query that surfaced each track (genre, mood, decade or instrument).
- **Derived** — duration in minutes and bands, explicit/version/preview flags, title, artist and album
  name lengths, long/short track flags and popularity band.

**2,432 tracks are explicit**. The query column makes the file usable as a genre and mood
sample, while duration, popularity and title features support musicology and recommendation work.

## 🧾 Columns (31)

`track_id`, `title`, `title_short`, `title_version`, `duration_seconds`, `duration_minutes`, `rank`, `rank_band`, `explicit_lyrics`, `explicit_content_lyrics`, `explicit_content_cover`, `preview_url`, `cover_url`, `artist_id`, `artist_name`, `artist_picture`, `album_id`, `album_title`, `album_cover`, `query`, `duration_band`, `is_explicit`, `has_version`, `has_preview`, `title_length`, `title_word_count`, `artist_name_length`, `album_title_length`, `is_long_track`, `is_short_track`, `is_popular`

## 💡 Ideas for using this data

1. **Genre landscape** — track counts and popularity by search query.
2. **Duration trends** — has song length changed by genre?
3. **Explicit content** — prevalence by genre and artist.
4. **Title patterns** — remix/live/version suffixes and title lengths.
5. **Artist concentration** — the long tail of artists vs repeat appearances.
6. **Album structure** — tracks per album in the sample.
7. **Popularity vs duration** — do shorter tracks rank higher?
8. **Text analysis** — title word frequencies by genre query.
9. **Recommendation features** — a clean track-level feature table.

## 📁 Files

| File | What it is |
|---|---|
| `deezer_tracks.csv` | 14,654 tracks x 31 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`music`, `deezer`, `tracks`, `audio`, `genres`, `catalogue`, `recommendation`

## 🔗 Provenance

- **Source:** **Deezer public API**, `https://api.deezer.com/search/track`, no key required.
- **Scope:** the first 200 results for each of 80 genre/mood/decade/instrument queries, deduplicated
  by track id — a query-stratified sample, not the full catalogue.
- **Processing:** nested artist and album objects flattened; duration, popularity and title features
  derived; the originating query retained.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Continuous.** The catalogue changes as tracks are added and removed.

## ⚠️ Caveats

- The sample is query-stratified and capped at 200 results per query, so it is not representative.
- Deezer's `rank` is a proprietary popularity score, not a play count.
- Preview URLs expire and may not resolve after the snapshot.
- Release dates and genres are not returned by the track search endpoint.
- Duplicate recordings under different ids are possible.
- Metadata is user/label supplied and can contain inconsistencies.
- The API is undocumented for bulk use; availability can change.

## 📜 Licence

Deezer metadata is provided for non-commercial use; recordings remain with their rights holders.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `track_id` | `number` | Deezer track id. |
| 2 | `title` | `string` | Track title. |
| 3 | `title_short` | `string` | Short title. |
| 4 | `title_version` | `string` | Version suffix (remix, live, ...). |
| 5 | `duration_seconds` | `number` | Track duration in seconds. |
| 6 | `duration_minutes` | `number` | Duration in minutes. |
| 7 | `rank` | `number` | Deezer popularity rank (higher is more popular). |
| 8 | `rank_band` | `string` | Popularity band. |
| 9 | `explicit_lyrics` | `boolean` | true when lyrics are explicit. |
| 10 | `explicit_content_lyrics` | `number` | Explicit-content code for lyrics. |
| 11 | `explicit_content_cover` | `number` | Explicit-content code for cover art. |
| 12 | `preview_url` | `string` | 30-second preview MP3 URL. |
| 13 | `cover_url` | `string` | Album cover URL. |
| 14 | `artist_id` | `number` | Artist id. |
| 15 | `artist_name` | `string` | Artist name. |
| 16 | `artist_picture` | `string` | Artist image URL. |
| 17 | `album_id` | `number` | Album id. |
| 18 | `album_title` | `string` | Album title. |
| 19 | `album_cover` | `string` | Album cover URL. |
| 20 | `query` | `string` | Search query that surfaced the track. |
| 21 | `duration_band` | `string` | Duration band. |
| 22 | `is_explicit` | `boolean` | true when the track is explicit. |
| 23 | `has_version` | `boolean` | true when the title has a version suffix. |
| 24 | `has_preview` | `boolean` | true when a preview URL exists. |
| 25 | `title_length` | `number` | Characters in the title. |
| 26 | `title_word_count` | `number` | Words in the title. |
| 27 | `artist_name_length` | `number` | Characters in the artist name. |
| 28 | `album_title_length` | `number` | Characters in the album title. |
| 29 | `is_long_track` | `boolean` | true when longer than six minutes. |
| 30 | `is_short_track` | `boolean` | true when shorter than two minutes. |
| 31 | `is_popular` | `boolean` | true when rank is 500,000 or higher. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
