# Linestylethicknessmodifier Distancefromobject Linestylethicknessmodifier, Linestylethicknessmodifier Noise Linestylethicknessmodifier, Linestylethicknessmodifier Tangent Linestylethicknessmodifier, Masklayer Bpy Struct ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: LineStyleThicknessModifier_DistanceFromObject(LineStyleThicknessModifier); LineStyleThicknessModifier_Noise(LineStyleThicknessModifier); LineStyleThicknessModifier_Tangent(LineStyleThicknessModifier); MaskLayer(bpy_struct); MaskModifier(Modifier); MeshCacheModifier(Modifier); MeshDeformModifier(Modifier); MeshLoopColorLayer(bpy_struct); MeshSequenceCacheModifier(Modifier).

## LineStyleThicknessModifier_DistanceFromObject(LineStyleThicknessModifier)

### LineStyleThicknessModifier_DistanceFromObject(LineStyleThicknessModifier)

base classes — bpy_struct, LineStyleModifier, LineStyleThicknessModifier

class bpy.types. LineStyleThicknessModifier_DistanceFromObject ( LineStyleThicknessModifier )

Adjusts line width according to how far the stroke sits from a chosen object.

blend

Sets the way this modifier's output is combined with the underlying base value (default 'MIX' )

Type :

Literal[‘MIX’, ‘ADD’, ‘SUBTRACT’, ‘MULTIPLY’, ‘DIVIDE’, ‘DIFFERENCE’, ‘MINIMUM’, ‘MAXIMUM’]

curve

The curve that drives curve-based mapping (readonly)

Type :

CurveMapping

expanded

True when the modifier's tab is shown unfolded (default False)

Type :

bool

influence

Weight that scales how strongly the modifier alters the property (in [0, 1], default 0.0)

Type :

float

invert

Reverse the direction in which the linear mapping fades out (default False)

Type :

bool

mapping

Choose which mapping mode applies (default 'LINEAR' )

- LINEAR
Linear – Use linear mapping.

- CURVE
Curve – Use curve mapping.

Type :

Literal[‘LINEAR’, ‘CURVE’]

range_max

Top of the input range over which the mapping operates (in [-inf, inf], default 0.0)

Type :

float

range_min

Bottom of the input range over which the mapping operates (in [-inf, inf], default 0.0)

Type :

float

target

Object that the distance is measured from

Type :

Object

type

The modifier's kind (default '`ALONG_STROKE`' , readonly)

Type :

Literal[Linestyle Thickness Modifier Type Items]

use

Turn this modifier on or off while strokes are rendered (default False)

Type :

bool

value_max

Highest value the mapping can output (in [-inf, inf], default 0.0)

Type :

float

value_min

Lowest value the mapping can output (in [-inf, inf], default 0.0)

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

