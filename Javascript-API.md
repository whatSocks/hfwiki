High Fidelity uses Javascript as the language for scriptable in-world objects, as well as extensions to the capability of the Interface client.  In the File menu of the interface, under scripts, you can open and run javascript extensions, and those scripts that are running will persist across sessions.  Additionally, you can deploy javascript code by entering it as an 'assignment', which will be deployed to the first available assignment client, which is a dedicated machine/device that will connect to the domain of your choice and do something.  The various function calls and properties for things that you can do from within these Javascript files are listed here. 

# Avatar functions  
If you are running on the interface client, the 'Avatar' is you, and is called 'MyAvatar'.  If you are running an assignment that is not on an interactive client, the avatar object is called 'Avatar'.  

* Vec3 MyAvatar.position 
* float MyAvatar.scale 
* Vec3 MyAvatar.handPosition 
* float MyAvatar.bodyYaw
* float MyAvatar.bodyPitch
* float MyAvatar.bodyRoll
* Quat MyAvatar.orientation 
* Quat MyAvatar.headOrientation
* float MyAvatar.headPitch 
* float MyAvatar.audioLoudness 
* float MyAvatar.audioAverageLoudness 
* String MyAvatar.faceModelURL 
* String MyAvatar.skeletonModelURL
* String MyAvatar.billboardURL 
* bool MyAvatar.shouldRenderLocally 

### Animation Of Joints 
Use these functions to get and set the rotations of an avatar's joints.  

stringList MyAvatar.getJointNames() 
This function will return a list of names of joints in the avatar you are wearing (obviously we are going to need to pick some sort of typical standard so that animations can be mapped to avatars) 

MyAvatar.setJointData(string jointName, Quat rotation)     set a joint to a new position
MyAvatar.clearJointData("joint_R_hip")  Return the joint to the default position

Note that right now, joint positions are updated every frame whenever they are moved away from the default position.  More work to come on using known last state and delta vectors to more efficiently encode. 

# Particles
Particles are moving/moveable objects that are stored in an octree server and transmitted to clients and interactive agents that are near enough to see them.  Particles can have model files attached to them, changing their appearance.  
 
Callback Functions: 
* particleCollisionWithVoxel(ParticleID particleID, VoxelDetail voxel);
* particleCollisionWithParticle(ParticleID idA, ParticleID idB);

Functions:
* ParticleID addParticle(ParticleProperties properties)
* ParticleID identifyParticle(ParticleID particleID)
* ParticleProperties getParticleProperties(ParticleID particleID)
* ParticleID editParticle(ParticleID particleID, ParticleProperties properties);
* deleteParticle(ParticleID particleID)
* ParticleID findClosestParticle(vec3 center, float radius)
* QVector<ParticleID> findParticles(vec3 center, float radius)

# Voxels 
Voxels are the space filling 'blocks' consisting of colors and other meta-values that you see around you in the virtual world.  Voxels can be created, deleted, and changed by interactive programs.  

* VoxelDetail getVoxelAt(float x, float y, float z, float scale)
* void setVoxelNonDestructive(float x, float y, float z, float scale, uchar red, uchar green, uchar blue)
* void setVoxel(float x, float y, float z, float scale, uchar red, uchar green, uchar blue)
* void eraseVoxel(float x, float y, float z, float scale)

# Clipboard functions for Voxels 
Clipboard.  -->
* cutVoxel(VoxelDetail sourceVoxel);
* cutVoxel(float x, float y, float z, float s);
* copyVoxel(VoxelDetail sourceVoxel);
* copyVoxel(float x, float y, float z, float s);
* pasteVoxel(VoxelDetail destinationVoxel);
* pasteVoxel(float x, float y, float z, float s);
* deleteVoxel(const VoxelDetail& sourceVoxel);
* deleteVoxel(float x, float y, float z, float s);
* exportVoxel(const VoxelDetail& sourceVoxel);
* exportVoxel(float x, float y, float z, float s);
* importVoxels();
* nudgeVoxel(VoxelDetail sourceVoxel, vec3 nudgeVec);
* nudgeVoxel(float x, float y, float z, float s, vec3 nudgeVec);

