# Bpy Extras Submodule Bpy Extras Io Utils, Bpy Extras Submodule Bpy Extras Node Utils, Types With Custom Property Support, Bake Save Mode Items ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: bpy_extras submodule (bpy_extras.io_utils); bpy_extras submodule (bpy_extras.node_utils); Types with Custom Property Support; Bake Save Mode Items; Bake Target Items; Brush Image Brush Type Items; Exr Codec Items; File Path Foreach Flag Items; Geometry Nodes Gizmo Color Items.

## bpy_extras submodule (bpy_extras.io_utils)

### bpy_extras submodule (bpy_extras.io_utils) 

bpy_extras.io_utils. orientation_helper ( axis_forward = 'Y' , axis_up = 'Z' ) 

A decorator for import/export classes that adds the properties the axis conversion system and IO helpers need,
preset to the given default axes.

Parameters :

- axis_forward ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – The default forward axis.

- axis_up ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – The default up axis.

Returns :

A class decorator.

Return type :

Callable[[type], type]

bpy_extras.io_utils. axis_conversion ( from_forward = 'Y' , from_up = 'Z' , to_forward = 'Y' , to_up = 'Z' ) 

Every argument names an axis;
the first two describe the source and the last two the target.

Parameters :

- from_forward ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – Source forward axis.

- from_up ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – Source up axis.

- to_forward ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – Target forward axis.

- to_up ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – Target up axis.

Returns :

The conversion matrix.

Return type :

mathutils.Matrix

bpy_extras.io_utils. axis_conversion_ensure ( operator , forward_attr , up_attr ) 

Makes sure an operator holds valid axis conversion settings; meant
for use from bpy.types.Operator.check.

Parameters :

- operator (bpy.types.Operator) – the operator to access axis attributes from.

- forward_attr ( str ) – attribute storing the forward axis

- up_attr ( str ) – attribute storing the up axis

Returns :

True if the value was modified.

Return type :

bool

bpy_extras.io_utils. create_derived_objects ( depsgraph , objects ) 

Given a sequence of objects, this returns their instances.

Parameters :

- depsgraph (bpy.types.Depsgraph) – The evaluated depsgraph.

- objects (Sequence[bpy.types.Object]) – A sequence of objects.

Returns :

A dictionary where each key is an object from objects ,
values are lists of (object, matrix) tuples representing instances.

Return type :

dict[bpy.types.Object, list[tuple[bpy.types.Object, mathutils.Matrix]]]

bpy_extras.io_utils. poll_file_object_drop ( context ) 

A stock implementation for FileHandler poll_drop methods. It lets both the 3D Viewport and
the Outliner (in ViewLayer display mode) serve as targets for dragging and dropping files.

Parameters :

context (bpy.types.Context) – The context.

Returns :

Whether the drop target is valid.

Return type :

bool

bpy_extras.io_utils. unpack_list ( list_of_tuples ) 

Collapse a sequence of tuples down to one list.

Parameters :

list_of_tuples ( Sequence [ tuple ] ) – A sequence of tuples to unpack.

Returns :

A flat list of all values.

Return type :

list

bpy_extras.io_utils. unpack_face_list ( list_of_tuples ) 

Flatten a list of faces (triangles or quads), padding each triangle
with a trailing zero so every group has four entries.

Parameters :

list_of_tuples ( Sequence [ tuple [ int , ... ] ] ) – A sequence of face index tuples (3 or 4 elements each).

Returns :

A flat list of face indices, padded with zeros.

Return type :

list[int]

bpy_extras.io_utils. path_reference ( filepath , base_src , base_dst , mode = 'AUTO' , copy_subdir = '' , copy_set = None , library = None ) 

Hand back a filepath expressed relative to a destination directory, for
exporters to use.

Parameters :

- filepath ( str ) – the file path to return,
supporting blenders relative '//' prefix.

- base_src ( str ) – the directory the filepath is relative to
(normally the blend file).

- base_dst ( str ) – the directory the filepath will be referenced from
(normally the export path).

