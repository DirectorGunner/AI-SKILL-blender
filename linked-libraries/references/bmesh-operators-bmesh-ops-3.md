# Bmesh Operators Bmesh Ops (part 3)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

- steps ( int ) – Number of steps.

- use_merge ( bool ) – Merge first/last when the angle is a full revolution.

- use_normal_flip ( bool ) – Create faces with reversed direction.

- use_duplicate ( bool ) – Duplicate the geometry, otherwise extrude.

Returns :

- geom_last :
Result of last step.

type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. rotate_uvs ( bm , faces = [] , use_ccw = False ) 

UV Rotation.

Cycle the loop UVs

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- faces (list[bmesh.types.BMFace]) – Input faces.

- use_ccw ( bool ) – Rotate counter-clockwise if true, otherwise clockwise.

bmesh.ops. reverse_uvs ( bm , faces = [] ) 

UV Reverse.

Reverse the UVs

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- faces (list[bmesh.types.BMFace]) – Input faces.

bmesh.ops. rotate_colors ( bm , faces = [] , use_ccw = False , color_index = 0 ) 

Color Rotation.

Cycle the loop colors

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- faces (list[bmesh.types.BMFace]) – Input faces.

- use_ccw ( bool ) – Rotate counter-clockwise if true, otherwise clockwise.

- color_index ( int ) – Index into color attribute list.

bmesh.ops. reverse_colors ( bm , faces = [] , color_index = 0 ) 

Color Reverse

Reverse the loop colors.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- faces (list[bmesh.types.BMFace]) – Input faces.

- color_index ( int ) – Index into color attribute list.

bmesh.ops. split_edges ( bm , edges = [] , verts = [] , use_verts = False ) 

Edge Split.

Disconnects faces along input edges.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- edges (list[bmesh.types.BMEdge]) – Input edges.

- verts (list[bmesh.types.BMVert]) – Optional tag verts, use to have greater control of splits.

- use_verts ( bool ) – Use verts for splitting, else just find verts to split from edges.

Returns :

- edges :
The original edges that were disconnected.

type list[bmesh.types.BMEdge]

Return type :

dict[str, Any]

bmesh.ops. create_grid ( bm , x_segments = 0 , y_segments = 0 , size = 0 , matrix = mathutils.Matrix.Identity(4) , calc_uvs = False ) 

Create Grid.

Creates a grid with a variable number of subdivisions

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- x_segments ( int ) – Number of x segments.

- y_segments ( int ) – Number of y segments.

- size ( float ) – Size of the grid.

- matrix (mathutils.Matrix) – Matrix to multiply the new geometry with.

- calc_uvs ( bool ) – Calculate default UVs.

Returns :

- verts :
Output verts.

type list[bmesh.types.BMVert]

Return type :

dict[str, Any]

bmesh.ops. create_uvsphere ( bm , u_segments = 0 , v_segments = 0 , radius = 0 , matrix = mathutils.Matrix.Identity(4) , calc_uvs = False ) 

Create UV Sphere.

Creates a UV sphere with a variable number of subdivisions.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- u_segments ( int ) – Number of u segments.

- v_segments ( int ) – Number of v segments.

- radius ( float ) – Radius.

- matrix (mathutils.Matrix) – Matrix to multiply the new geometry with.

- calc_uvs ( bool ) – Calculate default UVs.

Returns :

- verts :
Output verts.

type list[bmesh.types.BMVert]

Return type :

dict[str, Any]

bmesh.ops. create_icosphere ( bm , subdivisions = 0 , radius = 0 , matrix = mathutils.Matrix.Identity(4) , calc_uvs = False ) 

Create Ico-Sphere.

Creates an ico-sphere with a variable number of subdivisions.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- subdivisions ( int ) – How many times to recursively subdivide the sphere.

- radius ( float ) – Radius.

- matrix (mathutils.Matrix) – Matrix to multiply the new geometry with.

