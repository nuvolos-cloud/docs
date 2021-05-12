---
description: Tips and tricks with VS Code applications on Nuvolos
---

# VS Code

[VS Code](https://code.visualstudio.com) applications are available on Nuvolos as the suggested GUI integrated development environment for Python. All VS Code applications come with a `conda` environment already in place in which you can [install your required packages](install-a-software-package.md#the-conda-environment).

## Interactive Python development

The VS Code application is an excellent interactive development environment. You can find a detailed and complete guide for interactive development with IPython [here](https://code.visualstudio.com/docs/python/jupyter-support-py), the following documentation helps you get started quickly in the context of the Nuvolos apps.

### Creating an interactive IPython window in VS Code

VS Code comes equipped with a conda package manager. In order to be able to start interactive IPython windows, you will first need to install some packages into the VS Code app. To do so, take the following steps:

1. Open a VS Code command prompt either by finding **View &gt; Command Palette** in the menu, or by hitting the **Ctrl + Shift + P** key combination. 
2. In the VS Code command palette, type Jupyter: Create and the autocomplete should offer you the Create Interactive Window option. 
3. You might be prompted to install ipykernel, in this case proceed to do so \(this might take a minute or so to complete\).  **If you have ommited step 3, you can later:** 
4. Open a terminal in VS Code. You can do this by finding **Terminal &gt; New Terminal** in the menu or hitting the **Ctrl + Shift + \`** key combination. In the terminal type `conda install --freeze-installed ipykernel` and wait for the process to complete. After that, you should be able to perform steps 1 and 2 without any further issues.



