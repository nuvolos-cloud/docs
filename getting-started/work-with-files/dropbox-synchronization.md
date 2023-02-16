---
description: >-
  Keep your files on Nuvolos in sync with your Dropbox account, enabling
  seamless transition between work on Nuvolos and your local computer.
---

# Dropbox synchronization

### Link your Dropbox account

Nuvolos supports synchronizing files with your Dropbox account. In order to enable synchronization, go to the [Account >  Settings > Dropbox Sync ](https://az.nuvolos.cloud/user/settings/dropbox) and click the **Enable Access** button. You'll be redirected to Dropbox to log in with your account and authorize Nuvolos to read and write parts of your dropbox storage area.

{% hint style="info" %}
In case you're logged in to Dropbox at the time of starting the linking process on Nuvolos, the system will automatically assume that you want to link the Dropbox account you're logged in with. However, you can link any Dropbox account, even with a different email address. Just make sure you log out of Dropbox before starting the linking process, then you'll be able to choose which Dropbox account to link.&#x20;
{% endhint %}

Nuvolos will have its own special folder inside Dropbox, to avoid requesting access to your complete Dropbox account. According to the convention of Dropbox, files synced with Nuvolos will be stored under the **Apps > nuvolos.cloud** folder in your Dropbox account. The Organization > Space > Instance hierarchy will be reflected inside the **Apps > nuvolos.cloud** folder.

{% hint style="info" %}
Once your account is linked, whenever a Nuvolos application is started (if you already have the application running, then stop it and restart it) the synchronization to Dropbox will begin as well.
{% endhint %}

Whilst for most cases **instantaneous bidirectional synchronization** will happen between Nuvolos and Dropbox, currently the following limitations apply to Dropbox synchronization:

* Files created outside **your** application (e.g. uploaded on the web interface, created by a co-author, distributed from another instance) will only be synchronized once the application is restarted.
* The synchronization only runs if your application is running.

### Restoring Nuvolos snapshots

Restoring Nuvolos snapshots requires special care if Dropbox integration is enabled, as otherwise, the Dropbox version of the files (more recent) will overwrite the restored files.

If Dropbox integration is enabled, proceed as follows to restore from a snapshot:

1. In Nuvolos, restore the snapshot - this will also automatically stop applications.
2. In Dropbox (website or local application), delete the instance folder (located at: Apps > nuvolos.cloud > \[Your Org] > \[Your space] > \[ Your Instance ] )
3. In Nuvolos navigate to the Files view and select "Personal" instead of "Workspace". Then check the "Show hidden files" option Still in the Nuvolos Files view, delete the `.local > share > maestral`folder
4. In Nuvolos, start your application. Upon the successful start, the Dropbox synchronisation service in Nuvolos will recreate the instance folder. Next, the synchronisation with Dropbox for the restored files shall resume.

### Excluding files

Files can be excluded from synchronization by editing the hidden file /files/.mignore&#x20;

This file follows the [same syntax as .gitignore ](https://git-scm.com/docs/gitignore#\_pattern\_format)
