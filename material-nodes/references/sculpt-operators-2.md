# Sculpt Operators (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. paint_mask_slice ( * , mask_threshold = 0.5 , fill_holes = True , new_object = True )

Divide the paint mask from the surface

Parameters :

- mask_threshold ( float ) – Threshold, Lowest mask level needed to classify the point viable for creating a surface from the original (in [0, 1], optional)

- fill_holes ( bool ) – Fill Holes, Seal openings after dividing the mask (optional)

- new_object ( bool ) – Slice to New Object, Form a distinct item from the divided mask (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. project_line_gesture ( * , xstart = 0 , xend = 0 , ystart = 0 , yend = 0 , flip = False , cursor = 5 , use_front_faces_only = False , use_limit_to_segment = False )

Project the surface onto a plane described by a line

Parameters :

- xstart ( int ) – X Start, (in [-inf, inf], optional)

- xend ( int ) – X End, (in [-inf, inf], optional)

- ystart ( int ) – Y Start, (in [-inf, inf], optional)

- yend ( int ) – Y End, (in [-inf, inf], optional)

- flip ( bool ) – Flip, (optional)

- cursor ( int ) – Cursor, Pointer appearance during the interactive operation (in [0, inf], optional)

- use_front_faces_only ( bool ) – Front Faces Only, Influence only surfaces oriented toward the camera (optional)

- use_limit_to_segment ( bool ) – Limit to Segment, Confine the gesture activity to the zone within the segment without extending along the complete line (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. sample_detail_size ( * , location = (0, 0) , mode = 'DYNTOPO' )

Acquire the surface fineness at the target location

Parameters :

- location ( Sequence [ int ] ) – Location, Zone coordinates of sampling (array of 2 items, in [0, 32767], optional)

- mode ( Literal [ 'DYNTOPO' , 'VOXEL' ] ) – Detail Mode, Sculpting workflow context that will apply the sampled measurement (optional)

- DYNTOPO
Dyntopo – Sample dyntopo detail.

- VOXEL
Voxel – Sample mesh voxel size.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. sculptmode_toggle ( )

Switch sculpt mode active in the main viewport

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. set_persistent_base ( )

Reinitialize the reference surface being sculpted upon

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. set_pivot_position ( * , mode = 'UNMASKED' , mouse_x = 0.0 , mouse_y = 0.0 )

Establish where the sculpt deformation pivot is located

Parameters :

- mode ( Literal [ 'ORIGIN' , 'UNMASKED' , 'BORDER' , 'ACTIVE' , 'SURFACE' ] ) – Mode, (optional)

- ORIGIN
Origin – Sets the pivot to the origin of the sculpt.

- UNMASKED
Unmasked – Sets the pivot position to the average position of the unmasked vertices.

- BORDER
Mask Border – Sets the pivot position to the center of the border of the mask.

- ACTIVE
Active Vertex – Sets the pivot position to the active vertex position.

- SURFACE
Surface – Sets the pivot position to the surface under the cursor.

- mouse_x ( float ) – Mouse Position X, Position of the mouse used for "Surface" and "Active Vertex" mode (in [0, inf], optional)

- mouse_y ( float ) – Mouse Position Y, Position of the mouse used for "Surface" and "Active Vertex" mode (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. symmetrize ( * , merge_tolerance = 0.0005 )

Mirror the topology edits to maintain balance

Parameters :

merge_tolerance ( float ) – Merge Distance, Proximity threshold for merging symmetrical points (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. trim_box_gesture ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , use_front_faces_only = False , location = (0, 0) , trim_mode = 'DIFFERENCE' , use_cursor_depth = False , trim_orientation = 'VIEW' , trim_extrude_mode = 'FIXED' , trim_solver = 'MANIFOLD' )

Perform a shape operation on the surface and a rectangular boundary specified by the cursor

Parameters :

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- use_front_faces_only ( bool ) – Front Faces Only, Influence only surfaces oriented toward the camera (optional)

- location ( Sequence [ int ] ) – Location, Cursor position (array of 2 items, in [-inf, inf], optional)

- trim_mode ( Literal [ 'DIFFERENCE' , 'UNION' , 'JOIN' ] ) – Trim Mode, (optional)

- DIFFERENCE
Difference – Use a difference boolean operation.

- UNION
Union – Use a union boolean operation.

- JOIN
Join – Join the new mesh as separate geometry, without performing any boolean operation.

- use_cursor_depth ( bool ) – Use Cursor for Depth, Use cursor position and span for the size and placement of the trimming boundary (optional)

- trim_orientation ( Literal [ 'VIEW' , 'SURFACE' ] ) – Shape Orientation, (optional)

- VIEW
View – Use the view to orientate the trimming shape.

- SURFACE
Surface – Use the surface normal to orientate the trimming shape.

- trim_extrude_mode ( Literal [ 'PROJECT' , 'FIXED' ] ) – Extrude Mode, (optional)

- PROJECT
Project – Align trim geometry with the perspective of the current view for a tapered shape.

- FIXED
Fixed – Align trim geometry orthogonally for a shape with 90 degree angles.

- trim_solver ( Literal [ 'EXACT' , 'FLOAT' , 'MANIFOLD' ] ) – Solver, (optional)

- EXACT
Exact – Slower solver with the best results for coplanar faces.

- FLOAT
Float – Simple solver with good performance, without support for overlapping geometry.

- MANIFOLD
Manifold – Fastest solver that works only on manifold meshes but gives better results.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. trim_lasso_gesture ( * , path = None , use_smooth_stroke = False , smooth_stroke_factor = 0.75 , smooth_stroke_radius = 35 , use_front_faces_only = False , location = (0, 0) , trim_mode = 'DIFFERENCE' , use_cursor_depth = False , trim_orientation = 'VIEW' , trim_extrude_mode = 'FIXED' , trim_solver = 'MANIFOLD' )

Perform a shape operation on the surface and a form specified by the cursor

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- use_smooth_stroke ( bool ) – Stabilize Stroke, Cursor motion lags behind and pursues a softer route (optional)

- smooth_stroke_factor ( float ) – Smooth Stroke Factor, Greater levels yield softer motion (in [0.5, 0.99], optional)

- smooth_stroke_radius ( int ) – Smooth Stroke Radius, Smallest span from prior point prior to resuming motion (in [10, 200], optional)

- use_front_faces_only ( bool ) – Front Faces Only, Influence only surfaces oriented toward the camera (optional)

- location ( Sequence [ int ] ) – Location, Cursor position (array of 2 items, in [-inf, inf], optional)

- trim_mode ( Literal [ 'DIFFERENCE' , 'UNION' , 'JOIN' ] ) – Trim Mode, (optional)

- DIFFERENCE
Difference – Use a difference boolean operation.

- UNION
Union – Use a union boolean operation.

- JOIN
Join – Join the new mesh as separate geometry, without performing any boolean operation.

- use_cursor_depth ( bool ) – Use Cursor for Depth, Use cursor position and span for the size and placement of the trimming boundary (optional)

- trim_orientation ( Literal [ 'VIEW' , 'SURFACE' ] ) – Shape Orientation, (optional)

- VIEW
View – Use the view to orientate the trimming shape.

- SURFACE
Surface – Use the surface normal to orientate the trimming shape.

- trim_extrude_mode ( Literal [ 'PROJECT' , 'FIXED' ] ) – Extrude Mode, (optional)

- PROJECT
Project – Align trim geometry with the perspective of the current view for a tapered shape.

- FIXED
Fixed – Align trim geometry orthogonally for a shape with 90 degree angles.

- trim_solver ( Literal [ 'EXACT' , 'FLOAT' , 'MANIFOLD' ] ) – Solver, (optional)

- EXACT
Exact – Slower solver with the best results for coplanar faces.

- FLOAT
Float – Simple solver with good performance, without support for overlapping geometry.

- MANIFOLD
Manifold – Fastest solver that works only on manifold meshes but gives better results.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. trim_line_gesture ( * , xstart = 0 , xend = 0 , ystart = 0 , yend = 0 , flip = False , cursor = 5 , use_front_faces_only = False , use_limit_to_segment = False , location = (0, 0) , trim_mode = 'DIFFERENCE' , use_cursor_depth = False , trim_orientation = 'VIEW' , trim_extrude_mode = 'FIXED' , trim_solver = 'MANIFOLD' )

Erase a portion of the surface on either edge of a line

Parameters :

- xstart ( int ) – X Start, (in [-inf, inf], optional)

- xend ( int ) – X End, (in [-inf, inf], optional)

- ystart ( int ) – Y Start, (in [-inf, inf], optional)

- yend ( int ) – Y End, (in [-inf, inf], optional)

- flip ( bool ) – Flip, (optional)

- cursor ( int ) – Cursor, Pointer appearance during the interactive operation (in [0, inf], optional)

- use_front_faces_only ( bool ) – Front Faces Only, Influence only surfaces oriented toward the camera (optional)

- use_limit_to_segment ( bool ) – Limit to Segment, Confine the gesture activity to the zone within the segment without extending along the complete line (optional)

- location ( Sequence [ int ] ) – Location, Cursor position (array of 2 items, in [-inf, inf], optional)

- trim_mode ( Literal [ 'DIFFERENCE' , 'UNION' , 'JOIN' ] ) – Trim Mode, (optional)

- DIFFERENCE
Difference – Use a difference boolean operation.

- UNION
Union – Use a union boolean operation.

- JOIN
Join – Join the new mesh as separate geometry, without performing any boolean operation.

- use_cursor_depth ( bool ) – Use Cursor for Depth, Use cursor position and span for the size and placement of the trimming boundary (optional)

- trim_orientation ( Literal [ 'VIEW' , 'SURFACE' ] ) – Shape Orientation, (optional)

- VIEW
View – Use the view to orientate the trimming shape.

- SURFACE
Surface – Use the surface normal to orientate the trimming shape.

- trim_extrude_mode ( Literal [ 'PROJECT' , 'FIXED' ] ) – Extrude Mode, (optional)

- PROJECT
Project – Align trim geometry with the perspective of the current view for a tapered shape.

- FIXED
Fixed – Align trim geometry orthogonally for a shape with 90 degree angles.

- trim_solver ( Literal [ 'EXACT' , 'FLOAT' , 'MANIFOLD' ] ) – Solver, (optional)

- EXACT
Exact – Slower solver with the best results for coplanar faces.

- FLOAT
Float – Simple solver with good performance, without support for overlapping geometry.

- MANIFOLD
Manifold – Fastest solver that works only on manifold meshes but gives better results.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. trim_polyline_gesture ( * , path = None , use_front_faces_only = False , location = (0, 0) , trim_mode = 'DIFFERENCE' , use_cursor_depth = False , trim_orientation = 'VIEW' , trim_extrude_mode = 'FIXED' , trim_solver = 'MANIFOLD' )

Perform a shape operation on the surface and a polygonal form specified by the cursor

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- use_front_faces_only ( bool ) – Front Faces Only, Influence only surfaces oriented toward the camera (optional)

Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.sculpt. paint_mask_slice ( * , mask_threshold = 0.5 , fill_holes = True , new_object = True )
Slices the paint mask out of the mesh.
Parameters:
- mask_threshold ( float ) – Threshold, Minimum mask value to consider the vertex valid to extract a face from the original mesh (in [0, 1], optional)
- fill_holes ( bool ) – Fill Holes, Fill holes after slicing the mask (optional)
- new_object ( bool ) – Slice to New Object, Create a new object from the sliced mask (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.sculpt. project_line_gesture ( * , xstart = 0 , xend = 0 , ystart = 0 , yend = 0 , flip = False , cursor = 5 , use_front_faces_only = False , use_limit_to_segment = False )
Projects the geometry onto a plane defined by a line.
Parameters:
- xstart ( int ) – X Start, (in [-inf, inf], optional)
- xend ( int ) – X End, (in [-inf, inf], optional)
- ystart ( int ) – Y Start, (in [-inf, inf], optional)
- yend ( int ) – Y End, (in [-inf, inf], optional)
- flip ( bool ) – Flip, (optional)
- cursor ( int ) – Cursor, Mouse cursor style to use during the modal operator (in [0, inf], optional)
- use_front_faces_only ( bool ) – Front Faces Only, Affect only faces facing towards the view (optional)
- use_limit_to_segment ( bool ) – Limit to Segment, Apply the gesture action only to the area that is contained within the segment without extending its effect to the entire line (optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.sculpt. sample_detail_size ( * , location = (0, 0) , mode = 'DYNTOPO' )
Samples the mesh detail at the clicked point.
Parameters:
- location ( Sequence [ int ] ) – Location, Screen coordinates of sampling (array of 2 items, in [0, 32767], optional)
- mode ( Literal [ 'DYNTOPO' , 'VOXEL' ] ) – Detail Mode, Target sculpting workflow that is going to use the sampled size (optional)
- DYNTOPO — Dyntopo: sample dyntopo detail.
- VOXEL — Voxel: sample mesh voxel size.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.sculpt. sculptmode_toggle ( )
Toggles sculpt mode in the 3D view.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.sculpt. set_persistent_base ( )
Resets the copy of the mesh being sculpted on.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.sculpt. set_pivot_position ( * , mode = 'UNMASKED' , mouse_x = 0.0 , mouse_y = 0.0 )
Sets the sculpt transform pivot position.
Parameters:
- mode ( Literal [ 'ORIGIN' , 'UNMASKED' , 'BORDER' , 'ACTIVE' , 'SURFACE' ] ) – Mode, (optional)
- ORIGIN — Origin: set the pivot to the sculpt's origin.
- UNMASKED — Unmasked: set the pivot to the average position of the unmasked vertices.
- BORDER — Mask Border: set the pivot to the center of the mask's border.
- ACTIVE — Active Vertex: set the pivot to the active vertex position.
- SURFACE — Surface: set the pivot to the surface under the cursor.
- mouse_x ( float ) – Mouse Position X, Position of the mouse used for "Surface" and "Active Vertex" mode (in [0, inf], optional)
- mouse_y ( float ) – Mouse Position Y, Position of the mouse used for "Surface" and "Active Vertex" mode (in [0, inf], optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.sculpt. symmetrize ( * , merge_tolerance = 0.0005 )
Symmetrizes the topology modifications.
Parameters: merge_tolerance ( float ) – Merge Distance, Distance within which symmetrical vertices are merged (in [0, inf], optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.sculpt. trim_box_gesture ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , use_front_faces_only = False , location = (0, 0) , trim_mode = 'DIFFERENCE' , use_cursor_depth = False , trim_orientation = 'VIEW' , trim_extrude_mode = 'FIXED' , trim_solver = 'MANIFOLD' )
Runs a boolean operation between the mesh and a rectangle defined by the cursor.
Parameters:
- xmin ( int ) – X Min, (in [-inf, inf], optional)
- xmax ( int ) – X Max, (in [-inf, inf], optional)
- ymin ( int ) – Y Min, (in [-inf, inf], optional)
- ymax ( int ) – Y Max, (in [-inf, inf], optional)
- wait_for_input ( bool ) – Wait for Input, (optional)
- use_front_faces_only ( bool ) – Front Faces Only, Affect only faces facing towards the view (optional)
- location ( Sequence [ int ] ) – Location, Mouse location (array of 2 items, in [-inf, inf], optional)
- trim_mode ( Literal [ 'DIFFERENCE' , 'UNION' , 'JOIN' ] ) – Trim Mode, (optional)
- DIFFERENCE — Difference: use a difference boolean operation.
- UNION — Union: use a union boolean operation.
- JOIN — Join: join the new mesh as separate geometry, without performing any boolean operation.
- use_cursor_depth ( bool ) – Use Cursor for Depth, Use cursor location and radius for the dimensions and position of the trimming shape (optional)
- trim_orientation ( Literal [ 'VIEW' , 'SURFACE' ] ) – Shape Orientation, (optional)
- VIEW — View: use the view to orientate the trimming shape.
- SURFACE — Surface: use the surface normal to orientate the trimming shape.
- trim_extrude_mode ( Literal [ 'PROJECT' , 'FIXED' ] ) – Extrude Mode, (optional)
- PROJECT — Project: align trim geometry with the perspective of the current view for a tapered shape.
- FIXED — Fixed: align trim geometry orthogonally for a shape with 90 degree angles.

- trim_solver ( Literal [ 'EXACT' , 'FLOAT' , 'MANIFOLD' ] ) – Solver, (optional)
- EXACT — Exact: slower solver with the best results for coplanar faces.
- FLOAT — Float: simple solver with good performance, without support for overlapping geometry.
- MANIFOLD — Manifold: fastest solver, works only on manifold meshes but gives better results.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.sculpt. trim_lasso_gesture ( * , path = None , use_smooth_stroke = False , smooth_stroke_factor = 0.75 , smooth_stroke_radius = 35 , use_front_faces_only = False , location = (0, 0) , trim_mode = 'DIFFERENCE' , use_cursor_depth = False , trim_orientation = 'VIEW' , trim_extrude_mode = 'FIXED' , trim_solver = 'MANIFOLD' )
Runs a boolean operation between the mesh and a shape defined by the cursor.
Parameters:
- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)
- use_smooth_stroke ( bool ) – Stabilize Stroke, Selection lags behind mouse and follows a smoother path (optional)
- smooth_stroke_factor ( float ) – Smooth Stroke Factor, Higher values give a smoother stroke (in [0.5, 0.99], optional)
- smooth_stroke_radius ( int ) – Smooth Stroke Radius, Minimum distance from last point before selection continues (in [10, 200], optional)
- use_front_faces_only ( bool ) – Front Faces Only, Affect only faces facing towards the view (optional)
- location ( Sequence [ int ] ) – Location, Mouse location (array of 2 items, in [-inf, inf], optional)
- trim_mode ( Literal [ 'DIFFERENCE' , 'UNION' , 'JOIN' ] ) – Trim Mode, (optional)
- DIFFERENCE — Difference: use a difference boolean operation.
- UNION — Union: use a union boolean operation.
- JOIN — Join: join the new mesh as separate geometry, without performing any boolean operation.
- use_cursor_depth ( bool ) – Use Cursor for Depth, Use cursor location and radius for the dimensions and position of the trimming shape (optional)
- trim_orientation ( Literal [ 'VIEW' , 'SURFACE' ] ) – Shape Orientation, (optional)
- VIEW — View: use the view to orientate the trimming shape.
- SURFACE — Surface: use the surface normal to orientate the trimming shape.
- trim_extrude_mode ( Literal [ 'PROJECT' , 'FIXED' ] ) – Extrude Mode, (optional)
- PROJECT — Project: align trim geometry with the perspective of the current view for a tapered shape.
- FIXED — Fixed: align trim geometry orthogonally for a shape with 90 degree angles.
- trim_solver ( Literal [ 'EXACT' , 'FLOAT' , 'MANIFOLD' ] ) – Solver, (optional)
- EXACT — Exact: slower solver with the best results for coplanar faces.
- FLOAT — Float: simple solver with good performance, without support for overlapping geometry.
- MANIFOLD — Manifold: fastest solver, works only on manifold meshes but gives better results.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.sculpt. trim_line_gesture ( * , xstart = 0 , xend = 0 , ystart = 0 , yend = 0 , flip = False , cursor = 5 , use_front_faces_only = False , use_limit_to_segment = False , location = (0, 0) , trim_mode = 'DIFFERENCE' , use_cursor_depth = False , trim_orientation = 'VIEW' , trim_extrude_mode = 'FIXED' , trim_solver = 'MANIFOLD' )
Removes a portion of the mesh on one side of a line.
Parameters:
- xstart ( int ) – X Start, (in [-inf, inf], optional)
- xend ( int ) – X End, (in [-inf, inf], optional)
- ystart ( int ) – Y Start, (in [-inf, inf], optional)
- yend ( int ) – Y End, (in [-inf, inf], optional)
- flip ( bool ) – Flip, (optional)
- cursor ( int ) – Cursor, Mouse cursor style to use during the modal operator (in [0, inf], optional)
- use_front_faces_only ( bool ) – Front Faces Only, Affect only faces facing towards the view (optional)
- use_limit_to_segment ( bool ) – Limit to Segment, Apply the gesture action only to the area that is contained within the segment without extending its effect to the entire line (optional)
- location ( Sequence [ int ] ) – Location, Mouse location (array of 2 items, in [-inf, inf], optional)
- trim_mode ( Literal [ 'DIFFERENCE' , 'UNION' , 'JOIN' ] ) – Trim Mode, (optional)
- DIFFERENCE — Difference: use a difference boolean operation.
- UNION — Union: use a union boolean operation.
- JOIN — Join: join the new mesh as separate geometry, without performing any boolean operation.
- use_cursor_depth ( bool ) – Use Cursor for Depth, Use cursor location and radius for the dimensions and position of the trimming shape (optional)
- trim_orientation ( Literal [ 'VIEW' , 'SURFACE' ] ) – Shape Orientation, (optional)
- VIEW — View: use the view to orientate the trimming shape.
- SURFACE — Surface: use the surface normal to orientate the trimming shape.
- trim_extrude_mode ( Literal [ 'PROJECT' , 'FIXED' ] ) – Extrude Mode, (optional)
- PROJECT — Project: align trim geometry with the perspective of the current view for a tapered shape.
- FIXED — Fixed: align trim geometry orthogonally for a shape with 90 degree angles.
- trim_solver ( Literal [ 'EXACT' , 'FLOAT' , 'MANIFOLD' ] ) – Solver, (optional)
- EXACT — Exact: slower solver with the best results for coplanar faces.
- FLOAT — Float: simple solver with good performance, without support for overlapping geometry.
- MANIFOLD — Manifold: fastest solver, works only on manifold meshes but gives better results.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.sculpt. trim_polyline_gesture ( * , path = None , use_front_faces_only = False , location = (0, 0) , trim_mode = 'DIFFERENCE' , use_cursor_depth = False , trim_orientation = 'VIEW' , trim_extrude_mode = 'FIXED' , trim_solver = 'MANIFOLD' )
Runs a boolean operation between the mesh and a polygonal shape defined by the cursor.
Parameters:
- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)
- use_front_faces_only ( bool ) – Front Faces Only, Affect only faces facing towards the view (optional)
