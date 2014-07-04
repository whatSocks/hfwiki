High Fidelity uses Javascript as the language for scriptable in-world objects, as well as extensions to the capability of the Interface client.  In the File menu of the interface, under scripts, you can open and run javascript extensions, and those scripts that are running will persist across sessions.  Additionally, you can deploy javascript code by entering it as an 'assignment', which will be deployed to the first available assignment client, which is a dedicated machine/device that will connect to the domain of your choice and do something.  The various function calls and properties for things that you can do from within these Javascript files are listed here. 

# Avatar  
If you are running on the interface client, the 'Avatar' is you, and is called 'MyAvatar'.  If you are running an assignment that is not on an interactive client, the avatar object is called 'Avatar'.  

### Properties:

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
* String MyAvatar.displayName
* String MyAvatar.faceModelURL 
* String MyAvatar.skeletonModelURL
* String MyAvatar.billboardURL 
* array MyAvatar.jointNames
* String MyAvatar.sessionUUID
* number MyAvatar.collisionGroups
* bool MyAvatar.shouldRenderLocally 
* number MyAvatar.motionBehaviors
* Vec3 MyAvatar.gravity


### Functions:

* Vec3 MyAvatar.getTargetAvatarPosition()
The position of the avatar that you are looking at.
* MyAvatar.updateCollisionGroups()
* MyAvatar.goHome() 
* MyAvatar.increaseSize()
* MyAvatar.decreaseSize()
* MyAvatar.resetSize()
* MyAvatar.updateLocationInDataServer()
* MyAvatar.addThrust(Vec3 trust)
* Vec3 MyAvatar.getThrust()
* MyAvatar.setThrust(Vec3 newTrust)
* MyAvatar.updateMotionBehaviorsFromMenu()


### Callback Functions:

* MyAvatar.collisionWithAvatar(string myUUID, string theirUUID, object collisionInfo)

### Attachments

* MyAvatar.attach(string attachmentURL, string jointName, Vec3 translation,Quat rotation, float scale, bool allowDuplicates, bool useSaved)
* MyAvatar.attach(string attachmentURL, string jointName, Vec3 translation,Quat rotation, float scale, bool allowDuplicates)
* MyAvatar.attach(string attachmentURL, string jointName, Vec3 translation,Quat rotation, float scale)
* MyAvatar.attach(string attachmentURL, string jointName, Vec3 translation,Quat rotation)
* MyAvatar.attach(string attachmentURL, string jointName, Vec3 translation)
* MyAvatar.attach(string attachmentURL, string jointName)
* MyAvatar.attach(string attachmentURL)
* MyAvatar.detachOne(string attachmentURL, string jointName)
* MyAvatar.detachOne(string attachmentURL)
* MyAvatar.detachAll(string attachmentURL, string jointName)
* MyAvatar.detachAll(string attachmentURL)

### Animation Of Joints 
Use these functions to get and set the rotations of an avatar's joints.  

* stringList MyAvatar.getJointNames() 
This function will return a list of names of joints in the avatar you are wearing (obviously we are going to need to pick some sort of typical standard so that animations can be mapped to avatars) 

* MyAvatar.setJointData(string jointName, Quat rotation)     
Set a joint to a new position
* Quat MyAvatar.getJointRotation(string jointName)
Current joint position
* MyAvatar.clearJointData("joint_R_hip")  
Return a joint to the default position

Note that right now, joint positions are updated every frame whenever they are moved away from the default position.  More work to come on using known last state and delta vectors to more efficiently encode. 

# Particles
Particles are moving/moveable objects that are stored in an octree server and transmitted to clients and interactive agents that are near enough to see them.  Particles can have model files attached to them, changing their appearance.  
 
### Callback Functions: 
* particleCollisionWithVoxel(ParticleID particleID, VoxelDetail voxel);
* particleCollisionWithParticle(ParticleID idA, ParticleID idB);

