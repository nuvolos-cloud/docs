---
description: Nuvolos supports Airflow 2 as a self-service application
---

# Airflow

For researchers who require scheduled workflows, Nuvolos supports Airflow (2.2.1) as a self-service application. Airflow runs inside a JupyterLab application, making it easy to edit Airflow DAG files, install packages and use the Nuvolos filesystem for data processing.

The JupyterLab application is collaborative, so DAGs can be worked on simultaneously by multiple users in a "Google Docs"-like fashion.

### Configuration

DAGs should be created as Python files in the `/files/airflow/dags` folder, [refer to Airflow documentation](https://airflow.apache.org/docs/apache-airflow/stable/tutorial.html) for an example.

#### Setting up your first DAG

1. Create a new Python file named `/files/airflow/dags/tutorial.py` and copy the contents of the tutorial DAG from [the Airflow tutorial](https://airflow.apache.org/docs/apache-airflow/stable/tutorial.html#example-pipeline-definition).
2. Click on the Airflow tab and click on the All DAGs filter selector on the UI, the DAG should show up on the list like on the screenshot below.
3. Click on the slider toggle next to the `tutorial` DAG name to enable the DAG and start the first execution.
4. You should quickly see that the DAG has executed successfully by seeing a _1_ in a green circle in the _Runs_ column.

![](<../../.gitbook/assets/Screenshot 2021-11-01 at 15.16.59.png>)

Airlfow Connections and Variables can be configured on the Airflow UI.

Airflow on Nuvolos uses a CeleryExecutor back-end to be able to execute tasks in parallel.

### Installing packages

To install packages used in DAGs, simply open a JupyterLab terminal and pip / conda / mamba install the required package.

### Logs

Task execution, scheduler and DAG bag update logs are in `/files/airflow/logs`.





####
