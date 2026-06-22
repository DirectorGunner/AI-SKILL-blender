# Clip Operators (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Clip Operators

bpy.ops.clip. add_marker ( * , location = (0.0, 0.0) )

Deposit a fresh marker at the specified location

Parameters :

location (mathutils.Vector) – Location, Location of marker on frame (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. add_marker_at_click ( )

Deposit a fresh marker where the user clicks

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. add_marker_move ( * , `CLIP_OT`_add_marker = {} , `TRANSFORM_OT`_translate = {} )

Insert a marker and reposition it within the footage

Parameters :

- `CLIP_OT`_add_marker ( dict [ str , Any ] ) – Add Marker, Place new marker at specified location (optional, bpy.ops.clip.add_marker() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. add_marker_slide ( * , `CLIP_OT`_add_marker = {} , `TRANSFORM_OT`_translate = {} )

Insert a marker and drag it with the mouse until release

Parameters :

- `CLIP_OT`_add_marker ( dict [ str , Any ] ) – Add Marker, Place new marker at specified location (optional, bpy.ops.clip.add_marker() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. apply_solution_scale ( * , distance = 0.0 )

Adjust scale within the solution to equate the separation between selected tracks to the target value

Parameters :

distance ( float ) – Distance, Distance between selected tracks (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. average_tracks ( * , keep_original = True )

Combine the values of selected tracks into the active track

Parameters :

keep_original ( bool ) – Keep Original, Keep original tracks (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. bundles_to_mesh ( )

Form a point cloud by extracting the positions of reconstructed track points

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/clip.py:292

bpy.ops.clip. camera_preset_add ( * , name = '' , remove_name = False , remove_active = False , use_focal_length = True )

Add or remove a Tracking Camera Intrinsics Preset

Parameters :

- name ( str ) – Name, Name of the preset, used to make the path name (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

- use_focal_length ( bool ) – Include Focal Length, Include focal length into the preset (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.clip. change_frame ( * , frame = 0 )

Manually adjust the playback position

Parameters :

frame ( int ) – Frame, (in [-1048574, 1048574], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. clean_tracks ( * , frames = 0 , error = 0.0 , action = 'SELECT' )

Purge tracks having substantial errors or insufficient coverage

Parameters :

- frames ( int ) – Tracked Frames, Affect tracks which are tracked less than the specified number of frames (in [0, inf], optional)

- error ( float ) – Reprojection Error, Affect tracks which have a larger reprojection error (in [0, inf], optional)

- action ( Literal [ 'SELECT' , '`DELETE_TRACK`' , '`DELETE_SEGMENTS`' ] ) – Action, Cleanup action to execute (optional)

- SELECT
Select – Select unclean tracks.

- `DELETE_TRACK`
Delete Track – Delete unclean tracks.

- `DELETE_SEGMENTS`
Delete Segments – Delete unclean segments of tracks.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. clear_solution ( )

Erase every solution and reconstruction

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. clear_track_path ( * , action = 'REMAINED' , clear_active = False )

Delete trajectories following or preceding the current position, or wipe the entire track

Parameters :

- action ( Literal [ 'UPTO' , 'REMAINED' , 'ALL' ] ) – Action, Clear action to execute (optional)

- UPTO
Clear Up To – Clear path up to current frame.

- REMAINED
Clear Remained – Clear path at remaining frames (after current).

- ALL
Clear All – Clear the whole path.

- clear_active ( bool ) – Clear Active, Clear active track only instead of all selected tracks (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. constraint_to_fcurve ( )

Create F-Curves for an entity that duplicates motion controlled by this constraint

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/clip.py:530

bpy.ops.clip. copy_tracks ( )

Duplicate selected tracks to the internal clipboard

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. create_plane_track ( )

Assemble a plane track from the selected point tracks

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. cursor_set ( * , location = (0.0, 0.0) )

Determine the 2D cursor placement

Parameters :

location (mathutils.Vector) – Location, Cursor location in normalized clip coordinates (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. delete_marker ( * , confirm = True )

Discard the marker linked to the current frame from selected tracks

Parameters :

confirm ( bool ) – Confirm, Prompt for confirmation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. delete_proxy ( )

Purge cached proxy files from the filesystem

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/clip.py:359

bpy.ops.clip. delete_track ( * , confirm = True )

Discard all selected tracks

Parameters :

confirm ( bool ) – Confirm, Prompt for confirmation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. detect_features ( * , placement = 'FRAME' , margin = 16 , threshold = 0.5 , min_distance = 120 )

Locate salient points and insert markers for tracking purposes

Parameters :

- placement ( Literal [ 'FRAME' , '`INSIDE_GPENCIL`' , '`OUTSIDE_GPENCIL`' ] ) – Placement, Placement for detected features (optional)

- FRAME
Whole Frame – Place markers across the whole frame.

- `INSIDE_GPENCIL`
Inside Annotated Area – Place markers only inside areas outlined with the Annotation tool.

- `OUTSIDE_GPENCIL`
Outside Annotated Area – Place markers only outside areas outlined with the Annotation tool.

- margin ( int ) – Margin, Only features further than margin pixels from the image edges are considered (in [0, inf], optional)

- threshold ( float ) – Threshold, Threshold level to consider feature good enough for tracking (in [0.0001, inf], optional)

- min_distance ( int ) – Distance, Minimal distance accepted between two features (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. disable_markers ( * , action = 'DISABLE' )

Deactivate or reactivate selected markers

Parameters :

action ( Literal [ 'DISABLE' , 'ENABLE' , 'TOGGLE' ] ) – Action, Disable action to execute (optional)

- DISABLE
Disable – Disable selected markers.

- ENABLE
Enable – Enable selected markers.

- TOGGLE
Toggle – Toggle disabled flag for selected markers.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. dopesheet_select_channel ( * , location = (0.0, 0.0) , extend = False )

Pick a movie motion tracking channel

Parameters :

- location (mathutils.Vector) – Location, Mouse location to select channel (array of 2 items, in [-inf, inf], optional)

- extend ( bool ) – Extend, Extend selection rather than clearing the existing selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. dopesheet_view_all ( )

Reset the viewable region to display the complete keyframe span

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. filter_tracks ( * , track_threshold = 5.0 )

Remove tracks that display anomalous spiking in their motion curves

Parameters :

track_threshold ( float ) – Track Threshold, Filter Threshold to select problematic tracks (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/clip.py:206

bpy.ops.clip. frame_jump ( * , position = 'PATHSTART' )

Go to a special frame location

Parameters :

position ( Literal [ 'PATHSTART' , 'PATHEND' , 'FAILEDPREV' , 'FAILNEXT' ] ) – Position, Position to jump to (optional)

- PATHSTART
Path Start – Jump to start of current path.

- PATHEND
Path End – Jump to end of current path.

- FAILEDPREV
Previous Failed – Jump to previous failed frame.

- FAILNEXT
Next Failed – Jump to next failed frame.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. graph_center_current_frame ( )

Translate the view to place the active frame in the center

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. graph_delete_curve ( * , confirm = True )

Erase the track paired with the chosen curve

Parameters :

confirm ( bool ) – Confirm, Prompt for confirmation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. graph_delete_knot ( )

Remove control points from curves

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. graph_disable_markers ( * , action = 'DISABLE' )

Toggle activation of selected markers

Parameters :

action ( Literal [ 'DISABLE' , 'ENABLE' , 'TOGGLE' ] ) – Action, Disable action to execute (optional)

- DISABLE
Disable – Disable selected markers.

- ENABLE
Enable – Enable selected markers.

- TOGGLE
Toggle – Toggle disabled flag for selected markers.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. graph_select ( * , location = (0.0, 0.0) , extend = False )

Pick graph trajectories

Parameters :

- location (mathutils.Vector) – Location, Mouse location to select nearest entity (array of 2 items, in [-inf, inf], optional)

- extend ( bool ) – Extend, Extend selection rather than clearing the existing selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. graph_select_all_markers ( * , action = 'TOGGLE' )

Modify selection state of all markers within the active track

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Selection action to execute (optional)

- TOGGLE
Toggle – Toggle selection for all elements.

- SELECT
Select – Select all elements.

- DESELECT
Deselect – Deselect all elements.

- INVERT
Invert – Invert selection of all elements.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. graph_select_box ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , deselect = False , extend = True )

Choose curve vertices via rectangular selection

Parameters :

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- deselect ( bool ) – Deselect, Deselect rather than select items (optional)

- extend ( bool ) – Extend, Extend selection instead of deselecting everything first (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. graph_view_all ( )

Display every trajectory in the view

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. hide_tracks ( * , unselected = False )

Conceal selected tracks

Parameters :

unselected ( bool ) – Unselected, Hide unselected tracks (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. hide_tracks_clear ( )

Unhide all concealed tracks

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. join_tracks ( )

Consolidate selected tracks into a single entity

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. keyframe_delete ( )

Discard a keyframe from selected tracks at the current position

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. keyframe_insert ( )

Append a keyframe to selected tracks at the current position

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. lock_selection_toggle ( )

Toggle the Lock Selection mode in the clip editor

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. lock_tracks ( * , action = 'LOCK' )

Safeguard or unsafeguard selected tracks

Parameters :

action ( Literal [ 'LOCK' , 'UNLOCK' , 'TOGGLE' ] ) – Action, Lock action to execute (optional)

- LOCK
Lock – Lock selected tracks.

- UNLOCK
Unlock – Unlock selected tracks.

- TOGGLE
Toggle – Toggle locked flag for selected tracks.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. mode_set ( * , mode = 'TRACKING' )

Establish the clip editor's interaction mode

Parameters :

mode (Literal[Clip Editor Mode Items]) – Mode, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. new_image_from_plane_marker ( )

Produce a new image from the plane marker's visual content

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. open ( * , directory = '' , files = None , hide_props_region = True , check_existing = False , filter_blender = False , filter_backup = False , filter_image = True , filter_movie = True , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 9 , relative_path = True , show_multiview = False , use_multiview = False , display_type = 'DEFAULT' , sort_method = '' )

Import a sequence or video file

Parameters :

- directory ( str ) – Directory, Directory of the file (optional, never None)

- files ( bpy_prop_collection [ OperatorFileListElement ]) – Files, (optional)

- hide_props_region ( bool ) – Hide Operator Properties, Collapse the region displaying the operator settings (optional)

- check_existing ( bool ) – Check Existing, Check and warn on overwriting existing files (optional)

- filter_blender ( bool ) – Filter .blend files, (optional)

- filter_backup ( bool ) – Filter backup .blend files, (optional)

- filter_image ( bool ) – Filter image files, (optional)

- filter_movie ( bool ) – Filter movie files, (optional)

- filter_python ( bool ) – Filter Python files, (optional)

- filter_font ( bool ) – Filter font files, (optional)

- filter_sound ( bool ) – Filter sound files, (optional)

- filter_text ( bool ) – Filter text files, (optional)

- filter_archive ( bool ) – Filter archive files, (optional)

- filter_btx ( bool ) – Filter btx files, (optional)

- filter_alembic ( bool ) – Filter Alembic files, (optional)

- filter_usd ( bool ) – Filter USD files, (optional)

- filter_obj ( bool ) – Filter OBJ files, (optional)

- filter_volume ( bool ) – Filter OpenVDB volume files, (optional)

- filter_folder ( bool ) – Filter folders, (optional)

- filter_blenlib ( bool ) – Filter Blender IDs, (optional)

- filemode ( int ) – File Browser Mode, The setting for the file browser mode to load a .blend file, a library or a special file (in [1, 9], optional)

- relative_path ( bool ) – Relative Path, Select the file relative to the blend file (optional)

- show_multiview ( bool ) – Enable Multi-View, (optional)

- use_multiview ( bool ) – Use Multi-View, (optional)

- display_type ( Literal [ 'DEFAULT' , '`LIST_VERTICAL`' , '`LIST_HORIZONTAL`' , 'THUMBNAIL' ] ) – Display Type, (optional)

- DEFAULT
Default – Automatically determine display type for files.

- `LIST_VERTICAL`
Short List – Display files as short list.

- `LIST_HORIZONTAL`
Long List – Display files as a detailed list.

- THUMBNAIL
Thumbnails – Display files as thumbnails.

- sort_method ( Literal [ 'DEFAULT' , '`FILE_SORT_ALPHA`' , '`FILE_SORT_EXTENSION`' , '`FILE_SORT_TIME`' , '`FILE_SORT_SIZE`' , '`ASSET_CATALOG`' ] ) – File sorting mode, (optional)

- DEFAULT
Default – Automatically determine sort method for files.

- `FILE_SORT_ALPHA`
Name – Sort the file list alphabetically.

- `FILE_SORT_EXTENSION`
Extension – Sort the file list by extension/type.

- `FILE_SORT_TIME`
Modified Date – Sort files by modification time.

- `FILE_SORT_SIZE`
Size – Sort files by size.

- `ASSET_CATALOG`
Asset Catalog – Sort the asset list so that assets in the same catalog are kept together. Within a single catalog, assets are ordered by name. The catalogs are in order of the flattened catalog hierarchy..

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. paste_tracks ( )

Reinsert tracks stored in the internal clipboard

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. prefetch ( )

Load frames into memory for smoother performance during playback and tracking

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. rebuild_proxy ( )

Regenerate all chosen proxies and timecode indices in the background

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. refine_markers ( * , backwards = False )

Enhance the accuracy of selected markers by running the tracker between the track's origin and the current point

Parameters :

backwards ( bool ) – Backwards, Do backwards tracking (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. reload ( )

Reimport the clip

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. select ( * , extend = False , deselect_all = False , location = (0.0, 0.0) )
