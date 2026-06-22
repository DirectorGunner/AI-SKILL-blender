# Uv Operators (part 3)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Uv Operators

- nth ( int ) – Selected, Number of selected elements in the repetitive sequence (in [1, inf], optional)

- offset ( int ) – Offset, Offset from the starting point (in [-inf, inf], optional)

- object_index ( int ) – (in [-1, inf], optional)

- index ( int ) – (in [-1, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. shortest_path_select ( * , use_face_step = False , use_topology_distance = False , use_fill = False , skip = 0 , nth = 1 , offset = 0 ) 

Selects the shortest route linking two vertices, edges, or faces

Parameters :

- use_face_step ( bool ) – Face Stepping, Traverse connected faces (includes diagonals and edge-rings) (optional)

- use_topology_distance ( bool ) – Topology Distance, Find the minimum number of steps, ignoring spatial distance (optional)

- use_fill ( bool ) – Fill Region, Select all paths between the source/destination elements (optional)

- skip ( int ) – Deselected, Number of deselected elements in the repetitive sequence (in [0, inf], optional)

- nth ( int ) – Selected, Number of selected elements in the repetitive sequence (in [1, inf], optional)

- offset ( int ) – Offset, Offset from the starting point (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. smart_project ( * , angle_limit = 1.15192 , margin_method = 'SCALED' , rotate_method = '`AXIS_ALIGNED_Y`' , island_margin = 0.0 , area_weight = 0.0 , correct_aspect = True , scale_to_bounds = False ) 

Unwraps the chosen faces of mesh objects by projection

Parameters :

- angle_limit ( float ) – Angle Limit, Lower for more projection groups, higher for less distortion (in [0, 1.5708], optional)

- margin_method ( Literal [ 'SCALED' , 'ADD' , 'FRACTION' ] ) – Margin Method, (optional)

- SCALED
Scaled – Multiply the margin by the existing UV scale.

- ADD
Add – Apply the margin straight, disregarding UV scale.

- FRACTION
Fraction – Give an exact fraction of the final UV output.

- rotate_method ( Literal [ '`AXIS_ALIGNED`' , '`AXIS_ALIGNED_X`' , '`AXIS_ALIGNED_Y`' ] ) – Rotation Method, (optional)

- `AXIS_ALIGNED`
Axis-aligned – Turned to its tightest rectangle, vertical or horizontal.

- `AXIS_ALIGNED_X`
Axis-aligned (Horizontal) – Turn islands so they line up horizontally.

- `AXIS_ALIGNED_Y`
Axis-aligned (Vertical) – Turn islands so they line up vertically.

- island_margin ( float ) – Island Margin, Margin to reduce bleed from adjacent islands (in [0, 1], optional)

- area_weight ( float ) – Area Weight, Weight projection’s vector by faces with larger areas (in [0, 1], optional)

- correct_aspect ( bool ) – Correct Aspect, Map UVs taking aspect ratio of the image associated with the material into account (optional)

- scale_to_bounds ( bool ) – Scale to Bounds, Scale UV coordinates to bounds after unwrapping (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. snap_cursor ( * , target = 'PIXELS' ) 

Moves the cursor onto the chosen target type

Parameters :

target ( Literal [ 'PIXELS' , 'SELECTED' , 'ORIGIN' ] ) – Target, Target to snap the selected UVs to (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. snap_selected ( * , target = 'PIXELS' ) 

Moves the selected UV vertices onto the chosen target type

Parameters :

target ( Literal [ 'PIXELS' , 'CURSOR' , '`CURSOR_OFFSET`' , '`ADJACENT_UNSELECTED`' ] ) – Target, Target to snap the selected UVs to (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. sphere_project ( * , direction = '`VIEW_ON_EQUATOR`' , align = '`POLAR_ZX`' , pole = 'PINCH' , seam = False , correct_aspect = True , clip_to_bounds = False , scale_to_bounds = False ) 

Maps the mesh's UV vertices onto the curved outside of a sphere

Parameters :

- direction ( Literal [ '`VIEW_ON_EQUATOR`' , '`VIEW_ON_POLES`' , '`ALIGN_TO_OBJECT`' ] ) – Direction, Direction of the sphere or cylinder (optional)

- `VIEW_ON_EQUATOR`
View on Equator – The 3D viewpoint sits at the equator.

- `VIEW_ON_POLES`
View on Poles – The 3D viewpoint sits at the poles.

- `ALIGN_TO_OBJECT`
Align to Object – Follow the object's transform for alignment.

- align ( Literal [ '`POLAR_ZX`' , '`POLAR_ZY`' ] ) – Align, How to determine rotation around the pole (optional)

- `POLAR_ZX`
Polar ZX – Take X as polar 0.

- `POLAR_ZY`
Polar ZY – Take Y as polar 0.

- pole ( Literal [ 'PINCH' , 'FAN' ] ) – Pole, How to handle faces at the poles (optional)

- PINCH
Pinch – Squeeze the UVs together at the poles.

- FAN
Fan – Spread the UVs out at the poles.

- seam ( bool ) – Preserve Seams, Separate projections by islands isolated by seams (optional)

- correct_aspect ( bool ) – Correct Aspect, Map UVs taking aspect ratio of the image associated with the material into account (optional)

- clip_to_bounds ( bool ) – Clip to Bounds, Clip UV coordinates to bounds after unwrapping (optional)

- scale_to_bounds ( bool ) – Scale to Bounds, Scale UV coordinates to bounds after unwrapping (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. stitch ( * , use_limit = False , snap_islands = True , limit = 0.01 , static_island = 0 , active_object_index = 0 , midpoint_snap = False , clear_seams = True , mode = 'VERTEX' , stored_mode = 'VERTEX' , selection = None , objects_selection_count = (0, 0, 0, 0, 0, 0) ) 

Joins selected UV vertices that are close together

Parameters :

- use_limit ( bool ) – Use Limit, Stitch UVs within a specified limit distance (optional)

- snap_islands ( bool ) – Snap Islands, Snap islands together (on edge stitch mode, rotates the islands too) (optional)

- limit ( float ) – Limit, Limit distance in normalized coordinates (in [0, inf], optional)

- static_island ( int ) – Static Island, Island that stays in place when stitching islands (in [0, inf], optional)

- active_object_index ( int ) – Active Object, Index of the active object (in [0, inf], optional)

- midpoint_snap ( bool ) – Snap at Midpoint, UVs are stitched at midpoint instead of at static island (optional)

- clear_seams ( bool ) – Clear Seams, Clear seams of stitched edges (optional)

- mode ( Literal [ 'VERTEX' , 'EDGE' ] ) – Operation Mode, Use vertex or edge stitching (optional)

- stored_mode ( Literal [ 'VERTEX' , 'EDGE' ] ) – Stored Operation Mode, Use vertex or edge stitching (optional)

- selection ( bpy_prop_collection [ SelectedUvElement ]) – Selection, (optional)

- objects_selection_count ( Sequence [ int ] ) – Objects Selection Count, (array of 6 items, in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. unwrap ( * , method = 'CONFORMAL' , fill_holes = False , correct_aspect = True , use_subsurf_data = False , margin_method = 'SCALED' , margin = 0.001 , no_flip = False , iterations = 10 , use_weights = False , weight_group = 'uv_importance' , weight_factor = 1.0 ) 

Unwraps the mesh belonging to the object under edit

Parameters :

- method ( Literal [ '`ANGLE_BASED`' , 'CONFORMAL' , '`MINIMUM_STRETCH`' ] ) – Method, Unwrapping method (Angle Based usually gives better results than Conformal, while being somewhat slower) (optional)

- fill_holes ( bool ) – Fill Holes, Virtually fill holes in mesh before unwrapping, to better avoid overlaps and preserve symmetry (optional)

- correct_aspect ( bool ) – Correct Aspect, Map UVs taking aspect ratio of the image associated with the material into account (optional)

- use_subsurf_data ( bool ) – Use Subdivision Surface, Map UVs taking vertex position after Subdivision Surface modifier has been applied (optional)

- margin_method ( Literal [ 'SCALED' , 'ADD' , 'FRACTION' ] ) – Margin Method, (optional)

- SCALED
Scaled – Multiply the margin by the existing UV scale.

- ADD
Add – Apply the margin straight, disregarding UV scale.

- FRACTION
Fraction – Give an exact fraction of the final UV output.

- margin ( float ) – Margin, Space between islands (in [0, 1], optional)

- no_flip ( bool ) – No Flip, Prevent flipping UV’s, flipping may lower distortion depending on the position of pins (optional)

- iterations ( int ) – Iterations, Number of iterations when “Minimum Stretch” method is used (in [0, 10000], optional)

- use_weights ( bool ) – Importance Weights, Whether to take into account per-vertex importance weights (optional)

- weight_group ( str ) – Weight Group, Vertex group name for importance weights (modulating the deform) (optional, never None)

- weight_factor ( float ) – Weight Factor, How much influence the weightmap has for weighted parameterization, 0 being no influence (in [-10000, 10000], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. weld ( ) 

Fuses the selected UV vertices into one

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
