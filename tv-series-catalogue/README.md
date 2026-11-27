---
annotations_creators:
- no-annotation
language:
- en
license: cc-by-4.0
multilinguality:
- monolingual
size_categories:
- 10K<n<1M
source_datasets:
- original
task_categories:
- tabular-classification
task_ids: []
pretty_name: "Television Series Catalogue TVmaze"
tags:
- tabular
- history
---

# Television Series Catalogue TVmaze


## ⭐ Upvote & Support
If you find this dataset useful for your research, machine learning projects, or data visualization, please consider giving it an **Upvote**! Your support helps make open data more accessible to the community.


# Television Series Catalogue — TVmaze

**Subtitle:** 91,563 TV shows with genres, networks, ratings, run dates, cast of identifiers and synopses.

---

## 📖 Description

### 91,563 television series from around the world

TVmaze catalogues every scripted, reality, animated and documentary series it can identify. This
dataset contains **91,563 shows** with **63 parameters**, from 1930s radio-era titles to
current streaming releases.

- **Show** — TVmaze id, title, type, language, status, genres, episode runtime and average runtime.
- **Broadcast** — premiere and finale dates, run length in years, schedule time and days,
  network, network country and timezone, web channel and DVD country.
- **Ratings** — TVmaze user rating (0-10), popularity weight, a rating × weight score and the
  number of genres.
- **Identifiers** — IMDb, TheTVDB and TVRage ids, TVmaze URL and official site.
- **Text and media** — plain-text synopsis (600 characters) with its length, poster image URL and
  the title of the most recent episode.
- **Derived** — premiere decade, running / ended / upcoming flags, 9 type flags, 6 genre flags,
  presence flags and show age in days.

**11,885 shows carry a rating** (mean **6.71**) and **14,582 are still running**. The
networks with the most titles are United States (18,493), United Kingdom (13,600), Japan (5,975), Russian Federation (5,035), Korea, Republic of (2,683).

## 🧾 Columns (63)

`tvmaze_id`, `name`, `type`, `language`, `status`, `genres`, `genre_count`, `runtime_minutes`, `average_runtime_minutes`, `premiered`, `premiered_year`, `premiered_month`, `ended`, `ended_year`, `run_years`, `is_running`, `is_ended`, `is_upcoming`, `schedule_time`, `schedule_days`, `schedule_day_count`, `rating_average`, `weight`, `network_name`, `network_id`, `network_country`, `network_country_code`, `network_timezone`, `web_channel`, `dvd_country`, `tvrage_id`, `thetvdb_id`, `imdb_id`, `url`, `official_site`, `image_url`, `summary`, `summary_length`, `updated_date`, `previous_episode`, `has_image`, `has_official_site`, `has_imdb`, `has_thetvdb`, `has_web_channel`, `premiered_decade`, `is_scripted`, `is_reality`, `is_animation`, `is_documentary`, `is_game_show`, `is_talk_show`, `is_award_show`, `is_children`, `is_variety`, `genre_drama`, `genre_comedy`, `genre_action`, `genre_scifi`, `genre_crime`, `genre_thriller`, `rating_weighted`, `age_days`

## 💡 Ideas for using this data

1. **Ratings** — what predicts a high TVmaze rating: genre, network, runtime?
2. **Longevity** — run length by type and country.
3. **Genres** — genre co-occurrence networks.
4. **Streaming vs broadcast** — web-channel shows vs network shows.
5. **Timeline** — shows premiered per year since 1950.
6. **Runtime** — episode length by genre and decade.
7. **Cancellation** — status mix by network and premiere decade.
8. **NLP** — topic-model the synopses.

## 📁 Files

| File | What it is |
|---|---|
| `tv_series.csv` | 91,563 shows x 63 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`television`, `entertainment`, `media`, `ratings`, `tvmaze`, `culture`, `streaming`

## 🔗 Provenance

- **Source:** **TVmaze API** (`api.tvmaze.com/shows`, paginated 250 shows per page).
- **Processing:** every page of the public catalogue was read until the API returned 404; nested
  network, country, schedule, rating, image and externals objects were flattened; HTML was stripped
  from synopses; flags and derived metrics added.
- **Snapshot date:** 27 November 2026.

## 🔄 Update frequency

**Daily.** TVmaze updates its catalogue continuously.

## ⚠️ Caveats

- TVmaze is a community-maintained database, so coverage of non-English and older shows is uneven.
- Ratings are TVmaze user ratings, not Nielsen or IMDb scores.
- The episode count is not included because it would require one request per show.
- Premiere and end dates are missing for some titles.
- Summaries are truncated to 600 characters and stripped of HTML.
- Status values are as recorded by TVmaze and can lag real-world cancellations.

## 📜 Licence

TVmaze data, CC BY-SA 4.0 — attribute TVmaze (tvmaze.com).

