import bpy

# Replace the path below with the path to your new GLTF shirt
new_gltf_path = "C:\\Users\\abhinay.kumar04\\Downloads\\new_shirt.gltf"

# Replace the path below with the path where you want to export the modified GLTF file
export_path = "C:\\Users\\abhinay.kumar04\\Downloads\\modified_shirt.gltf"

# Delete the existing shirt
bpy.ops.object.select_all(action='DESELECT')
bpy.data.objects['shirt'].select_set(True)
bpy.ops.object.delete(use_global=False, confirm=False)

# Import the new shirt
bpy.ops.import_scene.gltf(filepath=new_gltf_path, files=[{"name":"new_shirt.gltf", "name":"new_shirt.gltf"}], loglevel=50)

# Resize and position the new shirt on the hanger
bpy.ops.transform.translate(value=(0, 0, 2.04376), orient_axis_ortho='X', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', constraint_axis=(False, False, True), mirror=False, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False, snap=False, snap_elements={'INCREMENT'}, use_snap_project=False, snap_target='CLOSEST', use_snap_self=True, use_snap_edit=True, use_snap_nonedit=True, use_snap_selectable=False)
bpy.ops.transform.resize(value=(0.887978, 0.887978, 0.887978), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=False, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False, snap=False, snap_elements={'INCREMENT'}, use_snap_project=False, snap_target='CLOSEST', use_snap_self=True, use_snap_edit=True, use_snap_nonedit=True, use_snap_selectable=False)
bpy.ops.transform.translate(value=(0, 0.428799, 0), orient_axis_ortho='X', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', constraint_axis=(False, True, False), mirror=False, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False, snap=False, snap_elements={'INCREMENT'}, use_snap_project=False, snap_target='CLOSEST', use_snap_self=True, use_snap_edit=True, use_snap_nonedit=True, use_snap_selectable=False)
bpy.ops.transform.translate(value=(0, 0, 0.130189), orient_axis_ortho='X', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', constraint_axis=(False, False, True), mirror=False, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False, snap=False, snap_elements={'INCREMENT'}, use_snap_project=False, snap_target='CLOSEST', use_snap_self=True, use_snap_edit=True, use_snap_nonedit=True, use_snap_selectable=False)

#Create a new material for the shirt
new_material = bpy.data.materials.new(name="NewShirtMaterial")

#Set the material color to red
new_material.diffuse_color = (1, 0, 0, 1)

#Assign the new material to the shirt
shirt_obj = bpy.context.selected_objects[0]
if shirt_obj.type == "MESH":
for slot in shirt_obj.material_slots:
slot.material = new_material
