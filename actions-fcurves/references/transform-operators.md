# Transform Operators (part 1)

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

### Transform Operators

bpy.ops.transform. bbone_resize ( * , value = (1.0, 1.0, 1.0) , orient_type = 'GLOBAL' , orient_matrix = ((0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0)) , orient_matrix_type = 'GLOBAL' , constraint_axis = (False, False, False) , mirror = False , release_confirm = False , use_accurate = False )

Modify the visual dimensions of chosen bendy bones

Parameters :

- value (mathutils.Vector) – Display Size, (array of 3 items, in [-inf, inf], optional)

- orient_type ( str ) – Orientation, Transformation orientation (optional)

- orient_matrix (mathutils.Matrix) – Matrix, (multi-dimensional array of 3 * 3 items, in [-inf, inf], optional)

- orient_matrix_type ( str ) – Matrix Orientation, (optional)

- constraint_axis ( Sequence [ bool ] ) – Constraint Axis, (array of 3 items, optional)

- mirror ( bool ) – Mirror Editing, (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. bend ( * , value = (0.0,) , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , snap = False , gpencil_strokes = False , center_override = (0.0, 0.0, 0.0) , release_confirm = False , use_accurate = False )

Curve selected items between the 3D cursor and pointer location

Parameters :

- value ( Sequence [ float ] ) – Angle, (array of 1 items, in [-inf, inf], optional)

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

bpy.ops.transform. create_orientation ( * , name = '' , use_view = False , use = False , overwrite = False )

Generate a transform orientation from current geometry

Parameters :

- name ( str ) – Name, Name of the new custom orientation (optional, never None)

- use_view ( bool ) – Use View, Use the current view instead of the active object to create the new orientation (optional)

- use ( bool ) – Use After Creation, Select orientation after its creation (optional)

- overwrite ( bool ) – Overwrite Previous, Overwrite previously created orientation with same name (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. delete_orientation ( )

Remove a transform orientation

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. edge_bevelweight ( * , value = 0.0 , snap = False , release_confirm = False , use_accurate = False )

Alter bevel weighting of selected edges

Parameters :

- value ( float ) – Factor, (in [-1, 1], optional)

- snap ( bool ) – Use Snapping Options, (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. edge_crease ( * , value = 0.0 , snap = False , release_confirm = False , use_accurate = False )

Alter crease weighting of selected edges

Parameters :

- value ( float ) – Factor, (in [-1, 1], optional)

- snap ( bool ) – Use Snapping Options, (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. edge_slide ( * , value = 0.0 , single_side = False , use_even = False , flipped = False , use_clamp = True , mirror = False , snap = False , snap_elements = {'INCREMENT'} , use_snap_project = False , snap_target = 'CLOSEST' , use_snap_self = True , use_snap_edit = True , use_snap_nonedit = True , use_snap_selectable = False , snap_point = (0.0, 0.0, 0.0) , correct_uv = True , release_confirm = False , use_accurate = False )

Glide an edge loop along a mesh surface

Parameters :

- value ( float ) – Factor, (in [-10, 10], optional)

- single_side ( bool ) – Single Side, (optional)

- use_even ( bool ) – Even, Make the edge loop match the shape of the adjacent edge loop (optional)

- flipped ( bool ) – Flipped, When Even mode is active, flips between the two adjacent edge loops (optional)

- use_clamp ( bool ) – Clamp, Clamp within the edge extents (optional)

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

bpy.ops.transform. from_gizmo ( )

Alter selected items based on the current gizmo mode

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. mirror ( * , orient_type = 'GLOBAL' , orient_matrix = ((0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0)) , orient_matrix_type = 'GLOBAL' , constraint_axis = (False, False, False) , gpencil_strokes = False , center_override = (0.0, 0.0, 0.0) , release_confirm = False , use_accurate = False )

Flip selected items across one or several planes

Parameters :

- orient_type ( str ) – Orientation, Transformation orientation (optional)

- orient_matrix (mathutils.Matrix) – Matrix, (multi-dimensional array of 3 * 3 items, in [-inf, inf], optional)

- orient_matrix_type ( str ) – Matrix Orientation, (optional)

- constraint_axis ( Sequence [ bool ] ) – Constraint Axis, (array of 3 items, optional)

- gpencil_strokes ( bool ) – Edit Grease Pencil, Edit selected Grease Pencil strokes (optional)

- center_override (mathutils.Vector) – Center Override, Force using this center value (when set) (array of 3 items, in [-inf, inf], optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. push_pull ( * , value = 0.0 , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , snap = False , center_override = (0.0, 0.0, 0.0) , release_confirm = False , use_accurate = False )

Move selected items outward or inward

Parameters :

- value ( float ) – Distance, (in [-inf, inf], optional)

- mirror ( bool ) – Mirror Editing, (optional)

- use_proportional_edit ( bool ) – Proportional Editing, (optional)

- proportional_edit_falloff (Literal[Proportional Falloff Items]) – Proportional Falloff, Falloff type for proportional editing mode (optional)

- proportional_size ( float ) – Proportional Size, (in [1e-06, inf], optional)

- use_proportional_connected ( bool ) – Connected, (optional)

- use_proportional_projected ( bool ) – Projected (2D), (optional)

- snap ( bool ) – Use Snapping Options, (optional)

- center_override (mathutils.Vector) – Center Override, Force using this center value (when set) (array of 3 items, in [-inf, inf], optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. resize ( * , value = (1.0, 1.0, 1.0) , mouse_dir_constraint = (0.0, 0.0, 0.0) , orient_type = 'GLOBAL' , orient_matrix = ((0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0)) , orient_matrix_type = 'GLOBAL' , constraint_axis = (False, False, False) , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , snap = False , snap_elements = {'INCREMENT'} , use_snap_project = False , snap_target = 'CLOSEST' , use_snap_self = True , use_snap_edit = True , use_snap_nonedit = True , use_snap_selectable = False , snap_point = (0.0, 0.0, 0.0) , gpencil_strokes = False , texture_space = False , remove_on_cancel = False , use_duplicated_keyframes = False , center_override = (0.0, 0.0, 0.0) , release_confirm = False , use_accurate = False )

Enlarge or shrink selected items

Parameters :

- value (mathutils.Vector) – Scale, (array of 3 items, in [-inf, inf], optional)

- mouse_dir_constraint (mathutils.Vector) – Mouse Directional Constraint, (array of 3 items, in [-inf, inf], optional)

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

- gpencil_strokes ( bool ) – Edit Grease Pencil, Edit selected Grease Pencil strokes (optional)

- texture_space ( bool ) – Edit Texture Space, Edit object data texture space (optional)

- remove_on_cancel ( bool ) – Remove on Cancel, Remove elements on cancel (optional)

- use_duplicated_keyframes ( bool ) – Duplicated Keyframes, Transform duplicated keyframes (optional)

- center_override (mathutils.Vector) – Center Override, Force using this center value (when set) (array of 3 items, in [-inf, inf], optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. rotate ( * , value = 0.0 , orient_axis = 'Z' , orient_type = 'GLOBAL' , orient_matrix = ((0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0)) , orient_matrix_type = 'GLOBAL' , constraint_axis = (False, False, False) , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , snap = False , snap_elements = {'INCREMENT'} , use_snap_project = False , snap_target = 'CLOSEST' , use_snap_self = True , use_snap_edit = True , use_snap_nonedit = True , use_snap_selectable = False , snap_point = (0.0, 0.0, 0.0) , gpencil_strokes = False , center_override = (0.0, 0.0, 0.0) , release_confirm = False , use_accurate = False )

Revolve selected items around an axis

Parameters :

- value ( float ) – Angle, (in [-inf, inf], optional)

- orient_axis (Literal[Axis Xyz Items]) – Axis, (optional)

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

- gpencil_strokes ( bool ) – Edit Grease Pencil, Edit selected Grease Pencil strokes (optional)

- center_override (mathutils.Vector) – Center Override, Force using this center value (when set) (array of 3 items, in [-inf, inf], optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. rotate_normal ( * , value = 0.0 , orient_axis = 'Z' , orient_type = 'GLOBAL' , orient_matrix = ((0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0)) , orient_matrix_type = 'GLOBAL' , constraint_axis = (False, False, False) , mirror = False , release_confirm = False , use_accurate = False )

Revolve custom surface normals of selected items

Parameters :

- value ( float ) – Angle, (in [-inf, inf], optional)

- orient_axis (Literal[Axis Xyz Items]) – Axis, (optional)

- orient_type ( str ) – Orientation, Transformation orientation (optional)

- orient_matrix (mathutils.Matrix) – Matrix, (multi-dimensional array of 3 * 3 items, in [-inf, inf], optional)

- orient_matrix_type ( str ) – Matrix Orientation, (optional)

- constraint_axis ( Sequence [ bool ] ) – Constraint Axis, (array of 3 items, optional)

- mirror ( bool ) – Mirror Editing, (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. select_orientation ( * , orientation = 'GLOBAL' )

Activate a specific transform orientation

Parameters :

orientation ( str ) – Orientation, Transformation orientation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. seq_slide ( * , value = (0.0, 0.0) , use_restore_handle_selection = False , snap = False , texture_space = False , remove_on_cancel = False , use_duplicated_keyframes = False , view2d_edge_pan = False , release_confirm = False , use_accurate = False )

Move a sequence strip in the timeline

Parameters :

- value (mathutils.Vector) – Offset, (array of 2 items, in [-inf, inf], optional)

- use_restore_handle_selection ( bool ) – Restore Handle Selection, Restore handle selection after tweaking (optional)

- snap ( bool ) – Use Snapping Options, (optional)

- texture_space ( bool ) – Edit Texture Space, Edit object data texture space (optional)

- remove_on_cancel ( bool ) – Remove on Cancel, Remove elements on cancel (optional)

- use_duplicated_keyframes ( bool ) – Duplicated Keyframes, Transform duplicated keyframes (optional)

- view2d_edge_pan ( bool ) – Edge Pan, Enable edge panning in 2D view (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. shear ( * , angle = 0.0 , orient_axis = 'Z' , orient_axis_ortho = 'X' , orient_type = 'GLOBAL' , orient_matrix = ((0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0)) , orient_matrix_type = 'GLOBAL' , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , snap = False , gpencil_strokes = False , release_confirm = False , use_accurate = False )

Skew selected items along the specified axis

Parameters :

- angle ( float ) – Angle, (in [-inf, inf], optional)

- orient_axis (Literal[Axis Xyz Items]) – Axis, (optional)

- orient_axis_ortho (Literal[Axis Xyz Items]) – Axis Ortho, (optional)

- orient_type ( str ) – Orientation, Transformation orientation (optional)

- orient_matrix (mathutils.Matrix) – Matrix, (multi-dimensional array of 3 * 3 items, in [-inf, inf], optional)

- orient_matrix_type ( str ) – Matrix Orientation, (optional)

- mirror ( bool ) – Mirror Editing, (optional)

- use_proportional_edit ( bool ) – Proportional Editing, (optional)

- proportional_edit_falloff (Literal[Proportional Falloff Items]) – Proportional Falloff, Falloff type for proportional editing mode (optional)

- proportional_size ( float ) – Proportional Size, (in [1e-06, inf], optional)

- use_proportional_connected ( bool ) – Connected, (optional)

- use_proportional_projected ( bool ) – Projected (2D), (optional)

- snap ( bool ) – Use Snapping Options, (optional)

- gpencil_strokes ( bool ) – Edit Grease Pencil, Edit selected Grease Pencil strokes (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.transform. shrink_fatten ( * , value = 0.0 , use_even_offset = False , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , snap = False , release_confirm = False , use_accurate = False )
