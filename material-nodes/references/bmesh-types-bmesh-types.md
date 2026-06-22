# Bmesh Types Bmesh Types (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### BMesh Types (bmesh.types)
### Base Mesh Type
class bmesh.types. BMesh
Blender's core BMesh data structure.

calc_loop_triangles ( )
Computes a triangle tessellation from quads/ngons.
Returns: The triangulated faces.
Return type: list[tuple[bmesh.types.BMLoop, bmesh.types.BMLoop, bmesh.types.BMLoop]]

calc_volume ( * , signed = False )
Computes the mesh volume from the face normals.
Parameters: signed ( bool ) – when signed is true, negative values may be returned.
Returns: The volume of the mesh.
Return type: float

clear ( )
Clears all mesh data.

copy ( )
Returns: A copy of this BMesh.
Return type: bmesh.types.BMesh

free ( )
Explicitly frees the BMesh data from memory, so any further access raises exceptions.
Note: the BMesh is freed automatically, usually when the script finishes executing; but since that moment is sometimes hard to predict, freeing the data explicitly can be useful.

from_mesh ( mesh , * , face_normals = True , vertex_normals = True , use_shape_key = False , shape_key_index = 0 )
Initializes this bmesh from an existing mesh data-block.
Parameters:
- mesh (bpy.types.Mesh) – The mesh data to load.
- face_normals ( bool ) – Calculate face normals.
- vertex_normals ( bool ) – Calculate vertex normals.
- use_shape_key ( bool ) – Use the locations from a shape key.
- shape_key_index ( int ) – The shape key index to use.
Note: call it multiple times to join multiple meshes. Custom-data layers are only copied from mesh on initialization; later calls copy custom-data to matching layers, and layers missing on the target mesh aren't added.

from_object ( object , depsgraph , * , cage = False , face_normals = True , vertex_normals = True )
Initializes this bmesh from an existing object data-block (only meshes are currently supported).
Parameters:
- object (bpy.types.Object) – The object data to load.
- depsgraph (bpy.types.Depsgraph) – The dependency graph for evaluated data.
- cage ( bool ) – Get the mesh as a deformed cage.
- face_normals ( bool ) – Calculate face normals.
- vertex_normals ( bool ) – Calculate vertex normals.

normal_update ( )
Updates the normals of the mesh's faces and verts.
Note: a vertex whose is_wire is True gets a zero-vector normal.

select_flush ( select )
Flushes selection from vertices, regardless of the current selection mode.
Parameters: select ( bool ) – flush selection or de-selected elements.

select_flush_mode ( * , flush_down = False )
Flushes selection according to the current mode, bmesh.types.BMesh.select_mode.
Parameters: flush_down ( bool ) – Flush selection down from faces to edges & verts or from edges to verts. This option is ignored when vertex selection mode is enabled.

to_mesh ( mesh )
Writes this BMesh's data into an existing Mesh data-block.
Parameters: mesh (bpy.types.Mesh) – The mesh data to write into.

transform ( matrix , * , filter = None )
Transforms the mesh, optionally filtering to flagged data only.
Parameters:
- matrix (mathutils.Matrix) – 4x4 transform matrix.
- filter ( set [ Literal [ 'SELECT' , 'HIDE' , 'SEAM' , 'SMOOTH' , 'TAG' ] ] | None ) – Flag to filter vertices.

uv_select_flush ( select )
Flushes selection from UV vertices to edges & faces, regardless of the selection mode.
Parameters: select ( bool ) – Flush selection or de-selected elements.
Note: this doesn't flush the selection to the mesh; typically call bmesh.types.BMesh.uv_select_sync_to_mesh() afterwards.

uv_select_flush_mode ( * , flush_down = False )
Flushes UV selection according to the current mode, bmesh.types.BMesh.select_mode.
Parameters: flush_down ( bool ) – Flush selection down from faces to edges & verts or from edges to verts. This option is ignored when vertex selection mode is enabled.

