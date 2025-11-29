# Portugal Property Price Dynamics (2022-2024) - End-to-End ELT Project

## 🛠️ Tech Stack Badges
[![Data Warehouse: Snowflake](https://img.shields.io/badge/Data%20Warehouse-Snowflake-blue?style=flat-square&logo=snowflake&logoColor=white)](https://www.snowflake.com/)
[![ELT/Modeling: dbt](https://img.shields.io/badge/ELT%20&%20Modeling-dbt-orange?style=flat-square&logo=dbt&logoColor=white)](https://www.getdbt.com/)
[![Cloud Platform: Google Cloud](https://img.shields.io/badge/Cloud%20Platform-Google%20Cloud-yellow?style=flat-square&logo=google-cloud&logoColor=white)](https://cloud.google.com/)
[![Visualization: Looker](https://img.shields.io/badge/Visualization-Looker-green?style=flat-square&logo=google-data-studio&logoColor=white)](https://cloud.google.com/looker-studio)
[![Language: SQL](https://img.shields.io/badge/Language-SQL-grey?style=flat-square&logo=postgresql&logoColor=white)](https://en.wikipedia.org/wiki/SQL)

## 🌟 Overview
This project is a comprehensive **End-to-End ELT (Extract, Load, Transform) pipeline** and data analysis focused on **Portuguese real estate listings** from 2022 to 2024. 

The primary goal was to showcase a modern data stack workflow—from raw data ingestion in the cloud to final, interactive data visualization—to derive actionable insights into property price changes and key market trends across different property categories (Houses, Apartments, Land).

### 🚀 What this project shows
- Cloud data ingestion (GCS + BigQuery)  
- Cross-cloud data migration → Snowflake  
- 3-layer architecture (Staging → Cleaned → Analytics)  
- Full dbt implementation (stg / int / mart, macros, tests, documentation)  
- Kimball dimensional modeling (star schema)  
- Interactive Looker dashboard with YoY trends & KPIs

## ⚙️ Core Technology Details

| Category | Tool/Service | Purpose |
| :--- | :--- | :--- |
| **Data Ingestion** | Google Cloud Storage (GCS) & BigQuery | Initial storage of raw CSV data and facilitating the initial connection/access. |
| **Data Warehouse** | Snowflake | Centralized data storage, serving as the raw, staging, and final analytics environment. |
| **Transformation (ELT)** | dbt (data build tool) | Data modeling, implementing cleaning logic (standardization, deduplication), and enforcing data quality through tests. |
| **Visualization** | Looker | Creating the final, interactive dashboard with KPIs and trend analysis. |

## 🏗️ Data Architecture (ELT Pipeline)

The project follows a robust, layered approach within the Snowflake Data Warehouse, modeled using dbt (data build tool):

1.  **Extract & Load (Raw Layer):** Raw, unprocessed data is loaded into a dedicated schema in Snowflake (The data was initially accessed from GCS/BigQuery).
2.  **Staging Layer (`stg`):** Basic cleaning steps are applied, including selecting necessary columns, type casting, and renaming fields for consistency.
3.  **Intermediate Layer (`int`):** Complex business logic is applied here, such as:
    * Deduplication of listings.
    * Standardizing categorical text fields (e.g., property categories, conservation status).
    * Calculating derived fields (e.g., price per square meter).
4.  **Marts Layer (`mart`):** Final, aggregated, and fact tables are created. These tables are optimized and ready for consumption by the Looker BI tool.

### 📊 Key Insights (2022–2024)
- National average house price rose from €237K → €401K (+69%)  
- Apartment prices actually fell from €511K → €352K (-31%)  
- Lisboa remains the most expensive district (€508K avg)  
- Weak price–bedroom correlation (0.28) → location > size
  
## 🔗 **View the Live Dashboard on Looker** \[*[Dashboard Here](https://lookerstudio.google.com/reporting/ad129fa3-88c9-4850-8969-fab8c1e4e6a7)*]

## 📁 Repository Structure


```
portugal-real-estate-analysis/
│
├── .gitattributes
├── Graph.png
├── INT_DEDUPLICATED_PROPERTIES.csv
├── INT_IMPUTE_BEDROOMS_WC.csv
├── STG_RAW_PROPERTY_LISTINGS;.csv
├── dim_date.csv
├── dim_listing_attributes.csv
├── dim_location.csv
├── dim_property.csv
├── fact_listing.csv
├── kpi_properties_summary.csv
└── raw_portugal_listings.csv
```
