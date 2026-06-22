# Greasepencilshrinkwrapmodifier Modifier, Greasepencilsimplifymodifier Modifier, Greasepencilsmoothmodifier Modifier, Greasepencilsubdivmodifier Modifier ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: GreasePencilShrinkwrapModifier(Modifier); GreasePencilSimplifyModifier(Modifier); GreasePencilSmoothModifier(Modifier); GreasePencilSubdivModifier(Modifier); GreasePencilTextureModifier(Modifier); GreasePencilThickModifierData(Modifier).

## GreasePencilShrinkwrapModifier(Modifier)

### GreasePencilShrinkwrapModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilShrinkwrapModifier ( Modifier )

Conforms an object onto a target surface by wrapping it tightly around it.

auxiliary_target

Additional mesh target to shrink to

Type :

Object

cull_face

Stop vertices from projecting to a face on the target when facing towards/away (default 'OFF' )

Type :

Literal[Shrinkwrap Face Cull Items]

invert_layer_filter

Invert layer filter (default False)

Type :

bool

invert_layer_pass_filter

Invert layer pass filter (default False)

Type :

bool

invert_material_filter

Invert material filter (default False)

Type :

bool

invert_material_pass_filter

Invert material pass filter (default False)

Type :

bool

invert_vertex_group

Invert vertex group weights (default False)

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

offset

Distance to keep from the target (in [-inf, inf], default 0.05)

Type :

float

open_influence_panel

(default False)

Type :

bool

project_limit

Limit the distance used for projection (zero disables) (in [0, inf], default 0.0)

Type :

float

smooth_factor

Amount of smoothing to apply (in [0, 1], default 0.05)

Type :

float

smooth_step

Number of times to apply smooth (high numbers can reduce FPS) (in [1, 10], default 1)

Type :

int

subsurf_levels

Number of subdivisions that must be performed before extracting vertices' positions and normals (in [0, 6], default 0)

Type :

int

target

Mesh target to shrink to

Type :

Object

tree_node_filter

Layer name (default "", never None)

Type :

str

use_invert_cull

When projecting in the negative direction invert the face cull mode (default False)

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

use_negative_direction

Allow vertices to move in the negative direction of axis (default False)

Type :

bool

use_positive_direction

Allow vertices to move in the positive direction of axis (default True)

Type :

bool

use_project_x

(default False)

Type :

bool

use_project_y

(default False)

Type :

bool

use_project_z

(default False)

Type :

bool

vertex_group_name

Vertex group name for modulating the deform (default "", never None)

Type :

str

wrap_method

(default '`NEAREST_SURFACEPOINT`' )

Type :

Literal[Shrinkwrap Type Items]

wrap_mode

Select how vertices are constrained to the target surface (default '`ON_SURFACE`' )

Type :

Literal[Modifier Shrinkwrap Mode Items]

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

## GreasePencilSimplifyModifier(Modifier)

### GreasePencilSimplifyModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilSimplifyModifier ( Modifier )

Reduces the point count of strokes.

distance

Distance between points (in [0, inf], default 0.1)

Type :

float

factor

Factor of Simplify (in [0, 100], default 0.0)

Type :

float

invert_layer_filter

Invert layer filter (default False)

Type :

bool

invert_layer_pass_filter

Invert layer pass filter (default False)

Type :

bool

invert_material_filter

Invert material filter (default False)

Type :

bool

invert_material_pass_filter

Invert material pass filter (default False)

Type :

bool

invert_vertex_group

Invert vertex group weights (default False)

Type :

bool

layer_pass_filter

Layer pass filter (in [0, 100], default 0)

Type :

int

length

Length of each segment (in [0, inf], default 0.1)

Type :

float

material_filter

Material used for filtering

Type :

Material

material_pass_filter

Material pass (in [0, 100], default 0)

Type :

int

mode

How to simplify the stroke (default 'FIXED' )

- FIXED
Fixed – Drop every other vertex along the stroke, sparing the end points.

- ADAPTIVE
Adaptive – Run a Ramer-Douglas-Peucker pass that thins the stroke while holding its overall shape.

- SAMPLE
Sample – Lay the stroke out again using segments of the length you set.

- MERGE
Merge – Collapse stroke vertices that sit closer together than a set distance.

Type :

Literal['FIXED', 'ADAPTIVE', 'SAMPLE', 'MERGE']

open_influence_panel

(default False)

Type :

bool

sharp_threshold

Preserve corners that have sharper angle than this threshold (in [0, 3.14159], default 0.0)

Type :

float

step

Number of times to apply simplify (in [1, 50], default 1)

Type :

int

tree_node_filter

Layer name (default "", never None)

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

Vertex group name for modulating the deform (default "", never None)

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

## GreasePencilSmoothModifier(Modifier)

### GreasePencilSmoothModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilSmoothModifier ( Modifier )

Applies a smoothing pass as an effect.

custom_curve

Custom curve to apply effect (readonly)

Type :

CurveMapping

factor

Amount of smooth to apply (in [0, 1], default 1.0)

Type :

float

invert_layer_filter

Invert layer filter (default False)

Type :

bool

invert_layer_pass_filter

Invert layer pass filter (default False)

