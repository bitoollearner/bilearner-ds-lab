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
