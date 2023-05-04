import bpy

# replace the shirt with a new gltf file
new_shirt_path = "C:\\Users\\abhinay.kumar04\\Downloads\\new_shirt.gltf"
bpy.ops.object.select_all(action="DESELECT")
bpy.data.objects["shirt"].select_set(True)
bpy.ops.object.delete(use_global=False)
bpy.ops.import_scene.gltf(filepath=new_shirt_path)

# transform the new shirt
shirt_obj = bpy.context.selected_objects[0]
shirt_obj.name = "shirt"
shirt_obj.scale *= 3.30587
shirt_obj.location.y -= 4.75175
shirt_obj.rotation_euler.z -= 0.424993

# export the hanger with the new shirt
export_path = "C:\\Users\\abhinay.kumar04\\Downloads\\hanger_with_new_shirt.gltf"
bpy.ops.export_scene.gltf(filepath=export_path)
