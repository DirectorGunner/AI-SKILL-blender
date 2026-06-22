# Constraint Operators

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

### Constraint Operators

bpy.ops.constraint. add_target ( )

Enroll a recipient in the constraint

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/constraint.py:26

bpy.ops.constraint. apply ( * , constraint = '' , owner = 'OBJECT' , report = False )

Implement the constraint and withdraw it from the roster

Parameters :

- constraint ( str ) – Constraint, Name of the constraint to edit (optional, never None)

- owner ( Literal [ 'OBJECT' , 'BONE' ] ) – Owner, The owner of this constraint (optional)

- OBJECT
Object – Edit a constraint on the active object.

- BONE
Bone – Edit a constraint on the active bone.

- report ( bool ) – Report, Create a notification after the operation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.constraint. childof_clear_inverse ( * , constraint = '' , owner = 'OBJECT' )

Nullify the counterbalancing transform for Child Of constraint

Parameters :

- constraint ( str ) – Constraint, Name of the constraint to edit (optional, never None)

- owner ( Literal [ 'OBJECT' , 'BONE' ] ) – Owner, The owner of this constraint (optional)

- OBJECT
Object – Edit a constraint on the active object.

- BONE
Bone – Edit a constraint on the active bone.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.constraint. childof_set_inverse ( * , constraint = '' , owner = 'OBJECT' )

Calibrate the counterbalancing transform for Child Of constraint

Parameters :

- constraint ( str ) – Constraint, Name of the constraint to edit (optional, never None)

- owner ( Literal [ 'OBJECT' , 'BONE' ] ) – Owner, The owner of this constraint (optional)

- OBJECT
Object – Edit a constraint on the active object.

- BONE
Bone – Edit a constraint on the active bone.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.constraint. copy ( * , constraint = '' , owner = 'OBJECT' , report = False )

Reproduce constraint at the same location in the roster

Parameters :

- constraint ( str ) – Constraint, Name of the constraint to edit (optional, never None)

- owner ( Literal [ 'OBJECT' , 'BONE' ] ) – Owner, The owner of this constraint (optional)

- OBJECT
Object – Edit a constraint on the active object.

- BONE
Bone – Edit a constraint on the active bone.

- report ( bool ) – Report, Create a notification after the operation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.constraint. copy_to_selected ( * , constraint = '' , owner = 'OBJECT' )

Duplicate constraint across other picked entities/skeletal parts

Parameters :

- constraint ( str ) – Constraint, Name of the constraint to edit (optional, never None)

- owner ( Literal [ 'OBJECT' , 'BONE' ] ) – Owner, The owner of this constraint (optional)

- OBJECT
Object – Edit a constraint on the active object.

- BONE
Bone – Edit a constraint on the active bone.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.constraint. delete ( * , constraint = '' , owner = 'OBJECT' , report = False )

Withdraw constraint from the roster

Parameters :

- constraint ( str ) – Constraint, Name of the constraint to edit (optional, never None)

- owner ( Literal [ 'OBJECT' , 'BONE' ] ) – Owner, The owner of this constraint (optional)

- OBJECT
Object – Edit a constraint on the active object.

- BONE
Bone – Edit a constraint on the active bone.

- report ( bool ) – Report, Create a notification after the operation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.constraint. disable_keep_transform ( )

Diminish the strength of this constraint to nothing while preserving the entity's current state. Other energized constraints retain their bearing on the ultimate outcome

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/constraint.py:86

bpy.ops.constraint. followpath_path_animate ( * , constraint = '' , owner = 'OBJECT' , frame_start = 1 , length = 100 )

Establish a standard timeline progression for the path used by this constraint unless one is already in place

Parameters :

- constraint ( str ) – Constraint, Name of the constraint to edit (optional, never None)

- owner ( Literal [ 'OBJECT' , 'BONE' ] ) – Owner, The owner of this constraint (optional)

- OBJECT
Object – Edit a constraint on the active object.

