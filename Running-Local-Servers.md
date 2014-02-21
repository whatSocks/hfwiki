## Linux
* Assuming a successful build in a fresh repo...
* In a terminal start the domain-server:
```
cd ~/my-repo/domain-server/
ln -sf ../build/domain-server/domain-server ./
./domain-server
```
* In a second terminal start the assignment-clients:
```
cd ~/my-repo/assignment-client/
mkdir resources
ln -sf ../build/assignment-client/assignment-client ./
./assignment-client -n 5
```
* In the interface client: File --> Go To Domain... --> 127.0.0.1