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
pretty_name: "Active U.S. Weather Alerts - Live NWS Snapshot"
tags:
- tabular
- geography
---

# Active U.S. Weather Alerts — Live NWS Snapshot

**Subtitle:** 678 active watches, warnings and advisories with severity, timing, zones and hazard flags.

---

## 📖 Description

### 678 active weather alerts across the United States

The National Weather Service publishes every active watch, warning and advisory as CAP messages.
This dataset is a live snapshot of **678 alerts** expanded to **49 parameters**.

- **Alert identity** — CAP id, event, headline, category, status and message type.
- **Geography** — affected-area description, UGC zone codes and SAME geocodes with counts.
- **Hazard** — severity, urgency, certainty, response type and scope.
- **Timing** — sent, effective, onset, expiry and end timestamps plus duration, lead time and age.
- **Derived** — numeric severity/urgency/certainty ranks, a combined risk score, warning/watch/
  advisory and hazard-type flags, text lengths and instruction presence.

**175 of the alerts are warnings**, and the snapshot spans **308 state-level area
prefixes**. The data supports hazard monitoring, alert-fatigue studies and text classification.

## 🧾 Columns (49)

`alert_id`, `event`, `headline`, `area_desc`, `zone_count`, `same_count`, `status`, `message_type`, `category`, `severity`, `certainty`, `urgency`, `response`, `scope`, `sender_name`, `language`, `sent`, `effective`, `onset`, `expires`, `ends`, `duration_hours`, `lead_time_hours`, `age_hours`, `severity_rank`, `urgency_rank`, `certainty_rank`, `risk_score`, `is_warning`, `is_watch`, `is_advisory`, `is_statement`, `is_fire`, `is_flood`, `is_winter`, `is_heat`, `is_wind`, `is_severe_storm`, `is_marine`, `has_instruction`, `description_length`, `instruction_length`, `zone_list`, `parameter_keys`, `nws_headline_words`, `description_words`, `event_length`, `is_extreme`, `is_immediate`

## 💡 Ideas for using this data

1. **Hazard mix** — alert types by region and season.
2. **Alert fatigue** — how often the same zone is warned.
3. **Lead time** — warning lead times by hazard type.
4. **Text classification** — headline/description topic modelling.
5. **Risk scoring** — rank alerts by severity, urgency and certainty.
6. **Geographic hot spots** — zones with the most simultaneous alerts.
7. **Duration** — expected vs actual alert lifetimes.
8. **Instruction quality** — which alerts include protective actions.

## 📁 Files

| File | What it is |
|---|---|
| `weather_alerts.csv` | 678 alerts x 49 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`weather`, `alerts`, `nws`, `hazards`, `united-states`, `live-data`

## 🔗 Provenance

- **Source:** **National Weather Service API** (`https://api.weather.gov/alerts/active`),
  CAP/GeoJSON.
- **Processing:** one live snapshot of all active alerts; geocodes, parameters and timestamps
  expanded; ranks, durations and hazard flags derived.
- **Snapshot date:** 24 November 2026 (UTC).

## 🔄 Update frequency

**Real time.** The NWS alerts feed changes continuously.

## ⚠️ Caveats

- A single snapshot: alerts appear and expire within hours.
- Zone codes require the NWS zone shapefiles to be mapped.
- Severity and urgency are as assigned by the issuing office and vary in consistency.
- Some alerts cover large multi-state areas and are counted once.
- The API is rate-limited and occasionally returns partial results.

## 📜 Licence

U.S. Government work (National Weather Service), public domain.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
