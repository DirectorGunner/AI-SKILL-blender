# Armature Operators

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

### Armature Operators

bpy.ops.armature. align ( )

Line up picked bones with the focused bone (or their predecessor).

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. assign_to_collection ( * , collection_index = -1 , new_collection_name = '' )

Put all active bones into a group, or extract them, contingent on whether the focused bone is already assigned.

Parameters :

- collection_index ( int ) – Collection Index, Index of the collection to assign selected bones to. When the operator should create a new bone collection, use new_collection_name to define the collection name, and set this parameter to the parent index of the new bone collection (in [-1, inf], optional)

- new_collection_name ( str ) – Name, Name of a to-be-added bone collection. Only pass this if you want to create a new bone collection and assign the selected bones to it. To assign to an existing collection, do not include this parameter and use collection_index (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. autoside_names ( * , type = 'XAXIS' )

Systematically relabel active bones according to their location relative to a chosen axis.

Parameters :

type ( Literal [ 'XAXIS' , 'YAXIS' , 'ZAXIS' ] ) – Axis, Axis to tag names with (optional)

- XAXIS
X-Axis – Left/Right.

- YAXIS
Y-Axis – Front/Back.

- ZAXIS
Z-Axis – Top/Bottom.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. bone_primitive_add ( * , name = 'Bone' )

Produce a fresh bone positioned at the 3D crosshairs.

Parameters :

name ( str ) – Name, Name of the newly created bone (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. calculate_roll ( * , type = '`POS_X`' , axis_flip = False , axis_only = False )

Immediately correct the orientation of active bones' local axes.

Parameters :

- type ( Literal [ '`POS_X`' , '`POS_Z`' , '`GLOBAL_POS_X`' , '`GLOBAL_POS_Y`' , '`GLOBAL_POS_Z`' , '`NEG_X`' , '`NEG_Z`' , '`GLOBAL_NEG_X`' , '`GLOBAL_NEG_Y`' , '`GLOBAL_NEG_Z`' , 'ACTIVE' , 'VIEW' , 'CURSOR' ] ) – Type, (optional)

- axis_flip ( bool ) – Flip Axis, Negate the alignment axis (optional)

- axis_only ( bool ) – Shortest Rotation, Ignore the axis direction, use the shortest rotation to align (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. click_extrude ( )

Build a novel bone from the final picked articulation to the cursor spot.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. collection_add ( )

Bring in a bone collection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. collection_assign ( * , name = '' )

Add active bones to the designated group.

Parameters :

name ( str ) – Bone Collection, Name of the bone collection to assign this bone to; empty to assign to the active bone collection (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. collection_create_and_assign ( * , name = '' )

Fabricate a bone group and place all active bones within it.

Parameters :

name ( str ) – Bone Collection, Name of the bone collection to create (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. collection_deselect ( )

Unselect bones belonging to the current Bone Collection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. collection_move ( * , direction = 'UP' )

Shift the active Bone Collection's location in the list.

Parameters :

direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Direction to move the active Bone Collection towards (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. collection_remove ( )

Discard the focused bone collection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. collection_remove_unused ( )

Discard all bone groups that lack both bones and offspring. Recursively applies, purging groups whose sole progeny are also unused.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/anim.py:619

bpy.ops.armature. collection_select ( )

Mark bones in the current Bone Collection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. collection_show_all ( )

Display every bone collection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/anim.py:574

bpy.ops.armature. collection_unassign ( * , name = '' )

Take away active bones from the focused bone group.

Parameters :

name ( str ) – Bone Collection, Name of the bone collection to unassign this bone from; empty to unassign from the active bone collection (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. collection_unassign_named ( * , name = '' , bone_name = '' )

Remove the named bone from that group.

Parameters :

- name ( str ) – Bone Collection, Name of the bone collection to unassign this bone from; empty to unassign from the active bone collection (optional, never None)

- bone_name ( str ) – Bone Name, Name of the bone to unassign from the collection; empty to use the active bone (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. collection_unsolo_all ( )

Turn off 'solo' mode on every bone group.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/anim.py:597

bpy.ops.armature. copy_bone_color_to_selected ( * , bone_type = 'EDIT' )

Apply the focused bone's tint to all active bones.

Parameters :

bone_type ( Literal [ 'EDIT' , 'POSE' ] ) – Type, (optional)

- EDIT
Bone – Apply Bone colors from the focused bone to all active bones.

- POSE
Pose Bone – Apply Pose Bone colors from the focused pose bone to all active pose bones.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/anim.py:493

bpy.ops.armature. delete ( * , confirm = True )

Eliminate active bones from the armature.

Parameters :

confirm ( bool ) – Confirm, Prompt for confirmation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. dissolve ( )

Fuse active bones into the armature.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. duplicate ( * , do_flip_names = False )

Produce copies of active bones within the same rig.

Parameters :

do_flip_names ( bool ) – Flip Names, Try to flip names of the bones, if possible, instead of adding a number extension (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. duplicate_move ( * , `ARMATURE_OT`_duplicate = {} , `TRANSFORM_OT`_translate = {} )

Produce copies of active bones within the same rig and relocate them.

Parameters :

- `ARMATURE_OT`_duplicate ( dict [ str , Any ] ) – Duplicate Selected Bone(s), Produce copies of active bones within the same rig (optional, bpy.ops.armature.duplicate() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. extrude ( * , forked = False )

Extend new bones outward from active articulations.

Parameters :

forked ( bool ) – Forked, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. extrude_forked ( * , `ARMATURE_OT`_extrude = {} , `TRANSFORM_OT`_translate = {} )

Extend new bones outward from active articulations and reposition them.

Parameters :

- `ARMATURE_OT`_extrude ( dict [ str , Any ] ) – Extrude, Extend new bones outward from active articulations (optional, bpy.ops.armature.extrude() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. extrude_move ( * , `ARMATURE_OT`_extrude = {} , `TRANSFORM_OT`_translate = {} )

Extend new bones outward from active articulations and reposition them.

Parameters :

- `ARMATURE_OT`_extrude ( dict [ str , Any ] ) – Extrude, Extend new bones outward from active articulations (optional, bpy.ops.armature.extrude() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. fill ( )

Form a bone between chosen articulations and/or the 3D crosshairs.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. flip_names ( * , do_strip_numbers = False )

Reverse (and normalize) the directional tags in active bone designations.

Parameters :

do_strip_numbers ( bool ) – Strip Numbers, Try to remove right-most dot-number from flipped names.Warning: May result in incoherent naming in some cases(optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. hide ( * , unselected = False )

Mark active bones as invisible in Edit Mode.

Parameters :

unselected ( bool ) – Unselected, Hide unselected rather than selected (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. move_to_collection ( * , collection_index = -1 , new_collection_name = '' )

Shift bones to a group.

Parameters :

- collection_index ( int ) – Collection Index, Index of the collection to move selected bones to. When the operator should create a new bone collection, do not include this parameter and pass new_collection_name (in [-1, inf], optional)

- new_collection_name ( str ) – Name, Name of a to-be-added bone collection. Only pass this if you want to create a new bone collection and move the selected bones to it. To move to an existing collection, do not include this parameter and use collection_index (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. parent_clear ( * , type = 'CLEAR' )

Break the lineage link between active bones and their mothers.

Parameters :

type ( Literal [ 'CLEAR' , 'DISCONNECT' ] ) – Clear Type, What way to clear parenting (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. parent_set ( * , type = 'CONNECTED' )

Establish the active bone as the mother of active bones.

Parameters :

type ( Literal [ 'CONNECTED' , 'OFFSET' ] ) – Parent Type, Type of parenting (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. reveal ( * , select = True )

Display all bones concealed in Edit Mode.

Parameters :

select ( bool ) – Select, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. roll_clear ( * , roll = 0.0 )

Zero out orientation for active bones.

Parameters :

roll ( float ) – Roll, (in [-6.28319, 6.28319], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. select_all ( * , action = 'TOGGLE' )

Change selection status for every bone.

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Selection action to execute (optional)

- TOGGLE
Toggle – Change selection for all elements.

- SELECT
Select – Pick all elements.

- DESELECT
Deselect – Unselect all elements.

- INVERT
Invert – Flip selection state for all elements.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. select_hierarchy ( * , direction = 'PARENT' , extend = False )

Mark the nearest ancestors/descendants of active bones.

Parameters :

- direction ( Literal [ 'PARENT' , 'CHILD' ] ) – Direction, (optional)

- extend ( bool ) – Extend, Extend the selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. select_less ( )

Unselect bones at the edges of each selection zone.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. select_linked ( * , all_forks = False )

Activate every bone joined through lineage connections to the present selection.

Parameters :

all_forks ( bool ) – All Forks, Follow forks in the parents chain (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. select_linked_pick ( * , deselect = False , all_forks = False )

Toggle bone selection through lineage connections at the cursor.

Parameters :

- deselect ( bool ) – Deselect, (optional)

- all_forks ( bool ) – All Forks, Follow forks in the parents chain (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. select_mirror ( * , only_active = False , extend = False )

Duplicate the bone selection across the midline.

Parameters :

- only_active ( bool ) – Active Only, Only operate on the active bone (optional)

- extend ( bool ) – Extend, Extend the selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. select_more ( )

Activate bones attached to the present selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. select_similar ( * , type = 'LENGTH' , threshold = 0.1 )

Activate bones matching comparable traits.

Parameters :

- type ( Literal [ 'CHILDREN' , '`CHILDREN_IMMEDIATE`' , 'SIBLINGS' , 'LENGTH' , 'DIRECTION' , 'PREFIX' , 'SUFFIX' , '`BONE_COLLECTION`' , 'COLOR' , 'SHAPE' ] ) – Type, (optional)

- threshold ( float ) – Threshold, (in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. separate ( )

Partition active bones into their own rig.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. shortest_path_pick ( )

Activate the shortest chain between two bones.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. split ( )

Isolate active bones from unselected connected ones.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. subdivide ( * , number_cuts = 1 )

Fragment active bones into shorter sequences.

Parameters :

number_cuts ( int ) – Number of Cuts, (in [1, 1000], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. switch_direction ( )

Invert the trajectory of a bone lineage (swap head and foot).

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.armature. symmetrize ( * , direction = '`NEGATIVE_X`' , copy_bone_colors = False )

Enforce symmetry by replicating or using current bones.

Parameters :

- direction ( Literal [ '`NEGATIVE_X`' , '`POSITIVE_X`' ] ) – Direction, Which sides to copy from and to (when both are selected) (optional)

- copy_bone_colors ( bool ) – Bone Colors, Copy colors to existing bones (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