uv_select_flush_shared ( select )
Flushes selection from UV vertices to contiguous UVs, regardless of the selection mode.
Parameters: select ( bool ) – Flush selection or de-selected elements.
Note: this doesn't flush the selection to the mesh; typically call bmesh.types.BMesh.uv_select_sync_to_mesh() afterwards.

uv_select_foreach_set ( select , / , * , loop_verts = () , loop_edges = () , faces = () , sticky_select_mode = '`SHARED_LOCATION`' )
Sets the UV selection state for loop-vertices, loop-edges & faces — a close equivalent to selecting in the UV editor.
Parameters:
- select ( bool ) – The selection state to set.
- loop_verts (Iterable[bmesh.types.BMLoop]) – Loop verts to operate on.
- loop_edges (Iterable[bmesh.types.BMLoop]) – Loop edges to operate on.
- faces (Iterable[bmesh.types.BMFace]) – Faces to operate on.
- sticky_select_mode (Literal['`SHARED_LOCATION`', 'DISABLED', '`SHARED_VERTEX`']) – See bpy.types.ToolSettings.uv_sticky_select_mode, which may be passed in directly.
Note: this function is selection-mode independent; typically call bmesh.types.BMesh.uv_select_flush_mode() afterwards. It also doesn't flush the selection to the mesh; typically call bmesh.types.BMesh.uv_select_sync_to_mesh() afterwards.

uv_select_foreach_set_from_mesh ( select , / , * , verts = () , edges = () , faces = () , sticky_select_mode = '`SHARED_LOCATION`' )
Selects or de-selects mesh elements while updating the UV selection — an equivalent to selecting from the 3D viewport for operations that keep a synchronized UV selection.
Parameters:
- select ( bool ) – The selection state to set.
- verts (Iterable[bmesh.types.BMVert]) – Verts to operate on.
- edges (Iterable[bmesh.types.BMEdge]) – Edges to operate on.
- faces (Iterable[bmesh.types.BMFace]) – Faces to operate on.
- sticky_select_mode (Literal['`SHARED_LOCATION`', 'DISABLED', '`SHARED_VERTEX`']) – See bpy.types.ToolSettings.uv_sticky_select_mode, which may be passed in directly.

uv_select_sync_from_mesh ( * , sticky_select_mode = '`SHARED_LOCATION`' )
Syncs selection from the mesh to UVs.
Parameters: sticky_select_mode (Literal['`SHARED_LOCATION`', 'DISABLED', '`SHARED_VERTEX`']) – Behavior when flushing from the mesh to the UV selection (bpy.types.ToolSettings.uv_sticky_select_mode, which may be passed in directly); use this only when preparing to create a UV selection.
Note: this doesn't flush the selection to the mesh; typically call bmesh.types.BMesh.uv_select_sync_to_mesh() afterwards.

uv_select_sync_to_mesh ( )
Syncs selection from UVs to the mesh.

edges
The mesh's edge sequence (read-only).
Type: bmesh.types.BMEdgeSeq

faces
The mesh's face sequence (read-only).
Type: bmesh.types.BMFaceSeq

