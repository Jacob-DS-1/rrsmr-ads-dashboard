# RR SMR ADS Dashboard

Public Streamlit dashboard for exploring the modelled GB grid impact of integrating three Rolls-Royce SMR units at Wylfa under a set of demand, weather, and deployment scenarios.

The live dashboard is available here:

https://rrsmr-ads-dashboard-hu9hhjxrc7qrpjvjedde8l.streamlit.app

## What this repository contains

This repository contains the dashboard application and the compact, dashboard-ready data extracts used by the app.

It is designed for presentation, review, and exploration of final model outputs. It does not contain the full modelling workflow and does not regenerate the underlying analysis.

The full reproducibility repository is here:

https://github.com/Jacob-DS-1/rrsmr-ads-public

## What the dashboard shows

The dashboard presents scenario comparisons for the potential contribution of three SMR units to the GB electricity system, including:

- annual SMR generation and gas displacement proxy results
- residual demand before and after SMR output
- low-wind stress-case behaviour
- surplus and curtailment-risk proxy hours
- differences between staggered and simultaneous SMR commissioning assumptions
- downloadable dashboard-ready summary tables

The dashboard is intended to support interpretation of the results, not to act as a full dispatch model or market forecast.

## Scenario dimensions

The dashboard lets the user compare results across four main dimensions:

- FES pathway — the Future Energy Scenarios pathway used to anchor demand and supply assumptions.
- Demand climate scenario — selected UKCP18-based climate realisations used to shape demand.
- Supply/weather case — average-wind, low-wind, and high-wind supply-side weather cases.
- SMR deployment case — staggered commissioning as the central case, with simultaneous commissioning as a stress-test sensitivity.

## Data included

The app reads from the data directory.

Key dashboard inputs include:

- annual_summary.csv
- period_summary.csv
- low_wind_case_study_selection_rankings.csv
- low_wind_case_study_pressure_day.csv
- qa_checks.csv
- sensitivity_definitions.csv
- smr_assumptions.csv
- hourly_metrics_dashboard.parquet/

The hourly dataset is stored as a partitioned Parquet directory:

    data/hourly_metrics_dashboard.parquet/

This keeps individual files small enough for GitHub while preserving efficient loading in the Streamlit app.

## Running locally

From the repository root:

    python3 -m venv .venv
    source .venv/bin/activate
    pip install -r requirements.txt
    streamlit run app.py

The app entrypoint is:

    app.py

## Repository structure

    .
    ├── app.py
    ├── requirements.txt
    ├── README.md
    ├── README_upstream_dashboard.md
    ├── dashboard_data_dictionary.md
    └── data/
        ├── annual_summary.csv
        ├── period_summary.csv
        ├── low_wind_case_study_selection_rankings.csv
        ├── low_wind_case_study_pressure_day.csv
        ├── qa_checks.csv
        ├── sensitivity_definitions.csv
        ├── smr_assumptions.csv
        └── hourly_metrics_dashboard.parquet/

## Notes on interpretation

This dashboard presents a frozen set of model outputs. It is intended for transparent exploration of scenario results and assumptions.

The gas displacement metric is a simplified proxy based on changes in residual demand after SMR output. It should not be interpreted as a full power-market dispatch result.

Surplus hours are also a proxy. They indicate periods where modelled residual demand after SMR output falls below zero, but they do not represent a full curtailment optimisation.

## Related repository

The dashboard data was generated from the main reproducibility workflow:

https://github.com/Jacob-DS-1/rrsmr-ads-public
