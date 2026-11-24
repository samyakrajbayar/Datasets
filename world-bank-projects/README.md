---
annotations_creators:
- no-annotation
language:
- en
license: cc-by-4.0
multilinguality:
- monolingual
size_categories:
- 10K<n<100K
source_datasets:
- original
task_categories:
- tabular-classification
task_ids: []
pretty_name: "World Bank Project Portfolio"
tags:
- tabular
- economics
- finance
---

# World Bank Project Portfolio

**Subtitle:** 22,575 development projects with commitments, sectors, regions, dates and status.

---

## 📖 Description

### 22,575 World Bank investment projects

The World Bank's projects API documents every investment project it has financed, with approvals,
commitments, sectors and status. This dataset contains **22,575 projects** and **81 parameters**.

- **Identity** — project id, name, country, region, product line and lending instrument.
- **Finance** — total commitment, IBRD/IDA split, grants, disbursements, repayments and fees.
- **Timing** — board approval, closing and last-status dates plus approval fiscal year.
- **Classification** — sector, theme, financial type, status, team lead and quality ratings.
- **Derived** — approval/closing years, duration, age, active/closed/dropped flags, IDA/IBRD/grant
  flags, commitment bands, grant share, disbursement ratio, abstract length and region flags.

The portfolio represents **$0.0 billion** in commitments across **209 countries
and territories**, with **2,659 active projects** — a direct view of development finance.

## 🧾 Columns (81)

`id`, `projectid`, `project_name`, `countryname`, `countrycode`, `countryshortname`, `regionname`, `region_code`, `prodline`, `prodlinetext`, `lendinginstr`, `lendinginstrtype`, `projectfinancialtype`, `projectstatusdisplay`, `status`, `statusdate`, `boardapprovaldate`, `closingdate`, `laststatusdate`, `approvalfy`, `fiscalyear`, `lendprojectcost`, `totalamt`, `totalcommamt`, `grant_usd_amt`, `ibrdcommamt`, `idacommamt`, `curr_total_commitment`, `curr_ibrd_commitment`, `curr_ida_commitment`, `curr_project_cost`, `disbursement`, `commitment`, `repayment`, `interestandcharges`, `fees`, `loanid`, `loantype`, `loantypedesc`, `financierdesc`, `financiertype`, `sector1`, `theme1`, `mjthemecode`, `mjtheme_namecode`, `mttheme1name`, `project_abstract`, `project_gp_info`, `teamleadname`, `teamleademail`, `locations`, `url`, `listing_relative_url`, `source`, `p2a_flag`, `overall_currentrating`, `performance_currentrating`, `mequality`, `environment_riskdo`, `completion_riskdo`, `proj_last_upd_date`, `approval_year`, `approval_month`, `closing_year`, `duration_days`, `age_years`, `is_active`, `is_closed`, `is_dropped`, `is_ida`, `is_ibrd`, `has_grant`, `has_abstract`, `totalamt_band`, `grant_share`, `disbursement_ratio`, `abstract_length`, `is_africa`, `is_asia`, `is_latin_america`, `is_europe_central_asia`

## 💡 Ideas for using this data

1. **Portfolio** — commitments by region, country and decade.
2. **Instruments** — IDA vs IBRD vs grants by sector.
3. **Disbursement** — which projects lag their commitments.
4. **Project size** — amount distributions and mega-projects.
5. **Sectors** — education vs health vs infrastructure over time.
6. **Duration** — approval-to-closing timelines.
7. **Text** — abstracts for topic modelling.
8. **Performance** — quality ratings vs project characteristics.

## 📁 Files

| File | What it is |
|---|---|
| `world_bank_projects.csv` | 22,575 projects x 81 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`world-bank`, `development`, `finance`, `projects`, `economics`, `international`

## 🔗 Provenance

- **Source:** **World Bank Projects API**
  (`https://search.worldbank.org/api/v2/projects`), all projects with all fields.
- **Sampling:** full portfolio paged 500 projects at a time.
- **Processing:** 60 fields retained; dates parsed, financial ratios and region/status flags derived.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Continuous upstream; snapshot here.** The portfolio is updated as projects change.

## ⚠️ Caveats

- Commitment amounts are USD equivalents at approval and are not inflation-adjusted.
- Many projects have missing closing dates or quality ratings.
- Country names can cover multi-country operations.
- The API includes projects from the 1940s onward with uneven field coverage.
- Disbursement figures are as of the last update, not final.

## 📜 Licence

World Bank Open Data, CC BY 4.0 — attribution required.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
