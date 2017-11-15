---
layout: post
title: Use Cython to speed up python code
date: 2017-11-14 
categories: blog
tags: [Cython, Python]
header-img: img/top.png    #这篇文章标题背景图片
---

Cython is able to speed up python code.

It can automatically convert python function to C language, and compile to a lib which could be imported directly by python.

Let's knock the door!

###Installation###

> conda install cython

###Hello World###

<center>
    <p><img src="/img/fbbe4cc313cb4db8b3d41a2439a10e76.jpeg" align="center"></p>
</center>

- write one-line python code to "helloworld**.pyx**":
	
	> print "Hello World" 
	
- create a python code to compile this pyx file. Generally, we named it as "setup.py", which is similar to *setuptools*:

	```python
	from distutils.core import setup
	from Cython.Build import cythonize
	
	setup(
	    ext_modules = cythonize("helloworld.pyx")
	)
	
	```
	
- use terminal to compile:

	> python setup.py build_ext --inplace		
- We can include this function like python lib:

	```python
	import helloworld
	```
	
	It will print out "Hello World".
	
###Details###

See: [http://docs.cython.org/en/latest/](http://docs.cython.org/en/latest/)