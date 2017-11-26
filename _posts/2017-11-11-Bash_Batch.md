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

### When I want to merge a lot of daily data files to a single one, sometimes cdo will tell me：

> cdo: Argument list too long 

### Because there are so many files if ten years requested.

### A solution is to combine files for each year, then combine all years.

### We need to use a bash for loop to implement:

```bash
#!/bin/bash

rm -rf flx.nc
rm -rf slv.nc

year_start=2001
year_end=2009

for year in $(eval echo "{$year_start..$year_end}")
do
	echo $year
	cdo cat flx/*$year*.nc4 flx$year.nc
	cdo cat slv/*$year*.nc4 slv$year.nc
done

cdo cat flx*.nc flx.nc
cdo cat slv*.nc slv.nc

#rm -rf flx*.nc
#rm -rf slv*.nc
```


