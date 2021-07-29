---
description: Tips for using JupyterLab on Nuvolos
---

# JupyterLab

## Adding a new launcher

In some cases it might be useful to have multiple conda environments inside a single JupyterLab application.

In this case we recommend to create a new conda environment and install a launcher **into the environment** as following:

```text
conda create env --name my_new_env
conda activate my_new_env
conda install ipykernel
ipython kernel install --prefix=/opt/conda --name "My New Env"
```



