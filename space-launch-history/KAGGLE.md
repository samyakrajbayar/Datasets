# Dawn of the Space Age — 1,200 Orbital Launch Attempts, 1957–1970

**Subtitle:** Every orbital launch attempt of the first space-race era, with 53 parameters on rockets, pads, orbits, providers, payloads and mission outcomes.

---

## 📖 Description

Between Sputnik in October 1957 and the end of 1970, humanity went from "no object in orbit" to landing people on the Moon. This dataset captures that sprint as structured data: **1,200 orbital launch attempts** from the Launch Library 2 catalogue, each described by **53 parameters**.

Each row is one launch attempt and includes:

- **Timing** — NET (No Earlier Than) timestamp in UTC, window start and end, precision of the scheduled time, plus derived year, month, day, hour, weekday and quarter.
- **Outcome** — status code and name (Success, Failure, Partial Failure…), failure reason text, and pre-launch probability / weather concerns where reported.
- **Vehicle** — rocket configuration name, family and variant (e.g. Vostok-K, Atlas-Agena B, R-7 Semyorka), full configuration name.
- **Mission** — mission name, type (Communications, Earth Science, Test Flight, Human Spaceflight…), truncated description, target orbit abbreviation and name, crew count, payload count and payload categories.
- **Infrastructure** — launch pad name and coordinates, launch site name and country code.
- **Provider** — launch service provider name, abbreviation, country and type (Government / Commercial / Multinational).
- **Historical counters** — global orbital launch attempt number at that moment, cumulative attempts for the site, pad and agency, attempts within that year, and pad turnaround in days.
- **Media & links** — webcast flag, counts of reference/video links and mission patches, programme names, hashtag, image URL and the API record URL.

Because the historical counters are cumulative, you can reconstruct each agency's and each pad's learning curve directly from the file.

## 🧾 Columns (53)

`launch_id`, `launch_name`, `launch_designator`, `status_abbrev`, `status_name`, `net_utc`, `window_start_utc`, `window_end_utc`, `net_precision`, `year`, `month`, `day`, `hour`, `weekday`, `quarter`, `probability_pct`, `weather_concerns`, `fail_reason`, `provider`, `provider_abbrev`, `provider_country`, `provider_type`, `rocket_name`, `rocket_family`, `rocket_variant`, `rocket_full_name`, `mission_name`, `mission_type`, `mission_description`, `orbit_abbrev`, `orbit_name`, `pad_name`, `pad_latitude`, `pad_longitude`, `location_name`, `location_country_code`, `n_crew`, `n_payloads`, `payload_types`, `orbital_launch_attempt_count`, `location_launch_attempt_count`, `pad_launch_attempt_count`, `agency_launch_attempt_count`, `orbital_launch_attempt_count_year`, `pad_turnaround_days`, `has_webcast`, `n_info_urls`, `n_vid_urls`, `n_mission_patches`, `programs`, `hashtag`, `image_url`, `info_url`

## 💡 Ideas for using this data

1. **Reliability over time** — failure rate by provider, rocket family and year across the space race.
2. **Learning curves** — use `agency_launch_attempt_count` and `pad_launch_attempt_count` to model how quickly organisations improved.
3. **Launch cadence** — monthly launch counts by country; spot the 1957–58 Sputnik surge and the 1969–70 Apollo build-up.
4. **Pad utilisation** — turnaround days per pad, and which pads were the busiest bottlenecks.
5. **Payload and orbit mix** — how the balance shifted from test flights to communications and reconnaissance.
6. **Classification** — predict launch success from rocket family, provider, orbit and pad features.
7. **Geospatial** — map launch sites by latitude/longitude and relate site choice to target orbit inclination.

## ⚠️ Caveats

- Coverage is the **first 1,200 records** of the Launch Library 2 catalogue ordered by date, i.e. the 1957–1970 era — not the full history of spaceflight.
- Some early launches have incomplete metadata (missing orbit, payload details, or exact times), reflecting sparse historical records.
- `probability_pct` and `weather_concerns` are essentially empty for this era.
- `pad_turnaround_days` is computed from the API's turnaround value and is missing for pads with no previous launch on record.
- "Success" reflects the catalogue's assessment of the launch (reaching orbit), not mission-level scientific success.

## 🔗 Provenance & licence

- Source: The Space Devs **Launch Library 2** API (`ll.thespacedevs.com`, v2.3.0), community-maintained and free for non-commercial use with attribution.
- Snapshot: November 2026. 1,200 rows × 53 columns.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
