# Nodetreeinterfacesocketimage Nodetreeinterfacesocket, Nodetreeinterfacesocketint Nodetreeinterfacesocket, Nodetreeinterfacesocketintfactor Nodetreeinterfacesocket, Nodetreeinterfacesocketintpercentage Nodetreeinterfacesocket ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: NodeTreeInterfaceSocketImage(NodeTreeInterfaceSocket); NodeTreeInterfaceSocketInt(NodeTreeInterfaceSocket); NodeTreeInterfaceSocketIntFactor(NodeTreeInterfaceSocket); NodeTreeInterfaceSocketIntPercentage(NodeTreeInterfaceSocket); NodeTreeInterfaceSocketIntUnsigned(NodeTreeInterfaceSocket); NodeTreeInterfaceSocketMask(NodeTreeInterfaceSocket).

## NodeTreeInterfaceSocketImage(NodeTreeInterfaceSocket)

### NodeTreeInterfaceSocketImage(NodeTreeInterfaceSocket)

base classes — bpy_struct, NodeTreeInterfaceItem, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceSocketImage ( NodeTreeInterfaceSocket )

A node socket that carries an image

default_value

Value fed in while the socket stays unlinked

Type :

Image

draw ( context , layout )

Render the settings shown for this interface socket

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, the layout placed in the UI (never None)

init_socket ( node , socket , data_path )

Set up a fresh node socket instance

Parameters :

- node (Node) – Node, the node owning the socket being set up (never None)

- socket (NodeSocket) – Socket, the socket being set up (never None)

- data_path ( str ) – Data Path, route to this socket's specialized data (never None)

from_socket ( node , socket )

Fill in template parameters by copying an existing socket

Parameters :

- node (Node) – Node, the node owning the source socket (never None)

- socket (NodeSocket) – Socket, the source socket (never None)

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

Either the matching RNA type or the supplied default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

Either the matching class or the supplied default if none is found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data NodeTreeInterfaceItem.item_type NodeTreeInterfaceItem.parent NodeTreeInterfaceItem.position NodeTreeInterfaceItem.index NodeTreeInterfaceSocket.name NodeTreeInterfaceSocket.identifier NodeTreeInterfaceSocket.description NodeTreeInterfaceSocket.socket_type NodeTreeInterfaceSocket.in_out NodeTreeInterfaceSocket.hide_value NodeTreeInterfaceSocket.hide_in_modifier | NodeTreeInterfaceSocket.force_non_field NodeTreeInterfaceSocket.is_inspect_output NodeTreeInterfaceSocket.is_panel_toggle NodeTreeInterfaceSocket.layer_selection_field NodeTreeInterfaceSocket.menu_expanded NodeTreeInterfaceSocket.optional_label NodeTreeInterfaceSocket.select NodeTreeInterfaceSocket.attribute_domain NodeTreeInterfaceSocket.default_attribute_name NodeTreeInterfaceSocket.structure_type NodeTreeInterfaceSocket.default_input NodeTreeInterfaceSocket.bl_socket_idname |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id | bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeTreeInterfaceItem.bl_rna_get_subclass NodeTreeInterfaceItem.bl_rna_get_subclass_py NodeTreeInterfaceSocket.bl_system_properties_get NodeTreeInterfaceSocket.draw NodeTreeInterfaceSocket.init_socket NodeTreeInterfaceSocket.from_socket NodeTreeInterfaceSocket.bl_rna_get_subclass NodeTreeInterfaceSocket.bl_rna_get_subclass_py |

## NodeTreeInterfaceSocketInt(NodeTreeInterfaceSocket)

### NodeTreeInterfaceSocketInt(NodeTreeInterfaceSocket)

base classes — bpy_struct, NodeTreeInterfaceItem, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceSocketInt ( NodeTreeInterfaceSocket )

A node socket that carries an integer value

default_value

Value fed in while the socket stays unlinked (in [-inf, inf], default 0)

Type :

int

max_value

Upper bound on the value (in [-inf, inf], default 0)

Type :

int

min_value

Lower bound on the value (in [-inf, inf], default 0)

Type :

int

subtype

Variant tag applied to the default value (default 'DEFAULT' )

Type :

Literal[‘DEFAULT’]

draw ( context , layout )

Render the settings shown for this interface socket

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, the layout placed in the UI (never None)

init_socket ( node , socket , data_path )

Set up a fresh node socket instance

Parameters :

