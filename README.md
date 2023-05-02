import bpy

# Load the glTF file
bpy.ops.import_scene.gltf(filepath='path/to/your/file.gltf')

# Select the imported object (assuming it's the only mesh object in the scene)
obj = bpy.context.scene.objects[0]
bpy.context.view_layer.objects.active = obj
obj.select_set(True)

# Apply a scale transformation to the object
bpy.ops.transform.resize(value=(0.01, 0.01, 0.01))

# Set the pivot point for the rotation to be the bottom center of the object
bpy.context.scene.tool_settings.transform_pivot_point = 'ACTIVE_ELEMENT'
bpy.context.scene.cursor.location = obj.matrix_world @ obj.data.vertices[0].co

# Create a keyframe animation for the folding
frame_start = 0
frame_end = 30
frame_step = 1

# Create a keyframe for the initial pose
obj.rotation_euler = (0, 0, 0)
obj.keyframe_insert(data_path='rotation_euler', frame=frame_start)

# Create a keyframe for the left side fold
obj.rotation_euler = (-1.57, 0, 0)
obj.keyframe_insert(data_path='rotation_euler', frame=frame_end/4)

# Create a keyframe for the right side fold
obj.rotation_euler = (-1.57, 0, -3.14)
obj.keyframe_insert(data_path='rotation_euler', frame=frame_end/2)

# Create a keyframe for the bottom fold
obj.rotation_euler = (-3.14, 0, -3.14)
obj.keyframe_insert(data_path='rotation_euler', frame=frame_end*3/4)

# Create a keyframe for the final pose
obj.rotation_euler = (-3.14, 0, 0)
obj.keyframe_insert(data_path='rotation_euler', frame=frame_end)

# Export the folded object as a new glTF file
bpy.ops.export_scene.gltf(filepath='path/to/your/folded/file.gltf')
