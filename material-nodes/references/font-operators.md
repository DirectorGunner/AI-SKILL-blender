# Font Operators

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Font Operators

bpy.ops.font.case_set(*, case='LOWER')

Set character form

Parameters:

case (Literal['LOWER', 'UPPER']) – Case, Reduced or raised form (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.case_toggle()

Flip character form

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.change_character(*, delta=1)

Shift character value

Parameters:

delta (int) – Delta, Sum to rise or fall the character value with (in [-255, 255], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.change_spacing(*, delta=1.0)

Shift letter width

Parameters:

delta (float) – Delta, Sum to fall or climb the spacing amount with (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.delete(*, type='`PREVIOUS_CHARACTER`')

Wipe words by location of the caret

Parameters:

type (Literal['`NEXT_CHARACTER`', '`PREVIOUS_CHARACTER`', '`NEXT_WORD`', '`PREVIOUS_WORD`', 'SELECTION', '`NEXT_OR_SELECTION`', '`PREVIOUS_OR_SELECTION`']) – Type, Which text segment to wipe (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.line_break()

Put a line split at caret location

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.move(*, type='`LINE_BEGIN`')

Shift caret to a location category

Parameters:

type (Literal['`LINE_BEGIN`', '`LINE_END`', '`TEXT_BEGIN`', '`TEXT_END`', '`PREVIOUS_CHARACTER`', '`NEXT_CHARACTER`', '`PREVIOUS_WORD`', '`NEXT_WORD`', '`PREVIOUS_LINE`', '`NEXT_LINE`', '`PREVIOUS_PAGE`', '`NEXT_PAGE`']) – Type, Where to place caret (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.move_select(*, type='`LINE_BEGIN`')

Move the caret while building a region

Parameters:

type (Literal['`LINE_BEGIN`', '`LINE_END`', '`TEXT_BEGIN`', '`TEXT_END`', '`PREVIOUS_CHARACTER`', '`NEXT_CHARACTER`', '`PREVIOUS_WORD`', '`NEXT_WORD`', '`PREVIOUS_LINE`', '`NEXT_LINE`', '`PREVIOUS_PAGE`', '`NEXT_PAGE`']) – Type, Where to place caret, to create a region (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.open(*, filepath='', hide_props_region=True, check_existing=False, filter_blender=False, filter_backup=False, filter_image=False, filter_movie=False, filter_python=False, filter_font=True, filter_sound=False, filter_text=False, filter_archive=False, filter_btx=False, filter_alembic=False, filter_usd=False, filter_obj=False, filter_volume=False, filter_folder=True, filter_blenlib=False, filemode=9, relative_path=True, display_type='THUMBNAIL', sort_method='')

Bring in a new character set from a source

Parameters:

- filepath (str) – File Path, Course to source (optional, never None)
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
- relative_path (bool) – Relative Path, Aim for the source as associated with the blend source (optional)
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

bpy.ops.font.select_all()

Mark every letter

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.select_word()

Mark the term under the caret

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.selection_set()

Put caret mark boundary

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.style_set(*, style='BOLD', clear=False)

Set character layout

Parameters:

- style (Literal['BOLD', 'ITALIC', 'UNDERLINE', '`SMALL_CAPS`']) – Style, Form to put the pick to (optional)
- clear (bool) – Clear, Drop form in lieu of putting it (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.style_toggle(*, style='BOLD')

Flip character layout

Parameters:

style (Literal['BOLD', 'ITALIC', 'UNDERLINE', '`SMALL_CAPS`']) – Style, Form to put the pick to (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.text_copy()

Deposit the highlighted text to the paste bin

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.text_cut()

Move the highlighted text to the paste bin

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.text_insert(*, text='', accent=False)

Push text at caret spot

Parameters:

- text (str) – Text, Wording to push at the caret site (optional, never None)
- accent (bool) – Accent Mode, The subsequent keystroke will cross through the prior, for rare sign entry (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.text_insert_unicode()

Put in Unicode Symbol

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.text_paste(*, selection=False)

Restore wording from the paste bin

Parameters:

selection (bool) – Selection, Paste wording chosen elsewhere somewhat than saved (X11/Wayland exclusively) (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.text_paste_from_file(*, filepath='', hide_props_region=True, check_existing=False, filter_blender=False, filter_backup=False, filter_image=False, filter_movie=False, filter_python=False, filter_font=False, filter_sound=False, filter_text=True, filter_archive=False, filter_btx=False, filter_alembic=False, filter_usd=False, filter_obj=False, filter_volume=False, filter_folder=True, filter_blenlib=False, filemode=9, display_type='DEFAULT', sort_method='')

Restore material from a record

Parameters:

- filepath (str) – File Path, Course to source (optional, never None)
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

bpy.ops.font.textbox_add()

Insert a blank text receptacle

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.textbox_remove(*, index=0)

Erase the text receptacle

Parameters:

index (int) – Index, The active text receptacle (in [0, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.font.unlink()

Sever the lively character set collection

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]
