---
description: Nuvolos Compute Units explained
---

# Nuvolos Compute Units

## Definition

Nuvolos Compute Unit \(NCU\) is the computational unit for regular \(non-[HPC](../../research/hpc-interactive.md)\) applications run by users.

In terms of computational resource, an NCU consists of 1 virtual CPU \(vCPU\) and 4 GBs of RAM and adequate temporary storage to run a particular application.

## NCU hold of applications

Every time a user starts an application, a corresponding number of NCUs are checked out from the service. As a general rule of thumb:

* Applications in teaching spaces consist of a single NCU,
* applications in research spaces consist of 5 NCUs.

It is possible to calibrate applications with different NCU requirements, please reach out to our support in order to configure a different setup for your application.

## NCU limits of a resource pool

Each resource pool is endowed with a certain number of NCUs available to be used consecutively. The information of NCU limits is available in the [Monitoring dashboard](monitoring-resource-usage.md). There are three types of NCUs quoted, each differ in terms of time availability:

* **Round-the-clock** NCUs are available to use 24 hours a day, every day of the term of the Nuvolos subscription.
* **Power save** NCUs are available to use 12 hours a day, every day of the month during the academic year \(thus power save NCUs are not available in the summer months\).
* **Burst** NCUs are available to user 3 hours a day every workday during the academic year \(thus, burst NCUs are not available in the summer months\).

In practice, each NCU type corresponds to a certain amount of compute hour limit for the subscription term:

* **Round-the-clock** NCUs are available for 8760 hours a year.
* **Power save** NCUs are available for 3240 hours a year.
* **Burst** NCUs are available for 540 hours a year.

To calculate the total compute hours available to a resource pool for a year, the total amount of compute hours available to a resource pool is the sumproduct of resource pools and the above yearly rates.

