import bpy

# Create curve 1
curve1 = bpy.data.curves.new(name="Curve1", type='CURVE')
curve1.dimensions = '3D'
spline1 = curve1.splines.new(type='BEZIER')
spline1.bezier_points.add(2)
spline1.bezier_points[0].co = (-1.0, 0.0, 0.0)
spline1.bezier_points[1].co = (0.0, 0.5, 0.0)
spline1.bezier_points[2].co = (1.0, 0.0, 0.0)
curve1_ob = bpy.data.objects.new(name="Curve1", object_data=curve1)

# Create curve 2
curve2 = bpy.data.curves.new(name="Curve2", type='CURVE')
curve2.dimensions = '3D'
spline2 = curve2.splines.new(type='BEZIER')
spline2.bezier_points.add(2)
spline2.bezier_points[0].co = (0.0, 1.0, 0.0)
spline2.bezier_points[1].co = (0.5, 0.0, 0.0)
spline2.bezier_points[2].co = (0.0, -1.0, 0.0)
curve2_ob = bpy.data.objects.new(name="Curve2", object_data=curve2)

# Create curve 3
curve3 = bpy.data.curves.new(name="Curve3", type='CURVE')
curve3.dimensions = '3D'
spline3 = curve3.splines.new(type='BEZIER')
spline3.bezier_points.add(2)
spline3.bezier_points[0].co = (0.0, -1.0, 0.0)
spline3.bezier_points[1].co = (-0.5, 0.0, 0.0)
spline3.bezier_points[2].co = (0.0, 1.0, 0.0)
curve3_ob = bpy.data.objects.new(name="Curve3", object_data=curve3)

# Link curves to the scene
bpy.context.scene.collection.objects.link(curve1_ob)
bpy.context.scene.collection.objects.link(curve2_ob)
bpy.context.scene.collection.objects.link(curve3_ob)

# Select the object to be folded
bpy.ops.object.select_all(action='DESELECT')
bpy.data.objects['name_of_object_to_be_folded'].select_set(True)

# Apply the modifiers to fold the object along the curves
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve"].object = curve1_ob
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve"].object = curve2_ob
bpy.ops.object.modifier_add(type='CURVE')
bpy.context.object.modifiers["Curve"].object = curve3_ob

# Export the folded object in GLTF format
export_path = "D:/GLTFVERTICAL/folded_object.gltf"
bpy.ops.export_scene.gltf(filepath=export_path, export_format='GLTF_SEPARATE')
