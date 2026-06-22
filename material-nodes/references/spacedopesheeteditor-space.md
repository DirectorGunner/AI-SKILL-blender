# Spacedopesheeteditor Space, Spacefilebrowser Space, Spacegrapheditor Space, Spaceimageeditor Space

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: SpaceDopeSheetEditor(Space); SpaceFileBrowser(Space); SpaceGraphEditor(Space); SpaceImageEditor(Space).

## SpaceDopeSheetEditor(Space)

### SpaceDopeSheetEditor(Space)

base classes — bpy_struct, Space

class bpy.types. SpaceDopeSheetEditor ( Space )

The space data for the Dope Sheet

cache_cloth

Draw the cloth point cache of the active object (default False)

Type :

bool

cache_dynamicpaint

Draw the Dynamic Paint cache of the active object (default False)

Type :

bool

cache_particles

Draw the particle point cache of the active object (default False)

Type :

bool

cache_rigidbody

Draw the Rigid Body cache of the active object (default False)

Type :

bool

cache_simulation_nodes

Draw the active object's simulation nodes cache plus its bake data (default False)

Type :

bool

cache_smoke

Draw the smoke cache of the active object (default False)

Type :

bool

cache_softbody

Draw the softbody point cache of the active object (default False)

Type :

bool

dopesheet

Options that filter the animation data (readonly)

Type :

DopeSheet

mode

Which editing context is on screen (default 'ACTION' )

- DOPESHEET
Dope Sheet – Edit all keyframes in scene.

- ACTION
Action Editor – Edit keyframes in active object’s Object-level action.

- SHAPEKEY
Shape Key Editor – Edit keyframes in active object’s Shape Keys action.

- GPENCIL
Grease Pencil – Edit timings for all Grease Pencil sketches in file.

- MASK
Mask – Edit timings for Mask Editor splines.

- CACHEFILE
Cache File – Edit timings for Cache File data-blocks.

- TIMELINE
Timeline – Simple timeline view with playback controls in the header, without channel list, side-panel, or footer.

Type :

Literal[‘DOPESHEET’, ‘ACTION’, ‘SHAPEKEY’, ‘GPENCIL’, ‘MASK’, ‘CACHEFILE’, ‘TIMELINE’]

overlays

Options for drawing the overlays (readonly, never None)

Type :

SpaceDopeSheetOverlay

show_cache

Draw the status of cached frames along the timeline (default False)

Type :

bool

show_extremes

Highlight keyframes where the value flow reverses, judged against neighboring keys (default False)

Type :

bool

show_interpolation

Draw keyframe handle types together with non-Bézier interpolation modes (default False)

Type :

bool

show_markers

If any are defined, give markers a dedicated strip along the editor's lower edge (default False)

Type :

bool

show_pose_markers

Draw the active action's markers in place of the Scene markers (Action and Shape Key Editors only) (default False)

Type :

bool

show_region_channels

(default False)

Type :

bool

show_region_footer

(default False)

Type :

bool

show_region_hud

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

show_sliders

Draw sliders next to the F-Curve channels (default False)

Type :

bool

ui_mode

Which editing context is on screen (default 'ACTION' )

- DOPESHEET
Dope Sheet – Edit all keyframes in scene.

- ACTION
Action Editor – Edit keyframes in active object’s Object-level action.

- SHAPEKEY
Shape Key Editor – Edit keyframes in active object’s Shape Keys action.

- GPENCIL
Grease Pencil – Edit timings for all Grease Pencil sketches in file.

- MASK
Mask – Edit timings for Mask Editor splines.

- CACHEFILE
Cache File – Edit timings for Cache File data-blocks.

Type :

Literal[‘DOPESHEET’, ‘ACTION’, ‘SHAPEKEY’, ‘GPENCIL’, ‘MASK’, ‘CACHEFILE’]

use_auto_merge_keyframes

Merge neighboring keyframes on their own (default True)

Type :

bool

use_marker_sync

Keep markers in sync as keyframes are edited (default False)

Type :

bool

use_realtime_update

While keyframes are being transformed, push the animation-data changes through to other views (default True)

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

## SpaceFileBrowser(Space)

### SpaceFileBrowser(Space)

