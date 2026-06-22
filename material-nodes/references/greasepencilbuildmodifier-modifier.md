# Greasepencilbuildmodifier Modifier, Greasepencilcolormodifier Modifier, Greasepencildashmodifierdata Modifier, Greasepencildashmodifiersegment Bpy Struct ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: GreasePencilBuildModifier(Modifier); GreasePencilColorModifier(Modifier); GreasePencilDashModifierData(Modifier); GreasePencilDashModifierSegment(bpy_struct); GreasePencilEnvelopeModifier(Modifier); GreasePencilHookModifier(Modifier).

## GreasePencilBuildModifier(Modifier)

### GreasePencilBuildModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilBuildModifier ( Modifier )

Animates strokes as they show up and fade away.

concurrent_time_alignment

Controls when strokes begin appearing or disappearing (default 'START' )

- START
Align Start – All strokes start at same time (i.e. short strokes finish earlier).

- END
Align End – All strokes end at same time (i.e. short strokes start later).

Type :

Literal[‘START’, ‘END’]

fade_factor

Sets how much of each stroke fades in or out (in [0, 1], default 0.0)

Type :

float

fade_opacity_strength

How strongly the fade affects stroke opacity in addition to it (in [0, 1], default 0.0)

Type :

float

fade_thickness_strength

How strongly the fade affects stroke thickness in addition to it (in [0, 1], default 0.0)

Type :

float

frame_end

End Frame (when Restrict Frame Range is enabled) (in [-1.04857e+06, 1.04857e+06], default 125.0)

Type :

float

frame_start

Start Frame (when Restrict Frame Range is enabled) (in [-1.04857e+06, 1.04857e+06], default 1.0)

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

length

How many frames the build effect may last at most, unless a later GP keyframe arrives first (in [1, 1.04857e+06], default 100.0)

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

Controls the way strokes get built (default 'SEQUENTIAL' )

- SEQUENTIAL
Sequential – Strokes appear/disappear one after the other, but only a single one changes at a time.

- CONCURRENT
Concurrent – Multiple strokes appear/disappear at once.

- ADDITIVE
Additive – Builds only new strokes (assuming ‘additive’ drawing).

Type :

Literal[‘SEQUENTIAL’, ‘CONCURRENT’, ‘ADDITIVE’]

object

Object used as build starting position

Type :

Object

open_fading_panel

(default False)

Type :

bool

open_frame_range_panel

(default False)

Type :

bool

open_influence_panel

(default False)

Type :

bool

percentage_factor

Sets how much of each stroke is shown (in [0, 1], default 0.0)

Type :

float

speed_factor

Scale the captured drawing speed by this factor (in [0, 100], default 1.2)

Type :

float

speed_maxgap

Largest allowed gap between strokes, in seconds (in [0, 100], default 0.5)

Type :

float

start_delay

Frames to wait after each GP keyframe before the modifier kicks in (in [0, 1.04857e+06], default 0.0)

Type :

float

target_vertex_group

Output Vertex group (default “”, never None)

Type :

str

time_mode

Choose drawing speed, a frame count, or a manual factor to drive the build (default 'FRAMES' )

- DRAWSPEED
Natural Drawing Speed – Use recorded speed multiplied by a factor.

- FRAMES
Number of Frames – Set a fixed number of frames for all build animations.

- PERCENTAGE
Percentage Factor – Set a manual percentage to build.

Type :

Literal[‘DRAWSPEED’, ‘FRAMES’, ‘PERCENTAGE’]

transition

Sets the way strokes animate — whether they appear or vanish (default 'GROW' )

- GROW
Grow – Show points in the order they occur in each stroke (e.g. for animating lines being drawn).

- SHRINK
Shrink – Hide points from the end of each stroke to the start (e.g. for animating lines being erased).

- FADE
Vanish – Hide points in the order they occur in each stroke (e.g. for animating ink fading or vanishing after getting drawn).

Type :

Literal[‘GROW’, ‘SHRINK’, ‘FADE’]

tree_node_filter

Layer name (default “”, never None)

Type :

str

use_fading

Let strokes fade away rather than being cut off directly (default False)

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

use_percentage

Decide the visible points from a percentage factor (default False)

Type :

bool

use_restrict_frame_range

Affect strokes only within the chosen frame range (default False)

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

## GreasePencilColorModifier(Modifier)

### GreasePencilColorModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilColorModifier ( Modifier )

color_mode

Attributes to modify (default 'BOTH' )

- BOTH
Stroke & Fill – Modify fill and stroke colors.

- STROKE
Stroke – Modify stroke color only.

- FILL
Fill – Modify fill color only.

Type :

Literal[‘BOTH’, ‘STROKE’, ‘FILL’]

