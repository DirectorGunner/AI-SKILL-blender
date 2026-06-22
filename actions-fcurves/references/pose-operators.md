# Pose Operators (part 1)

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

### Pose Operators 

bpy.ops.pose. armature_apply ( * , selected = False ) 

Treat the current pose as the default rest configuration

Parameters :

selected ( bool ) – Selected Only, Only apply the selected bones (with propagation to children) (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. autoside_names ( * , axis = 'XAXIS' ) 

Automatically assigns names to selected bones based on which side of the chosen axis they occupy

Parameters :

axis ( Literal [ 'XAXIS' , 'YAXIS' , 'ZAXIS' ] ) – Axis, Axis to tag names with (optional)

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

bpy.ops.pose. blend_to_neighbor ( * , factor = 0.5 , prev_frame = 0 , next_frame = 0 , channels = 'ALL' , axis_lock = 'FREE' ) 

Smoothly transition from the current position toward a neighboring keyframe

Parameters :

- factor ( float ) – Factor, Weighting factor for which keyframe is favored more (in [0, 1], optional)

- prev_frame ( int ) – Previous Keyframe, Frame number of keyframe immediately before the current frame (in [-1048574, 1048574], optional)

- next_frame ( int ) – Next Keyframe, Frame number of keyframe immediately after the current frame (in [-1048574, 1048574], optional)

- channels ( Literal [ 'ALL' , 'LOC' , 'ROT' , 'SIZE' , 'BBONE' , 'CUSTOM' ] ) – Channels, Set of properties that are affected (optional)

- ALL
All Properties – All properties, including transforms, bendy bone shape, and custom properties.

- LOC
Location – Location only.

- ROT
Rotation – Rotation only.

- SIZE
Scale – Scale only.

- BBONE
Bendy Bone – Bendy Bone shape properties.

- CUSTOM
Custom Properties – Custom properties.

- axis_lock ( Literal [ 'FREE' , 'X' , 'Y' , 'Z' ] ) – Axis Lock, Transform axis to restrict effects to (optional)

- FREE
Free – All axes are affected.

- X
X – Only X-axis transforms are affected.

- Y
Y – Only Y-axis transforms are affected.

- Z
Z – Only Z-axis transforms are affected.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. blend_with_rest ( * , factor = 0.5 , prev_frame = 0 , next_frame = 0 , channels = 'ALL' , axis_lock = 'FREE' ) 

Shift the current pose closer to or further from the rest configuration

Parameters :

- factor ( float ) – Factor, Weighting factor for which keyframe is favored more (in [0, 1], optional)

- prev_frame ( int ) – Previous Keyframe, Frame number of keyframe immediately before the current frame (in [-1048574, 1048574], optional)

- next_frame ( int ) – Next Keyframe, Frame number of keyframe immediately after the current frame (in [-1048574, 1048574], optional)

- channels ( Literal [ 'ALL' , 'LOC' , 'ROT' , 'SIZE' , 'BBONE' , 'CUSTOM' ] ) – Channels, Set of properties that are affected (optional)

- ALL
All Properties – All properties, including transforms, bendy bone shape, and custom properties.

- LOC
Location – Location only.

- ROT
Rotation – Rotation only.

- SIZE
Scale – Scale only.

- BBONE
Bendy Bone – Bendy Bone shape properties.

- CUSTOM
Custom Properties – Custom properties.

- axis_lock ( Literal [ 'FREE' , 'X' , 'Y' , 'Z' ] ) – Axis Lock, Transform axis to restrict effects to (optional)

- FREE
Free – All axes are affected.

- X
X – Only X-axis transforms are affected.

- Y
Y – Only Y-axis transforms are affected.

- Z
Z – Only Z-axis transforms are affected.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. breakdown ( * , factor = 0.5 , prev_frame = 0 , next_frame = 0 , channels = 'ALL' , axis_lock = 'FREE' ) 

Build an appropriate transition pose at the current keyframe

Parameters :

- factor ( float ) – Factor, Weighting factor for which keyframe is favored more (in [0, 1], optional)

- prev_frame ( int ) – Previous Keyframe, Frame number of keyframe immediately before the current frame (in [-1048574, 1048574], optional)

- next_frame ( int ) – Next Keyframe, Frame number of keyframe immediately after the current frame (in [-1048574, 1048574], optional)

- channels ( Literal [ 'ALL' , 'LOC' , 'ROT' , 'SIZE' , 'BBONE' , 'CUSTOM' ] ) – Channels, Set of properties that are affected (optional)

- ALL
All Properties – All properties, including transforms, bendy bone shape, and custom properties.

- LOC
Location – Location only.

- ROT
Rotation – Rotation only.

- SIZE
Scale – Scale only.

- BBONE
Bendy Bone – Bendy Bone shape properties.

- CUSTOM
Custom Properties – Custom properties.

- axis_lock ( Literal [ 'FREE' , 'X' , 'Y' , 'Z' ] ) – Axis Lock, Transform axis to restrict effects to (optional)

- FREE
Free – All axes are affected.

- X
X – Only X-axis transforms are affected.

- Y
Y – Only Y-axis transforms are affected.

- Z
Z – Only Z-axis transforms are affected.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. constraint_add ( * , type = '`CHILD_OF`' ) 

Attach a constraint to the active bone

Parameters :

type (Literal[Constraint Type Items]) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. constraint_add_with_targets ( * , type = '`CHILD_OF`' ) 

Attach a constraint to the active bone, automatically linking the target to the chosen Objects or Bones

Parameters :

type (Literal[Constraint Type Items]) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. constraints_clear ( ) 

Strip all constraints from the chosen bones

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. constraints_copy ( ) 

Duplicate constraints to additional chosen bones

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. copy ( ) 

Retain the current pose configuration of the chosen bones in the clipboard

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. flip_names ( * , do_strip_numbers = False ) 

Corrects and reverses the axis tags in the names of selected bones

Parameters :

do_strip_numbers ( bool ) – Strip Numbers, Try to remove right-most dot-number from flipped names.Warning: May result in incoherent naming in some cases(optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. hide ( * , unselected = False ) 

Exclude selected bones from appearance in Pose Mode

Parameters :

unselected ( bool ) – Unselected, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. ik_add ( * , with_targets = True ) 

Affix an Inverse Kinematics Constraint to the active Bone, with an optional chosen bone or object as target

Parameters :

with_targets ( bool ) – With Targets, Assign IK Constraint with targets derived from the select bones/objects (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. ik_clear ( ) 

Strip all Inverse Kinematics Constraints from chosen bones

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. loc_clear ( ) 

Restore the position of selected bones to factory defaults

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. paste ( * , flipped = False , selected_mask = False ) 

Place the retained pose onto the active pose

Parameters :

- flipped ( bool ) – Flipped on X-Axis, Paste the stored pose flipped on to current pose (optional)

- selected_mask ( bool ) – On Selected Only, Only paste the stored pose on to selected bones in the current pose (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. paths_calculate ( * , display_type = 'RANGE' , range = 'SCENE' , bake_location = 'HEADS' ) 

Determine motion paths for the chosen bones

Parameters :

- display_type (Literal[Motionpath Display Type Items]) – Display Type, (optional)

- range (Literal[Motionpath Range Items]) – Computation Range, (optional)

- bake_location (Literal[Motionpath Bake Location Items]) – Bake Location, Which point on the bones is used when calculating paths (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. paths_clear ( * , only_selected = False ) 

Undocumented, consider contributing.

Parameters :

only_selected ( bool ) – Only Selected, Only clear motion paths of selected bones (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. paths_range_update ( ) 

Align the frame range for motion paths with the Scene's current frame span

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. paths_update ( ) 

Refresh paths for bones that already have them

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. propagate ( * , mode = '`NEXT_KEY`' , end_frame = 250.0 ) 

Push selected aspects of the current pose forward to future keyframes

Parameters :

- mode ( Literal [ '`NEXT_KEY`' , '`LAST_KEY`' , '`BEFORE_FRAME`' , '`BEFORE_END`' , '`SELECTED_KEYS`' , '`SELECTED_MARKERS`' ] ) – Terminate Mode, Method used to determine when to stop propagating pose to keyframes (optional)

- `NEXT_KEY`
To Next Keyframe – Propagate pose to first keyframe following the current frame only.

- `LAST_KEY`
To Last Keyframe – Propagate pose to the last keyframe only (i.e. making action cyclic).

- `BEFORE_FRAME`
Before Frame – Propagate pose to all keyframes between current frame and 'Frame' property.

- `BEFORE_END`
Before Last Keyframe – Propagate pose to all keyframes from current frame until no more are found.

- `SELECTED_KEYS`
On Selected Keyframes – Propagate pose to all selected keyframes.

- `SELECTED_MARKERS`
On Selected Markers – Propagate pose to all keyframes occurring on frames with Scene Markers after the current frame.

- end_frame ( float ) – End Frame, Frame to stop propagating frames to (for 'Before Frame' mode) (in [1.17549e-38, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. push ( * , factor = 0.5 , prev_frame = 0 , next_frame = 0 , channels = 'ALL' , axis_lock = 'FREE' ) 

Amplify the active pose relative to the breakdown pose

Parameters :

- factor ( float ) – Factor, Weighting factor for which keyframe is favored more (in [0, 1], optional)

- prev_frame ( int ) – Previous Keyframe, Frame number of keyframe immediately before the current frame (in [-1048574, 1048574], optional)

- next_frame ( int ) – Next Keyframe, Frame number of keyframe immediately after the current frame (in [-1048574, 1048574], optional)

- channels ( Literal [ 'ALL' , 'LOC' , 'ROT' , 'SIZE' , 'BBONE' , 'CUSTOM' ] ) – Channels, Set of properties that are affected (optional)

- ALL
All Properties – All properties, including transforms, bendy bone shape, and custom properties.

- LOC
Location – Location only.

- ROT
Rotation – Rotation only.

- SIZE
Scale – Scale only.

- BBONE
Bendy Bone – Bendy Bone shape properties.

- CUSTOM
Custom Properties – Custom properties.

- axis_lock ( Literal [ 'FREE' , 'X' , 'Y' , 'Z' ] ) – Axis Lock, Transform axis to restrict effects to (optional)

- FREE
Free – All axes are affected.

- X
X – Only X-axis transforms are affected.

- Y
Y – Only Y-axis transforms are affected.

- Z
Z – Only Z-axis transforms are affected.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. quaternions_flip ( ) 

Reverse quaternion values to reach the desired rotation, while preserving the final orientation

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. relax ( * , factor = 0.5 , prev_frame = 0 , next_frame = 0 , channels = 'ALL' , axis_lock = 'FREE' ) 

Move the current pose toward its breakdown configuration

Parameters :

- factor ( float ) – Factor, Weighting factor for which keyframe is favored more (in [0, 1], optional)

- prev_frame ( int ) – Previous Keyframe, Frame number of keyframe immediately before the current frame (in [-1048574, 1048574], optional)

- next_frame ( int ) – Next Keyframe, Frame number of keyframe immediately after the current frame (in [-1048574, 1048574], optional)

- channels ( Literal [ 'ALL' , 'LOC' , 'ROT' , 'SIZE' , 'BBONE' , 'CUSTOM' ] ) – Channels, Set of properties that are affected (optional)

- ALL
All Properties – All properties, including transforms, bendy bone shape, and custom properties.

- LOC
Location – Location only.

- ROT
Rotation – Rotation only.

- SIZE
Scale – Scale only.

- BBONE
Bendy Bone – Bendy Bone shape properties.

- CUSTOM
Custom Properties – Custom properties.

- axis_lock ( Literal [ 'FREE' , 'X' , 'Y' , 'Z' ] ) – Axis Lock, Transform axis to restrict effects to (optional)

- FREE
Free – All axes are affected.

- X
X – Only X-axis transforms are affected.

- Y
Y – Only Y-axis transforms are affected.

- Z
Z – Only Z-axis transforms are affected.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. reveal ( * , select = True ) 

Show all bones that were concealed during Pose Mode

Parameters :

select ( bool ) – Select, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. rot_clear ( ) 

Restore the rotation of selected bones to factory defaults

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. rotation_mode_set ( * , type = 'QUATERNION' ) 

Define the rotation format applied by selected bones

Parameters :

type (Literal[Object Rotation Mode Items]) – Rotation Mode, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. scale_clear ( ) 

Restore the scale of selected bones to factory defaults

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. select_all ( * , action = 'TOGGLE' ) 

Switch selection status for all bones

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Selection action to execute (optional)

- TOGGLE
Toggle – Toggle selection for all elements.

- SELECT
Select – Select all elements.

- DESELECT
Deselect – Deselect all elements.

- INVERT
Invert – Invert selection of all elements.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. select_constraint_target ( ) 

Highlight bones that serve as targets for the presently selected bones

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. select_grouped ( * , extend = False , type = 'COLLECTION' ) 

Highlight all visible bones organized by matching properties

Parameters :

- extend ( bool ) – Extend, Extend selection instead of deselecting everything first (optional)

- type ( Literal [ 'COLLECTION' , 'COLOR' , 'KEYINGSET' , 'CHILDREN' , '`CHILDREN_IMMEDIATE`' , 'PARENT' , 'SIBLINGS' ] ) – Type, (optional)

- COLLECTION
Collection – Same collections as the active bone.

- COLOR
Color – Same color as the active bone.

- KEYINGSET
Keying Set – All bones affected by active Keying Set.

- CHILDREN
Children – Select all children of currently selected bones.

- `CHILDREN_IMMEDIATE`
Immediate Children – Select direct children of currently selected bones.

- PARENT
Parents – Select the parents of currently selected bones.

- SIBLINGS
Siblings – Select all bones that have the same parent as currently selected bones.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. select_hierarchy ( * , direction = 'PARENT' , extend = False ) 

Pick the direct parent and children of currently selected bones

Parameters :

- direction ( Literal [ 'PARENT' , 'CHILD' ] ) – Direction, (optional)

- extend ( bool ) – Extend, Extend the selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. select_linked ( ) 

Pick all bones joined by connected ancestry from the active selection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. select_linked_pick ( * , extend = False ) 

Pick bones joined by connected ancestry underneath the cursor

Parameters :

extend ( bool ) – Extend, Extend selection instead of deselecting everything first (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. select_mirror ( * , only_active = False , extend = False ) 

Reverse the bone selection across the symmetry plane

Parameters :

- only_active ( bool ) – Active Only, Only operate on the active bone (optional)

- extend ( bool ) – Extend, Extend the selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. select_parent ( ) 

Highlight bones that serve as parents for the currently selected bones

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. selection_set_add ( ) 

Establish a fresh vacant Selection Set

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/bone_selection_sets.py:147

bpy.ops.pose. selection_set_add_and_assign ( ) 

Establish a fresh Selection Set pre-filled with the currently selected bones

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/bone_selection_sets.py:278

bpy.ops.pose. selection_set_assign ( ) 

Include selected bones in the Selection Set

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/bone_selection_sets.py:194

bpy.ops.pose. selection_set_copy ( ) 

Retain the chosen Selection Set(s) in the clipboard

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/bone_selection_sets.py:290

bpy.ops.pose. selection_set_delete_all ( ) 

Erase all Selection Sets from this Armature

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/bone_selection_sets.py:77

bpy.ops.pose. selection_set_deselect ( ) 

Take Selection Set bones away from the current selection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/bone_selection_sets.py:261

bpy.ops.pose. selection_set_move ( * , direction = 'UP' ) 

Shift the active Selection Set forward or backward in its ordering

Parameters :

direction ( Literal [ 'UP' , 'DOWN' ] ) – Move Direction, Direction to move the active Selection Set: UP (default) or DOWN (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/bone_selection_sets.py:126

bpy.ops.pose. selection_set_paste ( ) 

Bring fresh Selection Set(s) into the workspace from the clipboard

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/bone_selection_sets.py:302

bpy.ops.pose. selection_set_remove ( ) 

Erase a Selection Set from this Armature

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/bone_selection_sets.py:165

bpy.ops.pose. selection_set_remove_bones ( ) 

Take the selected bones out of all Selection Sets

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/bone_selection_sets.py:89

bpy.ops.pose. selection_set_select ( * , selection_set_index = -1 ) 

Highlight the bones within this Selection Set

Parameters :

selection_set_index ( int ) – Selection Set Index, Which Selection Set to select; -1 uses the active Selection Set (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/bone_selection_sets.py:239

bpy.ops.pose. selection_set_unassign ( ) 

Take selected bones away from the Selection Set

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/bone_selection_sets.py:213

bpy.ops.pose. transforms_clear ( ) 

Restore the position, rotation, and scale of selected bones to factory defaults

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. user_transforms_clear ( * , only_selected = True ) 

Reset pose bone transforms to their keyframed state

Parameters :

only_selected ( bool ) – Only Selected, Only visible/selected bones (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pose. visual_transform_apply ( ) 

Bake the final constrained position of pose bones into their transform data

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
