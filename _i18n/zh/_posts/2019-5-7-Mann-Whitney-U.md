---
title: 
  zh: "曼-惠特尼U检验 - 概述"
excerpt_separator: "<!--more-->"
categories:
  - Stat
tags:
  - Theory
author_profile: true
mathjax: true
comments: true
toc: true
toc_sticky: true
language: zh
permalink: /mannwhitneyu/

  
---

在此系列, 本文将介绍曼-惠特尼U检验，并且实现为小样本显著性检验的Python代码。这是 [Scipy](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.mannwhitneyu.html){:target="_blank"} 的原版曼-惠特尼U检验的扩展代码。

当前（2019）的scipy版本仅支持大样本检验（n>20），所以新代码补充了小样本（n<20）检验的方法。

[第一部分](https://hatchin.netlify.com/zh/mannwhitneyu/): 曼-惠特尼U检验的概述

[第二部分](https://hatchin.netlify.com/zh/mannwhitneyutool/?utm_source=blog&utm_medium=post&utm_campaign=part1){:target="_blank"} : 曼-惠特尼U检验的Python实现

曼-惠特尼U检验
----------------------------

曼-惠特尼U检验是独立样本t-检验的一种非参数检验替代。它同时检验了排列的顺序和分布的形状。给定两个独立数组，它将检验是否其中一组数据倾向于大于另一组数据 （样本均值的检验）。理论上，在大样本检验中，曼-惠特尼检验也可以用于检验两组数据是否来自不同分布，即使它们的中位数非常相似。

该检验并不假设样本是正太分布，或方差相等， 或两组样本数量相同。

因此:
  - 当样本不来自正太分布时，曼-惠特尼U检验通常作为t-检验的替代被采用;
  - 通常，当样本数小（n<20）时采用曼-惠特尼U检验;
  - 曼-惠特尼U检验可检测不同的分布的形状与分散程度，以及中位数的区别。


检验统计量与计算实例
----------------------
设想我们将要实验调查一种新药的有效性。一共有n=10名被试被随机分配服用新药或安慰剂。被试将记录下他们的不适程度（数值越高，越不舒服）。

数据如下：

| 安慰剂     | 7 | 5 | 6 | 4 | 12 |
| :---        | :---:  |  :---:  | :---:  | :---:  |  ---: |
| 新药    | 3 | 6 | 4 | 2 | 1  |

假设如下所示，并且这是一个 5%的显著性水平检验 (i.e., $$\alpha=0.05$$): 

$$
H_{0}: 这两个分布相同 
\\
H_{1}: 这两个分布不相同
$$

因为样本数很小 ($$n_{1}=n_{2}=5$$)， 所以非参数检验将被采用。我们将用曼-惠特尼U检验解决这个问题。

曼-惠特尼U检验的检验统计量被记作 $$U$$ ，它在原假设下的分布是已知的. 对于小样本， $$U$$ 的分布被列成了表。当样本量大于 ~20时， $$U$$ 的分布近似于正太分布。 

### 小样本例子
统计量， $$U$$，计算起来非常简单，特别是对于小样本检验。 

1. 计算轶 

   第一步是为数据分级。我们将全部数据（将两组被试数据放到一起（n=10））按大小顺序排列，并为它们分配等级（从1到10），结果如下表：
   
   | 数值 （已排序）  ||            轶（等级）   ||
   安慰剂    |   新药   | 安慰剂| 新药 |
   |:---------| :-----------: | :-----: |---------: |
   |          |  1            |         |1          |
   |          |  2            |         | 2         |
   |          |  3            |         | 3         |
   |          |  2            |         | 2         |
   4          |  4            |  4.5    | 4.5       |
   5          |               | 6       |           |
   6          |  6            | 7.5     | 7.5       |
   7          |               | 9       |           |
   12         |               | 10      |           |
   
   对于相等的数据，我们使用它们的轶的平均值。
   
2. 计算各组轶的总和
   
   第二步是计算各组轶的和，$$R$$。
   
   对于安慰剂组，
   
   $$
   R_{1} = 4.5 + 6 + 7.5 + 9 + 10 = 37
   $$
   
   对于新药组，
   
   $$
   R_{2} = 1 + 2 + 3 + 2 + 4.5 + 7.5 = 18
   $$
   
3. 计算 $$U$$
   
   给定如下公式，
   
   $$
   U_{i} = n_{1}n_{2} + \frac{n_{i}(n_{i}+1)}{2} - R_{i}
   \\
   U =  min( U_{1}, ..., U_{i})
   $$
   
   那么在本例中，
   
   $$
   U_{1} = 5(5) + \frac{5(6)}{2} - 37 = 3
   \\
   U_{1} = 5(5) + \frac{5(6)}{2} - 18 = 22
   $$
  
   因此统计量  $$U=3$$。
   
4. 比较 $$U$$ 与 $$U$$的临界值
   
   在每一次检验中，我们都将判断基于观测到的 $$U$$ 值，原假设是否成立。对于曼-惠特尼U检验，判断的方式与其他参数检验相同。我们将首先定义 $$U$$的临界值， 满足：
   
   {: style="text-align:center"}
   若 $$U \leq \ U的临界值$$，我们拒绝原假设 $$H_{0}$$，而
   
   {: style="text-align:center"}
   若 $$U > \ U的临界值$$ ，我们不拒绝原假设 $$H_{0}$$。
   
    $$U$$ 的临界值表如下：
   
   <iframe src="https://drive.google.com/file/d/1tDhqpREuVXevtImG0N_oviIFcb3khlah/preview" width="600" height="450"></iframe>
   从表中可得， $$U的临界值 = 2$$ 因此，
   
   $$
   U = 3 > 2 = \ U的临界值
   $$
   
   我们不拒绝原假设 $$H_{0}$$ 并且在显著程度$$\alpha =0.05$$时，没有显著性的证据表明这两个分布不相等。 
   
### 在大样本的情况下 (n > 20)

当样本数量大时，$$U$$ 值近似于一个正太分布，所以可以用Z-检验检测原假设。

1. 计算 $$U$$
   
   在此，
   
   $$
   U =  max( U_{1}, ..., U_{i})
   $$

2. 计算 $$U$$ 统计量的Z值

   $$
   \sigma _{U}={\sqrt {n_{1}n_{2}(n_{1}+n_{2}+1) \over 12}}
   \\
   \\
   Z = \frac{ U - \frac{n_{1}n{2}}{2}}{\sigma _{U}}
   $$
   
3. 判断

   比较观测到的Z值与Z的临界值以判断应保留或拒绝原假设。
   相似地，在5%的显著程度上，
   
   {: style="text-align:center"}
   若 $$Z \leq \ Z的临界值 = 1.96$$，我们不拒绝$$H_{0}$$ 而，
   
   {: style="text-align:center"}
   若 $$Z > \ Z的临界值 = 1.96$$，拒绝 $$H_{0}$$ 。
   
   
曼-惠特尼U检验的Python实现
----------------------

今天，多数统计包都可以使用曼-惠特尼U检验。比如在Python中， [scipy.stat](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.mannwhitneyu.html){:target="_blank"} 含有曼-惠特尼U检验。

然而，曼-惠特尼U检验的scipy版本提及：
```
Use only when the number of observation in each sample is > 20.
（仅当观测样本量>20时可用）
```

因为曼-惠特尼U检验对于小样本检验而言非常有用，比如医疗数据（许多临床试验只有非常少的样本量），所以在这里使用Python实现了一个完整的曼-惠特尼U检验，可用于小样本与大样本两种情况。

在 [第二部分](hatchin.netlify.com/zh/mannwhitneyutool/?utm_source=blog&utm_medium=post&utm_campaign=part1)，将详细展示这个新应用。

---------------------------------

更多细节：

[曼-惠特尼U检验：网页应用](https://mannwhitney.herokuapp.com/?utm_source=blog&utm_medium=post&utm_campaign=Webpage){:target="_blank"}

[源代码](https://github.com/Hatchin/Mann-Whitney-U-Test/blob/master/mannwhitney.py){:target="_blank"}

[Github](https://github.com/Hatchin/Mann-Whitney-U-Test){:target="_blank"}

