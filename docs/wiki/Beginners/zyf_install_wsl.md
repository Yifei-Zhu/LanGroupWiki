---
layout: page
title: How to install WSL on Windows
author: Yifei Zhu
comments: true
tags:
 - Linux
 - Windows
---
*This article is written with reference to [the official documentation](https://learn.microsoft.com/zh-cn/windows/wsl).*

## What is WSL?
The Windows Subsystem for Linux (WSL) lets developers install a Linux distribution directly on Windows.


### WSL1
WSL1 (Windows Subsystem for Linux 1) does not support direct access to hardware, including NVIDIA graphics cards, because it uses a system call translation layer rather than providing a full Linux kernel.
   This means it can't directly interact with hardware to utilize features like GPU acceleration.
### WSL2
WSL2 uses a different architecture that includes running a real Linux kernel on Windows, allowing for full system call compatibility and direct hardware access through virtualization.
This enables WSL2 to support NVIDIA GPU acceleration by using CUDA, OpenCL, and other GPU-accelerated computations, which is beneficial for computational heavy tasks in science, engineering, and machine learning applications.

!!! info "WSL2(Recommended)"
      To use NVIDIA GPUs with WSL, you need to use WSL2.

## Install WSL command
You can now install everything you need to run WSL with a single command.
Open PowerShell or Windows Command Prompt in administrator mode by right-clicking and selecting "Run as administrator", enter the following command, then **restart your machine**.

```PowerShell
wsl --install
```
This command will enable the features necessary to run WSL and install the Ubuntu distribution of Linux.

!!! tldr "install options"
     - `--distribution`: Specify the Linux distribution to install. You can find available distributions by running `wsl --list --online`.
     - `--no-launch`: Install the Linux distribution but do not launch it automatically.
     - `--web-download`: Install from an online source rather than using the Microsoft Store.

### Other commands

#### List available Linux distributions
```PowerShell
wsl --list --online
```

#### List installed Linux distributions (Check which version of WSL you are running)
```PowerShell
wsl --list --verbose
wsl -l -v
```

#### Set WSL version to 1 or 2
```PowerShell
wsl --set-version <distribution name> <versionNumber>
```

#### Set default WSL version
```PowerShell
wsl --set-default-version <Version>
```

