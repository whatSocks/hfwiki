### Coal's CentOS 6.5 Domain-Server and Assignment-Client Compile Guide

I wrote this originally for virtual machines (KVM, not OpenVZ).

On a side-note you can also compile the Interface using this configuration but as I wrote this using a KVM Virtual Machine with no X-Windows, I never tried to run it. On a desktop machine you should probably be able to compile and run "Interface" fine just ignoring the parts marked specifically for VMs.

***

Yum install for the compile/build tools in general:
```bash
yum groupinstall "development tools" -y
```

Yum install for most all hardware configurations:
```bash
yum install openssl-devel ruby perl-version git gperf texinfo wget -y
yum install libxcb libxcb-devel xcb-util xcb-util-devel xcb-util-*-devel -y
yum install libX11-devel libXrender-devel libicu-devel libxslt-devel -y
yum install libXext-devel libXmu-devel libXt-devel libXi-devel -y
yum install SDL SDL-devel gmp gmp-devel -y
```

OPTIONAL: For users under KVM Virtualized Environments for GL graphics support (It really does not hurt to install these but I run my world under a KVM virtual machine so I needed it for 3D/OpenGL:
```bash
yum install mesa-libGL zlib-devel mesa-libGL-devel mesa-libGLU-devel -y
```

Install CMake Manually from source:
```bash
wget http://www.cmake.org/files/v2.8/cmake-2.8.12.2.tar.gz
tar xvfz cmake-2.8.12.2.tar.gz
rm -rf cmake-2.8.12.2.tar.gz
cd cmake-2.8.12.2
./configure
gmake
gmake install
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

Install QT from source:
```bash
cd /usr/src
wget http://download.qt-project.org/official_releases/qt/5.2/5.2.1/single/qt-everywhere-opensource-src-5.2.1.tar.gz
tar -vxf qt-everywhere-opensource-src-5.2.1.tar.gz
rm -f qt-everywhere-opensource-src-5.2.1.tar.gz
cd qt-everywhere-opensource-src-5.2.1
./configure --prefix=/usr/ -opensource -openssl -nomake examples -nomake tests
gmake
gmake install
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