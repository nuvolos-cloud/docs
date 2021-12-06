---
description: Generic recommendations to recover from application issues
---

# Troubleshooting applications

In certain cases an application might become unresponsive, unstable or unable to start. This might be due to:

* An application level problem (e.g. RStudio can freeze the browser if outputting too much information)
* A configuration issue
* A problem occuring after installing extensions or software packages

Nuvolos offers the following features to recover from such scenarios:

### Clearing user application settings

If an application is not launching, freezing or otherwise misbehaving (e.g. has wrong screen resolution), the first thing to try is to clear user application settings. Most applications store files in the HOME folder of the user, which can be easily cleared in Nuvolos using the applications list.

Steps:

1\. Navigate to the application list

2\. Select "Clear settings" in the "..." menu for the given application

![](<../../.gitbook/assets/image (17).png>)

3\. Launch the application again.

### Restore application libraries

In certain cases installing an application package / library / add-on can adversely impact the behavior of an application (e.g. not being able to execute a code or launch the application).

In this case please try restoring the application from a snapshot that contains a still working version of the application:

1. Open the snapshot from the snapshot view
2. Open the application list on the sidebar
3. On the "..." beside the application select to Stage the application
4. Start a distribution to the given instance which will overwrite the packages with the snapshotted version
5. Once the distribution is complete, restart the application
