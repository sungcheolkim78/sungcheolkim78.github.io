---
title: 'Install cuda and cuDNN on home machine'
date: 2022-07-14
tags:
  - ml
  - cuda
  - linux
---

To learn the deep learning algorithms, I changed my home computer into dual boot machine with windows 10 and pop! os 22.04

# Install cuda tools

Make an account in nvidia home page and you can download cuda tools. As of today (22/07/14), I can download cuda 11.7 version. 
If you choose options like `linux`, `x86_64`, `Ubuntu`, `22.04`, `deb(network)`, then you will get the following commands 
instructions. 

```{shell}
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-ubuntu2204.pin
sudo mv cuda-ubuntu2204.pin /etc/apt/preferences.d/cuda-repository-pin-600
sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/3bf863cc.pub
sudo add-apt-repository "deb https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/ /"
sudo apt-get update
sudo apt-get -y install cuda
```

Then you can install cuda tools. 

# Install cuDNN 

For deeplearning pipeline, you also need to install cuDNN and you can find the link [here](https://developer.nvidia.com/rdp/cudnn-download)
Please log in to nvidia website first. As of today (22/07/14), you can download two versions - `cuDNN v8.4.1 for CUDA 11.x`
and `cuDNN v8.4.1 for CUDA 10.2`

you can find the details of the instructions [here](https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html)

```{shell}
sudo dpkg -i cudnn-local-repo-${OS}-8.x.x.x_1.0-1_amd64.deb
sudo cp /var/cudnn-local-repo-*/cudnn-local-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get install libcudnn8=8.x.x.x-1+cudaX.Y
sudo apt-get install libcudnn8-dev=8.x.x.x-1+cudaX.Y
sudo apt-get install libcudnn8-samples=8.x.x.x-1+cudaX.Y
```

You can also reference the following [site](https://medium.com/geekculture/installing-cudnn-and-cuda-toolkit-on-ubuntu-20-04-for-machine-learning-tasks-f41985fcf9b2)

# Compile tensorflow

Once you install `cuda` and `cudnn`, you can start to compile `tensorflow`. Before you start, please follow instructions in [here](https://www.tensorflow.org/install/source)
The key component is to install `go` and `bazelisk`. 

# Compile Jax

You can also compile jax using this [site](https://jax.readthedocs.io/en/latest/developer.html). Please make sure to install jaxlib and jax. 

