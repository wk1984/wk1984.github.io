---
layout: post
title: Using R language in Python
date: 2017-12-21
categories: blog
tags: [R, Python, conda]
header-img: img/top.png    #这篇文章标题背景图片
---

Some packages are only available in R environment.

This post will introduce how to use R in Python.

###- INSTALLING PYTHON AND R
Both Python and R can be managed through the Anaconda platform, which is available for Linux, OSX and Windows. The default installation includes Python, and R can easily be installed later. The 64bit Python3 installer is a suitable download choice for most people.

After Anaconda has been installed on your system, you can use the command line conda package manager or the GUI-driven anaconda-navigator to install Python packages, R, and R libraries. For comprehensive instructions on both of these, refer to the official documentation. Brief step-by-step instructions to get up and running with conda follow.

####PYTHON
When the **Anaconda** installation has finished, Python is accessible by running python in a terminal (on Windows, you might have to run the Anaconda specific command prompt to access Python).

Anaconda also includes graphical interfaces for interacting with Python, which can be invoked by running **spyder** or **jupyter-notebook** from the command line.

To install a new python package from the Anaconda repositories, simply run **conda install < package name >** in a terminal. You can also use the pip package manager, but it will be easier to keep track of packages by sticking to one installation method.

####R
R can be installed via **conda install -c r r-essentials**, which bundles R with some of its most frequently used libraries (for a minimal R setup, substitute r or r-base for r-essentials). 

-c r specifies that this package will be fetched from the R-channel in the Anaconda repositories. 

After the installation completes, R can be invoked from the command line by typing R.

Like with Python, the jupyter-notebook can be used with R, simply launch the notebook and click **New >> R** (technically made possible via the r-irkernel and r-irdisplay packages in the r-essentials bundle). 

Another GUI-driven editor for R can be installed via **conda install -c r rstudio**, and launched by typing rstudio at the command prompt.

To install a new R package, simply type **conda install -c r < package name >**. 

All R package names are prefixed with **r-**. 

You can also use the standard **install.packages() within R**, but it will be easier to keep track of packages by sticking to one installation method.