# Collisionmodifier Modifier, Correctivesmoothmodifier Modifier, Curvemodifier Modifier, Datatransfermodifier Modifier ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: CollisionModifier(Modifier); CorrectiveSmoothModifier(Modifier); CurveModifier(Modifier); DataTransferModifier(Modifier); DecimateModifier(Modifier); DepsgraphObjectInstance(bpy_struct); DynamicPaintModifier(Modifier); EdgeSplitModifier(Modifier).

## CollisionModifier(Modifier)

### CollisionModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. CollisionModifier ( Modifier )

A modifier that marks where in the modifier stack collision is evaluated

settings

(readonly, never None)

Type :

CollisionSettings

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

## CorrectiveSmoothModifier(Modifier)

### CorrectiveSmoothModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. CorrectiveSmoothModifier ( Modifier )

Counteract the distortion that deformation introduces.

factor

Strength of the smoothing pass (in [-inf, inf], default 0.5)

Type :

float

invert_vertex_group

Flip the weighting of the vertex group (default False)

Type :

bool

is_bind

(default False, readonly)

Type :

bool

iterations

(in [0, 32767], default 5)

Type :

int

rest_source

Pick where the rest positions are taken from (default 'ORCO' )

- ORCO
Original Coords – Take rest positions from the base mesh's own vertex coordinates.

- BIND
Bind Coords – Take rest positions from the bound vertex coordinates instead.

Type :

Literal['ORCO', 'BIND']

scale

Counterbalance any scaling applied by modifiers further up the stack (in [-inf, inf], default 1.0)

Type :

float

smooth_type

Which algorithm carries out the smoothing (default 'SIMPLE' )

- SIMPLE
Simple – Average the neighbouring edge-vertices together.

- `LENGTH_WEIGHTED`
Length Weight – Average the neighbouring edge-vertices, but weight each by edge length.

Type :

Literal['SIMPLE', '`LENGTH_WEIGHTED`']

use_only_smooth

Smooth the mesh but skip rebuilding the surface (default False)

Type :

bool

use_pin_boundary

Hold boundary vertices fixed so they aren't smoothed (default False)

Type :

bool

vertex_group

The vertex group whose weights set the modifier's per-point strength (default "", never None)

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

## CurveModifier(Modifier)

### CurveModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. CurveModifier ( Modifier )

A modifier that bends geometry along a curve.

deform_axis

Along which axis the curve does its deforming (default '`POS_X`' )

Type :

Literal['`POS_X`', '`POS_Y`', '`POS_Z`', '`NEG_X`', '`NEG_Y`', '`NEG_Z`']

invert_vertex_group

Flip the weighting of the vertex group (default False)

Type :

bool

object

Curve object to deform with

Type :

Object

vertex_group

The vertex group whose weights set the modifier's per-point strength (default "", never None)

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

## DataTransferModifier(Modifier)

### DataTransferModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. DataTransferModifier ( Modifier )

Copies selected data across from one mesh onto another.

data_types_edges

Selects which edge layers get copied over (default set())

- `SHARP_EDGE`
Sharp – Carry across the sharp-edge marking.

- SEAM
UV Seam – Carry across the UV seam marking.

- CREASE
Crease – Carry across subdivision crease values.

- `BEVEL_WEIGHT_EDGE`
Bevel Weight – Carry across bevel weighting.

- `FREESTYLE_EDGE`
Freestyle – Carry across the Freestyle edge marking.

Type :

set[Literal[‘`SHARP_EDGE`’, ‘SEAM’, ‘CREASE’, ‘`BEVEL_WEIGHT_EDGE`’, ‘`FREESTYLE_EDGE`’]]

data_types_loops

Selects which face-corner layers get copied over (default set())

- `CUSTOM_NORMAL`
Custom Normals – Carry across the custom normals.

- `COLOR_CORNER`
Colors – Carry across color attributes.

- UV
UVs – Carry across UV layers.

Type :

set[Literal[‘`CUSTOM_NORMAL`’, ‘`COLOR_CORNER`’, ‘UV’]]

data_types_polys

Selects which face layers get copied over (default set())

- SMOOTH
Smooth – Carry across the flat/smooth marking.

