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

* Install [**Anaconda**](https://www.anaconda.com/download/)
 *    Create a new environment, e.g., **EEMD_ENV**
 *    Use terminal in **EEMD_ENV**
* Install **gcc, make, pkg-config, and gsl** by using the terminal:
 *    > conda install -y gcc pkg-config gsl
* Install **Git**:
 *    > sudo port install git
* Clone repos:
 *    >  git clone https://wk1984@bitbucket.org/luukko/libeemd.git
 *    >  git clone https://wk1984@bitbucket.org/luukko/pyeemd.git
* Compile **libeemd**:
 *    > cd libeemd
 *    > make
 *    > cd ..
* Install **pyeemd**:
 *    > cd pyeemd
 *    > python setup.py install
* Copy **libeemd** files 

  * Find out which the pyeemd install folder is, e.g., "~/anaconda/envs/EEMD_ENV/lib/python2.7/site-packages/pyeemd-1.4-py2.7.egg/pyeemd"
  * Copy "eemd.h", "libeemd.a", "libeemd.so", and "libeemd.so.1.4.1" to pyeemd install folder.

* **Finish** 
 
**Part II: Examples**

**Part III: Q&A**