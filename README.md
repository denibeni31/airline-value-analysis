# Airline Value & Customer Experience Analysis

An independent data science learning project using Python and Pandas to explore U.S. airline reliability and consumer value. The current analysis focuses on flight delays, cancellations, and route-specific performance.

**Status:** Work in progress — exploratory data analysis. The long-term goal is to compare reliability, ticket prices, and customer satisfaction in a flight comparison tool. Pricing, customer satisfaction, SQL, Excel, predictive modeling, and the tool are planned work.

## Current analysis

The [Jupyter notebook](pynotebooks/flight_analysis.ipynb) includes:

- Dataset inspection and missing-value investigation.
- Filtering completed flights separately from cancellations and diversions.
- Airline-level delay and cancellation rates using Pandas grouping and aggregation.
- Exploration of flights departing Orlando International Airport (MCO).
- A focused Delta and JetBlue comparison on MCO → JFK.
- Initial exploration of scheduled departure times.

## Data

Source: U.S. Department of Transportation, Bureau of Transportation Statistics (BTS), [Reporting Carrier On-Time Performance](https://transtats.bts.gov/DL_SelectFields.aspx?QO_fu146_anzr=b0-gvzr&gnoyr_VQ=FGJ).

The local dataset contains **631,970 flight records and 25 columns for July 2026**. It includes flight dates, carriers, airports, scheduled times, delays, cancellations, diversions, flight durations, distances, and delay causes. The raw data is excluded from GitHub; download it from BTS to run the notebook.

## Preliminary findings

Across the dataset, **28.34% of 612,038 completed flights** arrived at least 15 minutes late.

For MCO → JFK in July 2026:

| Metric | Delta (DL) | JetBlue (B6) |
| --- | ---: | ---: |
| Scheduled flights | 155 | 235 |
| Completed flights | 146 | 200 |
| Arrival-delay rate | 36.30% | 40.00% |
| Cancellation rate | 5.81% | 14.47% |
| Diverted flights | 0 | 1 |

Arrival-delay rates use completed flights (neither cancelled nor diverted) as the denominator and define late arrival as `ARR_DELAY >= 15` minutes. Cancellation rates use all scheduled flights as the denominator. These results cover one month and are descriptive comparisons; they do not establish long-term performance or causal effects.

## Run locally

1. Clone this repository and open it in VS Code or another Jupyter-compatible editor.
2. Create a Python environment and install the dependencies:

   ```powershell
   python -m venv .venv
   .\.venv\Scripts\python.exe -m pip install -r requirements.txt
   ```

3. Download July 2026 Reporting Carrier On-Time Performance data from BTS. Select fields matching the columns listed below, extract the CSV, and save it as `data/raw/T_ONTIME_REPORTING.csv`.
4. Open `pynotebooks/flight_analysis.ipynb`, select the `.venv` Python kernel, and run all cells in order. The notebook reads the CSV using a path relative to the `pynotebooks` folder.

<details>
<summary>CSV columns used by this project</summary>

```text
FL_DATE, OP_UNIQUE_CARRIER, OP_CARRIER_FL_NUM, ORIGIN_AIRPORT_ID,
ORIGIN, DEST_AIRPORT_ID, DEST, CRS_DEP_TIME, DEP_TIME, DEP_DELAY,
CRS_ARR_TIME, ARR_TIME, ARR_DELAY, CANCELLED, CANCELLATION_CODE,
DIVERTED, CRS_ELAPSED_TIME, ACTUAL_ELAPSED_TIME, AIR_TIME, DISTANCE,
CARRIER_DELAY, WEATHER_DELAY, NAS_DELAY, SECURITY_DELAY,
LATE_AIRCRAFT_DELAY
```

</details>

## Project structure

```text
Airline_Value_Analysis_Project/
├── data/
│   ├── raw/               # Local BTS CSV; excluded from Git
│   └── processed/         # Local derived data; excluded from Git
├── pynotebooks/
│   └── flight_analysis.ipynb
├── sql/                   # Planned SQL analysis
├── excel/                 # Planned Excel analysis
├── outputs/               # Future charts and summaries
├── README.md
├── requirements.txt
└── .gitignore
```

Empty folders may not appear on GitHub until files are added.

## Next steps

- Compare morning, afternoon, and evening departure reliability.
- Create visualizations and explore additional routes and airports.
- Incorporate ticket-price and customer satisfaction data.
- Extend the workflow with SQL, Excel, and statistical analysis as the project develops.

This project is being built incrementally while learning data science. The notebook records both the analysis and learning progress.
