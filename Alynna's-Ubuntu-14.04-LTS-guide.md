#### Totally based on: Coal's CentOS 6.5 Domain-Server and Assignment-Client Compile Guide

## Warning: Currently in progress

0) Add Ubuntu's QT5 PPA.  It will save us a long compile later.
```bash
apt-add-repository ppa:ubuntu-sdk-team/ppa
```

1) First make sure that you have the universe repository in /etc/apt/sources.list, then get current:
```bash
apt-get update
apt-get upgrade
```
1a) If necessary, reboot.

2) Install a build environment if you haven't already
```bash
apt-get install build-essential
```

3) Install dependencies (big long list just paste it in):
```bash
apt-get install openssl libssl-dev ruby perl perf git gperf texinfo libxcb1 libxcb1-dev xcb xcb-proto  libx11-6 libx11-dev libx11-xcb1 libx11-xcb-dev libxrender-dev libicu-dev libxslt1-dev libxext-dev libxmu-dev libxmu-headers libxt-dev libxi-dev libsdl2-dev libgmp10 libgmp-dev zlib1g zlib1g-dev mesa-common-dev libgl1-mesa-dev m4
```

Install CMake Manually from source:
```bash
wget http://www.cmake.org/files/v2.8/cmake-2.8.12.2.tar.gz
tar xvfz cmake-2.8.12.2.tar.gz
rm -rf cmake-2.8.12.2.tar.gz
cd cmake-2.8.12.2
./configure
make
make install
```

Install GLM from source:
```bash
cd /usr/src
wget http://hivelocity.dl.sourceforge.net/project/ogl-math/glm-0.9.5.3/glm-0.9.5.3.zip
unzip glm-0.9.5.3.zip
rm -rf glm-0.9.5.3.zip
ln -s /usr/src/glm/glm /usr/include/
```

Install Nettle from source:
```bash
cd /usr/src
wget http://www.lysator.liu.se/~nisse/archive/nettle-2.7.1.tar.gz
tar xvfz nettle-2.7.1.tar.gz
rm -rf nettle-2.7.1.tar.gz
cd nettle-2.7.1
./configure --prefix=/usr/
make && make install
```

Install GNUtls from source:
```bash
cd /usr/src
wget ftp://ftp.gnutls.org/gcrypt/gnutls/v3.2/gnutls-3.2.14.tar.xz
tar xJf gnutls-3.2.14.tar.xz
rm -rf gnutls-3.2.14.tar.xz
cd gnutls-3.2.14
./configure --prefix=/usr/
make
make install
```

Install Freeglut from source:
```bash
cd /usr/src
wget http://iweb.dl.sourceforge.net/project/freeglut/freeglut/2.8.1/freeglut-2.8.1.tar.gz
tar xvfz freeglut-2.8.1.tar.gz
rm -rf freeglut-2.8.1.tar.gz
cd freeglut-2.8.1
./configure --prefix=/usr/
make && make install
```

Make sure the libraries and QT are available:
```
Folder where QT stuff ends up if following previous instructions:
export QT_CMAKE_PREFIX_PATH=/usr/lib/cmake/
Make sure that the libraries can be found:
export LD_LIBRARY_PATH=/usr/lib
```

Prepare to build HIFI from source:
```bash
cd /usr/src
git clone https://github.com/highfidelity/hifi.git
mkdir hifi/build
cd hifi/build
cmake ..
```

Now pick what you want to build, from interface (which does little good on a machine with no X like I did) or for services:
```bash
make domain-server
make assignment-client
```

To make the Interface on a machine with X, just run:
```bash
make interface
```