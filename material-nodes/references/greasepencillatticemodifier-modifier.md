# Greasepencillatticemodifier Modifier, Greasepencillayer Greasepenciltreenode, Greasepencillengthmodifier Modifier, Greasepencillineartmodifier Modifier

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: GreasePencilLatticeModifier(Modifier); GreasePencilLayer(GreasePencilTreeNode); GreasePencilLengthModifier(Modifier); GreasePencilLineartModifier(Modifier).

## GreasePencilLatticeModifier(Modifier)

### GreasePencilLatticeModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilLatticeModifier ( Modifier )

Bends strokes by way of a lattice object.

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

invert_vertex_group

Flip the weights of the vertex group (default False)

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

object

Lattice object to deform with

Type :

Object

open_influence_panel

(default False)

Type :

bool

strength

Strength of modifier effect (in [-inf, inf], default 1.0)

Type :

float

tree_node_filter

Layer name (default “”, never None)

Type :

str

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

vertex_group_name

Name of the vertex group that scales the deformation (default “”, never None)

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

## GreasePencilLayer(GreasePencilTreeNode)

### GreasePencilLayer(GreasePencilTreeNode)

base classes — bpy_struct, GreasePencilTreeNode

class bpy.types. GreasePencilLayer ( GreasePencilTreeNode )

Collection of related drawings

blend_mode

Blend mode (default 'REGULAR' )

Type :

Literal[‘REGULAR’, ‘HARDLIGHT’, ‘ADD’, ‘SUBTRACT’, ‘MULTIPLY’, ‘DIVIDE’]

frames

Grease Pencil frames (default None, readonly)

Type :

GreasePencilFrames[GreasePencilFrame]

ignore_locked_materials

Permit editing strokes that rely on locked materials (default False)

Type :

bool

lock_frame

Lock current frame displayed by layer (default False)

Type :

bool

mask_layers

List of Masking Layers (default None, readonly)

Type :

GreasePencilLayerMasks[GreasePencilLayerMask]

matrix_local

Local transformation matrix of the layer (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)), readonly)

Type :

mathutils.Matrix

matrix_parent_inverse

Inverse of layer’s parent transformation matrix (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)), readonly)

Type :

mathutils.Matrix

opacity

Layer Opacity (in [0, 1], default 0.0)

Type :

float

parent

Parent object

Type :

Object

parent_bone

Name of parent bone. Only used when the parent object is an armature. (default “”, never None)

Type :

str

pass_index

Index number for the “Layer Index” pass (in [0, inf], default 0)

Type :

int

radius_offset

Radius change to apply to current strokes (in [-inf, inf], default 0.0)

Type :

float

rotation