- `FREESTYLE_FACE`
Freestyle Mark – Carry across the Freestyle face marking.

Type :

set[Literal[‘SMOOTH’, ‘`FREESTYLE_FACE`’]]

data_types_verts

Selects which vertex layers get copied over (default set())

- `VGROUP_WEIGHTS`
Vertex Groups – Carry across the active vertex group or all of them.

- `BEVEL_WEIGHT_VERT`
Bevel Weight – Carry across bevel weighting.

- `COLOR_VERTEX`
Colors – Carry across color attributes.

Type :

set[Literal[‘`VGROUP_WEIGHTS`’, ‘`BEVEL_WEIGHT_VERT`’, ‘`COLOR_VERTEX`’]]

edge_mapping

Chooses how source edges get paired with destination edges (default 'NEAREST' )

Type :

Literal[Dt Method Edge Items]

invert_vertex_group

Reverses the effect of the vertex group (default False)

Type :

bool

islands_precision

Sets how precisely islands are handled; around 0.1 is usually plenty, and larger numbers can slow things down considerably (in [0, 1], default 0.0)

Type :

float

layers_uv_select_dst

Chooses the rule for pairing source layers with destination layers (default 'NAME' )

Type :

Literal[Dt Layers Select Dst Items]

layers_uv_select_src

Picks which layers move across when the type has several (default 'ALL' )

Type :

Literal[Dt Layers Select Src Items]

layers_vcol_loop_select_dst

Chooses the rule for pairing source layers with destination layers (default 'NAME' )

Type :

Literal[Dt Layers Select Dst Items]

layers_vcol_loop_select_src

Picks which layers move across when the type has several (default 'ALL' )

Type :

Literal[Dt Layers Select Src Items]

layers_vcol_vert_select_dst

Chooses the rule for pairing source layers with destination layers (default 'NAME' )

Type :

Literal[Dt Layers Select Dst Items]

layers_vcol_vert_select_src

Picks which layers move across when the type has several (default 'ALL' )

Type :

Literal[Dt Layers Select Src Items]

layers_vgroup_select_dst

Chooses the rule for pairing source layers with destination layers (default 'NAME' )

Type :

Literal[Dt Layers Select Dst Items]

layers_vgroup_select_src

Picks which layers move across when the type has several (default 'ALL' )

Type :

Literal[Dt Layers Select Src Items]

loop_mapping

Chooses how source face corners get paired with destination corners (default '`NEAREST_POLYNOR`' )

Type :

Literal[Dt Method Loop Items]

max_distance

Caps the spacing allowed between paired source and destination elements when the mapping isn’t topology-based (in [0, inf], default 1.0)

Type :

float

mix_factor

Weighting applied as data lands on the destination; what it does varies with the mix mode, and it scales by vertex-group weights where one is assigned (in [0, 1], default 0.0)

Type :

float

mix_mode

Chooses the way source values combine with the existing destination values (default 'REPLACE' )

Type :

Literal[Dt Mix Mode Items]

object

The mesh whose data is being pulled in

Type :

Object

poly_mapping

Chooses how source faces get paired with destination faces (default 'NEAREST' )

Type :

Literal[Dt Method Poly Items]

ray_radius

Thickness of the cast rays, handy in particular when raycasting onto vertices or edges (in [0, inf], default 0.0)

Type :

float

use_edge_data

Turns on copying of edge data (default False)

Type :

bool

use_loop_data

Turns on copying of face-corner data (default False)

Type :

bool

use_max_distance

Requires source elements to sit nearer than the set distance to the destination (default False)

Type :

bool

use_object_transform

Computes both meshes in world space rather than locally (default True)

Type :

bool

use_poly_data

Turns on copying of face data (default False)

Type :

bool

use_vert_data

Turns on copying of vertex data (default False)

Type :

bool

vert_mapping

Chooses how source vertices get paired with destination vertices (default 'NEAREST' )

Type :

Literal[Dt Method Vertex Items]

vertex_group

Names the vertex group that picks out the affected region (default “”, never None)

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

## DecimateModifier(Modifier)

### DecimateModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. DecimateModifier ( Modifier )

Reduces a mesh’s polygon count.

