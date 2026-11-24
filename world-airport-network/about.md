World Airport Network

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

43 columns; one row per airport.
