---
description: Performance, timeout limits, shared access and optimizations
---

# Configuring applications

When working with student applications on Nuvolos, it is important to consider the following performance characteristics:

### Resource allocation time

If a class size is large (e.g. above \~50 users / or if individual applications have been customized to request higher resources) and students are expected to launch their applications at the same time, it can happen that resource allocation becomes slower (e.g. application launch time can be around 5 minutes instead of the usual 30-60 seconds).&#x20;

For a good user experience, we recommend that instructors pre-launch the required application(s) for all users before students are expected to start work with it. Nuvolos supports both automatic and manual application prestart.&#x20;

In both automatic and manual mode the progress and outcome of a pre-launch is visible in the task view.

{% hint style="info" %}
For optimal resource allocation, only the very first prestart triggers the start of a given application for all users in the space. Subsequent prestart events first check which users actually used the applications around the **last prestart time**, and the app will be started only for them automatically.&#x20;
{% endhint %}

#### Automatic

Using automatic application prestart instructors can create scheduled prestarts ahead of time. This can be performed from the 'Application' view in the sidebar, by clicking on the three dots beside the application name and selecting the 'Schedule for start' option, and setting the time and date by when all apps in the space should be up and running.&#x20;

The following limitations apply:\
\- The time of the schedule has to be in at least 30 minutes, as it takes time to start all applications. \
\- In a space, up to twenty scheduled prestarts can exist at the same time\
\- Setting a prestart date more than 6 months into the future is not allowed\
\- Setting a prestart date for archived courses is not allowed

![](../../.gitbook/assets/scheduled\_startup.png)

The scheduled prestarts can be viewed, edited, and deleted from under the list of applications. If you wish the create a new schedule for the same time a week away, you can do that by clicking on 'add to next week' under the Actions column.

![](../../.gitbook/assets/scheduled\_startups.png)

The next scheduled startup can also be viewed from the space overview page.

![](../../.gitbook/assets/next\_scheduled\_startup.png)

#### Manual

Pre-launching can be performed from the 'Applications' view on the sidebar, by clicking the three dots beside the application name and selecting the 'Start for all users' option:

![](../../.gitbook/assets/start\_for\_all.png)

{% hint style="info" %}
Student applications are stopped automatically after 1 hour of inactivity, so it does not make sense to perform the pre-launch more than an hour before the planned start time.
{% endhint %}

Pre-launching will start the application for all users in the space: for students, their respective applications will be started, for space administrators, the application in the master instance will be started. In case a space administrator is also an editor in a student instance, that application will also be started for the administrator.

### Configuring applications

Each application can be configured by a space administrator. The following aspects may be customized:

1. Application inactivity timeout
2. Application resources
3. Shared access

All of these items can be found by clicking on **Configure** in the Applications view of an Instance.

![](../../.gitbook/assets/configuration.png)

#### Configuring application inactivity timeout

Please refer to our documentation of [inactivity](https://docs.nuvolos.cloud/getting-started/work-with-applications/long-running-applications#automatic-stopping-due-to-inactivity) for details on what we understand on an application breaching the inactivity limit. The slider changes the amount of time (in hours) after which the application is shut down if it is inactive during the time period. If you distribute an application, the setting at the time of distribution is also enforced at the target application.

{% hint style="warning" %}
Increasing the inactivity limit may result in higher-than-desired resource utilization of your organization.
{% endhint %}

#### Configuring application resources

Resource availability to applications running in non-exclusive environments is understood in Nuvolos Compute Units (NCUs). For a detailed description of NCUs, you may refer to its [documentation](https://docs.nuvolos.cloud/settings-and-administration/billing-budgeting-and-resource-pools/nuvolos-compute-units#definition). You may scale the NCU allocation of an application to a higher or lower level depending on the expected workload of the application. Applications can be started with 1, 2, 4, 8, 12 or 16 NCUs. If you distribute an application, the setting at the time of distribution is also enforced at the target application.&#x20;

{% hint style="warning" %}
Increasing the NCU utilization of an application may result in higher-than-desired resource utilization of your organization.
{% endhint %}

#### Configuring shared access

Applications can be configured to be shared access in case shared group work is expected from users of an instance. Please refer to our detailed guide [here](set-up-group-work/collaborative-editing.md).

### Performance sensitive code

On Nuvolos each student runs the code with the same application configuration as the instructor.

Nevertheless it is important to consider that when many students are concurrently executing a computationally intensive code, the application performance might be inferior to what the instructor experienced during material development when potentially the load from other users was lower.

Whilst usually this is within a reasonable factor, we recommend that during **interactive sessions with a large number of students**, either:

a) Code examples should be adjusted such that  they execute within a minute or so maximum.

b) The space should be configured to have larger per-student resources to provide adequate compute performance. For the most performance sensitive cases, we suggest dedicated compute nodes for each application - please reach out to our support team to discuss such an option.

For out-of-class work when concurrency is lower, these considerations can be appropriately relaxed.
