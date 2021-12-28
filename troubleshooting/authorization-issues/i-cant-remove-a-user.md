# I can't revoke a user

#### If you're having problems revoking a user from an organization, space, or instance, here are some issues you might want to examine:

* **You do not have the permission to revoke a user.**

To remove a user from an organization, you must be have an organization manager role. To remove a user from a space or instance, you must be an administrator of that space.

* **You are following the wrong steps.**

To revoke an organization-level role, follow the steps [here](../../actions/organization-management/revoke-user-access.md), space-level [here](../../actions/space-management/revoke-space-administrator-role.md), and instance-level [here](../../actions/space-management/revoke-instance-users.md).

* **You have lost connection to the internet.**

If you lose your internet connection, your request to revoke a user might not be received by the server. Make sure you restore your connection, refresh the page and try to revoke the user again.

* **There has been a server-side error and the user revoke request was not properly processed by Nuvolos.**

In some cases, it might happen that a server-side error occurs such that the user removal request is not processed properly by Nuvolos. Please wait for some time and then try to revoke the user again.\


#### &#x20;None of these solutions worked - how to proceed?

If none of the above solutions worked, please contact **support@alphacruncher.com.**
