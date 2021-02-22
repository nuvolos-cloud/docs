---
description: >-
  This section provides examples on how to upload datasets to Nuvolos with
  different applications.
---

# Data upload workflow

{% hint style="info" %}
The examples in this section assume that the user is uploading tables to Nuvolos using Nuvolos Applications. Make sure that the table file has been uploaded to Nuvolos. Check the documentation [here](../../getting-started/work-with-files/) for information on file upload.
{% endhint %}

### 1. Python

```python
from nuvolos import get_connection
import pandas as pd

df = pd.read_csv(...) #read your data
con = get_connection()
df.to_sql("TABLE_NAME", con=con, if_exists='replace', index=False, chunksize=10000)
```

### 2. R

```r
df <- read.csv('path_to_data') #read your data
con <- nuvolos::get_connection()
DBI::dbWriteTable(con, name="TABLE_NAME", value=df)
```

### 3. Matlab

```text
df = readtable('path_to_data')
con = get_connection()
sqlwrite(con,'TABLE_NAME',df)
```

