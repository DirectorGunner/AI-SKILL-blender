# Depsgraph Bpy Struct, Displacemodifier Modifier

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Depsgraph(bpy_struct); DisplaceModifier(Modifier).

## Depsgraph(bpy_struct)

### Depsgraph(bpy_struct)

### Dependency graph: Evaluated ID example

The snippet below shows how to reach the evaluated form of an ID — an object, a material, and
so on — starting from its original.
You need this whenever the state you want already reflects animation, constraints, and modifiers.

`text
import bpy

class `OBJECT_OT`_evaluated_example(bpy.types.Operator):
"""Access evaluated object state and do something with it"""
bl_label = "DEG Access Evaluated Object"
bl_idname = "object.evaluated_example"

def execute(self, context):
### This is an original object. Its data does not have any modifiers applied.
obj = context.object
if obj is None or obj.type != 'MESH':
self.report({'INFO'}, "No active mesh object to get info from")
return {'CANCELLED'}
### Evaluated object exists within a specific dependency graph.
### We will request evaluated object from the dependency graph which corresponds to the
### current scene and view layer.
#
### NOTE: This call ensure the dependency graph is fully evaluated. This might be expensive
### if changes were made to the scene, but is needed to ensure no dangling or incorrect
### pointers are exposed.
depsgraph = context.evaluated_depsgraph_get()
### Actually request evaluated object.
#
### This object has animation and drivers applied on it, together with constraints and
### modifiers.
#
### For mesh objects the object.data will be a mesh with all modifiers applied.
### This means that in access to vertices or faces after modifier stack happens via fields of
### object_eval.object.
#
### For other types of objects the object_eval.data does not have modifiers applied on it,
### but has animation applied.
#
### NOTE: All ID types have `evaluated_get()`, including materials, node trees, worlds.
object_eval = obj.evaluated_get(depsgraph)
mesh_eval = object_eval.data
self.report({'INFO'}, f"Number of evaluated vertices: {len(mesh_eval.vertices)}")
return {'FINISHED'}

def register():
bpy.utils.register_class(`OBJECT_OT`_evaluated_example)

def unregister():
bpy.utils.unregister_class(`OBJECT_OT`_evaluated_example)

if __name__ == "__main__":
register()
`

### Dependency graph: Original object example

Here the original ID is reached instead.
That access matters when you need to test whether an object is selected, or to compare pointers.

`text
import bpy

class `OBJECT_OT`_original_example(bpy.types.Operator):
"""Access original object and do something with it"""
bl_label = "DEG Access Original Object"
bl_idname = "object.original_example"

def check_object_selected(self, object_eval):
### Selection depends on a context and is only valid for original objects. This means we need
### to request the original object from the known evaluated one.
#
### NOTE: All ID types have an `original` field.
obj = object_eval.original
return obj.select_get()

def execute(self, context):
### NOTE: It seems redundant to iterate over original objects to request evaluated ones
### just to get original back. But we want to keep example as short as possible, but in real
### world there are cases when evaluated object is coming from a more meaningful source.
depsgraph = context.evaluated_depsgraph_get()
for obj in context.editable_objects:
object_eval = obj.evaluated_get(depsgraph)
if self.check_object_selected(object_eval):
self.report({'INFO'}, f"Object is selected: {object_eval.name}")
return {'FINISHED'}

def register():
bpy.utils.register_class(`OBJECT_OT`_original_example)

def unregister():
bpy.utils.unregister_class(`OBJECT_OT`_original_example)

if __name__ == "__main__":
register()
`

### Dependency graph: Iterate over all object instances

There are times you need every instance together with its matrix — writing an exporter or a
custom render engine, for instance.
The example walks through every object and instance present in the scene.

`text
import bpy

class `OBJECT_OT`_object_instances(bpy.types.Operator):
"""Access original object and do something with it"""
bl_label = "DEG Iterate Object Instances"
bl_idname = "object.object_instances"

def execute(self, context):
depsgraph = context.evaluated_depsgraph_get()
for object_instance in depsgraph.object_instances:
### This is an object which is being instanced.
obj = object_instance.object
### `is_instance` denotes whether the object is coming from instances (as an opposite of
### being an emitting object. )
if not object_instance.is_instance:
print(f"Object {obj.name} at {object_instance.matrix_world}")
else:
### Instanced will additionally have fields like uv, random_id and others which are
### specific for instances. See Python API for DepsgraphObjectInstance for details,
print(f"Instance of {obj.name} at {object_instance.matrix_world}")
return {'FINISHED'}

def register():
bpy.utils.register_class(`OBJECT_OT`_object_instances)

def unregister():
bpy.utils.unregister_class(`OBJECT_OT`_object_instances)

if __name__ == "__main__":
register()
`

