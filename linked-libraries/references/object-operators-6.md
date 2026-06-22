# Object Operators (part 6)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. rotation_clear ( * , clear_delta = False ) 

Reset the object's orientation to default

Parameters :

clear_delta ( bool ) – Clear Delta, Also reset offset orientation in addition to the primary orientation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. scale_clear ( * , clear_delta = False ) 

Reset the object's size to default

Parameters :

clear_delta ( bool ) – Clear Delta, Also reset offset scaling in addition to the primary scaling (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. select_all ( * , action = 'TOGGLE' ) 

Modify visibility selection across all objects in the viewport

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Modify all highlighting (optional)

- TOGGLE
Toggle – Flip highlight state on every element.

- SELECT
Select – Highlight every element.

- DESELECT
Deselect – Remove highlighting from every element.

- INVERT
Invert – Flip highlight state on every element.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. select_by_type ( * , extend = False , type = 'MESH' ) 

Highlight all objects sharing a kind

Parameters :

- extend ( bool ) – Extend, Add to the existing selection instead of replacing it (optional)

- type (Literal[Object Type Items]) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. select_camera ( * , extend = False ) 

Highlight the primary camera

Parameters :

extend ( bool ) – Extend, Add to the existing selection instead of replacing it (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object.py:124

bpy.ops.object. select_grouped ( * , extend = False , type = '`CHILDREN_RECURSIVE`' ) 

Highlight all objects associated via many criteria

Parameters :

- extend ( bool ) – Extend, Add to the existing selection instead of replacing it (optional)

- type ( Literal [ '`CHILDREN_RECURSIVE`' , 'CHILDREN' , 'PARENT' , 'SIBLINGS' , 'TYPE' , 'COLLECTION' , 'HOOK' , 'PASS' , 'COLOR' , 'KEYINGSET' , '`LIGHT_TYPE`' ] ) – Type, (optional)

- `CHILDREN_RECURSIVE`
Children.

- CHILDREN
Immediate Children.

- PARENT
Parent.

- SIBLINGS
Siblings – Shared parent.

- TYPE
Type – Shared object type.

- COLLECTION
Collection – Shared collection.

- HOOK
Hook.

- PASS
Pass – Render pass index.

- COLOR
Color – Object color.

- KEYINGSET
Keying Set – Objects included in active Keying Set.

- `LIGHT_TYPE`
Light Type – Matching light types.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. select_hierarchy ( * , direction = 'PARENT' , extend = False ) 

Highlight object family members relative to the active object

Parameters :

- direction ( Literal [ 'PARENT' , 'CHILD' ] ) – Direction, Family line direction to highlight (optional)

- extend ( bool ) – Extend, Add to the existing selection instead of replacing it (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object.py:174

bpy.ops.object. select_less ( ) 

Deselect the periphery objects in parent/child hierarchies

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. select_linked ( * , extend = False , type = 'OBDATA' ) 

Highlight all objects sharing data references

Parameters :

- extend ( bool ) – Extend, Add to the existing selection instead of replacing it (optional)

- type ( Literal [ 'OBDATA' , 'MATERIAL' , 'DUPGROUP' , 'PARTICLE' , 'LIBRARY' , '`LIBRARY_OBDATA`' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. select_mirror ( * , extend = False ) 

Highlight the paired mirrored objects of selected items e.g. "L.sword" and "R.sword"

Parameters :

extend ( bool ) – Extend, Add to the existing selection instead of replacing it (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. select_more ( ) 

Highlight connected family members

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. select_pattern ( * , pattern = '*' , case_sensitive = False , extend = True ) 

Highlight objects matching a title pattern

Parameters :

- pattern ( str ) – Pattern, Name filter using '*', '?' and '[abc]' unix style wildcards (optional, never None)

- case_sensitive ( bool ) – Case Sensitive, Perform case-aware matching (optional)

- extend ( bool ) – Extend, Add to the existing selection instead of replacing it (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object.py:45

bpy.ops.object. select_random ( * , ratio = 0.5 , seed = 0 , action = 'SELECT' ) 

Highlight or remove highlighting from random visible objects

Parameters :

- ratio ( float ) – Ratio, Fraction of items to modify (in [0, 1], optional)

- seed ( int ) – Random Seed, State for the random number generator (in [0, inf], optional)

- action ( Literal [ 'SELECT' , 'DESELECT' ] ) – Action, Modify highlighting (optional)

- SELECT
Select – Highlight every element.

- DESELECT
Deselect – Remove highlighting from every element.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. select_same_collection ( * , collection = '' ) 

Highlight objects in a matching group

Parameters :

collection ( str ) – Collection, Title of the group to highlight (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shade_auto_smooth ( * , use_auto_smooth = True , angle = 0.523599 ) 

Insert a modifier that automatically tags mesh edges based on the angle between bordering faces

Parameters :

- use_auto_smooth ( bool ) – Auto Smooth, Insert modifier to mark edge sharpness mechanically (optional)

- angle ( float ) – Angle, Upper threshold for face normal divergence that is still treated as smooth (in [0, 3.14159], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shade_flat ( * , keep_sharp_edges = True ) 

Render and show polygons consistently, using face direction vectors

Parameters :

keep_sharp_edges ( bool ) – Keep Sharp Edges, Retain manually tagged sharp edges, which otherwise duplicate smooth-shaded faces (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shade_smooth ( * , keep_sharp_edges = True ) 

Render and show polygons with fluidity, using averaged vertex direction vectors

Parameters :

keep_sharp_edges ( bool ) – Keep Sharp Edges, Retain manually tagged sharp edges. Tagged boundaries stay sharp (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shade_smooth_by_angle ( * , angle = 0.523599 , keep_sharp_edges = True ) 

Tag mesh edges based on the angle between adjacent polygons

Parameters :

- angle ( float ) – Angle, Upper threshold for face normal divergence that is still treated as smooth (in [0, 3.14159], optional)

- keep_sharp_edges ( bool ) – Keep Sharp Edges, Insert sharp tags instead of blanking previous ones (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shaderfx_add ( * , type = '`FX_BLUR`' ) 

Attach a rendering effect to the current object

Parameters :

type (Literal[Object Shaderfx Type Items]) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shaderfx_copy ( * , shaderfx = '' ) 

Replicate an effect in an identical position within the stack

Parameters :

shaderfx ( str ) – Shader, Name of the shaderfx to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shaderfx_move_down ( * , shaderfx = '' ) 

Shift an effect lower on the evaluation order

Parameters :

shaderfx ( str ) – Shader, Name of the shaderfx to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shaderfx_move_to_index ( * , shaderfx = '' , index = 0 ) 

Set an effect's sequence number so it processes after a specified number of other effects

Parameters :

- shaderfx ( str ) – Shader, Name of the shaderfx to edit (optional, never None)

- index ( int ) – Index, The index to move the effect to (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shaderfx_move_up ( * , shaderfx = '' ) 

Shift an effect higher on the evaluation order

Parameters :

shaderfx ( str ) – Shader, Name of the shaderfx to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shaderfx_remove ( * , shaderfx = '' , report = False ) 

Discard an effect from the current Grease Pencil object

Parameters :

- shaderfx ( str ) – Shader, Name of the shaderfx to edit (optional, never None)

- report ( bool ) – Report, Issue a message window after the procedure finishes (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shape_key_add ( * , from_mix = True ) 

Introduce a shape key to the object

Parameters :

from_mix ( bool ) – From Mix, Fabricate the new shape key from the active mix of existing keys (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shape_key_apply_to_basis ( ) 

Bake all selected shape key changes into the reference key, then remove them

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shape_key_clear ( ) 

Set all shape key influences to zero or to enforced limits

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shape_key_copy ( ) 

Reproduce the active shape key

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shape_key_lock ( * , action = 'LOCK' ) 

Modify the protection status of all shape keys on the active object

Parameters :

action ( Literal [ 'LOCK' , 'UNLOCK' ] ) – Action, Lock operation to run on shape keys (optional)

- LOCK
Lock – Protect all shape keys.

- UNLOCK
Unlock – Unprotect all shape keys.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shape_key_make_basis ( ) 

Make this shape key the reference, essentially baking it. Note that this bakes the shape key at 100% strength

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shape_key_mirror ( * , use_topology = False ) 

Mirror the active shape key along the local X axis

Parameters :

use_topology ( bool ) – Topology Mirror, Use topology mirroring (when both halves have matching, unique connectivity) (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shape_key_move ( * , type = 'TOP' ) 

Reorder the chosen shape keys up or down

Parameters :

type ( Literal [ 'TOP' , 'UP' , 'DOWN' , 'BOTTOM' ] ) – Type, (optional)

- TOP
Top – Top of the list.

- UP
Up.

- DOWN
Down.

- BOTTOM
Bottom – Bottom of the list.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shape_key_remove ( * , all = False , apply_mix = False ) 

Discard a shape key from the object

Parameters :

- all ( bool ) – All, Discard every shape key (optional)

- apply_mix ( bool ) – Apply Mix, Bake the active mix of shape keys into geometry before removing them (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. shape_key_retime ( ) 

Clear the time offsets for relative shape keys

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

set[Literal[Operator Return Items]]

bpy.ops.object. shape_key_transfer ( * , mode = 'OFFSET' , use_clamp = False ) 

Duplicates the shape key from another picked object onto the current one

Parameters :

- mode ( Literal [ 'OFFSET' , '`RELATIVE_FACE`' , '`RELATIVE_EDGE`' ] ) – Transformation Mode, How to position the shape in relation to the fresh configuration (optional)

- OFFSET
Offset – Applies the relative positional movement.

- `RELATIVE_FACE`
Relative Face – Computes relative placement (based on faces).

- `RELATIVE_EDGE`
Relative Edge – Computes relative placement (based on edges).

- use_clamp ( bool ) – Clamp Offset, Limit the transformation so vertices stay within original movement distances (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object.py:515

bpy.ops.object. simulation_nodes_cache_bake ( * , selected = False ) 

Cook down simulations within geometry nodes modifiers to a cache

Parameters :

selected ( bool ) – Selected, Process cached simulations on all picked objects (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. simulation_nodes_cache_calculate_to_frame ( * , selected = False ) 

Compute simulations in geometry nodes modifiers beginning at frame 0 and ending at the playhead

Parameters :

selected ( bool ) – Selected, Process all picked objects rather than only the working object (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. simulation_nodes_cache_delete ( * , selected = False ) 

Wipe out stored/baked simulations in geometry nodes modifiers

Parameters :

selected ( bool ) – Selected, Erase cache from all picked objects (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. skin_armature_create ( * , modifier = '' ) 

Generate a bone framework matching the skin structure

Parameters :

modifier ( str ) – Modifier, Title of the modifier to adjust (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. skin_loose_mark_clear ( * , action = 'MARK' ) 

Flag/unflag picked vertices as freestanding

Parameters :

action ( Literal [ 'MARK' , 'CLEAR' ] ) – Action, (optional)

- MARK
Mark – Flag picked vertices as freestanding.

- CLEAR
Clear – Designate picked vertices as attached.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. skin_radii_equalize ( ) 

Equalize skin dimensions of picked vertices on all cardinal directions

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. skin_root_mark ( ) 

Designate picked vertices as base points

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. speaker_add ( * , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Put a speaker into the workspace

Parameters :

- enter_editmode ( bool ) – Enter Edit Mode, Open edit mode right after inserting this item (optional)

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

bpy.ops.object. subdivision_set ( * , level = 1 , relative = False , ensure_modifier = True ) 

Assigns a Subdivision Surface iterations (1 to 5)

Parameters :

- level ( int ) – Level, (in [-100, 100], optional)

- relative ( bool ) – Relative, Treat the subdivision surface iterations as an added step on top of the current setting (optional)

- ensure_modifier ( bool ) – Ensure Modifier, Build the matching modifier when it isn't already there (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object.py:242

bpy.ops.object. surfacedeform_bind ( * , modifier = '' ) 

Anchor geometry to target in surface deform modifier

Parameters :

modifier ( str ) – Modifier, Title of the modifier to adjust (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. text_add ( * , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Insert a text object into the workspace

Parameters :

- radius ( float ) – Radius, (in [0, inf], optional)

- enter_editmode ( bool ) – Enter Edit Mode, Open edit mode right after inserting this item (optional)

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

bpy.ops.object. track_clear ( * , type = 'CLEAR' ) 

Erase a tracking linkage or attribute from an item

Parameters :

type ( Literal [ 'CLEAR' , '`CLEAR_KEEP_TRANSFORM`' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. track_set ( * , type = 'DAMPTRACK' )
