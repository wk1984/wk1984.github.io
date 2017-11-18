---
layout: post
title: Using ANUSPLIN on Mac OS
date: 2017-11-17 
categories: blog
tags: [ANUSPLIN, Wine, Dosbox, Mac]
header-img: img/top.png    #这篇文章标题背景图片
---

I have only a windows version of ANUSPLIN.

Now, I want to use it to do some interpolation tasks.

There obviously are several potential ways.

First of all, we can install virtual machine, such as Parallel Desktop.
	
	- Too big
	- Be paid
	- Need to install whole windows system

However, I like a light Way: **Wine + Dosbox**, that I use here. Because the ANUSPLIN was basically developed with DOS interface.  

	- install Wine and Dosbox
	- Probably, MacPort is a quick and easy way
		- sudo port install wine
		- sudo port install dosbox

Then, the commands need to be modify.

For example, 

Raw command on Windows:

	> ..\..\exec\splina < tmaxa.cmd > tmaxa.log
	
I need to run it with wine like the following:

	> wine ../../exec/splina < tmaxa.cmd > tmaxa.log
	
Then, it works.

<center>
    <p><img src="/img/WX20171117-181045@2x.png" align="center"></p>
</center>

Enjoooy!