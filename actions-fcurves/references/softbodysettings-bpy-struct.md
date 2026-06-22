# Softbodysettings Bpy Struct, Soundequalizermodifier Stripmodifier, Soundstrip Strip, Spaceclipoverlay Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: SoftBodySettings(bpy_struct); SoundEqualizerModifier(StripModifier); SoundStrip(Strip); SpaceClipOverlay(bpy_struct); SpaceDopeSheetOverlay(bpy_struct); Speaker(ID); SpeedControlStrip(EffectStrip).

## SoftBodySettings(bpy_struct)

### SoftBodySettings(bpy_struct)

base class — bpy_struct

class bpy.types. SoftBodySettings ( bpy_struct )

The soft body simulation settings attached to an object.

aero

Make edges ‘sail’ (in [0, 30000], default 0)

Type :

int

aerodynamics_type

How aerodynamic interaction is computed (default 'SIMPLE' )

- SIMPLE
Simple – Surrounding media exert a drag force on edges.

- `LIFT_FORCE`
Lift Force – As edges move through the media, they pick up a lift force.

Type :

Literal[‘SIMPLE’, ‘`LIFT_FORCE`’]

ball_damp

Blending to inelastic collision (in [0.001, 1], default 0.0)

Type :

float

ball_size

Absolute ball size or factor if not manually adjusted (in [-10, 10], default 0.0)

Type :

float

ball_stiff

Ball inflating pressure (in [0.001, 100], default 0.0)

Type :

float

bend

Bending Stiffness (in [0, 10], default 0.0)

Type :

float

choke

‘Viscosity’ inside collision target (in [0, 100], default 0)

Type :

int

collision_collection

Limit colliders to this collection

Type :

Collection

collision_type

Choose Collision Type (default 'MANUAL' )

- MANUAL
Manual – Manual adjust.

- AVERAGE
Average – Average Spring length * Ball Size.

- MINIMAL
Minimal – Minimal Spring length * Ball Size.

- MAXIMAL
Maximal – Maximal Spring length * Ball Size.

- MINMAX
AvMinMax – (Min+Max)/2 * Ball Size.

Type :

Literal[‘MANUAL’, ‘AVERAGE’, ‘MINIMAL’, ‘MAXIMAL’, ‘MINMAX’]

damping

Edge spring friction (in [0, 50], default 0.0)

Type :

float

effector_weights

(readonly)

Type :

EffectorWeights

error_threshold

The Runge-Kutta ODE solver error limit, low value gives more precision, high values speed (in [0.001, 10], default 0.0)

Type :

float

friction

General media friction for point movements (in [0, 50], default 0.0)

Type :

float

fuzzy

Fuzziness while on collision, high values make collision handling faster but less stable (in [1, 100], default 0)

Type :

int

goal_default

Default Goal (vertex target position) value (in [0, 1], default 0.0)

Type :

float

goal_friction

Goal (vertex target position) friction (in [0, 50], default 0.0)

Type :

float

goal_max

Goal maximum, vertex weights are scaled to match this range (in [0, 1], default 0.0)

Type :

float

goal_min

Goal minimum, vertex weights are scaled to match this range (in [0, 1], default 0.0)

Type :

float

goal_spring

Goal (vertex target position) spring stiffness (in [0, 0.999], default 0.0)

Type :

float

gravity

Apply gravitation to point movement (in [-10, 10], default 0.0)

Type :

float

location_mass_center