- calc_uvs ( bool ) – Calculate default UVs.

Returns :

- verts :
Output verts.

type list[bmesh.types.BMVert]

Return type :

dict[str, Any]

bmesh.ops. create_monkey ( bm , matrix = mathutils.Matrix.Identity(4) , calc_uvs = False ) 

Create Suzanne.

Creates a monkey (standard blender primitive).

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- matrix (mathutils.Matrix) – Matrix to multiply the new geometry with.

- calc_uvs ( bool ) – Calculate default UVs.

Returns :

- verts :
Output verts.

type list[bmesh.types.BMVert]

Return type :

dict[str, Any]

bmesh.ops. create_cone ( bm , cap_ends = False , cap_tris = False , segments = 0 , radius1 = 0 , radius2 = 0 , depth = 0 , matrix = mathutils.Matrix.Identity(4) , calc_uvs = False ) 

Create Cone.

Creates a cone with variable radius at both ends

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- cap_ends ( bool ) – Whether or not to fill in the ends with faces.

- cap_tris ( bool ) – Fill ends with triangles instead of ngons.

- segments ( int ) – Number of vertices in the base circle.

- radius1 ( float ) – Radius of one end.

- radius2 ( float ) – Radius of the opposite end.

- depth ( float ) – Distance between ends.

- matrix (mathutils.Matrix) – Matrix to multiply the new geometry with.

- calc_uvs ( bool ) – Calculate default UVs.

Returns :

- verts :
Output verts.

type list[bmesh.types.BMVert]

Return type :

dict[str, Any]

bmesh.ops. create_circle ( bm , cap_ends = False , cap_tris = False , segments = 0 , radius = 0 , matrix = mathutils.Matrix.Identity(4) , calc_uvs = False ) 

Generates a circle.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- cap_ends ( bool ) – Optionally fill in the circle with a face.

- cap_tris ( bool ) – Fill the circle with triangles instead of an n-gon.

- segments ( int ) – Number of vertices in the circle.

- radius ( float ) – Radius of the circle.

When multiplying new geometry with a transformation, the matrix parameter accepts a mathutils.Matrix object to apply scaling, rotation, or translation to generated vertices.

calc_uvs ( bool ) – Whether to generate texture coordinates automatically upon creation.

Returns :

- verts :
Output verts.

type list[bmesh.types.BMVert]

Return type :

dict[str, Any]

bmesh.ops. create_cube ( bm , size = 0 , matrix = mathutils.Matrix.Identity(4) , calc_uvs = False ) –

Cube Generation

Produces a six-sided box primitive within the bmesh.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh target for the operation.

- size ( float ) – Dimensions of each side.

- matrix (mathutils.Matrix) – Linear transformation to apply to all new vertices.

- calc_uvs ( bool ) – Whether to generate default texture coordinate mapping.

Returns :

- verts :
Output verts.

type list[bmesh.types.BMVert]

Return type :

dict[str, Any]

bmesh.ops. bevel ( bm , geom = [] , offset = 0 , offset_type = 'OFFSET' , profile_type = 'SUPERELLIPSE' , segments = 0 , profile = 0 , affect = 'VERTICES' , clamp_overlap = False , material = 0 , loop_slide = False , mark_seam = False , mark_sharp = False , harden_normals = False , face_strength_mode = 'NONE' , miter_outer = 'SHARP' , miter_inner = 'SHARP' , spread = 0 , custom_profile = None , vmesh_method = 'ADJ' ) –

Chamfering Tool

Rounds off edges and vertex corners with configurable geometry.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh target for the operation.

- geom (list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]) – Selection of edges and corner vertices to process.

- offset ( float ) – Distance to move the chamfered edge outward.

- offset_type ( Literal [ 'OFFSET' , 'WIDTH' , 'DEPTH' , 'PERCENT' , 'ABSOLUTE' ] ) – Interpretation of the offset value (absolute distance, perpendicular width, depth into faces, scaled percentage, or pixel-perfect measurement).

