# Geometryset, Gpencilsculptsettings Bpy Struct, Gppaint Paint, Greasepencil Id ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: GeometrySet; GPencilSculptSettings(bpy_struct); GpPaint(Paint); GreasePencil(ID); GreasePencilArrayModifier(Modifier).

## GeometrySet

### GeometrySet

### Accessing Evaluated Geometry

`	ext
import bpy

### The GeometrySet can only be retrieved from an evaluated object. So one always
### needs a depsgraph that has evaluated the object.
depsgraph = bpy.context.view_layer.depsgraph
ob = bpy.context.active_object
ob_eval = depsgraph.id_eval_get(ob)

### Get the final evaluated geometry of an object.
geometry = ob_eval.evaluated_geometry()

### Print basic information like the number of elements.
print(geometry)

### A geometry set may have a name. It can be set with the Set Geometry Name node.
print(geometry.name)

### Access "realized" geometry components.
print(geometry.mesh)
print(geometry.pointcloud)
print(geometry.curves)
print(geometry.volume)
print(geometry.grease_pencil)

### Access the mesh without final subdivision applied.
print(geometry.mesh_base)

### Accessing instances is a bit more tricky, because there is no specific
### mechanism to expose instances. Instead, two accessors are provided which
### are easy to keep working in the future even if we get a proper Instances type.

### This is a pointcloud that provides access to all the instance attributes.
### There is a point per instances. May return None if there is no instances data.
instances_pointcloud = geometry.instances_pointcloud()

if instances_pointcloud is not None:
### This is a list containing the data that is instanced. The list may contain
### None, objects, collections or other GeometrySets. If the geometry does not
### have instances, the list is empty.
references = geometry.instance_references()

### Besides normal generic attributes, there are also two important
### instance-specific attributes. "instance_transform" is a 4x4 matrix attribute
### containing the transforms of each instance.
instance_transforms = instances_pointcloud.attributes["instance_transform"]

### ".reference_index" contains indices into the `references` list above and
### determines what geometry each instance uses.
reference_indices = instances_pointcloud.attributes[".reference_index"]
`

class GeometrySet

Holds several geometry components, possibly of different kinds, together — for instance a mesh alongside curves and nested instances.

instance_references ( )

Returns the list of geometries that the .reference_index attribute on the pointcloud from bpy.types.GeometrySet.instances_pointcloud() points into. Entries may be other geometry sets, objects, collections, or None.

Return type :

list[None | bpy.types.Object | bpy.types.Collection | bpy.types.GeometrySet]

instances_pointcloud ( )

Hands back a pointcloud describing the geometry’s instances, which you should treat as read-only. Each instance gets one point, and its per-instance data lives in the point attributes. Local transforms are kept in the instance_transform attribute, and the .reference_index attribute names what each point instances by indexing into the list from bpy.types.GeometrySet.instance_references() .

Return type :

bpy.types.PointCloud

curves

Within the geometry set, the curves data-block.

Type :

bpy.types.Curves

grease_pencil

Within the geometry set, the Grease Pencil data-block.

Type :

bpy.types.GreasePencil

mesh

Within the geometry set, the mesh data-block.

Type :

bpy.types.Mesh

mesh_base

Within the geometry set, the mesh data-block before final subdivision is applied.

Type :

bpy.types.Mesh

name

A non-unique label for the geometry set, handy mainly while debugging.

Type :

str

pointcloud

Within the geometry set, the point-cloud data-block.

Type :

bpy.types.PointCloud

volume

Within the geometry set, the volume data-block.

Type :

bpy.types.Volume

static from_evaluated_object ( evaluated_object )

Produces a geometry set out of an evaluated object’s evaluated geometry; usually bpy.types.Object.evaluated_geometry() is the handier route.

Parameters :

evaluated_object (bpy.types.Object) – The object, already evaluated, that the geometry set is built from.

## GPencilSculptSettings(bpy_struct)

### GPencilSculptSettings(bpy_struct)

base class — bpy_struct

class bpy.types. GPencilSculptSettings ( bpy_struct )

Shared properties for the Grease Pencil stroke-sculpting tools.

guide

(readonly)

Type :

GPencilSculptGuide

intersection_threshold

Cutoff that governs where strokes intersect (in [0, 10], default 0.1)

Type :

float

lock_axis

(default 'VIEW' )

- VIEW
View – Align strokes with the view plane as it currently sits.

- `AXIS_Y`
Front (X-Z) – Drop strokes onto the plane locked to Y.

