_A collection of notes for new users_

## OS X: Revealing the Library directory
Snapshots and Logs are saved to _Users>Username>Library>Application Support>Interface_

Recent versions of OSX hide the library folder by default, and it must be enabled through the terminal with `"chflags nohidden ~/Library/“`

## OS X: Setting up FaceShift
Load fsHighFidelity

If multiple sensor drivers are available, choose Openni 2.0 Sensor Plugin. 

Follow the instructions to run through the training, build, and save your profile.

Enable Network Streaming under Tracking>Network>Faceshift Network

Enable Faceshift (TCP) in Interface under Developer>Avatar Options

## OS X: Setting up the Razer Hydra

Download the Sixense SDK from http://sixense.com/hardware/sixensesdk

Copy lib/osx_x64/release_dll/libsixense_x64.dylib to Applications/Interface/Contents/Frameworks 

## OS X: Setting up the Oculus Rift

## OS X: "Interface cannot be opened because of a problem" after update to Build 148

Build 148 won't run without the Sixense SDK installed in the Frameworks folder as described above.