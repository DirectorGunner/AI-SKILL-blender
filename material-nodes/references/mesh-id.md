# Mesh Id, Meshlooptriangle Bpy Struct, Meshpolygon Bpy Struct, Metaball Id

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Mesh(ID); MeshLoopTriangle(bpy_struct); MeshPolygon(bpy_struct); MetaBall(ID).

## Mesh(ID)

### Mesh(ID)

### Mesh Data

You reach the mesh data in object mode; it is laid out for tight storage, and when you need more flexible mesh editing from Python, reach for bmesh instead.

Four primary arrays hold the geometry of a Blender mesh.

- Mesh.vertices (each a point located in space)

- Mesh.edges (each pointing at a pair of vertices)

- Mesh.loops (each pointing at one vertex plus one edge)

- Mesh.polygons: (each pointing at a span of loops)

A polygon points at a span within the loop array; because of this it holds neither vertices nor corner data such as UVs on its own, just references to the loops it spans.

Since Mesh.loops, Mesh.uv_layers and Mesh.vertex_colors share the same alignment, one set of polygon loop indices retrieves the UVs and vertex colors just as it retrieves the vertices.

To compare mesh API options see: NGons and Tessellation Faces

The script below walks each polygon and prints its vertices and UVs; it assumes the active object is a mesh that has UVs.

```text
import bpy

me = bpy.context.object.data
uv_layer = me.uv_layers.active.data

for poly in me.polygons:
print("Polygon index: {:d}, length: {:d}".format(poly.index, poly.loop_total))

# Range is used here to show how the polygons reference loops,
# for convenience 'poly.loop_indices' can be used instead.
for loop_index in range(poly.loop_start, poly.loop_start + poly.loop_total):
print(" Vertex: {:d}".format(me.loops[loop_index].vertex_index))
print(" UV: {!r}".format(uv_layer[loop_index].uv))
```

base classes — bpy_struct, ID

class bpy.types. Mesh ( ID )

A data-block that holds the geometric surfaces of a mesh

animation_data

This data-block's animation data (readonly)

Type :

AnimData

attributes

Geometry attributes (default None, readonly)

Type :

AttributeGroupMesh[Attribute]

auto_texspace

Adjust active object’s texture space automatically when transforming object (default True)

Type :

bool

color_attributes

Geometry color attributes (default None, readonly)

Type :

AttributeGroupMesh[Attribute]

corner_normals

Per-corner "slit" normal direction, shaped by vertex normals, sharp faces, sharp edges, and custom normals; may come back empty. (default None, readonly)

Type :

bpy_prop_collection[MeshNormalValue]

cycles

Cycles mesh settings (readonly)

Type :

CyclesMeshSettings

edges

Edges of the mesh (default None, readonly)

Type :

MeshEdges[MeshEdge]

has_custom_normals

True if there is custom normal data for this mesh (default False, readonly)

Type :

bool

is_editmode

True when used in editmode (default False, readonly)

Type :

bool

loop_triangle_polygons

The face index for each loop triangle (default None, readonly)

Type :

bpy_prop_collection[ReadOnlyInteger]

loop_triangles

Tessellation of mesh polygons into triangles (default None, readonly)

Type :

MeshLoopTriangles[MeshLoopTriangle]

loops

Loops of the mesh (face corners) (default None, readonly)

Type :

MeshLoops[MeshLoop]

materials

(default None, readonly)

Type :

IDMaterials[Material]

normals_domain

The attribute domain carrying enough detail to express the mesh's normals (default 'FACE' , readonly)

Type :

Literal[‘POINT’, ‘FACE’, ‘CORNER’]

polygon_normals

Each face's normal direction, set by its winding order and the placement of its vertices (default None, readonly)

Type :

bpy_prop_collection[MeshNormalValue]

polygons

Polygons of the mesh (default None, readonly)

Type :

MeshPolygons[MeshPolygon]

radial_symmetry

Count of mirrored regions arranged around a central axis (array of 3 items, in [1, 64], default (1, 1, 1))

Type :

bpy_prop_array[int]

remesh_mode

(default 'VOXEL' )

- VOXEL
Voxel – Use the voxel remesher.

- QUAD
Quad – Use the quad remesher.

Type :

Literal[‘VOXEL’, ‘QUAD’]

remesh_voxel_adaptivity

Cuts the final face count by thinning geometry where fine detail isn't required, which produces triangles. Any value above 0 turns off Fix Poles. (in [0, 1], default 0.0)

Type :

float

remesh_voxel_size

Object-space voxel size used when evaluating volume; smaller settings keep finer detail. (in [0, inf], default 0.1)

