A .fst file is just a text file that gives us information on the model, its textures, blendshape mappings and skeleton mappings. Below is an example of our default avatar's head .fst file. 

faceshift target mapping file<br>
name=defaultAvatar_head<br>
filename= defaultAvatar/defaultAvatar_head.fbx<br>
texdir= defaultAvatar<br>
scale=80<br>
lod = defaultAvatar/defaultAvatar_head_lod40.fbx = 5<br>
lod = defaultAvatar/defaultAvatar_head_lod60.fbx = 10<br>
lod = defaultAvatar/defaultAvatar_head_lod80.fbx = 20<br>
joint = jointNeck = jointNeck<br>
bs = BrowsD_L = Leye1.BrowsD_L = 1<br>
bs = BrowsD_R = Reye1.BrowsD_R = 1<br>
bs = CheekSquint_L = Leye1.CheekSquint_L = 1<br>
bs = CheekSquint_R = Reye1.CheekSquint_R = 1<br>
bs = EyeBlink_L = Leye1.EyeBlink_L = 1<br>
bs = EyeBlink_R = Reye1.EyeBlink_R = 1<br>
bs = EyeDown_L = Leye1.EyeDown_L = 1<br>
bs = EyeDown_R = Reye1.EyeDown_R = 1<br>
bs = EyeIn_L = Leye1.EyeIn_L = 1<br>
bs = EyeIn_R = Reye1.EyeIn_R = 1<br>
bs = EyeOpen_L = Leye1.EyeOpen_L = 1<br>
bs = EyeOpen_R = Reye1.EyeOpen_R = 1<br>
bs = EyeOut_L = Leye1.EyeOut_L = 1<br>
bs = EyeOut_R = Reye1.EyeOut_R = 1<br>
bs = EyeUp_L = Leye1.EyeUp_L = 1<br>
bs = EyeUp_R = Reye1.EyeUp_R = 1<br>
bs = JawOpen = Mouth.JawOpen = 1<br>
bs = LipsFunnel = Mouth.LipsFunnel = 1<br>
bs = LipsLowerDown = Mouth.LipsLowerDown = 1<br>
bs = LipsPucker = Mouth.LipsPucker = 1<br>
bs = LipsStretch_L = Mouth.LipsStretch_L = 1<br>
bs = LipsStretch_R = Mouth.LipsStretch_R = 1<br>
bs = LipsUpperUp = Mouth.LipsUpperUp = 1<br>
bs = MouthDimple_L = Mouth.MouthDimple_L = 1<br>
bs = MouthDimple_R = Mouth.MouthDimple_R = 1<br>
bs = MouthFrown_L = Mouth.MouthFrown_L = 1<br>
bs = MouthFrown_R = Mouth.MouthFrown_R = 1<br>
bs = MouthLeft = Mouth.MouthLeft = 1<br>
bs = MouthRight = Mouth.MouthRight = 1<br>
bs = MouthSmile_L = Mouth.MouthSmile_L = 1<br>
bs = MouthSmile_R = Mouth.MouthSmile_R = 1<br>
bs = Puff = Mouth.Puff = 1<br>
bs = Sneer = Mouth.Sneer = 1<br>


The information at the top of this file specifies the name (name) of the avatar and where the .fbx file (filename) and texture files (texdir) can be found. It also specifies the scale (scale) of the model. If after importing your model you find it to be too small or too large. You should adjust the scale and reupload the fst file. If created together, the head and body models' scale should be the same in each .fst file. 

Below the model name are the Level of Detail mappings. LOD's are reduced (in polygons) versions for your highest resolution model. These LOD's are shown to others when they are at the specified distances listed in the LOD . So for example:
 
lod = defaultAvatar/defaultAvatar_Head_lod40.fbx = 5

means that when someone is five meters from you and looking at you, they will see defaultAvatar_head_lod40.fbx. We do this to keep the performance high for everyone. If you don't create and specify LOD files and performance is low for people, you will automatically be shown as a 'billboard', an auto generated 64x64 .png file, to nearby people to protect their framerate. 

We suggest creating three LOD's with 40, 60, and 80 percent reductions or decimations depending on which modeling tool you are using and then mapping them to 5, 10, and 20 meters respectively. 

The next section of the file shows the blendshape mappings. For more information on blendshapes, refer to the [Creating Blendshapes for your Avatar](https://github.com/highfidelity/hifi/wiki/Creating-Blendshapes-for-your-Avatar) document. 
As you can see from the example the blendshape (bs) is mapped to the Shape name and given a weight where "0" is off and "1" is 100%. 

These mapping and the fst file can be generated in two ways.

1. Using Faceshift's client. If you are using the faceshift client to rig your avatar head and an approved 3D camera to drive facial expressions, refer to the Exporting your Rigged Avatar document. 

1. Manually. If you don't have faceshift and are just using the default 2D camera face tracking option, just create a text file and save as .fst or change the file name after saving. Make sure you specify which directories the fbx and texture files are.