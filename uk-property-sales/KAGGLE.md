# UK Property Sales 2025–2026

**Subtitle:** 1,450,241 residential property transactions with prices, addresses, postcodes and property attributes.

---

## 📖 Description

### 1,450,241 residential property sales in England and Wales

HM Land Registry's Price Paid Data records every residential property sale that reaches completion
in England and Wales. This dataset streams the **2025, 2026 files** and derives
**33 parameters** per transaction.

- **Transaction** — id, price, completion date and record status.
- **Property** — type, new-build flag, tenure, full address decomposition (PAON, SAON, street,
  locality, town, city, district, county) and postcode hierarchy.
- **Ownership** — standard vs additional-property category and freehold/leasehold tenure.
- **Derived** — year, month, quarter, price bands, postcode area/district/sector, new-build,
  freehold and additional-ownership flags, address length and price per address character.

The file contains roughly **2.4% new-build sales** and spans
**260+ towns** in the sample alone. It is the standard source for UK house-price, affordability
and property-market research.

## 🧾 Columns (33)

`transaction_id`, `price`, `date_of_transfer`, `postcode`, `property_type_code`, `property_type`, `new_build`, `tenure`, `paon`, `saon`, `street`, `locality`, `town`, `city`, `district`, `county`, `ppd_category`, `record_status`, `transfer_year`, `transfer_month`, `transfer_quarter`, `transfer_weekday`, `price_band`, `postcode_area`, `postcode_district`, `postcode_sector`, `is_new_build`, `is_freehold`, `is_additional_ownership`, `has_saon`, `has_postcode`, `address_length`, `price_per_letter`

## 💡 Ideas for using this data

1. **House prices** — median price by postcode district and property type.
2. **Time series** — monthly price and volume trends.
3. **New build premium** — new-build prices vs equivalent stock.
4. **Tenure** — leasehold vs freehold price gaps.
5. **Regional inequality** — price distributions across counties.
6. **Additional properties** — buy-to-let and second-home share.
7. **Address parsing** — text features from PAON/SAON/street.
8. **Maps** — postcode-level price choropleths.
9. **Volume** — transaction counts as a market-activity indicator.

## 📁 Files

| File | What it is |
|---|---|
| `uk_property_sales.csv` | 1,450,241 transactions x 33 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`real-estate`, `housing`, `uk`, `property-prices`, `land-registry`, `economics`

## 🔗 Provenance

- **Source:** **HM Land Registry Price Paid Data** annual CSVs
  (`pp-2025.csv`, `pp-2026.csv`), published as open data.
- **Processing:** both files streamed row by row; postcode hierarchy, date parts and property flags
  derived; the raw files are not stored in the repository.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Monthly.** HM Land Registry publishes a new Price Paid file each month.

## ⚠️ Caveats

- Covers England and Wales only; Scotland and Northern Ireland have separate registers.
- Prices are as reported at completion and are not adjusted for inflation or property size.
- Category B rows are additional-ownership transactions and should be separated in analysis.
- Address fields are free text and are not geocoded.
- Delete/change records are included where the register supplies them.
- Postcode sector is approximated by dropping the final letter of the postcode.

## 📜 Licence

Contains HM Land Registry data © Crown copyright, licensed under the Open Government Licence v3.0.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
