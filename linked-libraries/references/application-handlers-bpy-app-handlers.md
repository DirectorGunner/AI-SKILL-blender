# Application Handlers Bpy App Handlers, Console Operators, Ed Operators

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Application Handlers (bpy.app.handlers); Console Operators; Ed Operators.

## Application Handlers (bpy.app.handlers)

### Application Handlers (bpy.app.handlers)
This module contains callback lists.

### Basic Handler Example
The simplest example of adding a handler:
```python
import bpy

def my_handler(scene):
    print("Frame Change", scene.frame_current)

bpy.app.handlers.frame_change_pre.append(my_handler)
```

### Persistent Handler Example
By default, handlers are freed when loading new files; sometimes you want one to keep running across multiple files (for instance when it's part of an add-on). For that, use the bpy.app.handlers.persistent decorator.
```python
import bpy
from bpy.app.handlers import persistent

@persistent
def load_handler(dummy):
    print("Load Handler:", bpy.data.filepath)

bpy.app.handlers.load_post.append(load_handler)
```

### Note on Altering Data
Be careful altering data from handlers. During rendering, the frame_change_pre and frame_change_post handlers run on one thread while the viewport updates on another, so if a handler changes data the viewport reads, Blender can crash. In such cases, lock the interface (Render → Lock Interface or bpy.types.RenderSettings.use_lock_interface) before starting a render. Here's an example of a mesh altered from a handler:
```python
def frame_change_pre(scene):
    # A triangle that shifts in the z direction.
    zshift = scene.frame_current * 0.1
    vertices = [(-1, -1, zshift), (1, -1, zshift), (0, 1, zshift)]
    triangles = [(0, 1, 2)]

    object = bpy.data.objects["The Object"]
    object.data.clear_geometry()
    object.data.from_pydata(vertices, [], triangles)
```

bpy.app.handlers. animation_playback_post
On ending animation playback. Accepts one or two arguments: the scene data-block, and optionally the dependency graph being updated.
Type: list[Callable[[bpy.types.Scene, bpy.types.Depsgraph], None] | Callable[[bpy.types.Scene], None]]

bpy.app.handlers. animation_playback_pre
On starting animation playback. Accepts one or two arguments: the scene data-block, and optionally the dependency graph being updated.
Type: list[Callable[[bpy.types.Scene, bpy.types.Depsgraph], None] | Callable[[bpy.types.Scene], None]]

bpy.app.handlers. annotation_post
On drawing an annotation (after). Accepts two arguments: the annotation data-block and dependency graph.
Type: list[Callable[[bpy.types.GreasePencil, bpy.types.Depsgraph], None]]

bpy.app.handlers. annotation_pre
On drawing an annotation (before). Accepts two arguments: the annotation data-block and dependency graph.
Type: list[Callable[[bpy.types.GreasePencil, bpy.types.Depsgraph], None]]

bpy.app.handlers. blend_import_post
On linking or appending data (after). Accepts one argument: a BlendImportContext.
Type: list[Callable[[bpy.types.BlendImportContext], None]]

bpy.app.handlers. blend_import_pre
On linking or appending data (before). Accepts one argument: a BlendImportContext.
Type: list[Callable[[bpy.types.BlendImportContext], None]]

bpy.app.handlers. composite_cancel
On a compositing background job (cancel). Accepts one argument: the scene data-block.
Type: list[Callable[[bpy.types.Scene], None]]

bpy.app.handlers. composite_post
On a compositing background job (after). Accepts one argument: the scene data-block.
Type: list[Callable[[bpy.types.Scene], None]]

bpy.app.handlers. composite_pre
On a compositing background job (before). Accepts one argument: the scene data-block.
Type: list[Callable[[bpy.types.Scene], None]]

bpy.app.handlers. depsgraph_update_post
On depsgraph update (post). Accepts one or two arguments: the scene data-block, and optionally the dependency graph being updated.
Type: list[Callable[[bpy.types.Scene, bpy.types.Depsgraph], None] | Callable[[bpy.types.Scene], None]]

bpy.app.handlers. depsgraph_update_pre
On depsgraph update (pre). Accepts one or two arguments: the scene data-block, and optionally the dependency graph being updated.
Type: list[Callable[[bpy.types.Scene, bpy.types.Depsgraph], None] | Callable[[bpy.types.Scene], None]]

bpy.app.handlers. exit_pre
Just before Blender shuts down, while all data is still valid. Accepts one boolean argument: True means either a user was working in Blender and exited, or Blender is exiting in a situation that should be treated that way; False means Blender is running in background mode, or is exiting due to failed command-line arguments, etc.
Type: list[Callable[[bool], None]]

bpy.app.handlers. frame_change_post
Called after a frame change for playback and rendering, once the data has been evaluated for the new frame. Accepts one or two arguments: the scene data-block, and optionally the dependency graph being updated.
Type: list[Callable[[bpy.types.Scene, bpy.types.Depsgraph], None] | Callable[[bpy.types.Scene], None]]

bpy.app.handlers. frame_change_pre
Called when a frame change is triggered for playback and rendering, before any data is evaluated for the new frame. This lets you change data and relations (for example, swapping an object to another mesh) for the new frame. Note it isn't meant as a "before the frame changes" event, and the dependency graph isn't available here since data and relations may have been altered and the graph hasn't yet been updated for them. Accepts one or two arguments: the scene data-block, and optionally the dependency graph being updated.
Type: list[Callable[[bpy.types.Scene, bpy.types.Depsgraph], None] | Callable[[bpy.types.Scene], None]]

bpy.app.handlers. load_factory_preferences_post
On loading factory preferences (after).
Type: list[Callable[[], None]]

bpy.app.handlers. load_factory_startup_post
On loading factory startup (after).
Type: list[Callable[[], None]]

bpy.app.handlers. load_post
On loading a new blend file (after). Accepts one argument: the file being loaded, an empty string for the startup-file.
Type: list[Callable[[str], None]]

bpy.app.handlers. load_post_fail
On failure to load a new blend file (after). Accepts one argument: the file being loaded, an empty string for the startup-file.
Type: list[Callable[[str], None]]

bpy.app.handlers. load_pre
On loading a new blend file (before). Accepts one argument: the file being loaded, an empty string for the startup-file.
Type: list[Callable[[str], None]]

bpy.app.handlers. object_bake_cancel
On canceling a bake job; called in the main thread. Accepts one argument: the object data-block being baked.
Type: list[Callable[[bpy.types.Object], None]]

bpy.app.handlers. object_bake_complete
On completing a bake job; called in the main thread. Accepts one argument: the object data-block being baked.
Type: list[Callable[[bpy.types.Object], None]]

bpy.app.handlers. object_bake_pre
Before starting a bake job. Accepts one argument: the object data-block being baked.
Type: list[Callable[[bpy.types.Object], None]]

bpy.app.handlers. redo_post
On loading a redo step (after). Accepts one argument: the scene data-block.
Type: list[Callable[[bpy.types.Scene], None]]

bpy.app.handlers. redo_pre
On loading a redo step (before). Accepts one argument: the scene data-block.
Type: list[Callable[[bpy.types.Scene], None]]

bpy.app.handlers. render_cancel
On canceling a render job. Accepts one argument: the scene data-block being rendered.
Type: list[Callable[[bpy.types.Scene], None]]

bpy.app.handlers. render_complete
On completion of a render job. Accepts one argument: the scene data-block being rendered.
Type: list[Callable[[bpy.types.Scene], None]]

bpy.app.handlers. render_init
On initialization of a render job. Accepts one argument: the scene data-block being rendered.
Type: list[Callable[[bpy.types.Scene], None]]

bpy.app.handlers. render_post
On render (after). Accepts one argument: the scene data-block being rendered.
Type:

list[Callable[[bpy.types.Scene], None]]

bpy.app.handlers. render_pre
On render (before). Accepts one argument: the scene data-block being rendered.
Type: list[Callable[[bpy.types.Scene], None]]

bpy.app.handlers. render_stats
On printing render statistics. Accepts one argument: the render stats (render/saving time, plus, in background mode, the frame and used [peak] memory).
Type: list[Callable[[str], None]]

bpy.app.handlers. render_write
On writing a render frame (directly after the frame is written). Accepts one argument: the scene data-block being rendered.
Type: list[Callable[[bpy.types.Scene], None]]

bpy.app.handlers. save_post
On saving a blend file (after). Accepts one argument: the file being saved, an empty string for the startup-file.
Type: list[Callable[[str], None]]

bpy.app.handlers. save_post_fail
On failure to save a blend file (after). Accepts one argument: the file being saved, an empty string for the startup-file.
Type: list[Callable[[str], None]]

bpy.app.handlers. save_pre
On saving a blend file (before). Accepts one argument: the file being saved, an empty string for the startup-file.
Type: list[Callable[[str], None]]

bpy.app.handlers. translation_update_post
On translation-settings update.
Type: list[Callable[[], None]]

bpy.app.handlers. undo_post
On loading an undo step (after). Accepts one argument: the scene data-block.
Type: list[Callable[[bpy.types.Scene], None]]

bpy.app.handlers. undo_pre
On loading an undo step (before). Accepts one argument: the scene data-block.
Type: list[Callable[[bpy.types.Scene], None]]

bpy.app.handlers. version_update
On ending the versioning code.
Type: list[Callable[[], None]]

bpy.app.handlers. xr_session_start_pre
On starting an xr session (before).
Type: list[Callable[[], None]]

bpy.app.handlers. persistent
A function decorator for callback functions that shouldn't be removed when loading new files.
Type: type

## Console Operators

### Console Operators

bpy.ops.console. autocomplete ( )

Compute the context up to the input point and supply a catalog or complete the name if a single option remains

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/console.py:61

bpy.ops.console. banner ( )

Emit text when the terminal launches

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/console.py:104

bpy.ops.console. clear ( * , scrollback = True , history = False )

Purge message by category

Parameters :

- scrollback ( bool ) – Scrollback, Clear the scrollback history (optional)

- history ( bool ) – History, Clear the command history (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.console. clear_line ( )

Erase the line and commit it to history

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.console. copy ( * , delete = False )

Move highlighted characters to the clipboard

Parameters :

delete ( bool ) – Delete Selection, Whether to delete the selection after copying (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.console. copy_as_script ( )

Duplicate the terminal view for use in a code file

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/console.py:82

bpy.ops.console. delete ( * , type = '`NEXT_CHARACTER`' )

Purge content by position

Parameters :

type ( Literal [ '`NEXT_CHARACTER`' , '`PREVIOUS_CHARACTER`' , '`NEXT_WORD`' , '`PREVIOUS_WORD`' ] ) – Type, Which part of the text to delete (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.console. execute ( * , interactive = False )

Interpret and run the current line as a Python command

Parameters :

interactive ( bool ) – interactive, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/console.py:38

bpy.ops.console. history_append ( * , text = '' , current_character = 0 , remove_duplicates = False )

Append history at cursor position

Parameters :

- text ( str ) – Text, Text to insert at the cursor position (optional, never None)

- current_character ( int ) – Cursor, The index of the cursor (in [0, inf], optional)

- remove_duplicates ( bool ) – Remove Duplicates, Remove duplicate items in the history (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.console. history_cycle ( * , reverse = False )

Traverse through saved commands

Parameters :

reverse ( bool ) – Reverse, Reverse cycle history (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.console. indent ( )

Prepend four spaces at line beginning

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.console. indent_or_autocomplete ( )

Pad highlighted content or fill in automatically

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.console. insert ( * , text = '' )

Deposit content at the input location

Parameters :

text ( str ) – Text, Text to insert at the cursor position (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.console. language ( * , language = '' )

Pick the programming language for this console

Parameters :

language ( str ) – Language, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/console.py:136

bpy.ops.console. move ( * , type = '`LINE_BEGIN`' , select = False )

Displace input location

Parameters :

- type ( Literal [ '`LINE_BEGIN`' , '`LINE_END`' , '`PREVIOUS_CHARACTER`' , '`NEXT_CHARACTER`' , '`PREVIOUS_WORD`' , '`NEXT_WORD`' ] ) – Type, Where to move cursor to (optional)

- select ( bool ) – Select, Whether to select while moving (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.console. paste ( * , selection = False )

Load text from the clipboard

Parameters :

selection ( bool ) – Selection, Paste text selected elsewhere rather than copied (X11/Wayland only) (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.console. scrollback_append ( * , text = '' , type = 'OUTPUT' )

Append terminal content by category

Parameters :

- text ( str ) – Text, Text to insert at the cursor position (optional, never None)

- type ( Literal [ 'OUTPUT' , 'INPUT' , 'INFO' , 'ERROR' ] ) – Type, Console output type (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.console. select_all ( )

Highlight every line

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.console. select_set ( )

Establish the console selection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.console. select_word ( )

Highlight the word at the input location

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.console. unindent ( )

Erase four spaces from line beginning

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## Ed Operators

### Ed Operators

**bpy.ops.ed.flush_edits**( )

Push changes from active editing modes back into the data.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.ed.lib_id_fake_user_toggle**( )

Preserve a data-block in the file even with zero users.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.ed.lib_id_generate_preview**( )

Produce a preview image for the chosen data-block automatically.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.ed.lib_id_generate_preview_from_object**( )

Create a preview by rendering the currently active object.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.ed.lib_id_load_custom_preview**( * , filepath = '' , hide_props_region = True , check_existing = False , filter_blender = False , filter_backup = False , filter_image = True , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 9 , show_multiview = False , use_multiview = False , display_type = 'DEFAULT' , sort_method = '' )

Import an image file to visually represent the data-block.

Parameters:
- filepath ( str ) – File Path, Path to file (optional, never None)
- hide_props_region ( bool ) – Hide Operator Properties, Collapse the region displaying the operator settings (optional)
- check_existing ( bool ) – Check Existing, Check and warn on overwriting existing files (optional)
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
- filemode ( int ) – File Browser Mode, The setting for the file browser mode to load a .blend file, a library or a special file (in [1, 9], optional)
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

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.ed.lib_id_override_editable_toggle**( )

Control whether a library override can be altered.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.ed.lib_id_remove_preview**( )

Delete the preview of a data-block.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.ed.lib_id_unlink**( )

Remove a data-block reference and clear the slot.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.ed.redo**( )

Reapply an action that was undone.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.ed.undo**( )

Reverse the last action.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.ed.undo_history**( * , item = 0 )

Step backward or forward through the undo history to a specific action.

Parameters:
- item ( int ) – Item, (in [0, inf], optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.ed.undo_push**( * , message = 'Add an undo step *function may be moved*' )

Record an undo checkpoint (for internal use).

Parameters:
- message ( str ) – Undo Message, (optional, never None)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.ed.undo_redo**( )

Undo the previous action, then redo it.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]
