 # 🚀 Big Data End-to-End Pipeline Project

## 🧩 Overview

This project demonstrates a complete big data pipeline integrating on-premise data ingestion, cloud-based ETL, data transformation, and analytics using the Microsoft Azure ecosystem.

It showcases how data flows from local datasets (Python, MySQL, MongoDB) into the Azure Data Lake (Bronze, Silver, Gold architecture) and is processed using Azure Data Factory, Databricks (PySpark), and Synapse Analytics for analysis and insights.

## ⚙️ Project Architecture

Key Stages:

1. **Data Ingestion**
* Load raw datasets into:
    - **MySQL Database** using Python (via pymysql / sqlalchemy).
    - **MongoDB Database** using Python (via pymongo).
* Data is initially stored locally and structured/unstructured data is prepared for cloud ingestion.

2. **Azure Setup**
* **Resource Group**: Created to manage all Azure services under one logical container.
* **Storage Account**: Created to host the Data Lake with three layers:
    - **🥉 Bronze Layer** – Raw data (directly ingested from source systems).
    - **🥈 Silver Layer** – Cleaned and transformed data.
    - **🥇 Gold Layer** – Aggregated and curated data for analytics.

3. **Data Orchestration (Azure Data Factory)**
* **Azure Data Factory (ADF)** pipelines are configured to:
     - Extract data from GitHub (HTTP source) and MySQL Database.
     - Load data into Bronze Layer of Azure Data Lake.
* Data flow is scheduled and monitored within ADF.

4. **Data Processing (Azure Databricks)**
* Databricks notebooks written in PySpark read data from:
     - **Bronze Layer (Azure Data Lake).**
     - **MongoDB Database.**
* Data transformations and analysis performed using PySpark.
* The cleaned and processed data is written back to the Silver Layer of Data Lake.

5. **Data Analytics (Azure Synapse Analytics)**
* Synapse SQL Pools query data from the Silver Layer.
* Data is aggregated and transformed using SQL scripts.
* Final outputs are stored in the Gold Layer for business analytics and reporting.

## 🧠 Technologies & Tools Used

| **Category**             | **Tools / Technologies**                                                                |
| ------------------------ | --------------------------------------------------------------------------------------- |
| **Programming Language** | Python, PySpark                                                                         |
| **Databases**            | MySQL, MongoDB                                                                          |
| **Cloud Platform**       | Microsoft Azure                                                                         |
| **Azure Services**       | Resource Group, Storage Account, Data Lake, Data Factory, Databricks, Synapse Analytics |
| **Data Movement**        | Azure Data Factory (ADF)                                                                |
| **Data Transformation**  | Azure Databricks (PySpark)                                                              |
| **Data Analysis**        | Azure Synapse SQL                                                                       |
| **Version Control**      | GitHub                                                                                  |
| **Data Flow Layers**     | Bronze → Silver → Gold                                                                  |

## 🧰 Steps to Simulate

**1️⃣ Local Environment Setup**
* Install dependencies:
```bash
pip install pymysql sqlalchemy pymongo pandas azure-storage-blob
```
* Configure connection to MySQL and MongoDB.
* Load dataset from local CSV/JSON files into databases.

**2️⃣ Azure Resource Creation**
* Create a Resource Group in the Azure Portal.
* Create a Storage Account with hierarchical namespace enabled.
* Set up containers for Bronze, Silver, and Gold layers.

**3️⃣ Azure Data Factory (ADF)**
* Create linked services:
     - **HTTP (GitHub source)**
     - **Azure Data Lake Storage**
     - **MySQL Database**
* Build a pipeline to move data → **Bronze Layer.**

**4️⃣ Azure Databricks**
* Connect Databricks to Data Lake and MongoDB.
* Use **PySpark** to:
     - Clean and transform raw data.
     - Perform analytics operations.
* Write output → **Silver Layer.**

**5️⃣ Azure Synapse Analytics**
* Connect Synapse to **Silver Layer.**
* Run SQL queries to aggregate data.
* Export results → **Gold Layer.**