### Dependency graph: Object.to_mesh()

A helper that pulls a mesh out of any object carrying geometry. Exporters, render engines, and
tools that want the evaluated mesh as it appears in the viewport reach for it.

Object.to_mesh() is tightly bound to the dependency graph: whether you call it on an original or
an evaluated object changes what you get back.

Called on the original object, the mesh is built without animation or modifiers folded in:

- A mesh comes back roughly as if the source had been duplicated.

- A curve turns off its own modifiers along with those on the objects acting as its bevel and taper.

- A meta-ball yields nothing but an empty mesh, since the polygonization step runs as part of modifier evaluation.

Called on the evaluated object, every modifier is included.

Note

The object owns the resulting mesh. Release it with to_mesh_clear().

Note

Treat the returned mesh as throwaway; it can’t be linked from objects in the main database. For
something that needs to stick around, reach for new_from_object()
instead.

Note

When the object carries no geometry (a camera, say), the function hands back None.

`text
import bpy

class `OBJECT_OT`_object_to_mesh(bpy.types.Operator):
"""Convert selected object to mesh and show number of vertices"""
bl_label = "DEG Object to Mesh"
bl_idname = "object.object_to_mesh"

def execute(self, context):
### Access input original object.
obj = context.object
if obj is None:
self.report({'INFO'}, "No active mesh object to convert to mesh")
return {'CANCELLED'}
### Avoid annoying None checks later on.
if obj.type not in {'MESH', 'CURVE', 'SURFACE', 'FONT', 'META'}:
self.report({'INFO'}, "Object cannot be converted to mesh")
return {'CANCELLED'}
depsgraph = context.evaluated_depsgraph_get()
### Invoke to_mesh() for original object.
mesh_from_orig = obj.to_mesh()
self.report({'INFO'}, f"{len(mesh_from_orig.vertices)} in new mesh without modifiers.")
### Remove temporary mesh.
obj.to_mesh_clear()
### Invoke to_mesh() for evaluated object.
object_eval = obj.evaluated_get(depsgraph)
mesh_from_eval = object_eval.to_mesh()
self.report({'INFO'}, f"{len(mesh_from_eval.vertices)} in new mesh with modifiers.")
### Remove temporary mesh.
object_eval.to_mesh_clear()
return {'FINISHED'}

def register():
bpy.utils.register_class(`OBJECT_OT`_object_to_mesh)

def unregister():
bpy.utils.unregister_class(`OBJECT_OT`_object_to_mesh)

if __name__ == "__main__":
register()
`

### Dependency graph: bpy.data.meshes.new_from_object()

A helper that produces a fresh mesh copied from any object with geometry. The mesh joins the main
database and other objects may reference it. It’s the usual choice for tools that spawn new objects
or bake modifiers down.

Called on the original object, the mesh is built without animation or modifiers folded in:

- With a mesh, the outcome is close to making a copy of the original.

- With a curve, its own modifiers are skipped, as are the modifiers on whatever objects serve as bevel and taper.

- With a meta-ball, the result is empty, because turning it into polygons happens during modifier evaluation.

Called on the evaluated object, every modifier is included.

Every link the mesh holds — materials among them — is pointed back to the original, which keeps the
main database valid and coherent.

Note

When the object carries no geometry (a camera, say), the function hands back None.

`text
import bpy

class `OBJECT_OT`_mesh_from_object(bpy.types.Operator):
"""Convert selected object to mesh and show number of vertices"""
bl_label = "DEG Mesh From Object"
bl_idname = "object.mesh_from_object"

def execute(self, context):
### Access input original object.
obj = context.object
if obj is None:
self.report({'INFO'}, "No active mesh object to convert to mesh")
return {'CANCELLED'}
### Avoid annoying None checks later on.
if obj.type not in {'MESH', 'CURVE', 'SURFACE', 'FONT', 'META'}:
self.report({'INFO'}, "Object cannot be converted to mesh")
return {'CANCELLED'}
depsgraph = context.evaluated_depsgraph_get()
object_eval = obj.evaluated_get(depsgraph)
mesh_from_eval = bpy.data.meshes.new_from_object(object_eval)
self.report({'INFO'}, f"{len(mesh_from_eval.vertices)} in new mesh, and is ready for use!")
return {'FINISHED'}

def register():
bpy.utils.register_class(`OBJECT_OT`_mesh_from_object)

def unregister():
bpy.utils.unregister_class(`OBJECT_OT`_mesh_from_object)

if __name__ == "__main__":
register()
`

### Dependency graph: Simple exporter

Pulling the earlier examples together, this one sketches a minimal exporter script.

