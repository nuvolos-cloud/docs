# Spaces

## Overview

A core feature of Nuvolos is that projects are encapsulated and self-contained in terms of both data and software. This feature is realized by the concept and hierarchical level called _space._ A space lives within the context of an organization, and different spaces can be created for managing activities such as a course, a summer school, a research project, or a dataset. Spaces contain at least one, but in certain use cases may contain a number of instances, which represent separate work contexts that allow for access control and sharing of data between the members of a space \(e.g. teachers and students\). A space, therefore, can be seen as a logical unit to organize:

* **Tabular data**
  * Raw tabular data \(tables\)
  * Views on the raw data \(Views\)
* **Files** \(e.g. code, CSV files, etc.\)
* **Applications** \(containers with custom installed packages\)
* **Logs \(runs\)**: A run is a named collection of logs that can have multiple “instances” of the run. Each of these instances logs output generated during a specific occasion the user did something.

## Features

* **Self-contained:** Nuvolos strongly supports the _gather and manipulate_ workflow paradigm. The user first gathers all the relevant data available in the organization into their space, then begins work with the data in a self-contained and enclosed environment. 
* **Branched:** Instances provide the possibility of maintaining multiple mutations of the same core concept. 
* **Versioned:** The current state of any instance can be snapshotted to create an immutable, restorable state, enabling full protection and reproducibility of a project. 
* **Shareable**: users can share their work inside a space. 
* **Teaching-ready:** It is natural to set up a course as a space, where students and professors have their own sandboxes, and teaching material \(including code and data\) can be distributed relying on the previous features.

## Access control

On each structural level of Nuvolos, a variety of user roles are defined to control access and possible actions of users. 

Access to space contents \(database tables, files, etc.\) is controlled on the instance level. However, each space has one or more administrators, who have special privileges. For example, administrators can invite other administrators for the space and have editor rights for all instances in the space. They are also allowed to create new instances in the space and invite editors/viewers for any of its instances. The user who creates the space will, by default, attain space administrator rights.

**Space visibility**

* **Public space**: A space that contains publicly available resources available to the entire organization, including external members. A natural example is a publicly available dataset uploaded to Nuvolos, e.g. data from FRED. Any user in the organization automatically becomes a viewer of the master instance of public spaces, and organization managers become viewers in all of its instances. 
* **Affiliate-only space**: A space that contains a resource that is only accessible by affiliated members of the organization. A typical example is a vendor-provided dataset with a campus-wide license. Faculty members and affiliated members automatically become viewers of its master instance. Organization managers also become viewers in all of its instances. 
* **Faculty-only space**: A space that contains a resource that is only accessible for faculty members of the organization. Faculty members automatically become viewers of its master instance. Organization managers also become viewers in all of its instances. A typical example: vendor-provided dataset with a faculty-wide license. 
* **Private space**: A space that contains a resource that is only accessible for members of the organization on a case-by-case basis. Only organization managers become viewers in all of its instances, everyone else has to be invited by the space administrator. A typical example: any research group project or course is designated to be a private space.

**Visual representation**

On the web UI, each user is able to browse and search the spaces they have access to. The following rules apply for deciding which spaces to display:

* If the user is not a viewer/editor of any of the views in the space, is not an admin of the space, or a manager in the organization, they cannot see the space at all. 
* If the user’s highest role is a viewer on one or more views in the space, they can see the space and choose from all the views they have access to. 
* If the user’s highest role is an editor on one or more views in the space, they can see the space and choose from all the instances they have access to \(both viewer or editor\). 
* If the user is an administrator of the space, they can see the space and choose from all the instances in it. 
* If the user is an org manager, they are a viewer in all instances of all spaces automatically. 
* If the user is a faculty member, they have no special rights. They cannot see the space if its administrator has not invited them.

