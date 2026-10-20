## 🛠️ Tech Stack

![Azure](https://img.shields.io/badge/Microsoft_Azure-0089D6?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Azure Data Lake](https://img.shields.io/badge/Azure_Data_Lake-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Azure Synapse](https://img.shields.io/badge/Azure_Synapse-0066FF?style=for-the-badge&logo=azure-synapse-analytics&logoColor=white)
![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=for-the-badge&logo=databricks&logoColor=white)
![Apache Spark](https://img.shields.io/badge/Apache_Spark-E25A1C?style=for-the-badge&logo=apachespark&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Jupyter](https://img.shields.io/badge/Jupyter_Notebooks-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)




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

Pipeline Dataflow

![PipelineDataFlow](https://raw.githubusercontent.com/Izzy1122/azure-uk-south-repository/refs/heads/dev/Screenshots/PipelineDataFlow.png)


Pipeline Run Reports

![PipelineRunReport](https://raw.githubusercontent.com/Izzy1122/azure-uk-south-repository/refs/heads/dev/Screenshots/PipelineRunReport.png)


Pipeline Activity Run Metrics. The Failed was as a result to my computer being off and Integration Runtime not being active thus Failed.

![Pipeline activity run metrics](https://raw.githubusercontent.com/Izzy1122/azure-uk-south-repository/refs/heads/dev/Screenshots/Pipeline%20activity%20run%20metrics.png)

Filtered to my latest Manual Trigger

![Pipeline activity run metrics2](https://raw.githubusercontent.com/Izzy1122/azure-uk-south-repository/refs/heads/dev/Screenshots/Pipeline%20activity%20run%20metrics2.png)

Triggers

![Trigger](https://raw.githubusercontent.com/Izzy1122/azure-uk-south-repository/refs/heads/dev/Screenshots/Trigger.png)

![TriggerNow](https://raw.githubusercontent.com/Izzy1122/azure-uk-south-repository/refs/heads/dev/Screenshots/TriggerNow.png)

Integration Runtime

![IntegrationRuntime](https://raw.githubusercontent.com/Izzy1122/azure-uk-south-repository/refs/heads/dev/Screenshots/IntegrationRuntime.png)

Linked Services

![LinkedServices](https://raw.githubusercontent.com/Izzy1122/azure-uk-south-repository/refs/heads/dev/Screenshots/LinkedServices.png)


DataBricks (Notebook and Compute)

![compute](https://raw.githubusercontent.com/Izzy1122/azure-uk-south-repository/refs/heads/dev/Screenshots/compute.png)

![DataBricks](https://raw.githubusercontent.com/Izzy1122/azure-uk-south-repository/refs/heads/dev/Screenshots/DataBricks.png)

SQL VIEWS

![SQLviewsAndQuery](https://raw.githubusercontent.com/Izzy1122/azure-uk-south-repository/refs/heads/dev/Screenshots/SQLviewsAndQuery.png)

SQL Querries

![Query1](https://raw.githubusercontent.com/Izzy1122/azure-uk-south-repository/refs/heads/dev/Screenshots/Query1.png)

![Queryy](https://raw.githubusercontent.com/Izzy1122/azure-uk-south-repository/refs/heads/dev/Screenshots/Queryy.png)

![Query4](https://raw.githubusercontent.com/Izzy1122/azure-uk-south-repository/refs/heads/dev/Screenshots/Query4.png)

PowerBI

![PowerBi](https://raw.githubusercontent.com/Izzy1122/azure-uk-south-repository/refs/heads/dev/Screenshots/PowerBi.png)


🎯 Skills Demonstrated
Cloud Engineering

• ADLS Gen2

• Azure Databricks 

• Azure Synapse Serverless SQL

• Managed Identity authentication

Data Engineering

• Multi‑dataset ingestion

• Data cleaning and transformation

• CSV processing

• Schema validation

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


# 📬 Contact

**Israel Obiomah — Data Engineer/Analyst | Power BI | Python | SQL**  
LinkedIn: [linkedin.com/in/israel-obiomah-6ba609253] 


[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](YOUR_LINKEDIN_URL)
[![GitHub](https://img.shields.io/badge/GitHub-000000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/izzy1122)
