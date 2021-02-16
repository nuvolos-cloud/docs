---
description: >-
  This feature is still in preview and might be subject to changes in the
  future.
---

# Dropbox synchronization \(preview\)

Nuvolos supports synchronizing files with your Dropbox account. In order to enable synchronization, go to the [Account &gt;  Settings &gt; Dropbox](https://nuvolos.cloud/user/dropbox) menu and click the **Enable** button. 

Nuvolos will have its own special folder inside Dropbox, to avoid requesting access to your complete Dropbox account. According to the convention of Dropbox, files synced with Nuvolos will be stored under the **Apps &gt; nuvolos.cloud** folder in your Dropbox account. The Organization &gt; Space &gt; Instance hierarchy will be reflected inside the **Apps &gt; nuvolos.cloud** folder.

Once your account is linked, whenever a Nuvolos application is started \(if you already have the application running, then stop it and restart it\) the synchronization to Dropbox will begin as well.

Whilst for most cases **instantaneous bidirectional synchronization** will happen between Nuvolos and Dropbox, currently the following limitations apply to Dropbox synchronization:

* Files created outside **your** application \(e.g. uploaded on the web interface, created by a co-author, distributed from another instance\) will only be synchronized every hour.
* The synchronization only runs if your application is running.

{% hint style="warning" %}
**Restoring Nuvolos snapshots requires special care** if Dropbox integration is enabled, as otherwise, the Dropbox version of the files \(more recent\) will overwrite the restored files.

If Dropbox integration is enabled, proceed as follows to restore from a snapshot:

1. In Nuvolos, restore the snapshot - this will also automatically stop applications.
2. In Dropbox \(website or local application\), delete the instance folder \(located at: Apps &gt; nuvolos.cloud &gt;  \[Your Org\] &gt; \[Your space\] &gt; **\[ Your Instance \]** \) 
3. In Nuvolos navigate to the Files view and select "Personal" instead of "Workspace". Then check the "Show hidden files" option
4. Still in the Nuvolos Files view, delete the ".local &gt; share &gt; maestral" folder 
5. In Nuvolos, start your application. Upon the successful start, the Dropbox synchronisation service in Nuvolos will recreate the instance folder. Next, the synchronisation with Dropbox for the restored files shall resume.
{% endhint %}


