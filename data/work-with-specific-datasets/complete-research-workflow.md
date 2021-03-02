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

After opening the Matlab application, the following bit of code will return the entire database table as a Matlab table-type object. The query we are executing is a merge of a monthly stock series table \(for Apple monthly stock prices\) and the Fama-French factor table as follows:

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





## R/RStudio workflow

