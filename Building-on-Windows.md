##Requirements
* CMake — download [here](http://www.cmake.org/cmake/resources/software.html), grab the Win32 installer
* Visual Studio 2012 — a free version called VS Express can be downloaded [here](http://www.microsoft.com/visualstudio/eng/downloads#d-express-windows-desktop)
* Qt 5.1 libraries — see section below

##Downloading Qt 5.1
Download the online installer [here](http://qt-project.org/downloads), for example I grabbed _Qt Online Installer for Windows 32-bit (13 MB)_

When it asks you to select components, ONLY select the following:
* Qt > Qt 5.1.0 > **msvc2010 32-bit OpenGL**

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
* An error will pop up saying project files may be invalid.  Click **OK**
* Click **Add Entry** in the upper right and enter **"CMAKE_PREFIX_PATH"** as Name, Type **Path** and a Value of **"C:/Qt/5.1.0/msvc2010_opengl;C:\Program Files (x86)\Microsoft SDKs\Windows\v7.1A\Lib"**  You may need to modify this for your Qt or Visual Studio configuration.
* Click **Configure**
* Once it says "Configuring done" at the bottom, click **Generate**
* Close CMake

##Building
* Open **C:\hifi-win32\hifi.sln** in Visual Studio 2012
* Ensure you are in the **Debug** build target (you should be by default)
* In the Solution Explorer, right click **interface** and click **Set as StartUp Project**
* Right click **interface** and click **Build**
* Once finished, the build log should say something similar to "Build: 13 succeeded, 0 failed, 0 up-to-date, 0 skipped"
* Before you can debug the program, you must copy the required DLLs to the debug folder
* Copy all the DLLs from **C:\hifi-master\externals\win32-dll\Debug** to **C:\hifi-win32\interface\Debug**
* Now you can run and debug "interface" through Visual Studio