- profile_type ( Literal [ 'SUPERELLIPSE' , 'CUSTOM' ] ) – Shape type for the rounded edge (standard superellipse or user-defined curve).

- segments ( int ) – How many subdivisions to add along the chamfered region.

- profile ( float ) – Curvature from linear (0) through rounded (0.5) to pinched (1).

- affect ( Literal [ 'VERTICES' , 'EDGES' ] ) – Which geometry type to process (corner points or connecting edges).

- clamp_overlap ( bool ) – Prevent chamfered regions from intersecting one another.

- material ( int ) – Slot index for new faces (-1 uses surrounding face materials).

- loop_slide ( bool ) – Maintain edge-aligned width rather than centering the offset.

- mark_seam ( bool ) – Mark seams so they continue across the chamfered area.

- mark_sharp ( bool ) – Preserve sharp markings through the chamfer.

- harden_normals ( bool ) – Make surface normal discontinuities explicit.

- face_strength_mode ( Literal [ 'NONE' , 'NEW' , 'AFFECTED' , 'ALL' ] ) – Whether to apply face strength weighting and which faces to include.

- miter_outer ( Literal [ 'SHARP' , 'PATCH' , 'ARC' ] ) – Intersection style at outer corners (peaked, flat patch, or curved).

- miter_inner ( Literal [ 'SHARP' , 'PATCH' , 'ARC' ] ) – Intersection style at inner corners (peaked, flat patch, or curved).

- spread ( float ) – Offset distance applied to miter vertices.

- custom_profile (bpy.types.bpy_struct | None) – A CurveProfile object defining edge shape; passes through when None.

- vmesh_method ( Literal [ 'ADJ' , 'CUTOFF' ] ) – Algorithm for vertex-corner geometry (adjacency-based or threshold cutoff).

Returns :

- faces :
Output faces.

type list[bmesh.types.BMFace]

- edges :
Output edges.

type list[bmesh.types.BMEdge]

- verts :
Output verts.

type list[bmesh.types.BMVert]

Return type :

dict[str, Any]

bmesh.ops. beautify_fill ( bm , faces = [] , edges = [] , use_restrict_tag = False , method = 'AREA' ) –

Triangle Equalization

Reorientation of polygon diagonals to produce evenly proportioned triangles.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh target for the operation.

- faces (list[bmesh.types.BMFace]) – Triangulated regions to process.

- edges (list[bmesh.types.BMEdge]) – Boundaries available for diagonal flipping.

- use_restrict_tag ( bool ) – Flip only diagonals between differently marked boundary vertices.

- method ( Literal [ 'AREA' , 'ANGLE' ] ) – Optimization metric (smallest enclosed area or minimal corner angles).

Returns :

- geom :
New flipped faces and edges

Parameters:
- bm (bmesh.types.BMesh) – The bmesh to act on.
- faces (list[bmesh.types.BMFace]) – Input faces.
- faces_exclude (list[bmesh.types.BMFace]) – Input faces to explicitly exclude from inset.
- use_boundary ( bool ) – Inset face boundaries.
- use_even_offset ( bool ) – Scale the offset to give more even thickness.
- use_interpolate ( bool ) – Blend face data across the inset.
- use_relative_offset ( bool ) – Scale the offset by surrounding geometry.
- use_edge_rail ( bool ) – Inset the region along existing edges.
- thickness ( float ) – Inset distance from the boundary.
- depth ( float ) – Distance to raise or lower the inset face along its normal.
- use_outset ( bool ) – Outset rather than inset.
Returns:
- faces: Output faces. type list[bmesh.types.BMFace]
Return type: dict[str, Any]

