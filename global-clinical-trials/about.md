Global Clinical Trials Registry

### The world's clinical trial registry, flattened for analysis

ClinicalTrials.gov is the largest trial registry on earth. This snapshot takes
**10,000 study records** (the most recently updated ones) and flattens the registration
document into **81 tidy columns** — one row per trial.

What each row carries:
- **Identity** — NCT number, brief and official title, acronym, sponsor protocol id,
  submitting organisation and its class, secondary identifiers.
- **Status and dates** — overall and last-known status, why a trial stopped, start,
  primary-completion and completion dates, first-posted, last-updated and results-posted dates.
- **Design** — study type, phase (raw list plus a cleaned label), allocation, intervention
  model, masking, primary purpose, number of arms, enrollment count and type.
- **Conditions and interventions** — full condition and keyword lists, intervention names
  and types, arm-group count.
- **Outcomes** — primary outcome measures and counts, secondary and other outcome counts.
- **Eligibility** — sex, minimum and maximum age, standard age groups, healthy-volunteer flag,
  sampling method.
- **Geography and sponsorship** — every country with a site, site and facility counts,
  US-site flag, lead sponsor and class, collaborator list.
- **Oversight and sharing** — FDA drug/device regulation flags, data-monitoring-committee flag,
  individual-patient-data sharing statement, reference count.
- **Derived features** — planned duration in days, start year, age bounds in years,
  pediatric/adult/senior flags, industry/academic sponsor flags, enrollment size band,
  randomised/blinded flags, update lag and title/abstract lengths.

**0 trials (0.0%)** are industry-sponsored and **1,354** have posted results,
so the file supports both registry science and meta-research on reporting bias.

81 columns; one row per registered study, flattened from the ClinicalTrials.gov API v2 JSON.
