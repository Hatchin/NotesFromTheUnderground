---
title: 
  en: "Mann Whitney U Test - Overview"
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
language: en
permalink: /mannwhitneyu/


---

In this series, I am going to take a journey on Mann-Whitney U test and my Python solution for testing on small sample size. There is going to be an extension for original Mann-Whitney U test in [Scipy](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.mannwhitneyu.html){:target="_blank"}. 

Because the current scipy version only support test for large sample size(n>20),  the new script is made to test for small sample size (n < 20).

[Part 1](https://hatchin.netlify.com/mannwhitneyu/): an overview of Mann-Whitney U test

[Part 2](https://hatchin.netlify.com/mannwhitneyutool/?utm_source=blog_mannwhitneyu&utm_medium=blog_content&utm_campaign=blog){:target="_blank"} : an introduction to Mann-Whitney U test in Python

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

The hypothesis is given below and and the test is supposed to run at the 5% level of significance (i.e., $$\alpha=0.05$$).: 

$$
H_{0}: The \ two \ populations \ are \ equal \ versus
\\
H_{1}: The \ two \ populations \ are \ not \ equal.
$$

The sample size is small ($$n_{1}=n_{2}=5$$), so a nonparametric test is appropriate. We are going to use Mann-Whitney U test to solve this problem. 

The test statistic for the Mann-Whitney U Test is denoted $$U$$, whose whose distribution under the null hypothesis is known. In the case of small samples, the distribution is tabulated, but for sample sizes above ~20, approximation using the normal distribution is fairly good. 

### Small Sample Example
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
   
   Given,
   
   $$
   U_{i} = n_{1}n_{2} + \frac{n_{i}(n_{i}+1)}{2} - R_{i}
   \\
   U =  min( U_{1}, ..., U_{i})
   $$
   
   For this example,
   
   $$
   U_{1} = 5(5) + \frac{5(6)}{2} - 37 = 3
   \\
   U_{1} = 5(5) + \frac{5(6)}{2} - 18 = 22
   $$
  
   Thus, the test statistic is  $$U=3$$.
   
4. Compare $$U$$ with critical $$U$$
   
   In every test, we must determine whether the observed $$U$$ supports the null hypothesis. This is done following the same approach used in parametric testing. Specifically, we determine a critical value of $$U$$ such that,
   
   {: style="text-align:center"}
   If $$U \leq critical \ U$$, we reject $$H_{0}$$ in favor of $$H_{1}$$ and,
   
   {: style="text-align:center"}
   if $$U > critical \ U$$ we do not reject $$H_{0}$$.
   
   The table of critical $$U$$ is as follows.
   
   <iframe src="https://drive.google.com/file/d/1tDhqpREuVXevtImG0N_oviIFcb3khlah/preview" width="600" height="450"></iframe>
   
   From this table, we could get the critical $$U = 2$$ and therefore, 
   
   $$
   U = 3 > 2 = critical \ U
   $$
   
   We do not reject $$H_{0}$$ and do not have statistically significant evidence at $$\alpha =0.05$$, to show that the two populations are not equal. 
   
### When sample size is larger (n > 20)

With samples this large, the value of $$U$$ approaches a normal distribution, and so the null hypothesis can be tested by a Z-test.

1. Compute $$U$$
   
   Here,
   
   $$
   U =  max( U_{1}, ..., U_{i})
   $$

2. Compute the z value of $$U$$ statistic

   $$
   \sigma _{U}={\sqrt {n_{1}n_{2}(n_{1}+n_{2}+1) \over 12}}
   \\
   \\
   Z = \frac{ U - \frac{n_{1}n{2}}{2}}{\sigma _{U}}
   $$
   
3. Determination

   Compare the obtained Z value and the critical Z value to determine whether to retain or reject the null hypothesis. 
   at the 5% level of significance, similarly,
   
   {: style="text-align:center"}
   If $$Z \leq critical \ Z = 1.96$$, we do not reject $$H_{0}$$ and,
   
   {: style="text-align:center"}
   if $$Z > critical \ Z = 1.96$$ we reject $$H_{0}$$ in favor of $$H_{1}$$.
   
   
Python Script for Mann–Whitney U test
----------------------

The Mann–Whitney U test is included in most modern statistical packages. For instance, in Python, Mann-Whitney U is available in [scipy.stat](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.mannwhitneyu.html){:target="_blank"}. 

However, the scipy version of Mann-Whitney U test noted that
```
Use only when the number of observation in each sample is > 20.
```

Because Mann-Whitney U test is very useful in small data sample cases, such as clinical dataset (many clinical trials only have very few samples), a complete application of Mann-Whitney U test, including two conditions of small sample and large sample, was developed. 

In [Part 2](https://hatchin.netlify.com/mannwhitneyutool/?utm_source=blog_mannwhitneyu&utm_medium=blog_content&utm_campaign=blog), we go further to have a detailed demo on the new application.

---------------------------------

More details could be found:

[Tool: Web Application](https://mannwhitney.herokuapp.com/?utm_source=blog&utm_medium=post&utm_campaign=Webpage){:target="_blank"}

[Package Source Code](https://github.com/Hatchin/Mann-Whitney-U-Test/blob/master/mannwhitney.py){:target="_blank"}

[Github](https://github.com/Hatchin/Mann-Whitney-U-Test){:target="_blank"}
