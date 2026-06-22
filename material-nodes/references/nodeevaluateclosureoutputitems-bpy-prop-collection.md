# Nodeevaluateclosureoutputitems Bpy Prop Collection, Nodeframe Nodeinternal, Nodefunctionformatstringitem Bpy Struct, Nodefunctionformatstringitems Bpy Prop Collection ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: NodeEvaluateClosureOutputItems(bpy_prop_collection); NodeFrame(NodeInternal); NodeFunctionFormatStringItem(bpy_struct); NodeFunctionFormatStringItems(bpy_prop_collection); NodeGeometryBakeItem(bpy_struct); NodeGeometryBakeItems(bpy_prop_collection); NodeGeometryCaptureAttributeItem(bpy_struct); NodeGeometryCaptureAttributeItems(bpy_prop_collection); NodeGeometryForeachGeometryElementGenerationItems(bpy_prop_collection); NodeGeometryForeachGeometryElementInputItems(bpy_prop_collection); NodeGeometryForeachGeometryElementMainItems(bpy_prop_collection).

## NodeEvaluateClosureOutputItems(bpy_prop_collection)

### NodeEvaluateClosureOutputItems(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodeEvaluateClosureOutputItems ( bpy_prop_collection )

new ( socket_type , name )

Append an item onto the end

Parameters :

- socket_type (Literal[Node Socket Data Type Items]) – Socket Type, Socket type of the item

- name ( str ) – Name, (never None)

Returns :

Item, New item

Return type :

NodeEvaluateClosureOutputItem

remove ( item )

Delete an item

Parameters :

item (NodeEvaluateClosureOutputItem) – Item, The item to remove (never None)

clear ( )

Delete every item

move ( from_index , to_index )

Shift an item to a different position

Parameters :

- from_index ( int ) – From Index, Index of the item to move (in [0, inf])

- to_index ( int ) – To Index, Target index for the item (in [0, inf])

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

| NodeEvaluateClosure.output_items | |

## NodeFrame(NodeInternal)

### NodeFrame(NodeInternal)

base classes — bpy_struct, Node, NodeInternal

class bpy.types. NodeFrame ( NodeInternal )

Group related nodes inside a shared region. Handy for tidiness when you do not need a node group's reusability.

label_size

Point size of the font used to draw the label (in [8, 64], default 0)

Type :

int

shrink

Pull the frame in to its smallest bounding box (default False)

Type :

bool

text

Type :

Text

classmethod is_registered_node_type ( )

True if a registered node type

Returns :

Result

Return type :

bool

classmethod input_template ( index )

Input socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index )

Output socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

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

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get | Node.socket_value_update Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py |

## NodeFunctionFormatStringItem(bpy_struct)

### NodeFunctionFormatStringItem(bpy_struct)

base class — bpy_struct

class bpy.types. NodeFunctionFormatStringItem ( bpy_struct )

color

