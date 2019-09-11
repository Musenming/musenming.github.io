---
layout:     post
title: CUPY_INSTALL
subtitle: 环境配置
date:       2019-07-30
author:     Musen
header-img: img/post-bg-keybord.jpg
catalog: true
tags:
    - Data_Science
---
##要求：
您需要具有以下组件才能使用CuPy。

1.NVIDIA CUDA GPU
2.GPU的计算能力必须至少为3.0。
3.CUDA工具包
4.支持的版本：8.0,9.0,9.1,9.2,10.0和10.1。
5.如果您安装了多个版本的CUDA 6.Toolkit，CuPy将自动选择其中一个CUDA安装。有关详细信息，请参阅使用自定义CUDA安装。
7.Python：
支持的版本：2.7.6 +，3.4.3 +，3.5.1 +，3.6.0 +和3.7.0+。
NumPy的
支持的版本：1.9,1.10,1.11,1.12,1.13,1.14,1.15和1.16。
8.在安装CuPy期间将自动安装NumPy。
9.在安装CuPy之前，我们建议您升级setuptools并pip：

$ pip install -U setuptools pip
*注意：在Windows上，CuPy仅支持Python 3.6.0或更高版本。*

可选库：
只有安装了相应的库，才会启用CuPy中的某些功能。

cuDNN（加速深度神经网络计算的库）
支持的版本：v5，v5.1，v6，v7，v7.1，v7.2，v7.3，v7.4和v7.5。
NCCL （用于执行集体多GPU /多节点计算的库）
支持的版本：v1.3.4，v2，v2.1，v2.2，v2.3和v2.4。
##安装CuPy 
轮子（预编译的二进制包）可用于Linux（Python 2.7或更高版本）和Windows（Python 3.6或更高版本）。软件包名称因您在主机上安装的CUDA版本而异。

(For CUDA 8.0)
$ pip install cupy-cuda80

(For CUDA 9.0)
$ pip install cupy-cuda90

(For CUDA 9.1)
$ pip install cupy-cuda91

(For CUDA 9.2)
$ pip install cupy-cuda92

(For CUDA 10.0)
$ pip install cupy-cuda100

(For CUDA 10.1)
$ pip install cupy-cuda101
*注意：这些轮子中包含最新版本的cuDNN和NCCL库。您不必手动安装它们。*

使用轮子时，请注意不要同时安装多个CuPy包。这些包和cupy包中的任何一个（源安装）都相互冲突。请确保只安装了一个CuPy包（cupy或者cupy-cudaXXXX是CUDA版本）：

$ pip freeze | grep cupy
从源代码安装CuPy 
建议尽可能使用轮子。但是，如果轮子不能满足您的要求（例如，您正在运行非Linux环境或想要使用轮子不支持的CUDA / cuDNN / NCCL版本），您还可以从源代码构建CuPy。

从源代码安装时，需要C++编译器g++。您需要在安装CuPy之前安装它。这是每个平台的典型安装方法：

# Ubuntu 16.04
$ apt-get install g++

# CentOS 7
$ yum install gcc-c++
注意

从源代码安装CuPy时，如果在安装时这些库不可用，则将禁用可选库（cuDNN和NCCL）提供的功能。有关说明，请参阅安装cuDNN和NCCL。

注意

如果升级或降级CUDA Toolkit，cuDNN或NCCL的版本，则可能需要重新安装CuPy。有关详细信息，请参阅重新安装CuPy。

使用PIP 
您可以通过安装CuPy包pip。

$ pip install cupy
使用压缩包
源代码树的压缩包通过提供或发布说明页面。你可以从tarball安装CuPy：pip download cupy

$ pip install cupy-x.x.x.tar.gz
您还可以从克隆的Git存储库安装CuPy的开发版本：

$ git clone https://github.com/cupy/cupy.git
$ cd cupy
$ pip install .
如果您使用从GitHub下载的源代码树，则需要安装Cython 0.28.0或更高版本（）。pip install cython