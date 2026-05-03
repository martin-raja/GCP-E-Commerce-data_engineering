# 🚀 End-to-End Data Engineering Project: E-Commerce Analytics Pipeline

---

## 📌 1. Project Overview

This project demonstrates a **complete end-to-end data engineering pipeline** built using modern data stack tools. It ingests raw transactional data, processes and models it into an analytics-ready format, and enables business insights through reporting.

The dataset used is the **Brazilian E-Commerce Public Dataset by Olist**, which simulates real-world e-commerce operations including orders, customers, products, and payments.

---

## 🎯 2. Business Objective

The goal of this project is to transform raw e-commerce data into meaningful insights that help answer critical business questions:

### Key Business Questions:

* What is the overall revenue trend over time?
* Who are the most valuable customers?
* Which product categories drive the most revenue?
* What is the Average Order Value (AOV)?
* Which payment methods are most used?
* How efficient is the delivery process?

---

## 🏗️ 3. Architecture Overview

```text
        Source Data (CSV - Kaggle)
                    │
                    ▼
         Python Ingestion Scripts
                    │
                    ▼
        Raw Storage (Data Lake - GCS)
                    │
                    ▼
     BigQuery Staging Tables (Raw Layer)
                    │
                    ▼
   Transformation Layer (SQL / dbt Models)
                    │
                    ▼
        Analytics Layer (Star Schema)
                    │
                    ▼
        BI Dashboard (Looker / Power BI)
```

---

## 🛠️ 4. Tech Stack

| Layer           | Technology Used            |
| --------------- | -------------------------- |
| Ingestion       | Python (pandas, requests)  |
| Storage         | Google Cloud Storage (GCS) |
| Data Warehouse  | BigQuery                   |
| Transformation  | SQL / dbt                  |
| Orchestration   | Apache Airflow             |
| Visualization   | Looker / Power BI          |
| Version Control | GitHub                     |

---

## 📂 5. Project Structure

```bash
data-engineering-pipeline/
│
├── data/                  # Raw and processed data
├── ingestion/             # Data ingestion scripts
├── warehouse/             # SQL models (staging + marts)
├── transformations/       # dbt models (optional)
├── dags/                  # Airflow DAGs
├── tests/                 # Data quality checks
├── configs/               # Configuration files
├── utils/                 # Helper functions
├── docs/                  # Architecture diagrams
├── README.md
```

---

## 📊 6. Dataset Description

The dataset consists of multiple related tables:

* **customers** → Customer demographic details
* **orders** → Order lifecycle data
* **order_items** → Product-level order details
* **payments** → Payment transactions
* **products** → Product metadata
* **sellers** → Seller information

This multi-table structure allows us to simulate a real-world relational data system.

---

## ⭐ 7. Data Modeling (Star Schema)

The project follows a **star schema design** for analytics optimization.

### 🔶 Fact Table

#### `fact_orders`

| Column        | Description             |
| ------------- | ----------------------- |
| order_id      | Unique order identifier |
| customer_id   | Customer identifier     |
| order_date    | Date of purchase        |
| total_amount  | Total order value       |
| payment_type  | Payment method          |
| delivery_days | Delivery duration       |

---

### 🔶 Dimension Tables

#### `dim_customers`

* customer_id
* city
* state

#### `dim_products`

* product_id
* category
* weight

#### `dim_sellers`

* seller_id
* seller_city

#### `dim_date`

* date, year, month, day

### Data Model
<img width="2000" height="1200" alt="image" src="https://github.com/user-attachments/assets/4eb5ec24-8bfd-4843-a856-f7d230c4fa1b" />
---

## 🔄 8. Data Pipeline Flow

### Step 1: Data Ingestion

* Extract CSV files from source dataset
* Load into local storage / GCS bucket
* Preserve raw data (no transformation)

### Step 2: Data Loading

* Load raw data into BigQuery staging tables
* Use schema auto-detection or predefined schema

### Step 3: Data Transformation

* Clean and standardize data
* Join multiple tables
* Create fact and dimension tables
* Aggregate business metrics

### Step 4: Data Quality Checks

* Check for null values in key columns
* Detect duplicates
* Validate revenue values
* Ensure referential integrity

### Step 5: Orchestration

* Automate pipeline using Airflow DAG
* Schedule daily or batch runs

---

## 🧠 9. Key Transformations

### Fact Table Creation

* Combine orders, order_items, and payments
* Calculate total revenue per order
* Derive delivery time

### Aggregations

* Customer lifetime value
* Monthly revenue trends
* Product category performance

---

## ✅ 10. Data Quality Strategy

Ensuring data reliability is critical:

* **Null Checks** → Mandatory fields like order_id
* **Duplicate Checks** → Unique constraint validation
* **Range Checks** → No negative revenue
* **Business Logic Checks** → Delivery days must be positive

---

## 📊 11. Analytics & Dashboard

The final dataset enables powerful visualizations:

### Dashboard Sections:

* Revenue Overview
* Customer Insights
* Product Performance
* Delivery Analysis

### KPIs:

* Total Revenue
* Total Orders
* Average Order Value (AOV)
* Top Products
* Delivery SLA %

---

## ⚙️ 12. Setup Instructions

```bash
git clone <your-repo-url>
cd data-engineering-pipeline
pip install -r requirements.txt
```

### Run Ingestion

```bash
python ingestion/ingest_csv.py
```

---

## ▶️ 13. Running the Pipeline

* Step 1: Ingest data
* Step 2: Load to BigQuery
* Step 3: Execute SQL transformations
* Step 4: Run data quality checks
* Step 5: Refresh dashboards

---

## 🚀 14. Future Enhancements

* Implement dbt for transformation management
* Add CI/CD using GitHub Actions
* Introduce streaming pipeline (Kafka / PubSub)
* Add monitoring & alerting
* Partition and cluster BigQuery tables for performance

---

## 💼 15. Business Impact

This project simulates how organizations:

* Convert raw data into actionable insights
* Improve decision-making using analytics
* Monitor operational efficiency
* Identify growth opportunities

---

## 🧾 16. Resume Highlights

* Designed and implemented a scalable data pipeline
* Built star schema data model for analytics
* Performed complex SQL transformations
* Ensured data quality and reliability
* Delivered business insights through dashboards

---

## 🙌 17. Conclusion

This project demonstrates the **full lifecycle of data engineering**, from ingestion to insights. It showcases both **technical depth** and **business understanding**, making it highly relevant for real-world applications.

---
