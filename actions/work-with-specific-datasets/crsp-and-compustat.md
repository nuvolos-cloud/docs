# CRSP and Compustat

## Getting access

In order to get access to a dataset, the organization managers can provide information whether the dataset is currently made available in Nuvolos.

## Accessing data in Nuvolos

In order to access data in Nuvolos, please refer to the specific documentation pages [here](../work-with-data-in-nuvolos/).

## About Compustat and CRSP

Combining data from the Compustat and CRSP databases is a standard operation as CRSP contains security price information, while Compustat features information on fundamentals. The detailed documentation for each dataset can be found in the respective dataset spaces if the organization has access.

## Linking Compustat and CRSP

To join CRSP with COMPUSTAT, the link table approach is often used. A link table associates unique identifiers of two different sources.

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
2. Using the link table provided by the CRSP-COMPUSTAT merged database.

### Merging by CUSIP

Merging CRSP and COMPUSTAT using CUSIP, the following steps are required:

* From the CRSP database, get stock identifiers from table NAME\_HISTORY. This table contains information on identifiers such as PERMNO and CUSIP, as well as other codes. The start date \(column NAMEDT\) and end date \(column NAMEENDDT\) define the period for which a particular stock identifier was valid. If NAMEENDDT is not available, this means that the stock data in NAME\_HISTORY is still accurate until the most recent date in the dataset.
* From COMPUSTAT, select a table that contains the CUSIP identifiers to merge it with the table NAME\_HISTORY in CRSP. Merging based on the CUSIP identifier requires dates from COMPUSTAT and CRSP to fall within the temporal interval defined by NAMEDT and NAMEENDDT.

### Merging by CRSP/COMPUSTAT Merged Database <a id="merging-by-crspcompustat-merged-database"></a>

The vendor database CRSP-COMPUSTAT Merged provides a link table \(**LINK\_HISTORY**\) that can be used to merge CRSP with COMPUSTAT with the following information:

* **CCMID**: Compustat's permanent identifier, either GVKEY for companies or GVKEYX for indexes.
* **LPERMNO**: CRSP PERMNO link during link period.
* **LPERMCO**: CRSP PERMCO link during link period.
* **LINKTYPE**: A code to describe the type of link between CRSP and COMPUSTAT.
* **LINKDT**: first effective date of the link.
* **LINKENDDT**: last effective date of the link. If LINKENDDT is null, this means that the link is still effective.

Merging CRSP and COMPUSTAT using **LINK\_HISTORY**, the following steps are required:

* Choose between CRSP or COMPUSTAT as the first dataset to merge with CRSP-COMPUSTAT. If merging CRSP with CRSP-COMPUSTAT, then the join is done based on PERMNO. If merging COMPUSTAT with CRSP-COMPUSTAT, then the join is done based on GVKEY. When merging the first dataset with CRSP-COMPUSTAT, both identifiers of CRSP \(PERMNO\) and COMPUSTAT \(GVKEY\) will be present in the output table.
* Merge the resulting table from the previous step with the second dataset. If the first dataset was CRSP, then merge it with COMPUSTAT on GVKEY. Otherwise, merge it with CRSP on PERMNO.

  _At all times ensure that the dates from CRSP and COMPUSTAT fall within the LINKDT and LINKENDDT range._

### A worked example using the RStudio app

In the following, it will be assumed that the tables have been distributed to the current state of the instance of the example. To distribute data, follow the instructions detailed [here](../work-with-data-in-nuvolos/add-data-to-your-working-instance.md).

#### Designing the query

The suggested workflow is to use the query editor on the UI first to design the query. This step is not compulsory, however it is considered best practice. The steps to perform query design can be found [here](../work-with-data-in-nuvolos/the-table-view.md).

#### The query

In the example. the following tables were distributed to the work instance's current state:

Compustat:

1. FUNDA \(Fundamentals Annual\)

CSRP:

1. MSF \(Monthly price information\)

CCM \(The merge database\):

1. CCMXPF\_LINKTABLE

**The first subquery - fundamentals from Compustat:**

We select a couple of fundamentals from FUNDA along with the important identifiers GVKEY and DATADATE. It is important to note that the result of a naive query might contain some duplicate GVKEY-DATADATE combinations which need to be deduplicated.

A simple query that does basic deduplication is the following:

```sql
SELECT DF.GVKEY, DF.DATADATE, DF.ACCO, DF.AJEX, DF.CURCD, DF.RANK_IN_KEY FROM 
(SELECT DISTINCT GVKEY, DATADATE, ACCO, AJEX, CURCD, ROW_NUMBER() OVER (PARTITION BY GVKEY, DATADATE ORDER BY DATADATE) AS RANK_IN_KEY 
FROM FUNDA T
WHERE FYEAR >= 2000 AND FYEAR <= 2010) DF
WHERE DF.RANK_IN_KEY = 1 OR (DF.RANK_IN_KEY > 1 AND DF.AJEX IS NOT NULL)
```

An alternative would be to use R to run a simple query and have R run the deduplication. This is syntactically simpler, but at this point, the database engine cannot be used to combine large tables, so the R application needs to handle the computational and memory burden:

```r
# Load the pipe operator for more readable code
library(magrittr)

# Standard practice to access data in Nuvolos from R inside the Nuvolos app
# The nuvolos library is pre-installed on Nuvolos R applications.
conn <- nuvolos::get_connection()
result_data <- dbGetQuery(conn,"SELECT GVKEY, DATADATE, ACCO, AJEX, CURCD FROM FUNDA WHERE FYEAR >= 2000 AND FYEAR <= 2010")

# Simple deduplicate using dplyr::distinct
result_data_dedup <- result_data %>% dplyr::distinct(GVKEY, DATADATE, .keep_all = TRUE)

```

