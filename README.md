import bpy
import os


blender_file = r'D:\IXRVP\Folding_Template-Hanging.blend'
gltf_file = r'D:\GLTFVERTICAL\ShirtY.gltf'
# gltf_file = r'D:\GLTFVERTICAL\frontblack.gltf'


# Set the name of the collection where the appended objects will be placed
target_collection_name = "MyTargetCollection"

# Get the directory of the GLTF file
gltf_dir = os.path.dirname(gltf_file)

# Append the objects from the .blend file
with bpy.data.libraries.load(blender_file, link=False) as (data_from, data_to):
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
    if obj is not None and obj.type == 'MESH':
        # Unlink object from its current collection (if any)
        if obj.users_collection:
            obj.users_collection[0].objects.unlink(obj)

        target_collection.objects.link(obj)

# Clear existing objects in the scene
bpy.ops.object.select_all(action='DESELECT')
bpy.ops.object.select_by_type(type='MESH')
bpy.ops.object.delete()

# Import the GLTF file
bpy.ops.import_scene.gltf(filepath=gltf_file, directory=gltf_dir)

hanger = bpy.data.objects.get("ZZZZZZZZZZZ")
if hanger is None:
    print("Hanger object not found")
else:
    hanger_location = hanger.location.copy()
    hanger_scale = hanger.scale.copy()
    hanger_rotation_rad = hanger.rotation_euler.copy()
    print('hanger', hanger_location, hanger_scale, hanger_rotation_rad)

    shirt = bpy.data.objects.get("F1606CHAC009_AP1532.002_F1606CHAC009_AP1532.001")
    # shirt = bpy.data.objects.get("BQ7270.002")
    if shirt is not None:
        shirt.rotation_mode = 'XYZ'

        # Set the origin of the shirt to its bounding box center
        bpy.context.view_layer.objects.active = shirt
        bpy.ops.object.origin_set(type='ORIGIN_GEOMETRY', center='BOUNDS')

        shirt.location = hanger_location
        shirt.location.z = hanger_location.z
        shirt.scale = hanger_scale
        shirt.rotation_euler = hanger_rotation_rad
        print('shirt', shirt.location, shirt.scale, shirt.rotation_euler)
    else:
        print("Shirt object not found")
