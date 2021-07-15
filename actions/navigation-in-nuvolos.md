---
description: How to find your way around Nuvolos
---

# Navigate in Nuvolos

Navigation in Nuvolos is closely linked to the [structure of Nuvolos](../data-organization/). The user can understand their position and navigate using the following highlighted parts of the user interface.

1. The **Nuvolos** logo
2. The **breadcrumbs**
3. The **navigational sidebar**

### The Nuvolos logo

The nuvolos logo will always take the user to the _Dashboard._

## The breadcrumb

The breadcrumb is a sequence of selectable drop-down lists that allows the user to choose the organization \(level 1\), space \(level 2\), instance \(level 3\), and state \(level 4\). For example, if the user is looking at a state overview, the breadcrumb will look like the following:

In the above breadcrumb, the following information is available:

* The user is currently in the "NEW ORGANIZATION" organization.
* The user is in the "NO NAME" space inside the organization.
* Inside the space, the user is working in the "MASTER" Instance.
* Inside "MASTER", the user is working with the "CURRENT STATE", which is the mutable state.

As visible, the breadcrumb can take the user either to the Dashboard \(via the home icon\), or the user can change the organization, space, instance, or snapshot where one of the following could happen:

* If the user changes the organization, then the interface will redirect to the dashboard and a space needs to be selected.

![](../.gitbook/assets/screen-shot-2020-03-16-at-2.14.11-pm.png)

* If the user changes the space, then three scenarios are possible depending on the rule the user has in the particular space:
  * If the user is an administrator of the space, then they will be taken to the "CURRENT STATE"  state of the "MASTER" instance of the selected space.
  * If the user is not a space administrator but has an editor role in one of the instances, then they  will be taken to the "CURRENT STATE" state of that instance.
  * If the user is not a space administrator or an instance editor, then they will be taken to one of the immutable states of an instance where the user is a viewer.

## The sidebar

There are two navigational sidebars in Nuvolos: the dashboard sidebar and the state-level sidebar.

### Dashboard sidebar

From the dashboard, the sidebar will look similar to this:

Visibly, the Dashboard icon is highlighted, making clear that the user is currently viewing the Dashboard of Nuvolos. Clicking on any of the other icons, either a list of spaces will be visible, or the list of Organization Users \(granted that the viewer has appropriate role to view the list of the organization users\).

### State-level sidebar

The second sidebar is used in state level work, or when the user is doing work in an application.

The layout is the following:

From top to bottom the icons will take the user to the following views \(also visible by hovering over an icon\):

* Overview
* Space, instance, and state settings \(available only for space administrators\)
* Files
* Tables
* Applications
* Snapshot operations \(create snapshot, view snapshots\)
* Object distribution

Similar to the dashboard sidebar, the currently active view is highlighted with a darker background.



