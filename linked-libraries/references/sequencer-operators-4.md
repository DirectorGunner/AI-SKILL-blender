# Sequencer Operators (part 4)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

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
