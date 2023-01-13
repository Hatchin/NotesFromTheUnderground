---
title: 
  en: "Conditional Gan Summary"
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
language: en
permalink: /mannwhitneyutool/

  
---


Worked on conditional GAN (cGAN) and image inpainting projects for a while. Here is a brief summary of the experience, thinking and lessons. 

Inspired a lot by [this blog](https://spaces.ac.cn/)!

Generative modeling is an unsupervised learning task in machine learning that involves automatically discovering and learning the patterns in input data in such a way that the model can be used to generate or output new examples that plausibly could have been drawn from the original dataset.

I also see the Discriminator as a special loss function learnt by neural network to measure the difference between two distributions.

------------------------

## DCGAN

DCGAN is the first GAN using CNN. Some good intro [link](https://zhuanlan.zhihu.com/p/158568480) and [link](https://zhuanlan.zhihu.com/p/83630387) 

----------------------------
## WGAN

WGAN is based on the fact that JS divergence is not a good measurement of two distribution difference, especially for high dimension data. However the tweak is very easy:
- In the D, remove the sigmoid from the last layer
- take the loss instead of log(loss) for both G and D
- for parameters in D, do weight clipping
- instead of momentum or Adam, RMSProp and SGD are recommended. 

Good intro [link](https://zhuanlan.zhihu.com/p/25071913), [link](https://zhuanlan.zhihu.com/p/58260684)

## SNGAN

Weigth clipping is sometimes too brutal to satisfy the 1-Lipschitz restriction. Gradient clipping was an alternative way. Similar to WGAN, spectral norm is later introduced as a way to satisfy the 1-Lipschitz restriction. 

## Modulation GAN
This is related to AdaIn

Good intro [link](https://zhuanlan.zhihu.com/p/57875010)
