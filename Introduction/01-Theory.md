# Overview

- [Overview](#overview)
- [Abbreviation](#abbreviation)
- [DBT](#dbt)
- [Why DBT](#why-dbt)
- [What does dbt do?](#what-does-dbt-do)
- [How does dbt work?](#how-does-dbt-work)
- [Example Workflow](#example-workflow)

&nbsp;

&nbsp;

&nbsp;

# Abbreviation

- DBT = Data Build Tool
- ETL = Extract Transform Load

&nbsp;

&nbsp;

# DBT

DBT is the tool for **_transforming data_** within data warehouse.

It's a command line tool and transformation framework used by data engineers and analysts to transform data in a data warehouse using SQL and some basic Python (for dbt Python models or scripting).

&nbsp;

Data warehouse = any of the modern data platforms like **Snowflake**, **Redshift**, **BigQuery**, **DataBricks**.

DBT only focus on **T** i.e transforming raw data into actionable insights.

The **extraction** of data from source and **loading** raw data into data warehouse are completed using some other tools.

&nbsp;

&nbsp;

# Why DBT

1. <u>**_Affordable:_**</u> DBT is more Affordable

2. <u>**_free open source:_**</u> It offers free open source version

3. <u>**_No specialized skill required:_**</u> DBT primarily uses SQL, which is a familiar language. So no specialized skill requires.

4. <u>**_Takes full advantage of modern cloud data platform:_**</u> Modern cloud data platform like Redshift, BigQuery, Snowflake and DataBricks
   come with significant processing power. With its ETL approach and low local resource requirements DBT take full advantage of these modern cloud
   data platform

5. <u>**_Build-in Features:_**</u> DBT offers several build-in features such as **Version control**, **Automated Testing**, **Document
   Generating**, and **Data lineage visualization**. These features can ensure that the data transformations are reliable and maintainable over time
   even if data volumes and complexity grow.

6. <u>**_Easy Team Collaboration:_**</u> DBT allows large data team to collaborate easily by providing **integrated platform for coding, testing, documentation and development**

&nbsp;

&nbsp;

# What does dbt do?

dbt lets you:

- Write SQL to transform raw data into clean, usable datasets.
- Organize SQL transformations like code (modular, reusable).
- Test and document your data pipelines.
- Version control your transformations (using Git).
- Automatically manage dependencies between data models.

&nbsp;

&nbsp;

# How does dbt work?

- You write SQL models (`SELECT` statements) and save them in `.sql` files.
- dbt compiles those files into `CREATE TABLE AS SELECT` or `CREATE VIEW` statements.
- It runs them on your data warehouse (like `Snowflake`, `BigQuery`, `Redshift`, `Databricks`).
- dbt builds a `DAG` (directed acyclic graph) of all dependencies between models.

&nbsp;

&nbsp;

# Example Workflow

You could have:

- **stg_orders.sql** → stages raw orders data
- **int_orders_cleaned.sql** → intermediate cleaned data
- **fct_orders.sql** → final fact table

&nbsp;

&nbsp;
