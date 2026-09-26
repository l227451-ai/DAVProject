# Olist E-Commerce Data Engineering Pipeline

## Project Overview

This project develops an end-to-end data engineering pipeline for the Brazilian E-Commerce Public Dataset by Olist using Apache Spark and Databricks.

The pipeline follows the Medallion Architecture:

**Bronze → Silver → Gold**

The objective is to ingest raw e-commerce data, clean and transform it, create business-ready analytical datasets, and support BI reporting.

## Data Source

The project uses the Brazilian E-Commerce Public Dataset by Olist.

Source: Kaggle — Brazilian E-Commerce Public Dataset by Olist

The dataset contains approximately 100,000 orders from 2016–2018 and includes information about orders, customers, products, sellers, payments, reviews, and locations.

## Full and Incremental Load Strategy

The original Olist dataset is a static historical dataset rather than a continuously updated production source.

Therefore, this project simulates an incremental ingestion scenario using `order_purchase_timestamp` as the temporal watermark.

### Full Load

Orders purchased on or before:

`2018-05-31 23:59:59`

### Incremental Load

Orders purchased after:

`2018-05-31 23:59:59`

through the end of the available dataset.

The Orders dataset is used as the temporal anchor. Related transactional records are associated with orders through `order_id`.

## Repository Structure

```text
data/
├── full_load/
│   ├── olist_orders_dataset_full.csv
│   ├── olist_order_items_dataset_full.csv
│   ├── olist_order_payments_dataset_full.csv
│   └── olist_order_reviews_dataset_full.csv
│
└── incremental_load/
    ├── olist_orders_dataset_incremental.csv
    ├── olist_order_items_dataset_incremental.csv
    ├── olist_order_payments_dataset_incremental.csv
    └── olist_order_reviews_dataset_incremental.csv

notebooks/
src/
proposal/
```

## Sample Data

The repository contains representative Full Load and Incremental Load samples for development and testing.

The complete source dataset is not stored in this repository. The repository contains only the sample data required for pipeline development.

## Technology Stack

* Apache Spark / PySpark
* Databricks Free Edition
* Python
* GitHub
* Power BI

## Project Architecture

```text
Olist CSV Data
      ↓
   Bronze
      ↓
   Silver
      ↓
    Gold
      ↓
 Power BI
```

## Important Note

The Full/Incremental split is a project simulation based on the historical Olist dataset. The original Olist source does not provide a live incremental API or native change-data-capture stream.

## Team

**Team Members:**

* Rafia Mohsin
* Shanzey Shahid Khan

**Course:** Data Analysis and Visualization

**Instructor:** Amir Iqbal
