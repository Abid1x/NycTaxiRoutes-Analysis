## Project Overview

This project implements an end-to-end **big data engineering pipeline** on the Databricks platform, 
ingesting raw NYC taxi trip data, enforcing schema integrity, applying multi-stage transformations, 
and surfacing actionable geospatial and temporal analytics — all without a single line of raw SQL. 
Pure Spark. Pure DataFrame API.

The dataset includes pick-up/drop-off timestamps, location IDs, trip distances, fare amounts, 
payment types, and passenger counts — joined against a NYC Taxi Zone Lookup Table to map raw 
location IDs to real-world borough and zone names.

---

## Skills & Tools

![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=flat&logo=databricks&logoColor=white)
![PySpark](https://img.shields.io/badge/PySpark-E25A1C?style=flat&logo=apachespark&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonaws&logoColor=white)
![Amazon S3](https://img.shields.io/badge/Amazon_S3-569A31?style=flat&logo=amazons3&logoColor=white)
![Amazon Athena](https://img.shields.io/badge/Amazon_Athena-232F3E?style=flat&logo=amazonaws&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)

| Domain | Stack & Skills |
|---|---|
| **Distributed Compute** | Apache Spark on Databricks, cluster orchestration, in-memory distributed processing across partitioned RDDs |
| **Cloud Infrastructure** | AWS S3 for data lake storage, Amazon Athena for serverless SQL querying, cloud-native DBFS integration |
| **Data Ingestion** | Schema inference at read-time, CSV parsing at scale, DBFS file management, fault-tolerant data loading |
| **Pipeline Design** | End-to-end modular ETL architecture — Extract → Transform → Aggregate → Serve |
| **Spark DataFrame API** | `groupBy`, `agg`, `orderBy`, `filter`, `join`, `window()`, `partitionBy`, `withColumn`, `toDF` |
| **Window & Ranking Functions** | Partition-aware ranking, lag/lead operations, dense rank for tie-breaking at scale |
| **Geospatial Enrichment** | LocationID → Borough/Zone resolution via broadcast join against NYC Taxi Zone Lookup Table |
| **Temporal Feature Engineering** | Day-of-week extraction, hourly bucketing, month-level filtering, multi-year aggregation |
| **Data Cleaning & QA** | Type casting, null handling, predicate pushdown filtering, output validation against expected schema |
| **Libraries** | PySpark, Pandas, Datetime, OS |

---

## Key Engineering Decisions

- **Pure DataFrame API** — zero raw SQL (`spark.sql()` not used), enforcing programmatic, testable transformation logic
- **Schema inference at ingestion** — flexible loading with post-ingestion type casting
- **Window functions** for rank-based filtering without reducing dataset granularity
- **Broadcast joins** implicitly leveraged for the small lookup table enrichment
- **Tie-breaking determinism** — all rankings use secondary sort keys for reproducibility
