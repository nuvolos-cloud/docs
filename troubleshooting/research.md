# Research

## Researcher: Can I use \[Software package x]?

It depends. Our applications come with the conda package manager pre-installed. You can try to install your software package via conda, see our [guide](../getting-started/work-with-applications/install-a-software-package.md) for more details.

If the package cannot be installed via self-service, then please contact us at [**support@nuvolos.cloud**](mailto:support@nuvolos.cloud).

## Researcher: Is git supported?

Yes, git is supported via applications. In any application you can start, **git and git-lfs is available on the command line** of your application.

Each user has their own ssh key which they can use to authenticate with git repositories. This requires two steps:

1. [Copy your Nuvolos public key](https://az.nuvolos.cloud/user/settings/ssh) and [add it to your git provider](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).
2. Clone the git repository using the **SSH** protocol (make sure the repository URL starts with **git@**) **** and not via the https protocol.

![](<../.gitbook/assets/image (13).png>)

Now you should be able to securely pull / push code from any application, without having to enter passwords.

## Researcher: Is Dropbox supported?

Yes, please see our [Dropbox integration guide](../getting-started/work-with-files/dropbox-synchronization.md).
