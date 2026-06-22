# Bmesh Operators Bmesh Ops (part 2)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

- matrix (mathutils.Matrix) – Matrix defining rotation.

- verts (list[bmesh.types.BMVert]) – Input vertices.

- space (mathutils.Matrix) – Matrix to define the space (typically object matrix).

- use_shapekey ( bool ) – Transform shape keys too.

bmesh.ops. translate ( bm , vec = mathutils.Vector() , space = mathutils.Matrix.Identity(4) , verts = [] , use_shapekey = False ) 

Translate.

Translate vertices by an offset.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- vec ( Sequence [ float ] ) – Translation offset.

- space (mathutils.Matrix) – Matrix to define the space (typically object matrix).

- verts (list[bmesh.types.BMVert]) – Input vertices.

- use_shapekey ( bool ) – Transform shape keys too.

bmesh.ops. scale ( bm , vec = mathutils.Vector() , space = mathutils.Matrix.Identity(4) , verts = [] , use_shapekey = False ) 

Scale.

Scales vertices by a factor.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- vec ( Sequence [ float ] ) – Scale factor.

- space (mathutils.Matrix) – Matrix to define the space (typically object matrix).

- verts (list[bmesh.types.BMVert]) – Input vertices.

- use_shapekey ( bool ) – Transform shape keys too.

bmesh.ops. transform ( bm , matrix = mathutils.Matrix.Identity(4) , space = mathutils.Matrix.Identity(4) , verts = [] , use_shapekey = False ) 

Transform.

Applies a matrix transformation to a set of vertices. Multiplies
the vertex coordinates with the matrix.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- matrix (mathutils.Matrix) – Transform matrix.

- space (mathutils.Matrix) – Matrix to define the space (typically object matrix).

- verts (list[bmesh.types.BMVert]) – Input vertices.

- use_shapekey ( bool ) – Transform shape keys too.

bmesh.ops. object_load_bmesh ( bm , scene , object ) 

Object Load BMesh.

Loads a bmesh into an object/mesh. This is a "private"
BMOP.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- scene (bpy.types.Scene) – The scene.

- object (bpy.types.Object) – The object.

bmesh.ops. bmesh_to_mesh ( bm , mesh , object ) 

BMesh to Mesh.

Converts a bmesh to a Mesh. This is reserved for exiting edit-mode.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- mesh (bpy.types.Mesh) – The mesh to write into.

- object (bpy.types.Object) – The object.

bmesh.ops. mesh_to_bmesh ( bm , mesh , object , use_shapekey = False ) 

Mesh to BMesh.

Load the contents of a mesh into the bmesh. this BMOP is private, it's
reserved exclusively for entering edit-mode.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- mesh (bpy.types.Mesh) – The mesh to read from.

- object (bpy.types.Object) – The object.

- use_shapekey ( bool ) – Load active shapekey coordinates into verts.

bmesh.ops. extrude_discrete_faces ( bm , faces = [] , use_normal_flip = False , use_select_history = False ) 

Individual Face Extrude.

Extrudes faces individually.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- faces (list[bmesh.types.BMFace]) – Input faces.

- use_normal_flip ( bool ) – Create faces with reversed direction.

- use_select_history ( bool ) – Preserve the selection history in the extruded geometry.

Returns :

- faces :
Output faces.

