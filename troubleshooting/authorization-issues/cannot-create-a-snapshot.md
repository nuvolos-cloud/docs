# I can't create a snapshot

#### If you're having problems creating a new snapshot, here are some issues you might want to examine:

* **You do not have the permission to create a snapshot**

In order to create a snapshot in an instance, the user must be the instance editor. If you don't have the required role to create a snapshot, you can ask the instance editor to do it, or invite you to become an instance editor which allows you to create a snapshot.

* **You followed the wrong steps for creating a snapshot**

Make sure you follow the correct steps required for creating an instance. For more details, check [here](../../actions/instance-management/create-a-snapshot.md).

* **You are in Distributed instance.**

A special instance exists in each space and takes the name Distributed. This instance contains a list of all snapshots that you shared with other members of the space. You cannot create a snapshot from within the Distributed instance. Make sure you open any of the other instances where you are an editor to be able to create a snapshot.

* You are not in **CURRENT STATE**.

A snapshot can be created only from within the current state of your instance. Make sure that you navigate to CURRENT STATE in order to be able to create a snapshot.

* **You have lost connection to the internet.**

If you lose your internet connection, your request to create a snapshot might not be received by the server. Make sure you restore your connection, refresh the page and try to create the snapshot again.

* **There has been a server-side error and the snapshot creation request was not properly processed by DataHub.**

In some cases, it might happen that a server-side error occurs such that the request to create a snapshot is not processed properly by the server. Please wait for some time and then try to create the snapshot again.

####  None of these solutions worked - how to proceed?

If none of the above solutions worked, please contact **support@alphacruncher.com.**

