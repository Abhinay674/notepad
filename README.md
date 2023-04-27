C:\Program Files\Blender Foundation\Blender 3.4>blender -b D:\blendblendfile\Folding_Template_Shirt_with_sleeve.blend -P D:\blendscript\foldingautomationshirt.txt -- D:\GLTFVERTICAL\BQ7270_KiksWOL_back-red.gltf D:\GLTFVERTICAL\folded_shirt.gltf
Blender 3.4.1 (hash 55485cb379f7 built 2022-12-20 01:51:19)
Read prefs: C:\Users\abhinay.kumar04\AppData\Roaming\Blender Foundation\Blender\3.4\config\userpref.blend
Read blend: D:\blendblendfile\Folding_Template_Shirt_with_sleeve.blend
Data are loaded, start creating Blender stuff
glTF import finished in 0.10s
Error: Python: Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "D:\blendscript\foldingautomationshirt.txt", line 32, in <module>
    folded_mesh.from_pydata(vertices, [], indices)
  File "C:\Program Files\Blender Foundation\Blender 3.4\3.4\scripts\modules\bpy_types.py", line 565, in from_pydata
    face_lengths = tuple(map(len, faces))
TypeError: object of type 'int' has no len()

Blender quit