- mode ( Literal [ 'AUTO' , 'ABSOLUTE' , 'RELATIVE' , 'MATCH' , 'STRIP' , 'COPY' ] ) – the method used to reference the path.

- copy_subdir ( str ) – the subdirectory of base_dst to use when mode='COPY'.

- copy_set ( set [ tuple [ str , str ] ] | None ) – collect from/to pairs when mode='COPY',
pass to path_reference_copy when exporting is done.

- library (bpy.types.Library | None) – The library this path is relative to.

Returns :

the new filepath.

Return type :

str

bpy_extras.io_utils. path_reference_copy ( copy_set , report=<built-in function print> ) 

Carry out the file copies gathered by path_reference

Parameters :

- copy_set ( set [ tuple [ str , str ] ] ) – set of (from, to) pairs to copy.

- report ( Callable [ [ str ] , None ] ) – function used for reporting warnings, takes a string argument.

bpy_extras.io_utils. unique_name ( key , name , name_dict , name_max = -1 , clean_func = None , sep = '.' ) 

Helper for keeping unique names, which may have special characters
removed and be capped at a maximum length.

Parameters :

- key ( Any ) – Unique item this name belongs to, name_dict[key] will be reused
when available.
This can be the object, mesh, material, etc instance itself.
Any hashable object associated with the name .

- name ( str ) – The name used to create a unique value in name_dict .

- name_dict ( dict [ Any , str ] ) – This is used to cache namespace to ensure no collisions
occur, this should be an empty dict initially and only modified by this
function.

- name_max ( int ) – Maximum length of the name. When -1 the name is unlimited.

- clean_func ( Callable [ [ str ] , str ] | None ) – Function to call on name before creating a unique value.

- sep ( str ) – Separator to use when between the name and a number when a
duplicate name is found.

Returns :

A unique name.

Return type :

str

class bpy_extras.io_utils. ExportHelper 

check ( _context ) 

Confirm the filepath and axis conversion settings are valid.

Returns :

True when a property was updated.

Return type :

bool

invoke ( context , _event ) 

Open the file selector for export, seeding a default filepath
from the name of the current blend file.

Parameters :

context (bpy.types.Context) – The context.

Returns :

The operator return value.

Return type :

set[str]

class bpy_extras.io_utils. ImportHelper 

check ( _context ) 

Confirm the axis conversion settings are valid.

Returns :

True when a property was updated.

Return type :

bool

invoke ( context , _event ) 

Open the file selector for import.

Parameters :

context (bpy.types.Context) – The context.

Returns :

The operator return value.

Return type :

set[str]

invoke_popup ( context , confirm_text = '' ) 

Bring up a popup confirmation dialog when a filepath is already set;
otherwise drop back to the file selector.

Parameters :

- context (bpy.types.Context) – The context.

- confirm_text ( str ) – Label for the confirm button,
defaults to the operator label.

Returns :

The operator return value.

Return type :

set[str]

## bpy_extras submodule (bpy_extras.node_utils)

### bpy_extras submodule (bpy_extras.node_utils) 

bpy_extras.node_utils. connect_sockets ( input , output ) 

Link two sockets inside a node tree.

This helps because links made via the regular Python API come out
invalid when one of the sockets is a virtual socket (the grayed-out sockets in
Group Input and Group Output nodes).

It stands in for node_tree.links.new(input, output)

Parameters :

- input (bpy.types.NodeSocket) – The input socket.

- output (bpy.types.NodeSocket) – The output socket.

bpy_extras.node_utils. find_base_socket_type ( socket ) 

Determine the socket's base class.

A socket may carry a subtype such as NodeSocketFloatFactor,
yet only the base type is permitted, e.g. NodeSocketFloat

Parameters :

socket (bpy.types.NodeSocket) – The socket to find the base type for.

Returns :

The base socket type identifier.

Return type :

str

bpy_extras.node_utils. find_node_input ( node , name ) 

Locate a node input socket by its name.

Since names aren't unique, the first match is returned.

Parameters :

