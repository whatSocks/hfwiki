At a minimum you need to run a domain-server and multiple assignment-clients.  The domain-server is in charge of handing out simulation assignments and providing their IP addresses to connecting clients.  The assignment-server is currently a single executable that spawns copies of itself.  Each copy knows how to wear multiple hats (audio-mixer, avatar-mixer, voxel-server, particle-server, or metavoxel-server) and will wear whatever hat their domain-server assigns them.

## Mac
* Assuming a successful build in a fresh repo...
* In a terminal start the domain-server:
```
# navigate to the domain-server directory
cd ~/my-repo/build/domain-server/Debug/
# run the executable
./domain-server
```
* In a second terminal start the assignment-clients:
```
cd ~/my-repo/build/assignment-client/Debug/
mkdir resources
./assignment-client -n 5
```
## Linux
* Assuming a successful build in a fresh repo...
* In a terminal start the domain-server:
```
cd ~/my-repo/build/domain-server/
./domain-server
```
* In a second terminal start the assignment-clients:
```
cd ~/my-repo/build/assignment-client/
mkdir resources
./assignment-client -n 5
```
* In the interface client: File --> Go To Domain... --> 127.0.0.1

## Windows
* Assuming a successful build in a fresh repo...
* Click the start button and run cmd.exe (Command window):
```
cd <hifi_folder>/build/domain-server/Release
domain-server.exe
```
* In a second command window start the assignment-clients:
```
cd <hifi_folder>/build/assignment-client/Release
mkdir resources
assignment-client.exe -n 5
```
* In the interface client: File --> Go To Domain... --> 127.0.0.1 (localhost)
* Please note that currently the assignment clients still take a lot of CPU.
* Also note that at this moment only interfaces clients running on windows seem to be able to connect to a domain-server running on windows. Mac interface clients will crash the moment they arrive.

##General
* To run your own domain-server make sure port 40102 is open and forwarded to the machine running the domain-server.
