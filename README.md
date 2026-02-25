# air-quality-insights-berlin-open-meteo
# Air Quality & Weather Insights with Open‑Meteo

This project is an end‑to‑end data analysis pipeline that pulls **real‑time air quality and weather data** from the free [Open‑Meteo APIs][web:33][web:32], stores it in a tabular structure, performs exploratory analysis, and generates simple data quality and health‑risk indicators.

The goal is to **showcase practical data engineering and data science skills**:

- Connecting to real‑world **public APIs** (no API key required)
- Building a **reproducible data pipeline** in Python / Google Colab
- Performing **data cleaning, feature engineering, and EDA**
- Producing **insights and visualizations** that could be used in a dashboard
- Structuring the work for **professional presentation on GitHub**

Although the examples focus on **Berlin, Germany**, the pipeline can easily be parameterized for any city by changing a few coordinates.

---

## Features

- Fetches **hourly air quality data** (PM2.5, PM10, ozone, NO2, SO2, etc.) via the Open‑Meteo Air Quality API. [web:33]
- Fetches **hourly weather data** (temperature, relative humidity, wind speed, precipitation) via the Open‑Meteo Weather API. [web:32]
- Merges air quality and weather into a single **time‑series dataset**.
- Computes simple **derived metrics**:
  - Approximate AQI bucket (Good / Moderate / Unhealthy) based on PM2.5.
  - “Discomfort index” combining temperature and humidity.
- Performs **basic EDA**:
  - Summary statistics
  - Correlation between pollution and weather variables
  - Simple plots (time series of PM2.5, comparison by hour of day)
- Designed to run **end‑to‑end in Google Colab** with minimal setup.

---

## Tech Stack

- **Python 3**
- **Google Colab** (runs out‑of‑the‑box)
- `requests` for API calls
- `pandas` / `numpy` for data wrangling
- `matplotlib` / `seaborn` for visualization

---

## Architecture Overview

1. **Data Ingestion**  
   Call Open‑Meteo’s REST APIs for:
   - Air quality: hourly pollutants (PM2.5, PM10, NO2, O3, etc.) [web:33]  
   - Weather: hourly temperature, humidity, wind speed, etc. [web:32]

2. **Data Processing**  
   - Convert JSON responses into pandas DataFrames.
   - Join air quality and weather data on timestamp.
   - Handle missing values and basic type conversions.

3. **Feature Engineering & Analysis**  
   - Compute derived metrics (e.g., AQI bucket based on PM2.5).
   - Aggregate statistics (daily averages, variability).
   - Visualize time‑series patterns.

4. **Outputs**  
   - Cleaned CSV dataset.
   - PNG charts.
   - Notebook with analyses and commentary.
## Data Sources

This project uses **live public APIs**:

1. **Open‑Meteo Air Quality API** (no API key) [web:33]  
   - Provides hourly forecasts of pollutants such as **PM2.5, PM10, ozone, NO2, SO2, CO**.
   - Endpoint example:  
     `https://air-quality-api.open-meteo.com/v1/air-quality?latitude=52.52&longitude=13.405&hourly=pm2_5,pm10,ozone, ...`

2. **Open‑Meteo Weather API** (no API key) [web:32]  
   - Provides hourly weather variables such as **temperature, humidity, wind speed, precipitation**.
   - Endpoint example:  
     `https://api.open-meteo.com/v1/forecast?latitude=52.52&longitude=13.405&hourly=temperature_2m,relative_humidity_2m,...`

Both APIs are **free for non‑commercial use**, and designed for reproducible research and data science demos.
