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
