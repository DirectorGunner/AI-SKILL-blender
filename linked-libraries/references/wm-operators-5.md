# Wm Operators (part 5)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

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

- global_scale ( float ) – Scale, Adjusts object dimensions relative to the world's origin (in [0.0001, 10000], optional)

- apply_modifiers ( bool ) – Apply Modifiers, Execute modifiers on exported geometry (optional)

- export_selected_objects ( bool ) – Export Selected Objects, Restrict export to currently-selected objects only (optional)

- collection ( str ) – Source Collection, Write only objects from this collection and its children (optional, never None)

- export_uv ( bool ) – Export UVs, (optional)

- export_normals ( bool ) – Export Vertex Normals, Include calculated or pre-computed vertex normals (optional)

- export_colors ( Literal [ 'NONE' , 'SRGB' , 'LINEAR' ] ) – Export Vertex Colors, Output per-vertex color attributes (optional)

- NONE
None – Do not import/export color attributes.

- SRGB
sRGB – Vertex colors in the file are in sRGB color space.

- LINEAR
Linear – Vertex colors in the file are in linear color space.

- export_attributes ( bool ) – Export Vertex Attributes, Write user-defined vertex attributes (optional)

- export_triangulated_mesh ( bool ) – Export Triangulated Mesh, Converts all ngons of 4+ vertices to triangles. Meshes in the scene are unaffected. Works like Triangulate with ngon-method: "Beauty", quad-method: "Shortest Diagonal", min vertices: 4 (optional)

- ascii_format ( bool ) – ASCII Format, Output in text-based format; otherwise uses binary (optional)

- filter_glob ( str ) – Extension Filter, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. ply_import ( * , filepath = '' , directory = '' , files = None , check_existing = False , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , global_scale = 1.0 , use_scene_unit = False , forward_axis = 'Y' , up_axis = 'Z' , merge_verts = False , import_colors = 'SRGB' , import_attributes = True , filter_glob = '*.ply' ) 

Loads a PLY file as an object

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

- global_scale ( float ) – Scale, (in [1e-06, 1e+06], optional)

- use_scene_unit ( bool ) – Scene Unit, Incorporates the active scene's scale factor into imported data (optional)

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

- merge_verts ( bool ) – Merge Vertices, Consolidates vertices that are close together (optional)

- import_colors ( Literal [ 'NONE' , 'SRGB' , 'LINEAR' ] ) – Vertex Colors, Read in color attributes at each vertex (optional)

- NONE
None – Do not import/export color attributes.

- SRGB
sRGB – Vertex colors in the file are in sRGB color space.

- LINEAR
Linear – Vertex colors in the file are in linear color space.

- import_attributes ( bool ) – Vertex Attributes, Read in custom vertex attributes (optional)

- filter_glob ( str ) – Extension Filter, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. previews_batch_clear ( * , files = None , directory = '' , filter_blender = True , filter_folder = True , use_scenes = True , use_collections = True , use_objects = True , use_intern_data = True , use_trusted = False , use_backups = True ) 

Clears thumbnails in selected .blend files

Parameters :

- files ( bpy_prop_collection [ OperatorFileListElement ]) – files, (optional)

- directory ( str ) – directory, (optional, never None)

- filter_blender ( bool ) – filter_blender, (optional)

- filter_folder ( bool ) – filter_folder, (optional)

- use_scenes ( bool ) – Scenes, Erase thumbnails for scenes (optional)

- use_collections ( bool ) – Collections, Erase thumbnails for collections (optional)

- use_objects ( bool ) – Objects, Erase thumbnails for objects (optional)

- use_intern_data ( bool ) – Materials & Textures, Remove 'internal' previews (materials, textures, images, etc.) (optional)

- use_trusted ( bool ) – Trusted Blend Files, Enable Python evaluation for selected files (optional)