angle_limit

Dissolves only those angles that fall under this threshold (planar only) (in [0, 3.14159], default 0.0872665)

Type :

float

decimate_type

(default 'COLLAPSE' )

- COLLAPSE
Collapse – Reduce by collapsing edges.

- UNSUBDIV
Un-Subdivide – Reduce faces by reversing subdivision.

- DISSOLVE
Planar – Merge geometry into flat polygons.

Type :

Literal[‘COLLAPSE’, ‘UNSUBDIV’, ‘DISSOLVE’]

delimit

Restricts where geometry is allowed to merge (default set())

Type :

set[Literal[Mesh Delimit Mode Items]]

face_count

How many faces the decimated mesh currently holds (in [-inf, inf], default 0, readonly)

Type :

int

invert_vertex_group

Reverses the effect of the vertex group (collapse only) (default False)

Type :

bool

iterations

How many passes are run to thin the geometry (unsubdivide only) (in [0, 32767], default 0)

Type :

int

ratio

Target triangle ratio after reduction (collapse only) (in [0, 1], default 1.0)

Type :

float

symmetry_axis

The axis across which symmetry is mirrored (default 'X' )

Type :

Literal[Axis Xyz Items]

use_collapse_triangulate

Retains the triangles produced by decimation (collapse only) (default False)

Type :

bool

use_dissolve_boundaries

Removes every vertex lying between face boundaries (planar only) (default False)

Type :

bool

use_symmetry

Preserves symmetry along a chosen axis (default False)

Type :

bool

vertex_group

Names the vertex group (collapse only) (default “”, never None)

Type :

str

vertex_group_factor

Strength applied to the vertex group (in [0, 1000], default 1.0)

Type :

float

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

## DepsgraphObjectInstance(bpy_struct)

### DepsgraphObjectInstance(bpy_struct)

base class — bpy_struct

class bpy.types. DepsgraphObjectInstance ( bpy_struct )

Further detail attached to the dependency-graph object iterator (Warning: everything exposed here is the ‘evaluated’ form, not the original .blend IDs)

instance_object

The evaluated object that this iterator is instancing (readonly)

Type :

Object

is_instance

Flags whether some other object produced this one (default False, readonly)

Type :

bool

matrix_world

The world-space transform matrix that was generated (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)), readonly)

Type :

mathutils.Matrix

object

The evaluated object the iterator currently references (readonly)

Type :

Object

orco

Generated coordinates expressed in the parent object’s space (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

parent

For an instance, the parent object that produced it (readonly)

Type :

Object

particle_system

The evaluated particle system this object was instanced out of (readonly)

Type :

ParticleSystem

persistent_id

Stable identifier letting motion-blur match objects between frames (array of 8 items, in [-inf, inf], default (0, 0, 0, 0, 0, 0, 0, 0), readonly)

Type :

bpy_prop_array[int]

random_id

A random id tied to this instance, usually feeding randomized shading (in [0, inf], default 0, readonly)

Type :

int

show_particles

Whether the object’s particle portion shows up in the render (default False, readonly)

Type :

bool

show_self

Whether the object’s own geometry shows up in the render (default False, readonly)

Type :

bool

uv

UV coordinates expressed in the parent object’s space (array of 2 items, in [-inf, inf], default (0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

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

| Depsgraph.object_instances | |

## DynamicPaintModifier(Modifier)

### DynamicPaintModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. DynamicPaintModifier ( Modifier )

The Dynamic Paint modifier

brush_settings

(readonly)

Type :

DynamicPaintBrushSettings

canvas_settings

(readonly)

Type :

DynamicPaintCanvasSettings

ui_type

(default 'CANVAS' )

Type :

Literal[Prop Dynamicpaint Type Items]

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

## EdgeSplitModifier(Modifier)

### EdgeSplitModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. EdgeSplitModifier ( Modifier )

A modifier that breaks edges apart to make them sharp

split_angle

Edges are split once their angle rises above this (in [0, 3.14159], default 0.523599)

Type :

float

use_edge_angle

Split any edge where the angle between its faces is large (default True)

Type :

bool

use_edge_sharp

Split any edge flagged as sharp (default True)

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
