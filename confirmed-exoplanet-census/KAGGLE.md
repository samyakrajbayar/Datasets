# Confirmed Exoplanet Census - 6,473 Worlds

**Subtitle:** Every confirmed exoplanet with orbit, mass, radius and host-star parameters.

**Tags:** `astronomy`, `space`, `physics`, `science`, `exoplanets`, `nasa`, `astrophysics`, `tabular`, `regression`, `clustering`

**Dataset File:** `exoplanets.csv` (40,428 rows, 98 columns, 24.3 MB)

---

## 📖 Description

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

## 🧾 Columns (98)

`pl_name`, `hostname`, `hd_name`, `hip_name`, `tic_id`, `gaia_dr2_id`, `gaia_dr3_id`, `pl_letter`, `default_flag`, `pl_controv_flag`, `disc_locale`, `discoverymethod`, `disc_year`, `disc_facility`, `disc_instrument`, `disc_telescope`, `disc_pubdate`, `disc_refname`, `pl_orbper`, `pl_orbpererr1`, `pl_orbpererr2`, `pl_orbsmax`, `pl_orbsmaxerr1`, `pl_orbsmaxerr2`, `pl_orbeccen`, `pl_orbeccenerr1`, `pl_orbeccenerr2`, `pl_orbtper`, `pl_orblper`, `pl_imppar`, `pl_trandur`, `pl_tranmid`, `ttv_flag`, `pl_occdep`, `pl_ratdor`, `pl_ratror`, `pl_rade`, `pl_radeerr1`, `pl_radeerr2`, `pl_radj`, `pl_bmasse`, `pl_bmasseerr1`, `pl_bmasseerr2`, `pl_bmassj`, `pl_bmassprov`, `pl_dens`, `pl_denserr1`, `pl_denserr2`, `pl_eqt`, `pl_insol`, `pl_insolerr1`, `pl_insolerr2`, `pl_orbincl`, `st_spectype`, `st_teff`, `st_tefferr1`, `st_tefferr2`, `st_rad`, `st_raderr1`, `st_mass`, `st_masserr1`, `st_met`, `st_metratio`, `st_logg`, `st_age`, `st_lum`, `st_vsin`, `st_rotp`, `st_radv`, `sy_snum`, `sy_pnum`, `sy_mnum`, `sy_dist`, `sy_disterr1`, `sy_vmag`, `sy_kmag`, `sy_gaiamag`, `sy_plx`, `cb_flag`, `st_nphot`, `st_nrvc`, `st_nspec`, `ra`, `dec`, `glat`, `glon`, `orbital_period_years`, `orbital_speed_kms`, `planet_type`, `mass_class`, `density_class`, `in_habitable_zone`, `teq_class`, `transit_depth_ppm`, `discovery_decade`, `star_type_group`, `distance_light_years`, `system_planet_rank`

## 💡 Ideas for using this data

1. **Planet radius valley** — plot the radius distribution split by equilibrium temperature and reproduce the gap between super-Earths and mini-Neptunes.
2. **Detection-method bias** — compare period, radius and distance distributions for transit, radial-velocity, microlensing and imaging discoveries.
3. **Habitable zone census** — count temperate, rocky candidates per spectral class and per discovery decade.
4. **Mass–radius diagram** — fit a power law to `pl_bmasse` vs `pl_rade`, colouring by density class.
5. **Discovery timeline** — planets per year by facility; watch Kepler (2009–2013), K2 and TESS take over.
6. **Host-star metallicity** — test whether giant-planet hosts are more metal-rich than small-planet hosts.
7. **Classification** — predict `planet_type` from orbit and stellar features; or regress equilibrium temperature.
8. **Multi-planet systems** — use `sy_pnum` to study orbital spacing and the compactness of Kepler systems.
9. **Sky map** — plot RA/Dec or galactic coordinates to show the Kepler and TESS fields.

## 📁 Files

