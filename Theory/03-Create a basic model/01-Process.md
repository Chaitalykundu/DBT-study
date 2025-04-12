# Overview

- [Overview](#overview)
- [Introduction](#introduction)
- [Steps to create a basic model](#steps-to-create-a-basic-model)
    - [1. Navigate to your dbt project folder](#1-navigate-to-your-dbt-project-folder)
    - [2. Go to the models directory](#2-go-to-the-models-directory)
    - [3. Create a model file](#3-create-a-model-file)
    - [4. Add a source or seed](#4-add-a-source-or-seed)
    - [5. Add this seed to `dbt_project.yml`](#5-add-this-seed-to-dbt_projectyml)
    - [6. run the seed file](#6-run-the-seed-file)
    - [6. Run the model](#6-run-the-model)
    - [7. Check the output](#7-check-the-output)

&nbsp;

&nbsp;

&nbsp;

# Introduction

A dbt model is essentially just a SQL `SELECT` statement saved as a `.sql` file, and dbt will materialize it as a table/view in your data warehouse.

&nbsp;

&nbsp;

# Steps to create a basic model

### 1. Navigate to your dbt project folder

```bash
 cd <DBT_PROJECT_NAME>
```

&nbsp;

### 2. Go to the models directory

models live in the `/models` folder

&nbsp;

### 3. Create a model file

For example, create a file named `customers.sql`:

```sql
-- models/customers.sql
SELECT
  id,
  first_name,
  last_name,
  email,
  created_at
FROM {{ ref('raw_customers') }}
WHERE email IS NOT NULL;
```

&nbsp;

### 4. Add a source or seed

If any reference or source table doesn’t exist, you can create a basic `seed` or another model to simulate it.

Create a CSV file for seed in `raw_customers.csv` in `seeds` folder:

```csv
id,first_name,last_name,email,created_at
1,John,Doe,john.doe@example.com,2022-01-01
2,Jane,Smith,,2022-02-01
```

&nbsp;

### 5. Add this seed to `dbt_project.yml`

```yml
seeds:
  my_project: # Project name
    customer:   # table name
      file: raw_customers.csv
```

&nbsp;

### 6. run the seed file

```bash
dbt seed
```

&nbsp;

### 6. Run the model

```bash
dbt run
```

&nbsp;

### 7. Check the output

This creates a table/view in your data warehouse under the configured schema, like details.customers.
