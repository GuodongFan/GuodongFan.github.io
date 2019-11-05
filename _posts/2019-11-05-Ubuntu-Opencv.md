---
title:  Ubuntu编译安装opencv的坑
published: true
category: work
tag: work
---

### 错误
```
cv2.error: OpenCV(4.1.1) /io/opencv/modules/highgui/src/window.cpp:615: error: (-2:Unspecified error) The function is not implemented. Rebuild the library with Windows, GTK+ 2.x or Cocoa support. If you are on Ubuntu or Debian, install libgtk2.0-dev and pkg-config, then re-run cmake or configure script in function 'cvDestroyWindow'
```

### 解决
```
cmake -D CMAKE_BUILD_TYPE=Release \
-D PYTHON3_EXECUTABLE=/data/anaconda3/envs/tf/bin/python3.6 \
-D PYTHON_INCLUDE_DIR=/data/anaconda3/envs/tf/include/python3.6m \
-D PYTHON_INCLUDE_DIR2=/data/anaconda3/envs/tf/include/python3.6m \
-D PYTHON_LIBRARY=/data/anaconda3/envs/tf/lib/libpython3.6m.so \
-D PYTHON3_NUMPY_INCLUDE_DIRS=/data/anaconda3/envs/tf/lib/python3.6/dist-packages/numpy/core/include/\
-D OPENCV_GENERATE_PKGCONFIG=ON \
-D WITH_GTK_2_X=ON\
-D CMAKE_INSTALL_PREFIX=/usr/local ..
```

安装上GTK与pkg-config后，要加上WITH_GTK_2_X=ON

估计用cmake-gui的时候也是GTK没打开。