base classes — bpy_struct, Space

class bpy.types. SpaceFileBrowser ( Space )

The space data for the file browser

active_operator

(readonly)

Type :

Operator

bookmarks

The user's bookmarks (default None)

Type :

bpy_prop_collection[FileBrowserFSMenuEntry]

bookmarks_active

Which bookmark is active (-1 when there is none) (in [-32768, 32767], default 0)

Type :

int

browse_mode

Which File Editor view is in use (ordinary file browsing or asset browsing) (default 'FILES' )

Type :

Literal[Space File Browse Mode Items]

operator

(readonly)

Type :

Operator

params

The parameters and settings driving the file browser (readonly)

Type :

FileSelectParams

recent_folders

(default None)

Type :

bpy_prop_collection[FileBrowserFSMenuEntry]

recent_folders_active

Which recent folder is active (-1 when there is none) (in [-32768, 32767], default 0)

Type :

int

show_region_tool_props

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

system_bookmarks

The system's bookmarks (default None, readonly)

Type :

bpy_prop_collection[FileBrowserFSMenuEntry]

system_bookmarks_active

Which system bookmark is active (-1 when there is none) (in [-32768, 32767], default 0)

Type :

int

system_folders

The system's folders (typically root, mounted drives, and so on) (default None, readonly)

Type :

bpy_prop_collection[FileBrowserFSMenuEntry]

system_folders_active

Which system folder is active (-1 when there is none) (in [-32768, 32767], default 0)

Type :

int

activate_asset_by_id ( id_to_activate , * , deferred = False )

Make active and select the asset entry standing for the given ID

Parameters :

- id_to_activate (ID) – id_to_activate

- deferred ( bool ) – Whether the ID becomes active right away (false) or once the file browser has refreshed (true) (optional)

activate_file_by_relative_path ( * , relative_path = '' )

Make a file active and add it to the selection, keyed by its path relative to the current File Browser directory

Parameters :

relative_path ( str ) – relative_path, (optional, never None)

deselect_all ( )

Clear the selection of all files

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

## SpaceGraphEditor(Space)

### SpaceGraphEditor(Space)

base classes — bpy_struct, Space

class bpy.types. SpaceGraphEditor ( Space )

The space data for the Graph Editor

cursor_position_x

X-value component of the Graph Editor 2D-Value cursor (in [-inf, inf], default 0.0)

Type :

float

cursor_position_y

Y-value component of the Graph Editor 2D-Value cursor (in [-inf, inf], default 0.0)

Type :

float

dopesheet

Options that filter the animation data (readonly)

Type :

DopeSheet

has_ghost_curves

Whether this Graph Editor instance is holding any ghost curves (default False, readonly)

Type :

bool

mode

Which editing context is on screen (default 'FCURVES' )

Type :

Literal[Space Graph Mode Items]

pivot_point

The center used when rotating or scaling (default '`BOUNDING_BOX_CENTER`' )

Type :

Literal[‘`BOUNDING_BOX_CENTER`’, ‘CURSOR’, ‘`INDIVIDUAL_ORIGINS`’]

show_cursor

Draw the 2D cursor (default True)

Type :

bool

show_extrapolation

(default True)

Type :

bool

show_handles

Draw the handles of Bézier control points (default True)

Type :

bool

show_markers

If any are defined, give markers a dedicated strip along the editor's lower edge (default False)

Type :

bool

show_region_channels

(default False)

Type :

bool

show_region_footer

(default False)

Type :

bool

show_region_hud

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

show_sliders

Draw sliders next to the F-Curve channels (default False)

Type :

bool

use_auto_lock_translation_axis

Lock keyframe movement to the dominant axis automatically (default False)

Type :

bool

use_auto_merge_keyframes

Merge neighboring keyframes on their own (default True)

Type :

bool

use_auto_normalization

Recompute curve normalization automatically after each curve edit (default True)

Type :

bool

use_normalization

Show curves rescaled to a -1 to 1 range, making it easier to edit several curves with differing ranges together (default False)

Type :

bool

use_only_selected_keyframe_handles

Draw and edit handles only for the selected keyframes (default False)

Type :

bool

use_realtime_update

While keyframes are being transformed, push the animation-data changes through to other views (default True)

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

