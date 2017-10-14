---
layout: post
title: Compile LIBEEMD in Windows 
date: 2017-10-14
categories: blog
tags: [signal, nonlinear, trend, eemd, python, C, Windows]
description: EEMD method to estimate nonlinear trend
header-img: img/top.png    #这篇文章标题背景图片
---

**Compile libeemd in windows**

**Part I: Install EEMD packages**

1. Install [**Anaconda**](https://www.anaconda.com/download/)
 *    Create a new environment, e.g., **EEMD_ENV**
 *    Use terminal in **EEMD_ENV**

	![Example Figure 1:](/img/eemd_win_001.png "Figure 1")

1. Install **m2w64-gcc, make, m2w64-pkg-config, and m2w64-gsl** by using the terminal:
 *    > conda install make
 *    > conda install m2w64-pkg-config
 *    > conda install -c msys2 m2w64-gsl
 *    > conda install -c msys2 m2w64-gcc
1. Clone repos:
 *    >  git clone https://wk1984@bitbucket.org/luukko/libeemd.git
 *    >  git clone https://wk1984@bitbucket.org/luukko/pyeemd.git
    
1. Goto **libeemd**:
 *    > cd libeemd

1. Create a new folder **'obj'** manually or in DOS:
    > mkdir obj

1. Edit **Makefile** in libeemd:

	**line 58**: Delet or comment "ln -sf $@ libeemd.so". This line is only for creating linkage to specific version lib. It does not work in windows.
	> ln -sf $@ libeemd.so

1. Compile **libeemd**:

 *    > make

	It will be warning:

    ```bash
          1 [main] make 5020 find_fast_cwd: WARNING: Couldn't compute FAST_CWD pointer.  Please report this problem to
    the public mailing list cygwin@cygwin.com
    make: uname: Command not found
    cp src/eemd.h eemd.h
    make: cp: Command not found
    Makefile:60: recipe for target `eemd.h' failed
    make: *** [eemd.h] Error 127
    ```

    Igore the information above. That is only because the cmd "cp src/eemd.h" does not work.

    We can copy the file "src/eemd.h" manually.

 *    > cd ..

1. Install **pyeemd**:
 *    > cd pyeemd
 *    > python setup.py install
 
1. Copy **libeemd** files 
   * Find out which the pyeemd install folder is, e.g., "~/anaconda/envs/EEMD_ENV/lib/python2.7/site-packages/pyeemd-1.4-py2.7.egg/pyeemd"
   * Copy **"src/eemd.h", "libeemd.a", and "libeemd.so.1.4.1"** to pyeemd install folder.
   * Rename **libeemd.so.1.4.1** to **libeemd.so**

1. **Finish** 
 
**Part II: Examples**

Taking an example of global temperature time-series

```python
-
```
![Example Figure:](/img/eemd_test.png "Global Temperature")


**Part III: Q&A**