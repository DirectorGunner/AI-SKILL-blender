# Sequencer Operators (part 3)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

bpy.ops.sequencer.retiming_transition_add(*, duration=0)

Create smooth interpolation between 2 speed-adjusted sections.

Parameters:

duration (int) – Duration, Period of held frame region (in [0, inf], optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.sample(*, size=1)

Employ mouse to capture color from the current picture.

Parameters:

size (int) – Sample Size, (in [1, 128], optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.scene_frame_range_update()

Refresh the time span of a scene piece.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.scene_strip_add(*, move_strips=True, frame_start=0, channel=1, replace_sel=True, overlap=False, overlap_shuffle_override=False, skip_locked_or_muted_channels=True, scene='')

Insert a piece that uses an existing scene as source media.

Parameters:

- move_strips (bool) – Move Strips, Automatically initiate mouse-driven translation of strips after insertion (optional)
- frame_start (int) – Start Frame, Where on the timeline the strip begins (in [-inf, inf], optional)
- channel (int) – Channel, Sequencer track for placement (in [1, 128], optional)
- replace_sel (bool) – Replace Selection, Clear prior selections once the operation finishes (optional)
- overlap (bool) – Allow Overlap, Permit new strips to overlap without correction (optional)
- overlap_shuffle_override (bool) – Override Overlap Shuffle Behavior, Use overlap mode from tool configuration (optional)
- skip_locked_or_muted_channels (bool) – Skip Locked or Muted Channels, Bypass muted or protected tracks when inserting (optional)
- scene (str) – Scene, (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.scene_strip_add_new(*, move_strips=True, frame_start=0, channel=1, replace_sel=True, overlap=False, overlap_shuffle_override=False, skip_locked_or_muted_channels=True, type='NEW')

Insert a piece that uses a fresh scene as source media.

Parameters:

- move_strips (bool) – Move Strips, Automatically initiate mouse-driven translation of strips after insertion (optional)
- frame_start (int) – Start Frame, Where on the timeline the strip begins (in [-inf, inf], optional)
- channel (int) – Channel, Sequencer track for placement (in [1, 128], optional)
- replace_sel (bool) – Replace Selection, Clear prior selections once the operation finishes (optional)
- overlap (bool) – Allow Overlap, Permit new strips to overlap without correction (optional)
- overlap_shuffle_override (bool) – Override Overlap Shuffle Behavior, Use overlap mode from tool configuration (optional)
- skip_locked_or_muted_channels (bool) – Skip Locked or Muted Channels, Bypass muted or protected tracks when inserting (optional)
- type (Literal['NEW', 'EMPTY', '`LINK_COPY`', '`FULL_COPY`']) – Type, (optional)
  - NEW
    New – Insert new piece with a fresh bare scene using defaults.
  - EMPTY
    Copy Settings – Insert a piece with a bare scene, and replicate parameters from the active scene.
  - `LINK_COPY`
    Linked Copy – Insert a piece and bring in the groups from the active scene (shallow copy).
  - `FULL_COPY`
    Full Copy – Insert a piece and produce a complete duplicate of the active scene.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.select(*, wait_to_deselect_others=False, use_select_on_click=False, mouse_x=0, mouse_y=0, extend=False, deselect=False, toggle=False, deselect_all=False, select_passthrough=False, center=False, linked_handle=False, linked_time=False, side_of_frame=False, ignore_connections=False)

Choose a piece (most recent picked becomes the "active piece").

Parameters:

- wait_to_deselect_others (bool) – Wait to Deselect Others, (optional)
- use_select_on_click (bool) – Act on Click, Rather than pick on press, hold to see drag. Otherwise pick on release (optional)
- mouse_x (int) – Mouse X, (in [-inf, inf], optional)
- mouse_y (int) – Mouse Y, (in [-inf, inf], optional)
- extend (bool) – Extend, Add to choice instead of clearing prior choice (optional)
- deselect (bool) – Deselect, Remove from choice (optional)
- toggle (bool) – Toggle Selection, Switch choice state (optional)
- deselect_all (bool) – Deselect On Nothing, Clear all choice when pointer is empty (optional)
- select_passthrough (bool) – Only Select Unselected, Disregard the pick action when the piece is previously chosen (optional)
- center (bool) – Center, Use the piece midpoint when picking, in composition mode apply to grow piece choice (optional)
- linked_handle (bool) – Linked Handle, Pick locations next to the active piece (optional)
- linked_time (bool) – Linked Time, Pick other pieces or locations at the same moment, or all speed-adjustment points after the active in speed-adjustment mode (optional)
- side_of_frame (bool) – Side of Frame, Pick all pieces on same direction of the current picture as the pointer (optional)
- ignore_connections (bool) – Ignore Connections, Pick pieces independently regardless of connection state (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.select_all(*, action='TOGGLE')

Pick or unpick all pieces.

Parameters:

action (Literal['TOGGLE', 'SELECT', 'DESELECT', 'INVERT']) – Action, Pick operation to run (optional)

- TOGGLE
  Toggle – Switch choice for all items.
- SELECT
  Select – Pick all items.
- DESELECT
  Deselect – Unpick all items.
- INVERT
  Invert – Switch choice of all items.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.select_box(*, xmin=0, xmax=0, ymin=0, ymax=0, wait_for_input=True, mode='SET', tweak=False, include_handles=False, ignore_connections=False)

Pick pieces via rectangular selection.

Parameters:

- xmin (int) – X Min, (in [-inf, inf], optional)
- xmax (int) – X Max, (in [-inf, inf], optional)
- ymin (int) – Y Min, (in [-inf, inf], optional)
- ymax (int) – Y Max, (in [-inf, inf], optional)
- wait_for_input (bool) – Wait for Input, (optional)
- mode (Literal['SET', 'ADD', 'SUB']) – Mode, (optional)
  - SET
    Set – Establish a fresh choice.
  - ADD
    Extend – Grow the existing choice.
  - SUB
    Subtract – Reduce the existing choice.
- tweak (bool) – Tweak, Permit box pick to pass through to sequence slide when the pointer is over a piece (optional)
- include_handles (bool) – Select Handles, Pick the pieces and their locations (optional)
- ignore_connections (bool) – Ignore Connections, Pick pieces independently regardless of connection state (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.select_circle(*, x=0, y=0, radius=25, wait_for_input=True, mode='SET', ignore_connections=False)

Pick pieces via circular selection.

Parameters:

- x (int) – X, (in [-inf, inf], optional)
- y (int) – Y, (in [-inf, inf], optional)
- radius (int) – Radius, (in [1, inf], optional)
- wait_for_input (bool) – Wait for Input, (optional)
- mode (Literal['SET', 'ADD', 'SUB']) – Mode, (optional)
  - SET
    Set – Establish a fresh choice.
  - ADD
    Extend – Grow the existing choice.
  - SUB
    Subtract – Reduce the existing choice.
- ignore_connections (bool) – Ignore Connections, Pick pieces independently regardless of connection state (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.select_grouped(*, type='TYPE', extend=False, use_active_channel=False)

Pick all pieces arranged by varied properties.

Parameters:

- type (Literal['TYPE', '`TYPE_BASIC`', '`TYPE_EFFECT`', 'DATA', 'EFFECT', '`EFFECT_LINK`', 'OVERLAP']) – Type, (optional)
  - TYPE
    Type – Common piece category.
  - `TYPE_BASIC`
    Global Type – All pieces of same general category (pictorial or auditory).
  - `TYPE_EFFECT`
    Effect Type – Common piece effect category (if active piece is not an effect one, pick all non-effect pieces).
  - DATA
    Data – Common information (scene, picture, sound, etc.).
  - EFFECT
    Effect – Common effects.
  - `EFFECT_LINK`
    Effect/Linked – Other pieces impacted by the active one (overlapping timing, and below or effect-connected).
  - OVERLAP
    Overlap – Overlapping duration.
- extend (bool) – Extend, Add to choice instead of clearing prior choice (optional)
- use_active_channel (bool) – Same Channel, Only think about pieces on the identical track as the active one (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.select_handle(*, wait_to_deselect_others=False, use_select_on_click=False, mouse_x=0, mouse_y=0, ignore_connections=False)

Pick piece location.

Parameters:

- wait_to_deselect_others (bool) – Wait to Deselect Others, (optional)
- use_select_on_click (bool) – Act on Click, Rather than pick on press, hold to see drag. Otherwise pick on release (optional)
- mouse_x (int) – Mouse X, (in [-inf, inf], optional)
- mouse_y (int) – Mouse Y, (in [-inf, inf], optional)
- ignore_connections (bool) – Ignore Connections, Pick pieces independently regardless of connection state (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.select_handles(*, side='BOTH')

Pick adjustment handles on the margins of the chosen piece.

Parameters:

side (Literal['LEFT', 'RIGHT', 'BOTH', '`LEFT_NEIGHBOR`', '`RIGHT_NEIGHBOR`', '`BOTH_NEIGHBORS`']) – Side, Which margin of the handle is picked (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.select_lasso(*, path=None, use_smooth_stroke=False, smooth_stroke_factor=0.75, smooth_stroke_radius=35, mode='SET')

Pick pieces via freehand selection.

Parameters:

- path (bpy_prop_collection[OperatorMousePath]) – Path, (optional)
- use_smooth_stroke (bool) – Stabilize Stroke, Choice lags behind the pointer and follows a softer arc (optional)
- smooth_stroke_factor (float) – Smooth Stroke Factor, Larger numbers generate a softer path (in [0.5, 0.99], optional)
- smooth_stroke_radius (int) – Smooth Stroke Radius, Least separation from last point before choice resumes (in [10, 200], optional)
- mode (Literal['SET', 'ADD', 'SUB']) – Mode, (optional)
  - SET
    Set – Establish a fresh choice.
  - ADD
    Extend – Grow the existing choice.
  - SUB
    Subtract – Reduce the existing choice.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.select_less()

Contract the active choice of adjoining picked pieces.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.select_linked()

Pick all pieces neighboring the active choice.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.select_linked_pick(*, extend=False)

Pick a string of linked pieces nearest to the pointer.

Parameters:

extend (bool) – Extend, Grow the choice (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.select_more()

Pick more pieces neighboring the active choice.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

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
