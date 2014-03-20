## Requirements

Faceshift has the following requirements and limitations for importing:
1. Blendshapes: fsStudio currently only support blendshapes to map the blendshapes of the actor face to your imported character. The blendshapes do not need to correspond one-to-one, instead, you will need to define for each blendshape of the actor face in fsStudio a combination of blendshape weights on your character.
1. Head pose: to map the head pose onto your character, your character needs to have a neck joint. This joint must be named: jointNeck
1. Eye Gaze: to map the eye gaze onto your character, your character needs to have a joint for each eye. These joints must be named: jointEyeLeft and jointEyeRight

## Import

In the Display tab you can select different targets for animation. fsStudio provides a set of default characters, but you can also import your own character via the fbx file format. You will need to create a mapping from the fsStudio actor face to your own characters. The mapping can be saved, and fsStudio will automatically list all imported target characters where the created mapping file resides in the target directory of the workspace. To import a new character click **Import**, previous imported characters can be edited.
![Import button](http://cdn.freshdesk.com/data/helpdesk/attachments/production/2012510/original/target_import.png?1352990859)


## Mapping

In order to import your own character, you need to create a mapping between the fsStudio actor face and your target character. To start, first load the fbx file of your character by clicking **New Target.** The left pane should display your actor face of fsStudio, the right pane should display your imported character, potentially misaligned and at different scale. You can adapt the alignment and scale in the top part of the window. Keep in mind that a global translational alignment between the actor face and target character is automatically defined once you map the neck joint of the actor face to the neck joint of your own character, so translational alignment should only be set after mapping the joints. You may define a name of your imported character, by default it is the name of the fbx file. In case textures are not displayed correctly, as the fbx file may contain invalid file paths, you can define a default texture directory where the textures of your target character reside.
![Rigging window](http://cdn.freshdesk.com/data/helpdesk/attachments/production/2012513/original/target_import_gui.png?1352990887)


## Joints
Head pose and eye gaze are defined by joints in the actor face. In order to map these to your own target character, your rig also needs to have the corresponding joints. Please select the appropriate joints in your rig for each of the actor face joints. Joints that are not mapped will be ignored, e.g. if you don't map the neck joint, then head pose will not be mapped onto your target character.
 
## Blendshapes
Expressions are defined via blendshape mapping. For each of the blendshapes of fsStudio, select and activate the corresponding blendshapes on your target character. One blendshape in fsStudio may be mapped to multiple blendshapes in your target character and vice versa.
 
## Load/Save
Your mapping may be stored to disk as a text file (.fst file) by clicking **Save Mapping**, and accordingly you can load a previous mapping by clicking **Load Mapping**. In order to make sure that fsStudio loads a mapping by default, save the mapping file to the target directory in your workspace.

Your avatar will not be rigged in Interface unless the name of the avatar and the name of the saved .fst file are identical. 
