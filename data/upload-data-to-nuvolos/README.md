# Upload tables to Nuvolos

#### Nuvolos users can import and upload data into their tables. To do so, the user has a number of options which are illustrated below.

{% hint style="info" %}
Before proceeding, please consider if your use-case is well suited for loading table data into Nuvolos. Table data has a number of advantages, especially in the following use-cases:

* **Combining with other datasets**: if you are combining a dataset with other datasets on Nuvolos that come in a table format, it is often easiest to do the joins directly via SQL statements.
* **Cross-application compatibility**: tables provide a cross-application typed data structure that can make data easier to analyze with multiple applications.
* **Large dataset support**: tables support data volumes that are sometimes difficult to efficiently store in regular files.

If none of the above benefits are essential, then storing data in files is often the simpler solution.
{% endhint %}

### **1. Data import for small datasets**

If you want to import moderate data sizes  \(&lt;1 million rows\) into Nuvolos, the current avenue is to do it through applications. Read and format the data in the app and then you can write it to the tables using any of the application scripts provided [here](small-data-upload-scripts.md). 

### **2. Data import for large datasets**

If the data is large,  the above approach would be too slow, as it performs INSERT INTO statements in batches of 10000 records. Nuvolos's alternative approach for large datasets requires the following steps:

1- Start a Jupyter + Python 3.8 app in your Nuvolos instance.

2- Install a version of the database connector library that support bulk loading with Pandas:

```bash
pip uninstall --yes nuvolos
pip uninstall --yes snowflake-connector-python
pip install -I git+https://github.com/nuvolos-cloud/snowflake-connector-python.git#egg=snowflake-connector-python[pandas]
pip install -I nuvolos==0.2.9
```

3- Restart the Jupyter Kernel.

4- Get a database connection with:

```python
import pandas
from snowflake.connector.pandas_tools import pd_writer
from nuvolos import get_engine
```

5- Read the large CSV file in chunks and bulk load the chunks into the database:

```python
engine = get_engine()
for df in pd.read_csv("/files/large_csv_sample.csv", chunksize=10000000):
    df.to_sql("table_name", engine, if_exists="append", 
              index=False, method=pd_writer)
```

### 

### 3. Using Excel

To upload data to Nuvolos using Excel, please refer to our instructions on [accessing and uploading data with Excel.](https://docs.nuvolos.cloud/data/access-data-from-applications#connecting-with-excel)

### 4. Support request

If you have a specific data onboarding task that you want to discuss with us, you can open a support request by sending an email to **support@nuvolos.cloud.**
