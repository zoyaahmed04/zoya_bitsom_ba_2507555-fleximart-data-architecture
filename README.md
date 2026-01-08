# FlexiMart Data Architecture Project

**Student Name:** Zoya Ahmed  
**Student ID:** 2507555  
**Course:** BITSOM Business Analytics  
**Date:** January 2026  


## Project Overview

This project implements a complete data architecture solution for FlexiMart,
covering the full lifecycle of data from raw ingestion to analytical reporting.

The work includes:
- building an ETL pipeline to clean and load transactional data,
- designing and querying relational and NoSQL databases,
- and implementing a star-schema data warehouse to support OLAP analysis
  and business decision-making.

The project demonstrates practical understanding of data engineering concepts,
database modeling, and analytical query design.


## Repository Structure

├── part1-database-etl/
│ ├── README.md
│ ├── etl_pipeline.py
│ ├── schema_documentation.md
│ ├── business_queries.sql
│ ├── data_quality_report.txt
│ └── requirements.txt
│
├── part2-nosql/
│ ├── README.md
│ ├── nosql_analysis.md
│ ├── mongodb_operations.js
│ └── products_catalog.json
│
├── part3-datawarehouse/
│ ├── README.md
│ ├── star_schema_design.md
│ ├── warehouse_schema.sql
│ ├── warehouse_data.sql
│ └── analytics_queries.sql
│
├── data/
│ ├── customers_raw.csv
│ ├── products_raw.csv
│ └── sales_raw.csv
│
├── .gitignore
└── README.md


## Project Overview
This project implements a complete data architecture solution for FlexiMart,
covering data ingestion, cleaning, relational modeling, NoSQL design, and data
warehousing. It demonstrates how raw transactional data can be transformed into
structured databases and analytical systems to support business intelligence
and decision-making.


## Technologies Used

### Programming & Data Processing
- Python 3.x
- pandas
- mysql-connector-python

### Databases
- MySQL 8.0 (Relational & Data Warehouse)
- MongoDB 6.0 (NoSQL)

### Query Languages
- SQL (DDL, DML, OLAP queries)
- MongoDB Query Language

### Version Control
- Git & GitHub


## Project Breakdown

### Part 1 – Database & ETL
- Extracted raw customer, product, and sales data from CSV files.
- Cleaned data by handling missing values, duplicates, and inconsistent formats.
- Loaded cleaned data into a MySQL relational database.
- Wrote SQL business queries to analyze revenue, product performance, and customer spending.
- Documented schema design, normalization (3NF), and data quality handling.

### Part 2 – NoSQL (MongoDB)
- Analyzed limitations of relational databases for flexible product catalogs.
- Designed a document-based product catalog using MongoDB.
- Implemented MongoDB operations including filtering, aggregation, updates, and analysis.
- Demonstrated flexible schemas and embedded documents for customer reviews.

### Part 3 – Data Warehouse & OLAP
- Designed a star schema with fact and dimension tables.
- Implemented a data warehouse schema in MySQL.
- Loaded realistic warehouse data for analytical purposes.
- Wrote OLAP queries for drill-down analysis, product performance, and customer segmentation.

### Key Learnings

- Built a complete ETL pipeline for cleaning and loading real-world datasets.
- Strengthened understanding of relational database design and normalization.
- Applied SQL joins, aggregations, and OLAP concepts to answer business questions.
- Learned when and why NoSQL databases are preferable over relational databases.
- Designed and implemented a star-schema data warehouse for analytical workloads.
- Improved documentation and project structuring using GitHub best practices.

### Challenges Faced

## Data Quality Issues
- Dealt with missing values, duplicates, and inconsistent formats.
- Solved using pandas-based data cleaning and validation logic.

## Database Modeling
- Understanding normalization and dimensional modeling required careful planning.
- Addressed by clearly separating transactional, analytical, and NoSQL use cases.

## Tooling & Environment Setup
- Managing multiple databases and tools was initially challenging.
- Resolved through incremental testing and structured execution steps.

## Setup Instructions

### Relational Database & Data Warehouse Setup

```bash
# Create databases
mysql -u root -p -e "CREATE DATABASE fleximart;"
mysql -u root -p -e "CREATE DATABASE fleximart_dw;"

# Run Part 1 - ETL Pipeline
python part1-database-etl/etl_pipeline.py

# Run Part 1 - Business Queries
mysql -u root -p fleximart < part1-database-etl/business_queries.sql

# Run Part 3 - Data Warehouse
mysql -u root -p fleximart_dw < part3-datawarehouse/warehouse_schema.sql
mysql -u root -p fleximart_dw < part3-datawarehouse/warehouse_data.sql
mysql -u root -p fleximart_dw < part3-datawarehouse/analytics_queries.sql

bash exit

### MangoDB Setup
mongosh < part2-nosql/mongodb_operations.js


