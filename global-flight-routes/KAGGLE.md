# Global Flight Routes Network

**Subtitle:** 67,663 airline routes with airport coordinates, airline details, aircraft and great-circle distances.

---

## 📖 Description

### 67,663 airline routes linking the world's airports

OpenFlights publishes the route map assembled from airline schedules and airport registries. This
dataset joins **67,663 routes** to airport coordinates, airline details and aircraft equipment, giving
**44 parameters** per route.

- **Airline** — code, id, name, IATA/ICAO codes, callsign, country and active flag.
- **Endpoints** — airport codes, names, cities, countries, coordinates, elevation and timezone for
  both origin and destination.
- **Route** — codeshare flag, stops, aircraft equipment codes and equipment count.
- **Derived geography** — great-circle distance and bands, domestic/international flags, altitude
  gap, latitude/longitude gaps, equator crossing and eastbound direction.

**34,774 routes are international** and the longest non-stop route in the file is **16,082 km**
(LUN to SLI). The network supports hub
analysis, airline strategy, graph analytics and travel-demand modelling.

## 🧾 Columns (44)

`airline`, `airline_id`, `airline_name`, `airline_iata`, `airline_icao`, `airline_callsign`, `airline_country`, `airline_active`, `source_airport`, `source_airport_id`, `source_name`, `source_city`, `source_country`, `source_icao`, `source_lat`, `source_lon`, `source_altitude_ft`, `source_timezone`, `destination_airport`, `destination_airport_id`, `destination_name`, `destination_city`, `destination_country`, `destination_icao`, `destination_lat`, `destination_lon`, `destination_altitude_ft`, `destination_timezone`, `codeshare`, `stops`, `equipment`, `equipment_count`, `primary_equipment`, `distance_km`, `distance_band`, `is_domestic`, `is_international`, `is_codeshare`, `has_stops`, `altitude_gap_ft`, `lat_gap`, `lon_gap`, `crosses_equator`, `eastbound`

## 💡 Ideas for using this data

1. **Network analysis** — degree and betweenness centrality of airports.
2. **Hub structure** — airlines with the most concentrated networks.
3. **Route length** — domestic vs international distance distributions.
4. **Geographic patterns** — eastbound vs westbound and equator-crossing routes.
5. **Codeshares** — which airlines share the most routes.
6. **Aircraft deployment** — equipment codes by distance band.
7. **Community detection** — country and regional route communities.
8. **Connectivity gaps** — airports with few inbound routes.
9. **Graph ML** — link prediction on the airport network.

## 📁 Files

| File | What it is |
|---|---|
| `flight_routes.csv` | 67,663 routes x 44 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`aviation`, `airlines`, `routes`, `network`, `geography`, `transport`

## 🔗 Provenance

- **Source:** **OpenFlights** data files (`routes.dat`, `airports.dat`, `airlines.dat`)
  from the openflights-data GitHub repository.
- **Processing:** routes joined to airports by IATA code (falling back to OpenFlights id) and to
  airlines by id/IATA; great-circle distances and geography features derived.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Static archive.** OpenFlights updates the data files irregularly.

## ⚠️ Caveats

- OpenFlights has not been continuously maintained; some routes and airlines are historical.
- Route records are airline-declared, not observed flights; frequencies are not included.
- Airport coordinates are rounded in the source and distances use a spherical Earth.
- Duplicate route rows were removed on the nine raw fields.
- Equipment codes are IATA aircraft types and are often missing.

## 📜 Licence

OpenFlights data, Open Database License (ODbL 1.0).

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
