# Movietrackingstabilization Bpy Struct, Movietrackingtracks Bpy Prop Collection, Multicamstrip Effectstrip, Multiplystrip Effectstrip ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: MovieTrackingStabilization(bpy_struct); MovieTrackingTracks(bpy_prop_collection); MulticamStrip(EffectStrip); MultiplyStrip(EffectStrip); NDOFMotionEventData(bpy_struct); NlaStrip(bpy_struct); NlaStripFCurves(bpy_prop_collection).

## MovieTrackingStabilization(bpy_struct)

### MovieTrackingStabilization(bpy_struct)

base class — bpy_struct

class bpy.types. MovieTrackingStabilization ( bpy_struct )

2D stabilization driven by tracking markers

active_rotation_track_index

Position of the active track in the rotation-stabilization track list (in [-inf, inf], default 0)

Type :

int

active_track_index

Position of the active track in the translation-stabilization track list (in [-inf, inf], default 0)

Type :

int

anchor_frame

Frame used as the stabilization anchor; every other frame is positioned relative to it (in [0, 1048574], default 0)

Type :

int

filter_type

Which interpolation handles the sub-pixel shifts and rotations introduced by stabilization (default 'NEAREST' )

- NEAREST
Nearest – No interpolation, use nearest neighbor pixel.

- BILINEAR
Bilinear – Simple interpolation between adjacent pixels.

- BICUBIC
Bicubic – High quality pixel interpolation.

Type :

Literal[‘NEAREST’, ‘BILINEAR’, ‘BICUBIC’]

influence_location

Degree to which the stabilization affects footage location (in [0, 1], default 0.0)

Type :

float

influence_rotation

Degree to which the stabilization affects footage rotation (in [0, 1], default 0.0)

Type :

float

influence_scale

Degree to which the stabilization affects footage scale (in [0, 1], default 0.0)

Type :

float

rotation_tracks

Set of tracks feeding 2D stabilization (translation) (default None, readonly)

Type :

bpy_prop_collection[MovieTrackingTrack]

scale_max

Cap on how much automatic scaling is allowed (in [0, 10], default 0.0)

Type :

float

show_tracks_expanded

Display the UI list of the tracks taking part in stabilization (default False)

Type :

bool

target_position

