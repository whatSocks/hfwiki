Very basic description of our javascript API so far.  

# My Avatar  

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

# Particles 
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
* VoxelDetail getVoxelAt(float x, float y, float z, float scale)
* void setVoxelNonDestructive(float x, float y, float z, float scale, uchar red, uchar green, uchar blue)
* void setVoxel(float x, float y, float z, float scale, uchar red, uchar green, uchar blue)
* void eraseVoxel(float x, float y, float z, float scale)

# Audio 
* Sound Sound(URL)
* playSound(Sound sound, AudioInjectorOptions injectorOptions)

# Math Helper functions 
Quaternion functions:
* quat Quat.multiply(const glm::quat& q1, const glm::quat& q2);
* Quat.fromVec3(const glm::vec3& vec3);
* quat Quat.fromPitchYawRoll(float pitch, float yaw, float roll);
* quat inverse(const glm::quat& q);
* vec3 getFront(const glm::quat& orientation);
* vec3 getRight(const glm::quat& orientation);
* vec3 getUp(const glm::quat& orientation);
* vec3 safeEulerAngles(const glm::quat& orientation);
* quat angleAxis(float angle, const glm::vec3& v);

Vector3 functions: 
* vec3 multiply(const glm::vec3& v1, const glm::vec3& v2);
* vec3 multiply(const glm::vec3& v1, float f);
* vec3 multiplyQbyV(const glm::quat& q, const glm::vec3& v);
* vec3 sum(const glm::vec3& v1, const glm::vec3& v2);
* vec3 subtract(const glm::vec3& v1, const glm::vec3& v2);
* float length(const glm::vec3& v);

# Camera Functions
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