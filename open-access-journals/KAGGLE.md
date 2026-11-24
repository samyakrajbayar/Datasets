# Open-Access Journals - DOAJ Directory

**Subtitle:** 23,667 journals from DOAJ with fees, licenses, policies and metadata

**Tags:** `tabular`, `publishing`, `research`

**Dataset File:** `doaj_journals.csv` (23,667 rows, 77 columns, 27.3 MB)

**Provenance & Source:** Directory of Open Access Journals (doaj.org)

**Expected Update Frequency:** `annually`

---

## 📖 Description

### Every journal in the Directory of Open Access Journals

DOAJ publishes its entire journal index as a single CSV. This dataset contains **23,667 journals from
141 countries** with **77 parameters** — the full DOAJ export, not a sample.

- **Identity** — title, alternative title, journal URL, DOAJ URL, print and electronic ISSN, publisher,
  country and supporting organisations.
- **Open-access terms** — OA start year, licences and attributes, licence URL, machine-readable CC flag,
  copyright retention, DOAJ compliance.
- **Editorial policy** — peer-review process and URL, plagiarism screening, aims/scope, editorial board
  and author-instruction URLs.
- **Fees** — APC flag, amount and URL, waiver policy, other fees, plus derived APC band, diamond-OA and
  waiver flags.
- **Preservation and identifiers** — preservation services and national-library partner, deposit policy,
  persistent identifiers.
- **Classification** — LCC codes, subjects, keywords and accepted languages.
- **Activity** — article-record count, most recent article date, added/updated/reviewed dates.
- **Derived** — multilingual, fee, licence, preservation and metadata-coverage flags, parsed amounts and
  days since update.

**8,889 journals charge an APC**, **23,516** use a Creative Commons licence, and the file covers the
whole DOAJ index — ideal for open-access policy and publishing-economics research.

## 🧾 Columns (77)

`title`, `journal_url`, `doaj_url`, `oa_start_year`, `alternative_title`, `pissn`, `eissn`, `keywords`, `languages`, `publisher`, `country`, `other_organisation`, `other_organisation_country`, `licenses`, `license_attributes`, `license_url`, `cc_machine_readable`, `author_holds_copyright`, `copyright_url`, `review_process`, `review_url`, `plagiarism_policy`, `aims_url`, `editorial_board_url`, `instructions_url`, `weeks_to_publication`, `apc`, `apc_url`, `apc_amount`, `waiver_policy`, `waiver_url`, `other_fees`, `other_fees_url`, `preservation_services`, `preservation_national_library`, `preservation_url`, `deposit_policy`, `deposit_url`, `persistent_identifiers`, `doaj_compliant`, `continues`, `continued_by`, `lcc_codes`, `subscribe_to_open`, `mirror_journal`, `open_journals_collective`, `subjects`, `added_date`, `last_updated`, `last_full_review`, `article_records`, `most_recent_article`, `title_length`, `is_multilingual`, `language_count`, `keyword_count`, `subject_count`, `lcc_count`, `has_apc`, `apc_amount_numeric`, `apc_band`, `has_waiver`, `has_other_fees`, `is_diamond`, `is_cc_licensed`, `has_cc_machine_readable`, `author_retains_copyright`, `has_persistent_identifier`, `preservation_count`, `has_preservation`, `has_deposit_policy`, `weeks_to_publication_numeric`, `added_year`, `days_since_update`, `has_review_process`, `has_plagiarism_policy`, `has_doaj_record_url`

## 💡 Ideas for using this data

1. **Diamond open access** — countries and subjects that publish without fees.
2. **APC geography** — APC levels by country, publisher and discipline.
3. **Licence adoption** — CC BY vs CC BY-NC vs other licences by subject.
4. **Policy quality** — preservation, PID, plagiarism and review-policy coverage by region.
5. **Publication speed** — reported weeks to publication by publisher and subject.
6. **Publisher concentration** — the largest publishers by journal count.
7. **Multilingual publishing** — language combinations and regional patterns.
8. **Metadata completeness** — which fields are missing most, and where?
9. **Journal recommender** — match a manuscript to journals by subject, APC and speed.

## 📁 Files

| File | What it is |
|---|---|
| `doaj_journals.csv` | 23,667 journals x 77 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`open-access`, `journals`, `doaj`, `publishing`, `bibliometrics`, `research-policy`, `metadata`

## 🔗 Provenance

- **Source:** **DOAJ journal CSV export**, `https://doaj.org/csv` (the complete public journal
  index, about 26 MB).
- **Scope:** every journal record in the export at snapshot time.
- **Processing:** 52 source columns renamed to snake_case; fee, licence, language, subject and date
  fields parsed; 25 derived flags, counts and bands added.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Daily.** DOAJ updates its index and regenerates the CSV export continuously.

## ⚠️ Caveats

- APC amounts are self-reported as free text and may mix currencies; no conversion is applied.
- Policy fields are journal declarations, not independently audited.
- Some fields are empty for older or less complete records.
- `weeks_to_publication` is self-reported and often missing.
- DOAJ vets journals for inclusion, but inclusion is not an endorsement of quality.
- Country refers to the publisher, which may differ from the editorial base.
- The CSV export is a snapshot; DOAJ changes continuously.

## 📜 Licence

