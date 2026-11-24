# Open Library Book Catalogue — 13,088 Works Across 20 Subjects

**Subtitle:** A subject-sampled slice of Open Library with authors, publication decades, page counts, ratings, reading activity and ebook availability.

---

## 📖 Description

Open Library holds tens of millions of bibliographic records, which makes it wonderful for research and painful to work with. This dataset is a **ready-to-analyse sample of 13,088 works** drawn evenly from 20 popular subjects, giving you a balanced corpus for text, recommendation and publishing-market analysis.

**Subjects included:** fantasy, science fiction, mystery, romance, history, biography, philosophy, poetry, psychology, business, mathematics, physics, cooking, travel, art, computer programming, medicine, politics, religion, education — roughly 600–700 unique works each, with `source_subject` recording where each row came from.

**What each record contains:**

- **Bibliographic** — work key, title, subtitle, primary author, full author list, author count, first publish year, derived decade and `age_years` (relative to 2026), language list and count.
- **Descriptive metadata** — up to 12 subject tags, subject count, plus counts of associated people, places and time periods.
- **Physical** — median page count across editions, edition count, ISBN count, publisher count, first publisher and place of publication.
- **Engagement** — average rating, rating count, reading-log count, want-to-read, currently-reading and already-read counts, and a derived `completion_rate`.
- **Access** — ebook access category (borrowable / printdisabled / public / no_ebook), full-text availability, public-scan flag and number of Internet Archive scans.
- **Text features** — title length and word count, useful as cheap baselines before embeddings.

## 🧾 Columns (36)

`work_key`, `title`, `subtitle`, `primary_author`, `n_authors`, `authors`, `first_publish_year`, `publication_decade`, `age_years`, `n_languages`, `languages`, `n_subjects`, `subjects`, `n_people`, `n_places`, `n_times`, `number_of_pages_median`, `edition_count`, `ratings_average`, `ratings_count`, `readinglog_count`, `want_to_read_count`, `currently_reading_count`, `already_read_count`, `completion_rate`, `ebook_access`, `has_fulltext`, `public_scan`, `n_ia_scans`, `n_isbn`, `n_publishers`, `publisher`, `publish_place`, `title_length`, `title_word_count`, `source_subject`

## 💡 Ideas for using this data

1. **What makes a book popular?** Model `ratings_count` / `want_to_read_count` from page count, decade, subject and author count.
2. **Genre length profiles** — page-count distributions by subject (poetry vs fantasy vs medicine).
3. **Recommender** — item-item similarity using subject overlap plus title tokens.
4. **Publishing trends** — works per decade by subject; spot the post-2000 explosion in fantasy and programming titles.
5. **Ebook access and age** — how strongly does publication year predict public-domain scan availability?
6. **Author productivity** — authors appearing across multiple subjects (only within this sample).
7. **NLP** — train a subject classifier on titles, then inspect which words are most predictive.

## ⚠️ Caveats

- This is a **subject-filtered sample**, not the whole catalogue; it is not representative of all published books.
- Subject tagging on Open Library is community-contributed and inconsistent; the same book can carry dozens of overlapping tags.
- Ratings and reading-log counts are sparse — many rows are legitimately blank, and popular bestsellers dominate the non-null values.
- Only 12 subject tags per work are kept (out of a potentially much longer list).
- Deduplication used the work key; different editions of the same work share one row.

## 🔗 Provenance & licence

- Source: Open Library Search API (`openlibrary.org/search.json`), an Internet Archive project. Bibliographic metadata is openly available; cover images and full texts carry their own licences.
- Snapshot: November 2026. 13,088 rows × 36 columns.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
