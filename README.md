import bpy

# Specify the path to your .blend file
blend_file_path = "path/to/your/file.blend"

# Open the .blend file
with bpy.data.libraries.load(blend_file_path) as (data_from, data_to):
    pass

# Check the Blender version used to create the .blend file
if "version" in data_from:
    blender_version = data_from.version
    print("Blender Version:", blender_version)
else:
    print("Blender version information not found.")
