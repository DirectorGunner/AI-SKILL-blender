# Object Operators (part 3)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

- location (mathutils.Vector) – Location, Placement point for the newly inserted object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Orientation to apply when inserting the object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Size scaling during insertion (array of 3 items, in [-inf, inf], optional)

- background ( bool ) – Put in Background, Renders the image behind all scene geometry (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. explode_refresh ( * , modifier = '' ) 

Update the Explode modifier's cached information

Parameters :

modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. fix_to_camera ( * , use_location = True , use_rotation = True , use_scale = True ) 

Produce new animation frames anchoring the selected object/bone to the view camera when frames lack existing keyframes

Parameters :

- use_location ( bool ) – Location, Add position keyframes for fixing to the active scene camera (optional)

- use_rotation ( bool ) – Rotation, Add orientation keyframes for fixing to the active scene camera (optional)

- use_scale ( bool ) – Scale, Add scaling keyframes for fixing to the active scene camera (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/copy_global_transform.py:639

bpy.ops.object. forcefield_toggle ( ) 

Enable or disable the force field attached to this object

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. geometry_node_bake_delete_single ( * , session_uid = 0 , modifier_name = '' , bake_id = 0 ) 

Discard baked simulation results from a single node or bake element

Parameters :

- session_uid ( int ) – Session UID, Session UID of the data-block to use by the operator (in [-inf, inf], optional)

- modifier_name ( str ) – Modifier Name, Name of the modifier that contains the node (optional, never None)

- bake_id ( int ) – Bake ID, Nested node id of the node (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. geometry_node_bake_pack_single ( * , session_uid = 0 , modifier_name = '' , bake_id = 0 ) 

Compress baked simulation data from external storage back into the .blend project file

Parameters :

- session_uid ( int ) – Session UID, Session UID of the data-block to use by the operator (in [-inf, inf], optional)

- modifier_name ( str ) – Modifier Name, Name of the modifier that contains the node (optional, never None)

- bake_id ( int ) – Bake ID, Nested node id of the node (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. geometry_node_bake_single ( * , session_uid = 0 , modifier_name = '' , bake_id = 0 ) 

Process and store a single bake node simulation output

Parameters :

- session_uid ( int ) – Session UID, Session UID of the data-block to use by the operator (in [-inf, inf], optional)

- modifier_name ( str ) – Modifier Name, Name of the modifier that contains the node (optional, never None)

- bake_id ( int ) – Bake ID, Nested node id of the node (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. geometry_node_bake_unpack_single ( * , session_uid = 0 , modifier_name = '' , bake_id = 0 , method = '`USE_LOCAL`' ) 

Write cached simulation data from the .blend file out to the file system

Parameters :

- session_uid ( int ) – Session UID, Session UID of the data-block to use by the operator (in [-inf, inf], optional)

- modifier_name ( str ) – Modifier Name, Name of the modifier that contains the node (optional, never None)

- bake_id ( int ) – Bake ID, Nested node id of the node (in [0, inf], optional)

- method ( Literal [ '`USE_LOCAL`' , '`WRITE_LOCAL`' , '`USE_ORIGINAL`' , '`WRITE_ORIGINAL`' ] ) – Method, How to unpack (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. geometry_node_tree_copy_assign ( ) 

Replicate the current geometry node collection and connect it to the running modifier

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. geometry_nodes_input_attribute_toggle ( * , input_name = '' , modifier_name = '' ) 

Toggle between pulling data from a stored attribute versus using a direct scalar/single value

Parameters :

- input_name ( str ) – Input Name, (optional, never None)

- modifier_name ( str ) – Modifier Name, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. geometry_nodes_move_to_nodes ( * , use_selected_objects = False ) 

Relocate socket definitions from a modifier wrapper into a standalone node assembly

Parameters :

use_selected_objects ( bool ) – Selected Objects, Affect all selected objects instead of just the active object (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/geometry_nodes.py:285

bpy.ops.object. grease_pencil_add ( * , type = 'EMPTY' , use_in_front = True , stroke_depth_offset = 0.05 , use_lights = True , stroke_depth_order = '3D' , radius = 1.0 , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Insert a Grease Pencil sketch layer into the workspace

Parameters :

- type (Literal[Object Gpencil Type Items]) – Type, (optional)

- use_in_front ( bool ) – Show In Front, Render Line Art Grease Pencil atop all objects in the viewport (optional)

- stroke_depth_offset ( float ) – Stroke Offset, Vertical spacing parameter for the Line Art modifier (in [0, inf], optional)

- use_lights ( bool ) – Use Lights, Illumination affects this Grease Pencil layer (optional)

- stroke_depth_order ( Literal [ '2D' , '3D' ] ) – Stroke Depth Order, Determines ordering approach for strokes in three-dimensional areas (for layers not shown 'In Front') (optional)

- 2D
2D Layers – Render strokes using layer stacking to determine sequence.

- 3D
3D Location – Display strokes using true spatial positioning.

- radius ( float ) – Radius, (in [0, inf], optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, Direction the inserted object will face (optional)

- WORLD
World – Orient the object to global axes.

- VIEW
View – Orient the object to match the camera view.

- CURSOR
3D Cursor – Use the 3D cursor's orientation for the object.

- location (mathutils.Vector) – Location, Placement point for the newly inserted object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Orientation to apply when inserting the object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Size scaling during insertion (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. grease_pencil_dash_modifier_segment_add ( * , modifier = '' ) 

Insert a section into the dash modifier

Parameters :

modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. grease_pencil_dash_modifier_segment_move ( * , modifier = '' , type = 'UP' ) 

Reorder the selected dash segment upward or downward

Parameters :

- modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

- type ( Literal [ 'UP' , 'DOWN' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. grease_pencil_dash_modifier_segment_remove ( * , modifier = '' , index = 0 ) 

Discard the active segment from the dash modifier

Parameters :

- modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

- index ( int ) – Index, Index of the segment to remove (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. grease_pencil_time_modifier_segment_add ( * , modifier = '' ) 

Insert a section into the time modifier

Parameters :

modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. grease_pencil_time_modifier_segment_move ( * , modifier = '' , type = 'UP' ) 

Shift the active time segment up or down the sequence

Parameters :

- modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

- type ( Literal [ 'UP' , 'DOWN' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. grease_pencil_time_modifier_segment_remove ( * , modifier = '' , index = 0 ) 

Erase the active segment from the time modifier

Parameters :

- modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

- index ( int ) – Index, Index of the segment to remove (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. hide_collection ( * , collection_index = -1 , toggle = False , extend = False ) 

Conceal all but one collection's contents (Shift to expand selection)

Parameters :

- collection_index ( int ) – Collection Index, Index of the collection to change visibility (in [-1, inf], optional)

- toggle ( bool ) – Toggle, Invert visibility state (optional)

- extend ( bool ) – Extend, Grow visibility scope (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. hide_render_clear_all ( ) 

Make all render-hidden objects visible by unsetting their hide-from-render flags

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object.py:743

bpy.ops.object. hide_view_clear ( * , select = True ) 

Unhide objects that were temporarily masked from view

Parameters :

select ( bool ) – Select, Make revealed objects part of the current selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. hide_view_set ( * , unselected = False ) 

Mask objects away from the 3D display temporarily

Parameters :

unselected ( bool ) – Unselected, Hide non-selected rather than selected objects (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. hook_add_newob ( ) 

Attach selected vertices to a freshly created control object

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. hook_add_selob ( * , use_bone = False ) 

Attach selected vertices to the topmost selected control object

Parameters :

use_bone ( bool ) – Active Bone, Bind the hook to the control object's active bone (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. hook_assign ( * , modifier = '' ) 

Transfer the selected vertices to an already-existing hook

Parameters :

modifier ( str ) – Modifier, Modifier number to assign to (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. hook_recenter ( * , modifier = '' ) 

Move the hook's pivot point to the 3D cursor

Parameters :

modifier ( str ) – Modifier, Modifier number to assign to (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. hook_remove ( * , modifier = '' ) 

Delete a hook constraint from the current object

Parameters :

modifier ( str ) – Modifier, Modifier number to remove (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. hook_reset ( * , modifier = '' ) 

Recompute and eliminate stored translation offset

Parameters :

modifier ( str ) – Modifier, Modifier number to assign to (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. hook_select ( * , modifier = '' ) 

Highlight vertices controlled by the hook on the mesh

Parameters :

modifier ( str ) – Modifier, Modifier number to remove (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. instance_offset_from_cursor ( ) 

Configure the offset positioning for collection copies based on where the 3D cursor is

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object.py:936

bpy.ops.object. instance_offset_from_object ( ) 

Configure the offset positioning for collection copies based on the active object's current location

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object.py:968

bpy.ops.object. instance_offset_to_cursor ( ) 

Transfer the offset positioning for collection copies to the 3D cursor position

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object.py:951

bpy.ops.object. isolate_type_render ( ) 

Hide objects of the same category as the active one from rendering (except the active one)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object.py:723

bpy.ops.object. join ( ) 

Merge all highlighted objects into the active one

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. join_shapes ( * , use_mirror = False ) 

Incorporate the vertex geometry of selected objects as shape keys or refresh existing shape keys with equivalent labels

Parameters :

use_mirror ( bool ) – Mirror, Flip the shape key values along an axis (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. join_uvs ( ) 

Duplicate UV coordinate sets from the active object to selected targets (requires matching geometry)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object.py:623

bpy.ops.object. laplaciandeform_bind ( * , modifier = '' ) 

Engage the laplacian deform modifier's mesh binding system

Parameters :

modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. lattice_add_to_selected ( * , fit_to_selected = True , radius = 1.0 , margin = 0.0 , add_modifiers = True , resolution_u = 2 , resolution_v = 2 , resolution_w = 2 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Create a deformable lattice grid and apply it to shape selected geometry

Parameters :

- fit_to_selected ( bool ) – Fit to Selected, Extend lattice boundaries to encompass the selected deformable objects (optional)

- radius ( float ) – Radius, (in [0, inf], optional)

- margin ( float ) – Margin, Expand lattice size around geometry (in [0, inf], optional)

- add_modifiers ( bool ) – Add Modifiers, Automatically attach lattice deformation modifiers to selected objects (optional)

- resolution_u ( int ) – Resolution U, Lattice density along U direction (in [1, 64], optional)

- resolution_v ( int ) – V, Lattice density along V direction (in [1, 64], optional)

- resolution_w ( int ) – W, Lattice density along W direction (in [1, 64], optional)

- enter_editmode ( bool ) – Enter Edit Mode, Switch to edit mode immediately after creation (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, Direction the inserted object will face (optional)

- WORLD
World – Orient the object to global axes.

- VIEW
View – Orient the object to match the camera view.

- CURSOR
3D Cursor – Use the 3D cursor's orientation for the object.

- location (mathutils.Vector) – Location, Placement point for the newly inserted object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Orientation to apply when inserting the object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Size scaling during insertion (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. light_add ( * , type = 'POINT' , radius = 1.0 , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Place a light source into the scene

Parameters :

- type (Literal[Light Type Items]) – Type, (optional)

- radius ( float ) – Radius, (in [0, inf], optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, Direction the inserted object will face (optional)

- WORLD
World – Orient the object to global axes.

- VIEW
View – Orient the object to match the camera view.

- CURSOR
3D Cursor – Use the 3D cursor's orientation for the object.

- location (mathutils.Vector) – Location, Placement point for the newly inserted object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Orientation to apply when inserting the object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Size scaling during insertion (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. light_linking_blocker_collection_new ( ) 

Build a fresh light-linking catalog used by the current light emitter

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. light_linking_blockers_link ( * , link_state = 'INCLUDE' ) 

Tie the chosen shadow-blocking objects to the current light emitter

Parameters :

link_state ( Literal [ 'INCLUDE' , 'EXCLUDE' ] ) – Link State, Shadow connection mode (optional)

- INCLUDE
Include – Add selected blockers to shadow-casting from the active emitter.

- EXCLUDE
Exclude – Prevent selected blockers from shadow-casting from the active emitter.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. light_linking_blockers_select ( ) 

Highlight all geometry that shadows this light source

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. light_linking_receiver_collection_new ( ) 

Build a fresh light-linking catalog used by the current light emitter

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. light_linking_receivers_link ( * , link_state = 'INCLUDE' ) 

Tie the chosen illuminated objects to the current light emitter

Parameters :

link_state ( Literal [ 'INCLUDE' , 'EXCLUDE' ] ) – Link State, Light connection mode (optional)
