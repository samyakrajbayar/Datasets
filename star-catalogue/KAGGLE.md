# Star Catalogue — HYG Hipparcos/Bright Star/Gliese Merge

**Subtitle:** 119,626 stars with positions, distances, proper motions, spectral types and derived stellar classes.

---

## 📖 Description

### 119,626 stars from the HYG catalogue

The HYG database merges the Hipparcos, Yale Bright Star and Gliese catalogues into one file with
positions, distances, motions and spectral types. This dataset contains **119,626 stars** and
**64 parameters**.

- **Identity** — HYG id, Hipparcos, HD, HR and Gliese numbers, Bayer/Flamsteed designations and
  proper names.
- **Position** — right ascension, declination, galactic x/y/z and constellation.
- **Distance and motion** — parsecs, light years, parallax, proper motions and radial velocity.
- **Photometry** — apparent and absolute magnitude, colour index and luminosity.
- **Derived** — spectral and luminosity classes, giant/supergiant/dwarf/white-dwarf flags, binary
  and variable flags, total proper motion and space velocity, magnitude/colour/distance bands, naked-eye
  and nearby flags and galactic-plane membership.

**465 stars carry a proper name**, **8,921 are naked-eye objects** and **8,744 lie
within 50 parsecs** — a base table for stellar populations, colour-magnitude diagrams and
constellation mapping.

## 🧾 Columns (64)

`id`, `hip`, `hd`, `hr`, `gl`, `bf`, `proper`, `ra`, `dec`, `dist`, `pmra`, `pmdec`, `rv`, `mag`, `absmag`, `spect`, `ci`, `x`, `y`, `z`, `vx`, `vy`, `vz`, `rarad`, `decrad`, `pmrarad`, `pmdecrad`, `bayer`, `flam`, `con`, `comp`, `comp_primary`, `base`, `lum`, `var`, `var_min`, `var_max`, `distance_ly`, `distance_pc`, `parallax_mas`, `proper_motion_mas_yr`, `space_velocity_kms`, `spectral_class`, `luminosity_class`, `is_giant`, `is_supergiant`, `is_dwarf_main_sequence`, `is_white_dwarf`, `is_binary`, `is_variable`, `has_proper_name`, `has_bayer`, `has_spectral_type`, `is_naked_eye`, `is_bright_star`, `magnitude_band`, `absmag_band`, `color_band`, `distance_band`, `is_nearby`, `high_proper_motion`, `constellation`, `hemisphere`, `in_galactic_plane`

## 💡 Ideas for using this data

1. **Hertzsprung-Russell diagram** — colour index vs absolute magnitude.
2. **Stellar populations** — spectral classes by distance band.
3. **Kinematics** — proper motion and space velocity distributions.
4. **Constellations** — star counts and brightness per constellation.
5. **Binaries** — multiplicity fraction by spectral class.
6. **Variables** — variable-star fraction across the catalogue.
7. **Solar neighbourhood** — the 50 pc volume.
8. **Names** — nomenclature coverage and historical naming.

## 📁 Files

| File | What it is |
|---|---|
| `hyg_stars.csv` | 119,626 stars x 64 parameters. |
| `data_dictionary.csv` | Column / type / description for every field. |
| `notebook.ipynb` | Starter notebook that loads the CSV and analyses it. |
| `dataset-metadata.json` | Kaggle API metadata. |
| `about.md` | Plain-text About block. |

## 🏷️ Tags

`astronomy`, `stars`, `hipparcos`, `catalogue`, `astrophysics`, `space`

## 🔗 Provenance

- **Source:** **HYG Database v4.1** (`hygdata_v41.csv`), maintained by David Nash on
  GitHub.
- **Processing:** catalogue parsed as delivered; distance, motion, luminosity and colour features
  derived; rows without a magnitude dropped.
- **Snapshot date:** 24 November 2026.

## 🔄 Update frequency

**Irregular.** The HYG database is updated occasionally by its maintainer.

## ⚠️ Caveats

- Distances come from Hipparcos parallaxes and are unreliable beyond a few hundred parsecs.
- Spectral types are heterogeneous across the source catalogues.
- Luminosity class parsing from spectral strings is heuristic.
- The catalogue is complete only to about magnitude 9 and is not a volume-complete survey.
- Coordinates are J2000 and proper motions are epoch-dependent.

## 📜 Licence

HYG Database by David Nash, CC BY-SA 4.0.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
