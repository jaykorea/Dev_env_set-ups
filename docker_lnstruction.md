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
