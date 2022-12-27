# Install dependancy


- install g2o
```
sudo apt-get install ros-melodic-libg2o
```

- install gtsam
```
- Add PPA
sudo add-apt-repository ppa:borglab/gtsam-release-4.0
sudo apt update  # not necessary since Bionic
- Install:
sudo apt install libgtsam-dev libgtsam-unstable-dev
```
- install octomap
```
sudo apt-get install ros-melodic-octomap
```
- install libpointmatcher
```
sudo apt-get install ros-melodic-libpointmatcher
```
- install pcl
```
sudo apt-get install ros-melodic-pcl-ros
```
- install apriltag

```
git clone https://github.com/AprilRobotics/apriltag.git

mkdir build

cd build
cmake -DCMAKE_BUILD_TYPE=release
make -j8
sudo make install
```

- install find_object_2d
install find_object_2d source to catkin workspace
```
git clone https://github.com/introlab/find-object.git src/find_object_2d
catkin_make 
```

# Install Rtabmap
```
cmake .. -DWITH_CERES=ON
make -j8
sudo make install
```
