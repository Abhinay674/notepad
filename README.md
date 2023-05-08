If your script doesn't contain object names for the shirt and hanger, it might be challenging to attach different shirts automatically. In that case, you'll need to modify your script to handle different shirt objects dynamically. Here's a general outline of the steps you can take:

1. Import the necessary modules:
   ```python
   import bpy
   import mathutils
   ```

2. Define the transformation parameters for attaching the shirt:
   ```python
   # Define the translation, rotation, and scale values
   translation = mathutils.Vector((x, y, z))
   rotation_euler = mathutils.Euler((rx, ry, rz), 'XYZ')
   scale = mathutils.Vector((sx, sy, sz))
   ```

3. Iterate through each shirt object and apply the transformations:
   ```python
   # Iterate through each selected object
   for obj in bpy.context.selected_objects:
       # Apply the transformations to the object
       obj.location += translation
       obj.rotation_euler.rotate(rotation_euler)
       obj.scale *= scale
   ```

In this code snippet, you'll need to replace `x`, `y`, `z`, `rx`, `ry`, `rz`, `sx`, `sy`, and `sz` with the appropriate translation, rotation, and scale values you recorded in the info window for attaching the shirt.

To use this modified script with different shirts, follow these steps:

1. Open your Blender file and make sure the hanger and the shirt you want to attach are present in the scene.

2. Select the shirt object you want to attach.

3. Run the modified script. It will iterate through the selected objects and apply the recorded transformations to each one.

By using this modified script, you should be able to attach different shirts to the hanger based on the recorded transformation parameters.
