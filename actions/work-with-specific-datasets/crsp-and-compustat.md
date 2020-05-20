# CRSP and Compustat

## Getting access

In order to get access to a dataset, the organization managers can provide information whether the dataset is currently made available in Nuvolos.

## Accessing data in Nuvolos

If CRSP and Compustat datasets are available to your organization, please see the relevant documentation pages [here](../work-with-data-in-nuvolos/) on accessing data in Nuvolos applications.

## About Compustat and CRSP

 **CRSP Stock and Indexes dataset**: The CRSP US Stock Databases contain daily and monthly market and corporate action data for over 32,000 active and inactive securities with primary listings on the NYSE, NYSE American, NASDAQ, NYSE Arca and Bats exchanges and include CRSP broad market indexes. CRSP databases are characterized by their comprehensive corporate action information and highly accurate total return calculations.  
  
**COMPUSTAT North America**: Compustat North America \(Standard & Poor’s \(McGraw-Hill\)\) is a database of U.S. and Canadian fundamental and market information on more than 24,000 active and inactive publicly held companies. It provides more than 300 annual and 100 quarterly Income Statement, Balance Sheet, Statement of Cash Flows and supplemental data items. If applicable there is a quarterly update.

## Linking Compustat and CRSP

Both datasets assign non-volatile unique identifiers to securities and companies. CRSP tracks the "lifecycle" of a security, through corporate events such as mergers, acquisitions and rebrandings. To match these identifiers, the link table approach is often used. A link table associates unique identifiers of two different sources.

**CRSP** identifiers:

* **PERMNO** and **PERMCO**. These are unique and permanent identifiers, they are never reassigned and do not change during the life history of a stock.
* **CUSIP**: a nine-digit numeric \(e.g., 037833100 for Apple\) or nine-character alphanumeric \(e.g., 38259P508 for Google\) code that identifies a North American financial security. CRSP keeps 8-digits and 9-digits versions of CUSIP. In the 8-digits version, the last digit is removed. A stock's CUSIP can change over time, but is never reassigned.
* **Ticker**: unique identifier assigned to a stock traded on a particular exchange. Tickers can be reassigned.

**COMPUSTAT** identifiers:

* **GVKEY**: a unique and permanent retrieval key assigned to each company \(issue, currency, index\) in the COMPUSTAT database. GVKEYs do not change, and they are not reassigned.
* **CUSIP**: COMPUSTAT keeps the full 9-digits version of CUSIP.
* **Ticker**.

CRSP/COMPUSTAT link generation approaches:

1. Using the CUSIP identifier, present by default in both datasets.
2. Using an identifier linking table provided by the CRSP-COMPUSTAT Merged Database.

### Merging by CUSIP

Without access to the CRSP / Compustat Merged Database, the recommended way of joining security time series data with fundamental data from Compustat is to match records using the CUSIP security identifier, available in both datasets. CUSIP is a nine-character alphanumeric identifier for publicly traded securities, and is administered CUSIP Service Bureau in 1968. Unlike security tickers, CUSIP is not a reusable security identifier. CRSP and Compustat use slightly different approach to keep CUSIP records: CRSP drops the 9th checksum digit in CUSIP and keeps historical CUSIPs in the `NAME_HISTORY` table, while Compustat uses the full 9-digit CUSIP and keeps only the most current CUSIP for each security.

A join query matching the CRSP daily stock prices with Compustat annual gross profits would look like:

```sql
SELECT
    SHI.KYPERMNO,
    SHI.CUSIP,
    TSDP.CALDT,
    ABS(TSDP.PRC) AS PRC,
    FN1.GVKEY,
    FN1.GP
FROM
    SECURITY_HEADER_INFORMATION SHI
INNER JOIN
    TIME_SERIES_DAILY_PRIMARY TSDP
ON
    SHI.KYPERMNO=TSDP.KYPERMNO
-- NOT ALL CRSP RECORDS CAN BE MATCHED TO COMPUSTAT ON CUSIP
LEFT JOIN
    SECURITY SY
ON
    SY.CUSIP=SHI.CUSIP9
LEFT JOIN
    CO_AFND1 FN1
ON
    SY.GVKEY=FN1.GVKEY
AND YEAR(FN1.DATADATE)=YEAR(TSDP.CALDT)
WHERE
    FN1.INDFMT='INDL'
AND FN1.DATAFMT='STD'
AND FN1.POPSRC='D'
AND FN1.CONSOL='C'
ORDER BY
    SHI.KYPERMNO,
    TSDP.CALDT;
```

