# Overview

- [Overview](#overview)
- [Models](#models)
- [Jinja + SQL (Templating)](#jinja--sql-templating)
- [ref() Function](#ref-function)
- [Materializations](#materializations)
- [Sources](#sources)
- [Tests](#tests)
- [Documentation](#documentation)
- [Seeds](#seeds)
- [Snapshots](#snapshots)
- [Macros](#macros)
- [Typical dbt Workflow](#typical-dbt-workflow)

&nbsp;

&nbsp;

&nbsp;

# Models

- **What**: SQL files that define a transformation step (like a SELECT query).

- **Stored as**: `.sql` files in the `models/` folder.

- Example:

  ```sql
  -- models/stg_customers.sql
  SELECT id, name, email FROM raw.customers;
  ```

- **Run with**: `dbt run`
  This compiles the SQL and runs it on your warehouse (like Snowflake, BigQuery, etc.).

&nbsp;

&nbsp;

# Jinja + SQL (Templating)

- dbt uses Jinja templating on top of SQL.

- You can reuse code, add logic, or dynamically reference models.

- Example:

  ```sql
  SELECT * FROM {{ ref('stg_customers') }}
  ```

&nbsp;

&nbsp;

# ref() Function

- `ref('model_name')` tells dbt:

  - The model depends on another model.
  - dbt manages dependencies and execution order.

- It also helps with lineage graphs.

&nbsp;

&nbsp;

# Materializations

- Determines how dbt builds a model in your warehouse:

  - **view** (default): a simple SQL view
  - **table**: persists data as a table
  - **incremental**: only new/changed data is processed
  - **ephemeral**: temporary models for use in other models (not materialized)

&nbsp;

&nbsp;

# Sources

- Declare raw tables as sources, so they are trackable and testable.

- Example:

  ```yaml
  sources:
    - name: raw
      tables:
        - name: customers
  ```

&nbsp;

&nbsp;

# Tests

- You can write data quality tests like:

  - not_null
  - unique
  - relationships

- Custom tests also possible in SQL.

- Example:

  ```yaml
  - name: stg_customers
    columns:
      - name: id
        tests:
          - not_null
          - unique
  ```

&nbsp;

&nbsp;

# Documentation

- Auto-generate documentation using:

  ```bash
  dbt docs generate
  dbt docs serve
  ```

- You get lineage graphs, model descriptions, and test coverage.

&nbsp;

&nbsp;

# Seeds

- Static CSV files loaded into your warehouse as tables.
- Useful for lookups, mappings, or test data.

&nbsp;

&nbsp;

# Snapshots

- Capture slowly changing dimensions (SCDs).
- Useful when source data changes but you want to keep history.

&nbsp;

&nbsp;

# Macros

- Reusable SQL snippets/functions using Jinja.
- Define once, use many times.

&nbsp;

&nbsp;

# Typical dbt Workflow

- Define sources
- Create models (staging → intermediate → marts)
- Add tests & documentation
- Run dbt (`dbt run`, `dbt test`)
- Schedule with dbt Cloud or orchestrators like Airflow
