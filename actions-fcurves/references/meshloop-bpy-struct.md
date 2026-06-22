# Meshloop Bpy Struct, Meshloopcolor Bpy Struct, Meshloops Bpy Prop Collection, Meshlooptriangles Bpy Prop Collection ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: MeshLoop(bpy_struct); MeshLoopColor(bpy_struct); MeshLoops(bpy_prop_collection); MeshLoopTriangles(bpy_prop_collection); MeshNormalValue(bpy_struct); MeshPolygons(bpy_prop_collection); MeshSkinVertex(bpy_struct); MeshSkinVertexLayer(bpy_struct); MeshStatVis(bpy_struct); MeshUVLoop(bpy_struct); MeshVertex(bpy_struct); MeshVertices(bpy_prop_collection); MetaBallElements(bpy_prop_collection).

## MeshLoop(bpy_struct)

### MeshLoop(bpy_struct)

base class — bpy_struct

class bpy.types. MeshLoop ( bpy_struct )

Loop in a Mesh data-block

bitangent

Bitangent vector of this vertex for this face (must be computed beforehand using calc_tangents, use it only if really needed, slower access than bitangent_sign) (array of 3 items, in [-1, 1], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

bitangent_sign

Sign of the bitangent vector of this vertex for this face (must be computed beforehand using calc_tangents, bitangent = bitangent_sign * cross(normal, tangent)) (in [-1, 1], default 0.0, readonly)

Type :

float

edge_index

Edge index (in [0, inf], default 0)

Type :

int

index

Index of this loop (in [0, inf], default 0, readonly)

Type :

int

normal

The normal direction of the face corner, taking into account sharp faces, sharp edges, and custom normal data (array of 3 items, in [-1, 1], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

tangent

Local space unit length tangent vector of this vertex for this face (must be computed beforehand using calc_tangents) (array of 3 items, in [-1, 1], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

vertex_index

Vertex index (in [0, inf], default 0)

Type :

int

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

| Mesh.loops | |

## MeshLoopColor(bpy_struct)

### MeshLoopColor(bpy_struct)

base class — bpy_struct

class bpy.types. MeshLoopColor ( bpy_struct )

Vertex loop colors in a Mesh

color

Color in sRGB color space (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

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

| MeshLoopColorLayer.data | |

## MeshLoops(bpy_prop_collection)

### MeshLoops(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MeshLoops ( bpy_prop_collection )

Collection of mesh loops

add ( count )

add

Parameters :

count ( int ) – Count, Number of loops to add (in [0, inf])

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

| Mesh.loops | |

## MeshLoopTriangles(bpy_prop_collection)

### MeshLoopTriangles(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MeshLoopTriangles ( bpy_prop_collection )

Tessellation of mesh polygons into triangles

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

## MeshNormalValue(bpy_struct)

### MeshNormalValue(bpy_struct)

base class — bpy_struct

class bpy.types. MeshNormalValue ( bpy_struct )

Vector in a mesh normal array

vector

3D vector (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

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

| Mesh.corner_normals Mesh.polygon_normals | Mesh.vertex_normals |

## MeshPolygons(bpy_prop_collection)

### MeshPolygons(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MeshPolygons ( bpy_prop_collection )

Collection of mesh polygons

active

The active face for this mesh (in [-inf, inf], default 0)

Type :

int

add ( count )

add

Parameters :

count ( int ) – Count, Number of polygons to add (in [0, inf])

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

## MeshSkinVertex(bpy_struct)

### MeshSkinVertex(bpy_struct)

base class — bpy_struct

class bpy.types. MeshSkinVertex ( bpy_struct )

Per-vertex skin data for use with the Skin modifier

radius

Radius of the skin (array of 2 items, in [0, inf], default (0.0, 0.0))

Type :

bpy_prop_array[float]

use_loose

When a vertex has several neighboring edges, it gets hulled straight onto them (default False)

Type :

bool

use_root

Marks the vertex as a root for rotation calculations and armature generation; enabling this flag leaves other roots in the same mesh island untouched (default False)

Type :

bool

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

| MeshSkinVertexLayer.data | |

## MeshSkinVertexLayer(bpy_struct)

### MeshSkinVertexLayer(bpy_struct)

base class — bpy_struct

class bpy.types. MeshSkinVertexLayer ( bpy_struct )

Per-vertex skin data for use with the Skin modifier

data

(default None, readonly)

Type :

bpy_prop_collection[MeshSkinVertex]

name

Name of skin layer (default "", never None)

Type :

str

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

| Mesh.skin_vertices | |

## MeshStatVis(bpy_struct)

### MeshStatVis(bpy_struct)

base class — bpy_struct

class bpy.types. MeshStatVis ( bpy_struct )

distort_max

Maximum angle to display (in [0, 3.14159], default 0.785398)

Type :

float

distort_min

Minimum angle to display (in [0, 3.14159], default 0.0872665)

Type :

float

overhang_axis

(default '`NEG_Z`' )

Type :

Literal[Object Axis Items]

overhang_max

Maximum angle to display (in [0, 3.14159], default 0.785398)

Type :

float

overhang_min

Minimum angle to display (in [0, 3.14159], default 0.0)

Type :

float

sharp_max

Maximum angle to display (in [-3.14159, 3.14159], default 3.14159)

Type :

float

sharp_min

Minimum angle to display (in [-3.14159, 3.14159], default 1.5708)

Type :

float

thickness_max

Maximum for measuring thickness (in [0, 1000], default 0.1)

Type :

float

thickness_min

Minimum for measuring thickness (in [0, 1000], default 0.0)

Type :

float

thickness_samples

Number of samples to test per face (in [1, 32], default 1)

Type :

int

type

Type of data to visualize/check (default 'OVERHANG' )

Type :

Literal[‘OVERHANG’, ‘THICKNESS’, ‘INTERSECT’, ‘DISTORT’, ‘SHARP’]

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

- default (type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| ToolSettings.statvis | |

## MeshUVLoop(bpy_struct)

### MeshUVLoop(bpy_struct)

base class — bpy_struct

class bpy.types. MeshUVLoop ( bpy_struct )

(Deprecated) Layer of UV coordinates in a Mesh data-block

pin_uv

(default False)

Type :

bool

uv

(array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

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

| MeshUVLoopLayer.data | |

## MeshVertex(bpy_struct)

### MeshVertex(bpy_struct)

base class — bpy_struct

class bpy.types. MeshVertex ( bpy_struct )

Vertex in a Mesh data-block

co

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

groups

Weights for the vertex groups this vertex is member of (default None, readonly)

Type :

bpy_prop_collection[VertexGroupElement]

hide

(default False)

Type :

bool

index

Index of this vertex (in [0, inf], default 0, readonly)

Type :

int

normal

Vertex Normal (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

select

(default False)

Type :

bool

undeformed_co

On meshes that carry modifiers, this is the vertex coordinate before any deforming modifiers run, which generated texture coordinates rely on (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

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

| Mesh.vertices | |

## MeshVertices(bpy_prop_collection)

### MeshVertices(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MeshVertices ( bpy_prop_collection )

Collection of mesh vertices

add ( count )

add

Parameters :

count ( int ) – Count, Number of vertices to add (in [0, inf])

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

| Mesh.vertices | |

## MetaBallElements(bpy_prop_collection)

### MetaBallElements(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MetaBallElements ( bpy_prop_collection )

Collection of metaball elements

active

Last selected element (readonly)

Type :

MetaElement

new ( * , type = 'BALL' )

Add a new element to the metaball

Parameters :

type (Literal[Metaelem Type Items]) – Type for the new metaball element (optional)

Returns :

The newly created metaball element

Return type :

MetaElement

remove ( element )

Remove an element from the metaball

Parameters :

element (MetaElement) – The element to remove (never None)

clear ( )

Remove all elements from the metaball

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

| MetaBall.elements | |
