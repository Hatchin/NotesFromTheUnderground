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

| Placebo     | 7 | 5 | 6 | 4 | 12 |
| :---        | :---:  |  :---:  | :---:  | :---:  |  ---: |
| New Drug    | 3 | 6 | 4 | 2 | 1  |

The hypothesis is given below: 

$$
H_{0}: The \ two \ populations \ are \ equal \ versus
\\
H_{1}: The \ two \ populations \ are \ not \ equal.
$$

The sample size is small ($$n_{1}=n_{2}=5$$), so a nonparametric test is appropriate. We are going to use Mann Whitney U test to solve this problem. 

The test statistic for the Mann Whitney U Test is denoted $$U$$, whose whose distribution under the null hypothesis is known. In the case of small samples, the distribution is tabulated, but for sample sizes above ~20, approximation using the normal distribution is fairly good. 

### Calculation
The statistic, $$U$$, could be easily calculated by hand, especially for small samples. 

1. Assign ranks 

   The first step is to rank all the data. To do so we order the data from smallest to largest. This is done on the combined or total sample (i.e., pooling the data from the two treatment groups (n=10)), and assigning ranks from 1 to 10, as follows.
   
   | Sample Value (Ordered)  ||            Ranks   ||
   Placebo    |   New Drugs   | Placebo | New Drugs |
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
   
   For the tie values, we use their mean of ranks. 
   
2. Sum the ranks for each group
   
   The second step is to calculate the sum of ranks, $$R$$, of each group.  
   
   In the placebo group, 
   
   $$
   R_{1} = 4.5 + 6 + 7.5 + 9 + 10 = 37
   $$
   
   In the new drugs group,
   
   $$
   R_{2} = 1 + 2 + 3 + 2 + 4.5 + 7.5 = 18
   $$
   
3. Compute $$U$$
   
   Given
   
   $$
