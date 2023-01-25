# add key
```
sudo sh \
    -c 'echo "deb http://packages.ros.org/ros/ubuntu `lsb_release -sc` main" \
        > /etc/apt/sources.list.d/ros-latest.list'
```
```
wget http://packages.ros.org/ros.key -O - | sudo apt-key add -
```

# apt update
```
sudo apt-get update
```
# install catkin tools
```
sudo apt-get install python3-catkin-tools
```