| File | What it is |
|---|---|
| `exoplanets.csv` | 40,428 confirmed exoplanets x 98 parameters. |
| `data_dictionary.csv` | Column / type / description for all fields. |
| `notebook.ipynb` | Starter notebook: radius valley, mass-radius, discovery timeline. |
| `dataset-metadata.json` | Kaggle API metadata (`kaggle datasets create -p .`). |
| `about.md` | Plain-text About block for the Kaggle web form. |

## 🏷️ Tags

`astronomy`, `space`, `physics`, `science`, `exoplanets`, `nasa`, `astrophysics`, `tabular`, `regression`, `clustering`

## 🔗 Provenance

- **Primary source:** NASA Exoplanet Archive, `ps` (Planetary Systems) table, served by the
  Table Access Protocol endpoint `https://exoplanetarchive.ipac.caltech.edu/TAP/sync`
  (query: `select * from ps`).
- **Upstream curation:** NASA Exoplanet Science Institute (NExScI) at Caltech, aggregating peer-reviewed
  detections from Kepler, K2, TESS, radial-velocity surveys, microlensing, imaging and astrometry.
- **Collection method:** direct TAP query, one JSON response, converted to CSV without filtering; 12
  derived columns computed from the archive values (formulas documented in the data dictionary).
- **Snapshot date:** 20 November 2026.
- **Record count:** every row returned by the table at snapshot time (the archive's `default_flag`
  column marks its preferred parameter set when a planet has several).

## 🔄 Update frequency

**Never (static snapshot).** The NASA Exoplanet Archive adds planets continuously; this file is frozen at the snapshot date above. Re-run `scripts/11_exoplanets.py` for a refreshed version — roughly monthly cadence is enough.

## ⚠️ Caveats

- Mass is frequently `m·sin i` rather than true mass — see `pl_bmassprov` before treating masses as exact.
- Uncertainty columns are asymmetric (err1 = lower, err2 = upper) and are often empty for older discoveries.
- Transit, RV and microlensing detections probe very different regions of parameter space, so the file is not a volume-complete sample of planets.
- Some planets appear more than once when the archive holds competing parameter sets; filter `default_flag = 1` for one row per planet.
- `st_lum` is log10(L/L_sun) and `st_logg` is log10(g in cgs) — both are logarithmic, not linear.

## 📜 Licence

Public domain / openly available. NASA Exoplanet Archive data are produced by Caltech/IPAC under contract with NASA and are free to use with attribution to the archive and the original discovery papers (see `disc_refname`).

### 📋 Column Definitions & File Header

