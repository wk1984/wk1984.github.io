---
layout: post
title: Using NCO to calculate area-weighted average
date: 2017-11-21
categories: blog
tags: [NCO, Area-weighted, NetCDF]
header-img: img/top.png    #这篇文章标题背景图片
---

NCO provides some tools to do quick analysis on NC files.

Now, I need to calculate area-weighted average anomaly for global land surface.

Raw monthly temperature anomaly file: **tmp.nc**

- **calculate year mean:**

> cdo yearmean tmp.nc in.nc

- **calculate areal weight:**

> ncap -h -O -s "weights=cos(lat*3.1415/180)" in.nc in.nc   

- **calculate average:**

> ncwa -h -O -w weights -a lat,lon in.nc global_mean.nc  