bmesh.ops. offset_edgeloops ( bm , edges = [] , use_cap_endpoint = False )
Edge-loop Offset. Adds edge loops using a simple edge-outset method.
Parameters:
- bm (bmesh.types.BMesh) – The bmesh to act on.
- edges (list[bmesh.types.BMEdge]) – Input edges.
- use_cap_endpoint ( bool ) – Extend loop around end-points.
Returns:
- edges: Output edges. type list[bmesh.types.BMEdge]
Return type: dict[str, Any]

bmesh.ops. wireframe ( bm , faces = [] , thickness = 0 , offset = 0 , use_replace = False , use_boundary = False , use_even_offset = False , use_crease = False , crease_weight = 0 , use_relative_offset = False , material_offset = 0 )
Wire Frame. Produces a wire-frame copy of the faces.
Parameters:
- bm (bmesh.types.BMesh) – The bmesh to act on.
- faces (list[bmesh.types.BMFace]) – Input faces.
- thickness ( float ) – Wire thickness.
- offset ( float ) – Offset the thickness from the center.
- use_replace ( bool ) – Remove original geometry.
- use_boundary ( bool ) – Inset face boundaries.
- use_even_offset ( bool ) – Scale the offset to give more even thickness.
- use_crease ( bool ) – Crease hub edges for improved subdivision surface.
- crease_weight ( float ) – The mean crease weight for resulting edges.
- use_relative_offset ( bool ) – Scale the offset by surrounding geometry.
- material_offset ( int ) – Offset material index of generated faces.
Returns:
- faces: Output faces. type list[bmesh.types.BMFace]
Return type: dict[str, Any]

bmesh.ops. poke ( bm , faces = [] , offset = 0 , center_mode = '`MEAN_WEIGHTED`' , use_relative_offset = False )
Poke. Splits each face into a triangle fan from a central vertex.
Parameters:
- bm (bmesh.types.BMesh) – The bmesh to act on.
- faces (list[bmesh.types.BMFace]) – Input faces.
- offset ( float ) – Center vertex offset along normal.
- center_mode ( Literal [ '`MEAN_WEIGHTED`' , 'MEAN' , 'BOUNDS' ] ) – Calculation mode for center vertex.
- use_relative_offset ( bool ) – Apply offset.
Returns:
- verts: Output verts. type list[bmesh.types.BMVert]
- faces: Output faces. type list[bmesh.types.BMFace]
Return type: dict[str, Any]

bmesh.ops. convex_hull ( bm , input = [] , use_existing_faces = False )
Convex Hull. Builds a convex hull from the vertices supplied in input. With use_existing_faces true, the hull won't output triangles already covered by a pre-existing face. Every hull vertex, face, and edge is added to geom.out; any input elements that end up inside the hull (not used by an output face) are added to the geom_interior.out slot; the geom_unused.out slot holds all interior geometry that is completely unused; and geom_holes.out holds the edges and faces that were in the input and form part of the hull.
Parameters:
- bm (bmesh.types.BMesh) – The bmesh to act on.
- input (list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]) – Input geometry.
- use_existing_faces ( bool ) – Skip hull triangles that are covered by a pre-existing face.
Returns:
- geom: type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]
- geom_interior: type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]
- geom_unused: type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]
- geom_holes: type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]
Return type: dict[str, Any]

bmesh.ops. symmetrize ( bm , input = [] , direction = '-X' , dist = 0 , use_shapekey = False )
Symmetrize. Makes the mesh elements in the input slot symmetrical. Unlike ordinary mirroring it copies in only one direction, set by the direction slot, splitting the edges and faces that cross the plane of symmetry as needed to enforce symmetry. All new vertices, edges, and faces are added to the geom.out slot.
Parameters:
- bm (bmesh.types.BMesh) – The bmesh to act on.
- input (list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]) – Input geometry.
- direction ( Literal [ '-X' , '-Y' , '-Z' , 'X' , 'Y' , 'Z' ] ) – Axis to use.
- dist ( float ) – Minimum distance.
- use_shapekey ( bool ) – Transform shape keys too.
Returns:
- geom: type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]
Return type: dict[str, Any]
