---
layout: post
title: Compile CDO
date: 2017-10-12
categories: blog
tags: [CDO, Climate, Data, Operators, Compile]
header-img: img/top.png    #这篇文章标题背景图片
---

Due to CDO installation by using MacPorts still has some issues, I need to compile and install CDO by myself.

Here is a tracking of entire processes, including various libs and cdo.

ISSUE - 1:  

**Bug occured in compiling jasper.** Need to be fixed.

```bash
make[3]: *** [jpg_dummy.lo] Error 1
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all-recursive] Error 1
```

**Solution:** It may be caused by the change of compilation method. To solute this issue, please move to old version (jasper-1.900.0.zip)

Script:

```bash
export INSTALL_ROOT=/Users/kangwang/cdo/
echo $INSTALL_ROOT
mkdir $INSTALL_ROOT/src_bundle $INSTALL_ROOT/build
export LDFLAGS=-L$INSTALL_ROOT/lib/
export CPPFLAGS=-I$INSTALL_ROOT/include/

rm -rf *.gz

wget http://zlib.net/zlib-1.2.11.tar.gz
tar -zxvf zlib-1.2.11.tar.gz
cd zlib-1.2.11
./configure --prefix=$INSTALL_ROOT
make all install
cd ..

wget https://support.hdfgroup.org/ftp/lib-external/szip/2.1.1/src/szip-2.1.1.tar.gz
tar -zxvf szip-2.1.1.tar.gz
cd szip-2.1.1
./configure --prefix=$INSTALL_ROOT
make all install
cd ..

wget http://www.hdfgroup.org/ftp/HDF5/current/src/hdf5-1.10.1.tar.gz
tar -zxvf hdf5-1.10.1.tar.gz
cd hdf5-1.10.1
./configure --with-zlib=$INSTALL_ROOT --with-szlib=$INSTALL_ROOT --prefix=$INSTALL_ROOT
make all install
cd ..

wget https://curl.haxx.se/download/curl-7.56.0.tar.gz
tar -zxvf curl-7.56.0.tar.gz
cd curl-7.56.0
./configure --prefix=$INSTALL_ROOT --with-zlib=$INSTALL_ROOT --with-pic
make all install
cd ..

wget https://github.com/Unidata/netcdf-c/archive/v4.4.1.1.tar.gz
tar -zxvf v4.4.1.1.tar.gz
cd netcdf-c-4.4.1.1
./configure --with-hdf5=$INSTALL_ROOT --with-zlib=$INSTALL_ROOT --with-szlib=$INSTALL_ROOT --prefix=/usr/local --enable-netcdf-4
make all install
cd ..

wget http://www.ece.uvic.ca/~frodo/jasper/software/jasper-1.900.0.zip
tar -zxvf jasper-1.900.0.tar.gz
cd jasper-1.900.0
./configure CFLAGS=-fPIC -prefix=$INSTALL_ROOT
make all install

wget https://software.ecmwf.int/wiki/download/attachments/3473437/grib_api-1.24.0-Source.tar.gz
tar -zxvf grib_api-1.24.0-Source.tar.gz
cd grib_api-1.24.0-Source
./configure CFLAGS=-fPIC --prefix=$INSTALL_ROOT --with-netcdf=$INSTALL_ROOT --with-jasper=$INSTALL_ROOT --disable-jpeg
make && make install
cd ..

wget http://download.osgeo.org/proj/proj-4.9.3.tar.gz
tar -zxvf proj-4.9.3.tar.gz
cd tar -zxvf proj-4.9.3
./configure CFLAGS=-fPIC prefix=$INSTALL_ROOT --enable-static=yes --enable-shared=no
make && make install
cd ..

```

