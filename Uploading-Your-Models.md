In order to send you model's head or skeleton to us you must first prepare your assets and your [fst file](https://github.com/highfidelity/hifi/wiki/The-FST-file). 

By default the avatar part's name will be whatever is stated inside the .fst file using the “name" tag. 

Begin by creating a local directory for all of your assets. Name this the name of the model. 

i.e.: name=defaultAvatar_Head

We recommend you place your fbx file and all the associated textures in this directory. Remember, your model cannot exceed 10MB and your textures should be either a jpeg or png. 

Make sure the paths used in the .fbx files and in the .fst file are correct.

Inside the .fst, you can either use absolute path:

ie: texdir=/home/MyAccount/Document/MyModel/textures

Or relative path:

ie: 
name= defaultAvatar_head
filename=defaultAvatar_head.fbx
texdir=.

The "." lets us know that the files can be found in the directory you have placed your fst file. If you have nested your assests in another directory within the master directory you must specify that too. 

ie:
name= defaultAvatar_head
filename=fbx_files/defaultAvatar_head.fbx
texdir=textures