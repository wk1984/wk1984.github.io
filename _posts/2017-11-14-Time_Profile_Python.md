---
layout: post
title: Get Time Profile of python script
date: 2017-11-14 
categories: blog
tags: [Time, Profile, Script, Python]
header-img: img/top.png    #这篇文章标题背景图片
---

For example, the pyDeltaRCM model is so slow.

We want to figure out where is the potential improvement.

So we need to test each function's performance, i.e., find what are the most time-cost functions/lines.

In terminal, we can use the following command:

> python -m cProfile -s cumulative run_pyDeltaRCM.py

Then we will see:

<center>
    <p><img src="/img/WX20171114-180728@2x.png" align="center"></p>
</center>

It is useful to improve the code to save much more time.