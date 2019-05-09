---
title: "Mann Whitney U Test - with Python Solution for Small Sample"
excerpt_separator: "<!--more-->"
categories:
  - Stat
tags:
  - Tool
  - Web App
author_profile: 
  subscribe: false
mathjax: true
comments: true
toc: true
toc_sticky: true
---
In this part, I am going to show a demo on the Mann-Whitney U Test Python script which is able to perform test on both small and large sample size. 

Mann-Whitney U test is very useful in small data sample cases, such as clinical dataset (many clinical trials only have very few samples). However, in many modern statistical packages which included Mann-Whitney U test, they were only valid when the data sample size was large. Hence, it is necessary and helpful to have a complete application of Mann-Whitney U test, including two conditions of small sample and large sample. 

[Part 1](https://hatchin.github.io/stat/Mann-Whitney-U/?utm_source=blog&utm_medium=post&utm_campaign=part2){:target="_blank"}: an overview of Mann-Whitney U test

[Part 2](https://hatchin.github.io/stat/Mann-Whitney-U-Tool/): an introduction to new Mann-Whitney U test function

------------------------

[Tool: Web Application](https://mannwhitney.herokuapp.com/?utm_source=blog&utm_medium=post&utm_campaign=Webpage){:target="_blank"}

[Package Source Code](https://github.com/Hatchin/Mann-Whitney-U-Test/blob/master/mannwhitney.py){:target="_blank"}

[Github](https://github.com/Hatchin/Mann-Whitney-U-Test){:target="_blank"}

Demo
----------------------------

### Installation

Download [Mann-Whitney-U-Test](https://github.com/Hatchin/Mann-Whitney-U-Test) to a directory of your choice and then run:

```
pip install -r requirements.txt
```
  
### Use It

In order to use Mann-Whitney-U-Test, you need your data organized as a list like the following:

```
from mannwhitney import *
data1 = [1,2,3,4,4,5]
data2 = [4,5,6,6,9,10,14]
```

Then you could run it just as follows:
```
mwm = mannWhitney(data1,
                  data2, 
                  tail='two', 
                  significant_level=0.05) # two-tailed test
                                          # at 0.05 significance
```

### Analyze

After testing, you could fetch the following results:

`mwm.n1` & `mwm.n2`  the number of sample size for a group

`mwm.sample_size`    small or large sample size

`mwm.significance`   whether the test show signicant difference

`mwm.criticalu`      the critical U value obtained from the table (only available when sample size is small)

`mwm.p`              the p value calculated from the testing data (only available when sample size is large)

`mwm.stat_a`         the U statistics calculated from the testing data

`mwm.effectsize`     the effect size

`mwm.largergroup`    the index of the larger group (1 or 2)

Web Application
--------------

You could also visit the [webpage](https://mannwhitney.herokuapp.com/?utm_source=blog&utm_medium=post&utm_campaign=Webpage){:target="_blank"} which is an application for this script if you don't want to run the code. 

<p align="center">
  <img src="https://raw.githubusercontent.com/Hatchin/Mann-Whitney-U-Test/master/demo.png" alt="">Example
</p>

Similary, just provide two groups of data and the application will run the test and show all the result. 

The valid format of input data includes:
  - copy directly from Excel (a row or a column)
  - mannul typing
    - separate with comma, e.g. `1, 2, 3, 4`
    - separate with space, e.g. `1 2 3 4`
    - mixture, e.g. `1  2  , 3, 4`
    
### Run the server on your instance

It is easy to set up your application and run it on your machine. After installing the required packages, simply run

```
python app.py runserver
```

Then it is on at [http://127.0.0.1:5000/](http://127.0.0.1:5000/)
