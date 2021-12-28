# Access table data from applications

Nuvolos is set up so you can access your data tables stored in Nuvolos from either in-Nuvolos applications or external, non-Nuvolos applications.

## Accessing data from applications running in Nuvolos

Currently three applications are supported in Nuvolos: Spyder, JupyterLab and RStudio.

### Accessing data tables from Python in Nuvolos

If you want to use Nuvolos-hosted Python (via JupyterLab or Spyder), the data access will be simple:

1. Make sure you have the data available.
2. **Run** your application.
3. Inside your app, you will need to use the `nuvolos` [Python library](https://github.com/nuvolos-cloud/python-connector) developed by Alphacruncher, which is pre-installed in the Jupyter application

Usage example:

```python
from nuvolos import get_engine
import pandas as pd

engine = get_engine()
df = pd.read_sql("SELECT * FROM table", con=engine)
```

### Accessing data tables from R in Nuvolos

If you want to use Nuvolos-hosted R (via RStudio), the data access will be simple:

1. Make sure you have the data available.
2. **Run** your application.
3. Inside RStudio, you will need to use the [r-connector](https://github.com/nuvolos-cloud/r-connector) developed by Alphacruncher.

Usage example:

```r
con <- nuvolos::get_connection()
result_data <- dbGetQuery(conn,"SELECT * FROM table LIMIT 10")
```

## Accessing data tables from external, non-Nuvolos applications

### Connecting with R

First, please download and install the [Snowflake ODBC database driver](https://docs.snowflake.com/en/user-guide/odbc.html) for your platform, which is required to access the Nuvolos database service. You do not need to create a named data source.

Once the ODBC driver is installed, please install the Nuvolos `r-connector` package developed by Alphacruncher:

```r
install.packages("remotes")
remotes::install_github("nuvolos-cloud/r-connector")
```

Next,  [obtain access tokens](obtain-tokens-for-your-data.md) and database/schema names from the Connection Guide on the Nuvolos _Tables_ interface of the instance you wish to access:

![Connection Guide](https://gblobscdn.gitbook.com/assets%2F-LihBjXi93rsUENhHsab%2F-M2cRBfkOEK87ab37B2l%2F-M2cRkQS\_MidAHIPoC3K%2FScreen%20Shot%202020-03-17%20at%201.22.49%20PM.png)

Finally, pass the username, password, database name and schema name to the `get_connection()` function:

```r
con <- get_connection(username = "my_user", password = "my_password", 
                      dbname = "my_database", schemaname= "my_schema")
result_data <- dbGetQuery(conn,"SELECT * FROM table LIMIT 10")
```

### Connecting with Python

First, install the `nuvolos` package developed by Alphacruncher:

```bash
pip install nuvolos
```

Next,  [obtain access tokens](obtain-tokens-for-your-data.md) and database/schema names from the Connection Guide on the Nuvolos _Tables_ interface of the instance you wish to access:

![](broken-reference)

Finally, pass the username/password and database/schema specified in the _Connection Guide_ to the get\_engine() function:

```python
from nuvolos import get_engine
import pandas as pd

engine = get_engine(username="username", password = "password", 
                    dbname = "dbname", schemaname="schemaname")
df = pd.read_sql("SELECT * FROM table", con=engine)
```

### Connecting with SAS

Accessing data from out-of-Nuvolos SAS applications consists of the following steps:

1. Install[ the Snowflake ODBC driver](setting-up-odbc-drivers.md).
2. [Obtain access tokens](obtain-tokens-for-your-data.md) and database/schema names from the Connection Guide on the Nuvolos tables interface.
3. Establish connection.

In SAS we suggest creating a library of the contents of your instance. To do this, we suggest posing the following statement to SAS:

```
libname NUVOLOS odbc complete="DRIVER={SnowflakeDSIIDriver};
SERVER=alphacruncher.eu-central-1.snowflakecomputing.com;
UID=<USER NAME>;
PWD=<PASSWORD>" qualifier="<DATABASE NAME>" schema="<SCHEMA NAME>" 
dbcommit=200000 autocommit=no preserve_col_names=yes preserve_tab_names=yes
readbuff=32000 insertbuff=32000;
```

In the above example `<USER NAME>, <PASSWORD>` can be learned from [obtaining your tokens](obtain-tokens-for-your-data.md), and `<DATABASE NAME>, <SCHEMA NAME>` can be learned by [finding your database and schema path](find-your-database-and-schema-path.md).

#### Running a query from a query file with SAS

Assuming you have composed an SQL query that you would like to run in SAS, and saved it in the file `source/to/file.sql`. The following code puts the SQL statement in the file to a macro named  `sqlcode` in SAS:

```
data _null_;
infile 'source/to/file.sql' recfm=f lrecl=32767 pad;
input @1 sqlcode $32767.;
call symputx('sqlcode', sqlcode);
put sqlcode=;
run;
```

The following statement executes the above query:

```
proc sql;
	connect using NUVOLOS;
	select * from connection to NUVOLOS(
		USE SCHEMA "<DATABASE NAME>"."<SCHEMA NAME>";
	);
	create table test as select * from connection to NUVOLOS(
		&sqlcode
	);
quit;
```

To analyze the above SAS statement, notice the following:

1. We are using the SAS SQL Procedure Pass-Through Facility twice.
2. The first statement makes sure that SAS connects to the correct database and schema. We strongly suggest using this statement first whenever you are using the Pass-Through Facility.
3. The second statement creates a table called `test` based on the code that is in the file `source/to/file.sql.`

