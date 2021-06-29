---
description: >-
  Nuvolos supports long-running applications whilst attempting to automatically
  stop applications which are no longer required to run.
---

# Long-running applications

### Automatic stopping due to inactivity

In order to efficiently allocate resources, Nuvolos automatically stops inactive applications. Depending on the space type, this happens after different inactivity periods:

* In Education-purpose spaces, the default inactivity limit is **one hours**.
* In Research-purpose spaces, the default inactivity limit is **six hours**.

For **research spaces** Nuvolos considers an application being active if either: 

* It is actively opened on Nuvolos
* It is actively computing \(using more than half of a single virtual CPU\)

{% hint style="info" %}
Researchers can launch long running computations and their application will keep running until actively computing. If the computation is finished \(either due to completion or an error\) and the application is not opened on Nuvolos, it will be auto-stopped. We therefore recommend explicitly capturing output logs to ensure that any warnings or errors are captured.
{% endhint %}

For **education spaces** the application is only considered active if it is actively opened, unattended long-running computations will be automatically terminated.

{% hint style="info" %}
To keep an application active in an education space, you need to make sure that the application is in focus in your browser for more than one \(uninterrupted\) minute either every hour.
{% endhint %}



