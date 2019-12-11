# Organizations

## Overview

An organization collects a group of project environments called _spaces_, and offers common administrative, cost and licensing control over these project environments. 

An organization represents the highest level of interaction context in Nuvolos: once a user logs in to Nuvolos, the first step is to choose an organization to work in. Starting from an organization, the user can then select which space they want to work with.

Being a member of an organization grants the user automatic access to specific spaces, and the user may request access to further protected spaces. In practice, a real-world legal entity \(e.g. university\) can have more than one organizations associated with it. For example, if the university has a complicated licensing and cost allocation structure for a vendor dataset, then it might be necessary to create separate organizations for different datasets, and it will be the university management's discretion to invite the appropriate users to these special organizations.

## Features

* Organizations own all the data and files created by their members.
* Organizations offer high-level administrative management of members and spaces.

## Access control

On each structural level of Nuvolos, a variety of user roles are defined to control access and possible actions of users. 

An organization has four types of members, each member type having slightly different capability on the organization structural level.

* **Organization managers:** managers oversee and manage the assets that an organization has within Nuvolos. Organization managers can request the addition of new vendor datasets, create new spaces, and delete any of the spaces inside the organization. Managers have view privileges in all instances in all spaces of the organization. This provides full read access to every data ever created by any faculty member of the organization, plus all vendor datasets available to the organization. Generally, each organization has only a few managers. Furthermore, organization managers can send invitations to faculty members to join the organization.
* **Faculty members:** a ****faculty member can create new spaces \(where they automatically become space administrators\) and send invitations to colleagues or students to join or create an instance in the spaces where they are administrators.
* **Affiliated members:** Affiliated members can view the master instance of public and affiliate-only spaces. Furthermore, affiliated members can be invited by organization managers or faculty members to work in specific spaces that are private in the organization.
* **External members:** External members can view the master instance of public spaces. Furthermore, external members can be invited by organization managers or faculty members to work in specific spaces that are private in the organization.

  




