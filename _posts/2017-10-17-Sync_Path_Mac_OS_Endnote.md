---
layout: post
title: Change the sync library in Endnote X8
date: 2017-10-17
categories: blog
tags: [Sync, Library, Path, Endnote, X8]
header-img: img/top.png    #这篇文章标题背景图片
---

I moved Endnote library (*.enl) to another folder in Mac OS.

It does not sync.

When I check the preferences of Endnote, it does not allow me change the "Sync this Endnote Library".

The solution is to edit the following file:

> ~/Library/Preferences/com.ThomsonResearchSoft.EndNote.plist
> 

Change the Value of "**SyncLibraryPath**"