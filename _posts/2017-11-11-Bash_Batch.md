---
layout: post
title: Using Bash script
date: 2017-11-11
categories: blog
tags: [Bash, Script, For loop]
header-img: img/top.png    #这篇文章标题背景图片
---

If there are many geotiff files need to be converted to netCDF files, how can we do?

The easy way is to use GDAL.

We can write a simple script to implement this task.

```bash
suffix=".tif"

for i in $(ls *.tif); do 

# remove suffix:
foo=${i%$suffix}

gdal_translate -of netCDF -co "FORMAT=NC4" $i $foo.nc

done
```