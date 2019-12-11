# I can't see a snapshot

#### If, after logging into the DataHub, you're having trouble finding a specific snapshot, here are some issues you can examine:

* **The snapshot you are looking for is not among the snapshots visualized by default.**

By default, the list of snapshots will show only five snapshots. If you cannot find a snapshot then it might be because it is now shown in the first five items. Simply increase the number of rows per page using the option at the bottom of the table, or navigate to the next page by using the right arrow at the bottom..

![](../../.gitbook/assets/screen-shot-2019-07-16-at-1.18.45-pm-2.png)

* **You don't have the right permission to view the snapshot**

To view an instance, you need to be an instance editor or a viewer. If you don't have the right permission to view the snapshots of an instance, contact the space admin and ask her to grant you permission.

* **The snapshot does not exist anymore because it was deleted.**

A snapshot might disappear because the space admin deleted it. If you are the instance editor, then you can [recover](accidental-data-loss/deleted-a-snapshot-by-mistake.md) the deleted snapshot within 24 hours of the deletion time. If you are not the instance editor, then you can contact the editor and ask if the snapshot could be restored.

* **You have lost connection to the internet.**

If you lose your internet connection, the data retrieval request might fail and the browser doesn't receive the list of snapshots from the server. Make sure you restore your connection and refresh the page.

* **There has been a server-side error and the list of snapshots was not properly served by DataHub.**

In some cases, it might happen that a server-side error occurs such that the snapshot data is not served properly. Wait for a few minutes, refresh the page and then check again.  


### None of these solutions worked - how to proceed?

If none of the above solutions worked, please contact **support@alphacruncher.com.**

