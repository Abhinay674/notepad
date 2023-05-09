import bpy
import sys

# Set the input parameters
blender_file = sys.argv[5]  # Path to the Blender file (.blend)
gltf_file = sys.argv[6]     # Path to the shirt file (.gltf)

# Load the Blender file
bpy.ops.wm.open_mainfile(filepath=blender_file)

# Import the shirt
bpy.ops.import_scene.gltf(filepath=gltf_file)

# Get references to the hanger and the shirt object
hanger = bpy.data.objects.get("hanger")
shirt = bpy.data.objects.get("shirt")

if hanger is not None and shirt is not None:
    # Get the hanger's position and scale
    hanger_location = hanger.location.copy()
    hanger_scale = hanger.scale.copy()

    # Set the shirt's position and scale to match the hanger
    shirt.location = hanger_location
    shirt.scale = hanger_scale

    # Parent the shirt to the hanger
    shirt.parent = hanger

    # Set the output path for the exported GLTF file
    output_gltf_file = "output.gltf"  # Replace with your desired output file path

    # Select the shirt object
    shirt.select_set(True)

    # Export the selected shirt object as GLTF
    bpy.ops.export_scene.gltf(filepath=output_gltf_file, export_selected=True)
else:
    print("Failed to find hanger or shirt object")

# Save the modified scene
bpy.ops.wm.save_mainfile(filepath=blender_file)
