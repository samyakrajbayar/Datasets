# NYC 311 Service Requests

**Subtitle:** 200,000 NYC 311 requests with agency, location and resolution details

**Tags:** `tabular`, `urban`, `civic`

**Dataset File:** `nyc_311_requests.csv` (200,000 rows, 52 columns, 152.8 MB)

**Provenance & Source:** NYC Open Data Portal (data.cityofnewyork.us)

**Expected Update Frequency:** `monthly`

---

## 📖 Description

### 200,000 New York City service requests

NYC 311 is the city's non-emergency request system: noise, heat, potholes, sanitation, water, trees and
more. This dataset takes the **200,000 most recent requests** and expands each into **52 parameters**.

- **Request identity** — unique key, created and closed timestamps, status, due date, channel.
- **Responsibility** — agency code and name, complaint type, descriptor, facility type.
- **Location** — incident address, street, cross streets, ZIP, borough, community board, council
  district, police precinct, park facility, latitude/longitude and State Plane coordinates.
- **Outcome** — resolution description and last resolution update.
- **Derived** — response hours and days, closed flags, 1-day and 7-day closure flags, year/month/
  weekday/hour, weekend flag, coarse complaint category, location flag, text lengths and topic flags.

**153,951 requests (77.0%) are closed**, **33,098 are noise complaints**, and
requests span **6 boroughs** — a ready-made civic-operations and response-time dataset.

## 🧾 Columns (52)

`unique_key`, `created_date`, `closed_date`, `agency`, `agency_name`, `complaint_type`, `descriptor`, `location_type`, `incident_zip`, `incident_address`, `street_name`, `cross_street_1`, `cross_street_2`, `intersection_street_1`, `intersection_street_2`, `address_type`, `city`, `landmark`, `facility_type`, `status`, `due_date`, `resolution_description`, `resolution_action_updated_date`, `community_board`, `council_district`, `police_precinct`, `borough`, `park_borough`, `open_data_channel_type`, `park_facility_name`, `latitude`, `longitude`, `x_coordinate`, `y_coordinate`, `response_hours`, `response_days`, `is_closed`, `is_open`, `closed_within_1_day`, `closed_within_7_days`, `year`, `month`, `day_of_week`, `hour`, `is_weekend`, `complaint_category`, `has_location`, `resolution_length`, `descriptor_length`, `is_noise`, `is_heat_hot_water`, `is_street_condition`

## 💡 Ideas for using this data

1. **Response-time equity** — median closure time by borough, ZIP and complaint type.
2. **Agency performance** — which agencies close fastest, and how much do they backload?
3. **Seasonality** — heat complaints in winter, noise in summer; plot a heatmap by month and hour.
4. **Channel shift** — phone vs online vs mobile over time.
5. **Geography** — hex-bin request density and compare with population or income.
6. **Backlog** — open requests by age and type; which categories stall?
7. **Resolution text NLP** — cluster resolution descriptions to find recurring outcomes.
8. **Classification** — predict the responsible agency from the complaint text.
9. **Equity audit** — response time vs neighbourhood demographics (external join required).

## 📁 Files

| File | What it is |
|---|---|
| `nyc_311_requests.csv` | 200,000 service requests x 52 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`nyc`, `311`, `civic`, `open-data`, `service-requests`, `urban`, `response-time`

## 🔗 Provenance

- **Source:** **NYC Open Data**, 311 Service Requests from 2010 to present,
  `https://data.cityofnewyork.us/resource/erm2-nwe9.json` (Socrata).
- **Scope:** the 200,000 most recent requests by `created_date`, five pages of 40,000.
- **Processing:** timestamps parsed, response times and calendar fields derived, complaint types mapped
  to a coarse category, topic flags added.
- **Snapshot date:** 22 November 2026.

## 🔄 Update frequency

**Daily.** New York City publishes 311 requests continuously.

## ⚠️ Caveats

