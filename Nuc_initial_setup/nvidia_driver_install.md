# install nvidia driver on nuc
- 1. etc/modprobe.d/blacklist.conf 에서 blacklist nouveau 추가
- 2. update
```
sudo update-initramfs -u
```