The color shown for this socket type within the node editor (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

name

(default “”, never None)

Type :

str

socket_type

(default 'FLOAT' )

Type :

Literal[Node Socket Data Type Items]

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

| FunctionNodeFormatString.format_items NodeFunctionFormatStringItems.new | NodeFunctionFormatStringItems.remove |

## NodeFunctionFormatStringItems(bpy_prop_collection)

### NodeFunctionFormatStringItems(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodeFunctionFormatStringItems ( bpy_prop_collection )

A set of format string items.

new ( socket_type , name )

Append an item onto the end

Parameters :

- socket_type (Literal[Node Socket Data Type Items]) – Socket Type, Socket type of the item

- name ( str ) – Name, (never None)

Returns :

Item, New item

Return type :

NodeFunctionFormatStringItem

remove ( item )

Delete an item

Parameters :

item (NodeFunctionFormatStringItem) – Item, The item to remove (never None)

clear ( )

Delete every item

move ( from_index , to_index )

Shift an item to a different position

Parameters :

- from_index ( int ) – From Index, Index of the item to move (in [0, inf])

- to_index ( int ) – To Index, Target index for the item (in [0, inf])

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

| FunctionNodeFormatString.format_items | |

## NodeGeometryBakeItem(bpy_struct)

### NodeGeometryBakeItem(bpy_struct)

base class — bpy_struct

class bpy.types. NodeGeometryBakeItem ( bpy_struct )

attribute_domain

The attribute domain under which the attribute lives within the baked data (default 'POINT' )

Type :

Literal[Attribute Domain Items]

color

The color shown for this socket type within the node editor (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

is_attribute

This bake item holds an attribute kept on a geometry (default False)

Type :

bool

name

(default “”, never None)

Type :

str

socket_type

(default 'FLOAT' )

Type :

Literal[Node Socket Data Type Items]

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

| GeometryNodeBake.bake_items NodeGeometryBakeItems.new | NodeGeometryBakeItems.remove |

## NodeGeometryBakeItems(bpy_prop_collection)

### NodeGeometryBakeItems(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodeGeometryBakeItems ( bpy_prop_collection )

A set of bake items.

new ( socket_type , name )

Append an item onto the end

Parameters :

- socket_type (Literal[Node Socket Data Type Items]) – Socket Type, Socket type of the item

- name ( str ) – Name, (never None)

Returns :

Item, New item

Return type :

NodeGeometryBakeItem

remove ( item )

Delete an item

Parameters :

item (NodeGeometryBakeItem) – Item, The item to remove (never None)

clear ( )

Delete every item

move ( from_index , to_index )

Shift an item to a different position

Parameters :

- from_index ( int ) – From Index, Index of the item to move (in [0, inf])

- to_index ( int ) – To Index, Target index for the item (in [0, inf])

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

| GeometryNodeBake.bake_items | |

## NodeGeometryCaptureAttributeItem(bpy_struct)

### NodeGeometryCaptureAttributeItem(bpy_struct)

base class — bpy_struct

class bpy.types. NodeGeometryCaptureAttributeItem ( bpy_struct )

color

The color shown for this socket type within the node editor (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

data_type

(default 'FLOAT' )

Type :

Literal[Attribute Type Items]

name

(default “”, never None)

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

| GeometryNodeCaptureAttribute.capture_items NodeGeometryCaptureAttributeItems.new | NodeGeometryCaptureAttributeItems.remove |

## NodeGeometryCaptureAttributeItems(bpy_prop_collection)

### NodeGeometryCaptureAttributeItems(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodeGeometryCaptureAttributeItems ( bpy_prop_collection )

A set holding the capture attribute items for this node.

new ( socket_type , name )

Append a fresh item after the existing ones.

Parameters :

- socket_type (Literal[Node Socket Data Type Items]) – Socket Type, Socket type of the item

- name ( str ) – Name, (never None)

Returns :

Item, New item

Return type :

NodeGeometryCaptureAttributeItem

remove ( item )

Delete one item.

Parameters :

item (NodeGeometryCaptureAttributeItem) – Item, The item to remove (never None)

clear ( )

Delete every item at once.

move ( from_index , to_index )

Shift an item to a different slot.

Parameters :

- from_index ( int ) – From Index, Index of the item to move (in [0, inf])

- to_index ( int ) – To Index, Target index for the item (in [0, inf])

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

| GeometryNodeCaptureAttribute.capture_items | |

## NodeGeometryForeachGeometryElementGenerationItems(bpy_prop_collection)

### NodeGeometryForeachGeometryElementGenerationItems(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodeGeometryForeachGeometryElementGenerationItems ( bpy_prop_collection )

A set holding the generation items for this node.

new ( socket_type , name )

Append a fresh item after the existing ones.

Parameters :

- socket_type (Literal[Node Socket Data Type Items]) – Socket Type, Socket type of the item

- name ( str ) – Name, (never None)

Returns :

Item, New item

Return type :

ForeachGeometryElementGenerationItem

remove ( item )

Delete one item.

Parameters :

item (ForeachGeometryElementGenerationItem) – Item, The item to remove (never None)

clear ( )

Delete every item at once.

move ( from_index , to_index )

Shift an item to a different slot.

Parameters :

- from_index ( int ) – From Index, Index of the item to move (in [0, inf])

- to_index ( int ) – To Index, Target index for the item (in [0, inf])

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

| GeometryNodeForeachGeometryElementOutput.generation_items | |

## NodeGeometryForeachGeometryElementInputItems(bpy_prop_collection)

### NodeGeometryForeachGeometryElementInputItems(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodeGeometryForeachGeometryElementInputItems ( bpy_prop_collection )

A set holding the input items for this node.

new ( socket_type , name )

Append a fresh item after the existing ones.

Parameters :

- socket_type (Literal[Node Socket Data Type Items]) – Socket Type, Socket type of the item

- name ( str ) – Name, (never None)

Returns :

Item, New item

Return type :

ForeachGeometryElementInputItem

remove ( item )

Delete one item.

Parameters :

item (ForeachGeometryElementInputItem) – Item, The item to remove (never None)

clear ( )

Delete every item at once.

move ( from_index , to_index )

Shift an item to a different slot.

Parameters :

- from_index ( int ) – From Index, Index of the item to move (in [0, inf])

- to_index ( int ) – To Index, Target index for the item (in [0, inf])

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

| GeometryNodeForeachGeometryElementOutput.input_items | |

## NodeGeometryForeachGeometryElementMainItems(bpy_prop_collection)

### NodeGeometryForeachGeometryElementMainItems(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodeGeometryForeachGeometryElementMainItems ( bpy_prop_collection )

A set holding the main items for this node.

new ( socket_type , name )

Append a fresh item after the existing ones.

Parameters :

- socket_type (Literal[Node Socket Data Type Items]) – Socket Type, Socket type of the item

- name ( str ) – Name, (never None)

Returns :

Item, New item

Return type :

ForeachGeometryElementMainItem

remove ( item )

Delete one item.

Parameters :

item (ForeachGeometryElementMainItem) – Item, The item to remove (never None)

clear ( )

Delete every item at once.

move ( from_index , to_index )

Shift an item to a different slot.

Parameters :

- from_index ( int ) – From Index, Index of the item to move (in [0, inf])

- to_index ( int ) – To Index, Target index for the item (in [0, inf])

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

| GeometryNodeForeachGeometryElementOutput.main_items | |

## See also

- [Bpy Struct](bpy-struct.md)
