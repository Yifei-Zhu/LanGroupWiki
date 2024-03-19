---
layout: page
title: An example of a successful Uni-Mol installation
author: Yifei Zhu
comments: true
tags:
 - Linux
 - Python
 - PyTorch
 - RDKit
---
## Uni-Mol

## Overview of installation
Rather than a tutorial, we provide here a case study of installing Uni-Mol on Ubuntu 22.04.
There are many methods and configurations for installation, we will only provide one possible solution here.
Before the installation of Uni-Mol, [the NVIDIA GPUs should be correctly set up](./nvidia_in_ubuntu.md).

Here, some important configurations of my computer and working environment before installation are listed below:
- System: Ubuntu 22.04
- GPU*1: NVIDIA GeForce GTX 1070
- Driver Version 536.23
- CUDA 12.4
- Anaconda Distribution

Finally, the environment configurations:
- Rdkit==2022.9.3
- Python==3.8
- PyTorch==2.2.1

## Installation of Uni-Mol

### 1 Create a Conda virtual environment
Conda virtual environments can avoid environment conflicts to a certain extent.
```Bash
conda create -n YOUR_ENV_NAME python=3.8
```
Here, `YOUR_ENV_NAME` is set to `unimol`.

Then, activate the `unimol` environment.
```Bash
conda activate unimol
```

### 2 [Install PyTorch]((./pytorch_in_ubuntu.md).)
It is note that the current Uni-Core requires torch>=2.0.0 by default.

### 3 Install Uni-Core
#### Clone Uni-Core repository
```Bash
git clone https://github.com/dptech-corp/Uni-Core
```

#### Install dependencies
```Bash
pip install -r requirements.txt
```

#### Install Uni-Core
```Bash
pip install .
```

### 4 Install Uni-Mol
#### Clone Uni-Mol repository
```Bash
git clone https://github.com/dptech-corp/Uni-Mol.git
```
#### Download pretrained weights
```Bash
cd Uni-Mol/unimol_tools/unimol_tools

wget https://github.com/dptech-corp/Uni-Mol/releases/download/v0.1/mol_pre_all_h_220816.pt
wget https://github.com/dptech-corp/Uni-Mol/releases/download/v0.1/mol_pre_no_h_220816.pt
wget https://github.com/dptech-corp/Uni-Mol/releases/download/v0.1/pocket_pre_220816.pt
wget https://github.com/dptech-corp/Uni-Mol/releases/download/v0.1/mof_pre_no_h_CORE_MAP_20230505.pt
wget https://github.com/dptech-corp/Uni-Mol/releases/download/v0.1/mp_all_h_230313.pt
wget https://github.com/dptech-corp/Uni-Mol/releases/download/v0.1/oled_pre_no_h_230101.pt

mkdir -p weights
mv *.pt weights/

cd ..
```

#### Install Uni-Mol
```Bash
pip install -r requirements.txt
pip install scikit-learn
python setup.py install
```
Here, the package `scikit-learn` is probably forgotten in somewhere by the Uni-Mol developers.
After installing Uni-Mol for the first time and trying to run it I was prompted with this missing package.
Here, the version of `scikit-learn` installed is 1.3.2.

