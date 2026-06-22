# Wm Operators (part 6)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. read_factory_userpref ( * , use_factory_startup_app_template_only = False ) 

Initializes factory-default settings. To preserve changes to preferences, use "Save Preferences"

Parameters :

use_factory_startup_app_template_only ( bool ) – Factory Startup App-Template Only, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. read_history ( ) 

Updates history and bookmarks

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. read_homefile ( * , filepath = '' , load_ui = True , use_splash = False , use_factory_startup = False , use_factory_startup_app_template_only = False , app_template = 'Template' , use_empty = False ) 

Reads the initial file

Parameters :

- filepath ( str ) – File Path, Location of an alternate initial file (optional, never None)

- load_ui ( bool ) – Load UI, Include user interface layout from the .blend file (optional)

- use_splash ( bool ) – Splash, (optional)

- use_factory_startup ( bool ) – Factory Startup, Read the initial ('factory startup') blend file. This is separate from the normal start-up file that users can store (optional)

- use_factory_startup_app_template_only ( bool ) – Factory Startup App-Template Only, (optional)

- app_template ( str ) – (optional, never None)

- use_empty ( bool ) – Empty, On completion, erase everything except scenes, windows, and workspaces. Permits loading the startup file with its scene structure and window arrangement preserved, minus objects, materials, animations, … (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. read_userpref ( ) 

Restores the previously-saved settings

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. recover_auto_save ( * , filepath = '' , hide_props_region = True , check_existing = False , filter_blender = True , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = False , filter_blenlib = False , filemode = 8 , display_type = '`LIST_VERTICAL`' , sort_method = '' , use_scripts = False ) 

Loads an automatically-preserved file to retrieve it

Parameters :

- filepath ( str ) – File Path, Path to file (optional, never None)

- hide_props_region ( bool ) – Hide Operator Properties, Minimize the panel containing operator configuration (optional)

- check_existing ( bool ) – Check Existing, Verifies and alerts when about to overwrite current files (optional)

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

- use_scripts ( bool ) – Trusted Source, Permit .blend file to run scripts on startup; default sourced from system configuration (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. recover_last_session ( * , use_scripts = False ) 

Restores the most recent closed file ("quit.blend")

Parameters :

use_scripts ( bool ) – Trusted Source, Permit .blend file to run scripts on startup; default sourced from system configuration (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. redraw_timer ( * , type = 'DRAW' , iterations = 10 , time_limit = 0.0 ) 

Executes a simple redraw timer to measure interface refresh velocity

Parameters :

- type ( Literal [ 'DRAW' , '`DRAW_SWAP`' , '`DRAW_WIN`' , '`DRAW_WIN_SWAP`' , '`ANIM_STEP`' , '`ANIM_PLAY`' , 'UNDO' ] ) – Type, (optional)

- DRAW
Draw Region – Draw region.

- `DRAW_SWAP`
Draw Region & Swap – Draw region and swap.

- `DRAW_WIN`
Draw Window – Draw window.

- `DRAW_WIN_SWAP`
Draw Window & Swap – Draw window and swap.

- `ANIM_STEP`
Animation Step – Animation steps.

- `ANIM_PLAY`
Animation Play – Animation playback.

- UNDO
Undo/Redo – Undo and redo.

- iterations ( int ) – Iterations, How many times to redraw (in [1, inf], optional)

- time_limit ( float ) – Time Limit, Duration to run the test for (replaces iterations) (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. revert_mainfile ( * , use_scripts = False ) 

Restarts from the saved version

Parameters :

use_scripts ( bool ) – Trusted Source, Permit .blend file to run scripts on startup; default sourced from system configuration (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. save_as_mainfile ( * , filepath = '' , hide_props_region = True , check_existing = True , filter_blender = True , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , compress = False , relative_remap = True , copy = False )

Stores the current file at a new location

Parameters :

- filepath ( str ) – File Path, Path to file (optional, never None)

- hide_props_region ( bool ) – Hide Operator Properties, Minimize the panel containing operator configuration (optional)

- check_existing ( bool ) – Check Existing, Verifies and alerts when about to overwrite current files (optional)

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

- compress ( bool ) – Compress, Saves using compression in .blend file (optional)

- relative_remap ( bool ) – Remap Relative, Adjusts relative paths when outputting to a different location (optional)

- copy ( bool ) – Save Copy, Preserves the current working state but leaves the saved file as inactive (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. save_homefile ( ) 

Designates the current file as the initial startup file

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. save_mainfile ( * , filepath = '' , hide_props_region = True , check_existing = True , filter_blender = True , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , compress = False , relative_remap = False , exit = False , incremental = False ) 

Persists the current Blender file

Parameters :

- filepath ( str ) – File Path, Path to file (optional, never None)

- hide_props_region ( bool ) – Hide Operator Properties, Minimize the panel containing operator configuration (optional)

- check_existing ( bool ) – Check Existing, Verifies and alerts when about to overwrite current files (optional)

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

- compress ( bool ) – Compress, Saves using compression in .blend file (optional)

- relative_remap ( bool ) – Remap Relative, Adjusts relative paths when outputting to a different location (optional)

- exit ( bool ) – Exit, Exit Blender after saving (optional)

- incremental ( bool ) – Incremental, Saves the current file with a numerically-incremented name that avoids overwriting existing files (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. save_userpref ( ) 

Establishes the current preferences as default

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. search_menu ( ) 

Displays a popup to search across all menus in the current context

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. search_operator ( ) 

Displays a popup to search across all operators in current context

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. search_single_menu ( * , menu_idname = '' , initial_query = '' )

Displays a popup to search within a specific menu in current context

Parameters :

- menu_idname ( str ) – Menu Name, Menu to search in (optional, never None)

- initial_query ( str ) – Initial Query, Query to insert into the search box (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. set_stereo_3d ( * , display_mode = 'ANAGLYPH' , anaglyph_type = '`RED_CYAN`' , interlace_type = '`ROW_INTERLEAVED`' , use_interlace_swap = False , use_sidebyside_crosseyed = False ) 

Switches 3D stereo capability for the current window (or adjusts the display technique)

Parameters :

- display_mode (Literal[Stereo3D Display Items]) – Display Mode, (optional)

- anaglyph_type (Literal[Stereo3D Anaglyph Type Items]) – Anaglyph Type, (optional)

- interlace_type (Literal[Stereo3D Interlace Type Items]) – Interlace Type, (optional)

- use_interlace_swap ( bool ) – Swap Left/Right, Exchanges left and right stereo signals (optional)

- use_sidebyside_crosseyed ( bool ) – Cross-Eyed, Left eye sees right image and vice versa (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. set_working_color_space ( * , convert_colors = True , working_space = '' ) 

Updates the color space used throughout this file

Parameters :

- convert_colors ( bool ) – Convert Colors in All Data-blocks, Updates colors in all data-blocks to the new space (optional)

- working_space ( str ) – Working Space, Color space to select (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. splash ( ) 

Displays the splash screen containing release details

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. splash_about ( ) 

Shows a window with facts about Blender

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. stl_export ( * , filepath = '' , check_existing = True , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , ascii_format = False , use_batch = False , export_selected_objects = False , collection = '' , global_scale = 1.0 , use_scene_unit = False , forward_axis = 'Y' , up_axis = 'Z' , apply_modifiers = True , filter_glob = '*.stl' ) 

Exports the scene to an STL file

Parameters :

- filepath ( str ) – File Path, Path to file (optional, never None)

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

- ascii_format ( bool ) – ASCII Format, Output in text-based format; otherwise uses binary (optional)

- use_batch ( bool ) – Batch Export, Write each object to its own file (optional)

- export_selected_objects ( bool ) – Export Selected Objects, Restrict export to currently-selected objects only (optional)

- collection ( str ) – Source Collection, Write only objects from this collection and its children (optional, never None)

- global_scale ( float ) – Scale, (in [1e-06, 1e+06], optional)

- use_scene_unit ( bool ) – Scene Unit, Incorporates the active scene's scale factor into exported data (optional)

- forward_axis ( Literal [ 'X' , 'Y' , 'Z' , '`NEGATIVE_X`' , '`NEGATIVE_Y`' , '`NEGATIVE_Z`' ] ) – Forward Axis, (optional)

- X
X – Positive X axis.

- Y
Y – Positive Y axis.

- Z
Z – Positive Z axis.

- `NEGATIVE_X`
-X – Negative X axis.

- `NEGATIVE_Y`
-Y – Negative Y axis.

- `NEGATIVE_Z`
-Z – Negative Z axis.

- up_axis ( Literal [ 'X' , 'Y' , 'Z' , '`NEGATIVE_X`' , '`NEGATIVE_Y`' , '`NEGATIVE_Z`' ] ) – Up Axis, (optional)

- X
X – Positive X axis.

- Y
Y – Positive Y axis.

- Z
Z – Positive Z axis.

- `NEGATIVE_X`
-X – Negative X axis.

- `NEGATIVE_Y`
-Y – Negative Y axis.

- `NEGATIVE_Z`
-Z – Negative Z axis.

- apply_modifiers ( bool ) – Apply Modifiers, Execute modifiers on exported geometry (optional)

- filter_glob ( str ) – Extension Filter, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. stl_import ( * , filepath = '' , directory = '' , files = None , check_existing = False , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , global_scale = 1.0 , use_scene_unit = False , use_facet_normal = False , forward_axis = 'Y' , up_axis = 'Z' , use_mesh_validate = True , filter_glob = '*.stl' )
