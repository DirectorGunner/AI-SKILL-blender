# Pose Operators (part 2)

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. copy ( )
Copies the selected bones' current pose to the internal clipboard.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. flip_names ( * , do_strip_numbers = False )
Flips (and corrects) the axis suffixes in the names of the selected bones.
Parameters: do_strip_numbers ( bool ) – Strip Numbers, Try to remove right-most dot-number from flipped names. Warning: May result in incoherent naming in some cases (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. hide ( * , unselected = False )
Tags the selected bones to be hidden in Pose Mode.
Parameters: unselected ( bool ) – Unselected, (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. ik_add ( * , with_targets = True )
Adds an IK Constraint to the active Bone; the target can be a selected bone or object.
Parameters: with_targets ( bool ) – With Targets, Assign IK Constraint with targets derived from the select bones/objects (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. ik_clear ( )
Removes all IK Constraints from the selected bones.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. loc_clear ( )
Resets the selected bones' locations to their default values.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. paste ( * , flipped = False , selected_mask = False )
Pastes the stored pose onto the current pose.
Parameters:
- flipped ( bool ) – Flipped on X-Axis, Paste the stored pose flipped on to current pose (optional)
- selected_mask ( bool ) – On Selected Only, Only paste the stored pose on to selected bones in the current pose (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. paths_calculate ( * , display_type = 'RANGE' , range = 'SCENE' , bake_location = 'HEADS' )
Calculates paths for the selected bones.
Parameters:
- display_type (Literal[Motionpath Display Type Items]) – Display Type, (optional)
- range (Literal[Motionpath Range Items]) – Computation Range, (optional)
- bake_location (Literal[Motionpath Bake Location Items]) – Bake Location, Which point on the bones is used when calculating paths (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. paths_clear ( * , only_selected = False )
Undocumented, consider contributing.
Parameters: only_selected ( bool ) – Only Selected, Only clear motion paths of selected bones (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. paths_range_update ( )
Updates the motion-paths frame range from the Scene's current frame range.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. paths_update ( )
Recalculates paths for bones that already have them.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. propagate ( * , mode = '`NEXT_KEY`' , end_frame = 250.0 )
Copies selected aspects of the current pose to subsequent poses already keyframed.
Parameters:
- mode ( Literal [ '`NEXT_KEY`' , '`LAST_KEY`' , '`BEFORE_FRAME`' , '`BEFORE_END`' , '`SELECTED_KEYS`' , '`SELECTED_MARKERS`' ] ) – Terminate Mode, Method used to determine when to stop propagating pose to keyframes (optional)
- `NEXT_KEY` — To Next Keyframe: propagate the pose only to the first keyframe after the current frame.
- `LAST_KEY` — To Last Keyframe: propagate the pose only to the last keyframe (i.e. making the action cyclic).
- `BEFORE_FRAME` — Before Frame: propagate the pose to all keyframes between the current frame and the 'Frame' property.
- `BEFORE_END` — Before Last Keyframe: propagate the pose to all keyframes from the current frame until no more are found.
- `SELECTED_KEYS` — On Selected Keyframes: propagate the pose to all selected keyframes.
- `SELECTED_MARKERS` — On Selected Markers: propagate the pose to all keyframes occurring on frames with Scene Markers after the current frame.
- end_frame ( float ) – End Frame, Frame to stop propagating frames to (for 'Before Frame' mode) (in [1.17549e-38, inf], optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. push ( * , factor = 0.5 , prev_frame = 0 , next_frame = 0 , channels = 'ALL' , axis_lock = 'FREE' )
Exaggerates the current pose relative to the breakdown pose.
Parameters:
- factor ( float ) – Factor, Weighting factor for which keyframe is favored more (in [0, 1], optional)
- prev_frame ( int ) – Previous Keyframe, Frame number of keyframe immediately before the current frame (in [-1048574, 1048574], optional)
- next_frame ( int ) – Next Keyframe, Frame number of keyframe immediately after the current frame (in [-1048574, 1048574], optional)
- channels ( Literal [ 'ALL' , 'LOC' , 'ROT' , 'SIZE' , 'BBONE' , 'CUSTOM' ] ) – Channels, Set of properties that are affected (optional)
- ALL — All Properties: all properties, including transforms, bendy bone shape, and custom properties.
- LOC — Location: location only.
- ROT — Rotation: rotation only.
- SIZE — Scale: scale only.
- BBONE — Bendy Bone: bendy bone shape properties.
- CUSTOM — Custom Properties: custom properties.
- axis_lock ( Literal [ 'FREE' , 'X' , 'Y' , 'Z' ] ) – Axis Lock, Transform axis to restrict effects to (optional)
- FREE — Free: all axes are affected.
- X — X: only X-axis transforms are affected.
- Y — Y: only Y-axis transforms are affected.
- Z — Z: only Z-axis transforms are affected.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. quaternions_flip ( )
Flips quaternion values to achieve the desired rotations while keeping the same orientations.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. relax ( * , factor = 0.5 , prev_frame = 0 , next_frame = 0 , channels = 'ALL' , axis_lock = 'FREE' )

Makes the current pose more similar to its breakdown pose.
Parameters:
- factor ( float ) – Factor, Weighting factor for which keyframe is favored more (in [0, 1], optional)
- prev_frame ( int ) – Previous Keyframe, Frame number of keyframe immediately before the current frame (in [-1048574, 1048574], optional)
- next_frame ( int ) – Next Keyframe, Frame number of keyframe immediately after the current frame (in [-1048574, 1048574], optional)
- channels ( Literal [ 'ALL' , 'LOC' , 'ROT' , 'SIZE' , 'BBONE' , 'CUSTOM' ] ) – Channels, Set of properties that are affected (optional)
- ALL — All Properties: all properties, including transforms, bendy bone shape, and custom properties.
- LOC — Location: location only.
- ROT — Rotation: rotation only.
- SIZE — Scale: scale only.
- BBONE — Bendy Bone: bendy bone shape properties.
- CUSTOM — Custom Properties: custom properties.
- axis_lock ( Literal [ 'FREE' , 'X' , 'Y' , 'Z' ] ) – Axis Lock, Transform axis to restrict effects to (optional)
- FREE — Free: all axes are affected.
- X — X: only X-axis transforms are affected.
- Y — Y: only Y-axis transforms are affected.
- Z — Z: only Z-axis transforms are affected.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. reveal ( * , select = True )
Reveals all bones hidden in Pose Mode.
Parameters: select ( bool ) – Select, (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. rot_clear ( )
Resets the selected bones' rotations to their default values.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. rotation_mode_set ( * , type = 'QUATERNION' )
Sets the rotation representation used by the selected bones.
Parameters: type (Literal[Object Rotation Mode Items]) – Rotation Mode, (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. scale_clear ( )
Resets the selected bones' scaling to their default values.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. select_all ( * , action = 'TOGGLE' )
Toggles the selection status of all bones.
Parameters: action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Selection action to execute (optional)
- TOGGLE — Toggle: toggle selection for all elements.
- SELECT — Select: select all elements.
- DESELECT — Deselect: deselect all elements.
- INVERT — Invert: invert selection of all elements.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. select_constraint_target ( )
Selects bones used as targets for the currently selected bones.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. select_grouped ( * , extend = False , type = 'COLLECTION' )
Selects all visible bones grouped by similar properties.
Parameters:
- extend ( bool ) – Extend, Extend selection instead of deselecting everything first (optional)
- type ( Literal [ 'COLLECTION' , 'COLOR' , 'KEYINGSET' , 'CHILDREN' , '`CHILDREN_IMMEDIATE`' , 'PARENT' , 'SIBLINGS' ] ) – Type, (optional)
- COLLECTION — Collection: same collections as the active bone.
- COLOR — Color: same color as the active bone.
- KEYINGSET — Keying Set: all bones affected by the active Keying Set.
- CHILDREN — Children: select all children of the currently selected bones.
- `CHILDREN_IMMEDIATE` — Immediate Children: select direct children of the currently selected bones.
- PARENT — Parents: select the parents of the currently selected bones.
- SIBLINGS — Siblings: select all bones that have the same parent as the currently selected bones.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. select_hierarchy ( * , direction = 'PARENT' , extend = False )
Selects the immediate parent/children of the selected bones.
Parameters:
- direction ( Literal [ 'PARENT' , 'CHILD' ] ) – Direction, (optional)
- extend ( bool ) – Extend, Extend the selection (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. select_linked ( )
Selects all bones linked by connected parent/child relationships from the current selection.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. select_linked_pick ( * , extend = False )
Selects bones linked by connected parent/child relationships under the mouse cursor.
Parameters: extend ( bool ) – Extend, Extend selection instead of deselecting everything first (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. select_mirror ( * , only_active = False , extend = False )
Mirrors the bone selection.
Parameters:
- only_active ( bool ) – Active Only, Only operate on the active bone (optional)
- extend ( bool ) – Extend, Extend the selection (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. select_parent ( )
Selects bones that are parents of the currently selected bones.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. selection_set_add ( )
Creates a new empty Selection Set.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/bone_selection_sets.py:147

bpy.ops.pose. selection_set_add_and_assign ( )
Creates a new Selection Set with the currently selected bones.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/bone_selection_sets.py:278

bpy.ops.pose. selection_set_assign ( )
Adds the selected bones to a Selection Set.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/bone_selection_sets.py:194

bpy.ops.pose. selection_set_copy ( )
Copies the selected Selection Set(s) to the clipboard.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/bone_selection_sets.py:290

bpy.ops.pose. selection_set_delete_all ( )
Removes all Selection Sets from this Armature.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/bone_selection_sets.py:77

bpy.ops.pose. selection_set_deselect ( )
Removes Selection Set bones from the current selection.

Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/bone_selection_sets.py:261

bpy.ops.pose. selection_set_move ( * , direction = 'UP' )
Moves the active Selection Set up or down the list of sets.
Parameters: direction ( Literal [ 'UP' , 'DOWN' ] ) – Move Direction, Direction to move the active Selection Set: UP (default) or DOWN (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/bone_selection_sets.py:126

bpy.ops.pose. selection_set_paste ( )
Adds new Selection Set(s) from the clipboard.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/bone_selection_sets.py:302

bpy.ops.pose. selection_set_remove ( )
Removes a Selection Set from this Armature.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/bone_selection_sets.py:165

bpy.ops.pose. selection_set_remove_bones ( )
Removes the selected bones from all Selection Sets.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/bone_selection_sets.py:89

bpy.ops.pose. selection_set_select ( * , selection_set_index = -1 )
Selects the bones from this Selection Set.
Parameters: selection_set_index ( int ) – Selection Set Index, Which Selection Set to select; -1 uses the active Selection Set (in [-inf, inf], optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/bone_selection_sets.py:239

bpy.ops.pose. selection_set_unassign ( )
Removes the selected bones from a Selection Set.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/bone_selection_sets.py:213

bpy.ops.pose. transforms_clear ( )
Resets the location, rotation, and scaling of the selected bones to their default values.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. user_transforms_clear ( * , only_selected = True )
Resets pose bone transforms to the keyframed state.
Parameters: only_selected ( bool ) – Only Selected, Only visible/selected bones (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.pose. visual_transform_apply ( )
Applies the final constrained position of pose bones to their transform.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
