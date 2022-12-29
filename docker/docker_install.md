# Install docker for ubuntu18.04

- 1. 시스템을 최신으로 하기 위한 업데이트를 한다. 
```
sudo apt update
```
- 2. 사전 설치를 한다. 
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
- 3. Docker repository key를 Add 한다. 
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
````
- 4. Docker repository를 Add 한다. 
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
```
- 5. 시스템을 최신으로 하기 위한 다시 업데이트를 한다. 
```
sudo apt update
```
- 6. install docker with apt
```
sudo apt install docker-ce
```

# check available or installed docker version with command
```
apt-cache policy docker-ce
```
# check if docker is well installed and running
```
sudo systemctl status docker 
```
