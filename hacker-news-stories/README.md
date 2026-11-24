---
license: cc-by-4.0
task_categories:
- tabular
tags:
- tabular
pretty_name: "Hacker News Stories 2023-2026"
---

# Hacker News Stories 2023-2026

**Subtitle:** 36,000 stories with points, comments, domains, author & timestamp info

**Tags:** `tabular`, `technology`, `social-media`

**Dataset File:** `hacker_news_stories.csv` (41,784 rows, 30 columns, 12.8 MB)

**Provenance & Source:** Algolia Hacker News Search API (hn.algolia.com)

**Expected Update Frequency:** `monthly`

---

## 📖 Description

### 36,000 Hacker News stories

Hacker News is the technology community's most-read link board. This dataset samples **36,000 stories
submitted between December 2023 and November 2026** with **30 parameters**.

- **Story** — item id, title, URL and derived domain, submitter, points, comment count and timestamps.
- **Post type** — self text plus Ask HN, Show HN and job flags.
- **Derived** — title/url lengths, tag count, age in days and hours, points per hour, comments per
  point, year/month/day/hour/weekday, weekend flag and an engagement score.

Stories link to **14,158 distinct domains**, and **1,637 Ask HN** plus **3,420 Show HN**
posts are included. The monthly sampling covers every month in the window, so the file supports both
time-series and content analysis.

## 🧾 Columns (30)

`object_id`, `title`, `url`, `domain`, `author`, `points`, `num_comments`, `created_at`, `created_at_i`, `story_text`, `has_url`, `has_text`, `is_ask_hn`, `is_show_hn`, `is_job`, `title_length`, `title_word_count`, `url_length`, `tag_count`, `age_days`, `age_hours`, `points_per_hour`, `comments_per_point`, `year`, `month`, `day`, `hour`, `day_of_week`, `is_weekend`, `engagement_score`

## 💡 Ideas for using this data

1. **What goes viral** — points and comments vs domain, title style and post type.
2. **Domain influence** — which domains dominate the front page over time?
3. **Show HN vs Ask HN** — engagement differences and best posting times.
4. **Title linguistics** — clickbait patterns, question titles and word choice.
5. **Temporal patterns** — hour-of-week heatmaps of submissions and engagement.
6. **Topic clustering** — TF-IDF on titles to find recurring technology themes.
7. **Aging curve** — points per hour for old vs recent stories (survivorship caveat).
8. **Domain diversity** — concentration of links across the long tail.
9. **Predicting engagement** — regress log points on title and domain features.

## 📁 Files

| File | What it is |
|---|---|
| `hacker_news_stories.csv` | 36,000 stories x 30 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`hacker-news`, `technology`, `social-media`, `engagement`, `text`, `time-series`, `links`

## 🔗 Provenance

- **Source:** **Algolia Hacker News Search API**,
  `https://hn.algolia.com/api/v1/search_by_date?tags=story` (unofficial mirror of the official
  Firebase HN API).
- **Scope:** up to 1,000 stories per month for December 2023 through November 2026.
- **Processing:** monthly queries with `numericFilters` on `created_at_i`, deduplicated by item id;
  domains parsed from URLs; engagement and calendar features derived.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Continuous.** New stories are submitted constantly.

## ⚠️ Caveats

- Algolia caps each query at 1,000 hits, so months with more stories are truncated.
- Points and comments are point-in-time snapshot values, not final totals.
- Deleted or dead stories are not returned.
- `story_text` is HTML and only present for self-posts.
- Domain is empty for self-posts and for some non-standard URLs.
- November 2026 is partial (through the snapshot date).
- Algolia is an unofficial mirror; ids and timestamps match HN but availability is not guaranteed.

## 📜 Licence

Hacker News content belongs to its authors; metadata is provided for research use.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `object_id` | `number` | Hacker News item id. |
| 2 | `title` | `string` | Story title. |
| 3 | `url` | `string` | Linked URL, where the story links out. |
| 4 | `domain` | `string` | Domain of the linked URL. |
| 5 | `author` | `string` | Submitter username. |
| 6 | `points` | `number` | Points at snapshot time. |
| 7 | `num_comments` | `number` | Comment count. |
| 8 | `created_at` | `datetime` | Submission timestamp (ISO). |
| 9 | `created_at_i` | `number` | Submission Unix timestamp. |
| 10 | `story_text` | `string` | Self-post text (Ask HN, Show HN, ...). |
| 11 | `has_url` | `boolean` | true when the story links to an external URL. |
| 12 | `has_text` | `boolean` | true when the story has self-post text. |
| 13 | `is_ask_hn` | `boolean` | true for Ask HN posts. |
| 14 | `is_show_hn` | `boolean` | true for Show HN posts. |
| 15 | `is_job` | `boolean` | true for job posts. |
| 16 | `title_length` | `number` | Characters in the title. |
| 17 | `title_word_count` | `number` | Words in the title. |
| 18 | `url_length` | `number` | Characters in the URL. |
| 19 | `tag_count` | `number` | Number of Algolia tags. |
| 20 | `age_days` | `number` | Days since submission at 2026-11-22. |
| 21 | `age_hours` | `number` | Hours since submission. |
| 22 | `points_per_hour` | `number` | Points divided by age in hours. |
| 23 | `comments_per_point` | `number` | Comments divided by points. |
| 24 | `year` | `number` | Submission year. |
| 25 | `month` | `number` | Submission month. |
| 26 | `day` | `number` | Submission day of month. |
| 27 | `hour` | `number` | Submission hour (UTC). |
| 28 | `day_of_week` | `string` | Submission weekday. |
| 29 | `is_weekend` | `boolean` | true for Saturday/Sunday. |
| 30 | `engagement_score` | `number` | Comments + points (simple engagement total). |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
