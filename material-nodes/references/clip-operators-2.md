# Clip Operators (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Pick motion tracking markers

Parameters :

- extend ( bool ) – Extend, Extend selection rather than clearing the existing selection (optional)

- deselect_all ( bool ) – Deselect On Nothing, Deselect all when nothing under the cursor (optional)

- location (mathutils.Vector) – Location, Mouse location in normalized coordinates, 0.0 to 1.0 is within the image bounds (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. select_all ( * , action = 'TOGGLE' )

Alter the selection state of all motion tracking markers

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

bpy.ops.clip. select_box ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , mode = 'SET' )

Choose markers via rectangular boundary

Parameters :

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Set a new selection.

- ADD
Extend – Extend existing selection.

- SUB
Subtract – Subtract existing selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. select_circle ( * , x = 0 , y = 0 , radius = 25 , wait_for_input = True , mode = 'SET' )

Pick markers via circular selection

Parameters :

- x ( int ) – X, (in [-inf, inf], optional)

- y ( int ) – Y, (in [-inf, inf], optional)

- radius ( int ) – Radius, (in [1, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Set a new selection.

- ADD
Extend – Extend existing selection.

- SUB
Subtract – Subtract existing selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. select_grouped ( * , group = 'ESTIMATED' )

Pick every track in the designated category

Parameters :

group ( Literal [ 'KEYFRAMED' , 'ESTIMATED' , 'TRACKED' , 'LOCKED' , 'DISABLED' , 'COLOR' , 'FAILED' ] ) – Group, Select tracks by group (optional)

- KEYFRAMED
Keyframed Tracks – Select all keyframed tracks.

- ESTIMATED
Estimated Tracks – Select all estimated tracks.

- TRACKED
Tracked Tracks – Select all tracked tracks.

- LOCKED
Locked Tracks – Select all locked tracks.

- DISABLED
Disabled Tracks – Select all disabled tracks.

- COLOR
Tracks with Same Color – Select all tracks with same color as active track.

- FAILED
Failed Tracks – Select all tracks which failed to be reconstructed.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. select_lasso ( * , path = None , use_smooth_stroke = False , smooth_stroke_factor = 0.75 , smooth_stroke_radius = 35 , mode = 'SET' )

Pick markers via freehand encirclement

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- use_smooth_stroke ( bool ) – Stabilize Stroke, Selection lags behind mouse and follows a smoother path (optional)

- smooth_stroke_factor ( float ) – Smooth Stroke Factor, Higher values give a smoother stroke (in [0.5, 0.99], optional)

- smooth_stroke_radius ( int ) – Smooth Stroke Radius, Minimum distance from last point before selection continues (in [10, 200], optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Set a new selection.

- ADD
Extend – Extend existing selection.

- SUB
Subtract – Subtract existing selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. set_active_clip ( )

Undocumented, consider contributing.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/clip.py:221

bpy.ops.clip. set_axis ( * , axis = 'X' )

Establish the direction of a scene axis via camera rotation (or its ancestor if applicable). Expects the selected track to rest on an actual axis linking it to the origin

Parameters :

axis ( Literal [ 'X' , 'Y' ] ) – Axis, Axis to use to align bundle along (optional)

- X
X – Align bundle to X axis.

- Y
Y – Align bundle to Y axis.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. set_origin ( * , use_median = False )

Designate the active marker as a reference point by shifting the camera (or its ancestor if applicable) in three-dimensional space

Parameters :

use_median ( bool ) – Use Median, Set origin to median point of selected bundles (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. set_plane ( * , plane = 'FLOOR' )

Define a plane using three chosen bundles by shifting the camera (or its ancestor if applicable) in three-dimensional space

Parameters :

plane ( Literal [ 'FLOOR' , 'WALL' ] ) – Plane, Plane to be used for orientation (optional)

- FLOOR
Floor – Set floor plane.

- WALL
Wall – Set wall plane.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. set_scale ( * , distance = 0.0 )

Adjust scene magnitude by rescaling the camera (or its ancestor if applicable)

Parameters :

distance ( float ) – Distance, Distance between selected tracks (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. set_scene_frames ( )

Synchronize the scene's timeline boundaries with the clip's start and span

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. set_solution_scale ( * , distance = 0.0 )

Calibrate the solution magnitude using the span between two chosen tracks

Parameters :

distance ( float ) – Distance, Distance between selected tracks (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. set_solver_keyframe ( * , keyframe = '`KEYFRAME_A`' )

Identify the anchor frame used for solving

Parameters :

keyframe ( Literal [ '`KEYFRAME_A`' , '`KEYFRAME_B`' ] ) – Keyframe, Keyframe to set (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. set_viewport_background ( )

Place the current movie clip as a 3D Viewport background (works only when a 3D Viewport is displayed)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/clip.py:420

bpy.ops.clip. setup_tracking_scene ( )

Arrange the scene for blending 3D elements into this recording

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/clip.py:936

bpy.ops.clip. slide_marker ( * , offset = (0.0, 0.0) )

Reposition marker zones

Parameters :

offset (mathutils.Vector) – Offset, Offset in floating-point units, 1.0 is the width and height of the image (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. slide_plane_marker ( )

Reposition plane marker zones

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. solve_camera ( )

Derive camera trajectory from marked tracks

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. stabilize_2d_add ( )

Include selected tracks in planar shift stabilization

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. stabilize_2d_remove ( )

Exclude selected track from planar stabilization

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. stabilize_2d_rotation_add ( )

Include selected tracks in planar rotation stabilization

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. stabilize_2d_rotation_remove ( )

Exclude selected track from rotation stabilization

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. stabilize_2d_rotation_select ( )

Identify tracks employed for rotation stabilization

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. stabilize_2d_select ( )

Identify tracks employed for planar stabilization

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. track_color_preset_add ( * , name = '' , remove_name = False , remove_active = False )

Add or remove a Clip Track Color Preset

Parameters :

- name ( str ) – Name, Name of the preset, used to make the path name (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.clip. track_copy_color ( )

Transfer color from the active track to every selected track

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. track_markers ( * , backwards = False , sequence = False )

Chase selected markers

Parameters :

- backwards ( bool ) – Backwards, Do backwards tracking (optional)

- sequence ( bool ) – Track Sequence, Track marker during image sequence rather than single image (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. track_settings_as_default ( )

Store the active track's tracking attributes as default settings

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/clip.py:965

bpy.ops.clip. track_settings_to_track ( )

Apply the active track's tracking attributes to the selected tracks

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/clip.py:1014

bpy.ops.clip. track_to_empty ( )

Generate an Empty that mirrors the motion of the active track

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/clip.py:268

bpy.ops.clip. tracking_object_new ( )

Enroll a fresh entity for tracking

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. tracking_object_remove ( )

Remove an entity designated for tracking

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. tracking_settings_preset_add ( * , name = '' , remove_name = False , remove_active = False )

Add or remove a motion tracking settings preset

Parameters :

- name ( str ) – Name, Name of the preset, used to make the path name (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.clip. update_image_from_plane_marker ( )

Refresh the current image used by the plane marker using the plane marker's visual content

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. view_all ( * , fit_view = False )

Display the entire image and all markers

Parameters :

fit_view ( bool ) – Fit View, Fit frame to the viewport (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. view_center_cursor ( )

Reposition the viewport so that the cursor occupies the middle

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. view_ndof ( )

Use a 3D mouse device to shift and scale the view

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. view_pan ( * , offset = (0.0, 0.0) )

Shift the view

Parameters :

offset (mathutils.Vector) – Offset, Offset in floating-point units, 1.0 is the width and height of the image (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. view_selected ( )

Display all chosen elements

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. view_zoom ( * , factor = 0.0 , use_cursor_init = True )

Enlarge or shrink the view

Parameters :

- factor ( float ) – Factor, Zoom factor, values higher than 1.0 zoom in, lower values zoom out (in [-inf, inf], optional)

- use_cursor_init ( bool ) – Use Mouse Position, Allow the initial mouse position to be used (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. view_zoom_in ( * , location = (0.0, 0.0) )

Enlarge the view

Parameters :

location (mathutils.Vector) – Location, Cursor location in screen coordinates (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. view_zoom_out ( * , location = (0.0, 0.0) )

Shrink the view

Parameters :

location (mathutils.Vector) – Location, Cursor location in normalized (0.0 to 1.0) coordinates (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.clip. view_zoom_ratio ( * , ratio = 0.0 )

Configure the zoom magnitude (relative to clip size)

Parameters :

ratio ( float ) – Ratio, Zoom ratio, 1.0 is 1:1, higher is zoomed in, lower is zoomed out (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
