# Air Pollution Data Analysis

This repository contains an air quality dataset and an analysis notebook for exploring health impacts.

## Files

- `Air_Quality_and_Health_Impacts_20260715.csv` - dataset with air quality and health impact data.
- `work.ipynb` - Jupyter notebook for analyzing the dataset.

## Usage

1. Open `work.ipynb` in Jupyter Notebook or JupyterLab.
2. Load `Air_Quality_and_Health_Impacts_20260715.csv` for analysis.
3. Run the notebook cells to explore data cleaning, visualization, and insights.

## Notes

- The notebook likely contains the analysis workflow and any visualizations.
- Update this README if additional scripts or documentation are added.


## START OF THE PROJECT

1. We are going to start with first dataset on Air Quality and Health impacts. https://data.cityofnewyork.us/Environment/Air-Quality-and-Health-Impacts/c3uy-2p5r/about_data 

2. The initial questions are:

3. Find how many unique values are there in the columns (to write...)

4. AI Disclosure: Generative AI (Google/ChatGPT) was utilized during data preprocessing to assist with writing Python code. Specifically, the AI provided a script to map NYC United Hospital Fund (UHF) geographic codes (Geo Join ID) to their respective NYC boroughs based on their leading digit. All AI-generated code was reviewed, debugged, and verified by the author before integration.

5. ## AI Disclosure (cleaning phase)

Generative AI (Claude) was used to help diagnose and fix data-cleaning
bugs, including:
- Identifying that Community District ("CD") and Citywide rows use a
  different Geo Join ID convention than UHF/Borough rows, and should be
  filtered out before mapping boroughs by leading digit.
- Converting Data Value and Start_Date to proper numeric/datetime types.
- Deriving a Period Length / Period Duration column from the Time Period
  text field (e.g., "2017-2019" → 3-year average) since some readings are
  multi-year averages rather than single-year values.

