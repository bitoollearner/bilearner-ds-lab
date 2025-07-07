# 📊 Microsoft Fabric Data Engineering Project – Yahoo Finance Stock Lakehouse

This project is a **complete end-to-end data engineering solution** built using **Microsoft Fabric** that ingests, processes, and serves financial stock market data from **Yahoo Finance**. It uses a modular **Medallion architecture** (Bronze → Silver → Gold) powered by **Data Pipelines, Notebooks, Lakehouse tables**, and **SQL databases** to enable analytics, BI reporting, and machine learning.

---

## 📚 Table of Contents

- [🚀 Project Overview](#-project-overview)
- [🎯 Features](#-features)
- [🏗️ Architecture](#️-architecture)
- [📁 Folder Structure](#-folder-structure)
- [🔧 Technologies Used](#-technologies-used)
- [⚙️ Configuration](#️-configuration)
- [▶️ How to Run](#️-how-to-run)
- [🧠 Use Cases](#-use-cases)
- [📈 Future Enhancements](#-future-enhancements)
- [🙋‍♂️ Author](#-author)
- [📄 License](#-license)

---

## 🚀 Project Overview

This repository demonstrates how to:

- 🔄 Automate data ingestion from Yahoo Finance APIs
- 🧼 Apply transformation using Spark Notebooks in Microsoft Fabric
- 🧊 Store data in a **Lakehouse** using the Bronze/Silver/Gold model
- 🗃️ Serve trusted data through **SQL Database tables**
- 📊 Prepare data for **Power BI dashboards** and **ML pipelines**

---

## 🎯 Features

- Multi-layered ETL architecture using **Fabric Pipelines**
- Ingests:
  - ✅ Historical Stock Prices
  - ✅ Financial Statements (Income, Balance Sheet, Cash Flow)
  - ✅ Company Information
  - ✅ Stock Market News
- Separate notebooks for each domain — easy to debug, maintain, and scale
- Gold layer writes to both Lakehouse and SQL Database
- Logging via stored procedures (`usp_logdetails`) for pipeline traceability
- Environment-based configs via JSON

---

## 🏗️ Architecture

```text
                 +---------------------+
                 |  Yahoo Finance API  |
                 +---------------------+
                           ↓
                   [ Bronze Pipelines ]
                           ↓
                   [ Silver Pipelines ]
                           ↓
                   [  Gold Pipelines  ]
                           ↓
       +------------------------------------------+
       | Fabric Lakehouse Tables + SQL Database   |
       +------------------------------------------+


📁 Folder Structure
📦 Project Root
├── 📂 Pipelines
│   ├── 📂 bronze
│   │   ├── 📂 bronze-yf-stock-pipelines
│   │   │   ├── bronze-yf-stock-Income-statement-pipeline
│   │   │   ├── bronze-yf-stock-getting-historical-data-pipeline
│   │   │   ├── bronze-yf-stock-companies-news-pipeline
│   │   │   ├── bronze-yf-stock-companies-info-pipeline
│   │   │   ├── bronze-yf-stock-cash-flow-pipeline
│   │   │   ├── bronze-yf-stock-balance-sheet-pipeline
│   │   │   └── bronze-yf-master-pipeline
│   │   └── 📂 bronze-yf-stock-notebook
│   │       ├── bronze-getting-historical-data
│   │       ├── bronze-companies-stock-news
│   │       ├── bronze-companies-information
│   │       ├── bronze-companies-Income-statement
│   │       ├── bronze-companies-cash-flow-statement
│   │       └── bronze-companies-balance-sheet
│
│   ├── 📂 silver
│   │   ├── 📂 silver-yf-stock-pipelines
│   │   │   ├── silver-yf-stock-Income-statement-pipeline
│   │   │   ├── silver-yf-stock-getting-historical-data-pipeline
│   │   │   ├── silver-yf-stock-companies-news-pipeline
│   │   │   ├── silver-yf-stock-companies-info-pipeline
│   │   │   ├── silver-yf-stock-cash-flow-pipeline
│   │   │   ├── silver-yf-stock-balance-sheet-pipeline
│   │   │   └── silver-yf-master-pipeline
│   │   └── 📂 silver-yf-stock-notebook
│   │       ├── silver-getting-historical-data
│   │       ├── silver-companies-stock-news
│   │       ├── silver-companies-information
│   │       ├── silver-companies-Income-statement
│   │       ├── silver-companies-cash-flow-statement
│   │       └── silver-companies-balance-sheet
│
│   └── 📂 gold
│       ├── 📂 gold-yf-stock-pipelines
│       │   ├── gold-yf-stock-sql-table-pipeline
│       │   ├── gold-yf-stock-master-notebook-run
│       │   └── gold-yf-master-pipeline
│       └── 📂 gold-yf-stock-notebook
│           ├── gold-yahoo-stock-news
│           ├── gold-yahoo-financial-statements
│           └── gold-financials-stock-data
│
├── 📂 Lakehouse
│   └── 📂 yahoo_stock_LH
│       ├── 📂 tables
│       │   ├── yahoo_financial_statements
│       │   ├── yahoo_stock
│       │   └── yahoo_stock_news
│       ├── 📂 bronze
│       │   ├── comp_bal_sheet_data
│       │   ├── comp_cash_flow_data
│       │   ├── comp_incm_stmt_data
│       │   ├── comp_info_data
│       │   ├── comp_news_data
│       │   └── yfinance_data
│       ├── 📂 silver
│       │   ├── comp_bal_sheet_data
│       │   ├── comp_cash_flow_data
│       │   ├── comp_incm_stmt_data
│       │   ├── comp_info_data
│       │   ├── comp_news_data
│       │   └── yfinance_data
│       ├── 📂 gold
│       └── 📂 master_files
│           ├── breakdown_categories
│           ├── company_code
│           └── pipelines
│
├── 📂 config
│   └── yahoo_env
│
└── 📂 Sql_database
    └── yf-stock-db
        ├── 📂 tables
        │   ├── 📂 dbo
        │   │   └── log_details
        │   └── 📂 gold
        │       ├── yahoo_financial_statements
        │       ├── yahoo_stock
        │       └── yahoo_stock_news
        └── 📂 stored_procedures
            └── usp_logdetails


🔧 Technologies Used

| Layer          | Technology                              |
| -------------- | --------------------------------------- |
| Ingestion      | Microsoft Fabric Pipelines              |
| Transformation | Microsoft Fabric Notebooks (PySpark)    |
| Storage        | Microsoft Fabric Lakehouse              |
| Serving        | Fabric SQL DB, Delta Tables             |
| Source         | Yahoo Finance API (`yfinance`)          |
| Logging        | SQL Stored Procedure (`usp_logdetails`) |
| Configuration  | JSON-based environment settings         |


⚙️ Configuration

{
  "tickers": ["AAPL", "TSLA", "GOOG"],
  "start_date": "2023-01-01",
  "end_date": "2025-01-01",
  "news_api_key": "<your_api_key>",
  "log_schema": "dbo"
}


🧠 Use Cases
📊 Create stock dashboards with Power BI

📈 Train ML models on historical stock trends

📰 Track sentiment using news and price correlation

💹 Perform financial health analysis using income/balance/cash flow

🧾 Build investment screeners


📈 Future Enhancements
 Real-time ingestion via Azure Event Hub

 MLFlow integration for model tracking

 Power BI dashboard templates

 CI/CD deployment via GitHub Actions

 Data Quality checks in Silver Layer


🙋‍♂️ Author
Shiv
Co-founder & Director of Product Strategy
Pyzen Technologies, Delhi, India
🔗 LinkedIn • 🌐 pyzentech.com

