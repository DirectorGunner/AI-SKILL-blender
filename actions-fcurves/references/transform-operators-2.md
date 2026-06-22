# Transform Operators (part 2)

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

Shrinks/fattens the selected vertices along their normals.
Parameters:
- value ( float ) – Offset, (in [-inf, inf], optional)
- use_even_offset ( bool ) – Offset Even, Scale the offset to give more even thickness (optional)
- mirror ( bool ) – Mirror Editing, (optional)
- use_proportional_edit ( bool ) – Proportional Editing, (optional)
- proportional_edit_falloff (Literal[Proportional Falloff Items]) – Proportional Falloff, Falloff type for proportional editing mode (optional)
- proportional_size ( float ) – Proportional Size, (in [1e-06, inf], optional)
- use_proportional_connected ( bool ) – Connected, (optional)
- use_proportional_projected ( bool ) – Projected (2D), (optional)
- snap ( bool ) – Use Snapping Options, (optional)
- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)
- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.transform. skin_resize ( * , value = (1.0, 1.0, 1.0) , orient_type = 'GLOBAL' , orient_matrix = ((0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0)) , orient_matrix_type = 'GLOBAL' , constraint_axis = (False, False, False) , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , snap = False , snap_elements = {'INCREMENT'} , use_snap_project = False , snap_target = 'CLOSEST' , use_snap_self = True , use_snap_edit = True , use_snap_nonedit = True , use_snap_selectable = False , snap_point = (0.0, 0.0, 0.0) , release_confirm = False , use_accurate = False )
Scales the selected vertices' skin radii.
Parameters:
- value (mathutils.Vector) – Scale, (array of 3 items, in [-inf, inf], optional)
- orient_type ( str ) – Orientation, Transformation orientation (optional)
- orient_matrix (mathutils.Matrix) – Matrix, (multi-dimensional array of 3 * 3 items, in [-inf, inf], optional)
- orient_matrix_type ( str ) – Matrix Orientation, (optional)
- constraint_axis ( Sequence [ bool ] ) – Constraint Axis, (array of 3 items, optional)
- mirror ( bool ) – Mirror Editing, (optional)
- use_proportional_edit ( bool ) – Proportional Editing, (optional)
- proportional_edit_falloff (Literal[Proportional Falloff Items]) – Proportional Falloff, Falloff type for proportional editing mode (optional)
- proportional_size ( float ) – Proportional Size, (in [1e-06, inf], optional)
- use_proportional_connected ( bool ) – Connected, (optional)
- use_proportional_projected ( bool ) – Projected (2D), (optional)
- snap ( bool ) – Use Snapping Options, (optional)
- snap_elements (set[Literal[Snap Element Items]]) – Snap to Elements, (optional)
- use_snap_project ( bool ) – Project Individual Elements, (optional)
- snap_target (Literal[Snap Source Items]) – Snap Base, Point on source that will snap to target (optional)
- use_snap_self ( bool ) – Target: Include Active, (optional)
- use_snap_edit ( bool ) – Target: Include Edit, (optional)
- use_snap_nonedit ( bool ) – Target: Include Non-Edited, (optional)
- use_snap_selectable ( bool ) – Target: Exclude Non-Selectable, (optional)
- snap_point (mathutils.Vector) – Point, (array of 3 items, in [-inf, inf], optional)
- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)
- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.transform. tilt ( * , value = 0.0 , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , snap = False , release_confirm = False , use_accurate = False )
Tilts the selected control vertices of a 3D curve.
Parameters:
- value ( float ) – Angle, (in [-inf, inf], optional)
- mirror ( bool ) – Mirror Editing, (optional)
- use_proportional_edit ( bool ) – Proportional Editing, (optional)
- proportional_edit_falloff (Literal[Proportional Falloff Items]) – Proportional Falloff, Falloff type for proportional editing mode (optional)
- proportional_size ( float ) – Proportional Size, (in [1e-06, inf], optional)
- use_proportional_connected ( bool ) – Connected, (optional)
- use_proportional_projected ( bool ) – Projected (2D), (optional)
- snap ( bool ) – Use Snapping Options, (optional)
- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)
- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.transform. tosphere ( * , value = 0.0 , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , snap = False , gpencil_strokes = False , center_override = (0.0, 0.0, 0.0) , release_confirm = False , use_accurate = False )
Moves the selected items outward into a spherical shape around the geometric center.
Parameters:
- value ( float ) – Factor, (in [0, 1], optional)
- mirror ( bool ) – Mirror Editing, (optional)
- use_proportional_edit ( bool ) – Proportional Editing, (optional)
- proportional_edit_falloff (Literal[Proportional Falloff Items]) – Proportional Falloff, Falloff type for proportional editing mode (optional)
- proportional_size ( float ) – Proportional Size, (in [1e-06, inf], optional)
- use_proportional_connected ( bool ) – Connected, (optional)
- use_proportional_projected ( bool ) – Projected (2D), (optional)
- snap ( bool ) – Use Snapping Options, (optional)
- gpencil_strokes ( bool ) – Edit Grease Pencil, Edit selected Grease Pencil strokes (optional)
- center_override (mathutils.Vector) – Center Override, Force using this center value (when set) (array of 3 items, in [-inf, inf], optional)
- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)
- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.transform. trackball ( * , value = (0.0, 0.0) , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , snap = False , gpencil_strokes = False , center_override = (0.0, 0.0, 0.0) , release_confirm = False , use_accurate = False )
Rotates the selected items in trackball style.
Parameters:
- value ( Sequence [ float ] ) – Angle, (array of 2 items, in [-inf, inf], optional)

