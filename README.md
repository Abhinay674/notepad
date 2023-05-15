#Code to import asset 

import bpy
import sys
from bpy_extras.io_utils import ImportHelper
from bpy.types import Operator
from bpy.props import StringProperty
from bpy.utils import register_class

argv = sys.argv
print("Prachi args",argv)

hanger_file_name=argv[5]

meshname = ''


#file_loc ='C:/IXRVP/Storage/3DAssets\\'+hanger_file_name
file_loc =hanger_file_name
print("aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",file_loc)
print('hangerfilename',hanger_file_name)
#file_loc3 = 'C:/IXRVP/Storage/3DAssets\\'+hanger_file_name[0:-5]+'_hanger'
file_loc3 = hanger_file_name[0:-5]+'_hanger.gltf'
print('exportpath',file_loc3)



#Replace the filepath with the filepath of the asset stored in the server

bpy.ops.import_scene.gltf(filepath=file_loc)

#Code to select the imported file (Blender by default donot select the imported GLTF file)

objects = bpy.context.scene.objects
for ob in bpy.data.objects:
    if(ob.type == "MESH"):
        meshname = ob.name
        break;
    break;

#print('meshname',meshname)
#bpy.data.objects[meshname].select_set(True)
#bpy.context.view_layer.objects.active = bpy.data.objects[meshname]

#Code to position the asset on the hanger

bpy.ops.transform.resize(value=(1.76449, 1.76449, 1.76449), orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', mirror=False, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False, snap=False, snap_elements={'INCREMENT'}, use_snap_project=False, snap_target='CLOSEST', use_snap_self=True, use_snap_edit=True, use_snap_nonedit=True, use_snap_selectable=False)
bpy.ops.transform.translate(value=(0, 0, 1.72207), orient_axis_ortho='X', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', constraint_axis=(False, False, True), mirror=False, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False, snap=False, snap_elements={'INCREMENT'}, use_snap_project=False, snap_target='CLOSEST', use_snap_self=True, use_snap_edit=True, use_snap_nonedit=True, use_snap_selectable=False)
bpy.ops.transform.translate(value=(0, 0.099364, 0), orient_axis_ortho='X', orient_type='GLOBAL', orient_matrix=((1, 0, 0), (0, 1, 0), (0, 0, 1)), orient_matrix_type='GLOBAL', constraint_axis=(False, True, False), mirror=False, use_proportional_edit=False, proportional_edit_falloff='SMOOTH', proportional_size=1, use_proportional_connected=False, use_proportional_projected=False, snap=False, snap_elements={'INCREMENT'}, use_snap_project=False, snap_target='CLOSEST', use_snap_self=True, use_snap_edit=True, use_snap_nonedit=True, use_snap_selectable=False)

#Code to export the gltf file

#Replace the filepath with the location of the exported file
file_loc2 = file_loc3
bpy.ops.export_scene.gltf(filepath=file_loc2, export_format ='GLTF_EMBEDDED',)




<<< Start VVVV >>>
dto ..> VVVConversionDTO [assetFileName=ShirtY.gltf, blenderFileName=Folding_Template-Hanging.blend, blenderPythonScriptFileName=Hanging - Code (Input-GLTF).txt]
blenderExecutablePath /bin/blender
foldingTemplatePath /opt/ixrvp/Storage/BlenderScript/
blendFilePath /opt/ixrvp/Storage/BlenderBlendFiles/
templateFileName Hanging - Code (Input-GLTF).txt
blendFileName Folding_Template-Hanging.blend
assetFileName ShirtY.gltf
/bin/blender -b /opt/ixrvp/Storage/BlenderBlendFiles/Folding_Template-Hanging.blend -P /opt/ixrvp/Storage/BlenderScript/Hanging - Code (Input-GLTF).txt /opt/ixrvp/app/ixrvp-static-file-server/static/ShirtY.gltf
Blender 2.82 (sub 7)
Read blend: /opt/ixrvp/Storage/BlenderBlendFiles/Folding_Template-Hanging.blend
Error: File written by newer Blender binary (290.0), expect loss of data!
Error: File format is not supported in file '/opt/ixrvp/app/ixrvp-static-file-server/static/ShirtY.gltf'
Prachi args ['/bin/blender', '-b', '/opt/ixrvp/Storage/BlenderBlendFiles/Folding_Template-Hanging.blend', '-P', '/opt/ixrvp/Storage/BlenderScript/Hanging - Code (Input-GLTF).txt', '/opt/ixrvp/app/ixrvp-static-file-server/static/ShirtY.gltf']
aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa /opt/ixrvp/app/ixrvp-static-file-server/static/ShirtY.gltf
hangerfilename /opt/ixrvp/app/ixrvp-static-file-server/static/ShirtY.gltf
exportpath /opt/ixrvp/app/ixrvp-static-file-server/static/ShirtY_hanger.gltf

Blender quit

Exited with error code : 1
