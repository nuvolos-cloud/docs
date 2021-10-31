# Install a software package

In Nuvolos, almost all applications are equipped with conda environments and we also let our users load user-written packages and extensions.

## Basic provisions

All Nuvolos applications come with a set of useful \*nix applications pre-installed:

* git
* git-lfs
* vim
* build-essential (includes make)
* xterm for GUI based applications for terminal emulation
* Nuvolos data connectors for supported languages

## The conda environment

Except for R, all Nuvolos applications come equipped with the package manager [conda](https://docs.conda.io/en/latest/), and more recent applications alias conda to a faster drop-in replacement called [mamba](https://github.com/mamba-org/mamba). Conda is a non-language specific package manager which lets you install language-specific packages and system libraries as a non-root user. For the Python language, most packages available via **pip** can also be installed via **conda**.

{% hint style="info" %}
Always try to install software with **conda **first and keep **pip **as a last option.

We also recommend passing the '--freeze-installed' flag when installing with conda, to ensure the minimal possible changes to the conda environment.

If you cannot self-service your packages, contact us at [**support@nuvolos.cloud**](mailto:support@nuvolos.cloud) and we will help you.
{% endhint %}

As an example, suppose you want to install [imagemagick](https://anaconda.org/conda-forge/imagemagick) and [gifsicle](https://anaconda.org/conda-forge/gifsicle) for mass editing gifs. The following command will install this to the conda environment of your application:

```
conda install --freeze-installed gifsicle imagemagick
```

{% hint style="success" %}
When distributing and snapshotting an application, the contents of the conda environment are also impacted. This is a key feature for reproducibility.
{% endhint %}

## Tips and tricks

### Single-purpose applications

{% hint style="info" %}
We strongly suggest creating single-purpose applications.&#x20;
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

## Known issues

There are no current known issues. Please do not hesitate to reach out to us if you see anything out of the ordinary.



