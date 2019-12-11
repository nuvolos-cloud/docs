# I can't see an application

#### If, after logging into the DataHub, you're having trouble finding a specific application, here are some issues you can examine:

* **The application you are looking for is not among the snapshots visualized by default.**

By default, the list of applications will show only five apps. If you cannot find an application, then it might be because it is now shown in the first five items. Simply increase the number of rows per page using the option at the bottom of the table, or navigate to the next page by using the right arrow at the bottom..

![](../../.gitbook/assets/screen-shot-2019-07-16-at-1.18.45-pm-2.png)

* **You are looking in the wrong place.**

There are three places where you can see applications:

1. From the **dashboard**, you can view the list of all _running_ applications in your instances.
2. From **CURRENT STATE**, you can view all _running_ and _stopped_ applications within an instance of which you are an editor \(if you are a viewer, then you won't be able to see applications in the CURRENT STATE\).
3. If you click on one of the snapshots of an instance, you can view only the applications that existed in the CURRENT STATE at the time the snapshot were taken.

* **You don't have the right permission to view the application**

To view an application, you need to be an instance editor or a viewer of an instance. Instance viewers cannot see the applications in the CURRENT STATE, only those in the snapshots. If you don't have the right permission to view the snapshots of an instance, you can ask the instance editor to invite you to become an instance editor which allows you to view the application.

* **The application does not exist anymore because it was deleted.**

An application might disappear because the instance editor deleted it or the snapshot that contained it wa deleted. If you are the instance editor, then you can [recover](../authorization-issues/accidental-data-loss/deleted-an-application-by-mistake.md) the deleted application within 24 hours of the deletion time, or you can [recover](../authorization-issues/accidental-data-loss/deleted-a-snapshot-by-mistake.md) the deleted snapshot that contained the application. If you are not the instance editor, then you can contact the editor and ask if the application or snapshot could be restored. 

* **You have lost connection to the internet.**

If you lose your internet connection, the data retrieval request might fail and the browser doesn't receive the list of applications from the server. Make sure you restore your connection and refresh the page.

* **There has been a server-side error and the list of applications was not properly served by DataHub.**

In some cases, it might happen that a server-side error occurs such that the application data is not served properly. Wait for a few minutes, refresh the page and then check again.  


### None of these solutions worked - how to proceed?

If none of the above solutions worked, please contact **support@alphacruncher.com.**

