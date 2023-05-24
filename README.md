#Code to import asset 

import bpy
from bpy_extras.io_utils import ImportHelper
from bpy.types import Operator
from bpy.props import StringProperty

meshname = ''

#Replace the filepath with the filepath of the asset stored in the server
bpy.ops.import_scene.gltf(filepath='D:\GLTFVERTICAL\greenshirt.gltf', import_pack_images=True, merge_vertices=False, guess_original_bind_pose=True,) 

#Code to select the imported asset (Imported glTF file won't be selected by default in Blender)

objects = bpy.context.scene.objects
for ob in bpy.data.objects:
    if(ob.type == "MESH"):
        meshname = ob.name

bpy.data.objects[meshname].select_set(True)
bpy.context.view_layer.objects.active = bpy.data.objects[meshname]

#Code to scale down the asset to required dimensions
bpy.ops.transform.resize(value=(0.01, 0.01, 0.01), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False)
bpy.ops.transform.resize(value=(1, 1, 0.1), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', constraint_axis=(False, False, True), mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False)

#Code to apply the guiding curves to the asset

bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve"].object = bpy.data.objects["BezierCurve"]
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve.001"].object = bpy.data.objects["BezierCurve.001"]
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve.002"].object = bpy.data.objects["BezierCurve.002"]
bpy.ops.object.modifier_apply(modifier="Curve")
bpy.ops.object.modifier_apply(modifier="Curve.001")
bpy.ops.object.modifier_apply(modifier="Curve.002")

#Code to export the gltf file

objects = bpy.context.scene.objects
for obj in objects:
    obj.select_set(obj.type == "CURVE")
# delete all selected objects
bpy.ops.object.delete()

#Replace the filepath with the location of the exported file
file_loc2 = 'D:\GLTFVERTICAL\greenshirt_folding.gltf'
bpy.ops.export_scene.gltf(filepath=file_loc2, export_format ='GLTF_EMBEDDED',)









Read blend: D:\IXRVP\Folding_Template_Shirt_with_sleeve.blend
Data are loaded, start creating Blender stuff
glTF import finished in 0.23s
Error: Python: Traceback (most recent call last):
  File "D:\IXRVP\Folding_Template_Shirt_with_sleeve.blend\Text", line 30, in <module>
KeyError: 'bpy_prop_collection[key]: key "BezierCurve" not found'
