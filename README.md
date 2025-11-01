# ssm_dashboard

### Main Branch Structure & Usage

The `main` branch is structured to reflect the full data pipeline.

Only stable, tested, and production-ready code, notebooks, and assets should be pushed directly to `main`. Please use feature branches or PRs for all development work.


```
ssm_dashboard/
│
├── data/                      # All datasets and supporting files
│   ├── raw/                   # Unmodified source data
│   └── data_sources_audit.md  # Markdown file detailing data sources
│
├── notebooks/                # Development and exploration notebooks
│   ├── 01_data_collection/   # Ingesting and loading public data
│   ├── 02_data_cleaning/     # Cleaning and normalizing raw datasets
│   └── 03_exploration/       # Exploratory Data Analysis (EDA)
│
├── scripts/                  # Production-grade scripts
│   ├── clean/                # Data transformation logic
│   └── etl/                  # Extract, Transform, Load
│
├── dashboard/                # Dashboard source code
│   ├── data/                 # Dashboard data
│   ├── pages/                # UI components
│   ├── reports/              # Individual reports/Mini dashboards
│   ├── utils/                # Shared functions, helpers, constants
│   ├── paths.py              # Data paths, helper functions
│   └── Home.py               # Main dashboard app entry point
│
├── docs/                     # Project documentation and planning
│   ├── data_sources.md       # List of public data sources and details
│   └── Dataset Analysis.pdf  # From initial data exploration
│
├── README.md                 # Project overview and getting started
├── start.bat                 # To run app
└── requirements.txt          # Python dependencies
```


# Ontario Municipalities Dashboard

An interactive prototype Streamlit app that visualizes socioeconomic and demographic indicators for Ontario SSMs (service system managers). It renders a choropleth map and summary metrics for median household income, homeownership rate, population, and growth rates, with drill‑downs for any municipality.

## Features

* **Interactive map (Plotly Mapbox)**: choropleth by selected metric with pan/zoom.
* **Ontario summary**: province‑wide headline numbers and change metrics.
* **Region details**: select any CSD to see income, homeownership, households, and population metrics side‑by‑side.
* **Name normalization & safe formatting**: utilities to clean place names and display numbers with sensible defaults.

## Quickstart

**Python 3.9–3.12** recommended.

```bash
# 1) Create/activate a virtual environment (recommended)
python -m venv .venv
# Windows: 
.\.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate

# 2) Install dependencies
pip install -r requirements.txt
# or
pip install streamlit pandas numpy geopandas folium streamlit-folium
pip install plotly beautifulsoup4 seaborn matplotlib scipy statsmodels


# 3) Run the app
streamlit run dashboard/Home.py
# OR
.\start.bat

# 4) Run if changed files for cleaning of region-SSM mapping
python scripts/clean/clean_extract_ssm.py
```


## References

* **App prototype**: `prototype/streamlit-insights`
* **Client meeting — sample dashboards**:

  * ArcGIS Experience: [https://experience.arcgis.com/experience/6ebef168efed4d86bf1f1af69008a423/](https://experience.arcgis.com/experience/6ebef168efed4d86bf1f1af69008a423/)
  * CMHC Housing Market Information: [https://www03.cmhc-schl.gc.ca/hmip-pimh/#Profile/35/2/Ontario](https://www03.cmhc-schl.gc.ca/hmip-pimh/#Profile/35/2/Ontario)
