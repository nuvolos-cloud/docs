# Access data from applications

Nuvolos is set up so you can reach data stored in Nuvolos from either in-Nuvolos applications or non-Nuvolos applications.

## Accessing data in in-Nuvolos applications

Currently three applications are supported in Nuvolos: Spyder, JupyterLab and RStudio.

### Accessing data from Python in Nuvolos

If you want to use Nuvolos-hosted Python \(via JupyterLab or Spyder\), the data access will be simple:

1. Make sure you have the data available.
2. **Run** your application.
3. Inside your app, you will need to use the [python-connector library](https://github.com/datahub-ac/python-connector) developed by Alphacruncher.

### Accessing data from R in Nuvolos

If you want to use Nuvolos-hosted R \(via RStudio\), the data access will be simple:

1. Make sure you have the data available.
2. **Run** your application.
3. Inside RStudio, you will need to use the [r-connector](https://github.com/datahub-ac/r-connector) developed by Alphacruncher.

## Accessing data in non-Nuvolos applications

Accessing data from out of Nuvolos applications generally consists of the following steps:

1. Set up your database engine connection handler by [installing the Snowflake ODBC driver](setting-up-odbc-drivers.md) or relying on native Snowflake support.
2. [Obtain tokens](obtain-tokens-for-your-data.md) from the Nuvolos web interface.
3. Establish connection.

### Connecting with SAS

In SAS we suggest creating a library of the contents of your instance. To do this, we suggest posing the following statement to SAS:

```text
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

```text
data _null_;
infile 'source/to/file.sql' recfm=f lrecl=32767 pad;
input @1 sqlcode $32767.;
call symputx('sqlcode', sqlcode);
put sqlcode=;
run;
```

The following statement executes the above query:

```text
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



