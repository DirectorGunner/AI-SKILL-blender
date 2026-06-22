# Object Operators (part 1)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

### Object Operators 

bpy.ops.object. add ( * , radius = 1.0 , type = 'EMPTY' , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Introduce an entity to the viewport

Parameters :

- radius ( float ) – Radius, (in [0, inf], optional)

- type (Literal[Object Type Items]) – Type, (optional)

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

bpy.ops.object. add_modifier_menu ( ) 

Undocumented, consider contributing.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_ui/properties_data_modifier.py:303

bpy.ops.object. add_named ( * , linked = False , name = '' , session_uid = 0 , matrix = ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)) , drop_x = 0 , drop_y = 0 ) 

Introduce a named entity

Parameters :

- linked ( bool ) – Linked, Duplicate object but not object data, linking to the original data (optional)

- name ( str ) – Name, Name of the data-block to use by the operator (optional, never None)

- session_uid ( int ) – Session UID, Session UID of the data-block to use by the operator (in [-inf, inf], optional)

- matrix (mathutils.Matrix) – Matrix, (multi-dimensional array of 4 * 4 items, in [-inf, inf], optional)

- drop_x ( int ) – Drop X, X-coordinate (screen space) to place the new object under (in [-inf, inf], optional)

- drop_y ( int ) – Drop Y, Y-coordinate (screen space) to place the new object under (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. align ( * , bb_quality = True , align_mode = '`OPT_2`' , relative_to = '`OPT_4`' , align_axis = set() ) 

Position entities consistently

Parameters :

- bb_quality ( bool ) – High Quality, Enables high quality but slow calculation of the bounding box for perfect results on complex shape meshes with rotation/scale (optional)

- align_mode ( Literal [ '`OPT_1`' , '`OPT_2`' , '`OPT_3`' ] ) – Align Mode, Side of object to use for alignment (optional)

- relative_to ( Literal [ '`OPT_1`' , '`OPT_2`' , '`OPT_3`' , '`OPT_4`' ] ) – Relative To, Reference location to align to (optional)

- `OPT_1`
Scene Origin – Use the scene origin as the position for the selected objects to align to.

- `OPT_2`
3D Cursor – Use the 3D cursor as the position for the selected objects to align to.

- `OPT_3`
Selection – Use the selected objects as the position for the selected objects to align to.

- `OPT_4`
Active – Use the active object as the position for the selected objects to align to.

- align_axis ( set [ Literal [ 'X' , 'Y' , 'Z' ] ] ) – Align, Align to axis (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object_align.py:386

bpy.ops.object. anim_transforms_to_deltas ( ) 

Reframe entity animation for standard movements as differential movements

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object.py:839

bpy.ops.object. armature_add ( * , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Introduce an armature entity to the viewport

Parameters :

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

bpy.ops.object. assign_property_defaults ( * , process_data = True , process_bones = True ) 

Register the present values of custom features as their foundation, for implementation as element of the relaxed stance arrangement in NLA path blending

Parameters :

- process_data ( bool ) – Process data properties, (optional)

- process_bones ( bool ) – Process bone properties, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object.py:1001

bpy.ops.object. bake ( * , type = 'COMBINED' , pass_filter = set() , filepath = '' , width = 512 , height = 512 , margin = 16 , margin_type = 'EXTEND' , use_selected_to_active = False , max_ray_distance = 0.0 , cage_extrusion = 0.0 , cage_object = '' , normal_space = 'TANGENT' , normal_r = '`POS_X`' , normal_g = '`POS_Y`' , normal_b = '`POS_Z`' , target = '`IMAGE_TEXTURES`' , save_mode = 'INTERNAL' , use_clear = False , use_cage = False , use_split_materials = False , use_automatic_name = False , uv_layer = '' )

Process surface appearance information for chosen objects

Parameters :

- type (Literal[Bake Pass Type Items]) – Type, Type of pass to bake, some of them may not be supported by the current render engine (optional)

- pass_filter (set[Literal[Bake Pass Filter Type Items]]) – Pass Filter, Filter to combined, diffuse, glossy, transmission and subsurface passes (optional)

- filepath ( str ) – File Path, Image filepath to use when saving externally (optional, never None)

- width ( int ) – Width, Horizontal dimension of the baking map (external only) (in [1, inf], optional)

- height ( int ) – Height, Vertical dimension of the baking map (external only) (in [1, inf], optional)

- margin ( int ) – Margin, Extends the baked result as a post process filter (in [0, inf], optional)

- margin_type (Literal[Bake Margin Type Items]) – Margin Type, Which algorithm to use to generate the margin (optional)

- use_selected_to_active ( bool ) – Selected to Active, Bake shading on the surface of selected objects to the active object (optional)

- max_ray_distance ( float ) – Max Ray Distance, The maximum ray distance for matching points between the active and selected objects. If zero, there is no limit (in [0, inf], optional)

- cage_extrusion ( float ) – Cage Extrusion, Inflate the active object by the specified distance for baking. This helps matching to points nearer to the outside of the selected object meshes (in [0, inf], optional)

- cage_object ( str ) – Cage Object, Object to use as cage, instead of calculating the cage from the active object with cage extrusion (optional, never None)

- normal_space (Literal[Normal Space Items]) – Normal Space, Choose normal space for baking (optional)

- normal_r (Literal[Normal Swizzle Items]) – R, Axis to bake in red channel (optional)

- normal_g (Literal[Normal Swizzle Items]) – G, Axis to bake in green channel (optional)

- normal_b (Literal[Normal Swizzle Items]) – B, Axis to bake in blue channel (optional)

- target (Literal[Bake Target Items]) – Target, Where to output the baked map (optional)

- save_mode (Literal[Bake Save Mode Items]) – Save Mode, Where to save baked image textures (optional)

- use_clear ( bool ) – Clear, Clear images before baking (only for internal saving) (optional)

- use_cage ( bool ) – Cage, Cast rays to active object from a cage (optional)

- use_split_materials ( bool ) – Split Materials, Split baked maps per material, using material name in output file (external only) (optional)

- use_automatic_name ( bool ) – Automatic Name, Automatically name the output file with the pass type (optional)

- uv_layer ( str ) – UV Layer, UV layer to override active (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. bake_image ( ) 

Process surface appearance information for chosen objects

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. camera_add ( * , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Introduce a camera entity to the viewport

Parameters :

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

bpy.ops.object. camera_custom_update ( ) 

Modify exclusive camera controls employing parameters from the code

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. clear_override_library ( ) 

Erase the chosen regional deviations and reallocate their references to the imported resources as available, otherwise reset them and designate them as prohibited from modification

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. collection_add ( ) 

Introduce an entity to a fresh collection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. collection_external_asset_drop ( * , session_uid = 0 , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) , use_instance = True , drop_x = 0 , drop_y = 0 , collection = '' ) 

Introduce the dragged collection to the viewport

Parameters :

- session_uid ( int ) – Session UID, Session UID of the data-block to use by the operator (in [-inf, inf], optional)

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

- use_instance ( bool ) – Instance, Add the dropped collection as collection instance (optional)

- drop_x ( int ) – Drop X, X-coordinate (screen space) to place the new object under (in [-inf, inf], optional)

- drop_y ( int ) – Drop Y, Y-coordinate (screen space) to place the new object under (in [-inf, inf], optional)

- collection ( str ) – Collection, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. collection_instance_add ( * , name = 'Collection' , collection = '' , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) , session_uid = 0 , drop_x = 0 , drop_y = 0 ) 

Introduce a collection replica

Parameters :

- name ( str ) – Name, Collection name to add (optional, never None)

- collection ( str ) – Collection, (optional)

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

- session_uid ( int ) – Session UID, Session UID of the data-block to use by the operator (in [-inf, inf], optional)

- drop_x ( int ) – Drop X, X-coordinate (screen space) to place the new object under (in [-inf, inf], optional)

- drop_y ( int ) – Drop Y, Y-coordinate (screen space) to place the new object under (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. collection_link ( * , collection = '' ) 

Introduce an entity to a residing collection

Parameters :

collection ( str ) – Collection, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. collection_objects_select ( ) 

Highlight all entities in collection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. collection_remove ( ) 

Erase the highlighted entity from this collection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. collection_unlink ( ) 

Unbind the collection from all entities

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. constraint_add ( * , type = '' ) 

Append a confinement to the highlighted entity

Parameters :

type ( str ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. constraint_add_with_targets ( * , type = '' ) 

Append a confinement to the highlighted entity, with destination (when applicable) designated to the chosen entities/bone structures

Parameters :

type ( str ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. constraints_clear ( ) 

Strip all confines from the chose entities

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. constraints_copy ( ) 

Replicate confines to other chose entities

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. convert ( * , target = 'MESH' , keep_original = False , merge_customdata = True , thickness = 5 , faces = True , offset = 0.01 ) 

Reclassify chose entities into an alternative representation

Parameters :

- target ( Literal [ 'CURVE' , 'MESH' , 'POINTCLOUD' , 'CURVES' , 'GREASEPENCIL' ] ) – Target, Type of object to convert to (optional)

- CURVE
Curve – Curve from Mesh or Text objects.

- MESH
Mesh – Mesh from Curve, Surface, Metaball, Text, or Point Cloud objects.

- POINTCLOUD
Point Cloud – Point Cloud from Mesh objects.

- CURVES
Curves – Curves from evaluated curve data.

- GREASEPENCIL
Grease Pencil – Grease Pencil from Curve or Mesh objects.

- keep_original ( bool ) – Keep Original, Keep original objects instead of replacing them (optional)

- merge_customdata ( bool ) – Merge UVs, Merge UV coordinates that share a vertex to account for imprecision in some modifiers (optional)

- thickness ( int ) – Thickness, (in [1, 100], optional)

- faces ( bool ) – Export Faces, Export faces as filled strokes (optional)

- offset ( float ) – Stroke Offset, Offset strokes from fill (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. copy_global_transform ( ) 

Send the configuration of the presently highlighted entity or bone structure to the clipboard. Applies global dimension configurations

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/copy_global_transform.py:150

bpy.ops.object. copy_relative_transform ( ) 

Send the configuration of the presently highlighted entity or bone structure to the clipboard. Applies dimension configurations proportional to a designated entity or the highlighted setting camera

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/copy_global_transform.py:180

bpy.ops.object. correctivesmooth_bind ( * , modifier = '' ) 

Bind rest stance in Corrective Smooth adjustment

Parameters :

modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. curves_empty_hair_add ( * , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Introduce a blank curve entity to the viewport using the chose mesh as floor

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
