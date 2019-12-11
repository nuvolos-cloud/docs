# I can't remove a user

#### If you're having problems removing a user from an organization, space, or instance, here are some issues you might want to examine:

* **You do not have the permission to remove a user.**

To remove a user from an organization, you must be have an organization manager role. To remove a user from a space, you must be an administrator of that space. Finally, to remove a user from an instance, you must be an administrator of the space which contains that instance. For more information, check the documentation on how to revoke a user [here](../../actions/organization-management/revoke-user-access.md).

* **You have lost connection to the internet.**

If you lose your internet connection, your request to remove a space might not be received by the server. Make sure you restore your connection, refresh the page and try to delete the space again.

* **There has been a server-side error and the user removal request was not properly processed by DataHub.**

In some cases, it might happen that a server-side error occurs such that the user removal request is not processed properly by DataHub. Please wait for some time and then try to remove the user again.

####  None of these solutions worked - how to proceed?

If none of the above solutions worked, please contact **support@alphacruncher.com.**