- node (Node) – Node, the node owning the socket being set up (never None)

- socket (NodeSocket) – Socket, the socket being set up (never None)

- data_path ( str ) – Data Path, route to this socket's specialized data (never None)

from_socket ( node , socket )

Fill in template parameters by copying an existing socket

Parameters :

- node (Node) – Node, the node owning the source socket (never None)

- socket (NodeSocket) – Socket, the source socket (never None)

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

Either the matching RNA type or the supplied default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

Either the matching class or the supplied default if none is found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data NodeTreeInterfaceItem.item_type NodeTreeInterfaceItem.parent NodeTreeInterfaceItem.position NodeTreeInterfaceItem.index NodeTreeInterfaceSocket.name NodeTreeInterfaceSocket.identifier NodeTreeInterfaceSocket.description NodeTreeInterfaceSocket.socket_type NodeTreeInterfaceSocket.in_out NodeTreeInterfaceSocket.hide_value NodeTreeInterfaceSocket.hide_in_modifier | NodeTreeInterfaceSocket.force_non_field NodeTreeInterfaceSocket.is_inspect_output NodeTreeInterfaceSocket.is_panel_toggle NodeTreeInterfaceSocket.layer_selection_field NodeTreeInterfaceSocket.menu_expanded NodeTreeInterfaceSocket.optional_label NodeTreeInterfaceSocket.select NodeTreeInterfaceSocket.attribute_domain NodeTreeInterfaceSocket.default_attribute_name NodeTreeInterfaceSocket.structure_type NodeTreeInterfaceSocket.default_input NodeTreeInterfaceSocket.bl_socket_idname |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id | bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeTreeInterfaceItem.bl_rna_get_subclass NodeTreeInterfaceItem.bl_rna_get_subclass_py NodeTreeInterfaceSocket.bl_system_properties_get NodeTreeInterfaceSocket.draw NodeTreeInterfaceSocket.init_socket NodeTreeInterfaceSocket.from_socket NodeTreeInterfaceSocket.bl_rna_get_subclass NodeTreeInterfaceSocket.bl_rna_get_subclass_py |

## NodeTreeInterfaceSocketIntFactor(NodeTreeInterfaceSocket)

### NodeTreeInterfaceSocketIntFactor(NodeTreeInterfaceSocket)

base classes — bpy_struct, NodeTreeInterfaceItem, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceSocketIntFactor ( NodeTreeInterfaceSocket )

A node socket that carries an integer value

default_value

Value fed in while the socket stays unlinked (in [0, inf], default 0)

Type :

int

max_value

Upper bound on the value (in [-inf, inf], default 0)

Type :

int

min_value

Lower bound on the value (in [-inf, inf], default 0)

Type :

int

subtype

Variant tag applied to the default value (default 'DEFAULT' )

Type :

Literal[‘DEFAULT’]

draw ( context , layout )

Render the settings shown for this interface socket

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, the layout placed in the UI (never None)

init_socket ( node , socket , data_path )

Set up a fresh node socket instance

Parameters :

- node (Node) – Node, the node owning the socket being set up (never None)

- socket (NodeSocket) – Socket, the socket being set up (never None)

- data_path ( str ) – Data Path, route to this socket's specialized data (never None)

from_socket ( node , socket )

Fill in template parameters by copying an existing socket

Parameters :

- node (Node) – Node, the node owning the source socket (never None)

- socket (NodeSocket) – Socket, the source socket (never None)

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

Either the matching RNA type or the supplied default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

Either the matching class or the supplied default if none is found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data NodeTreeInterfaceItem.item_type NodeTreeInterfaceItem.parent NodeTreeInterfaceItem.position NodeTreeInterfaceItem.index NodeTreeInterfaceSocket.name NodeTreeInterfaceSocket.identifier NodeTreeInterfaceSocket.description NodeTreeInterfaceSocket.socket_type NodeTreeInterfaceSocket.in_out NodeTreeInterfaceSocket.hide_value NodeTreeInterfaceSocket.hide_in_modifier | NodeTreeInterfaceSocket.force_non_field NodeTreeInterfaceSocket.is_inspect_output NodeTreeInterfaceSocket.is_panel_toggle NodeTreeInterfaceSocket.layer_selection_field NodeTreeInterfaceSocket.menu_expanded NodeTreeInterfaceSocket.optional_label NodeTreeInterfaceSocket.select NodeTreeInterfaceSocket.attribute_domain NodeTreeInterfaceSocket.default_attribute_name NodeTreeInterfaceSocket.structure_type NodeTreeInterfaceSocket.default_input NodeTreeInterfaceSocket.bl_socket_idname |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id | bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeTreeInterfaceItem.bl_rna_get_subclass NodeTreeInterfaceItem.bl_rna_get_subclass_py NodeTreeInterfaceSocket.bl_system_properties_get NodeTreeInterfaceSocket.draw NodeTreeInterfaceSocket.init_socket NodeTreeInterfaceSocket.from_socket NodeTreeInterfaceSocket.bl_rna_get_subclass NodeTreeInterfaceSocket.bl_rna_get_subclass_py |

