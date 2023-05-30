#Code to import asset 
import sys
import bpy
from bpy_extras.io_utils import ImportHelper
from bpy.types import Operator
from bpy.props import StringProperty

argv = sys.argv
print("Prachi args",argv)

foldnew_file_name=argv[5]
print("fileName form FOldinfing INput-gltf",foldnew_file_name)


meshname = ''


file_loc =foldnew_file_name
print("locationnnnnnnnnn",file_loc)

file_loc3 = foldnew_file_name[0:-5]+'_folding'
print("file loc3",file_loc3);


#Replace the filepath with the filepath of the asset stored in the server
bpy.ops.import_scene.gltf(filepath=file_loc)

#Code to select the imported asset (Imported glTF file wont be selected automatically in Blender)

objects = bpy.context.scene.objects
for ob in bpy.data.objects:
    if(ob.type == "MESH"):
        meshname = ob.name
		

bpy.data.objects[meshname].select_set(True)
bpy.context.view_layer.objects.active = bpy.data.objects[meshname]


#Code to scale down the asset to required dimensions
bpy.ops.transform.resize(value=(1.09947, 1.09947, 1.09947), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=False, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False, snap=False, snap_elements={'INCREMENT'}, use_snap_project=False, snap_target='CLOSEST', use_snap_self=True, use_snap_edit=True, use_snap_nonedit=True, use_snap_selectable=False)
bpy.ops.transform.translate(value=(-1.21139, -0.999898, 0.220455), orient_axis_ortho='X', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=False, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False, snap=False, snap_elements={'INCREMENT'}, use_snap_project=False, snap_target='CLOSEST', use_snap_self=True, use_snap_edit=True, use_snap_nonedit=True, use_snap_selectable=False)
bpy.ops.transform.translate(value=(0.071381, 0.00772619, -0.332159), orient_axis_ortho='X', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=False, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False, snap=False, snap_elements={'INCREMENT'}, use_snap_project=False, snap_target='CLOSEST', use_snap_self=True, use_snap_edit=True, use_snap_nonedit=True, use_snap_selectable=False)
bpy.ops.transform.translate(value=(2.40625, 12.8375, -0.784209), orient_axis_ortho='X', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=False, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False, snap=False, snap_elements={'INCREMENT'}, use_snap_project=False, snap_target='CLOSEST', use_snap_self=True, use_snap_edit=True, use_snap_nonedit=True, use_snap_selectable=False)
bpy.ops.transform.translate(value=(-1.57014, -9.26738, -3.31383), orient_axis_ortho='X', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=False, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False, snap=False, snap_elements={'INCREMENT'}, use_snap_project=False, snap_target='CLOSEST', use_snap_self=True, use_snap_edit=True, use_snap_nonedit=True, use_snap_selectable=False)
bpy.ops.transform.resize(value=(1, 1, 0.512429), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', constraint_axis=(False, False, True), mirror=False, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False, snap=False, snap_elements={'INCREMENT'}, use_snap_project=False, snap_target='CLOSEST', use_snap_self=True, use_snap_edit=True, use_snap_nonedit=True, use_snap_selectable=False)
bpy.ops.transform.rotate(value=-2.60148, orient_axis='X', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', constraint_axis=(True, False, False), mirror=False, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False, snap=False, snap_elements={'INCREMENT'}, use_snap_project=False, snap_target='CLOSEST', use_snap_self=True, use_snap_edit=True, use_snap_nonedit=True, use_snap_selectable=False)
bpy.ops.transform.rotate(value=-0.417376, orient_axis='X', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', constraint_axis=(True, False, False), mirror=False, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False, snap=False, snap_elements={'INCREMENT'}, use_snap_project=False, snap_target='CLOSEST', use_snap_self=True, use_snap_edit=True, use_snap_nonedit=True, use_snap_selectable=False)




#Code to apply the guiding curves to the asset
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve"].object = bpy.data.objects["BezierCurve.001"]
bpy.context.object.modifiers["Curve"].deform_axis = 'NEG_X'
bpy.ops.object.modifier_apply(modifier="Curve")
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve"].object = bpy.data.objects["BezierCurve.002"]
bpy.context.object.modifiers["Curve"].deform_axis = 'POS_X'
bpy.ops.object.modifier_apply(modifier="Curve")
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve"].object = bpy.data.objects["BezierCurve"]
bpy.context.object.modifiers["Curve"].deform_axis = 'POS_X'
bpy.ops.object.modifier_apply(modifier="Curve")
bpy.context.object.location[0] = 0
bpy.context.object.location[1] = 0
bpy.context.object.location[2] = 0


#Code to export the gltf file
objects = bpy.context.scene.objects
for obj in objects:
    obj.select_set(obj.type == "CURVE")

#delete all selected objects
bpy.ops.object.delete()

#Replace the filepath with the location of the exported file
file_loc2 = file_loc3
bpy.ops.export_scene.gltf(filepath=file_loc2, export_format ='GLTF_EMBEDDED',)
