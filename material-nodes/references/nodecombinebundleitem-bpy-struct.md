# Nodecombinebundleitem Bpy Struct, Nodecombinebundleitems Bpy Prop Collection, Nodecompositorfileoutputitem Bpy Struct, Nodecompositorfileoutputitems Bpy Prop Collection ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: NodeCombineBundleItem(bpy_struct); NodeCombineBundleItems(bpy_prop_collection); NodeCompositorFileOutputItem(bpy_struct); NodeCompositorFileOutputItems(bpy_prop_collection); NodeCustomGroup(Node); NodeEnableOutput(NodeInternal); NodeEvaluateClosure(NodeInternal); NodeEvaluateClosureInputItem(bpy_struct); NodeEvaluateClosureInputItems(bpy_prop_collection); NodeEvaluateClosureOutputItem(bpy_struct).

## NodeCombineBundleItem(bpy_struct)

### NodeCombineBundleItem(bpy_struct)

base class — bpy_struct

class bpy.types. NodeCombineBundleItem ( bpy_struct )

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

structure_type

The category of higher-order types this socket is meant to carry (default 'AUTO' )

Type :

Literal[Node Socket Structure Type Items]

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

| NodeCombineBundle.bundle_items NodeCombineBundleItems.new | NodeCombineBundleItems.remove |

## NodeCombineBundleItems(bpy_prop_collection)

### NodeCombineBundleItems(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodeCombineBundleItems ( bpy_prop_collection )

A set of combine bundle items.

new ( socket_type , name )

Append an item onto the end

Parameters :

- socket_type (Literal[Node Socket Data Type Items]) – Socket Type, Socket type of the item

- name ( str ) – Name, (never None)

Returns :

Item, New item

Return type :

NodeCombineBundleItem

remove ( item )

Delete an item

Parameters :

item (NodeCombineBundleItem) – Item, The item to remove (never None)

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

| NodeCombineBundle.bundle_items | |

## NodeCompositorFileOutputItem(bpy_struct)

### NodeCompositorFileOutputItem(bpy_struct)

base class — bpy_struct

class bpy.types. NodeCompositorFileOutputItem ( bpy_struct )

color

The color shown for this socket type within the node editor (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

format

(readonly)

Type :

ImageFormatSettings

name

(default “”, never None)

Type :

str

override_node_format

Save this file with its own format rather than the node's format (default False)

Type :

bool

save_as_render

When writing a byte image, run the render portion of the display transform first (default False)

Type :

bool

socket_type

(default 'FLOAT' )

Type :

Literal[Node Socket Data Type Items]

vector_socket_dimensions

How many dimensions the vector socket has (in [2, 4], default 0)

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

| CompositorNodeOutputFile.file_output_items NodeCompositorFileOutputItems.new | NodeCompositorFileOutputItems.remove |

## NodeCompositorFileOutputItems(bpy_prop_collection)

### NodeCompositorFileOutputItems(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodeCompositorFileOutputItems ( bpy_prop_collection )

A set of file output items.

new ( socket_type , name )

Append an item onto the end

Parameters :

- socket_type (Literal[Node Socket Data Type Items]) – Socket Type, Socket type of the item

- name ( str ) – Name, (never None)

Returns :

Item, New item

Return type :

NodeCompositorFileOutputItem

remove ( item )

Delete an item

Parameters :

item (NodeCompositorFileOutputItem) – Item, The item to remove (never None)

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

| CompositorNodeOutputFile.file_output_items | |

## NodeCustomGroup(Node)

### NodeCustomGroup(Node)

base classes — bpy_struct, Node

class bpy.types. NodeCustomGroup ( Node )

The parent node type used by custom-registered node group types.

node_tree

Type :

NodeTree

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset | bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py |

## NodeEnableOutput(NodeInternal)

### NodeEnableOutput(NodeInternal)

base classes — bpy_struct, Node, NodeInternal

class bpy.types. NodeEnableOutput ( NodeInternal )

Forward the incoming value, or instead emit the fallback value.

data_type

(default 'FLOAT' )

Type :

Literal[Node Socket Data Type Items]

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

## NodeEvaluateClosure(NodeInternal)

### NodeEvaluateClosure(NodeInternal)

base classes — bpy_struct, Node, NodeInternal

class bpy.types. NodeEvaluateClosure ( NodeInternal )

Run the supplied closure.

active_input_index

Position of the currently active item (in [0, inf], default 0)

Type :

int

active_output_index

Position of the currently active item (in [0, inf], default 0)

Type :

int

define_signature

Have this node establish a closure signature for other nodes to use (default False)

Type :

bool

input_items

(default None, readonly)

Type :

NodeEvaluateClosureInputItems[NodeEvaluateClosureInputItem]

output_items

(default None, readonly)

Type :

NodeEvaluateClosureOutputItems[NodeEvaluateClosureOutputItem]

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

## NodeEvaluateClosureInputItem(bpy_struct)

### NodeEvaluateClosureInputItem(bpy_struct)

base class — bpy_struct

class bpy.types. NodeEvaluateClosureInputItem ( bpy_struct )

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

structure_type

The category of higher-order types this socket is meant to carry (default 'AUTO' )

Type :

Literal[Node Socket Structure Type Items]

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

| NodeEvaluateClosure.input_items NodeEvaluateClosureInputItems.new | NodeEvaluateClosureInputItems.remove |

## NodeEvaluateClosureInputItems(bpy_prop_collection)

### NodeEvaluateClosureInputItems(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodeEvaluateClosureInputItems ( bpy_prop_collection )

new ( socket_type , name )

Append an item onto the end

Parameters :

- socket_type (Literal[Node Socket Data Type Items]) – Socket Type, Socket type of the item

- name ( str ) – Name, (never None)

Returns :

Item, New item

Return type :

NodeEvaluateClosureInputItem

remove ( item )

Delete an item

Parameters :

item (NodeEvaluateClosureInputItem) – Item, The item to remove (never None)

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

| NodeEvaluateClosure.input_items | |

## NodeEvaluateClosureOutputItem(bpy_struct)

### NodeEvaluateClosureOutputItem(bpy_struct)

base class — bpy_struct

class bpy.types. NodeEvaluateClosureOutputItem ( bpy_struct )

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

structure_type

The category of higher-order types this socket is meant to carry (default 'AUTO' )

Type :

Literal[Node Socket Structure Type Items]

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

| NodeEvaluateClosure.output_items NodeEvaluateClosureOutputItems.new | NodeEvaluateClosureOutputItems.remove |

## See also

- [Bpy Struct](bpy-struct.md)
