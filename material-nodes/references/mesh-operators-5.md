# Mesh Operators (part 5)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Parameters :

delimit (set[Literal[Mesh Delimit Mode Items]]) – Delimit, Constrain the reachable region (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_linked_pick ( * , deselect = False , delimit = {'SEAM'} , object_index = -1 , index = -1 ) 

Toggle marking on vertices attached to the edge under the cursor

Parameters :

- deselect ( bool ) – Deselect, (optional)

- delimit (set[Literal[Mesh Delimit Mode Items]]) – Delimit, Constrain the reachable region (optional)

- object_index ( int ) – (in [-1, inf], optional)

- index ( int ) – (in [-1, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_loose ( * , extend = False ) 

Highlight unattached topology based on the current pick style

Parameters :

extend ( bool ) – Extend, Grow the current highlighting (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_mirror ( * , axis = {'X'} , extend = False ) 

Mark geometry at reflected places

Parameters :

- axis (set[Literal[Axis Flag Xyz Items]]) – Axis, (optional)

- extend ( bool ) – Extend, Add to what is already marked (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_mode ( * , use_extend = False , use_expand = False , type = 'VERT' , action = 'TOGGLE' ) 

Adjust what kind of parts can be selected

Parameters :

- use_extend ( bool ) – Extend, (optional)

- use_expand ( bool ) – Expand, (optional)

- type (Literal[Mesh Select Mode Items]) – Type, (optional)

- action ( Literal [ 'DISABLE' , 'ENABLE' , 'TOGGLE' ] ) – Action, What to do with the pick style (optional)

- DISABLE
Disable – Turn off the pick style.

- ENABLE
Enable – Turn on the pick style.

- TOGGLE
Toggle – Flip the pick style.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_more ( * , use_face_step = True ) 

Grow the choice to take in adjacent elements

Parameters :

use_face_step ( bool ) – Face Step, Follow face neighbors (rather than edge neighbors) (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_next_item ( ) 

Highlight the subsequent part (in pick history order)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/mesh.py:18

bpy.ops.mesh. select_non_manifold ( * , extend = True , use_wire = True , use_boundary = True , use_multi_face = True , use_non_contiguous = True , use_verts = True ) 

Highlight all broken or fragmented geometry elements

Parameters :

- extend ( bool ) – Extend, Add to what is already marked (optional)

- use_wire ( bool ) – Wire, Unattached spine segments (optional)

- use_boundary ( bool ) – Boundaries, Border spine segments (optional)

- use_multi_face ( bool ) – Multiple Faces, Spines used by more than two surfaces (optional)

- use_non_contiguous ( bool ) – Non Contiguous, Spines between surfaces with misaligned normals (optional)

- use_verts ( bool ) – Vertices, Points that join multiple face islands (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_nth ( * , skip = 1 , nth = 1 , offset = 0 ) 

Alternate marking on elements starting at the focal point

Parameters :

- skip ( int ) – Deselected, How many unmarked parts per cycle (in [1, inf], optional)

- nth ( int ) – Selected, How many marked parts per cycle (in [1, inf], optional)

- offset ( int ) – Offset, Starting point shift (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_prev_item ( ) 

Highlight the prior part (in pick history order)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/mesh.py:43

bpy.ops.mesh. select_random ( * , ratio = 0.5 , seed = 0 , action = 'SELECT' ) 

Arbitrarily mark parts

Parameters :

- ratio ( float ) – Ratio, How much of the total to mark in a haphazard manner (in [0, 1], optional)

- seed ( int ) – Random Seed, Seed to feed the randomizer (in [0, inf], optional)

- action ( Literal [ 'SELECT' , 'DESELECT' ] ) – Action, What to do with each element (optional)

- SELECT
Select – Mark each part.

- DESELECT
Deselect – Remove marks from each part.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_similar ( * , type = '`VERT_NORMAL`' , compare = 'EQUAL' , threshold = 0.0 ) 

Mark vertices, spines or surfaces that resemble one another by attribute

Parameters :

- type ( Literal [ '`VERT_NORMAL`' , '`VERT_FACES`' , '`VERT_GROUPS`' , '`VERT_EDGES`' , '`VERT_CREASE`' , '`EDGE_LENGTH`' , '`EDGE_DIR`' , '`EDGE_FACES`' , '`EDGE_FACE_ANGLE`' , '`EDGE_CREASE`' , '`EDGE_BEVEL`' , '`EDGE_SEAM`' , '`EDGE_SHARP`' , '`EDGE_FREESTYLE`' , '`FACE_MATERIAL`' , '`FACE_AREA`' , '`FACE_SIDES`' , '`FACE_PERIMETER`' , '`FACE_NORMAL`' , '`FACE_COPLANAR`' , '`FACE_SMOOTH`' , '`FACE_FREESTYLE`' ] ) – Type, (optional)

- compare ( Literal [ 'EQUAL' , 'GREATER' , 'LESS' ] ) – Compare, (optional)

- threshold ( float ) – Threshold, (in [0, 100000], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_similar_region ( ) 

Highlight similar face regions matching the current choice

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_ungrouped ( * , extend = False ) 

Mark points that do not belong to a cluster

Parameters :

extend ( bool ) – Extend, Grow the current highlighting (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. separate ( * , type = 'SELECTED' ) 

Extract picked parts into a fresh mesh

Parameters :

type ( Literal [ 'SELECTED' , 'MATERIAL' , 'LOOSE' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. set_normals_from_faces ( * , keep_sharp = False ) 

Make custom directions match the surface facets

Parameters :

keep_sharp ( bool ) – Keep Sharp Edges, Leave corners unmodified on pointed borders (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. set_sharpness_by_angle ( * , angle = 0.523599 , extend = False ) 

Mark spines as hard based on how much the surfaces diverge

Parameters :

- angle ( float ) – Angle, (in [0.000174533, 3.14159], optional)

- extend ( bool ) – Extend, Include additional hard spines without erasing existing marks (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. shape_propagate_to_all ( ) 

Push chosen point placements into every other variation

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. shortest_path_pick ( * , edge_mode = 'SELECT' , use_face_step = False , use_topology_distance = False , use_fill = False , skip = 0 , nth = 1 , offset = 0 , index = -1 ) 

Highlight the quickest chain connecting two marked spots

Parameters :

- edge_mode ( Literal [ 'SELECT' , 'SEAM' , 'SHARP' , 'CREASE' , 'BEVEL' , 'FREESTYLE' ] ) – Edge Tag, The mark to apply when highlighting the quickest chain (optional)

- use_face_step ( bool ) – Face Stepping, Go through attached surfaces (takes diagonals and sequences into account) (optional)

- use_topology_distance ( bool ) – Topology Distance, Get the least steps ignoring how far apart in room they are (optional)

- use_fill ( bool ) – Fill Region, Highlight every chain from start to finish (optional)

- skip ( int ) – Deselected, How many unmarked parts per cycle (in [0, inf], optional)

- nth ( int ) – Selected, How many marked parts per cycle (in [1, inf], optional)

- offset ( int ) – Offset, Starting point shift (in [-inf, inf], optional)

- index ( int ) – (in [-1, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. shortest_path_select ( * , edge_mode = 'SELECT' , use_face_step = False , use_topology_distance = False , use_fill = False , skip = 0 , nth = 1 , offset = 0 ) 

Highlight the quickest chain between chosen spots or regions

Parameters :

- edge_mode ( Literal [ 'SELECT' , 'SEAM' , 'SHARP' , 'CREASE' , 'BEVEL' , 'FREESTYLE' ] ) – Edge Tag, The mark to apply when highlighting the quickest chain (optional)

- use_face_step ( bool ) – Face Stepping, Go through attached surfaces (takes diagonals and sequences into account) (optional)

- use_topology_distance ( bool ) – Topology Distance, Get the least steps ignoring how far apart in room they are (optional)

- use_fill ( bool ) – Fill Region, Highlight every chain from start to finish (optional)

- skip ( int ) – Deselected, How many unmarked parts per cycle (in [0, inf], optional)

- nth ( int ) – Selected, How many marked parts per cycle (in [1, inf], optional)

- offset ( int ) – Offset, Starting point shift (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. smooth_normals ( * , factor = 0.5 ) 

Ease custom directions by blending with neighboring vertex directions

Parameters :

factor ( float ) – Factor, How much to blend (in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. solidify ( * , thickness = 0.01 ) 

Build a skin layer by bulging outward, accounting for acute corners

Parameters :

thickness ( float ) – Thickness, (in [-10000, 10000], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. sort_elements ( * , type = '`VIEW_ZAXIS`' , elements = {'VERT'} , reverse = False , seed = 0 ) 

Rearrange chosen elements, based on a given technique

Parameters :

- type ( Literal [ '`VIEW_ZAXIS`' , '`VIEW_XAXIS`' , '`CURSOR_DISTANCE`' , 'MATERIAL' , 'SELECTED' , 'RANDOMIZE' , 'REVERSE' ] ) – Type, Which sorting to perform (optional)

- `VIEW_ZAXIS`
View Z Axis – Arrange by depth in the viewport, farthest ahead.

- `VIEW_XAXIS`
View X Axis – Arrange horizontally in the viewport.

- `CURSOR_DISTANCE`
Cursor Distance – Arrange by space to the 3D pointer.

- MATERIAL
Material – Arrange face regions by slot index, smallest ahead.

- SELECTED
Selected – Put marked components first, keeping their sequence.
Warning: This affects unmarked parts' positions too.

- RANDOMIZE
Randomize – Rearrange in random sequence.

- REVERSE
Reverse – Flip the current sequence.

- elements ( set [ Literal [ 'VERT' , 'EDGE' , 'FACE' ] ] ) – Elements, What to rearrange (points, edges and/or regions) (optional)

- reverse ( bool ) – Reverse, Reverse the sorting effect (optional)

- seed ( int ) – Seed, Seed for random-based work (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. spin ( * , steps = 12 , dupli = False , angle = 1.5708 , use_auto_merge = True , use_normal_flip = False , center = (0.0, 0.0, 0.0) , axis = (0.0, 0.0, 0.0) ) 

Create copies by rotating chosen points around the viewport origin

Parameters :

- steps ( int ) – Steps, How many divisions (in [0, 1000000], optional)

- dupli ( bool ) – Use Duplicates, (optional)

- angle ( float ) – Angle, How much to turn per step (in [-inf, inf], optional)

- use_auto_merge ( bool ) – Auto Merge, Collapse first/last when the angle equals a full turn (optional)

- use_normal_flip ( bool ) – Flip Normals, (optional)

- center (mathutils.Vector) – Center, Focal point in global coordinate space (array of 3 items, in [-inf, inf], optional)

- axis (mathutils.Vector) – Axis, Rotation axis in global coordinate space (array of 3 items, in [-1, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. split ( ) 

Tear off chosen geometry from the rest of the mesh

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. split_normals ( ) 

Break apart custom directions of picked points

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. subdivide ( * , number_cuts = 1 , smoothness = 0.0 , ngon = True , quadcorner = '`STRAIGHT_CUT`' , fractal = 0.0 , fractal_along_normal = 0.0 , seed = 0 ) 

Slice chosen spines into pieces

Parameters :

- number_cuts ( int ) – Number of Cuts, (in [1, 100], optional)

- smoothness ( float ) – Smoothness, How much to smooth (in [0, 1000], optional)

- ngon ( bool ) – Create N-Gons, When off, fresh faces get 3 or 4 corners only (optional)

- quadcorner ( Literal [ 'INNERVERT' , 'PATH' , '`STRAIGHT_CUT`' , 'FAN' ] ) – Quad Corner Type, How to split rectangular edges (anything but Straight Cut blocks n-gons) (optional)

- fractal ( float ) – Fractal, Randomness scaling (in [0, 1e+06], optional)

- fractal_along_normal ( float ) – Along Normal, Include fractal jitter perpendicular to the surface only (in [0, 1], optional)

- seed ( int ) – Random Seed, Seed to feed the randomizer (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. subdivide_edgering ( * , number_cuts = 10 , interpolation = 'PATH' , smoothness = 1.0 , profile_shape_factor = 0.0 , profile_shape = 'SMOOTH' ) 

Slice edges crossing the chosen sequence

Parameters :

- number_cuts ( int ) – Number of Cuts, (in [0, 1000], optional)

- interpolation ( Literal [ 'LINEAR' , 'PATH' , 'SURFACE' ] ) – Interpolation, Which blend technique (optional)

- smoothness ( float ) – Smoothness, How much to smooth (in [0, 1000], optional)

- profile_shape_factor ( float ) – Profile Factor, How much interim fresh edges get narrowed/widened (in [-1000, 1000], optional)

- profile_shape (Literal[Proportional Falloff Curve Only Items]) – Profile Shape, Outline of the profile (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. symmetrize ( * , direction = '`NEGATIVE_X`' , threshold = 0.0001 ) 

Impose matching form and makeup across an orientation

Parameters :

- direction (Literal[Symmetrize Direction Items]) – Direction, What to replicate from and to (optional)

- threshold ( float ) – Threshold, Range for snapping middle points to the center line (in [0, 10], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. symmetry_snap ( * , direction = '`NEGATIVE_X`' , threshold = 0.05 , factor = 0.5 , use_center = True ) 

Align point groups to their reflected spots

Parameters :

- direction (Literal[Symmetrize Direction Items]) – Direction, What to replicate from and to (optional)

- threshold ( float ) – Threshold, Range for finding matching points (in [0, 10], optional)

- factor ( float ) – Factor, Balance between the placements of the points (in [0, 1], optional)

- use_center ( bool ) – Center, Align middle points to the center line (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. tris_convert_to_quads ( * , face_threshold = 0.698132 , shape_threshold = 0.698132 , topology_influence = 0.0 , uvs = False , vcols = False , seam = False , sharp = False , materials = False , deselect_joined = False ) 

Join three-cornered faces into four-cornered forms where feasible

Parameters :

- face_threshold ( float ) – Max Face Angle, Maximum opening (in [0, 3.14159], optional)

- shape_threshold ( float ) – Max Shape Angle, Maximum shape opening (in [0, 3.14159], optional)

- topology_influence ( float ) – Topology Influence, How much to favor rectangular lattices and touching shapes (in [0, 2], optional)

- uvs ( bool ) – Compare UVs, (optional)

- vcols ( bool ) – Compare Color Attributes, (optional)

- seam ( bool ) – Compare Seam, (optional)

- sharp ( bool ) – Compare Sharp, (optional)

- materials ( bool ) – Compare Materials, (optional)

- deselect_joined ( bool ) – Deselect Joined, Mark only unjoined three-cornered forms that persist (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. unsubdivide ( * , iterations = 2 ) 

Go backwards on chosen spines and surfaces

Parameters :

iterations ( int ) – Iterations, How many steps to revert (in [1, 1000], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. uv_texture_add ( ) 

Generate a texture map

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. uv_texture_remove ( ) 

Erase a texture map

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. uvs_reverse ( ) 

Reverse the direction of texture markers within surfaces

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. uvs_rotate ( * , use_ccw = False ) 

Turn texture markers within surfaces

Parameters :

use_ccw ( bool ) – Counter Clockwise, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. vert_connect ( ) 

Link chosen points of surfaces, breaking apart the region

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. vert_connect_concave ( ) 

Slice inward-bending surfaces by linking to form outward-pointing forms

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. vert_connect_nonplanar ( * , angle_limit = 0.0872665 ) 

Slice tilted surfaces exceeding the angle threshold

Parameters :

angle_limit ( float ) – Max Angle, Angle limit (in [0, 3.14159], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. vert_connect_path ( ) 

Link points by their choice sequence, making new spines, breaking apart surfaces

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. vertices_smooth ( * , factor = 0.0 , repeat = 1 , xaxis = True , yaxis = True , zaxis = True , wait_for_input = True ) 

Round out the corners of chosen points

Parameters :

- factor ( float ) – Smoothing, How much to smooth (in [-10, 10], optional)

- repeat ( int ) – Repeat, How many passes to make (in [1, 1000], optional)

- xaxis ( bool ) – X-Axis, Round along the X axis (optional)

- yaxis ( bool ) – Y-Axis, Round along the Y axis (optional)

- zaxis ( bool ) – Z-Axis, Round along the Z axis (optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. vertices_smooth_laplacian ( * , repeat = 1 , lambda_factor = 1.0 , lambda_border = 5e-05 , use_x = True , use_y = True , use_z = True , preserve_volume = True ) 

Ease picked points by diffusion-based smoothing

Parameters :

- repeat ( int ) – How many times to ease the mesh, (in [1, 1000], optional)

- lambda_factor ( float ) – Spread rate, (in [1e-07, 1000], optional)

- lambda_border ( float ) – Spread rate at edges, (in [1e-07, 1000], optional)

- use_x ( bool ) – Smooth X Axis, Ease the object leftward and rightward (optional)

- use_y ( bool ) – Smooth Y Axis, Ease the object forward and back (optional)

- use_z ( bool ) – Smooth Z Axis, Ease the object upward and downward (optional)

- preserve_volume ( bool ) – Preserve Volume, Keep the amount of stuff constant after easing (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. wireframe ( * , use_boundary = True , use_even_offset = True , use_relative_offset = False , use_replace = True , thickness = 0.01 , offset = 0.01 , use_crease = False , crease_weight = 0.01 ) 

Produce a framework by hollowing out surfaces

Parameters :

- use_boundary ( bool ) – Boundary, Hollow face edges (optional)

- use_even_offset ( bool ) – Offset Even, Balance the offset to give more steady thinness (optional)

- use_relative_offset ( bool ) – Offset Relative, Weigh the offset by nearby topology (optional)

- use_replace ( bool ) – Replace, Strip out the original surfaces (optional)

- thickness ( float ) – Thickness, (in [0, 10000], optional)

- offset ( float ) – Offset, (in [0, 10000], optional)

- use_crease ( bool ) – Crease, Crease hubs to enhance subdivision surface (optional)

- crease_weight ( float ) – Crease Weight, (in [0, 1000], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
