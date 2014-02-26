# Avatar Properties 

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

Callback Functions: 
* keyPressEvent(KeyEvent event)
* keyReleaseEvent(KeyEvent event)
* mouseMoveEvent(MouseEvent event)
* mousePressEvent(MouseEvent event)
* mouseReleaseEvent(MouseEvent event);
* touchBeginEvent(TouchEvent event);
* touchEndEvent(TouchEvent event);
* wheelEvent(WheelEvent event);

