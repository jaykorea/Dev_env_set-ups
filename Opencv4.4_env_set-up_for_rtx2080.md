# opencv_env_setting

# Install dependency

- 1. 기존 버전이 설치되어있는지를 확인 후 설치가 안 되어있으면 설치를 진행하면 됨
```
pkg-config --modversion opencv
```
 
- 2. 제거
```
sudo apt-get purge libopencv* python-opencv
sudo apt-get autoremove
 
sudo find /usr/local/ -name "*opencv*" -exec rm -i {} \;
```

- 3. 준비

```
sudo apt-get update
sudo apt-get upgrade
 
sudo apt-get install build-essential cmake
sudo apt-get install pkg-config
sudo apt-get install libjpeg-dev libtiff5-dev libpng-dev
 
sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libxvidcore-dev libx264-dev libxine2-dev
 
sudo apt-get install libv4l-dev v4l-utils
 
sudo apt-get install libstreamer1.0-dev libstreamer-plugins-base1.0-dev
 
sudo apt-get install libgtk2.0-dev
 
sudo apt-get install libgtk-3-dev
sudo apt-get install libqt4-dev
sudo apt-get install libqt5-dev
 
sudo apt-get install mesa-utils libgl1-mesa-dri libgtkgl2.0-dev libgtkglext1-dev
 
sudo apt-get install python2.7-dev python3-dev python-numpy python3-numpy
```

# Download OPENCV
```
wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.4.0.zip
wget -O opencv.zip https://github.com/opencv/opencv/archive/4.4.0.zip

unzip opencv.zip
unzip opencv_contrib.zip
```

# Cmake option
- make folder in opencv folder
```
mkdir build
```
```
cmake -D CMAKE_BUILD_TYPE=RELEASE \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D WITH_TBB=OFF \
-D WITH_IPP=OFF \
-D WITH_1394=OFF \
-D BUILD_WITH_DEBUG_INFO=OFF \
-D BUILD_DOCS=OFF \
-D BUILD_EXAMPLES=OFF \
-D BUILD_TESTS=OFF \
-D BUILD_PERF_TESTS=OFF \
-D WITH_CUDA=ON \
-D WITH_CUDNN=ON \
-D OPENCV_DNN_CUDA=ON \
-D CUDA_FAST_MATH=ON \
-D CUDA_ARCH_BIN=7.5 \
-D WITH_CUBLAS=ON \
-D WITH_CUFFT=ON \
-D WITH_QT=ON \
-D WITH_GTK=OFF \
-D WITH_OPENGL=ON \
-D WITH_V4L=ON \
-D WITH_FFMPEG=ON \
-D WITH_XINE=ON \
-D BUILD_NEW_PYTHON_SUPPORT=ON \
-D INSTALL_C_EXAMPLES=OFF \
-D INSTALL_PYTHON_EXAMPLES=OFF \
-D OPENCV_GENERATE_PKGCONFIG=ON \
-D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-4.4.0/modules \
-D OPENCV_ENABLE_NONFREE=ON \
-D BUILD_EXAMPLES=OFF ..
```

```
make -j$
sudo make install
sudo ldconfig
```

# Done
