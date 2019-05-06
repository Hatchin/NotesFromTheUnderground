---
title: "Mann Whitney U Test Tool"
excerpt_separator: "<!--more-->"
categories:
  - Stat
tags:
  - Tool
  - Web App
author_profile: true
mathjax: true
comments: true
---

Use of Mann-Whitney test
----------------------------

The Mann–Whitney U test is a non-parametric alternative test to the independent sample t-test. It is a test of both location and shape. Given two independent samples, it tests whether one variable tends to have values higher than the other (test on sample means). Theoretically, in large samples the Mann-Whitney test can also detect differences in spread even when the medians are very similar. 

This test does not assume that the samples is normally distributed, that the variances of the two populations are equal or that the two sample sizes are equal.

Hence, in summary:
  - The Mann-Whitney U test is used as an alternative to a t test when the data are not normally distributed;
  - The Mann-Whitney U test is usually used in cases that data sample size is small;
  - The test can detect differences in shape and spread as well as just differences in medians.
  

Test Statistic and Calculation Example
----------------------
Consider a test designed to investigate the effectiveness of a new drug. A total of n=10 participants are randomized to receive either the new drug or a placebo. Participants are asked to record the significance of discomfort (the higher the value, the more uncomfortable). The data are shown below.

Pros | Cons 
--- | --- 
Very efficient |  Prone to outliers
O(no.iteration * no.clusters * no.instances * no.data \ dimensions) | Cannot have categorical variables (since we are computing means, must be numerical)
Make use of all the data |  


\begin{table}[]
\begin{tabular}{@{}lllll@{}}
\toprule
Placebo  & 7 & 5 & 6 & 4 & 12\\ \midrule
New Drug & 3 & 6 & 4 & 2 & 1\\ \bottomrule
\end{tabular}
\end{table}
