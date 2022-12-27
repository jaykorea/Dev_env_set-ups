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

- install apriltag

```
git clone https://github.com/AprilRobotics/apriltag.git

mkdir build

cd build
cmake -DCMAKE_BUILD_TYPE=release
make -j8
sudo make install
```
