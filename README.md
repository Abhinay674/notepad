import bpy
import math

# Load the glTF file
bpy.ops.import_scene.gltf(filepath='path/to/your/file.gltf')

# Select the imported object (assuming it's the only mesh object in the scene)
obj = bpy.context.scene.objects[0]
bpy.context.view_layer.objects.active = obj
obj.select_set(True)

# Apply a scale transformation to the object
bpy.ops.transform.resize(value=(0.01, 0.01, 0.01))
bpy.ops.transform.resize(value=(1, 1, 0.1), constraint_axis=(False, False, True))

# Create a keyframe animation for the folding
frame_start = 0
frame_end = 30
frame_step = 1

# Create a keyframe for the initial pose
obj.rotation_euler = (0, 0, 0)
obj.keyframe_insert(data_path='rotation_euler', frame=frame_start)

# Create a keyframe for the final pose
obj.rotation_euler = (math.radians(-90), 0, 0)
obj.keyframe_insert(data_path='rotation_euler', frame=frame_end)

# Create keyframes for the intermediate poses
for frame in range(frame_start + frame_step, frame_end, frame_step):
    # Calculate the rotation angles for the folding effect
    angle_x = -1 * math.radians(90 * (frame / frame_end))
    angle_y = 0
    angle_z = math.radians(180 * (frame / frame_end))

    # Apply the rotation to the object
    obj.rotation_euler = (angle_x, angle_y, angle_z)
    obj.keyframe_insert(data_path='rotation_euler', frame=frame)

# Export the folded object as a new glTF file
bpy.ops.export_scene.gltf(filepath='path/to/your/folded/file.gltf')
