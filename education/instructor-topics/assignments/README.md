---
description: Create and review assignments in Nuvolos
---

# Assignments

Nuvolos supports the creation, dissemination, and review of assignments, without having to download, upload, and send files around.

### Creating an assignment

An assignment is a collection of Nuvolos objects (e.g. files, folders) and an associated deadline until which the students can hand in their work.

An assignment is created whenever during material distribution time, the "Create an assignment" checkbox is selected. In this case, the deadline until which hand-ins are accepted needs to be selected (after the deadline passes, students can no longer hand-in material).

Created assignments are visible on the dashboard of a space, as well from the Distribute > Assignments menu from the sidebar.

{% hint style="info" %}
In most cases, the instructor prepares the placeholder files that will be filled out by the student and distributes these placeholders. It is also possible however to stage and distribute entire directories when an assignment is created, in this case, the whole directory will be handed in by the student and the instructor can review whatever material was inside at hand-in time.
{% endhint %}

#### Modifying assignments

Space administrators can modify assignments (deadlines, descriptions and handback visibility) by clicking the "pencil" icon inside the assignment description field once the assignment dialog is opened or from the Distribute > Assignments sidebar menu.

### Reviewing assignments

To grade assignments, a space administrator can click the "Grade" button on the assignment dialog header. This will open the grade table, from which each assignment hand-in can be opened by clicking the "Review" button.

This will launch the application inside the student instance, with a **copy** of the student submission mounted in the files area. All packages installed by the student will be available for the instructor, so open-ended projects are fully supported as well.

#### Providing feedback

Feedback can be provided inside the submitted files in any form the instructor sees fit (Nuvolos maintains a copy of the original handed in file for reference if needed).&#x20;

We suggest making explicit (inline) comments so that it is clear to the student when reviewing the hand-back what has been the instructor's (I) comment. An example is below:

```
var = 1   # I: Use a more informative variable name

test_tuple = (False, "test")

if test_tuple:   # I: Use test_tuple[0] instead
    print("This should not appear.")
```

Once the files have been reviewed, the instructor can assign a grade by clicking the grade icon on the sidebar which brings up the grade table. There the currently graded instance / handin will be highlighted and a grade can be entered as free text.

### Handing back assignments

During the grading process, the hand-backs are not visible to students. Once the review of all hand-ins is completed, the assignment can be edited as described above and the visibility of hand-backs can be enabled.&#x20;

By opening the Assignment dialog, students will be able to view their grades and also launch the application with the corrected files available for review (without being able to modify them).

When students start their applications after hand-backs have been enabled, they will see a special Assignments > handback folder, which will contain the reviewed version of the material (read-only). They can then check the reviewed file for feedback from the instructor.

### Exporting grades

Grades can be exported from the grade table in Excel format which can then be used to upload to other systems if needed.
