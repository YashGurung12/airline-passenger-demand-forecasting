# Airline Passenger Demand Forecasting & Granularity Analysis

## 📌 Project Overview
This project presents an end-to-end time series analysis and forecasting framework using the classic **Airline Passengers dataset (1949–1960)**. The primary objective is evaluating multi-frequency resampling techniques—converting low-frequency monthly aggregate data into high-frequency daily and hourly granularities—and building robust statistical models to forecast future passenger demand.

---

## 🎯 Business Objectives & Problem Statement
Airlines operate across multiple temporal horizons:
- **Executive & Strategic Teams:** Require monthly and annual long-term growth forecasts for fleet allocation and capacity planning.
- **Ground & Flight Operations:** Require daily and hourly volume estimates for airport staffing, gate management, and fuel distribution.

### Key Objectives:
1. **Resampling Analysis:** Evaluate forward-fill (`ffill`) and linear interpolation (`interpolate`) methods for converting monthly data into daily (`D`) and hourly (`h`) granularities.
2. **Visual Assessment:** Analyze signal-to-noise ratio and visual clutter when displaying high-frequency interpolated data over long-term temporal horizons.
3. **Time Series Forecasting:** Implement and compare statistical forecasting models (Moving Average, Holt-Winters Exponential Smoothing, ARIMA) using standardized evaluation metrics.

---

## 📊 Dataset Overview
- **Dataset Name:** Box-Jenkins AirPassenger Dataset
- **Timeframe:** 1949 – 1960 (12 Years / 144 Monthly Observations)
- **Primary Metric:** Passengers (in Thousands)
- **Key Characteristics:** Strong upward linear trend with expanding annual multiplicative seasonality.

---

## 🛠️ Resampling Implementation

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load dataset and set datetime index
df = pd.read_csv('data.csv', parse_dates=['Year-Month'], index_col='Year-Month')

# Monthly to Daily Forward-Fill
df_daily = df.resample('D').ffill()

# Monthly to Hourly Linear Interpolation
df_hourly = df.resample('h').interpolate()