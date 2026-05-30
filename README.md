# Energy Data Analytics Pipeline

An end-to-end ELT data pipeline analyzing energy production, revenue,
efficiency, and CO2 emissions across 50 power plants, 8 energy sources,
and 365 days of operational data.

## Pipeline Summary
- **Total Records Processed:** 18,250
- **Power Plants:** 50
- **Days of Data:** 365
- **Total Production:** 267.7 TWh
- **Total Revenue:** $18.70B
- **Total CO2 Emissions:** 56.96M tons
- **Avg Efficiency:** 80.33%
- **Anomalies Detected:** 89

## Dashboard Visualizations
![Energy Pipeline Dashboard](energy_pipeline_dashboard.png)

## ELT Pipeline Architecture

### Stage 1: EXTRACT
- Data extraction from 50 power plants
- Missing value validation (0 missing)
- Duplicate detection (0 duplicates)
- Raw data saved to SQLite database

### Stage 2: LOAD (Staging)
- Raw data loaded to staging tables
- 18,250 records staged successfully

### Stage 3: TRANSFORM
- Date feature engineering (year, month, quarter)
- KPI calculation (profit margin, cost/MWh, revenue/MWh)
- Anomaly detection using Z-score (89 anomalies found)
- Rolling averages (7-day, 30-day)
- Renewable vs non-renewable classification

### Stage 4: LOAD (Analytics)
- Transformed data loaded to analytics tables
- Daily summary table (10,950 rows)
- Monthly summary table (104 rows)

## Energy Sources Analyzed
| Source | Type | Avg CO2 (tons/MWh) |
|---|---|---|
| Solar | Renewable | 0.00 |
| Wind | Renewable | 0.00 |
| Nuclear | Low Carbon | 0.00 |
| Hydro | Renewable | 0.01 |
| Geothermal | Renewable | 0.05 |
| Biomass | Renewable | 0.23 |
| Natural Gas | Non-Renewable | 0.45 |
| Coal | Non-Renewable | 0.82 |

## Technologies
- Python, Pandas, NumPy
- SQLite (ELT Pipeline Storage)
- Matplotlib, Seaborn
- Apache Airflow (Scheduling)
- Google Colab (T4 GPU)