bpy.ops.transform. skin_resize ( * , value = (1.0, 1.0, 1.0) , orient_type = 'GLOBAL' , orient_matrix = ((0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0)) , orient_matrix_type = 'GLOBAL' , constraint_axis = (False, False, False) , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , snap = False , snap_elements = {'INCREMENT'} , use_snap_project = False , snap_target = 'CLOSEST' , use_snap_self = True , use_snap_edit = True , use_snap_nonedit = True , use_snap_selectable = False , snap_point = (0.0, 0.0, 0.0) , release_confirm = False , use_accurate = False )

Modify chosen vertices' skin dimensions

Parameters :

- value (mathutils.Vector) – Scale, (array of 3 items, in [-inf, inf], optional)

- orient_type ( str ) – Orientation, Transformation orientation (optional)

- orient_matrix (mathutils.Matrix) – Matrix, (multi-dimensional array of 3 * 3 items, in [-inf, inf], optional)

- orient_matrix_type ( str ) – Matrix Orientation, (optional)

- constraint_axis ( Sequence [ bool ] ) – Constraint Axis, (array of 3 items, optional)

- mirror ( bool ) – Mirror Editing, (optional)

- use_proportional_edit ( bool ) – Proportional Editing, (optional)

- proportional_edit_falloff (Literal[Proportional Falloff Items]) – Proportional Falloff, Falloff type for proportional editing mode (optional)

- proportional_size ( float ) – Proportional Size, (in [1e-06, inf], optional)

- use_proportional_connected ( bool ) – Connected, (optional)

- use_proportional_projected ( bool ) – Projected (2D), (optional)

- snap ( bool ) – Use Snapping Options, (optional)

- snap_elements (set[Literal[Snap Element Items]]) – Snap to Elements, (optional)

- use_snap_project ( bool ) – Project Individual Elements, (optional)

- snap_target (Literal[Snap Source Items]) – Snap Base, Point on source that will snap to target (optional)

- use_snap_self ( bool ) – Target: Include Active, (optional)

- use_snap_edit ( bool ) – Target: Include Edit, (optional)

- use_snap_nonedit ( bool ) – Target: Include Non-Edited, (optional)

- use_snap_selectable ( bool ) – Target: Exclude Non-Selectable, (optional)

