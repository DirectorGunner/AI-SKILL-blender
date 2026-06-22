# Wm Operators (part 7)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

Pops up a search for a menu in the current context.
Parameters:
- menu_idname ( str ) – Menu Name, Menu to search in (optional, never None)
- initial_query ( str ) – Initial Query, Query to insert into the search box (optional, never None)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.wm. set_stereo_3d ( * , display_mode = 'ANAGLYPH' , anaglyph_type = '`RED_CYAN`' , interlace_type = '`ROW_INTERLEAVED`' , use_interlace_swap = False , use_sidebyside_crosseyed = False )
Toggles 3D stereo support for the current window (or changes the display mode).
Parameters:
- display_mode (Literal[Stereo3D Display Items]) – Display Mode, (optional)
- anaglyph_type (Literal[Stereo3D Anaglyph Type Items]) – Anaglyph Type, (optional)
- interlace_type (Literal[Stereo3D Interlace Type Items]) – Interlace Type, (optional)
- use_interlace_swap ( bool ) – Swap Left/Right, Swap left and right stereo channels (optional)
- use_sidebyside_crosseyed ( bool ) – Cross-Eyed, Right eye should see left image and vice versa (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.wm. set_working_color_space ( * , convert_colors = True , working_space = '' )
Changes the working color space of all colors in this blend file.
Parameters:
- convert_colors ( bool ) – Convert Colors in All Data-blocks, Change colors in all data-blocks to the new working space (optional)
- working_space ( str ) – Working Space, Color space to set (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.wm. splash ( )
Opens the splash screen with release info.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.wm. splash_about ( )
Opens a window with information about Blender.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.wm. stl_export ( * , filepath = '' , check_existing = True , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , ascii_format = False , use_batch = False , export_selected_objects = False , collection = '' , global_scale = 1.0 , use_scene_unit = False , forward_axis = 'Y' , up_axis = 'Z' , apply_modifiers = True , filter_glob = '*.stl' )
Saves the scene to an STL file.
Parameters:
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
- DEFAULT — Default: automatically determine the display type for files.
- `LIST_VERTICAL` — Short List: display files as a short list.
- `LIST_HORIZONTAL` — Long List: display files as a detailed list.
- THUMBNAIL — Thumbnails: display files as thumbnails.
- sort_method ( str ) – File sorting mode, (optional)
- ascii_format ( bool ) – ASCII Format, Export file in ASCII format, export as binary otherwise (optional)
- use_batch ( bool ) – Batch Export, Export each object to a separate file (optional)
- export_selected_objects ( bool ) – Export Selected Objects, Export only selected objects instead of all supported objects (optional)
- collection ( str ) – Source Collection, Export only objects from this collection (and its children) (optional, never None)
- global_scale ( float ) – Scale, (in [1e-06, 1e+06], optional)
- use_scene_unit ( bool ) – Scene Unit, Apply current scene's unit (as defined by unit scale) to exported data (optional)
- forward_axis ( Literal [ 'X' , 'Y' , 'Z' , '`NEGATIVE_X`' , '`NEGATIVE_Y`' , '`NEGATIVE_Z`' ] ) – Forward Axis, (optional)
- X — X: positive X axis.
- Y — Y: positive Y axis.
- Z — Z: positive Z axis.
- `NEGATIVE_X` — -X: negative X axis.
- `NEGATIVE_Y` — -Y: negative Y axis.
- `NEGATIVE_Z` — -Z: negative Z axis.
- up_axis ( Literal [ 'X' , 'Y' , 'Z' , '`NEGATIVE_X`' , '`NEGATIVE_Y`' , '`NEGATIVE_Z`' ] ) – Up Axis, (optional)
- X — X: positive X axis.
- Y — Y: positive Y axis.
- Z — Z: positive Z axis.
- `NEGATIVE_X` — -X: negative X axis.
- `NEGATIVE_Y` — -Y: negative Y axis.
- `NEGATIVE_Z` — -Z: negative Z axis.
- apply_modifiers ( bool ) – Apply Modifiers, Apply modifiers to exported meshes (optional)
- filter_glob ( str ) – Extension Filter, (optional, never None)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.wm. stl_import ( * , filepath = '' , directory = '' , files = None , check_existing = False , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , global_scale = 1.0 , use_scene_unit = False , use_facet_normal = False , forward_axis = 'Y' , up_axis = 'Z' , use_mesh_validate = True , filter_glob = '*.stl' )

Bring in an STL file as an object

Parameters :

- filepath ( str ) – File Path, Location to the file (optional, never None)

- directory ( str ) – Directory, Folder of the file (optional, never None)

- files ( bpy_prop_collection [ OperatorFileListElement ]) – Files, (optional)

- check_existing ( bool ) – Check Existing, Verify and caution when writing over files (optional)

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

- filemode ( int ) – File Browser Mode, Settings for the file browser type to open a .blend file, a library or particular file (in [1, 9], optional)

- display_type ( Literal [ 'DEFAULT' , '`LIST_VERTICAL`' , '`LIST_HORIZONTAL`' , 'THUMBNAIL' ] ) – Display Type, (optional)

- DEFAULT
Default – Determine display format for files automatically.

- `LIST_VERTICAL`
Short List – Show files in a concise list arrangement.

- `LIST_HORIZONTAL`
Long List – Show files with more information in a detailed layout.

- THUMBNAIL
Thumbnails – Show files as image previews.

- sort_method ( str ) – File sorting mode, (optional)

- global_scale ( float ) – Scale, (in [1e-06, 1e+06], optional)

- use_scene_unit ( bool ) – Scene Unit, Use current scene's unit scale (as specified by unit measurement) on brought-in content (optional)

- use_facet_normal ( bool ) – Facet Normals, Utilize (importing) facet normals (note that this will still yield flat shading) (optional)

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

- use_mesh_validate ( bool ) – Validate Mesh, Ensure the data is valid (when disabled, imported content may be problematic causing slowdowns or crashes when interacting with or presenting) (optional)

- filter_glob ( str ) – Extension Filter, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. sysinfo ( * , filepath = '' ) 

Gather system specification details, sent to a document

Parameters :

filepath ( str ) – filepath, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:2225

bpy.ops.wm. tool_set_by_brush_type ( * , brush_type = '' , space_type = 'EMPTY' ) 

Identify the fitting tool for this brush category then turn it on

Parameters :

- brush_type ( str ) – Brush Type, Category identifier for the appropriate tool will be discovered (optional, never None)

- space_type ( Literal [ 'EMPTY' , '`VIEW_3D`' , '`IMAGE_EDITOR`' , '`NODE_EDITOR`' , '`SEQUENCE_EDITOR`' , '`CLIP_EDITOR`' , '`DOPESHEET_EDITOR`' , '`GRAPH_EDITOR`' , '`NLA_EDITOR`' , '`TEXT_EDITOR`' , 'CONSOLE' , 'INFO' , 'TOPBAR' , 'STATUSBAR' , 'OUTLINER' , 'PROPERTIES' , '`FILE_BROWSER`' , 'SPREADSHEET' , 'PREFERENCES' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:2439

bpy.ops.wm. tool_set_by_id ( * , name = '' , cycle = False , as_fallback = False , space_type = 'EMPTY' ) 

Pick the tool based on label (to be used with input maps)

Parameters :

- name ( str ) – Identifier, Code reference of the tool (optional, never None)

- cycle ( bool ) – Cycle, Switch among instruments in this collection (optional)

- as_fallback ( bool ) – Set Fallback, Establish the alternate tool rather than the main tool (optional)

- space_type ( Literal [ 'EMPTY' , '`VIEW_3D`' , '`IMAGE_EDITOR`' , '`NODE_EDITOR`' , '`SEQUENCE_EDITOR`' , '`CLIP_EDITOR`' , '`DOPESHEET_EDITOR`' , '`GRAPH_EDITOR`' , '`NLA_EDITOR`' , '`TEXT_EDITOR`' , 'CONSOLE' , 'INFO' , 'TOPBAR' , 'STATUSBAR' , 'OUTLINER' , 'PROPERTIES' , '`FILE_BROWSER`' , 'SPREADSHEET' , 'PREFERENCES' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:2348

bpy.ops.wm. tool_set_by_index ( * , index = 0 , cycle = False , expand = True , as_fallback = False , space_type = 'EMPTY' ) 

Activate the instrument by its slot number (to be used with shortcuts)

Parameters :

- index ( int ) – Index in Toolbar, (in [-inf, inf], optional)

- cycle ( bool ) – Cycle, Switch among tools in this set (optional)

- expand ( bool ) – expand, Allow tool subdivisions (optional)

- as_fallback ( bool ) – Set Fallback, Make the secondary tool active rather than principal (optional)

- space_type ( Literal [ 'EMPTY' , '`VIEW_3D`' , '`IMAGE_EDITOR`' , '`NODE_EDITOR`' , '`SEQUENCE_EDITOR`' , '`CLIP_EDITOR`' , '`DOPESHEET_EDITOR`' , '`GRAPH_EDITOR`' , '`NLA_EDITOR`' , '`TEXT_EDITOR`' , 'CONSOLE' , 'INFO' , 'TOPBAR' , 'STATUSBAR' , 'OUTLINER' , 'PROPERTIES' , '`FILE_BROWSER`' , 'SPREADSHEET' , 'PREFERENCES' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:2398

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:2398

bpy.ops.wm. toolbar ( ) 

Not yet described, submissions welcome.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:2506

bpy.ops.wm. toolbar_fallback_pie ( ) 

Not yet described, submissions welcome.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:2530

bpy.ops.wm. toolbar_prompt ( ) 

Quick-access capability mimicking a leader command for tool activation

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:2630

bpy.ops.wm. url_open ( * , url = '' ) 

Bring up a page in the default web viewer

Parameters :

url ( str ) – URL, Address to browse (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:1074

bpy.ops.wm. url_open_preset ( * , type = '' ) 

Bring up a common page in the default web viewer

Parameters :

type ( str ) – Site, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:1144

bpy.ops.wm. usd_export ( * , filepath = '' , check_existing = True , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = True , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , filter_glob = '*.usd' , selected_objects_only = False , collection = '' , export_animation = False , export_hair = False , export_uvmaps = True , rename_uvmaps = True , export_mesh_colors = True , export_normals = True , export_materials = True , export_subdivision = '`BEST_MATCH`' , export_armatures = True , only_deform_bones = False , export_shapekeys = True , use_instancing = False , evaluation_mode = 'RENDER' , generate_preview_surface = True , generate_materialx_network = False , convert_orientation = False , export_global_forward_selection = '`NEGATIVE_Z`' , export_global_up_selection = 'Y' , export_textures_mode = 'NEW' , overwrite_textures = False , relative_paths = True , xform_op_mode = 'TRS' , root_prim_path = '/root' , export_custom_properties = True , custom_properties_namespace = 'userProperties' , accessibility_label = '' , accessibility_description = '' , author_blender_name = True , convert_world_material = True , allow_unicode = True , export_meshes = True , export_lights = True , export_cameras = True , export_curves = True , export_points = True , export_volumes = True , triangulate_meshes = False , quad_method = '`SHORTEST_DIAGONAL`' , ngon_method = 'BEAUTY' , usdz_downscale_size = 'KEEP' , usdz_downscale_custom_size = 128 , merge_parent_xform = False , convert_scene_units = 'METERS' , meters_per_unit = 1.0 ) 

Ship the current composition as a USD storage file

Parameters :

- filepath ( str ) – File Path, Location to file (optional, never None)

- check_existing ( bool ) – Check Existing, Verify and warn when writing over files (optional)

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

- filemode ( int ) – File Browser Mode, Configuration for the file browser type to open a .blend file, a library or specific file (in [1, 9], optional)

- display_type ( Literal [ 'DEFAULT' , '`LIST_VERTICAL`' , '`LIST_HORIZONTAL`' , 'THUMBNAIL' ] ) – Display Type, (optional)

- DEFAULT
Default – Identify display method for files automatically.

- `LIST_VERTICAL`
Short List – Show files in a brief list view.

- `LIST_HORIZONTAL`
Long List – Show files in a comprehensive tabular format.

- THUMBNAIL
Thumbnails – Show files as icon previews.

- sort_method ( str ) – File sorting mode, (optional)

- filter_glob ( str ) – (optional, never None)

- selected_objects_only ( bool ) – Selection Only, Ship only chosen things. Hidden ancestors of picked things are written as bare translate (optional)

- collection ( str ) – Collection, (optional, never None)

- export_animation ( bool ) – Animation, Ship all frames in the render frame set, rather than just the now frame (optional)

- export_hair ( bool ) – Hair, Ship hair particle arrays as USD lines (optional)

- export_uvmaps ( bool ) – UV Maps, Put all surface shade coordinates in the shipped file (optional)

- rename_uvmaps ( bool ) – Rename UV Maps, Rename main render shade coordinate to "st" to match USD rules (optional)

- export_mesh_colors ( bool ) – Color Attributes, Put surface hue properties in the shipped data (optional)

- export_normals ( bool ) – Normals, Add regular vectors for shipped meshes to the data (optional)

- export_materials ( bool ) – Materials, Transmit viewport configuration of materials as USD review materials, and transmit material links as shape subsets (optional)

- export_subdivision ( Literal [ 'IGNORE' , 'TESSELLATE' , '`BEST_MATCH`' ] ) – Subdivision, Pick how subdivision changes get mapped to the USD subdivision type on transmit (optional)

- IGNORE
Ignore – Scheme = None. Write foundation mesh no subdivision.

- TESSELLATE
Tessellate – Scheme = None. Write subdivided mesh.

- `BEST_MATCH`
Best Match – Scheme = Catmull-Clark, as feasible. Reverts to writing the subdivided mesh for the Basic subdivision classification.

- export_armatures ( bool ) – Armatures, Write joint systems and meshes with joint changes as USD joint structures and shaped meshes (optional)
