# Greasepencildrawing Bpy Struct, Greasepencilframe Bpy Struct, Greasepencilframes Bpy Prop Collection, Greasepencillayergroup Greasepenciltreenode ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: GreasePencilDrawing(bpy_struct); GreasePencilFrame(bpy_struct); GreasePencilFrames(bpy_prop_collection); GreasePencilLayerGroup(GreasePencilTreeNode); GreasePencilLayerMask(bpy_struct); GreasePencilLayerMasks(bpy_prop_collection); GreasePencilTimeModifierSegment(bpy_struct); GreasePencilv3Layers(bpy_prop_collection); GroupNodeViewerPathElem(ViewerPathElem).

## GreasePencilDrawing(bpy_struct)

### GreasePencilDrawing(bpy_struct)

base class — bpy_struct

class bpy.types. GreasePencilDrawing ( bpy_struct )

A Grease Pencil drawing

attributes

Geometry attributes (default None, readonly)

Type :

AttributeGroupGreasePencilDrawing[Attribute]

color_attributes

Geometry color attributes (default None, readonly)

Type :

AttributeGroupGreasePencilDrawing[Attribute]

curve_offsets

Offset indices of the first point of each curve (default None, readonly)

Type :

bpy_prop_collection[IntAttributeValue]

type

Drawing type (default 'DRAWING' , readonly)

Type :

Literal[‘DRAWING’, ‘REFERENCE’]

user_count

Count of keyframes that make use of this drawing (in [-inf, inf], default 0, readonly)

Type :

int

strokes

Return a collection of all the Grease Pencil strokes in this drawing.

Note

This API should not be used for performance critical operations.
Use the GreasePencilDrawing.attributes API instead.

Note

When point/curves count of a drawing is changed, the slice returned by this
call prior to the change is no longer valid. You need to get the new stroke
slice via drawing.strokes[n] .

(readonly)

add_strokes ( sizes )

Add new strokes with provided sizes at the end

Parameters :

sizes ( Sequence [ int ] ) – Sizes, The number of points in each stroke (array of 1 items, in [1, inf])

remove_strokes ( * , indices = (0,) )

Remove all strokes. If indices are provided, remove only the strokes with the given indices.

Parameters :

indices ( Sequence [ int ] ) – Indices, The indices of the strokes to remove (array of 1 items, in [0, inf], optional)

resize_strokes ( sizes , * , indices = (0,) )

Resize all existing strokes. If indices are provided, resize only the strokes with the given indices. If the new size for a stroke is smaller, the stroke is trimmed. If the new size for a stroke is larger, the new end values are default initialized.

Parameters :

- sizes ( Sequence [ int ] ) – Sizes, The number of points in each stroke (array of 1 items, in [1, inf])

- indices ( Sequence [ int ] ) – Indices, The indices of the stroke to resize (array of 1 items, in [0, inf], optional)

reorder_strokes ( new_indices )

Reorder the strokes by the new indices.

Parameters :

new_indices ( Sequence [ int ] ) – New indices, The new index for each of the strokes (array of 1 items, in [0, inf])

set_types ( * , type = '`CATMULL_ROM`' , indices = (0,) )

Set the curve type. If indices are provided, set only the types with the given curve indices.

Parameters :

- type (Literal[Curves Type Items]) – Type, (optional)

- indices ( Sequence [ int ] ) – Indices, The indices of the curves to resize (array of 1 items, in [0, inf], optional)

tag_positions_changed ( )

Indicate that the positions of points in the drawing have changed

vertex_group_assign ( vgroup_name , indices_ptr , weight )

Assign points to vertex group

Parameters :

- vgroup_name ( str ) – Vertex Group Name, Name of the vertex group (never None)

- indices_ptr ( Sequence [ int ] ) – Indices, The point indices to assign the weight to (array of 1 items, in [-inf, inf])

- weight ( float ) – Vertex weight (in [0, 1])

vertex_group_remove ( vgroup_name , indices_ptr )

Remove points from vertex group

Parameters :

- vgroup_name ( str ) – Vertex Group Name, Name of the vertex group (never None)

- indices_ptr ( Sequence [ int ] ) – Indices, The point indices to remove from the vertex group (array of 1 items, in [-inf, inf])

set_vertex_weights ( vertex_group_name , indices , weights , * , assign_mode = 'REPLACE' )

Set the weights of vertices in a grease pencil drawing

Parameters :

- vertex_group_name ( str ) – Vertex Group Name, Name of the vertex group (never None)

- indices ( Sequence [ int ] ) – Indices, The point indices in the vertex group to modify (array of 1 items, in [-inf, inf])