## NodeTreeInterfaceSocketIntPercentage(NodeTreeInterfaceSocket)

### NodeTreeInterfaceSocketIntPercentage(NodeTreeInterfaceSocket)

base classes — bpy_struct, NodeTreeInterfaceItem, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceSocketIntPercentage ( NodeTreeInterfaceSocket )

A node socket that carries an integer value

default_value

Value fed in while the socket stays unlinked (in [0, inf], default 0)

Type :

int

max_value

Upper bound on the value (in [-inf, inf], default 0)

Type :

int

min_value

Lower bound on the value (in [-inf, inf], default 0)

Type :

int

subtype

Variant tag applied to the default value (default 'DEFAULT' )

Type :

Literal[‘DEFAULT’]

draw ( context , layout )

Render the settings shown for this interface socket

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, the layout placed in the UI (never None)

init_socket ( node , socket , data_path )

Set up a fresh node socket instance

Parameters :

- node (Node) – Node, the node owning the socket being set up (never None)

- socket (NodeSocket) – Socket, the socket being set up (never None)

- data_path ( str ) – Data Path, route to this socket's specialized data (never None)

from_socket ( node , socket )

Fill in template parameters by copying an existing socket

Parameters :

- node (Node) – Node, the node owning the source socket (never None)

- socket (NodeSocket) – Socket, the source socket (never None)

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

Either the matching RNA type or the supplied default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

Either the matching class or the supplied default if none is found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data NodeTreeInterfaceItem.item_type NodeTreeInterfaceItem.parent NodeTreeInterfaceItem.position NodeTreeInterfaceItem.index NodeTreeInterfaceSocket.name NodeTreeInterfaceSocket.identifier NodeTreeInterfaceSocket.description NodeTreeInterfaceSocket.socket_type NodeTreeInterfaceSocket.in_out NodeTreeInterfaceSocket.hide_value NodeTreeInterfaceSocket.hide_in_modifier | NodeTreeInterfaceSocket.force_non_field NodeTreeInterfaceSocket.is_inspect_output NodeTreeInterfaceSocket.is_panel_toggle NodeTreeInterfaceSocket.layer_selection_field NodeTreeInterfaceSocket.menu_expanded NodeTreeInterfaceSocket.optional_label NodeTreeInterfaceSocket.select NodeTreeInterfaceSocket.attribute_domain NodeTreeInterfaceSocket.default_attribute_name NodeTreeInterfaceSocket.structure_type NodeTreeInterfaceSocket.default_input NodeTreeInterfaceSocket.bl_socket_idname |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id | bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeTreeInterfaceItem.bl_rna_get_subclass NodeTreeInterfaceItem.bl_rna_get_subclass_py NodeTreeInterfaceSocket.bl_system_properties_get NodeTreeInterfaceSocket.draw NodeTreeInterfaceSocket.init_socket NodeTreeInterfaceSocket.from_socket NodeTreeInterfaceSocket.bl_rna_get_subclass NodeTreeInterfaceSocket.bl_rna_get_subclass_py |

## NodeTreeInterfaceSocketIntUnsigned(NodeTreeInterfaceSocket)

### NodeTreeInterfaceSocketIntUnsigned(NodeTreeInterfaceSocket)

base classes — bpy_struct, NodeTreeInterfaceItem, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceSocketIntUnsigned ( NodeTreeInterfaceSocket )

A node socket that carries an integer value

default_value

Value fed in while the socket stays unlinked (in [0, inf], default 0)

Type :

int

max_value

Upper bound on the value (in [-inf, inf], default 0)

Type :

int

min_value

Lower bound on the value (in [-inf, inf], default 0)

Type :

int

subtype

Variant tag applied to the default value (default 'DEFAULT' )