custom_curve

Custom curve to apply effect (readonly)

Type :

CurveMapping

hue

Color hue offset (in [0, 1], default 0.5)

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

open_influence_panel

(default False)

Type :

bool

saturation

Color saturation factor (in [0, inf], default 0.5)

Type :

float

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

value

Color value factor (in [0, inf], default 0.5)

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

## GreasePencilDashModifierData(Modifier)

### GreasePencilDashModifierData(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilDashModifierData ( Modifier )

Produces a dot-dash pattern along strokes.

dash_offset

Distance into each stroke before the dashed pattern starts being generated (in [-inf, inf], default 0)

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

open_influence_panel

(default False)

Type :

bool

segment_active_index

Active index in the segment list (in [0, inf], default 0)

Type :

int

segments

(default None, readonly)

Type :

bpy_prop_collection[GreasePencilDashModifierSegment]

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

## GreasePencilDashModifierSegment(bpy_struct)

### GreasePencilDashModifierSegment(bpy_struct)

base class — bpy_struct

class bpy.types. GreasePencilDashModifierSegment ( bpy_struct )

Settings that define one dash segment.

dash

How many points in a row from the source stroke this segment keeps (in [1, 32767], default 2)

Type :

int

gap

How many points get skipped once this segment ends (in [0, 32767], default 1)

Type :

int

material_index

Index of the material applied to the generated segment; -1 keeps the existing material. (in [-1, 32767], default -1)

Type :

int

name

Name of the dash segment (default “”, never None)

Type :

str

opacity

Scale applied to the source point’s opacity when creating the new points (in [0, 1], default 1.0)

Type :

float

radius

Scale applied to the source point’s radius when creating the new points (in [0, 1], default 1.0)

Type :

float

use_cyclic

Make individual stroke dashes cyclic (default False)

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

| GreasePencilDashModifierData.segments | |

## GreasePencilEnvelopeModifier(Modifier)

### GreasePencilEnvelopeModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilEnvelopeModifier ( Modifier )

Stroke modifier that wraps strokes in an envelope.

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

mat_nr

The material to use for the new strokes (in [-1, 32767], default -1)

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

Which algorithm produces the envelope (default 'SEGMENTS' )

- DEFORM
Deform – Deform the stroke to best match the envelope shape.

- SEGMENTS
Segments – Add segments to create the envelope. Keep the original stroke..

- FILLS
Fills – Add fill segments to create the envelope. Don’t keep the original stroke..

Type :

Literal[‘DEFORM’, ‘SEGMENTS’, ‘FILLS’]

open_influence_panel

(default False)

Type :

bool

skip

How many of the generated segments to leave out to cut down complexity (in [0, inf], default 0)

Type :

int

spread

How many points to skip so that straight segments are produced (in [1, inf], default 10)

Type :

int

strength

Multiplier for the strength of the new strokes (in [0, inf], default 1.0)

Type :

float

thickness

Multiplier for the thickness of the new strokes (in [0, inf], default 1.0)

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

## GreasePencilHookModifier(Modifier)

### GreasePencilHookModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilHookModifier ( Modifier )

Hook modifier that shifts where stroke points sit.

center

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

custom_curve

Custom curve to apply effect (readonly)

Type :

CurveMapping

falloff_radius

When nonzero, the range from the hook at which influence drops to nothing (in [0, inf], default 0.0)

Type :

float

falloff_type

(default 'SMOOTH' )

Type :

Literal[‘NONE’, ‘CURVE’, ‘SMOOTH’, ‘SPHERE’, ‘ROOT’, ‘`INVERSE_SQUARE`’, ‘SHARP’, ‘LINEAR’, ‘CONSTANT’]

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

matrix_inverse

Undo the transform between this object and its target (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((1.0, 0.0, 0.0, 0.0), (0.0, 1.0, 0.0, 0.0), (0.0, 0.0, 1.0, 0.0), (0.0, 0.0, 0.0, 1.0)))

Type :

mathutils.Matrix

object

Parent Object for hook, also recalculates and clears offset

Type :

Object

open_falloff_panel

(default False)

Type :

bool

open_influence_panel

(default False)

Type :

bool

strength

Relative force of the hook (in [0, 1], default 0.5)

Type :

float

subtarget

Name of Parent Bone for hook (if applicable), also recalculates and clears offset (default “”, never None)

Type :

str

tree_node_filter

Layer name (default “”, never None)

Type :

str

use_custom_curve

Drive a factor along the strokes from a custom curve (default False)

Type :

bool

use_falloff_uniform

Correct for object scale that is not uniform (default False)

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

## See also

- [Bpy Struct](bpy-struct.md)