### Merging by CRSP/COMPUSTAT Merged Database <a id="merging-by-crspcompustat-merged-database"></a>

The vendor database CRSP-COMPUSTAT Merged provides a link table \(`LINK_HISTORY`\) that can be used to merge CRSP with COMPUSTAT with the following information:

* **CCMID**: Compustat's permanent identifier, either `GVKEY` for companies or `GVKEYX` for indexes.
* **LPERMNO**: CRSP `PERMNO` link during link period.
* **LPERMCO**: CRSP `PERMCO` link during link period.
* **LINKTYPE**: A code to describe the type of link between CRSP and COMPUSTAT.
* **LINKDT**: first effective date of the link.
* **LINKENDDT**: last effective date of the link. If `LINKENDDT` is null, this means that the link is still effective.

Merging CRSP and COMPUSTAT using **LINK\_HISTORY**, the following steps are required:

* Choose between CRSP or COMPUSTAT as the first dataset to merge with CRSP-COMPUSTAT. If merging CRSP with CRSP-COMPUSTAT, then the join is done based on `PERMNO`. If merging COMPUSTAT with CRSP-COMPUSTAT, then the join is done based on `GVKEY`. When merging the first dataset with CRSP-COMPUSTAT, both identifiers of CRSP \(`PERMNO`\) and COMPUSTAT \(`GVKEY`\) will be present in the output table.
* Merge the resulting table from the previous step with the second dataset. If the first dataset was CRSP, then merge it with COMPUSTAT on `GVKEY`. Otherwise, merge it with CRSP on `PERMNO`.

  _At all times ensure that the dates from CRSP and COMPUSTAT fall within the LINKDT and LINKENDDT range._

### A worked example using the RStudio app

{% hint style="info" %}
**The code examples below are meant for providing a starting point, but may need to be adjusted depending on the research question. All researchers should review and verify that the code they use is in line with their research questions.**
{% endhint %}

In the following, it will be assumed that the tables have been distributed to the current state of the instance of the example. To distribute data, follow the instructions detailed [here](../work-with-data-in-nuvolos/add-data-to-your-working-instance.md).

#### Designing the query

The suggested workflow is to use the query editor on the UI first to design the query. This step is not compulsory, however it is considered best practice. The steps to perform query design can be found [here](../work-with-data-in-nuvolos/the-table-view.md).

#### The query

In the example. the following tables were distributed to the work instance's current state:

Compustat:

1. `FUNDA` \(Fundamentals Annual\)

CSRP:

1. `MSF` \(Monthly price information\)

CCM \(The merge database\):

1. `CCMXPF_LINKTABLE`

**The first subquery - fundamentals from Compustat:**

We select a couple of fundamentals from `FUNDA` along with the important identifiers `GVKEY` and `DATADATE`. It is important to note that the result of a naive query might contain some duplicate `GVKEY`-`DATADATE` combinations which need to be deduplicated.

A simple query that does basic deduplication is the following:

```sql
SELECT
    DF.GVKEY,
    DF.DATADATE,
    DF.ACCO,
    DF.AJEX,
    DF.CURCD,
    DF.RANK_IN_KEY
FROM
    (
        SELECT DISTINCT
            GVKEY,
            DATADATE,
            ACCO,
            AJEX,
            CURCD,
            ROW_NUMBER() OVER (PARTITION BY GVKEY, DATADATE ORDER BY DATADATE) AS RANK_IN_KEY
        FROM
            FUNDA T
        WHERE
            FYEAR >= 2000
        AND FYEAR <= 2010) DF
WHERE
    DF.RANK_IN_KEY = 1
OR  (
        DF.RANK_IN_KEY > 1
    AND DF.AJEX IS NOT NULL)
```

An alternative would be to use R to run a simple query and have R run the deduplication. This is syntactically simpler, but at this point, the database engine cannot be used to combine large tables, so the R application needs to handle the computational and memory burden:

```r
# Load the pipe operator for more readable code
library(magrittr)

# Standard practice to access data in Nuvolos from R inside the Nuvolos app
# The nuvolos library is pre-installed on Nuvolos R applications.
conn <- nuvolos::get_connection()
result_data <- dbGetQuery(conn,"SELECT
    GVKEY,
    DATADATE,
    ACCO,
    AJEX,
    CURCD
FROM
    FUNDA
WHERE
    FYEAR >= 2000
AND FYEAR <= 2010")

# Simple deduplicate using dplyr::distinct
result_data_dedup <- result_data %>% dplyr::distinct(GVKEY, DATADATE, .keep_all = TRUE)

```