### Functions:
* ParticleID addParticle(ParticleProperties properties)
* ParticleID identifyParticle(ParticleID particleID)
* ParticleProperties getParticleProperties(ParticleID particleID)
* ParticleID editParticle(ParticleID particleID, ParticleProperties properties);
* deleteParticle(ParticleID particleID)
* ParticleID findClosestParticle(vec3 center, float radius)
* QVector<ParticleID> findParticles(vec3 center, float radius)

### ParticleProperties

* Vec3 ParticleProperties.position
* {red:, green:, blue:} ParticleProperties.color
* float ParticleProperties.radius
* Vec3 ParticleProperties.velocity
* Vec3 ParticleProperties.gravity
* float ParticleProperties.damping
* float ParticleProperties.lifetime
* string ParticleProperties.script
* bool ParticleProperties.inHand
* bool ParticleProperties.shouldDie
* string ParticleProperties.modelURL
* float ParticleProperties.modelScale
* Vec3 ParticleProperties.modelTranslation
* Quat ParticleProperties.modelRotation


# Voxels 
Voxels are the space filling 'blocks' consisting of colors and other meta-values that you see around you in the virtual world.  Voxels can be created, deleted, and changed by interactive programs.  

### Functions:
* number getTreeScale() provide the world scale
* VoxelDetail getVoxelAt(float x, float y, float z, float scale) checks the local voxel tree for a voxel at the specified location and scale

_"Voxels.getVoxelAt(0, 0, 0, 1.0).red" would return the value of red from the voxel at the coordinates 0,0,0._
* void setVoxelNonDestructive(float x, float y, float z, float scale, uchar red, uchar green, uchar blue) queues the creation of a voxel which will be sent by calling process on the PacketSender
* void setVoxel(float x, float y, float z, float scale, uchar red, uchar green, uchar blue) queues the destructive creation of a voxel which will be sent by calling process on the PacketSender
* void eraseVoxel(float x, float y, float z, float scale) queues the deletion of a voxel, sent by calling process on the PacketSender
* RayToVoxelIntersectionResult findRayIntersection(PickRay ray) If the scripting context has visible voxels, this will determine a ray intersection, the results may be inaccurate if the engine is unable to access the visible voxels, in which case result.accurate will be false.
* RayToVoxelIntersectionResult findRayIntersectionBlocking(PickRay ray) If the scripting context has visible voxels, this will determine a ray intersection, and will block in order to return an accurate result
* Vec3 getFaceVector(string face) returns a voxel space axis aligned vector for the face, useful in doing voxel math
* VoxelDetail getVoxelEnclosingPoint(Vec3 point) checks the local voxel tree for the smallest voxel enclosing the point

### VoxelDetail

* float x
* float y
* float z
* float s
* number red
* number green
* number blue

### RayToVoxelIntersectionResult

* bool intersects
* bool accurate
* VoxelDetail voxel
* float distance
* string face  (possible values MIN_X_FACE, MAX_X_FACE, MIN_Y_FACE, MAX_Y_FACE, MIN_Z_FACE, MAX_Z_FACE, UNKNOWN_FACE)
* Vec3 intersection

# Clipboard functions for Voxels 
Clipboard.

### Functions:

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

### Callback Functions:

* readyToImport()

# Audio
Audio is continuously mixed in 3D and re-transmitted to interactive clients by the 'Audio Mixer' assignment clients.  Audio can be injected into the world, using these commands. 

* Sound Sound(URL)
* AudioInjector playSound(Sound sound, AudioInjectorOptions injectorOptions)
* AudioInjector playSound(Sound sound)
* stopInjector(AudioInjector injector)
* isInjectorPlaying(AudioInjector injector)
* startDrumSound(float volume,float frequence, float duration, float decay, AudioInjectorOptions injectorOptions)
* startDrumSound(float volume,float frequence, float duration, float decay)

### Sound

* bool hasDownloaded

### AudioInjectorOptions

* Vec3 position
* float volume
* bool loop

### AudioInjector

Functions:
* void injectAudio()
* void stop()

Callback Functions:
* void finished()
 
### Timer functions
You can set a single shot or repeating timer event, in the following way:

var one_timer = Script.setTimeout(function() { print("One time timer fired!"); }, 10000);

