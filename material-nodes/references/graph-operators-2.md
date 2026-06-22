# Graph Operators (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Graph-based keyframe operations and animation tools

Identifier keyframes that share the same F-Curve channel as ones currently active

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.graph.select_more ( )
Grow keyframe selection to nearby frames in the same curves

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.graph.shear ( * , factor = 0.0 , direction = '`FROM_LEFT`' )
Adjust key values in a linear progression, preserving relative spacing by anchoring to one end

Parameters:
- factor ( float ) – Shear Factor, The magnitude to apply for skewing (in [-inf, inf], optional)
- direction ( Literal [ '`FROM_LEFT`' , '`FROM_RIGHT`' ] ) – Direction, Which boundary acts as the fixed anchor point (optional)
- `FROM_LEFT`: Use the left key as the fixed reference
- `FROM_RIGHT`: Use the right key as the fixed reference

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.graph.smooth ( )
Blend curve points using weighted averages to reduce noise and irregular motion

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.graph.snap ( * , type = 'CFRA' )
Align selected keyframes to designated positions in the timeline or value axis

Parameters:
type ( Literal [ 'CFRA' , 'VALUE' , '`NEAREST_FRAME`' , '`NEAREST_SECOND`' , '`NEAREST_MARKER`' , 'HORIZONTAL' ] ) – Type, (optional)
- CFRA: Realign selected keyframes to match the playhead frame
- VALUE: Reposition selected keyframe heights to the cursor Y coordinate
- `NEAREST_FRAME`: Shift keyframes to whole-frame boundaries (corrects subframe timing errors)
- `NEAREST_SECOND`: Realign keyframes to the nearest whole second mark
- `NEAREST_MARKER`: Reposition keyframes at timeline marker locations
- HORIZONTAL: Straighten out curve handles for smoother transitions

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.graph.snap_cursor_value ( )
Update the cursor height to the center-point of all selected keyframe values

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.graph.sound_to_samples ( * , filepath = '' , check_existing = False , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = True , filter_python = False , filter_font = False , filter_sound = True , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 9 , show_multiview = False , use_multiview = False , display_type = 'DEFAULT' , sort_method = '' , low = 0.0 , high = 100000.0 , attack = 0.005 , release = 0.2 , threshold = 0.0 , use_accumulate = False , use_additive = False , use_square = False , sthreshold = 0.1 )
Translate audio waveforms into keyframe samples across chosen curve channels

Parameters:
- filepath ( str ) – File Path, Location of the audio file (optional, never None)
- check_existing ( bool ) – Check Existing, Warn before replacing files (optional)
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
- filemode ( int ) – File Browser Mode, Controls which file types the browser accepts (in [1, 9], optional)
- show_multiview ( bool ) – Enable Multi-View, (optional)
- use_multiview ( bool ) – Use Multi-View, (optional)
- display_type ( Literal [ 'DEFAULT' , '`LIST_VERTICAL`' , '`LIST_HORIZONTAL`' , 'THUMBNAIL' ] ) – Display Type, (optional)
- DEFAULT: Let system choose display layout based on file type
- `LIST_VERTICAL`: Show entries in a compact vertical list
- `LIST_HORIZONTAL`: Show entries in a full-width list with details
- THUMBNAIL: Show entries as large thumbnail icons
- sort_method ( str ) – File sorting mode, (optional)
- low ( float ) – Lowest Frequency, Cutoff for removing frequencies below this range (in [0, 100000], optional)
- high ( float ) – Highest Frequency, Cutoff for removing frequencies above this range (in [0, 100000], optional)
- attack ( float ) – Attack Time, Controls how quickly the envelope can climb (lower = steeper rise) (in [0, 2], optional)
- release ( float ) – Release Time, Controls how quickly the envelope can fall (lower = steeper drop) (in [0, 5], optional)
- threshold ( float ) – Threshold, Minimum signal level to register (in [0, 1], optional)
- use_accumulate ( bool ) – Accumulate, Sum only positive fluctuations in the envelope (optional)
- use_additive ( bool ) – Additive, Combine all envelope amplitudes (or with Accumulate, both positive and negative swings) (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

- use_square ( bool ) – Square, Convert output to a binary waveform (negative → -1, positive → 1) (optional)
- sthreshold ( float ) – Square Threshold, In square mode, values with absolute magnitude below this round to zero (in [0, 1], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.graph.time_offset ( * , frame_offset = 0.0 )
Translate selected keyframes along the time axis

Parameters:
frame_offset ( float ) – Frame Offset, How many frames to shift forward or backward (in [-inf, inf], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.graph.view_all ( * , include_handles = True )
Reframe viewport to encompass all keyframes and handles

Parameters:
include_handles ( bool ) – Include Handles, Measure bounds of curve control handles when computing extents (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.graph.view_frame ( )
Center the view on the currently active timeline frame

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.graph.view_selected ( * , include_handles = True )
Reframe viewport to fit all currently highlighted keyframes

Parameters:
include_handles ( bool ) – Include Handles, Measure bounds of curve control handles when computing extents (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]
