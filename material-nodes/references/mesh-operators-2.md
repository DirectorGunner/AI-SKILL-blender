# Mesh Operators (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. edge_face_add ( )

Establish an edge or polygon on the selected

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. edge_rotate ( * , use_ccw = False )

Revolve an edge or neighboring faces

Parameters :

use_ccw ( bool ) – Counter Clockwise, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. edge_split ( * , type = 'EDGE' )

Partition chosen edges such that each neighboring polygon receives its own copy

Parameters :

type ( Literal [ 'EDGE' , 'VERT' ] ) – Type, Method to use for splitting (optional)

- EDGE
Faces by Edges – Split faces along selected edges.

- VERT
Faces & Edges by Vertices – Split faces and edges connected to selected vertices.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. edgering_select ( * , delimit_edge_ring = {'NGONS'} , extend = False , deselect = False , toggle = False , object_index = -1 , edge_index = -1 , vert_index = -1 , face_index = -1 )

Activate an edge ring

Parameters :

- delimit_edge_ring (set[Literal[Mesh Walk Delimit Edge Ring Items]]) – Edge Ring Delimit, Delimit edge ring selection (optional)

- extend ( bool ) – Extend Select, Extend the selection (optional)

- deselect ( bool ) – Deselect, Remove from the selection (optional)

- toggle ( bool ) – Toggle Select, Toggle the selection (optional)

- object_index ( int ) – (in [-1, inf], optional)

- edge_index ( int ) – (in [-1, inf], optional)

- vert_index ( int ) – (in [-1, inf], optional)

