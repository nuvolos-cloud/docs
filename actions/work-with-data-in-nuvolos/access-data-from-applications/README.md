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

### 





