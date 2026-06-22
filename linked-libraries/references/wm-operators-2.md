# Wm Operators (part 2)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

Toggle a context value

Parameters :

- data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using accessible windows in the current .blend project) (optional, never None)

- reverse ( bool ) - Reverse, Cycles forward (optional)

- wrap ( bool ) - Wrap, Returns to the start/end settings (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:624

bpy.ops.wm. context_cycle_int ( * , data_path = '' , reverse = False , wrap = False ) 

Establishes a context variable (beneficial for cycling active material, vertex groups, collections, etc.)

Parameters :

- data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using accessible windows in the current .blend project) (optional, never None)

- reverse ( bool ) - Reverse, Cycles forward (optional)

- wrap ( bool ) - Wrap, Returns to the start/end settings (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:584

bpy.ops.wm. context_menu_enum ( * , data_path = '' ) 

Undocumented, consider contributing.

Parameters :

data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using accessible windows in the current .blend project) (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:703

bpy.ops.wm. context_modal_mouse ( * , data_path_iter = '' , data_path_item = '' , header_text = '' , input_scale = 0.01 , invert = False , initial_x = 0 ) 

Modifies arbitrary parameters via mouse interaction

Parameters :

- data_path_iter ( str ) - data_path_iter, Context-relative trajectory, must reference an enumerable group (optional, never None)

- data_path_item ( str ) - data_path_item, Each item's parameter from the enumerable (int or float) (optional, never None)

- header_text ( str ) - Header Text, Display text exhibited in the header during adjustment (optional, never None)

- input_scale ( float ) - input_scale, Multiplier for cursor movement before calculating the adjustment (in [-inf, inf], optional)

- invert ( bool ) - invert, Reverses the mouse motion (optional)

- initial_x ( int ) - initial_x, (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:1014

bpy.ops.wm. context_pie_enum ( * , data_path = '' ) 

Undocumented, consider contributing.

Parameters :

data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using accessible windows in the current .blend project) (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:735

bpy.ops.wm. context_scale_float ( * , data_path = '' , value = 1.0 ) 

Multiplies a float context variable

Parameters :

- data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using visible windows in the current .blend project) (optional, never None)

- value ( float ) - Value, Specifies the multiplier (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:338

bpy.ops.wm. context_scale_int ( * , data_path = '' , value = 1.0 , always_step = True ) 

Multiplies an int context variable

Parameters :

- data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using visible windows in the current .blend project) (optional, never None)

- value ( float ) - Value, Specifies the multiplier (in [-inf, inf], optional)

- always_step ( bool ) - Always Step, Guarantees modification by a minimum of 1 when 'value' is not 1.0 (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:376

bpy.ops.wm. context_set_boolean ( * , data_path = '' , value = True ) 

Assigns a context variable

Parameters :

- data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using visible windows in the current .blend project) (optional, never None)

- value ( bool ) - Value, Intended value (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:267

bpy.ops.wm. context_set_enum ( * , data_path = '' , value = '' ) 

Assigns a context variable

Parameters :

- data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using visible windows in the current .blend project) (optional, never None)

- value ( str ) - Value, Intended value (as a string) (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:267

bpy.ops.wm. context_set_float ( * , data_path = '' , value = 0.0 , relative = False ) 

Assigns a context variable

Parameters :

- data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using visible windows in the current .blend project) (optional, never None)

- value ( float ) - Value, Intended value (in [-inf, inf], optional)

- relative ( bool ) - Relative, Adds to the current variable (delta) (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:267

bpy.ops.wm. context_set_id ( * , data_path = '' , value = '' ) 

Assigns a context variable to a data component

Parameters :

- data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using visible windows in the current .blend project) (optional, never None)

- value ( str ) - Value, Intended value (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:817

bpy.ops.wm. context_set_int ( * , data_path = '' , value = 0 , relative = False ) 

Assigns a context variable

Parameters :

- data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using visible windows in the current .blend project) (optional, never None)

- value ( int ) - Value, Intended value (in [-inf, inf], optional)

- relative ( bool ) - Relative, Adds to the current variable (delta) (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:267

bpy.ops.wm. context_set_string ( * , data_path = '' , value = '' )

Assigns a context variable

Parameters :

- data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using visible windows in the current .blend project) (optional, never None)

- value ( str ) - Value, Intended value (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:267

bpy.ops.wm. context_set_value ( * , data_path = '' , value = '' ) 

Assigns a context variable

Parameters :

- data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using visible windows in the current .blend project) (optional, never None)

- value ( str ) - Value, Intended value (as a string) (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:480

bpy.ops.wm. context_toggle ( * , data_path = '' , module = '' ) 

Reverses a context variable

Parameters :

- data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using visible windows in the current .blend project) (optional, never None)

- module ( str ) - Module, Optionally substitute the setting with a module (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:504

bpy.ops.wm. context_toggle_enum ( * , data_path = '' , value_1 = '' , value_2 = '' ) 

Reverses a context variable

Parameters :

- data_path ( str ) - Context Attributes, Context parameter-trajectory (expanded using visible windows in the current .blend project) (optional, never None)

- value_1 ( str ) - Value, Alternate option (optional, never None)

- value_2 ( str ) - Value, Alternate option (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:545

bpy.ops.wm. debug_menu ( * , debug_value = 0 ) 

Displays a popup for configuring the debug level

Parameters :

debug_value ( int ) - Debug Value, (in [-32768, 32767], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. doc_view ( * , doc_id = '' ) 

Launches online API documentation in the default web browser

Parameters :

doc_id ( str ) - Doc ID, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:1361

bpy.ops.wm. doc_view_manual ( * , doc_id = '' ) 

Loads online guide content

Parameters :

doc_id ( str ) - Doc ID, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:1334

bpy.ops.wm. doc_view_manual_ui_context ( ) 

Displays context-based documentation in the default web browser

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. drop_blend_file ( * , filepath = '' ) 

Undocumented, consider contributing.

Parameters :

filepath ( str ) - filepath, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/wm.py:3658

bpy.ops.wm. drop_import_file ( * , directory = '' , files = None ) 

Facilitates file handlers in receiving dropped files

Parameters :

- directory ( str ) - Directory, Folder containing the file (optional, never None)

- files ( bpy_prop_collection [ OperatorFileListElement ]) - Files, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. fbx_import ( * , filepath = '' , directory = '' , files = None , check_existing = False , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , global_scale = 1.0 , mtl_name_collision_mode = '`MAKE_UNIQUE`' , import_colors = 'SRGB' , use_custom_normals = True , use_custom_props = True , use_custom_props_enum_as_string = True , import_subdivision = False , ignore_leaf_bones = False , validate_meshes = True , use_anim = True , anim_offset = 1.0 , filter_glob = '*.fbx' ) 

Ingests an FBX file into the current composition

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

- global_scale ( float ) - Scale, (in [1e-06, 1e+06], optional)

- mtl_name_collision_mode ( Literal [ '`MAKE_UNIQUE`' , '`REFERENCE_EXISTING`' ] ) - Material Name Collision, Conduct when an imported material shares a name with an existing material (optional)

- `MAKE_UNIQUE`
Make Unique - Adds each FBX material as a separate Blender material.

- `REFERENCE_EXISTING`
Reference Existing - When a material shares the same name, links to the existing one rather than importing a copy.

- import_colors ( Literal [ 'NONE' , 'SRGB' , 'LINEAR' ] ) - Vertex Colors, Ingests vertex color information (optional)

- NONE
None - Disables color attribute import.

- SRGB
sRGB - Vertex colors present in sRGB color space.

- LINEAR
Linear - Vertex colors present in linear color space.

- use_custom_normals ( bool ) - Custom Normals, Ingests personalized normals, or Blender will generate them (optional)

- use_custom_props ( bool ) - Custom Properties, Ingests user-defined characteristics as personalized variables (optional)

- use_custom_props_enum_as_string ( bool ) - Enums As Strings, Stores customized enumeration settings as words (optional)

- import_subdivision ( bool ) - Subdivision Data, Ingests FBX subdivision information as surface refinement modifiers (optional)

- ignore_leaf_bones ( bool ) - Ignore Leaf Bones, Disregards the final bone in each sequence (used to denote the size of the preceding bone) (optional)

- validate_meshes ( bool ) - Validate Meshes, Guarantees the structure is sound (when disabled, geometry might be imported causing application crashes during display or modification) (optional)

- use_anim ( bool ) - Import Animation, Ingests FBX motion sequences (optional)

- anim_offset ( float ) - Offset, Time displacement to apply to motion sequences, in frames (in [-1e+06, 1e+06], optional)

- filter_glob ( str ) - Extension Filter, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. grease_pencil_export_pdf ( * , filepath = '' , check_existing = True , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = True , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , use_fill = True , selected_object_type = 'ACTIVE' , frame_mode = 'ACTIVE' , stroke_sample = 0.0 , use_uniform_width = False ) 

Outputs Grease Pencil as a PDF document

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

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. grease_pencil_export_svg ( * , filepath = '' , check_existing = True , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = True , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , display_type = 'DEFAULT' , sort_method = '' , use_fill = True , selected_object_type = 'ACTIVE' , frame_mode = 'ACTIVE' , stroke_sample = 0.0 , use_uniform_width = False , use_clip_camera = False )
