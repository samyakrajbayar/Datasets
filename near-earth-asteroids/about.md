Near-Earth Asteroids

### Every known near-Earth asteroid, with full orbital elements

NASA/JPL's Small-Body Database is the authoritative catalogue of Solar System objects. This dataset
is a complete query of its **near-Earth object** subset: **43,367 asteroids** with **60 parameters** each.

Columns cover:
- **Identity** — SPK id, full name, proper name, permanent/provisional designation, discovery number.
- **Dynamics** — semi-major axis, eccentricity, perihelion and aphelion, inclination, node, argument of
  perihelion, mean anomaly, epoch, time of perihelion, period in days and years, mean motion,
  and a derived orbit class (Atira / Aten / Apollo / Amor).
- **Hazard metrics** — Earth MOID in AU, km and lunar distances, the standard
  potentially-hazardous flag, Earth- and Mars-crossing flags, and the Tisserand parameter.
- **Orbit quality** — observation arc, first and last observation dates, RMS residual,
  condition code, orbit producer and a two-body flag.
- **Physical properties** — absolute magnitude H, measured diameter, a size estimate from H for the
  majority without a measured diameter, albedo, rotation period, SMASSII and Tholen spectral types.
- **Derived features** — diameter and inclination classes, retrograde, near-circular and
  high-eccentricity flags, name features and data-completeness flags.

**24,643 objects** are Apollo-class and **23,447** meet the MOID-based potentially-hazardous
criterion. Diameter is missing for most objects, which makes the H-to-size estimate a useful,
explicitly documented imputation rather than a hidden one.

60 columns; one row per near-Earth asteroid.
