# CareSync – Azure Data Factory

## Overview

This repository contains the Azure Data Factory (ADF) implementation of the CareSync data engineering project.

Azure Data Factory is used as the data orchestration layer to manage and coordinate data ingestion and processing workflows. It contains the factory configuration, datasets, linked services, pipelines, and triggers required to organize the data engineering process.

This repository works alongside the CareSync Azure Databricks repository, which handles notebook-based data transformations using the Medallion Architecture.

## Architecture

The ADF component is responsible for orchestrating the data pipeline workflow and coordinating the execution of data processing activities.

**Workflow:**

Source Data → Azure Data Factory → Azure Databricks → Data Transformation → Analytics-ready Data

## Repository Structure

```text
caresync_adf_repo/
│
├── dataset/
│   └── Dataset configurations
│
├── factory/
│   └── Azure Data Factory configuration
│
├── linkedService/
│   └── Connection configurations
│
├── pipeline/
│   └── Data pipeline definitions
│
├── trigger/
│   └── Pipeline triggers
│
├── publish_config.json
│
└── README.md
```

## Technologies Used

- Microsoft Azure Data Factory
- Azure Data Factory Pipelines
- Linked Services
- Datasets
- Pipeline Triggers
- Azure Databricks

## Key Responsibilities

- Organizing and orchestrating data workflows.
- Managing source and destination connections through linked services.
- Configuring datasets for data integration.
- Managing pipeline execution.
- Coordinating data processing with Azure Databricks.
- Supporting an organized and maintainable data engineering architecture.

## Project Integration

This repository is one component of the CareSync end-to-end Azure Data Engineering project.

The Azure Databricks implementation is maintained separately:

**Databricks Repository:** https://github.com/Srinivas-49/caresyncadbrepo

Together, both repositories represent the orchestration and transformation components of the CareSync data platform.

## Author

Srinivas-49

