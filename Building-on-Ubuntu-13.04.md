The following changes will get hifi building on Ubuntu 13.04. Start with a clean checkout of the hifi project.

## deb package installs

```
$ sudo apt-get install build-essential cmake git libcurl4-openssl-dev libasound2 libxmu-dev libxi-dev freeglut3-dev libasound2-dev libjack-dev
```

## Qt dependencies

1. Download lastest Qt packages from [Qt Project](http://qt-project.org/downloads) and install/untar on your prefered path.
2. Set your `QT_CMAKE_PREFIX_PATH` environment variable to point to the cmake folder on your Qt installation: 

```
$ export QT_CMAKE_PREFIX_PATH=~/Qt5.2.0/5.2.0/gcc_64/lib/cmake
```
It's recommended that you move this variable setup to your `~/.bashrc` and/or `~/.bash_profile` so you'll save setting the path on new bash instances:

```
$ echo 'export QT_CMAKE_PREFIX_PATH=~/Qt5.2.0/5.2.0/gcc_64/lib/cmake' >> ~/.bashrc
```

## cmake
```
$ cd build
(make sure this directory is empty if its the first time building)
$ cmake ..
(all projects should compile successfully)
```

## starting the interface

From hifi/interface (not hifi/build/interface) so the resources/ directory can be found, run the interface with this

```
../build/interface/interface --local
```

## Build errors

If you see this error
```
Linking CXX executable assignment-client
/usr/bin/ld: ../libraries/voxel-server-library/libvoxel-server-library.a(civetweb.c.o): undefined reference to symbol 'dlclose@@GLIBC_2.2.5'
/usr/bin/ld: note: 'dlclose@@GLIBC_2.2.5' is defined in DSO /lib/x86_64-linux-gnu/libdl.so.2 so try adding it to the linker command line
/lib/x86_64-linux-gnu/libdl.so.2: could not read symbols: Invalid operation
collect2: error: ld returned 1 exit status
```
It can be fixed with this hack, append "-ldl" to link.txt with this 
```
build$ sed -i -e's/$/-ldl/' assignment-client/CMakeFiles/assignment-client.dir/link.txt

```

