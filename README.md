# Citibike & Weather Data Analysis

This project is part of my **Codecademy Data Engineer Portfolio**.  
It combines Citibike trip data and Newark Airport weather data for 2016, performing:
- Data cleaning and transformation
- Relational database creation in SQLite
- Creation of analytical SQL views for ridership and weather insights

---

## 📂 Folder Structure
├── data
│ ├── processed
│ │ ├── citibike_cleaned.csv
│ │ └── weather_cleaned.csv
│ └── raw
│ ├── JC-201601-citibike-tripdata.csv
│ ├── JC-201602-citibike-tripdata.csv
│ ├── ...
│ └── newark_airport_2016.csv
│
├── notebooks
│ ├── codecademy_citibike_final.ipynb # Data cleaning and transformation
│ └── codecademy_citibike_database_and_views.ipynb # Database creation and SQL views
│
├── src
│ ├── codecademy_citibike_final.py # Python script for cleaning
│ └── codecademy_citibike_database_and_views.py # Python script for DB + views
│
└── README.md # You are here


---

## 🚀 How to Run

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/yourusername/codecademy_citibike_weather_project.git
cd codecademy_citibike_weather_project

2️⃣ Install Dependencies
Make sure you have Python 3.8+ installed, then run:

bash
Copy
Edit
pip install pandas sqlalchemy matplotlib
(You may also need Jupyter if you want to run notebooks)

3️⃣ Open in Jupyter Notebook
bash
Copy
Edit
jupyter notebook
Run notebooks/codecademy_citibike_final.ipynb first to clean and prepare data

Then run notebooks/codecademy_citibike_database_and_views.ipynb to create the database and views

🗄 Database Schema
The database contains three main tables:

stations — station IDs, names, and coordinates

trips — trip-level data including start/end times, distances, speeds

weather — daily weather metrics from Newark Airport

Primary and foreign keys ensure data integrity between tables.

📊 Created SQL Views
1. v_daily_ridership — Daily ride counts and averages

2. v_hourly_ridership — Hourly ride patterns

3. v_station_daily_ridership — Station-level daily usage

4. v_daily_ridership_weather — Weather metrics joined with ridership

5. v_weather_effects — Weather conditions grouped into precipitation buckets

6. v_top_stations — Top stations by ride count

7. v_commute_profile — Commuting behavior trends

📄 Project Write-Up
A detailed explanation of my data cleaning, schema design, and view creation process can be found here:

📜 License
This project is released under the MIT License.
