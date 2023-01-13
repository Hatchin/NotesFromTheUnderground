---
title: 
  zh: "条件GAN总结"
excerpt_separator: "<!--more-->"
categories:
  - Neural_Network
  - Deep_Learning
  - Generative_Model
tags:
  - Theory
author_profile: true
mathjax: true
comments: true
toc: true
toc_sticky: true
language: zh
permalink: /cgansummary/

  
---


做了一段时间条件生成模型跟图像补全。记录一些思考总结。

苏剑林的[博客](https://spaces.ac.cn/)科普讲得很好!

生成模型就是一类非监督学习，从输入中学习类别模式从而产生新的数据。

其中GAN里的判别器也可以看做是一种用来衡量两个分布的近似程度的特殊损失函数。

------------------------

## DCGAN
DCGAN将CNN应用在了GAN的生成器跟判别器上。
一些不错的介绍[link](https://zhuanlan.zhihu.com/p/158568480) 和 [link](https://zhuanlan.zhihu.com/p/83630387)。

----------------------------
## WGAN
原本GAN的判别损失相当于计算分布之间的JS散度，而JS散度会带来梯度消失的问题，特别是对于高维数据类型。WGAN就是为了解决这个问题，并且修改非常简单
- 判别器最后一层去掉sigmoid
- 生成器和判别器的loss不取log
- 每次更新判别器的参数之后把它们的绝对值截断到不超过一个固定常数c
- 不要用基于动量的优化算法（包括momentum和Adam），推荐RMSProp，SGD也行

一些不错的介绍 [link](https://zhuanlan.zhihu.com/p/25071913) 和 [link](https://zhuanlan.zhihu.com/p/58260684)。

## SNGAN

为了满足1-Lipschitz限制，参数截断有一点太简单粗暴了。后来提出来梯度截断。后来使用spectral norm来满足这一限制。 

## Modulation GAN
这个源于AdaIn

一些不错的介绍[link](https://zhuanlan.zhihu.com/p/57875010)