- This is a recency sample, not a random or complete historical extract.
- Timestamps are local New York time; daylight-saving transitions are not normalised.
- Open requests have no closed_date and therefore no response time.
- Complaint types are free-text choices and change over the years.
- Coordinates are missing for a minority of requests (e.g. anonymous or address-only).
- Resolution descriptions are operator text and can be terse or boilerplate.
- The 200,000-row sample may not support fine-grained historical comparisons.

## 📜 Licence

NYC Open Data is licensed under the Open Data Commons Attribution License.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `unique_key` | `number` | Unique service-request identifier. |
| 2 | `created_date` | `datetime` | Request creation timestamp (local time). |
| 3 | `closed_date` | `datetime` | Request closure timestamp, where closed. |
| 4 | `agency` | `string` | Responsible agency code. |
| 5 | `agency_name` | `string` | Responsible agency name. |
| 6 | `complaint_type` | `string` | Complaint type as selected by the caller. |
| 7 | `descriptor` | `string` | Complaint sub-type / descriptor. |
| 8 | `location_type` | `string` | Location type (residential, commercial, ...). |
| 9 | `incident_zip` | `number` | ZIP code of the incident. |
| 10 | `incident_address` | `string` | Street address of the incident. |
| 11 | `street_name` | `string` | Street name. |
| 12 | `cross_street_1` | `string` | First cross street. |
| 13 | `cross_street_2` | `string` | Second cross street. |
| 14 | `intersection_street_1` | `string` | First intersection street. |
| 15 | `intersection_street_2` | `string` | Second intersection street. |
| 16 | `address_type` | `string` | Address type (address, blockface, intersection, ...). |
| 17 | `city` | `string` | City (usually New York). |
| 18 | `landmark` | `string` | Landmark name, if any. |
| 19 | `facility_type` | `string` | Facility type, if the request concerns a facility. |
| 20 | `status` | `string` | Request status (Open, In Progress, Closed, ...). |
| 21 | `due_date` | `datetime` | Agency due date. |
| 22 | `resolution_description` | `string` | Agency resolution text. |
| 23 | `resolution_action_updated_date` | `datetime` | Last resolution update. |
| 24 | `community_board` | `string` | Community board district. |
| 25 | `council_district` | `number` | City council district. |
| 26 | `police_precinct` | `string` | Police precinct. |
| 27 | `borough` | `string` | Borough of the incident. |
| 28 | `park_borough` | `string` | Parks department borough. |
| 29 | `open_data_channel_type` | `string` | How the request was submitted (phone, online, mobile, ...). |
| 30 | `park_facility_name` | `string` | Park or facility name. |
| 31 | `latitude` | `number` | Latitude (WGS84). |
| 32 | `longitude` | `number` | Longitude (WGS84). |
| 33 | `x_coordinate` | `number` | State plane X coordinate. |
| 34 | `y_coordinate` | `number` | State plane Y coordinate. |
| 35 | `response_hours` | `number` | Closed minus created, in hours. |
| 36 | `response_days` | `number` | response_hours / 24. |
| 37 | `is_closed` | `boolean` | true when a closed_date is present. |
| 38 | `is_open` | `boolean` | true when status is Open. |
| 39 | `closed_within_1_day` | `boolean` | true when closed within 24 hours. |
| 40 | `closed_within_7_days` | `boolean` | true when closed within 7 days. |
| 41 | `year` | `number` | Year the request was created. |
| 42 | `month` | `number` | Month number. |
| 43 | `day_of_week` | `string` | Weekday name. |
| 44 | `hour` | `number` | Hour of creation (0-23). |
| 45 | `is_weekend` | `boolean` | true for Saturday/Sunday. |
| 46 | `complaint_category` | `string` | Coarse category derived from complaint_type. |
| 47 | `has_location` | `boolean` | true when latitude and longitude are present. |
| 48 | `resolution_length` | `number` | Characters in the resolution description. |
| 49 | `descriptor_length` | `number` | Characters in the descriptor. |
| 50 | `is_noise` | `boolean` | true for noise complaints. |
| 51 | `is_heat_hot_water` | `boolean` | true for heat/hot-water complaints. |
| 52 | `is_street_condition` | `boolean` | true for street-condition complaints. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, machine learning projects, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
