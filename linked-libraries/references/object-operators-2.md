# Object Operators (part 2)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. curves_random_add ( * , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Introduce a curves entity containing arbitrary curve data to the viewport

Parameters :

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. data_instance_add ( * , name = '' , session_uid = 0 , type = 'ACTION' , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) , drop_x = 0 , drop_y = 0 ) 

Introduce an entity representation duplicate

Parameters :

- name ( str ) – Name, Name of the data-block to use by the operator (optional, never None)

- session_uid ( int ) – Session UID, Session UID of the data-block to use by the operator (in [-inf, inf], optional)

- type (Literal[Id Type Items]) – Type, (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

- drop_x ( int ) – Drop X, X-coordinate (screen space) to place the new object under (in [-inf, inf], optional)

- drop_y ( int ) – Drop Y, Y-coordinate (screen space) to place the new object under (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. data_transfer ( * , use_reverse_transfer = False , use_freeze = False , data_type = '`VGROUP_WEIGHTS`' , use_create = True , vert_mapping = 'NEAREST' , edge_mapping = 'NEAREST' , loop_mapping = '`NEAREST_POLYNOR`' , poly_mapping = 'NEAREST' , use_auto_transform = False , use_object_transform = True , use_max_distance = False , max_distance = 1.0 , ray_radius = 0.0 , islands_precision = 0.1 , layers_select_src = 'ACTIVE' , layers_select_dst = 'ACTIVE' , mix_mode = 'REPLACE' , mix_factor = 1.0 ) 

Distribute structure layer(s) (weights, edge boundary, etc.) from highlighted to chose meshes

Parameters :

- use_reverse_transfer ( bool ) – Reverse Transfer, Transfer from selected objects to active one (optional)

- use_freeze ( bool ) – Freeze Operator, Prevent changes to settings to re-run the operator, handy to change several things at once with heavy geometry (optional)

- data_type ( Literal [ '`VGROUP_WEIGHTS`' , '`BEVEL_WEIGHT_VERT`' , '`COLOR_VERTEX`' , '`SHARP_EDGE`' , 'SEAM' , 'CREASE' , '`BEVEL_WEIGHT_EDGE`' , '`FREESTYLE_EDGE`' , '`CUSTOM_NORMAL`' , '`COLOR_CORNER`' , 'UV' , 'SMOOTH' , '`FREESTYLE_FACE`' ] ) – Data Type, Which data to transfer (optional)

- `VGROUP_WEIGHTS`
Vertex Group(s) – Transfer active or all vertex groups.

- `BEVEL_WEIGHT_VERT`
Bevel Weight – Transfer bevel weights.

- `COLOR_VERTEX`
Colors – Color Attributes.

- `SHARP_EDGE`
Sharp – Transfer sharp mark.

- SEAM
UV Seam – Transfer UV seam mark.

- CREASE
Subdivision Crease – Transfer crease values.

- `BEVEL_WEIGHT_EDGE`
Bevel Weight – Transfer bevel weights.

- `FREESTYLE_EDGE`
Freestyle Mark – Transfer Freestyle edge mark.

- `CUSTOM_NORMAL`
Custom Normals – Transfer custom normals.

- `COLOR_CORNER`
Colors – Color Attributes.

- UV
UVs – Transfer UV layers.

- SMOOTH
Smooth – Transfer flat/smooth mark.

- `FREESTYLE_FACE`
Freestyle Mark – Transfer Freestyle face mark.

- use_create ( bool ) – Create Data, Add data layers on destination meshes if needed (optional)

- vert_mapping (Literal[Dt Method Vertex Items]) – Vertex Mapping, Method used to map source vertices to destination ones (optional)

- edge_mapping (Literal[Dt Method Edge Items]) – Edge Mapping, Method used to map source edges to destination ones (optional)

- loop_mapping (Literal[Dt Method Loop Items]) – Face Corner Mapping, Method used to map source faces' corners to destination ones (optional)

- poly_mapping (Literal[Dt Method Poly Items]) – Face Mapping, Method used to map source faces to destination ones (optional)

- use_auto_transform ( bool ) – Auto Transform, Automatically compute transformation to get the best possible match between source and destination meshes.Warning: Results will never be as good as manual matching of objects(optional)

- use_object_transform ( bool ) – Object Transform, Evaluate source and destination meshes in global space (optional)

- use_max_distance ( bool ) – Only Neighbor Geometry, Source elements must be closer than given distance from destination one (optional)

- max_distance ( float ) – Max Distance, Maximum allowed distance between source and destination element, for non-topology mappings (in [0, inf], optional)

- ray_radius ( float ) – Ray Radius, 'Width' of rays (especially useful when raycasting against vertices or edges) (in [0, inf], optional)

- islands_precision ( float ) – Islands Precision, Factor controlling precision of islands handling (the higher, the better the results) (in [0, 10], optional)

- layers_select_src (Literal[Dt Layers Select Src Items]) – Source Layers Selection, Which layers to transfer, in case of multi-layers types (optional)

- layers_select_dst (Literal[Dt Layers Select Dst Items]) – Destination Layers Matching, How to match source and destination layers (optional)

- mix_mode (Literal[Dt Mix Mode Items]) – Mix Mode, How to affect destination elements with source values (optional)

- mix_factor ( float ) – Mix Factor, Factor to use when applying data to destination (exact behavior depends on mix mode) (in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. datalayout_transfer ( * , modifier = '' , data_type = '' , use_delete = False , layers_select_src = 'ACTIVE' , layers_select_dst = 'ACTIVE' ) 

Distribute schematic of structure layer(s) from highlighted to chose meshes

Parameters :

- modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

- data_type ( Literal [ '`VGROUP_WEIGHTS`' , '`BEVEL_WEIGHT_VERT`' , '`COLOR_VERTEX`' , '`SHARP_EDGE`' , 'SEAM' , 'CREASE' , '`BEVEL_WEIGHT_EDGE`' , '`FREESTYLE_EDGE`' , '`CUSTOM_NORMAL`' , '`COLOR_CORNER`' , 'UV' , 'SMOOTH' , '`FREESTYLE_FACE`' ] ) – Data Type, Which data to transfer (optional)

- `VGROUP_WEIGHTS`
Vertex Group(s) – Transfer active or all vertex groups.

- `BEVEL_WEIGHT_VERT`
Bevel Weight – Transfer bevel weights.

- `COLOR_VERTEX`
Colors – Color Attributes.

- `SHARP_EDGE`
Sharp – Transfer sharp mark.

- SEAM
UV Seam – Transfer UV seam mark.

- CREASE
Subdivision Crease – Transfer crease values.

- `BEVEL_WEIGHT_EDGE`
Bevel Weight – Transfer bevel weights.

- `FREESTYLE_EDGE`
Freestyle Mark – Transfer Freestyle edge mark.

- `CUSTOM_NORMAL`
Custom Normals – Transfer custom normals.

- `COLOR_CORNER`
Colors – Color Attributes.

- UV
UVs – Transfer UV layers.

- SMOOTH
Smooth – Transfer flat/smooth mark.

- `FREESTYLE_FACE`
Freestyle Mark – Transfer Freestyle face mark.

- use_delete ( bool ) – Exact Match, Also delete some data layers from destination if necessary, so that it matches exactly source (optional)

- layers_select_src (Literal[Dt Layers Select Src Items]) – Source Layers Selection, Which layers to transfer, in case of multi-layers types (optional)

- layers_select_dst (Literal[Dt Layers Select Dst Items]) – Destination Layers Matching, How to match source and destination layers (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. delete ( * , use_global = False , confirm = True ) 

Erase chose entities

Parameters :

- use_global ( bool ) – Delete Globally, Remove object from all scenes (optional)

- confirm ( bool ) – Confirm, Prompt for confirmation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. delete_fix_to_camera_keys ( ) 

Erase all control points that were developed by the 'Fix to Scene Camera' task

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/copy_global_transform.py:639

bpy.ops.object. drop_geometry_nodes ( * , session_uid = 0 , show_datablock_in_modifier = True ) 

Undocumented, consider contributing.

Parameters :

- session_uid ( int ) – Session UID, Session UID of the geometry node group being dropped (in [-inf, inf], optional)

- show_datablock_in_modifier ( bool ) – Show the data-block selector in the modifier, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. drop_named_material ( * , name = '' , session_uid = 0 ) 

Undocumented, consider contributing.

Parameters :

- name ( str ) – Name, Name of the data-block to use by the operator (optional, never None)

- session_uid ( int ) – Session UID, Session UID of the data-block to use by the operator (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. duplicate ( * , linked = False , mode = 'TRANSLATION' ) 

Replicate chose entities

Parameters :

- linked ( bool ) – Linked, Duplicate object but not object data, linking to the original data (optional)

- mode (Literal[Transform Mode Type Items]) – Mode, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. duplicate_move ( * , `OBJECT_OT`_duplicate = {} , `TRANSFORM_OT`_translate = {} ) 

Replicate the chose entities and shift them

Parameters :

- `OBJECT_OT`_duplicate ( dict [ str , Any ] ) – Duplicate Objects, Replicate chose entities (optional, bpy.ops.object.duplicate() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. duplicate_move_linked ( * , `OBJECT_OT`_duplicate = {} , `TRANSFORM_OT`_translate = {} ) 

Replicate the chose entities, excluding their representation, and shift them

Parameters :

- `OBJECT_OT`_duplicate ( dict [ str , Any ] ) – Duplicate Objects, Replicate chose entities (optional, bpy.ops.object.duplicate() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. duplicates_make_real ( * , use_base_parent = False , use_hierarchy = False ) 

Transform instanced entities connected to this entity into originals

Parameters :

- use_base_parent ( bool ) – Parent, Parent newly created objects to the original instancer (optional)

- use_hierarchy ( bool ) – Keep Hierarchy, Maintain parent child relationships (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. editmode_toggle ( ) 

Switch entity's alteration mode

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. effector_add ( * , type = 'FORCE' , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Introduce a blank entity housing a force mechanism to the viewport

Parameters :

- type ( Literal [ 'FORCE' , 'WIND' , 'VORTEX' , 'MAGNET' , 'HARMONIC' , 'CHARGE' , 'LENNARDJ' , 'TEXTURE' , 'GUIDE' , 'BOID' , 'TURBULENCE' , 'DRAG' , 'FLUID' ] ) – Type, (optional)

- radius ( float ) – Radius, (in [0, inf], optional)

- enter_editmode ( bool ) – Enter Edit Mode, Enter edit mode when adding this object (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. empty_add ( * , type = '`PLAIN_AXES`' , radius = 1.0 , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Introduce a blank entity to the viewport

Parameters :

- type (Literal[Object Empty Drawtype Items]) – Type, (optional)

- radius ( float ) – Radius, (in [0, inf], optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. empty_image_add ( * , filepath = '' , hide_props_region = True , check_existing = False , filter_blender = False , filter_backup = False , filter_image = True , filter_movie = True , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 9 , relative_path = True , show_multiview = False , use_multiview = False , display_type = 'DEFAULT' , sort_method = '' , name = '' , session_uid = 0 , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) , background = False ) 

Introduce a blank visual representation asset to environment with matter

Parameters :

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

- relative_path ( bool ) – Relative Path, Select the file relative to the blend file (optional)

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

- sort_method ( Literal [ 'DEFAULT' , '`FILE_SORT_ALPHA`' , '`FILE_SORT_EXTENSION`' , '`FILE_SORT_TIME`' , '`FILE_SORT_SIZE`' , '`ASSET_CATALOG`' ] ) – File sorting mode, (optional)

- DEFAULT
Default – Automatically determine sort method for files.

- `FILE_SORT_ALPHA`
Name – Sort the file list alphabetically.

- `FILE_SORT_EXTENSION`
Extension – Sort the file list by extension/type.

- `FILE_SORT_TIME`
Modified Date – Sort files by modification time.

- `FILE_SORT_SIZE`
Size – Sort files by size.

- `ASSET_CATALOG`
Asset Catalog – Sort the asset list so that assets in the same catalog are kept together. Within a single catalog, assets are ordered by name. The catalogs are in order of the flattened catalog hierarchy..

- name ( str ) – Name, Name of the data-block to use by the operator (optional, never None)

- session_uid ( int ) – Session UID, Session UID of the data-block to use by the operator (in [-inf, inf], optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.
