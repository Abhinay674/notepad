import sys
import bpy
from bpy_extras.io_utils import ImportHelper
from bpy.types import Operator
from bpy.props import StringProperty

argv = sys.argv
print("Prachi args",argv)

foldnew_file_name=argv[5]

print("fileName from Folding Input GLTF", foldnew_file_name)

meshname = ''

file_loc = foldnew_file_name
print("Location:", file_loc)

file_loc3 = foldnew_file_name[0:-5]+'_folding'

# Replace the filepath with the filepath of the asset stored in the server
bpy.ops.import_scene.gltf(filepath=file_loc)

# Code to select the imported asset (Imported glTF file won't be selected automatically in Blender)
for ob in bpy.data.objects:
    if ob.type == "MESH":
        meshname = ob.name

imported_object = bpy.data.objects[meshname]
imported_object.select_set(True)
bpy.context.view_layer.objects.active = imported_object

# Code to scale down the asset to required dimensions
bpy.ops.transform.resize(value=(0.5, 0.5, 0.5), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False)
bpy.ops.transform.resize(value=(0.5, 0.5, 0.5), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', constraint_axis=(False, False, True), mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False)

# Code to apply the guiding curves to the asset
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve"].object = bpy.data.objects["BezierCurve"]
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve"].object = bpy.data.objects["BezierCurve.001"]
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve"].object = bpy.data.objects["BezierCurve.002"]
bpy.ops.object.modifier_apply(modifier="Curve")
bpy.ops.object.modifier_apply(modifier="Curve")
bpy.ops.object.modifier_apply(modifier="Curve")

# Code to fold the shirt left to right
bpy.ops.mesh.select_all(action='SELECT')
bpy.ops.transform.rotate(value=1.5708, orient_axis='Z', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False)

# Code to fold the shirt right to left
bpy.ops.mesh.select_all(action='SELECT')
bpy.ops.transform.rotate(value=-1.5708, orient_axis='Z', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False)

# Code to fold the shirt bottom to top
bpy.ops.object.mode_set(mode='EDIT')
bpy.ops.mesh.select_all(action='SELECT')
bpy.ops.transform.rotate(value=-1.5708, orient_axis='Y', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False)

# Code to export the gltf file with the folded shirt
file_loc4 = foldnew_file_name[0:-5]+'_folded'
bpy.ops.export_scene.gltf(filepath=file_loc4, export_format='GLTF_EMBEDDED')