Type :

bool

invert_material_filter

Invert material filter (default False)

Type :

bool

invert_material_pass_filter

Invert material pass filter (default False)

Type :

bool

invert_vertex_group

Invert vertex group weights (default False)

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

open_influence_panel

(default False)

Type :

bool

step

Number of times to apply smooth (high numbers can reduce fps) (in [1, 1000], default 1)

Type :

int

tree_node_filter

Layer name (default "", never None)

Type :

str

use_custom_curve

Use a custom curve to define a factor along the strokes (default False)

Type :

bool

use_edit_position

When on, the modifier acts on each point's position (default True)

Type :

bool

use_edit_strength

When on, the modifier acts on each point's color strength (default False)

Type :

bool

use_edit_thickness

When on, the modifier acts on each point's thickness (default False)

Type :

bool

use_edit_uv

When on, the modifier acts on each point's UV rotation factor (default False)

Type :

bool

use_keep_shape

Smooth out fine detail while leaving the broad shape intact (default False)

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

use_smooth_ends

Smooth ends of strokes (default False)

Type :

bool

vertex_group_name

Vertex group name for modulating the deform (default "", never None)

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

## GreasePencilSubdivModifier(Modifier)

### GreasePencilSubdivModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilSubdivModifier ( Modifier )

Adds extra points along each stroke through subdivision.

invert_layer_filter

Invert layer filter (default False)

Type :

bool

invert_layer_pass_filter

Invert layer pass filter (default False)

Type :

bool

invert_material_filter

Invert material filter (default False)

Type :

bool

invert_material_pass_filter

Invert material pass filter (default False)

Type :

bool

layer_pass_filter

Layer pass filter (in [0, 100], default 0)

Type :

int

level

Level of subdivision (in [0, 16], default 1)

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

open_influence_panel

(default False)

Type :

bool

subdivision_type

Select type of subdivision algorithm (default '`CATMULL_CLARK`' )

Type :

Literal['`CATMULL_CLARK`', 'SIMPLE']

tree_node_filter

Layer name (default "", never None)

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

## GreasePencilTextureModifier(Modifier)

### GreasePencilTextureModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilTextureModifier ( Modifier )

Remaps the texture coordinates carried by strokes.

alignment_rotation

Additional rotation applied to dots and square strokes (in [-1.5708, 1.5708], default 0.0)

Type :

float

fill_offset

Additional offset of the fill UV (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

fill_rotation

Additional rotation of the fill UV (in [-inf, inf], default 0.0)

Type :

float

fill_scale

Additional scale of the fill UV (in [0.01, 100], default 1.0)

Type :

float

fit_method

(default '`CONSTANT_LENGTH`' )

- `CONSTANT_LENGTH`
Constant Length – Hold the texture to a fixed length no matter how long the individual stroke is.

- `FIT_STROKE`
Stroke Length – Stretch or shrink the texture so it spans each stroke's length.

Type :

Literal['`CONSTANT_LENGTH`', '`FIT_STROKE`']

invert_layer_filter

Invert layer filter (default False)

Type :

bool

invert_layer_pass_filter

Invert layer pass filter (default False)

Type :

bool

invert_material_filter

Invert material filter (default False)

Type :

bool

invert_material_pass_filter

Invert material pass filter (default False)

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

mode

(default 'STROKE' )

- STROKE
Stroke – Touch the stroke texture coordinates and nothing else.

- FILL
Fill – Touch the fill texture coordinates and nothing else.

- `STROKE_AND_FILL`
Stroke & Fill – Touch the texture coordinates of both stroke and fill.

Type :

Literal['STROKE', 'FILL', '`STROKE_AND_FILL`']

open_influence_panel

(default False)

Type :

bool

tree_node_filter

Layer name (default "", never None)

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

uv_offset

Offset value to add to stroke UVs (in [-inf, inf], default 0.0)

Type :

float

uv_scale

Factor to scale the UVs (in [0, inf], default 1.0)

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

## GreasePencilThickModifierData(Modifier)

### GreasePencilThickModifierData(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilThickModifierData ( Modifier )

Changes how thick the strokes are drawn.

custom_curve

Custom curve to apply effect (readonly)

Type :

CurveMapping

invert_layer_filter

Invert layer filter (default False)

Type :

bool

invert_layer_pass_filter

Invert layer pass filter (default False)

Type :

bool

invert_material_filter

Invert material filter (default False)

Type :

bool

invert_material_pass_filter

Invert material pass filter (default False)

Type :

bool

invert_vertex_group

Invert vertex group weights (default False)

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

open_influence_panel

(default False)

Type :

bool

thickness

Absolute thickness to apply everywhere (in [-10, 100], default 0.02)

Type :

float

thickness_factor

Factor to multiply the thickness with (in [0, inf], default 1.0)

Type :

float

tree_node_filter

Layer name (default "", never None)

Type :

str

use_custom_curve

Use a custom curve to define a factor along the strokes (default False)

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

use_uniform_thickness

Replace the stroke thickness (default False)

Type :

bool

use_weight_factor

Use weight to modulate effect (default False)

Type :

bool

vertex_group_name

Vertex group name for modulating the deform (default "", never None)

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
