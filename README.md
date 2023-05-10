import bpy


blender_file = 'D:\IXRVP\Folding_Template-Hanging.blend'
gltf_file = 'D:\GLTFVERTICAL\ShirtY.gltf'


# Set the name of the collection where the appended objects will be placed
target_collection_name = "MyTargetCollection"

# Append the objects from the .blend file
with bpy.data.libraries.load(blender_file) as (data_from, data_to):
    for obj_name in data_from.objects:
        if obj_name.startswith("ZZZZZZZZZZZ"):
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
    
    hanger = bpy.data.objects["ZZZZZZZZZZZ.001"]
    hanger_location = hanger.location.copy()
    hanger_scale = hanger.scale.copy()
    hanger_rotation_rad = hanger.rotation_euler.copy()
    print('hanger',hanger_location,hanger_scale,hanger_rotation_rad)
    
    shirt = bpy.data.objects.get("F1606CHAC009_AP1532.002_F1606CHAC009_AP1532.001")
    
    if shirt is not None:
        bpy.ops.object.select_all(action='DESELECT')
        shirt.select_set(True)
        bpy.context.view_layer.objects.active = shirt
    else:
        print("Shirt object not found")
    
    shirt.rotation_mode = 'XYZ'
    
    shirt.location = hanger_location
    shirt.scale = hanger_scale
    shirt.rotation_euler = hanger_rotation_rad
    print('shirt',shirt.location,shirt.scale,shirt.rotation_euler)
    

   
    
    