- node (bpy.types.Node) – The node to search.

- name ( str ) – The name of the input socket.

Returns :

The input socket or None if not found.

Return type :

bpy.types.NodeSocket | None

## Types with Custom Property Support

### Types with Custom Property Support 

Custom-property access is available on the types below (and on their sub-types).

The quick-start section on Custom Properties shows examples of how to
use custom properties.

- bpy.types.Bone

- bpy.types.BoneCollection

- bpy.types.EditBone

- bpy.types.GizmoGroupProperties

- bpy.types.GizmoProperties

- bpy.types.ID

- bpy.types.KeyConfigPreferences

- bpy.types.Node

- bpy.types.NodeSocket

- bpy.types.NodeTreeInterfaceSocket

- bpy.types.NodesModifier

- bpy.types.OperatorProperties

- bpy.types.PoseBone

- bpy.types.PropertyGroup

- bpy.types.Strip

- bpy.types.TimelineMarker

- bpy.types.View3DShading

- bpy.types.ViewLayer

## Bake Save Mode Items

### Bake Save Mode Items 

INTERNAL :

Internal.

Keep the baking map inside an internal image data-block.

EXTERNAL :

External.

Write the baking map out to an external file.

## Bake Target Items

### Bake Target Items 

`IMAGE_TEXTURES` :

Image Textures.

Bake onto the image data-blocks tied to the active image texture nodes in materials.

`VERTEX_COLORS` :

Active Color Attribute.

Bake onto the active color attribute carried by meshes.

## Brush Image Brush Type Items

### Brush Image Brush Type Items

DRAW :

Draw.

SOFTEN :

Soften.

SMEAR :

Smear.

CLONE :

Clone.

FILL :

Fill.

MASK :

Mask.

## Exr Codec Items

### Exr Codec Items

NONE :

None.

Leave the data uncompressed.

ZIP :

ZIP.

Lossless zip applied to blocks of 16 image rows.

PIZ :

PIZ.

Lossless wavelet scheme that handles noisy or grainy footage well.

DWAA :

DWAA (lossy).

A JPEG-style lossy method working on blocks of 32 image rows.

DWAB :

DWAB (lossy).

A JPEG-style lossy method working on blocks of 256 image rows.

HTJ2K :

HTJ2K.

Lossless coding built on high-throughput JPEG 2000. Files come out smaller, though support in other applications is still thin since it is recent.

ZIPS :

ZIPS.

Lossless zip, with each image row compressed on its own.

RLE :

RLE.

Lossless run-length encoding.

PXR24 :

Pxr24 (lossy).

Lossy method for 32-bit float images that retains 24 bits of every float.

B44 :

B44 (lossy).

Lossy method for 16-bit float images locked to a 2.3:1 ratio.

B44A :

B44A (lossy).

Lossy method for 16-bit float images locked to a 2.3:1 ratio.

## File Path Foreach Flag Items

### File Path Foreach Flag Items

`SKIP_LINKED` :

Skip Linked.

Pass over the paths belonging to linked IDs.

`SKIP_PACKED` :

Skip Packed.

Pass over paths whose matching data has been packed.

`RESOLVE_TOKEN` :

Resolve Token.

Expand the tokens in a virtual filepath down to one concrete filepath. For now this only applies to UDIM tiles.

`SKIP_WEAK_REFERENCES` :

Skip Weak References.

Pass over weak reference paths. Such paths are usually handy extras rather than something the current .blend file actually reads data from.

`SKIP_MULTIFILE` :

Skip Multi-file.

Pass over paths where one directory backs an array of files, such as image sequence strips or point caches. Only the first path gets handled in that case, which matters for directory-manipulation callbacks that would otherwise touch the same directory over and over.

`RELOAD_EDITED` :

Reload Edited.

Reload the data whenever its path is changed.

## Geometry Nodes Gizmo Color Items

### Geometry Nodes Gizmo Color Items

PRIMARY :

Primary.

SECONDARY :

Secondary.

X :

-

Y :

-

Z :

-
