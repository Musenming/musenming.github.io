---
layout:     post
title: 西瓜书决策树练习
subtitle: machine learning
date:       2019-09-19
author:     Musen
header-img: img/post-bg-ioses.jpg
catalog: true
tags:
    - machine learning
---
<script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: { inlineMath: [ ['$','$'], ['\\(','\\)'] ], processEscapes: true } }); </script> <script type="text/javascript" async src="//cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML"> </script>

### 采用决策树方法 学习 练习1.1 中（两个样例）的决策树，并与练习1.1的版本空间进行比较。

样例为：

|青绿 |蜷缩 |浊响|好|
|:---:|:---:|:---:|:---:|
|乌黑 |稍蜷 |沉闷|否|

数据集含有两个训练样例，$\begin{vmatrix}\nu\end{vmatrix}$ =2

①开始学习时，根节点包含所有样例，正例占比为：$P_1=\frac{1}{2}$ ，反例比例为：$P_2=\frac{1}{2}$

当前结点的信息熵为：

$$Ent(D)=-\sum_{k=1}^{2}P_klog_{2}P_k$$

②当前属性合集为：{色泽，根蒂，敲声}，先选择色泽对D进行划分，$D_1$（色泽=青绿），$D_2$（色泽=乌黑）,$D_1$的正例占比$P_1=1$，$D_1$反例占比$P_2=0$；$D_2$的正例占比$P_1=0$，反例占比$P_2=1$，计算信息熵得到：

$$Ent(D_1)=-(\frac{1}{2}log_20)=0$$

$$Ent(D_2)=-(0log_2\frac{1}{2})=0$$
  
算到这里，我发现两个样例，算不了信息增益和信息熵。。。。
后来发现，熵为0以后就不能再往下分了，所以只有两层

![决策树.jpg](https://raw.githubusercontent.com/Musenming/musenming.github.io/master/img/%E5%86%B3%E7%AD%96%E6%A0%91.jpg) 

**版本空间为：**

![版本空间.jpg](https://raw.githubusercontent.com/Musenming/musenming.github.io/master/img/%E7%89%88%E6%9C%AC%E7%A9%BA%E9%97%B4.jpg)
 
**版本空间比决策树更加复杂，版本空间包括了很多冗余情况**

**代码参考：**
```python
import pandas as pd
from sklearn import tree
import graphviz
import pydotplus
from IPython.display import Image

melon_data = pd.DataFrame(
    [
        ["青绿", "蜷缩", "浊响", True],
        # ["乌黑", "蜷缩", "浊响", True],
        # ["青绿", "硬挺", "清脆", False],
        ["乌黑", "稍蜷", "沉闷", False],
    ],
    columns=["色泽", "根蒂", "敲声", "target"],
)

dic = {
    "青绿": "Green",
    "乌黑": "black",
    "蜷缩": "Curled_up",
    "硬挺": "Starched",
    "稍蜷": "Slightly_curled_up",
    "浊响": "dull",
    "清脆": "liquidly",
    "沉闷": "rumble",
    "色泽": "color",
    "根蒂": "root",
    "敲声": "sound",
}

# one-hot coder
for f in melon_data.columns[0:3]:
    melon_data[f] = melon_data[f].map(dic)
    dummies = pd.get_dummies(melon_data[f], prefix=dic[f])
    melon_data = melon_data.join(dummies)
melon_data = melon_data.drop(["色泽", "根蒂", "敲声"], axis=1)

# train a clf
clf = tree.DecisionTreeClassifier()
clf_fit = clf.fit(melon_data.drop(["target"], axis=1), melon_data["target"])

# plot it！
dot_data = tree.export_graphviz(
    clf_fit,
    out_file=None,
    feature_names=melon_data.columns[1:],
    class_names=[u"Good", u"Bad"],
    filled=True,
    rounded=True,
    special_characters=True,
)
graph = pydotplus.graph_from_dot_data(dot_data)
Image(graph.create_png())
```





