# Wm Operators (part 4)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

Create a link from a Library .blend file

Parameters :

- filepath ( str ) – File Path, The location of the file (optional, never None)

- directory ( str ) – Directory, Where the file is stored (optional, never None)

- filename ( str ) – File Name, The name of the target file (optional, never None)

- files ( bpy_prop_collection [ OperatorFileListElement ]) – Files, (optional)

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

- link ( bool ) – Link, Bring in objects or data-blocks via linking as opposed to duplication (optional)

- do_reuse_local_id ( bool ) – Re-Use Local Data, Make use of existing previously-matched appended data-blocks rather than adding fresh ones (optional)

- clear_asset_data ( bool ) – Clear Asset Data, Strip asset metadata and tags from the original data-block (optional)

- autoselect ( bool ) – Select, Choose new objects (optional)

- active_collection ( bool ) – Active Collection, Add new objects to the active collection (optional)

- instance_collections ( bool ) – Instance Collections, Make instances from collections as opposed to placing them into the scene directly (optional)

- instance_object_data ( bool ) – Instance Object Data, Create instances when object data are unreferenced by any objects (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. memory_statistics ( ) 

Output memory statistics to the console

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. obj_export ( * , filepath = '' , check_existing = True , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , export_animation = False , start_frame = -2147483648 , end_frame = 2147483647 , forward_axis = '`NEGATIVE_Z`' , up_axis = 'Y' , global_scale = 1.0 , apply_modifiers = True , apply_transform = True , export_eval_mode = '`DAG_EVAL_VIEWPORT`' , export_selected_objects = False , export_uv = True , export_normals = True , export_colors = False , export_materials = True , export_pbr_extensions = False , path_mode = 'AUTO' , export_triangulated_mesh = False , export_curves_as_nurbs = False , export_object_groups = False , export_material_groups = False , export_vertex_groups = False , export_smooth_groups = False , smooth_group_bitflags = False , filter_glob = '*.obj;*.mtl' , collection = '' ) 

Exports the scene to a Wavefront OBJ file

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

- export_animation ( bool ) – Export Animation, Include animation frames instead of just the current one (optional)

- start_frame ( int ) – Start Frame, First frame for export (in [-inf, inf], optional)

- end_frame ( int ) – End Frame, Last frame for export (in [-inf, inf], optional)

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

- global_scale ( float ) – Scale, Multiplies the dimensions of objects relative to world origin (in [0.0001, 10000], optional)

- apply_modifiers ( bool ) – Apply Modifiers, Execute modifiers on exported geometry (optional)

- apply_transform ( bool ) – Apply Transform, Bake object transformations into exported geometry (optional)

- export_eval_mode ( Literal [ '`DAG_EVAL_RENDER`' , '`DAG_EVAL_VIEWPORT`' ] ) – Object Properties, Sets object characteristics like visibility and modifiers for either render or viewport display (optional)

- `DAG_EVAL_RENDER`
Render – Export objects as they appear in render.

- `DAG_EVAL_VIEWPORT`
Viewport – Export objects as they appear in the viewport.

- export_selected_objects ( bool ) – Export Selected Objects, Restrict export to currently-selected objects only (optional)

- export_uv ( bool ) – Export UVs, (optional)

- export_normals ( bool ) – Export Normals, Output per-face normals for flat-shaded faces, per-corner normals for smooth ones (optional)

- export_colors ( bool ) – Export Colors, Include color attributes at each vertex (optional)

- export_materials ( bool ) – Export Materials, Output MTL library. Image textures in MTL require a Principled-BSDF node (optional)

- export_pbr_extensions ( bool ) – Export Materials with PBR Extensions, Output MTL using PBR formats (roughness, metallic, sheen, coat, anisotropy, transmission) (optional)

- path_mode ( Literal [ 'AUTO' , 'ABSOLUTE' , 'RELATIVE' , 'MATCH' , 'STRIP' , 'COPY' ] ) – Path Mode, Approach for resolving file references (optional)

- AUTO
Auto – Use relative paths with subdirectories only.

- ABSOLUTE
Absolute – Always write absolute paths.

- RELATIVE
Relative – Write relative paths where possible.

- MATCH
Match – Match absolute/relative setting with input path.

- STRIP
Strip – Write filename only.

- COPY
Copy – Copy the file to the destination path.

- export_triangulated_mesh ( bool ) – Export Triangulated Mesh, Converts all ngons of 4+ vertices to triangles. Meshes in the scene are unaffected. Works like Triangulate with ngon-method: "Beauty", quad-method: "Shortest Diagonal", min vertices: 4 (optional)

- export_curves_as_nurbs ( bool ) – Export Curves as NURBS, Write curves in parametric form rather than as mesh (optional)

- export_object_groups ( bool ) – Export Object Groups, Concatenate mesh name to object name with '_' separator (optional)

- export_material_groups ( bool ) – Export Material Groups, Form an OBJ group for each geometry segment with a distinct material (optional)

- export_vertex_groups ( bool ) – Export Vertex Groups, Write the vertex group name of a face. Approximated by choosing the vertex group with the most presence among the face's vertices (optional)

- export_smooth_groups ( bool ) – Export Smooth Groups, Make identifiers for each group of smooth faces as individual integer values (optional)

- smooth_group_bitflags ( bool ) – Bitflags Smooth Groups, When exporting smooth groups, use 'bitflags' values rather than unique integers. Distinct groups may share a bitflag if they have no mutual sharp edges or vertices (optional)

- filter_glob ( str ) – Extension Filter, (optional, never None)

- collection ( str ) – Collection, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. obj_import ( * , filepath = '' , directory = '' , files = None , check_existing = False , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , global_scale = 1.0 , clamp_size = 0.0 , forward_axis = '`NEGATIVE_Z`' , up_axis = 'Y' , use_split_objects = True , use_split_groups = False , import_vertex_groups = False , validate_meshes = True , close_spline_loops = True , collection_separator = '' , mtl_name_collision_mode = '`MAKE_UNIQUE`' , filter_glob = '*.obj;*.mtl' ) 

Imports a Wavefront OBJ scene

Parameters :

- filepath ( str ) – File Path, Path to file (optional, never None)

- directory ( str ) – Directory, Directory of the file (optional, never None)

- files ( bpy_prop_collection [ OperatorFileListElement ]) – Files, (optional)

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

- global_scale ( float ) – Scale, Adjusts object dimensions relative to the world's origin (in [0.0001, 10000], optional)

- clamp_size ( float ) – Clamp Bounding Box, Resize objects to keep bounding box within this threshold. Value 0 disables constraint (in [0, 1000], optional)

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

- use_split_objects ( bool ) – Split By Object, Treats each OBJ 'o' as its own distinct object (optional)

- use_split_groups ( bool ) – Split By Group, Treats each OBJ 'g' as its own distinct object (optional)

- import_vertex_groups ( bool ) – Vertex Groups, Converts OBJ groups into vertex groups (optional)

- validate_meshes ( bool ) – Validate Meshes, Ensures imported data passes validity checks (if disabled, problematic data may cause crashes) (optional)

- close_spline_loops ( bool ) – Detect Cyclic Curves, Links curve endpoints when overlapping control points are discovered (if disabled, curves will remain unclosed) (optional)

- collection_separator ( str ) – Path Separator, Symbol dividing object names into hierarchical structures (optional, never None)

- mtl_name_collision_mode ( Literal [ '`MAKE_UNIQUE`' , '`REFERENCE_EXISTING`' ] ) – Material Name Collision, Handling strategy when material names clash during import (optional)

- `MAKE_UNIQUE`
Make Unique – Create new materials with unique names for each OBJ file.

- `REFERENCE_EXISTING`
Reference Existing – Use existing materials with same name instead of creating new ones.

- filter_glob ( str ) – Extension Filter, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. open_mainfile ( * , filepath = '' , hide_props_region = True , check_existing = False , filter_blender = True , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , load_ui = True , use_scripts = False , display_file_selector = True , state = 0 ) 

Launches a Blender file

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

- load_ui ( bool ) – Load UI, Include user interface layout from the .blend file (optional)

- use_scripts ( bool ) – Trusted Source, Permit .blend file to run scripts on startup; default sourced from system configuration (optional)

- display_file_selector ( bool ) – Display File Selector, (optional)

- state ( int ) – State, (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. operator_cheat_sheet ( ) 

Creates a text-block listing all operators for scripting reference

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:2257

bpy.ops.wm. operator_defaults ( ) 

Resets the active operator to its initial values

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. operator_pie_enum ( * , data_path = '' , prop_string = '' ) 

Undocumented, consider contributing.

Parameters :

- data_path ( str ) – Operator, Operator name (in Python as string) (optional, never None)

- prop_string ( str ) – Property, Property name (as a string) (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:777

bpy.ops.wm. operator_preset_add ( * , name = '' , remove_name = False , remove_active = False , operator = '' ) 

Adds or removes an Operator Preset

Parameters :

- name ( str ) – Name, Title of the preset, becomes the path name (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

- operator ( str ) – Operator, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.wm. operator_presets_cleanup ( * , operator = '' , properties = None ) 

Eliminates obsolete operator settings from presets that could generate issues

Parameters :

- operator ( str ) – operator, (optional, never None)

- properties ( bpy_prop_collection [ OperatorFileListElement ]) – properties, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:924

bpy.ops.wm. owner_disable ( * , owner_id = '' ) 

Deactivate an add-on within a workspace

Parameters :

owner_id ( str ) – UI Tag, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:2305

bpy.ops.wm. owner_enable ( * , owner_id = '' ) 

Activates an add-on in a workspace

Parameters :

owner_id ( str ) – UI Tag, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:2290

bpy.ops.wm. path_open ( * , filepath = '' ) 

Displays a path in a file browser

Parameters :

filepath ( str ) – filepath, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:1167

bpy.ops.wm. ply_export ( * , filepath = '' , check_existing = True , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , forward_axis = 'Y' , up_axis = 'Z' , global_scale = 1.0 , apply_modifiers = True , export_selected_objects = False , collection = '' , export_uv = True , export_normals = False , export_colors = 'SRGB' , export_attributes = True , export_triangulated_mesh = False , ascii_format = False , filter_glob = '*.ply' ) 

Writes the scene to a PLY file

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
