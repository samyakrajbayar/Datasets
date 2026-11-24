Active Satellite Orbits

### Everything currently in orbit, with its orbital mechanics worked out

A snapshot of the **CelesTrak** general-perturbations catalogue, derived from US Space Force tracking
data: **12,901 satellites** described by **41 parameters**, including the full set of orbital
elements plus the geometry analysts usually have to compute themselves.

Each row contains:
- **Identity** — object name, international designator (whose prefix is the launch year),
  NORAD catalogue number and the general-perturbations record id.
- **Orbital elements** — epoch, mean motion, eccentricity, inclination, right ascension of the ascending
  node, argument of perigee, mean anomaly, B* drag term and its derivatives, element set number and
  revolution count at epoch.
- **Geometry** — semi-major axis, period, perigee and apogee (computed from mean motion and
  eccentricity) and mean altitude above the Earth's surface.
- **Derived mechanics** — orbital regime (LEO/MEO/GEO/HEO), geostationary and geosynchronous flags,
  sun-synchronous, polar and retrograde flags, mean orbital speed from the vis-viva equation,
  revolutions per day, and inclination and altitude bands.
- **Fleet structure** — an inferred constellation label (Starlink, OneWeb, Planet, Iridium, GPS, ...),
  operator group, number of catalogue objects in that constellation, launch year and satellite age.

**12,199 objects are in low Earth orbit**, **396 are geostationary**, and the largest constellations
in the file are Starlink (11,206), OneWeb (651), BeiDou (56), GPS (32), Galileo (32) — a direct measurement of the
mega-constellation era.

41 columns; one row per catalogued object.
