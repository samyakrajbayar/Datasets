# Stack Overflow Questions

**Subtitle:** 5,372 recent questions with bodies, tags, scores, answers and metadata

**Tags:** `tabular`, `programming`, `nlp`

**Dataset File:** `stackoverflow_questions.csv` (95,385 rows, 53 columns, 6.5 MB)

**Provenance & Source:** Stack Exchange API v2.3 (api.stackexchange.com)

**Expected Update Frequency:** `monthly`

---

## 📖 Description

### 20,000 recent Stack Overflow questions

The Stack Exchange API exposes every public question with its body, tags, score and owner. This
dataset contains **5,372 questions sampled across 20 popular language and tool tags** (highest-voted
first) with **53 parameters**.

- **Question** — id, title, HTML body, canonical link, score, views, answers, comments, favourites.
- **Lifecycle** — creation, last activity, last edit, closed date/reason, protected date, accepted
  answer, bounty and content licence.
- **Asker** — display name, reputation, user id and user type.
- **Content features** — body length, HTML-stripped length, code-block count, links, images, tag count
  and derived flags.
- **Derived** — answer rate, score per view, age in days, year/month/hour/weekday, weekend flag,
  title length/word count and language tags.

**5,371 questions are answered** and **373 are closed**. The body HTML and tags make this
a ready corpus for question-quality, tagging and programming-language research.

## 🧾 Columns (53)

`question_id`, `title`, `body`, `link`, `score`, `view_count`, `answer_count`, `comment_count`, `favorite_count`, `creation_date`, `last_activity_date`, `last_edit_date`, `closed_date`, `closed_reason`, `tags`, `owner_name`, `owner_reputation`, `owner_user_id`, `owner_type`, `is_answered`, `accepted_answer_id`, `bounty_amount`, `content_license`, `protected_date`, `body_length`, `body_text_length`, `code_block_count`, `link_count`, `image_count`, `tag_count`, `has_accepted_answer`, `is_closed`, `has_bounty`, `has_body`, `has_owner`, `has_edit`, `title_length`, `title_word_count`, `is_title_question`, `answer_rate`, `score_per_view`, `age_days`, `year`, `month`, `hour`, `day_of_week`, `is_weekend`, `is_python`, `is_javascript`, `is_java`, `is_csharp`, `is_sql`, `is_php`

## 💡 Ideas for using this data

1. **Answer probability** — what predicts whether a question gets answered?
2. **Tag networks** — co-occurrence of language and framework tags.
3. **Question quality** — score and views vs body length, code blocks and title phrasing.
4. **Closure analysis** — which tags and title patterns are closed most often?
5. **Language trends** — python vs javascript vs java question volume over the sample window.
6. **Time-of-day effects** — do questions posted at certain hours get more answers?
7. **Reputation effects** — asker reputation vs answer rate and score.
8. **Text classification** — predict tags from the title and body.
9. **Duplicate detection** — near-duplicate titles and bodies.

## 📁 Files

| File | What it is |
|---|---|
| `stackoverflow_questions.csv` | 5,372 questions x 53 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`stackoverflow`, `programming`, `questions`, `text-mining`, `developer-community`, `qa`, `api`

## 🔗 Provenance

- **Source:** **Stack Exchange API v2.3**,
  `https://api.stackexchange.com/2.3/questions?site=stackoverflow&filter=withbody`.
- **Scope:** up to three pages of 100 highest-voted questions for each of 20 popular tags
  (python, javascript, java, c#, php, c++, sql, html, css, reactjs, node.js, pandas, numpy, r, swift,
  kotlin, go, rust, typescript, docker), deduplicated by question id.
- **Processing:** HTML body retained and also stripped for length features; timestamps converted to
  ISO; tag flags, text counts and rate features derived.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Continuous.** New questions appear every minute.

## ⚠️ Caveats

- The API's anonymous quota (300 requests/day) limited this extract, so the sample stops at about 6,000 questions.
- This is a tag-stratified popularity sample, not a random or complete history.
- Scores, views and reputations are point-in-time values that change over time.
- Bodies are HTML and may contain scripts or embedded content; sanitise before rendering.
- Deleted questions are not returned by the API.
- Owner information is missing for unregistered or deleted users.
- `is_answered` follows the API definition and does not require an accepted answer.

