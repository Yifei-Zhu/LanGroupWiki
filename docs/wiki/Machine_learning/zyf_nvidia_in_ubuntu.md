---
layout: page
title: How to use NVIDIA GPUs on Linux
author: Yifei Zhu
comments: true
tags:
 - Linux
 - NVIDIA
---
Follow this wiki step by step to set up NVIDIA GPU on Linux (using Ubuntu 22.04 as an example)

## 1 Install a Suitable NVIDIA Driver
### Method 1: Manually download and install
This driver can be manually downloaded and installed from the [NVIDIA official website](https://www.nvidia.cn/geforce/drivers/).

### Method 2: Command line
##### Update your package list

```Bash
sudo apt update
```
##### List available drivers:

```Bash
ubuntu-drivers devices
```

##### Install the recommended or the specific version NVIDIA driver

```Bash
sudo ubuntu-drivers autoinstall
```
or

```Bash
sudo apt install nvidia-driver-532
```
##### Reboot your computer

```Bash
sudo reboot
```

## 2 Install CUDA Toolkit

Visit the [CUDA Toolkits Downloads pages](https://developer.nvidia.com/cuda-downloads) on the NVIDIA official website.
Then choose the options according to your situation.
NVIDIA provide three ways to install the CUDA Toolkit with specific version.
Here is the `runfile(local)` I recommend because I am sure you are as lazy as me.

!!! info "Installation of other development tools"
      While you run the command `sudo sh cuda_xxxxxx_linux.run`, you need several development tools, such as `gcc`, `g++`, `make`, etc.
      If you haven't installed them yet, you can use `sudo apt install build-essential` to install almost of them.


After the installation is complete, to ensure that `nvcc` and other CUDA commands can be called from anywhere, you need to add the CUDA Toolkit's binary directory to your PATH environment variable, as well as configure the LD_LIBRARY_PATH for the library files.
You can add the following lines to your `.bashrc` or `.profile` file:

```Bash
export PATH=/usr/local/cuda-12.4/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-12.4/lib64:$LD_LIBRARY_PATH
```
Then you should apply the environment variables

Finally, use the following command to test the environment configuration:

```Bash
nvcc -V
```

