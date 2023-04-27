import sys
import bpy
from bpy_extras.io_utils import ImportHelper
from bpy.types import Operator
from bpy.props import StringProperty

argv = sys.argv
print("Prachi args", argv)

foldnew_file_name = argv[5]

print("fileName form FOldinfing INput-gltf", foldnew_file_name)

meshname = ''

file_loc = foldnew_file_name
print("locationnnnnnnnnn", file_loc)

file_loc3 = foldnew_file_name[0:-5] + '_folding'

# Replace the filepath with the filepath of the asset stored in the server
bpy.ops.import_scene.gltf(filepath=file_loc)

# Code to select the imported asset (Imported glTF file won't be selected automatically in Blender)
for ob in bpy.data.objects:
    if ob.type == "MESH":
        meshname = ob.name

bpy.data.objects[meshname].select_set(True)
bpy.context.view_layer.objects.active = bpy.data.objects[meshname]

# Code to scale down the asset to required dimensions
bpy.ops.transform.resize(value=(0.01, 0.01, 0.01), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=True, use_proportional_projected=True)
bpy.ops.transform.resize(value=(1, 1, 0.1), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', constraint_axis=(False, False, True), mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=True, use_proportional_projected=True)

# Code to apply the guiding curves to the asset
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve"].object = bpy.data.objects["BezierCurve"]
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve.001"].object = bpy.data.objects["BezierCurve.001"]
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve.002"].object = bpy.data.objects["BezierCurve.002"]
bpy.ops.object.modifier_apply(modifier="Curve")
bpy.ops.object.modifier_apply(modifier="Curve.001")
bpy.ops.object.modifier_apply(modifier="Curve.002")
bpy.ops.object.origin_set(type='ORIGIN_GEOMETRY', center='MEDIAN')
bpy.context.object.location[0] = 0
bpy.context.object.location[1] = 0
bpy.context.object.location[2] = 0

# Code to fold from left to right
bpy.ops.object.mode_set(mode='EDIT')
bpy.ops.mesh.select_all(action='SELECT')
bpy.ops.mesh.subdivide(number_cuts=3)
bpy.ops.mesh.select_all(action='DESELECT')
bpy.ops.mesh.select_mode(use_extend=False, use_expand=False, type='FACE')
bpy.ops.mesh.select_nth(nth=2, offset=0)
bpy.ops.transform.translate(value=(-0.05, 0, 0), constraint_axis=(True, False, False), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=True, use_proportional_projected=True)
bpy.ops.object.mode_set(mode='OBJECT')

# Code to fold from right to left
bpy.ops.object.mode_set(mode='EDIT')
bpy.ops.mesh.select_all(action='SELECT')
bpy.ops.mesh.subdivide(number_cuts=3)
bpy.ops.mesh.select_all(action='DESELECT')
bpy.ops.mesh.select_mode(use_extend=False, use_expand=False, type='FACE')
bpy.ops.mesh.select_nth(nth=2, offset=0)
bpy.ops.transform.translate(value=(0.05, 0, 0), constraint_axis=(True, False, False), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=True, use_proportional_projected=True)

# Code to fold from bottom to top
bpy.ops.object.mode_set(mode='EDIT')
bpy.ops.mesh.select_all(action='SELECT')
bpy.ops.mesh.subdivide(number_cuts=3)
bpy.ops.mesh.select_all(action='DESELECT')
bpy.ops.mesh.select_mode(use_extend=False, use_expand=False, type='FACE')
bpy.ops.mesh.select_nth(nth=2, offset=0)
bpy.ops.transform.translate(value=(0, 0, 0.05), constraint_axis=(False, False, True), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=True, use_proportional_projected=True)


