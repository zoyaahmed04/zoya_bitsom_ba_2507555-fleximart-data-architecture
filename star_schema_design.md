## Section 1: Schema Overview

The FlexiMart data warehouse follows a star schema design to support efficient
analytical querying and reporting.


### FACT TABLE: fact_sales

**Grain:** One row per product per order line item  
**Business Process:** Sales transactions

**Measures (Numeric Facts):**
- quantity_sold: Number of units sold
- unit_price: Price per unit at the time of sale
- discount_amount: Discount applied on the transaction
- total_amount: Final sale amount calculated as  
  (quantity_sold × unit_price − discount_amount)

**Foreign Keys:**
- date_key → dim_date
- product_key → dim_product
- customer_key → dim_customer

The fact_sales table stores transactional metrics that can be aggregated across
different dimensions such as time, product, and customer.


### DIMENSION TABLE: dim_date

**Purpose:** Date dimension for time-based analysis  
**Type:** Conformed dimension

**Attributes:**
- date_key (PK): Surrogate key in YYYYMMDD format
- full_date: Actual calendar date
- day_of_week: Day name (Monday, Tuesday, etc.)
- month: Month number (1–12)
- month_name: Month name (January, February, etc.)
- quarter: Quarter of the year (Q1–Q4)
- year: Calendar year
- is_weekend: Boolean flag indicating weekend or weekday

This dimension enables detailed time-based analysis, such as monthly and yearly
sales trends.


### DIMENSION TABLE: dim_product

**Purpose:** Stores descriptive information about products.

**Attributes:**
- product_key (PK): Surrogate key
- product_id: Business key from source system
- product_name: Name of the product
- category: Product category
- subcategory: Product subcategory

The product dimension allows analysis of sales by product type, category, and
subcategory.


### DIMENSION TABLE: dim_customer

**Purpose:** Stores descriptive customer information.

**Attributes:**
- customer_key (PK): Surrogate key
- customer_id: Business key from source system
- customer_name: Full name of the customer
- email: Customer email address
- city: Customer city

The customer dimension supports customer-level sales analysis and segmentation.

## Section 2: Design Decisions

The fact_sales table is designed at the transaction line-item level, where each
row represents a single product sold in a transaction. This granularity was
chosen because it provides the most detailed view of sales data. It allows
FlexiMart to analyze sales at both fine-grained and aggregated levels, such as
individual product performance, order-level analysis, and overall revenue
trends.

Surrogate keys are used instead of natural keys to improve performance and
maintain consistency. Natural keys from source systems may change over time or
contain business meaning, which can complicate joins and historical tracking.
Surrogate keys are system-generated, stable, and optimized for joins in a data
warehouse environment.

This star schema design supports drill-down and roll-up operations by separating
measures from dimensions. Analysts can roll up data to higher levels, such as
monthly or yearly sales, or drill down to daily, product-level, or customer-
level details using the dimension tables.

## Section 3: Sample Data Flow

This section demonstrates how a single sales transaction flows from the source
system into the data warehouse using the star schema design.

### Source Transaction
Order #101  
Customer: John Doe  
Product: Laptop  
Quantity: 2  
Unit Price: 50,000  
Transaction Date: 2024-01-15  


### Data Warehouse Representation

**fact_sales**

{
date_key: 20240115,
product_key: 5,
customer_key: 12,
quantity_sold: 2,
unit_price: 50000,
discount_amount: 0,
total_amount: 100000
}


**dim_date**

{
date_key: 20240115,
full_date: '2024-01-15',
day_of_week: 'Monday',
month: 1,
month_name: 'January',
quarter: 'Q1',
year: 2024,
is_weekend: false
}


**dim_product**

{
product_key: 5,
product_name: 'Laptop',
category: 'Electronics',
subcategory: 'Computing'
}


**dim_customer**

{
customer_key: 12,
customer_name: 'John Doe',
city: 'Mumbai'
}


This example shows how a single sales transaction from the source system is
transformed into a star schema structure in the data warehouse. The fact_sales
table stores measurable metrics, while the dimension tables provide descriptive
context that supports analytical queries and reporting.