Location of center of mass (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

mass

General Mass value (in [0, 50000], default 0.0)

Type :

float

plastic

Permanent deform (in [0, 100], default 0)

Type :

int

pull

Edge spring stiffness when longer than rest length (in [0, 0.999], default 0.0)

Type :

float

push

Edge spring stiffness when shorter than rest length (in [0, 0.999], default 0.0)

Type :

float

rotation_estimate

Estimated rotation matrix (multi-dimensional array of 3 * 3 items, in [-inf, inf], default ((0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0)))

Type :

mathutils.Matrix

scale_estimate

Estimated scale matrix (multi-dimensional array of 3 * 3 items, in [-inf, inf], default ((0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0)))

Type :

mathutils.Matrix

shear

Shear Stiffness (in [0, 1], default 0.0)

Type :

float

speed

Tweak timing for physics to control frequency and speed (in [0.01, 100], default 0.0)

Type :

float

spring_length

Alter spring length to shrink/blow up (unit %) 0 to disable (in [0, 200], default 0)

Type :

int

step_max

Maximal # solver steps/frame (in [0, 30000], default 0)

Type :

int

step_min

Minimal # solver steps/frame (in [0, 30000], default 0)

Type :

int

use_auto_step

Use velocities for automagic step sizes (default False)

Type :

bool

use_diagnose

Turn on SB diagnose console prints (default False)

Type :

bool

use_edge_collision

Edges collide too (default False)

Type :

bool

use_edges

Use Edges as springs (default False)

Type :

bool

use_estimate_matrix

Store the estimated transforms in the soft body settings (default False)

Type :

bool

use_face_collision

Faces collide too, can be very slow (default False)

Type :

bool

use_goal

Define forces for vertices to stick to animated position (default False)

Type :

bool

use_self_collision

Enable naive vertex ball self collision (default False)

Type :

bool

use_stiff_quads

Add diagonal springs on 4-gons (default False)

Type :

bool

vertex_group_goal

Control point weight values (default “”, never None)

Type :

str

vertex_group_mass

Control point mass values (default “”, never None)

Type :

str

vertex_group_spring

Control point spring strength values (default “”, never None)

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

| Object.soft_body | SoftBodyModifier.settings |

## SoundEqualizerModifier(StripModifier)

### SoundEqualizerModifier(StripModifier)

base classes — bpy_struct, StripModifier

class bpy.types. SoundEqualizerModifier ( StripModifier )

Applies equalization to audio

graphics

Graphical form of the equalization (default None, readonly)

Type :

bpy_prop_collection[EQCurveMappingData]

new_graphic ( min_freq , max_freq )

Insert another EQ band

Parameters :

- min_freq ( float ) – Minimum Frequency, Minimum Frequency (in [0, 20000])

- max_freq ( float ) – Maximum Frequency, Maximum Frequency (in [0, 20000])

Returns :

The graphical Equalizer definition that was just created

Return type :

EQCurveMappingData

clear_soundeqs ( )

Delete every graphical equalizer belonging to the Equalizer modifier

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

The matching RNA type, or the default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

The matching class, or the default if none is found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data StripModifier.name StripModifier.type StripModifier.mute StripModifier.enable StripModifier.show_expanded | StripModifier.input_mask_type StripModifier.mask_time StripModifier.input_mask_strip StripModifier.input_mask_id StripModifier.is_active |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values StripModifier.bl_rna_get_subclass StripModifier.bl_rna_get_subclass_py |

## SoundStrip(Strip)

### SoundStrip(Strip)

base classes — bpy_struct, Strip

class bpy.types. SoundStrip ( Strip )

A sequencer strip that schedules a sound to play across a span of time

animation_offset_end

Animation end offset (trim end) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_end’.

Type :

int

animation_offset_start

Animation start offset (trim start) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_start’.

Type :

int

content_trim_end

How many frames to skip at the tail of the underlying source. Trimming the source turns later frames into holds (in [0, inf], default 0)

Type :

int

content_trim_start

How many frames to skip at the head of the underlying source. Trimming the source turns earlier frames into holds (in [0, inf], default 0)

Type :

int

pan

Panning applied to the sound during playback (Mono sources only) (in [-inf, inf], default 0.0)

Type :

float

pitch_correction

Hold the audio's original pitch even as playback speed changes (default False)

Type :

bool

retiming_keys

(default None, readonly)

Type :

RetimingKeys[RetimingKey]

show_waveform

Draw the audio waveform within the strip (default False)

Type :

bool

sound

The Sound data-block this strip draws from

Type :

Sound

sound_offset

Subframe shift of where the sound source begins, measured in seconds (in [-inf, inf], default 0.0)

Type :

float

volume

Volume at which the sound plays back (in [0, 100], default 1.0)

Type :

float

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

The matching RNA type, or the default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

The matching class, or the default if none is found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start | Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py |

## SpaceClipOverlay(bpy_struct)

### SpaceClipOverlay(bpy_struct)

base class — bpy_struct

class bpy.types. SpaceClipOverlay ( bpy_struct )

Configuration for the overlays drawn in the Movie Clip editor

show_cursor

Draw the 2D cursor (default True)

Type :

bool

show_overlays

Draw overlays such as the cursor and annotations (default True)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

The matching RNA type, or the default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

The matching class, or the default if none is found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| SpaceClipEditor.overlay | |

## SpaceDopeSheetOverlay(bpy_struct)

### SpaceDopeSheetOverlay(bpy_struct)

base class — bpy_struct

class bpy.types. SpaceDopeSheetOverlay ( bpy_struct )

show_overlays

Draw the overlays (default True)

Type :

bool

show_scene_strip_range

With scene time synchronization active in the sequence editor, draw the span of the current scene strip (default False)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

The matching RNA type, or the default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

The matching class, or the default if none is found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| SpaceDopeSheetEditor.overlays | |

## Speaker(ID)

### Speaker(ID)

base classes — bpy_struct, ID

class bpy.types. Speaker ( ID )

Data-block holding a 3D audio speaker object

animation_data

This data-block's animation data (readonly)

Type :

AnimData

attenuation

Strength with which distance affects volume, according to the distance model (in [0, inf], default 1.0)

Type :

float

cone_angle_inner

Inner cone angle in degrees; volume stays at 100% within this cone (in [0, 360], default 360.0)

Type :

float

cone_angle_outer

Outer cone angle in degrees; past it the volume drops to the outer cone volume, and it is interpolated between the inner and outer cones (in [0, 360], default 360.0)

Type :

float

cone_volume_outer

Volume beyond the outer cone (in [0, 1], default 1.0)

Type :

float

distance_max

Farthest distance considered for volume, regardless of how distant the object becomes (in [0, inf], default 3.40282e+38)

Type :

float

distance_reference

Distance of reference where volume reaches 100% (in [0, inf], default 1.0)

Type :

float

muted

Silence the speaker (default False)

Type :

bool

pitch

Pitch the sound plays back at (in [0.1, 10], default 1.0)

Type :

float

sound

The sound data-block the speaker uses

Type :

Sound

volume

Loudness of the sound (in [0, 1], default 1.0)

Type :

float

volume_max

Highest volume, regardless of how near the object gets (in [0, 1], default 1.0)

Type :

float

volume_min

Lowest volume, regardless of how distant the object gets (in [0, 1], default 0.0)

Type :

float

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| bpy.context.speaker BlendData.speakers | BlendDataSpeakers.new BlendDataSpeakers.remove |

## SpeedControlStrip(EffectStrip)

### SpeedControlStrip(EffectStrip)

base classes — bpy_struct, Strip, EffectStrip

class bpy.types. SpeedControlStrip ( EffectStrip )

Strip used to govern how fast other strips play

input_1

The effect strip's first input (never None)

Type :

Strip

input_count

(in [0, inf], default 0, readonly)

Type :

int

speed_control

Which method controls the speed (default 'STRETCH' )

- STRETCH
Stretch – Change the input's playback speed so its length matches the strip.

- MULTIPLY
Multiply – Scale the speed by the speed factor.

- `FRAME_NUMBER`
Frame Number – A frame number within the input strip.

- LENGTH
Length – A percentage of the input strip's length.

Type :

Literal[‘STRETCH’, ‘MULTIPLY’, ‘`FRAME_NUMBER`’, ‘LENGTH’]

speed_factor

Scale the strip's present speed by this number, or remap the current frame onto this frame (in [-inf, inf], default 0.0)

Type :

float

speed_frame_number

A frame number within the input strip (in [-inf, inf], default 0.0)

Type :

float

speed_length

A percentage of the input strip's length (in [-inf, inf], default 0.0)

Type :

float

use_frame_interpolate

Crossfade-blend the current frame into the next one (default False)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset | Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys EffectStrip.use_deinterlace EffectStrip.alpha_mode EffectStrip.use_flip_x EffectStrip.use_flip_y EffectStrip.use_float EffectStrip.use_reverse_frames EffectStrip.color_multiply EffectStrip.multiply_alpha EffectStrip.color_saturation EffectStrip.strobe EffectStrip.transform EffectStrip.crop EffectStrip.use_proxy EffectStrip.proxy |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py EffectStrip.bl_rna_get_subclass EffectStrip.bl_rna_get_subclass_py |
