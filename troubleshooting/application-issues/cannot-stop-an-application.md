# I can't stop a running application

#### If, after logging into the DataHub, you're having trouble stopping a running application, here are some issues you can examine:

* **You don't have the right permission to stop the application**

To stop a running application in an instance, you need to be the editor of that instance. Instance viewers cannot start or stop applications. If you don't have the right permission to stop an application, contact the instance editor and discuss with her stopping the application.

* **Give it some time.**

Stopping an application might require some time. Please give it some time to stop.

* **You are looking in the wrong place.**

To stop an application, you must be either in the **CURRENT STATE** of an instance of which you are an editor, or in the dashboard where you can open and stop your running applications.

* **There is no running application to stop.**

Make sure that you have [created](../../settings-and-administration/instance-management/create-an-application.md) and started the application before stopping it.

* **The application you want to start does not exist anymore because it was deleted.**

An application might disappear because the instance editor deleted it. If you are the instance editor, then you can [recover](../authorization-issues/accidental-data-loss/deleted-an-application-by-mistake.md) the deleted application within 24 hours of the deletion time. If you are not the instance editor, then you can contact the editor and ask if the application or could be restored.

* **You have lost connection to the internet.**

If you lose your internet connection, the application stop request might not reach the server and therefore the application will not be stopped. Make sure you restore your connection,  refresh the page and try to stop the application again.

* **There has been a server-side error and the application stop data was not properly served by DataHub.**

In some cases, it might happen that a server-side error occurs such that the application data is not served properly, making it impossible to stop the application. Wait for a few minutes, refresh the page and then try to stop the application.  


### None of these solutions worked - how to proceed?

If none of the above solutions worked, please contact **support@alphacruncher.com.**

