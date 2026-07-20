# Air Pollution Data Analysis

This repository contains an air quality dataset and an analysis notebook for exploring health impacts.

## To Obtain the data sets (if the datasets doesn't work you know where to get them)

- Create a new folder
- Open 'https://data.cityofnewyork.us/Environment/Air-Quality-and-Health-Impacts/c3uy-2p5r/about_data' for air quality and health impact data.
- Export the data into a csv file open it into the folder you just created.
- Open `https://a816-dohbesp.nyc.gov/IndicatorPublic/data-explorer/health-impacts-of-air-pollution/?id=2117#display=summary'
- Scroll all the way down to download and click download this view 


## What you need

- `Air_Quality_and_Health_Impacts_20260715.csv` - dataset with air quality and health impact data.
- `WORK_IN_PROGRESS.ipynb` - Jupyter notebook for analyzing the dataset.
- `NYC EH Data Portal - Asthma emergency department visits due to PM2.5 (filtered).csv` - dataset with Asthma emergency department visits due to PM2.5
- `Dataset2.ipynb` - Jupyter notebook for analyzing the dataset. (the second dataset)
- Make sure python, seaborn, pandas, and plotly in installed so the data runs smoothly.

## To download these (if you have them skip this step)

- donwload them in your terminal
- `%pip install jupyterlab`
- `%pip install python`
- `%pip install pandas` 
- `%pip install seaborn`
- `%pip install plotly` (to be able to see the graphs).
- `%pip install matplotlib` 

## Usage

1. Run Jupyter lab or Jupyter notebook on your terminal (depending on your device).
2. Open `WORK_IN_PROGRESS.ipynb` in Jupyter Notebook or Jupyter Lab.
3. Load `Air_Quality_and_Health_Impacts_20260715.csv` for analysis.
   - Repeat these steps for the second dataset
4. Open `Dataset2.ipynb` in Jupyter Notebook or Jupyter Lab.
5. Load `NYC EH Data Portal - Asthma emergency department visits due to PM2.5 (filtered).csv` for analysis.
6. Run the notebook cells to explore data cleaning, visualization, and insights.

## Notes

- The notebook likely contains the analysis workflow and any visualizations.
- Update this README if additional scripts or documentation are added.


## START OF THE PROJECT

1. We are going to start with first dataset on Air Quality and Health impacts. https://data.cityofnewyork.us/Environment/Air-Quality-and-Health-Impacts/c3uy-2p5r/about_data

2. The initial questions are:
   - Which borough has the highest air quality?
   - Why some boroughs have better air quality than other ones?

3. Find how many unique values are there in the columns (to write...)

## AI Disclosure

Generative AI (Google/ChatGPT) was utilized during data preprocessing to assist with writing Python code. Specifically, the AI provided a script to map NYC United Hospital Fund (UHF) geographic codes (Geo Join ID) to their respective NYC boroughs based on their leading digit. All AI-generated code was reviewed, debugged, and verified by the author before integration.
