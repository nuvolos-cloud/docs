---
description: >-
  This feature is still in preview and might be subject to changes in the
  future.
---

# Dropbox synchronization \(preview\)

Nuvolos supports synchronizing files with your Dropbox account. In order to enable synchronization, go to the Account &gt;  Settings &gt; Dropbox menu and click the **Link your Dropbox Account** button. 

Nuvolos will have its own special folder inside Dropbox, to avoid requesting access to your complete Dropbox account. According to the convention of Dropbox, files synced with Nuvolos will be stored under the **Apps &gt; nuvolos.cloud** folder in your Dropbox account. The Organization &gt; Space &gt; Instance hierarchy will be reflected inside the **Apps &gt; nuvolos.cloud** folder.

Once your account is linked, whenever a Nuvolos application is started \(if you already have the application running, then stop it and restart it\) the synchronization to Dropbox will begin as well.

Whilst for the most case **live bidirectional synchronization** will happen between Nuvolos and Dropbox, currently the following limitations apply to Dropbox synchronization:

* Files created outside **your** application \(e.g. uploaded on the web interface, created by a co-author, distributed from another instance\) will only be synchronized every hour.
* The synchronization only runs if your application is running.
* In a given instance only one application can run \(you can run multiple applications in different instances\).