| # | Column Name | Data Type | Description |
|---|---|---|---|
| 1 | `pl_name` | `string` | Planet name as used by the NASA Exoplanet Archive. |
| 2 | `hostname` | `string` | Host star name. |
| 3 | `hd_name` | `string` | HD catalogue identifier of the host star. |
| 4 | `hip_name` | `string` | Hipparcos catalogue identifier of the host star. |
| 5 | `tic_id` | `string` | TESS Input Catalog identifier of the host star. |
| 6 | `gaia_dr2_id` | `string` | Gaia Data Release 2 source id of the host star. |
| 7 | `gaia_dr3_id` | `string` | Gaia Data Release 3 source id of the host star. |
| 8 | `pl_letter` | `string` | Letter designating the planet within its system (b, c, d...). |
| 9 | `default_flag` | `number` | 1 if this is the archive's default parameter set for the planet. |
| 10 | `pl_controv_flag` | `number` | 1 if the planet's existence or parameters are disputed. |
| 11 | `disc_locale` | `string` | Where the discovery was announced (Ground, Space, ...). |
| 12 | `discoverymethod` | `string` | Detection technique (Transit, Radial Velocity, Imaging, Microlensing...). |
| 13 | `disc_year` | `number` | Year the discovery was announced. |
| 14 | `disc_facility` | `string` | Facility credited with the discovery. |
| 15 | `disc_instrument` | `string` | Instrument credited with the discovery. |
| 16 | `disc_telescope` | `string` | Telescope credited with the discovery. |
| 17 | `disc_pubdate` | `string` | Publication date of the discovery paper. |
| 18 | `disc_refname` | `string` | Reference string for the discovery paper. |
| 19 | `pl_orbper` | `number` | Orbital period in days. |
| 20 | `pl_orbpererr1` | `number` | Lower 1-sigma uncertainty on orbital period (days). |
| 21 | `pl_orbpererr2` | `number` | Upper 1-sigma uncertainty on orbital period (days). |
| 22 | `pl_orbsmax` | `number` | Semi-major axis of the orbit in AU. |
| 23 | `pl_orbsmaxerr1` | `number` | Lower uncertainty on semi-major axis (AU). |
| 24 | `pl_orbsmaxerr2` | `number` | Upper uncertainty on semi-major axis (AU). |
| 25 | `pl_orbeccen` | `number` | Orbital eccentricity. |
| 26 | `pl_orbeccenerr1` | `number` | Lower uncertainty on eccentricity. |
| 27 | `pl_orbeccenerr2` | `number` | Upper uncertainty on eccentricity. |
| 28 | `pl_orbtper` | `number` | Time of periastron passage (BJD). |
| 29 | `pl_orblper` | `number` | Argument of periastron (degrees). |
| 30 | `pl_imppar` | `number` | Transit impact parameter (stellar radii). |
| 31 | `pl_trandur` | `number` | Transit duration (hours). |
| 32 | `pl_tranmid` | `number` | Transit midpoint (BJD). |
| 33 | `ttv_flag` | `number` | 1 if transit timing variations are detected. |
| 34 | `pl_occdep` | `number` | Occultation depth (ppm). |
| 35 | `pl_ratdor` | `number` | Ratio of semi-major axis to stellar radius. |
| 36 | `pl_ratror` | `number` | Ratio of planet radius to stellar radius. |
| 37 | `pl_rade` | `number` | Planet radius in Earth radii. |
| 38 | `pl_radeerr1` | `number` | Lower uncertainty on planet radius (Earth radii). |
| 39 | `pl_radeerr2` | `number` | Upper uncertainty on planet radius (Earth radii). |
| 40 | `pl_radj` | `number` | Planet radius in Jupiter radii. |
| 41 | `pl_bmasse` | `number` | Planet mass or mass*sin(i) in Earth masses. |
| 42 | `pl_bmasseerr1` | `number` | Lower uncertainty on planet mass (Earth masses). |
| 43 | `pl_bmasseerr2` | `number` | Upper uncertainty on planet mass (Earth masses). |
| 44 | `pl_bmassj` | `number` | Planet mass in Jupiter masses. |
| 45 | `pl_bmassprov` | `string` | How the mass was measured (Mass, Msini, Msin(i)/sin(i)...). |
| 46 | `pl_dens` | `number` | Planet bulk density (g/cm^3). |
| 47 | `pl_denserr1` | `number` | Lower uncertainty on planet density. |
| 48 | `pl_denserr2` | `number` | Upper uncertainty on planet density. |
| 49 | `pl_eqt` | `number` | Equilibrium temperature (K), assuming zero albedo. |
| 50 | `pl_insol` | `number` | Insolation flux received by the planet (Earth flux). |
| 51 | `pl_insolerr1` | `number` | Lower uncertainty on insolation flux. |
| 52 | `pl_insolerr2` | `number` | Upper uncertainty on insolation flux. |
| 53 | `pl_orbincl` | `number` | Orbital inclination (degrees). |
| 54 | `st_spectype` | `string` | Stellar spectral type. |
| 55 | `st_teff` | `number` | Stellar effective temperature (K). |
| 56 | `st_tefferr1` | `number` | Lower uncertainty on stellar temperature. |
| 57 | `st_tefferr2` | `number` | Upper uncertainty on stellar temperature. |
| 58 | `st_rad` | `number` | Stellar radius (solar radii). |
| 59 | `st_raderr1` | `number` | Lower uncertainty on stellar radius. |
| 60 | `st_mass` | `number` | Stellar mass (solar masses). |
| 61 | `st_masserr1` | `number` | Lower uncertainty on stellar mass. |
| 62 | `st_met` | `number` | Stellar metallicity [Fe/H] (dex). |
| 63 | `st_metratio` | `string` | Stellar metallicity as a raw abundance ratio. |
| 64 | `st_logg` | `number` | Stellar surface gravity log10(g) (cgs). |
| 65 | `st_age` | `number` | Stellar age (Gyr). |
| 66 | `st_lum` | `number` | Stellar luminosity log10(L/L_sun). |
| 67 | `st_vsin` | `number` | Stellar projected rotational velocity (km/s). |
| 68 | `st_rotp` | `number` | Stellar rotation period (days). |
| 69 | `st_radv` | `number` | Stellar radial velocity (km/s). |
| 70 | `sy_snum` | `number` | Number of stars in the system. |
| 71 | `sy_pnum` | `number` | Number of confirmed planets in the system. |
| 72 | `sy_mnum` | `number` | Number of moons in the system. |
| 73 | `sy_dist` | `number` | Distance to the system (parsecs). |
| 74 | `sy_disterr1` | `number` | Lower uncertainty on system distance. |
| 75 | `sy_vmag` | `number` | V-band apparent magnitude of the host star. |
| 76 | `sy_kmag` | `number` | K-band apparent magnitude of the host star. |
| 77 | `sy_gaiamag` | `number` | Gaia G-band apparent magnitude of the host star. |
| 78 | `sy_plx` | `number` | Parallax of the system (mas). |
| 79 | `cb_flag` | `number` | 1 if the planet orbits a circumbinary system. |
| 80 | `st_nphot` | `number` | Number of photometric observation sets in the archive. |
| 81 | `st_nrvc` | `number` | Number of radial-velocity observation sets. |
| 82 | `st_nspec` | `number` | Number of spectroscopic observation sets. |
| 83 | `ra` | `number` | Right ascension of the host star (degrees). |
| 84 | `dec` | `number` | Declination of the host star (degrees). |
| 85 | `glat` | `number` | Galactic latitude (degrees). |
| 86 | `glon` | `number` | Galactic longitude (degrees). |
| 87 | `orbital_period_years` | `number` | Orbital period converted to Earth years. |
| 88 | `orbital_speed_kms` | `number` | Mean orbital speed (km/s) from semi-major axis and period. |
| 89 | `planet_type` | `string` | Radius class: Sub-Earth, Earth-size, Super-Earth, Mini-Neptune, Neptune-size, Jupiter-size, Giant. |
| 90 | `mass_class` | `string` | Mass class from Earth masses (<2, 2-10, 10-50, 50-300, >300). |
| 91 | `density_class` | `string` | Rocky / Intermediate / Gaseous from bulk density. |
| 92 | `in_habitable_zone` | `boolean` | true when insolation flux is between 0.35 and 1.5 Earth fluxes. |
| 93 | `teq_class` | `string` | Equilibrium-temperature band (Cold, Temperate, Warm, Hot, Ultra-hot). |
| 94 | `transit_depth_ppm` | `number` | Derived transit depth in ppm from (Rp/Rs)^2. |
| 95 | `discovery_decade` | `string` | Decade of the discovery year. |
| 96 | `star_type_group` | `string` | Coarse spectral group (O/B, A, F, G, K, M, other). |
| 97 | `distance_light_years` | `number` | System distance converted to light years. |
| 98 | `system_planet_rank` | `number` | Planet letter index within the system (b=1). |



---

## 🌟 Support & Community
If you find this dataset valuable for your research, portfolio, or machine learning projects, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and notebook submissions are warmly welcomed in the Discussions tab.