type list[bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. extrude_edge_only ( bm , edges = [] , use_normal_flip = False , use_select_history = False ) 

Extrude Only Edges.

Extrudes Edges into faces, note that this is very simple, there's no fancy
winged extrusion.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- edges (list[bmesh.types.BMEdge]) – Input edges.

- use_normal_flip ( bool ) – Create faces with reversed direction.

- use_select_history ( bool ) – Preserve the selection history in the extruded geometry.

Returns :

- geom :
Output geometry.

type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. extrude_vert_indiv ( bm , verts = [] , use_select_history = False ) 

Individual Vertex Extrude.

Extrudes individual vertices, creating new vertices connected by wire edges.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- verts (list[bmesh.types.BMVert]) – Input vertices.

- use_select_history ( bool ) – Preserve the selection history in the extruded geometry.

Returns :

- edges :
Output wire edges.

type list[bmesh.types.BMEdge]

- verts :
Output vertices.

type list[bmesh.types.BMVert]

Return type :

dict[str, Any]

bmesh.ops. connect_verts ( bm , verts = [] , faces_exclude = [] , check_degenerate = False ) 

Connect Verts.

Split faces by adding edges that connect verts .

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- verts (list[bmesh.types.BMVert]) – Input vertices.

- faces_exclude (list[bmesh.types.BMFace]) – Input faces to explicitly exclude from connecting.

- check_degenerate ( bool ) – Prevent splits with overlaps & intersections.

Returns :

- edges :

type list[bmesh.types.BMEdge]

Return type :

dict[str, Any]

bmesh.ops. connect_verts_concave ( bm , faces = [] ) 

Connect Verts to form Convex Faces.

Splits concave faces into convex faces.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- faces (list[bmesh.types.BMFace]) – Input faces.

Returns :

- edges :

type list[bmesh.types.BMEdge]

- faces :

type list[bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. connect_verts_nonplanar ( bm , angle_limit = 0 , faces = [] ) 

Connect Verts Across non Planar Faces.

Split faces by connecting edges along non planar faces .

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- angle_limit ( float ) – Maximum angle of non-planarity before splitting (radians).

- faces (list[bmesh.types.BMFace]) – Input faces.

Returns :

- edges :

type list[bmesh.types.BMEdge]

- faces :

type list[bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. connect_vert_pair ( bm , verts = [] , verts_exclude = [] , faces_exclude = [] ) 

Connect Vert Pair.

Connect a pair of vertices by splitting faces along the shortest path between them.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- verts (list[bmesh.types.BMVert]) – Input vertices.

- verts_exclude (list[bmesh.types.BMVert]) – Input vertices to explicitly exclude from connecting.

- faces_exclude (list[bmesh.types.BMFace]) – Input faces to explicitly exclude from connecting.

Returns :

- edges :

type list[bmesh.types.BMEdge]

Return type :

dict[str, Any]

bmesh.ops. extrude_face_region ( bm , geom = [] , edges_exclude = set() , use_keep_orig = False , use_normal_flip = False , use_normal_from_adjacent = False , use_dissolve_ortho_edges = False , use_select_history = False , skip_input_flip = False ) 

Extrude Faces.

Extrude operator (does not transform)

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- geom (list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]) – Edges and faces.

- edges_exclude (set[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]) – Input edges to explicitly exclude from extrusion.

- use_keep_orig ( bool ) – Keep original geometry (requires geom to include edges).

- use_normal_flip ( bool ) – Create faces with reversed direction.

- use_normal_from_adjacent ( bool ) – Use winding from surrounding faces instead of this region.

- use_dissolve_ortho_edges ( bool ) – Dissolve edges whose faces form a flat surface.

- use_select_history ( bool ) – Preserve the selection history in the extruded geometry.

- skip_input_flip ( bool ) – Skip flipping of input faces to preserve original orientation.

Returns :

- geom :

type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. dissolve_verts ( bm , verts = [] , use_face_split = False , use_boundary_tear = False ) 

Dissolve Verts.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- verts (list[bmesh.types.BMVert]) – Input vertices.

- use_face_split ( bool ) – Split off face corners to maintain surrounding geometry.

- use_boundary_tear ( bool ) – Split off face corners instead of merging faces.

bmesh.ops. dissolve_edges ( bm , edges = [] , use_verts = False , use_face_split = False , angle_threshold = 0 ) 

Dissolve Edges.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- edges (list[bmesh.types.BMEdge]) – Input edges.

- use_verts ( bool ) – Dissolve verts left between only 2 edges.

- use_face_split ( bool ) – Split off face corners to maintain surrounding geometry.

- angle_threshold ( float ) – Do not dissolve verts between 2 edges when their angle exceeds this threshold.
Disabled by default.

Returns :

- region :

type list[bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. dissolve_faces ( bm , faces = [] , use_verts = False ) 

Dissolve Faces.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- faces (list[bmesh.types.BMFace]) – Input faces.

- use_verts ( bool ) – Dissolve verts left between only 2 edges.

Returns :

- region :

type list[bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. dissolve_limit ( bm , angle_limit = 0 , use_dissolve_boundaries = False , verts = [] , edges = [] , delimit = set() ) 

Limited Dissolve.

Dissolve planar faces and co-linear edges.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- angle_limit ( float ) – Maximum angle (radians) between face normals for dissolving.

- use_dissolve_boundaries ( bool ) – Dissolve all vertices in between face boundaries.

- verts (list[bmesh.types.BMVert]) – Input vertices.

- edges (list[bmesh.types.BMEdge]) – Input edges.

- delimit ( set [ Literal [ 'NORMAL' , 'MATERIAL' , 'SEAM' , 'SHARP' , 'UV' ] ] ) – Delimit dissolve operation.

Returns :

- region :

type list[bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. dissolve_degenerate ( bm , dist = 0 , edges = [] ) 

Degenerate Dissolve.

Dissolve edges with no length, faces with no area.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- dist ( float ) – Maximum distance to consider degenerate.

- edges (list[bmesh.types.BMEdge]) – Input edges.

bmesh.ops. triangulate ( bm , faces = [] , quad_method = 'BEAUTY' , ngon_method = 'BEAUTY' ) 

Triangulate.

Triangulate faces, splitting quads and n-gons into triangles.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- faces (list[bmesh.types.BMFace]) – Input faces.

- quad_method ( Literal [ 'BEAUTY' , 'FIXED' , 'ALTERNATE' , '`SHORT_EDGE`' , '`LONG_EDGE`' ] ) – Method for splitting the quads into triangles.

- ngon_method ( Literal [ 'BEAUTY' , '`EAR_CLIP`' ] ) – Method for splitting the polygons into triangles.

Returns :

- edges :

type list[bmesh.types.BMEdge]

- faces :

type list[bmesh.types.BMFace]

- face_map :

type dict[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace, bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

- face_map_double :
Duplicate faces.

type dict[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace, bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. unsubdivide ( bm , verts = [] , iterations = 0 ) 

Un-Subdivide.

Reduce detail in geometry containing grids.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- verts (list[bmesh.types.BMVert]) – Input vertices.

- iterations ( int ) – Number of times to unsubdivide.

bmesh.ops. subdivide_edges ( bm , edges = [] , smooth = 0 , smooth_falloff = 'SMOOTH' , fractal = 0 , along_normal = 0 , cuts = 0 , seed = 0 , custom_patterns = {} , edge_percents = {} , quad_corner_type = '`STRAIGHT_CUT`' , use_grid_fill = False , use_single_edge = False , use_only_quads = False , use_sphere = False , use_smooth_even = False ) 

Subdivide Edges.

Advanced operator for subdividing edges
with options for face patterns, smoothing and randomization.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- edges (list[bmesh.types.BMEdge]) – Input edges.

- smooth ( float ) – Smoothness factor.

- smooth_falloff ( Literal [ 'SMOOTH' , 'SPHERE' , 'ROOT' , 'SHARP' , 'LINEAR' , '`INVERSE_SQUARE`' ] ) – Smooth falloff type.

- fractal ( float ) – Fractal randomness factor.

- along_normal ( float ) – Factor (0 to 1) controlling how much fractal displacement is restricted to the normal.

- cuts ( int ) – Number of cuts.

- seed ( int ) – Seed for the random number generator.

- custom_patterns ( dict ) – Internal use only, not accessible from Python.

- edge_percents (dict[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace, float]) – Mapping of edges to a float (0 to 1) controlling the cut position along each edge.

- quad_corner_type ( Literal [ '`STRAIGHT_CUT`' , '`INNER_VERT`' , 'PATH' , 'FAN' ] ) – Quad corner type.

- use_grid_fill ( bool ) – Fill in fully-selected faces with a grid.

- use_single_edge ( bool ) – Tessellate the case of one edge selected in a quad or triangle.

- use_only_quads ( bool ) – Only subdivide quads (for loop-cut).

- use_sphere ( bool ) – Project new vertices onto a sphere (used for spherical primitives).

- use_smooth_even ( bool ) – Maintain even offset when smoothing.

Returns :

- geom_inner :

type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

- geom_split :

type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

- geom :
Contains all output geometry.

type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. subdivide_edgering ( bm , edges = [] , interp_mode = 'LINEAR' , smooth = 0 , cuts = 0 , profile_shape = 'SMOOTH' , profile_shape_factor = 0 ) 

Subdivide Edge-Ring.

Take an edge-ring, and subdivide with interpolation options.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- edges (list[bmesh.types.BMEdge]) – Input edges.

- interp_mode ( Literal [ 'LINEAR' , 'PATH' , 'SURFACE' ] ) – Interpolation method.

- smooth ( float ) – Smoothness factor.

- cuts ( int ) – Number of cuts.

- profile_shape ( Literal [ 'SMOOTH' , 'SPHERE' , 'ROOT' , 'SHARP' , 'LINEAR' , '`INVERSE_SQUARE`' ] ) – Profile shape type.

- profile_shape_factor ( float ) – How much intermediary new edges are shrunk/expanded.

Returns :

- faces :
Output faces.

type list[bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. bisect_plane ( bm , geom = [] , dist = 0 , plane_co = mathutils.Vector() , plane_no = mathutils.Vector() , use_snap_center = False , clear_outer = False , clear_inner = False ) 

Bisect Plane.

Bisects the mesh by a plane (cut the mesh in half).

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- geom (list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]) – Input geometry.

- dist ( float ) – Minimum distance when testing if a vert is exactly on the plane.

- plane_co ( Sequence [ float ] ) – Point on the plane.

- plane_no ( Sequence [ float ] ) – Normal of the plane.

- use_snap_center ( bool ) – Snap axis aligned verts to the center.

- clear_outer ( bool ) – When enabled, remove all geometry on the positive side of the plane.

- clear_inner ( bool ) – When enabled, remove all geometry on the negative side of the plane.

Returns :

- geom_cut :
Output geometry aligned with the plane (new and existing).

type list[bmesh.types.BMVert | bmesh.types.BMEdge]

- geom :
Input and output geometry (result of cut).

type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. delete ( bm , geom = [] , context = 'VERTS' ) 

Delete Geometry.

Utility operator to delete geometry.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- geom (list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]) – Input geometry.

- context ( Literal [ 'VERTS' , 'EDGES' , '`FACES_ONLY`' , '`EDGES_FACES`' , 'FACES' , '`FACES_KEEP_BOUNDARY`' , '`TAGGED_ONLY`' ] ) – Geometry types to delete.

bmesh.ops. duplicate ( bm , geom = [] , dest = None , use_select_history = False , use_edge_flip_from_face = False ) 

Duplicate Geometry.

Utility operator to duplicate geometry,
optionally into a destination mesh.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- geom (list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]) – Input geometry.

- dest (bmesh.types.BMesh | None) – Destination bmesh, if None will use current one.

- use_select_history ( bool ) – Preserve the selection history in the duplicated geometry.

- use_edge_flip_from_face ( bool ) – Copy edge flip state from connected faces.

Returns :

- geom_orig :

type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

- geom :

type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

- vert_map :

type dict[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace, bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

- edge_map :

type dict[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace, bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

- face_map :

type dict[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace, bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

- boundary_map :
Boundary edges from the split geometry that maps edges from the original geometry
to the destination edges.

type dict[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace, bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

- isovert_map :

type dict[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace, bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. split ( bm , geom = [] , dest = None , use_only_faces = False ) 

Split Off Geometry.

Disconnect geometry from adjacent edges and faces,
optionally into a destination mesh.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- geom (list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]) – Input geometry.

- dest (bmesh.types.BMesh | None) – Destination bmesh, if None will use current one.

- use_only_faces ( bool ) – When enabled, don't duplicate loose verts/edges.

Returns :

- geom :

type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

- boundary_map :
Boundary edges from the split geometry that maps edges from the original geometry
to the destination edges.

When the source edges have been deleted, the destination edge will be used
for both the key and the value.

type dict[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace, bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

- isovert_map :

type dict[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace, bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. spin ( bm , geom = [] , cent = mathutils.Vector() , axis = mathutils.Vector() , dvec = mathutils.Vector() , angle = 0 , space = mathutils.Matrix.Identity(4) , steps = 0 , use_merge = False , use_normal_flip = False , use_duplicate = False ) 

Spin.

Extrude or duplicate geometry a number of times,
rotating and possibly translating after each step

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- geom (list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]) – Input geometry.

- cent ( Sequence [ float ] ) – Rotation center.

- axis ( Sequence [ float ] ) – Rotation axis.

- dvec ( Sequence [ float ] ) – Translation delta per step.

- angle ( float ) – Total rotation angle (radians).

- space (mathutils.Matrix) – Matrix to define the space (typically object matrix).
