# Clone a Github repository

While creating a new space, you may choose to clone a repository hosted on Github.com. Both public and private repositories are supported, however your unique ssh key needs to be set up before the feature is ready for use.

{% hint style="success" %}
To get help with setting up your SSH keys, please follow our guide here: [https://docs.nuvolos.cloud/troubleshooting/research#researcher-is-git-supported](https://docs.nuvolos.cloud/troubleshooting/research#researcher-is-git-supported)
{% endhint %}

{% hint style="warning" %}
You can choose to use an HTTPS based URL, however SSH is preferred, if you plan to make changes and push them to the repository. If you decide to use an HTTPS url, SSH key set up can be safely skipped.
{% endhint %}

Type a name for the course and a short description, then pick the resource pool to be used. Click the 'Create space based on a template' switch to activate it:

![Cloning a Github.com repository](../../../.gitbook/assets/find\_the\_clone\_switch.png)

Click 'Clone a Github repository' and type or paste the URL for the repository you would like to clone.

![The space is ready to be created](<../../../.gitbook/assets/Screenshot 2022-02-14 at 17.37.05.png>)

Clicking 'Add Space' button will create the space for you, where you can add your applications as usual. Cloning happens in the background and depending on the size of the repository it may take some time to complete. You can check its progress using the 'Tasks' entry on under 'User notifications'.

Once the cloning is finished, the repository will be available in the root directory of every application in the space.
