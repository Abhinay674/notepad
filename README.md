C:\Program Files\Blender Foundation\Blender 3.4>blender -b D:\blendblendfile\Folding_Template-Hanging.blend -P D:\blendscript\football2.py D:\GLTFVERTICAL\ShirtY.gltf
Blender 3.4.1 (hash 55485cb379f7 built 2022-12-20 01:51:19)
Read prefs: C:\Users\abhinay.kumar04\AppData\Roaming\Blender Foundation\Blender\3.4\config\userpref.blend
Read blend: D:\blendblendfile\Folding_Template-Hanging.blend
Error: Python: Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "D:\blendscript\football2.py", line 23, in <module>
    bpy.data.objects["Sketchfab_model"].select_set(True)
KeyError: 'bpy_prop_collection[key]: key "Sketchfab_model" not found'
Error: File format is not supported in file 'D:\GLTFVERTICAL\ShirtY.gltf'

Blender quit
  
  
  
  import bpy

# replace the shirt with a new gltf file
new_shirt_path = "D:\GLTFVERTICAL\ShirtY.gltf"
bpy.ops.object.select_all(action="DESELECT")
bpy.data.objects["Sketchfab_model"].select_set(True)
bpy.ops.object.delete(use_global=False)
bpy.ops.import_scene.gltf(filepath=new_shirt_path)

# transform the new shirt
shirt_obj = bpy.context.selected_objects[0]
shirt_obj.name = "Sketchfab_model"
shirt_obj.scale *= 3.30587
shirt_obj.location.y -= 4.75175
shirt_obj.rotation_euler.z -= 0.424993

# export the hanger with the new shirt
export_path = "D:\GLTFVERTICAL\ShirtY_hanger.gltf"
bpy.ops.export_scene.gltf(filepath=export_path)