**The second subquery - using the linking table:**

The following is a simplified possible query of the linking logic. The first table named `INP` is just the result of the previously presented query. This is joined together based on `GVKEY` with the linking table. Some care is needed, due to the fact that a link between a `GVKEY` and `PERMNO` can be transient - hence the linking happens only for timestamps that fall in the linking period. More complicated logics can be implemented using overlap intervals. For the appropriate choice of `LINKTYPE`, consult the dataset documentation, the present version is a standard choice.

```sql
SELECT
    INP.*,
    LT.LPERMNO,
    LT.LINKPRIM,
    LT.LINKDT,
    LT.LINKENDDT
FROM
    (
        SELECT
            DF.GVKEY,
            DF.DATADATE,
            DF.ACCO,
            DF.AJEX,
            DF.CURCD,
            DF.RANK_IN_KEY
        FROM
            (
                SELECT DISTINCT
                    GVKEY,
                    DATADATE,
                    ACCO,
                    AJEX,
                    CURCD,
                    ROW_NUMBER() OVER (PARTITION BY GVKEY, DATADATE ORDER BY DATADATE) AS
                    RANK_IN_KEY
                FROM
                    FUNDA T
                WHERE
                    FYEAR >= 2000
                AND FYEAR <= 2010) DF
        WHERE
            DF.RANK_IN_KEY = 1
        OR  (
                DF.RANK_IN_KEY > 1
            AND DF.AJEX IS NOT NULL) ) INP
INNER JOIN
    CCMXPF_LINKTABLE LT
ON
    LT.GVKEY = INP.GVKEY
AND (
        INP.DATADATE >= LT.LINKDT
    OR  LT.LINKDT IS NULL)
AND (
        INP.DATADATE <= LT.LINKENDDT
    OR  LT.LINKDT IS NULL)
WHERE
    LT.LINKTYPE IN ('LU',
                    'LC')
```

Based on flavour and use-case, additional deduplication might be necessary as there might be multiple `PERMNO` matches for a `GVKEY`. This is easiest to be done using the previously presented syntax in R, however this involves the drawback of not being able to run later join operations using the database engine.

#### Putting it together with CRSP

The last step of the merging process is to take a CRSP table with PERMNO identifiers and join it using the result of the previous query. The `MSF` table contains monthly pricing information and the bid/ask average `PRC` is queried in this toy example.

```sql
SELECT
    FUNDLINK.*,
    MSF.PRC
FROM
    (
        SELECT
            INP.*,
            LT.LPERMNO,
            LT.LINKPRIM,
            LT.LINKDT,
            LT.LINKENDDT
        FROM
            (
                SELECT
                    DF.GVKEY,
                    DF.DATADATE,
                    DF.ACCO,
                    DF.AJEX,
                    DF.CURCD,
                    DF.RANK_IN_KEY
                FROM
                    (
                        SELECT DISTINCT
                            GVKEY,
                            DATADATE,
                            ACCO,
                            AJEX,
                            CURCD,
                            ROW_NUMBER() OVER (PARTITION BY GVKEY, DATADATE ORDER BY DATADATE) AS
                            RANK_IN_KEY
                        FROM
                            FUNDA T
                        WHERE
                            FYEAR >= 2000
                        AND FYEAR <= 2010) DF
                WHERE
                    DF.RANK_IN_KEY = 1
                OR  (
                        DF.RANK_IN_KEY > 1
                    AND DF.AJEX IS NOT NULL) ) INP
        INNER JOIN
            CCMXPF_LINKTABLE LT
        ON
            LT.GVKEY = INP.GVKEY
        AND (
                INP.DATADATE >= LT.LINKDT
            OR  LT.LINKDT IS NULL)
        AND (
                INP.DATADATE <= LT.LINKENDDT
            OR  LT.LINKDT IS NULL)
        WHERE
            LT.LINKTYPE IN ('LU',
                            'LC') ) FUNDLINK
INNER JOIN
    MSF
ON
    MSF.PERMNO = FUNDLINK.LPERMNO
AND YEAR(MSF.DATE) = YEAR(FUNDLINK.DATADATE)
AND MONTH(MSF.DATE) = MONTH(FUNDLINK.DATADATE)
```

To minimize the memory footprint of an application, it is thus suggested to run the above query in R in the following manner:

