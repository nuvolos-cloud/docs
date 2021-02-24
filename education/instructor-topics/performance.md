---
description: >-
  Suggestions on how to achieve best performance and good user experience for
  students when running code on Nuvolos
---

# Application performance

When working with student applications on Nuvolos, it is important to consider the following performance characteristics:

### Higher resource requirements

If a class size is large \(e.g. above ~50 users / or if individual applications have higher resource settings\) and students are expected to launch their applications at the same time, it can happen that resource allocation becomes slower. For a good user experience, we recommend that instructors pre-launch the student applications between **30-45 minutes before** students are expected to start work with it.

Pre-launching can be performed from the 'Applications' view on the sidebar, by clicking the three dots besides the application name and selecting the "Start for all users" option:

![](../../.gitbook/assets/image%20%284%29.png)

### Performance sensitive code

On Nuvolos each student runs the code with the same application configuration as the instructor.

Nevertheless it is important to consider that when many students are concurrently executing a computationally intensive code, the application performance might be inferior to what the instructor experienced during material development when potentially the load from other users was lower.

Whilst usually this is within a reasonable factor, we recommend that during **interactive sessions with a large number of students**, either:

a\) code examples should be adjusted such that  they execute within a minute or so maximum

b\) the space should be configured to have larger per-student resources to provide adequate compute performance

For out-of-class work when concurrency is lower, these considerations can be appropriately relaxed.

