# Nodejoinbundle Nodeinternal, Nodeoutputs Bpy Prop Collection, Nodereroute Nodeinternal, Nodes Bpy Prop Collection ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: NodeJoinBundle(NodeInternal); NodeOutputs(bpy_prop_collection); NodeReroute(NodeInternal); Nodes(bpy_prop_collection); NodeSeparateBundle(NodeInternal); NodeSeparateBundleItem(bpy_struct); NodeSeparateBundleItems(bpy_prop_collection); NodesModifier(Modifier); NodesModifierBake(bpy_struct).

## NodeJoinBundle(NodeInternal)

### NodeJoinBundle(NodeInternal)

base classes — bpy_struct, Node, NodeInternal

class bpy.types. NodeJoinBundle ( NodeInternal )

Merge several bundles into one

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

## NodeOutputs(bpy_prop_collection)

### NodeOutputs(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodeOutputs ( bpy_prop_collection )

A set holding the node's sockets.

new ( type , name , * , identifier = '' , use_multi_input = False )

Attach a new socket to this node.

Parameters :

- type ( str ) – Type, Data type (never None)

- name ( str ) – Name, (never None)

- identifier ( str ) – Identifier, Unique socket identifier (optional, never None)

- use_multi_input ( bool ) – Make the socket multi-input (valid for inputs only) (optional)

Returns :

New socket

Return type :

NodeSocket

remove ( socket )

Detach one socket from this node.

Parameters :

socket (NodeSocket) – The socket to remove

clear ( )

Strip every socket off this node.

move ( from_index , to_index )

Reposition a socket within the list.

Parameters :

- from_index ( int ) – From Index, Index of the socket to move (in [0, inf])

- to_index ( int ) – To Index, Target index for the socket (in [0, inf])

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

| Node.outputs | |

## NodeReroute(NodeInternal)

### NodeReroute(NodeInternal)

base classes — bpy_struct, Node, NodeInternal

class bpy.types. NodeReroute ( NodeInternal )

A single-socket routing helper that accepts one input and feeds several outputs

socket_idname

(default “”, never None)

Type :

str

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

## Nodes(bpy_prop_collection)

### Nodes(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. Nodes ( bpy_prop_collection )

A set holding the nodes.

active

Active node in this tree

Type :

Node

new ( type )

Place a node into this node tree.

Parameters :

type ( str ) – Type, Type of node to add (Warning: should be same as node.bl_idname, not node.type!) (never None)

Returns :

New node

Return type :

Node

remove ( node )

Take a node out of this node tree.

Parameters :

node (Node) – The node to remove (never None)

clear ( )

Empty the node tree of all nodes.

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

| NodeTree.nodes | |

## NodeSeparateBundle(NodeInternal)

### NodeSeparateBundle(NodeInternal)

base classes — bpy_struct, Node, NodeInternal

class bpy.types. NodeSeparateBundle ( NodeInternal )

Break a bundle apart into several sockets.

active_index

Index of the active item (in [0, inf], default 0)

Type :

int

bundle_items

(default None, readonly)

Type :

NodeSeparateBundleItems[NodeSeparateBundleItem]

define_signature

When set, this node lays down a bundle signature for other nodes to follow (default False)

Type :

bool

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

## NodeSeparateBundleItem(bpy_struct)

### NodeSeparateBundleItem(bpy_struct)

base class — bpy_struct

class bpy.types. NodeSeparateBundleItem ( bpy_struct )

color

The node editor's color for the matching socket type (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0), readonly)

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

Which higher-order types are anticipated to pass through this socket (default 'AUTO' )

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

| NodeSeparateBundle.bundle_items NodeSeparateBundleItems.new | NodeSeparateBundleItems.remove |

## NodeSeparateBundleItems(bpy_prop_collection)

### NodeSeparateBundleItems(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodeSeparateBundleItems ( bpy_prop_collection )

A set holding the separate bundle items for this node.

new ( socket_type , name )

Append a fresh item after the existing ones.

Parameters :

- socket_type (Literal[Node Socket Data Type Items]) – Socket Type, Socket type of the item

- name ( str ) – Name, (never None)

Returns :

Item, New item

Return type :

NodeSeparateBundleItem

remove ( item )

Delete one item.

Parameters :

item (NodeSeparateBundleItem) – Item, The item to remove (never None)

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

| NodeSeparateBundle.bundle_items | |

## NodesModifier(Modifier)

### NodesModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. NodesModifier ( Modifier )

bake_directory

Location on disk where the bake data is stored (default “”, never None, blend relative // prefix supported)

Type :

str

bake_target

Where to store the baked data (default 'PACKED' )

- PACKED
Packed – Pack the baked data into the .blend file.

- DISK
Disk – Store the baked data in a directory on disk.

Type :

Literal[‘PACKED’, ‘DISK’]

bakes

(default None, readonly)

Type :

NodesModifierBakes[NodesModifierBake]

node_group

Node group that controls what this modifier does

Type :

NodeTree

node_warnings

(default None, readonly)

Type :

bpy_prop_collection[NodesModifierWarning]

open_bake_data_blocks_panel

(default False)

Type :

bool

open_bake_panel

(default False)

Type :

bool

open_manage_panel

(default False)

Type :

bool

open_named_attributes_panel

(default False)

Type :

bool

open_output_attributes_panel

(default False)

Type :

bool

open_warnings_panel

(default False)

Type :

bool

panels

(default None, readonly)

Type :

NodesModifierPanels[NodesModifierPanel]

show_group_selector

(default False)

Type :

bool

show_manage_panel

(default False)

Type :

bool

bl_system_properties_get ( * , do_create = False )

DEBUG ONLY. Internal access to runtime-defined RNA data storage, intended solely for testing and debugging purposes. Do not access it in regular scripting work, and in particular, do not assume that it contains writable data

Parameters :

do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)

Returns :

The system properties root container, or None if there are no system properties stored in this data yet, and its creation was not requested

Return type :

PropertyGroup

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## NodesModifierBake(bpy_struct)

### NodesModifierBake(bpy_struct)

base class — bpy_struct

class bpy.types. NodesModifierBake ( bpy_struct )

bake_id

Identifier for this bake which remains unchanged even when the bake node is renamed, grouped or ungrouped (in [-inf, inf], default 0, readonly)

Type :

int

bake_mode

(default 'ANIMATION' )

- ANIMATION
Animation – Bake a frame range.

- STILL
Still – Bake a single frame.

Type :

Literal[‘ANIMATION’, ‘STILL’]

bake_target

Where to store the baked data (default 'INHERIT' )

- INHERIT
Inherit from Modifier – Use setting from the modifier.

- PACKED
Packed – Pack the baked data into the .blend file.

- DISK
Disk – Store the baked data in a directory on disk.

Type :

Literal[‘INHERIT’, ‘PACKED’, ‘DISK’]

data_blocks

(default None, readonly)

Type :

NodesModifierBakeDataBlocks[NodesModifierDataBlock]

directory

Location on disk where the bake data is stored (default “”, never None, blend relative // prefix supported)

Type :

str

frame_end

Frame where the baking ends (in [-inf, inf], default 0)

Type :

int

frame_start

Frame where the baking starts (in [-inf, inf], default 0)

Type :

int

node

Bake node or simulation output node that corresponds to this bake. This node may be deeply nested in the modifier node group. It can be none in some cases like missing linked data blocks. (readonly)

Type :

Node

use_custom_path

Set a custom location for the baked data by hand (default False)

Type :

bool

use_custom_simulation_frame_range

Replace the scene's simulation frame range with a custom one (default False)

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

| NodesModifier.bakes | |
