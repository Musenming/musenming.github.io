---
layout:     post
title: 西瓜书chapter2课后习题
subtitle: machine learning
date:       2019-09-17
author:     Musen
header-img: img/home-bg-art.jpg
catalog: true
tags:
    - machine learning
---
<script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: { inlineMath: [ ['$','$'], ['\\(','\\)'] ], processEscapes: true } }); </script> <script type="text/javascript" async src="//cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML"> </script>

# Chapter 2
## 2.1 数据集包含1000个样本，其中500个正例，500个反例，将其划分为包含70%样本的训练集和30%样本的测试集用于留出法评估，试估算共有多少种划分方式。
①由题意可知，本题所要考察的是留出法

②为了保证训练集和测试集划分的数据要保证一致性和随机性，那么在选取的正例/反例要保证相同的比例

③同时要保证随机性，所以样本应该随机选择；

④训练集各分类选取样本数：500*70%=350

⑤在训练集完成选择以后，剩下的样本归为测试集，故我们只需要计算训练集有多少种分法

⑥最后答案为：
 
$$(C_{500}^{350})^2=3.292004453709973e+266$$

代码如下：
```python
#训练集种类计算
p = int(input("正例："))
n = int(input("反例："))
t = int(input("训练集比例（%）："))
a = int(p*(t/100))
b = int(n*(t/100))
def p_test(m,n):
    r1=1
    for i in range(1,m):
        r1=r1*(i)
    r2=1
    for i in range(1,n):
        r2=r2*(i)
    r3=1
    for i in range(1,m-n):
        r3=r3*(i)
    return (r1/(r2*r3))
p1 = p_test(p,a)
n1 = p_test(n,b)
result = p1*n1
print (result)
```
## 2.2 数据集包含100个样本，其中正反例各一半，假定学习算法所产生的模型是将新样本预测为训练样本数较多的类别（训练样本数相同时进行随机猜测），试给出用10折交叉验证法和留一法分别对错误率进行评估所得的结果

错误率定义为：

$$ E(f;D)=\frac{1}{m}\ \sum_{i=1}^m(f(x_i)\ne{y_i})$$

**10折交叉验证法**：样本平均分为了10份，由题意可知，选择出来的测试集含有反例数应该为（0-10），我们用x表示，则在测试样本中，正例数为10-x

当$(0\lt{x}\le5)$时，训练集中，反例数大于正例数，这时训练结果为负，按照错误率定义，错误率为:$\frac{10-x}{10}$

当$(5\lt{x}\le10)$时，训练集中正例数小于反例数，这时训练结果为正，按照错误率定义，错误率为:$\frac{x}{10}$ 

综上：
$$ E(f;D)=
\begin{cases}
\frac{10-x}{10}, & \text{$(0\lt{x}\le5)$}  \\
\frac{x}{10}, & \text{$(5\lt{x}\le10)$}
\end{cases}
$$ 

要计算错误率的数值，还需要用到$E(f;D)=\int_{X-D}\prod ({f(x_i)\ne{y_i}})p(x)dx$,$p(x)$表示试验集中取到正例数为x的概率，$p(x)=\frac{C_{50}^{x}*C_{50}^{10-x}}{C_{100}^{x}}$

计算$p(x)$的代码如下：

```python
from scipy.special import comb, perm
for i in range (0,11):
    a=comb(50,i)
    b=comb(50,10-i)
    c=comb(100,10)
    re=(a*b)/c
    print("|",i,"|",re,"|")
```
$p(x)$数据如下：

| 0 | 0.0005934196725858287 |
|:---:|:---:|
| 1 | 0.007236825275436936 |
| 2 | 0.037993332696043915 |
| 3 | 0.11309643221147955 |
| 4 | 0.21141321703168622 |
| 5 | 0.2593335462255351 |
| 6 | 0.21141321703168622 |
| 7 | 0.11309643221147955 |
| 8 | 0.037993332696043915 |
| 9 | 0.007236825275436936 |
| 10 | 0.0005934196725858287 |

**最后：$E(f;D)$=0.617**

**留一法**：该法将数据分为100份，每次选一个出来，不管测试集选出的样本是正例还是反例，训练集测出的结果都与测试集相反，所以错误率是**100%**

## 2.4 试述真正例率（TPR）、假正例率（FPR）与查准率（P）、查全率（R）之间的联系。
四者的定义式为：

$$TPR=\frac{TP}{TP+FN}、FPR=\frac{FP}{TN+FP}、
P=\frac{TP}{TP+FP}、R=\frac{TP}{TP+FN}$$ 

通过定义式可知：

**①TPR与R值相同**
## 2.6 试述错误率与ROC曲线之间的关系

$$TPR=\frac{TP}{TP+FN}、FPR=\frac{FP}{TN+FP}$$

$$E(f;D)=\frac{FP+FN}{TN+FP+TP+FN}$$ 

ROC曲线上的每一个点都对应了一组（TPR，FPR）值，我一直在考虑两者之间是否存在代数关系，公式如上所示。

参考真假正例率的定义，由于样本中正例和反例的比例是确定的。因此以某个样本的score为阈值时（即对应ROC曲线中的一个点），该点的真正例率越高，假正例率越低，则错误率越低，因此越靠近（0，1）点错误率越低。