Type :

float

shape_keys

(readonly)

Type :

Key

skin_vertices

All skin vertices (default None, readonly)

Type :

bpy_prop_collection[MeshSkinVertexLayer]

texco_mesh

Derive texture coordinates from another mesh

Type :

Mesh

texspace_location

Texture space location (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

texspace_size

Texture space size (array of 3 items, in [-inf, inf], default (1.0, 1.0, 1.0))

Type :

mathutils.Vector

texture_mesh

Use another mesh for texture indices (vertex indices must be aligned)

Type :

Mesh

total_edge_sel

Selected edge count in editmode (in [0, inf], default 0, readonly)

Type :

int

total_face_sel

Selected face count in editmode (in [0, inf], default 0, readonly)

Type :

int

total_vert_sel

Selected vertex count in editmode (in [0, inf], default 0, readonly)

Type :

int

use_auto_texspace

Adjust active object’s texture space automatically when transforming object (default True)

Type :

bool

use_mirror_topology

Mirror by topology, for cases where the two halves of the mesh share matching, unique topology (default False)

Type :

bool

use_mirror_vertex_groups

While painting, mirror the left/right vertex groups; the symmetry settings decide which axis is used. (default True)

Type :

bool

use_mirror_x

Turn on X-axis symmetry (default False)

Type :

bool

use_mirror_y

Turn on Y-axis symmetry (default False)

Type :

bool

use_mirror_z

Turn on Z-axis symmetry (default False)

Type :

bool

use_paint_bone_selection

Select bones while painting (default True)

Type :

bool

use_paint_mask

Mask painting by face selection (default False)

Type :

bool

use_paint_mask_vertex

Mask painting by vertex selection (default False)

Type :

bool

use_remesh_fix_poles

Yields fewer poles together with cleaner topology flow (default False)

Type :

bool

use_remesh_preserve_attributes

Carry every attribute over onto the new mesh (default False)

Type :

bool

use_remesh_preserve_volume

Project the mesh so the original's volume and detail survive (default False)

Type :

bool

uv_layer_clone

The UV loop layer that serves as the cloning source

Type :

MeshUVLoopLayer

uv_layer_clone_index

Clone UV loop layer index (in [0, inf], default 0)

Type :

int

uv_layer_stencil

The UV loop layer that masks off the painted area

Type :

MeshUVLoopLayer

uv_layer_stencil_index

Mask UV loop layer index (in [0, inf], default 0)

Type :

int

uv_layers

All UV loop layers (default None, readonly)

Type :

UVLoopLayers[MeshUVLoopLayer]

vertex_colors

Legacy vertex color layers. Deprecated, use color attributes instead. (default None, readonly)

Type :

LoopColors[MeshLoopColorLayer]

vertex_normals

Each vertex's normal direction, taken as the average of the faces surrounding it (default None, readonly)

Type :

bpy_prop_collection[MeshNormalValue]

vertices

Vertices of the mesh (default None, readonly)

Type :

MeshVertices[MeshVertex]

edge_creases

Per-edge crease weights for the subdivision surface; these map onto the "crease_edge" attribute.

(readonly)

edge_keys

(readonly)

vertex_creases

Per-vertex crease weights for the subdivision surface; these map onto the "crease_vert" attribute.

(readonly)

vertex_paint_mask

Per-vertex mask weights used in sculpting and painting; these map onto the ".sculpt_mask" attribute.

(readonly)

transform ( matrix , * , shape_keys = False )

Apply a matrix to the mesh's vertices (Warning: a negative matrix flips the normals)

Parameters :

- matrix (mathutils.Matrix) – Matrix (multi-dimensional array of 4 * 4 items, in [-inf, inf])

- shape_keys ( bool ) – Transform Shape Keys (optional)

flip_normals ( )

Reverse the winding on every polygon (tessellation is cleared; custom normals aren't touched)

set_sharp_from_angle ( * , angle = 3.14159 )

Clear the "sharp_edge" attribute and repopulate it from the angle between faces meeting at manifold edges

Parameters :

angle ( float ) – Angle, Angle between faces beyond which edges are marked sharp (in [0, 3.14159], optional)

split_faces ( )

Split faces based on the edge angle

calc_tangents ( * , uvmap = '' )

Work out the tangents and bitangent signs so that, paired with the custom normals, you have a full tangent space for normal mapping (any missing custom normals get computed too)

Parameters :

uvmap ( str ) – Name of the UV map to use for tangent space computation (optional, never None)

free_tangents ( )

Free tangents

calc_loop_triangles ( )

Build the loop-triangle tessellation (works in editmode as well)

calc_smooth_groups ( * , use_bitflags = False , use_boundary_vertices_for_bitflags = False )

Derive smooth groups out of the sharp edges

Parameters :

- use_bitflags ( bool ) – Produce bitflags groups instead of simple numeric values (optional)

- use_boundary_vertices_for_bitflags ( bool ) – Also consider different smoothgroups sharing only vertices (but without any common edge) as neighbors, preventing them from sharing the same bitflag value. Only effective when use_bitflags is set. WARNING: Will overflow (run out of available bits) easily with some types of topology, e.g. large fans of sharp edges (optional)

Returns :

poly_groups , Smooth Groups, bpy_prop_array[int]

groups , Total number of groups, int

Return type :

tuple[bpy_prop_array[int], int]

normals_split_custom_set ( normals )

Assign this mesh's custom normals (pass zero-vectors where you want the automatic ones kept)

Parameters :

normals ( Sequence [ float ] ) – Normals (multi-dimensional array of 1 * 3 items, in [-1, 1])

normals_split_custom_set_from_vertices ( normals )

Assign this mesh's custom normals from the vertices' normals (pass zero-vectors where you want the automatic ones kept)

Parameters :

normals ( Sequence [ float ] ) – Normals (multi-dimensional array of 1 * 3 items, in [-1, 1])

update ( * , calc_edges = False , calc_edges_loose = False )

update

Parameters :

- calc_edges ( bool ) – Calculate Edges, Force recalculation of edges (optional)

- calc_edges_loose ( bool ) – Calculate Loose Edges, Calculate the loose state of each edge (optional)

update_gpu_tag ( )

update_gpu_tag

unit_test_compare ( * , mesh = None , threshold = 7.1526e-06 )

unit_test_compare

Parameters :

- mesh (Mesh) – Mesh to compare to (optional)

- threshold ( float ) – Threshold, Comparison tolerance threshold (in [0, inf], optional)

Returns :

Return value, String description of result of comparison (never None)

Return type :

str

clear_geometry ( )

Strip every bit of geometry from the mesh. Shape keys and materials are left untouched by this.

validate ( * , verbose = False , clean_customdata = True )

Check the geometry; returns True if any invalid geometry on the mesh was fixed up or stripped out

Parameters :

- verbose ( bool ) – Verbose, Output information about the errors found (optional)

- clean_customdata ( bool ) – Clean Custom Data, Deprecated, has no effect (optional)

Returns :

Result

Return type :

bool

validate_material_indices ( )

Check the polygons' material indices; returns True if any invalid index on the mesh was reset (to the default of 0)

Returns :

Result

Return type :

bool

count_selected_items ( )

Return the number of selected items (vert, edge, face)

Returns :

Result, (array of 3 items, in [0, inf])

Return type :

bpy_prop_array[int]

edge_creases_ensure ( )

edge_creases_remove ( )

from_pydata ( vertices , edges , faces , shade_flat = True )

Build a mesh out of vertex, edge, and face lists.
This is the stopgap until a nicer geometry-creation path exists.

Parameters :

- vertices ( Iterable [ Sequence [ float ] ] ) – one float triplet per point, holding its (X, Y, Z)
eg: [(0.0, 1.0, 0.5), …].

- edges ( Iterable [ Sequence [ int ] ] ) – int pairs, where each pair holds two indices back into the
vertices argument. eg: [(1, 2), …]

Hand in an empty iterable and the edges get worked out from the polygons instead.

- faces ( Iterable [ Sequence [ int ] ] ) – an iterator over faces, where each face holds three or more indices back into
the vertices argument. eg: [(5, 6, 8, 9), (1, 2, 3), …]

Warning

Invalid mesh data
(out of range indices, edges with matching indices,
2 sided faces… etc) are not prevented.
If the data used for mesh creation isn’t known to be valid,
run Mesh.validate after this function.

shade_flat ( )

Display and render faces flat off their face normals, turning the "sharp_face" attribute on for every face

shade_smooth ( )

Display and render faces smoothly off interpolated vertex normals, dropping the "sharp_face" attribute

vertex_creases_ensure ( )

vertex_creases_remove ( )

vertex_paint_mask_ensure ( )

vertex_paint_mask_remove ( )

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| bpy.context.mesh BlendData.meshes BlendDataMeshes.new BlendDataMeshes.new_from_object BlendDataMeshes.remove | Mesh.texco_mesh Mesh.texture_mesh Mesh.unit_test_compare Object.to_mesh |

## MeshLoopTriangle(bpy_struct)

### MeshLoopTriangle(bpy_struct)

base class — bpy_struct

class bpy.types. MeshLoopTriangle ( bpy_struct )

Tessellated triangle in a Mesh data-block

area

Area of this triangle (in [0, inf], default 0.0, readonly)

Type :

float

index

Index of this loop triangle (in [0, inf], default 0, readonly)

Type :

int

loops

Indices of mesh loops that make up the triangle (array of 3 items, in [0, inf], default (0, 0, 0), readonly)

Type :

bpy_prop_array[int]

material_index

Material slot index of this triangle (in [0, inf], default 0, readonly)

Type :

int

normal

Local space unit length normal vector for this triangle (array of 3 items, in [-1, 1], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

polygon_index

Index of mesh face that the triangle is a part of (in [0, inf], default 0, readonly)

Type :

int

split_normals

Local space unit length custom normal vectors of the face corners of this triangle (multi-dimensional array of 3 * 3 items, in [-1, 1], default ((0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0)), readonly)

Type :

bpy_prop_array[float]

use_smooth

(default False, readonly)

Type :

bool

vertices

Indices of triangle vertices (array of 3 items, in [0, inf], default (0, 0, 0), readonly)

Type :

bpy_prop_array[int]

center

The midpoint of the face.

(readonly)

edge_keys

(readonly)

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Mesh.loop_triangles | |

## MeshPolygon(bpy_struct)

### MeshPolygon(bpy_struct)

base class — bpy_struct

class bpy.types. MeshPolygon ( bpy_struct )

Polygon in a Mesh data-block

area

Read only area of this face (in [0, inf], default 0.0, readonly)

Type :

float

center

Center of this face (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

hide

(default False)

Type :

bool

index

Index of this face (in [0, inf], default 0, readonly)

Type :

int

loop_start

Index of the first loop of this face (in [0, inf], default 0)

Type :

int

loop_total

Number of loops used by this face (in [0, inf], default 0, readonly)

Type :

int

material_index

Material slot index of this face (in [0, inf], default 0)

Type :

int

normal

Local space unit length normal vector for this face (array of 3 items, in [-1, 1], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

select

(default False)

Type :

bool

use_smooth

(default False)

Type :

bool

vertices

Vertex indices (array of 3 items, in [0, inf], default (0, 0, 0))

Type :

bpy_prop_array[int]

edge_keys

(readonly)

loop_indices

(readonly)

flip ( )

Invert winding of this face (flip its normal)

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Mesh.polygons | |

## MetaBall(ID)

### MetaBall(ID)

base classes — bpy_struct, ID

class bpy.types. MetaBall ( ID )

A data-block whose blobby surfaces make up a metaball

animation_data

This data-block's animation data (readonly)

Type :

AnimData

cycles

Cycles mesh settings (readonly)

Type :

CyclesMeshSettings

elements

Metaball elements (default None, readonly)

Type :

MetaBallElements[MetaElement]

is_editmode

True when used in editmode (default False, readonly)

Type :

bool

materials

(default None, readonly)

Type :

IDMaterials[Material]

render_resolution

Polygonization resolution in rendering (in [0.005, 10000], default 0.2)

Type :

float

resolution

Polygonization resolution in the 3D viewport (in [0.005, 10000], default 0.4)

Type :

float

texspace_location

Texture space location (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

texspace_size

Texture space size (array of 3 items, in [-inf, inf], default (1.0, 1.0, 1.0))

Type :

mathutils.Vector

threshold

Influence of metaball elements (in [0, 5], default 0.6)

Type :

float

update_method

Metaball edit update behavior (default '`UPDATE_ALWAYS`' )

- `UPDATE_ALWAYS`
Always – While editing, update metaball always.

- HALFRES
Half – While editing, update metaball in half resolution.

- FAST
Fast – While editing, update metaball without polygonization.

- NEVER
Never – While editing, don’t update metaball at all.

Type :

Literal[‘`UPDATE_ALWAYS`’, ‘HALFRES’, ‘FAST’, ‘NEVER’]

use_auto_texspace

Adjust active object’s texture space automatically when transforming object (default True)

Type :

bool

transform ( matrix )

Transform metaball elements by a matrix

Parameters :

matrix (mathutils.Matrix) – Matrix (multi-dimensional array of 4 * 4 items, in [-inf, inf])

update_gpu_tag ( )

update_gpu_tag

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| bpy.context.meta_ball BlendData.metaballs | BlendDataMetaBalls.new BlendDataMetaBalls.remove |

## See also

- [Bpy Struct](bpy-struct.md)
