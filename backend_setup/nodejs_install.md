# install node js v16 
- install curl
```
sudo apt-get install curl
```
- install build-essential if not installed
```
sudo apt-get install build-essential
```
- add nodejs ppa
```
curl -sL https://deb.nodesource.com/setup_16.x | sudo -E bash -
```
- install nodejs
```
sudo apt-get install nodejs
```

# set npm global module path
- make global module path
```
mkdir ~/.npm-global-modules
```
- npm config set
```
npm config set prefix '~/.npm-global-modules'
```
- export to zshrc or profile
```
export PATH=$PATH:~/.npm-global-modules/bin

source ~/.zshrc && source ~/.profile
```
