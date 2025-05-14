# Data Engineering Project on COVID-19 Reporting using Azure Data Factory

![Project Banner](https://your-image-link.com/banner.png)

## 📌 Project Overview

This project demonstrates how to build an end-to-end data engineering solution for COVID-19 reporting using various Azure services. It involves ingesting, transforming, and visualizing COVID-19 data from the ECDC (European Centre for Disease Prevention and Control) and Eurostat (population data). The final output is a Power BI dashboard for analytics and reporting.

---

## 🔧 Tools & Technologies Used

- **Azure Data Factory**
- **Azure Blob Storage**
- **Azure Data Lake Storage Gen2**
- **Azure SQL Database**
- **Azure HDInsight**
- **Azure Databricks (PySpark)**
- **Power BI Desktop & Power BI Service**

---

## 📁 Folder Structure

├── ecdc_data/ # Raw data from ECDC
├── eurostat_data/ # Population data from Eurostat
├── raw/ # Unprocessed raw data
├── processed/ # Cleaned & transformed data
├── lookup_data/ # Lookup files for transformation
├── sql_scripts/ # SQL scripts for Azure SQL Database
├── pyspark_notebooks/ # PySpark notebooks for Databricks
├── hdinsight_scripts/ # Scripts used in HDInsight
├── powerbi_reports/ # Power BI dashboard files
├── Screenshots/ # Screenshots of ADF pipelines and visuals


---

## 🛠️ Data Engineering Workflow

### 1. **Data Ingestion**

- COVID-19 data is ingested from the [ECDC official website](https://www.ecdc.europa.eu/en).
- Population data is downloaded from [Eurostat](https://ec.europa.eu/eurostat).
- Azure Data Factory pipelines use **Copy Activity** to load raw CSV files into Azure Blob Storage.

![Data Ingestion Pipeline](Screenshots/ecdc_pipeline.png)

---

### 2. **Data Validation and Processing**

- **Get Metadata**, **Filter**, and **If Condition** activities are used to validate datasets.
- Data is passed through Azure Data Lake and transformed using:
  - **Azure HDInsight** (Hive scripts)
  - **Azure Databricks** (PySpark)
  - **ADF Mapping Data Flows**

![Data Flow Pipeline](Screenshots/dataflow_pipeline.png)

---

### 3. **Data Transformation**

- Pivoting and filtering operations are performed using Data Flow in ADF.
- Lookup tables are joined to enrich the dataset.
- Processed data is loaded to **Azure SQL Database** for querying.

![Pivot Transformation](Screenshots/pivot.png)

---

### 4. **Data Loading**

- SQL scripts are used to create and populate tables in Azure SQL DB.
- Final dataset includes key metrics such as:
  - Cases per 100k population
  - Mortality Rate
  - Region and country-wise breakdown

---

### 5. **Data Visualization (Power BI)**

- The cleaned data is visualized in Power BI.
- Reports highlight trends in COVID-19 cases and deaths by country, region, and time.

![Power BI Dashboard](Screenshots/powerbi.png)

---

## 📊 Power BI Dashboard Highlights

- Daily/weekly case trends
- Country-wise COVID-19 impact
- Population-normalized metrics (e.g., cases per 100k)

---

## 📈 Sample ADF Pipelines & Data Flows

- **Ingest Data Pipeline**
- **Data Transformation with Data Flow**
- **Load to Azure SQL DB**

![ADF Data Flow](Screenshots/dataflow.png)

---

## ✅ Key Takeaways

- Demonstrates full ETL lifecycle using Azure.
- Scalable design using cloud services.
- End-to-end pipeline integration with visualization.

---

## 👤 Author

**Abishek Kedarsethi**

- [LinkedIn](https://in.linkedin.com/in/abishek-kedarsethi)

---

## 📎 References

- [ECDC COVID-19 Dataset](https://www.ecdc.europa.eu/en)
- [Eurostat Population Dataset](https://ec.europa.eu/eurostat)
