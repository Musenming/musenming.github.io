---
layout:     post
title: 数据画图graphviz包安装
subtitle: 环境配置
date:       2019-09-19
author:     Musen
header-img: img/post-bg-os-metro.jpg
catalog: true
tags:
    - Python
---
<script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: { inlineMath: [ ['$','$'], ['\\(','\\)'] ], processEscapes: true } }); </script> <script type="text/javascript" async src="//cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML"> </script>
# **graphviz install**
昨晚跑一个需要画图的代码，import数据画图graphviz包。最开始直接`pip install graphviz`，一直报`No module named 'graphviz'`

百思不得其解，后来突然反应过来，我的jupyter是在anaconda下安装的，我又用`conda install graphviz`安装。欧克，同样的报错。

然后我又添加环境变量，将`E:\anaconda3\pkgs\graphviz-2.38-hfd603c8_2\Library\bin\graphviz`添加到了path。绝望，还是报错。

打不死的小强到处找博客找解决方案，终于在今天中午找到了，敲下`conda install python-graphviz`

后来知道是为了给python添加graphviz模块，否则python无法调用。

欧克，终于跑通了！