- `AXIS_X`
Side (Y-Z) – Drop strokes onto the plane locked to X.

- `AXIS_Z`
Top (X-Y) – Drop strokes onto the plane locked to Z.

- CURSOR
Cursor – Align strokes with the 3D cursor’s present orientation.

Type :

Literal[‘VIEW’, ‘`AXIS_Y`’, ‘`AXIS_X`’, ‘`AXIS_Z`’, ‘CURSOR’]

multiframe_falloff_curve

A custom curve that shapes how the brush effect falls off across Grease Pencil frames (readonly)

Type :

CurveMapping

thickness_primitive_curve

A custom curve that shapes primitive thickness (readonly)

Type :

CurveMapping

use_automasking_layer_active

Restrict the effect to the active layer alone (default False)

Type :

bool

use_automasking_layer_stroke

Restrict the effect to strokes beneath the cursor (default False)

Type :

bool

use_automasking_material_active

Restrict the effect to the active material alone (default False)

Type :

bool

use_automasking_material_stroke

Restrict the effect to strokes beneath the cursor (default False)

Type :

bool

use_automasking_stroke

Restrict the effect to strokes beneath the cursor (default False)

Type :

bool

use_multiframe_falloff

While editing in multiframe mode, apply a falloff so the brush effect is weighted per frame (default False)

Type :

bool

use_scale_thickness

Let stroke thickness scale along as strokes are transformed (default False)

Type :

bool

use_thickness_curve

Drive primitive stroke thickness from a curve (default False)

Type :

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

| ToolSettings.gpencil_sculpt | |

## GpPaint(Paint)

### GpPaint(Paint)

base classes — bpy_struct, Paint

class bpy.types. GpPaint ( Paint )

color_mode

Paint Mode (default 'MATERIAL' )

- MATERIAL
Material – Paint with the active material’s base color.

- VERTEXCOLOR
Color Attribute – Paint the material using a color attribute.

Type :

Literal[‘MATERIAL’, ‘VERTEXCOLOR’]

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

| bpy_struct.id_data Paint.brush Paint.brush_asset_reference Paint.eraser_brush Paint.eraser_brush_asset_reference Paint.palette Paint.show_brush Paint.show_brush_on_surface Paint.show_low_resolution Paint.use_sculpt_delay_updates Paint.show_bvh_nodes Paint.use_symmetry_x Paint.use_symmetry_y | Paint.use_symmetry_z Paint.use_symmetry_feather Paint.cavity_curve Paint.use_cavity Paint.tile_offset Paint.tile_x Paint.tile_y Paint.tile_z Paint.show_strength_curve Paint.show_size_curve Paint.show_jitter_curve Paint.unified_paint_settings |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Paint.bl_rna_get_subclass Paint.bl_rna_get_subclass_py |

### References

| ToolSettings.gpencil_paint | |

## GreasePencil(ID)

### GreasePencil(ID)

base classes — bpy_struct, ID

class bpy.types. GreasePencil ( ID )

Data-block holding Grease Pencil data.

after_color

Tint used for ghost frames drawn after the active one (array of 3 items, in [0, 1], default (0.12549, 0.082353, 0.529412))

Type :

mathutils.Color

animation_data

Animation data attached to this data-block (readonly)

Type :

AnimData

attributes

Geometry attributes (default None, readonly)

Type :

AttributeGroupGreasePencil[Attribute]

before_color

Tint used for ghost frames drawn ahead of the active one (array of 3 items, in [0, 1], default (0.145098, 0.419608, 0.137255))

Type :

mathutils.Color

color_attributes

Geometry color attributes (default None, readonly)

Type :

AttributeGroupGreasePencil[Attribute]

ghost_after_range

How many frames at most are shown following the current one (0 hides every later frame) (in [0, 120], default 1)

Type :

int

ghost_before_range

How many frames at most are shown preceding the current one (0 hides every earlier frame) (in [0, 120], default 1)

Type :

int

layer_groups

Grease Pencil layer groups (default None, readonly)

Type :

GreasePencilv3LayerGroup[GreasePencilLayerGroup]

layers

Grease Pencil layers (default None, readonly)

Type :

GreasePencilv3Layers[GreasePencilLayer]

materials

(default None, readonly)

Type :

IDMaterials[Material]

onion_factor

Adjusts the fade opacity of the onion frames that are shown (in [0, 1], default 0.5)

Type :

float

onion_keyframe_type

Keyframe category used as a filter (default 'ALL' )

- ALL
All – Include all Keyframe types.

