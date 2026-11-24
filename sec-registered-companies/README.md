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
pretty_name: "SEC-Registered Companies"
tags:
- tabular
- business
- finance
---

# SEC-Registered Companies

**Subtitle:** 10,399 EDGAR registrants with industry, jurisdiction and filing counts

**Tags:** `finance`, `business`, `investing`, `tabular`

**Dataset File:** `sec_companies.csv` (10,399 rows, 66 columns, 4.9 MB)

**Provenance & Source:** US Securities and Exchange Commission (SEC) EDGAR submissions API

**Expected Update Frequency:** `annually`

---

## 📖 Description

### Every SEC-registered company, with its filing footprint

EDGAR is the U.S. Securities and Exchange Commission's filing system. This dataset lists
**10,399 registrants** — operating companies, funds and trusts — with **66 parameters**
derived from their submissions record.

Per company:
- **Identity** — CIK, name, tickers and exchanges, entity type, filer category, EIN and LEI.
- **Industry** — SIC code, description and a derived SIC division (manufacturing, finance, services, ...).
- **Incorporation and contact** — state/country of incorporation, fiscal year end, business and mailing
  addresses, phone, website and investor-relations site.
- **Filing footprint** — counts of 10-K, 10-Q, 8-K, Form 4, DEF 14A, S-1, 20-F, 6-K, 13F and SC 13G
  filings in EDGAR's recent table, latest filing / annual report / quarterly report dates, the filing
  span and the latest accession number.
- **Derived activity** — active-filer flag, days since the last filing, filings per year, insider-filing
  share, annual-report lag, fund/foreign-issuer/proxy/quarterly-filer flags.

**9,937 companies (95.6%)** filed within 400 days of the snapshot. Because the
recent-filings table is capped by EDGAR, the counts measure recent activity rather than all-time volume —
and the mix of annual, quarterly and insider filings is a good proxy for corporate form.

## 🧾 Columns (66)

`cik`, `name`, `tickers`, `ticker_count`, `primary_ticker`, `exchanges`, `exchange_count`, `entity_type`, `category`, `sic_code`, `sic_description`, `sic_division`, `owner_org`, `fiscal_year_end`, `fiscal_year_end_month`, `state_of_incorporation`, `state_of_incorporation_name`, `is_foreign_incorporated`, `ein`, `lei`, `has_lei`, `description`, `website`, `investor_website`, `phone`, `business_street`, `business_city`, `business_state`, `business_zip`, `mailing_city`, `mailing_state`, `former_name_count`, `latest_former_name`, `latest_filing_date`, `latest_10k_date`, `latest_10q_date`, `filing_count_recent`, `filings_10k`, `filings_10q`, `filings_8k`, `filings_form4`, `filings_def14a`, `filings_s1`, `filings_20f`, `filings_6k`, `filings_13f`, `filings_sc13g`, `insider_transactions_issuer`, `insider_transactions_owner`, `has_recent_filings`, `first_recent_filing`, `latest_accession`, `latest_primary_document`, `filing_span_days`, `is_operating_company`, `is_investment_fund`, `is_large_accelerated`, `is_smaller_reporting`, `is_foreign_issuer`, `files_quarterly`, `has_proxy`, `days_since_latest_filing`, `is_active_filer`, `filings_per_year`, `insider_filing_share`, `annual_report_lag_days`

## 💡 Ideas for using this data

1. **Filer landscape** — entity type and filer category mix; how many registrants are actually operating companies?
2. **Industry map** — SIC division distribution, and which divisions file the most 8-Ks per year.
3. **Activity decay** — `days_since_latest_filing` distribution; find dormant shell companies and delisted names.
4. **Foreign issuers** — 20-F/6-K filers by incorporation jurisdiction.
5. **Insider activity** — Form 4 share of filings as a proxy for insider-trading intensity by industry.
6. **Annual-report lag** — how long after fiscal year end do companies file their 10-K?
7. **Geographic clustering** — business city/state versus SIC division (Delaware incorporations, NYC finance).
8. **Fund universe** — investment funds versus operating companies: different filing rhythms, different columns.
9. **Registry quality** — tickers, LEI and website completeness by filer category.

