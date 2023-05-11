import bpy

blender_file = 'D:\IXRVP\Folding_Template-Hanging.blend'
gltf_file = 'D:\GLTFVERTICAL\frontblack.gltf'

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
    if obj is not None and obj.type == 'MESH':
        # Unlink object from its current collection (if any)
        if obj.users_collection:
            obj.users_collection[0].objects.unlink(obj)
        target_collection.objects.link(obj)

# Save the current scene's collection and active object
original_collection = bpy.context.collection
original_active_object = bpy.context.view_layer.objects.active

# Import the glTF file
bpy.ops.import_scene.gltf(filepath=gltf_file)

# Get the imported shirt object
shirt = bpy.context.selected_objects[-1]  # Assuming the last selected object is the shirt
if shirt is None or shirt.type != 'MESH':
    print("Shirt object not found or not a mesh")
else:
    # Set the shirt's properties
    hanger = bpy.data.objects["ZZZZZZZZZZZ"]
    shirt.location = hanger.location
    shirt.scale = hanger.scale
    shirt.rotation_euler = hanger.rotation_euler

# Restore the original collection and active object
bpy.context.collection = original_collection
bpy.context.view_layer.objects.active = original_active_object
