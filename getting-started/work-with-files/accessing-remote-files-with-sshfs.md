---
description: Preview feature
---

# Accessing remote files with SSHFS

In Nuvolos applications, you can access files stored on your server via a secure SSH connection and use them as if they were on the file system of the Nuvolos application.

## Prerequisites

### Create an SSH key

To be able to authenticate with your server using SSH, you will need to create an SSH key in Nuvolos and add the generated public key to the `authorized_keys` file on your server to accept the newly generated SSH key. Under Linux systems, the file is usually located under `~/.ssh/authorized_keys` .

To do this, [go to your account settings](https://app.nuvolos.cloud/user/settings/profile) and click on the _SSH Keys_ tab. Click on the _Generate SSH Key_ button to create an SSH key:

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-03 at 14.58.38.png" alt=""><figcaption></figcaption></figure>

### Configure the connection using environment variables

Next, on the _Environment_ tab, add the following environment variables that specify:

* `SSHFS_USER`: The username to use when connecting with the remote host.
* `SSHFS_SERVER`: The SSH server Nuvolos applications will connect to.
* `SSHFS_REMOTE_PATH`: The path on the remote SSH server to be mounted.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-03 at 15.03.54.png" alt=""><figcaption></figcaption></figure>

## Configuring your Nuvolos application

Currently, SSHFS connection is a preview feature, please reach out to Nuvolos Support to enable SSHFS mounting for your specific Nuvolos application. Once the feature will reach GA state, this will be configurable in the Nuvolos application configuration.

## Accessing remote files

Once the prerequisite configuration has been done and the applications have been also configured to use SSHFS, you can start your Nuvolos application.&#x20;

The files from the remote server will be accessible under the path `/sshfs`. If you wish to use a different path, please reach out to Nuvolos support.
