# Restore a snapshot

{% hint style="info" %}
Restoring a snapshot means replacing the content of the current state with the content of the snapshot being restored. Make sure that you have the right permission to restore a snapshot. Only instance editors are allowed to restore snapshots. If you don't have the right permissions to restore a snapshot, then you can either ask the instance editor to do so, or you can ask the instance editor to share the snapshot in your instance and where can work with that snapshot.  
{% endhint %}

## **To restore a snapshot:**

1- Open a space.

2- Go to the timeline view of snapshots, which you can do via the toolbar breadcrumbs or from the left sidebar.

![](../../.gitbook/assets/screen-shot-2020-03-19-at-3.17.21-pm.png)

3- Identify the snapshot you want to restore.

4- If you want to restore the snapshot to the current state of the currently selected instance, then click on the restore icon next to the snapshot name. Otherwise, if you want to restore the snapshot to the current state of another instance \(of which you should be an editor\) then click on the two persons icon.

![](../../.gitbook/assets/screen-shot-2020-03-19-at-3.21.54-pm.png)

5- If you chose to restore to the current state of the selected instance, then you will need to confirm the operation. Otherwise, if you chose to restore to another instance, then you will be asked to select the target instance.

{% hint style="success" %}
Regardless of the target instance selected, an automatic snapshot of the current state of the target instance will be created before restoring the snapshot. This allows the user to revert the restoration operation.
{% endhint %}
