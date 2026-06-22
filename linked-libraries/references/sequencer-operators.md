# Sequencer Operators (part 1)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

bpy.ops.sequencer.add_scene_strip_from_scene_asset(*, move_strips=True, frame_start=0, channel=1, replace_sel=True, overlap=False, overlap_shuffle_override=False, skip_locked_or_muted_channels=True, asset_library_type='LOCAL', asset_library_identifier='', relative_asset_identifier='')

Creates a sequencer strip using a duplicate of a scene asset as its source media.

Parameters:

- move_strips (bool) – Move Strips, Automatically initiate mouse-driven translation of strips after insertion (optional)
- frame_start (int) – Start Frame, Where on the timeline the strip begins (in [-inf, inf], optional)
- channel (int) – Channel, Sequencer track for placement (in [1, 128], optional)
- replace_sel (bool) – Replace Selection, Clear prior selections once the operation finishes (optional)
- overlap (bool) – Allow Overlap, Permit new strips to overlap without correction (optional)
- overlap_shuffle_override (bool) – Override Overlap Shuffle Behavior, Use overlap mode from tool configuration (optional)
- skip_locked_or_muted_channels (bool) – Skip Locked or Muted Channels, Bypass muted or protected tracks when inserting (optional)
- asset_library_type (Literal[Asset Library Type Items]) – Asset Library Type, (optional)
- asset_library_identifier (str) – Asset Library Identifier, (optional, never None)
- relative_asset_identifier (str) – Relative Asset Identifier, (optional, never None)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.box_blade(*, xmin=0, xmax=0, ymin=0, ymax=0, wait_for_input=True, mode='SET', type='SOFT', ignore_selection=True, ignore_connections=False, remove_gaps=True)

