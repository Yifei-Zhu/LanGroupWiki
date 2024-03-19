---
layout: page
title: How to use PyTorch on Linux
author: Yifei Zhu
comments: true
tags:
 - Linux
 - Python
 - PyTorch
---
Follow this wiki step by step to set up PyTorch on Linux (using Ubuntu 22.04 as an example)
If you want to configure the GPU-version PyTorch, you should correctly [set up the NVIDIA GPUs on your Linux](./nvidia_in_ubuntu.md).

## 1 Install Anaconda or Miniconda
Miniconda is a free minimal installer for conda.
It is a small bootstrap version of Anaconda that includes only conda, Python, the packages they both depend on, and a small number of other useful packages (like pip, zlib, and a few others).

If you are configuring a conda environment on your own laptop, we recommend using miniconda.
However, here we take Anaconda as an example.

#### Download Anaconda

You can manually download the `Anaconda_xxxx.sh` from the official website or other mirrors, for example, [Tsinghua sonrce](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/).
You can also use `wget` command to download the `.sh` file.

#### Install Anaconda
Then run `bash Anaconda_xxxx.sh` to install Anaconda on your system.
Finally, restart the terminal.

!!! info "`base` environment is not activated"
      If the `base` environment is not automatically activated when you finish the installation, you should run the command `conda init bash` and `conda activate base` following the prompts.

## 2 Install PyTorch
Visit the [PyTorch official website](https://pytorch.org/) and select options according to your situations.
Just run the command in the local terminal.

!!! info "A dedicated environment for PyTorch"
      If you are concerned about potential conflicts between different project environments, it's advisable to create a dedicated environment specifically for PyTorch.
      You can do this by executing `conda create -n YOUR_ENV_NAME python=3.xx`, where `YOUR_ENV_NAME` is the name you choose for your PyTorch environment, and `3.xx` is the Python version you intend to use.

      Then you can use `conda activate YOUR_ENV_NAME` to activate this environment, in which you can run the command obtained from the PyTorch official website to install PyTorch.

## 3 Checking the installation
```Python
import torch
print(torch.cuda.is_available())
```
Running this code will print `True` if PyTorch can access a GPU (meaning CUDA is available and configured correctly for PyTorch).