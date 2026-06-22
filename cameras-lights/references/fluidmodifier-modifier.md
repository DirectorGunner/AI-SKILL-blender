# Fluidmodifier Modifier, Fmodifier Bpy Struct, Fmodifiercycles Fmodifier, Followtrackconstraint Constraint ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: FluidModifier(Modifier); FModifier(bpy_struct); FModifierCycles(FModifier); FollowTrackConstraint(Constraint); FreestyleModules(bpy_prop_collection); FreestyleModuleSettings(bpy_struct); GreasePencilArmatureModifier(Modifier); GreasePencilTimeModifier(Modifier); HookModifier(Modifier).

## FluidModifier(Modifier)

### FluidModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. FluidModifier ( Modifier )

Modifier that runs a fluid simulation.

domain_settings

(readonly)

Type :

FluidDomainSettings

effector_settings

(readonly)

Type :

FluidEffectorSettings

flow_settings

(readonly)

Type :

FluidFlowSettings

fluid_type

(default 'NONE' )

- NONE
None.

- DOMAIN
Domain – Container of the fluid simulation.

- FLOW
Flow – Add or remove fluid to a domain object.

- EFFECTOR
Effector – Deflect fluids and influence the fluid flow.

Type :

Literal[‘NONE’, ‘DOMAIN’, ‘FLOW’, ‘EFFECTOR’]

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

## FModifier(bpy_struct)

### FModifier(bpy_struct)

base class — bpy_struct

subclasses —
FModifierCycles, FModifierEnvelope, FModifierFunctionGenerator, FModifierGenerator, FModifierLimits, FModifierNoise, FModifierSmooth, FModifierStepped

class bpy.types. FModifier ( bpy_struct )

Base type for things that alter an F-Curve's values.

active

Whether this F-Curve modifier exposes its settings in the editor (default False)

Type :

bool

blend_in

Count of frames measured from the start frame over which the influence ramps up (in [-inf, inf], default 0.0)

Type :

float

blend_out

Count of frames measured from the end frame over which the influence ramps down (in [-inf, inf], default 0.0)

Type :

float

frame_end

Frame at which the modifier stops having an effect, when Restrict Frame Range is active (in [-inf, inf], default 0.0)

Type :

float

frame_start

Frame at which the modifier begins having an effect, when Restrict Frame Range is active (in [-inf, inf], default 0.0)

Type :

float

influence

How strongly the F-Curve Modifier acts once it is past any fade in or out (in [0, 1], default 1.0)

Type :

float

is_valid

Set when the F-Curve Modifier's settings are invalid, so it is skipped during evaluation (default True, readonly)

Type :

bool

mute

Turn evaluation of the F-Curve modifier on (default False)

Type :

bool

name

Name given to the F-Curve Modifier (default “”, never None)

Type :

str

show_expanded

Whether the F-Curve Modifier's panel appears expanded in the UI (default False)

Type :

bool

type

Kind of F-Curve Modifier (default 'NULL' , readonly)

Type :

Literal[Fmodifier Type Items]

use_influence

When set, a default factor scales down what the F-Curve Modifier does (default False)

Type :

bool

use_restricted_range

Confine the F-Curve Modifier to the chosen frame range, which helps mask off its effect so several can be chained (default False)

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| FCurve.modifiers FCurveModifiers.active FCurveModifiers.new | FCurveModifiers.remove NlaStrip.modifiers |

## FModifierCycles(FModifier)

### FModifierCycles(FModifier)

base classes — bpy_struct, FModifier

class bpy.types. FModifierCycles ( FModifier )

Loops the values from the F-Curve it modifies.

cycles_after

Cap on how many cycles may run past the final keyframe, where 0 means unlimited (in [-32768, 32767], default 0)

Type :

int

cycles_before

Cap on how many cycles may run ahead of the first keyframe, where 0 means unlimited (in [-32768, 32767], default 0)

Type :

int

mode_after

Which cycling mode applies past the last keyframe (default 'NONE' )

- NONE
No Cycles – Don’t do anything.

- REPEAT
Repeat Motion – Repeat keyframe range as-is.

- `REPEAT_OFFSET`
Repeat with Offset – Repeat keyframe range, but with offset based on gradient between start and end values.

- MIRROR
Repeat Mirrored – Alternate between forward and reverse playback of keyframe range.

Type :

Literal[‘NONE’, ‘REPEAT’, ‘`REPEAT_OFFSET`’, ‘MIRROR’]

mode_before

Which cycling mode applies ahead of the first keyframe (default 'NONE' )

- NONE
No Cycles – Don’t do anything.

- REPEAT
Repeat Motion – Repeat keyframe range as-is.

- `REPEAT_OFFSET`
Repeat with Offset – Repeat keyframe range, but with offset based on gradient between start and end values.

- MIRROR
Repeat Mirrored – Alternate between forward and reverse playback of keyframe range.

Type :

Literal[‘NONE’, ‘REPEAT’, ‘`REPEAT_OFFSET`’, ‘MIRROR’]

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

## FollowTrackConstraint(Constraint)

### FollowTrackConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. FollowTrackConstraint ( Constraint )

Pins an object's motion to follow the target motion track.

camera

Camera the motion is parented to; when left empty the active scene camera is used instead

Type :

Object

clip

Movie Clip that supplies the tracking data

Type :

MovieClip

depth_object

Object whose surface is projected onto to establish depth within camera space

Type :

Object

frame_method

The way the footage is fitted inside the camera frame (default 'STRETCH' )

Type :

Literal[‘STRETCH’, ‘FIT’, ‘CROP’]

