# install cartographer
- install dependencies
```
sudo apt-get update
sudo apt-get install -y python-wstool python-rosdep ninja-build stow
```
- build
```
mkdir catkin_ws
cd catkin_ws
wstool init src
wstool merge -t src https://raw.githubusercontent.com/cartographer-project/cartographer_ros/master/cartographer_ros.rosinstall
wstool update -t src
```
- rodep install, if ilbasl error, remove that package in package.xml!
```
sudo rosdep init
rosdep update
rosdep install --from-paths src --ignore-src --rosdistro=${ROS_DISTRO} -y
```
- install abesill
```
src/cartographer/scripts/install_abseil.sh
```
- remove when confilct
```
sudo apt-get remove ros-${ROS_DISTRO}-abseil-cpp
```
- build and install
```
catkin_make_isolated --install --use-ninja
```

# install cuda amcl
- clone
```
git clone https://github.com/atinfinity/amcl.git
```
- edit cuda gen code in Cmakelists to 75(for rtx2060, xavier agx)

# install gmap
- clone
```
git clone https://github.com/ros-perception/slam_gmapping.git
```
- clone dependency
```
git clone htttps://github.com/ros-perception/openslam_gmapping.git
```
- edit max laser beam param to 4096
```
nano openslam_gmapping/include/scanmatcher/scanmatcher.h
```
