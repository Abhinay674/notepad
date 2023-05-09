import bpy

# Specify the path to the .blend file you want to import
blend_file_path = "D:/hanger.blend"

# Set the name of the collection where the appended objects will be placed
target_collection_name = "MyTargetCollection"

# Append the objects from the .blend file
with bpy.data.libraries.load(blend_file_path) as (data_from, data_to):
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
        target_collection.objects.link(obj)
