# Pokémon Complete Stats — 1,351 Pokémon, 46 Engineered Features

**Subtitle:** Every Pokémon with base stats, types, abilities, breeding data, physical measurements and 15+ derived battle features.

---

## 📖 Description

There are dozens of "Pokémon stats" CSVs on the internet, and almost all of them stop at six stats and two type columns. This one goes further: **1,351 Pokémon** (all national-dex entries, including alternate forms such as Mega Evolutions, regional variants and Gigantamax forms) with **46 columns** pulled from the [PokéAPI](https://pokeapi.co) GraphQL endpoint.

Beyond the raw API fields, the dataset ships with derived features designed for actual modelling:

- **Battle composites** — `physique_score`, `special_score`, `offense_score`, `defense_score`, plus `stat_total` and `stat_average`.
- **Physical proxies** — height and weight in both API units and metric, plus a `bmi` feature (a playful but genuinely predictive variable for bulky Pokémon).
- **Catch & breeding economy** — `capture_rate`, a normalised `capture_difficulty`, `base_happiness`, `hatch_counter`, estimated `hatch_steps_estimate`, and `gender_ratio_male_pct`.
- **Evolution & taxonomy** — generation, colour, habitat, body shape, `evolves_from_species_id` so you can rebuild evolution chains.
- **Ability profile** — full ability list, count, and a dedicated `hidden_ability` column.

Because each row is a single Pokémon with both categorical and numeric features, it works equally well for EDA, clustering, regression (predicting `base_experience` or `capture_rate` from stats) and teaching feature engineering.

## 🧾 Column groups

- **Identity**: `pokemon_id`, `name`, `generation`, `generation_id`, `is_default_form`
- **Rarity**: `is_legendary`, `is_mythical`, `is_baby`
- **Typing**: `type_1`, `type_2`, `type_count`
- **Size**: `height_dm`, `height_m`, `weight_hg`, `weight_kg`, `bmi`
- **Stats**: `hp`, `attack`, `defense`, `special_attack`, `special_defense`, `speed`, `stat_total`, `stat_average`, and the four composites
- **Abilities**: `n_abilities`, `abilities`, `hidden_ability`
- **Catching/breeding**: `capture_rate`, `capture_difficulty`, `base_happiness`, `gender_ratio_male_pct`, `hatch_counter`, `hatch_steps_estimate`, `growth_rate_id`, `evolves_from_species_id`
- **Taxonomy**: `color`, `habitat`, `shape`, `has_gender_differences`, `name_length`

## 💡 Ideas for using this data

1. **Type-effectiveness EDA** — which type pairs have the highest average stat totals?
2. **Clustering** — do unsupervised clusters recover the classic "sweeper / wall / tank" archetypes?
3. **Regression** — predict `base_experience` or `capture_rate` from stats and typing.
4. **Power creep over generations** — track `stat_total` by generation and legendary status.
5. **Classification** — can a model tell legendary/mythical Pokémon from regular ones using only stats and size?

## ⚠️ Caveats

- Alternate forms appear as separate rows with ids outside the classic 1–1025 range; filter on `is_default_form` for species-level analysis.
- `gender_ratio_male_pct` is empty for genderless species.
- `bmi` is a derived novelty feature, not a health metric.

## 🔗 Provenance & licence

- Source: PokéAPI (`graphql.pokeapi.co`, v1beta2) — community-maintained, Pokémon data © Nintendo / Game Freak / The Pokémon Company, used here for non-commercial research and fan analytics.
- Snapshot: November 2026. 1,351 rows × 46 columns.

---

## 🌟 Support & Community
If you find this dataset valuable for your machine learning workflows, analyses, or data explorations, **please give it an upvote (👍) on Kaggle!**
Feedback, questions, and community notebook submissions are warmly welcomed in the Discussions tab.
