import bpy
import json

# Set the path to the glTF file to be folded
gltf_file_path = "path/to/your/tshirt.gltf"

# Set the path to the output file
output_file_path = "path/to/your/folded_tshirt.gltf"

# Load the glTF file
with open(gltf_file_path, 'r') as f:
    data = json.load(f)

# Extract the t-shirt mesh data
for mesh in data['meshes']:
    if mesh['name'] == 'T-Shirt':
        indices = mesh['primitives'][0]['indices']
        vertices = mesh['primitives'][0]['attributes']['POSITION']
        normals = mesh['primitives'][0]['attributes']['NORMAL']
        texcoords = mesh['primitives'][0]['attributes']['TEXCOORD_0']

# Create a new mesh for the folded t-shirt
folded_mesh = bpy.data.meshes.new("Folded T-Shirt")

# Create a new object and link it to the scene
folded_object = bpy.data.objects.new("Folded T-Shirt", folded_mesh)
bpy.context.scene.collection.objects.link(folded_object)

# Set the folded t-shirt mesh data
folded_mesh.from_pydata(vertices, [], indices)
folded_mesh.normals_split_custom_set_from_vertices(normals)
folded_mesh.uv_layers.new()
folded_mesh.uv_layers.active.data.foreach_set("uv", texcoords)

# Apply the folding transformation
# Replace the following code with your own folding algorithm
folded_object.rotation_euler = (0.0, 0.0, 1.0)

# Export the folded glTF file
bpy.ops.export_scene.gltf(filepath=output_file_path, export_format="GLTF_SEPARATE")
