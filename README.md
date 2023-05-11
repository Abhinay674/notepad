import bpy


blender_file = 'D:\blendblendfile\Mannequin_Template.blend'
gltf_file = 'D:\GLTFVERTICAL\blackred.gltf'
#gltf_file = 'D:\GLTFVERTICAL\frontblack.gltf'


# Set the name of the collection where the appended objects will be placed
target_collection_name = "MyTargetCollection"

# Append the objects from the .blend file
with bpy.data.libraries.load(blender_file) as (data_from, data_to):
    for obj_name in data_from.objects:
        if obj_name.startswith("bwSec_21.002"):
            data_to.objects.append(obj_name)

# Create a new collection or use an existing one to hold the appended objects
target_collection = bpy.data.collections.get(target_collection_name)
if not target_collection:
    target_collection = bpy.data.collections.new(target_collection_name)
    bpy.context.scene.collection.children.link(target_collection)

# Link the appended objects to the target collection
for obj in data_to.objects:
   # obj = bpy.data.objects[obj_name]
    if obj is not None and obj.type == 'MESH' :
        # Unlink object from its current collection (if any)
        if obj.users_collection:
            obj.users_collection[0].objects.unlink(obj)

        target_collection.objects.link(obj)


    bpy.ops.import_scene.gltf(filepath=gltf_file)
    
    mannequin = bpy.data.objects["bwSec_21.002"]
    mannequin_location = mannequin.location.copy()
    mannequin_scale = mannequin.scale.copy()
    mannequin_rotation_rad = mannequin.rotation_euler.copy()
    print('mannequin',mannequin_location,mannequin_scale,mannequin_rotation_rad)
    
    #shirt = bpy.data.objects.get("F1606CHAC009_AP1532.002_F1606CHAC009_AP1532.001")
    shirt = bpy.data.objects.get("BQ7270.002")
    if shirt is not None:
        bpy.ops.object.select_all(action='DESELECT')
        shirt.select_set(True)
        bpy.context.view_layer.objects.active = shirt
    else:
        print("Shirt object not found")
    
    shirt.rotation_mode = 'XYZ'
    
    bpy.context.view_layer.objects.active = shirt
    bpy.ops.object.origin_set(type='ORIGIN_GEOMETRY', center='BOUNDS')
    
    shirt.location = mannequin_location
    shirt.location.z = mannequin_location.z - mannequin_location.z
    shirt.scale = mannequin_scale
    shirt.rotation_euler = mannequin_rotation_rad
    print('shirt',shirt.location,shirt.scale,shirt.rotation_euler)
    

   
    
    Error: Python: Traceback (most recent call last):
  File "\Text", line 13, in <module>
OSError: load: C:\Dlendblendfile\Mannequin_Template.blend failed to open blend file

GPUTexture: Texture allocation failed.Error: Region could not be drawn!
GPUTexture: Texture allocation failed.Error: Region could not be drawn!
GPUTexture: Texture allocation failed.Error: Region could not be drawn!
GPUTexture: Texture allocation failed.Error: Region could not be drawn!
GPUTexture: Texture allocation failed.Error: Region could not be drawn!
GPUTexture: Texture allocation failed.Error: Region could not be drawn!
GPUTexture: Texture allocation failed.Error: Region could not be drawn!
GPUTexture: Texture allocation failed.Error: Region could not be drawn!
GPUTexture: Texture allocation failed.Error: Region could not be drawn!
GPUTexture: Texture allocation failed.Error: Region could not be drawn!
GPUTexture: Texture allocation failed.Error: Region could not be drawn!
GPUTexture: Texture allocation failed.Error: Region could not be drawn!
GPUTexture: Texture allocation failed.Error: Region could not be drawn!
GPUTexture: Texture allocation failed.Error: Region could not be drawn!
GPUTexture: Texture allocation failed.Error: Region could not be drawn!
