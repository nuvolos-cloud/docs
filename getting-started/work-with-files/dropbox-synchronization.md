---
description: >-
  This feature is still in preview and might be subject to changes in the
  future.
---

# Dropbox synchronization \(preview\)

Nuvolos supports synchronizing files with your Dropbox account. In order to enable synchronization, go to the Account &gt;  Settings &gt; Dropbox menu and click the **Link your Dropbox Account** button. 

Nuvolos will have its own special folder inside Dropbox, to avoid requesting access to your complete Dropbox account. According to the convention of Dropbox, files synced with Nuvolos will be stored under the **Apps &gt; nuvolos.cloud** folder in your Dropbox account. The Organization &gt; Space &gt; Instance hierarchy will be reflected inside the **Apps &gt; nuvolos.cloud** folder.

Once your account is linked, whenever a Nuvolos application is started \(if you already have the application running, then stop it and restart it\) the synchronization to Dropbox will begin as well.

Whilst for the most case **instantaneous bidirectional synchronization** will happen between Nuvolos and Dropbox, currently the following limitations apply to Dropbox synchronization:

* Files created outside **your** application \(e.g. uploaded on the web interface, created by a co-author, distributed from another instance\) will only be synchronized every hour.
* The synchronization only runs if your application is running.

{% hint style="warning" %}
**Restoring Nuvolos snapshots requires special care** if Dropbox integration is enabled, as otherwise the restored files will be overwritten from the copies from Dropbox.

If Dropbox integration is enabled, the following steps need to be taken when restoring a snapshot:

1. Restore the snapshot in Nuvolos - this will also automatically stop applications.
2. In Dropbox delete the instance folder \(located at: Apps &gt; nuvolos.cloud &gt;  \[Your Org\] &gt; \[Your space\] &gt; **\[ Your Instance \]** \) 
3. In Nuvolos navigate to the Files view and select "Personal" instead of "Workspace". Then check the "Show hidden files" option
4. In Nuvolos Files view delete the ".local &gt; share &gt; maestral" folder 
5. Start your application, now the instance folder will be recreated and the restored files should be synchronized back to Dropbox.
{% endhint %}



