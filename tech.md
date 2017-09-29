---
layout: page 
title: "Tech Notes" 
description: "思想有多远，我们就可以走多远. <br>(We can go as far as we thought)" 
header-img: "img/top.png" 
---

1. Softwares List (mainly for Mac) - updated: 2017-09-29

	- **Github Desktop**: [https://desktop.github.com/](https://desktop.github.com/)
	- **MarkDown IDE for Mac OS**: [https://macdown.uranusjr.com/](https://macdown.uranusjr.com/)
	- **Anaconda**: [https://www.anaconda.com/download/](https://www.anaconda.com/download/)
	- **QGIS**: [http://www.qgis.org/en/site/forusers/download.html](http://www.qgis.org/en/site/forusers/download.html)
	- **gcc & gfortran**: [http://hpc.sourceforge.net/](http://hpc.sourceforge.net/)
	- **NCL/NCAR**: [http://www.ncl.ucar.edu/Download/](http://www.ncl.ucar.edu/Download/)
	- **CDO**: [https://code.mpimet.mpg.de/projects/cdo/](https://code.mpimet.mpg.de/projects/cdo/)
	- **Panoply (Gridded data viewer)**: [https://www.giss.nasa.gov/tools/panoply/](https://www.giss.nasa.gov/tools/panoply/)
	- **Texmaker (Tex IDE)**: [http://www.xm1math.net/texmaker/](http://www.xm1math.net/texmaker/)
	- **MacTex (Latex for Mac OS)**:[http://www.tug.org/mactex/](http://www.tug.org/mactex/)

1. Install pkgs in Anaconda - updated: 2017-09-29

	1.	Create a **NEW** python environment

		> * Pip 9.0.1
		> * Python 2.7.13
		> * Setuptools 27.2.0
		> * Vs2008_runtime 9.00.30729.5054
		> * Vs2015_runtime 14.0.25420
		> * Wheel 0.29.0

	1. install pkgs using **Terminal** BY the **ORDER** of:

		> 1. conda install -y -c conda-forge basemap
		> 1. conda install -y pandas scipy simplejson
		> 1. conda install -y -c conda-forge rasterio
		> 1. pip install pyshp pycrs shapely netcdf4
		> 1. conda install -y -c conda-forge gdal=2.0
		> 1. conda install -c anaconda statsmodels
	
	1. install my package:
	
		> 1. git clone https://wk1984@bitbucket.org/wk1984/quick-analysis-and-visualization.git
		> 1. cd quick-analysis-and-visualization
		> 1. python setup.py install
		
	1. test:
		> print -c "from QuickPlots import QuickPlots"