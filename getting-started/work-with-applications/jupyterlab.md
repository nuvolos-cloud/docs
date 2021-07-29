---
description: Tips for using JupyterLab on Nuvolos
---

# JupyterLab

## Adding a new launcher

In some cases it might be useful to have multiple conda environments inside a single JupyterLab application and be able to launch notebooks from the JupyterLab launcher with kernels that run in these environments.

{% hint style="info" %}
We recommend that the kernel specification associated with the new conda environments created is always installed into the base conda environment \(and not user / system prefix\) to make sure that the kernel/launcher will function well after distributing an application. 

Our examples below follow this convention. If you don't want to share the application, then you can also follow instructions from other sources where typically the kernel specification is installed into the user home directory.
{% endhint %}

The following can be done from a JupyterLab terminal and shortly afterwards a new Launcher should appear.

### Python

In this case we recommend to create a new conda environment and install a launcher **into the environment** as following:

```bash
conda create env --name my_new_env
conda activate my_new_env
conda install ipykernel
ipython kernel install --prefix=/opt/conda --name "My New Env"
```

### R

In this case we recommend to create a new conda environment and install a launcher **into the environment** as following:

```bash
conda create env --name my_new_env
conda activate my_new_env
conda install r-recommended r-irkernel
R -e 'IRkernel::installspec(prefix="/opt/conda")'
```

\*\*\*\*

### 

