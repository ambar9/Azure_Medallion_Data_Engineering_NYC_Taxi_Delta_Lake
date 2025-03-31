# Azure Medallion Data Engineering: NYC Taxi & Delta Lake

## Project Overview

![Architecture](assets\project_architechture.png)

This project provides a comprehensive, **industry-ready** approach to building an end-to-end data engineering pipeline on Azure. It covers in-demand tools and technologies in detail.The project focuses on building a parameterized dynamic data pipeline in **Azure Data Factory** to pull data directly from APIs using powerful PySpark functions in **Databricks** for data transformation. The project follows a **medallion architecture** (Bronze, Silver, Gold layers).

This project aims to equip individuals, from beginners to experienced data engineers, with the skills and understanding needed to be competitive in the world of data engineering.

## Key Technologies and Concepts Covered

*   **Azure Data Factory (ADF):** Creating **parameterized dynamic data pipelines** to pull data from APIs. Utilizing activities such as ForEach, parameters, parameterized datasets, and parameterized linked services.
*   **Databricks:** A unified analytics platform used for powerful clusters and **PySpark**. PySpark will be used to move data between the Bronze, Silver, and Gold layers.
*   **Delta Lake:** A special file format built on top of Parquet that provides **transactional logs**, enabling features like data versioning and time travel.
*   **Medallion Architecture:** Implementing Bronze (raw), Silver (transformed), and Gold (modeled) layers for data management.
*   **Parquet File Format:** Using performant **column-based file formats** designed for big data storage.
*   **API Integration:** Directly fetching data from websites using HTTP connections instead of manual uploads.
*   **Data Lake (Azure Data Lake Storage Gen2):** Utilizing blob storage with a **hierarchical namespace** to act as a data lake for storing data in different layers.
*   **Security:** Implementing security parameters such as **managed identities** (system-managed identities) for secure data access.
*   **Service Principal:** Creating and configuring a service principal in Azure Active Directory (Microsoft Entra ID) to grant Databricks secure access to the data lake.
*   **Spark SQL:** Querying Delta tables using SQL commands within Databricks.
*   **Power BI Connectivity:** Establishing a connection from Databricks to Power BI to serve data for visualization.

## Project Architecture

The project follows a medallion architecture:

*   **Bronze Layer (Raw Zone):** Ingesting data directly from the NYC Taxi open dataset API into Azure Data Lake Storage Gen2 in Parquet format using Azure Data Factory.
*   **Silver Layer (Transformed Zone):** Reading data from the Bronze layer using Databricks and PySpark, applying necessary transformations, and storing the transformed data back into Azure Data Lake Storage Gen2 in Parquet format.
*   **Gold Layer (Modeled Zone/Serving Layer):** Reading data from the Silver layer using Databricks and PySpark, further modeling the data, and storing it as **Delta tables** in Azure Data Lake Storage Gen2. These Delta tables can then be queried and served to reporting tools like Power BI .


### Project Phases

1.  **Phase One: Data Ingestion (Bronze Layer)**
    *   Creating an Azure Data Lake Storage Gen2 account.
    *   Creating an Azure Data Factory instance.
    *   Building **dynamic pipelines** in Azure Data Factory to fetch NYC Taxi data directly from the API.
    *   Storing the raw data in Parquet format in the **Bronze** container of the data lake.
    *   Manually uploading lookup CSV files (trip type and trip zone) to the Bronze layer.

2.  **Phase Two: Data Transformation (Silver Layer)**
    *   Creating an Azure Databricks workspace and a compute cluster.
    *   Setting up **data access** from Databricks to the Azure Data Lake Storage Gen2 using a service principal.
    *   Reading data from the Bronze layer (CSV and Parquet) using PySpark.
    *   Applying data transformations using PySpark.
    *   Writing the transformed data in Parquet format to the **Silver** container of the data lake.

3.  **Phase Three: Data Modeling and Serving (Gold Layer)**
    *   Reading data from the Silver layer using Databricks and PySpark.
    *   Creating a database in Databricks.
    *   Writing the modeled data as **Delta tables** to the **Gold** container of the data lake.
    *   Exploring **Delta Lake** features such as transaction logs, data versioning, and time travel.
    *   Querying the Delta tables using **Spark SQL**.
    *   Establishing a connection from **Databricks to Power BI** to visualize the data.
