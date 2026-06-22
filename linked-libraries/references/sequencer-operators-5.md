# Sequencer Operators (part 5)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

bpy.ops.sequencer.select_side(*, side='BOTH')

Pick pieces on the designated direction of the chosen pieces.

Parameters:

side (Literal['MOUSE', 'LEFT', 'RIGHT', 'BOTH', '`NO_CHANGE`']) – Side, Which direction to apply the choice to (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.select_side_of_frame(*, extend=False, side='LEFT')

Pick pieces in relation to the current picture.

Parameters:

- extend (bool) – Extend, Add to choice instead of clearing prior choice (optional)
- side (Literal['LEFT', 'RIGHT', 'CURRENT']) – Side, (optional)
  - LEFT
    Left – Pick to the left of the current picture.
  - RIGHT
    Right – Pick to the right of the current picture.
  - CURRENT
    Current Frame – Pick crossing the current picture.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.set_range_to_strips(*, preview=False)

Span the picture range to the chosen pieces beginning and conclusion.

Parameters:

preview (bool) – Preview, Span the preview range instead (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.slip(*, offset=0.0, slip_keyframes=False, use_cursor_position=False, ignore_connections=False)

Reposition the source material within chosen pieces.

Parameters:

- offset (float) – Offset, Shift in the source material of the piece (in [-inf, inf], optional)
- slip_keyframes (bool) – Slip Keyframes, Relocate the control points alongside the material (optional)
- use_cursor_position (bool) – Use Cursor Position, Slip pieces under the pointer rather than all chosen pieces (optional)
- ignore_connections (bool) – Ignore Connections, Do not slip attached pieces if employing pointer position (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.snap(*, frame=0, side='LEFT', keep_offset=True)

Shift pieces to the current picture, employing the active piece as the pivot, and the pointer location in relation to the playhead to establish which direction of the playhead to snap to.

Parameters:

- frame (int) – Frame, Picture where chosen pieces will be shifted (in [-inf, inf], optional)
- side (Literal['LEFT', 'RIGHT']) – Snap Side, Which direction of the playhead pieces should snap to when no locations are picked (optional)
- keep_offset (bool) – Keep Offset, Whether the choice should be shifted completely or by each individual piece (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.sound_strip_add(*, filepath='', directory='', files=None, check_existing=False, filter_blender=False, filter_backup=False, filter_image=False, filter_movie=False, filter_python=False, filter_font=False, filter_sound=True, filter_text=False, filter_archive=False, filter_btx=False, filter_alembic=False, filter_usd=False, filter_obj=False, filter_volume=False, filter_folder=True, filter_blenlib=False, filemode=9, relative_path=True, display_type='DEFAULT', sort_method='', move_strips=True, frame_start=0, channel=1, replace_sel=True, overlap=False, overlap_shuffle_override=False, skip_locked_or_muted_channels=True, cache=False, mono=False)

Insert an audio piece into the sequencer.

Parameters:

- filepath (str) – File Path, Source to the file (optional, never None)
- directory (str) – Directory, Containing folder of the file (optional, never None)
- files (bpy_prop_collection[OperatorFileListElement]) – Files, (optional)
- check_existing (bool) – Check Existing, Notify user before overwriting (optional)
- filter_blender (bool) – Filter .blend files, (optional)
- filter_backup (bool) – Filter backup .blend files, (optional)
- filter_image (bool) – Filter image files, (optional)
- filter_movie (bool) – Filter movie files, (optional)
- filter_python (bool) – Filter Python files, (optional)
- filter_font (bool) – Filter font files, (optional)
- filter_sound (bool) – Filter sound files, (optional)
- filter_text (bool) – Filter text files, (optional)
- filter_archive (bool) – Filter archive files, (optional)
- filter_btx (bool) – Filter btx files, (optional)
- filter_alembic (bool) – Filter Alembic files, (optional)
- filter_usd (bool) – Filter USD files, (optional)
- filter_obj (bool) – Filter OBJ files, (optional)
- filter_volume (bool) – Filter OpenVDB volume files, (optional)
- filter_folder (bool) – Filter folders, (optional)
- filter_blenlib (bool) – Filter Blender IDs, (optional)
- filemode (int) – File Browser Mode, Setting for the file browser mode to load a .blend file, a library or a special file (in [1, 9], optional)
- relative_path (bool) – Relative Path, Use path relative to the .blend file (optional)
- display_type (Literal['DEFAULT', '`LIST_VERTICAL`', '`LIST_HORIZONTAL`', 'THUMBNAIL']) – Display Type, (optional)
  - DEFAULT
    Default – Infer presentation from file types.
  - `LIST_VERTICAL`
    Short List – Compact file list view.
  - `LIST_HORIZONTAL`
    Long List – Comprehensive file list view.
  - THUMBNAIL
    Thumbnails – Picture previews.
- sort_method (Literal['DEFAULT', '`FILE_SORT_ALPHA`', '`FILE_SORT_EXTENSION`', '`FILE_SORT_TIME`', '`FILE_SORT_SIZE`', '`ASSET_CATALOG`']) – File sorting mode, (optional)
  - DEFAULT
    Default – Infer sorting approach from file types.
  - `FILE_SORT_ALPHA`
    Name – Order file list in alphabetical sequence.
  - `FILE_SORT_EXTENSION`
    Extension – Order file list by file kind.
  - `FILE_SORT_TIME`
    Modified Date – Order files by change timestamp.
  - `FILE_SORT_SIZE`
    Size – Order files by storage size.
  - `ASSET_CATALOG`
    Asset Catalog – Order assets so those in the same collection stay together. Within a single collection, assets are ordered alphabetically. The collections are in order of the expanded collection hierarchy..
- move_strips (bool) – Move Strips, Automatically initiate mouse-driven translation of strips after insertion (optional)
- frame_start (int) – Start Frame, Where on the timeline the strip begins (in [-inf, inf], optional)
- channel (int) – Channel, Sequencer track for placement (in [1, 128], optional)
- replace_sel (bool) – Replace Selection, Clear prior selections once the operation finishes (optional)
- overlap (bool) – Allow Overlap, Permit new strips to overlap without correction (optional)
- overlap_shuffle_override (bool) – Override Overlap Shuffle Behavior, Use overlap mode from tool configuration (optional)
- skip_locked_or_muted_channels (bool) – Skip Locked or Muted Channels, Bypass muted or protected tracks when inserting (optional)
- cache (bool) – Cache, Store the sound in active memory (optional)
- mono (bool) – Mono, Merge all the sound's audio channels into a single channel (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.split(*, frame=0, channel=0, type='SOFT', use_cursor_position=False, side='MOUSE', ignore_selection=False, ignore_connections=False)

Partition the chosen pieces into halves.

Parameters:

- frame (int) – Frame, Picture where chosen pieces will be partitioned (in [-inf, inf], optional)
- channel (int) – Channel, Track in which piece will be severed (in [-inf, inf], optional)
- type (Literal['SOFT', 'HARD']) – Type, How the cut is performed on selected pieces (optional)
- use_cursor_position (bool) – Use Cursor Position, Sever at the pointer instead of current picture (optional)
- side (Literal['MOUSE', 'LEFT', 'RIGHT', 'BOTH', '`NO_CHANGE`']) – Side, Which direction continues picked after severing (optional)
- ignore_selection (bool) – Ignore Selection, Make cut even if piece is not picked maintaining choice state after cut (optional)
- ignore_connections (bool) – Ignore Connections, Keep cuts isolated to individual strips (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.split_multicam(*, camera=1)

Partition multicam piece and pick camera.

Parameters:

camera (int) – Camera, (in [1, 32], optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

File:

startup/bl_operators/sequencer.py:96

bpy.ops.sequencer.strip_color_tag_set(*, color='NONE')

Use color marking for the chosen pieces.

Parameters:

color (Literal[Strip Color Items]) – Color Tag, (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.strip_jump(*, next=True, center=True)

Shift picture to next or prior modification location.

Parameters:

- next (bool) – Next Strip, (optional)
- center (bool) – Use Strip Center, (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.strip_modifier_add(*, type='')

Attach a modifier to the piece.

Parameters:

type (str) – Type, (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.strip_modifier_copy(*, type='REPLACE')

Apply modifiers of the active piece to all chosen pieces.

Parameters:

type (Literal['REPLACE', 'APPEND']) – Type, (optional)

- REPLACE
  Replace – Overwrite modifiers in place.
- APPEND
  Append – Attach active modifiers to chosen pieces.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.strip_modifier_equalizer_redefine(*, graphs='SIMPLE', name='Name')

Modify the definitions of equalizer curves.

Parameters:

- graphs (Literal['SIMPLE', 'DOUBLE', 'TRIPLE']) – Graphs, Quantity of curves (optional)
  - SIMPLE
    Unique – One distinct graphical meaning.
  - DOUBLE
    Double – Graphical meaning in 2 areas.
  - TRIPLE
    Triplet – Graphical meaning in 3 areas.
- name (str) – Name, Name of modifier to redescribe (optional, never None)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.strip_modifier_move(*, name='Name', direction='UP')

Reposition modifier within the compilation.

Parameters:

- name (str) – Name, Name of modifier to discard (optional, never None)
- direction (Literal['UP', 'DOWN']) – Type, (optional)
  - UP
    Up – Reposition modifier upward in the compilation.
  - DOWN
    Down – Reposition modifier downward in the compilation.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.strip_modifier_move_to_index(*, modifier='', index=0)

Modify the piece modifier's rank in the compilation so it computes following the configured number of others.

Parameters:

- modifier (str) – Modifier, Name of the modifier to manage (optional, never None)
- index (int) – Index, The rank to move the modifier to (in [0, inf], optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.strip_modifier_remove(*, name='Name')

Detach a modifier from the piece.

Parameters:

name (str) – Name, Name of modifier to discard (optional, never None)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.strip_modifier_set_active(*, modifier='')

Enable the piece modifier to employ as the reference.

Parameters:

modifier (str) – Modifier, Name of the piece modifier to manage (optional, never None)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

- `ASSET_CATALOG`
Asset Catalog – Group the asset list by catalog so that assets sharing a catalog stay together; within one catalog they run in name order, and the catalogs follow the order of the flattened catalog hierarchy.

- move_strips ( bool ) – Move Strips, Once strips are dropped on the timeline, immediately pick them up for mouse translation (optional)

- frame_start ( int ) – Start Frame, The strip's first frame (in [-inf, inf], optional)

- channel ( int ) – Channel, Which channel the strip is placed on (in [1, 128], optional)

- replace_sel ( bool ) – Replace Selection, After the add completes, drop the previously selected strips (optional)

- overlap ( bool ) – Allow Overlap, Leave any overlap on the new strips uncorrected (optional)

- overlap_shuffle_override ( bool ) – Override Overlap Shuffle Behavior, Defer to the overlap_mode tool setting for how overlapping strips are shuffled (optional)

- skip_locked_or_muted_channels ( bool ) – Skip Locked or Muted Channels, Permit movie strips to be added onto muted or locked channels (optional)

- cache ( bool ) – Cache, Keep the sound resident in memory (optional)

- mono ( bool ) – Mono, Fold all of the sound's channels down to one (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sequencer. split ( * , frame = 0 , channel = 0 , type = 'SOFT' , use_cursor_position = False , side = 'MOUSE' , ignore_selection = False , ignore_connections = False ) 

Cut each selected strip into two

Parameters :

- frame ( int ) – Frame, The frame at which the selected strips are divided (in [-inf, inf], optional)

- channel ( int ) – Channel, The channel where the cut is made (in [-inf, inf], optional)

- type ( Literal [ 'SOFT' , 'HARD' ] ) – Type, Which kind of split to run on the strips (optional)

- use_cursor_position ( bool ) – Use Cursor Position, Cut at the cursor's location rather than at the current frame (optional)

- side ( Literal [ 'MOUSE' , 'LEFT' , 'RIGHT' , 'BOTH' , '`NO_CHANGE`' ] ) – Side, Which part stays selected after the cut (optional)

- ignore_selection ( bool ) – Ignore Selection, Cut even unselected strips, leaving the selection state unchanged afterward (optional)

- ignore_connections ( bool ) – Ignore Connections, Stop the split from carrying through to connected strips (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sequencer. split_multicam ( * , camera = 1 ) 

Cut a multicam strip and select its camera

Parameters :

camera ( int ) – Camera, (in [1, 32], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/sequencer.py:96

bpy.ops.sequencer. strip_color_tag_set ( * , color = 'NONE' ) 

Assign a color tag to the selected strips

Parameters :

color (Literal[Strip Color Items]) – Color Tag, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sequencer. strip_jump ( * , next = True , center = True ) 

Send the playhead to the next or previous edit point

Parameters :

- next ( bool ) – Next Strip, (optional)

- center ( bool ) – Use Strip Center, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sequencer. strip_modifier_add ( * , type = '' ) 

Attach a modifier to the strip

Parameters :

type ( str ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sequencer. strip_modifier_copy ( * , type = 'REPLACE' ) 

Carry the active strip's modifiers over to every selected strip

Parameters :

type ( Literal [ 'REPLACE' , 'APPEND' ] ) – Type, (optional)

- REPLACE
Replace – Overwrite the modifiers on the destination.

- APPEND
Append – Tack the active modifiers onto the selected strips.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sequencer. strip_modifier_equalizer_redefine ( * , graphs = 'SIMPLE' , name = 'Name' ) 

Rebuild the equalizer graphs

Parameters :

- graphs ( Literal [ 'SIMPLE' , 'DOUBLE' , 'TRIPLE' ] ) – Graphs, How many graphs to use (optional)

- SIMPLE
Unique – A single graphical definition.

- DOUBLE
Double – A graphical definition divided into 2 sections.

- TRIPLE
Triplet – A graphical definition divided into 3 sections.

- name ( str ) – Name, Which modifier to redefine, by name (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sequencer. strip_modifier_move ( * , name = 'Name' , direction = 'UP' ) 

Shift a modifier up or down within the stack

Parameters :

- name ( str ) – Name, The modifier to act on, by name (optional, never None)

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Type, (optional)

- UP
Up – Move the modifier one place up the stack.

- DOWN
Down – Move the modifier one place down the stack.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sequencer. strip_modifier_move_to_index ( * , modifier = '' , index = 0 ) 

Reposition the strip modifier within the stack so it is evaluated after the chosen number of others

Parameters :

- modifier ( str ) – Modifier, The modifier to edit, by name (optional, never None)

- index ( int ) – Index, Where in the stack to move the modifier (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sequencer. strip_modifier_remove ( * , name = 'Name' ) 

Take a modifier off the strip

Parameters :

name ( str ) – Name, The modifier to remove, by name (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sequencer. strip_modifier_set_active ( * , modifier = '' ) 

Make a strip modifier the active one so it acts as the context

Parameters :

modifier ( str ) – Modifier, The strip modifier to edit, by name (optional, never None)

Returns :

Result of the operator call.

Return type :

bpy.ops.sequencer.strip_transform_clear(*, property='ALL')

Return image shift to initial state.

Parameters:

property (Literal['POSITION', 'SCALE', 'ROTATION', 'ALL']) – Property, Strip shift characteristic to be restored (optional)

- POSITION
  Position – Reset piece shift location.
- SCALE
  Scale – Reset piece shift magnitude.
- ROTATION
  Rotation – Reset piece shift rotation.
- ALL
  All – Reset piece shift location, magnitude and rotation.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.strip_transform_fit(*, fit_method='FIT')

Fit image dimensions within the viewport boundaries.

Parameters:

fit_method (Literal[Strip Scale Method Items]) – Fit Method, How to scale the image within the viewport (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.swap(*, side='RIGHT')

Exchange active piece with piece to the right or left.

Parameters:

side (Literal['LEFT', 'RIGHT']) – Side, Direction of the piece to exchange (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.swap_data()

Exchange 2 sequencer pieces.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.swap_inputs()

Exchange the dual inputs of the effect piece.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.text_cursor_move(*, type='`LINE_BEGIN`', select_text=False)

Move mark in text.

Parameters:

- type (Literal['`LINE_BEGIN`', '`LINE_END`', '`TEXT_BEGIN`', '`TEXT_END`', '`PREVIOUS_CHARACTER`', '`NEXT_CHARACTER`', '`PREVIOUS_WORD`', '`NEXT_WORD`', '`PREVIOUS_LINE`', '`NEXT_LINE`']) – Type, Where to move mark to, to form a pick (optional)
- select_text (bool) – Select Text, Form a pick while moving mark (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.text_cursor_set(*, select_text=False)

Fix mark location in text.

Parameters:

select_text (bool) – Select Text, Form a pick while moving mark (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.text_delete(*, type='`NEXT_OR_SELECTION`')

Erase text at mark location.

Parameters:

type (Literal['`NEXT_OR_SELECTION`', '`PREVIOUS_OR_SELECTION`']) – Type, Which section of the text to erase (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.text_deselect_all()

Unpick all symbols.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.text_edit_copy()

Duplicate text to clipboard.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.text_edit_cut()

Move text to clipboard.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.text_edit_mode_toggle()

Switch text editing.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.text_edit_paste()

Insert text from clipboard.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.text_insert(*, string='')

Enter text at mark location.

Parameters:

string (str) – String, Message to be entered at mark location (optional, never None)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.text_line_break()

Enter line separation at mark location.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.text_select_all()

Pick all symbols.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.unlock()

Unprotect pieces so they can be moved.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.unmute(*, unselected=False)

Toggle sound on (un)chosen pieces.

Parameters:

unselected (bool) – Unselected, Toggle sound on unselected rather than chosen pieces (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.view_all()

Display all the pieces in the sequencer.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.view_all_preview()

Magnify preview to fit in the zone.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.view_frame()

Shift the presentation to the current picture.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.view_ghost_border(*, xmin=0, xmax=0, ymin=0, ymax=0, wait_for_input=True)

Establish the limits of the border used for offset presentation.

Parameters:

- xmin (int) – X Min, (in [-inf, inf], optional)
- xmax (int) – X Max, (in [-inf, inf], optional)
- ymin (int) – Y Min, (in [-inf, inf], optional)
- ymax (int) – Y Max, (in [-inf, inf], optional)
- wait_for_input (bool) – Wait for Input, (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.view_selected()

Magnify the sequencer on the chosen pieces.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.view_zoom_ratio(*, ratio=1.0)

Modify magnification ratio of sequencer preview.

Parameters:

ratio (float) – Ratio, Magnification ratio, 1.0 is 1:1, greater is magnified in, lesser is magnified out (in [-inf, inf], optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]
