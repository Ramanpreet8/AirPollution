# NYC Air Quality and Asthma Emergency Visits

Exploring how PM2.5 air pollution relates to asthma emergency department (ED)
visits across New York City boroughs and neighborhoods, using two public
datasets.

## Questions

**Air quality** (`WORK_IN_PROGRESS.ipynb`)
- Which borough has the lowest (best) and highest (worst) PM2.5 concentration?
- How do PM2.5 levels vary across the five boroughs, and how have they changed over time?

**Asthma ED visits** (`Dataset2.ipynb`)
- Which borough has the highest burden of asthma ED visits attributable to PM2.5, in counts and in rates?
- Which age group is most affected (2005-2007)?

## Key Findings

### Air quality (PM2.5 annual mean, borough level, 2009-2024)

- **Manhattan has the worst PM2.5 and Staten Island the best.** Manhattan was
  highest in all 16 years (average 9.4 mcg/m³). Staten Island was lowest in 15
  of 16 years (average 7.2 mcg/m³); Queens edged it out in the other.
- **Air quality improved sharply everywhere.** Citywide PM2.5 fell about 40%,
  from 10.4 mcg/m³ in 2009 to 6.3 in 2024. Every borough dropped 39-42%, with
  the Bronx improving most (-42%). The borough ranking barely changed.
- **Progress isn't perfectly steady.** Citywide PM2.5 rose from 5.8 (2022) to
  6.7 (2023) before falling again in 2024.

### Asthma ED visits attributable to PM2.5 (2005-2007)

- **The Bronx has the highest burden, in counts and in rates.** Estimated
  annual visits: Bronx 2,016, Brooklyn 1,675, Manhattan 1,283, Queens 862,
  Staten Island 170. Per 100,000 people, the Bronx rate is 212.5 for children
  and 122.3 for adults, about 1.7x and 2.1x the citywide rates.
- **Counts and rates tell different stories.** Brooklyn is second in counts but
  third in rates for both age groups. Manhattan ranks second in children's
  rates (179.4) and has the highest PM2.5 of any borough.
- **Adults have more visits, but children are hit harder per person.** Adults
  account for about 60% of visits citywide, but the children's rate (126.3) is
  about 2.2x the adult rate (56.9).
- **The burden fell in every borough** between 2005-2007 and 2017-2019. In the
  Bronx, children's rates dropped about 49% and adults' about 57%. The Bronx
  stayed highest for adults in every period, and for children in four of the
  five (Manhattan was higher in 2009-2011).
- **The three neighborhoods with the most visits** are High Bridge-Morrisania
  and Crotona-Tremont (Bronx) and Bedford Stuyvesant-Crown Heights (Brooklyn).

### Linking the two datasets

- **PM2.5 level alone does not explain asthma burden.** Across the 42 UHF
  neighborhoods, PM2.5 and asthma ED rates are only weakly correlated
  (Spearman 0.15-0.29, Pearson 0.06-0.18, depending on period and age group).
  Manhattan has the highest PM2.5, but the Bronx has the highest asthma burden.

## Data

