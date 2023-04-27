C:\Program Files\Blender Foundation\Blender 3.4>blender -b D:\blendblendfile\Folding_Template_Shirt_with_sleeve.blend -P D:\blendscript\foldingautomationshirt.txt -- D:\GLTFVERTICAL\BQ7270_KiksWOL_back-red.gltf D:\GLTFVERTICAL\folded_shirt.gltf
Blender 3.4.1 (hash 55485cb379f7 built 2022-12-20 01:51:19)
Read prefs: C:\Users\abhinay.kumar04\AppData\Roaming\Blender Foundation\Blender\3.4\config\userpref.blend
Read blend: D:\blendblendfile\Folding_Template_Shirt_with_sleeve.blend
Data are loaded, start creating Blender stuff
glTF import finished in 0.10s
Error: Python: Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "D:\blendscript\foldingautomationshirt.txt", line 32, in <module>
    folded_mesh.from_pydata(vertices, [], indices)
  File "C:\Program Files\Blender Foundation\Blender 3.4\3.4\scripts\modules\bpy_types.py", line 565, in from_pydata
    face_lengths = tuple(map(len, faces))
TypeError: object of type 'int' has no len()

Blender quit

  
  
  
  
  import bpy
import sys

argv = sys.argv
argv = argv[argv.index("--") + 1:]

# Load the gltf file
bpy.ops.import_scene.gltf(filepath=argv[0])

# Get the imported mesh
mesh_obj = bpy.context.selected_objects[0]
mesh = mesh_obj.data

# Create the new folded mesh
folded_mesh = bpy.data.meshes.new(name="FoldedMesh")

# Define the vertices and indices of the folded mesh
vertices = []
indices = []

# Add vertices for each loop in the mesh
for loop in mesh.loops:
    vertex = mesh.vertices[loop.vertex_index]
    vertices.append([vertex.co.x, vertex.co.y, vertex.co.z])

# Add indices for each face in the mesh
for face in mesh.polygons:
    for vert_idx, loop_idx in zip(face.vertices, face.loop_indices):
        indices.append((mesh.loops[loop_idx].vertex_index))

# Set the vertices and indices of the folded mesh
folded_mesh.from_pydata(vertices, [], indices)

# Create the folded mesh object
folded_mesh_obj = bpy.data.objects.new(name="FoldedMeshObj", object_data=folded_mesh)

# Add the folded mesh object to the scene
bpy.context.scene.collection.objects.link(folded_mesh_obj)

# Save the folded mesh as a gltf file
bpy.ops.export_scene.gltf(filepath=argv[1])
