# Upload data to Nuvolos

Nuvolos users can import and upload data into their tables. To do so, the user has to use Python via the latest Jupyter image.

## **Data import for small datasets**

If the data to be loaded is small-to-midsize \(&lt;1 million rows\), then the approach is simple and requires a few steps as illustrated below:

```python
from nuvolos import get_connection
import pandas as pd

df = pd.read_csv(...) #read your data

con = get_connection()
df.to_sql("TABLE_NAME", con=con, if_exists='replace', index=False, chunksize=10000)
```

## **Data import for large datasets**

If the data is large,  the above approach would be too slow, as it performs INSERT INTO statements in batches of 10000 records. Nuvolos's alternative approach for large datasets requires the following steps:

1- Start a Jupyter + Python 3.8 app in your Nuvolos instance.

2- Install a version of the database connector library that support bulk loading with Pandas:

```bash
pip uninstall --yes nuvolos
pip uninstall --yes snowflake-connector-python
pip install -I git+https://github.com/nuvolos-cloud/snowflake-connector-python.git#egg=snowflake-connector-python[pandas]
pip install -I nuvolos==0.2.9
```

3- Restart the Jupyter Kernel

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



