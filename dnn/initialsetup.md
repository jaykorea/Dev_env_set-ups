# Install dependancy
```
############################## python 3 #######################################
# if you not install pip (python3)
sudo apt-get install python3-pip
pip install --upgrade pip3

# install torch v1.7 (for python 3)
wget https://nvidia.box.com/shared/static/wa34qwrwtk9njtyarwt5nvo6imenfy26.whl -O torch-1.7.0-cp36-cp36m-linux_aarch64.whl
sudo apt-get install python3-pip libopenblas-base libopenmpi-dev 
pip3 install Cython
pip3 install numpy torch-1.7.0-cp36-cp36m-linux_aarch64.whl

# install torchvision v0.8.1 (for python3)
sudo apt-get install libjpeg-dev zlib1g-dev libpython3-dev libavcodec-dev libavformat-dev libswscale-dev
git clone --branch v0.8.1 https://github.com/pytorch/vision torchvision
cd torchvision
export BUILD_VERSION=0.8.1 
sudo python3 setup.py install
```
## when error, add to zshrc or bashrc
```
export OPENBLAS_CORETYPE=ARMV8
```
## unicode error on python pip
```
export LC_ALL="en_US.UTF-8"
```


# ref link
```
https://github.com/wang-xinyu/tensorrtx/tree/master/yolov5
```
