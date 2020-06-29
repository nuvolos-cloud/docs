---
description: Getting started with teaching a course
---

# Get started with a course

{% hint style="success" %}
In most cases, it is possible to set up a class from scratch in less than 5 minutes.
{% endhint %}

## Add a new class

Classes are spaces in Nuvolos where instructors add learning materials \(data, code and applications\) for their students. Organization managers and faculty members may create classes.

1. Navigate to _Classes_
2. Select + NEW CLASS 
3. Enter desired class name and description
4. Select + ADD SPACE
5. Select application
6. Enter desired application name
7. Select + ADD APPLICATION

![Create a class](../../.gitbook/assets/create_class_ed.gif)

## Add teaching material

Course material are items like code, documents or data files that are used to support learning. The following animation shows you how to navigate to the files of the master instance and upload course material.

![Uploading two files](../../.gitbook/assets/upload_files_ed.gif)

## Distribute to prospective students

You can distribute the teaching material to prospective and existing students by using the distribute feature. For a very basic use case, we demonstrate how to distribute the two files uploaded previously.

![](../../.gitbook/assets/distribute_ed.gif)

The key steps of the process:

1. **Select the objects you want to distribute**
   * Not selecting anything will default to distributing everything from the current state of the instance.
   * Applications are automatically added to the distribution, you have the option to remove them.
2. **Select the target**
   * By default you will distribute to all students - every existing instance and future instance.
3. **Select distribution strategy**
   * By default overwrite is suggested, consult the detailed distribution documentation for other options and their use cases.
4. **Specify a notification message**
   * Your current students will receive the message you specified to their e-mail address.

## Invite students

Ways to invite students to join the course :

* By sharing an Invite Link \(requires the least work from the instructors' side\)
* By e-mail \(good for small classes\)
* By inviting a group \(via e-mail\)

Invited students will be able to see only their workspace, not the master instance or other students' instances.

Invite with a Sharing Link:

1. Navigate to _Course Users_
2. Select + INVITE
3. Copy Sharing Link.

![Finding and copying the invitation link](../../.gitbook/assets/invitation_link_out_ed.gif)

## Invite teaching assistants

Teaching assistants are able to see everything that is going on in the class, they have the _space admin_ role. The user who created the class automatically becomes a _space admin_ as well. To invite teaching assistants with this elevated role, follow the instructions below.

![Inviting a teaching assistant](../../.gitbook/assets/space_admin_invite_ed.gif)

## Best practice: Structuring your class

As described in the structure document, a space \(in particular, a class\) consists of multiple instances. As a space administrator of your class, you have complete control over how many instances your space might have and which students may access what instance.

### Suggested layout

In the suggested standard layout:

* All instructors \(professors and teaching assistants alike\) control the teaching material in the **master** instance. In terms of roles:
  * The professor and designated teaching assistants have space admin role in the space and edit material in the master instance.
* Every student is invited to their own instance, each student having the following roles:
  * Editor role on their own personal instance.
  * Viewer role on the distributed instance \(this is given by definition\).
* [Group work](set-up-group-work.md) is kept in a separate space, any specialized instances are not kept together with the standard layout.

{% hint style="success" %}
The benefit of this layout is that distribution target can be "All Students" without compromising integrity. 

In general, we suggest to keep your spaces simple if you have the ability to create multiple.
{% endhint %}

