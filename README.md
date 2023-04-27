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
bpy.ops.import_scene.gltf(filepath=file_loc, import_pack_images=True, import_shading='NORMALS', name='ImportedObject')

# Get the imported object by its name
imported_object = bpy.data.objects['ImportedObject']

# Select the imported object
imported_object.select_set(True)
bpy.context.view_layer.objects.active = imported_object

# Code to scale down the asset to required dimensions
bpy.ops.transform.resize(
    value=(0.01, 0.01, 0.01), 
    orient_type='GLOBAL', 
    orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), 
    orient_matrix_type='GLOBAL', 
    mirror=True, 
    use_proportional_edit=False, 
    proportional_edit_falloff='SMOOTH', 
    proportional_size=1, 
    use_proportional_connected=False, 
    use_proportional_projected=False,
)
