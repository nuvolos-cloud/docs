---
description: Application specific recommendations for GPU computations
---

# GPU computation

## Introduction

The NVIDIA device drivers will be loaded in all GPU supported images once a GPU node is started on Nuvolos. However depending on the image type additional components \(e.g. CUDA toolkit\) might need to be installed via conda.

If you launch a GPU accelerated node on Nuvolos, the `nvidia-smi` [tool ](https://developer.nvidia.com/nvidia-system-management-interface)will be available from the command line / terminal. You can use this to check the load on the given GPU to verify how effectively the code is leveraging the accelerator.

Please find below some examples on how to get started with GPU computations on Nuvolos or consult directly the relevant machine learning library documentation. If you require additional support, please reach out to our team directly.

## Python

We recommend to install the appropriate cudatoolkit from conda that is compatible with the target library and then use a conda packaged version of the library that can leverage the cudatoolkit.

### PyTorch

For example, to run pytorch with on Nuvolos, simply run:

```text
conda install pytorch torchvision torchaudio cudatoolkit=10.2 -c pytorch
```

### Tensorflow

To run tensorflow with GPU acceleration, install via conda:

```text
conda install -c anaconda tensorflow-gpu==2.4.1
pip install gast==0.3.3
```

## Rstudio

With Machine Learning \(CUDA enabled\) Rstudio images you can run GPU computations on GPU accelerated nodes. These images have the CUDA runtime / toolkit installed as well.

### XGBoost

We recommend to use the pre-built experimental binary to get started with XGBoost and R. In a terminal on a GPU node:

```text
# define version used - update if needed
XGBOOST_VERSION=1.4.1
# download binary
wget https://github.com/dmlc/xgboost/releases/download/v${XGBOOST_VERSION}/xgboost_r_gpu_linux_${XGBOOST_VERSION}.tar.gz
# Install dependencies
R -q -e "install.packages(c('data.table', 'jsonlite'))"
# Install XGBoost
R CMD INSTALL ./xgboost_r_gpu_linux_${XGBOOST_VERSION}.tar.gz
```

You can test the code via the following example program: [https://rdrr.io/cran/xgboost/src/demo/gpu\_accelerated.R](https://rdrr.io/cran/xgboost/src/demo/gpu_accelerated.R)