- weights ( Sequence [ float ] ) – Weights, The weight for each corresponding index in the indices array (array of 1 items, in [0, 1])

- assign_mode ( Literal [ 'REPLACE' , 'ADD' , 'SUBTRACT' ] ) – (optional)

- REPLACE
Replace – Replace.

- ADD
Add – Add.

- SUBTRACT
Subtract – Subtract.

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

| GreasePencilFrame.drawing | |

## GreasePencilFrame(bpy_struct)

### GreasePencilFrame(bpy_struct)

base class — bpy_struct

class bpy.types. GreasePencilFrame ( bpy_struct )

A Grease Pencil keyframe

drawing

A Grease Pencil drawing

Type :

GreasePencilDrawing

frame_number

The frame number in the scene (in [-1048574, 1048574], default 0, readonly)

Type :

int

keyframe_type

Type of keyframe (default 'KEYFRAME' )

- KEYFRAME
Keyframe – Normal keyframe, e.g. for key poses.

- BREAKDOWN
Breakdown – A breakdown pose, e.g. for transitions between key poses.

- `MOVING_HOLD`
Moving Hold – A keyframe that is part of a moving hold.

- EXTREME
Extreme – An ‘extreme’ pose, or some other purpose as needed.

- JITTER
Jitter – A filler or baked keyframe for keying on ones, or some other purpose as needed.

- GENERATED
Generated – A key generated automatically by a tool, not manually created.

Type :

Literal[‘KEYFRAME’, ‘BREAKDOWN’, ‘`MOVING_HOLD`’, ‘EXTREME’, ‘JITTER’, ‘GENERATED’]

select

Frame Selection in the Dope Sheet (default False)

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

| GreasePencilFrames.copy GreasePencilFrames.move GreasePencilFrames.new | GreasePencilLayer.current_frame GreasePencilLayer.frames GreasePencilLayer.get_frame_at |

## GreasePencilFrames(bpy_prop_collection)

### GreasePencilFrames(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. GreasePencilFrames ( bpy_prop_collection )

Collection of Grease Pencil frames

new ( frame_number )

Add a new Grease Pencil frame

Parameters :

frame_number ( int ) – Frame Number, The frame on which the drawing appears (in [-1048574, 1048574])

Returns :

The newly created frame

Return type :

GreasePencilFrame

remove ( frame_number )

Remove a Grease Pencil frame

Parameters :

frame_number ( int ) – Frame Number, The frame number of the frame to remove (in [-1048574, 1048574])

copy ( from_frame_number , to_frame_number , * , instance_drawing = False )

Copy a Grease Pencil frame

Parameters :

- from_frame_number ( int ) – Source Frame Number, The frame number of the source frame (in [-1048574, 1048574])

- to_frame_number ( int ) – Frame Number of Copy, The frame number to copy the frame to (in [-1048574, 1048574])

- instance_drawing ( bool ) – Instance Drawing, Let the copied frame use the same drawing as the source (optional)

Returns :

The newly copied frame

Return type :

GreasePencilFrame

move ( from_frame_number , to_frame_number )

Move a Grease Pencil frame

Parameters :

- from_frame_number ( int ) – Source Frame Number, The frame number of the source frame (in [-1048574, 1048574])

- to_frame_number ( int ) – Target Frame Number, The frame number to move the frame to (in [-1048574, 1048574])

Returns :

The moved frame

Return type :

GreasePencilFrame

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

| GreasePencilLayer.frames | |

## GreasePencilLayerGroup(GreasePencilTreeNode)

### GreasePencilLayerGroup(GreasePencilTreeNode)

base classes — bpy_struct, GreasePencilTreeNode

class bpy.types. GreasePencilLayerGroup ( GreasePencilTreeNode )

Group of Grease Pencil layers

children

Layer groups directly nested under this one, in stack order so the first entry sits at the bottom of the tree. (default None, readonly)

Type :

bpy_prop_collection[GreasePencilTreeNode]

color_tag

(default 'COLOR1' )

Type :

Literal[‘NONE’, ‘COLOR1’, ‘COLOR2’, ‘COLOR3’, ‘COLOR4’, ‘COLOR5’, ‘COLOR6’, ‘COLOR7’, ‘COLOR8’]

is_expanded

The layer group shows expanded in the UI (default False)

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

| bpy_struct.id_data GreasePencilTreeNode.name GreasePencilTreeNode.hide GreasePencilTreeNode.lock GreasePencilTreeNode.select GreasePencilTreeNode.use_onion_skinning | GreasePencilTreeNode.use_masks GreasePencilTreeNode.channel_color GreasePencilTreeNode.next_node GreasePencilTreeNode.prev_node GreasePencilTreeNode.parent_group |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values GreasePencilTreeNode.bl_rna_get_subclass GreasePencilTreeNode.bl_rna_get_subclass_py |

