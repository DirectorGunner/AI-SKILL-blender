# Cycles Operators, Dpaint Operators, File Operators

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Cycles Operators; Dpaint Operators; File Operators.

## Cycles Operators

### Cycles Operators

**bpy.ops.cycles.denoise_animation**( * , input_filepath = '' , output_filepath = '' )

Use the denoising algorithm to clean up a rendered animation. Requires denoising data passes saved as OpenEXR.

Parameters:
- input_filepath ( str ) – Input Filepath, Image file path for denoising. If blank, uses the render output path and frame range (optional, never None)
- output_filepath ( str ) – Output Filepath, If blank, denoises in place (optional, never None)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

File: addons_core/cycles/operators.py:49

**bpy.ops.cycles.merge_images**( * , input_filepath1 = '' , input_filepath2 = '' , output_filepath = '' )

Merge OpenEXR files rendered at different sample counts into a single image with lower noise.

Parameters:
- input_filepath1 ( str ) – Input Filepath, Image file path to merge (optional, never None)
- input_filepath2 ( str ) – Input Filepath, Image file path to merge (optional, never None)
- output_filepath ( str ) – Output Filepath, Image file path for the merged result (optional, never None)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

File: addons_core/cycles/operators.py:137

**bpy.ops.cycles.use_shading_nodes**( )

Activate node-based materials on a light.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

File: addons_core/cycles/operators.py:23

## Dpaint Operators

### Dpaint Operators

**bpy.ops.dpaint.bake**( )

Render the dynamic paint sequence to texture.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.dpaint.output_toggle**( * , output = 'A' )

Add or take away a Dynamic Paint data layer.