Type :

Literal[‘DEFAULT’]

draw ( context , layout )

Render the settings shown for this interface socket

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, the layout placed in the UI (never None)

init_socket ( node , socket , data_path )

Set up a fresh node socket instance

Parameters :

- node (Node) – Node, the node owning the socket being set up (never None)

- socket (NodeSocket) – Socket, the socket being set up (never None)

- data_path ( str ) – Data Path, route to this socket's specialized data (never None)

from_socket ( node , socket )

Fill in template parameters by copying an existing socket

Parameters :

- node (Node) – Node, the node owning the source socket (never None)

- socket (NodeSocket) – Socket, the source socket (never None)

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

Either the matching RNA type or the supplied default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

Either the matching class or the supplied default if none is found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data NodeTreeInterfaceItem.item_type NodeTreeInterfaceItem.parent NodeTreeInterfaceItem.position NodeTreeInterfaceItem.index NodeTreeInterfaceSocket.name NodeTreeInterfaceSocket.identifier NodeTreeInterfaceSocket.description NodeTreeInterfaceSocket.socket_type NodeTreeInterfaceSocket.in_out NodeTreeInterfaceSocket.hide_value NodeTreeInterfaceSocket.hide_in_modifier | NodeTreeInterfaceSocket.force_non_field NodeTreeInterfaceSocket.is_inspect_output NodeTreeInterfaceSocket.is_panel_toggle NodeTreeInterfaceSocket.layer_selection_field NodeTreeInterfaceSocket.menu_expanded NodeTreeInterfaceSocket.optional_label NodeTreeInterfaceSocket.select NodeTreeInterfaceSocket.attribute_domain NodeTreeInterfaceSocket.default_attribute_name NodeTreeInterfaceSocket.structure_type NodeTreeInterfaceSocket.default_input NodeTreeInterfaceSocket.bl_socket_idname |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id | bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeTreeInterfaceItem.bl_rna_get_subclass NodeTreeInterfaceItem.bl_rna_get_subclass_py NodeTreeInterfaceSocket.bl_system_properties_get NodeTreeInterfaceSocket.draw NodeTreeInterfaceSocket.init_socket NodeTreeInterfaceSocket.from_socket NodeTreeInterfaceSocket.bl_rna_get_subclass NodeTreeInterfaceSocket.bl_rna_get_subclass_py |

## NodeTreeInterfaceSocketMask(NodeTreeInterfaceSocket)

### NodeTreeInterfaceSocketMask(NodeTreeInterfaceSocket)

base classes — bpy_struct, NodeTreeInterfaceItem, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceSocketMask ( NodeTreeInterfaceSocket )

A node socket that carries a mask

default_value

Value fed in while the socket stays unlinked

Type :

Mask

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

Either the matching RNA type or the supplied default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

Either the matching class or the supplied default if none is found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data NodeTreeInterfaceItem.item_type NodeTreeInterfaceItem.parent NodeTreeInterfaceItem.position NodeTreeInterfaceItem.index NodeTreeInterfaceSocket.name NodeTreeInterfaceSocket.identifier NodeTreeInterfaceSocket.description NodeTreeInterfaceSocket.socket_type NodeTreeInterfaceSocket.in_out NodeTreeInterfaceSocket.hide_value NodeTreeInterfaceSocket.hide_in_modifier | NodeTreeInterfaceSocket.force_non_field NodeTreeInterfaceSocket.is_inspect_output NodeTreeInterfaceSocket.is_panel_toggle NodeTreeInterfaceSocket.layer_selection_field NodeTreeInterfaceSocket.menu_expanded NodeTreeInterfaceSocket.optional_label NodeTreeInterfaceSocket.select NodeTreeInterfaceSocket.attribute_domain NodeTreeInterfaceSocket.default_attribute_name NodeTreeInterfaceSocket.structure_type NodeTreeInterfaceSocket.default_input NodeTreeInterfaceSocket.bl_socket_idname |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id | bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeTreeInterfaceItem.bl_rna_get_subclass NodeTreeInterfaceItem.bl_rna_get_subclass_py NodeTreeInterfaceSocket.bl_system_properties_get NodeTreeInterfaceSocket.draw NodeTreeInterfaceSocket.init_socket NodeTreeInterfaceSocket.from_socket NodeTreeInterfaceSocket.bl_rna_get_subclass NodeTreeInterfaceSocket.bl_rna_get_subclass_py |
