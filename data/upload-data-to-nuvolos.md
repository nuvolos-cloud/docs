# Upload table data to Nuvolos

#### Nuvolos users can import and upload data into their tables. To do so, the user has a number of options which are illustrated below.

{% hint style="info" %}
Before proceeding, please consider if your use-case is well suited for loading table data into Nuvolos. Table data has a number of advantages, especially in the following use-cases:

* **Combining with other datasets**: if you are combining a dataset with other datasets on Nuvolos that come in a table format, it is often easiest to do the joins directly via SQL statements.
* **Cross-application compatibility**: tables provide a cross-application typed data structure that can make data easier to analyze with multiple applications.
* **Large dataset support**: tables support data volumes that are sometimes difficult to efficiently store in regular files.

If none of the above benefits are essential, then storing data in files is often the simpler solution.
{% endhint %}

### \*\*\*\*

### 1. Uploading data programmatically

{% hint style="info" %}
The examples below assume that the user is uploading tables to Nuvolos using Nuvolos Applications. Make sure that the table file has been uploaded to Nuvolos. Check the documentation [here](../getting-started/work-with-files/) for information on file upload.
{% endhint %}

#### 1. Python

**Instead of Pandas's `df.to_sql`, use `nuvolos.to_sql`** , which has a similar signature but uses highly efficient bulk data loading. `df.to_sql` is not supported in Python applications running on Nuvolos. 

{% hint style="info" %}
**We strongly recommend using lowercase Pandas DataFrame column and index names and a lowercase table name when uploading tables to Nuvolos in order for the resulting database table name and column name to be case-insensitive.**

Using uppercase or mixed-case DataFrame column or index names can lead to inconsistent DataFrame column names when reading data with `pandas.read_sql`, depending on whether the code is run on- or off-Nuvolos. 
{% endhint %}



```python
from nuvolos import get_connection, to_sql
import pandas as pd

df = pd.read_csv(...) #read your data
con = get_connection()
to_sql(df=df, name="table_name", con=con, if_exists='replace', index=False)
```

If you wish to upload data to Nuvolos from your own PC, please follow the [instructions on how to obtain connection tokens](https://docs.nuvolos.cloud/data/access-data-from-applications#connecting-with-python) and the database name and schema name to use:

```python
from nuvolos import get_connection, to_sql
import pandas as pd

df = pd.read_csv(...) #read your data
con = get_connection(dbname = "dbname", schemaname="schemaname")
to_sql(df=df, name="table_name", con=con, if_exists='replace', index=False)
```

{% hint style="info" %}
The above example assumes the use of the latest \(&gt;= 0.4.1\) version of the`nuvolos-odbc` \(for use in Nuvolos applications\) or `nuvolos`package \(for off-Nuvolos use on your local PC\) from PyPI.
{% endhint %}

To update to the latest `nuvolos-odbc` \(for use in Nuvolos applications\) or `nuvolos` package \(for off-Nuvolos use\), please execute the following commands in your Python environment:

In existing, older Nuvolos Python applications:

```bash
pip uninstall nuvolos
pip install --upgrade nuvolos-odbc
```

Off-Nuvolos, on your local PC:

```text
pip install --upgrade nuvolos
```

#### 2. R

```r
df <- read.csv('path_to_data') #read your data
con <- nuvolos::get_connection()
DBI::dbWriteTable(con, name="table_name", value=df)
```

If you wish to upload data to Nuvolos from your own PC, please follow the [instructions on how to obtain connection tokens](https://docs.nuvolos.cloud/data/access-data-from-applications#connecting-with-r) and the database name and schema name to use:

```python
df <- read.csv('path_to_data') #read your data
nuvolos::to_sql(df=df, name="table_name", dbname="dbname", schemaname="schemaname", if_exists='replace', index=FALSE)
```

#### 3. Matlab

```text
df = readtable('path_to_data')
con = get_connection()
sqlwrite(con,'TABLE_NAME',df)
```

### 2. Using Excel

To upload data to Nuvolos using Excel, please refer to our instructions on [accessing and uploading data with Excel.](https://docs.nuvolos.cloud/data/access-data-from-applications#connecting-with-excel)

### 3. Support request

If you have a specific data onboarding task that you want to discuss with us, you can open a support request by sending an email to **support@nuvolos.cloud.**

