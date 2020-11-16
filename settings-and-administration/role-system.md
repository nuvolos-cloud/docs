---
description: The in-depth guide to the role system
---

# Roles

Nuvolos has a role system that is directly mapped to the structure of Nuvolos. On each structural level, a variety of roles exist with different actions available for different use cases.

In order to fully understand the role system, the [structure of Nuvolos](../our-features/data-organization/) is a suggested read.

## Organization level roles

As described in detail, organizations are cost and accounting centers. On the organization level, the following four roles exist:

### No role

If a user has no role in an organization, they cannot view any content contained in the organization. If a user has a role, it can be[ revoked](organization-management/revoke-user-access.md) by an organization manager.

### Member

An organization member is any user who has been invited in any capacity into any space in the organization.

* Members are able to view **Public** spaces in the organization. 
* Members are able to view any content in the organization they are specifically invited to. 
* The membership role signifies that a connection has at least at one point in time existed between the user and the organization.

### Faculty

An organization faculty member is a user who has the ability to control resources in the organization. 

* Faculty members can create spaces and invite users to the spaces they have created. Any user who creates a space automatically becomes _space admin_ of that space. 
* Faculty members can view **Public** and **Faculty only** spaces as well as any content they are invited to. 
* The faculty role is powerful in the sense that it has the ability to propagate licensed content to other users.

### Manager

An organization manager is a user who has the ability to view resources in the organization as well as control membership.

* Organization managers can create spaces and invite users to the spaces they have created. Any user who creates a space automatically becomes _space admin_ of that space. 
* Organization managers can view all content in the organization however they can modify content where they received explicit invitation to do so. 
* Organization managers can invite additional Faculty to the organization. 
* Organization managers can revoke access to the organization's resources. 

## Space level roles

Spaces have a single special elevated role, that of a space admin. Every other user accessing a space has access to the space via having an editor or viewer role in one or more instances of the space.

### Space admin

Space admins have administrative power restricted to the scope of a single space.

* Space admins can view and edit every instance in the space:
  * They can upload/download files, run applications and query/modify tables.
  * They can create/delete snapshots. 
* Space admins have the right to invite users to instances as editors or viewers. 
* Space admins have the right to create instances in a space.

## Instance level roles

### Editor

* Instance editors **can modify** the contents of the **current state** of an instance: they can upload/download files and run applications. 
* Instance editors **can** also **create snapshots** of the current state of the instance.

### Viewer

* Instance viewers can view the contents of snapshots in the instance, including writing queries against data.





