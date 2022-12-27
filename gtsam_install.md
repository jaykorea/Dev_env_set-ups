
# Install GTSAM from Ubuntu PPA
GTSAM can be installed on Ubuntu via these PPA repositories as well. At present (Nov 2020), packages for Xenial (u16.04), Bionic (u18.04), and Focal (u20.04) are published.

Add PPA for GTSAM nightly builds (develop branch)
# Add PPA
```
sudo add-apt-repository ppa:borglab/gtsam-develop
sudo apt update  # not necessary since Bionic
```
# Install:
```
sudo apt install libgtsam-dev libgtsam-unstable-dev
```
Add PPA for the latest GTSAM 4.x stable release
# Add PPA
```
sudo add-apt-repository ppa:borglab/gtsam-release-4.0
sudo apt update  # not necessary since Bionic
```
# Install:
```
sudo apt install libgtsam-dev libgtsam-unstable-dev
```
# ETC
- change nvidia GPG key
```
sudo add-apt-repository ppa:borglab/gtsam-release-4.0
```
