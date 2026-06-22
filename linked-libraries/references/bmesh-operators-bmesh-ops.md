# Bmesh Operators Bmesh Ops (part 1)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

### BMesh Operators (bmesh.ops) 

This module gives access to low level bmesh operations.

Most operators take input and return output, they can be chained together
to perform useful operations.

### Operator Example 

This script shows how operators can be used to model a link of a chain.

`\text
### This script uses bmesh operators to make 2 links of a chain.

import bpy
import bmesh
import math
import mathutils

### Make a new BMesh
bm = bmesh.new()

### Add a circle XXX, should return all geometry created, not just verts.
bmesh.ops.create_circle(
bm,
cap_ends=False,
radius=0.2,
segments=8)

### Spin and deal with geometry on side 'a'
edges_start_a = bm.edges[:]
geom_start_a = bm.verts[:] + edges_start_a
ret = bmesh.ops.spin(
bm,
geom=geom_start_a,
angle=math.radians(180.0),
steps=8,
axis=(1.0, 0.0, 0.0),
cent=(0.0, 1.0, 0.0))
edges_end_a = [ele for ele in ret["geom_last"]
if isinstance(ele, bmesh.types.BMEdge)]
del ret

### Extrude and create geometry on side 'b'
ret = bmesh.ops.extrude_edge_only(
bm,
edges=edges_start_a)
geom_extrude_mid = ret["geom"]
del ret

### Collect the edges to spin XXX, 'extrude_edge_only' could return this.
verts_extrude_b = [ele for ele in geom_extrude_mid
if isinstance(ele, bmesh.types.BMVert)]
edges_extrude_b = [ele for ele in geom_extrude_mid
if isinstance(ele, bmesh.types.BMEdge) and ele.is_boundary]
bmesh.ops.translate(
bm,
verts=verts_extrude_b,
vec=(0.0, 0.0, 1.0))

### Create the circle on side 'b'
ret = bmesh.ops.spin(
bm,
geom=verts_extrude_b + edges_extrude_b,
angle=-math.radians(180.0),
steps=8,
axis=(1.0, 0.0, 0.0),
cent=(0.0, 1.0, 1.0))
edges_end_b = [ele for ele in ret["geom_last"]
if isinstance(ele, bmesh.types.BMEdge)]
del ret

### Bridge the resulting edge loops of both spins 'a & b'
bmesh.ops.bridge_loops(
bm,
edges=edges_end_a + edges_end_b)

### Now we have made a links of the chain, make a copy and rotate it
### (so this looks something like a chain)

ret = bmesh.ops.duplicate(
bm,
geom=bm.verts[:] + bm.edges[:] + bm.faces[:])
geom_dupe = ret["geom"]
verts_dupe = [ele for ele in geom_dupe if isinstance(ele, bmesh.types.BMVert)]
del ret

### position the new link
bmesh.ops.translate(
bm,
verts=verts_dupe,
vec=(0.0, 0.0, 2.0))
bmesh.ops.rotate(
bm,
verts=verts_dupe,
cent=(0.0, 1.0, 0.0),
matrix=mathutils.Matrix.Rotation(math.radians(90.0), 3, 'Z'))

### Done with creating the mesh, simply link it into the scene so we can see it

### Finish up, write the bmesh into a new mesh
me = bpy.data.meshes.new("Mesh")
bm.to_mesh(me)
bm.free()

### Add the mesh to the scene
obj = bpy.data.objects.new("Object", me)
bpy.context.collection.objects.link(obj)

### Select and make active
bpy.context.view_layer.objects.active = obj
obj.select_set(True)
`\

bmesh.ops. smooth_vert ( bm , verts = [] , factor = 0 , mirror_clip_x = False , mirror_clip_y = False , mirror_clip_z = False , clip_dist = 0 , use_axis_x = False , use_axis_y = False , use_axis_z = False ) 

Vertex Smooth.

Smooths vertices by averaging their positions with neighboring vertices.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- verts (list[bmesh.types.BMVert]) – Input vertices.

- factor ( float ) – Smoothing factor.

- mirror_clip_x ( bool ) – Set vertices close to the x axis before the operation to 0.

- mirror_clip_y ( bool ) – Set vertices close to the y axis before the operation to 0.

- mirror_clip_z ( bool ) – Set vertices close to the z axis before the operation to 0.

- clip_dist ( float ) – Clipping threshold for the above three slots.

- use_axis_x ( bool ) – Smooth vertices along X axis.

- use_axis_y ( bool ) – Smooth vertices along Y axis.

