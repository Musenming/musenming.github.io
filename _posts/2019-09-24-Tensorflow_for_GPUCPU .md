---
layout:     post
title: Tensorflow for GPU/CPU 
subtitle: Deep Learning
date:       2019-09-24
author:     Musen
header-img: img/tag-bg.jpg
catalog: true
tags:
    - Deep Learning
---
<script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: { inlineMath: [ ['$','$'], ['\\(','\\)'] ], processEscapes: true } }); </script> <script type="text/javascript" async src="//cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML"> </script>

## Train the model of time series prediction code of tensorflow framework.
### 1. Install Tensorflow Framework

- For CPU:
  > pip install tensorflow
- For GPU:
  > pip install tensorflow-gpu  # stable

**Notice: My GPU can't use version 1.13 or others that is higher, so I install version 1.12, you should check your GPU's version .**

### 2. Use tensorflow for CPU

- If you install tensorflow for CPU, you can run it directly.
- But you install tensorflow for GPU, you should add these codes in your package.
```python
import os
os.environ["CUDA_VISIBLE_DEVICES"]="-1"    
import tensorflow as tf
```

### 3. Use tensorflow for GPU

- System will automatically assign which GPU device to run your code.
- If you want to assign one or more GPU devices to excute your code, you can add this order in front of your order.
  
  one:
  > with tf.device('/gpu:1'):

  more:
  > for d in ['/gpu:2', '/gpu:3']:

  > with tf.device(d):
