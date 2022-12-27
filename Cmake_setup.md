# Install Latest Cmake

- Download latest cmake version
```
wget https://cmake.org/files/v3.16/cmake-3.16.2.tar.gz
```

- unZip
```
tar -xvzf 해당파일.tar.gz
cd 압축풀린폴더
./bootstrap --prefix=/usr/local
make
sudo make install
```
- add path to bashrc/zshrc or bash_profile
```
PATH=/usr/local/bin:$PATH:$HOME/bin
```

