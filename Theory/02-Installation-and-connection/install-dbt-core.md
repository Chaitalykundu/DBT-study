# Overview

- [Overview](#overview)
- [Install dbt-core or create a dbt Cloud account](#install-dbt-core-or-create-a-dbt-cloud-account)
- [Step 1 : Install Python (if not already installed)](#step-1--install-python-if-not-already-installed)
- [Step 2 : Install virtual environment](#step-2--install-virtual-environment)
    - [create virtual environment using the following command](#create-virtual-environment-using-the-following-command)
    - [to activate virtual environment](#to-activate-virtual-environment)
- [Step 3: Install dbt-core with an adapter](#step-3-install-dbt-core-with-an-adapter)
- [Step 4: Verify installation](#step-4-verify-installation)

&nbsp;

&nbsp;

&nbsp;

# Install dbt-core or create a dbt Cloud account

To get started with dbt, you have two main options depending on your preference

1. Install dbt-core (for local development)
2. Create a dbt Cloud Account (Managed UI and orchestration)

&nbsp;

&nbsp;

# Step 1 : Install Python (if not already installed)

Make sure `Python 3.8–3.11` is installed. You can check by running:

```bash
python3 --version
```

&nbsp;

&nbsp;

# Step 2 : Install virtual environment

### create virtual environment using the following command

```bash
python -m venv dbt-env
```

or

```bash
python3 -m venv dbt-env
```

&nbsp;

### to activate virtual environment

```bash
dbt-env/scripts/activate
```

&nbsp;

&nbsp;

# Step 3: Install dbt-core with an adapter

Choose your database adapter:

**Postgres**:

```bash
pip install dbt-postgres
```

&nbsp;

Snowflake:

```bash
pip install dbt-snowflake
```

&nbsp;

BigQuery:

```bash
pip install dbt-bigquery
```

&nbsp;

Databricks:

```bash
pip install dbt-databricks
```

&nbsp;

&nbsp;

# Step 4: Verify installation

```bash
dbt --version
```

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;