### References

| GreasePencil.layer_groups GreasePencilTreeNode.parent_group GreasePencilv3LayerGroup.active GreasePencilv3LayerGroup.move GreasePencilv3LayerGroup.move_bottom GreasePencilv3LayerGroup.move_to_layer_group GreasePencilv3LayerGroup.move_to_layer_group | GreasePencilv3LayerGroup.move_top GreasePencilv3LayerGroup.new GreasePencilv3LayerGroup.new GreasePencilv3LayerGroup.remove GreasePencilv3Layers.move_to_layer_group GreasePencilv3Layers.new |

## GreasePencilLayerMask(bpy_struct)

### GreasePencilLayerMask(bpy_struct)

base class — bpy_struct

class bpy.types. GreasePencilLayerMask ( bpy_struct )

List of Mask Layers

hide

Set mask Visibility (default False)

Type :

bool

invert

Invert mask (default False)

Type :

bool

name

Mask layer name (default “”, never None)

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

| GreasePencilLayer.mask_layers | |

## GreasePencilLayerMasks(bpy_prop_collection)

### GreasePencilLayerMasks(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. GreasePencilLayerMasks ( bpy_prop_collection )

Collection of Grease Pencil masking layers

active_mask_index

Active index in layer mask array (in [0, inf], default 0)

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

| GreasePencilLayer.mask_layers | |

## GreasePencilTimeModifierSegment(bpy_struct)

### GreasePencilTimeModifierSegment(bpy_struct)

base class — bpy_struct

class bpy.types. GreasePencilTimeModifierSegment ( bpy_struct )

Holds the settings for one dash segment.

name

Name of the dash segment (default "", never None)

Type :

str

segment_end

Last frame of the segment (in [0, 32767], default 2)

Type :

int

segment_mode

(default 'NORMAL' )

- NORMAL
Regular – Offset runs in the normal playback direction.

- REVERSE
Reverse – Offset runs against the playback direction.

- PINGPONG
Ping Pong – Bounce back and forth.

Type :

Literal['NORMAL', 'REVERSE', 'PINGPONG']

segment_repeat

Number of cycle repeats (in [1, 32767], default 1)

Type :

int

segment_start

First frame of the segment (in [0, 32767], default 1)

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

| GreasePencilTimeModifier.segments | |

## GreasePencilv3Layers(bpy_prop_collection)

### GreasePencilv3Layers(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. GreasePencilv3Layers ( bpy_prop_collection )

A set of Grease Pencil layers held by a data-block.

active

Active Grease Pencil layer

Type :

GreasePencilLayer

new ( name , * , set_active = True , layer_group = None )

Create another Grease Pencil layer.

Parameters :

- name ( str ) – Name, Name of the layer (never None)

- set_active ( bool ) – Set Active, Set the newly created layer as the active layer (optional)

- layer_group (GreasePencilLayerGroup) – The layer group the new layer will be created in (use None for the main stack) (optional)

Returns :

The newly created layer

Return type :

GreasePencilLayer

remove ( layer )

Delete a Grease Pencil layer.

Parameters :

layer (GreasePencilLayer) – The layer to remove (never None)

move ( layer , type )

Shift a Grease Pencil layer within its layer group or the main stack.

Parameters :

- layer (GreasePencilLayer) – The layer to move (never None)

- type ( Literal [ 'DOWN' , 'UP' ] ) – Direction of movement

move_top ( layer )

Send a Grease Pencil layer up to the top of its layer group or the main stack.

Parameters :

layer (GreasePencilLayer) – The layer to move (never None)

move_bottom ( layer )

Send a Grease Pencil layer down to the bottom of its layer group or the main stack.

Parameters :

layer (GreasePencilLayer) – The layer to move (never None)

move_to_layer_group ( layer , layer_group )

Relocate a Grease Pencil layer into a layer group.

Parameters :

- layer (GreasePencilLayer) – The layer to move (never None)

- layer_group (GreasePencilLayerGroup) – The layer group the layer will be moved into (use None for the main stack)

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

| GreasePencil.layers | |

## GroupNodeViewerPathElem(ViewerPathElem)

### GroupNodeViewerPathElem(ViewerPathElem)

base classes — bpy_struct, ViewerPathElem

class bpy.types. GroupNodeViewerPathElem ( ViewerPathElem )

node_id

(in [-inf, inf], default 0)

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

| bpy_struct.id_data ViewerPathElem.type | ViewerPathElem.ui_name |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ViewerPathElem.bl_rna_get_subclass ViewerPathElem.bl_rna_get_subclass_py |