Euler rotation of the layer (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Euler

scale

Scale of the layer (array of 3 items, in [-inf, inf], default (1.0, 1.0, 1.0))

Type :

mathutils.Vector

tint_color

Color for tinting stroke colors (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

tint_factor

Factor of tinting color (in [0, 1], default 0.0)

Type :

float

translation

Translation of the layer (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

use_lights

Let lights act on the stroke and fill materials (default False)

Type :

bool

use_viewlayer_masks

Bring the mask layers into the view-layer render (default True)

Type :

bool

viewlayer_render

Restrict this Layer to the named View Layer render output; leave empty to always include it (default “”, never None)

Type :

str

get_frame_at ( frame_number )

Get the frame at given frame number

Parameters :

frame_number ( int ) – Frame Number, (in [-1048574, 1048574])

Returns :

Frame

Return type :

GreasePencilFrame

current_frame ( )

The Grease Pencil frame at the current scene time on this layer

Return type :

GreasePencilFrame

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

| bpy_struct.id_data GreasePencilTreeNode.name GreasePencilTreeNode.hide GreasePencilTreeNode.lock GreasePencilTreeNode.select GreasePencilTreeNode.use_onion_skinning | GreasePencilTreeNode.use_masks GreasePencilTreeNode.channel_color GreasePencilTreeNode.next_node GreasePencilTreeNode.prev_node GreasePencilTreeNode.parent_group |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values GreasePencilTreeNode.bl_rna_get_subclass GreasePencilTreeNode.bl_rna_get_subclass_py |

### References

| GreasePencil.layers GreasePencilv3Layers.active GreasePencilv3Layers.move GreasePencilv3Layers.move_bottom | GreasePencilv3Layers.move_to_layer_group GreasePencilv3Layers.move_top GreasePencilv3Layers.new GreasePencilv3Layers.remove |

## GreasePencilLengthModifier(Modifier)

### GreasePencilLengthModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilLengthModifier ( Modifier )

Lengthens or shortens strokes.

end_factor

Length added to the end of each stroke, scaled by its own length (in [-inf, inf], default 0.1)

Type :

float

end_length

Length added to the end of each stroke in absolute units (in [-inf, inf], default 0.1)

Type :

float

invert_curvature

Flip the curvature of the stroke’s extension (default False)

Type :

bool

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

max_angle

When working out the extrapolation shape, disregard stroke points whose neighbors differ by more than this angle (in [0, 3.14159], default 2.96706)

Type :

float

mode

Picks how length is measured (default 'RELATIVE' )

- RELATIVE
Relative – Length in ratio to the stroke’s length.

- ABSOLUTE
Absolute – Length in geometry space.

Type :

Literal[‘RELATIVE’, ‘ABSOLUTE’]

open_curvature_panel

(default False)

Type :

bool

open_influence_panel

(default False)

Type :

bool

open_random_panel

(default False)

Type :

bool

overshoot_factor

Sets which fraction of the stroke feeds the extension calculation (in [0, 1], default 0.1)

Type :

float

point_density

Total number of added points, found by multiplying this by Start/End (in [0.1, 1000], default 30.0)

Type :

float

random_end_factor

Amount of random length tacked onto the end of each stroke (in [-inf, inf], default 0.0)

Type :

float

random_offset

Gently shift each stroke’s random value (in [-inf, inf], default 0.0)

Type :

float

random_start_factor

Amount of random length tacked onto the start of each stroke (in [-inf, inf], default 0.0)

Type :

float

seed

Random seed (in [0, inf], default 0)

Type :

int

segment_influence

Sets how much each segment’s length sways the final curvature; raising it lets short segments matter less overall. (in [-2, 3], default 0.0)

Type :

float

start_factor

Length added to the start of each stroke, scaled by its own length (in [-inf, inf], default 0.1)

Type :

float

start_length

Length added to the start of each stroke in absolute units (in [-inf, inf], default 0.1)

Type :

float

step

Number of frames between randomization steps (in [1, 100], default 4)

Type :

int

tree_node_filter

Layer name (default “”, never None)

Type :

str

use_curvature

Trace the curvature of the stroke (default True)

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

use_random

Let values vary randomly over time (default False)

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

## GreasePencilLineartModifier(Modifier)

### GreasePencilLineartModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilLineartModifier ( Modifier )

Produces Line Art strokes out of a chosen source.

chaining_image_threshold

Segments closer than this in image distance get joined into one chain (in [0, 0.3], default 0.001)

Type :

float

crease_threshold

Any angle under this value counts as a crease. Crease angle priority: object Line Art crease override > mesh auto smooth angle > Line Art default crease. (in [0, 3.14159], default 2.44346)

Type :

float

invert_source_vertex_group

Flip the source vertex group values (default False)

Type :

bool

is_baked

This modifier holds baked data (default False)

Type :

bool

level_end

Largest occlusion count allowed for the generated strokes (in [0, 128], default 0)

Type :

int

level_start

Smallest occlusion count allowed for the generated strokes (in [0, 128], default 0)

Type :

int

light_contour_object

Generate the light contour from this light object

Type :

Object

opacity

Strength value applied to the generated strokes (in [0, 1], default 1.0)

Type :

float

overscan

Padding that keeps strokes from cutting off sharply at the image edge (in [0, 0.5], default 0.1)

Type :

float

radius

Radius given to the generated strokes (in [0, 1], default 0.0025)

Type :

float

shadow_camera_far

Far clipping distance of shadow camera (in [0, 10000], default 200.0)

Type :

float

shadow_camera_near

Near clipping distance of shadow camera (in [0, 10000], default 0.1)

Type :

float

shadow_camera_size

Acts as the “Orthographic Scale” of an orthographic camera. Placing that camera at the light’s position with this scale defines how far the shadow “camera” reaches. (in [0, 10000], default 200.0)

Type :

float

shadow_region_filtering

Pick feature lines coming from lit or shaded areas. Cast shadow and light contour stay unaffected because they lie on the border. (default 'NONE' )

- NONE
None – Not filtering any lines based on illumination region.

- ILLUMINATED
Illuminated – Only selecting lines from illuminated regions.

- SHADED
Shaded – Only selecting lines from shaded regions.

- `ILLUMINATED_ENCLOSED`
Illuminated (Enclosed Shapes) – Selecting lines from lit regions, and make the combination of contour, light contour and shadow lines into enclosed shapes.

Type :

Literal[‘NONE’, ‘ILLUMINATED’, ‘SHADED’, ‘`ILLUMINATED_ENCLOSED`’]

silhouette_filtering

Pick either contour or silhouette (default 'NONE' )

Type :

Literal[‘NONE’, ‘GROUP’, ‘INDIVIDUAL’]

smooth_tolerance

How strongly jagged chains get smoothed (in [0, 30], default 0.0)

Type :

float

source_camera

Use the named camera object when generating Line Art strokes

Type :

Object

source_collection

Build strokes from the objects within this collection

Type :

Collection

source_object

Build strokes from this object

Type :

Object

source_type

Line Art stroke source type (default 'COLLECTION' )

Type :

Literal[‘COLLECTION’, ‘OBJECT’, ‘SCENE’]

source_vertex_group

Match against the start of vertex group names on mesh objects; an empty value matches everything (default “”, never None)

Type :

str

split_angle

Screen-space angle under which a stroke gets divided in two (in [0, 3.14159], default 0.0)

Type :

float

stroke_depth_offset

Nudge strokes a little toward the camera to dodge clipping while keeping viewport depth (in [-0.1, inf], default 0.05)

Type :

float

target_layer

Grease Pencil layer the generated strokes get assigned to (default “”, never None)

Type :

str

target_material

Grease Pencil material given to the generated strokes

Type :

Material

use_back_face_culling

Drop every back face to run faster; doing so puts edges at different occlusion levels than when left off (default False)

Type :

bool

use_cache

Reuse cached scene data from the first Line Art modifier in the stack; some settings then become unavailable. (default False)

Type :

bool

use_clip_plane_boundaries

Let lines produced by the near/far clipping plane appear (default True)

Type :

bool

use_contour

Build strokes from contour lines (default False)

Type :

bool

use_crease

Build strokes from creased edges (default False)

Type :

bool

use_crease_on_sharp

Let crease show on sharp edges (default True)

Type :

bool

use_crease_on_smooth

Let crease edges appear within smooth surfaces (default False)

Type :

bool

use_custom_camera

Swap the active camera for a custom one (default False)

Type :

bool

use_detail_preserve

Hold onto the zig-zag “noise” during initial chaining (default False)

Type :

bool

use_edge_mark

Build strokes from Freestyle marked edges (default False)

Type :

bool

use_edge_overlap

Let edges sharing one location (e.g. from edge split) display correctly. May run slower. (default False)

Type :

bool

use_face_mark

Use Freestyle face marks to filter feature lines (default False)

Type :

bool

use_face_mark_boundaries

Filter feature lines according to face mark boundaries (default False)

Type :

bool

use_face_mark_invert

Flip the face mark filtering (default False)

Type :

bool

use_face_mark_keep_contour

Hold onto contour lines during filtering (default True)

Type :

bool

use_fuzzy_all

Handle every line as one line type so they all chain together (default False)

Type :

bool

use_fuzzy_intersections

Handle intersection and contour lines as the same type so they can chain together (default False)

Type :

bool

use_geometry_space_chain

Chain using geometry distance rather than image space (default False)

Type :

bool

use_image_boundary_trimming

Cut every edge exactly at the image boundary, overscan region included (default False)

Type :

bool

use_intersection

Build strokes from intersections (default False)

Type :

bool

use_intersection_mask

Mask bits to match from Collection Line Art settings (array of 8 items, default (False, False, False, False, False, False, False, False))

Type :

bpy_prop_array[bool]

use_intersection_match

Demand that every intersection mask match instead of only one (default False)

Type :

bool

use_invert_collection

Pick everything apart from the lines in the named collection (default False)

Type :

bool

use_invert_silhouette

Pick the anti-silhouette lines (default False)

Type :

bool

use_light_contour

Build light/shadow separation lines from a reference light object (default False)

Type :

bool

use_loose

Build strokes from loose edges (default False)

Type :

bool

use_loose_as_contour

Give loose edges the contour type (default False)

Type :

bool

use_loose_edge_chain

Let loose edges be chained together (default False)

Type :

bool

use_material

Build strokes from the borders between materials (default False)

Type :

bool

use_material_mask

Apply material masks to drop occluded strokes (default False)

Type :

bool

use_material_mask_bits

Mask bits to match from Material Line Art settings (array of 8 items, default (False, False, False, False, False, False, False, False))

Type :

bpy_prop_array[bool]

use_material_mask_match

Demand that every material mask match instead of only one (default False)

Type :

bool

use_multiple_levels

Build strokes across a span of occlusion levels (default False)

Type :

bool

use_object_instances

Let particle objects and face/vertex instances show up in Line Art (default True)

Type :

bool

use_offset_towards_custom_camera

Offset strokes toward the chosen camera rather than the active one (default False)

Type :

bool

use_output_vertex_group_match_by_name

Match the output vertex group by its name (default True)

Type :

bool

use_overlap_edge_type_support

Permit a single edge to carry several overlapping types, producing one stroke per overlapping type. (default False)

Type :

bool

use_shadow

Cast contour lines using a light source object (default False)

Type :

bool

vertex_group

Vertex group name for selected strokes (default “”, never None)

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
