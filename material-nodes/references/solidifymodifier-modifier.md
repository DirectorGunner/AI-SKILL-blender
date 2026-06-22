# Solidifymodifier Modifier, Sound Id, Space Bpy Struct, Spaceclipeditor Space ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: SolidifyModifier(Modifier); Sound(ID); Space(bpy_struct); SpaceClipEditor(Space); SpaceConsole(Space).

## SolidifyModifier(Modifier)

### SolidifyModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. SolidifyModifier ( Modifier )

Gives a mesh a solid skin while correcting for sharp angles

bevel_convex

Weight of the bevel applied to outward-facing edges (in [-1, 1], default 0.0)

Type :

float

edge_crease_inner

Crease value given to the inner edges (in [0, 1], default 0.0)

Type :

float

edge_crease_outer

Crease value given to the outer edges (in [0, 1], default 0.0)

Type :

float

edge_crease_rim

Crease value applied along the edges that form the rim (in [0, 1], default 0.0)

Type :

float

invert_vertex_group

Flip how the vertex group affects the result (default False)

Type :

bool

material_offset

Shifts the material index used by the faces that get created (in [-32768, 32767], default 0)

Type :

int

material_offset_rim

Shifts the material index used by the newly created rim faces (in [-32768, 32767], default 0)

Type :

int

nonmanifold_boundary_mode

Picks which algorithm handles boundary adjustment (default 'NONE' )

- NONE
None – No shape correction.

- ROUND
Round – Round open perimeter shape.

- FLAT
Flat – Flat open perimeter shape.

Type :

Literal[‘NONE’, ‘ROUND’, ‘FLAT’]

nonmanifold_merge_threshold

Below this distance, degenerate geometry gets merged together (in [0, 1], default 0.0001)

Type :

float

nonmanifold_thickness_mode

Picks which algorithm computes thickness (default 'CONSTRAINTS' )

- FIXED
Fixed – Most basic thickness calculation.

- EVEN
Even – Even thickness calculation which takes the angle between faces into account.

- CONSTRAINTS
Constraints – Thickness calculation using constraints, most advanced.

Type :

Literal[‘FIXED’, ‘EVEN’, ‘CONSTRAINTS’]

offset

Shifts where the thickness sits relative to the center (in [-inf, inf], default -1.0)

Type :

float

rim_vertex_group

Vertex group the generated rim geometry gets weighted toward (default “”, never None)

Type :

str

shell_vertex_group

Vertex group the generated shell geometry gets weighted toward (default “”, never None)

Type :

str

solidify_mode

Picks which algorithm is used (default 'EXTRUDE' )

- EXTRUDE
Simple – Output a solidified version of a mesh by simple extrusion.

- `NON_MANIFOLD`
Complex – Output a manifold mesh even if the base mesh is non-manifold, where edges have 3 or more connecting faces. This method is slower..

Type :

Literal[‘EXTRUDE’, ‘`NON_MANIFOLD`’]

thickness

How thick the resulting shell is (in [-inf, inf], default 0.01)

Type :

float

thickness_clamp

Limits the offset relative to the scale of the geometry (in [0, 100], default 0.0)

Type :

float

thickness_vertex_group

Thickness factor applied where the vertex group has no influence (in [0, 1], default 0.0)

Type :

float

use_even_offset

Keep thickness consistent by compensating at sharp corners (slow, turn off when unused) (default False)

Type :

bool

use_flat_faces

Have faces take on the smallest vertex weight from their vertices (keeps new faces parallel to the originals, slow, turn off when unused) (default False)

Type :

bool

use_flip_normals

Reverse the direction the faces point (default False)

Type :

bool

use_quality_normals

Compute normals that give more uniform thickness (slow, turn off when unused) (default False)

Type :

bool

use_rim

Build edge loops connecting the inner and outer surfaces along face edges (slow, turn off when unused) (default True)

Type :

bool

use_rim_only

Attach the rim to the original data only (default False)

Type :

bool

use_thickness_angle_clamp

Restrict thickness according to angles (default False)

Type :

bool

vertex_group

Name of the vertex group (default “”, never None)

Type :

str

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## Sound(ID)

### Sound(ID)

base classes — bpy_struct, ID

class bpy.types. Sound ( ID )

A data-block that points at an external or packed sound file

channels

How the audio channels are laid out (default 'INVALID' , readonly)

