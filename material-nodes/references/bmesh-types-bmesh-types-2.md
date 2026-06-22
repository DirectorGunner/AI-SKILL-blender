# Bmesh Types Bmesh Types (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Warning: existing references to the N'th element will keep pointing at the data at that index.

layers
custom-data layers (read-only).
Type: bmesh.types.BMLayerAccessVert

class bmesh.types. BMEdgeSeq

ensure_lookup_table ( )
Ensures the internal data needed for int subscript access is initialized for verts/edges/faces, e.g. bm.verts[index]. Call it again after adding/removing data in this sequence.

get ( verts , fallback = None )
Returns an edge that uses the verts passed.
Parameters:
- verts (Sequence[bmesh.types.BMVert]) – Pair of verts (exactly 2).
- fallback ( Any ) – Return this value if nothing is found.
Returns: The edge found or the fallback value.
Return type: bmesh.types.BMEdge | None

index_update ( )
Initializes the index values of this sequence — the equivalent of looping over all elements and assigning their index values:
```text
for index, ele in enumerate(sequence):
    ele.index = index
```
Note: running this on sequences other than bmesh.types.BMesh.verts, bmesh.types.BMesh.edges, bmesh.types.BMesh.faces works but won't give each element a valid index — instead its order in the sequence is set.

new ( verts , source = None )
Creates a new edge from a given pair of verts.
Parameters:
- verts (Sequence[bmesh.types.BMVert]) – Vertex pair.
- source (bmesh.types.BMEdge | None) – Existing edge to initialize settings (optional argument).
Returns: The newly created edge.
Return type: bmesh.types.BMEdge

remove ( edge )
Removes an edge.
Parameters: edge (bmesh.types.BMEdge) – The edge to remove.

sort ( * , key = None , reverse = False )
Sorts the elements of this sequence, using an optional custom sort key. Element indices aren't changed; use bmesh.types.BMElemSeq.index_update() for that.
Parameters:
- key (Callable[[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace], int] | None) – The key that sets the ordering of the elements.
- reverse ( bool ) – Reverse the order of the elements
Note: when the 'key' argument isn't provided, the elements are reordered following their current index value — so you can set indices manually before calling this method.
Warning: existing references to the N'th element will keep pointing at the data at that index.

layers
custom-data layers (read-only).
Type: bmesh.types.BMLayerAccessEdge

class bmesh.types. BMFaceSeq

ensure_lookup_table ( )
Ensures the internal data needed for int subscript access is initialized for verts/edges/faces, e.g. bm.verts[index]. Call it again after adding/removing data in this sequence.

get ( verts , fallback = None )
Returns a face that uses the verts passed.
Parameters:
- verts (Sequence[bmesh.types.BMVert]) – Sequence of verts.
- fallback ( Any ) – Return this value if nothing is found.
Returns: The face found or the fallback value.
Return type: bmesh.types.BMFace | None

index_update ( )
Initializes the index values of this sequence — the equivalent of looping over all elements and assigning their index values:
```text
for index, ele in enumerate(sequence):
    ele.index = index
```
Note: running this on sequences other than bmesh.types.BMesh.verts, bmesh.types.BMesh.edges, bmesh.types.BMesh.faces works but won't give each element a valid index — instead its order in the sequence is set.

new ( verts , source = None )
Creates a new face from a given set of verts.
Parameters:
- verts (Sequence[bmesh.types.BMVert]) – Sequence of 3 or more verts.
- source (bmesh.types.BMFace | None) – Existing face to initialize settings (optional argument).
Returns: The newly created face.
Return type: bmesh.types.BMFace

remove ( face )
Removes a face.
Parameters: face (bmesh.types.BMFace) – The face to remove.

sort ( * , key = None , reverse = False )
Sorts the elements of this sequence, using an optional custom sort key. Element indices aren't changed; use bmesh.types.BMElemSeq.index_update() for that.
Parameters:
- key (Callable[[bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace], int] | None) – The key that sets the ordering of the elements.
- reverse ( bool ) – Reverse the order of the elements
Note: when the 'key' argument isn't provided, the elements are reordered following their current index value — so you can set indices manually before calling this method.
Warning: existing references to the N'th element will keep pointing at the data at that index.

active
active face.
Type: bmesh.types.BMFace | None