- KEYFRAME
Keyframe – Normal keyframe, e.g. for key poses.

- BREAKDOWN
Breakdown – A breakdown pose, e.g. for transitions between key poses.

- `MOVING_HOLD`
Moving Hold – A keyframe that is part of a moving hold.

- EXTREME
Extreme – An ‘extreme’ pose, or some other purpose as needed.

- JITTER
Jitter – A filler or baked keyframe for keying on ones, or some other purpose as needed.

- GENERATED
Generated – A key generated automatically by a tool, not manually created.

Type :

Literal[‘ALL’, ‘KEYFRAME’, ‘BREAKDOWN’, ‘`MOVING_HOLD`’, ‘EXTREME’, ‘JITTER’, ‘GENERATED’]

onion_mode

Which frames the onion display draws (default 'ABSOLUTE' )

- ABSOLUTE
Frames – Frames in absolute range of the scene frame.

- RELATIVE
Keyframes – Frames in relative range of the Grease Pencil keyframes.

- SELECTED
Selected – Only selected keyframes.

Type :

Literal[‘ABSOLUTE’, ‘RELATIVE’, ‘SELECTED’]

root_nodes

Top-level nodes of the layer tree, listed in stack order so the first entry sits at the bottom of the tree. (default None, readonly)

Type :

bpy_prop_collection[GreasePencilTreeNode]

stroke_depth_order

Controls how strokes are sorted in 3D for objects that are not drawn ‘In Front’ (default '2D' )

Type :

Literal[Stroke Depth Order Items]

use_autolock_layers

Lock every layer apart from the active one so other layers aren’t changed by mistake (default False)

Type :

bool

use_ghost_custom_colors

Apply user-chosen colors to the ghost frames (default False)

Type :

bool

use_onion_fade

Draw onion keyframes with a gradual fade in transparency (default False)

Type :

bool

use_onion_loop

Show onion keyframes suited to looping animation (default False)

Type :

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| bpy.context.annotation_data bpy.context.gpencil bpy.context.grease_pencil | BlendData.grease_pencils BlendDataGreasePencilsV3.new BlendDataGreasePencilsV3.remove |

## GreasePencilArrayModifier(Modifier)

### GreasePencilArrayModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilArrayModifier ( Modifier )

Builds a grid of repeated instances.

constant_offset

Spacing applied between successive items (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

count

Number of items (in [1, 32767], default 2)

Type :

int

invert_layer_filter

Flip the layer filter (default False)

Type :

bool

invert_layer_pass_filter

Flip the layer pass filter (default False)

Type :

bool

invert_material_filter

Flip the material filter (default False)

Type :

bool

invert_material_pass_filter

Flip the material pass filter (default False)

Type :

bool

layer_pass_filter

Layer pass filter (in [0, 100], default 0)

Type :

int

material_filter

Material used for filtering

Type :

Material

material_pass_filter

Material pass (in [0, 100], default 0)

Type :

int

offset_object

Take another object’s position and rotation to set how far apart and how much rotated the arrayed copies are

Type :

Object

open_constant_offset_panel

(default False)

Type :

bool

open_influence_panel

(default False)

Type :

bool

open_object_offset_panel

(default False)

Type :

bool

open_randomize_panel

(default False)

Type :

bool

open_relative_offset_panel

(default False)

Type :

bool

random_offset

Amount by which location varies (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

random_rotation

Amount by which rotation varies (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Euler

random_scale

Amount by which scale varies (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

relative_offset

Spacing between arrayed items scaled by the geometry’s own size (array of 3 items, in [-inf, inf], default (1.0, 0.0, 0.0))

Type :

mathutils.Vector

replace_material

Material index applied to generated strokes (0 retains the original material) (in [0, 32767], default 0)

Type :

int

seed

Random seed (in [0, inf], default 1)

Type :

int

tree_node_filter

Layer name (default “”, never None)

Type :

str

use_constant_offset

Turn on offsetting (default False)

Type :

bool

use_layer_group_filter

Filter by layer group name (default False)

Type :

bool

use_layer_pass_filter

Use layer pass filter (default False)

Type :

bool

use_material_pass_filter

Use material pass filter (default False)

Type :

bool

use_object_offset

Fold another object’s transform into the overall offset (default False)

Type :

bool

use_relative_offset

Apply an offset that scales with the object’s bounding box (default True)

Type :

bool

use_uniform_random_scale

Share one random seed across every scale axis for uniform scaling (default False)

Type :

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## See also

- [Bpy Struct](bpy-struct.md)
