# 📊 Microsoft Fabric Data Engineering Project – Yahoo Finance Stock

This project is a **production-grade, end-to-end data engineering solution** built on **Microsoft Fabric**. It automates the ingestion, transformation, and curation of stock market and financial data from **Yahoo Finance**, structured using a **Medallion architecture (Bronze → Silver → Gold)** and served via **Lakehouse tables** and **SQL Database**.

The output is ready for use in **Power BI dashboards**, **Machine Learning models**, and **financial insights delivery**.

---

## 📚 Table of Contents

- [🚀 Project Overview](#-project-overview)
- [🌟 Features](#-features)
- [🏗️ Architecture Diagram](#-architecture-diagram)
- [📁 Folder Structure](#-folder-structure)
- [🔧 Technologies Used](#-technologies-used)
- [🧠 Use Cases](#-use-cases)
- [▶️ Project Video](#-project-video)
- [📦 Project Materials](#-project-materials)
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
- Metadata-driven Data Pipelines
- Configurable PySpark Notebooks
- Delta Lake Storage and Lakehouse Integration
- End-to-end Logging via SQL Stored Procedures
- Batch readiness
- Optimized for BI & ML downstream use
- Embedded Power BI dashboards
- Fabric CI/CD deployment enabled

---

## 🏗️ Architecture Diagram
<img src="https://raw.githubusercontent.com/bitoollearner/bilearner-ds-lab/main/yahoo-finance/Yahoo-Stock-Architecture.png" alt="Yahoo Stock Architecture Diagram" />


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
|   └── pipeline-metadata-notebook
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


## 🧠 Use Cases

- 📊 Historical stock price analytics
- 💼 Company financial health dashboards
- 🔍 News-based stock movement correlation
- 📊 ML model training for stock prediction
- 📈 Risk scoring and investment insights

---

## 📦 Project Video

You can view the complete end-to-end project video here:

🔗 [Microsoft Fabric Data Engineering Project End to End](https://youtu.be/3Q3QzjbEQgk)


---

## 📦 Project Materials

You can find supporting notebooks, configurations, and Power BI reports here:

🔗 [Please complete this form regarding the project materials. Thank you!](https://docs.google.com/forms/d/e/1FAIpQLSclOVSLYW0AJN-ZDGzVK6Xhi6RaHo5hTX44aTsG0IR32Du1pA/viewform)

---

## 👨‍💼 Author

[**BI Learner**](www.youtube.com/@bilearner)\
[LinkedIn](https://www.linkedin.com/in/bilearner/)

---

## 📄 License

Licensed under the **MIT License**. See the `LICENSE` file for more details.

---

> ✨ Built with Microsoft Fabric for scalable, intelligent data engineering solutions.

