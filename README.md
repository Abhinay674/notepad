import bpy
import pygltf

# Load the GLTF file
gltf = pygltf.GLTF2().load('tshirt.gltf')

# Extract the mesh data
mesh = gltf.scenes[0].nodes[0].mesh

# Create a new mesh object in Blender
mesh_data = bpy.data.meshes.new(name='T-Shirt')
obj = bpy.data.objects.new(name='T-Shirt', object_data=mesh_data)
bpy.context.collection.objects.link(obj)
mesh_data.from_pydata(mesh.vertices, [], mesh.faces)

# Load and run the folding script
with open('your_script_file.py', 'r') as script_file:
    script = script_file.read()
    
exec(script)

# Save the folded mesh as a Blend file
bpy.ops.wm.save_as_mainfile(filepath='folded_tshirt.blend')