layers
custom-data layers (read-only).
Type: bmesh.types.BMLayerAccessFace

class bmesh.types. BMLoopSeq

layers
custom-data layers (read-only).
Type: bmesh.types.BMLayerAccessLoop

class bmesh.types. BMIter
An internal BMesh type for looping over verts/faces/edges, used for iterating over bmesh.types.BMElemSeq types.

### Selection History
class bmesh.types. BMEditSelSeq

add ( element )
Adds an element to the selection history (does nothing if it's already added).
Parameters: element (BMVert | BMEdge | BMFace) – The element to add.

clear ( )
Empties the selection history.

discard ( element )
Discards an element from the selection history. Like remove, but doesn't raise an error when the element isn't in the selection list.
Parameters: element (BMVert | BMEdge | BMFace) – The element to discard.

remove ( element )
Removes an element from the selection history.
Parameters: element (BMVert | BMEdge | BMFace) – The element to remove.

validate ( )
Ensures all elements in the selection history are selected.

active
The last selected element, or None (read-only).
Type: bmesh.types.BMVert | bmesh.types.BMEdge | bmesh.types.BMFace | None

class bmesh.types. BMEditSelIter

### Custom-Data Layer Access
class bmesh.types. BMLayerAccessVert
Exposes custom-data layer attributes.

bool
A generic boolean custom-data layer.
Type: bmesh.types.BMLayerCollection[bool]

color
A generic 8-bit-precision RGBA color custom-data layer.
Type: bmesh.types.BMLayerCollection[mathutils.Vector]

deform
Vertex deform weight bmesh.types.BMDeformVert (TODO).
Type: bmesh.types.BMLayerCollection[bmesh.types.BMDeformVert]

float
A generic float custom-data layer.
Type: bmesh.types.BMLayerCollection[float]

float_color
A generic float-precision RGBA color custom-data layer.
Type: bmesh.types.BMLayerCollection[mathutils.Vector]

float_vector
A generic float-precision 3D vector custom-data layer.
Type: bmesh.types.BMLayerCollection[mathutils.Vector]

int
A generic int custom-data layer.
Type: bmesh.types.BMLayerCollection[int]

shape

Vertex shape-key absolute location (as a 3D Vector).
Type: bmesh.types.BMLayerCollection[mathutils.Vector]

skin
Accessor for the skin layer.
Type: bmesh.types.BMLayerCollection[ bmesh.types.BMVertSkin ]

string
A generic string custom-data layer (exposed as bytes, 255 max length).
Type: bmesh.types.BMLayerCollection[bytes]

class bmesh.types. BMLayerAccessEdge
Exposes custom-data layer attributes.

bool
A generic boolean custom-data layer.
Type: bmesh.types.BMLayerCollection[bool]

color
A generic 8-bit-precision RGBA color custom-data layer.
Type: bmesh.types.BMLayerCollection[mathutils.Vector]

float
A generic float custom-data layer.
Type: bmesh.types.BMLayerCollection[float]

float_color
A generic float-precision RGBA color custom-data layer.
Type: bmesh.types.BMLayerCollection[mathutils.Vector]

float_vector
A generic float-precision 3D vector custom-data layer.
Type: bmesh.types.BMLayerCollection[mathutils.Vector]

int
A generic int custom-data layer.
Type: bmesh.types.BMLayerCollection[int]

string
A generic string custom-data layer (exposed as bytes, 255 max length).
Type: bmesh.types.BMLayerCollection[bytes]

class bmesh.types. BMLayerAccessFace
Exposes custom-data layer attributes.

bool
A generic boolean custom-data layer.
Type: bmesh.types.BMLayerCollection[bool]

color
A generic 8-bit-precision RGBA color custom-data layer.
Type: bmesh.types.BMLayerCollection[mathutils.Vector]

float
A generic float custom-data layer.
Type: bmesh.types.BMLayerCollection[float]

float_color
A generic float-precision RGBA color custom-data layer.
Type: bmesh.types.BMLayerCollection[mathutils.Vector]

float_vector
A generic float-precision 3D vector custom-data layer.
Type: bmesh.types.BMLayerCollection[mathutils.Vector]

int
A generic int custom-data layer.
Type: bmesh.types.BMLayerCollection[int]

string
A generic string custom-data layer (exposed as bytes, 255 max length).
Type: bmesh.types.BMLayerCollection[bytes]

class bmesh.types. BMLayerAccessLoop
Exposes custom-data layer attributes.

bool
A generic boolean custom-data layer.
Type: bmesh.types.BMLayerCollection[bool]

color
A generic 8-bit-precision RGBA color custom-data layer.
Type: bmesh.types.BMLayerCollection[mathutils.Vector]

float
A generic float custom-data layer.
Type: bmesh.types.BMLayerCollection[float]

float_color
A generic float-precision RGBA color custom-data layer.
Type: bmesh.types.BMLayerCollection[mathutils.Vector]

float_vector
A generic float-precision 3D vector custom-data layer.
Type: bmesh.types.BMLayerCollection[mathutils.Vector]

int
A generic int custom-data layer.
Type: bmesh.types.BMLayerCollection[int]

string
A generic string custom-data layer (exposed as bytes, 255 max length).
Type: bmesh.types.BMLayerCollection[bytes]

uv
Accessor for bmesh.types.BMLoopUV UV (as a 2D Vector).
Type: bmesh.types.BMLayerCollection[bmesh.types.BMLoopUV]

class bmesh.types. BMLayerCollection
Gives access to a collection of custom-data layers of the same type; behaves like a Python dictionary, except it also supports list-like index access.

get ( key , default = None )
Returns the value of the layer matching the key, or default when not found (matching Python's dictionary function of the same name).
Parameters:
- key ( str ) – The key associated with the layer.
- default ( Any ) – Optional argument for the value to return if key is not found.
Returns: The layer matching the key or the default value.
Return type: bmesh.types.BMLayerItem | Any

items ( )
Returns the (key, value) pairs of collection members (matching Python's dict.items() functionality).
Returns: (key, value) pairs for each member of this collection.
Return type: list[tuple[str, bmesh.types.BMLayerItem]]

keys ( )
Returns the identifiers of collection members (matching Python's dict.keys() functionality).
Returns: the identifiers for each member of this collection.
Return type: list[str]

new ( name = '' )
Creates a new layer.
Parameters: name ( str ) – Optional name argument (will be made unique).
Returns: The newly created layer.
Return type: bmesh.types.BMLayerItem

remove ( layer )
Removes a layer.
Parameters: layer (bmesh.types.BMLayerItem) – The layer to remove.

values ( )
Returns the values of the collection (matching Python's dict.values() functionality).
Returns: the members of this collection.
Return type: list[bmesh.types.BMLayerItem]

verify ( )
Creates a new layer or returns an existing active layer.
Returns: The newly created layer, or the existing active layer.
Return type: bmesh.types.BMLayerItem

active
The active layer of this type (read-only).
Type: bmesh.types.BMLayerItem | None

is_singleton
True if there can exist only one layer of this type (read-only).
Type: bool

class bmesh.types. BMLayerItem
Exposes a single custom-data layer; its main purpose is as an item accessor to custom-data when used with vert/edge/face/loop data.

copy_from ( other )
Copies data from another layer.
Parameters: other (bmesh.types.BMLayerItem) – Another layer to copy from.

name
The layer's unique name (read-only).
Type: str

### Custom-Data Layer Types
class bmesh.types. BMLoopUV

pin_uv
UV pin state.
Type: bool

uv
Loop UV (as a 2D Vector).
Type: mathutils.Vector

class bmesh.types. BMDeformVert

clear ( )
Clears all weights.

get ( key , default = None )
Returns the deform weight matching the key, or default when not found (matching Python's dictionary function of the same name).
Parameters:
- key ( int ) – The vertex group index.
- default ( Any ) – Optional argument for the value to return if key is not found.
Returns: The deform weight, or the default when not found.
Return type: float | Any

items ( )
Returns (group, weight) pairs for this vertex (matching Python's dict.items() functionality).
Returns: (key, value) pairs for each deform weight of this vertex.
Return type: list[tuple[int, float]]

keys ( )
Returns the group indices used by this vertex (matching Python's dict.keys() functionality).
Returns: The deform group indices this vertex uses.
Return type: list[int]

values ( )
Returns the weights of the deform vertex (matching Python's dict.values() functionality).
Returns: The weights that influence this vertex.
Return type: list[float]
