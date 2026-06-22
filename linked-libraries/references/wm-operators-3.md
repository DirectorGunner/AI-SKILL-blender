# Wm Operators (part 3)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

Outputs Grease Pencil as an SVG image

Parameters :

- filepath ( str ) - File Path, Destination file path (optional, never None)

- check_existing ( bool ) - Check Existing, Alerts and verifies before overwriting files (optional)

- filter_blender ( bool ) - Filter .blend files, (optional)

- filter_backup ( bool ) - Filter backup .blend files, (optional)

- filter_image ( bool ) - Filter image files, (optional)

- filter_movie ( bool ) - Filter movie files, (optional)

- filter_python ( bool ) - Filter Python files, (optional)

- filter_font ( bool ) - Filter font files, (optional)

- filter_sound ( bool ) - Filter sound files, (optional)

- filter_text ( bool ) - Filter text files, (optional)

- filter_archive ( bool ) - Filter archive files, (optional)

- filter_btx ( bool ) - Filter btx files, (optional)

- filter_alembic ( bool ) - Filter Alembic files, (optional)

- filter_usd ( bool ) - Filter USD files, (optional)

- filter_obj ( bool ) - Filter OBJ files, (optional)

- filter_volume ( bool ) - Filter OpenVDB volume files, (optional)

- filter_folder ( bool ) - Filter folders, (optional)

- filter_blenlib ( bool ) - Filter Blender IDs, (optional)

- filemode ( int ) - File Browser Mode, Browser configuration for loading .blend files, libraries, or specialized formats (in [1, 9], optional)

- display_type ( Literal [ 'DEFAULT' , '`LIST_VERTICAL`' , '`LIST_HORIZONTAL`' , 'THUMBNAIL' ] ) - Display Type, (optional)

- DEFAULT
Default - Chooses display type based on file type.

- `LIST_VERTICAL`
Short List - Displays files in a compact list.

- `LIST_HORIZONTAL`
Long List - Displays files with comprehensive details.

- THUMBNAIL
Thumbnails - Displays files as preview icons.

- sort_method ( str ) - File sorting mode, (optional)

- use_fill ( bool ) - Fill, Exports drawn lines with fill applied (optional)

- selected_object_type ( Literal [ 'ACTIVE' , 'SELECTED' , 'VISIBLE' ] ) - Object, Which items to include in the export (optional)

- ACTIVE
Active - Restricts export to the current item.

- SELECTED
Selected - Restricts export to highlighted items.

- VISIBLE
Visible - Restricts export to all visible items.

- frame_mode ( Literal [ 'ACTIVE' , 'SELECTED' , 'SCENE' ] ) - Frames, Which frames to include in the export (optional)

- ACTIVE
Active - Restricts export to the current frame.

- SELECTED
Selected - Restricts export to highlighted frames.

- SCENE
Scene - Restricts export to all composition frames.

- stroke_sample ( float ) - Sampling, Fidelity of line sampling. Lower numbers mean higher accuracy, and zero disables sampling (in [0, 100], optional)

- use_uniform_width ( bool ) - Uniform Width, Exports drawn lines with consistent thickness (optional)