`text
import bpy

class `OBJECT_OT`_simple_exporter(bpy.types.Operator):
"""Simple (fake) exporter of selected objects"""
bl_label = "DEG Export Selected"
bl_idname = "object.simple_exporter"

apply_modifiers: bpy.props.BoolProperty(name="Apply Modifiers")

def execute(self, context):
depsgraph = context.evaluated_depsgraph_get()
for object_instance in depsgraph.object_instances:
if not self.is_object_instance_from_selected(object_instance):
### We only export selected objects.
continue
### NOTE: This will create a mesh for every instance, which is not ideal at all. In
### reality destination format will support some sort of instancing mechanism, so the
### code here will simply say "instance this object at object_instance.matrix_world".
mesh = self.create_mesh_for_object_instance(object_instance)
if mesh is None:
### Happens for non-geometry objects.
continue
print(f"Exporting mesh with {len(mesh.vertices)} vertices "
f"at {object_instance.matrix_world}")

self.clear_mesh_for_object_instance(object_instance)

return {'FINISHED'}

def is_object_instance_from_selected(self, object_instance):
### For instanced objects we check selection of their instancer (more accurately: check
### selection status of the original object corresponding to the instancer).
if object_instance.parent:
return object_instance.parent.original.select_get()
### For non-instanced objects we check selection state of the original object.
return object_instance.object.original.select_get()

def create_mesh_for_object_instance(self, object_instance):
if self.apply_modifiers:
return object_instance.object.to_mesh()
else:
return object_instance.object.original.to_mesh()

def clear_mesh_for_object_instance(self, object_instance):
if self.apply_modifiers:
return object_instance.object.to_mesh_clear()
else:
return object_instance.object.original.to_mesh_clear()

def register():
bpy.utils.register_class(`OBJECT_OT`_simple_exporter)

def unregister():
bpy.utils.unregister_class(`OBJECT_OT`_simple_exporter)

if __name__ == "__main__":
register()
`

### Dependency graph: Object.to_curve()

A helper that pulls a curve out of text and curve objects. Exporters, render engines, and tools
that need the curve standing in for the object typically use it.

It expects the evaluated dependency graph as a mandatory argument, plus an optional boolean
apply_modifiers that defaults to false. With apply_modifiers set and a curve object, the spline
deform modifiers act on the control points. Bear in mind that constructive modifiers and ones that
aren’t spline-enabled stay off — so Array won’t run, nor will deform modifiers whose Apply On Spline
option is switched off.

Given a text object, the text becomes a 3D curve and is returned. apply_modifiers carries no weight
for text objects since modifiers never run on them. Hand in anything other than a curve or a text
object and the call reports an error.

Note

The object owns the curve that comes back. Release it through to_curve_clear().

Note

Treat the resulting curve as throwaway; it can’t be referenced from objects in the main
database.

`text
import bpy

class `OBJECT_OT`_object_to_curve(bpy.types.Operator):
"""Convert selected object to curve and show number of splines"""
bl_label = "DEG Object to Curve"
bl_idname = "object.object_to_curve"

def execute(self, context):
### Access input original object.
obj = context.object
if obj is None:
self.report({'INFO'}, "No active object to convert to curve")
return {'CANCELLED'}
if obj.type not in {'CURVE', 'FONT'}:
self.report({'INFO'}, "Object cannot be converted to curve")
return {'CANCELLED'}
depsgraph = context.evaluated_depsgraph_get()
### Invoke to_curve() without applying modifiers.
curve_without_modifiers = obj.to_curve(depsgraph)
self.report({'INFO'}, f"{len(curve_without_modifiers.splines)} splines in a new curve without modifiers.")
### Remove temporary curve.
obj.to_curve_clear()
### Invoke to_curve() with applying modifiers.
curve_with_modifiers = obj.to_curve(depsgraph, apply_modifiers=True)
self.report({'INFO'}, f"{len(curve_with_modifiers.splines)} splines in new curve with modifiers.")
### Remove temporary curve.
obj.to_curve_clear()
return {'FINISHED'}

def register():
bpy.utils.register_class(`OBJECT_OT`_object_to_curve)

def unregister():
bpy.utils.unregister_class(`OBJECT_OT`_object_to_curve)

if __name__ == "__main__":
register()
`

base class — bpy_struct

class bpy.types. Depsgraph ( bpy_struct )

ids

Every data-block in its evaluated form (default None, readonly)

Type :

bpy_prop_collection[ID]

mode

Which evaluation mode is in effect (default 'VIEWPORT' , readonly)

- VIEWPORT
Viewport – Non-rendered viewport mode.

- RENDER
Render – Render.

Type :

Literal[‘VIEWPORT’, ‘RENDER’]

object_instances

Every object instance up for display or render (Warning: Treat this strictly as an iterator rather than a sequence, and hold on to no references to the items it yields) (default None, readonly)

