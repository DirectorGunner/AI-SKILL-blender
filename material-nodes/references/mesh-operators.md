# Mesh Operators (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Mesh Operators

bpy.ops.mesh. attribute_set ( * , value_float = 0.0 , value_float_vector_2d = (0.0, 0.0) , value_float_vector_3d = (0.0, 0.0, 0.0) , value_int = 0 , value_int_vector_2d = (0, 0) , value_color = (1.0, 1.0, 1.0, 1.0) , value_bool = False )

Modifies the active attribute across chosen elements

Parameters :

- value_float ( float ) – Value, (in [-inf, inf], optional)

- value_float_vector_2d ( Sequence [ float ] ) – Value, (array of 2 items, in [-inf, inf], optional)

- value_float_vector_3d ( Sequence [ float ] ) – Value, (array of 3 items, in [-inf, inf], optional)

- value_int ( int ) – Value, (in [-inf, inf], optional)

- value_int_vector_2d ( Sequence [ int ] ) – Value, (array of 2 items, in [-inf, inf], optional)

- value_color ( Sequence [ float ] ) – Value, (array of 4 items, in [-inf, inf], optional)

- value_bool ( bool ) – Value, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. average_normals ( * , average_type = '`CUSTOM_NORMAL`' , weight = 50 , threshold = 0.01 )

Smooth custom normals on picked vertices via the chosen method

Parameters :

- average_type ( Literal [ '`CUSTOM_NORMAL`' , '`FACE_AREA`' , '`CORNER_ANGLE`' ] ) – Type, Averaging method (optional)

- `CUSTOM_NORMAL`
Custom Normal – Take average of vertex normals.

- `FACE_AREA`
Face Area – Set all vertex normals by face area.

- `CORNER_ANGLE`
Corner Angle – Set all vertex normals by corner angle.

- weight ( int ) – Weight, Weight applied per face (in [1, 100], optional)

