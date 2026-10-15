# End-to-End E-Commerce Sales Medallion ETL Pipeline (PySpark)

## 📌 Project Overview
This project implements a complete **Medallion Architecture (Bronze -> Silver -> Gold)** ETL pipeline using **PySpark** in Google Colab[cite: 4]. The pipeline processes raw e-commerce sales data, handles intentional data quality issues, performs automated validation checks, and generates business-ready analytics reports[cite: 4].

---

## 🏗️ Architecture & Data Flow

### 1. Raw Data Generation
* Generates 10,000 synthetic e-commerce sales records with intentional data quality issues (missing values, negative unit prices, zero quantities, and duplicate records) to test pipeline resiliency[cite: 4].

### 2. Bronze Layer (Raw Ingestion)
* Enforces explicit schema (`StructType`)[cite: 4].
* Stores raw CSV data directly into Parquet format at `/content/bronze_orders` without any modifications[cite: 4].

### 3. Silver Layer (Cleaning & Validation)
* **Deduplication:** Removes duplicate order IDs[cite: 4].
* **Standardization:** Trims whitespaces, applies title capitalization (`initcap`), and converts date strings to proper date objects[cite: 4].
* **Quality Filtering:** Splits records into valid (`silver_df`) and rejected (`rejected_df`) datasets based on business validation rules[cite: 4].
* **Automated Quality Checks:** Uses Python `assert` statements to ensure no nulls, invalid prices, or duplicates remain[cite: 4].

### 4. Gold Layer (Analytics & Aggregations)
Creates business-level aggregated views using Spark SQL[cite: 4]:
* **Daily Sales Report:** Aggregates total delivered orders and daily revenue[cite: 4].
* **Product Sales Summary:** Ranks top products by total revenue[cite: 4].
* **Order Status Breakdown:** Tracks delivered, shipped, cancelled, and returned order volumes[cite: 4].

### 5. Report Export
* Coalesces and exports the daily sales analytics report into a single CSV file for stakeholders[cite: 4].

---

## 🛠️ Tech Stack & Tools
* **Language:** Python 3[cite: 4]
* **Framework:** PySpark (Spark SQL, DataFrames)[cite: 4]
* **Storage Formats:** Parquet, CSV[cite: 4]
* **Environment:** Google Colab[cite: 4]

---

## 👤 Author
* **Name:** Keerthika
* **Role:** Data Engineering / PySpark    
