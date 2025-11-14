# NYC_TAXI-AZURE-END-END-DATA-PIPELINE

This project demonstrates a complete data engineering pipeline built using Azure Data Factory, Azure Databricks, and Azure Data Lake Gen2. The pipeline ingests NYC Taxi Trip data from a public API, processes it through the Medallion Architecture (Bronze → Silver → Gold), and prepares it for analytics consumption in Tableau.


![NycTaxi](https://github.com/user-attachments/assets/5e4f9ad1-b9e4-438b-ac6e-ebd40fa3431f)


🔗 Source Data

API: NYC Taxi & Limousine Commission Trip Record Data


https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page


🏗️ Architecture Overview

The pipeline follows the Medallion Architecture:


1. Bronze Layer (Raw Data)


Data is ingested from the NYC API using Azure Data Factory (ADF).


ADF uses a ForEach activity with a Range(1, 12) loop to fetch monthly data from January 2024 to December 2024.


Inside the ForEach, an If Condition activity checks conditions before executing the copy operation.


Data is written in Parquet format to the Bronze folder in Azure Data Lake Gen2.



2. Silver Layer (Cleaned & Enriched Data)

   

Data is processed in Azure Databricks for:

Data cleaning


Column renaming


Schema alignment


Basic transformations


Cleaned datasets are stored in Parquet format in the Silver folder of Data Lake Gen2.




3. Gold Layer (Business-Level Data)

   

Additional business logic and transformations are applied in Databricks.


Output is stored in:


Delta format (Delta Lake) in Data Lake Gen2


A Delta Table for optimized analytics and querying


Gold layer is optimized for consumption by BI tools.



📊 Consumption Layer


Final curated datasets are connected to Tableau for dashboards and analytics.


⚙️ Azure Data Factory Activities Used


ForEach Activity: Loops through the months of 2024 using Range(1, 12)


If Condition Activity: Controls logic for handling month-based conditions


Copy Activity: Copies API data into the Bronze layer depending on True/False conditions inside If Condition



🛠️ Tools & Technologies


Azure Data Factory


Azure Databricks


Azure Data Lake Storage Gen2


Delta Lake

Parquet & Delta File Formats

Tableau (for visualization)
