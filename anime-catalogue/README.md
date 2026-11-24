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
pretty_name: "Anime Catalogue: 5,000 Titles with Scores & Tags"
tags:
- tabular
- media
---

# Anime Catalogue — 5,000 Titles with Scores, Studios, Tags and Runtime

**Subtitle:** The 5,000 most popular anime on AniList, with 42 columns covering ratings, popularity, studios, genres, tags, seasons and airing history.

---

## 📖 Description

Recommendation systems and popularity analyses usually need three things at once: **ratings**, **metadata** and **popularity signals**. This dataset has all three for **5,000 anime titles**, ordered by AniList popularity so you get the culturally relevant slice of the medium rather than a random dump.

**Identity & cataloguing.** AniList id, MyAnimeList id (for joining with MAL datasets), romaji / English / native titles, synonym count, format (TV, MOVIE, OVA, ONA, SPECIAL…), status, source material (manga, light novel, original, game…), country of origin, season and season year.

**Scale & scheduling.** Episode count, episode duration, computed total runtime, start and end year/month, computed `airing_span_months`, trailer host, and the next airing episode for ongoing shows.

**Quality signals.** `average_score` (weighted, 0–100), `mean_score`, `popularity` (users with the title on a list), `favourites`, `trending`, plus a derived `score_per_episode` ratio.

**Creative metadata.** Genres and genre count, the main animation studio(s), community tags with the top five extracted, an adult-content flag, and a description truncated to 800 characters with HTML stripped — ready for NLP.

**Media assets.** Cover colour (great for palette extraction), cover and banner image URLs, and the AniList page URL.

## 🧾 Columns (42)

`anilist_id`, `mal_id`, `title_romaji`, `title_english`, `title_native`, `n_synonyms`, `format`, `status`, `source`, `country_of_origin`, `season`, `season_year`, `episodes`, `duration_min`, `total_runtime_min`, `start_year`, `start_month`, `end_year`, `end_month`, `airing_span_months`, `average_score`, `mean_score`, `popularity`, `favourites`, `trending`, `n_genres`, `genres`, `primary_studio`, `n_studios`, `all_studios`, `n_tags`, `top_tags`, `is_adult`, `description_length`, `description`, `cover_color`, `cover_image_url`, `banner_image_url`, `trailer_site`, `next_airing_episode`, `site_url`, `score_per_episode`

## 💡 Ideas for using this data

1. **Recommender systems** — content-based (genres + tags + studio) or hybrid with popularity-weighted scoring; evaluate precision@k on favourites.
2. **What makes an anime popular?** Regress `popularity` / `favourites` on format, episodes, studio, source and genre features.
3. **Studio analysis** — which studios consistently score above the median? Adjust for genre mix.
4. **Score vs popularity** — find the "underrated" quadrant: high score, low popularity.
5. **NLP on synopses** — topic modelling or embeddings on `description`, then cluster by theme.
6. **Seasonality** — average scores by season and year to test the "sequel fatigue" hypothesis.
7. **Runtime economics** — does `total_runtime_min` predict completion or favourites per minute?

## ⚠️ Caveats

- Titles are the **top 5,000 by popularity**, not a complete catalogue — very obscure or brand-new shows are excluded, which biases score distributions upward.
- Scores are community ratings (selection bias inherent).
- Descriptions are truncated to 800 characters and HTML-stripped.
- `next_airing_episode` is only populated for currently airing shows at snapshot time.
- A handful of entries have missing English titles or MAL ids.

## 🔗 Provenance & licence

- Source: AniList public GraphQL API (anime metadata © their respective studios; AniList community data under AniList's terms).
- Snapshot: November 2026. 5,000 rows × 42 columns. Intended for non-commercial research and portfolio work.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