- threshold ( float ) – Threshold, Threshold value for different weights to be considered equal (in [0, 10], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. beautify_fill ( * , angle_limit = 3.14159 )

Modify face topology to reduce degeneracy in the mesh

Parameters :

angle_limit ( float ) – Max Angle, Angle limit (in [0, 3.14159], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. bevel ( * , offset_type = 'OFFSET' , offset = 0.0 , profile_type = 'SUPERELLIPSE' , offset_pct = 0.0 , segments = 1 , profile = 0.5 , affect = 'EDGES' , clamp_overlap = False , loop_slide = True , mark_seam = False , mark_sharp = False , material = -1 , harden_normals = False , face_strength_mode = 'NONE' , miter_outer = 'SHARP' , miter_inner = 'SHARP' , spread = 0.1 , vmesh_method = 'ADJ' , release_confirm = False )

Slant edges and vertices to generate bevels and chamfers

Parameters :

- offset_type ( Literal [ 'OFFSET' , 'WIDTH' , 'DEPTH' , 'PERCENT' , 'ABSOLUTE' ] ) – Width Type, The method for determining the size of the bevel (optional)

- OFFSET
Offset – Amount is offset of new edges from original.

- WIDTH
Width – Amount is width of new face.

- DEPTH
Depth – Amount is perpendicular distance from original edge to bevel face.

- PERCENT
Percent – Amount is percent of adjacent edge length.

- ABSOLUTE
Absolute – Amount is absolute distance along adjacent edge.

- offset ( float ) – Width, Bevel amount (in [0, 1e+06], optional)

- profile_type ( Literal [ 'SUPERELLIPSE' , 'CUSTOM' ] ) – Profile Type, The type of shape used to rebuild a beveled section (optional)

- SUPERELLIPSE
Superellipse – The profile can be a concave or convex curve.

- CUSTOM
Custom – The profile can be any arbitrary path between its endpoints.

- offset_pct ( float ) – Width Percent, Bevel amount for percentage method (in [0, 100], optional)

- segments ( int ) – Segments, Segments for curved edge (in [1, 1000], optional)

- profile ( float ) – Profile, Controls profile shape (0.5 = round) (in [0, 1], optional)

- affect ( Literal [ 'VERTICES' , 'EDGES' ] ) – Affect, Affect edges or vertices (optional)

- VERTICES
Vertices – Affect only vertices.

- EDGES
Edges – Affect only edges.

- clamp_overlap ( bool ) – Clamp Overlap, Do not allow beveled edges/vertices to overlap each other (optional)

- loop_slide ( bool ) – Loop Slide, Prefer sliding along edges to even widths (optional)

- mark_seam ( bool ) – Mark Seams, Preserve seams along beveled edges (optional)

- mark_sharp ( bool ) – Mark Sharp, Preserve sharp edges along beveled edges (optional)

- material ( int ) – Material Index, Material for bevel faces (-1 means use adjacent faces) (in [-1, inf], optional)

- harden_normals ( bool ) – Harden Normals, Match normals of new faces to adjacent faces (optional)

- face_strength_mode ( Literal [ 'NONE' , 'NEW' , 'AFFECTED' , 'ALL' ] ) – Face Strength Mode, Whether to set face strength, and which faces to set face strength on (optional)

- NONE
None – Do not set face strength.

- NEW
New – Set face strength on new faces only.

- AFFECTED
Affected – Set face strength on new and modified faces only.

- ALL
All – Set face strength on all faces.

- miter_outer ( Literal [ 'SHARP' , 'PATCH' , 'ARC' ] ) – Outer Miter, Pattern to use for outside of miters (optional)

- SHARP
Sharp – Outside of miter is sharp.

- PATCH
Patch – Outside of miter is squared-off patch.

- ARC
Arc – Outside of miter is arc.

- miter_inner ( Literal [ 'SHARP' , 'ARC' ] ) – Inner Miter, Pattern to use for inside of miters (optional)

- SHARP
Sharp – Inside of miter is sharp.

- ARC
Arc – Inside of miter is arc.

- spread ( float ) – Spread, Amount to spread arcs for arc inner miters (in [0, 1e+06], optional)

- vmesh_method ( Literal [ 'ADJ' , 'CUTOFF' ] ) – Vertex Mesh Method, The method to use to create meshes at intersections (optional)

- ADJ
Grid Fill – Default patterned fill.

- CUTOFF
Cutoff – A cutoff at each profile's end before the intersection.

- release_confirm ( bool ) – Confirm on Release, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. bisect ( * , plane_co = (0.0, 0.0, 0.0) , plane_no = (0.0, 0.0, 0.0) , use_fill = False , clear_inner = False , clear_outer = False , threshold = 0.0001 , xstart = 0 , xend = 0 , ystart = 0 , yend = 0 , flip = False , cursor = 5 )

Slice the mesh with a plane (drag to orient it)

Parameters :

- plane_co (mathutils.Vector) – Plane Point, A point on the plane (array of 3 items, in [-inf, inf], optional)

- plane_no (mathutils.Vector) – Plane Normal, The direction the plane points (array of 3 items, in [-1, 1], optional)

- use_fill ( bool ) – Fill, Fill in the cut (optional)

- clear_inner ( bool ) – Clear Inner, Remove geometry behind the plane (optional)

- clear_outer ( bool ) – Clear Outer, Remove geometry in front of the plane (optional)

- threshold ( float ) – Axis Threshold, Preserves the existing geometry along the cut plane (in [0, 10], optional)

- xstart ( int ) – X Start, (in [-inf, inf], optional)

- xend ( int ) – X End, (in [-inf, inf], optional)

- ystart ( int ) – Y Start, (in [-inf, inf], optional)

- yend ( int ) – Y End, (in [-inf, inf], optional)

- flip ( bool ) – Flip, (optional)

- cursor ( int ) – Cursor, Mouse cursor style to use during the modal operator (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. blend_from_shape ( * , shape = '' , blend = 1.0 , add = True )

Combine vertices into a shape key

Parameters :

- shape ( str ) – Shape, Shape key to use for blending (optional)

- blend ( float ) – Blend, Blending factor (in [-1000, 1000], optional)

- add ( bool ) – Add, Add rather than blend between shapes (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. bridge_edge_loops ( * , type = 'SINGLE' , use_merge = False , merge_factor = 0.5 , twist_offset = 0 , number_cuts = 0 , interpolation = 'PATH' , smoothness = 1.0 , profile_shape_factor = 0.0 , profile_shape = 'SMOOTH' )

Span faces over two or more picked edge loops

Parameters :

- type ( Literal [ 'SINGLE' , 'CLOSED' , 'PAIRS' ] ) – Connect Loops, Method of bridging multiple loops (optional)

- use_merge ( bool ) – Merge, Merge rather than creating faces (optional)

- merge_factor ( float ) – Merge Factor, (in [0, 1], optional)

- twist_offset ( int ) – Twist, Twist offset for closed loops (in [-1000, 1000], optional)

- number_cuts ( int ) – Number of Cuts, (in [0, 1000], optional)

- interpolation ( Literal [ 'LINEAR' , 'PATH' , 'SURFACE' ] ) – Interpolation, Interpolation method (optional)

- smoothness ( float ) – Smoothness, Smoothness factor (in [0, 1000], optional)

- profile_shape_factor ( float ) – Profile Factor, How much intermediary new edges are shrunk/expanded (in [-1000, 1000], optional)

- profile_shape (Literal[Proportional Falloff Curve Only Items]) – Profile Shape, Shape of the profile (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. colors_reverse ( )

Invert direction of corner colors within face polygons

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. colors_rotate ( * , use_ccw = False )

Cycle the order of corner colors in face polygons

Parameters :

use_ccw ( bool ) – Counter Clockwise, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. convex_hull ( * , delete_unused = True , use_existing_faces = True , make_holes = False , join_triangles = True , face_threshold = 0.698132 , shape_threshold = 0.698132 , topology_influence = 0.0 , uvs = False , vcols = False , seam = False , sharp = False , materials = False , deselect_joined = False )

Wrap picked vertices in a convex shell

Parameters :

- delete_unused ( bool ) – Delete Unused, Delete selected elements that are not used by the hull (optional)

- use_existing_faces ( bool ) – Use Existing Faces, Skip hull triangles that are covered by a pre-existing face (optional)

- make_holes ( bool ) – Make Holes, Delete selected faces that are used by the hull (optional)

- join_triangles ( bool ) – Join Triangles, Merge adjacent triangles into quads (optional)

- face_threshold ( float ) – Max Face Angle, Face angle limit (in [0, 3.14159], optional)

- shape_threshold ( float ) – Max Shape Angle, Shape angle limit (in [0, 3.14159], optional)

- topology_influence ( float ) – Topology Influence, How much to prioritize regular grids of quads as well as quads that touch existing quads (in [0, 2], optional)

- uvs ( bool ) – Compare UVs, (optional)

- vcols ( bool ) – Compare Color Attributes, (optional)

- seam ( bool ) – Compare Seam, (optional)

- sharp ( bool ) – Compare Sharp, (optional)

- materials ( bool ) – Compare Materials, (optional)

- deselect_joined ( bool ) – Deselect Joined, Only select remaining triangles that were not merged (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. customdata_custom_splitnormals_add ( )

Introduce a custom normals data layer if not already present

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. customdata_custom_splitnormals_clear ( )

Erase the custom normals data layer

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. customdata_mask_clear ( )

Wipe vertex sculpt mask information

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. customdata_skin_add ( )

Introduce a vertex skin data layer

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. customdata_skin_clear ( )

Eliminate vertex skin data layer

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. decimate ( * , ratio = 1.0 , use_vertex_group = False , vertex_group_factor = 1.0 , invert_vertex_group = False , use_symmetry = False , symmetry_axis = 'Y' )

Lower geometry detail by removing edges

Parameters :

- ratio ( float ) – Ratio, (in [0, 1], optional)

- use_vertex_group ( bool ) – Vertex Group, Use active vertex group as an influence (optional)

- vertex_group_factor ( float ) – Weight, Vertex group strength (in [0, 1000], optional)

- invert_vertex_group ( bool ) – Invert, Invert vertex group influence (optional)

- use_symmetry ( bool ) – Symmetry, Maintain symmetry on an axis (optional)

- symmetry_axis (Literal[Axis Xyz Items]) – Axis, Axis of symmetry (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. delete ( * , type = 'VERT' )

Purge picked vertices, edges or faces

Parameters :

type ( Literal [ 'VERT' , 'EDGE' , 'FACE' , '`EDGE_FACE`' , '`ONLY_FACE`' ] ) – Type, Method used for deleting mesh data (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. delete_edgeloop ( * , use_face_split = True )

Destroy an edge loop by joining faces on either side

Parameters :

use_face_split ( bool ) – Face Split, Split off face corners to maintain surrounding geometry (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. delete_loose ( * , use_verts = True , use_edges = True , use_faces = False )

Erase isolated vertices, edges or polygons

Parameters :

- use_verts ( bool ) – Vertices, Remove loose vertices (optional)

- use_edges ( bool ) – Edges, Remove loose edges (optional)

- use_faces ( bool ) – Faces, Remove loose faces (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. dissolve_degenerate ( * , threshold = 0.0001 )

Collapse faces with nearly no area and very short edges

Parameters :

threshold ( float ) – Merge Distance, Maximum distance between elements to merge (in [1e-06, 50], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. dissolve_edges ( * , use_verts = True , angle_threshold = 3.14159 , use_face_split = False )

Obliterate edges and combine adjacent faces

Parameters :

- use_verts ( bool ) – Dissolve Vertices, Dissolve remaining vertices which connect to only two edges (optional)

- angle_threshold ( float ) – Angle Threshold, Remaining vertices which separate edge pairs are preserved if their edge angle exceeds this threshold. (in [0, 3.14159], optional)

- use_face_split ( bool ) – Face Split, Split off face corners to maintain surrounding geometry (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. dissolve_faces ( * , use_verts = False )

Obliterate picked polygons

Parameters :

use_verts ( bool ) – Dissolve Vertices, Dissolve remaining vertices which connect to only two edges (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. dissolve_limited ( * , angle_limit = 0.0872665 , use_dissolve_boundaries = False , delimit = {'NORMAL'} )

Demolish chosen edges and vertices constrained by surrounding geometry angles

Parameters :

- angle_limit ( float ) – Max Angle, Angle limit (in [0, 3.14159], optional)

- use_dissolve_boundaries ( bool ) – All Boundaries, Dissolve all vertices in between face boundaries (optional)

- delimit (set[Literal[Mesh Delimit Mode Items]]) – Delimit, Delimit dissolve operation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. dissolve_mode ( * , use_verts = False , angle_threshold = 3.14159 , use_face_split = False , use_boundary_tear = False )

Demolish topology depending on edit mode selection

Parameters :

- use_verts ( bool ) – Dissolve Vertices, Dissolve remaining vertices which connect to only two edges (optional)

- angle_threshold ( float ) – Angle Threshold, Remaining vertices which separate edge pairs are preserved if their edge angle exceeds this threshold. (in [0, 3.14159], optional)

- use_face_split ( bool ) – Face Split, Split off face corners to maintain surrounding geometry (optional)

- use_boundary_tear ( bool ) – Tear Boundary, Split off face corners instead of merging faces (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. dissolve_verts ( * , use_face_split = False , use_boundary_tear = False )

Obliterate points and stitch surrounding edges and faces

Parameters :

- use_face_split ( bool ) – Face Split, Split off face corners to maintain surrounding geometry (optional)

- use_boundary_tear ( bool ) – Tear Boundary, Split off face corners instead of merging faces (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. dupli_extrude_cursor ( * , rotate_source = True )

Produce and extend chosen vertices, edges or faces toward the pointer

Parameters :

rotate_source ( bool ) – Rotate Source, Rotate initial selection giving better shape (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. duplicate ( * , mode = 1 )

Produce copies of chosen vertices, edges or faces

Parameters :

mode ( int ) – Mode, (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. duplicate_move ( * , `MESH_OT`_duplicate = {} , `TRANSFORM_OT`_translate = {} )

Produce a mesh replica and reposition it

Parameters :

- `MESH_OT`_duplicate ( dict [ str , Any ] ) – Duplicate, Duplicate selected vertices, edges or faces (optional, bpy.ops.mesh.duplicate() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mesh. edge_collapse ( )

Eradicate isolated edge and face areas, uniting UV and color properties. Capable of collapsing edge-rings plus connected face zones into points
