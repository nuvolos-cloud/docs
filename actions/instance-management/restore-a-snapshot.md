# Restore a snapshot

![](../../.gitbook/assets/info_simple.svg.png)Restoring a snapshot means replacing the content of the current state with the content of the snapshot being restored. Make sure that you have the right permission to restore a snapshot. Only instance editors are allowed to restore snapshots. If you don't have the right permissions to restore a snapshot, then you can either ask the instance editor to do so, or you can ask the instance editor to share the snapshot in your instance and where can work with that snapshot.

![](../../.gitbook/assets/info_simple.svg.png)Upon a successful completion of the operation, you will be redirected to the snapshot view of your current state where you will see that the files and data are now those of the restored snapshot.  


**To restore a snapshot:**

1. Go to the instance view where you can see the list of snapshots within an instance. This can be done by clicking on level 3 \(Instance\) from the side bar. 
2. From the table of snapshots, choose the snapshot you want to restore and in the corresponding row for that snapshot click on the red icon contained in the column Restore. 
3. Alternatively, you can click on the name of the snapshot in the same table which will illustrate a blue alert message with a button called **RESTORE SNAPSHOT** -&gt; click on that button. 
4. You will then be redirected to a view where you will be warned against the consequences of this action. 
5. An option is available to REVIEW the snapshot before restoring it -&gt; simply click on the **REVIEW** button. 
6. If you have already reviewed the content of the snapshot, click on **RESTORE SNAPSHOT** to complete the operation. 
7. Click on the **DISTRIBUTE SNAPSHOT** button at the bottom.

## 

![This chart illustrates what happens when a snapshot is restored. Take an instance with one snapshot \(Snapshot 1\). When the user restores Snapshot 1, the content of the current state\(files, tables, and applications\) gets replaced by the content of Snapshot 1.](../../.gitbook/assets/instance-restoration-4.svg)



