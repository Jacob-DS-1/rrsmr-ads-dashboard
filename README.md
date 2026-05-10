# RR SMR ADS Dashboard

Frozen Streamlit results dashboard for the RR SMR ADS project.

This repository is dashboard-only. It does not contain the full analysis workflow and does not rerun modelling. The data folder contains compact dashboard-ready extracts generated from a locally audited run of the main reproducibility repository.

Main reproducibility repository:
https://github.com/Jacob-DS-1/rrsmr-ads-public

## Local run

Run:

    python3 -m venv .venv
    source .venv/bin/activate
    pip install -r requirements.txt
    streamlit run app.py

## Streamlit Community Cloud

App entrypoint:

    app.py

Recommended app secret:

    dashboard_password = "your-access-code"

## Data

The dashboard reads from:

    data/

The hourly dashboard extract is stored as a Parquet dataset directory named:

    data/hourly_metrics_dashboard.parquet/

This keeps individual Git files below GitHub's large-file limit while preserving the app's expected path.
