_A collection of notes for new users_

# Basic Features
## Snapshots
Use Command-S or Control-S to take a Snapshot, it will save to _Users>Username>Library>Application Support>Interface_ on Mac.
## Key tips and useful shortcuts
* Use 'Tab' to toggle the voxel editor on and off.
* Use '0' to create a voxel.
* To see all the scripts that are running go to File>Running Scipts . To add additional scripts or run your own, go [here](https://alphas.highfidelity.io/t/fun-and-useful-js-scripts/154) to learn more. 
* If you create a Voxel and want to undo Ctrl+Z works.

# Basic Setup
## OS X: Revealing the Library directory
Snapshots and Logs are saved to _Users>Username>Library>Application Support>Interface_

Recent versions of OSX hide the Library directory/folder by default, and it must be enabled through the Terminal with this command: `"chflags nohidden ~/Library/“`

If you prefer a less permanent way to go to the User Library folder:
Finder --> Go --> press the Alt key --> then you can select the Library folder

## OS X: Setting up FaceShift
1. Load fsHighFidelity
2. If multiple sensor drivers are available, choose Openni 2.0 Sensor Plugin. 
3. Follow the instructions to run through the training, build, and save your profile.
4. Enable Network Streaming under Tracking>Network>Faceshift Network
5. Enable Faceshift (TCP) in Interface under Developer>Avatar Options

## OS X: Setting up the Razer Hydra
1. Download the Sixense SDK from http://sixense.com/hardware/sixensesdk
2. Copy lib/osx_x64/release_dll/libsixense_x64.dylib to Applications/Interface/Contents/Frameworks 

## OS X: Setting up the Oculus Rift
_We're currently working on adding the needed resources to the installer to enable Rift mode._

# Troubleshooting
## OS X: "Interface cannot be opened because of a problem" after update to Build 148
Build 148 won't run without the Sixense SDK installed in the Frameworks folder as described above under "Setting up the Razer Hydra".