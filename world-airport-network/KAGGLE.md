# World Airport Network

**Subtitle:** 7,698 airports with IATA/ICAO codes, coordinates and route graph statistics

**Tags:** `aviation`, `transportation`, `geospatial`, `networks`, `airports`, `travel`, `logistics`, `graph-analysis`, `tabular`, `economics`

**Dataset File:** `airports.csv` (7,698 rows, 43 columns, 1.9 MB)

---

## 📖 Description

### The world's airports as a graph

OpenFlights maintains one of the most widely used open aviation registries. This dataset joins its
**airport directory** with its **airline route table** to describe **7,698 airports** in
237 countries using **43 parameters** — including the network structure
that only appears once routes are aggregated.

Each row is one airport and contains:
- **Identity** — OpenFlights id, name, city, country, IATA and ICAO codes, facility type and data source.
- **Position** — latitude, longitude, elevation in feet, UTC offset, DST rule and IANA time zone.
- **Network degree** — departing and arriving route records, distinct airlines, distinct non-stop
  destinations, foreign destinations, countries served, domestic versus international route counts and
  the international share.
- **Dominant carrier** — the airline with the most routes at that airport and how many it runs.
- **Reach** — mean and maximum great-circle route distance, and the airport code of the longest hop.
- **Role** — a hub class derived from route count, from Isolated to Global hub.
- **Country context** — continent, UN region and sub-region, population, GDP per capita, distance to the
  national capital, a near-capital flag, the number of airports in the country and routes per million people.

**7,698 of 7,698 records are scheduled-service airports**; about **3,262** have at least
one route in the airlines table, which makes the difference between "an airport exists" and "an airport is
connected" directly measurable.

## 🧾 Columns (43)

`airport_id`, `name`, `city`, `country`, `iata`, `icao`, `latitude`, `longitude`, `altitude_ft`, `tz_offset_hours`, `dst`, `tz_database`, `type`, `source`, `continent`, `region`, `subregion`, `hemisphere`, `altitude_band`, `has_iata`, `is_scheduled_service`, `utc_offset_band`, `n_routes_out`, `n_routes_in`, `n_airlines`, `n_destinations`, `n_destinations_international`, `n_countries_served`, `n_domestic_routes`, `share_international_pct`, `top_airline`, `top_airline_routes`, `mean_route_distance_km`, `max_route_distance_km`, `farthest_destination`, `hub_class`, `capital_distance_km`, `is_near_capital`, `routes_per_million_people`, `country_population`, `country_gdp_per_capita_usd`, `airports_in_country`, `name_word_count`

## 💡 Ideas for using this data

1. **Airport ranking** — build a hub index from degree, destination count and international share.
2. **Network analysis** — the route table implies a directed graph; compute centrality, communities and degree distributions from the per-airport aggregates.
3. **Hub-and-spoke structure** — plot `n_destinations` against `n_airlines` to separate fortress hubs from diversified ones.
4. **Long-haul geography** — map `max_route_distance_km`; which airports exist only because of ultra-long-haul aircraft?
5. **Isolation** — find countries where many airports exist but almost none are connected.
6. **Capital concentration** — `capital_distance_km` versus route count; how much traffic funnels through capital-city airports?
7. **Aviation and wealth** — `routes_per_million_people` against GDP per capita.
8. **Time zones** — airports per UTC offset band; where does the world's air traffic actually sit?
9. **Classification** — predict `hub_class` from geography and country features.

## 📁 Files

| File | What it is |
|---|---|
| `airports.csv` | 7,698 airports x 43 parameters, route-network enriched. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook: hub ranking, long-haul map, wealth vs connectivity. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`aviation`, `transportation`, `geospatial`, `networks`, `airports`, `travel`, `logistics`, `graph-analysis`, `tabular`, `economics`

## 🔗 Provenance

- **Source:** **OpenFlights** open data, `airports.dat` and `routes.dat`
  (`github.com/jpatokal/openflights/data`). Airport records ultimately derive from OurAirports and DAFIF;
  route records are contributed by airlines and the OpenFlights community.
- **Licence of the upstream files:** Open Database License (ODbL) 1.0.
- **Transformation:** airport rows reshaped into 14 named columns; the route table aggregated per airport
  to produce degree, destination, airline, distance and domestic/international statistics.
- **Enrichment:** country population, GDP per capita, capital coordinates and UN regions joined from the
  World Bank-backed `countries-of-the-world` table in this repository by country name.
- **Snapshot date:** 20 November 2026.

## 🔄 Update frequency

