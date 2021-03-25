---
description: Create and review assignments in Nuvolos
---

# Assignments

Nuvolos supports the creation, dissemination and review of assignments, without having to download, upload and send files around.

### Creating an assignment

An assignment is a collection of Nuvolos objects \(e.g. files\) and an associated deadline until which the students can hand in their work.

An assignment is created whenever during material distribution time, the "Create an assignment" checkbox is selected. In this case, the deadline until which hand-ins are accepted needs to be selected \(after the deadline passes, students can no longer hand-in material\).

Created assignments are visible on the dashboard of a space, as well from the Distribute &gt; Object Bundles menu from the sidebar.

#### Modifying assignments

Assignment deadlines and descriptions can be changed by selecting the "Object bundles" entry under the "Distribute" menu on the sidebar. The 'pencil' icon can be clicked beside each assignment to make changes.

### Reviewing assignments

When an assignment is created a special "Assignments" folder will appear inside the instructor's application \(in the master instance - if the application is already running it should be restarted\) with two sub-folders:

* **handin**: This folder contains the original work submitted by students and is not editable. It is for audit purposes so that both instructor and the student can see what has been submitted.
* **handback**: This folder contains the reviewed work by the instructor and is editable. Instructors need to work inside the handback directory. It contains the same content as **handin** before the review begins.

Each hand-in by a student will be under the following folder structure:

```text
Assignments > handin > [student_instance_name] > [assignment_name] > [handin_id]
```

A hand-in ID is a timestamp + identifier combination, where the student can choose an identifier \(by default their instance name, but can be changed if needed for better anonymity\). Students can hand-in multiple versions of their work, so the instructor generally needs to review the latest submission.

{% hint style="info" %}
The Assignments folder is only visible inside the application and currently is not accessible from the web-interface.
{% endhint %}

#### Providing feedback

Feedback can be provided inside the files in the Assignments &gt; handback folder in any form the instructor sees fit. We suggest making explicit comments so that it is clear to the student when reviewing the hand-back what has been the instructor's \(I\) comment. An example is below:

```text
test_tuple = (False, "test")

### I: Test_tuple will evaluate to a "truthy" value. 
### I: Use test_tuple[0] instead.
if test_tuple:
    print("This should not appear.")
```

### Handing back assignments

During the grading process, the hand-backs are not visible to students. Once the review of all hand-ins is completed, the assignment can be edited on the "Bundles" view and the visibility of hand-backs can be enabled.

When students start their applications after hand-backs have been enabled, they will see a special Assignments &gt; handback folder, which will contain the reviewed version of the material \(read-only\). They can then check the reviewed file for feedback from the instructor.

### Communication

When the assignment is distributed, the students will receive a notification just like for regular distributions. 

For other events like changing deadlines, enabling hand-back visibility, we recommend that the instructor provides an entry in the files &gt; README.md file and distributes this entry with the appropriate message.

