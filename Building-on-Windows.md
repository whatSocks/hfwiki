##Requirements
* git or GitHub
* CMake — download [here](http://www.cmake.org/cmake/resources/software.html), grab the Win32 installer
* Visual Studio C++ 2010 Express for Desktop — a free version can be downloaded [here](http://www.visualstudio.com/en-us/downloads#d-2010-express)
* Windows SDK 7.1/.NET 4 Framework - http://www.microsoft.com/en-us/download/details.aspx?id=8279
* VS2010 SP1 - http://www.microsoft.com/en-us/download/details.aspx?id=4422
* Qt 5.2.0 - msvc2010_opengl version - see below
* zLib for windows - Complete Package except sources [here (http://gnuwin32.sourceforge.net/downlinks/zlib.php)


##Downloading Qt 5.2
You can use the online installer, or the offline installer. If you use the offline installer, be sure to select the "OpenGL" version.
* Download the online installer [here](http://qt-project.org/downloads), for example I grabbed _Qt Online Installer for Windows 32-bit (13 MB)_
    * When it asks you to select components, ONLY select the following:
        * Qt > Qt 5.2.0 > **msvc2010 32-bit OpenGL**

* Download the offline installer [here] (http://download.qt-project.org/official_releases/qt/5.2/5.2.0/qt-windows-opensource-5.2.0-msvc2010_opengl-x86-offline.exe)

##Configure Qt 5.2
Once Qt is installed, you need to manually configure the following:
* Make sure the Qt runtime DLLs are loadable (You could add the Qt\5.2.0\msvc2010_opengl\bin\ directory to your path.) - You must do this before you attempt to build because some tools for the build depend on Qt.
* Set the QT_CMAKE_PREFIX_PATH environment variable to your Qt\5.2.0\msvc2010_opengl directory

##Configure zLib
NOTE: zLib should configure itself correctly on install. However, sometimes zLib doesn't properly detect system components and fails to configure itself correctly. When it fails, it will not correctly set the #if HAVE_UNISTD_H at line 287 of zconf.h to #if 0... if it fails, you're build will have errors in the voxels target. You can correct this by setting the #if to 0 instead of 1, since Windows does not have unistd.h.

##Getting the source
The easiest way to grab the source is by cloning the repository from https://github.com/worklist/hifi. Or by downloading a zip of the entire repository from [here](https://github.com/worklist/hifi) and clicking **Download ZIP** which is at the bottom of the right toolbar.

This guide assumes you extract the source  or clone to **C:\Development\HiFi\hifi**

##Configuring, Running cmake
* cd **C:\Development\Hifi\hifi\**
* mkdir build
* cd build
* cmake .. -G "Visual Studio 10" -Wno-dev 

##Building
* Open **C:\Development\HiFi\hifi\build\hifi.sln** in Visual Studio 2010
* Ensure you are in the **Debug** build target (you should be by default)
* Click the "Build Solution" button on your tool bar or Debug menu (or press F7)
* Once finished, the build log should say something similar to "Build: 20 succeeded, 0 failed, 0 up-to-date, 1 skipped"

##Preparing to run "Interface"
We don't currently have a Windows installer, so before running Interface, you will need to ensure that all required resources are loadable. 

* In particular you must make sure all required DLLs are loadable. You can accomplish this in several different ways. 

    One technique is described below:
    * create a directory C:\Development\HiFi\windows-dlls
    * add C:\Development\HiFi\windows-dlls to your path
    * copy the following files into this directory: zlib1.dll, freeglut.dll, glew32.dll

    Note: you will find freeglut.dll and glew32.dll in the C:\Development\HiFi\hifi\interface\external tree. You will need to find the zlib1.dll from where you installed zLib.

* You also need to make the interface\resources directory available to interface.exe. To do that, copy the contents of C:\Development\HiFi\hifi\interface\resources to C:\Development\HiFi\build\interface\Debug\resources or if you're building a Release build to C:\Development\HiFi\build\interface\Release\resources

##Running "Interface"
If you need to debug Interface, you can run interface from within Visual Studio (see more below). You can also run Interface by launching it from command line or File Explorer from **C:\Development\HiFi\hifi\build\interface\Debug\interface.exe**

##Debugging "Interface"
* In the Solution Explorer, right click **interface** and click **Set as StartUp Project**
* Now you can run and debug "interface" through Visual Studio