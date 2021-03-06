# I can't delete an application

#### If, after logging into the DataHub, you're having trouble deleting an application, here are some issues you can examine:

* **You don't have the right permission to delete an application.**

To delete an application in an instance, you need to be the editor of that instance. Instance viewers cannot delete applications. If you don't have the right permission to delete an application, contact the instance editor and discuss with him the deletion of the instance.

* **The application is running.**

Only stopped applications can be deleted. Therefore, before deleting an application check the status of the application and make sure that it is stopped.

* **Give it some time.**

Deleting an application might require several seconds, please wait for some time until it's done.

* **You are looking in the wrong place.**

To delete an application, you must be in the **CURRENT STATE** of an instance of which you are an editor. Once in the current state, click on **Application List** button from the side bar on the left.

* **The application you want to start does not exist anymore because it was deleted.**

It can be that the application you want to delete has been already deleted. If you are the instance editor, then you can [recover](../authorization-issues/accidental-data-loss/deleted-an-application-by-mistake.md) the deleted application within 24 hours of the deletion time.

* **You have lost connection to the internet.**

If you lose your internet connection, the data retrieval request might fail and the browser doesn't send the deletion request to server. Make sure you restore your connection,  refresh the page and try to delete the application again.

* **There has been a server-side error and the application deletion request was not properly processed by DataHub.**

In some cases, it might happen that a server-side error occurs such that the application data is not served properly, making it impossible to start the application. Wait for a few minutes, refresh the page and then try to start the application.  


### None of these solutions worked - how to proceed?

If none of the above solutions worked, please contact **support@alphacruncher.com.**