- use_axis_z ( bool ) – Smooth vertices along Z axis.

bmesh.ops. smooth_laplacian_vert ( bm , verts = [] , lambda_factor = 0 , lambda_border = 0 , use_x = False , use_y = False , use_z = False , preserve_volume = False ) 

Vertex Smooth Laplacian.

Smooths vertices using Laplacian smoothing based on
Desbrun et al. Implicit Fairing of Irregular Meshes using Diffusion and Curvature Flow.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- verts (list[bmesh.types.BMVert]) – Input vertices.

- lambda_factor ( float ) – Lambda parameter.

- lambda_border ( float ) – Lambda param in border.

- use_x ( bool ) – Smooth object along X axis.

- use_y ( bool ) – Smooth object along Y axis.

- use_z ( bool ) – Smooth object along Z axis.

- preserve_volume ( bool ) – Apply volume preservation after smooth.

bmesh.ops. recalc_face_normals ( bm , faces = [] ) 

Right-Hand Faces.

Computes an "outside" normal for the specified input faces.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- faces (list[bmesh.types.BMFace]) – Input faces.

bmesh.ops. planar_faces ( bm , faces = [] , iterations = 0 , factor = 0 ) 

Planar Faces.

Iteratively flatten faces.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- faces (list[bmesh.types.BMFace]) – Input geometry.

- iterations ( int ) – Number of times to flatten faces (for when connected faces are used)

- factor ( float ) – Influence for making planar each iteration

Returns :

- geom :
Output slot, computed boundary geometry.

type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. region_extend ( bm , geom = [] , use_contract = False , use_faces = False , use_face_step = False ) 

Region Extend.

Used to implement the select more/less tools.
Puts geometry surrounding regions of geometry in geom into geom.out .

If use_faces is 0 then geom.out spits out verts and edges,
otherwise it spits out faces.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- geom (list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]) – Input geometry.

- use_contract ( bool ) – Find boundary inside the regions, not outside.

- use_faces ( bool ) – Extend from faces instead of edges.

- use_face_step ( bool ) – Step over connected faces.

Returns :

- geom :
Output slot, computed boundary geometry.

type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. rotate_edges ( bm , edges = [] , use_ccw = False ) 

Edge Rotate.

Rotates edges topologically. Also known as "spin edge" to some people.
Simple example: [/] becomes [|] then [\\] .

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- edges (list[bmesh.types.BMEdge]) – Input edges.

- use_ccw ( bool ) – Turn edges counter-clockwise if true, else clockwise.

Returns :

- edges :
Newly spun edges.

type list[bmesh.types.BMEdge]

Return type :

dict[str, Any]

bmesh.ops. reverse_faces ( bm , faces = [] , flip_multires = False ) 

Reverse Faces.

Inverts the vertex sequence of faces.
This reverses the face normal direction.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- faces (list[bmesh.types.BMFace]) – Input faces.

- flip_multires ( bool ) – Maintain multi-res offset.

bmesh.ops. flip_quad_tessellation ( bm , faces = [] ) 

Flip Quad Tessellation

Flip the tessellation direction of the selected quads.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- faces (list[bmesh.types.BMFace]) – Input faces.

bmesh.ops. bisect_edges ( bm , edges = [] , cuts = 0 , edge_percents = {} ) 

Edge Bisect.

Divides input edges into segments (creating 2-valence verts).

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- edges (list[bmesh.types.BMEdge]) – Input edges.

- cuts ( int ) – Number of cuts.

- edge_percents (dict[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace, float]) – Undocumented.

Returns :

- geom_split :
Newly created vertices and edges.

type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. mirror ( bm , geom = [] , matrix = mathutils.Matrix.Identity(4) , merge_dist = 0 , axis = 'X' , mirror_u = False , mirror_v = False , mirror_udim = False , use_shapekey = False ) 

Mirror.

Copies geometry in reverse across an axis. Overlapping vertices are fused using
merge_dist . Original and mirrored vertex pairs join when they fall within the merge_dist threshold.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- geom (list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]) – Input geometry.

- matrix (mathutils.Matrix) – Matrix defining the mirror transformation.

- merge_dist ( float ) – Maximum distance for merging. does no merging if 0.

- axis ( Literal [ 'X' , 'Y' , 'Z' ] ) – The axis to use.

- mirror_u ( bool ) – Mirror UVs across the u axis.

- mirror_v ( bool ) – Mirror UVs across the v axis.

- mirror_udim ( bool ) – Mirror UVs in each tile.

