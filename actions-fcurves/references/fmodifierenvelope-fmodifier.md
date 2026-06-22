# Fmodifierenvelope Fmodifier, Fmodifierenvelopecontrolpoint Bpy Struct, Fmodifierenvelopecontrolpoints Bpy Prop Collection, Fmodifierfunctiongenerator Fmodifier ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: FModifierEnvelope(FModifier); FModifierEnvelopeControlPoint(bpy_struct); FModifierEnvelopeControlPoints(bpy_prop_collection); FModifierFunctionGenerator(FModifier); FModifierGenerator(FModifier); FModifierLimits(FModifier); FModifierNoise(FModifier); FModifierSmooth(FModifier); FModifierStepped(FModifier); FollowPathConstraint(Constraint).

## FModifierEnvelope(FModifier)

### FModifierEnvelope(FModifier)

base classes — bpy_struct, FModifier

class bpy.types. FModifierEnvelope ( FModifier )

Rescales the values of the F-Curve it modifies.

control_points

The control points that give the envelope its shape (default None, readonly)

Type :

FModifierEnvelopeControlPoints[FModifierEnvelopeControlPoint]

default_max

How far above the Reference Value the default 1:1 influence reaches (in [-inf, inf], default 1.0)

Type :

float

default_min

How far below the Reference Value the default 1:1 influence reaches (in [-inf, inf], default -1.0)

Type :

float

reference_value

The value the envelope's influence is built around and centered on (in [-inf, inf], default 0.0)

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

| bpy_struct.id_data FModifier.name FModifier.type FModifier.show_expanded FModifier.mute FModifier.is_valid FModifier.active | FModifier.use_restricted_range FModifier.frame_start FModifier.frame_end FModifier.blend_in FModifier.blend_out FModifier.use_influence FModifier.influence |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FModifier.bl_rna_get_subclass FModifier.bl_rna_get_subclass_py |

## FModifierEnvelopeControlPoint(bpy_struct)

### FModifierEnvelopeControlPoint(bpy_struct)

base class — bpy_struct

class bpy.types. FModifierEnvelopeControlPoint ( bpy_struct )

A single control point belonging to an envelope F-Modifier.

frame

The frame at which this control-point sits (in [-inf, inf], default 0.0)

Type :

float

max

The envelope's ceiling at this control-point (in [-inf, inf], default 0.0)

Type :

float

min

The envelope's floor at this control-point (in [-inf, inf], default 0.0)

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| FModifierEnvelope.control_points FModifierEnvelopeControlPoints.add | FModifierEnvelopeControlPoints.remove |

## FModifierEnvelopeControlPoints(bpy_prop_collection)

### FModifierEnvelopeControlPoints(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. FModifierEnvelopeControlPoints ( bpy_prop_collection )

The set of control points that shape the envelope.

add ( frame )

Insert a new control point into a FModifierEnvelope

Parameters :

frame ( float ) – Frame to add this control-point (in [-inf, inf])

Returns :

Newly created control-point

Return type :

FModifierEnvelopeControlPoint

remove ( point )

Delete a control-point from an FModifierEnvelope

Parameters :

point (FModifierEnvelopeControlPoint) – Control-point to remove (never None)

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

| FModifierEnvelope.control_points | |

## FModifierFunctionGenerator(FModifier)

### FModifierFunctionGenerator(FModifier)

base classes — bpy_struct, FModifier

class bpy.types. FModifierFunctionGenerator ( FModifier )

Produces values from one of the built-in functions.

amplitude

Multiplier that sets the peak and trough values (in [-inf, inf], default 1.0)

Type :

float

function_type

Which built-in function to apply (default 'SIN' )

- SIN
Sine.

- COS
Cosine.

- TAN
Tangent.

- SQRT
Square Root.

- LN
Natural Logarithm.

- SINC
Normalized Sine – sin(x) / x.

Type :

Literal[‘SIN’, ‘COS’, ‘TAN’, ‘SQRT’, ‘LN’, ‘SINC’]

phase_multiplier

Multiplier that sets how fast the function runs (in [-inf, inf], default 1.0)

Type :

float

phase_offset

Fixed amount by which the function's time input is shifted (in [-inf, inf], default 0.0)

Type :

float

use_additive

Adds this modifier's output onto the existing values rather than replacing them (default False)

