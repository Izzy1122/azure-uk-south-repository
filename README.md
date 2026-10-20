📌 Overview


This project processes multiple CSV sales datasets stored together in a single folder named CRM+Sales+Opportunities inside the raw_data container in Azure Data Lake Storage Gen2. The pipeline ingests all datasets, applies structured cleaning and transformation steps in Databricks, and writes the refined outputs into a dedicated transformed zone.

Azure Synapse Serverless SQL then exposes these cleaned datasets using OPENROWSET, enabling direct SQL querying over the lake. Power BI connects to Synapse to build interactive reports based on the transformed data. The project demonstrates practical cloud data engineering skills: multi‑dataset ingestion, data cleaning, transformation, lake‑based SQL analytics, and downstream reporting.

🏗️ Architecture



Raw Data (ADLS Gen2)
        ↓

        
Databricks (Cleaning & Transformation)
        ↓

        
Transformed Data (ADLS Gen2)
        ↓

        
Synapse Serverless SQL (OPENROWSET Views)
        ↓

        
Power BI (Dashboards & Reporting)

🧰 Technologies Used



-Azure Services

• Azure Data Lake Storage Gen2

• Azure Databricks

• Azure Synapse Analytics (Serverless SQL)

• Azure Active Directory (Managed Identity)

-Data Engineering

• PySpark

• CSV → cleaned CSV

• Data validation

• SQL views

• OPENROWSET queries

-Analytics

• Power BI

• Synapse SQL endpoint

-Version Control

• GitHub

• Modular project structure

• Documentation


🔄 Pipeline Steps

1. Raw Data Ingestion
Raw CSV files are stored in an ADLS Gen2 container.
This acts as the landing zone for all incoming data.

2. Databricks Cleaning & Transformation
Databricks notebooks process every dataset in the folder using a consistent cleaning workflow:

• Schema inference

• Null handling

• Duplicate removal

• Type casting

• String trimming

• Data validation

• Standardized output formatting

• Cleaned datasets are written to:  transformed-data/dataset/*.csv


3. Synapse Serverless SQL Views
Synapse exposes the transformed data using OPENROWSET.

Example:  
SELECT *
FROM OPENROWSET(
    BULK 'https://<storage-account>.dfs.core.windows.net/transformed-data/accounts/*.csv',
    FORMAT = 'CSV',
    PARSER_VERSION = '2.0',
    HEADER_ROW = TRUE
) AS rows;


Views created:

• vAccounts

• vData_Dictionary

• vProducts

• vSales_Pipeline

• vSalesTeam

These views allow SQL querying directly over ADLS without a dedicated SQL pool



4. Power BI Reporting
Power BI connects to the Synapse SQL endpoint and loads the serverless views.

Dashboards include:

• Sales performance

• Customer insights

• Product trends

• Pipeline metrics

📊 Screenshots



🎯 Skills Demonstrated
Cloud Engineering

• ADLS Gen2

• Databricks notebooks

• Synapse Serverless SQL

• Managed Identity authentication

Data Engineering

• ETL pipeline design

• Data cleaning and transformation

• CSV processing

• SQL view creation

• OPENROWSET usage

Analytics

• Power BI dashboarding

• SQL querying

• Data modelling

Software Engineering

• GitHub version control

• Modular folder structure

• Documentation and diagrams

📈 Project Summary
This project shows the full workflow from raw data to analytics, including cleaning, transformation, SQL querying, and dashboard creation. It demonstrates practical Azure data engineering skills used in real cloud environments.
