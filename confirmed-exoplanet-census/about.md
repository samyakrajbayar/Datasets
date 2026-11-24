Confirmed Exoplanet Census

### A census of every confirmed planet outside the Solar System

The NASA Exoplanet Archive is the reference catalogue of confirmed exoplanets. This snapshot exports its
`ps` (planetary systems) table as a single flat CSV: **40,428 parameter-set rows covering 6,473
distinct planets**, described by **98 parameters** spanning discovery, orbit, bulk properties,
host star and system geometry. A planet with several published parameter sets appears once per set;
filter `default_flag = 1` for exactly one row per planet.

Every row includes:
- **Identity & discovery** — planet and host names, HD/HIP/TIC/Gaia cross-ids, detection method, year,
  facility, instrument, telescope and the discovery reference.
- **Orbit** — period with asymmetric uncertainties, semi-major axis, eccentricity, argument of periastron,
  impact parameter, transit duration/midpoint, TTV flag, radius and semi-major-axis ratios.
- **Bulk properties** — radius in Earth and Jupiter radii, mass (with the provenance of that mass:
  true mass or m·sin i), density, equilibrium temperature, insolation flux, orbital inclination.
- **Host star** — spectral type, effective temperature, radius, mass, metallicity, surface gravity, age,
  luminosity, rotation and radial velocity.
- **System** — star / planet / moon counts, distance, parallax, V/K/Gaia magnitudes, circumbinary flag,
  number of photometric, RV and spectroscopic datasets, and sky position (RA/Dec, galactic).

Twelve derived features are appended so the file is analysis-ready: orbital period in years, mean orbital
speed, radius class, mass class, density class, habitable-zone flag, equilibrium-temperature band, transit
depth in ppm, discovery decade, stellar spectral group, distance in light years and the planet's rank in
its system.

The catalogue is naturally imbalanced toward transits and radial-velocity detections, and mass is often a
lower limit — both are part of the phenomenon, not a defect, and make the file good material for
selection-effect studies.

98 columns; one row per confirmed planet parameter set.