- INVALID
Invalid – Invalid.

- MONO
Mono – Mono.

- STEREO
Stereo – Stereo.

- `STEREO_LFE`
Stereo LFE – Stereo FX.

- `CHANNELS_4`
4 Channels – 4 Channels.

- `CHANNELS_5`
5 Channels – 5 Channels.

- `SURROUND_51`
5.1 Surround – 5.1 Surround.

- `SURROUND_61`
6.1 Surround – 6.1 Surround.

- `SURROUND_71`
7.1 Surround – 7.1 Surround.

Type :

Literal[‘INVALID’, ‘MONO’, ‘STEREO’, ‘`STEREO_LFE`’, ‘`CHANNELS_4`’, ‘`CHANNELS_5`’, ‘`SURROUND_51`’, ‘`SURROUND_61`’, ‘`SURROUND_71`’]

filepath

The audio sample file backing this Sound data-block (default “”, never None, blend relative // prefix supported)

Type :

str

packed_file

(readonly)

Type :

PackedFile

samplerate

Audio sample rate, given in Hz (in [-inf, inf], default 0, readonly)

Type :

int

use_memory_cache

Decode the sound file and hold it in RAM (default False)

Type :

bool

use_mono

When several audio channels are present, mix them down to one (default False)

Type :

bool

factory

This sound's aud.Factory object.

(readonly)

pack ( )

Embed the sound into the open blend file

unpack ( * , method = '`USE_LOCAL`' )

Extract the sound back out to the samples filename

Parameters :

method (Literal[Unpack Method Items]) – method, How to unpack (optional)

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| BlendData.sounds BlendDataSounds.load BlendDataSounds.remove NodeSocketSound.default_value | NodeTreeInterfaceSocketSound.default_value SoundStrip.sound Speaker.sound |

## Space(bpy_struct)

### Space(bpy_struct)

base class — bpy_struct

subclasses —
SpaceClipEditor, SpaceConsole, SpaceDopeSheetEditor, SpaceFileBrowser, SpaceGraphEditor, SpaceImageEditor, SpaceInfo, SpaceNLA, SpaceNodeEditor, SpaceOutliner, SpacePreferences, SpaceProperties, SpaceSequenceEditor, SpaceSpreadsheet, SpaceTextEditor, SpaceView3D

class bpy.types. Space ( bpy_struct )

The space data attached to a screen area

show_locked_time

Keep the visible timeline range in sync with other time-based editors (default False)

Type :

bool

show_region_header

(default False)

Type :

bool

type

Which space data type this is (default 'EMPTY' , readonly)

Type :

Literal[Space Type Items]

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

- default (type | None ) – Value returned if nothing matches.

Returns :

The matching class, or the default if none is found.

Return type :

type

classmethod draw_handler_add ( callback , args , region_type , draw_type )

Register a fresh draw handler on this kind of space.
Whenever the named region of that space type is redrawn, the handler runs.
Note: for the moment, every argument here is positional-only.

Parameters :

- callback ( Callable [ ... , Any ] ) – A function invoked at region draw time.
It is handed the arguments listed below, and any value it hands back gets thrown away.

- args ( tuple [ Any , ... ] ) – Arguments handed to the callback.

- region_type ( str ) – The region type the callback draws in; usually WINDOW . (bpy.types.Region.type)

- draw_type ( str ) – Usually `POST_PIXEL` for 2D drawing and `POST_VIEW` for 3D drawing. In some cases `PRE_VIEW` can be used. BACKDROP can be used for backdrops in the node editor.

Returns :

A handler reference you can remove afterward.

Return type :

object

classmethod draw_handler_remove ( handler , region_type )

Detach a draw handler that had been registered earlier.

Parameters :

- handler ( object ) – The draw handler to take off.

- region_type ( str ) – The region type that handler was attached to.

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Area.spaces AreaSpaces.active | Context.space_data |

## SpaceClipEditor(Space)

### SpaceClipEditor(Space)

base classes — bpy_struct, Space

class bpy.types. SpaceClipEditor ( Space )

The space data for the clip editor

annotation_source

Which source the annotation is drawn from (default 'CLIP' )

- CLIP
Clip – Show annotation data-block which belongs to movie clip.

- TRACK
Track – Show annotation data-block which belongs to active track.

Type :

Literal[‘CLIP’, ‘TRACK’]

blend_factor

How strongly the rasterized mask overlay is blended in (in [0, 1], default 0.7)

Type :

float

clip

The movie clip shown and edited within this space

Type :

MovieClip

clip_user

Settings that pick which frame of the movie clip appears (readonly, never None)

Type :

MovieClipUser

cursor_location

Where the 2D cursor sits in this view (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

lock_selection

Pin the viewport to the selected markers while playing back (default False)

Type :

bool

lock_time_cursor

Pin the curves view to the time cursor while playing back and tracking (default False)

Type :

bool

mask

The mask shown and edited within this space

Type :

Mask

mask_display_type

How mask splines are drawn (default 'OUTLINE' )

- OUTLINE
Outline – Display white edges with black outline.

- DASH
Dash – Display dashed black-white edges.

- BLACK
Black – Display black edges.

- WHITE
White – Display white edges.

Type :

Literal[‘OUTLINE’, ‘DASH’, ‘BLACK’, ‘WHITE’]

mask_overlay_mode

Which overlay mode the rasterized mask uses (default 'ALPHACHANNEL' )

- ALPHACHANNEL
Alpha Channel – Show alpha channel of the mask.

- COMBINED
Combined – Combine space background image with the mask.

Type :

Literal[‘ALPHACHANNEL’, ‘COMBINED’]

mode

Which editing context is on screen (default 'TRACKING' )

Type :

Literal[Clip Editor Mode Items]

overlay

Configuration for the overlays drawn in the Movie Clip editor (readonly, never None)

Type :

SpaceClipOverlay

path_length

How many frames of the path get drawn (in [0, inf], default 20)

Type :

int

pivot_point

The center used when rotating or scaling (default '`MEDIAN_POINT`' )

- `BOUNDING_BOX_CENTER`
Bounding Box Center – Pivot around bounding box center of selected object(s).

- CURSOR
2D Cursor – Pivot around the 2D cursor.

- `INDIVIDUAL_ORIGINS`
Individual Origins – Pivot around each object’s own origin.

- `MEDIAN_POINT`
Median Point – Pivot around the median point of selected objects.

Type :

Literal[‘`BOUNDING_BOX_CENTER`’, ‘CURSOR’, ‘`INDIVIDUAL_ORIGINS`’, ‘`MEDIAN_POINT`’]

scopes

Scopes used to visualize statistics about the movie clip (readonly)

Type :

MovieClipScopes

show_annotation

Draw annotations in this view (default True)

Type :

bool

show_blue_channel

Draw the blue channel of the frame (default True)

Type :

bool

show_bundles

Draw where 3D markers project onto the footage (default False)

Type :

bool

show_disabled

Draw the footage's disabled tracks too (default True)

Type :

bool

show_filters

Draw the graph editor's filters (default False)

Type :

bool

show_gizmo

Draw gizmos of every type (default True)

Type :

bool

show_gizmo_navigate

Viewport navigation gizmo (default True)

Type :

bool

show_graph_frames

Draw the per-frame average error curve (solve the camera motion first) (default True)

Type :

bool

show_graph_hidden

Take in channels from objects or bones that aren't visible (default False)

Type :

bool

show_graph_only_selected

Limit channels to those tied to the selected objects and data (default False)

Type :

bool

show_graph_tracks_error

Draw the reprojection error curve for the selected tracks (default False)

Type :

bool

show_graph_tracks_motion

Draw the speed curves for the selected tracks (default True)

Type :

bool

show_green_channel

Draw the green channel of the frame (default True)

Type :

bool

show_grid

Draw a grid that reveals lens distortion (default False)

Type :

bool

show_marker_pattern

Draw the pattern boundbox of the markers (default True)

Type :

bool

show_marker_search

Draw the search boundbox of the markers (default False)

Type :

bool

show_mask_overlay

(default False)

Type :

bool

show_mask_spline

(default True)

Type :

bool

show_metadata

Draw the clip's metadata (default False)

Type :

bool

show_names

Draw track names along with their status (default False)

Type :

bool

show_red_channel

Draw the red channel of the frame (default True)

Type :

bool

show_region_channels

(default False)

Type :

bool

show_region_hud

(default False)

Type :

bool

show_region_toolbar

(default False)

Type :

bool

show_region_ui

(default False)

Type :

bool

show_seconds

Label timing with timecode rather than frame numbers (default False)

Type :

bool

show_stable

Draw stabilized footage in the editor (when stabilization is on) (default False)

Type :

bool

show_tiny_markers

Draw markers in a more compact form (default False)

Type :

bool

show_track_path

Draw the path along which a track moves (default True)

Type :

bool

use_grayscale_preview

Render the frame in grayscale (default False)

Type :

bool

use_manual_calibration

Turn on the manual calibration helpers (default False)

Type :

bool

use_mute_footage

Silence the footage and put up a black background in its place (default False)

Type :

bool

view

Which clip editor view is active (default 'CLIP' )

- CLIP
Clip – Show editing clip preview.

- GRAPH
Graph – Show graph view for active element.

- DOPESHEET
Dope Sheet – Dope Sheet view for tracking data.

Type :

Literal[‘CLIP’, ‘GRAPH’, ‘DOPESHEET’]

zoom_percentage

Zoom percentage (in [0.4, 80000], default 100.0)

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

classmethod draw_handler_add ( callback , args , region_type , draw_type )

Register a fresh draw handler on this kind of space.
Whenever the named region of that space type is redrawn, the handler runs.
Note: for the moment, every argument here is positional-only.

Parameters :

- callback ( Callable [ ... , Any ] ) – A function invoked at region draw time.
It is handed the arguments listed below, and any value it hands back gets thrown away.

- args ( tuple [ Any , ... ] ) – Arguments handed to the callback.

- region_type ( str ) – The region type the callback draws in; usually WINDOW . (bpy.types.Region.type)

- draw_type ( str ) – Usually `POST_PIXEL` for 2D drawing and `POST_VIEW` for 3D drawing. In some cases `PRE_VIEW` can be used. BACKDROP can be used for backdrops in the node editor.

Returns :

A handler reference you can remove afterward.

Return type :

object

classmethod draw_handler_remove ( handler , region_type )

Detach a draw handler that had been registered earlier.

Parameters :

- handler ( object ) – The draw handler to take off.

- region_type ( str ) – The region type that handler was attached to.

### Inherited Properties

| bpy_struct.id_data Space.type | Space.show_locked_time Space.show_region_header |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Space.bl_rna_get_subclass Space.bl_rna_get_subclass_py Space.draw_handler_add Space.draw_handler_remove |

## SpaceConsole(Space)

### SpaceConsole(Space)

base classes — bpy_struct, Space

class bpy.types. SpaceConsole ( Space )

The interactive Python console

font_size

Size of the font used to render the text (in [1, 256], default 0)

Type :

int

history

The history of commands (default None, readonly)

Type :

bpy_prop_collection[ConsoleLine]

language

Language used by the command line prompt (default “”, never None)

Type :

str

prompt

The command line prompt (default “”, never None)

Type :

str

scrollback

Output produced by commands (default None, readonly)

Type :

bpy_prop_collection[ConsoleLine]

select_end

(in [0, inf], default 0)

Type :

int

select_start

(in [0, inf], default 0)

Type :

int

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

classmethod draw_handler_add ( callback , args , region_type , draw_type )

Register a fresh draw handler on this kind of space.
Whenever the named region of that space type is redrawn, the handler runs.
Note: for the moment, every argument here is positional-only.

Parameters :

- callback ( Callable [ ... , Any ] ) – A function invoked at region draw time.
It is handed the arguments listed below, and any value it hands back gets thrown away.

- args ( tuple [ Any , ... ] ) – Arguments handed to the callback.

- region_type ( str ) – The region type the callback draws in; usually WINDOW . (bpy.types.Region.type)

- draw_type ( str ) – Usually `POST_PIXEL` for 2D drawing and `POST_VIEW` for 3D drawing. In some cases `PRE_VIEW` can be used. BACKDROP can be used for backdrops in the node editor.

Returns :

A handler reference you can remove afterward.

Return type :

object

classmethod draw_handler_remove ( handler , region_type )

Detach a draw handler that had been registered earlier.

Parameters :

- handler ( object ) – The draw handler to take off.

- region_type ( str ) – The region type that handler was attached to.

### Inherited Properties

| bpy_struct.id_data Space.type | Space.show_locked_time Space.show_region_header |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Space.bl_rna_get_subclass Space.bl_rna_get_subclass_py Space.draw_handler_add Space.draw_handler_remove |

## See also

- [Bpy Struct](bpy-struct.md)
