---
layout:     post
title: Centos系统安装Nvidia显卡驱动
subtitle: 显卡驱动安装问题
date:       2019-08-21
author:     Musen
header-img: img/post-bg-nvidia.jpg
catalog: true
tags:
    - Data_Science
---
因为要调用[Blazing SQL](https://docs.blazingdb.com/docs)，前几天给服务器重装显卡驱动，然后它就崩了(问题如下)，导致整个实验组没法用GPU跑代码，耽搁了很多时间，这里深感抱歉，这里记录下上次遇到的问题。

![GPU_Problem.jpg](https://raw.githubusercontent.com/Musenming/musenming.github.io/master/img/GPU_Problem.jpg)

显卡驱动具体安装以及更新的步骤可参考[这篇文章](https://note.youdao.com/ynoteshare1/index.html?id=0a9e41e397f999fc35c4678140bc1d50&type=note)。
试了几次，也重启了服务器都没用，后来终于找到了答案。

我之前安装的驱动都是直接使用以前下载的安装包，Nvidia的驱动包一直在更新，即使版本相同，我用的安装包已经更新，kernel不支持。

所以还是老老实实下载吧：
>wget https://www.nvidia.cn/content/DriverDownload-March2009/confirmation.php?url=/tesla/418.87/NVIDIA-Linux-x86_64-418.87.00.run&lang=cn&type=Tesla


