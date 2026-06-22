# Mesh Operators (part 3)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

set[Literal[Operator Return Items]]

bpy.ops.mesh. mark_seam ( * , clear = False )

(Un)brand picked edges as a seam

Parameters :

clear ( bool ) – Clear, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. mark_sharp ( * , clear = False , use_verts = False )

(Un)designate picked edges as sharp

Parameters :

- clear ( bool ) – Clear, (optional)

- use_verts ( bool ) – Vertices, Consider vertices instead of edges to select which edges to (un)tag as sharp (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. merge ( * , type = 'CENTER' , uvs = False )

Join picked points

Parameters :

- type ( Literal [ 'CENTER' , 'CURSOR' , 'COLLAPSE' , 'FIRST' , 'LAST' ] ) – Type, Merge method to use (optional)

- uvs ( bool ) – UVs, Move UVs according to merge (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. merge_normals ( )

Join custom normals of picked points

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. mod_weighted_strength ( * , set = False , face_strength = 'MEDIUM' )

Configure/Retrieve force of polygon (exploited in Weighted Normal adjuster)

Parameters :

- set ( bool ) – Set Value, Set value of faces (optional)

- face_strength ( Literal [ 'WEAK' , 'MEDIUM' , 'STRONG' ] ) – Face Strength, Strength to use for assigning or selecting face influence for weighted normal modifier (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. normals_make_consistent ( * , inside = False )

Orient face and vertex normals to point outward or inward through the mesh

Parameters :

inside ( bool ) – Inside, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. normals_tools ( * , mode = 'COPY' , absolute = False )

Manipulate custom normals via Normal Vector from UI

Parameters :

- mode ( Literal [ 'COPY' , 'PASTE' , 'ADD' , 'MULTIPLY' , 'RESET' ] ) – Mode, Mode of tools taking input from interface (optional)

- COPY
Copy Normal – Copy normal to the internal clipboard.

- PASTE
Paste Normal – Paste normal from the internal clipboard.

- ADD
Add Normal – Add normal vector with selection.

- MULTIPLY
Multiply Normal – Multiply normal vector with selection.

- RESET
Reset Normal – Reset the internal clipboard and/or normal of selected element.

- absolute ( bool ) – Absolute Coordinates, Copy Absolute coordinates of Normal vector (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. offset_edge_loops ( * , use_cap_endpoint = False )

Establish offset edge loop originating from the picked selection

Parameters :

use_cap_endpoint ( bool ) – Cap Endpoint, Extend loop around end-points (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. offset_edge_loops_slide ( * , `MESH_OT`_offset_edge_loops = {} , `TRANSFORM_OT`_edge_slide = {} )

Displace offset edge loop

Parameters :

- `MESH_OT`_offset_edge_loops ( dict [ str , Any ] ) – Offset Edge Loop, Create offset edge loop from the current selection (optional, bpy.ops.mesh.offset_edge_loops() keyword arguments)

- `TRANSFORM_OT`_edge_slide ( dict [ str , Any ] ) – Edge Slide, Slide an edge loop along a mesh (optional, bpy.ops.transform.edge_slide() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. point_normals ( * , mode = 'COORDINATES' , invert = False , align = False , target_location = (0.0, 0.0, 0.0) , spherize = False , spherize_strength = 0.1 )

Orient picked custom normals toward a definite Focal Point

Parameters :

- mode ( Literal [ 'COORDINATES' , 'MOUSE' ] ) – Mode, How to define coordinates to point custom normals to (optional)

- COORDINATES
Coordinates – Use static coordinates (defined by various means).

- MOUSE
Mouse – Follow mouse cursor.

- invert ( bool ) – Invert, Invert affected normals (optional)

- align ( bool ) – Align, Make all affected normals parallel (optional)

- target_location (mathutils.Vector) – Target, Target location to which normals will point (array of 3 items, in [-inf, inf], optional)

- spherize ( bool ) – Spherize, Interpolate between original and new normals (optional)

- spherize_strength ( float ) – Spherize Strength, Ratio of spherized normal to original normal (in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. poke ( * , offset = 0.0 , use_relative_offset = False , center_mode = '`MEDIAN_WEIGHTED`' )

Subdivide a polygon into a radial fan

Parameters :

- offset ( float ) – Poke Offset, Poke Offset (in [-1000, 1000], optional)

- use_relative_offset ( bool ) – Offset Relative, Scale the offset by surrounding geometry (optional)

- center_mode ( Literal [ '`MEDIAN_WEIGHTED`' , 'MEDIAN' , 'BOUNDS' ] ) – Poke Center, Poke face center calculation (optional)

- `MEDIAN_WEIGHTED`
Weighted Median – Weighted median face center.

- MEDIAN
Median – Median face center.

- BOUNDS
Bounds – Face bounds center.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. polybuild_delete_at_cursor ( * , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , release_confirm = False , use_accurate = False )

Undocumented, consider contributing.

Parameters :

- mirror ( bool ) – Mirror Editing, (optional)

- use_proportional_edit ( bool ) – Proportional Editing, (optional)

- proportional_edit_falloff (Literal[Proportional Falloff Items]) – Proportional Falloff, Falloff type for proportional editing mode (optional)

- proportional_size ( float ) – Proportional Size, (in [1e-06, inf], optional)

- use_proportional_connected ( bool ) – Connected, (optional)

- use_proportional_projected ( bool ) – Projected (2D), (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. polybuild_dissolve_at_cursor ( )

Undocumented, consider contributing.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. polybuild_extrude_at_cursor_move ( * , `MESH_OT`_polybuild_transform_at_cursor = {} , `MESH_OT`_extrude_edges_indiv = {} , `TRANSFORM_OT`_translate = {} )

Undocumented, consider contributing.

Parameters :

- `MESH_OT`_polybuild_transform_at_cursor ( dict [ str , Any ] ) – Poly Build Transform at Cursor, (optional, bpy.ops.mesh.polybuild_transform_at_cursor() keyword arguments)

- `MESH_OT`_extrude_edges_indiv ( dict [ str , Any ] ) – Extrude Only Edges, Extrude individual edges only (optional, bpy.ops.mesh.extrude_edges_indiv() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. polybuild_face_at_cursor ( * , create_quads = True , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , release_confirm = False , use_accurate = False )

Undocumented, consider contributing.

Parameters :

- create_quads ( bool ) – Create Quads, Automatically split edges in triangles to maintain quad topology (optional)

- mirror ( bool ) – Mirror Editing, (optional)

- use_proportional_edit ( bool ) – Proportional Editing, (optional)

- proportional_edit_falloff (Literal[Proportional Falloff Items]) – Proportional Falloff, Falloff type for proportional editing mode (optional)

- proportional_size ( float ) – Proportional Size, (in [1e-06, inf], optional)

- use_proportional_connected ( bool ) – Connected, (optional)

- use_proportional_projected ( bool ) – Projected (2D), (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. polybuild_face_at_cursor_move ( * , `MESH_OT`_polybuild_face_at_cursor = {} , `TRANSFORM_OT`_translate = {} )

Undocumented, consider contributing.

Parameters :

- `MESH_OT`_polybuild_face_at_cursor ( dict [ str , Any ] ) – Poly Build Face at Cursor, (optional, bpy.ops.mesh.polybuild_face_at_cursor() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. polybuild_split_at_cursor ( * , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , release_confirm = False , use_accurate = False )

Undocumented, consider contributing.

Parameters :

- mirror ( bool ) – Mirror Editing, (optional)

- use_proportional_edit ( bool ) – Proportional Editing, (optional)

- proportional_edit_falloff (Literal[Proportional Falloff Items]) – Proportional Falloff, Falloff type for proportional editing mode (optional)

- proportional_size ( float ) – Proportional Size, (in [1e-06, inf], optional)

- use_proportional_connected ( bool ) – Connected, (optional)

- use_proportional_projected ( bool ) – Projected (2D), (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. polybuild_split_at_cursor_move ( * , `MESH_OT`_polybuild_split_at_cursor = {} , `TRANSFORM_OT`_translate = {} )

Undocumented, consider contributing.

Parameters :

- `MESH_OT`_polybuild_split_at_cursor ( dict [ str , Any ] ) – Poly Build Split at Cursor, (optional, bpy.ops.mesh.polybuild_split_at_cursor() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. polybuild_transform_at_cursor ( * , mirror = False , use_proportional_edit = False , proportional_edit_falloff = 'SMOOTH' , proportional_size = 1.0 , use_proportional_connected = False , use_proportional_projected = False , release_confirm = False , use_accurate = False )

Undocumented, consider contributing.

Parameters :

- mirror ( bool ) – Mirror Editing, (optional)

- use_proportional_edit ( bool ) – Proportional Editing, (optional)

- proportional_edit_falloff (Literal[Proportional Falloff Items]) – Proportional Falloff, Falloff type for proportional editing mode (optional)

- proportional_size ( float ) – Proportional Size, (in [1e-06, inf], optional)

- use_proportional_connected ( bool ) – Connected, (optional)

- use_proportional_projected ( bool ) – Projected (2D), (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

- use_accurate ( bool ) – Accurate, Use accurate transformation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. polybuild_transform_at_cursor_move ( * , `MESH_OT`_polybuild_transform_at_cursor = {} , `TRANSFORM_OT`_translate = {} )

Undocumented, consider contributing.

Parameters :

- `MESH_OT`_polybuild_transform_at_cursor ( dict [ str , Any ] ) – Poly Build Transform at Cursor, (optional, bpy.ops.mesh.polybuild_transform_at_cursor() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. primitive_circle_add ( * , vertices = 32 , radius = 1.0 , fill_type = 'NOTHING' , calc_uvs = True , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Build a circular mesh

Parameters :

- vertices ( int ) – Vertices, (in [3, 10000000], optional)

- radius ( float ) – Radius, (in [0, inf], optional)

- fill_type ( Literal [ 'NOTHING' , 'NGON' , 'TRIFAN' ] ) – Fill Type, (optional)

- NOTHING
Nothing – Don't fill at all.

- NGON
N-Gon – Use n-gons.

- TRIFAN
Triangle Fan – Use triangle fans.

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

bpy.ops.mesh. primitive_cone_add ( * , vertices = 32 , radius1 = 1.0 , radius2 = 0.0 , depth = 2.0 , end_fill_type = 'NGON' , calc_uvs = True , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Build a tapered mesh

Parameters :

- vertices ( int ) – Vertices, (in [3, 10000000], optional)

- radius1 ( float ) – Radius 1, (in [0, inf], optional)

- radius2 ( float ) – Radius 2, (in [0, inf], optional)

- depth ( float ) – Depth, (in [0, inf], optional)

- end_fill_type ( Literal [ 'NOTHING' , 'NGON' , 'TRIFAN' ] ) – Base Fill Type, (optional)

- NOTHING
Nothing – Don't fill at all.

- NGON
N-Gon – Use n-gons.

- TRIFAN
Triangle Fan – Use triangle fans.

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

bpy.ops.mesh. primitive_cube_add ( * , size = 2.0 , calc_uvs = True , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Build a hexahedron mesh with six rectangular surfaces

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

bpy.ops.mesh. primitive_cube_add_gizmo ( * , calc_uvs = True , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) , matrix = ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)) )

Build a hexahedron mesh

Parameters :

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

- matrix (mathutils.Matrix) – Matrix, (multi-dimensional array of 4 * 4 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. primitive_cylinder_add ( * , vertices = 32 , radius = 1.0 , depth = 2.0 , end_fill_type = 'NGON' , calc_uvs = True , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Build a tubular mesh

Parameters :

- vertices ( int ) – Vertices, (in [3, 10000000], optional)

- radius ( float ) – Radius, (in [0, inf], optional)

- depth ( float ) – Depth, (in [0, inf], optional)

- end_fill_type ( Literal [ 'NOTHING' , 'NGON' , 'TRIFAN' ] ) – Cap Fill Type, (optional)

- NOTHING
Nothing – Don't fill at all.

- NGON
N-Gon – Use n-gons.

- TRIFAN
Triangle Fan – Use triangle fans.

- calc_uvs ( bool ) – Generate UVs, Generate a default UV map (optional)

- enter_editmode ( bool ) – Enter Edit Mode, Enter edit mode when adding this object (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.