- use_clip_camera ( bool ) - Clip Camera, Restricts exported geometry to camera bounds during camera view output (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. grease_pencil_import_svg ( * , filepath = '' , directory = '' , files = None , check_existing = False , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = True , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , relative_path = True , display_type = 'DEFAULT' , sort_method = '' , resolution = 10 , scale = 10.0 , use_scene_unit = False ) 

Ingests SVG into Grease Pencil

Parameters :

- filepath ( str ) - File Path, Destination file path (optional, never None)

- directory ( str ) - Directory, Folder containing the file (optional, never None)

- files ( bpy_prop_collection [ OperatorFileListElement ]) - Files, (optional)

- check_existing ( bool ) - Check Existing, Alerts and verifies before overwriting files (optional)

- filter_blender ( bool ) - Filter .blend files, (optional)

- filter_backup ( bool ) - Filter backup .blend files, (optional)

- filter_image ( bool ) - Filter image files, (optional)

- filter_movie ( bool ) - Filter movie files, (optional)

- filter_python ( bool ) - Filter Python files, (optional)

- filter_font ( bool ) - Filter font files, (optional)

- filter_sound ( bool ) - Filter sound files, (optional)

- filter_text ( bool ) - Filter text files, (optional)

- filter_archive ( bool ) - Filter archive files, (optional)

- filter_btx ( bool ) - Filter btx files, (optional)

- filter_alembic ( bool ) - Filter Alembic files, (optional)

- filter_usd ( bool ) - Filter USD files, (optional)

- filter_obj ( bool ) - Filter OBJ files, (optional)

- filter_volume ( bool ) - Filter OpenVDB volume files, (optional)

- filter_folder ( bool ) - Filter folders, (optional)

- filter_blenlib ( bool ) - Filter Blender IDs, (optional)

- filemode ( int ) - File Browser Mode, Browser configuration for loading .blend files, libraries, or specialized formats (in [1, 9], optional)

- relative_path ( bool ) - Relative Path, Chooses the file location relative to the .blend project (optional)

- display_type ( Literal [ 'DEFAULT' , '`LIST_VERTICAL`' , '`LIST_HORIZONTAL`' , 'THUMBNAIL' ] ) - Display Type, (optional)

- DEFAULT
Default - Chooses display type based on file type.

- `LIST_VERTICAL`
Short List - Displays files in a compact list.

- `LIST_HORIZONTAL`
Long List - Displays files with comprehensive details.

- THUMBNAIL
Thumbnails - Displays files as preview icons.

- sort_method ( str ) - File sorting mode, (optional)

- resolution ( int ) - Resolution, Precision of the produced motion paths (in [1, 100000], optional)

- scale ( float ) - Scale, Magnification of the converted motion paths (in [1e-06, 1e+06], optional)

- use_scene_unit ( bool ) - Scene Unit, Applies the active composition's unit sizing (as indicated by unit magnitude) to the imported content (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. id_linked_relocate ( * , id_session_uid = 0 , filepath = '' , directory = '' , filename = '' , check_existing = False , filter_blender = True , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = True , filemode = 1 , relative_path = True , display_type = 'DEFAULT' , sort_method = '' , link = True , do_reuse_local_id = False , clear_asset_data = False , autoselect = True , active_collection = False , instance_collections = False , instance_object_data = False )

Reorients a connected component, i.e. designates a replacement component to link, and adjusts its local uses to point to the newly linked component). Presently designed solely as an internal operation, not exposed in the user interface

Parameters :

- id_session_uid ( int ) - Linked ID Session UID, Distinctive runtime identifier for the connected component to reposition (in [0, inf], optional)

- filepath ( str ) - File Path, Destination file path (optional, never None)

- directory ( str ) - Directory, Folder containing the file (optional, never None)

- filename ( str ) - File Name, Title of the file (optional, never None)

- check_existing ( bool ) - Check Existing, Alerts and verifies before overwriting files (optional)

- filter_blender ( bool ) - Filter .blend files, (optional)

- filter_backup ( bool ) - Filter backup .blend files, (optional)

- filter_image ( bool ) - Filter image files, (optional)

- filter_movie ( bool ) - Filter movie files, (optional)

- filter_python ( bool ) - Filter Python files, (optional)

- filter_font ( bool ) - Filter font files, (optional)

- filter_sound ( bool ) - Filter sound files, (optional)

- filter_text ( bool ) - Filter text files, (optional)

- filter_archive ( bool ) - Filter archive files, (optional)

- filter_btx ( bool ) - Filter btx files, (optional)

- filter_alembic ( bool ) - Filter Alembic files, (optional)

- filter_usd ( bool ) - Filter USD files, (optional)

- filter_obj ( bool ) - Filter OBJ files, (optional)

- filter_volume ( bool ) - Filter OpenVDB volume files, (optional)

- filter_folder ( bool ) - Filter folders, (optional)

- filter_blenlib ( bool ) - Filter Blender IDs, (optional)

- filemode ( int ) - File Browser Mode, Browser configuration for loading .blend files, libraries, or specialized formats (in [1, 9], optional)

- relative_path ( bool ) - Relative Path, Chooses the file location relative to the .blend project (optional)

- display_type ( Literal [ 'DEFAULT' , '`LIST_VERTICAL`' , '`LIST_HORIZONTAL`' , 'THUMBNAIL' ] ) - Display Type, (optional)

- DEFAULT
Default - Chooses display type based on file type.

- `LIST_VERTICAL`
Short List - Displays files in a compact list.

- `LIST_HORIZONTAL`
Long List - Displays files with comprehensive details.

