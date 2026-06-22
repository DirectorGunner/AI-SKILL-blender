# Wm Operators (part 1)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

### Wm Operators 

bpy.ops.wm. alembic_export ( * , filepath = '' , check_existing = True , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = True , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , filter_glob = '*.abc' , start = -2147483648 , end = -2147483648 , xsamples = 1 , gsamples = 1 , sh_open = 0.0 , sh_close = 1.0 , selected = False , flatten = False , collection = '' , uvs = True , packuv = True , normals = True , vcolors = False , orcos = True , face_sets = False , subdiv_schema = False , apply_subdiv = False , curves_as_mesh = False , use_instancing = True , global_scale = 1.0 , triangulate = False , quad_method = '`SHORTEST_DIAGONAL`' , ngon_method = 'BEAUTY' , export_hair = True , export_particles = True , export_custom_properties = True , as_background_job = False , evaluation_mode = 'RENDER' , init_scene_frame_range = True ) 

Outputs the current scene as an Alembic archive

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

- filter_glob ( str ) - (optional, never None)

- start ( int ) - Start Frame, Initial frame for the export, or current scene's start if using default (in [-inf, inf], optional)

- end ( int ) - End Frame, Final frame for the export, or current scene's end if using default (in [-inf, inf], optional)

- xsamples ( int ) - Transform Samples, Sampling count per frame for motion transformations (in [1, 128], optional)

- gsamples ( int ) - Geometry Samples, Sampling count per frame for shape data (in [1, 128], optional)

- sh_open ( float ) - Shutter Open, Frame position when the shutter begins recording (in [-1, 1], optional)

- sh_close ( float ) - Shutter Close, Frame position when the shutter stops recording (in [-1, 1], optional)

- selected ( bool ) - Selected Objects Only, Exports only the highlighted geometry (optional)

- flatten ( bool ) - Flatten Hierarchy, Discards parent-child connections (optional)

- collection ( str ) - Collection, (optional, never None)

- uvs ( bool ) - UV Coordinates, Outputs texture coordinates (optional)

- packuv ( bool ) - Merge UVs, (optional)

- normals ( bool ) - Normals, Outputs surface orientation data (optional)

- vcolors ( bool ) - Color Attributes, Outputs color information (optional)

- orcos ( bool ) - Generated Coordinates, Outputs unmodified vertex positions (optional)

- face_sets ( bool ) - Face Sets, Outputs per-face shading assignments (optional)

- subdiv_schema ( bool ) - Use Subdivision Schema, Outputs meshes using Alembic's subdivision method (optional)

- apply_subdiv ( bool ) - Apply Subdivision Surface, Outputs subdivision surfaces as polygon meshes (optional)

- curves_as_mesh ( bool ) - Curves as Mesh, Outputs curves and NURBS as polygon meshes (optional)

- use_instancing ( bool ) - Use Instancing, Outputs duplicated geometry as Alembic instances; reduces file size yet may limit compatibility with other applications (optional)

- global_scale ( float ) - Scale, Factor to enlarge or reduce geometry relative to world space (in [0.0001, 1000], optional)

- triangulate ( bool ) - Triangulate, Outputs polygonal faces as triangle subdivisions (optional)

- quad_method (Literal[Modifier Triangulate Quad Method Items]) - Quad Method, Technique for splitting quadrilaterals (optional)

- ngon_method (Literal[Modifier Triangulate Ngon Method Items]) - N-gon Method, Technique for splitting polygons (optional)

- export_hair ( bool ) - Export Hair, Outputs hair particle geometry as keyframed splines (optional)

- export_particles ( bool ) - Export Particles, Outputs non-hair particle systems (optional)

- export_custom_properties ( bool ) - Export Custom Properties, Outputs user-defined parameters to Alembic .userProperties (optional)

- as_background_job ( bool ) - Run as Background Job, Allows the import to execute in the background without blocking Blender. This functionality is superseded; EXECUTE to run in the foreground, and INVOKE to run as a background operation (optional)

- evaluation_mode ( Literal [ 'RENDER' , 'VIEWPORT' ] ) - Settings, Indicates visibility behavior, modifier configuration, and contexts with distinct viewport and rendering parameters (optional)

- RENDER
Render - Applies rendering configuration to visibility and modifiers.

- VIEWPORT
Viewport - Applies viewport configuration to visibility and modifiers.

