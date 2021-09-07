---
description: >-
  Suggestions on how to achieve best performance and good user experience for
  students when running code on Nuvolos
---

# Application performance

When working with student applications on Nuvolos, it is important to consider the following performance characteristics:

### Resource allocation time

If a class size is large \(e.g. above ~50 users / or if individual applications have been customized to request higher resources\) and students are expected to launch their applications at the same time, it can happen that resource allocation becomes slower \(e.g. application launch time can be around 5 minutes instead of the usual 30-60 seconds\). 

For a good user experience, we recommend that instructors pre-launch the required application\(s\) for all users around **30 minutes before** students are expected to start work with it.

{% hint style="info" %}
Student application are stopped automatically after 1 hour of inactivity, so it does not make sense to perform the pre-launch more than an hour before the planned start time.
{% endhint %}

Pre-launching can be performed from the 'Applications' view on the sidebar, by clicking the three dots besides the application name and selecting the "Start for all users" option:

![](../../.gitbook/assets/start_for_all.png)

Pre-launching will start the application for all users in the space: for students, their respective applications will be started, for space administrators the application in the master instance will be started. In case a space administrator is also an editor in a student instance, that application will also be started for the administrator.

### Performance sensitive code

On Nuvolos each student runs the code with the same application configuration as the instructor.

Nevertheless it is important to consider that when many students are concurrently executing a computationally intensive code, the application performance might be inferior to what the instructor experienced during material development when potentially the load from other users was lower.

Whilst usually this is within a reasonable factor, we recommend that during **interactive sessions with a large number of students**, either:

a\) Code examples should be adjusted such that  they execute within a minute or so maximum.

b\) The space should be configured to have larger per-student resources to provide adequate compute performance. For the most performance sensitive cases, we suggest dedicated compute nodes for each application - please reach out to our support team to discuss such an option.

For out-of-class work when concurrency is lower, these considerations can be appropriately relaxed.