object

Movie tracking object to follow (if empty, camera object is used) (default “”, never None)

Type :

str

track

Movie tracking track to follow (default “”, never None)

Type :

str

use_3d_position

Use 3D position of track to parent to (default False)

Type :

bool

use_active_clip

Use active clip defined in scene (default False)

Type :

bool

use_undistorted_position

Parent to undistorted position of 2D track (default False)

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

## FreestyleModules(bpy_prop_collection)

### FreestyleModules(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. FreestyleModules ( bpy_prop_collection ) 

An ordered set of style modules, evaluated from the top down

new ( ) 

Append a style module to the Freestyle settings of a scene render layer

Returns :

Newly created style module

Return type :

FreestyleModuleSettings

remove ( module ) 

Delete a style module from the Freestyle settings of a scene render layer

Parameters :

module (FreestyleModuleSettings) – Style module to remove (never None)

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

| FreestyleSettings.modules | |

## FreestyleModuleSettings(bpy_struct)

### FreestyleModuleSettings(bpy_struct) 

base class — bpy_struct

class bpy.types. FreestyleModuleSettings ( bpy_struct ) 

Configuration that points at a single style module

script 

The Python text block holding the style module's code

Type :

Text

use 

Toggle whether this style module is active while strokes are rendered (default False)

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

| FreestyleModules.new FreestyleModules.remove | FreestyleSettings.modules |

## GreasePencilArmatureModifier(Modifier)

### GreasePencilArmatureModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilArmatureModifier ( Modifier )

Bends stroke points by way of an armature object.

invert_vertex_group

Flip the weights of the vertex group (default False)

Type :

bool

object

Armature object to deform with

Type :

Object

open_influence_panel

(default False)

Type :

bool

use_bone_envelopes

Tie bone envelopes into the armature modifier (default False)

Type :

bool

use_deform_preserve_volume

Interpolate deform rotations through quaternions (default False)

Type :

bool

use_vertex_groups

Tie vertex groups into the armature modifier (default True)

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

## GreasePencilTimeModifier(Modifier)

### GreasePencilTimeModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilTimeModifier ( Modifier )

Shifts which keyframes are shown over time.

frame_end

Final frame of the range (in [0, 1048574], default 250)

Type :

int

frame_scale

Evaluation time in seconds (in [0.001, 100], default 1.0)

Type :

float

frame_start

First frame of the range (in [0, 1048574], default 1)

Type :

int

invert_layer_filter

Invert layer filter (default False)

Type :

bool

invert_layer_pass_filter

Invert layer pass filter (default False)

Type :

bool

layer_pass_filter

Layer pass filter (in [0, 100], default 0)

Type :

int

mode

(default 'NORMAL' )

- NORMAL
Regular – Offset runs in the normal playback direction.

- REVERSE
Reverse – Offset runs against the playback direction.

- FIX
Fixed Frame – Hold on one frame so it stays put as time advances.

- PINGPONG
Ping Pong – Bounce back and forth, opening in reverse.

- CHAIN
Chain – A sequence of animation segments strung together.

Type :

Literal['NORMAL', 'REVERSE', 'FIX', 'PINGPONG', 'CHAIN']

offset

Number of frames to offset original keyframe number or frame to fix (in [-32768, 32767], default 1)

Type :

int

open_custom_range_panel

(default False)

Type :

bool

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

bpy_prop_collection[GreasePencilTimeModifierSegment]

tree_node_filter

Layer name (default "", never None)

Type :

str

use_custom_frame_range

Define a custom range of frames to use in modifier (default False)

Type :

bool

use_keep_loop

Retiming end frames and move to start of animation to keep loop (default True)

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

## HookModifier(Modifier)

### HookModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. HookModifier ( Modifier )

Drives vertex positions from an external object or bone.

center

Center of the hook, used for falloff and display (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

falloff_curve

Custom falloff curve (readonly)

Type :

CurveMapping

falloff_radius

When non-zero, sets how far from the hook the influence reaches before dropping off (in [0, inf], default 0.0)

Type :

float

falloff_type

(default 'SMOOTH' )

Type :

Literal['NONE', 'CURVE', 'SMOOTH', 'SPHERE', 'ROOT', '`INVERSE_SQUARE`', 'SHARP', 'LINEAR', 'CONSTANT']

invert_vertex_group

Invert vertex group influence (default False)

Type :

bool

matrix_inverse

Undoes the transform sitting between this object and its target (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((1.0, 0.0, 0.0, 0.0), (0.0, 1.0, 0.0, 0.0), (0.0, 0.0, 1.0, 0.0), (0.0, 0.0, 0.0, 1.0)))

Type :

mathutils.Matrix

object

The hook's parent object; setting it also recomputes and resets the offset

Type :

Object

strength

Relative force of the hook (in [0, 1], default 1.0)

Type :

float

subtarget

The parent bone's name for the hook where relevant; assigning it likewise recomputes and resets the offset (default "", never None)

Type :

str

use_falloff_uniform

Compensate for non-uniform object scale (default False)

Type :

bool

vertex_group

Name of the vertex group that sets per-point modifier influence (default "", never None)

Type :

str

vertex_indices

The indices of the vertices the modifier is bound to; on Bézier curves, handles register as extra vertices. (array of 64 items, in [0, inf], default (0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0), readonly)

Type :

bpy_prop_array[int]

vertex_indices_set ( indices )

Checks and stores the array of vertex indices the modifier is bound to.

Parameters :

indices ( Sequence [ int ] ) – Vertex Indices (array of 64 items, in [-inf, inf])

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
