##Requirements
* CMake — download [here](http://www.cmake.org/cmake/resources/software.html), grab the Win32 installer
* Visual Studio 2012 — a free version called VS Express can be downloaded [here](http://www.microsoft.com/visualstudio/eng/downloads#d-express-windows-desktop)
* Qt 4.x libraries — download VS2010 libs [here](http://qt-project.org/downloads), for example I grabbed _Qt libraries 4.8.5 for Windows (VS 2010, 235 MB)_ **MUST GRAB 4.X, NOT THE NEWER 5.X**

##Getting the source
The easiest way to grab the source is by going to [here](https://github.com/worklist/hifi) and clicking **Download ZIP** which is at the bottom of the right toolbar.

This tutorial assumes you extract the source to **C:\hifi-master**

##Configuring
* Run CMake (cmake-gui) and enter the following information
* Where is the source code: **C:\hifi-master** 
* Where to build the binaries: **C:\hifi-win32** 
* Click **Configure**.  It will ask if you want to create the directory, click **Yes**
* Select **Visual Studio 11** as the generator for the project
* Select **Use default native compilers** and click **Finish**
* Once it says "Configuring done" at the bottom, click **Generate**
* Close CMake

##Building
* Open **C:\hifi-win32\hifi.sln** in Visual Studio 2012
* Ensure you are in the **Debug** build target (you should be by default)
* In the Solution Explorer, right click **interface** and click **Set as StartUp Project**
* Right click **interface** and click **Build**
* Once finished, the build log should say something similar to "Build: 7 succeeded, 0 failed, 0 up-to-date, 0 skipped"
* Before you can debug the program, you must copy the required DLLs to the debug folder
* Copy all the DLLs from **C:\hifi-master\externals\win32-dll\Debug** to **C:\hifi-win32\interface\Debug**
* Now you can run and debug "interface" through Visual Studio