---
description: Nuvolos supports Airflow 2.0 as a self-service application
---

# Airflow

For researchers who require scheduled workflows, Nuvolos supports Airflow (2.0) as a self-service application. Airflow runs inside a JupyterLab application, making it easy to edit DAG files, install packages and use the Nuvolos filesystem for data-processing.

The JupyterLab application is collaborative, so DAGs can be worked on simultaneously by multiple users in a "Google Docs" like fashion.

### Configuration

#### Installing packages

To install packages used in DAGs, simply open a JupyterLab terminal and pip / conda install the required package.

#### Loading a DAG
