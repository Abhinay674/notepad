import bpy
import os

# Set the path to the Blender file containing the folding template
blend_file_path = "D:\\blendblendfile\\Folding_Template_Shirt_with_sleeve.blend"

# Set the path to the glTF shirt file you want to fold
gltf_file_path = "D:\\GLTFVERTICAL\\BQ7270_KiksWOL_back-red.gltf"

# Set the path to the Python script that automates the folding process
script_file_path = "D:\\blendscript\\foldingautomationshirt.py"

# Set the path to the output folder where the folded glTF file will be saved
output_folder_path = "D:\\folded_gltf_files"

# Create a new Blender scene and import the glTF file
bpy.ops.import_scene.gltf(filepath=gltf_file_path)

# Run the Python script that automates the folding process
exec(compile(open(script_file_path).read(), script_file_path, 'exec'))

# Set the output path for the folded glTF file
output_file_path = os.path.join(output_folder_path, "folded_shirt.gltf")

# Export the folded glTF file
bpy.ops.export_scene.gltf(filepath=output_file_path, export_format="GLTF_SEPARATE")
