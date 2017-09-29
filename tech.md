---
layout: page 
title: "Tech Notes" 
description: "思想有多远，我们就可以走多远. <br>(We can go as far as we thought)" 
header-img: "img/top.png" 
---
1. **Softwares List (mainly for Mac) - updated: 2017-09-29**
	1. Github Desktop: [https://desktop.github.com/](https://desktop.github.com/)
	2. MarkDown IDE for Mac OS: [https://macdown.uranusjr.com/](https://macdown.uranusjr.com/)
	3. Anaconda: [https://www.anaconda.com/download/](https://www.anaconda.com/download/)
	4. QGIS: [http://www.qgis.org/en/site/forusers/download.html](http://www.qgis.org/en/site/forusers/download.html)
	5. gcc & gfortran: [http://hpc.sourceforge.net/](http://hpc.sourceforge.net/)
	6. NCL/NCAR: [http://www.ncl.ucar.edu/Download/](http://www.ncl.ucar.edu/Download/)
	7. CDO: [https://code.mpimet.mpg.de/projects/cdo/](https://code.mpimet.mpg.de/projects/cdo/)

1. **install pkgs in Anaconda - updated: 2017-09-29**

	1.	Create a new python environment

		> a)	Pip 9.0.1

		> b)	Python 2.7.13

		> c)	Setuptools 27.2.0

		> d)	Vs2008_runtime 9.00.30729.5054

		> e)	Vs2015_runtime 14.0.25420

		> f)	Wheel 0.29.0

	1. install pkgs BY the ORDER:

		> conda install -y –c conda-forge basemap
		> 
		> conda install -y pandas scipy simplejson
		> 
		> conda install –y -c conda-forge rasterio
		> 
		> pip install pyshp pycrs shapely netcdf4
		> 
		> conda install -y –c conda-forge gdal=2.0
		> 
		> conda install -c anaconda statsmodels
	
	1. install my package:
	
		> git clone https://wk1984@bitbucket.org/wk1984/quick-analysis-and-visualization.git

		> cd quick-analysis-and-visualization

		> python setup.py install
		
	1. test:
		> print -c "from QuickPlots import QuickPlots" 