- face_index ( int ) – (in [-1, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. edges_select_sharp ( * , sharpness = 0.523599 )

Pick every edge above a sharpness threshold

Parameters :

sharpness ( float ) – Sharpness, (in [0.000174533, 3.14159], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. extrude_context ( * , use_normal_flip = False , use_dissolve_ortho_edges = False , mirror = False )

Protrude the selection

Parameters :

- use_normal_flip ( bool ) – Flip Normals, (optional)

- use_dissolve_ortho_edges ( bool ) – Dissolve Orthogonal Edges, (optional)

- mirror ( bool ) – Mirror Editing, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. extrude_context_move ( * , `MESH_OT`_extrude_context = {} , `TRANSFORM_OT`_translate = {} )

Push a zone outward matching the mean surface direction

Parameters :

- `MESH_OT`_extrude_context ( dict [ str , Any ] ) – Extrude Context, Extrude selection (optional, bpy.ops.mesh.extrude_context() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. extrude_edges_indiv ( * , use_normal_flip = False , mirror = False )

Push single edges outward only

Parameters :

- use_normal_flip ( bool ) – Flip Normals, (optional)

- mirror ( bool ) – Mirror Editing, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. extrude_edges_move ( * , `MESH_OT`_extrude_edges_indiv = {} , `TRANSFORM_OT`_translate = {} )

Protrude edges and move the outcome

Parameters :

- `MESH_OT`_extrude_edges_indiv ( dict [ str , Any ] ) – Extrude Only Edges, Extrude individual edges only (optional, bpy.ops.mesh.extrude_edges_indiv() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. extrude_faces_indiv ( * , mirror = False )

Push individual polygons outward only

Parameters :

mirror ( bool ) – Mirror Editing, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. extrude_faces_move ( * , `MESH_OT`_extrude_faces_indiv = {} , `TRANSFORM_OT`_shrink_fatten = {} )

Protrude every face in turn along its local surface normal

Parameters :

- `MESH_OT`_extrude_faces_indiv ( dict [ str , Any ] ) – Extrude Individual Faces, Extrude individual faces only (optional, bpy.ops.mesh.extrude_faces_indiv() keyword arguments)

- `TRANSFORM_OT`_shrink_fatten ( dict [ str , Any ] ) – Shrink/Fatten, Shrink/fatten selected vertices along normals (optional, bpy.ops.transform.shrink_fatten() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. extrude_manifold ( * , `MESH_OT`_extrude_region = {} , `TRANSFORM_OT`_translate = {} )

Extend and smooth coplanar surface edges to incorporate newly created ones

Parameters :

- `MESH_OT`_extrude_region ( dict [ str , Any ] ) – Extrude Region, Extrude region of faces (optional, bpy.ops.mesh.extrude_region() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. extrude_region ( * , use_normal_flip = False , use_dissolve_ortho_edges = False , mirror = False )

Push a polygonal zone outward

Parameters :

- use_normal_flip ( bool ) – Flip Normals, (optional)

- use_dissolve_ortho_edges ( bool ) – Dissolve Orthogonal Edges, (optional)

- mirror ( bool ) – Mirror Editing, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. extrude_region_move ( * , `MESH_OT`_extrude_region = {} , `TRANSFORM_OT`_translate = {} )

Protrude a polygonal zone and move the result

Parameters :

- `MESH_OT`_extrude_region ( dict [ str , Any ] ) – Extrude Region, Extrude region of faces (optional, bpy.ops.mesh.extrude_region() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. extrude_region_shrink_fatten ( * , `MESH_OT`_extrude_region = {} , `TRANSFORM_OT`_shrink_fatten = {} )

Push a zone outward matching its local surface direction

Parameters :

- `MESH_OT`_extrude_region ( dict [ str , Any ] ) – Extrude Region, Extrude region of faces (optional, bpy.ops.mesh.extrude_region() keyword arguments)

- `TRANSFORM_OT`_shrink_fatten ( dict [ str , Any ] ) – Shrink/Fatten, Shrink/fatten selected vertices along normals (optional, bpy.ops.transform.shrink_fatten() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. extrude_repeat ( * , steps = 10 , offset = (0.0, 0.0, 0.0) , scale_offset = 1.0 )

Protrude picked vertices, edges or faces with repetition

Parameters :

- steps ( int ) – Steps, (in [0, 1000000], optional)

- offset (mathutils.Vector) – Offset, Offset vector (array of 3 items, in [-100000, 100000], optional)

- scale_offset ( float ) – Scale Offset, (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. extrude_vertices_move ( * , `MESH_OT`_extrude_verts_indiv = {} , `TRANSFORM_OT`_translate = {} )

Protrude points and move the result

Parameters :

- `MESH_OT`_extrude_verts_indiv ( dict [ str , Any ] ) – Extrude Only Vertices, Extrude individual vertices only (optional, bpy.ops.mesh.extrude_verts_indiv() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. extrude_verts_indiv ( * , mirror = False )

Push individual points outward only

Parameters :

mirror ( bool ) – Mirror Editing, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. face_make_planar ( * , factor = 1.0 , repeat = 1 )

Straighten picked polygons

Parameters :

- factor ( float ) – Factor, (in [-10, 10], optional)

- repeat ( int ) – Iterations, (in [1, 10000], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. face_split_by_edges ( )

Integrate floating edges into faces (fragmenting them into separate polygons)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. faces_select_linked_flat ( * , sharpness = 0.0174533 )

Activate joined polygons constrained by edge curvature

Parameters :

sharpness ( float ) – Sharpness, (in [0.000174533, 3.14159], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. faces_shade_flat ( )

Render polygons with uniform coloration

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. faces_shade_smooth ( )

Render polygons with gradient coloration (computed from point normals)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. fill ( * , use_beauty = True )

Occupy a picked edge loop with polygons

Parameters :

use_beauty ( bool ) – Beauty, Use best triangulation division (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. fill_grid ( * , span = 1 , offset = 0 , use_interp_simple = False )

Build a grid spanning two loops

Parameters :

- span ( int ) – Span, Number of grid columns (in [1, 1000], optional)

- offset ( int ) – Offset, Vertex that is the corner of the grid (in [-1000, 1000], optional)

- use_interp_simple ( bool ) – Simple Blending, Use simple interpolation of grid vertices (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. fill_holes ( * , sides = 4 )

Plug gaps (perimeter edge loops)

Parameters :

sides ( int ) – Sides, Number of sides in hole required to fill (zero fills all holes) (in [0, 1000], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. flip_normals ( * , only_clnors = False )

Invert the direction of picked polygons' normals (and their vertex attributes)

Parameters :

only_clnors ( bool ) – Custom Normals Only, Only flip the custom loop normals of the selected elements (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. flip_quad_tessellation ( )

Reverse the tessellation orientation of picked quads

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. hide ( * , unselected = False )

Conceal (un)picked vertices, edges or faces

Parameters :

unselected ( bool ) – Unselected, Hide unselected rather than selected (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. inset ( * , use_boundary = True , use_even_offset = True , use_relative_offset = False , use_edge_rail = False , thickness = 0.0 , depth = 0.0 , use_outset = False , use_select_inset = False , use_individual = False , use_interpolate = True , release_confirm = False )

Recede fresh polygons into picked polygons

Parameters :

- use_boundary ( bool ) – Boundary, Inset face boundaries (optional)

- use_even_offset ( bool ) – Offset Even, Scale the offset to give more even thickness (optional)

- use_relative_offset ( bool ) – Offset Relative, Scale the offset by surrounding geometry (optional)

- use_edge_rail ( bool ) – Edge Rail, Inset the region along existing edges (optional)

- thickness ( float ) – Thickness, (in [0, inf], optional)

- depth ( float ) – Depth, (in [-inf, inf], optional)

- use_outset ( bool ) – Outset, Outset rather than inset (optional)

- use_select_inset ( bool ) – Select Outer, Select the new inset faces (optional)

- use_individual ( bool ) – Individual, Individual face inset (optional)

- use_interpolate ( bool ) – Interpolate, Blend face data across the inset (optional)

- release_confirm ( bool ) – Confirm on Release, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. intersect ( * , mode = '`SELECT_UNSELECT`' , separate_mode = 'CUT' , threshold = 1e-06 , solver = 'EXACT' )

Form an intersection cut across polygons

Parameters :

- mode ( Literal [ 'SELECT' , '`SELECT_UNSELECT`' ] ) – Source, (optional)

- SELECT
Self Intersect – Self intersect selected faces.

- `SELECT_UNSELECT`
Selected/Unselected – Intersect selected with unselected faces.

- separate_mode ( Literal [ 'ALL' , 'CUT' , 'NONE' ] ) – Separate Mode, (optional)

- ALL
All – Separate all geometry from intersections.

- CUT
Cut – Cut into geometry keeping each side separate (Selected/Unselected only).

- NONE
Merge – Merge all geometry from the intersection.

- threshold ( float ) – Merge Threshold, (in [0, 0.01], optional)

- solver ( Literal [ 'FLOAT' , 'EXACT' ] ) – Solver, Which Intersect solver to use (optional)

- FLOAT
Float – Simple solver with good performance, without support for overlapping geometry.

- EXACT
Exact – Slower solver with the best results for coplanar faces.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. intersect_boolean ( * , operation = 'DIFFERENCE' , use_swap = False , use_self = False , threshold = 1e-06 , solver = 'EXACT' )

Subtract solid geometry from picked to unpicked

Parameters :

- operation ( Literal [ 'INTERSECT' , 'UNION' , 'DIFFERENCE' ] ) – Boolean Operation, Which boolean operation to apply (optional)

- use_swap ( bool ) – Swap, Use with difference intersection to swap which side is kept (optional)

- use_self ( bool ) – Self Intersection, Do self-union or self-intersection (optional)

- threshold ( float ) – Merge Threshold, (in [0, 0.01], optional)

- solver ( Literal [ 'FLOAT' , 'EXACT' ] ) – Solver, Which Boolean solver to use (optional)

- FLOAT
Float – Faster solver, some limitations.

- EXACT
Exact – Exact solver, slower, handles more cases.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. knife_project ( * , cut_through = False )

Use outlines and perimeters from other bodies to score knife incisions

Parameters :

cut_through ( bool ) – Cut Through, Cut through all faces, not just visible ones (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. knife_tool ( * , use_occlude_geometry = True , only_selected = False , xray = True , visible_measurements = 'NONE' , angle_snapping = 'NONE' , angle_snapping_increment = 0.523599 , wait_for_input = True )

Score contemporary topology

Parameters :

- use_occlude_geometry ( bool ) – Occlude Geometry, Only cut the front most geometry (optional)

- only_selected ( bool ) – Only Selected, Only cut selected geometry (optional)

- xray ( bool ) – X-Ray, Show cuts hidden by geometry (optional)

- visible_measurements ( Literal [ 'NONE' , 'BOTH' , 'DISTANCE' , 'ANGLE' ] ) – Measurements, Visible distance and angle measurements (optional)

- NONE
None – Show no measurements.

- BOTH
Both – Show both distances and angles.

- DISTANCE
Distance – Show just distance measurements.

- ANGLE
Angle – Show just angle measurements.

- angle_snapping ( Literal [ 'NONE' , 'SCREEN' , 'RELATIVE' ] ) – Angle Snapping, Angle snapping mode (optional)

- NONE
None – No angle snapping.

- SCREEN
Screen – Screen space angle snapping.

- RELATIVE
Relative – Angle snapping relative to the previous cut edge.

- angle_snapping_increment ( float ) – Angle Snap Increment, The angle snap increment used when in constrained angle mode (in [0, 3.14159], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. loop_select ( * , delimit_edge_loop = {'NGONS', '`OUTER_CORNERS`'} , delimit_face_loop = set() , extend = False , deselect = False , toggle = False , object_index = -1 , edge_index = -1 , vert_index = -1 , face_index = -1 )

Activate a strand of linked edges

Parameters :

- delimit_edge_loop (set[Literal[Mesh Walk Delimit Edge Loop Items]]) – Delimit, Delimit edge loop selection (optional)

- delimit_face_loop (set[Literal[Mesh Walk Delimit Face Loop Items]]) – Face Loop Delimit, Delimit face loop selection (optional)

- extend ( bool ) – Extend Select, Extend the selection (optional)

- deselect ( bool ) – Deselect, Remove from the selection (optional)

- toggle ( bool ) – Toggle Select, Toggle the selection (optional)

- object_index ( int ) – (in [-1, inf], optional)

- edge_index ( int ) – (in [-1, inf], optional)

- vert_index ( int ) – (in [-1, inf], optional)

- face_index ( int ) – (in [-1, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. loop_to_region ( * , select_bigger = False )

Activate zones of polygons surrounded by a picked edge loop

Parameters :

select_bigger ( bool ) – Select Bigger, Select bigger regions instead of smaller ones (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. loopcut ( * , number_cuts = 1 , smoothness = 0.0 , falloff = '`INVERSE_SQUARE`' , object_index = -1 , edge_index = -1 , mesh_select_mode_init = (False, False, False) )

Introduce a fresh loop between present loops

Parameters :

- number_cuts ( int ) – Number of Cuts, (in [1, 1000000], optional)

- smoothness ( float ) – Smoothness, Smoothness factor (in [-1000, 1000], optional)

- falloff (Literal[Proportional Falloff Curve Only Items]) – Falloff, Falloff type of the feather (optional)

- object_index ( int ) – Object Index, (in [-1, inf], optional)

- edge_index ( int ) – Edge Index, (in [-1, inf], optional)

- mesh_select_mode_init ( Sequence [ bool ] ) – (array of 3 items, optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. loopcut_slide ( * , `MESH_OT`_loopcut = {} , `TRANSFORM_OT`_edge_slide = {} )

Score a mesh loop and move it

Parameters :

- `MESH_OT`_loopcut ( dict [ str , Any ] ) – Loop Cut, Add a new loop between existing loops (optional, bpy.ops.mesh.loopcut() keyword arguments)

- `TRANSFORM_OT`_edge_slide ( dict [ str , Any ] ) – Edge Slide, Slide an edge loop along a mesh (optional, bpy.ops.transform.edge_slide() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. mark_freestyle_edge ( * , clear = False )

(Un)brand picked edges as Freestyle edge highlights

Parameters :

clear ( bool ) – Clear, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. mark_freestyle_face ( * , clear = False )

(Un)mark picked polygons for bypass from Freestyle edge highlight discovery

Parameters :

clear ( bool ) – Clear, (optional)

Returns :

Result of the operator call.

Return type :
