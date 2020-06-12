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



## R/RStudio