Type :

bpy_prop_collection[DepsgraphObjectInstance]

objects

The dependency graph’s evaluated objects (default None, readonly)

Type :

bpy_prop_collection[Object]

scene

The original scene this dependency graph was built around (readonly)

Type :

Scene

scene_eval

The scene in its evaluated form (readonly)

Type :

Scene

updates

Changes affecting data-blocks (default None, readonly)

Type :

bpy_prop_collection[DepsgraphUpdate]

view_layer

The original view layer this dependency graph was built around (readonly)

Type :

ViewLayer

view_layer_eval

The view layer in its evaluated form (readonly)

Type :

ViewLayer

debug_relations_graphviz ( * , filepath = '' )

debug_relations_graphviz

Parameters :

filepath ( str ) – File Name, Optional output path for the graphviz debug file (optional, never None)

Returns :

Dot Graph, Graph in dot format

Return type :

str

debug_stats_gnuplot ( filepath , output_filepath )

debug_stats_gnuplot

Parameters :

- filepath ( str ) – File Name, Output path for the gnuplot debug file (never None)

- output_filepath ( str ) – Output File Name, File name where gnuplot script will save the result (never None)

debug_tag_update ( )

debug_tag_update

debug_stats ( )

Report the number of elements in the Dependency Graph

Returns :

result, (never None)

Return type :

str

update ( )

Recompute whatever data-blocks have changed — animation or modifiers, for example. Doing this throws away every reference to evaluated data-blocks held by this dependency graph.

id_eval_get ( id )

id_eval_get

Parameters :

id (ID) – Original ID to get evaluated complementary part for

Returns :

Evaluated ID for the given original one

Return type :

ID

id_type_updated ( id_type )

id_type_updated

Parameters :

id_type (Literal[Id Type Items]) – ID Type

Returns :

Updated, True if any data-block with this type was added, updated or removed

Return type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendDataMeshes.new_from_object Context.evaluated_depsgraph_get ID.evaluated_get Object.calc_matrix_camera Object.camera_fit_coords Object.closest_point_on_mesh Object.crazyspace_eval Object.ray_cast Object.to_curve | Object.to_mesh RenderEngine.bake RenderEngine.draw RenderEngine.render RenderEngine.update RenderEngine.view_draw RenderEngine.view_update Scene.ray_cast ViewLayer.depsgraph |

## DisplaceModifier(Modifier)

### DisplaceModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. DisplaceModifier ( Modifier )

Pushes vertices around to displace the surface.

direction

(default 'NORMAL' )

- X
X – Drive displacement along X using the texture’s intensity.

- Y
Y – Drive displacement along Y using the texture’s intensity.

- Z
Z – Drive displacement along Z using the texture’s intensity.

- NORMAL
Normal – Drive displacement along the vertex normal using the texture’s intensity.

- `CUSTOM_NORMAL`
Custom Normal – Drive displacement along the (averaged) custom normal using the texture’s intensity, dropping back to the vertex normal when unavailable.

- `RGB_TO_XYZ`
RGB to XYZ – Map the texture’s RGB channels onto XYZ to displace the mesh.

Type :

Literal[‘X’, ‘Y’, ‘Z’, ‘NORMAL’, ‘`CUSTOM_NORMAL`’, ‘`RGB_TO_XYZ`’]

invert_vertex_group

Reverses the effect of the vertex group (default False)

Type :

bool

mid_level

The texture value at which no displacement happens (in [-inf, inf], default 0.5)

Type :

float

space

(default 'LOCAL' )

- LOCAL
Local – The direction is expressed in local coordinates.

- GLOBAL
Global – The direction is expressed in global coordinates.

Type :

Literal[‘LOCAL’, ‘GLOBAL’]

strength

How far the geometry gets pushed (in [-inf, inf], default 1.0)

Type :

float

texture

Type :

Texture

texture_coords

(default 'LOCAL' )

- LOCAL
Local – Take texture coordinates from the local coordinate system.

- GLOBAL
Global – Take texture coordinates from the global coordinate system.

- OBJECT
Object – Take texture coordinates from the linked object’s local coordinate system.

- UV
UV – Take texture coordinates from the UVs.

Type :

Literal[‘LOCAL’, ‘GLOBAL’, ‘OBJECT’, ‘UV’]

texture_coords_bone

The bone that supplies the texture coordinates (default “”, never None)

Type :

str

texture_coords_object

The object that supplies the texture coordinates

Type :

Object

uv_layer

Name of the UV map (default “”, never None)

Type :

str

vertex_group

Names the vertex group that scales the modifier’s effect at each point (default “”, never None)

Type :

str

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## See also

- [Bpy Struct](bpy-struct.md)
