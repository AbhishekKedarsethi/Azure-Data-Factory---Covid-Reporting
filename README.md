# 🌐 End-to-End Azure Data Engineering Pipeline for COVID-19 Analytics

## 📑 Table of Contents
- [Overview](#overview)
- [Tools ⚙](#tools-)
- [Environment Setup](#environment-setup)
- [Architecture](#architecture)
- [📥 Data Extraction & Ingestion](#-data-extraction--ingestion)
- [📦 Copy Activity](#copy-activity)
- [⚙️ Data Ingestion Pipeline](#️-data-ingestion-pipeline)
- [🔄 Data Transformation](#-data-transformation)
- [🔥 Azure Databricks Activity](#-azure-databricks-activity)
- [📤 Copy Data to Azure SQL](#copy-data-to-azure-sql)
- [📊 Reporting with Power BI](#-reporting-with-power-bi)

---

## 🧾 Overview
This repository showcases a comprehensive end-to-end **data engineering solution** built on **Azure**. The project integrates various Azure services to orchestrate, transform, and visualize data. Key services used:
- **Azure Data Factory (ADF)** for orchestration  
- **Azure Databricks** for transformation using PySpark  
- **Power BI** for visualization  

---

## ⚙ Tools

#### 🔗 Data Integration/Ingestion
- ADF Data Flows within Azure Data Factory

#### 🔄 Transformation
- Azure Data Factory Data Flows
- Azure Databricks (PySpark)

#### 🏢 Data Warehouse Solution
- Azure SQL Database

#### 📊 Visualization
- Power BI Desktop
- Power BI Service

---

## 🏗 Environment Setup
- Azure Subscription  
- Azure Data Factory  
- Azure Blob Storage Account  
- Azure Data Lake Storage Gen2  
- Azure SQL Database  
- Azure Databricks Cluster  

---

## 📐 Architecture
![Alt Text](https://github.com/AbhishekKedarsethi/Azure-Data-Factory---Covid-Reporting/blob/bc15f8e1d8f9a572ecbfb5d9e4a5da4c3eb09955/images/Architecture.png)

<img src="images/architecture.png" alt="Data Pipeline Architecture" width="700"/>

---

## 📥 Data Extraction & Ingestion

#### 📚 Datasets Ingested
- **Cases and Deaths Data** – Daily COVID-19 cases and fatalities across EU.
- **Hospital Admissions Data** – Hospitalization and ICU admissions by date/country.
- **Population Data** – Age-wise population stats for EU nations.
- **Tests Conducted Data** – Historical COVID-19 testing records.

#### 🔄 Ingestion Methodology
Used **Azure Data Factory** pipelines to automate extraction and ingestion:
- Sources: HTTP endpoints and Blob Storage
- Destination: Azure Data Lake Storage Gen2 (Bronze Layer)

#### ⚙️ ADF Activities Used
- **Validation Activity**
- **Get Metadata Activity**
- **Copy Activity**

##### 📌 Example: Population Data Ingestion
Population dataset supports demographic analysis and mortality prediction modeling across EU.

---

## 📦 Copy Activity
Used for reliable and performant data movement from source to Data Lake using **ADF Copy Activity**.

![Alt Text](https://github.com/AbhishekKedarsethi/Azure-Data-Factory---Covid-Reporting/blob/bc15f8e1d8f9a572ecbfb5d9e4a5da4c3eb09955/images/Copy_Activity.png)


---

## ⚙️ Data Ingestion Pipeline – Step-by-Step

1. **Create Linked Service** to Azure Blob Storage  
2. **Create Source Dataset** (define schema & format)  
3. **Create Linked Service** to Data Lake Storage Gen2  
4. **Create Sink Dataset**  
5. **Build Pipeline** with:
   - Get Metadata Activity
   - If Condition Activity
   - Copy Activity  
6. **Load Data** into Azure Data Lake  
7. **Configure Trigger** (Daily/Hourly)

This structure was replicated across all datasets for uniform ingestion.

---

## 🔄 Data Transformation

#### Dataset: **Cases and Deaths**

1. Load from Azure Data Lake Gen2  
2. Filter for European countries  
3. Select key columns (country, date, indicator)  
4. Pivot ‘indicator’ column to create **cases** and **deaths** columns  
5. Lookup country codes (2-digit & 3-digit)  
6. Select final columns  
7. Save to Silver Layer  
8. Schedule pipeline trigger  

---

#### Dataset: **Hospital Admissions**

##### 📆 Weekly Path – Admissions Per 100k

- Filter by indicators:  
  - *Weekly new hospital admissions per 100k*  
  - *Weekly new ICU admissions per 100k*  
- Join with date dimension  
- Pivot & aggregate weekly data  
- Sort by week/country  
- Save to Azure Data Lake (Silver Layer)

##### 🗓️ Daily Path – Hospital & ICU Occupancy

- Filter indicators:  
  - *Daily hospital occupancy*  
  - *Daily ICU occupancy*  
- Pivot columns, sort data, and save final output  
- Configure scheduled trigger

---

## 🔥 Azure Databricks Activity

Used **Databricks Notebooks** within ADF to perform Spark-based scalable transformation.

#### Steps:
1. **Create Linked Service** to Databricks  
2. **Develop Notebook** with transformation logic  
3. **Create Pipeline** and add Databricks Activity  
4. **Configure error handling** with If/Else or failure paths  
5. **Automate** using scheduled or event-based triggers  

---

## 📤 Copy Data to Azure SQL

Data from Azure Data Lake Gen2 was transferred to Azure SQL for analytics and BI reporting.

### Pipeline Steps:
1. **Linked Service** to Azure Storage (source)  
2. **Source Dataset** definition  
3. **Linked Service** to Azure SQL  
4. **Sink Dataset** configuration  
5. **Build pipeline** to load validated data  
6. **Scheduled Trigger** for automation  

---

## 📊 Reporting with Power BI

Final layer of the pipeline enables dynamic reporting on transformed datasets.

#### 📈 Reporting Workflow:

1. **Connect to Azure SQL Database**  
2. **Data Analysis & Aggregation**  
   - Total cases, deaths  
   - Breakdown by country and time  
3. **Create Dashboards**:
   - Daily/weekly trends  
   - Hospitalization peak periods  
   - Regional comparisons  
4. **Publish to Power BI Service**  
5. **Optional: Enable "Publish to Web"** for embedding in external platforms  

---

## 📌 Summary
This project is a robust, production-style Azure-based **Data Engineering** workflow—from raw data ingestion to final dashboarding—ideal for real-world COVID-19 analytics.

---

>   
> [LinkedIn](https://in.linkedin.com/in/abishek-kedarsethi)
> 🧠 **Tools:** Azure Data Factory | Azure Databricks | Power BI | Azure SQL | Data Lake

---

