# docker login
- login to docker
```
docker login
username:
pwd:
```
# push to docker hub
- don't forget to change tag to user name
- docker image tag {이미지} {내 유저명}/{이미지}
```
docker image freeway:rev.04_jay jaykor97/freeway:rev.04_jay
```
```
docker push jaykor97/freeway:rev.04_jay
```
# docker backup(save)
- save docker image to tar
```
sudo docker save -o [저장할이름].tar [이미지 이름]
sudo docker save -o build-machin.tar build-machin
```
# docker load
- load backup file to image
```
sudo docker load < [백업한 파일이름].tar
sudo docker load < build-machin.tar   # 복원하기
sudo docker images   # 확인하기
```
# docker run command
```
sudo docker run --init --privileged -it --name freeway --net=host --gpus all -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix -v ~/docker_share:/data -v /dev:/dev --rm jaykor97/freeway:rev.04_jay /bin/zsh
```
# docker run command for external gui
- enable gpu capabilities and link to external dispaly port
```
xhost +local:docker
```
- run command
```
sudo docker run --init --privileged -it --name freeway --net=host --gpus=all -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix:rw -v ~/docker_share:/data -v /dev:/dev -v /tmp/.docker.xauth:/tmp/.docker.xauth:rw -e XAUTHORITY=/tmp/.docker.xauth -e QT_X11_NO_MITSHM=1 -e NVIDIA_DRIVER_CAPABILITIES=all --rm jaykor97/freeway:rev.04_jay /bin/zsh  
```
# error to load gpu drivier
- docker run 명령어를 사용하여 container를 생성할 때 --gpus 옵션을 사용하여 생성하는 경우 아래와 같이 문제가 발생한다.
- docker: Error response from daemon: could not select device driver "" with capabilities: [[gpu]].
- 해결 방안
- nvidia-container-toolkit을 설치하면 모든게 해결된다. 우선 nvidia repository를 추가한 다음 apt-get 명령어를 사용하여 nvidia-container-toolkit을 설치해 준다.
```
distribution=$(. /etc/os-release;echo $ID$VERSION_ID) \
   && curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add - \
   && curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
```
```
sudo apt-get update && sudo apt-get install -y nvidia-container-toolkit
sudo systemctl restart docker
```
# gazebo [[Err] [REST.cc:205] Error in REST request] error
- need to change ~/.ignition/fuel/config.yaml as following.
```
url: https://api.ignitionfuel.org

to

url: https://api.ignitionrobotics.org

```

# Gazebo model error ( Can not load gazebo without internet)
## gazebo keep requesting gazebo models to server even if internet is not connected
- download menifest gazebo model to .gazebo folder as 'models'
```
cd ~/.gazebo
git clone https://github.com/osrf/gazebo_models.git models
```
- edit GAZEBO_MODEL_DATABASE_URI as null
```
nano /usr/share/gazebo/setup.sh
nano /usr/share/gazebo-<version>/setup.sh
```
```
export GAZEBO_MASTER_URI=http://localhost:11345
export GAZEBO_MODEL_DATABASE_URI=
export GAZEBO_RESOURCE_PATH=/usr/share/gazebo-9:${GAZEBO_RESOURCE_PATH}
export GAZEBO_PLUGIN_PATH=/usr/lib/x86_64-linux-gnu/gazebo-9/plugins:${GAZEBO_PLUGIN_PATH}
export GAZEBO_MODEL_PATH=/usr/share/gazebo-9/models:${GAZEBO_MODEL_PATH}
export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/lib/x86_64-linux-gnu/gazebo-9/plugins
export OGRE_RESOURCE_PATH=/usr/lib/x86_64-linux-gnu/OGRE-1.9.
```
- after edit, source
```
source /usr/share/gazebo/setup.sh
source /usr/share/gazebo-<version>/setup.sh
```
- copy config to model.config in gazebo folder
```
cp ~/.gazebo/models/.git/config ~/.gazebo/models/.git/model.config
```
- and run command
```
gazebo --verbose
```

# docker roscore error
- stop all container first
```
docker stop $(docker ps -q)
```
- remove all container
```
docker rm $(docker ps -a -q)
```

