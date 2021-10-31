# Archival

Education spaces typically have a well-defined lifecycle: first the space is prepared for teaching or workshop, then the session(s) take place, finally the space is no longer used actively. To optimize storage usage for our users, education spaces are archived after a previously set date to free up resources that are rarely used anymore.

### What space archival means:

1. Application and personal data in student instances will be backed up to cold storage to free up storage space for use in other spaces.
2. Application and personal data can be [restored easily from snapshots](../../getting-started/working-with-snapshots/restore-a-snapshot.md#restore-a-snapshot) in archived spaces, after which the data can be downloaded or the application(s) can be started again.
3. After a few days grace period, restored instances in archived spaces are re-archived. To access the data or application again, the appropriate snapshot must be restored again. This can be repeated as many times as necessary.

### Notes for space archival:

1. The master and distributed instances in teaching spaces are **never **archived. We understand that instructors usually rely on past courses to build current ones - for that reason, data in the Master and Distributed instances is always just a few clicks away.
2. After a space has been archived, students can still access data and run applications in it. However, archived spaces are not meant for everyday use: instances with restored snapshots are periodically re-archived, without taking safety backups. Restoring a snapshot in an archived space should serve 2 purposes: either to download data or to distribute files/tables/applications to another space.

### Configuring space archival:

You can set the desired archival date at space creation time. The default value is 5 months after creation.

![](<../../.gitbook/assets/image (8).png>)

The space will be archived automatically shortly after the set date.

### Instance re-archival

To access data in student instances of archived spaces, each student can restore past snapshots to the current state. They will be able to work in the instance as before, however after a 3 days grace period, the contents of the current state will be deleted again.

{% hint style="warning" %}
When and instance is re-archived, all files and folders in its current state are deleted permanently. Don't upload new, valuable data to archived instances, as no automatic backup will be taken before re-archival!
{% endhint %}
