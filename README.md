# AAPL Stock Price Forecasting with Time Series Models

A personal project applying classical time series forecasting techniques to 5 years of Apple Inc. (AAPL) monthly stock data — comparing 8 models, from naive baselines to ARIMA/SARIMA to lagged regression, to see which one actually predicts best.

## Overview

Stock price forecasting is a classic time series problem: can past prices tell you anything useful about future ones? This project explores that question end-to-end — from raw data cleaning through exploratory analysis, decomposition, model building, and forecast evaluation — using AAPL's monthly closing price as the test case.

**Forecast horizon:** 6 months ahead

## Dataset

- **Source:** [NASDAQ](https://www.nasdaq.com/market-activity/stocks/aapl/historical) historical stock data
- **Range:** January 2021 – January 2026 (5 years), resampled to monthly frequency using the last trading day's close price
- **Size:** 61 monthly observations
- **Split:** 80/20 train-test (54 training / 6 test observations)

## Methods

**Exploratory analysis & decomposition**
- Descriptive statistics and visualization
- Additive vs. multiplicative seasonal decomposition (trend, seasonal, residual)

**Baseline & smoothing models**
- Naive method
- Average historical method
- Simple average method
- Moving average
- Single Exponential Smoothing (SES)
- Holt's Linear Trend
- Holt-Winters

**Statistical time series models**
- Augmented Dickey-Fuller (ADF) test for stationarity, with differencing
- ACF/PACF analysis to identify model order
- ARIMA, selected via AIC grid search
- SARIMA, for comparison against seasonal effects

**Regression-based approach**
- Time series regression using lagged closing prices (lag-1, lag-2) as predictors
- OLS coefficient analysis and residual diagnostics

All models were evaluated and compared using **MAE**, **RMSE**, and **MAPE**.

## Key Finding

The simplest model won. A regression using only the **previous month's closing price** outperformed every other model, including ARIMA and SARIMA, with the lowest RMSE of the group.

This points to AAPL's monthly price behaving close to a **random walk** — most of the predictive signal for next month is already contained in this month's price, leaving little room for more complex models to add value. A good reminder that model complexity should be justified by the data, not assumed.

## Tech Stack

- Python
- pandas, numpy
- statsmodels (decomposition, ADF test, ARIMA/SARIMA, OLS regression)
- matplotlib

## Repository Structure
