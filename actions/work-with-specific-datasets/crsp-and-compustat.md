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



