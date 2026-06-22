# Mesh Operators (part 4)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. primitive_grid_add ( * , x_subdivisions = 10 , y_subdivisions = 10 , size = 2.0 , calc_uvs = True , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Build a segmented flat mesh

Parameters :

- x_subdivisions ( int ) – X Subdivisions, (in [1, 10000000], optional)

- y_subdivisions ( int ) – Y Subdivisions, (in [1, 10000000], optional)

- size ( float ) – Size, (in [0, inf], optional)

- calc_uvs ( bool ) – Generate UVs, Generate a default UV map (optional)

- enter_editmode ( bool ) – Enter Edit Mode, Enter edit mode when adding this object (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. primitive_ico_sphere_add ( * , subdivisions = 2 , radius = 1.0 , calc_uvs = True , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Build a ball-like mesh with uniformly sized triangular faces

Parameters :

- subdivisions ( int ) – Subdivisions, (in [1, 10], optional)

- radius ( float ) – Radius, (in [0, inf], optional)

- calc_uvs ( bool ) – Generate UVs, Generate a default UV map (optional)

- enter_editmode ( bool ) – Enter Edit Mode, Enter edit mode when adding this object (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. primitive_monkey_add ( * , size = 2.0 , calc_uvs = True , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Build a Suzanne mesh

Parameters :

- size ( float ) – Size, (in [0, inf], optional)

- calc_uvs ( bool ) – Generate UVs, Generate a default UV map (optional)

- enter_editmode ( bool ) – Enter Edit Mode, Enter edit mode when adding this object (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. primitive_plane_add ( * , size = 2.0 , calc_uvs = True , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Build a solid flat mesh with 4 points

Parameters :

- size ( float ) – Size, (in [0, inf], optional)

- calc_uvs ( bool ) – Generate UVs, Generate a default UV map (optional)

- enter_editmode ( bool ) – Enter Edit Mode, Enter edit mode when adding this object (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. primitive_torus_add ( * , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , major_segments = 48 , minor_segments = 12 , mode = '`MAJOR_MINOR`' , major_radius = 1.0 , minor_radius = 0.25 , abso_major_rad = 1.25 , abso_minor_rad = 0.75 , generate_uvs = True )

Build a donut-shaped mesh

Parameters :

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, (array of 3 items, in [-inf, inf], optional)

- major_segments ( int ) – Major Segments, Number of segments for the main ring of the torus (in [3, 256], optional)

- minor_segments ( int ) – Minor Segments, Number of segments for the minor ring of the torus (in [3, 256], optional)

- mode ( Literal [ '`MAJOR_MINOR`' , '`EXT_INT`' ] ) – Dimensions Mode, (optional)

- `MAJOR_MINOR`
Major/Minor – Use the major/minor radii for torus dimensions.

- `EXT_INT`
Exterior/Interior – Use the exterior/interior radii for torus dimensions.

- major_radius ( float ) – Major Radius, Radius from the origin to the center of the cross sections (in [0, 10000], optional)

- minor_radius ( float ) – Minor Radius, Radius of the torus's cross section (in [0, 10000], optional)

- abso_major_rad ( float ) – Exterior Radius, Total Exterior Radius of the torus (in [0, 10000], optional)

- abso_minor_rad ( float ) – Interior Radius, Total Interior Radius of the torus (in [0, 10000], optional)

- generate_uvs ( bool ) – Generate UVs, Generate a default UV map (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/add_mesh_torus.py:222

bpy.ops.mesh. primitive_uv_sphere_add ( * , segments = 32 , ring_count = 16 , radius = 1.0 , calc_uvs = True , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Build a ball-like mesh with quad faces, with triangular faces at the pole zones

Parameters :

- segments ( int ) – Segments, (in [3, 100000], optional)

- ring_count ( int ) – Rings, (in [3, 100000], optional)

- radius ( float ) – Radius, (in [0, inf], optional)

- calc_uvs ( bool ) – Generate UVs, Generate a default UV map (optional)

- enter_editmode ( bool ) – Enter Edit Mode, Enter edit mode when adding this object (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. quads_convert_to_tris ( * , quad_method = 'BEAUTY' , ngon_method = 'BEAUTY' )

Render picked polygons as triangles

Parameters :

- quad_method (Literal[Modifier Triangulate Quad Method Items]) – Quad Method, Method for splitting the quads into triangles (optional)

- ngon_method (Literal[Modifier Triangulate Ngon Method Items]) – N-gon Method, Method for splitting the n-gons into triangles (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. region_to_loop ( )

Activate perimeter edges encircling the picked polygons

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. remove_doubles ( * , threshold = 0.0001 , use_centroid = True , use_unselected = False , use_sharp_edge_from_normals = False )

Join points by their closeness

Parameters :

- threshold ( float ) – Merge Distance, Maximum distance between elements to merge (in [1e-06, 50], optional)

- use_centroid ( bool ) – Centroid Merge, Move vertices to the centroid of the duplicate cluster, otherwise the vertex closest to the centroid is used. (optional)

- use_unselected ( bool ) – Unselected, Merge selected to other unselected vertices (optional)

- use_sharp_edge_from_normals ( bool ) – Sharp Edges, Calculate sharp edges using custom normal data (when available) (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. reorder_vertices_spatial ( )

Rearrange mesh faces and points using their placement for speedier BVH generation and sculpt workflows.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. reveal ( * , select = True )

Uncover every concealed point, edge and polygon

Parameters :

select ( bool ) – Select, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. rip ( * , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , release_confirm = False , use_accurate = False , use_fill = False )

Sever points or edges from neighboring geometry

Parameters :

- mirror ( bool ) – Mirror Editing, (optional)

- use_proportional_edit ( bool ) – Proportional Editing, (optional)

- proportional_edit_falloff (Literal[Proportional Falloff Items]) – Proportional Falloff, Falloff type for proportional editing mode (optional)

- proportional_size ( float ) – Proportional Size, (in [1e-06, inf], optional)

- use_proportional_connected ( bool ) – Connected, (optional)

- use_proportional_projected ( bool ) – Projected (2D), (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use precise mesh transformation (optional)

- use_fill ( bool ) – Fill, Fill the separated area (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. rip_edge ( * , location = (0.0, 0.0, 0.0) , direction = (0.0, 0.0, 0.0) ) 

Push out vertices from the nearest edge in the viewing frame

Parameters :

- location (mathutils.Vector) – Location, World-space ray origin for pushing vertices (array of 3 items, in [-inf, inf], optional)

- direction (mathutils.Vector) – Direction, World-space direction for pushing vertices (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. rip_edge_move ( * , `MESH_OT`_rip_edge = {} , `TRANSFORM_OT`_translate = {} ) 

Push vertices from edges and reposition the result

Parameters :

- `MESH_OT`_rip_edge ( dict [ str , Any ] ) – Push Vertices, Push out vertices from the nearest edge in the viewport (optional, bpy.ops.mesh.rip_edge() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Shift, Reposition picked items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. rip_move ( * , `MESH_OT`_rip = {} , `TRANSFORM_OT`_translate = {} ) 

Tear faces apart and shift the outcome

Parameters :

- `MESH_OT`_rip ( dict [ str , Any ] ) – Separate, Isolate vertices or edges from the rest of the mesh (optional, bpy.ops.mesh.rip() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Shift, Reposition picked items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. screw ( * , steps = 9 , turns = 1 , center = (0.0, 0.0, 0.0) , axis = (0.0, 0.0, 0.0) ) 

Generate a spiral by spinning chosen vertices around the viewport origin

Parameters :

- steps ( int ) – Steps, How many divisions (in [1, 100000], optional)

- turns ( int ) – Turns, How many full rotations (in [1, 100000], optional)

- center (mathutils.Vector) – Center, Focal point in global coordinate space (array of 3 items, in [-inf, inf], optional)

- axis (mathutils.Vector) – Axis, Rotation axis in global coordinate space (array of 3 items, in [-1, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_all ( * , action = 'TOGGLE' ) 

Toggle or alter the selection state of mesh elements

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, What to do with each element (optional)

- TOGGLE
Toggle – Flip selection for each part.

- SELECT
Select – Mark each part as picked.

- DESELECT
Deselect – Remove marks from each part.

- INVERT
Invert – Reverse what is and isn't picked.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_axis ( * , orientation = 'LOCAL' , sign = 'POS' , axis = 'X' , threshold = 0.0001 ) 

Pick all mesh data along a single orientation

Parameters :

- orientation (Literal[Transform Orientation Items]) – Axis Mode, Which reference frame to use (optional)

- sign ( Literal [ 'POS' , 'NEG' , 'ALIGN' ] ) – Axis Sign, Which half to pick (optional)

- axis (Literal[Axis Xyz Items]) – Axis, Which dimension to measure against (optional)

- threshold ( float ) – Threshold, (in [1e-06, 50], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_by_attribute ( ) 

Highlight geometry that matches an active property marker

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_by_pole_count ( * , pole_count = 4 , type = 'NOTEQUAL' , extend = False , exclude_nonmanifold = True ) 

Highlight vertices based on how many edges connect to them. In edge and face pick mode the linked forms are highlighted

Parameters :

- pole_count ( int ) – Pole Count, (in [0, inf], optional)

- type ( Literal [ 'LESS' , 'EQUAL' , 'GREATER' , 'NOTEQUAL' ] ) – Type, The kind of comparison to perform (optional)

- extend ( bool ) – Extend, Grow the current highlighting (optional)

- exclude_nonmanifold ( bool ) – Exclude Non Manifold, Leave out poles that are not manifold (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_edge_loop_multi ( * , delimit_edge_loop = {'NGONS', '`OUTER_CORNERS`'} ) 

Mark chains of attached edges from each chosen edge

Parameters :

delimit_edge_loop (set[Literal[Mesh Walk Delimit Edge Loop Items]]) – Delimit, How to constrain the chain selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_edge_ring_multi ( * , delimit_edge_ring = {'NGONS'} ) 

Mark closed sequences of aligned edges from each chosen edge

Parameters :

delimit_edge_ring (set[Literal[Mesh Walk Delimit Edge Ring Items]]) – Edge Ring Delimit, How to constrain the sequence selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_face_by_sides ( * , number = 4 , type = 'EQUAL' , extend = True ) 

Pick vertices or face regions by how many edges frame them

Parameters :

- number ( int ) – Number of Vertices, (in [3, inf], optional)

- type ( Literal [ 'LESS' , 'EQUAL' , 'GREATER' , 'NOTEQUAL' ] ) – Type, The kind of comparison to perform (optional)

- extend ( bool ) – Extend, Grow the current highlighting (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_interior_faces ( ) 

Mark face regions where every edge borders more than two faces

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_less ( * , use_face_step = True ) 

Reduce the selection by removing border items in each region

Parameters :

use_face_step ( bool ) – Face Step, Follow face neighbors (rather than edge neighbors) (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. select_linked ( * , delimit = {'SEAM'} ) 

Mark every vertex attached to the current choice
