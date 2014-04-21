The following are a set of load and scaling tests that should be run against the Voxel, Particle, and other Octree servers when testing scale.

* **Steady State Load** - Using the "seeingVoxelsExample.js" you can run multiple assignment client instances (50-100 instances) that connect to a voxel server, and constantly change their view to test voxel server load.

* **Burst connect/disconnect** - Using "testingVoxelViewerRestart.js" you can run multiple assignment client instances (50-100) which will connect and then quickly/randomly disconnect from the server.

* **Voxel-server restart while steady state clients connected** - Connect several clients to the server using seeingVoxelsExample.js, then using the domain-server status page, "restart" the voxel-server. You should see the server properly shut down all of it's sending threads, then shutdown, then restart, then have all the connected clients reconnect.

* **Voxel-server restart while burst connect/disconnect** - run several assignment client instances with testingVoxelViewerRestart.js, then while clients are connecting/disconnecting restart the voxel-server from the domain status page.

* **domain-server restart while steady state clients connected** - Connect several clients to the server using seeingVoxelsExample.js, then restart (or stop) the domain-server. Since the domain-server is shutting down, the voxel-server will lose it's assignment (no domain-server means no assignment). The voxel-server should detect this case and gracefully shutdown. You should see the server properly shut down all of it's sending threads, then shutdown, then wait for a new assignment. Restarting the domain-server should see the voxel-server restart, and begin serving content to the assignment-clients.

* **domain-server restart while burst connect/disconnect** - run several assignment client instances with testingVoxelViewerRestart.js, then while clients are connecting/disconnecting stop or restart the domain-server. Since the domain-server is shutting down, the voxel-server will lose it's assignment (no domain-server means no assignment). The voxel-server should detect this case and gracefully shutdown. You should see the server properly shut down all of it's sending threads, then shutdown, then wait for a new assignment. Restarting the domain-server should see the voxel-server restart, and begin serving content to the assignment-clients.

