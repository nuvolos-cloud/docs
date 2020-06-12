---
description: Getting started with doing research
---

# Get started

## Set up a research project

Research projects are spaces in Nuvolos where researchers can store and work on their code and data. Organization managers or faculty members may create research projects.

1. Navigate to _Research Projects_
2. Select "NEW RESEARCH PROJECT"
3. Enter desired project name and description
4. Select "ADD SPACE"
5. Select application
6. Enter desired application name
7. Select "ADD APPLICATION"

![Creating a research project](../.gitbook/assets/create_research_project_ed.gif)

When you create a research project, the project initializes with an instance called "Master instance". This is where the application will also be added.

## Add material to the project

You can add files and source code to your project via the file download/upload feature of Nuvolos.

![Uploading files](../.gitbook/assets/research_upload_file_ed.gif)

## Create alternate approaches

Creating alternate approaches in your research project can be done in two steps:

1. Create a new instance with an appropriate name.
2. Distribute material from the main master instance.
3. You will need to be comfortable with context switching, we suggest to take a look at our [navigation guide](../getting-started/navigation-in-nuvolos.md).

#### Create new instance

To create an instance:

1. Navigate to the overview of any instance in your space \(you can do this from the dashboard\).
2. Click on the gear button on the sidebar or equivalently the "Project Users" tile.
3. Switch to the instances tab and select "ADD NEW INSTANCE"
4. Pick whether you want to create an empty instance or to initialize it from an existing snapshot.
5. Name and describe your instance.

![Create a new empty instance](../.gitbook/assets/create_instance_ed.gif)

#### Distribute material to modify

To distribute some material:

1. First navigate to the files, applications you want to distribute.
2. Click on the stage button for the objects you want to distribute.
3. Click on the distribute menu on the sidebar or on the overview.
4. Follow the steps of distribution, for more details, refer to [our detailed guide](../getting-started/distribute-objects-in-nuvolos/).

In the following example, we distribute two files and an application to the previously created empty instance.

![Distributing material to an empty instance](../.gitbook/assets/research_distribute_ed.gif)

{% hint style="info" %}
Distribution is an asynchronous task - once you initiate it, it will run in the background. You will receive an e-mail with the outcome of a distribution.  
If the distribution fails for some reason, do not hesitate to contact us at [support@nuvolos.cloud](mailto:support@nuvolos.cloud).
{% endhint %}

Once the distribution has completed, we can verify that the distributed items are still there.

![Switching to the alternate instance with the new content in](../.gitbook/assets/verify_distribute_ed.gif)

## Invite collaborators

You can invite collaborators if you are a [space admin](../settings-and-administration/role-system.md#space-admin) in a research project. By default the creator of the project automatically becomes space admin, every other user has to be invited specifically with that role.

To make an informed decision about the type of roles you want in your project, consult [our detailed guide](../settings-and-administration/role-system.md).

### Invite co-authors with space admin rights

{% hint style="info" %}
If you invite a co-author to your project as a space admin, restricted to the project, they will receive every possible right, including the ability to invite additional co-authors, create alternate instances and deleting the project itself.
{% endhint %}

To invite a co-author, do the following steps:

1. Navigate to your space.
2. Either click on the "Project users" tile or select the gear button on the top of the left sidebar and select "Project Users" there.
3. Click on "Invite" in the top right corner of the pane.
4. Pick "Administrator Invitation".
5. Type the e-mail address, or comma separated list of e-mail addresses.

The invitations will be sent by e-mail to the recipients who need to accept the invitation to gain the role.

![Inviting a co-author as space admin](../.gitbook/assets/space_admin_research_invite_ed.gif)

 

### Invite co-authors with editor rights

{% hint style="info" %}
If you invite a co-author to your project as an instance editor to an instance, they will only be able to see and edit the contents of that particular instance. They will not be able to create more instances, invite users or do any modifications outside the scope of the particular instance they have the right to edit.
{% endhint %}

To invite a co-author as an instance editor, do the following steps:

1. Navigate to your space.
2. Either click on the "Project users" tile or select the gear button on the top of the left sidebar and select "Project Users" there.
3. Click on "Invite" in the top right corner of the pane.
4. Pick "User Invitation".
5. Pick the instance and the role you want to invite the user with.
6. Type the e-mail address, or comma separated list of e-mail addresses.

![Inviting an instance editor to the &quot;Alternate&quot; instance](../.gitbook/assets/instance_editor_research_invite_ed.gif)

## Work with applications

In Nuvolos, each application is a separate entity with a separate set of resources and environmental settings. Some important considerations:

1. You can have multiple applications of the same type \(e.g. RStudio\) in the same instance with different sets of packages or package versions.
2. When you [take a snapshot](../settings-and-administration/instance-management/create-a-snapshot.md), applications are snapshot along with all the packages, environmental files and so on.
3. Applications can be distributed \(see above\).

### Create a new application

In the workflow guide, we previously created an RStudio application upon creating the space itself. We will add a JupyterLab application to the Master instance of the research project.

1. Navigate to the Master instance overview \(from the dashboard or by changing context in the [breadcrumbs](../getting-started/navigation-in-nuvolos.md#the-breadcrumb)\)
2. Click on the Applications tile or sidebar menu item.
3. Click "ADD NEW APPLICATION" and choose the appropriate type.

![Add a new application](../.gitbook/assets/create_app_research_ed.gif)

### Run an application

In order to run an application, you can follow two routes:

1. Run a recent application from your dashboard.
2. Navigate to the instance of your choice and run the application directly from there.

#### Running from dashboard

The three latest applications will appear on your dashboard. You can verify the location of the application by hovering over the start-stop button.

#### Running from an instance

You can navigate to the application view of your instance and find the list of applications there.

We present a hybrid of the two approaches by showing how to find the recent applications' instance and running it from there:

![Starting an application by navigating to the instance](../.gitbook/assets/start_app_dashboard_ed.gif)

## Work with data

[Consult our detailed guide](../data/work-with-data.md) to start working with data.





