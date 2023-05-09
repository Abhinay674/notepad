# Append the objects from the .blend file
with bpy.data.libraries.load(blender_file) as (data_from, data_to):
    for obj_name in data_from.objects:
        if obj_name.startswith("hanger"):
            data_to.objects.append(obj_name)

# Create a new collection or use an existing one to hold the appended objects
target_collection = bpy.data.collections.get(target_collection_name)
if not target_collection:
    target_collection = bpy.data.collections.new(target_collection_name)
    bpy.context.scene.collection.children.link(target_collection)

# Link the appended objects to the target collection
for obj_name in data_to.objects:
    obj = data_to.objects[obj_name]
    if obj:
        # Unlink object from its current collection (if any)
        if obj.users_collection:
            obj.users_collection[0].objects.unlink(obj)

        target_collection.objects.link(obj)
