# Time Series Stock Forecasting & Anomaly Detection

This repository contains a time series analysis project for the **Time Series Analysis** course.  
We use **monthly stock prices (AAPL) from Yahoo Finance** to build, evaluate, and compare forecasting models, and later extend the pipeline with anomaly detection.

## Project Objectives

- Perform end-to-end time series analysis on real financial data.
- Explore and visualise the time series (trend, volatility, seasonality).
- Check stationarity (ADF test) and use ACF/PACF to guide model choice.
- Fit and compare:
  - Classical models: **ARIMA**
  - Modern model: **Prophet**
- Evaluate models using **RMSE, MAE, AIC, BIC**.
- (Next step) Implement **anomaly detection** and study its impact on forecasting performance.

> **Note:** Although the course dataset list includes multiple domains, this project instance uses stock data via the Yahoo Finance API (`yfinance`).

## Dataset

- **Source:** [Yahoo Finance](https://finance.yahoo.com/)
- **Ticker:** `AAPL` (Apple Inc.)
- **Frequency:** Daily prices resampled to **monthly** (last trading day of each month).
- **Variable modelled:** Adjusted close price / close price (column renamed to `y`).

Data is downloaded using `yfinance` in the notebook and saved under `data/raw/`.

## Methods & Workflow

1. **Data Loading & Preprocessing**
   - Download daily OHLCV data using `yfinance`.
   - Resample to monthly series.
   - Handle missing values using forward/backward fill.
   - Save processed series to `data/raw/`.

2. **Exploratory Analysis**
   - Time-series plots for price and monthly aggregated series.
   - Basic statistics (mean, std, min, max).
   - Optional decomposition to inspect trend and potential seasonality.

3. **Stationarity & Autocorrelation**
   - **ADF test** to check stationarity.
   - First differencing to stabilise the series.
   - **ACF/PACF** plots to understand autocorrelation structure and guide ARIMA orders.

4. **Forecasting Models**
   - **ARIMA(p, d, q)**:
     - Baseline models including the random walk ARIMA(0,1,0).
     - Additional models such as ARIMA(1,1,1) for comparison.
   - **Prophet**:
     - Fitted on the monthly price series.
     - Generates trend-aware forecasts with uncertainty intervals.

5. **Model Evaluation**
   - Train/test split (last 12 months as test set).
   - Metrics:
     - **RMSE** (Root Mean Squared Error)
     - **MAE** (Mean Absolute Error)
     - **AIC / BIC** (for ARIMA)
   - Visual comparison of:
     - Train vs Test (actual)
     - ARIMA forecast vs actual
     - Prophet forecast vs actual

6. **(Planned) Anomaly Detection**
   - Statistical methods (e.g. Z-score on returns, ARIMA residuals).
   - ML-based method (e.g. Isolation Forest on returns).
   - Re-forecasting after cleaning anomalies and comparing performance.

## Repository Structure

```text
.
├─ data/
│  ├─ raw/          # downloaded and saved stock time series (e.g. aapl_monthly.csv)
│  └─ processed/    # (optional) cleaned / transformed versions
├─ notebooks/
│  └─ 01_stock_forecasting.ipynb   # main notebook with full pipeline
├─ src/             # (optional) reusable helper functions
├─ README.md
└─ requirements.txt
