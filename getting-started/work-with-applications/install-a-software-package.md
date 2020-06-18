# Install a software package

In Nuvolos, almost all applications are equipped with conda environments and we also let our users load user-written packages and extensions.

## Basic provisions

All Nuvolos applications come with a set of useful \*nix applications pre-installed:

* git
* git-lfs
* vim
* build-essential \(includes make\)
* xterm for GUI based applications for terminal emulation
* Nuvolos data connectors for supported languages

## The conda environment

Except for R, all Nuvolos applications come equipped with the package manager [conda](https://docs.conda.io/en/latest/). Conda is a non-language specific package manager which lets you install language-specific packages and system libraries as a non-root user.

{% hint style="info" %}
Always try to install software with conda first. We suggest using [conda-forge](https://conda-forge.org/docs/user/introduction.html) instead of anaconda repositories.

If you cannot self-service your packages, contact us at [**support@nuvolos.cloud**](mailto:support@nuvolos.cloud) and we will help you.
{% endhint %}

As an example, suppose you want to install [imagemagick](https://anaconda.org/conda-forge/imagemagick) and [gifsicle](https://anaconda.org/conda-forge/gifsicle) for mass editing gifs. The following command will install this to the conda environment of your application:

```text
conda install -c conda-forge gifsicle imagemagick
```

{% hint style="success" %}
When distributing and snapshotting an application, the contents of the conda environment are also impacted. This is a key feature for reproducibility.
{% endhint %}

## The /dhlib folder

The `/dhlib` folder is the persistent package storage folder on Nuvolos. If a conda environment exists, it is also stored under `/dhlib`, as well as R packages. Only work in conda environments that are based under `/dhlib`!

## Tips and tricks

### Single purpose applications

{% hint style="info" %}
We strongly suggest creating single-purpose applications. 
{% endhint %}

This practice has the following benefits:

1. Conda or R package environments remain monolithic and fairly lightweight.
2. Distribution and snapshotting takes less storage and resources and conclude faster.

### Create a new application instead of upgrading

{% hint style="info" %}
If you are contemplating doing a major version update on your application, we suggest creating a new app in the same instance and starting there from scratch.
{% endhint %}

This practice has the following benefits:

1. Conda environments can break after major updates.
2. The reproducibility of your work may suffer - however it is trivial to maintain two monolithic and separate application structures in parallel, even in the same instance!
3. Distribution is based on filesystem-differences and after-upgrade distributions may become less stable due to the massive number of changes occurring on the filesystem.
