C:\Program Files\Blender Foundation\Blender 3.4>blender -b D:\blendblendfile\Folding_Template_Sleeveless_Shirt.blend -P D:\blendscript\foldingautomationshirt.txt D:\GLTFVERTICAL\BQ7270_KiksWOL_front-black.gltf
Blender 3.4.1 (hash 55485cb379f7 built 2022-12-20 01:51:19)
Read prefs: C:\Users\abhinay.kumar04\AppData\Roaming\Blender Foundation\Blender\3.4\config\userpref.blend
Read blend: D:\blendblendfile\Folding_Template_Sleeveless_Shirt.blend
Prachi args ['blender', '-b', 'D:\\blendblendfile\\Folding_Template_Sleeveless_Shirt.blend', '-P', 'D:\\blendscript\\foldingautomationshirt.txt', 'D:\\GLTFVERTICAL\\BQ7270_KiksWOL_front-black.gltf']
fileName from Folding Input GLTF D:\GLTFVERTICAL\BQ7270_KiksWOL_front-black.gltf
Location: D:\GLTFVERTICAL\BQ7270_KiksWOL_front-black.gltf
Data are loaded, start creating Blender stuff
glTF import finished in 0.10s
Error: Python: Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "D:\blendscript\foldingautomationshirt.txt", line 73, in <module>
    bpy.data.objects[foldnew_file_name].select_set(True)
KeyError: 'bpy_prop_collection[key]: key "D:\\GLTFVERTICAL\\BQ7270_KiksWOL_front-black.gltf" not found'
Error: File format is not supported in file 'D:\GLTFVERTICAL\BQ7270_KiksWOL_front-black.gltf'

Blender quit




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

bpy.data.objects[meshname].select_set(True)
bpy.context.view_layer.objects.active = bpy.data.objects[meshname]

# Code to scale down the asset to required dimensions
bpy.ops.transform.resize(value=(0.01, 0.01, 0.01), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False)
bpy.ops.transform.resize(value=(1, 1, 0.1), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', constraint_axis=(False, False, True), mirror=True, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False)

# Create curve 1
curve1 = bpy.data.curves.new(name="Curve1", type='CURVE')
curve1.dimensions = '3D'
spline1 = curve1.splines.new(type='BEZIER')
spline1.bezier_points.add(2)
spline1.bezier_points[0].co = (-1.0, 0.0, 0.0)
spline1.bezier_points[1].co = (0.0, 0.5, 0.0)
spline1.bezier_points[2].co = (1.0, 0.0, 0.0)
curve1_ob = bpy.data.objects.new(name="Curve1", object_data=curve1)

# Create curve 2
curve2 = bpy.data.curves.new(name="Curve2", type='CURVE')
curve2.dimensions = '3D'
spline2 = curve2.splines.new(type='BEZIER')
spline2.bezier_points.add(2)
spline2.bezier_points[0].co = (0.0, 1.0, 0.0)
spline2.bezier_points[1].co = (0.5, 0.0, 0.0)
spline2.bezier_points[2].co = (0.0, -1.0, 0.0)
curve2_ob = bpy.data.objects.new(name="Curve2", object_data=curve2)

# Create curve 3
curve3 = bpy.data.curves.new(name="Curve3", type='CURVE')
curve3.dimensions = '3D'
spline3 = curve3.splines.new(type='BEZIER')
spline3.bezier_points.add(2)
spline3.bezier_points[0].co = (0.0, -1.0, 0.0)
spline3.bezier_points[1].co = (-0.5, 0.0, 0.0)
spline3.bezier_points[2].co = (0.0, 1.0, 0.0)
curve3_ob = bpy.data.objects.new(name="Curve3", object_data=curve3)

# Link curves to the scene
bpy.context.scene.collection.objects.link(curve1_ob)
bpy.context.scene.collection.objects.link(curve2_ob)
bpy.context.scene.collection.objects.link(curve3_ob)

# Select the object to be folded
bpy.ops.object.select_all(action='DESELECT')
bpy.data.objects[foldnew_file_name].select_set(True)

# Apply the modifiers to fold the object along the curves
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve"].object = curve1_ob
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve"].object = curve2_ob
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve"].object = curve3_ob

# Export the folded object in GLTF format
export_path = "D:/GLTFVERTICAL/folded_object.gltf"
bpy.ops.export_scene.gltf(filepath=export_path, export_format='GLTF_SEPARATE')
