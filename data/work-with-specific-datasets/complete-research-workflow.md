---
description: Extracting and then writing back data
---

# Complete research workflow

Nuvolos supports a query-analyze-insert cycle to help researchers query, analyse and store data safely in a simple, integrated workflow. The workflow is demonstrated in two languages, but can be extended to any languages supported by Nuvolos.

## Matlab workflow

A standard skeleton scientific workflow in Matlab can be broken down into three main steps:

1. Query research-relevant data
2. Analyze, transform or otherwise manipulate data
3. Store results

### Querying relevant data

For the mock example, we are going to work with the Fama-French factor set that is available for our Demo user, we will be focusing on the [North America](https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/Data_Library/f-f_5developed.html) 5-factor table. The `NORTH_AMERICA_5_FACTORS`  [table has been distributed](../work-with-data.md#distribute-data-you-need) to the instance we are working in.

After opening the Matlab application, the following bit of code will return the entire database table as a Matlab table-type object. The query we are executing is a merge of a monthly stock series table \(for Apple monthly stock prices\) and the Fama-French factor table as follows.

The SQL query:

```text
SELECT NAF.*, SM.MPRC, SM.MRET*100, SM.MTCAP 
FROM NORTH_AMERICA_5_FACTORS NAF 
INNER JOIN SAZ_MTH SM 
ON SM.MCALDT = NAF.DATE 
WHERE KYPERMNO = 14593
```

The code that executes the query, the above string is saved in `query_string`.

```text
con = get_connection();
dataset_factor = select(con, query_string);
```

### The simple analysis

The previous step resulted in `dataset_factor` containing a Matlab `Table` object that holds the data. The `fitlm` method fits a linear regression on the table with an R-style formula. We then write back the fitted values to the Table as a column.

```text
mod = fitlm(dataset_factor,'SM_MRET_100 ~ 1 + MKT_RF + SMB + HML + RMW + CMA')
dataset_factor.FitFactor5 = mod.Fitted
```

### Storing results in the database

As a final step, we write back the results using the [data upload](../upload-data-to-nuvolos/small-data-upload-scripts.md#3-matlab) command for Matlab:

```text
sqlwrite(con,'APPLE_5FACTOR_FIT',dataset_factor)
```

As an end result, we can then find the table on the Nuvolos UI:

![](../../.gitbook/assets/screenshot-2021-03-04-113019.png)

## RStudio workflow

A standard skeleton scientific workflow in RStudio can be broken down into three main steps:

1. Query research-relevant data
2. Analyze, transform or otherwise manipulate data
3. Store results

It is possible to create more complext workflows, but it will usually consist of three-step modules such as above.

### Querying relevant data

For the mock example, we are going to work with the Fama-French factor set that is available for our Demo user, we will be focusing on the [North America](https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/Data_Library/f-f_5developed.html) 5-factor table. The `NORTH_AMERICA_5_FACTORS`  [table has been distributed](../work-with-data.md#distribute-data-you-need) to the instance we are working in.

After opening the RStudio application, the following bit of code will return the entire database table as an R data frame object. The query we are executing is a merge of a monthly stock series table \(for Apple monthly stock prices\) and the Fama-French factor table as follows.

The SQL query:

```text
SELECT NAF.*, SM.MPRC, SM.MRET*100, SM.MTCAP 
FROM NORTH_AMERICA_5_FACTORS NAF 
INNER JOIN SAZ_MTH SM 
ON SM.MCALDT = NAF.DATE 
WHERE KYPERMNO = 14593
```

The code that executes the query, the above string is saved in `query_string`.

```text
conn <- nuvolos::get_connection()
dataset_factor <- dbGetQuery(conn, query_string)
```

### The simple analysis

The previous step resulted in `dataset_factor` containing an R `data.frame` object that holds the data. The `lm` method fits a linear regression on the data frame. We put the fitted values to the data frame.

```text
mod <- lm(SM_MRET_100 ~ 1 + MKT_RF + SMB + HML + RMW + CMA, dataset_factor)
dataset_factor$FIT_FACTOR_5 <- mod$fitted.values
```

### Storing results in the database

As a final step, we write back the results using the [data upload](../upload-data-to-nuvolos/small-data-upload-scripts.md#2-r) command for R:

```text
DBI::dbWriteTable(conn, name="APPLE_5FACTOR_FIT", value=dataset_factor)
```





