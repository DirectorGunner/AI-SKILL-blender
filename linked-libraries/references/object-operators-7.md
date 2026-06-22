# Object Operators (part 7)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

Point the item toward a separate item, employing differing approaches/linkages

Parameters :

type ( Literal [ 'DAMPTRACK' , 'TRACKTO' , 'LOCKTRACK' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. transfer_mode ( * , use_flash_on_transfer = True ) 

Swaps the working item and implements the corresponding state on a fresh one below the cursor, retaining the current state in the previous one

Parameters :

use_flash_on_transfer ( bool ) – Flash On Transfer, Illuminate the receiving item when switching the state (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. transform_apply ( * , location = True , rotation = True , scale = True , properties = True , corrective_flip_normals = True , isolate_users = False ) 

Bake the item's movement, orientation, and sizing into its information

Parameters :

- location ( bool ) – Location, (optional)

- rotation ( bool ) – Rotation, (optional)

- scale ( bool ) – Scale, (optional)

- properties ( bool ) – Apply Properties, Revise attributes such as curve vertex thickness, character sizing and armature envelope (optional)

- corrective_flip_normals ( bool ) – Corrective Flip Normals, Reverse surface directions for items with negative sizing. (optional)

- isolate_users ( bool ) – Isolate Multi User Data, Produce fresh item-information holders if required (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. transform_axis_target ( ) 

Interchangeably direct cameras and lights at a spot (Ctrl translates)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. transform_to_mouse ( * , name = '' , session_uid = 0 , matrix = ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)) , drop_x = 0 , drop_y = 0 ) 

Relocate chosen piece(s) to the cursor spot

Parameters :

- name ( str ) – Name, Item designation to put (employs the working item when this and 'session_uid' are empty) (optional, never None)

- session_uid ( int ) – Session UUID, Session UUID of the item to put (employs the working item when this and 'name' are empty) (in [-inf, inf], optional)

- matrix (mathutils.Matrix) – Matrix, (multi-dimensional array of 4 * 4 items, in [-inf, inf], optional)

- drop_x ( int ) – Drop X, X-spot (display area) to put the fresh item under (in [-inf, inf], optional)

- drop_y ( int ) – Drop Y, Y-spot (display area) to put the fresh item under (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. transforms_to_deltas ( * , mode = 'ALL' , reset_values = True ) 

Shift ordinary item movements to differential movements, existing differential movements stay in place too

Parameters :

- mode ( Literal [ 'ALL' , 'LOC' , 'ROT' , 'SCALE' ] ) – Mode, What kinds of movements to shift (optional)

- ALL
All Transforms – Shift spot, orientation, and sizing movements.

- LOC
Location – Shift spot movements exclusively.

- ROT
Rotation – Shift orientation movements exclusively.

- SCALE
Scale – Shift sizing movements exclusively.

- reset_values ( bool ) – Reset Values, Discharge movement values following shifting to deltas (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object.py:777

bpy.ops.object. unlink_data ( ) 

Undocumented, consider contributing.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. update_shapes ( * , use_mirror = False ) 

Refresh current shape keys with the vertex positions of picked items sharing matching names

Parameters :

use_mirror ( bool ) – Mirror, Reflect the refreshed shape key figures (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_add ( ) 

Insert a fresh vertex cluster to the working item

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_assign ( ) 

Place the picked vertices into the working vertex cluster

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_assign_new ( ) 

Place the picked vertices into a fresh vertex cluster

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_clean ( * , group_select_mode = '' , limit = 0.0 , keep_single = False ) 

Discard vertex cluster allocations that aren't essential

Parameters :

- group_select_mode ( str ) – Subset, Identify which portion of clusters to employ (optional)

- limit ( float ) – Limit, Strip vertices whose power is at or below this point (in [0, 1], optional)

- keep_single ( bool ) – Keep Single, Safeguard vertices present in a minimum of one cluster when filtering (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_copy ( ) 

Duplicate the working vertex cluster

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_copy_to_selected ( ) 

Exchange vertex clusters of picked items with vertex clusters of the working item

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_deselect ( ) 

Unselect each picked vertex present in the working vertex cluster

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_invert ( * , group_select_mode = '' , auto_assign = True , auto_remove = True ) 

Reverse working vertex cluster's strength values

Parameters :

- group_select_mode ( str ) – Subset, Identify which portion of clusters to employ (optional)

- auto_assign ( bool ) – Add Weights, Insert vertices from clusters that register zero power prior to reversing (optional)

- auto_remove ( bool ) – Remove Weights, Erase vertices from clusters that register zero power following reversing (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_levels ( * , group_select_mode = '' , offset = 0.0 , gain = 1.0 )

Introduce a displacement and apply a multiplication factor to the weights of the working vertex cluster

Parameters :

- group_select_mode ( str ) – Subset, Identify which portion of clusters to employ (optional)

- offset ( float ) – Offset, Quantity to introduce to weights (in [-1, 1], optional)

- gain ( float ) – Gain, Quantity to increase weights by (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_limit_total ( * , group_select_mode = '' , limit = 4 ) 

Curtail deform weights connected to a vertex to a predetermined quantity by cutting the littlest weights

Parameters :

- group_select_mode ( str ) – Subset, Identify which portion of clusters to employ (optional)

- limit ( int ) – Limit, Peak count of deform weights (in [1, 32], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_lock ( * , action = 'TOGGLE' , mask = 'ALL' ) 

Flip the secure condition of entire or partial vertex clusters of working item

Parameters :

- action ( Literal [ 'TOGGLE' , 'LOCK' , 'UNLOCK' , 'INVERT' ] ) – Action, Secure action to perform on vertex clusters (optional)

- TOGGLE
Toggle – Unprotect each vertex cluster when minimum one is protected, otherwise safeguard each.

- LOCK
Lock – Protect each vertex cluster.

- UNLOCK
Unlock – Unprotect each vertex cluster.

- INVERT
Invert – Reverse the secure status of each vertex cluster.

- mask ( Literal [ 'ALL' , 'SELECTED' , 'UNSELECTED' , '`INVERT_UNSELECTED`' ] ) – Mask, Execute the action according to vertex cluster choice (optional)

- ALL
All – Run action on entire vertex clusters.

- SELECTED
Selected – Run on chosen vertex clusters.

- UNSELECTED
Unselected – Run on non-chosen vertex clusters.

- `INVERT_UNSELECTED`
Invert Unselected – Run the reverse of Secure/Unprotect to non-chosen vertex clusters.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_mirror ( * , mirror_weights = True , flip_group_names = True , all_groups = False , use_topology = False ) 

Duplicate vertex cluster, reverse strength and/or names, updating merely chosen vertices, reversing when both edges are chosen or else take from non-chosen

Parameters :

- mirror_weights ( bool ) – Mirror Weights, Duplicate strength (optional)

- flip_group_names ( bool ) – Flip Group Names, Reverse vertex cluster names (optional)

- all_groups ( bool ) – All Groups, Duplicate each vertex cluster strength (optional)

- use_topology ( bool ) – Topology Mirror, Use structural duplication (for when both edges of geometry contain matching, exclusive structure) (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_move ( * , direction = 'UP' ) 

Shift the working vertex cluster forward/backward in the row

Parameters :

direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Orientation to shift the working vertex cluster towards (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_normalize ( ) 

Proportion weights of the working vertex cluster, allowing the tallest units to attain 1.0

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_normalize_all ( * , group_select_mode = '' , lock_active = True ) 

Proportion every weights of every vertex clusters, enabling each vertex, the aggregate of every weights to equal 1.0

Parameters :

- group_select_mode ( str ) – Subset, Identify which portion of clusters to employ (optional)

- lock_active ( bool ) – Lock Active, Preserve the quantities of the working cluster while proportioning others (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_quantize ( * , group_select_mode = '' , steps = 4 ) 

Designate weights to a predetermined quantity of increments

Parameters :

- group_select_mode ( str ) – Subset, Identify which portion of clusters to employ (optional)

- steps ( int ) – Steps, Quantity of increments separating 0 and 1 (in [1, 1000], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_remove ( * , all = False , all_unlocked = False ) 

Erase the working or entire vertex clusters from the working item

Parameters :

- all ( bool ) – All, Erase every vertex clusters (optional)

- all_unlocked ( bool ) – All Unlocked, Erase every unprotected vertex clusters (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_remove_from ( * , use_all_groups = False , use_all_verts = False ) 

Pull the picked vertices from working or every vertex cluster(s)

Parameters :

- use_all_groups ( bool ) – All Groups, Pull from every clusters (optional)

- use_all_verts ( bool ) – All Vertices, Purge the working cluster (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_select ( ) 

Opt for every vertex delegated to the working vertex cluster

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_set_active ( * , group = '' ) 

Establish the working vertex cluster

Parameters :

group ( str ) – Group, Vertex cluster to establish as working (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_smooth ( * , group_select_mode = '' , factor = 0.5 , repeat = 1 , expand = 0.0 ) 

Smooth strength for picked vertices

Parameters :

- group_select_mode ( str ) – Subset, Identify which portion of clusters to employ (optional)

- factor ( float ) – Factor, (in [0, 1], optional)

- repeat ( int ) – Iterations, (in [1, 10000], optional)

- expand ( float ) – Expand/Contract, Broaden/reduce strength (in [-1, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_group_sort ( * , sort_type = 'NAME' )

Organize vertex clusters

Parameters :

sort_type ( Literal [ 'NAME' , '`BONE_HIERARCHY`' ] ) – Sort Type, Organization method (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_parent_set ( ) 

Establish picked items as offspring of the picked vertices

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_weight_copy ( ) 

Duplicate strength from working to picked

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_weight_delete ( * , weight_group = -1 ) 

Erase this strength from the vertex (inaccessible when vertex cluster is protected)

Parameters :

weight_group ( int ) – Weight Index, Position of root strength in working vertex cluster (in [-1, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_weight_normalize_active_vertex ( ) 

Proportion working vertex's strength

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_weight_paste ( * , weight_group = -1 ) 

Duplicate this cluster's strength to other picked vertices (inaccessible when vertex cluster is protected)

Parameters :

weight_group ( int ) – Weight Index, Position of root strength in working vertex cluster (in [-1, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. vertex_weight_set_active ( * , weight_group = -1 ) 

Establish as working vertex cluster

Parameters :

weight_group ( int ) – Weight Index, Position of root strength in working vertex cluster (in [-1, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. visual_geometry_to_objects ( ) 

Morph information and copies into tweakable items and hierarchies

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. visual_transform_apply ( ) 

Bake the item's appearance-based movement into its information

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. volume_add ( * , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Put a volume item into the workspace

Parameters :

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, Where the fresh item sits (optional)

- WORLD
World – Position the fresh item with respect to the world axes.

- VIEW
View – Position the fresh item with respect to the viewport.

- CURSOR
3D Cursor – Employ the 3D cursor's orientation for the fresh item.

- location (mathutils.Vector) – Location, Where the inserted item goes (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, How the inserted item is oriented (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, How the inserted item is sized (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. volume_import ( * , filepath = '' , directory = '' , files = None , hide_props_region = True , check_existing = False , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = True , filter_folder = True , filter_blenlib = False , filemode = 9 , relative_path = True , display_type = 'DEFAULT' , sort_method = '' , use_sequence_detection = True , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Fetch an OpenVDB volume record

Parameters :

- filepath ( str ) – File Path, Route to record (optional, never None)

- directory ( str ) – Directory, Route listing of the record (optional, never None)

- files ( bpy_prop_collection [ OperatorFileListElement ]) – Files, (optional)

- hide_props_region ( bool ) – Hide Operator Properties, Break down the area showing the action adjustments (optional)

- check_existing ( bool ) – Check Existing, Inspect and notify on replacing current records (optional)

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

- filemode ( int ) – File Browser Mode, The configuration for the record browser method to pull a .blend record, a stash or a particular record (in [1, 9], optional)

- relative_path ( bool ) – Relative Path, Opt for the record comparative to the blend record (optional)

- display_type ( Literal [ 'DEFAULT' , '`LIST_VERTICAL`' , '`LIST_HORIZONTAL`' , 'THUMBNAIL' ] ) – Display Type, (optional)

- DEFAULT
Default – Programmatically determine appearance approach for records.

- `LIST_VERTICAL`
Short List – Show records as abbreviated list.

- `LIST_HORIZONTAL`
Long List – Show records as an comprehensive listing.

- THUMBNAIL
Thumbnails – Show records as picture previews.

- sort_method ( str ) – File sorting mode, (optional)

- use_sequence_detection ( bool ) – Detect Sequences, Mechanically find moving sets in chosen volume records (depending on record designations) (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, Where the fresh item sits (optional)

- WORLD
World – Position the fresh item with respect to the world axes.

- VIEW
View – Position the fresh item with respect to the viewport.

- CURSOR
3D Cursor – Employ the 3D cursor's orientation for the fresh item.

- location (mathutils.Vector) – Location, Where the inserted item goes (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, How the inserted item is oriented (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, How the inserted item is sized (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. voxel_remesh ( ) 

Forms a fresh watertight geometry dependent on the extent of the working geometry. Every data layers get eliminated

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. voxel_size_edit ( ) 

Regulate the geometry particle measurement on the fly employed in the particle remesher

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
