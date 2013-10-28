The following changes will get hifi building on Ubuntu 13.04. Start with a clean checkout of the hifi project.

## deb package installs

```
$ sudo apt-get install qtdeclarative5-dev qtscript5-dev libqt5svg5-dev libqt5webkit5-dev qtmultimedia5-dev qtlocation5-dev qtsensors5-dev freeglut3-dev libxi-dev libxmu-dev libasound2-dev osspd
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
It can be fixed with this hack, edit 
```
build$ vi assignment-client/CMakeFiles/assignment-client.dir/link.txt
```
Append "-ldl" to the first and only line in that file.