is_valid
True when this element is valid (hasn't been freed or removed).
Type: bool

is_wrapped
True when this mesh is owned by Blender (typically the editmode BMesh).
Type: bool

loops
The mesh's loops (read-only).
Type: bmesh.types.BMLoopSeq
Note: loops must be accessed via faces; this is exposed only for layer access.

select_history
A sequence of selected items (the last is shown as active).
Type: bmesh.types.BMEditSelSeq

select_mode
The selection mode; it can't be assigned an empty set.
Type: set[Literal['VERT', 'EDGE', 'FACE']]

uv_select_sync_valid
True when the UV selection has been synchronized. Setting it to False makes the UV selection be ignored; setting it to True is supported, but it's up to the script author to ensure a correct selection state first.
Type: bool

verts
The mesh's vert sequence (read-only).
Type: bmesh.types.BMVertSeq

### Mesh Elements
class bmesh.types. BMVert
The BMesh vertex type.

calc_edge_angle ( fallback = None )
Returns the angle between this vert's two connected edges.
Parameters: fallback ( Any ) – return this when the vert doesn't have 2 edges (instead of raising a ValueError).
Returns: Angle between edges in radians.
Return type: float

calc_shell_factor ( )
Returns a multiplier based on the vertex's sharpness — a flat surface gives 1.0, and higher values mean sharper edges — used to maintain shell thickness when offsetting verts along their normals.
Returns: offset multiplier
Return type: float

copy_from ( other )
Copies values from another element of matching type.
Parameters: other ( Self ) – Another element of the same type to copy from.

copy_from_face_interp ( face )
Interpolates the customdata from a face onto this vert (the vert should overlap the face).
Parameters: face (bmesh.types.BMFace) – The face to interpolate data from.

copy_from_vert_interp ( vert_pair , fac )
Interpolates the customdata onto this vert from between two other verts.
Parameters:
- vert_pair (Sequence[bmesh.types.BMVert]) – The verts between which to interpolate data from.
- fac ( float ) – The interpolation factor.

hide_set ( hide )
Sets the hide state. Unlike the hide attribute, this also updates the selection and hide state of associated geometry.
Parameters: hide ( bool ) – Hidden or visible.

normal_update ( )
Updates the vertex normal; it doesn't update the normals of adjoining faces.
Note: the vertex normal will be a zero vector if the vertex's is_wire is True.

select_set ( select )
Sets the selection. Unlike the select attribute, this also updates the selection state of associated geometry.
Parameters: select ( bool ) – Select or de-select.
Note: this flushes selection down (e.g. selecting a face also selects its edges and vertices) but not up (e.g. de-selecting a vertex won't de-select faces that use it); flushing is typically still needed before finishing with a mesh.

co
The coordinates for this vertex, as a 3D wrapped vector.
Type: mathutils.Vector

hide
Hidden state of this element.
Type: bool

index
Index of this element.
Type: int
Note: this value isn't necessarily valid — while editing the mesh it can become dirty — and you can assign any number to it for a script's own logic. To ensure it's up to date, see bmesh.types.BMElemSeq.index_update().

is_boundary
True when this vertex is connected to boundary edges (read-only).
Type: bool

is_manifold
True when this vertex is manifold (read-only).
Type: bool

is_valid
True when this element is valid (hasn't been freed or removed).
Type: bool

is_wire
True when this vertex is not connected to any faces (read-only).
Type: bool

link_edges
Edges connected to this vertex (read-only).
Type: bmesh.types.BMElemSeq[bmesh.types.BMEdge]

link_faces
Faces connected to this vertex (read-only).
Type: bmesh.types.BMElemSeq[bmesh.types.BMFace]

link_loops
Loops that use this vertex (read-only).
Type: bmesh.types.BMElemSeq[bmesh.types.BMLoop]

normal
The normal for this vertex, as a 3D wrapped vector.
Type: mathutils.Vector

select
Selected state of this element.
Type: bool

tag
A generic attribute scripts can use for their own logic.
Type: bool

class bmesh.types. BMEdge
The BMesh edge connecting 2 verts.

calc_face_angle ( fallback = None )
Returns the angle between this edge's two connected faces.
Parameters: fallback ( Any ) – return this when the edge doesn't have 2 faces (instead of raising a ValueError).
Returns: The angle between 2 connected faces in radians.
Return type: float

calc_face_angle_signed ( fallback = None )
Returns the signed angle between this edge's two connected faces.
Parameters: fallback ( Any ) – return this when the edge doesn't have 2 faces (instead of raising a ValueError).
Returns: The angle between 2 connected faces in radians (negative for a concave join).
Return type: float

calc_length ( )
Returns the length of the edge.
Returns: The length between both verts.
Return type: float

calc_tangent ( loop )
Returns the tangent at this edge relative to a face (pointing inward into the face), using the face normal for the calculation.
Parameters: loop (bmesh.types.BMLoop) – The loop used for tangent calculation.
Returns: a normalized vector.
Return type: mathutils.Vector

copy_from ( other )
Copies values from another element of matching type.
Parameters: other ( Self ) – Another element of the same type to copy from.

hide_set ( hide )
Sets the hide state. Unlike the hide attribute, this also updates the selection and hide state of associated geometry.
Parameters: hide ( bool ) – Hidden or visible.

normal_update ( )
Updates the normals of all connected faces and the edge's verts.
Note: an edge vertex's normal will be a zero vector if the vertex's is_wire is True.

other_vert ( vert )
Returns the other vertex on this edge, or None if the vertex isn't used by this edge.

Parameters: vert (bmesh.types.BMVert) – a vert in this edge.
Returns: The edge's other vert.
Return type: bmesh.types.BMVert | None

select_set ( select )
Sets the selection. Unlike the select attribute, this also updates the selection state of associated geometry.
Parameters: select ( bool ) – Select or de-select.
Note: this flushes selection down (e.g. selecting a face also selects its edges and vertices) but not up (e.g. de-selecting a vertex won't de-select faces that use it); flushing is typically still needed before finishing with a mesh.

hide
Hidden state of this element.
Type: bool

index
Index of this element.
Type: int
Note: this value isn't necessarily valid — while editing the mesh it can become dirty — and you can assign any number to it for a script's own logic. To ensure it's up to date, see bmesh.types.BMElemSeq.index_update().

is_boundary
True when this edge is at the boundary of a face (read-only).
Type: bool

is_contiguous
True when this edge is manifold, between two faces with the same winding (read-only).
Type: bool

is_convex
True when this edge joins two convex faces, depends on a valid face normal (read-only).
Type: bool

is_manifold
True when this edge is manifold (read-only).
Type: bool

is_valid
True when this element is valid (hasn't been freed or removed).
Type: bool

is_wire
True when this edge is not connected to any faces (read-only).
Type: bool

link_faces
Faces connected to this edge (read-only).
Type: bmesh.types.BMElemSeq[bmesh.types.BMFace]

link_loops
Loops connected to this edge (read-only).
Type: bmesh.types.BMElemSeq[bmesh.types.BMLoop]

seam
Seam for UV unwrapping.
Type: bool

select
Selected state of this element.
Type: bool

smooth
Smooth state of this element.
Type: bool

tag
A generic attribute scripts can use for their own logic.
Type: bool

verts
Verts this edge uses (always 2) (read-only).
Type: bmesh.types.BMElemSeq[bmesh.types.BMVert]

class bmesh.types. BMFace
The BMesh face with 3 or more sides.

calc_area ( )
Returns the area of the face.
Returns: The area of the face.
Return type: float

calc_center_bounds ( )
Returns the bounds center of the face.
Returns: a 3D vector.
Return type: mathutils.Vector

calc_center_median ( )
Returns the median center of the face.
Returns: a 3D vector.
Return type: mathutils.Vector

calc_center_median_weighted ( )
Returns the median center of the face weighted by edge lengths.
Returns: a 3D vector.
Return type: mathutils.Vector

calc_perimeter ( )
Returns the perimeter of the face.
Returns: The perimeter of the face.
Return type: float

calc_tangent_edge ( )
Returns the face tangent based on the longest edge.
Returns: a normalized vector.
Return type: mathutils.Vector

calc_tangent_edge_diagonal ( )
Returns the face tangent based on the edge farthest from any vertex.
Returns: a normalized vector.
Return type: mathutils.Vector

calc_tangent_edge_pair ( )
Returns the face tangent based on the two longest disconnected edges.
- Tris: Use the edge pair with the most similar lengths.
- Quads: Use the longest edge pair.
- NGons: Use the two longest disconnected edges.
Returns: a normalized vector.
Return type: mathutils.Vector

calc_tangent_vert_diagonal ( )
Returns the face tangent based on the two most distant vertices.
Returns: a normalized vector.
Return type: mathutils.Vector

copy ( * , verts = True , edges = True )
Makes a copy of this face.
Parameters:
- verts ( bool ) – When set, the faces verts will be duplicated too.
- edges ( bool ) – When set, the faces edges will be duplicated too.
Returns: The newly created face.
Return type: bmesh.types.BMFace

copy_from ( other )
Copies values from another element of matching type.
Parameters: other ( Self ) – Another element of the same type to copy from.

copy_from_face_interp ( face , vert = True )
Interpolates the customdata from another face onto this one (the faces should overlap).
Parameters:
- face (bmesh.types.BMFace) – The face to interpolate data from.
- vert ( bool ) – When True, also copy vertex data.

hide_set ( hide )
Sets the hide state. Unlike the hide attribute, this also updates the selection and hide state of associated geometry.
Parameters: hide ( bool ) – Hidden or visible.

normal_flip ( )
Reverses the winding of a face, which flips its normal.

normal_update ( )
Updates the face normal from the positions of the face verts; it doesn't update the normals of the face verts.

select_set ( select )
Sets the selection. Unlike the select attribute, this also updates the selection state of associated geometry.
Parameters: select ( bool ) – Select or de-select.
Note: this flushes selection down (e.g. selecting a face also selects its edges and vertices) but not up (e.g. de-selecting a vertex won't de-select faces that use it); flushing is typically still needed before finishing with a mesh.

uv_select_set ( select )
Sets the UV face selection state.
Parameters: select ( bool ) – Select or de-select.
Note: this flushes selection down (selecting a face also selects its edges and vertices) but not up; flushing with bmesh.types.BMesh.uv_select_flush_mode() is still needed before finishing with a mesh.

edges
Edges of this face (read-only).
Type: bmesh.types.BMElemSeq[bmesh.types.BMEdge]

hide
Hidden state of this element.
Type: bool

index
Index of this element.
Type: int
Note: this value isn't necessarily valid — while editing the mesh it can become dirty — and you can assign any number to it for a script's own logic. To ensure it's up to date, see bmesh.types.BMElemSeq.index_update().

is_valid
True when this element is valid (hasn't been freed or removed).
Type: bool

loops
Loops of this face (read-only).
Type: bmesh.types.BMElemSeq[bmesh.types.BMLoop]

material_index
The face's material index.
Type: int

normal

The normal for this face, as a 3D wrapped vector.
Type: mathutils.Vector

select
Selected state of this element.
Type: bool

smooth
Smooth state of this element.
Type: bool

tag
A generic attribute scripts can use for their own logic.
Type: bool

uv_select
UV selected state of this element.
Type: bool

verts
Verts of this face (read-only).
Type: bmesh.types.BMElemSeq[bmesh.types.BMVert]

class bmesh.types. BMLoop
Normally accessed from bmesh.types.BMFace.loops, where each face loop represents a corner of the face.

calc_angle ( )
Returns the angle at this loop's corner of the face, computed so that sharper corners give lower angles.
Returns: The angle in radians.
Return type: float

calc_normal ( )
Returns the normal at this loop's corner of the face, falling back to the face normal for straight lines.
Returns: a normalized vector.
Return type: mathutils.Vector

calc_tangent ( )
Returns the tangent at this loop's corner of the face (pointing inward into the face), falling back to the face normal for straight lines.
Returns: a normalized vector.
Return type: mathutils.Vector

copy_from ( other )
Copies values from another element of matching type.
Parameters: other ( Self ) – Another element of the same type to copy from.

copy_from_face_interp ( face , vert = True , multires = True )
Interpolates the customdata from a face onto this loop (the loop's vert should overlap the face).
Parameters:
- face (bmesh.types.BMFace) – The face to interpolate data from.
- vert ( bool ) – When enabled, interpolate the loop's vertex data (optional).
- multires ( bool ) – When enabled, interpolate the loop's multires data (optional).

uv_select_edge_set ( select )
Sets the UV edge selection state.
Parameters: select ( bool ) – Select or de-select.
Note: this flushes selection down (selecting an edge also selects its vertices) but not up (de-selecting a vertex won't de-select the edges & faces that use it); flushing with bmesh.types.BMesh.uv_select_flush_mode() is still needed before finishing with a mesh.

uv_select_vert_set ( select )
Sets the UV vertex selection state.
Parameters: select ( bool ) – Select or de-select.
Note: this doesn't flush selection, so selecting a vertex won't select the edges & faces that use it; flushing with bmesh.types.BMesh.uv_select_flush_mode() is still needed before finishing with a mesh.

edge
The loop's edge (between this loop and the next) (read-only).
Type: bmesh.types.BMEdge

face
The face this loop belongs to (read-only).
Type: bmesh.types.BMFace

index
Index of this element.
Type: int
Note: this value isn't necessarily valid — while editing the mesh it can become dirty — and you can assign any number to it for a script's own logic. To ensure it's up to date, see bmesh.types.BMElemSeq.index_update().

is_convex
True when this loop is at the convex corner of a face, depends on a valid face normal (read-only).
Type: bool

is_valid
True when this element is valid (hasn't been freed or removed).
Type: bool

link_loop_next
The next face corner (read-only).
Type: bmesh.types.BMLoop

link_loop_prev
The previous face corner (read-only).
Type: bmesh.types.BMLoop

link_loop_radial_next
The next loop around the edge (read-only).
Type: bmesh.types.BMLoop

link_loop_radial_prev
The previous loop around the edge (read-only).
Type: bmesh.types.BMLoop

link_loops
Loops connected to this loop (read-only).
Type: bmesh.types.BMElemSeq[bmesh.types.BMLoop]

tag
A generic attribute scripts can use for their own logic.
Type: bool

uv_select_edge
UV edge selected state of this loop.
Type: bool

uv_select_vert
UV vertex selected state of this loop.
Type: bool

vert
The loop's vertex (read-only).
Type: bmesh.types.BMVert

### Sequence Accessors
class bmesh.types. BMElemSeq
A general sequence type for accessing any sequence of bmesh.types.BMVert, bmesh.types.BMEdge, bmesh.types.BMFace, bmesh.types.BMLoop. When accessed via bmesh.types.BMesh.verts, bmesh.types.BMesh.edges, bmesh.types.BMesh.faces there are also functions to create/remove items.

index_update ( )
Initializes the index values of this sequence — the equivalent of looping over all elements and assigning their index values:
```text
for index, ele in enumerate(sequence):
    ele.index = index
```
Note: running this on sequences other than bmesh.types.BMesh.verts, bmesh.types.BMesh.edges, bmesh.types.BMesh.faces works but won't give each element a valid index — instead its order in the sequence is set.

class bmesh.types. BMVertSeq

ensure_lookup_table ( )
Ensures the internal data needed for int subscript access is initialized for verts/edges/faces, e.g. bm.verts[index]. Call it again after adding/removing data in this sequence.

index_update ( )
Initializes the index values of this sequence — the equivalent of looping over all elements and assigning their index values:
```text
for index, ele in enumerate(sequence):
    ele.index = index
```
Note: running this on sequences other than bmesh.types.BMesh.verts, bmesh.types.BMesh.edges, bmesh.types.BMesh.faces works but won't give each element a valid index — instead its order in the sequence is set.

new ( co = (0.0, 0.0, 0.0) , source = None )
Creates a new vertex.
Parameters:
- co ( tuple [ float , float , float ] | Sequence [ float ] ) – The initial location of the vertex (optional argument).
- source (bmesh.types.BMVert | None) – Existing vert to initialize settings.
Returns: The newly created vertex.
Return type: bmesh.types.BMVert

remove ( vert )
Removes a vert.
Parameters: vert (bmesh.types.BMVert) – The vert to remove.

sort ( * , key = None , reverse = False )
Sorts the elements of this sequence, using an optional custom sort key. Element indices aren't changed; use bmesh.types.BMElemSeq.index_update() for that.
Parameters:
- key (Callable[[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace], int] | None) – The key that sets the ordering of the elements.
- reverse ( bool ) – Reverse the order of the elements
Note: when the 'key' argument isn't provided, the elements are reordered following their current index value — so you can set indices manually before calling this method.
