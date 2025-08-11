# Citibike Data Engineering & Analysis Project

## Overview
This project ingests, cleans, and stores Citibike trip and weather data in a relational SQLite database, then creates analytical views to support exploratory data analysis.  
It was completed in Google Colab as part of the Codecademy Data Engineer Career Path.

### Objectives
- **Data Cleaning** – Prepare cleaned Citibike trip and Newark weather data for reliable loading into a database.
- **Database Creation** – Design and build a relational SQLite schema with appropriate foreign key relationships.
- **View Population** – Implement six structured, reusable views to join and summarize project-specific metrics.
- **Project Insight** – Create SQL views that merge trips, bike stations, and weather metrics for exploration.

---

## Data Sources
- **Citibike** – Monthly .csv trip-level data with station IDs, timestamps, user demographics, and calculated trip metrics (duration, distance, speed, etc.).
- **Weather** – Daily weather data including temperature, precipitation, wind speed, and snowfall.

Both datasets were pre-cleaned in a separate step and stored on Google Drive.

---

## Tech & Tools
- **Languages**: Python, SQL
- **Database**: SQLite (via SQLAlchemy)
- **Libraries**: pandas, numpy, matplotlib
- **Environment**: Google Colab
- **Storage**: Google Drive

---

## Process

### 1. Mount Google Drive and Load Data
- Cleaned CSVs are read into `pandas` DataFrames with appropriate parsing for dates and times.

### 2. Data Preparation
- **Stations**: Merged start and end station records, removed blanks, standardized names, and consolidated duplicates by station ID.
- **Trips**: Selected relevant columns, coerced to correct data types, converted flags to booleans, normalized dates.
- **Weather**: Filtered to expected column values, added missing columns as `NaN`, corrected data fields.

### 3. Database Schema
**Tables:**
- `stations`: one row per station ID, name, latitude, longitude.
- `trips`: trip-level details, foreign keys to `stations` table.
- `weather`: daily weather observations.

All tables have primary keys; trips enforce foreign key constraints to `stations`.

---

## 4. Table Creation
- Existing tables are truncated in dependency order:
    1. `trips` (child table)
    2. `stations` (parent)
    3. `weather` (standalone)

---

## 5. Data Loading
- Pandas DataFrames load into SQLite using `.to_sql()` with explicit `dtype` mapping, multi-row inserts, and chunking for performance.

---

## 6. Analytical Views
Seven SQL views were created:
1. **v_daily_ridership** – Rides per date, average duration, and speed.
2. **v_hourly_ridership** – Hour-by-hour ride counts by day.
3. **v_station_daily_ridership** – Daily counts by start station.
4. **v_daily_ridership_weather** – Merges ridership metrics with weather.
5. **v_weather_effects** – Groups rides into precipitation buckets.
6. **v_top_stations** – Top stations by ride volume (start + end counts).
7. **v_commute_profile** – Commute hour trends, weekdays vs weekends.

---

## 7. View Testing
- Verified row counts and sample outputs for accuracy.
- Queried each view with `LIMIT 10` for quick inspection.

---

## File Structure
- **`notebooks/`** – Jupyter notebooks for data cleaning and preparation.
- **`src/`** – Python scripts for data cleaning, DB creation, and view definitions.
- **`data/`** – Raw and processed datasets.

---

## Next Steps
- Add indexes on high-usage columns (`start_station_id`, `end_station_id`, `start_date`) to improve query performance.
- Expand views to include monthly/seasonal trends for visualization.
- Extend weather analysis to seasonal patterns.

---

**Author:** Shaun  
**Course:** Codecademy Data Engineer Career Path
