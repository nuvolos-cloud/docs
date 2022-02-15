# Clone a Github repository

While creating a new space, you may choose to clone a repository hosted on Github.com. Both public and private repositories are supported.

{% hint style="success" %}
If you want to use SSH URLs(git@...), you **need** to set up SSH access from Nuvolos to GitHub, even for cloning public repositories! To get help with setting up your SSH keys, please follow our guide here: [https://docs.nuvolos.cloud/troubleshooting/research#researcher-is-git-supported](https://docs.nuvolos.cloud/troubleshooting/research#researcher-is-git-supported)
{% endhint %}

{% hint style="warning" %}
You can choose to use an HTTPS URL, especially if you only wish to pull from a public repository. If you plan to push commits to the remote, we recommend using a SSH URLs (as the HTTPS version will ask for username & password).
{% endhint %}

To initialize the space from a GitHub repository, click the 'Create space based on a template' switch to bring up new options:

![Cloning a Github.com repository](../../../.gitbook/assets/find\_the\_clone\_switch.png)

Click 'Clone a Github repository' and type or paste the URL for the repository you would like to clone.

![The space is ready to be created](<../../../.gitbook/assets/Screenshot 2022-02-14 at 17.37.05.png>)

Clicking 'Add Space' button will create the space for you, where you can add your applications as usual. Initialization happens in the background and depending on the size of the repository it may take some time to complete. You can check its progress using the 'Tasks' entry on under 'User notifications'.

Once the cloning is finished, the repository will be available in the root directory of every application in the space.
