# Screen Operators

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Screen Operators

bpy.ops.screen. actionzone ( * , modifier = 0 )

Process input in screen boundary areas to support mouse actions and gestures

Parameters :

modifier ( int ) – Modifier, Input modifier combination (in [0, 2], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. animation_cancel ( * , restore_frame = True )

Stop animation, reverting to the pre-animation frame

Parameters :

restore_frame ( bool ) – Restore Frame, Return to the frame that was active when playback started (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. animation_play ( * , reverse = False , sync = False )

Begin animation playback

Parameters :

- reverse ( bool ) – Play in Reverse, Run animation in reverse order (optional)

- sync ( bool ) – Sync, Skip frames if necessary to maintain consistent playback speed (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. animation_step ( )

Advance animation by the current cursor location

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. area_close ( )

Shut down the selected viewport

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. area_dupli ( )

Create an independent window containing the selected viewport

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. area_join ( * , source_xy = (0, 0) , target_xy = (0, 0) )

Combine chosen viewports into a single window

Parameters :

- source_xy ( Sequence [ int ] ) – Source location, (array of 2 items, in [-inf, inf], optional)

- target_xy ( Sequence [ int ] ) – Target location, (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. area_move ( * , x = 0 , y = 0 , delta = 0 , snap = False )

Relocate edges of the chosen viewport

Parameters :

- x ( int ) – X, (in [-inf, inf], optional)

- y ( int ) – Y, (in [-inf, inf], optional)

- delta ( int ) – Delta, (in [-inf, inf], optional)

- snap ( bool ) – Snapping, Allow precise edge alignment (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. area_options ( )

Options for partitioning and consolidating views

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. area_split ( * , direction = 'HORIZONTAL' , factor = 0.5 , cursor = (0, 0) )

Divide the chosen viewport into separate windows

Parameters :

- direction ( Literal [ 'HORIZONTAL' , 'VERTICAL' ] ) – Direction, (optional)

- factor ( float ) – Factor, (in [0, 1], optional)

- cursor ( Sequence [ int ] ) – Cursor, (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. area_swap ( * , cursor = (0, 0) )

Interchange the display positions of chosen viewports

Parameters :

cursor ( Sequence [ int ] ) – Cursor, (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. back_to_previous ( )

Restore the original display arrangement when exiting fullscreen view overlay

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. delete ( )

Discard the active workspace layout

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. drivers_editor_show ( )

Display the drivers editor in a separate window

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. frame_jump ( * , end = False )

Skip to the initial or final frame within the timeline range

Parameters :

end ( bool ) – Last Frame, Jump to the last frame of the frame range (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. frame_offset ( * , delta = 0 )

Shift the playhead forward or backward by a specified count

Parameters :

delta ( int ) – Delta, (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. header_toggle_menus ( )

Reveal or hide the header dropdown menus

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. info_log_show ( )

Display the info log in a separate window

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. keyframe_jump ( * , next = True )

Skip to the prior or subsequent keyframe

Parameters :

next ( bool ) – Next Keyframe, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. marker_jump ( * , next = True )

Skip to the prior or subsequent timeline marker

Parameters :

next ( bool ) – Next Marker, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. new ( )

Establish a new workspace layout

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. quadview_size ( )

Resize the viewports in Quad View configuration

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. redo_last ( )

Reveal settings for the most recent user action

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. region_blend ( )

Blend overlapping zones in and out

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. region_context_menu ( )

Reveal a context-sensitive menu for the zone

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. region_flip ( )

Switch the zone's alignment (left/right or top/bottom)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. region_quadview ( )

Partition the chosen viewport into four orthographic displays

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. region_scale ( )

Expand or contract the chosen viewport

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. region_toggle ( * , region_type = 'WINDOW' )

Display or conceal the zone

Parameters :

region_type (Literal[Region Type Items]) – Region Type, Which kind of zone to toggle visibility for (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. repeat_history ( * , index = 0 )

Reveal a list of prior actions to repeat

Parameters :

index ( int ) – Index, (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. repeat_last ( )

Execute the most recent action once more

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. screen_full_area ( * , use_hide_panels = False )

Switch the chosen viewport between expanded and full-screen states

Parameters :

use_hide_panels ( bool ) – Hide Panels, Conceal all side panels (Focus Mode) (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. screen_set ( * , delta = 1 )

Progress through the collection of workspaces

Parameters :

delta ( int ) – Delta, (in [-1, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. screenshot ( * , filepath = '' , hide_props_region = True , check_existing = True , filter_blender = False , filter_backup = False , filter_image = True , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 9 , show_multiview = False , use_multiview = False , display_type = 'DEFAULT' , sort_method = '' )

Grab an image of the entire Blender window

Parameters :

- filepath ( str ) – File Path, Destination file location (optional, never None)

- hide_props_region ( bool ) – Hide Operator Properties, Fold the area displaying the operator settings (optional)

- check_existing ( bool ) – Check Existing, Verify and inform if overwriting existing file (optional)

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

- filemode ( int ) – File Browser Mode, Configuration for the file browser to open a .blend file, a library or a special file (in [1, 9], optional)

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

- sort_method ( str ) – File sorting mode, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. screenshot_area ( * , filepath = '' , hide_props_region = True , check_existing = True , filter_blender = False , filter_backup = False , filter_image = True , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 9 , show_multiview = False , use_multiview = False , display_type = 'DEFAULT' , sort_method = '' )

Grab an image of a specific editor

Parameters :

- filepath ( str ) – File Path, Destination file location (optional, never None)

- hide_props_region ( bool ) – Hide Operator Properties, Fold the area displaying the operator settings (optional)

- check_existing ( bool ) – Check Existing, Verify and inform if overwriting existing file (optional)

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

- filemode ( int ) – File Browser Mode, Configuration for the file browser to open a .blend file, a library or a special file (in [1, 9], optional)

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

- sort_method ( str ) – File sorting mode, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. space_context_cycle ( * , direction = 'NEXT' )

Progress through editor contexts by moving to the next or previous one

Parameters :

direction ( Literal [ 'PREV' , 'NEXT' ] ) – Direction, Which direction to progress through (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. space_type_set_or_cycle ( * , space_type = 'EMPTY' )

Establish the editor category or change subtype

Parameters :

space_type (Literal[Space Type Items]) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. spacedata_cleanup ( )

Discard invisible editor configurations

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. time_jump ( * , backward = False )

Skip forward or backward by a number of frames or time units

Parameters :

backward ( bool ) – Backwards, Move backward through the timeline (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. userpref_show ( * , section = 'INTERFACE' )

Modify user settings and environment variables

Parameters :

section (Literal[Preference Section Items]) – Section to activate in the Preferences (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.screen. workspace_cycle ( * , direction = 'NEXT' )

Move through the collection of workspaces

Parameters :

direction ( Literal [ 'PREV' , 'NEXT' ] ) – Direction, Which direction to progress through (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
