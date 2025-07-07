# 📊 Microsoft Fabric Data Engineering Project – Yahoo Finance Stock Lakehouse

This project is a **production-grade, end-to-end data engineering solution** built on **Microsoft Fabric**. It automates the ingestion, transformation, and curation of stock market and financial data from **Yahoo Finance**, structured using a **Medallion architecture (Bronze → Silver → Gold)** and served via **Lakehouse tables** and **SQL Database**.

The output is ready for use in **Power BI dashboards**, **Machine Learning models**, and **financial insights delivery**.

---

## 📚 Table of Contents

- [🚀 Project Overview](#-project-overview)
- [🌟 Features](#-features)
- [🏗️ Architecture Diagram](#-architecture-diagram)
- [📁 Folder Structure](#-folder-structure)
- [🔧 Technologies Used](#-technologies-used)
- [⚙️ Configuration](#%EF%B8%8F-configuration)
- [🚦 Getting Started](#-getting-started)
- [🧠 Use Cases](#-use-cases)
- [📊 Future Enhancements](#-future-enhancements)
- [👨‍💼 Author](#-author)
- [📄 License](#-license)

---

## 🚀 Project Overview

This solution implements a highly scalable data lakehouse pipeline that:

- Ingests raw data from Yahoo Finance API
- Processes and cleans the data using Microsoft Fabric Notebooks (PySpark)
- Stores structured data in Bronze, Silver, and Gold layers
- Loads final trusted datasets into SQL Database and Lakehouse
- Enables analytical exploration via Power BI and ML workflows

---

## 🌟 Features

- Modular Medallion Architecture
- Domain-driven Data Pipelines
- Configurable PySpark Notebooks
- Delta Lake Storage and Lakehouse Integration
- End-to-end Logging via SQL Stored Procedures
- Real-time and batch readiness
- Optimized for BI & ML downstream use

---

## 🏗️ Architecture Diagram

```text
+------------------------+
|   Yahoo Finance API    |
+------------------------+
            ⬇
    [ Bronze Pipelines ]  — Raw JSON, CSV ingestion
            ⬇
    [ Silver Pipelines ]  — Data cleaning & normalization
            ⬇
    [  Gold Pipelines  ]  — Business aggregates, joining
            ⬇
+--------------------------------------------+
| Fabric Lakehouse Tables + SQL Gold Tables  |
+--------------------------------------------+
            ⬇
    [ Power BI / ML Modeling / Analytics ]
```

---

## 📁 Folder Structure

```text
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
```

---

## 🔧 Technologies Used

| Layer          | Technology                         |
| -------------- | ---------------------------------- |
| Ingestion      | Microsoft Fabric Pipelines         |
| Transformation | Fabric Notebooks (PySpark)         |
| Storage        | Microsoft Lakehouse (Delta Tables) |
| Serving        | SQL DB (Gold Tables)               |
| Source         | Yahoo Finance API, News API        |
| Logging        | SQL Procedure: `usp_logdetails`    |
| Configuration  | JSON-based env files               |

---

## ⚙️ Configuration

Update the following file with your environment-specific settings:

``

```json
{
  "tickers": ["AAPL", "TSLA", "GOOG"],
  "start_date": "2023-01-01",
  "end_date": "2025-01-01",
  "news_api_key": "<your_api_key>",
  "log_schema": "dbo"
}
```

---

## 🚦 Getting Started

1. **Configure** the `yahoo_env.json` file
2. **Run Bronze Master Pipeline**
   - Ingest raw data from APIs
3. **Run Silver Master Pipeline**
   - Clean, normalize and join data
4. **Run Gold Master Pipeline**
   - Load final tables into SQL and Lakehouse
5. **Validate** via SQL or Lakehouse table explorer
6. **Visualize** via Power BI or ML notebooks

---

## 🧠 Use Cases

- 📊 Historical stock price analytics
- 💼 Company financial health dashboards
- 🔍 News-based stock movement correlation
- 📊 ML model training for stock prediction
- 📈 Risk scoring and investment insights

---

## 📊 Future Enhancements

-

---

## 👨‍💼 Author

**Shiv**\
Co-founder & Director of Product Strategy\
[Pyzen Technologies](https://pyzentech.com) • Delhi, India\
[LinkedIn](https://www.linkedin.com) | [Website](https://pyzentech.com)

---

## 📄 License

Licensed under the **MIT License**. See `LICENSE` file for more details.

---

> ✨ Built with Microsoft Fabric for scalable, intelligent data engineering solutions.

