# opencv_env_setting

# Install dependency
- 기존 설치 opencv 제거
1. pkg-config --modversion opencv
으로 기존 버전이 설치되어있는지를 확인 후 설치가 안 되어있으면 설치를 진행하면 됨
 
2. 제거
sudo apt-get purge libopencv* python-opencv
sudo apt-get autoremove
 
sudo find /usr/local/ -name "*opencv*" -exec rm -i {} \;


3. 준비

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
wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.4.0.zip
```

# Cmake option
```
mkdir -p build
```