DOAJ metadata is released under CC0 1.0.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `title` | `string` | Journal title. |
| 2 | `journal_url` | `string` | Journal website. |
| 3 | `doaj_url` | `string` | DOAJ record URL. |
| 4 | `oa_start_year` | `number` | Year the journal began publishing all content under an open licence. |
| 5 | `alternative_title` | `string` | Alternative title. |
| 6 | `pissn` | `string` | Print ISSN. |
| 7 | `eissn` | `string` | Electronic ISSN. |
| 8 | `keywords` | `string` | Author keywords (comma-separated). |
| 9 | `languages` | `string` | Manuscript languages accepted. |
| 10 | `publisher` | `string` | Publisher name. |
| 11 | `country` | `string` | Country of the publisher. |
| 12 | `other_organisation` | `string` | Other supporting organisation. |
| 13 | `other_organisation_country` | `string` | Country of the other organisation. |
| 14 | `licenses` | `string` | Licences used by the journal. |
| 15 | `license_attributes` | `string` | Licence attributes (e.g. CC BY, CC BY-NC). |
| 16 | `license_url` | `string` | Licence terms URL. |
| 17 | `cc_machine_readable` | `string` | Whether CC licensing is machine-readable in articles. |
| 18 | `author_holds_copyright` | `string` | Whether authors retain copyright. |
| 19 | `copyright_url` | `string` | Copyright policy URL. |
| 20 | `review_process` | `string` | Peer-review process description. |
| 21 | `review_url` | `string` | Peer-review policy URL. |
| 22 | `plagiarism_policy` | `string` | Plagiarism screening policy. |
| 23 | `aims_url` | `string` | Aims and scope URL. |
| 24 | `editorial_board_url` | `string` | Editorial board URL. |
| 25 | `instructions_url` | `string` | Author instructions URL. |
| 26 | `weeks_to_publication` | `number` | Average weeks from submission to publication (as reported). |
| 27 | `apc` | `string` | Whether an article processing charge applies. |
| 28 | `apc_url` | `string` | APC information URL. |
| 29 | `apc_amount` | `string` | APC amount as reported (free text). |
| 30 | `waiver_policy` | `string` | APC waiver policy. |
| 31 | `waiver_url` | `string` | Waiver policy URL. |
| 32 | `other_fees` | `string` | Whether other fees apply. |
| 33 | `other_fees_url` | `string` | Other fees URL. |
| 34 | `preservation_services` | `string` | Preservation services listed. |
| 35 | `preservation_national_library` | `string` | National-library preservation partner. |
| 36 | `preservation_url` | `string` | Preservation policy URL. |
| 37 | `deposit_policy` | `string` | Deposit policy directories. |
| 38 | `deposit_url` | `string` | Deposit policy URL. |
| 39 | `persistent_identifiers` | `string` | Persistent article identifiers used. |
| 40 | `doaj_compliant` | `string` | Whether the journal meets DOAJ's open-access definition. |
| 41 | `continues` | `string` | Journal(s) this title continues. |
| 42 | `continued_by` | `string` | Journal(s) that continue this title. |
| 43 | `lcc_codes` | `string` | Library of Congress Classification codes. |
| 44 | `subscribe_to_open` | `string` | Subscribe-to-Open participation. |
| 45 | `mirror_journal` | `string` | Mirror journal flag. |
| 46 | `open_journals_collective` | `string` | Open Journals Collective participation. |
| 47 | `subjects` | `string` | Subject terms. |
| 48 | `added_date` | `datetime` | Date added to DOAJ. |
| 49 | `last_updated` | `datetime` | Date the DOAJ record was last updated. |
| 50 | `last_full_review` | `date` | Date of the last full DOAJ review. |
| 51 | `article_records` | `number` | Number of article records indexed. |
| 52 | `most_recent_article` | `datetime` | Date of the most recent indexed article. |
| 53 | `title_length` | `number` | Characters in the title. |
| 54 | `is_multilingual` | `boolean` | true when more than one manuscript language is accepted. |
| 55 | `language_count` | `number` | Number of accepted manuscript languages. |
| 56 | `keyword_count` | `number` | Number of keywords. |
| 57 | `subject_count` | `number` | Number of subject terms. |
| 58 | `lcc_count` | `number` | Number of LCC codes. |
| 59 | `has_apc` | `boolean` | true when an APC applies. |
| 60 | `apc_amount_numeric` | `number` | First numeric APC amount parsed from the text. |
| 61 | `apc_band` | `string` | APC amount band. |
| 62 | `has_waiver` | `boolean` | true when an APC waiver policy exists. |
| 63 | `has_other_fees` | `boolean` | true when other fees apply. |
| 64 | `is_diamond` | `boolean` | true when there is no APC and no other fees. |
| 65 | `is_cc_licensed` | `boolean` | true when a Creative Commons licence is used. |
| 66 | `has_cc_machine_readable` | `boolean` | true when CC licensing is machine-readable. |
| 67 | `author_retains_copyright` | `boolean` | true when authors retain copyright. |
| 68 | `has_persistent_identifier` | `boolean` | true when persistent identifiers are used. |
| 69 | `preservation_count` | `number` | Number of preservation services. |
| 70 | `has_preservation` | `boolean` | true when a preservation service is listed. |
| 71 | `has_deposit_policy` | `boolean` | true when a deposit policy is listed. |
| 72 | `weeks_to_publication_numeric` | `number` | Parsed weeks-to-publication value. |
| 73 | `added_year` | `number` | Year added to DOAJ. |
| 74 | `days_since_update` | `number` | Days between last update and 2026-11-22. |
| 75 | `has_review_process` | `boolean` | true when a review process is described. |
| 76 | `has_plagiarism_policy` | `boolean` | true when a plagiarism policy is declared. |
| 77 | `has_doaj_record_url` | `boolean` | true when a DOAJ record URL exists. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