- THUMBNAIL
Thumbnails - Displays files as preview icons.

- sort_method ( str ) - File sorting mode, (optional)

- link ( bool ) - Link, Establishes connections to items or components rather than duplicating them (optional)

- do_reuse_local_id ( bool ) - Re-Use Local Data, Attempts to recycle previously matching imported components rather than importing a copy (optional)

- clear_asset_data ( bool ) - Clear Asset Data, Removes asset categorization and labels from the original component (optional)

- autoselect ( bool ) - Select, Marks new items as picked (optional)

- active_collection ( bool ) - Active Collection, Positions new items in the active collection (optional)

- instance_collections ( bool ) - Instance Collections, Generates instances for collections, rather than incorporating them directly into the composition (optional)

- instance_object_data ( bool ) - Instance Object Data, Generates instances for component geometry that are unreferenced by any item (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. interface_theme_preset_add ( * , name = '' , remove_name = False , remove_active = False ) 

Adds a custom palette to the preset listing

Parameters :

- name ( str ) - Name, Title of the preset, utilized for generating the file path (optional, never None)

- remove_name ( bool ) - remove_name, (optional)

- remove_active ( bool ) - remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.wm. interface_theme_preset_remove ( * , name = '' , remove_name = False , remove_active = True ) 

Removes a custom palette from the preset listing

Parameters :

- name ( str ) - Name, Title of the preset, utilized for generating the file path (optional, never None)

- remove_name ( bool ) - remove_name, (optional)

- remove_active ( bool ) - remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.wm. interface_theme_preset_save ( * , name = '' , remove_name = False , remove_active = True ) 

Preserves a custom palette in the preset listing

Parameters :

- name ( str ) - Name, Title of the preset, utilized for generating the file path (optional, never None)

- remove_name ( bool ) - remove_name, (optional)

- remove_active ( bool ) - remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:711

bpy.ops.wm. keyconfig_preset_add ( * , name = '' , remove_name = False , remove_active = False ) 

Adds a custom keybinding setup to the preset listing

Parameters :

- name ( str ) - Name, Title of the preset, utilized for generating the file path (optional, never None)

- remove_name ( bool ) - remove_name, (optional)

- remove_active ( bool ) - remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.wm. keyconfig_preset_remove ( * , name = '' , remove_name = False , remove_active = True ) 

Removes a custom keybinding setup from the preset listing

Parameters :

- name ( str ) - Name, Title of the preset, utilized for generating the file path (optional, never None)

- remove_name ( bool ) - remove_name, (optional)

- remove_active ( bool ) - remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.wm. lib_reload ( * , library = '' , filepath = '' , directory = '' , filename = '' , hide_props_region = True , check_existing = False , filter_blender = True , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , relative_path = True , display_type = 'DEFAULT' , sort_method = '' )

Reloads a specified library

Parameters :

- library ( str ) – Library, Specifies which library is to be reloaded (optional, never None)

- filepath ( str ) – File Path, The location of the file (optional, never None)

- directory ( str ) – Directory, Where the file is stored (optional, never None)

- filename ( str ) – File Name, The name of the target file (optional, never None)

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

- relative_path ( bool ) – Relative Path, Select the file relative to the blend file (optional)

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

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. lib_relocate ( * , library = '' , filepath = '' , directory = '' , filename = '' , files = None , hide_props_region = True , check_existing = False , filter_blender = True , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , relative_path = True , display_type = 'DEFAULT' , sort_method = '' ) 

Moves the given library to another location

Parameters :

- library ( str ) – Library, The library to be relocated (optional, never None)

- filepath ( str ) – File Path, The location of the file (optional, never None)

- directory ( str ) – Directory, Where the file is stored (optional, never None)

- filename ( str ) – File Name, The name of the target file (optional, never None)

- files ( bpy_prop_collection [ OperatorFileListElement ]) – Files, (optional)

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

- relative_path ( bool ) – Relative Path, Select the file relative to the blend file (optional)

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

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. link ( * , filepath = '' , directory = '' , filename = '' , files = None , check_existing = False , filter_blender = True , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = True , filemode = 1 , relative_path = True , display_type = 'DEFAULT' , sort_method = '' , link = True , do_reuse_local_id = False , clear_asset_data = False , autoselect = True , active_collection = True , instance_collections = True , instance_object_data = True )
