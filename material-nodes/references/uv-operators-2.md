# Uv Operators (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Uv Operators

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. minimize_stretch ( * , fill_holes = True , blend = 0.0 , iterations = 0 ) 

Eases UV stretching by relaxing the angles

Parameters :

- fill_holes ( bool ) – Fill Holes, Virtually fill holes in mesh before unwrapping, to better avoid overlaps and preserve symmetry (optional)

- blend ( float ) – Blend, Blend factor between stretch minimized and original (in [0, 1], optional)

- iterations ( int ) – Iterations, Number of iterations to run, 0 is unlimited when run interactively (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. move_on_axis ( * , type = 'UDIM' , axis = 'X' , distance = 1 ) 

Shifts UVs along one axis

Parameters :

- type ( Literal [ 'DYNAMIC' , 'PIXEL' , 'UDIM' ] ) – Type, Move Type (optional)

- DYNAMIC
Dynamic – Step by the dynamic grid.

- PIXEL
Pixel – Step by a pixel.

- UDIM
UDIM – Step by a UDIM.

- axis ( Literal [ 'X' , 'Y' ] ) – Axis, Axis to move UVs on (optional)

- X
X axis – Shift vertices along the X axis.

- Y
Y axis – Shift vertices along the Y axis.

- distance ( int ) – Distance, Distance to move UVs (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. pack_islands ( * , udim_source = '`CLOSEST_UDIM`' , rotate = True , rotate_method = 'ANY' , scale = True , merge_overlap = False , margin_method = 'SCALED' , margin = 0.001 , pin = False , pin_method = 'LOCKED' , shape_method = 'CONCAVE' ) 

Reshapes every island so the UV/UDIM space is filled as completely as possible

Parameters :

- udim_source ( Literal [ '`CLOSEST_UDIM`' , '`ACTIVE_UDIM`' , '`ORIGINAL_AABB`' , '`CUSTOM_REGION`' ] ) – Pack to, (optional)

- `CLOSEST_UDIM`
Closest UDIM – Send islands to the nearest UDIM.

- `ACTIVE_UDIM`
Active UDIM – Send islands to the active UDIM image tile or to the UDIM grid tile under the 2D cursor.

- `ORIGINAL_AABB`
Original bounding box – Pack within the islands' starting bounding box.

- `CUSTOM_REGION`
Custom Region – Send islands into a custom region.

- rotate ( bool ) – Rotate, Rotate islands to improve layout (optional)

- rotate_method ( Literal [ 'ANY' , 'CARDINAL' , '`AXIS_ALIGNED`' , '`AXIS_ALIGNED_X`' , '`AXIS_ALIGNED_Y`' ] ) – Rotation Method, (optional)

- ANY
Any – Permit rotation at any angle.

- CARDINAL
Cardinal – Permit only 90-degree turns.

- `AXIS_ALIGNED`
Axis-aligned – Turned to its tightest rectangle, vertical or horizontal.

- `AXIS_ALIGNED_X`
Axis-aligned (Horizontal) – Turn islands so they line up horizontally.

- `AXIS_ALIGNED_Y`
Axis-aligned (Vertical) – Turn islands so they line up vertically.

- scale ( bool ) – Scale, Scale islands to fill unit square (optional)

- merge_overlap ( bool ) – Merge Overlapping, Overlapping islands stick together (optional)

- margin_method ( Literal [ 'SCALED' , 'ADD' , 'FRACTION' ] ) – Margin Method, (optional)

- SCALED
Scaled – Multiply the margin by the existing UV scale.

- ADD
Add – Apply the margin straight, disregarding UV scale.

- FRACTION
Fraction – Give an exact fraction of the final UV output.

- margin ( float ) – Margin, Space between islands (in [0, 1], optional)

- pin ( bool ) – Lock Pinned Islands, Constrain islands containing any pinned UV’s (optional)

- pin_method ( Literal [ 'SCALE' , 'ROTATION' , '`ROTATION_SCALE`' , 'LOCKED' ] ) – Pin Method, (optional)

- SCALE
Scale – Keep pinned islands from rescaling.

- ROTATION
Rotation – Keep pinned islands from rotating.

- `ROTATION_SCALE`
Rotation and Scale – Let pinned islands only translate.

- LOCKED
All – Hold pinned islands fixed in place.

- shape_method ( Literal [ 'CONCAVE' , 'CONVEX' , 'AABB' ] ) – Shape Method, (optional)

- CONCAVE
Exact Shape (Concave) – Work from the exact geometry.

- CONVEX
Boundary Shape (Convex) – Work from the convex hull.

- AABB
Bounding Box – Work from bounding boxes.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. paste ( ) 

Pastes the UV vertices that were copied

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. pin ( * , clear = False , invert = False ) 

Anchors or releases selected UV vertices so they hold across repeated unwraps

Parameters :

- clear ( bool ) – Clear, Clear pinning for the selection instead of setting it (optional)

- invert ( bool ) – Invert, Invert pinning for the selection instead of setting it (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. project_from_view ( * , orthographic = False , camera_bounds = True , correct_aspect = True , clip_to_bounds = False , scale_to_bounds = False ) 

Maps the mesh's UV vertices using the current 3D viewpoint

Parameters :

- orthographic ( bool ) – Orthographic, Use orthographic projection (optional)

- camera_bounds ( bool ) – Camera Bounds, Map UVs to the camera region taking resolution and aspect into account (optional)

- correct_aspect ( bool ) – Correct Aspect, Map UVs taking aspect ratio of the image associated with the material into account (optional)

- clip_to_bounds ( bool ) – Clip to Bounds, Clip UV coordinates to bounds after unwrapping (optional)

- scale_to_bounds ( bool ) – Scale to Bounds, Scale UV coordinates to bounds after unwrapping (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. randomize_uv_transform ( * , random_seed = 0 , use_loc = True , loc = (0.0, 0.0) , use_rot = True , rot = 0.0 , use_scale = True , scale_even = False , scale = (1.0, 1.0) ) 

Jitters the UV island's position, rotation, and scale at random

Parameters :

- random_seed ( int ) – Random Seed, Seed value for the random generator (in [0, 10000], optional)

- use_loc ( bool ) – Randomize Location, Randomize the location values (optional)

- loc (mathutils.Vector) – Location, Maximum distance the objects can spread over each axis (array of 2 items, in [-100, 100], optional)

- use_rot ( bool ) – Randomize Rotation, Randomize the rotation value (optional)

- rot ( float ) – Rotation, Maximum rotation (in [-6.28319, 6.28319], optional)

- use_scale ( bool ) – Randomize Scale, Randomize the scale values (optional)

- scale_even ( bool ) – Scale Even, Use the same scale value for both axes (optional)

- scale ( Sequence [ float ] ) – Scale, Maximum scale randomization over each axis (array of 2 items, in [-100, 100], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/uvcalc_transform.py:536

bpy.ops.uv. remove_doubles ( * , threshold = 0.02 , use_unselected = False , use_shared_vertex = False ) 

Merges together selected UV vertices that sit within a set radius of one another

Parameters :

- threshold ( float ) – Merge Distance, Maximum distance between welded vertices (in [0, 10], optional)

- use_unselected ( bool ) – Unselected, Merge selected to other unselected vertices (optional)

- use_shared_vertex ( bool ) – Shared Vertex, Weld UVs based on shared vertices (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. reset ( ) 

Restores the UV projection to its default

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. reveal ( * , select = True ) 

Brings back every UV vertex that was hidden

Parameters :

select ( bool ) – Select, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. rip ( * , mirror = False , release_confirm = False , use_accurate = False , location = (0.0, 0.0) ) 

Tears apart selected vertices or a selected region

Parameters :

- mirror ( bool ) – Mirror Editing, (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

- location (mathutils.Vector) – Location, Mouse location in normalized coordinates, 0.0 to 1.0 is within the image bounds (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. rip_move ( * , `UV_OT`_rip = {} , `TRANSFORM_OT`_translate = {} ) 

Splits the UVs apart and then drags the result

Parameters :

- `UV_OT`_rip ( dict [ str , Any ] ) – UV Rip, Rip selected vertices or a selected region (optional, bpy.ops.uv.rip() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. seams_from_islands ( * , mark_seams = True , mark_sharp = False ) 

Derives mesh seams from how the islands are laid out in the UV editor

Parameters :

- mark_seams ( bool ) – Mark Seams, Mark boundary edges as seams (optional)

- mark_sharp ( bool ) – Mark Sharp, Mark boundary edges as sharp (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select ( * , extend = False , deselect = False , toggle = False , deselect_all = False , select_passthrough = False , location = (0.0, 0.0) ) 

Selects UV vertices

Parameters :

- extend ( bool ) – Extend, Extend selection instead of deselecting everything first (optional)

- deselect ( bool ) – Deselect, Remove from selection (optional)

- toggle ( bool ) – Toggle Selection, Toggle the selection (optional)

- deselect_all ( bool ) – Deselect On Nothing, Deselect all when nothing under the cursor (optional)

- select_passthrough ( bool ) – Only Select Unselected, Ignore the select action when the element is already selected (optional)

- location (mathutils.Vector) – Location, Mouse location in normalized coordinates, 0.0 to 1.0 is within the image bounds (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_all ( * , action = 'TOGGLE' ) 

Alters the selection state of every UV vertex

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Selection action to execute (optional)

- TOGGLE
Toggle – Flip the selection state of every element.

- SELECT
Select – Mark every element as selected.

- DESELECT
Deselect – Clear the selection on every element.

- INVERT
Invert – Swap the selection state across all elements.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_box ( * , pinned = False , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , mode = 'SET' ) 

Selects UV vertices by dragging a box

Parameters :

- pinned ( bool ) – Pinned, Border select pinned UVs only (optional)

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Begin a brand-new selection.

- ADD
Extend – Grow the current selection.

- SUB
Subtract – Shrink the current selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_circle ( * , x = 0 , y = 0 , radius = 25 , wait_for_input = True , mode = 'SET' ) 

Selects UV vertices by dragging a circle

Parameters :

- x ( int ) – X, (in [-inf, inf], optional)

- y ( int ) – Y, (in [-inf, inf], optional)

- radius ( int ) – Radius, (in [1, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Begin a brand-new selection.

- ADD
Extend – Grow the current selection.

- SUB
Subtract – Shrink the current selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_edge_ring ( * , extend = False , location = (0.0, 0.0) ) 

Selects a ring of edges across connected UV vertices

Parameters :

- extend ( bool ) – Extend, Extend selection rather than clearing the existing selection (optional)

- location (mathutils.Vector) – Location, Mouse location in normalized coordinates, 0.0 to 1.0 is within the image bounds (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_lasso ( * , path = None , use_smooth_stroke = False , smooth_stroke_factor = 0.75 , smooth_stroke_radius = 35 , mode = 'SET' ) 

Selects UVs by drawing a freehand lasso

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- use_smooth_stroke ( bool ) – Stabilize Stroke, Selection lags behind mouse and follows a smoother path (optional)

- smooth_stroke_factor ( float ) – Smooth Stroke Factor, Higher values give a smoother stroke (in [0.5, 0.99], optional)

- smooth_stroke_radius ( int ) – Smooth Stroke Radius, Minimum distance from last point before selection continues (in [10, 200], optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Begin a brand-new selection.

- ADD
Extend – Grow the current selection.

- SUB
Subtract – Shrink the current selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_less ( ) 

Drops the UV vertices that sit on the edge of each selected region

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_linked ( ) 

Selects every UV vertex connected within the active UV map

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_linked_pick ( * , extend = False , deselect = False , location = (0.0, 0.0) ) 

Selects all UV vertices connected beneath the pointer

Parameters :

- extend ( bool ) – Extend, Extend selection rather than clearing the existing selection (optional)

- deselect ( bool ) – Deselect, Deselect linked UV vertices rather than selecting them (optional)

- location (mathutils.Vector) – Location, Mouse location in normalized coordinates, 0.0 to 1.0 is within the image bounds (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_loop ( * , extend = False , location = (0.0, 0.0) ) 

Selects a loop running through connected UV vertices

Parameters :

- extend ( bool ) – Extend, Extend selection rather than clearing the existing selection (optional)

- location (mathutils.Vector) – Location, Mouse location in normalized coordinates, 0.0 to 1.0 is within the image bounds (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_mode ( * , type = 'VERTEX' ) 

Switches the UV selection mode

Parameters :

type (Literal[Mesh Select Mode Uv Items]) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_more ( ) 

Grows the selection to UV vertices next to the current one

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_overlap ( * , extend = False ) 

Selects all UV faces that lie on top of one another

Parameters :

extend ( bool ) – Extend, Extend selection rather than clearing the existing selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_pinned ( ) 

Selects every pinned UV vertex

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_similar ( * , type = 'PIN' , compare = 'EQUAL' , threshold = 0.0 ) 

Selects UVs that share a property type

Parameters :

- type ( Literal [ 'PIN' , 'LENGTH' , '`LENGTH_3D`' , 'AREA' , '`AREA_3D`' , 'MATERIAL' , 'OBJECT' , 'SIDES' , 'WINDING' , 'FACE' ] ) – Type, (optional)

- PIN
Pinned.

- LENGTH
Length – Edge length in UV space.

- `LENGTH_3D`
Length 3D – Length of edge in 3D space.

- AREA
Area – Face area in UV space.

- `AREA_3D`
Area 3D – Area of face in 3D space.

- MATERIAL
Material.

- OBJECT
Object.

- SIDES
Polygon Sides.

- WINDING
Winding – Face direction defined by clockwise or anti-clockwise winding (facing up or facing down).

- FACE
Amount of Faces in Island.

- compare ( Literal [ 'EQUAL' , 'GREATER' , 'LESS' ] ) – Compare, (optional)

- threshold ( float ) – Threshold, (in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_split ( ) 

Selects only those faces that are fully selected

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. select_tile ( * , extend = False , tile = (0, 0) ) 

Selects the UVs inside a given tile

Parameters :

- extend ( bool ) – Extend, Extend the selection (optional)

- tile ( Sequence [ int ] ) – Tile, Tile location to select UVs (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. shortest_path_pick ( * , use_face_step = False , use_topology_distance = False , use_fill = False , skip = 0 , nth = 1 , offset = 0 , object_index = -1 , index = -1 ) 

Selects the shortest route linking two selections

Parameters :

- use_face_step ( bool ) – Face Stepping, Traverse connected faces (includes diagonals and edge-rings) (optional)

- use_topology_distance ( bool ) – Topology Distance, Find the minimum number of steps, ignoring spatial distance (optional)

- use_fill ( bool ) – Fill Region, Select all paths between the source/destination elements (optional)

- skip ( int ) – Deselected, Number of deselected elements in the repetitive sequence (in [0, inf], optional)
