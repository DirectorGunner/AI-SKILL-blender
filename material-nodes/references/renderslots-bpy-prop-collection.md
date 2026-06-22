# Renderslots Bpy Prop Collection, Repeatitem Bpy Struct, Scene Id, Scenedisplay Bpy Struct

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: RenderSlots(bpy_prop_collection); RepeatItem(bpy_struct); Scene(ID); SceneDisplay(bpy_struct).

## RenderSlots(bpy_prop_collection)

### RenderSlots(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. RenderSlots ( bpy_prop_collection )

Collection of render layers

active

Active render slot of the image

Type :

RenderSlot

active_index

Active render slot of the image (in [0, 32767], default 0)

Type :

int

new ( * , name = '' )

Create a new render slot on the image

Parameters :

name ( str ) – Name, New name for the render slot (optional, never None)

Returns :

Newly created render layer

Return type :

RenderSlot

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

| Image.render_slots | |

## RepeatItem(bpy_struct)

### RepeatItem(bpy_struct)

base class — bpy_struct

class bpy.types. RepeatItem ( bpy_struct )

color

Color shown for this socket type within the node editor (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

name

(default “”, never None)

Type :

str

socket_type

(default 'FLOAT' )

Type :

Literal[Node Socket Data Type Items]

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

| GeometryNodeBake.active_item GeometryNodeCaptureAttribute.active_item GeometryNodeFieldToGrid.active_item GeometryNodeRepeatOutput.active_item | GeometryNodeRepeatOutput.repeat_items NodeGeometryRepeatOutputItems.new NodeGeometryRepeatOutputItems.remove |

## Scene(ID)

### Scene(ID)

base classes — bpy_struct, ID

class bpy.types. Scene ( ID )

A Scene data-block: it holds the objects and sets the time- and render-related settings

active_clip

Active Movie Clip available to motion tracking constraints or usable as a camera's background image

Type :

MovieClip

animation_data

Animation data for this data-block (readonly)

Type :

AnimData

annotation

Data-block holding the 3D view's annotations

Type :

Annotation

audio_distance_model

Distance model used when computing distance attenuation (default '`INVERSE_CLAMPED`' )

- NONE
None – No distance attenuation.

- INVERSE
Inverse – Inverse distance model.

- `INVERSE_CLAMPED`
Inverse Clamped – Inverse distance model with clamping.

- LINEAR
Linear – Linear distance model.

- `LINEAR_CLAMPED`
Linear Clamped – Linear distance model with clamping.

- EXPONENT
Exponential – Exponential distance model.

- `EXPONENT_CLAMPED`
Exponential Clamped – Exponential distance model with clamping.

Type :

Literal[‘NONE’, ‘INVERSE’, ‘`INVERSE_CLAMPED`’, ‘LINEAR’, ‘`LINEAR_CLAMPED`’, ‘EXPONENT’, ‘`EXPONENT_CLAMPED`’]

audio_doppler_factor

Pitch factor used when computing the Doppler effect (in [0, inf], default 1.0)

Type :

float

audio_doppler_speed

Speed of sound used when computing the Doppler effect (in [0.01, inf], default 343.3)

Type :

float

audio_volume

Audio volume (in [0, 100], default 1.0)

Type :

float

background_set

Background set scene

Type :

Scene

camera

Active camera the scene is rendered through

Type :

Object

collection

The scene's root collection, owner of every object and nested collection placed in the scene (readonly, never None)

Type :

Collection

compositing_node_group

Compositor Nodes

Type :

NodeTree

cursor

(readonly, never None)

Type :

View3DCursor

cycles

Cycles render settings (readonly)

Type :

CyclesRenderSettings

cycles_curves

Cycles curves rendering settings (readonly)

Type :

CyclesCurveRenderSettings

display

Scene display settings for 3D viewport (readonly)

Type :

SceneDisplay

display_settings

Settings for the device the saved image would be shown on (readonly)

Type :

ColorManagedDisplaySettings

eevee

EEVEE settings for the scene (readonly)

Type :

SceneEEVEE

frame_current

Current frame; from Python prefer frame_set() to refresh animation data instead (in [-1048574, 1048574], default 1)

Type :

int

frame_current_final

Current frame once subframe and time remapping are applied (in [-1.04857e+06, 1.04857e+06], default 0.0, readonly)

Type :

float

frame_end

Last frame of the playback/rendering range (in [0, 1048574], default 250)

Type :

int

frame_float

(in [-1.04857e+06, 1.04857e+06], default 0.0)

Type :

float

frame_preview_end

Alternative end frame used for UI playback (in [-inf, inf], default 0)

Type :

int

frame_preview_start

Alternative start frame used for UI playback (in [-inf, inf], default 0)

Type :

int

frame_start

First frame of the playback/rendering range (in [0, 1048574], default 1)

Type :

int

frame_step

How many frames to advance for each rendered or played-back frame (in [0, 1048574], default 1)

Type :

int

frame_subframe

(in [0, 1], default 0.0)

Type :

float

gravity

A steady acceleration applied in a chosen direction (array of 3 items, in [-inf, inf], default (0.0, 0.0, -9.81))

Type :

mathutils.Vector

grease_pencil_settings

Grease Pencil settings for the scene (readonly)

Type :

SceneGpencil

hydra

Hydra settings for the scene (readonly)

Type :

SceneHydra

is_nla_tweakmode

True when an NLA-referenced action is currently being edited; strictly read-only (default False, readonly)

Type :

bool

keying_sets

Absolute Keying Sets for this Scene (default None, readonly)

Type :

KeyingSets[KeyingSet]

keying_sets_all

Every Keying Set you can use, both Builtins and this Scene's Absolute Keying Sets (default None, readonly)

Type :

KeyingSetsAll[KeyingSet]

lock_frame_selection_to_range

Stop the mouse from selecting a frame outside the frame range (default False)

Type :

bool

objects

(default None, readonly)

Type :

SceneObjects[Object]

render

(readonly, never None)

Type :

RenderSettings

rigidbody_world

(readonly)

Type :

RigidBodyWorld

safe_areas

(readonly, never None)

Type :

DisplaySafeAreas

sequence_editor

(readonly)

Type :

SequenceEditor

sequencer_colorspace_settings

Settings for the color space the sequencer operates in (readonly)

Type :

ColorManagedSequencerColorspaceSettings

show_keys_from_selected_only

Limit channels to those tied to the selected objects and data (default True)

Type :

bool

show_subframe

Show, and allow editing of, fractional frame values for the current frame (default False)

Type :

bool

simulation_frame_end

Frame on which simulations end (in [-inf, inf], default 250)

Type :

int

simulation_frame_start

Frame on which simulations start (in [-inf, inf], default 1)

Type :

int

sync_mode

How playback stays in sync (default '`AUDIO_SYNC`' )

- NONE
Play Every Frame – Skip syncing and play every frame.

- `FRAME_DROP`
Frame Dropping – Drop frames when playback falls behind.

- `AUDIO_SYNC`
Sync to Audio – Lock to audio playback, dropping frames as needed.

Type :

Literal[‘NONE’, ‘`FRAME_DROP`’, ‘`AUDIO_SYNC`’]

time_jump_delta

How many frames or seconds each jump moves forward or backward (in [0.1, inf], default 1.0)

Type :

float

time_jump_unit

Unit applied to timeline time jumps (default 'SECOND' )

- FRAME
Frame – Jump by frames.

- SECOND
Second – Jump by seconds.

Type :

Literal[‘FRAME’, ‘SECOND’]

timeline_markers

Markers shared by all timelines for the current scene (default None, readonly)

Type :

TimelineMarkers[TimelineMarker]

tool_settings

(readonly, never None)

Type :

ToolSettings

transform_orientation_slots

(default None, readonly)

Type :

bpy_prop_collection[TransformOrientationSlot]

unit_settings

Unit editing settings (readonly, never None)

Type :

UnitSettings

use_audio

Play audio from the Sequence Editor, or mute it (default False)

Type :

bool

use_audio_scrub

Play Sequence Editor audio while scrubbing (default False)

Type :

bool

use_custom_simulation_range

Apply a simulation range distinct from the scene range, for simulation nodes that don't set their own frame range (default False)

Type :

bool

use_gravity

Apply global gravity to all dynamics (default True)

Type :

bool

use_nodes

Enable the compositing node group. (default False)

Deprecated since version 5.0: removal planned in version 6.0

Kept only for compatibility and otherwise unused. Writing it does nothing, and reading it always yields True. Use #scene.render.use_compositing to switch compositing on or off.

Type :

bool

use_preview_range

Use a separate start/end frame range for animation playback and view renders (default False)

Type :

bool

use_stamp_note

User-supplied note for render stamping (default “”, never None)

Type :

str

view_layers

(default None, readonly)

Type :

ViewLayers[ViewLayer]

view_settings

Color management applied to the image prior to saving (readonly)

Type :

ColorManagedViewSettings

world

World the scene is rendered with

Type :

World

classmethod update_render_engine ( )

Kick off a render engine update

statistics ( view_layer )

statistics

Parameters :

view_layer (ViewLayer) – View Layer, (never None)

Returns :

Statistics, (never None)

Return type :

str

frame_set ( frame , * , subframe = 0.0 )

Set the scene frame, immediately refreshing every object and view layer

Parameters :

- frame ( int ) – Frame number to set (in [-1048574, 1048574])

- subframe ( float ) – Subframe time, between 0.0 and 1.0 (in [0, 1], optional)

uvedit_aspect ( object )

Fetch the uv aspect for the current object

Parameters :

object (Object) – Object (never None)

Returns :

aspect (array of 2 items, in [0, inf])

Return type :

mathutils.Vector

ray_cast ( depsgraph , origin , direction , * , distance = 1.70141e+38 )

Fire a ray at the evaluated geometry in world space

Parameters :

- depsgraph (Depsgraph) – The current dependency graph (never None)

- origin (mathutils.Vector) – (array of 3 items, in [-inf, inf])

- direction (mathutils.Vector) – (array of 3 items, in [-inf, inf])

- distance ( float ) – Maximum distance (in [0, inf], optional)

Returns :

result , bool

location , The hit location of this ray cast, mathutils.Vector

normal , The face normal at the ray cast hit location, mathutils.Vector

index , The face index, -1 when original data isn’t available, int

object , The original (un-evaluated) object that was hit. Note that location , normal , and index correspond to the evaluated object’s mesh., Object

matrix , Matrix, mathutils.Matrix

Return type :

tuple[bool, mathutils.Vector, mathutils.Vector, int, Object, mathutils.Matrix]

sequence_editor_create ( )

Make sure this scene has a valid sequence editor

Returns :

New sequence editor data or None

Return type :

SequenceEditor

sequence_editor_clear ( )

Remove this scene's sequence editor

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| bpy.context.scene bpy.context.sequencer_scene BlendData.scenes BlendDataScenes.new BlendDataScenes.remove Camera.view_frame CompositorNodeCryptomatteV2.scene CompositorNodeDefocus.scene CompositorNodeRLayers.scene Context.scene Depsgraph.scene Depsgraph.scene_eval ID.override_hierarchy_create IDOverrideLibrary.resync Image.save_render NodeSocketScene.default_value | NodeTreeInterfaceSocketScene.default_value Object.crazyspace_eval Object.is_deform_modified Object.is_modified RenderEngine.bind_display_space_shader RenderEngine.get_preview_pixel_size RenderEngine.register_pass RenderEngine.support_display_space_shader RenderEngine.update_render_passes Scene.background_set SceneStrip.scene StripsMeta.new_scene StripsTopLevel.new_scene Window.find_playing_scene Window.scene WorkSpace.sequencer_scene |

## SceneDisplay(bpy_struct)

### SceneDisplay(bpy_struct)

base class — bpy_struct

class bpy.types. SceneDisplay ( bpy_struct )

Scene display settings for 3D viewport

light_direction

Direction the light comes from for shadows and highlights (array of 3 items, in [-inf, inf], default (0.57735, 0.57735, 0.57735))

Type :

mathutils.Vector

matcap_ssao_attenuation

Attenuation constant (in [0, 100000], default 1.0)

Type :

float

matcap_ssao_distance

How far an object can be and still feed into the cavity/edge effect (in [0, 100000], default 0.2)

Type :

float

matcap_ssao_samples

Number of samples (in [1, 500], default 16)

Type :

int

render_aa

Anti-aliasing method applied to the final rendered image (default '8' )

- OFF
No Anti-Aliasing – Render the scene with anti-aliasing turned off.

- FXAA
Single Pass Anti-Aliasing – Render the scene with a one-pass anti-aliasing method (FXAA).

- 5
5 Samples – Render the scene with 5 anti-aliasing samples.

- 8
8 Samples – Render the scene with 8 anti-aliasing samples.

- 11
11 Samples – Render the scene with 11 anti-aliasing samples.

- 16
16 Samples – Render the scene with 16 anti-aliasing samples.

- 32
32 Samples – Render the scene with 32 anti-aliasing samples.

Type :

Literal[‘OFF’, ‘FXAA’, ‘5’, ‘8’, ‘11’, ‘16’, ‘32’]

shading

Shading settings for OpenGL render engine (readonly)

Type :

View3DShading

shadow_focus

Shadow factor hardness (in [0, 1], default 0.0)

Type :

float

shadow_shift

Shadow termination angle (in [0, 1], default 0.1)

Type :

float

viewport_aa

Anti-aliasing method applied when drawing the 3D viewport (default 'FXAA' )

- OFF
No Anti-Aliasing – Render the scene with anti-aliasing turned off.

- FXAA
Single Pass Anti-Aliasing – Render the scene with a one-pass anti-aliasing method (FXAA).

- 5
5 Samples – Render the scene with 5 anti-aliasing samples.

- 8
8 Samples – Render the scene with 8 anti-aliasing samples.

- 11
11 Samples – Render the scene with 11 anti-aliasing samples.

- 16
16 Samples – Render the scene with 16 anti-aliasing samples.

- 32
32 Samples – Render the scene with 32 anti-aliasing samples.

Type :

Literal[‘OFF’, ‘FXAA’, ‘5’, ‘8’, ‘11’, ‘16’, ‘32’]

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

| Scene.display | |

## See also

- [Bpy Struct](bpy-struct.md)
