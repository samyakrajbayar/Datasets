Nobel Prize Laureates 1901–2026

### Every Nobel Prize ever awarded, one row per laureate

Straight from the Nobel Foundation's open API: **1,085 rows** covering the 126 award years from
1901 to 2026, describing **1,005 individual laureates** and **31 organisational
laureates** through **46 parameters**.

Each row is one laureate receiving one prize (a shared prize therefore produces several rows sharing the
same `prize_year`/`category`), and includes:
- **The prize** — year, category and full official name, announcement date, prize amount in SEK, the
  inflation-adjusted amount and how many laureates shared it.
- **The laureate** — API id, person/organisation type, known name, full name, given and family name,
  gender, organisation name and the fraction of the prize received.
- **The citation** — the motivation text explaining the award.
- **Life and place** — birth date, city, country at the time and present-day country, continent of birth,
  death date and city, all affiliations with their cities and countries.
- **Derived measures** — age at award, birth and death year, lifespan, posthumous and shared-prize flags,
  share of the prize in percent, prize value per laureate, value of the laureate's own portion (raw and
  inflation-adjusted), decade, century, category group and years since the award.

Years in which a prize was not awarded appear as a single row with `laureate_type = none`, so the file can
be used directly for time-series work without silently dropping years.

46 columns; one row per laureate per prize.
