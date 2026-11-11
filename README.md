# CareSync – Azure Data Factory | Healthcare Data Engineering

## Overview

CareSync is an end-to-end healthcare data engineering project built using Microsoft Azure services. This repository contains the Azure Data Factory (ADF) implementation responsible for orchestrating data ingestion, managing metadata-driven workflows, and coordinating downstream data transformations in Azure Databricks.

The platform integrates healthcare data from multiple sources and organizes it into a structured Medallion Architecture to support reliable data processing and analytical reporting.

This repository works together with the [CareSync Azure Databricks repository](https://github.com/Srinivas-49/caresyncadbrepo).

## Solution Architecture

```text
Source Systems
    |
    |-- Neon PostgreSQL
    |
    |-- Azure Data Lake Storage CSV Files
    |
    v
Azure Data Factory
    |
    |-- Metadata-driven ingestion
    |-- Dynamic table processing
    |-- Pipeline orchestration
    |-- Audit and execution tracking
    |
    v
Azure Data Lake Storage Gen2
    |
    |-- Landing Zone
    |-- Parquet / CSV Files
    |
    v
Azure Databricks
    |
    |-- Bronze Layer
    |-- Silver Layer
    |-- Gold Layer
    |
    v
Healthcare Analytics
```

## Key Features

### 1. Metadata-Driven Data Ingestion
- Uses centralized control-table configurations to manage source tables.
- Dynamically identifies active tables for processing.
- Supports reusable ingestion pipelines.
- Uses parameters to manage source systems and table-level execution.

### 2. Multiple Source Integrations
- PostgreSQL data ingestion.
- CSV file ingestion from Azure Data Lake Storage.
- Configurable datasets and linked services.
- Parquet-based file movement for PostgreSQL ingestion.

### 3. Pipeline Orchestration
- Master pipeline to coordinate end-to-end execution.
- Reusable child pipelines for source-to-Silver processing.
- Dynamic ForEach activities for multiple-table execution.
- Databricks notebook orchestration for Silver-to-Gold transformations.

### 4. Audit Logging and Monitoring
- Tracks pipeline run IDs and table-level execution.
- Maintains processing status in audit tables.
- Captures in-progress, successful, and failed execution states.
- Records processing timestamps and row counts where configured.

### 5. Incremental Processing Support
- Uses metadata configurations and watermark values.
- Supports table-specific load strategies.
- Coordinates downstream FULL, APPEND, and MERGE processing through Databricks.

## Pipeline Components

| Pipeline | Responsibility |
|---|---|
| PL_MASTER | Coordinates the overall workflow |
| Pl_source_to_silver | Manages source ingestion for configured tables |
| pl_source_silver_inner | Handles table-level ingestion and Bronze-to-Silver execution |
| Pl_silver_to_gold | Orchestrates Gold-layer transformations |

## Repository Structure

```text
caresync_adf_repo/
│
├── dataset/
│   ├── AzureSqlTable1.json
│   ├── DS_csv_binary.json
│   ├── PostgreSqlTable1.json
│   └── ds_adls_p1.json
│
├── factory/
│   └── DF-Azure-P1.json
│
├── linkedService/
│   ├── ADLS_LS_CareSync_P1.json
│   ├── AzureDatabricks1.json
│   ├── caresync_sql_ls_p1.json
│   ├── keyvault_ls_p1.json
│   └── postgres_ls_caresync_p1.json
│
├── pipeline/
│   ├── PL_MASTER.json
│   ├── Pl_source_to_silver.json
│   ├── pl_source_silver_inner.json
│   ├── Pl_silver_to_gold.json
│   └── test.json
│
├── trigger/
│   └── caresync_trigger.json
│
├── publish_config.json
└── README.md
```

## Technologies Used

- Microsoft Azure Data Factory
- Azure Data Lake Storage Gen2
- Azure Databricks
- Azure SQL Database
- PostgreSQL
- Azure Key Vault
- Apache Parquet
- JSON
- SQL

## Related Repository

The transformation and analytical processing components are maintained separately:

**Azure Databricks:**  
https://github.com/Srinivas-49/caresyncadbrepo

Together, these repositories implement the orchestration and transformation layers of the CareSync healthcare data platform.

## Author

Srinivas

GitHub: https://github.com/Srinivas-49