## 📁 Files

| File | What it is |
|---|---|
| `sec_companies.csv` | 10,399 SEC registrants x 66 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: industries, activity, filing mix. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`finance`, `sec`, `edgar`, `companies`, `stock-market`, `business`, `corporate`, `regulation`, `tabular`, `investment`

## 🔗 Provenance

- **Sources:** SEC EDGAR **company_tickers.json** (CIK ↔ ticker mapping) and the
  **submissions API** (`https://data.sec.gov/submissions/CIK##########.json`) for each registrant.
- **Coverage:** the first 12,000 entries of the ticker file, enriched with their submissions records;
  a small number of CIKs have no submissions JSON and were skipped.
- **Processing:** recent-filings arrays were counted by form type; addresses, former names and
  entity metadata flattened; SIC codes mapped to divisions.
- **Derived columns:** SIC division, fiscal-year-end month, filing counts and rates, activity flags,
  insider share, annual-report lag.
- **Snapshot date:** 21 November 2026. Requests used a descriptive User-Agent at 5 concurrent
  connections, within EDGAR's 10-requests-per-second limit.

## 🔄 Update frequency

**Daily upstream.** EDGAR accepts filings every business day; re-run `scripts/30_sec_companies.py` for a fresh snapshot.

## ⚠️ Caveats

- EDGAR's `filings.recent` table holds only the most recent ~1,000 filings, so counts are recent activity, not lifetime totals.
- The ticker file covers companies with listed securities; private registrants without tickers are absent.
- `stateOfIncorporation` uses SEC codes; `is_foreign_incorporated` is a heuristic on those codes.
- Descriptions and addresses are self-reported and go stale after mergers or delistings.
- Some CIKs return no submissions JSON (funds with separate series, recent registrants) and were skipped.
- Phone, website and EIN are corporate contact data, not personal data.
- The 12,000-company cap means the file is a large sample of EDGAR, not its entire registry.

## 📜 Licence