# Audio
Audio is continuously mixed in 3D and re-transmitted to interactive clients by the 'Audio Mixer' assignment clients.  Audio can be injected into the world, using these commands. 

* Sound Sound(URL)
* playSound(Sound sound, AudioInjectorOptions injectorOptions)

# Math Helper functions 
Quaternion and Vector functions are included in the javascript API to make it easier to build content. 

Quaternion functions:
* quat Quat.multiply(const glm::quat& q1, const glm::quat& q2);
* Quat.fromVec3(const glm::vec3& vec3);
* quat Quat.fromPitchYawRoll(float pitch, float yaw, float roll);
* quat inverse(const glm::quat& q);
* vec3 getFront(const glm::quat& orientation);
* vec3 getRight(const glm::quat& orientation);
* vec3 getUp(const glm::quat& orientation);
* vec3 safeEulerAngles(const glm::quat& orientation);
* quat angleAxis(float angleInDegrees, const glm::vec3& v);

Vector3 functions: 
* vec3 multiply(const glm::vec3& v1, const glm::vec3& v2);
* vec3 multiply(const glm::vec3& v1, float f);
* vec3 multiplyQbyV(const glm::quat& q, const glm::vec3& v);
* vec3 sum(const glm::vec3& v1, const glm::vec3& v2);
* vec3 subtract(const glm::vec3& v1, const glm::vec3& v2);
* float length(const glm::vec3& v);

# Camera Functions
The camera is the viewport for an interactive client (Interface).  You can move the camera (independent of the avatar) through the javascript calls here.  

Addressable as Camera.foo():

* String getMode()
* setMode(string)
* setPosition(vec3) 
* vec3 getPosition() 
* setOrientation(quat) 
* quat getOrientation() 

// The following only work on independent cameras
// one time change to what the camera is looking at
* lookAt(vec3)
// fix what the camera is looking at, and keep the camera looking at this even if position changes
* keepLookingAt(vec3)
// stops the keep looking at feature, doesn't change what's being looked at, but will stop camera from
// continuing to update it's orientation to keep looking at the item
* void stopLooking() 

// Pick ray for point on screen
* PickRay computePickRay(x, y)

# Mouse, Keyboard and 3D Motion Controllers 
The mouse as well as 3D controllers like the Razer Hydra can be accessed from these functions. 

Callback Functions you can register: 
ex: Controller.mouseMoveEvent.connect(mouseMoveEvent); 
* keyPressEvent(KeyEvent event)
* keyReleaseEvent(KeyEvent event)
* mouseMoveEvent(MouseEvent event)
* mousePressEvent(MouseEvent event)
* mouseReleaseEvent(MouseEvent event);
* touchBeginEvent(TouchEvent event);
* touchEndEvent(TouchEvent event);
* wheelEvent(WheelEvent event);

Functions: 
* bool isPrimaryButtonPressed()
* vec2 getPrimaryJoystickPosition()
* int getNumberOfButtons() 
* isButtonPressed(int buttonIndex) 
* int getNumberOfTriggers()
* float getTriggerValue(int triggerIndex)
* int getNumberOfJoysticks()
* vec2 getJoystickPosition(int joystickIndex)
* int getNumberOfSpatialControls()
* vec3 getSpatialControlPosition(int controlIndex)
* vec3 getSpatialControlVelocity(int controlIndex)
* vec3 getSpatialControlNormal(int controlIndex)
* quat getSpatialControlRawRotation(int controlIndex)
* void captureKeyEvents(const KeyEvent& event)
* void releaseKeyEvents(const KeyEvent& event)
* void captureMouseEvents()
* void releaseMouseEvents()
* void captureTouchEvents()
* void releaseTouchEvents()
* void captureWheelEvents() 
* void releaseWheelEvents()
* void captureJoystick(int joystickIndex)
* void releaseJoystick(int joystickIndex)
* vec2 getViewportDimensions() 
