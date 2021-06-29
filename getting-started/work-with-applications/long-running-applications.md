---
description: >-
  Nuvolos supports long-running applications whilst attempting to automatically
  stop applications which are no longer required to run.
---

# Long-running applications

Nuvolos aims to provide the maximal resources for applications that require it, whilst freeing up resources from unused applications to optimize organization resource usage. As described below, we provide convenient default policies that:

* Allow long running computations to finish without user interaction
* Stop inactive applications, to free up resources for other organization members / minimize credit usage

We achieve the above through our automatic inactivity stopper as described below.

### Automatic stopping due to inactivity

In order to efficiently allocate resources, Nuvolos automatically stops inactive applications. Research and Education spaces are handled differently.

#### Research Spaces

For **research spaces** Nuvolos considers an application being active if **either**: 

* It is actively opened on Nuvolos
* It is actively computing \(using more than half of a single virtual CPU\)

In Research-purpose spaces, the default inactivity limit is **six hours** \(configurable\).

{% hint style="info" %}
Researchers can launch long running computations and their application will keep running until actively computing. If the computation is finished \(either due to completion or an error\) and the application is not opened on Nuvolos, it will be auto-stopped. We therefore recommend explicitly capturing output logs to ensure that any warnings or errors are captured.
{% endhint %}

#### Education spaces

For **education spaces** the application is only considered active if it is actively opened on Nuvolos, unattended long-running computations will be automatically terminated.

In Education-purpose spaces, the default inactivity limit is **one hour**.

{% hint style="info" %}
To keep an application active in an education space, you need to make sure that the application is in focus in your browser for more than one \(uninterrupted\) minute every hour.
{% endhint %}