- use_shapekey ( bool ) – Transform shape keys too.

Returns :

- geom :
Output geometry, mirrored.

type list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. find_doubles ( bm , verts = [] , keep_verts = [] , use_connected = False , dist = 0 ) 

Find Doubles.

Identifies which vertices should be merged together.
Returns a mapping suitable for the weld verts BMOP.

If keep_verts is used, vertices outside that set can only be merged
with vertices in that set.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- verts (list[bmesh.types.BMVert]) – Input vertices.

- keep_verts (list[bmesh.types.BMVert]) – List of verts to keep.

- use_connected ( bool ) – Limit the search for doubles by connected geometry.

- dist ( float ) – Maximum distance.

Returns :

- targetmap :

type dict[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace, bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. remove_doubles ( bm , verts = [] , use_connected = False , dist = 0 ) 

Remove Doubles.

Locates groups of vertices within a threshold distance and joins them,
using the weld verts BMOP.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- verts (list[bmesh.types.BMVert]) – Input verts.

- use_connected ( bool ) – Limit the search for doubles by connected geometry.

- dist ( float ) – Maximum distance.

bmesh.ops. collapse ( bm , edges = [] , uvs = False ) 

Collapse Connected.

Collapses connected vertices

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- edges (list[bmesh.types.BMEdge]) – Input edges.

- uvs ( bool ) – Also collapse UVs and such.

bmesh.ops. pointmerge_facedata ( bm , verts = [] , vert_snap = None ) 

Face-Data Point Merge.

Merge uv/vcols at a specific vertex.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- verts (list[bmesh.types.BMVert]) – Input vertices.

- vert_snap (bmesh.types.BMVert | None) – Snap vertex.

bmesh.ops. average_vert_facedata ( bm , verts = [] ) 

Average Vertices Face-vert Data.

Merge uv/vcols associated with the input vertices at
the bounding box center.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- verts (list[bmesh.types.BMVert]) – Input vertices.

bmesh.ops. pointmerge ( bm , verts = [] , merge_co = mathutils.Vector() ) 

Point Merge.

Merge verts together at a point.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- verts (list[bmesh.types.BMVert]) – Input vertices (all verts will be merged into the first).

- merge_co ( Sequence [ float ] ) – Position to merge at.

bmesh.ops. collapse_uvs ( bm , edges = [] ) 

Collapse Connected UVs.

Collapses connected UV vertices.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- edges (list[bmesh.types.BMEdge]) – Input edges.

bmesh.ops. weld_verts ( bm , targetmap = {} , use_centroid = False ) 

Weld Verts.

Fuses verts together (like remove doubles, merge, etc, which
use or will use this BMOP). You supply mappings from vertices to the vertices
they should merge with.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- targetmap (dict[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace, bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]) – Maps welded vertices to where they merge.

- use_centroid ( bool ) – Merge vertices to their centroid position,
otherwise use the position of the target vertex.

bmesh.ops. create_vert ( bm , co = mathutils.Vector() ) 

Make Vertex.

Creates a single vertex; this BMOP was necessary
for click-create-vertex.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- co ( Sequence [ float ] ) – The coordinate of the new vert.

Returns :

- vert :
The new vert.

type list[bmesh.types.BMVert]

Return type :

dict[str, Any]

bmesh.ops. join_triangles ( bm , faces = [] , cmp_seam = False , cmp_sharp = False , cmp_uvs = False , cmp_vcols = False , cmp_materials = False , angle_face_threshold = 0 , angle_shape_threshold = 0 , topology_influence = 0 , deselect_joined = False , merge_limit = 0 , neighbor_debug = 0 ) 

Join Triangles.

Intelligently merges triangles based on
angle thresholds and edge properties.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- faces (list[bmesh.types.BMFace]) – Input geometry.

- cmp_seam ( bool ) – Compare seam

- cmp_sharp ( bool ) – Compare sharp

- cmp_uvs ( bool ) – Compare UVs

- cmp_vcols ( bool ) – Compare VCols.

- cmp_materials ( bool ) – Compare materials.

- angle_face_threshold ( float ) – Undocumented.

- angle_shape_threshold ( float ) – Undocumented.

- topology_influence ( float ) – Undocumented.

- deselect_joined ( bool ) – Undocumented.

- merge_limit ( int ) – Undocumented.

- neighbor_debug ( int ) – Undocumented.

Returns :

- faces :
Joined faces.

type list[bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. contextual_create ( bm , geom = [] , mat_nr = 0 , use_smooth = False ) 

Contextual Create.

This operates like the F-key, creating
new faces from vertices, forms geometry from edge nets,
constructs wire edges, etc. It also merges faces.

Three verts become a triangle, four become a quad. Two
become a wire edge.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- geom (list[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace]) – Input geometry.

- mat_nr ( int ) – Material to use.

- use_smooth ( bool ) – Set smooth shading on newly created faces.

Returns :

- faces :
Newly-made face(s).

type list[bmesh.types.BMFace]

- edges :
Newly-made edge(s).

type list[bmesh.types.BMEdge]

Return type :

dict[str, Any]

bmesh.ops. bridge_loops ( bm , edges = [] , use_pairs = False , use_cyclic = False , use_merge = False , merge_factor = 0 , twist_offset = 0 ) 

Bridge edge loops with faces.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- edges (list[bmesh.types.BMEdge]) – Input edges.

- use_pairs ( bool ) – Undocumented.

- use_cyclic ( bool ) – Undocumented.

- use_merge ( bool ) – Merge rather than creating faces.

- merge_factor ( float ) – Merge factor.

- twist_offset ( int ) – Twist offset for closed loops.

Returns :

- faces :
New faces.

type list[bmesh.types.BMFace]

- edges :
New edges.

type list[bmesh.types.BMEdge]

Return type :

dict[str, Any]

bmesh.ops. grid_fill ( bm , edges = [] , mat_nr = 0 , use_smooth = False , use_interp_simple = False ) 

Grid Fill.

Create faces defined by 2 disconnected edge loops (which share edges).

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- edges (list[bmesh.types.BMEdge]) – Input edges.

- mat_nr ( int ) – Material to use.

- use_smooth ( bool ) – Smooth state to use.

- use_interp_simple ( bool ) – Use simple interpolation.

Returns :

- faces :
New faces.

type list[bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. holes_fill ( bm , edges = [] , sides = 0 ) 

Fill Holes.

Fill boundary edges with faces, copying surrounding custom-data.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- edges (list[bmesh.types.BMEdge]) – Input edges.

- sides ( int ) – Maximum number of sides for holes to fill (holes with more edges are skipped).

Returns :

- faces :
New faces.

type list[bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. face_attribute_fill ( bm , faces = [] , use_normals = False , use_data = False ) 

Face Attribute Fill.

Fill in faces with data from adjacent faces.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- faces (list[bmesh.types.BMFace]) – Input faces.

- use_normals ( bool ) – Copy face winding.

- use_data ( bool ) – Copy face data.

Returns :

- faces_fail :
Faces that could not be handled.

type list[bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. edgeloop_fill ( bm , edges = [] , mat_nr = 0 , use_smooth = False ) 

Edge Loop Fill.

Create faces defined by one or more non overlapping edge loops.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- edges (list[bmesh.types.BMEdge]) – Input edges.

- mat_nr ( int ) – Material to use.

- use_smooth ( bool ) – Smooth state to use.

Returns :

- faces :
New faces.

type list[bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. edgenet_fill ( bm , edges = [] , mat_nr = 0 , use_smooth = False , sides = 0 ) 

Edge Net Fill.

Create faces defined by enclosed edges.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- edges (list[bmesh.types.BMEdge]) – Input edges.

- mat_nr ( int ) – Material to use.

- use_smooth ( bool ) – Smooth state to use.

- sides ( int ) – Maximum number of sides for created faces.

Returns :

- faces :
New faces.

type list[bmesh.types.BMFace]

Return type :

dict[str, Any]

bmesh.ops. edgenet_prepare ( bm , edges = [] ) 

Edge-net Prepare.

Identifies several useful edge loop cases and modifies them so
they'll become a face when edgenet_fill is called. The cases covered are:

- One single loop; an edge is added to connect the ends

- Two loops; two edges are added to connect the endpoints (based on the
shortest distance between each endpoint).

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- edges (list[bmesh.types.BMEdge]) – Input edges.

Returns :

- edges :
New edges.

type list[bmesh.types.BMEdge]

Return type :

dict[str, Any]

bmesh.ops. rotate ( bm , cent = mathutils.Vector() , matrix = mathutils.Matrix.Identity(4) , verts = [] , space = mathutils.Matrix.Identity(4) , use_shapekey = False ) 

Rotate.

Rotate vertices around a center, using a 3x3 rotation matrix.

Parameters :

- bm (bmesh.types.BMesh) – The bmesh to operate on.

- cent ( Sequence [ float ] ) – Center of rotation.
