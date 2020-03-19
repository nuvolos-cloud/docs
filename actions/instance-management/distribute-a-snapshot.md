---
description: >-
  By distributing objects (files, tables, or applications) to another instance,
  the objects being distributed will be added and merged with the content of the
  current state of the target instance.
---

# Distribute objects

![](../../.gitbook/assets/info_simple.svg.png)AAP allows you to distribute the entire contents of your current state or a snapshot, otherwise you can distribute a few selected objects.

![](../../.gitbook/assets/info_simple.svg.png)Whether you choose to distribute the entire contents of a snapshot \(or current state\) or selected objects, a backup snapshot of the current state of the target instance will automatically be created before the merge.

![](../../.gitbook/assets/info_simple.svg.png)When you press the button to distribute, the actual operation will be scheduled and executed in the background. Upon completion, you will receive a notification email at your registered email address confirming the success or failure of the task.

## **There are two options to distribute objects:**

### **- Option 1: Distribute all/selected objects to existing instances.**

![](../../.gitbook/assets/info_simple.svg.png)**This option assumes that the instances with which you want to share the objects exist already.**

1. Open a state \(current state or an immutable snapshot\) 
2. If you want to distribute specific files or folders, you can use the STAGE button under the actions column in the table. The stage button is available for files, tables, and applications. 
3. If you want to distribute everything in your current state/snapshot, then go to the next step directly. 
4. From the sidebar on the left, click on STAGE. 
5. Choose whether you want to distribute the files you staged in step 3, or the the entire state. 
6. Next, select the target organization and space to which you want to distribute. In the selected space, you can choose to distribute to all instances or just a subset of them \(Please check [Notes on distribution to all instances](distribute-a-snapshot.md#notes-on-distribution-to-all-instances) about possible restrictions\). 
7. Select the distribution strategy for each of the three file types. The distribution strategy determines how to resolve potential conflicts between the state you're distributing from and the state you're distributing to. DataHub provides the following strategies for the respective use cases: 
   1. You want to distribute **extra objects** only, e.g. you want to distribute new pdf file\(s\) to all other instances. However, you don't want to overwrite any changes to files you have distributed earlier, because e.g. your students were supposed to work on the notebook you distributed yesterday. In this case, you want to use the "**Distribute extra objects \(files and tables\) compared to target**" option.
   2. You want to distribute the current state of your objects to the target state, even if it means **overwriting existing objects**. This is usually relevant if you want to e.g. distribute solution\(s\) to replace the previously distributed exercise file\(s\). After the distribute, each instance will have your version of the solution, while any original work done on the objects will still be accessible in the immutable snapshots taken before the distribution was carried out. In this case, you want to use the "**Distribute all objects \(overwrite target\)**" option.  Note that any additional files will be retained in the target state that are not contained in the state being distributed. This allows the target state to retain extra objects.
   3. You want to make sure that the target objects are **exacts replicas** of the source objects. If you distribute all objects, this will first clean the target state completely and create an exact replica of the source state. If you distribute only selected objects, each object will be cleaned and replaced separately. In this case, you want to use the "**Clean and replace target**" option.

  
8. Click on the **DISTRIBUTE**  button at the bottom. 

### **- Option 2: Distribute all objects to new instances.**

![](../../.gitbook/assets/info_simple.svg.png)**With** t**his option, you can only distribute the ENTIRE contents \(files, tables, and applications\) of your current state/snapshot and not selected files. For the Current State, this option will be available only if you haven't shared any full snapshot of the current state with other instance in your current space. For immutable states, the option is always available.**

1. Open a state \(current state or an immutable snapshot\).

2. According to your choice in step 2, you would see either of two options:

* If your choice was CURRENT STATE, then at the top of the page you will see the following banner and you have to click on INVITE AND SHARE STATE.

Starting from the CURRENT STATE, this will take you through a two-step operation where you first create a snapshot, and then you create one or more instances. First you need to provide a name and description of the snapshot, as well as a description of the next work phase. The next work phase description will be used to update the description of the current state. If no work is expected in the near future, tick the "No work is expected in the next stage" button. Once you create a snapshot, then you will be asked to choose the instance creation method and provide the necessary information\(see [here](../space-management/create-an-instance.md) for details\).

* If instead your choice was an immutable snapshot, then at the top of the page you will see the following banner and you have to click on CREATE INSTANCE.

![](../../.gitbook/assets/current_state.png)

In this case, all you need to do is to choose the instance creation method and provide the necessary information \(see [here](../space-management/create-an-instance.md) for details\).

#### Notes on distribution to all instances

Distribution to all instances bears special significance in the educational workflow: usually, you distribute new material to all instances, because you want to have each student to have the same material. When you distribute to all instances, in reality you first distribute to the special **Distributed** **instance**, and the objects will be distributed from there to all other instances subsequently. The reason for this behaviour is twofold:

* You may distribute objects from the current state, which is mutable. Since distribution is not instantaneous, it could happen that you change the current state _during_ a distribution process, which would result in inconsistent states distributed to different instances. To avoid it, DataHub first distributes your current state to the **Distributed instance**, and from there _the same immutable state_ is distributed to all other instances. This ensures consistency between instances.  ![](../../.gitbook/assets/info_simple.svg%20%281%29.png) For this very reason, you may only distribute to _exactly one_ target instance, if you're distributing from a mutable state. 
* As you distribute more than once, sometimes maybe only selectively, the state of the student instances become more and more complex. But what if a new student comes along, and you're supposed to create the same "starting state" for him/her too? This is where the Distributed instance comes in handy: the **Distributed instance** contains the **cumulative result of your subsequent distributions**. To get your new student up to speed, just create a new instance from the last snapshot in the Distributed instance: it'll contain everything you've distributed so far. 

#### ![](../../.gitbook/assets/info_simple.svg.png)If you are encountering a problem distributing a snapshot, refer to the troubleshooting guide [here](../../troubleshooting/authorization-issues/i-cant-distribute-a-snapshot.md). 

\*\*\*\*

## 

![This chart illustrates the process of snapshot distribution. A professor is the editor of the Master instance and they have one snapshot \(Snapshot 1\) taken at some point in time. Assume that the professor decides to distribute their snapshot to student 1. Once this snapshot has been distributed, the current state of student 1 will now contain the files, tables, and applications created by the student \(in white\) as well as the files and tables shared by the professor \(in yellow\). A copy of the snapshot distributed by the professor gets automatically stored in the Distributed instance.](../../.gitbook/assets/copy-of-datahub-architecture-main-architecture-2.svg)