- default (type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | LineStyleThicknessModifier.name |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleThicknessModifier.bl_rna_get_subclass LineStyleThicknessModifier.bl_rna_get_subclass_py |

## LineStyleThicknessModifier_Noise(LineStyleThicknessModifier)

### LineStyleThicknessModifier_Noise(LineStyleThicknessModifier)

base classes — bpy_struct, LineStyleModifier, LineStyleThicknessModifier

class bpy.types. LineStyleThicknessModifier_Noise ( LineStyleThicknessModifier )

Drives line width from a random noise signal.

amplitude

Strength of the noise signal (in [-inf, inf], default 0.0)

Type :

float

blend

Sets the way this modifier's output is combined with the underlying base value (default 'MIX' )

Type :

Literal[‘MIX’, ‘ADD’, ‘SUBTRACT’, ‘MULTIPLY’, ‘DIVIDE’, ‘DIFFERENCE’, ‘MINIMUM’, ‘MAXIMUM’]

expanded

True when the modifier's tab is shown unfolded (default False)

Type :

bool

influence

Weight that scales how strongly the modifier alters the property (in [0, 1], default 0.0)

Type :

float

period

Wavelength over which the noise repeats (in [-inf, inf], default 0.0)

Type :

float

seed

Seed value feeding the noise generator (in [1, 32767], default 0)

Type :

int

type

The modifier's kind (default '`ALONG_STROKE`' , readonly)

Type :

Literal[Linestyle Thickness Modifier Type Items]

use

Turn this modifier on or off while strokes are rendered (default False)

Type :

bool

use_asymmetric

Permit width to be applied unevenly to either side (default False)

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

- default (type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | LineStyleThicknessModifier.name |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleThicknessModifier.bl_rna_get_subclass LineStyleThicknessModifier.bl_rna_get_subclass_py |

## LineStyleThicknessModifier_Tangent(LineStyleThicknessModifier)

### LineStyleThicknessModifier_Tangent(LineStyleThicknessModifier)

base classes — bpy_struct, LineStyleModifier, LineStyleThicknessModifier

class bpy.types. LineStyleThicknessModifier_Tangent ( LineStyleThicknessModifier )

Sets line width from the stroke's running direction.

blend

Sets the way this modifier's output is combined with the underlying base value (default 'MIX' )

Type :

Literal[‘MIX’, ‘ADD’, ‘SUBTRACT’, ‘MULTIPLY’, ‘DIVIDE’, ‘DIFFERENCE’, ‘MINIMUM’, ‘MAXIMUM’]

curve

The curve that drives curve-based mapping (readonly)

Type :

CurveMapping

expanded

True when the modifier's tab is shown unfolded (default False)

Type :

bool

influence

Weight that scales how strongly the modifier alters the property (in [0, 1], default 0.0)

Type :

float

invert

Reverse the direction in which the linear mapping fades out (default False)

Type :

bool

mapping

Choose which mapping mode applies (default 'LINEAR' )

- LINEAR
Linear – Use linear mapping.

- CURVE
Curve – Use curve mapping.

Type :

Literal[‘LINEAR’, ‘CURVE’]

thickness_max

Largest width (in [0, 10000], default 0.0)

Type :

float

thickness_min

Smallest width (in [0, 10000], default 0.0)

Type :

float

type

The modifier's kind (default '`ALONG_STROKE`' , readonly)

Type :

Literal[Linestyle Thickness Modifier Type Items]

use

Turn this modifier on or off while strokes are rendered (default False)

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

- default (type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | LineStyleThicknessModifier.name |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleThicknessModifier.bl_rna_get_subclass LineStyleThicknessModifier.bl_rna_get_subclass_py |

## MaskLayer(bpy_struct)

### MaskLayer(bpy_struct)

base class — bpy_struct

class bpy.types. MaskLayer ( bpy_struct )

One mask layer that controls which pixels are masked.

alpha

Render Opacity (in [-inf, inf], default 0.0)

Type :

float

blend

How this mask layer blends with the others (default 'ADD' )

Type :

Literal[‘`MERGE_ADD`’, ‘`MERGE_SUBTRACT`’, ‘ADD’, ‘SUBTRACT’, ‘LIGHTEN’, ‘DARKEN’, ‘MUL’, ‘REPLACE’, ‘DIFFERENCE’]

falloff

Falloff curve applied to the feather (default 'SMOOTH' )

Type :

Literal[Proportional Falloff Curve Only Items]

hide

Hide this layer from the viewport (default False)

Type :

bool

hide_render

Exclude this layer from rendering (default False)

Type :

bool

hide_select

Block this layer from being selected in the viewport (default False)

Type :

bool

invert

Swap the mask's black and white (default False)

Type :

bool

name

Unique name of layer (default “”, never None)

Type :

str

select

Whether the layer is picked for editing in the Dope Sheet (default False)

Type :

bool

splines

Set of splines that make up this layer (default None, readonly)

Type :

MaskSplines[MaskSpline]

use_fill_holes

Detect holes while filling overlapping curves (default True)

Type :

bool

use_fill_overlap

Resolve self-intersections and overlaps prior to filling (default False)

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

| Mask.layers MaskLayers.active | MaskLayers.new MaskLayers.remove |

## MaskModifier(Modifier)

### MaskModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. MaskModifier ( Modifier )

A modifier that hides selected portions of the mesh.

armature

Armature whose bones supply the masking source

Type :

Object

invert_vertex_group

Use vertices that fall outside the defined region (default False)

Type :

bool

mode

(default '`VERTEX_GROUP`' )

Type :

Literal[‘`VERTEX_GROUP`’, ‘ARMATURE’]

threshold

Weights above this value are kept (in [0, 1], default 0.0)

Type :

float

use_smooth

Cut faces along the weight contour using vertex group weights (default False)

Type :

bool

vertex_group

Vertex group name (default “”, never None)

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

## MeshCacheModifier(Modifier)

### MeshCacheModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. MeshCacheModifier ( Modifier )

Cache Mesh

cache_format

(default 'MDD' )

Type :

Literal[‘MDD’, ‘PC2’]

deform_mode

(default 'OVERWRITE' )

- OVERWRITE
Overwrite – Replace vertex coordinates with cached values.

- INTEGRATE
Integrate – Integrate deformation from this modifier’s input with the mesh-cache coordinates (useful for shape keys).

Type :

Literal[‘OVERWRITE’, ‘INTEGRATE’]

eval_factor

Evaluation time in seconds (in [0, 1], default 0.0)

Type :

float

eval_frame

The frame to evaluate (starting at 0) (in [0, 1.04857e+06], default 0.0)

Type :

float

eval_time

Evaluation time in seconds (in [0, inf], default 0.0)

Type :

float

factor

Influence of the deformation (in [0, 1], default 1.0)

Type :

float

filepath

Path to external displacements file (default "", never None, blend relative // prefix supported)

Type :

str

flip_axis

(array of 3 items, default (False, False, False))

Type :

bpy_prop_array[bool]

forward_axis

(default '`POS_Y`' )

Type :

Literal[Object Axis Items]

frame_scale

Evaluation time in seconds (in [0, 100], default 1.0)

Type :

float

frame_start

Add this to the start frame (in [-1.04857e+06, 1.04857e+06], default 0.0)

Type :

float

interpolation

(default 'LINEAR' )

Type :

Literal[‘NONE’, ‘LINEAR’]

invert_vertex_group

Invert vertex group influence (default False)

Type :

bool

play_mode

(default 'SCENE' )

- SCENE
Scene – Use the time from the scene.

- CUSTOM
Custom – Use the modifier’s own time evaluation.

Type :

Literal[‘SCENE’, ‘CUSTOM’]

time_mode

Method to control playback time (default 'FRAME' )

- FRAME
Frame – Control playback using a frame-number (ignoring time FPS and start frame from the file).

- TIME
Time – Control playback using time in seconds.

- FACTOR
Factor – Control playback using a value between 0 and 1.

Type :

Literal[‘FRAME’, ‘TIME’, ‘FACTOR’]

up_axis

(default '`POS_Z`' )

Type :

Literal[Object Axis Items]

vertex_group

Name of the Vertex Group which determines the influence of the modifier per point (default "", never None)

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

## MeshDeformModifier(Modifier)

### MeshDeformModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. MeshDeformModifier ( Modifier )

Mesh deformation modifier to deform with other meshes

invert_vertex_group

Invert vertex group influence (default False)

Type :

bool

is_bound

Whether geometry has been bound to control cage (default False, readonly)

Type :

bool

object

Mesh object to deform with

Type :

Object

precision

The grid size for binding (in [2, 10], default 5)

Type :

int

use_dynamic_bind

Recompute binding dynamically on top of other deformers (slower and more memory consuming) (default False)

Type :

bool

vertex_group

Vertex group name (default "", never None)

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

## MeshLoopColorLayer(bpy_struct)

### MeshLoopColorLayer(bpy_struct)

base class — bpy_struct

class bpy.types. MeshLoopColorLayer ( bpy_struct )

Layer of vertex colors in a Mesh data-block

active

Sets the layer as active for display and editing (default False)

Type :

bool

active_render

Sets the layer as active for rendering (default False)

Type :

bool

data

(default None, readonly)

Type :

bpy_prop_collection[MeshLoopColor]

name

Name of Vertex color layer (default "", never None)

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| LoopColors.active LoopColors.new | LoopColors.remove Mesh.vertex_colors |

## MeshSequenceCacheModifier(Modifier)

### MeshSequenceCacheModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. MeshSequenceCacheModifier ( Modifier )

Cache Mesh

cache_file

Type :

CacheFile

object_path

Path to the object in the Alembic archive used to lookup geometric data (default "", never None)

Type :

str

read_data

Data to read from the cache (default { 'ATTRIBUTES' , 'COLOR' , 'POLY' , 'UV' , 'VERT' })

Type :

set[Literal[‘VERT’, ‘POLY’, ‘UV’, ‘COLOR’, ‘ATTRIBUTES’]]

use_vertex_interpolation

Allow interpolation of vertex positions (default True)

Type :

bool

velocity_scale

Multiplier used to control the magnitude of the velocity vectors for time effects (in [0, inf], default 1.0)

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