- init_scene_frame_range ( bool ) - (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. alembic_import ( * , filepath = '' , directory = '' , files = None , check_existing = False , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = True , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , relative_path = True , display_type = 'DEFAULT' , sort_method = '' , filter_glob = '*.abc' , scale = 1.0 , set_frame_range = True , validate_meshes = False , always_add_cache_reader = False , is_sequence = False , as_background_job = False ) 

Reads an Alembic archive

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

- filter_glob ( str ) - (optional, never None)

- scale ( float ) - Scale, Factor to enlarge or reduce geometry relative to world space (in [0.0001, 1000], optional)

- set_frame_range ( bool ) - Set Frame Range, If turned on, modifies composition start/end frames to align with the archive (optional)

- validate_meshes ( bool ) - Validate Meshes, Guarantees the structure is sound (when disabled, geometry might be imported causing application crashes during display or modification) (optional)

- always_add_cache_reader ( bool ) - Always Add Cache Reader, Assigns cache modifiers and constraints to imported geometry regardless of animation so modifications apply when reloading the archive (optional)

- is_sequence ( bool ) - Is Sequence, Specifies whether the cache is separated into discrete files (optional)

- as_background_job ( bool ) - Run as Background Job, Allows the export to execute in the background without blocking Blender. This functionality is superseded; EXECUTE to run in the foreground, and INVOKE to run as a background operation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. append ( * , filepath = '' , directory = '' , filename = '' , files = None , check_existing = False , filter_blender = True , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = True , filemode = 1 , display_type = 'DEFAULT' , sort_method = '' , link = False , do_reuse_local_id = False , clear_asset_data = False , autoselect = True , active_collection = True , instance_collections = False , instance_object_data = True , set_fake = False , use_recursive = True ) 

Imports from a Library .blend file

Parameters :

- filepath ( str ) - File Path, Destination file path (optional, never None)

- directory ( str ) - Directory, Folder containing the file (optional, never None)

- filename ( str ) - File Name, Title of the file (optional, never None)

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

- set_fake ( bool ) - Fake User, Assigns "Fake User" to imported components (excluding items and collections) (optional)

- use_recursive ( bool ) - Localize All, Converts all imported components locally, including those connected indirectly from other libraries (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. batch_rename ( * , data_type = 'OBJECT' , data_source = 'SELECT' , actions = None ) 

Changes names of multiple components concurrently

Parameters :

- data_type ( Literal [ 'OBJECT' , 'COLLECTION' , 'MATERIAL' , 'MESH' , 'CURVE' , 'META' , 'VOLUME' , 'GREASEPENCIL' , 'ARMATURE' , 'LATTICE' , 'LIGHT' , '`LIGHT_PROBE`' , 'CAMERA' , 'SPEAKER' , 'BONE' , 'NODE' , '`SEQUENCE_STRIP`' , '`ACTION_CLIP`' , 'SCENE' , 'BRUSH' ] ) - Type, Category of component to rename (optional)

- data_source ( Literal [ 'SELECT' , 'ALL' ] ) - Source, (optional)

- actions ( bpy_prop_collection [ BatchRenameAction ]) - actions, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:3283

bpy.ops.wm. blend_strings_utf8_validate ( ) 

Examines and corrects all text in the current .blend project to meet valid UTF-8 Unicode standards (required for older, version 2.4x region definitions)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/file.py:289

bpy.ops.wm. call_asset_shelf_popover ( * , name = '' ) 

Shows a defined asset shelf in a floating container

Parameters :

name ( str ) - Asset Shelf Name, Tag of the asset shelf to display (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. call_menu ( * , name = '' ) 

Displays a predefined context menu

Parameters :

name ( str ) - Name, Identifier of the menu (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. call_menu_pie ( * , name = '' ) 

Displays a predefined pie-shaped menu

Parameters :

name ( str ) - Name, Identifier of the pie menu (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. call_panel ( * , name = '' , keep_open = True ) 

Displays a predefined panel

Parameters :

- name ( str ) - Name, Identifier of the menu (optional, never None)

- keep_open ( bool ) - Keep Open, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. clear_recent_files ( * , remove = 'ALL' ) 

Clears the history of accessed files

Parameters :

remove ( Literal [ 'ALL' , 'MISSING' ] ) - Remove, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. collection_export_all ( ) 

Initiates all registered output handlers for every collection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. context_collection_boolean_set ( * , data_path_iter = '' , data_path_item = '' , type = 'TOGGLE' ) 

Sets boolean parameters across multiple components

Parameters :

- data_path_iter ( str ) - data_path_iter, Context-relative trajectory, must reference an enumerable group (optional, never None)

- data_path_item ( str ) - data_path_item, Each item's parameter from the enumerable (int or float) (optional, never None)

- type ( Literal [ 'TOGGLE' , 'ENABLE' , 'DISABLE' ] ) - Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:875

bpy.ops.wm. context_cycle_array ( * , data_path = '' , reverse = False ) 

Establishes a context array variable (beneficial for alternating active mesh editing mode)

Parameters :

- data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using accessible windows in the current .blend project) (optional, never None)

- reverse ( bool ) - Reverse, Cycles forward (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:673

bpy.ops.wm. context_cycle_enum ( * , data_path = '' , reverse = False , wrap = False )
