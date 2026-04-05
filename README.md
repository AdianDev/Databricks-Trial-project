# Databricks-Assignment_Synapx

# Healthcare FHIR Data Pipeline — Medallion Architecture

## 📌 Overview

This project implements an end-to-end data pipeline using the **Medallion Architecture (Raw → Bronze → Silver → Gold)** to ingest, transform, and model Healthcare FHIR data.
The pipeline processes paginated API data for multiple days and builds analytics-ready fact and dimension tables in the Gold layer.

---

## 🏗️ Architecture

The pipeline follows the Medallion Architecture:

```
Raw (API JSON)
    ↓
Bronze (Flattened ingestion)
    ↓
Silver (Cleaned & normalized)
    ↓
Gold (Star schema for analytics)
```

---

## 📥 Data Ingestion

* Source: FHIR REST API
* Pagination supported
* Ingests **2–3 days of data**
* Raw JSON stored before transformation

---

## 🥉 Bronze Layer

**Purpose:** Store flattened raw ingestion data

Features:

* Minimal transformation
* Metadata columns added
* Preserves source structure
* Supports replayability

---

## 🥈 Silver Layer

**Purpose:** Clean and normalize data

Features:

* Deduplication
* Standardized column names
* Data type casting
* SCD handling (where applicable)
* Business logic transformations

Tables:

* silver.fhir.patient
* silver.fhir.encounter
* silver.fhir.condition
* silver.fhir.observation

---

## 🥇 Gold Layer (Star Schema)

**Purpose:** Analytics-ready dimensional model

### Dimension Tables

* dim_patient
* dim_encounter

### Fact Tables

* fact_encounter
* fact_condition *(optional encounter FK)*
* fact_observation

---

## 🔗 Relationships

* One Patient → Many Encounters
* One Patient → Many Conditions
* One Patient → Many Observations
* One Encounter → Many Conditions *(optional)*
* One Encounter → Many Observations

---

## 🧾 Metadata & Versioning

Metadata fields added across layers:

* is_current
* effective_start_date
* effective_end_date
* last_updated
* extraction_timestamp
---

## 📊 ER Diagram

Gold layer ER model preview: 
<img width="1402" height="1121" alt="Gold ER model diagram" src="https://github.com/user-attachments/assets/1f649022-379a-49f0-b93c-936b9ec2e255" />

---

## ⚙️ Tech Stack

* PySpark
* Delta Lake
* Databricks / Spark environment
* REST API ingestion
* Medallion Architecture
* Star Schema Modeling


## ▶️ Execution Order

Run notebooks in this order:

1. Raw Ingestion
2. Bronze Layer
3. Silver Layer
4. Gold Layer

---

## ✅ Submission Checklist

* ✔ Ingested 2–3 days of data with pagination
* ✔ Implemented Medallion Architecture
* ✔ Added metadata and versioning
* ✔ Modular reusable code
* ✔ Star schema Gold model
* ✔ ER Diagram included

---

## 👤 Author

**Avnish Devshali**

---

## 📎 Notes

* fact_condition has **nullable encounter relationship**
* All Gold tables stored as Delta format
* Schema overwrite enabled for evolution


                 
