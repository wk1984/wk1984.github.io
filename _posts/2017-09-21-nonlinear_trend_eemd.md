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

**Part III: Q&A**