# 🗽 NYC Data Engineering Project

A production-grade, end-to-end data engineering pipeline built on Azure and Databricks to ingest, process, transform, and analyze New York City public datasets (e.g., NYC Taxi & Limousine Commission, Citibike). This project leverages a Lakehouse architecture to deliver scalable, reliable analytics and automated operational monitoring.

---

## 🏗️ System Architecture

```text
                  +-----------------------------------+
                  |   Data Source / API (NYC Public)  |
                  +-----------------------------------+
                                    │
                                    ▼
                  +-----------------------------------+
                  |      Azure Data Factory (ADF)     |
                  +-----------------------------------+
                                    │
                                    ▼
                  +-----------------------------------+
                  | Azure Data Lake Storage Gen2 (ADLS)
                  |     - Bronze Layer (Raw)          |
                  +-----------------------------------+
                                    │
                                    ▼
                  +-----------------------------------+
                  |         Azure Databricks          |
                  |     - Silver Layer (Cleansed)     |
                  |     - Gold Layer (Aggregated)     |
                  +-----------------------------------+
                         │                    │
        (Pipeline Failure) │                    │ (Processed Data)
                         ▼                    ▼
             +-----------------------+   +------------------------+
             |   Azure Logic Apps    |   | Power BI / Analytics   |
             |  (Automated Alerts)   |   +------------------------+
             +-----------------------+
