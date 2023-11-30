# syntax=quay.io/astronomer/airflow-extensions:latest

FROM quay.io/astronomer/astro-runtime:9.1.0-python-3.9-base

COPY include/astro_provider_snowflake-0.0.0-py3-none-any.whl /tmp

# Create the virtual environment
PYENV 3.8 snowpark requirements-snowpark.txt

# Install packages into the virtual environment
COPY requirements-snowpark.txt /tmp
RUN python3 -m pip install -r /tmp/requirements-snowpark.txt
RUN pip3 install astronomer-providers

RUN python3 -m venv dbt_venv && source dbt_venv/bin/activate && pip install --no-cache-dir dbt-snowflake && pip install --no-cache-dir dbt-postgres && deactivate