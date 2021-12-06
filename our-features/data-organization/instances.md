# Instances

## Overview

In Nuvolos, _spaces_ ensure project encapsulation and delineation. Spaces consist of one or multiple instances. Instances offer the opportunity to organize parallel workflows or branches in a space.  There are a number of use cases which make instances useful and necessary:

* **Course setting:** The professor and each student may have their own instance, thus their own branch of roughly the same material.\

* **Research project setting:** Researchers may have their own private instances where they test theories and only the stable findings get populated into the main research body material.\

* **Single user setting:** Similar to the research project, any user might want to maintain multiple branches or variations of roughly the same code and data.

## Features

Instances offer parallelization and branching inside a space.

* **Branching:** A user can create multiple instances of the same workflow. Branching relies heavily on the _distribution_ feature of instances.\

* **Distribute:** A user can distribute the contents of a snapshotted state to instances where they are an editor. This serves the purpose of branching and content dissemination.

## Access control

On each structural level of Nuvolos, a variety of user roles are defined to control access and possible actions of users.&#x20;

Access control of spaces is handled through roles in instances.

Each space has two special instances, Master and Distributed, which are created automatically at the creation of the space itself. These two instances cannot be deleted, except for the case if the entire space is removed.

Each user can have one of the following roles for each instance in each space:

* **Viewers** have read access to all snapshots of the instance (but they cannot create/delete snapshots). The viewer role provides a means to share spaces with users where they are able to see changes in the current state in realtime.
* **Editors** can modify the current state. A typical example is a vendor-provided dataset with a campus-wide license in the instance, meaning they can add/remove/update files, tables, and other objects, and have all the rights as viewers as well.

The access control model enables the legally correct execution of the following use-cases:

* **Institution-wide available vendor data:** Vendor provided data will reside in the dedicated organization for each institution. The _organization administrators_ of the institution will be able to see all vendor-provided data and any data created by any affiliates of the institution, as they are viewers of all instances of all spaces.&#x20;
* **Teaching a course:** _Faculty members_ can create a new space for each course they teach, in any organization they are affiliated with. They would become administrators of these spaces, while students will become members after they are invited to the course space. If course work requires homework assignments, it is suggested to create a separate instance for each student. Teaching assistants may be assigned a _space administrator_ role so they can handle the administration of the course. It is also possible to create multi-user instances in case the course requires group work or group assignments.
* **Managing a research project:** Researchers can create a separate space for each research collaboration they are part of. In the created space, the head of the project invites collaborators (possibly from other organizations as well). It is possible to create an instance for each collaborator so they can work in parallel and only share results that they deem worthy of merging into the group project.&#x20;
* **Private workflows:** _Faculty members_ are able to create new spaces where they become space administrators. In these spaces, only the organization administrators are viewers of all instances. Faculty members can then select the audience of each instance created in these spaces.
