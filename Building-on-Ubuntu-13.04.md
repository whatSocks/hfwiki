The following changes will get hifi building on Ubuntu 13.04. Start with a clean checkout of the hifi project.

## deb package installs

```
$ sudo apt-get install qtdeclarative5-dev qtscript5-dev libqt5svg5-dev libqt5webkit5-dev qtmultimedia5-dev qtlocation5-dev qtsensors5-dev freeglut3-dev libxi-dev libxmu-dev libasound2-dev libjack-jackd2-dev
```

## cmake
```
$ cd build
(make sure this directory is empty if its the first time building)
$ cmake ..
(all projects should compile successfully)
```

## starting servers

From the build directory, make a shell script from the contents below and run it.

```
./assignment-server/assignment-server &
./domain-server/domain-server --local  &
./voxel-server/voxel-server --local &
./avatar-mixer/avatar-mixer --local  &
./audio-mixer/audio-mixer --local &
```

## starting the interface

From hifi/interface (not hifi/build/interface) so the resources/ directory can be found, run the interface with this

```
../build/interface/interface --local
```

