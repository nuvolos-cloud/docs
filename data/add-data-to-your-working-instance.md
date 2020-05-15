# Adding data to a work instance

If you wish to work with data in vendor data set spaces \(like _CRSP US Stock and Indexes_\), you need to **distribute** the required tables to your working instance.

It is advised to source the tables from the latest available vendor data set snapshot.

This way, you can collect tables from multiple data sets into your working instance.

## Decide the target and the source

In the following example, we assume the working instance to be in the **Empty Org** organization and the **Documentation Class** space. This is the target of the distribution. The source is one of the two datasets currently available for the organization:

![](../.gitbook/assets/screen-shot-2020-03-17-at-9.57.36-am.png)

## Choose and stage the required data

We navigate into the dataset named **Test dataset** and to the Tables view of the **Current state**.

![](../.gitbook/assets/screen-shot-2020-03-17-at-9.59.17-am.png)

Here you can run a SQL query or preview the tables you currently have. We select the row for **TAB1** and the action **STAGE SELECTED** pops up similarly to what happened in the distribution guide. 

## Distribute

Once we've clicked **STAGE SELECTED** on the desired tables, we continue by distributing to our workspace in **Empty org - Documentation class.** In this particular use case, the Documentation class is set up as a class and we will distribute to the Master instance:

![](../.gitbook/assets/screen-shot-2020-03-17-at-10.01.04-am-2.png)

From here on, we just finalize distribution as usual.

{% hint style="info" %}
Currently it is **not** possible for the stage to contain objects from multiple sources, so once you are done in a particular source, you will need to distribute before moving on to another!
{% endhint %}





