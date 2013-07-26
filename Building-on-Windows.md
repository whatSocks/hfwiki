###Requirements
* CMake — download [here](http://www.cmake.org/cmake/resources/software.html), grab the Win32 installer
* Visual Studio 2012 — a free version called VS Express can be downloaded [here](http://www.microsoft.com/visualstudio/eng/downloads#d-express-windows-desktop)
* Qt 4.x libraries — download VS2010 libs [here](http://qt-project.org/downloads), for example I grabbed _Qt libraries 4.8.5 for Windows (VS 2010, 235 MB)_ **MUST GRAB 4.X, NOT THE NEWER 5.X**

###Getting the source
The easiest way to grab the source is by going to [here](https://github.com/worklist/hifi) and clicking **Download ZIP** which is at the bottom of the right toolbar.

This tutorial assumes you extract this source to **C:\hifi-master**

###Configuring
Run CMake (cmake-gui) and enter the following information:
* Where is the source code: **C:\hifi-master** 
* Where to build the binaries: **C:\hifi-win32** 

Click **Configure**.  Ensure the **Advanced** checkbox in the upper right is checked.

###Building

Open **C:\hifi-win32\hifi.sln** in Visual Studio.