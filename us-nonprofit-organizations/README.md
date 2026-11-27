---
annotations_creators:
- no-annotation
language:
- en
license: cc0-1.0
multilinguality:
- monolingual
size_categories:
- 10K<n<1M
source_datasets:
- original
task_categories:
- tabular-classification
task_ids: []
pretty_name: "US Nonprofit Organisations IRS BMF"
tags:
- tabular
- economics
---

# US Nonprofit Organisations IRS BMF


## ⭐ Upvote & Support
If you find this dataset useful for your research, machine learning projects, or data visualization, please consider giving it an **Upvote**! Your support helps make open data more accessible to the community.


# US Nonprofit Organisations — IRS Business Master File

**Subtitle:** 1,661,259 tax-exempt 501(c)(3) charities with assets, revenue, NTEE sector, ruling dates and addresses.

---

## 📖 Description

### 1,661,259 US 501(c)(3) nonprofit organisations

The IRS Exempt Organizations Business Master File is the official register of every organisation
recognised as tax-exempt in the United States. This dataset keeps the **1,661,259 public charities
(501(c)(3))** — churches, schools, hospitals, foundations, clubs and community groups — with
**53 parameters** per organisation.

- **Identity** — EIN, name, sort name, in-care-of, street, city, state, ZIP, foreign flag.
- **Exemption** — subsection, affiliation, classification, foundation code, deductibility,
  status, ruling date and ruling age in years.
- **Money** — assets, income, revenue in dollars plus the IRS bracket codes and bands, and
  revenue/income per asset.
- **Classification** — 26 NTEE categories derived from the NTEE code, legal form, activity code,
  group exemption number and filing requirement codes.
- **Geography** — state name, Census region and five-digit ZIP.

About **447,583 charities** report revenue figures; the remainder are
mostly churches and small organisations that are not required to file Form 990. The largest
NTEE categories are religion (206,845), education (185,660), human services (156,177), arts and culture (119,364), philanthropy (105,308).

## 🧾 Columns (53)

`ein`, `name`, `sort_name`, `ico`, `street`, `city`, `state`, `state_name`, `state_region`, `zip`, `zip5`, `group_exemption_number`, `subsection_code`, `subsection_desc`, `affiliation_code`, `affiliation_desc`, `classification_code`, `ruling_date`, `ruling_year`, `ruling_month`, `ruling_age_years`, `deductibility_code`, `foundation_code`, `foundation_desc`, `activity_code`, `organization_code`, `organization_desc`, `status_code`, `status_desc`, `tax_period`, `accounting_period`, `asset_code`, `asset_band`, `income_code`, `income_band`, `filing_requirement_code`, `pf_filing_requirement_code`, `asset_amount`, `income_amount`, `revenue_amount`, `revenue_per_asset`, `income_per_asset`, `ntee_code`, `ntee_category_letter`, `ntee_category`, `ntee_subcategory`, `is_foreign`, `source_file`, `has_asset_amount`, `has_income_amount`, `has_revenue`, `has_ntee`, `has_group_exemption`

## 💡 Ideas for using this data

1. **Sector map** — which NTEE categories dominate each state.
2. **Size distribution** — assets and revenue bands by category.
3. **Age** — ruling year vs survival and revenue growth.
4. **Churches vs charities** — reporting behaviour of religious organisations.
5. **Geography** — nonprofits per capita by ZIP or state.
6. **Foundations** — private foundations vs public charities.
7. **Group exemptions** — organisations filing under a central ruling.
8. **Text** — name and NTEE classification of millions of organisations.

## 📁 Files

| File | What it is |
|---|---|
| `us_nonprofits.csv` | 1,661,259 organisations x 53 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`nonprofits`, `charity`, `irs`, `united-states`, `finance`, `public-data`, `economics`

## 🔗 Provenance

- **Source:** **IRS Exempt Organizations Business Master File (BMF)**, regional CSV extracts
  `eo1.csv`-`eo4.csv` and `eo_xx.csv` from `irs.gov/pub/irs-soi/`.
- **Processing:** all five regional files read; records filtered to subsection `03` (501(c)(3));
  28 source columns mapped, code tables decoded, money fields parsed, NTEE and geography derived.
- **Snapshot date:** 27 November 2026.

## 🔄 Update frequency

**Monthly.** The IRS republishes the Business Master File each month.

## ⚠️ Caveats

- Only 501(c)(3) organisations are included; other subsections were filtered out.
- Asset, income and revenue amounts are 0 or blank for churches and small filers that do not file Form 990.
- Addresses are the IRS mailing address, which is often an accountant or attorney, not the programme site.
- Bracket codes (asset_code, income_code) come from the IRS and are coarser than the dollar amounts.
- The BMF is a registration file: it does not record whether an organisation is still active in its mission.
- Some organisations appear under a group exemption with the central organisation's EIN block.

## 📜 Licence

IRS Exempt Organizations Business Master File — US government work, public domain.

