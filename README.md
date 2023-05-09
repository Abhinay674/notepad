import bpy
import sys

# Set the input parameters
blender_file = sys.argv[5]  # Path to the Blender file (.blend)
script_file = sys.argv[6]   # Path to the Python script file (.py)
gltf_file = sys.argv[7]     # Path to the shirt file (.gltf)

# Load the Blender file
bpy.ops.wm.open_mainfile(filepath=blender_file)

# Import the shirt
bpy.ops.import_scene.gltf(filepath=gltf_file)

# Get references to the hanger and the shirt object
hanger = bpy.data.objects["hanger"]
shirt = bpy.data.objects["shirt"]

# Set the shirt's scale, rotation, and position
shirt.scale = hanger.scale  # Match the scale of the hanger
shirt.rotation_euler = hanger.rotation_euler  # Match the rotation of the hanger
shirt.location = hanger.location  # Match the position of the hanger

# Parent the shirt to the hanger
shirt.parent = hanger

# Save the modified scene
bpy.ops.wm.save_mainfile(filepath=blender_file)

# Execute the Python script
exec(compile(open(script_file).read(), script_file, 'exec'))