- use_backups ( bool ) – Save Backups, Keep a backup (.blend1) version of the files when saving with cleared previews (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/file.py:204

bpy.ops.wm. previews_batch_generate ( * , files = None , directory = '' , filter_blender = True , filter_folder = True , use_scenes = True , use_collections = True , use_objects = True , use_intern_data = True , use_trusted = False , use_backups = True ) 

Produces thumbnails in selected .blend files

Parameters :

- files ( bpy_prop_collection [ OperatorFileListElement ]) – Collection of file paths with common directory root (optional)

- directory ( str ) – Root path of all files listed in files collection (optional, never None)

- filter_blender ( bool ) – Show Blender files in the File Browser (optional)

- filter_folder ( bool ) – Show folders in the File Browser (optional)

- use_scenes ( bool ) – Scenes, Create thumbnails for scenes (optional)

- use_collections ( bool ) – Collections, Create thumbnails for collections (optional)

- use_objects ( bool ) – Objects, Create thumbnails for objects (optional)

- use_intern_data ( bool ) – Materials & Textures, Create 'internal' previews (materials, textures, images, etc.) (optional)

- use_trusted ( bool ) – Trusted Blend Files, Enable Python evaluation for selected files (optional)

- use_backups ( bool ) – Save Backups, Keep a backup (.blend1) version of the files when saving with generated previews (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/file.py:95

bpy.ops.wm. previews_clear ( * , id_type = set() ) 

Removes data-block previews (applicable to certain types like objects, materials, textures, etc.)

Parameters :

id_type ( set [ Literal [ 'ALL' , 'GEOMETRY' , 'SHADING' , 'SCENE' , 'COLLECTION' , 'OBJECT' , 'MATERIAL' , 'LIGHT' , 'WORLD' , 'TEXTURE' , 'IMAGE' ] ] ) – Data-Block Type, Specifies which previews to remove (optional)

- ALL
All Types.

- GEOMETRY
All Geometry Types – Clear previews for scenes, collections and objects.

- SHADING
All Shading Types – Clear previews for materials, lights, worlds, textures and images.

- SCENE
Scenes.

- COLLECTION
Collections.

- OBJECT
Objects.

- MATERIAL
Materials.

- LIGHT
Lights.

- WORLD
Worlds.

- TEXTURE
Textures.

- IMAGE
Images.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. previews_ensure ( ) 

Guarantees data-block previews exist and are current (for saving in .blend file; applies to certain types like materials, textures, etc.)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. properties_add ( * , data_path = '' ) 

Register a custom property to a data-block

Parameters :

data_path ( str ) – Property Edit, Property data_path edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:2139

bpy.ops.wm. properties_context_change ( * , context = '' ) 

Navigate to a distinct tab within the properties editor

Parameters :

context ( str ) – Context, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:2182

bpy.ops.wm. properties_edit ( * , data_path = '' , property_name = '' , property_type = 'FLOAT' , is_overridable_library = False , description = '' , use_soft_limits = False , array_length = 3 , default_int = (0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0) , min_int = -10000 , max_int = 10000 , soft_min_int = -10000 , soft_max_int = 10000 , step_int = 1 , default_bool = (False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False) , default_float = (0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0) , min_float = -10000.0 , max_float = -10000.0 , soft_min_float = -10000.0 , soft_max_float = -10000.0 , precision = 3 , step_float = 0.1 , subtype = '' , default_string = '' , id_type = 'OBJECT' , eval_string = '' ) 

Modifies a custom property's format, or adjusts its interface presentation

Parameters :

- data_path ( str ) – Property Edit, Property data_path edit (optional, never None)

- property_name ( str ) – Property Name, Property name edit (optional, never None)

- property_type ( Literal [ 'FLOAT' , '`FLOAT_ARRAY`' , 'INT' , '`INT_ARRAY`' , 'BOOL' , '`BOOL_ARRAY`' , 'STRING' , '`DATA_BLOCK`' , 'PYTHON' ] ) – Type, (optional)

- FLOAT
Float – A single floating-point value.

- `FLOAT_ARRAY`
Float Array – An array of floating-point values.

- INT
Integer – A single integer.

- `INT_ARRAY`
Integer Array – An array of integers.

- BOOL
Boolean – A true or false value.

- `BOOL_ARRAY`
Boolean Array – An array of true or false values.

- STRING
String – A string value.

- `DATA_BLOCK`
Data-Block – A data-block value.

- PYTHON
Python – Edit a Python value directly, for unsupported property types.

- is_overridable_library ( bool ) – Library Overridable, Permits the property to be overridden when the data-block is linked (optional)

- description ( str ) – Description, (optional, never None)

- use_soft_limits ( bool ) – Soft Limits, Constrains the Property Value slider to a specific range; values outside require manual entry (optional)

- array_length ( int ) – Array Length, (in [1, 32], optional)

- default_int ( Sequence [ int ] ) – Default Value, (array of 32 items, in [-inf, inf], optional)

- min_int ( int ) – Min, (in [-inf, inf], optional)

- max_int ( int ) – Max, (in [-inf, inf], optional)

- soft_min_int ( int ) – Soft Min, (in [-inf, inf], optional)

- soft_max_int ( int ) – Soft Max, (in [-inf, inf], optional)

- step_int ( int ) – Step, (in [1, inf], optional)

- default_bool ( Sequence [ bool ] ) – Default Value, (array of 32 items, optional)

- default_float ( Sequence [ float ] ) – Default Value, (array of 32 items, in [-inf, inf], optional)

- min_float ( float ) – Min, (in [-inf, inf], optional)

- max_float ( float ) – Max, (in [-inf, inf], optional)

- soft_min_float ( float ) – Soft Min, (in [-inf, inf], optional)

- soft_max_float ( float ) – Soft Max, (in [-inf, inf], optional)

- precision ( int ) – Precision, (in [0, 8], optional)

- step_float ( float ) – Step, (in [0.001, inf], optional)

- subtype ( str ) – Subtype, (optional)

- default_string ( str ) – Default Value, (optional, never None)

- id_type ( Literal [ 'ACTION' , 'ARMATURE' , 'BRUSH' , 'CACHEFILE' , 'CAMERA' , 'COLLECTION' , 'CURVE' , 'CURVES' , 'FONT' , 'GREASEPENCIL' , '`GREASEPENCIL_V3`' , 'IMAGE' , 'KEY' , 'LATTICE' , 'LIBRARY' , 'LIGHT' , '`LIGHT_PROBE`' , 'LINESTYLE' , 'MASK' , 'MATERIAL' , 'MESH' , 'META' , 'MOVIECLIP' , 'NODETREE' , 'OBJECT' , 'PAINTCURVE' , 'PALETTE' , 'PARTICLE' , 'POINTCLOUD' , 'SCENE' , 'SCREEN' , 'SOUND' , 'SPEAKER' , 'TEXT' , 'TEXTURE' , 'VOLUME' , 'WINDOWMANAGER' , 'WORKSPACE' , 'WORLD' ] ) – ID Type, (optional)

- eval_string ( str ) – Value, Python value for unsupported custom property types (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:1872

bpy.ops.wm. properties_edit_value ( * , data_path = '' , property_name = '' , eval_string = '' ) 

Updates the value of a custom property

Parameters :

- data_path ( str ) – Property Edit, Property data_path edit (optional, never None)

- property_name ( str ) – Property Name, Property name edit (optional, never None)

- eval_string ( str ) – Value, Value for custom property types that can only be edited as a Python expression (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:2096

bpy.ops.wm. properties_remove ( * , data_path = '' , property_name = '' ) 

System-level use (edit a property data_path)

Parameters :

- data_path ( str ) – Property Edit, Property data_path edit (optional, never None)

- property_name ( str ) – Property Name, Property name edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:2196

bpy.ops.wm. quit_blender ( ) 

Exit Blender

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. radial_control ( * , data_path_primary = '' , data_path_secondary = '' , use_secondary = '' , rotation_path = '' , color_path = '' , fill_color_path = '' , fill_color_override_path = '' , fill_color_override_test_path = '' , zoom_path = '' , image_id = '' , secondary_tex = False , release_confirm = False ) 

Adjusts size-related attributes (such as brush radius) using the mouse wheel

Parameters :

- data_path_primary ( str ) – Primary Data Path, Primary path of property to be set by the radial control (optional, never None)

- data_path_secondary ( str ) – Secondary Data Path, Secondary path of property to be set by the radial control (optional, never None)

- use_secondary ( str ) – Use Secondary, Path of property to select between the primary and secondary data paths (optional, never None)

- rotation_path ( str ) – Rotation Path, Path of property used to rotate the texture display (optional, never None)

- color_path ( str ) – Color Path, Path of property used to set the color of the control (optional, never None)

- fill_color_path ( str ) – Fill Color Path, Path of property used to set the fill color of the control (optional, never None)

- fill_color_override_path ( str ) – Fill Color Override Path, (optional, never None)

- fill_color_override_test_path ( str ) – Fill Color Override Test, (optional, never None)

- zoom_path ( str ) – Zoom Path, Path of property used to set the zoom level for the control (optional, never None)

- image_id ( str ) – Image ID, Path of ID that is used to generate an image for the control (optional, never None)

- secondary_tex ( bool ) – Secondary Texture, Modify brush secondary/mask texture (optional)

- release_confirm ( bool ) – Confirm On Release, Finish operation on key release (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. read_factory_settings ( * , use_factory_startup_app_template_only = False , app_template = 'Template' , use_empty = False ) 

Initializes factory-default startup file and settings. To preserve changes, apply "Save Startup File" and "Save Preferences"

Parameters :

- use_factory_startup_app_template_only ( bool ) – Factory Startup App-Template Only, (optional)

- app_template ( str ) – (optional, never None)

- use_empty ( bool ) – Empty, On completion, erase everything except scenes, windows, and workspaces. Permits loading the startup file with its scene structure and window arrangement preserved, minus objects, materials, animations, … (optional)
