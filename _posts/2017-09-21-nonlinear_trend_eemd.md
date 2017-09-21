---
layout: post
title: EEMD method
date: 2017-09-21
categories: blog
tags: [signal, nonlinear, trend, eemd, python, C]
description: EEMD method to estimate nonlinear trend
header-img: img/top.png    #这篇文章标题背景图片
---

**Note:**Only for MacOS

**Part I: Install EEMD packages**

1. Install [**Anaconda**](https://www.anaconda.com/download/)
 *    Create a new environment, e.g., **EEMD_ENV**
 *    Use terminal in **EEMD_ENV**
1. Install **gcc, make, pkg-config, and gsl** by using the terminal:
 *    > conda install -y gcc pkg-config gsl
1. Install **Git**:
 *    > sudo port install git
1. Clone repos:
 *    >  git clone https://wk1984@bitbucket.org/luukko/libeemd.git
 *    >  git clone https://wk1984@bitbucket.org/luukko/pyeemd.git
1. Compile **libeemd**:
 *    > cd libeemd
 *    > make
 *    > cd ..
1. Install **pyeemd**:
 *    > cd pyeemd
 *    > python setup.py install
1. Copy **libeemd** files 
   * Find out which the pyeemd install folder is, e.g., "~/anaconda/envs/EEMD_ENV/lib/python2.7/site-packages/pyeemd-1.4-py2.7.egg/pyeemd"
   * Copy "eemd.h", "libeemd.a", "libeemd.so", and "libeemd.so.1.4.1" to pyeemd install folder.

1. **Finish** 
 
**Part II: Examples**

Taking an example of global temperature time-series

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import statsmodels.api as sm
import pyeemd

url = 'https://data.giss.nasa.gov/gistemp/graphs/graph_data/Global_Mean_Estimates_based_on_Land_and_Ocean_Data/graph.csv';

data = pd.read_csv(url,skiprows=1)

year = data['Year']
tmp = data['No_Smoothing']
tmp = np.array(tmp)

X = sm.add_constant(year)
model = sm.OLS(tmp, X).fit()
predictions = model.predict(X)

imfs = pyeemd.eemd(tmp)

fig = plt.figure() 
ax = fig.add_subplot(111)
plt.plot(year, tmp)
eemd_lin = plt.plot(year, imfs[-1,:],label='EEMD')
reg_lin = plt.plot(year, predictions,label='Linear')

plt.legend()
plt.xlim([1879,2017])

trend_eemd = (imfs[-1,-1]-imfs[-1,0])/137.0*100.0
trend_linear = (predictions[134]-predictions[0])/137.0*100.0

plt.text(0.3,0.9, np.str(np.round(trend_eemd,3))+' $^o$C/100a'\
         ,  transform=ax.transAxes\
         , color = eemd_lin[0].get_color())
plt.text(0.3,0.85, np.str(np.round(trend_linear,3))+' $^o$C/100a'\
         ,  transform=ax.transAxes\
         , color = reg_lin[0].get_color())

plt.savefig('test.png',dpi=326)

plt.close()

```

Example Figure:

<center>
    <p><img src="img/eemd_test.png" align="center"></p>
</center>

**Part III: Q&A**