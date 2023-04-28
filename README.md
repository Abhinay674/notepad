# Code to scale down the asset to required dimensions
bpy.ops.transform.resize(value=(0.5, 0.5, 0.5), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False)
bpy.ops.transform.resize(value=(0.5, 0.5, 0.5), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', constraint_axis=(False, False, True), mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False)

# Code to fold the left side of the shirt backward
bpy.ops.object.mode_set(mode='EDIT')
bpy.ops.mesh.select_all(action='DESELECT')
bpy.ops.mesh.select_mode(type='VERT')
bpy.ops.mesh.select_circle(x=374, y=229, radius=30)
bpy.ops.mesh.select_circle(x=374, y=341, radius=30)
bpy.ops.transform.rotate(value=-1.5708, orient_axis='Z', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=True, use_proportional_edit=True, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=True, use_proportional_projected=False)
bpy.ops.transform.translate(value=(-0.1, 0, 0), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL')

# Code to fold the right side of the shirt backward
bpy.ops.mesh.select_all(action='DESELECT')
bpy.ops.mesh.select_circle(x=538, y=230, radius=30)
bpy.ops.mesh.select_circle(x=538, y=342, radius=30)
bpy.ops.transform.rotate(value=1.5708, orient_axis='Z', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=True, use_proportional_edit=True, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=True, use_proportional_projected=False)
bpy.ops.transform.translate(value=(0.1, 0, 0), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL')

# Code to fold the bottom of the shirt backward
bpy.ops.mesh.select_all(action='DESELECT')
bpy.ops.mesh.select_circle(x=451, y=116, radius=40)
bpy.ops.mesh.select_circle(x=451, y=166, radius=40)
bpy.ops.mesh.select_circle(x=451, y=216, radius=40)
bpy.ops.transform.rotate(value=-1.5708, orient_axis='Y', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=True, use_proportional_edit=True, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=True, use_proportional_projected=False)