- snap_point (mathutils.Vector) – Point, (array of 3 items, in [-inf, inf], optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. tilt ( * , value = 0.0 , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , snap = False , release_confirm = False , use_accurate = False )

Tilt selected control vertices of 3D curve

Parameters :

- value ( float ) – Angle, (in [-inf, inf], optional)

- mirror ( bool ) – Mirror Editing, (optional)

- use_proportional_edit ( bool ) – Proportional Editing, (optional)

- proportional_edit_falloff (Literal[Proportional Falloff Items]) – Proportional Falloff, Falloff type for proportional editing mode (optional)

- proportional_size ( float ) – Proportional Size, (in [1e-06, inf], optional)

- use_proportional_connected ( bool ) – Connected, (optional)

- use_proportional_projected ( bool ) – Projected (2D), (optional)

- snap ( bool ) – Use Snapping Options, (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. tosphere ( * , value = 0.0 , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , snap = False , gpencil_strokes = False , center_override = (0.0, 0.0, 0.0) , release_confirm = False , use_accurate = False )

Push selected items radially around their center

Parameters :

- value ( float ) – Factor, (in [0, 1], optional)

- mirror ( bool ) – Mirror Editing, (optional)

- use_proportional_edit ( bool ) – Proportional Editing, (optional)

- proportional_edit_falloff (Literal[Proportional Falloff Items]) – Proportional Falloff, Falloff type for proportional editing mode (optional)

- proportional_size ( float ) – Proportional Size, (in [1e-06, inf], optional)

- use_proportional_connected ( bool ) – Connected, (optional)

- use_proportional_projected ( bool ) – Projected (2D), (optional)

- snap ( bool ) – Use Snapping Options, (optional)

- gpencil_strokes ( bool ) – Edit Grease Pencil, Edit selected Grease Pencil strokes (optional)

- center_override (mathutils.Vector) – Center Override, Force using this center value (when set) (array of 3 items, in [-inf, inf], optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. trackball ( * , value = (0.0, 0.0) , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , snap = False , gpencil_strokes = False , center_override = (0.0, 0.0, 0.0) , release_confirm = False , use_accurate = False )

Trackball-style rotation of selected items

Parameters :

- value ( Sequence [ float ] ) – Angle, (array of 2 items, in [-inf, inf], optional)

- snap_elements (set[Literal[Snap Element Items]]) – Snap to Elements, (optional)

- use_snap_project ( bool ) – Project Individual Elements, (optional)

- snap_target (Literal[Snap Source Items]) – Snap Base, Point on source that will snap to target (optional)

- use_snap_self ( bool ) – Target: Include Active, (optional)

- use_snap_edit ( bool ) – Target: Include Edit, (optional)

- use_snap_nonedit ( bool ) – Target: Include Non-Edited, (optional)

- use_snap_selectable ( bool ) – Target: Exclude Non-Selectable, (optional)

- snap_point (mathutils.Vector) – Point, (array of 3 items, in [-inf, inf], optional)

- snap_align ( bool ) – Align with Point Normal, (optional)

- snap_normal (mathutils.Vector) – Normal, (array of 3 items, in [-inf, inf], optional)

- gpencil_strokes ( bool ) – Edit Grease Pencil, Edit selected Grease Pencil strokes (optional)

- cursor_transform ( bool ) – Transform Cursor, (optional)

- texture_space ( bool ) – Edit Texture Space, Edit object data texture space (optional)

- remove_on_cancel ( bool ) – Remove on Cancel, Remove elements on cancel (optional)

- use_duplicated_keyframes ( bool ) – Duplicated Keyframes, Transform duplicated keyframes (optional)

- view2d_edge_pan ( bool ) – Edge Pan, Enable edge panning in 2D view (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

- use_automerge_and_split ( bool ) – Auto Merge & Split, Forces the use of Auto Merge and Split (optional)

- translate_origin ( bool ) – Translate Origin, Translate origin instead of selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. vert_crease ( * , value = 0.0 , snap = False , release_confirm = False , use_accurate = False ) 

Adjusts the crease weight on the chosen vertices

Parameters :

- value ( float ) – Factor, (in [-1, 1], optional)

- snap ( bool ) – Use Snapping Options, (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. vert_slide ( * , value = 0.0 , use_even = False , flipped = False , use_clamp = True , direction = (0.0, 0.0, 0.0) , mirror = False , snap = False , snap_elements = {'INCREMENT'} , use_snap_project = False , snap_target = 'CLOSEST' , use_snap_self = True , use_snap_edit = True , use_snap_nonedit = True , use_snap_selectable = False , snap_point = (0.0, 0.0, 0.0) , correct_uv = True , release_confirm = False , use_accurate = False ) 

Glides a vertex along the surrounding mesh

Parameters :

- value ( float ) – Factor, (in [-10, 10], optional)

- use_even ( bool ) – Even, Make the edge loop match the shape of the adjacent edge loop (optional)

- flipped ( bool ) – Flipped, When Even mode is active, flips between the two adjacent edge loops (optional)

- use_clamp ( bool ) – Clamp, Clamp within the edge extents (optional)

- direction (mathutils.Vector) – Slide Direction, World-space direction (array of 3 items, in [-inf, inf], optional)

- mirror ( bool ) – Mirror Editing, (optional)

- snap ( bool ) – Use Snapping Options, (optional)

- snap_elements (set[Literal[Snap Element Items]]) – Snap to Elements, (optional)

- use_snap_project ( bool ) – Project Individual Elements, (optional)

- snap_target (Literal[Snap Source Items]) – Snap Base, Point on source that will snap to target (optional)

- use_snap_self ( bool ) – Target: Include Active, (optional)

- use_snap_edit ( bool ) – Target: Include Edit, (optional)

- use_snap_nonedit ( bool ) – Target: Include Non-Edited, (optional)

- use_snap_selectable ( bool ) – Target: Exclude Non-Selectable, (optional)

- snap_point (mathutils.Vector) – Point, (array of 3 items, in [-inf, inf], optional)

- correct_uv ( bool ) – Correct UVs, Correct UV coordinates when transforming (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. vertex_random ( * , offset = 0.0 , uniform = 0.0 , normal = 0.0 , seed = 0 , wait_for_input = True ) 

Applies a random jitter to the vertices

Parameters :

- offset ( float ) – Amount, Distance to offset (in [-inf, inf], optional)

- uniform ( float ) – Uniform, Increase for uniform offset distance (in [0, 1], optional)

- normal ( float ) – Normal, Align offset direction to normals (in [0, 1], optional)

- seed ( int ) – Random Seed, Seed for the random number generator (in [0, 10000], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. vertex_warp ( * , warp_angle = 6.28319 , offset_angle = 0.0 , min = -1.0 , max = 1.0 , viewmat = ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)) , center = (0.0, 0.0, 0.0) ) 

Bends vertices in an arc centered on the cursor

Parameters :

- warp_angle ( float ) – Warp Angle, Amount to warp about the cursor (in [-inf, inf], optional)

- offset_angle ( float ) – Offset Angle, Angle to use as the basis for warping (in [-inf, inf], optional)

- min ( float ) – Min, (in [-inf, inf], optional)

- max ( float ) – Max, (in [-inf, inf], optional)

- viewmat (mathutils.Matrix) – Matrix, (multi-dimensional array of 4 * 4 items, in [-inf, inf], optional)

- center (mathutils.Vector) – Center, (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