Use a rectangular marquee to define portions of strips to excise.

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
- type (Literal['SOFT', 'HARD']) – Type, How the cut is performed on selected pieces (optional)
- ignore_selection (bool) – Ignore Selection, In box blade mode, apply cuts to all pieces, ignoring selection state (optional)
- ignore_connections (bool) – Ignore Connections, Keep cuts isolated to individual strips (optional)
- remove_gaps (bool) – Remove Gaps, In box blade mode, join cut segments together, shifting later pieces forward (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.change_effect_type(*, type='CROSS')

Substitute an effect strip with another that accepts the same count of inputs.

Parameters:

type (Literal['CROSS', 'ADD', 'SUBTRACT', '`ALPHA_OVER`', '`ALPHA_UNDER`', '`GAMMA_CROSS`', 'MULTIPLY', 'WIPE', 'GLOW', 'COLOR', 'SPEED', 'MULTICAM', 'ADJUSTMENT', '`GAUSSIAN_BLUR`', 'TEXT', 'COLORMIX']) – Type, Which effect to apply (optional)

- CROSS
  Crossfade – Transition out of one movie while transition into another.
- ADD
  Add – Overlay color information from two clips.
- SUBTRACT
  Subtract – Remove one strip's colors from another.
- `ALPHA_OVER`
  Alpha Over – Layer alpha channel above other footage.
- `ALPHA_UNDER`
  Alpha Under – Layer alpha channel below other footage.
- `GAMMA_CROSS`
  Gamma Crossfade – Transition using color-corrected interpolation.
- MULTIPLY
  Multiply – Scale color from two clips together.
- WIPE
  Wipe – Push a cutting line across the image.
- GLOW
  Glow – Intensify highlights and apply diffusion.
- COLOR
  Color – Introduce a solid-color strip.
- SPEED
  Speed – Adjust playback velocity of film clips.
- MULTICAM
  Multicam Selector – Manage which camera feed is active.
- ADJUSTMENT
  Adjustment Layer – Use non-permanent image processing.
- `GAUSSIAN_BLUR`
  Gaussian Blur – Reduce sharpness along horizontal and vertical axes.
- TEXT
  Text – Introduce a text-based strip.
- COLORMIX
  Color Mix – Merge two strips via blend operations.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.change_path(*, filepath='', directory='', files=None, hide_props_region=True, check_existing=False, filter_blender=False, filter_backup=False, filter_image=False, filter_movie=False, filter_python=False, filter_font=False, filter_sound=False, filter_text=False, filter_archive=False, filter_btx=False, filter_alembic=False, filter_usd=False, filter_obj=False, filter_volume=False, filter_folder=True, filter_blenlib=False, filemode=9, relative_path=True, display_type='DEFAULT', sort_method='', use_placeholders=False)

Change the file reference for a sequencer strip.

Parameters:

- filepath (str) – File Path, Source to the file (optional, never None)
- directory (str) – Directory, Containing folder of the file (optional, never None)
- files (bpy_prop_collection[OperatorFileListElement]) – Files, (optional)
- hide_props_region (bool) – Hide Operator Properties, Collapse the panel with operator options (optional)
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
- sort_method (str) – File sorting mode, (optional)
- use_placeholders (bool) – Use Placeholders, Generate placeholder images for missing sequence frames (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.change_scene(*, scene='')

Replace the source scene for a strip.

Parameters:

scene (str) – Scene, (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.connect(*, toggle=True)

Link chosen strips together for aggregated picking.

Parameters:

toggle (bool) – Toggle, Switch connection state (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.copy()

Duplicate selected strips into a temporary buffer.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.crossfade_sounds()

Create level animation between two chosen audio pieces.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

File:

startup/bl_operators/sequencer.py:43

bpy.ops.sequencer.cursor_set(*, location=(0.0, 0.0))

Position the 2D cursor in the display.

Parameters:

location (mathutils.Vector) – Location, Where the cursor appears within normalized preview coordinates (array of 2 items, in [-inf, inf], optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.deinterlace_selected_movies()

Process all chosen video inputs to remove interlacing.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

File:

startup/bl_operators/sequencer.py:129

bpy.ops.sequencer.delete(*, delete_data=False)

Remove chosen strips from the sequencer.

Parameters:

delete_data (bool) – Delete Data, Also erase the underlying media after strip deletion (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.disconnect()

Separate chosen strips so they become independently selectable.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.duplicate(*, linked=False)

Reproduce the chosen strips.

Parameters:

linked (bool) – Linked, Clone the strip while referencing the original media (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.duplicate_move(*, `SEQUENCER_OT`_duplicate={}, `TRANSFORM_OT`_seq_slide={})

Reproduce chosen strips and slide them.

Parameters:

- `SEQUENCER_OT`_duplicate (dict[str, Any]) – Duplicate Strips, Copy the chosen strips (optional, bpy.ops.sequencer.duplicate() keyword arguments)
- `TRANSFORM_OT`_seq_slide (dict[str, Any]) – Sequence Slide, Move a clip across the timeline (optional, bpy.ops.transform.seq_slide() keyword arguments)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.duplicate_move_linked(*, `SEQUENCER_OT`_duplicate={}, `TRANSFORM_OT`_seq_slide={})

Reproduce chosen strips without duplicating their media, then slide them.

Parameters:

- `SEQUENCER_OT`_duplicate (dict[str, Any]) – Duplicate Strips, Copy the chosen strips (optional, bpy.ops.sequencer.duplicate() keyword arguments)
- `TRANSFORM_OT`_seq_slide (dict[str, Any]) – Sequence Slide, Move a clip across the timeline (optional, bpy.ops.transform.seq_slide() keyword arguments)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.effect_strip_add(*, type='CROSS', move_strips=True, frame_start=0, length=0, channel=1, replace_sel=True, overlap=False, overlap_shuffle_override=False, skip_locked_or_muted_channels=True, color=(0.0, 0.0, 0.0))

Insert an effect piece into the sequencer; many sit atop existing material.

Parameters:

- type (Literal['CROSS', 'ADD', 'SUBTRACT', '`ALPHA_OVER`', '`ALPHA_UNDER`', '`GAMMA_CROSS`', 'MULTIPLY', 'WIPE', 'GLOW', 'COLOR', 'SPEED', 'MULTICAM', 'ADJUSTMENT', '`GAUSSIAN_BLUR`', 'TEXT', 'COLORMIX']) – Type, Which effect to insert (optional)
  - CROSS
    Crossfade – Transition out of one movie while transition into another.
  - ADD
    Add – Overlay color information from two clips.
  - SUBTRACT
    Subtract – Remove one strip's colors from another.
  - `ALPHA_OVER`
    Alpha Over – Layer alpha channel above other footage.
  - `ALPHA_UNDER`
    Alpha Under – Layer alpha channel below other footage.
  - `GAMMA_CROSS`
    Gamma Crossfade – Transition using color-corrected interpolation.
  - MULTIPLY
    Multiply – Scale color from two clips together.
  - WIPE
    Wipe – Push a cutting line across the image.
  - GLOW
    Glow – Intensify highlights and apply diffusion.
  - COLOR
    Color – Introduce a solid-color strip.
  - SPEED
    Speed – Adjust playback velocity of film clips.
  - MULTICAM
    Multicam Selector – Manage which camera feed is active.
  - ADJUSTMENT
    Adjustment Layer – Use non-permanent image processing.
  - `GAUSSIAN_BLUR`
    Gaussian Blur – Reduce sharpness along horizontal and vertical axes.
  - TEXT
    Text – Introduce a text-based strip.
  - COLORMIX
    Color Mix – Merge two strips via blend operations.
- move_strips (bool) – Move Strips, Automatically initiate mouse-driven translation of strips after insertion (optional)
- frame_start (int) – Start Frame, Where on the timeline the strip begins (in [-inf, inf], optional)
- length (int) – Length, Duration of the piece in frames, or length of each piece if adding multiple (in [-inf, inf], optional)
- channel (int) – Channel, Sequencer track for placement (in [1, 128], optional)
- replace_sel (bool) – Replace Selection, Clear prior selections once the operation finishes (optional)
- overlap (bool) – Allow Overlap, Permit new strips to overlap without correction (optional)
- overlap_shuffle_override (bool) – Override Overlap Shuffle Behavior, Use overlap mode from tool configuration (optional)
- skip_locked_or_muted_channels (bool) – Skip Locked or Muted Channels, Bypass muted or protected tracks when inserting (optional)
- color (mathutils.Color) – Color, Start the piece with this coloration (array of 3 items, in [0, 1], optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]
