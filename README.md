# Azure Data Engineering Project: Healthcare Data Integration  

## Introduction  
This project integrates healthcare data from EMR systems, insurance claims, and NPI APIs using Azure services. Leveraging the Medallion Architecture, it transforms raw data into clean, analytics-ready datasets for business intelligence and reporting.

---

## Architecture of the Project  
The architecture follows the Medallion Architecture with **Landing**, **Bronze**, **Silver**, and **Gold** layers for data processing and transformation. Below is the visual representation of the project architecture:  

![Project Architecture]

![image](https://github.com/user-attachments/assets/35b572ea-7917-455f-8edd-f872484ee015)


### Explanation of Layers  
- **Landing Layer**:  
  Data is ingested from multiple sources:  
  - EMR Data (SQL)  
  - Claim Files (CSV in ADLS)  
  - NPI Data (via APIs)  

- **Bronze Layer**:  
  Raw data is stored in Parquet format.  

- **Silver Layer**:  
  Data is cleaned, deduplicated, and standardized.  

- **Gold Layer**:  
  Analytics-ready data is stored for reporting and business intelligence.  

---

## Services Used  
- **Azure SQL Database**: Stores EMR data for real-time updates.  
- **Azure Data Lake Storage Gen2 (ADLS Gen2)**: Stores claim files in CSV format.  
- **API Integration**: Fetches National Provider Information (NPI) data.  
- **Azure Data Factory (ADF)**: Automates data ingestion, validation, and processing.  
- **Databricks**: Cleans and transforms data between layers.  
- **Delta Lake**: Provides ACID transactions and historical tracking.  
- **Azure Key Vault**: Secures credentials and secrets.

---

## Project Workflow  
1. **Data Ingestion**:  
   - Retrieve EMR data from Azure SQL.  
   - Upload claim files to ADLS.  
   - Fetch NPI data via APIs.  
2. **Bronze Layer**: Store raw data in Parquet format.  
3. **Silver Layer**: Clean data, remove duplicates, and apply SCD Type 2 for history.  
4. **Gold Layer**: Prepare analytics-ready datasets for reporting.  
5. **Orchestration**: Use ADF pipelines to automate workflows; Databricks for advanced transformations.

---

## Steps Involved  

### Data Ingestion  
- Use ADF to connect to Azure SQL, ADLS, and APIs.  
- Validate and load raw data into the Bronze layer.

### Pipeline Implementation  
- **Lookup and Validation**: Identify and validate files dynamically.  
- **File Handling**: Archive valid files; process and validate into the Bronze layer.  
- **Audit Logging**: Track pipeline activities using Delta Lake.

### Data Transformation  
- **Bronze to Silver**: Clean, deduplicate, and standardize data. Apply SCD Type 2 for historical tracking.  
- **Silver to Gold**: Use Databricks notebooks for final transformations.

### Security  
- Retrieve credentials securely using Azure Key Vault.

---

## Conclusion  
This project demonstrates how Azure services enable scalable, secure, and efficient healthcare data integration. It ensures high-quality datasets for analytics and reporting while adhering to robust data governance practices.