| File | Source | Description |
|---|---|---|
| `Air_Quality_and_Health_Impacts_20260715.csv` | [NYC Open Data](https://data.cityofnewyork.us/Environment/Air-Quality-and-Health-Impacts/c3uy-2p5r/about_data) | Air quality measures and modeled health impacts by borough, UHF neighborhood, and community district (about 19,800 rows) |
| `NYC_EH_Data_Portal_-_Asthma_emergency_department_visits_due_to_PM2_5__filtered_.csv` | [NYC EH Data Portal](https://a816-dohbesp.nyc.gov/IndicatorPublic/data-explorer/health-impacts-of-air-pollution/?id=2117#display=summary) | Estimated asthma ED visits due to PM2.5, 2005-2007, citywide, by borough, and by UHF 42 neighborhood (47 rows) |

**Re-downloading the data**

1. Air quality: open the NYC Open Data link above, export the dataset as CSV,
   and save it in the project folder.
2. Asthma ED visits: open the Data Portal link above, scroll to the bottom of
   the page, and click "Download this view".

Make sure each file's name matches the one the notebook loads (see the
`pd.read_csv(...)` line near the top of each notebook).

### Key columns

**Air quality dataset**

| Column | Meaning |
|---|---|
| `Name` | Indicator, such as "Fine particles (PM 2.5)" or "Nitrogen dioxide (NO2)" |
| `Measure` / `Measure Info` | How it is measured (annual, summer, or winter mean) and its units (mcg/m³, ppb, per 100,000) |
| `Geo Type Name` | Geography level: Citywide, Borough, UHF34, UHF42, or CD |
| `Geo Join ID` | Geography code; the leading digit identifies the borough for Borough, UHF34, and UHF42 rows |
| `Time Period` | Year (for example `2024`) or multi-year span (for example `2005-2007`) |
| `Data Value` | The measured or estimated value |

**Asthma ED visits dataset**

| Column | Meaning |
|---|---|
| `GeoTypeDesc` | Citywide, Borough, or UHF 42 |
| `Estimated annual number (under age 18)` / `(age 18+)` | Estimated yearly ED visits attributable to PM2.5 |
| `Estimated annual rate ... per 100,000` | The same estimate per 100,000 children or adults (borough and citywide rows only) |

## Getting Started

Requires Python 3.10+.

```bash
git clone <repo-url>
cd <repo-folder>
pip install jupyterlab pandas seaborn plotly matplotlib
jupyter lab
```

Then open the notebooks and run each one from top to bottom:

1. `WORK_IN_PROGRESS.ipynb` (air quality dataset)
2. `Dataset2.ipynb` (asthma ED visits dataset)

Plotly charts need a running notebook to display; they may not render when
viewed on GitHub.

## Methodology

- **Borough mapping.** The leading digit of `Geo Join ID` is mapped to a borough
  (1 Bronx, 2 Brooklyn, 3 Manhattan, 4 Queens, 5 Staten Island). This is only
  valid for Borough, UHF34, and UHF42 rows, so Citywide and CD rows are excluded.
- **Air quality comparison.** Boroughs are compared using PM2.5 *annual mean*
  at the *Borough* geography level. Summer and winter means, and neighborhood
  rows, are not averaged into the same figure.
- **Asthma comparison.** Borough totals use only the Borough rows. The file also
  contains neighborhood rows that already sum to each borough, so adding all
  rows together would double-count. Comparisons use per-100,000 rates as well
  as raw counts, since counts largely reflect population size.
- **Cleaning.** Thousands separators are removed from numeric columns, dates
  and time periods are parsed, and columns not needed for the analysis are
  dropped.
- **Linking datasets.** For the 42 UHF neighborhoods, PM2.5 annual mean is
  compared with asthma ED rates for the closest matching period (for example,
  2009 against 2009-2011).

## Limitations

- Asthma figures are modeled estimates of the burden attributable to PM2.5,
  not measured hospital counts.
- The Dataset2 notebook covers only 2005-2007. The PM2.5 series starts in 2009,
  so the two datasets do not overlap for that period.
- Results show association, not causation, and neighborhood-level patterns do
  not necessarily apply to individuals.
- Borough rankings by raw count reflect population size, so rates are used for
  comparisons wherever they are available.

## Project Structure

```
.
├── README.md
├── WORK_IN_PROGRESS.ipynb      # Air quality analysis
├── Dataset2.ipynb              # Asthma ED visits analysis
├── Air_Quality_and_Health_Impacts_20260715.csv
└── NYC_EH_Data_Portal_-_Asthma_emergency_department_visits_due_to_PM2_5__filtered_.csv
```

## AI Disclosure

Generative AI (Google/ChatGPT) was used during data preprocessing to assist
with writing Python code. Specifically, the AI provided a script to map NYC
United Hospital Fund (UHF) geographic codes (Geo Join ID) to their respective
NYC boroughs based on their leading digit. All AI-generated code was reviewed,
debugged, and verified by the author before integration.

## License

Add a license (for example MIT) and state it here. The datasets are published
by the NYC Department of Health and Mental Hygiene and NYC Open Data; check
their terms of use before redistributing.