## SpaceImageEditor(Space)

### SpaceImageEditor(Space)

base classes — bpy_struct, Space

class bpy.types. SpaceImageEditor ( Space )

The space data for the image and UV editor

annotation

The annotation data attached to this space

Type :

Annotation

blend_factor

How strongly the rasterized mask overlay is blended in (in [0, 1], default 0.7)

Type :

float

cursor_location

Where the 2D cursor sits in this view (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

display_channels

Which channels of the image are shown (default 'COLOR' )

- `COLOR_ALPHA`
Color & Alpha – Display image with RGB colors and alpha transparency.

- COLOR
Color – Display image with RGB colors.

- ALPHA
Alpha – Display alpha transparency channel.

- `Z_BUFFER`
Z-Buffer – Display Z-buffer associated with image (mapped from camera clip start to end).

- RED
Red.

- GREEN
Green.

- BLUE
Blue.

Type :

Literal[‘`COLOR_ALPHA`’, ‘COLOR’, ‘ALPHA’, ‘`Z_BUFFER`’, ‘RED’, ‘GREEN’, ‘BLUE’]

image

The image shown and edited within this space

Type :

Image

image_user

Settings that pick which layer, pass, and frame of the image appear (readonly, never None)

Type :

ImageUser

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

Which editing context is on screen (default 'VIEW' )

Type :

Literal[Space Image Mode All Items]

overlay

Configuration for the overlays drawn in the UV/Image editor (readonly, never None)

Type :

SpaceImageOverlay

pivot_point

The pivot used for rotation and scaling (default '`BOUNDING_BOX_CENTER`' )

- `BOUNDING_BOX_CENTER`
Bounding Box Center – Pivot around bounding box center of selected object(s).

- CURSOR
3D Cursor – Pivot around the 3D cursor.

- `INDIVIDUAL_ORIGINS`
Individual Origins – Pivot around each object’s own origin.

- `MEDIAN_POINT`
Median Point – Pivot around the median point of selected objects.

- `ACTIVE_ELEMENT`
Active Element – Pivot around active object.

Type :

Literal[‘`BOUNDING_BOX_CENTER`’, ‘CURSOR’, ‘`INDIVIDUAL_ORIGINS`’, ‘`MEDIAN_POINT`’, ‘`ACTIVE_ELEMENT`’]

sample_histogram

Colors sampled along a line (readonly)

Type :

Histogram

scopes

Scopes used to visualize image statistics (readonly)

Type :

Scopes

show_annotation

Draw annotations in this view (default False)

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

show_mask_overlay

(default False)

Type :

bool

show_mask_spline

(default True)

Type :

bool

show_maskedit

Expose properties tied to mask editing (default False, readonly)

Type :

bool

show_paint

Expose properties tied to painting (default False, readonly)

Type :

bool

show_region_asset_shelf

Draw a region holding assets that might be relevant right now (brushes in paint modes, poses in Pose Mode, and the like) (default False)

Type :

bool

show_region_hud

(default False)

Type :

bool

show_region_tool_header

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

show_render

Expose properties tied to rendering (default False, readonly)

Type :

bool

show_repeat

Tile the image so it repeats beyond the edges of the main view (default False)

Type :

bool

show_sequencer_scene

Draw the render result of the sequencer scene rather than the active scene (default False)

Type :

bool

show_stereo_3d

Draw the image in Stereo 3D (default False)

Type :

bool

show_uvedit

Expose properties tied to UV editing (default False, readonly)

Type :

bool

ui_mode

Which editing context is on screen (default 'VIEW' )

- VIEW
View – Inspect images or render results.

- PAINT
Paint – Paint images in 2D.

- MASK
Mask – View and edit masks.

Type :

Literal[‘VIEW’, ‘PAINT’, ‘MASK’]

use_image_pin

Keep the current image on screen no matter which object is selected (default False)

Type :

bool

use_realtime_update

Refresh other affected window spaces on the fly so they mirror changes made during interactive actions like transform (default False)

Type :

bool

uv_editor

The UV editor settings (readonly, never None)

Type :

SpaceUVEditor

zoom

Zoom factor (array of 2 items, in [-inf, inf], default (0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

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