Known relative offset of the original shot that gets subtracted out (e.g. for a panning shot; can be animated) (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

target_rotation

Rotation present in the original shot that gets compensated (e.g. for deliberate tilting) (in [-inf, inf], default 0.0)

Type :

float

target_scale

Scale applied to the result to offset zoom in the original shot (in [1.192e-07, inf], default 0.0)

Type :

float

tracks

Set of tracks feeding 2D stabilization (translation) (default None, readonly)

Type :

bpy_prop_collection[MovieTrackingTrack]

use_2d_stabilization

Apply 2D stabilization to the footage (default False)

Type :

bool

use_autoscale

Scale the footage automatically so unfilled regions get covered while stabilizing (default False)

Type :

bool

use_stabilize_rotation

Steady the detected rotation around the frame center (default False)

Type :

bool

use_stabilize_scale

Offset any scale changes measured relative to the rotation center (default False)

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

| MovieTracking.stabilization | |

## MovieTrackingTracks(bpy_prop_collection)

### MovieTrackingTracks(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MovieTrackingTracks ( bpy_prop_collection )

Set of movie-tracking tracks

active

The track currently active in this tracking data. Deprecated, use objects[name].tracks.active

Type :

MovieTrackingTrack

new ( * , name = '' , frame = 1 )

Create new motion track in this movie clip

Parameters :

- name ( str ) – Name of new track (optional, never None)

- frame ( int ) – Frame, Frame number to add track on (in [0, 1048574], optional)

Returns :

Newly created track

Return type :

MovieTrackingTrack

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

| MovieTracking.tracks | |

## MulticamStrip(EffectStrip)

### MulticamStrip(EffectStrip)

base classes — bpy_struct, Strip, EffectStrip

class bpy.types. MulticamStrip ( EffectStrip )

Sequencer strip that handles multicam editing

animation_offset_end

End-side animation offset (trim end) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_end’.

Type :

int

animation_offset_start

Start-side animation offset (trim start) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_start’.

Type :

int

content_trim_end

Count of frames discarded at the end of the underlying source; the source is trimmed and later frames become holds (in [0, inf], default 0)

Type :

int

content_trim_start

Count of frames discarded at the start of the underlying source; the source is trimmed and earlier frames become holds (in [0, inf], default 0)

Type :

int

input_count

(in [0, inf], default 0, readonly)

Type :

int

multicam_source

(in [0, 127], default 0)

Type :

int

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

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset | Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys EffectStrip.use_deinterlace EffectStrip.alpha_mode EffectStrip.use_flip_x EffectStrip.use_flip_y EffectStrip.use_float EffectStrip.use_reverse_frames EffectStrip.color_multiply EffectStrip.multiply_alpha EffectStrip.color_saturation EffectStrip.strobe EffectStrip.transform EffectStrip.crop EffectStrip.use_proxy EffectStrip.proxy |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py EffectStrip.bl_rna_get_subclass EffectStrip.bl_rna_get_subclass_py |

## MultiplyStrip(EffectStrip)

### MultiplyStrip(EffectStrip)

base classes — bpy_struct, Strip, EffectStrip

class bpy.types. MultiplyStrip ( EffectStrip )

Multiply Strip

input_1

The effect strip's first input (never None)

Type :

Strip

input_2

The effect strip's second input (never None)

Type :

Strip

input_count

(in [0, inf], default 0, readonly)

Type :

int

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

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset | Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys EffectStrip.use_deinterlace EffectStrip.alpha_mode EffectStrip.use_flip_x EffectStrip.use_flip_y EffectStrip.use_float EffectStrip.use_reverse_frames EffectStrip.color_multiply EffectStrip.multiply_alpha EffectStrip.color_saturation EffectStrip.strobe EffectStrip.transform EffectStrip.crop EffectStrip.use_proxy EffectStrip.proxy |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py EffectStrip.bl_rna_get_subclass EffectStrip.bl_rna_get_subclass_py |

## NDOFMotionEventData(bpy_struct)

### NDOFMotionEventData(bpy_struct)

base class — bpy_struct

class bpy.types. NDOFMotionEventData ( bpy_struct )

Motion information from an NDOF device carried on window manager events.

progress

Reports which phase the gesture is currently in (default 'STARTING' , readonly)

Type :

Literal[‘STARTING’, ‘`IN_PROGRESS`’, ‘FINISHING’]

rotation

Rotation of this motion event given as an axis-angle pair. A magnitude of 1.0 on the vector corresponds to a full 360-degree turn, and the angle is usually multiplied by the time-delta before it is applied. (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

time_delta

Elapsed time in seconds since the prior motion event (in [-inf, inf], default 0.0, readonly)

Type :

float

translation

Movement carried by this motion event. Each axis ranges from -1 to 1 before the sensitivity preference scales it, and the result is usually multiplied by the time-delta prior to use. (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

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

| Event.ndof_motion | |

## NlaStrip(bpy_struct)

### NlaStrip(bpy_struct)

base class — bpy_struct

class bpy.types. NlaStrip ( bpy_struct )

Wraps and points at an already-existing Action.

action

The Action this strip points to

Type :

Action

action_frame_end

Final frame of the action that gets used (in [-inf, inf], default 0.0)

Type :

float

action_frame_start

Initial frame of the action that gets used (in [-inf, inf], default 0.0)

Type :

float

action_slot

Picks out which portion of the Action belongs to this strip; its name is what gets matched when a different Action is assigned

Type :

ActionSlot

action_slot_handle

A numeric handle marking which portion of the Action is meant for this NLA strip (in [-inf, inf], default 0)

Type :

int

action_suitable_slots

Action slots that would work for this NLA strip (default None, readonly)

Type :

bpy_prop_collection[ActionSlot]

active

Whether this NLA Strip is the active one (default False, readonly)

Type :

bool

blend_in

Count of frames at the strip start over which influence fades up (in [-inf, inf], default 0.0)

Type :

float

blend_out

(in [-inf, inf], default 0.0)

Type :

float

blend_type

How this strip's output is merged into the running result (default 'REPLACE' )

- REPLACE
Replace – The strip values replace the accumulated results by amount specified by influence.

- COMBINE
Combine – The strip values are combined with accumulated results by appropriately using addition, multiplication, or quaternion math, based on channel type.

- ADD
Add – Weighted result of strip is added to the accumulated results.

- SUBTRACT
Subtract – Weighted result of strip is removed from the accumulated results.

- MULTIPLY
Multiply – Weighted result of strip is multiplied with the accumulated results.

Type :

Literal[‘REPLACE’, ‘COMBINE’, ‘ADD’, ‘SUBTRACT’, ‘MULTIPLY’]

extrapolation

What happens in the gaps that fall outside the strip's range (default 'HOLD' )

- NOTHING
Nothing – Strip has no influence past its extents.

- HOLD
Hold – Hold the first frame if no previous strips in track, and always hold last frame.

- `HOLD_FORWARD`
Hold Forward – Only hold last frame.

Type :

Literal[‘NOTHING’, ‘HOLD’, ‘`HOLD_FORWARD`’]

fcurves

The F-Curves that drive this strip's influence and timing (default None, readonly)

Type :

NlaStripFCurves[FCurve]

frame_end

(in [-inf, inf], default 0.0)

Type :

float

frame_end_raw

Like frame_end, but accepts any value at all, even ones that leave the strip in an invalid state (in [-inf, inf], default 0.0)

Type :

float

frame_end_ui

Where the NLA strip ends. Be aware that setting it also revises the strip’s repeat count or the end frame of its action; to alter the end frame on its own, reach for the “frame_end” property instead. (in [-inf, inf], default 0.0)

Type :

float

frame_start

(in [-inf, inf], default 0.0)

Type :

float

frame_start_raw

Like frame_start, but accepts any value at all, even ones that leave the strip in an invalid state (in [-inf, inf], default 0.0)

Type :

float

frame_start_ui

Where the NLA strip begins. Be aware that setting it also revises the strip’s end frame; to alter the start frame on its own, reach for the “frame_start” property instead. (in [-inf, inf], default 0.0)

Type :

float

influence

How much this strip adds to the present result (in [0, 1], default 0.0)

Type :

float

last_slot_identifier

Identifier of the action slot assigned most recently. The slot marks which portion of the Action is meant for this strip, and its identifier is what gets matched when an Action is assigned. (default “”, never None)

Type :

str

modifiers

Modifiers acting on every F-Curve within the referenced Action (default None, readonly)

Type :

bpy_prop_collection[FModifier]

mute

Turn off evaluation of this NLA Strip (default False)

Type :

bool

name

(default “”, never None)

Type :

str

repeat

How many times the action range is looped (in [0.1, 1000], default 1.0)

Type :

float

scale

Factor by which the action is scaled (in [0.0001, 1000], default 1.0)

Type :

float

select

Whether this NLA Strip is selected (default False)

Type :

bool

strip_time

Which frame of the referenced Action gets evaluated (in [-inf, inf], default 0.0)

Type :

float

strips

The NLA Strips this strip contains, when its type is Meta (default None, readonly)

Type :

bpy_prop_collection[NlaStrip]

type

Which kind of NLA Strip this is (default 'CLIP' , readonly)

- CLIP
Action Clip – NLA Strip references some Action.

- TRANSITION
Transition – NLA Strip ‘transitions’ between adjacent strips.

- META
Meta – NLA Strip acts as a container for adjacent strips.

- SOUND
Sound Clip – NLA Strip representing a sound event for speakers.

Type :

Literal[‘CLIP’, ‘TRANSITION’, ‘META’, ‘SOUND’]

use_animated_influence

Drive the influence from an F-Curve instead of letting it be worked out automatically (default False)

Type :

bool

use_animated_time

Drive the strip time from an F-Curve instead of letting it be worked out automatically (default False)

Type :

bool

use_animated_time_cyclic

Loop the animated time so it stays within the action's start and end (default False)

Type :

bool

use_auto_blend

Derive the Blend In/Out frame counts automatically from overlapping strips (default False)

Type :

bool

use_reverse

Run this NLA Strip backwards (applies only when timing is worked out automatically) (default False)

Type :

bool

use_sync_length

Refresh the range of referenced action frames once the strip and its keyframes are tweaked (default False)

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

| bpy.context.active_nla_strip bpy.context.selected_nla_strips NlaStrip.strips | NlaStrips.new NlaStrips.remove NlaTrack.strips |

## NlaStripFCurves(bpy_prop_collection)

### NlaStripFCurves(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NlaStripFCurves ( bpy_prop_collection )

A set of F-Curves belonging to an NLA strip.

find ( data_path , * , index = 0 )

Locate an F-Curve. Be aware that this call walks every F-Curve in the NLA strip one by one.

Parameters :

- data_path ( str ) – Data Path, F-Curve data path (never None)

- index ( int ) – Index, Array index (in [0, inf], optional)

Returns :

The matching F-Curve, or None when there is none

Return type :

FCurve

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

| NlaStrip.fcurves | |
