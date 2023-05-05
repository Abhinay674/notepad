import bpy
from mathutils import Matrix, Vector

# Load the hanger and the new shirt
bpy.ops.import_scene.gltf(filepath='hanger.glb')
bpy.ops.import_scene.gltf(filepath='new_shirt.glb')

# Get the objects for the hanger and the new shirt
hanger = bpy.data.objects['hanger']
new_shirt = bpy.data.objects['new_shirt']

# Get the dimensions and position of the new shirt
new_shirt_dimensions = new_shirt.dimensions
new_shirt_location = new_shirt.location

# Calculate the necessary transformations
translation = Vector((0, 0, 0))  # adjust as necessary
rotation = Matrix.Rotation(0.5, 4, 'Z') @ Matrix.Rotation(0.5, 4, 'X')  # adjust as necessary
scale = hanger.dimensions / new_shirt_dimensions  # adjust as necessary
transform = Matrix.Translation(new_shirt_location) @ rotation.to_4x4() @ Matrix.Scale(scale[0], 4)  # adjust as necessary

# Apply the transformations to the new shirt
new_shirt.matrix_world = transform

# Export the hanger with the attached shirt
bpy.ops.export_scene.gltf(filepath='hanger_with_shirt.glb')

import bpy
from mathutils import Matrix, Vector

# Load the .blend hanger file
bpy.ops.wm.open_mainfile(filepath='path/to/hanger_file.blend')

# Import the hanger and the new shirt
bpy.ops.import_scene.gltf(filepath='path/to/new_shirt.glb')

# Get the objects for the hanger and the new shirt
hanger = bpy.data.objects['hanger']
new_shirt = bpy.data.objects['new_shirt']

# Calculate the necessary transformations...
