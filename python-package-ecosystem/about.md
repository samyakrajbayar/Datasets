Python Package Ecosystem

### The Python package ecosystem, ranked by real downloads

PyPI serves millions of package downloads a day and publishes the numbers. This dataset combines the
**top 4,999 projects by 30-day downloads** with each project's full PyPI metadata.

Per package you get **47 parameters**:
- **Reach** — download rank and count for the last 30 days, share of the ecosystem's downloads,
  download concentration implied by the ranks.
- **Identity** — name, summary, author, canonical URL, home page, project URLs (docs / source /
  changelog), keywords.
- **Licensing** — raw licence string plus a normalised class (MIT, Apache, GPL, BSD, MPL, LGPL,
  public domain, Creative Commons, other, unknown).
- **Compatibility** — `requires_python`, supported Python versions from classifiers, Python-3-only
  flag, wheel and sdist availability, file sizes, yanked files.
- **Dependencies** — runtime dependency count (extras excluded), extras entries, a has-dependencies flag.
- **Release history** — version count, first and latest release dates, total and yanked file counts,
  age, days since last release, releases per year, cadence and maturity bands.
- **Packaging hygiene** — classifier and topic counts, development status, project-URL completeness,
  pre-release flag.

The top 10 projects alone account for **11.1%** of all downloads in the file,
which makes download concentration, release cadence and dependency counts directly comparable.

47 columns; one row per PyPI project.
