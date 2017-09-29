---
layout: page 
title: "Tech Notes" 
description: "思想有多远，我们就可以走多远. <br>(We can go as far as we thought)" 
header-img: "img/top.png" 
---
## 1 - Softwares List (mainly for Mac) - updated: 2017-09-29

	1. Github Desktop: [https://desktop.github.com/](https://desktop.github.com/)
	1. MarkDown IDE for Mac OS: [https://macdown.uranusjr.com/](https://macdown.uranusjr.com/)
	3. Anaconda: [https://www.anaconda.com/download/](https://www.anaconda.com/download/)
	4. QGIS: [http://www.qgis.org/en/site/forusers/download.html](http://www.qgis.org/en/site/forusers/download.html)
	5. gcc & gfortran: [http://hpc.sourceforge.net/](http://hpc.sourceforge.net/)
	6. NCL/NCAR: [http://www.ncl.ucar.edu/Download/](http://www.ncl.ucar.edu/Download/)
	7. CDO: [https://code.mpimet.mpg.de/projects/cdo/](https://code.mpimet.mpg.de/projects/cdo/)
	8. Panoply (Gridded data viewer): [https://www.giss.nasa.gov/tools/panoply/](https://www.giss.nasa.gov/tools/panoply/)
	9. Texmaker (Tex IDE): [http://www.xm1math.net/texmaker/](http://www.xm1math.net/texmaker/)
	10. MacTex (Latex for Mac OS):[http://www.tug.org/mactex/](http://www.tug.org/mactex/)

## 2 - install pkgs in Anaconda - updated: 2017-09-29

	1.	Create a new python environment

		> * Pip 9.0.1
		> * Python 2.7.13
		> * Setuptools 27.2.0
		> * Vs2008_runtime 9.00.30729.5054
		> * Vs2015_runtime 14.0.25420
		> * Wheel 0.29.0

	1. install pkgs BY the ORDER:

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

