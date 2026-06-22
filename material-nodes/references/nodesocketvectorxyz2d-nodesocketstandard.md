# Nodesocketvectorxyz2D Nodesocketstandard, Nodesocketvectorxyz4D Nodesocketstandard, Nodesocketvirtual Nodesocketstandard, Nodestorebundleitem Nodeinternal ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: NodeSocketVectorXYZ2D(NodeSocketStandard); NodeSocketVectorXYZ4D(NodeSocketStandard); NodeSocketVirtual(NodeSocketStandard); NodeStoreBundleItem(NodeInternal); NodeTreeInterface(bpy_struct); NodeTreeInterfaceItem(bpy_struct); NodeTreeInterfacePanel(NodeTreeInterfaceItem); NodeTreeInterfaceSocketBool(NodeTreeInterfaceSocket).

## NodeSocketVectorXYZ2D(NodeSocketStandard)

### NodeSocketVectorXYZ2D(NodeSocketStandard) 

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketVectorXYZ2D ( NodeSocketStandard ) 

A node socket carrying a three-component vector.

default_value 

(array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

links 

Every node link attached to this socket, whether incoming or outgoing.

Type :

NodeLinks

Note

Takes O(len(nodetree.links)) time.

(readonly)

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default (bpy.types.Struct | None) – Fallback returned if no match is found.

Returns :

Either the matching RNA type or the supplied fallback when nothing matches.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default ( type | None ) – Fallback returned if no match is found.

Returns :

Either the matching class or the supplied fallback when nothing matches.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data NodeSocket.name NodeSocket.label NodeSocket.identifier NodeSocket.description NodeSocket.is_output NodeSocket.select NodeSocket.hide NodeSocket.enabled NodeSocket.link_limit NodeSocket.is_linked NodeSocket.is_unavailable NodeSocket.is_multi_input NodeSocket.show_expanded | NodeSocket.is_inactive NodeSocket.is_icon_visible NodeSocket.hide_value NodeSocket.pin_gizmo NodeSocket.node NodeSocket.type NodeSocket.display_shape NodeSocket.inferred_structure_type NodeSocket.bl_idname NodeSocket.bl_label NodeSocket.bl_subtype_label NodeSocket.links NodeSocketStandard.links |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeSocket.bl_system_properties_get NodeSocket.draw NodeSocket.draw_color NodeSocket.draw_color_simple NodeSocket.bl_rna_get_subclass NodeSocket.bl_rna_get_subclass_py NodeSocketStandard.draw NodeSocketStandard.draw_color NodeSocketStandard.draw_color_simple NodeSocketStandard.bl_rna_get_subclass NodeSocketStandard.bl_rna_get_subclass_py |

## NodeSocketVectorXYZ4D(NodeSocketStandard)

### NodeSocketVectorXYZ4D(NodeSocketStandard) 

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketVectorXYZ4D ( NodeSocketStandard ) 

A node socket carrying a three-component vector.

default_value 

(array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

mathutils.Vector

links 

Every node link attached to this socket, whether incoming or outgoing.

Type :

NodeLinks

Note

Takes O(len(nodetree.links)) time.

(readonly)

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default (bpy.types.Struct | None) – Fallback returned if no match is found.

Returns :

Either the matching RNA type or the supplied fallback when nothing matches.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default ( type | None ) – Fallback returned if no match is found.

Returns :

Either the matching class or the supplied fallback when nothing matches.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data NodeSocket.name NodeSocket.label NodeSocket.identifier NodeSocket.description NodeSocket.is_output NodeSocket.select NodeSocket.hide NodeSocket.enabled NodeSocket.link_limit NodeSocket.is_linked NodeSocket.is_unavailable NodeSocket.is_multi_input NodeSocket.show_expanded | NodeSocket.is_inactive NodeSocket.is_icon_visible NodeSocket.hide_value NodeSocket.pin_gizmo NodeSocket.node NodeSocket.type NodeSocket.display_shape NodeSocket.inferred_structure_type NodeSocket.bl_idname NodeSocket.bl_label NodeSocket.bl_subtype_label NodeSocket.links NodeSocketStandard.links |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeSocket.bl_system_properties_get NodeSocket.draw NodeSocket.draw_color NodeSocket.draw_color_simple NodeSocket.bl_rna_get_subclass NodeSocket.bl_rna_get_subclass_py NodeSocketStandard.draw NodeSocketStandard.draw_color NodeSocketStandard.draw_color_simple NodeSocketStandard.bl_rna_get_subclass NodeSocketStandard.bl_rna_get_subclass_py |

## NodeSocketVirtual(NodeSocketStandard)

### NodeSocketVirtual(NodeSocketStandard) 

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketVirtual ( NodeSocketStandard ) 

A virtual socket attached to a node.

links 

Every node link attached to this socket, whether incoming or outgoing.

Type :

NodeLinks

Note

Takes O(len(nodetree.links)) time.

(readonly)

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default (bpy.types.Struct | None) – Fallback returned if no match is found.

Returns :

Either the matching RNA type or the supplied fallback when nothing matches.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default ( type | None ) – Fallback returned if no match is found.

Returns :

Either the matching class or the supplied fallback when nothing matches.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data NodeSocket.name NodeSocket.label NodeSocket.identifier NodeSocket.description NodeSocket.is_output NodeSocket.select NodeSocket.hide NodeSocket.enabled NodeSocket.link_limit NodeSocket.is_linked NodeSocket.is_unavailable NodeSocket.is_multi_input NodeSocket.show_expanded | NodeSocket.is_inactive NodeSocket.is_icon_visible NodeSocket.hide_value NodeSocket.pin_gizmo NodeSocket.node NodeSocket.type NodeSocket.display_shape NodeSocket.inferred_structure_type NodeSocket.bl_idname NodeSocket.bl_label NodeSocket.bl_subtype_label NodeSocket.links NodeSocketStandard.links |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeSocket.bl_system_properties_get NodeSocket.draw NodeSocket.draw_color NodeSocket.draw_color_simple NodeSocket.bl_rna_get_subclass NodeSocket.bl_rna_get_subclass_py NodeSocketStandard.draw NodeSocketStandard.draw_color NodeSocketStandard.draw_color_simple NodeSocketStandard.bl_rna_get_subclass NodeSocketStandard.bl_rna_get_subclass_py |

## NodeStoreBundleItem(NodeInternal)

### NodeStoreBundleItem(NodeInternal) 

base classes — bpy_struct, Node, NodeInternal

class bpy.types. NodeStoreBundleItem ( NodeInternal ) 

Save one item of a bundle, keyed by its path and data type.

socket_type 

(default 'FLOAT' )

Type :

Literal[Node Socket Data Type Items]

structure_type 

The category of higher-order type that may pass through this socket (default 'AUTO' )

Type :

Literal[Node Socket Structure Type Items]

classmethod is_registered_node_type ( ) 

Returns true when the node type has been registered.

Returns :

Result

Return type :

bool

classmethod input_template ( index ) 

Template describing an input socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index ) 

Template describing an output socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default (bpy.types.Struct | None) – Fallback returned if no match is found.

Returns :

Either the matching RNA type or the supplied fallback when nothing matches.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default ( type | None ) – Fallback returned if no match is found.

Returns :

Either the matching class or the supplied fallback when nothing matches.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get | Node.socket_value_update Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py |

## NodeTreeInterface(bpy_struct)

### NodeTreeInterface(bpy_struct) 

base class — bpy_struct

class bpy.types. NodeTreeInterface ( bpy_struct ) 

The set of sockets and UI panels that a node group declares.

active 

Active item

Type :

NodeTreeInterfaceItem

active_index 

Position of the currently active item (in [0, inf], default 0)

Type :

int

items_tree 

Every entry held in the node interface (default None, readonly)

Type :

bpy_prop_collection[NodeTreeInterfaceItem]

new_socket ( name , * , description = '' , in_out = 'INPUT' , socket_type = 'DEFAULT' , parent = None ) 

Append a fresh socket to the interface.

Parameters :

- name ( str ) – Name, Name of the socket (never None)

- description ( str ) – Description, Description of the socket (optional, never None)

- in_out ( Literal [ 'INPUT' , 'OUTPUT' ] ) – Input/Output Type, Create an input or output socket (optional)

- INPUT
Input – Generate a input node socket.

- OUTPUT
Output – Generate a output node socket.

- socket_type ( Literal [ 'DEFAULT' ] ) – Socket Type, Type of socket generated on nodes (optional)

- parent (NodeTreeInterfacePanel) – Parent, Panel to add the socket in (optional)

Returns :

Socket, New socket

Return type :

NodeTreeInterfaceSocket

new_panel ( name , * , description = '' , default_closed = False ) 

Append a fresh panel to the interface.

Parameters :

- name ( str ) – Name, Name of the new panel (never None)

- description ( str ) – Description, Description of the panel (optional, never None)

- default_closed ( bool ) – Default Closed, Panel is closed by default on new nodes (optional)

Returns :

Panel, New panel

Return type :

NodeTreeInterfacePanel

copy ( item ) 

Duplicate an item into the interface.

Parameters :

item (NodeTreeInterfaceItem) – Item, Item to copy (never None)

Returns :

Item Copy, Copy of the item

Return type :

NodeTreeInterfaceItem

remove ( item , * , move_content_to_parent = True ) 

Delete an item from the interface.

Parameters :

- item (NodeTreeInterfaceItem) – Item, The item to remove (never None)

- move_content_to_parent ( bool ) – Move Content, If the item is a panel, move the contents to the parent instead of deleting it (optional)

clear ( ) 

Strip every item out of the interface.

move ( item , to_position ) 

Reposition an item.

Parameters :

- item (NodeTreeInterfaceItem) – Item, The item to move (never None)

- to_position ( int ) – To Position, Target position for the item in its current panel (in [0, inf])

move_to_parent ( item , parent , to_position ) 

Relocate an item to a different panel, a different position, or both.

Parameters :

- item (NodeTreeInterfaceItem) – Item, The item to move (never None)

- parent (NodeTreeInterfacePanel) – Parent, New parent of the item

- to_position ( int ) – To Position, Target position for the item in the new parent panel (in [0, inf])

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default (bpy.types.Struct | None) – Fallback returned if no match is found.

Returns :

Either the matching RNA type or the supplied fallback when nothing matches.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default ( type | None ) – Fallback returned if no match is found.

Returns :

Either the matching class or the supplied fallback when nothing matches.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| NodeTree.interface | UILayout.template_node_tree_interface |

## NodeTreeInterfaceItem(bpy_struct)

### NodeTreeInterfaceItem(bpy_struct) 

base class — bpy_struct

subclasses —
NodeTreeInterfacePanel, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceItem ( bpy_struct ) 

A single entry within a node tree interface.

index 

The item's overall position across every entry in the interface (in [-1, inf], default 0, readonly)

Type :

int

item_type 

Kind of interface entry this is (default 'PANEL' , readonly)

Type :

Literal[Node Tree Interface Item Type Items]

parent 

The panel this item sits inside (readonly)

Type :

NodeTreeInterfacePanel

position 

Where the item falls within its parent panel (in [-1, inf], default 0, readonly)

Type :

int

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default (bpy.types.Struct | None) – Fallback returned if no match is found.

Returns :

Either the matching RNA type or the supplied fallback when nothing matches.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default ( type | None ) – Fallback returned if no match is found.

Returns :

Either the matching class or the supplied fallback when nothing matches.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| NodeTreeInterface.active NodeTreeInterface.copy NodeTreeInterface.copy NodeTreeInterface.items_tree | NodeTreeInterface.move NodeTreeInterface.move_to_parent NodeTreeInterface.remove NodeTreeInterfacePanel.interface_items |

## NodeTreeInterfacePanel(NodeTreeInterfaceItem)

### NodeTreeInterfacePanel(NodeTreeInterfaceItem) 

base classes — bpy_struct, NodeTreeInterfaceItem

class bpy.types. NodeTreeInterfacePanel ( NodeTreeInterfaceItem ) 

A panel declared inside a node interface.

default_closed 

On new nodes the panel starts out collapsed (default False)

Type :

bool

description 

Panel description (default “”, never None)

Type :

str

interface_items 

Every entry held in the node panel (default None, readonly)

Type :

bpy_prop_collection[NodeTreeInterfaceItem]

name 

Panel name (default “”, never None)

Type :

str

persistent_uid 

An identifier that uniquely tags this panel inside its node tree (in [-inf, inf], default 0, readonly)

Type :

int

select 

Whether the panel is selected in the interface (default False)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default (bpy.types.Struct | None) – Fallback returned if no match is found.

Returns :

Either the matching RNA type or the supplied fallback when nothing matches.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default ( type | None ) – Fallback returned if no match is found.

Returns :

Either the matching class or the supplied fallback when nothing matches.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data NodeTreeInterfaceItem.item_type NodeTreeInterfaceItem.parent | NodeTreeInterfaceItem.position NodeTreeInterfaceItem.index |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeTreeInterfaceItem.bl_rna_get_subclass NodeTreeInterfaceItem.bl_rna_get_subclass_py |

### References 

| NodeTreeInterface.move_to_parent NodeTreeInterface.new_panel | NodeTreeInterface.new_socket NodeTreeInterfaceItem.parent |

## NodeTreeInterfaceSocketBool(NodeTreeInterfaceSocket)

### NodeTreeInterfaceSocketBool(NodeTreeInterfaceSocket) 

base classes — bpy_struct, NodeTreeInterfaceItem, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceSocketBool ( NodeTreeInterfaceSocket ) 

A node socket holding a boolean value.

default_value 

Input value used for unconnected socket (default False)

Type :

bool

draw ( context , layout ) 

Render the socket's interface settings.

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, Layout in the UI (never None)

init_socket ( node , socket , data_path ) 

Set up a node socket instance.

Parameters :

- node (Node) – Node, Node of the socket to initialize (never None)

- socket (NodeSocket) – Socket, Socket to initialize (never None)

- data_path ( str ) – Data Path, Path to specialized socket data (never None)

from_socket ( node , socket ) 

Derive the template parameters from a socket that already exists.

Parameters :

- node (Node) – Node, Node of the original socket (never None)

- socket (NodeSocket) – Socket, Original socket (never None)

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default (bpy.types.Struct | None) – Fallback returned if no match is found.

Returns :

Either the matching RNA type or the supplied fallback when nothing matches.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default ( type | None ) – Fallback returned if no match is found.

Returns :

Either the matching class or the supplied fallback when nothing matches.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data NodeTreeInterfaceItem.item_type NodeTreeInterfaceItem.parent NodeTreeInterfaceItem.position NodeTreeInterfaceItem.index NodeTreeInterfaceSocket.name NodeTreeInterfaceSocket.identifier NodeTreeInterfaceSocket.description NodeTreeInterfaceSocket.socket_type NodeTreeInterfaceSocket.in_out NodeTreeInterfaceSocket.hide_value NodeTreeInterfaceSocket.hide_in_modifier | NodeTreeInterfaceSocket.force_non_field NodeTreeInterfaceSocket.is_inspect_output NodeTreeInterfaceSocket.is_panel_toggle NodeTreeInterfaceSocket.layer_selection_field NodeTreeInterfaceSocket.menu_expanded NodeTreeInterfaceSocket.optional_label NodeTreeInterfaceSocket.select NodeTreeInterfaceSocket.attribute_domain NodeTreeInterfaceSocket.default_attribute_name NodeTreeInterfaceSocket.structure_type NodeTreeInterfaceSocket.default_input NodeTreeInterfaceSocket.bl_socket_idname |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id | bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeTreeInterfaceItem.bl_rna_get_subclass NodeTreeInterfaceItem.bl_rna_get_subclass_py NodeTreeInterfaceSocket.bl_system_properties_get NodeTreeInterfaceSocket.draw NodeTreeInterfaceSocket.init_socket NodeTreeInterfaceSocket.from_socket NodeTreeInterfaceSocket.bl_rna_get_subclass NodeTreeInterfaceSocket.bl_rna_get_subclass_py |
