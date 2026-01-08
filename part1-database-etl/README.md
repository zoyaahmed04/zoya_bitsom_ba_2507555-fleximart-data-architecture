# Part 1 – Database ETL

## Overview
This part of the project focuses on building a relational database for FlexiMart.
It includes data cleaning, database schema creation, and business analysis using SQL.

## Data Sources
- customers_raw.csv
- products_raw.csv
- sales_raw.csv

## ETL Process
The raw datasets contained missing values, duplicates, and inconsistent formats.
These issues were handled using Python (pandas) to produce clean CSV files that were
ready for database ingestion.

## Database Design
A MySQL database named `fleximart` was created with the following tables:
- customers
- products
- sales

Primary keys and foreign key relationships were defined to maintain data integrity.

## Business Queries
Business analysis was performed using SQL queries involving joins, aggregation,
and filtering to answer questions such as:
- total revenue generated
- top-selling products
- revenue by category
- top customers by spending

All queries are stored in `business_queries.sql`.

## Files in This Folder
- business_queries.sql
- data_quality_report.txt
- README.md