**The second subquery - using the linking table:**

The following is a simplified possible query of the linking logic. The first table named `INP` is just the result of the previously presented query. This is joined together based on `GVKEY` with the linking table. Some care is needed, due to the fact that a link between a `GVKEY` and `PERMNO` can be transient - hence the linking happens only for timestamps that fall in the linking period. More complicated logics can be implemented using overlap intervals. For the appropriate choice of `LINKTYPE`, consult the dataset documentation, the present version is a standard choice.

```sql
SELECT  INP.*, LT.LPERMNO, LT.LINKPRIM, LT.LINKDT, LT.LINKENDDT FROM
    (SELECT DF.GVKEY, DF.DATADATE, DF.ACCO, DF.AJEX, DF.CURCD, DF.RANK_IN_KEY FROM 
        (SELECT DISTINCT GVKEY, DATADATE, ACCO, AJEX, CURCD, ROW_NUMBER() OVER (PARTITION BY GVKEY, DATADATE ORDER BY DATADATE) AS RANK_IN_KEY 
        FROM FUNDA T
        WHERE FYEAR >= 2000 AND FYEAR <= 2010) DF
    WHERE DF.RANK_IN_KEY = 1 OR (DF.RANK_IN_KEY > 1 AND DF.AJEX IS NOT NULL) ) INP
INNER JOIN CCMXPF_LINKTABLE LT
ON LT.GVKEY = INP.GVKEY AND 
    (INP.DATADATE >= LT.LINKDT OR LT.LINKDT IS NULL) AND 
    (INP.DATADATE <= LT.LINKENDDT OR LT.LINKDT IS NULL)
WHERE LT.LINKTYPE IN ('LU', 'LC')
```

Based on flavour and use-case, additional deduplication might be necessary as there might be multiple `PERMNO` matches for a `GVKEY`. This is easiest to be done using the previously presented syntax in R, however this involves the drawback of not being able to run later join operations using the database engine.

#### Putting it together with CRSP

The last step of the merging process is to take a CRSP table with PERMNO identifiers and join it using the result of the previous query. The `MSF` table contains monthly pricing information and the bid/ask average `PRC` is queried in this toy example.

```sql
SELECT FUNDLINK.*, MSF.PRC FROM
        (SELECT  INP.*, LT.LPERMNO, LT.LINKPRIM, LT.LINKDT, LT.LINKENDDT FROM
        (SELECT DF.GVKEY, DF.DATADATE, DF.ACCO, DF.AJEX, DF.CURCD, DF.RANK_IN_KEY FROM 
            (SELECT DISTINCT GVKEY, DATADATE, ACCO, AJEX, CURCD, ROW_NUMBER() OVER (PARTITION BY GVKEY, DATADATE ORDER BY DATADATE) AS RANK_IN_KEY 
            FROM FUNDA T
            WHERE FYEAR >= 2000 AND FYEAR <= 2010) DF
        WHERE DF.RANK_IN_KEY = 1 OR (DF.RANK_IN_KEY > 1 AND DF.AJEX IS NOT NULL) ) INP
    INNER JOIN CCMXPF_LINKTABLE LT
    ON LT.GVKEY = INP.GVKEY AND 
        (INP.DATADATE >= LT.LINKDT OR LT.LINKDT IS NULL) AND 
        (INP.DATADATE <= LT.LINKENDDT OR LT.LINKDT IS NULL)
    WHERE LT.LINKTYPE IN ('LU', 'LC') ) FUNDLINK
INNER JOIN MSF
ON MSF.PERMNO = FUNDLINK.LPERMNO AND YEAR(MSF.DATE) = YEAR(FUNDLINK.DATADATE) AND MONTH(MSF.DATE) = MONTH(FUNDLINK.DATADATE)
```

To minimize the memory footprint of an application, it is thus suggested to run the above query in R in the following manner:

```r
# Load the pipe operator for more readable code
library(magrittr)

# Standard practice to access data in Nuvolos from R inside the Nuvolos app
# The nuvolos library is pre-installed on Nuvolos R applications.
conn <- nuvolos::get_connection()
result_data <- dbGetQuery(conn,"SELECT FUNDLINK.*, MSF.PRC FROM 
        (SELECT  INP.*, LT.LPERMNO, LT.LINKPRIM, LT.LINKDT, LT.LINKENDDT FROM
        (SELECT DF.GVKEY, DF.DATADATE, DF.ACCO, DF.AJEX, DF.CURCD, DF.RANK_IN_KEY FROM 
            (SELECT DISTINCT GVKEY, DATADATE, ACCO, AJEX, CURCD, ROW_NUMBER() OVER (PARTITION BY GVKEY, DATADATE ORDER BY DATADATE) AS RANK_IN_KEY 
            FROM FUNDA T
            WHERE FYEAR >= 2000 AND FYEAR <= 2010) DF
        WHERE DF.RANK_IN_KEY = 1 OR (DF.RANK_IN_KEY > 1 AND DF.AJEX IS NOT NULL) ) INP
    INNER JOIN CCMXPF_LINKTABLE LT
    ON LT.GVKEY = INP.GVKEY AND 
        (INP.DATADATE >= LT.LINKDT OR LT.LINKDT IS NULL) AND 
        (INP.DATADATE <= LT.LINKENDDT OR LT.LINKDT IS NULL)
    WHERE LT.LINKTYPE IN ('LU', 'LC') ) FUNDLINK
INNER JOIN MSF
ON MSF.PERMNO = FUNDLINK.LPERMNO AND YEAR(MSF.DATE) = YEAR(FUNDLINK.DATADATE) AND MONTH(MSF.DATE) = MONTH(FUNDLINK.DATADATE)")

### Additional operations on the result set
```









