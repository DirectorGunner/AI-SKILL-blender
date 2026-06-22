# Nodetreeinterfacesocketvector2D Nodetreeinterfacesocket, Nodetreeinterfacesocketvector4D Nodetreeinterfacesocket, Nodetreeinterfacesocketvectoracceleration Nodetreeinterfacesocket, Nodetreeinterfacesocketvectoracceleration2D Nodetreeinterfacesocket ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: NodeTreeInterfaceSocketVector2D(NodeTreeInterfaceSocket); NodeTreeInterfaceSocketVector4D(NodeTreeInterfaceSocket); NodeTreeInterfaceSocketVectorAcceleration(NodeTreeInterfaceSocket); NodeTreeInterfaceSocketVectorAcceleration2D(NodeTreeInterfaceSocket); NodeTreeInterfaceSocketVectorAcceleration4D(NodeTreeInterfaceSocket); NodeTreeInterfaceSocketVectorDirection(NodeTreeInterfaceSocket).

## NodeTreeInterfaceSocketVector2D(NodeTreeInterfaceSocket)

### NodeTreeInterfaceSocketVector2D(NodeTreeInterfaceSocket)

base classes — bpy_struct, NodeTreeInterfaceItem, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceSocketVector2D ( NodeTreeInterfaceSocket )

A node socket holding a 3D vector

default_value

Value fed in while the socket stays unlinked (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

bpy_prop_array[float]

dimensions

Component count of the vector socket (in [2, 4], default 0)

Type :

int

max_value

Upper bound on the value (in [-inf, inf], default 0.0)

Type :

float

min_value

Lower bound on the value (in [-inf, inf], default 0.0)

Type :

float

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

## NodeTreeInterfaceSocketVector4D(NodeTreeInterfaceSocket)

### NodeTreeInterfaceSocketVector4D(NodeTreeInterfaceSocket)

base classes — bpy_struct, NodeTreeInterfaceItem, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceSocketVector4D ( NodeTreeInterfaceSocket )

A node socket holding a 3D vector

default_value

Value fed in while the socket stays unlinked (array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

dimensions

Component count of the vector socket (in [2, 4], default 0)

Type :

int

max_value

Upper bound on the value (in [-inf, inf], default 0.0)

Type :

float

min_value

Lower bound on the value (in [-inf, inf], default 0.0)

Type :

float

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

## NodeTreeInterfaceSocketVectorAcceleration(NodeTreeInterfaceSocket)

### NodeTreeInterfaceSocketVectorAcceleration(NodeTreeInterfaceSocket)

base classes — bpy_struct, NodeTreeInterfaceItem, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceSocketVectorAcceleration ( NodeTreeInterfaceSocket )

A node socket holding a 3D vector

default_value

Value fed in while the socket stays unlinked (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

dimensions

Component count of the vector socket (in [2, 4], default 0)

Type :

int

max_value

Upper bound on the value (in [-inf, inf], default 0.0)

Type :

float

min_value

Lower bound on the value (in [-inf, inf], default 0.0)

Type :

float

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

## NodeTreeInterfaceSocketVectorAcceleration2D(NodeTreeInterfaceSocket)

### NodeTreeInterfaceSocketVectorAcceleration2D(NodeTreeInterfaceSocket)

base classes — bpy_struct, NodeTreeInterfaceItem, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceSocketVectorAcceleration2D ( NodeTreeInterfaceSocket )

A node socket holding a 3D vector

default_value

Value fed in while the socket stays unlinked (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

dimensions

Component count of the vector socket (in [2, 4], default 0)

Type :

int

max_value

Upper bound on the value (in [-inf, inf], default 0.0)

Type :

float

min_value

Lower bound on the value (in [-inf, inf], default 0.0)

Type :

float

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

## NodeTreeInterfaceSocketVectorAcceleration4D(NodeTreeInterfaceSocket)

### NodeTreeInterfaceSocketVectorAcceleration4D(NodeTreeInterfaceSocket)

base classes — bpy_struct, NodeTreeInterfaceItem, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceSocketVectorAcceleration4D ( NodeTreeInterfaceSocket )

A node socket holding a 3D vector

default_value

Value fed in while the socket stays unlinked (array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

mathutils.Vector

dimensions

Component count of the vector socket (in [2, 4], default 0)

Type :

int

max_value

Upper bound on the value (in [-inf, inf], default 0.0)

Type :

float

min_value

Lower bound on the value (in [-inf, inf], default 0.0)

Type :

float

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

## NodeTreeInterfaceSocketVectorDirection(NodeTreeInterfaceSocket)

### NodeTreeInterfaceSocketVectorDirection(NodeTreeInterfaceSocket) 

base classes — bpy_struct, NodeTreeInterfaceItem, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceSocketVectorDirection ( NodeTreeInterfaceSocket ) 

A node socket carrying a 3D vector

default_value 

Value supplied to the socket while nothing is wired into it (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

dimensions 

How many components the vector socket exposes (in [2, 4], default 0)

Type :

int

max_value 

Upper bound on the value (in [-inf, inf], default 0.0)

Type :

float

min_value 

Lower bound on the value (in [-inf, inf], default 0.0)

Type :

float

subtype 

Which subtype the default value carries (default 'DEFAULT' )

Type :

Literal[‘DEFAULT’]

draw ( context , layout ) 

Render the configuration controls for this interface socket

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, Layout in the UI (never None)

init_socket ( node , socket , data_path ) 

Set up a fresh instance of a node socket

Parameters :

- node (Node) – Node, Node of the socket to initialize (never None)

- socket (NodeSocket) – Socket, Socket to initialize (never None)

- data_path ( str ) – Data Path, Path to specialized socket data (never None)

from_socket ( node , socket ) 

Populate the template fields by copying them from a socket that already exists

Parameters :

- node (Node) – Node, Node of the original socket (never None)

- socket (NodeSocket) – Socket, Original socket (never None)

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

| bpy_struct.id_data NodeTreeInterfaceItem.item_type NodeTreeInterfaceItem.parent NodeTreeInterfaceItem.position NodeTreeInterfaceItem.index NodeTreeInterfaceSocket.name NodeTreeInterfaceSocket.identifier NodeTreeInterfaceSocket.description NodeTreeInterfaceSocket.socket_type NodeTreeInterfaceSocket.in_out NodeTreeInterfaceSocket.hide_value NodeTreeInterfaceSocket.hide_in_modifier | NodeTreeInterfaceSocket.force_non_field NodeTreeInterfaceSocket.is_inspect_output NodeTreeInterfaceSocket.is_panel_toggle NodeTreeInterfaceSocket.layer_selection_field NodeTreeInterfaceSocket.menu_expanded NodeTreeInterfaceSocket.optional_label NodeTreeInterfaceSocket.select NodeTreeInterfaceSocket.attribute_domain NodeTreeInterfaceSocket.default_attribute_name NodeTreeInterfaceSocket.structure_type NodeTreeInterfaceSocket.default_input NodeTreeInterfaceSocket.bl_socket_idname |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id | bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeTreeInterfaceItem.bl_rna_get_subclass NodeTreeInterfaceItem.bl_rna_get_subclass_py NodeTreeInterfaceSocket.bl_system_properties_get NodeTreeInterfaceSocket.draw NodeTreeInterfaceSocket.init_socket NodeTreeInterfaceSocket.from_socket NodeTreeInterfaceSocket.bl_rna_get_subclass NodeTreeInterfaceSocket.bl_rna_get_subclass_py |