Public domain — U.S. Securities and Exchange Commission. EDGAR data is a U.S. Government work and may be reused freely.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `cik` | `number` | SEC Central Index Key. |
| 2 | `name` | `string` | Company name as registered with the SEC. |
| 3 | `tickers` | `string` | Ticker symbols (semicolon-joined). |
| 4 | `ticker_count` | `number` | Number of listed tickers. |
| 5 | `primary_ticker` | `string` | First listed ticker. |
| 6 | `exchanges` | `string` | Exchanges the tickers trade on. |
| 7 | `exchange_count` | `number` | Number of exchanges. |
| 8 | `entity_type` | `string` | SEC entity type (operating company, investment fund, ...). |
| 9 | `category` | `string` | Filer category (Large accelerated filer, Smaller reporting company, ...). |
| 10 | `sic_code` | `number` | Standard Industrial Classification code. |
| 11 | `sic_description` | `string` | SIC industry description. |
| 12 | `sic_division` | `string` | SIC division name derived from the code range. |
| 13 | `owner_org` | `string` | SEC office that handles the filer. |
| 14 | `fiscal_year_end` | `number` | Fiscal year end as MMDD. |
| 15 | `fiscal_year_end_month` | `number` | Fiscal year end month (1-12). |
| 16 | `state_of_incorporation` | `string` | State or country of incorporation code. |
| 17 | `state_of_incorporation_name` | `string` | Full name of the incorporation jurisdiction. |
| 18 | `is_foreign_incorporated` | `boolean` | true when the incorporation code indicates a non-US jurisdiction. |
| 19 | `ein` | `number` | Employer Identification Number. |
| 20 | `lei` | `string` | Legal Entity Identifier, when registered. |
| 21 | `has_lei` | `boolean` | true when a LEI is present. |
| 22 | `description` | `number` | Company self-description (truncated to 600 characters). |
| 23 | `website` | `number` | Company website. |
| 24 | `investor_website` | `number` | Investor-relations website. |
| 25 | `phone` | `string` | Business phone. |
| 26 | `business_street` | `string` | Business address street. |
| 27 | `business_city` | `string` | Business address city. |
| 28 | `business_state` | `string` | Business address state/country code. |
| 29 | `business_zip` | `string` | Business address ZIP code. |
| 30 | `mailing_city` | `string` | Mailing address city. |
| 31 | `mailing_state` | `string` | Mailing address state/country code. |
| 32 | `former_name_count` | `number` | Number of previous names. |
| 33 | `latest_former_name` | `string` | Most recent previous name. |
| 34 | `latest_filing_date` | `date` | Date of the most recent EDGAR filing. |
| 35 | `latest_10k_date` | `date` | Date of the most recent annual report (10-K). |
| 36 | `latest_10q_date` | `date` | Date of the most recent quarterly report (10-Q). |
| 37 | `filing_count_recent` | `number` | Number of filings in EDGAR's recent-filings table. |
| 38 | `filings_10k` | `number` | 10-K annual reports in the recent table. |
| 39 | `filings_10q` | `number` | 10-Q quarterly reports in the recent table. |
| 40 | `filings_8k` | `number` | 8-K current reports in the recent table. |
| 41 | `filings_form4` | `number` | Form 4 insider-transaction filings. |
| 42 | `filings_def14a` | `number` | DEF 14A proxy statements. |
| 43 | `filings_s1` | `number` | S-1 registration statements. |
| 44 | `filings_20f` | `number` | 20-F annual reports for foreign private issuers. |
| 45 | `filings_6k` | `number` | 6-K foreign issuer reports. |
| 46 | `filings_13f` | `number` | 13F institutional holdings reports. |
| 47 | `filings_sc13g` | `number` | SC 13G beneficial-ownership filings. |
| 48 | `insider_transactions_issuer` | `number` | true when insider transactions exist for the issuer. |
| 49 | `insider_transactions_owner` | `number` | true when insider transactions exist for the owner. |
| 50 | `has_recent_filings` | `boolean` | true when the recent-filings table is non-empty. |
| 51 | `first_recent_filing` | `date` | Oldest filing date in the recent table. |
| 52 | `latest_accession` | `string` | Accession number of the latest filing. |
| 53 | `latest_primary_document` | `string` | Primary document filename of the latest filing. |
| 54 | `filing_span_days` | `number` | Days between the oldest and newest filing in the recent table. |
| 55 | `is_operating_company` | `boolean` | true when the entity type is a standard operating company. |
| 56 | `is_investment_fund` | `boolean` | true for funds and trusts. |
| 57 | `is_large_accelerated` | `boolean` | true for large accelerated filers. |
| 58 | `is_smaller_reporting` | `boolean` | true for smaller reporting companies. |
| 59 | `is_foreign_issuer` | `boolean` | true when the filer files 20-F or 6-K reports. |
| 60 | `files_quarterly` | `boolean` | true when the company files 10-Q reports. |
| 61 | `has_proxy` | `boolean` | true when a DEF 14A proxy statement is present. |
| 62 | `days_since_latest_filing` | `number` | Days between the latest filing and the snapshot date. |
| 63 | `is_active_filer` | `boolean` | true when the latest filing is within 400 days of the snapshot. |
| 64 | `filings_per_year` | `number` | Recent filings divided by the span of the recent table, annualised. |
| 65 | `insider_filing_share` | `number` | Share of recent filings that are Form 4 insider reports. |
| 66 | `annual_report_lag_days` | `number` | Days between the latest 10-K and the latest filing. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