**Never (static snapshot).** OpenFlights is largely frozen upstream; the network statistics here reflect the route table as of the snapshot date.

## ⚠️ Caveats

- Route coverage is community-maintained and uneven: some regions (notably parts of Africa and Central Asia) are under-reported.
- `\N` marks a missing IATA/ICAO code and is preserved rather than blanked so it can be filtered explicitly.
- Routes are counted as records in `routes.dat`; a route operated by three airlines counts three times.
- The country join is by name, so a few territories (e.g. 'Hong Kong', 'Macau') may not match a World Bank entity.
- Distances are great-circle, not flown track distances.
- The file is a snapshot of schedules, not of passenger volumes — no traffic or seat-capacity figures are included.

## 📜 Licence

Open Database License (ODbL) 1.0 for the OpenFlights airport and route data. Derived statistics may be shared under the same terms; attribution to OpenFlights and OurAirports is required.

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `airport_id` | `number` | OpenFlights airport identifier. |
| 2 | `name` | `string` | Airport name. |
| 3 | `city` | `string` | City served. |
| 4 | `country` | `string` | Country name as recorded by OpenFlights. |
| 5 | `iata` | `string` | 3-letter IATA code (\N when unassigned). |
| 6 | `icao` | `string` | 4-letter ICAO code (\N when unassigned). |
| 7 | `latitude` | `number` | Latitude in decimal degrees. |
| 8 | `longitude` | `number` | Longitude in decimal degrees. |
| 9 | `altitude_ft` | `number` | Elevation above sea level in feet. |
| 10 | `tz_offset_hours` | `number` | UTC offset in hours (fractional where applicable). |
| 11 | `dst` | `string` | Daylight-saving-time rule letter used by OpenFlights. |
| 12 | `tz_database` | `string` | IANA time-zone name. |
| 13 | `type` | `string` | Facility type: airport, heliport, seaplane base, closed. |
| 14 | `source` | `string` | Upstream data source for the record. |
| 15 | `continent` | `string` | Continent of the airport's country. |
| 16 | `region` | `string` | UN macro-region of the airport's country. |
| 17 | `subregion` | `string` | UN sub-region of the airport's country. |
| 18 | `hemisphere` | `string` | Northern or Southern hemisphere. |
| 19 | `altitude_band` | `string` | Elevation band from sea level to high plateau. |
| 20 | `has_iata` | `boolean` | true when the airport has an IATA code (i.e. is commercially ticketed). |
| 21 | `is_scheduled_service` | `boolean` | true for records typed `airport` (as opposed to heliport, seaplane base, closed). |
| 22 | `utc_offset_band` | `number` | UTC offset rounded to the nearest whole hour. |
| 23 | `n_routes_out` | `number` | Number of scheduled route records departing this airport. |
| 24 | `n_routes_in` | `number` | Number of scheduled route records arriving at this airport. |
| 25 | `n_airlines` | `number` | Distinct airlines operating to or from the airport. |
| 26 | `n_destinations` | `number` | Distinct airports reachable in one non-stop hop. |
| 27 | `n_destinations_international` | `number` | Distinct destination airports outside the airport's own country. |
| 28 | `n_countries_served` | `number` | Distinct foreign countries reachable non-stop. |
| 29 | `n_domestic_routes` | `number` | Route records whose origin and destination are in the same country. |
| 30 | `share_international_pct` | `number` | Percentage of this airport's route records that cross a border. |
| 31 | `top_airline` | `string` | Airline with the most route records at this airport. |
| 32 | `top_airline_routes` | `number` | Route records operated by that airline. |
| 33 | `mean_route_distance_km` | `number` | Mean great-circle distance of this airport's routes. |
| 34 | `max_route_distance_km` | `number` | Longest non-stop route from this airport. |
| 35 | `farthest_destination` | `string` | Airport code of that longest route. |
| 36 | `hub_class` | `string` | Network role from route count: Isolated, Feeder, Regional, Major, Global hub. |
| 37 | `capital_distance_km` | `string` | Great-circle distance to the country's capital city. |
| 38 | `is_near_capital` | `string` | true when the airport is within 40 km of its country's capital. |
| 39 | `routes_per_million_people` | `number` | Route records divided by country population in millions. |
| 40 | `country_population` | `number` | Country population (World Bank, joined). |
| 41 | `country_gdp_per_capita_usd` | `number` | Country GDP per capita (World Bank, joined). |
| 42 | `airports_in_country` | `number` | Number of airports in this file for the same country. |
| 43 | `name_word_count` | `number` | Number of words in the airport name. |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
