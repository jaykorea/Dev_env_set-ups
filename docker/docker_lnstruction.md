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
# docker load
- load backup file to image
```
sudo docker load < [백업한 파일이름].tar
sudo docker load < build-machin.tar   # 복원하기
sudo docker images   # 확인하기
```
# docker run command
```
sudo docker run --init --privileged -it --name freeway --net=host --gpus all -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix -v ~/docker_share:/data -v /dev:/dev --rm jaykor97freeway:rev.04_jay /bin/zsh

```