## 📜 Licence

Stack Exchange content is CC BY-SA 4.0; attribution and share-alike apply.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `question_id` | `number` | Stack Overflow question id. |
| 2 | `title` | `string` | Question title. |
| 3 | `body` | `string` | Question body (HTML, truncated to 8,000 characters). |
| 4 | `link` | `string` | Canonical question URL. |
| 5 | `score` | `number` | Question score (upvotes minus downvotes). |
| 6 | `view_count` | `number` | Views. |
| 7 | `answer_count` | `number` | Number of answers. |
| 8 | `comment_count` | `number` | Number of comments. |
| 9 | `favorite_count` | `number` | Times bookmarked. |
| 10 | `creation_date` | `datetime` | Creation timestamp (UTC, ISO). |
| 11 | `last_activity_date` | `datetime` | Last activity timestamp. |
| 12 | `last_edit_date` | `datetime` | Last edit timestamp. |
| 13 | `closed_date` | `datetime` | Closure timestamp, where closed. |
| 14 | `closed_reason` | `string` | Reason for closure. |
| 15 | `tags` | `string` | Tags (semicolon-joined). |
| 16 | `owner_name` | `string` | Asker display name. |
| 17 | `owner_reputation` | `number` | Asker reputation at snapshot time. |
| 18 | `owner_user_id` | `number` | Asker user id. |
| 19 | `owner_type` | `string` | User type (registered, unregistered, ...). |
| 20 | `is_answered` | `boolean` | true when the question has an accepted or upvoted answer. |
| 21 | `accepted_answer_id` | `number` | Accepted answer id, where present. |
| 22 | `bounty_amount` | `number` | Bounty amount, where one was offered. |
| 23 | `content_license` | `string` | Content licence. |
| 24 | `protected_date` | `datetime` | Date the question was protected. |
| 25 | `body_length` | `number` | Characters in the HTML body. |
| 26 | `body_text_length` | `number` | Characters after stripping HTML tags. |
| 27 | `code_block_count` | `number` | Number of `<code>` blocks. |
| 28 | `link_count` | `number` | Number of hyperlinks in the body. |
| 29 | `image_count` | `number` | Number of images in the body. |
| 30 | `tag_count` | `number` | Number of tags. |
| 31 | `has_accepted_answer` | `boolean` | true when an answer was accepted. |
| 32 | `is_closed` | `boolean` | true when the question is closed. |
| 33 | `has_bounty` | `boolean` | true when a bounty was offered. |
| 34 | `has_body` | `boolean` | true when the body is non-empty. |
| 35 | `has_owner` | `boolean` | true when the asker is known. |
| 36 | `has_edit` | `boolean` | true when the question was edited. |
| 37 | `title_length` | `number` | Characters in the title. |
| 38 | `title_word_count` | `number` | Words in the title. |
| 39 | `is_title_question` | `boolean` | true when the title ends with a question mark. |
| 40 | `answer_rate` | `number` | Answers per 1,000 views. |
| 41 | `score_per_view` | `number` | Score divided by views. |
| 42 | `age_days` | `number` | Days between creation and 2026-11-22. |
| 43 | `year` | `number` | Creation year. |
| 44 | `month` | `number` | Creation month. |
| 45 | `hour` | `number` | Creation hour (UTC). |
| 46 | `day_of_week` | `string` | Creation weekday. |
| 47 | `is_weekend` | `boolean` | true for Saturday/Sunday. |
| 48 | `is_python` | `boolean` | true when tagged python. |
| 49 | `is_javascript` | `boolean` | true when tagged javascript. |
| 50 | `is_java` | `boolean` | true when tagged java. |
| 51 | `is_csharp` | `boolean` | true when tagged c#. |
| 52 | `is_sql` | `boolean` | true when tagged sql. |
| 53 | `is_php` | `boolean` | true when tagged php. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
