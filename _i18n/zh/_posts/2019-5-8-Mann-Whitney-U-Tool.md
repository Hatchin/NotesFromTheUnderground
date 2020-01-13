---
title: 
  zh: "曼-惠特尼U检验 - 小样本检验Python版本"
excerpt_separator: "<!--more-->"
categories:
  - Stat
tags:
  - Tool
  - Web
author_profile: true
mathjax: true
comments: true
toc: true
toc_sticky: true
language: zh
permalink: /mannwhitneyutool/

---
此文将介绍如何用Python代码运行完整版的曼-惠特尼U检验，包括大样本检验（n>20）和小样本（n<20）检验。

对于小样本检验，比如医疗数据集（许多临床试验只有非常少的样例数据，曼-惠特尼U检验非常常用。然而在许多统计程序包里，只包含了曼-惠特尼U检验的大样本检验部分。因此，如果能获得一个完整版的曼-惠特尼U检验——即能做大样本检验又能做小样本检验——将很有用处。

[第一部分](https://hatchin.netlify.com/zh/mannwhitneyu/?utm_source=blog&utm_medium=post&utm_campaign=part2){:target="_blank"}: 曼-惠特尼U检验的概述

[第二部分](https://hatchin.netlify.com/mannwhitneyutool/): 曼-惠特尼U检验的Python实现

------------------------

[实例: 网页应用](https://mannwhitney.herokuapp.com/?utm_source=blog&utm_medium=post&utm_campaign=Webpage){:target="_blank"}

[源码](https://github.com/Hatchin/Mann-Whitney-U-Test/blob/master/mannwhitney.py){:target="_blank"}

[Github](https://github.com/Hatchin/Mann-Whitney-U-Test){:target="_blank"}

演示
----------------------------

### 安装

将[曼-惠特尼U检验](https://github.com/Hatchin/Mann-Whitney-U-Test) 下载到本地，然后运行：

```
pip install -r requirements.txt
```

### 使用

为使用曼-惠特尼U检验，需要将数据以list的形式输入：

```
from mannwhitney import *
data1 = [1,2,3,4,4,5]
data2 = [4,5,6,6,9,10,14]
```

然后可以简单地如下进行检验：
```
mwm = mannWhitney(data1,
                  data2, 
                  tail='two', 
                  significant_level=0.05) # two-tailed test
                                          # at 0.05 significance
```

### 分析

计算完毕后，将能调取以下数据：

`mwm.n1` & `mwm.n2`  int, 比如 10

​								数据样本量大小

`mwm.sample_size`   str, 比如 "small"

​								数据是大样本还是小样本

`mwm.significance`  bool, e.g. True

​								两组比较样本是否有显著性差异

`mwm.criticalu`       float, e.g. 3.0

​							    从表中取得的$$U$$的临界值（仅当小样本的情况下才能计算）

`mwm.p`              	   float, e.g. 0.05

​								从数据中计算得出的p 值（仅当大样本的情况下才能计算）

`mwm.stat_a`         	float, e.g. 3.0

​								从数据中计算出的$$U$$ 统计量

`mwm.effectsize`     float, e.g. 0.8

​								效应值

`mwm.largergroup`    int, e.g. 1

​								两组中较大样本的索引（1 或 2）

网页应用
--------------

如果不想运行代码，你也可以访问这个基于该代码的[应用网站](https://mannwhitney.herokuapp.com/?utm_source=blog&utm_medium=post&utm_campaign=Webpage){:target="_blank"} 。

<p align="center">
  <img src="https://raw.githubusercontent.com/Hatchin/Mann-Whitney-U-Test/master/demo.png" alt="">页面截图
</p>

类似地，输入两组数据后这个应用会自动进行运算并且返回结果。

正确的数据输入格式包括
  - 直接从Excel里选中复制（一行或一列）
  - 手动输入
    - 以英文逗号间隔，比如 `1, 2, 3, 4`
    - 以空格间隔， 比如 `1 2 3 4`
    - 同时以逗号和空格间隔，比如 `1  2  , 3, 4`
    
### 在本地运行服务器

配置应用程序并在本地计算机运行也很简单。在安装好前文提及的`requirement.txt` 后再运行：

```
python app.py runserver
```

就可以从 [http://127.0.0.1:5000/](http://127.0.0.1:5000/) 访问了。
