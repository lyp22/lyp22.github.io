---
published: true
title: ubuntu上opencv3.2和opencv_contrib安装中遇到的错误记录(cuda9.0)
category: opencv
tags: 
  - opencv
layout: post
---

# 改正版opencv_contrib 3.2下载地址

https://blog.csdn.net/qsczse943062710/article/details/79181831

# 步骤

解压opencv-3.2.0，比如为/home/XXX/opencv-3.2.0

解压我给的opencv_contrib-3.2.0至opencv-3.2.0的目录下（解压完后路径为/home/XXX/opencv-3.2.0/opencv_contrib-3.2.0），并在此处新建一个build文件夹（路径为/home/XXX/opencv-3.2.0/build）

进入build，执行：

```
cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local -D OPENCV_EXTRA_MODULES_PATH=/home/lyp/Data/Downtown/opencv-3.2.0/opencv_contrib/modules -D CUDA_GENERATION=Kepler ..
```
因为是cuda9.0不再支持2.0架构所以要加上-D CUDA_GENERATION=Kepler

# 遇到的错误

## 第一个错误

fatal error: LAPACKE_H_PATH-NOTFOUND/lapacke.h: No such file or directory #include “LAPACKE_H_PATH-NOTFOUND/lapacke.h” 

原因：未找到lapacke.h文件
 
方法： 

sudo apt-get install liblapacke-dev checkinstall 

修改出现问题的文件，例如我的文件是 

opencv-3.2.0/build/opencv_lapack.h 

将第二行中的#include"LAPACKE_H_PATH-NOTFOUND/lapacke.h" 修改为#include"lapacke.h"即可

## 第二个错误

使用Cmake编译opencv源码遇到如下错误

```
CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
CUDA_nppi_LIBRARY (ADVANCED)
linked by target "opencv_cudev" in directory D:/Cproject/opencv/opencv/sources/modules/cudev
linked by target "opencv_cudev" in directory D:/Cproject/opencv/opencv/sources/modules/cudev
```

### 1

找到行

find_cuda_helper_libs(nppi)

改为

```
  find_cuda_helper_libs(nppial)
  find_cuda_helper_libs(nppicc)
  find_cuda_helper_libs(nppicom)
  find_cuda_helper_libs(nppidei)
  find_cuda_helper_libs(nppif)
  find_cuda_helper_libs(nppig)
  find_cuda_helper_libs(nppim)
  find_cuda_helper_libs(nppist)
  find_cuda_helper_libs(nppisu)
  find_cuda_helper_libs(nppitc)
```

### 2

找到行

set(CUDA_npp_LIBRARY "${CUDA_nppc_LIBRARY};${CUDA_nppi_LIBRARY};${CUDA_npps_LIBRARY}")

改为

```
set(CUDA_npp_LIBRARY "${CUDA_nppc_LIBRARY};${CUDA_nppial_LIBRARY};${CUDA_nppicc_LIBRARY};${CUDA_nppicom_LIBRARY};${CUDA_nppidei_LIBRARY};${CUDA_nppif_LIBRARY};${CUDA_nppig_LIBRARY};${CUDA_nppim_LIBRARY};${CUDA_nppist_LIBRARY};${CUDA_nppisu_LIBRARY};${CUDA_nppitc_LIBRARY};${CUDA_npps_LIBRARY}")
```

### 3

找到行

unset(CUDA_nppi_LIBRARY CACHE)

改为

```
unset(CUDA_nppial_LIBRARY CACHE)
unset(CUDA_nppicc_LIBRARY CACHE)
unset(CUDA_nppicom_LIBRARY CACHE)
unset(CUDA_nppidei_LIBRARY CACHE)
unset(CUDA_nppif_LIBRARY CACHE)
unset(CUDA_nppig_LIBRARY CACHE)
unset(CUDA_nppim_LIBRARY CACHE)
unset(CUDA_nppist_LIBRARY CACHE)
unset(CUDA_nppisu_LIBRARY CACHE)
unset(CUDA_nppitc_LIBRARY CACHE)
```

### 4

找到文件OpenCVDetectCUDA.cmake

修改以下几行
```
 ...
  set(__cuda_arch_ptx "")
  if(CUDA_GENERATION STREQUAL "Fermi")
    set(__cuda_arch_bin "2.0")
  elseif(CUDA_GENERATION STREQUAL "Kepler")
    set(__cuda_arch_bin "3.0 3.5 3.7")
  ...
```

改为

```
  ...
  set(__cuda_arch_ptx "")
  if(CUDA_GENERATION STREQUAL "Kepler")
    set(__cuda_arch_bin "3.0 3.5 3.7")
  elseif(CUDA_GENERATION STREQUAL "Maxwell")
    set(__cuda_arch_bin "5.0 5.2")
  ...
```

### 5

cuda9中有一个单独的halffloat(cuda_fp16.h)头文件,也应该被包括在opencv的目录里

将头文件cuda_fp16.h添加至 opencv\modules\cudev\include\opencv2\cudev\common.hpp

即在common.hpp中添加

```
#include <cuda_fp16.h>
```


