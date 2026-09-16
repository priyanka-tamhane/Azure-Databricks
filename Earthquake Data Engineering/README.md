# 🌎 Earthquake Data Engineering Project using Azure Databricks

A hands-on **Azure Databricks Data Engineering project** that ingests earthquake data from the **USGS Earthquake Catalog API**, processes the data using **PySpark**, and organizes the data using the **Medallion Architecture**.

This project was built with a focus on practical data ingestion, transformation, Delta Lake, and PySpark concepts.

---

## 📌 Project Overview

The project demonstrates how to build a simple end-to-end data engineering pipeline using earthquake data obtained from the **U.S. Geological Survey (USGS)** Earthquake Catalog API.

The pipeline follows a layered architecture:

```text
USGS Earthquake API
        │
        ▼
     Bronze
   Raw API Data
        │
        ▼
      Silver
 Cleaned & Transformed
        │
        ▼
       Gold
  Analytics-Ready Data
```

The USGS Earthquake Catalog API provides earthquake event information and supports querying data using parameters such as time range, magnitude, location, and output format.

---

## 🏗️ Architecture

```text
                    ┌──────────────────────┐
                    │   USGS Earthquake    │
                    │         API          │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │       BRONZE         │
                    │     Raw API Data     │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │       SILVER         │
                    │ Cleaned & Validated  │
                    │    Earthquake Data   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │        GOLD          │
                    │ Analytics / Business │
                    │       Ready Data     │
                    └──────────────────────┘
```

The Bronze/Silver/Gold approach follows the Databricks **Medallion Architecture**, where data progressively becomes more validated, refined, and analytics-ready as it moves through the layers.

---

## 🔄 Data Pipeline

### 1. Data Ingestion

Earthquake data is retrieved from the **USGS Earthquake Catalog API**.

Source:

* USGS Earthquake Catalog
* FDSN Event Web Service
* GeoJSON API response

The API provides earthquake event information such as:

* Earthquake magnitude
* Location
* Geographic coordinates
* Time of occurrence
* Depth
* Place
* Event type
* Event status
* Other earthquake metadata

---

### 2. Bronze Layer 🥉

The Bronze layer stores the **raw API data** with minimal transformation.

Purpose:

* Preserve the original source data
* Provide a reliable raw layer
* Allow data to be reprocessed if transformation logic changes
* Maintain traceability back to the source

```text
USGS API
   ↓
Raw JSON / API response
   ↓
Bronze Delta Table
```

This follows the principle that the Bronze layer should preserve the raw state of source data and act as a foundation for downstream processing.

---

### 3. Silver Layer 🥈

The Silver layer transforms the raw data into a cleaner and more structured dataset.

Typical processing includes:

* Selecting required columns
* Flattening nested JSON structures
* Extracting geographic coordinates
* Converting timestamps
* Handling null values
* Data type conversion
* Filtering invalid records
* Renaming columns for readability

Example:

```text
Bronze
Raw + Nested Data
       │
       ▼
   PySpark
       │
       ▼
Silver
Clean + Structured Data
```

The Silver layer is where data cleansing, validation, normalization, deduplication, and schema handling are typically performed in a Databricks medallion architecture.

---

### 4. Gold Layer 🥇

The Gold layer contains data prepared for analytics and reporting.

Depending on the analysis, this layer can be used to answer questions such as:

* Which locations experienced the strongest earthquakes?
* How many earthquakes occurred during a particular period?
* What is the distribution of earthquake magnitudes?
* Which geographic regions experience more earthquake activity?
* What are the trends in earthquake activity over time?

```text
Silver
   ↓
Aggregation / Business Logic
   ↓
Gold
   ↓
Analytics / Reporting
```

Gold datasets are typically designed around business or analytical requirements and optimized for downstream consumption.

---

# 🛠️ Technologies Used

| Technology                 | Purpose                                  |
| -------------------------- | ---------------------------------------- |
| **Azure Databricks**       | Data engineering and processing platform |
| **Apache Spark / PySpark** | Distributed data processing              |
| **Delta Lake**             | Reliable table storage                   |
| **USGS Earthquake API**    | Data source                              |
| **Python**                 | API interaction and data processing      |
| **SQL / Spark SQL**        | Data querying and analysis               |
| **Medallion Architecture** | Data organization pattern                |

---

# 🧠 Key Data Engineering Concepts Practiced

Through this project, I practiced:

### Data Ingestion

* Consuming REST API data
* Working with JSON/GeoJSON
* Handling semi-structured data

### PySpark

* DataFrame operations
* Selecting and transforming columns
* Filtering records
* Data type conversion
* Working with nested structures
* Aggregations

### Delta Lake

* Creating Delta tables
* Reading and writing Delta data
* Layered data processing

### Medallion Architecture

```text
🥉 Bronze → Raw Data
🥈 Silver → Cleaned Data
🥇 Gold   → Analytics-Ready Data
```

### Data Engineering Workflow

```text
Extract
   ↓
Transform
   ↓
Validate
   ↓
Store
   ↓
Analyze
```

---

# 📊 Example Data Flow

A simplified representation of the processing:

```text
USGS Earthquake API
        │
        │ REST API
        ▼
   JSON / GeoJSON
        │
        ▼
┌─────────────────┐
│ Bronze Layer    │
│ Raw Earthquake  │
│ Data            │
└────────┬────────┘
         │
         │ PySpark
         ▼
┌─────────────────┐
│ Silver Layer    │
│ Cleaned &       │
│ Structured Data │
└────────┬────────┘
         │
         │ Aggregation
         ▼
┌─────────────────┐
│ Gold Layer      │
│ Analytics-Ready │
│ Data            │
└─────────────────┘
```

---

# 🎯 What I Learned

This project helped me understand how the individual concepts I've been learning fit together in a real data engineering workflow.

Some of the key takeaways were:

* How to consume data from a REST API
* How to work with semi-structured JSON data
* How PySpark can process and transform data
* Why a Bronze/Silver/Gold architecture is useful
* How raw data can progressively become analytics-ready
* How Databricks can be used to build an end-to-end data pipeline
* Automate API ingestion using **Databricks Workflows**
  
---

# 📚 References

**USGS Earthquake Catalog API**

https://earthquake.usgs.gov/fdsnws/event/1/

**Databricks Medallion Architecture**

https://docs.databricks.com/aws/en/lakehouse/medallion.html

---

## 🙌 Conclusion

This project was a great hands-on exercise in understanding how a modern cloud data engineering pipeline can be built using **Azure Databricks, PySpark, Delta Lake, and the Medallion Architecture**.

It also helped me move beyond learning individual Databricks features and understand how those concepts come together as an end-to-end data engineering solution.


#Azure #AzureDatabricks #Databricks #DataEngineering #PySpark #ApacheSpark #DeltaLake #Python #ETL #DataEngineer #MedallionArchitecture #BigData #USGS #CloudDataEngineering
