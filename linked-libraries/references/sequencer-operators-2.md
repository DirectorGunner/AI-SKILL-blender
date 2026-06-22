# Sequencer Operators (part 2)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

bpy.ops.sequencer.enable_proxies(*, proxy_25=False, proxy_50=False, proxy_75=False, proxy_100=False, overwrite=False)

Activate lower-resolution proxies on chosen movie and image material.

Parameters:

- proxy_25 (bool) – 25%, (optional)
- proxy_50 (bool) – 50%, (optional)
- proxy_75 (bool) – 75%, (optional)
- proxy_100 (bool) – 100%, (optional)
- overwrite (bool) – Overwrite, (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.export_subtitles(*, filepath='', hide_props_region=True, check_existing=True, filter_blender=False, filter_backup=False, filter_image=False, filter_movie=False, filter_python=False, filter_font=False, filter_sound=False, filter_text=False, filter_archive=False, filter_btx=False, filter_alembic=False, filter_usd=False, filter_obj=False, filter_volume=False, filter_folder=True, filter_blenlib=False, filemode=8, display_type='DEFAULT', sort_method='')

Write a .srt document using captions from text pieces.

Parameters:

- filepath (str) – File Path, Source to the file (optional, never None)
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

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.fades_add(*, duration_seconds=1.0, type='`IN_OUT`')

Create or modify gradual level changes for audio or visual material.

Parameters:

- duration_seconds (float) – Fade Duration, Time span of the fade in seconds (in [0.01, inf], optional)
- type (Literal['`IN_OUT`', 'IN', 'OUT', '`CURSOR_FROM`', '`CURSOR_TO`']) – Fade Type, Direction and timing: entry, exit, both entry and exit, ending at, or beginning from the current frame. Defaults to both entry and exit (optional)
  - `IN_OUT`
    Fade In and Out – Gradually increase then decrease levels.
  - IN
    Fade In – Gradually increase levels.
  - OUT
    Fade Out – Gradually decrease levels.
  - `CURSOR_FROM`
    From Current Frame – Gradually decrease from now until the end of overlapping material.
  - `CURSOR_TO`
    To Current Frame – Gradually increase from material start until now.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

File:

startup/bl_operators/sequencer.py:216

bpy.ops.sequencer.fades_clear()

Remove gradual level changes from chosen strips.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

File:

startup/bl_operators/sequencer.py:152

bpy.ops.sequencer.gap_insert(*, frames=10)

Create empty space at the current position to the right, disregarding choice or lock state.

Parameters:

frames (int) – Frames, Duration to insert following the current strip (in [0, inf], optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.gap_remove(*, all=False)

Fill empty space at the current position from the right, disregarding choice or lock state.

Parameters:

all (bool) – All Gaps, Remove all vacant areas to the right of the current position (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.image_strip_add(*, directory='', files=None, check_existing=False, filter_blender=False, filter_backup=False, filter_image=True, filter_movie=False, filter_python=False, filter_font=False, filter_sound=False, filter_text=False, filter_archive=False, filter_btx=False, filter_alembic=False, filter_usd=False, filter_obj=False, filter_volume=False, filter_folder=True, filter_blenlib=False, filemode=9, relative_path=True, show_multiview=False, use_multiview=False, display_type='DEFAULT', sort_method='', move_strips=True, frame_start=0, length=0, channel=1, replace_sel=True, overlap=False, overlap_shuffle_override=False, skip_locked_or_muted_channels=True, fit_method='FIT', set_view_transform=True, image_import_type='DETECT', use_sequence_detection=True, use_placeholders=False)

Insert a picture or sequence of pictures into the sequencer.

Parameters:

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
- show_multiview (bool) – Enable Multi-View, (optional)
- use_multiview (bool) – Use Multi-View, (optional)
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
- length (int) – Length, Duration of the piece in frames, or length of each piece if adding multiple (in [-inf, inf], optional)
- channel (int) – Channel, Sequencer track for placement (in [1, 128], optional)
- replace_sel (bool) – Replace Selection, Clear prior selections once the operation finishes (optional)
- overlap (bool) – Allow Overlap, Permit new strips to overlap without correction (optional)
- overlap_shuffle_override (bool) – Override Overlap Shuffle Behavior, Use overlap mode from tool configuration (optional)
- skip_locked_or_muted_channels (bool) – Skip Locked or Muted Channels, Bypass muted or protected tracks when inserting (optional)
- fit_method (Literal[Strip Scale Method Items]) – Fit Method, How to scale the image within the viewport (optional)
- set_view_transform (bool) – Set View Transform, Apply appropriate color transform based on media profile (optional)
- image_import_type (Literal['DETECT', 'SEQUENCE', 'INDIVIDUAL']) – Import As, How to handle the chosen pictures (optional)
  - DETECT
    Auto Detect – Add images as separate pieces, unless file naming indicates a numbered sequence, in which case combine into a single picture sequence.
  - SEQUENCE
    Image Sequence – Combine all chosen images into a single picture sequence. The sequence of images doesn't need to match Blender's numbering scheme, so placeholders can't be determined.
  - INDIVIDUAL
    Individual Images – Add each chosen image as a separate piece.
- use_sequence_detection (bool) – Detect Sequences, Automatically recognize picture sequences in chosen files (based on file labels) (optional)
- use_placeholders (bool) – Use Placeholders, Generate placeholder images for missing sequence frames (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.images_separate(*, length=1)

On picture sequence pieces, break into individual picture strips.

Parameters:

length (int) – Length, Duration of each picture (in [1, inf], optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.lock()

Protect strips from being moved.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.mask_strip_add(*, move_strips=True, frame_start=0, channel=1, replace_sel=True, overlap=False, overlap_shuffle_override=False, skip_locked_or_muted_channels=True, mask='')

Insert a mask piece into the sequencer.

Parameters:

- move_strips (bool) – Move Strips, Automatically initiate mouse-driven translation of strips after insertion (optional)
- frame_start (int) – Start Frame, Where on the timeline the strip begins (in [-inf, inf], optional)
- channel (int) – Channel, Sequencer track for placement (in [1, 128], optional)
- replace_sel (bool) – Replace Selection, Clear prior selections once the operation finishes (optional)
- overlap (bool) – Allow Overlap, Permit new strips to overlap without correction (optional)
- overlap_shuffle_override (bool) – Override Overlap Shuffle Behavior, Use overlap mode from tool configuration (optional)
- skip_locked_or_muted_channels (bool) – Skip Locked or Muted Channels, Bypass muted or protected tracks when inserting (optional)
- mask (str) – Mask, (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.meta_make()

Consolidate chosen pieces into a container-strip.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.meta_separate()

Extract the pieces from a container-strip back to the sequencer.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.meta_toggle()

Open or close a container-strip to edit enclosed pieces.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.movie_strip_add(*, filepath='', directory='', files=None, check_existing=False, filter_blender=False, filter_backup=False, filter_image=False, filter_movie=True, filter_python=False, filter_font=False, filter_sound=False, filter_text=False, filter_archive=False, filter_btx=False, filter_alembic=False, filter_usd=False, filter_obj=False, filter_volume=False, filter_folder=True, filter_blenlib=False, filemode=9, relative_path=True, show_multiview=False, use_multiview=False, display_type='DEFAULT', sort_method='', move_strips=True, frame_start=0, channel=1, replace_sel=True, overlap=False, overlap_shuffle_override=False, skip_locked_or_muted_channels=True, fit_method='FIT', set_view_transform=True, adjust_playback_rate=True, sound=True, use_framerate=True)

Insert a movie piece into the sequencer.

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
- show_multiview (bool) – Enable Multi-View, (optional)
- use_multiview (bool) – Use Multi-View, (optional)
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
- fit_method (Literal[Strip Scale Method Items]) – Fit Method, How to scale the image within the viewport (optional)
- set_view_transform (bool) – Set View Transform, Apply appropriate color transform based on media profile (optional)
- adjust_playback_rate (bool) – Adjust Playback Rate, Keep consistent playback speed regardless of scene FPS (optional)
- sound (bool) – Sound, Include audio track from the movie (optional)
- use_framerate (bool) – Set Scene Frame Rate, Match the scene's frame rate to the movie's frame rate (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.movieclip_strip_add(*, move_strips=True, frame_start=0, channel=1, replace_sel=True, overlap=False, overlap_shuffle_override=False, skip_locked_or_muted_channels=True, clip='')

Insert a motion-capture or tracking piece into the sequencer.

Parameters:

- move_strips (bool) – Move Strips, Automatically initiate mouse-driven translation of strips after insertion (optional)
- frame_start (int) – Start Frame, Where on the timeline the strip begins (in [-inf, inf], optional)
- channel (int) – Channel, Sequencer track for placement (in [1, 128], optional)
- replace_sel (bool) – Replace Selection, Clear prior selections once the operation finishes (optional)
- overlap (bool) – Allow Overlap, Permit new strips to overlap without correction (optional)
- overlap_shuffle_override (bool) – Override Overlap Shuffle Behavior, Use overlap mode from tool configuration (optional)
- skip_locked_or_muted_channels (bool) – Skip Locked or Muted Channels, Bypass muted or protected tracks when inserting (optional)
- clip (str) – Clip, (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.mute(*, unselected=False)

Toggle sound on (un)chosen pieces.

Parameters:

unselected (bool) – Unselected, Toggle sound on unselected rather than chosen pieces (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.offset_clear()

Reset content starting and ending points from the timeline positions.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.paste(*, keep_offset=False, x=0, y=0)

Place pieces from the temporary buffer into the timeline.

Parameters:

- keep_offset (bool) – Keep Offset, Maintain strip offset relative to the current position when pasting (optional)
- x (int) – X, (in [-inf, inf], optional)
- y (int) – Y, (in [-inf, inf], optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.preview_duplicate_move(*, `SEQUENCER_OT`_duplicate={}, `TRANSFORM_OT`_translate={})

Reproduce chosen strips in the preview window and slide them.

Parameters:

- `SEQUENCER_OT`_duplicate (dict[str, Any]) – Duplicate Strips, Copy the chosen strips (optional, bpy.ops.sequencer.duplicate() keyword arguments)
- `TRANSFORM_OT`_translate (dict[str, Any]) – Move, Translate chosen items (optional, bpy.ops.transform.translate() keyword arguments)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.preview_duplicate_move_linked(*, `SEQUENCER_OT`_duplicate={}, `TRANSFORM_OT`_translate={})

Reproduce chosen strips in the preview window without duplicating their media, then slide them.

Parameters:

- `SEQUENCER_OT`_duplicate (dict[str, Any]) – Duplicate Strips, Copy the chosen strips (optional, bpy.ops.sequencer.duplicate() keyword arguments)
- `TRANSFORM_OT`_translate (dict[str, Any]) – Move, Translate chosen items (optional, bpy.ops.transform.translate() keyword arguments)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.reassign_inputs()

Remap the input sources for an effect piece.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.rebuild_proxy()

Regenerate all chosen lower-resolution versions and time information.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.refresh_all()

Reload the sequencer window.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.reload(*, adjust_length=False)

Refresh pieces in the sequencer.

Parameters:

adjust_length (bool) – Adjust Length, Match piece duration to actual media length (optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.rename_channel()

Rename a sequencer track.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.rendersize()

Establish output dimensions and aspect from chosen piece.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.retiming_add_freeze_frame_slide(*, `SEQUENCER_OT`_retiming_freeze_frame_add={}, `TRANSFORM_OT`_seq_slide={})

Generate held frame and slide it.

Parameters:

- `SEQUENCER_OT`_retiming_freeze_frame_add (dict[str, Any]) – Add Freeze Frame, Generate held frame (optional, bpy.ops.sequencer.retiming_freeze_frame_add() keyword arguments)
- `TRANSFORM_OT`_seq_slide (dict[str, Any]) – Sequence Slide, Move a clip across the timeline (optional, bpy.ops.transform.seq_slide() keyword arguments)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.retiming_add_transition_slide(*, `SEQUENCER_OT`_retiming_transition_add={}, `TRANSFORM_OT`_seq_slide={})

Create smooth interpolation between 2 speed-adjusted sections and adjust its period.

Parameters:

- `SEQUENCER_OT`_retiming_transition_add (dict[str, Any]) – Add Speed Transition, Create smooth interpolation between 2 speed-adjusted sections (optional, bpy.ops.sequencer.retiming_transition_add() keyword arguments)
- `TRANSFORM_OT`_seq_slide (dict[str, Any]) – Sequence Slide, Move a clip across the timeline (optional, bpy.ops.transform.seq_slide() keyword arguments)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.retiming_freeze_frame_add(*, duration=0)

Generate held frame.

Parameters:

duration (int) – Duration, Period of held frame region (in [0, inf], optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.retiming_key_add(*, timeline_frame=0)

Generate speed-adjustment control point.

Parameters:

timeline_frame (int) – Timeline Frame, Position where control point will be added (in [0, inf], optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.retiming_key_delete()

Remove chosen speed-adjustment control points from the sequencer.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.retiming_reset()

Return a piece to its original playback velocity.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.retiming_segment_speed_set(*, speed=100.0)

Establish velocity for a speed-adjusted region.

Parameters:

speed (float) – Speed, Fresh velocity for speed-adjusted region (in [0.001, inf], optional)

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.sequencer.retiming_show()

Display speed-adjustment control points in chosen pieces.

Returns:

Operation result.

Return type:

set[Literal[Operator Return Items]]
