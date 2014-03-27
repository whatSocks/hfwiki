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