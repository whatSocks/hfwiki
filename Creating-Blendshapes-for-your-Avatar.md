In order to make your avatar expressive in Interface, you will need to create “Blendshapes” or “Shape Keys” depending on the 3D creation software you are using. Your avatar’s blendshapes will then be “rigged” from with Faceshift Studio and exported for you to use in Interface. 

## Maya

### Create your base 3D model 

The base model should have what ever expression you want your avatar to have by default -- when it is not receiving animation information from the depth camera/2D camera or when your face is in a neutral state.

![neutral face](https://s3-us-west-1.amazonaws.com/highfidelity-public/images/neutral.jpg) 


So, for example if your base model has it’s mouth open, when you are not smiling or your mouth is closed, your Avatar’s mouth will look open to other Avatars. It will also mean that if you open your mouth, you will be starting from a default open mouth position and your mouth will appear twice as open to other Avatars in Interface. 

Always "freeze transformation" and "delete history" on the base model before proceeding to blendshape, joints setup and paint weighting.

### Unwrap the UV 

Setup a texture for the 3D model. No one texture file can be larger than 1024x1024. Remember that the higher resolution the textures you use, the slower they will appear to other Avatar’s around you and possibly degrade the experience for others. 

Specularity and Ambient color are currently not supported but bump mapping is if a normal map texture is referenced. 

Textures that contain alpha information are supported in Interface, but not currently in Faceshift. 
Setup Joints 

Rename bones, paint weight, and parent any extra 3D object to the head joint. If you want to take advantage of Facshift’s Head Pose and Eye Tracking, you must create those joints and name them jointNeck, jointEyeLeft and jointEyeRight. 

### Create Blendshapes 

Create shapes for the eyes, mouth, brows etc. If you want to create a 1:1 mapping of shapes to map to Faceshifts, you will need to create shapes for:

* EyeBlink_L
* EyeBlink_R
* EyeSquint_L
* EyeSquint_R
* EyeDown_L
* EyeDown_R
* EyeIn_L
* EyeIn_R
* EyeOpen_L
* EyeOpen_R
* EyeOut_L
* EyeOut_R
* EyeUp_L
* EyeUp_R
* BrowsD_L
* BrowsD_R
* BrowsU_C
* BrowsU_L
* BrowsU_R
* JawFwd
* JawLeft
* JawOpen
* JawChew
* JawRight
* MouthLeft
* MouthRight
* MouthFrown_L
* MouthFrown_R
* MouthSmile_L
* MouthSmile_R
* MouthDimple_L
* MouthDimple_R
* LipsStretch_L
* LipsStretch_R
* LipsUpperClose
* LipsLowerClose
* LipsUpperUp
* LipsLowerDown
* LipsUpperOpen
* LipsLowerOpen
* LipsFunnel
* LipsPucker
* ChinLowerRaise
* ChinUpperRaise
* Sneer
* Puff
* CheekSquint_L
* CheekSquint_R

Ordering them exactly as shown above will make it easier to rig when you move to Faceshift. 

For a reference image of how these shapes should look, launch Faceshift studio, click the Training tab, click File/New Profile. On the left side of the window you will see all 48 shapes listed. Select one and the default model to the lists’ right will animate the desired modification for the blendshape.

### Before Exporting

Make sure all the blendshapes are in their original position (Location: X:0 Y:0 Z:0, Rotation: X:0° Y:0° Z:0°, Scale: X:1 Y:1 Z:1)
Delete all the blendshapes. This is necessary or all the shapes will get loaded into Faceshift when you import the fbx for rigging. 

Select the joints and all 3D objects and export them as a fbx binary. You many need to download the fbx plugin for your version of Maya. Do not embed the media when exporting. Make sure “Smooth Mesh” is selected. 

## Blender 

### Create your base 3D model 

The base model should have what ever expression you want your avatar to have by default -- when it is not receiving animation information from the depth camera/2D camera or when your face is in a neutral state. 

![neutral face](https://s3-us-west-1.amazonaws.com/highfidelity-public/images/neutral.jpg)


So, for example if your base model has it’s mouth open, when you are not smiling or your mouth is closed, your Avatar’s mouth will look open to other Avatars. It will also mean that if you open your mouth, you will be starting from a default open mouth position and your mouth will appear twice as open to other Avatars in Interface. 

Always "freeze transformation" and "delete history" on the base model before proceeding to blendshape, joints setup and paint weighting.

### Unwrap the UV 

Setup a texture for the 3D model. No one texture file can be larger than 1024x1024. Remember that the higher resolution the textures you use, the slower they will appear to other Avatar’s around you and possibly degrade the experience for others. 

Specularity and Ambient color are currently not supported but bump mapping is if a normal map texture is referenced. 

Textures that contain alpha information are supported in Interface, but not currently in Faceshift. 
Setup Armature 

Rename bones, paint weight, and parent any extra 3D object to the armature. If you want to take advantage of Facshift’s Head Pose and Eye Tracking, you must create those joints and name them jointNeck, jointEyeLeft and jointEyeRight. 

### Create shape keys (blendshapes) 

Create shapes for the eyes, mouth, brows etc. If you want to create a 1:1 mapping of shapes to map to Faceshifts, you will need to create shapes for:

* EyeBlink_L
* EyeBlink_R
* EyeSquint_L
* EyeSquint_R
* EyeDown_L
* EyeDown_R
* EyeIn_L
* EyeIn_R
* EyeOpen_L
* EyeOpen_R
* EyeOut_L
* EyeOut_R
* EyeUp_L
* EyeUp_R
* BrowsD_L
* BrowsD_R
* BrowsU_C
* BrowsU_L
* BrowsU_R
* JawFwd
* JawLeft
* JawOpen
* JawChew
* JawRight
* MouthLeft
* MouthRight
* MouthFrown_L
* MouthFrown_R
* MouthSmile_L
* MouthSmile_R
* MouthDimple_L
* MouthDimple_R
* LipsStretch_L
* LipsStretch_R
* LipsUpperClose
* LipsLowerClose
* LipsUpperUp
* LipsLowerDown
* LipsUpperOpen
* LipsLowerOpen
* LipsFunnel
* LipsPucker
* ChinLowerRaise
* ChinUpperRaise
* Sneer
* Puff
* CheekSquint_L
* CheekSquint_R

For a reference image of how these shapes should look, launch Faceshift studio, click the Training tab, click File/New Profile. On the left side of the window you will see all 48 shapes listed. Select one and the default model to the lists’ right will animate the desired modification for the blendshape.

### Before exporting

Make sure all the blendshapes are in their original position (Location: X:0 Y:0 Z:0, Rotation: X:0° Y:0° Z:0°, Scale: X:1 Y:1 Z:1)
Delete all the blendshapes. This is necessary or all the shapes will get loaded into Faceshift when you import the fbx for rigging. 

Select the Armature and all 3D objects and export them as a fbx file. You many need to download the fbx plugin for your version of Blender. You can use the default fbx export settings. 