Parameters:
- output ( Literal [ 'A' , 'B' ] ) – Output Toggle, (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.dpaint.surface_slot_add**( )

Create a new Dynamic Paint surface.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.dpaint.surface_slot_remove**( )

Delete the current surface slot.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.dpaint.type_toggle**( * , type = 'CANVAS' )

Switch whether a given type is on or off.

Parameters:
- type (Literal[Prop Dynamicpaint Type Items]) – Type, (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

## File Operators

### File Operators

bpy.ops.file.autopack_toggle()

Embed all linked media directly into the .blend

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.bookmark_add()

Place a marker at the selected or active directory

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.bookmark_cleanup()

Wipe out all defunct bookmarks

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.bookmark_delete(*, index=-1)

Trash the current bookmark

Parameters:

index (int) – Index, (in [-1, 20000], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.bookmark_move(*, direction='TOP')

Shift the chosen bookmark up or down the roster

Parameters:

direction (Literal['TOP', 'UP', 'DOWN', 'BOTTOM']) – Direction, Orientation to migrate the chosen bookmark (optional)

- TOP
Top – Top of the list.

- UP
Up.

- DOWN
Down.

- BOTTOM
Bottom – Bottom of the list.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.cancel()

Halt file work

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.delete()

Move marked items to the trash or recycle bin

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.directory_new(*, directory='', open=False, confirm=True)

Construct a new folder

Parameters:

- directory (str) – Directory, Label for the folder being made (optional, never None)
- open (bool) – Open, Bring up the folder (optional)
- confirm (bool) – Confirm, Show confirmation request (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.edit_directory_path()

Begin updating the directory box

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.execute()

Run the marked file

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.external_operation(*, operation='OPEN')

Perform an action on a document or directory outside of Blender

Parameters:

operation (Literal['OPEN', '`FOLDER_OPEN`', 'EDIT', 'NEW', 'FIND', 'SHOW', 'PLAY', 'BROWSE', 'PREVIEW', 'PRINT', 'INSTALL', 'RUNAS', 'PROPERTIES', '`FOLDER_FIND`', 'CMD']) – Operation, Work to execute with the marked document or route (optional)

- OPEN
Open – Launch the document.

- `FOLDER_OPEN`
Open Folder – Launch the folder.

- EDIT
Edit – Modify the document.

- NEW
New – Make a fresh document of this form.

- FIND
Find File – Seek documents of this form.

- SHOW
Show – Exhibit this document.

- PLAY
Play – Execute this document.

- BROWSE
Browse – Look through this document.

- PREVIEW
Preview – Peek at this document.

- PRINT
Print – Output this document.

- INSTALL
Install – Set up this document.

- RUNAS
Run As User – Run as specific user.

- PROPERTIES
Properties – Reveal system traits for this element.

- `FOLDER_FIND`
Find in Folder – Hunt for things in this folder.

- CMD
Command Prompt Here – Launch a shell session here.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.filenum(*, increment=1)

Boost the digit inside the file label

Parameters:

increment (int) – Increment, (in [-100, 100], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.filepath_drop(*, filepath='Path')

Undocumented, consider contributing.

Parameters:

filepath (str) – (optional, never None)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.find_missing_files(*, find_all=False, directory='', hide_props_region=True, check_existing=False, filter_blender=False, filter_backup=False, filter_image=False, filter_movie=False, filter_python=False, filter_font=False, filter_sound=False, filter_text=False, filter_archive=False, filter_btx=False, filter_alembic=False, filter_usd=False, filter_obj=False, filter_volume=False, filter_folder=False, filter_blenlib=False, filemode=9, display_type='DEFAULT', sort_method='')

Hunt for absent linked media

Parameters:

- find_all (bool) – Find All, Seek everything in the hunt scope, not simply what's gone missing (optional)
- directory (str) – Directory, Location containing the source material (optional, never None)
- hide_props_region (bool) – Hide Operator Properties, Fold the pane showing the task configuration (optional)
- check_existing (bool) – Check Existing, Inspect and notify if over-writing current materials (optional)
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
- filemode (int) – File Browser Mode, The setting for the file browser mode to load a .blend file, a library or a special file (in [1, 9], optional)

- display_type (Literal['DEFAULT', '`LIST_VERTICAL`', '`LIST_HORIZONTAL`', 'THUMBNAIL']) – Display Type, (optional)

- DEFAULT
Default – Automatically determine display type for files.

- `LIST_VERTICAL`
Short List – Display files as short list.

- `LIST_HORIZONTAL`
Long List – Display files as a detailed list.

- THUMBNAIL
Thumbnails – Display files as thumbnails.

- sort_method (str) – File sorting mode, (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.hidedot()

Flip concealment of hidden dot-style files

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.highlight()

Mark the chosen file(s)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.make_paths_absolute()

Transform all pointers to external resources into complete routes

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.make_paths_relative()

Transform all pointers to external resources into routes relative to the live .blend

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.mouse_execute()

Carry out the active file action for the item beneath your cursor (e.g. load)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.next()

Shift to the succeeding folder

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.pack_all()

Embed all energized linked media into the .blend

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.pack_libraries()

Import all information entities sourced from external .blend records into the present .blend. Imported links stay maintained so the source information can be un-embedded anew

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.parent()

Shift to the containing folder

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.previous()

Shift to the preceding folder

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.refresh()

Update the file catalog

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.rename()

Change the label of a document or folder

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.report_missing_files()

Provide info on all absent linked media

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.reset_recent()

Clear the roster of previously used documents

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.select(*, wait_to_deselect_others=False, use_select_on_click=False, mouse_x=0, mouse_y=0, extend=False, fill=False, open=True, deselect_all=False, only_activate_if_selected=False, pass_through=False)

Take action on clicks to mark and focus items

Parameters:

- wait_to_deselect_others (bool) – Wait to Deselect Others, (optional)
- use_select_on_click (bool) – Act on Click, Instead of marking on click-down, hold up to detect drag. Rather mark on release (optional)
- mouse_x (int) – Mouse X, (in [-inf, inf], optional)
- mouse_y (int) – Mouse Y, (in [-inf, inf], optional)
- extend (bool) – Extend, Grow the roster in lieu of wiping everything (optional)
- fill (bool) – Fill, Mark everything from the previous pick to here (optional)
- open (bool) – Open, Bring up a folder when picking it (optional)
- deselect_all (bool) – Deselect On Nothing, Wipe all choices when nothing sits at the cursor (optional)
- only_activate_if_selected (bool) – Only Activate if Selected, Don't tweak picks if the item at the cursor is picked already, turn on it (optional)
- pass_through (bool) – Pass Through, Permit further input processing upon success (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.select_all(*, action='TOGGLE')

Mark or unmark all items

Parameters:

action (Literal['TOGGLE', 'SELECT', 'DESELECT', 'INVERT']) – Action, Choice work to carry out (optional)

- TOGGLE
Toggle – Swap selection for every part.

- SELECT
Select – Mark every part.

- DESELECT
Deselect – Unmark every part.

- INVERT
Invert – Flip which are marked.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.select_bookmark(*, dir='')

Focus a recorded folder

Parameters:

dir (str) – Directory, (optional, never None)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.select_box(*, xmin=0, xmax=0, ymin=0, ymax=0, wait_for_input=True, mode='SET')

Mark/focus the item(s) enclosed by the perimeter

Parameters:

- xmin (int) – X Min, (in [-inf, inf], optional)
- xmax (int) – X Max, (in [-inf, inf], optional)
- ymin (int) – Y Min, (in [-inf, inf], optional)
- ymax (int) – Y Max, (in [-inf, inf], optional)
- wait_for_input (bool) – Wait for Input, (optional)
- mode (Literal['SET', 'ADD', 'SUB']) – Mode, (optional)

- SET
Set – Set a new selection.

- ADD
Extend – Extend existing selection.

- SUB
Subtract – Subtract existing selection.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.select_walk(*, direction='UP', extend=False, fill=False)

Pick/un-pick items by traversing via keyboard

Parameters:

- direction (Literal['UP', 'DOWN', 'LEFT', 'RIGHT']) – Walk Direction, Step in this heading (optional)
- extend (bool) – Extend, Grow the roster in lieu of wiping everything (optional)

- fill (bool) – Fill, Mark everything from the preceding pick to here (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.smoothscroll()

Glide in order to bring the live document into sight

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.sort_column_ui_context()

Switch arrangement to employ column beneath cursor

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.start_filter()

Start composing filtration wording

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.unpack_all(*, method='`USE_LOCAL`')

Extract every document packed into this .blend back to standalone types

Parameters:

method (Literal['`USE_LOCAL`', '`WRITE_LOCAL`', '`USE_ORIGINAL`', '`WRITE_ORIGINAL`', 'KEEP', 'REMOVE']) – Method, How to extract (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.unpack_item(*, method='`USE_LOCAL`', id_name='', id_type=19785)

Retrieve this document to a standalone type

Parameters:

- method (Literal['`USE_LOCAL`', '`WRITE_LOCAL`', '`USE_ORIGINAL`', '`WRITE_ORIGINAL`']) – Method, How to retrieve (optional)
- id_name (str) – ID Name, Label of the information block to retrieve (optional, never None)
- id_type (int) – ID Type, Code type of the information block (in [0, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.unpack_libraries()

Send every packed referenced information block to its stored roots

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.file.view_selected()

Shift the view so the picked items sit on display

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]
