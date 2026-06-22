# Preferences Operators (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Preferences Operators 

bpy.ops.preferences. addon_disable ( * , module = '' ) 

Deactivate the provided add-on

Parameters :

module ( str ) – Module, Module name of the add-on to disable (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:547

bpy.ops.preferences. addon_enable ( * , module = '' ) 

Activate the provided add-on

Parameters :

module ( str ) – Module, Module name of the add-on to enable (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:483

bpy.ops.preferences. addon_expand ( * , module = '' ) 

Reveal facts and configuration for the given add-on

Parameters :

module ( str ) – Module, Module name of the add-on to expand (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:924

bpy.ops.preferences. addon_install ( * , overwrite = True , enable_on_install = False , target = '' , filepath = '' , filter_folder = True , filter_python = True , filter_glob = '*.py;*.zip' ) 

Setup a new add-on

Parameters :

- overwrite ( bool ) – Overwrite, Remove existing add-ons with the same ID (optional)

- enable_on_install ( bool ) – Enable on Install, Enable after installing (optional)

- target ( str ) – Target Path, (optional)

- filepath ( str ) – filepath, (optional, never None)

- filter_folder ( bool ) – Filter folders, (optional)

- filter_python ( bool ) – Filter Python, (optional)

- filter_glob ( str ) – filter_glob, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:712

bpy.ops.preferences. addon_refresh ( ) 

Hunt for new modules in add-on locations

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:645

bpy.ops.preferences. addon_remove ( * , module = '' ) 

Erase the add-on from disk

Parameters :

module ( str ) – Module, Module name of the add-on to remove (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:873

bpy.ops.preferences. addon_show ( * , module = '' ) 

Unveil add-on preferences

Parameters :

module ( str ) – Module, Module name of the add-on to expand (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:950

bpy.ops.preferences. app_template_install ( * , overwrite = True , filepath = '' , filter_folder = True , filter_glob = '*.zip' ) 

Install an application template

Parameters :

- overwrite ( bool ) – Overwrite, Remove existing template with the same ID (optional)

- filepath ( str ) – filepath, (optional, never None)

- filter_folder ( bool ) – Filter folders, (optional)

- filter_glob ( str ) – filter_glob, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:1000

bpy.ops.preferences. asset_library_add ( * , directory = '' , hide_props_region = True , check_existing = False , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 9 , display_type = 'DEFAULT' , sort_method = '' ) 

Enlist a folder path to be accessed by the Asset Browser as an asset repository

Parameters :

- directory ( str ) – Directory, Directory of the file (optional, never None)

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

bpy.ops.preferences. asset_library_remove ( * , index = 0 ) 

Remove a path reference to a .blend file from Asset Browser discovery

Parameters :

index ( int ) – Index, (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.preferences. associate_blend ( ) 

Make this installation the handler for .blend files and to render their thumbnails

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.preferences. autoexec_path_add ( ) 

Enlist a path to exclude from automatic code execution

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.preferences. autoexec_path_remove ( * , index = 0 ) 

Erase a path reference from automatic code execution exclusion

Parameters :

index ( int ) – Index, (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.preferences. clear_filter ( ) 

Reset the query criteria

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.preferences. copy_prev ( ) 

Replicate settings from the last version

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:170

bpy.ops.preferences. extension_repo_add ( * , name = '' , remote_url = '' , use_access_token = False , access_token = '' , use_sync_on_startup = False , use_custom_directory = False , custom_directory = '' , type = 'REMOTE' ) 

Enlist a fresh repository for storing extensions

Parameters :

- name ( str ) – Name, Unique repository name (optional, never None)

- remote_url ( str ) – URL, Remote URL to the extension repository, the file-system may be referenced using the file URI scheme: "file://" (optional, never None)

- use_access_token ( bool ) – Requires Access Token, Repository requires an access token (optional)

- access_token ( str ) – Secret, Personal access token, may be required by some repositories (optional, never None)

- use_sync_on_startup ( bool ) – Check for Updates on Startup, Allow Blender to check for updates upon launch (optional)

- use_custom_directory ( bool ) – Custom Directory, Manually set the path for extensions to be stored. When disabled a user's extensions directory is created. (optional)

- custom_directory ( str ) – Custom Directory, The local directory containing extensions (optional, never None)

- type ( Literal [ 'REMOTE' , 'LOCAL' ] ) – Type, The kind of repository to add (optional)

- REMOTE
Add Remote Repository – Add a repository referencing a remote repository with support for listing and updating extensions.

- LOCAL
Add Local Repository – Add a repository managed manually without referencing an external repository.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.preferences. extension_repo_remove ( * , index = 0 , remove_files = False ) 

Erase an extension repository

Parameters :

- index ( int ) – Index, (in [0, inf], optional)

- remove_files ( bool ) – Remove Files, Remove extension files when removing the repository (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.preferences. extension_url_drop ( * , url = '' ) 

Process an extension URL that has been dropped

Parameters :

url ( str ) – URL, Location of the extension to install (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.preferences. keyconfig_activate ( * , filepath = '' ) 

Undocumented, consider contributing.

Parameters :

filepath ( str ) – filepath, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:91

bpy.ops.preferences. keyconfig_export ( * , all = False , filepath = '' , filter_folder = True , filter_text = True , filter_python = True ) 

Transmit key setup to a Python file

Parameters :

- all ( bool ) – All Keymaps, Write all keymaps (not just user modified) (optional)

- filepath ( str ) – filepath, (optional, never None)

- filter_folder ( bool ) – Filter folders, (optional)

- filter_text ( bool ) – Filter text, (optional)

- filter_python ( bool ) – Filter Python, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:324

bpy.ops.preferences. keyconfig_import ( * , filepath = 'keymap.py' , filter_folder = True , filter_text = True , filter_python = True , keep_original = True ) 

Ingest key setup from a Python file

Parameters :

- filepath ( str ) – filepath, (optional, never None)

- filter_folder ( bool ) – Filter folders, (optional)

- filter_text ( bool ) – Filter text, (optional)

- filter_python ( bool ) – Filter Python, (optional)

- keep_original ( bool ) – Keep Original, Keep original file after copying to configuration folder (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:259

bpy.ops.preferences. keyconfig_remove ( ) 

Erase the key config

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:463

bpy.ops.preferences. keyconfig_test ( ) 

Examine key configuration for contradictions

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:194

bpy.ops.preferences. keyitem_add ( ) 

Establish a fresh keybinding entry

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:411

bpy.ops.preferences. keyitem_remove ( * , item_id = 0 ) 

Erase a keybinding entry

Parameters :

item_id ( int ) – Item Identifier, Identifier of the item to remove (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:443

bpy.ops.preferences. keyitem_restore ( * , item_id = 0 ) 

Bring back a keybinding entry

Parameters :

item_id ( int ) – Item Identifier, Identifier of the item to restore (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:395

bpy.ops.preferences. keymap_restore ( * , all = False ) 

Bring back keybinding(s)

Parameters :

all ( bool ) – All Keymaps, Restore all keymaps to default (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:366

bpy.ops.preferences. reset_default_theme ( ) 

Return to the baseline theme colors

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.preferences. script_directory_add ( * , directory = '' , filter_folder = True ) 

Undocumented, consider contributing.

Parameters :

- directory ( str ) – directory, (optional, never None)

- filter_folder ( bool ) – Filter Folders, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:1256

bpy.ops.preferences. script_directory_remove ( * , index = 0 ) 

Undocumented, consider contributing.

Parameters :

index ( int ) – Index, Index of the script directory to remove (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:1286

bpy.ops.preferences. start_filter ( ) 

Begin entering filter keywords

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.preferences. studiolight_copy_settings ( * , index = 0 ) 

Duplicate Studio Light setup to the Studio Light editor

Parameters :

index ( int ) – index, (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:1227

bpy.ops.preferences. studiolight_install ( * , files = None , directory = '' , filter_folder = True , filter_glob = '*.png;*.jpg;*.hdr;*.exr' , type = 'MATCAP' ) 

Place a hand-defined light source

Parameters :

- files ( bpy_prop_collection [ OperatorFileListElement ]) – File Path, (optional)

- directory ( str ) – directory, (optional, never None)

- filter_folder ( bool ) – Filter Folders, (optional)

- filter_glob ( str ) – filter_glob, (optional, never None)

- type ( Literal [ 'MATCAP' , 'WORLD' , 'STUDIO' ] ) – Type, (optional)

- MATCAP
MatCap – Install custom MatCaps.

- WORLD
World – Install custom HDRIs.

- STUDIO
Studio – Install custom Studio Lights.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:1110

bpy.ops.preferences. studiolight_new ( * , filename = 'StudioLight' ) 

Preserve hand-edited studio light setup to a file

Parameters :

filename ( str ) – Name, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:1157

bpy.ops.preferences. studiolight_uninstall ( * , index = 0 ) 

Remove a Studio Light

Parameters :

index ( int ) – index, (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:1208

bpy.ops.preferences. theme_install ( * , overwrite = True , filepath = '' , filter_folder = True , filter_glob = '*.xml' ) 

Ingest and employ a Blender XML theme file

Parameters :

- overwrite ( bool ) – Overwrite, Remove existing theme file if exists (optional)

- filepath ( str ) – filepath, (optional, never None)

- filter_folder ( bool ) – Filter folders, (optional)

- filter_glob ( str ) – filter_glob, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/userpref.py:598

bpy.ops.preferences. unassociate_blend ( ) 

Disassociate this installation from .blend file handling

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

set[Literal[Operator Return Items]]

bpy.ops.preferences. autoexec_path_add ( )
Adds a path to exclude from auto-execution.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.preferences. autoexec_path_remove ( * , index = 0 )
Removes a path from the auto-execution exclusions.
Parameters: index ( int ) – Index, (in [0, inf], optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.preferences. clear_filter ( )
Clears the search filter.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.preferences. copy_prev ( )
Copies settings from the previous version.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:170

bpy.ops.preferences. extension_repo_add ( * , name = '' , remote_url = '' , use_access_token = False , access_token = '' , use_sync_on_startup = False , use_custom_directory = False , custom_directory = '' , type = 'REMOTE' )
Adds a new repository used to store extensions.
Parameters:
- name ( str ) – Name, Unique repository name (optional, never None)
- remote_url ( str ) – URL, Remote URL to the extension repository, the file-system may be referenced using the file URI scheme: "file://" (optional, never None)
- use_access_token ( bool ) – Requires Access Token, Repository requires an access token (optional)
- access_token ( str ) – Secret, Personal access token, may be required by some repositories (optional, never None)
- use_sync_on_startup ( bool ) – Check for Updates on Startup, Allow Blender to check for updates upon launch (optional)
- use_custom_directory ( bool ) – Custom Directory, Manually set the path for extensions to be stored. When disabled a user's extensions directory is created. (optional)
- custom_directory ( str ) – Custom Directory, The local directory containing extensions (optional, never None)
- type ( Literal [ 'REMOTE' , 'LOCAL' ] ) – Type, The kind of repository to add (optional)
- REMOTE — Add Remote Repository: add a repository referencing a remote one, with support for listing and updating extensions.
- LOCAL — Add Local Repository: add a repository managed manually, without referencing an external one.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.preferences. extension_repo_remove ( * , index = 0 , remove_files = False )
Removes an extension repository.
Parameters:
- index ( int ) – Index, (in [0, inf], optional)
- remove_files ( bool ) – Remove Files, Remove extension files when removing the repository (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.preferences. extension_url_drop ( * , url = '' )
Handles dropping an extension URL.
Parameters: url ( str ) – URL, Location of the extension to install (optional, never None)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.preferences. keyconfig_activate ( * , filepath = '' )
Undocumented, consider contributing.
Parameters: filepath ( str ) – filepath, (optional, never None)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:91

bpy.ops.preferences. keyconfig_export ( * , all = False , filepath = '' , filter_folder = True , filter_text = True , filter_python = True )
Exports the key configuration to a Python script.
Parameters:
- all ( bool ) – All Keymaps, Write all keymaps (not just user modified) (optional)
- filepath ( str ) – filepath, (optional, never None)
- filter_folder ( bool ) – Filter folders, (optional)
- filter_text ( bool ) – Filter text, (optional)
- filter_python ( bool ) – Filter Python, (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:324

bpy.ops.preferences. keyconfig_import ( * , filepath = 'keymap.py' , filter_folder = True , filter_text = True , filter_python = True , keep_original = True )
Imports the key configuration from a Python script.
Parameters:
- filepath ( str ) – filepath, (optional, never None)
- filter_folder ( bool ) – Filter folders, (optional)
- filter_text ( bool ) – Filter text, (optional)
- filter_python ( bool ) – Filter Python, (optional)
- keep_original ( bool ) – Keep Original, Keep original file after copying to configuration folder (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:259

bpy.ops.preferences. keyconfig_remove ( )
Removes a key config.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:463

bpy.ops.preferences. keyconfig_test ( )
Tests the key configuration for conflicts.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:194

bpy.ops.preferences. keyitem_add ( )
Adds a key map item.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:411

bpy.ops.preferences. keyitem_remove ( * , item_id = 0 )
Removes a key map item.
Parameters: item_id ( int ) – Item Identifier, Identifier of the item to remove (in [-inf, inf], optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:443

bpy.ops.preferences. keyitem_restore ( * , item_id = 0 )
Restores a key map item.
Parameters: item_id ( int ) – Item Identifier, Identifier of the item to restore (in [-inf, inf], optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:395

bpy.ops.preferences. keymap_restore ( * , all = False )
Restores key map(s).
Parameters: all ( bool ) – All Keymaps, Restore all keymaps to default (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:366

bpy.ops.preferences. reset_default_theme ( )
Resets to the default theme colors.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.preferences. script_directory_add ( * , directory = '' , filter_folder = True )
Undocumented, consider contributing.
Parameters:
- directory ( str ) – directory, (optional, never None)
- filter_folder ( bool ) – Filter Folders, (optional)
