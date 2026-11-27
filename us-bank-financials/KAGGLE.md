# US Bank Financial Statements — FDIC Institutions

**Subtitle:** 4,204 FDIC-insured banks with balance sheets, income, capital ratios and branch geography.

---

## 📖 Description

### 4,204 FDIC-insured US banks with full financial statements

The FDIC publishes a quarterly directory and call-report financials for every bank it insures.
This dataset joins the two: **4,204 active institutions**, **103 parameters**,
and one row per bank with the report quarter in `report_period`.

- **Institution** — certificate number, name, address, city, state, county, ZIP, latitude and
  longitude, CBSA, FDIC region, chartering agent, bank class and establishment date.
- **Balance sheet** — assets, deposits (domestic, insured, uninsured), liabilities, equity, loans,
  securities, intangibles, cash, premises and 12 loan categories.
- **Income** — net income, interest and noninterest income and expense, taxes, loan-loss provision.
- **Ratios** — loans to deposits, equity to assets, net interest margin, efficiency ratio,
  noncurrent assets, ROA, ROE, charge-off rate, Tier 1 leverage and risk-based capital.
- **Derived** — assets in billions, uninsured deposit share, assets and income per employee,
  community-bank and large-bank flags.

The banks in this snapshot hold **$0.03 trillion in assets** and
**$0.02 trillion in deposits**; **4,204** are FDIC-insured and
**161** have assets of USD 10 billion or more.

## 🧾 Columns (103)

`fdic_cert`, `name`, `address`, `address2`, `city`, `state`, `state_name`, `county`, `zip`, `latitude`, `longitude`, `cbsa_name`, `cbsa_code`, `csa_name`, `state_county_fips`, `bank_class`, `chartering_agent`, `charter_type`, `fed_district`, `fdic_region`, `fdic_region_name`, `insurance_date`, `established_date`, `effective_date`, `report_date`, `website`, `fed_rssd_id`, `minority_depository_status`, `cfpb_supervised`, `mutual_ownership`, `subchapter_s_c`, `trust_powers`, `industrial_bank`, `oakar_holder`, `savings_association_insurance`, `bif_insured`, `dif_insured`, `fdic_insured`, `conservatorship`, `active`, `bank_class_desc`, `institution_age_years`, `report_period`, `total_assets_usd`, `total_deposits_usd`, `domestic_deposits_usd`, `insured_deposits_usd`, `uninsured_deposits_usd`, `total_liabilities_usd`, `total_equity_usd`, `net_loans_usd`, `securities_usd`, `intangibles_usd`, `net_income_usd`, `interest_income_usd`, `interest_expense_usd`, `noninterest_income_usd`, `noninterest_expense_usd`, `income_tax_usd`, `provision_for_loan_losses_usd`, `employees`, `domestic_offices`, `foreign_offices`, `loans_to_deposits_pct`, `equity_to_assets_pct`, `net_interest_margin_pct`, `efficiency_ratio_pct`, `noncurrent_assets_pct`, `return_on_assets_pct`, `return_on_equity_pct`, `net_chargeoffs_to_loans_pct`, `loan_loss_reserve_to_loans_pct`, `tier1_leverage_ratio_pct`, `tier1_risk_based_ratio_pct`, `total_risk_based_ratio_pct`, `core_deposits_usd`, `trading_assets_usd`, `available_for_sale_securities_usd`, `held_to_maturity_securities_usd`, `construction_loans_usd`, `multifamily_loans_usd`, `residential_loans_usd`, `nonresidential_loans_usd`, `consumer_loans_usd`, `commercial_industrial_loans_usd`, `credit_card_loans_usd`, `agricultural_loans_usd`, `transaction_accounts_usd`, `time_deposits_usd`, `bank_premises_usd`, `specialization`, `investment_offices`, `branches`, `net_income_bank_measure_usd`, `assets_billions`, `deposits_billions`, `loans_to_assets_pct`, `uninsured_deposit_share_pct`, `assets_per_employee_musd`, `income_per_employee_kusd`, `has_uninsured_deposits`, `is_community_bank`, `is_large_bank`

## 💡 Ideas for using this data

1. **Size distribution** — assets per bank on a log scale; the long tail of community banks.
2. **Profitability** — ROA and net interest margin vs bank size.
3. **Funding risk** — uninsured deposit share by asset size (2023-style runs).
4. **Loan mix** — commercial real estate concentration by state.
5. **Capital** — Tier 1 leverage vs risk-based capital.
6. **Geography** — banks per state and assets per capita.
7. **Efficiency** — efficiency ratio benchmarks by specialisation.
8. **Consolidation** — institution age vs size and branching.

## 📁 Files

| File | What it is |
|---|---|
| `us_banks.csv` | 4,204 banks x 103 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`banking`, `finance`, `fdic`, `united-states`, `economics`, `financial-statements`

## 🔗 Provenance

- **Source:** **FDIC BankFind Suite API** — `/banks/institutions` (active institutions) and
  `/banks/financials` (latest report date `20260930`).
- **Processing:** institution records joined to financials on FDIC certificate number; 40 institution
  fields and 51 report fields selected; dates parsed, ratios and size bands derived.
- **Snapshot date:** 27 November 2026.

## 🔄 Update frequency

**Quarterly.** The FDIC publishes a new call report each quarter.

## ⚠️ Caveats

- Only active, FDIC-insured institutions are included; thrift-only and credit-union data are not part of this file.
- Financial columns come from a single report quarter and are not annual totals.
- Some capital ratios are blank for institutions that do not report them.
- Assets are reported in thousands of US dollars at the source and converted to dollars here.
- Institution addresses are the main office, not every branch.
- Bank failures, mergers and name changes are only visible through the current directory.

## 📜 Licence

FDIC public data — US government work, public domain.
