---
layout:     post
title: Problem of upgrading pip
subtitle: 环境配置
date:       2019-09-24
author:     Musen
header-img: img/post-bg-hacker.jpg
catalog: true
tags:
    - 环境配置
---
<script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: { inlineMath: [ ['$','$'], ['\\(','\\)'] ], processEscapes: true } }); </script> <script type="text/javascript" async src="//cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML"> </script>

### 1. 今天在装tensorflow的GPU版时pip突然崩了，于是开始更新，然后出现了一系列问题，记录如下

- **本地的pip与anaconda发生了冲突**
  
  这里需要禁用一个pip，可以修改环境变量，或者直接删除，我比较暴力，直接删除了anaconda，所以一会儿还得乖乖地装jupyter
- **pip更新出现问题，更新失败后，pip不存在**
  
  pip地upgrade需要管理员权限，这里可以直接右键powershell/cmd的exe，以管理员身份运行，或者加上`--user`

  *有一个问题需要注意一下，一旦pip更新失败，以前的pip也就没了，所以无法再次使用pip命令进行更新*

  这时候先:
  
  > python -m ensurepip
  
  然后以管理员权限进行更新
### 2. 附加
- Install tensorflow for GPU:
  
  > pip install tensorflow-gpu

### 3. 使用tensorflow框架的时间序列预测代码，如何在GPU上跑可以参考[这篇文章](https://tensorflow.google.cn/beta/guide/using_gpu)

