# Object Operators (part 4)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

- INCLUDE
Include – Add selected receivers to light-receiving from the active emitter.

- EXCLUDE
Exclude – Prevent selected receivers from light-receiving from the active emitter.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. light_linking_receivers_select ( ) 

Highlight all geometry illuminated by this light source

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. light_linking_unlink_from_collection ( ) 

Sever the connection of this object or collection from a light-linking catalog

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. lightprobe_add ( * , type = 'SPHERE' , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Insert a light-sampling instrument into the scene

Parameters :

- type ( Literal [ 'SPHERE' , 'PLANE' , 'VOLUME' ] ) – Type, (optional)

- SPHERE
Sphere – Probe capturing directional brightness samples everywhere around a point.

- PLANE
Plane – Probe sampling incoming radiance across a flat area.

- VOLUME
Volume – Probe for storing coarse radiance within a bounded region.

- radius ( float ) – Radius, (in [0, inf], optional)

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

bpy.ops.object. lightprobe_cache_bake ( * , subset = 'ALL' ) 

Compute and store illumination data in light probe volumes

Parameters :

subset ( Literal [ 'ALL' , 'SELECTED' , 'ACTIVE' ] ) – Subset, Which probes to process (optional)

- ALL
All Volumes – Process every light-sampling volume.

- SELECTED
Selected Only – Process only highlighted light-sampling volumes.

- ACTIVE
Active Only – Process only the topmost light-sampling volume.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. lightprobe_cache_free ( * , subset = 'SELECTED' ) 

Discard stored indirect brightness information

Parameters :

subset ( Literal [ 'ALL' , 'SELECTED' , 'ACTIVE' ] ) – Subset, Which probes to process (optional)

- ALL
All Light Probes – Erase stored brightness from all probes.

- SELECTED
Selected Only – Erase stored brightness from highlighted probes.

- ACTIVE
Active Only – Erase stored brightness from the topmost probe.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. lineart_bake_strokes ( * , bake_all = False ) 

Render and store Line Art sketch strokes for the current Grease Pencil object

Parameters :

bake_all ( bool ) – Bake All, Process every Line Art modifier (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. lineart_clear ( * , clear_all = False ) 

Erase all drawn lines from the current Grease Pencil object

Parameters :

clear_all ( bool ) – Clear All, Erase baked output from all Line Art modifiers (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. link_to_collection ( * , collection_uid = -1 , is_new = False , new_collection_name = '' ) 

Attach objects to a grouping container

Parameters :

- collection_uid ( int ) – Collection UID, Session UID of the collection to link to (in [-1, inf], optional)

- is_new ( bool ) – New, Attach objects to a newly created collection (optional)

- new_collection_name ( str ) – Name, Title for the freshly added collection (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. location_clear ( * , clear_delta = False ) 

Reset the object's placement to the origin

Parameters :

clear_delta ( bool ) – Clear Delta, Also reset offset location in addition to the primary location (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. make_dupli_face ( ) 

Transform objects into face-linked duplicates

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object.py:706

bpy.ops.object. make_links_data ( * , type = 'OBDATA' ) 

Duplicate properties from the active object to selected targets

Parameters :

type ( Literal [ 'OBDATA' , 'MATERIAL' , 'ANIMATION' , 'GROUPS' , 'DUPLICOLLECTION' , 'FONTS' , 'MODIFIERS' , 'EFFECTS' ] ) – Type, (optional)

- OBDATA
Link Object Data – Swap the assigned data reference.

- MATERIAL
Link Materials – Swap the assigned materials.

- ANIMATION
Link Animation Data – Swap the assigned animation track.

- GROUPS
Link Collections – Swap the assigned groups.

- DUPLICOLLECTION
Link Instance Collection – Swap the assigned collection instance.

- FONTS
Link Fonts to Text – Swap typeface assignments.

- MODIFIERS
Copy Modifiers – Swap modifier stacks.

- EFFECTS
Copy Grease Pencil Effects – Swap Grease Pencil effect configurations.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. make_links_scene ( * , scene = '' ) 

Attach selection to a different scene

Parameters :

scene ( str ) – Scene, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. make_local ( * , type = '`SELECT_OBJECT`' ) 

Localize linked asset data for use in the present file

Parameters :

type ( Literal [ '`SELECT_OBJECT`' , '`SELECT_OBDATA`' , '`SELECT_OBDATA_MATERIAL`' , 'ALL' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. make_override_library ( * , collection = 0 ) 

Establish an editable instance of the chosen linked objects and their dependency network

Parameters :

collection ( int ) – Override Collection, Session UID of the directly linked collection containing the selected object, to make an override from (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. make_single_user ( * , type = '`SELECTED_OBJECTS`' , object = False , obdata = False , material = False , animation = False , obdata_animation = False ) 

Break shared references so each object owns its data independently

Parameters :

- type ( Literal [ '`SELECTED_OBJECTS`' , 'ALL' ] ) – Type, (optional)

- object ( bool ) – Object, Make individual object instances (optional)

- obdata ( bool ) – Object Data, Unshare geometry data across objects (optional)

- material ( bool ) – Materials, Unshare material slots per data record (optional)

- animation ( bool ) – Object Animation, Unshare animation tracks per object (optional)

- obdata_animation ( bool ) – Object Data Animation, Unshare animation tracks for geometry (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. material_slot_add ( ) 

Create an empty material slot

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. material_slot_assign ( ) 

Map the current material slot to highlighted polygons

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. material_slot_copy ( ) 

Duplicate a material to other selected targets

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. material_slot_deselect ( ) 

Deselect faces assigned to the current material slot

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. material_slot_move ( * , direction = 'UP' ) 

Reorder the current material entry up or down

Parameters :

direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, How to shift the current material in the list (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. material_slot_remove ( ) 

Discard the current material slot

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. material_slot_remove_all ( ) 

Discard all material entries

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. material_slot_remove_unused ( ) 

Delete empty material slots

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. material_slot_select ( ) 

Highlight faces of the current material slot

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. meshdeform_bind ( * , modifier = '' ) 

Connect mesh vertices to a surrounding cage in mesh deform modifier

Parameters :

modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. metaball_add ( * , type = 'BALL' , radius = 2.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Add a metaball object to the scene

Parameters :

- type (Literal[Metaelem Type Items]) – Primitive, (optional)

- radius ( float ) – Radius, (in [0, inf], optional)

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

bpy.ops.object. mode_set ( * , mode = 'OBJECT' , toggle = False ) 

Alter the object interaction mode

Parameters :

- mode (Literal[Object Mode Items]) – Mode, (optional)

- toggle ( bool ) – Toggle, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. mode_set_with_submode ( * , mode = 'OBJECT' , toggle = False , mesh_select_mode = set() ) 

Alter the object interaction mode

Parameters :

- mode (Literal[Object Mode Items]) – Mode, (optional)

- toggle ( bool ) – Toggle, (optional)

- mesh_select_mode (set[Literal[Mesh Select Mode Items]]) – Mesh Mode, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. modifier_add ( * , type = 'SUBSURF' , use_selected_objects = False ) 

Attach a deformation/effect modifier to the current object

Parameters :

- type (Literal[Object Modifier Type Items]) – Type, (optional)

- use_selected_objects ( bool ) – Selected Objects, Affect all selected objects instead of just the active object (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. modifier_add_node_group ( * , asset_library_type = 'LOCAL' , asset_library_identifier = '' , relative_asset_identifier = '' , session_uid = 0 , use_selected_objects = False ) 

Attach a deformation/effect modifier to the current object

Parameters :

- asset_library_type (Literal[Asset Library Type Items]) – Asset Library Type, (optional)

- asset_library_identifier ( str ) – Asset Library Identifier, (optional, never None)

- relative_asset_identifier ( str ) – Relative Asset Identifier, (optional, never None)

- session_uid ( int ) – Session UID, Session UID of the data-block to use by the operator (in [-inf, inf], optional)

- use_selected_objects ( bool ) – Selected Objects, Affect all selected objects instead of just the active object (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. modifier_apply ( * , modifier = '' , report = False , merge_customdata = True , single_user = False , all_keyframes = False , use_selected_objects = False ) 

Lock a modifier into the geometry and take it off the stack

Parameters :

- modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

- report ( bool ) – Report, Issue a message window after the procedure finishes (optional)

- merge_customdata ( bool ) – Merge UVs, For mesh objects, unify UV locations that reference the same vertex to reduce floating-point artifacts (optional)

- single_user ( bool ) – Make Data Single User, Break any shared references in the object's data if necessary (optional)

- all_keyframes ( bool ) – Apply to all keyframes, For Grease Pencil objects, apply the modifier to every keyframe (optional)

- use_selected_objects ( bool ) – Selected Objects, Affect all selected objects instead of just the active object (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. modifier_apply_as_shapekey ( * , keep_modifier = False , modifier = '' , report = False , use_selected_objects = False ) 

Finalize a modifier as a fresh shape key and take it off the stack

Parameters :

- keep_modifier ( bool ) – Keep Modifier, Preserve the modifier in the stack (optional)

- modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

- report ( bool ) – Report, Issue a message window after the procedure finishes (optional)

- use_selected_objects ( bool ) – Selected Objects, Affect all selected objects instead of just the active object (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. modifier_convert ( * , modifier = '' ) 

Transform particle simulation into polygon geometry

Parameters :

modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. modifier_copy ( * , modifier = '' , use_selected_objects = False ) 

Replicate a modifier in an identical position within the stack

Parameters :

- modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

- use_selected_objects ( bool ) – Selected Objects, Affect all selected objects instead of just the active object (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. modifier_copy_to_selected ( * , modifier = '' ) 

Replicate the modifier from the current object to every selected target

Parameters :

modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. modifier_move_down ( * , modifier = '' ) 

Shift a modifier lower on the evaluation order

Parameters :

modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. modifier_move_to_index ( * , modifier = '' , index = 0 , use_selected_objects = False ) 

Set a modifier's sequence number so it processes after a specified number of other modifiers

Parameters :

- modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

- index ( int ) – Index, The index to move the modifier to (in [0, inf], optional)

- use_selected_objects ( bool ) – Selected Objects, Affect all selected objects instead of just the active object (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. modifier_move_up ( * , modifier = '' ) 

Shift a modifier higher on the evaluation order

Parameters :

modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. modifier_remove ( * , modifier = '' , report = False , use_selected_objects = False ) 

Discard a modifier from the current object

Parameters :

- modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

- report ( bool ) – Report, Issue a message window after the procedure finishes (optional)

- use_selected_objects ( bool ) – Selected Objects, Affect all selected objects instead of just the active object (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. modifier_set_active ( * , modifier = '' ) 

Designate a modifier as the current context

Parameters :

modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. modifiers_clear ( ) 

Remove every modifier from the chosen objects

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. modifiers_copy_to_selected ( ) 

Duplicate modifiers to other chosen targets

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. move_to_collection ( * , collection_uid = -1 , is_new = False , new_collection_name = '' ) 

Transfer objects to a grouping container

Parameters :

- collection_uid ( int ) – Collection UID, Session UID of the collection to move to (in [-1, inf], optional)

- is_new ( bool ) – New, Transfer objects to a newly created collection (optional)

- new_collection_name ( str ) – Name, Title for the freshly added collection (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. multires_base_apply ( * , modifier = '' , apply_heuristic = True ) 

Reshape the foundation mesh to align with the deformed geometry

Parameters :

- modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

- apply_heuristic ( bool ) – Apply Subdivision Heuristic, Slightly shift the foundation positions to account for subdivision (optional)