var multiple_timer = Script.setInterval(function() { print("Repeating timer fired!"); }, 1000);

// this would stop a scheduled single shot timer
Script.clearTimeout(one_timer);

// this stops the repeating timer
Script.clearInterval(multiple_timer);

# Math Helper functions 
Quaternion and Vector functions are included in the javascript API to make it easier to build content. 

Quaternion functions:
* quat Quat.multiply(const glm::quat& q1, const glm::quat& q2);
* quat Quat.fromVec3Degrees(const glm::vec3& vec3);
* quat Quat.fromVec3Radians(const glm::vec3& vec3);
* quat Quat.fromPitchYawRollDegrees(float pitch, float yaw, float roll);
* quat Quat.fromPitchYawRollRadians(float pitch, float yaw, float roll)
* quat inverse(const glm::quat& q);
* vec3 getFront(const glm::quat& orientation);
* vec3 getRight(const glm::quat& orientation);
* vec3 getUp(const glm::quat& orientation);
* vec3 safeEulerAngles(const glm::quat& orientation);
* quat angleAxis(float angleInDegrees, const glm::vec3& v);
* quat mix( quat q1, quat q2, float alpha);
* void print(string lable, quat q);

Vector3 functions: 
* vec3 cross(vec3 v1, vec3 v2);
* float dot(Vec3 v1, vec3 v2);
* vec3 multiply(const glm::vec3& v1, float f);
* vec3 multiplyQbyV(const glm::quat& q, const glm::vec3& v);
* vec3 sum(const glm::vec3& v1, const glm::vec3& v2);
* vec3 subtract(const glm::vec3& v1, const glm::vec3& v2);
* float length(const glm::vec3& v);
* float distance(Vec3 v1, Vec3 v2);
* Vec3 normalize( Vec3 v);
* void print( string lable, Vec3 v);

# Camera Functions
The camera is the viewport for an interactive client (Interface).  You can move the camera (independent of the avatar) through the javascript calls here.  

Addressable as Camera.foo():

* String getMode()
* setMode(string)
* setPosition(vec3) 
* vec3 getPosition() 
* setOrientation(quat) 
* quat getOrientation() 

The following only work on independent cameras.
* lookAt(vec3) One time change to what the camera is looking at.
* keepLookingAt(vec3) Fix what the camera is looking at, and keep the camera looking at this even if position changes.
* void stopLooking() Stops the keep looking at feature, doesn't change what's being looked at, but will stop camera from continuing to update its orientation to keep looking at the item.
* PickRay computePickRay(x, y) Pick ray for point on screen

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
* touchUpdateEvent(TouchEvent event);
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

# Window

* innerWidth
* innerHeight

### Functions:
* alert(string message)
* alert()
* confirm(string message)
* confirm()
* prompt(string message, string defaultText)
* prompt(string message)
* prompt()
* browse(string title, string directory, string nameFilter)
* browse(string title, string directory)
* browse(string title)
* browse()

# Settings

### Functions:
* getValue(string setting)
* getValue(string setting, string defaultValue)
* setValue(string setting, string value)

# Menu

### Callback Functions:
* menuItemEvent(string menuItem)

### Functions:
* addMenu(string menuName)
* removeMenu(string menuName)
* addSeparator(string menuName, string separatorName)
* removeSeparator(string menuName, string separatorName)
* addMenuItem (MenuItemProperties properties)
* addMenuItem(string menuName, string menuItem, string shortcutKey)
* addMenuItem(string menuName, string menuItem)
* removeMenuItem(string menuName, string menuItem)
* isOptionChecked(string menuOption)
* setIsOptionChecked(string menuOption, bool isChecked)

# location
NOTE: location without capital L

* href
* protocol
* hostname
* pathname

### Functions:
* assign(string url)

# AudioDevice

### Functions:
* setInputDevice(string deviceName)
* setOutputDevice(string deviceName)
* string getInputDevice()
* string getOutputDevice()
* string getDefaultInputDevice()
* string getDefaultOutputDevice()
* StringList getInputDevices()
* StringList getOutputDevices()
* float getInputVolume()
* setInputVolume(float volume)
