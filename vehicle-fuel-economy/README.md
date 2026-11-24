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
pretty_name: "U.S. Vehicle Fuel Economy & Emissions"
tags:
- tabular
- energy
- automotive
---

# U.S. Vehicle Fuel Economy & Emissions

**Subtitle:** 50,744 vehicle configurations with MPG, CO2, fuel costs, powertrains and technology flags.

---

## 📖 Description

### 50,744 U.S. vehicle configurations with fuel economy and emissions

The DOE/EPA Fuel Economy dataset lists every vehicle configuration sold in the United States, with
tested MPG, fuel costs, CO2 emissions and technology descriptors. This dataset contains **50,744
configurations** and **82 parameters**.

- **Vehicle** — id, make, model, base model, model year and EPA class.
- **Powertrain** — engine displacement, cylinders, transmission, drivetrain, fuel types and
  alternative-technology type.
- **Economy** — city, highway and combined MPG on both test cycles, unadjusted values and scores.
- **Emissions and cost** — tailpipe CO2, greenhouse-gas score, annual fuel cost, petroleum use and
  five-year savings.
- **Derived** — electric/hybrid/plug-in/flex/diesel flags, drivetrain flags, manual flag, gears,
  gallons per year, cost per mile, MPG/cost/CO2/range bands, vehicle age, turbo/supercharger and
  start-stop flags.

**1,693 configurations are battery-electric** and **2,427 are hybrids**, spread across
**146 manufacturers** and five decades of model years — the standard table for fleet, emissions
and consumer-economics analysis.

## 🧾 Columns (82)

`id`, `make`, `model`, `baseModel`, `year`, `VClass`, `drive`, `trany`, `trans_dscr`, `displ`, `cylinders`, `fuelType`, `fuelType1`, `fuelType2`, `atvType`, `evMotor`, `city08`, `highway08`, `comb08`, `cityA08`, `highwayA08`, `combA08`, `cityE`, `highwayE`, `combE`, `co2`, `co2A`, `co2TailpipeGpm`, `fuelCost08`, `fuelCostA08`, `ghgScore`, `ghgScoreA`, `feScore`, `youSaveSpend`, `range`, `rangeCity`, `rangeHwy`, `rangeA`, `phevCity`, `phevHwy`, `phevComb`, `barrels08`, `barrelsA08`, `UCity`, `UHighway`, `sCharger`, `tCharger`, `startStop`, `guzzler`, `mpgData`, `phevBlended`, `charge120`, `charge240`, `mfrCode`, `eng_dscr`, `createdOn`, `modifiedOn`, `is_electric`, `is_hybrid`, `is_plugin_hybrid`, `is_flex_fuel`, `is_diesel`, `is_manual`, `is_awd`, `is_4wd`, `is_fwd`, `is_rwd`, `gears`, `displacement_l`, `annual_gallons`, `cost_per_mile`, `co2_per_mile_g`, `mpg_band`, `cost_band`, `co2_band`, `range_band`, `vehicle_age`, `is_turbo`, `is_supercharged`, `is_start_stop`, `is_guzzler`, `is_model_year_2026`

## 💡 Ideas for using this data

1. **Efficiency trends** — MPG by model year and class.
2. **Electrification** — EV and hybrid share over time.
3. **Emissions** — CO2 vs MPG and vehicle class.
4. **Cost of ownership** — annual fuel cost distributions.
5. **Drivetrain** — AWD vs FWD efficiency penalties.
6. **Engine downsizing** — displacement and turbocharging trends.
7. **Class comparison** — pickups vs sedans vs SUVs.
8. **Prediction** — model combined MPG from vehicle attributes.
9. **Range** — EV range distributions.

## 📁 Files

| File | What it is |
|---|---|
| `fuel_economy.csv` | 50,744 configurations x 82 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`fuel-economy`, `vehicles`, `emissions`, `epa`, `energy`, `automotive`

## 🔗 Provenance

- **Source:** **fueleconomy.gov** vehicles dataset
  (`https://www.fueleconomy.gov/feg/epadata/vehicles.csv.zip`), published by the U.S. Department of
  Energy and EPA.
- **Processing:** zipped CSV parsed directly; numeric fields coerced; technology flags, bands and
  derived ratios added.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Annual.** A new model-year file is published each year, with updates during the year.

## ⚠️ Caveats

- MPG values are EPA test-cycle results, not real-world fuel economy.
- Many fields are blank for older model years and alternative-fuel vehicles.
- The file mixes current and historical model years.
- Annual fuel cost assumes 15,000 miles and reference fuel prices.
- Transmission gear counts are parsed from free text and may be missing.

## 📜 Licence

U.S. Government work (DOE/EPA), public domain.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
