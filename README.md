import bpy

# Step 1: Delete existing shirt object
existing_shirt_name = "Object001_Object001_mtl_0"
if existing_shirt_name in bpy.data.objects:
    bpy.data.objects[existing_shirt_name].select_set(True)
    bpy.ops.object.delete(use_global=False)

# Step 2: Import new shirt
new_shirt_path = "D:/GLTFVERTICAL/ShirtY.gltf"
bpy.ops.import_scene.gltf(filepath=new_shirt_path)

# Step 3: Rename new shirt object and transform it
new_shirt_obj = bpy.context.selected_objects[0]
new_shirt_obj.name = existing_shirt_name
new_shirt_obj.scale *= 3.30587
new_shirt_obj.location.y -= 4.75175
new_shirt_obj.rotation_euler.z -= 0.424993

# Step 4: Export hanger with new shirt
export_path = "D:/GLTFVERTICAL/ShirtY_hanger.gltf"
bpy.ops.export_scene.gltf(filepath=export_path)