```r
# Load the pipe operator for more readable code
library(magrittr)

# Standard practice to access data in Nuvolos from R inside the Nuvolos app
# The nuvolos library is pre-installed on Nuvolos R applications.
conn <- nuvolos::get_connection()
result_data <- dbGetQuery(conn,"SELECT
    FUNDLINK.*,
    MSF.PRC
FROM
    (
        SELECT
            INP.*,
            LT.LPERMNO,
            LT.LINKPRIM,
            LT.LINKDT,
            LT.LINKENDDT
        FROM
            (
                SELECT
                    DF.GVKEY,
                    DF.DATADATE,
                    DF.ACCO,
                    DF.AJEX,
                    DF.CURCD,
                    DF.RANK_IN_KEY
                FROM
                    (
                        SELECT DISTINCT
                            GVKEY,
                            DATADATE,
                            ACCO,
                            AJEX,
                            CURCD,
                            ROW_NUMBER() OVER (PARTITION BY GVKEY, DATADATE ORDER BY DATADATE) AS
                            RANK_IN_KEY
                        FROM
                            FUNDA T
                        WHERE
                            FYEAR >= 2000
                        AND FYEAR <= 2010) DF
                WHERE
                    DF.RANK_IN_KEY = 1
                OR  (
                        DF.RANK_IN_KEY > 1
                    AND DF.AJEX IS NOT NULL) ) INP
        INNER JOIN
            CCMXPF_LINKTABLE LT
        ON
            LT.GVKEY = INP.GVKEY
        AND (
                INP.DATADATE >= LT.LINKDT
            OR  LT.LINKDT IS NULL)
        AND (
                INP.DATADATE <= LT.LINKENDDT
            OR  LT.LINKDT IS NULL)
        WHERE
            LT.LINKTYPE IN ('LU',
                            'LC') ) FUNDLINK
INNER JOIN
    MSF
ON
    MSF.PERMNO = FUNDLINK.LPERMNO
AND YEAR(MSF.DATE) = YEAR(FUNDLINK.DATADATE)
AND MONTH(MSF.DATE) = MONTH(FUNDLINK.DATADATE);")

### Additional operations on the result set
```

### An alternative solution

Compared to the previous route, it is possible to directly link CRSP and COMPUSTAT vendor tables without using any derived entities such as `MSF` or `FUNDA`.

The below query provides an example of doing this, it is assumed that `TIME_SERIES_DAILY_PRIMARY,` `LINK_HISTORY` and `CO_AFND1` tables are available in the working instance's current state. 

```sql
SELECT
    TS.CALDT    AS DATE,
    TS.KYPERMNO AS PERMNO,
    FN.GVKEY,
    ABS(TS.PRC) AS PRC,
    FN.EPSFX    AS EPS
FROM
    LINK_HISTORY AS L
INNER JOIN
    TIME_SERIES_DAILY_PRIMARY AS TS
ON
    L.LPERMNO = TS.KYPERMNO
LEFT JOIN
    CO_AFND1 AS FN
ON
    FN.GVKEY = L.CCMID
AND FN.DATAFMT='STD'
AND FN.CONSOL='C'
AND FN.POPSRC='D'
AND FN.DATADATE BETWEEN TO_DATE(L.LINKDT::VARCHAR, 'YYYYMMDD') AND TO_DATE(NULLIF(L.LINKENDDT::
    VARCHAR, '99999999'), 'YYYYMMDD')
AND FN.DATADATE = TS.CALDT
ORDER BY
    PERMNO,
    DATE;
```

In order to run this query and assign it do a data.frame object in R, the following snippet can be used.

```sql
# Standard practice to access data in Nuvolos from R inside the Nuvolos app
# The nuvolos library is pre-installed on Nuvolos R applications.
conn <- nuvolos::get_connection()
result_data <- dbGetQuery(conn,"SELECT
    TS.CALDT    AS DATE,
    TS.KYPERMNO AS PERMNO,
    FN.GVKEY,
    ABS(TS.PRC) AS PRC,
    FN.EPSFX    AS EPS
FROM
    LINK_HISTORY AS L
INNER JOIN
    TIME_SERIES_DAILY_PRIMARY AS TS
ON
    L.LPERMNO = TS.KYPERMNO
LEFT JOIN
    CO_AFND1 AS FN
ON
    FN.GVKEY = L.CCMID
AND FN.DATAFMT='STD'
AND FN.CONSOL='C'
AND FN.POPSRC='D'
AND FN.DATADATE BETWEEN TO_DATE(L.LINKDT::VARCHAR, 'YYYYMMDD') AND TO_DATE(NULLIF(L.LINKENDDT::
    VARCHAR, '99999999'), 'YYYYMMDD')
AND FN.DATADATE = TS.CALDT
ORDER BY
    PERMNO,
    DATE;")
```




