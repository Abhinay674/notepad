import bpy

blender_file = 'D:\blendblendfile\Folding_Template-Hanging.blend'
gltf_file = 'D:\GLTFVERTICAL\ShirtY.gltf'


# Set the name of the collection where the appended objects will be placed
target_collection_name = "MyTargetCollection"

# Append the objects from the .blend file
with bpy.data.libraries.load(blender_file) as (data_from, data_to):
    data_to.objects = [name for name in data_from.objects]

# Create a new collection or use an existing one to hold the appended objects
target_collection = bpy.data.collections.get(target_collection_name)
if not target_collection:
    target_collection = bpy.data.collections.new(target_collection_name)
    bpy.context.scene.collection.children.link(target_collection)

# Link the appended objects to the target collection
for obj_name in data_to.objects:
    obj = bpy.data.objects.get(obj_name)
    if obj:
        # Unlink object from its current collection (if any)
        if obj.users_collection:
            obj.users_collection[0].objects.unlink(obj)

        target_collection.objects.link(obj)


Error: Python: Traceback (most recent call last):
  File "\Text", line 11, in <module>
OSError: load: C:\Dlendblendfile\Folding_Template-Hanging.blend failed to open blend file