- BONE
Bone – Edit a constraint on the active bone.

- frame_start ( int ) – Start Frame, First frame of path animation (in [-1048574, 1048574], optional)

- length ( int ) – Length, Number of frames that path animation should take (in [0, 1048574], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.constraint. limitdistance_reset ( * , constraint = '' , owner = 'OBJECT' )

Reinitialize the maximum span for Limit Distance Constraint

Parameters :

- constraint ( str ) – Constraint, Name of the constraint to edit (optional, never None)

- owner ( Literal [ 'OBJECT' , 'BONE' ] ) – Owner, The owner of this constraint (optional)

- OBJECT
Object – Edit a constraint on the active object.

- BONE
Bone – Edit a constraint on the active bone.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.constraint. move_down ( * , constraint = '' , owner = 'OBJECT' )

Reposition constraint lower in the roster

Parameters :

- constraint ( str ) – Constraint, Name of the constraint to edit (optional, never None)

- owner ( Literal [ 'OBJECT' , 'BONE' ] ) – Owner, The owner of this constraint (optional)

- OBJECT
Object – Edit a constraint on the active object.

- BONE
Bone – Edit a constraint on the active bone.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.constraint. move_to_index ( * , constraint = '' , owner = 'OBJECT' , index = 0 )

Adjust the constraint's location in the catalog so evaluation follows the specified number of other constraints

Parameters :

- constraint ( str ) – Constraint, Name of the constraint to edit (optional, never None)

- owner ( Literal [ 'OBJECT' , 'BONE' ] ) – Owner, The owner of this constraint (optional)

- OBJECT
Object – Edit a constraint on the active object.

- BONE
Bone – Edit a constraint on the active bone.

- index ( int ) – Index, The index to move the constraint to (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.constraint. move_up ( * , constraint = '' , owner = 'OBJECT' )

Reposition constraint higher in the roster

Parameters :

- constraint ( str ) – Constraint, Name of the constraint to edit (optional, never None)

- owner ( Literal [ 'OBJECT' , 'BONE' ] ) – Owner, The owner of this constraint (optional)

- OBJECT
Object – Edit a constraint on the active object.

- BONE
Bone – Edit a constraint on the active bone.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.constraint. normalize_target_weights ( )

Scale the importance of all recipient skeletal parts to total 100%

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/constraint.py:61

bpy.ops.constraint. objectsolver_clear_inverse ( * , constraint = '' , owner = 'OBJECT' )

Nullify the counterbalancing transform for Object Solver constraint

Parameters :

- constraint ( str ) – Constraint, Name of the constraint to edit (optional, never None)

- owner ( Literal [ 'OBJECT' , 'BONE' ] ) – Owner, The owner of this constraint (optional)

- OBJECT
Object – Edit a constraint on the active object.

- BONE
Bone – Edit a constraint on the active bone.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.constraint. objectsolver_set_inverse ( * , constraint = '' , owner = 'OBJECT' )

Calibrate the counterbalancing transform for Object Solver constraint

Parameters :

- constraint ( str ) – Constraint, Name of the constraint to edit (optional, never None)

- owner ( Literal [ 'OBJECT' , 'BONE' ] ) – Owner, The owner of this constraint (optional)

- OBJECT
Object – Edit a constraint on the active object.

- BONE
Bone – Edit a constraint on the active bone.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.constraint. remove_target ( * , index = 0 )

Unregister the recipient from the constraint

Parameters :

index ( int ) – index, (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/constraint.py:44

bpy.ops.constraint. stretchto_reset ( * , constraint = '' , owner = 'OBJECT' )

Restore the standard distance of the skeletal part for Stretch To Constraint

Parameters :

- constraint ( str ) – Constraint, Name of the constraint to edit (optional, never None)

- owner ( Literal [ 'OBJECT' , 'BONE' ] ) – Owner, The owner of this constraint (optional)

- OBJECT
Object – Edit a constraint on the active object.

- BONE
Bone – Edit a constraint on the active bone.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
