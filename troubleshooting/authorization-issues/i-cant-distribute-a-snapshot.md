# I can't distribute a snapshot

#### If, after logging into the DataHub, you're having trouble distributing a snapshot to other instances, here are some issues you can examine:

* **You don't have the right permission to distribute a snapshot.**

To distribute a snapshot from one instance to another, you need to be the editor of _both_ instances. An instance editor will not be able to distribute a snapshot to an instance where she is a viewer.

* **You are looking in the wrong place.**

To distribute a snapshot, you must open one of the _archived snapshot_, and from the left sidebar click on distribute snapshot. If you are viewing the current state of your instance, then you can first create a snapshot of your current state, and then distribute the snapshot to other instances. Check the steps [here]() for distributing a snapshot.

* **You are distributing a snapshot to a deleted instance.**

An instance might disappear because the instance editor deleted it. If you are the instance editor, then you can [recover](../../settings-and-administration/space-management/delete-an-instance.md) the deleted instance within 24 hours of the deletion time. If you are not the instance editor, then you can contact the editor and ask if the instance or could be restored.

* **You have lost connection to the internet.**

If you lose your internet connection, the distribute snapshot request might not reach the server and therefore the snapshot might not be distributed. Make sure you restore your connection,  refresh the page and try to distribute the snapshot again.

* **There has been a server-side error and the application stop data was not properly served by DataHub.**

In some cases, it might happen that a server-side error occurs such that the distribute request is not processed properly, making it impossible to distribute the snapshot. Wait for a few minutes, refresh the page and then try to distribute the snapshot again.  


### None of these solutions worked - how to proceed?

If none of the above solutions worked, please contact **support@alphacruncher.com.**