Type :

bool

value_offset

Fixed amount by which the output values are shifted (in [-inf, inf], default 0.0)

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

| bpy_struct.id_data FModifier.name FModifier.type FModifier.show_expanded FModifier.mute FModifier.is_valid FModifier.active | FModifier.use_restricted_range FModifier.frame_start FModifier.frame_end FModifier.blend_in FModifier.blend_out FModifier.use_influence FModifier.influence |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FModifier.bl_rna_get_subclass FModifier.bl_rna_get_subclass_py |

## FModifierGenerator(FModifier)

### FModifierGenerator(FModifier)

base classes — bpy_struct, FModifier

class bpy.types. FModifierGenerator ( FModifier )

Computes deterministic values for the F-Curve it modifies.

coefficients

The ‘x’ coefficients, ordered from the lowest power x^0 upward (array of 32 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

mode

Type of generator to use (default 'POLYNOMIAL' )

Type :

Literal[‘POLYNOMIAL’, ‘`POLYNOMIAL_FACTORISED`’]

poly_order

The highest power of ‘x’ for this polynomial (number of coefficients - 1) (in [1, 100], default 0)

Type :

int

use_additive

Adds this modifier's output onto the existing values rather than replacing them (default False)

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

| bpy_struct.id_data FModifier.name FModifier.type FModifier.show_expanded FModifier.mute FModifier.is_valid FModifier.active | FModifier.use_restricted_range FModifier.frame_start FModifier.frame_end FModifier.blend_in FModifier.blend_out FModifier.use_influence FModifier.influence |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FModifier.bl_rna_get_subclass FModifier.bl_rna_get_subclass_py |

## FModifierLimits(FModifier)

### FModifierLimits(FModifier)

base classes — bpy_struct, FModifier

class bpy.types. FModifierLimits ( FModifier )

Clamps the time and value range of the F-Curve it modifies.

max_x

Upper cap permitted on X (in [-inf, inf], default 0.0)

Type :

float

max_y

Upper cap permitted on Y (in [-inf, inf], default 0.0)

Type :

float

min_x

Lower cap permitted on X (in [-inf, inf], default 0.0)

Type :

float

min_y

Lower cap permitted on Y (in [-inf, inf], default 0.0)

Type :

float

use_max_x

Apply the upper X cap (default False)

Type :

bool

use_max_y

Apply the upper Y cap (default False)

Type :

bool

use_min_x

Apply the lower X cap (default False)

Type :

bool

use_min_y

Apply the lower Y cap (default False)

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

| bpy_struct.id_data FModifier.name FModifier.type FModifier.show_expanded FModifier.mute FModifier.is_valid FModifier.active | FModifier.use_restricted_range FModifier.frame_start FModifier.frame_end FModifier.blend_in FModifier.blend_out FModifier.use_influence FModifier.influence |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FModifier.bl_rna_get_subclass FModifier.bl_rna_get_subclass_py |

## FModifierNoise(FModifier)

### FModifierNoise(FModifier)

base classes — bpy_struct, FModifier

class bpy.types. FModifierNoise ( FModifier )

Adds randomness to the F-Curve it modifies.

blend_type

How the noise is combined with the existing F-Curve (default 'REPLACE' )

Type :

Literal[‘REPLACE’, ‘ADD’, ‘SUBTRACT’, ‘MULTIPLY’]

depth

How much fine-grained detail the noise carries (in [0, 32767], default 0)

Type :

int

lacunarity

Spacing between successive frequencies. Depth must exceed 0 for this to matter. (in [-inf, inf], default 2.0)

Type :

float

offset

Shift in time applied to the noise (in [-inf, inf], default 0.0)

Type :

float

phase

Random seed driving the noise (in [-inf, inf], default 1.0)

Type :

float

roughness

How much high-frequency detail appears. Depth must exceed 0 for this to matter. (in [-inf, inf], default 0.5)

Type :

float

scale

How the noise is stretched along the time axis (in [-inf, inf], default 1.0)

Type :

float

strength

Noise amplitude, i.e. how far it shifts the underlying curve (in [-inf, inf], default 1.0)

Type :

float

use_legacy_noise

Generate noise the old way, which has the drawback of sometimes producing values beyond the -1/1 range (default False)

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

| bpy_struct.id_data FModifier.name FModifier.type FModifier.show_expanded FModifier.mute FModifier.is_valid FModifier.active | FModifier.use_restricted_range FModifier.frame_start FModifier.frame_end FModifier.blend_in FModifier.blend_out FModifier.use_influence FModifier.influence |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FModifier.bl_rna_get_subclass FModifier.bl_rna_get_subclass_py |

## FModifierSmooth(FModifier)

### FModifierSmooth(FModifier)

base classes — bpy_struct, FModifier

class bpy.types. FModifierSmooth ( FModifier )

Applies Gaussian smoothing to the curve.

filter_width

How many frames are averaged around each keyframe. Larger values smooth more but cost performance. (in [1, 32], default 0)

Type :

int

sigma

The width of the Gaussian distribution measured in frames. Smaller values sharpen the result across the Filter Width. (in [0.1, 100], default 0.0)

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

| bpy_struct.id_data FModifier.name FModifier.type FModifier.show_expanded FModifier.mute FModifier.is_valid FModifier.active | FModifier.use_restricted_range FModifier.frame_start FModifier.frame_end FModifier.blend_in FModifier.blend_out FModifier.use_influence FModifier.influence |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FModifier.bl_rna_get_subclass FModifier.bl_rna_get_subclass_py |

## FModifierStepped(FModifier)

### FModifierStepped(FModifier)

base classes — bpy_struct, FModifier

class bpy.types. FModifierStepped ( FModifier )

Holds each interpolated F-Curve value across several frames while leaving the timing untouched.

frame_end

Frame at which the modifier stops acting, where relevant (in [-inf, inf], default 0.0)

Type :

float

frame_offset

Number of reference frames to count off before holding begins (lets you choose, say, a ‘1-3’ vs a ‘5-7’ hold pattern) (in [-inf, inf], default 0.0)

Type :

float

frame_start

Frame at which the modifier begins acting, where relevant (in [-inf, inf], default 0.0)

Type :

float

frame_step

How many frames each value is held for (in [-inf, inf], default 2.0)

Type :

float

use_frame_end

Limit the modifier so it acts only before its ‘end’ frame (default False)

Type :

bool

use_frame_start

Limit the modifier so it acts only after its ‘start’ frame (default False)

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

| bpy_struct.id_data FModifier.name FModifier.type FModifier.show_expanded FModifier.mute FModifier.is_valid FModifier.active | FModifier.use_restricted_range FModifier.frame_start FModifier.frame_end FModifier.blend_in FModifier.blend_out FModifier.use_influence FModifier.influence |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FModifier.bl_rna_get_subclass FModifier.bl_rna_get_subclass_py |

## FollowPathConstraint(Constraint)

### FollowPathConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. FollowPathConstraint ( Constraint )

Pins an object's motion to follow the target path.

forward_axis

Axis that points forward along the path (default '`FORWARD_X`' )

Type :

Literal[‘`FORWARD_X`’, ‘`FORWARD_Y`’, ‘`FORWARD_Z`’, ‘`TRACK_NEGATIVE_X`’, ‘`TRACK_NEGATIVE_Y`’, ‘`TRACK_NEGATIVE_Z`’]

offset

Shift away from the position that matches the current time frame (in [-1.04857e+06, 1.04857e+06], default 0.0)

Type :

float

offset_factor

Percentage that places the target somewhere along the curve's length (in [-inf, inf], default 0.0)

Type :

float

target

Target Curve object

Type :

Object

up_axis

Axis that points upward (default '`UP_X`' )

Type :

Literal[‘`UP_X`’, ‘`UP_Y`’, ‘`UP_Z`’]

use_curve_follow

Object will follow the heading and banking of the curve (default False)

Type :

bool

use_curve_radius

Object is scaled by the curve radius (default False)

Type :

bool

use_fixed_location

Keep the object locked to one fixed point along the curve's length no matter the time (default False)

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

| bpy_struct.id_data Constraint.name Constraint.type Constraint.is_override_data Constraint.owner_space Constraint.target_space Constraint.space_object Constraint.space_subtarget | Constraint.mute Constraint.enabled Constraint.show_expanded Constraint.is_valid Constraint.active Constraint.influence Constraint.error_location Constraint.error_rotation |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Constraint.bl_rna_get_subclass Constraint.bl_rna_get_subclass_py |
