# Data Warehouse and Analytics

A production-style end-to-end Data Warehouse project built using SQL Server, implementing the Medallion Architecture (Bronze, Silver, Gold layers) with full ETL pipeline, data integration, star schema modeling, and analytics reporting.

---

## Table of Content
* [Project Overview](#project-overview)
* [Architecture](#architecture)
* [Data Sources](#data-sources)
* [Medallion Layers](#medallion-layers)
* [Data Integration](#data-integration)
* [Star Schema](#star-schema)
* [ETL Workflow](#etl-workflow)
* [Project Structure](#project-structure)
* [Tech Stack](#tech-stack)

---

## Project Overview

This project builds a modern Data Warehouse on SQL Server that ingests raw data from CRM and ERP source systems, transforms it through Bronze, Silver, and Gold layers, and delivers business-ready data for reporting and analytics.

---

## Architecture

![High Level Architecture](Documents/data_architecture_overview.png)

---

## Data Sources

| Source | Format | Description |
|--------|--------|-------------|
| CRM | CSV Files | Customer, Sales, and Product Information |
| ERP | CSV Files | Customer Details, Location, and Product Categories |

**Object Type:** CSV Files
**Interface:** Files in Folders

---

## Medallion Layers

![Medallion Layer Comparison](Documents/medallion_layer_comparison.png)

| Category | Bronze Layer | Silver Layer | Gold Layer |
|----------|-------------|-------------|------------|
| **Definition** | Raw, unprocessed data as-is from sources | Clean & standardized data | Business-Ready data |
| **Objective** | Traceability & Debugging | Intermediate Layer — Prepare Data for Analysis | Provide data for reporting & Analytics |
| **Object Type** | Tables | Tables | Views |
| **Load Method** | Full Load (Truncate & Insert) | Full Load (Truncate & Insert) | None |
| **Data Transformation** | None (as-is) | Data Cleaning, Standardization, Normalization, Derived Columns, Data Enrichment | Data Integration, Data Aggregation, Business Logic & Rules |
| **Data Modeling** | None (as-is) | None (as-is) | Star Schema, Aggregated Objects, Flat Tables |
| **Target Audience** | Data Engineers | Data Analysts, Data Engineers | Data Analysts, Business Users |

---

## ETL Workflow

![Layer Workflow](Documents/layer_workflow.png)

### Bronze Layer
| Step | Description |
|------|-------------|
| Analysing | Interview source system experts |
| Coding | Data Ingestion |
| Validating | Data Completeness & Schema Checks |
| Docs & Version | Documenting & Versioning in Git |

### Silver Layer
| Step | Description |
|------|-------------|
| Analysing | Explore & Understand the Data |
| Coding | Data Cleansing |
| Validating | Data Correctness Checks |
| Docs & Version | Documenting & Versioning in Git — Data Flow, Data Integration |

### Gold Layer
| Step | Description |
|------|-------------|
| Analysing | Explore & Understand the Business Objects |
| Coding | Data Integration |
| Validating | Data Integration Checks |
| Docs & Version | Documenting & Versioning in Git — Data Model, Data Catalog, Data Flow |

---

## Data Integration

![Data Integration](Documents/data_integration_diagram.png)

### CRM Tables
- `crm_sales_details` — Transactional records about Sales & Orders
- `crm_cust_info` — Customer Information
- `crm_prd_info` — Current & History Product Information

### ERP Tables
- `erp_px_cat_g1v2` — Product Categories
- `erp_cust_az12` — Extra Customer Information (Birthdate)
- `erp_loc_a101` — Location of Customers (Country)

---

## Star Schema

![Sales Data Mart Star Schema](Documents/sales_data_mart_star_schema.png)

### gold.fact_sales
| Column | Description |
|--------|-------------|
| order_number | Unique order identifier |
| product_key | FK to dim_products |
| customer_key | FK to dim_customers |
| order_date | Date of order |
| shipping_date | Date of shipping |
| due_date | Due date |
| sales_amount | Total sales amount |
| quantity | Number of items |
| price | Price per item |

> Sales Calculation: **Sales = Quantity * Price**

### gold.dim_customers
| Column | Description |
|--------|-------------|
| customer_key | Primary Key |
| customer_id | Customer identifier |
| customer_number | Customer number |
| first_name | First name |
| last_name | Last name |
| country | Country |
| marital_status | Married / Single |
| gender | Gender |
| birthdate | Date of birth |

### gold.dim_products
| Column | Description |
|--------|-------------|
| product_key | Primary Key |
| product_id | Product identifier |
| product_number | Product number |
| product_name | Product name |
| category_id | Category identifier |
| category | Product category |
| subcategory | Product subcategory |
| maintenance | Yes / No |
| cost | Product cost |
| product_line | Product line |
| start_date | Product start date |

---

## Source System Interview

![Source System Interview](Documents/source_system_interview.png)

---

## Project Structure

data-warehouse-and-analytics/
│
├── datasets/          # Raw source CSV files (CRM & ERP)
├── scripts/           # SQL scripts for Bronze, Silver, Gold layers
├── tests/             # Data validation and quality test scripts
├── Documents/         # Architecture diagrams and documentation
└── README.md

---

## Tech Stack

| Category | Tools |
|----------|-------|
| Database | SQL Server |
| Language | T-SQL |
| Architecture | Medallion (Bronze, Silver, Gold) |
| Data Modeling | Star Schema |
| ETL | Stored Procedures |
| Version Control | GitHub |

---

## Author

**Ajay Karthik Pogula**
Data Analytics | Data Engineering
[GitHub](https://github.com/ajaykarthikpogula0101)
