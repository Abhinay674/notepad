C:\Program Files\Blender Foundation\Blender 3.4>blender -b D:\blendblendfile\Folding_Template_Sleeveless_Shirt.blend -P D:\blendscript\foldingautomationshirt.txt D:\GLTFVERTICAL\BQ7270_KiksWOL_back-red.gltf
Blender 3.4.1 (hash 55485cb379f7 built 2022-12-20 01:51:19)
Read prefs: C:\Users\abhinay.kumar04\AppData\Roaming\Blender Foundation\Blender\3.4\config\userpref.blend
Read blend: D:\blendblendfile\Folding_Template_Sleeveless_Shirt.blend
Prachi args ['blender', '-b', 'D:\\blendblendfile\\Folding_Template_Sleeveless_Shirt.blend', '-P', 'D:\\blendscript\\foldingautomationshirt.txt', 'D:\\GLTFVERTICAL\\BQ7270_KiksWOL_back-red.gltf']
fileName from Folding Input GLTF D:\GLTFVERTICAL\BQ7270_KiksWOL_back-red.gltf
Location: D:\GLTFVERTICAL\BQ7270_KiksWOL_back-red.gltf
Data are loaded, start creating Blender stuff
glTF import finished in 0.09s
Error: Python: Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "D:\blendscript\foldingautomationshirt.txt", line 52, in <module>
    bpy.context.object.modifiers["SimpleDeform"].limits[0][0] = [(0.0,0.0),(0.0,0.0),(0.0,0.0)]
TypeError: 'float' object does not support item assignment
Error: File format is not supported in file 'D:\GLTFVERTICAL\BQ7270_KiksWOL_back-red.gltf'

Blender quit
