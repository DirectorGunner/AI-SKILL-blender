# Greasepencilmirrormodifier Modifier, Greasepencilmultiplymodifier Modifier, Greasepencilnoisemodifier Modifier, Greasepenciloffsetmodifier Modifier ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: GreasePencilMirrorModifier(Modifier); GreasePencilMultiplyModifier(Modifier); GreasePencilNoiseModifier(Modifier); GreasePencilOffsetModifier(Modifier); GreasePencilOpacityModifier(Modifier); GreasePencilOutlineModifier(Modifier).

## GreasePencilMirrorModifier(Modifier)

### GreasePencilMirrorModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilMirrorModifier ( Modifier )

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

object

Object used as center

Type :

Object

open_influence_panel

(default False)

Type :

bool

tree_node_filter

Layer name (default “”, never None)

Type :

str

use_axis_x

Mirror the X axis (default True)

Type :

bool

use_axis_y

Mirror the Y axis (default False)

Type :

bool

use_axis_z

Mirror the Z axis (default False)

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

## GreasePencilMultiplyModifier(Modifier)

### GreasePencilMultiplyModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilMultiplyModifier ( Modifier )

Turns a single stroke into several strokes.

distance

Distance of duplications (in [-inf, inf], default 0.1)

Type :

float

duplicates

How many stroke copies get shown (in [0, 999], default 3)

Type :

int

fading_center

Fade center (in [0, 1], default 0.5)

Type :

float

fading_opacity

How much the stroke’s opacity is faded (in [0, 1], default 0.5)

Type :

float

fading_thickness

How much the stroke’s thickness is faded (in [0, 1], default 0.5)

Type :

float

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

offset

Offset of duplicates, -1 to 1 (inner to outer) (in [-inf, inf], default 0.0)

Type :

float

open_fading_panel

(default False)

Type :

bool

open_influence_panel

(default False)

Type :

bool

tree_node_filter

Layer name (default “”, never None)

Type :

str

use_fade

Taper the stroke thickness across each generated stroke (default False)

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

## GreasePencilNoiseModifier(Modifier)

### GreasePencilNoiseModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilNoiseModifier ( Modifier )

Stroke modifier that adds a noise effect.

custom_curve

Custom curve to apply effect (readonly)

Type :

CurveMapping

factor

Amount of noise to apply (in [0, inf], default 0.5)

Type :

float

factor_strength

How much noise gets applied to opacity (in [0, inf], default 0.0)

Type :

float

factor_thickness

How much noise gets applied to thickness (in [0, inf], default 0.0)

Type :

float

factor_uvs

How much noise gets applied to UV rotation (in [0, inf], default 0.0)

Type :

float

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

noise_offset

Shift the noise along the strokes (in [0, inf], default 0.0)

Type :

float

noise_scale

Scale the noise frequency (in [0, 1], default 0.0)

Type :

float

open_influence_panel

(default False)

Type :

bool

open_random_panel

(default False)

Type :

bool

random_mode

Sets where randomization happens (default 'STEP' )

- STEP
Steps – Randomize every number of frames.

- KEYFRAME
Keyframes – Randomize on keyframes only.

Type :

Literal[‘STEP’, ‘KEYFRAME’]

seed

Random seed (in [0, inf], default 1)

Type :

int

step

Number of frames between randomization steps (in [1, 100], default 4)

Type :

int

tree_node_filter

Layer name (default “”, never None)

Type :

str

use_custom_curve

Drive a factor along the strokes from a custom curve (default False)

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

Let values vary randomly over time (default True)

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

## GreasePencilOffsetModifier(Modifier)

### GreasePencilOffsetModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilOffsetModifier ( Modifier )

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

location

Values for change location (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

material_filter

Material used for filtering

Type :

Material

material_pass_filter

Material pass (in [0, 100], default 0)

Type :

int

offset_mode

(default 'RANDOM' )

- RANDOM
Random – Randomize stroke offset.

- LAYER
Layer – Offset layers by the same factor.

- STROKE
Stroke – Offset strokes by the same factor based on stroke draw order.

- MATERIAL
Material – Offset materials by the same factor.

Type :

Literal[‘RANDOM’, ‘LAYER’, ‘STROKE’, ‘MATERIAL’]

open_general_panel

(default False)

Type :

bool

open_influence_panel

(default False)

Type :

bool

rotation

Values for changes in rotation (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Euler

scale

Values for changes in scale (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

seed

Random seed (in [0, inf], default 0)

Type :

int

stroke_location

Value for changes in location (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

stroke_rotation

Value for changes in rotation (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Euler

stroke_scale

Value for changes in scale (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

stroke_start_offset

Offset starting point (in [0, inf], default 0)

Type :

int

stroke_step

Number of elements that will be grouped (in [1, 500], default 1)

Type :

int

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

use_uniform_random_scale

Share one random seed across every scale axis for uniform scaling (default False)

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

## GreasePencilOpacityModifier(Modifier)

### GreasePencilOpacityModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilOpacityModifier ( Modifier )

color_factor

Factor of opacity (in [-inf, inf], default 1.0)

Type :

float

color_mode

Attributes to modify (default 'BOTH' )

- BOTH
Stroke & Fill – Modify fill and stroke colors.

- STROKE
Stroke – Modify stroke color only.

- FILL
Fill – Modify fill color only.

- HARDNESS
Hardness – Modify stroke hardness.

Type :

Literal[‘BOTH’, ‘STROKE’, ‘FILL’, ‘HARDNESS’]

custom_curve

Custom curve to apply effect (readonly)

Type :

CurveMapping

hardness_factor

Factor of stroke hardness (in [0, inf], default 1.0)

Type :

float

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

open_influence_panel

(default False)

Type :

bool

tree_node_filter

Layer name (default “”, never None)

Type :

str

use_custom_curve

Drive a factor along the strokes from a custom curve (default False)

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

use_uniform_opacity

Set stroke opacity outright instead of adjusting each point (default False)

Type :

bool

use_weight_as_factor

Take the vertex group weight as the factor rather than as influence (default False)

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

## GreasePencilOutlineModifier(Modifier)

### GreasePencilOutlineModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilOutlineModifier ( Modifier )

Traces the silhouette of strokes as seen from the camera.

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

object

Target object to define stroke start

Type :

Object

open_influence_panel

(default False)

Type :

bool

outline_material

Material used for outline strokes

Type :

Material

sample_length

(in [-inf, inf], default 0.0)

Type :

float

subdivision

Number of subdivisions (in [0, 10], default 3)

Type :

int

thickness

Thickness of the perimeter stroke (in [1, 1000], default 1)

Type :

int

tree_node_filter

Layer name (default "", never None)

Type :

str

use_keep_shape

Try to keep global shape (default True)

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
