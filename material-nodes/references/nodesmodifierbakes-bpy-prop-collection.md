# Nodesmodifierbakes Bpy Prop Collection, Nodesmodifierpanels Bpy Prop Collection, Nodesmodifierwarning Bpy Struct, Nodesocket Bpy Struct ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: NodesModifierBakes(bpy_prop_collection); NodesModifierPanels(bpy_prop_collection); NodesModifierWarning(bpy_struct); NodeSocket(bpy_struct); NodeSocketBool(NodeSocketStandard); NodeSocketBundle(NodeSocketStandard); NodeSocketClosure(NodeSocketStandard).

## NodesModifierBakes(bpy_prop_collection)

### NodesModifierBakes(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodesModifierBakes ( bpy_prop_collection )

Stored bake data for each bake node.

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

## NodesModifierPanels(bpy_prop_collection)

### NodesModifierPanels(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodesModifierPanels ( bpy_prop_collection )

Current state of every panel the node group declares.

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

| NodesModifier.panels | |

## NodesModifierWarning(bpy_struct)

### NodesModifierWarning(bpy_struct)

base class — bpy_struct

class bpy.types. NodesModifierWarning ( bpy_struct )

A warning raised while a geometry nodes modifier is being evaluated

message

(default “”, readonly, never None)

Type :

str

type

(default 'ERROR' , readonly)

Type :

Literal[Node Warning Type Items]

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

| NodesModifier.node_warnings | |

## NodeSocket(bpy_struct)

### NodeSocket(bpy_struct)

base class — bpy_struct

subclasses —
NodeSocketStandard

class bpy.types. NodeSocket ( bpy_struct )

A node's input or output socket

bl_idname

(default “”, never None)

Type :

str

bl_label

The UI text shown for this socket type (default “”, never None)

Type :

str

bl_subtype_label

The UI text shown for this socket subtype (default “”, never None)

Type :

str

description

Socket tooltip (default “”, never None)

Type :

str

display_shape

Socket shape (default 'CIRCLE' )

Type :

Literal[‘CIRCLE’, ‘SQUARE’, ‘DIAMOND’, ‘`CIRCLE_DOT`’, ‘`SQUARE_DOT`’, ‘`DIAMOND_DOT`’, ‘LINE’, ‘`VOLUME_GRID`’, ‘LIST’]

enabled

Turn the socket on (default True)

Type :

bool

hide

Conceal the socket (default False)

Type :

bool

hide_value

Conceal the socket's input value (default False)

Type :

bool

identifier

Unique identifier for mapping sockets (default “”, readonly, never None)

Type :

str

inferred_structure_type

The socket's best-guess structure type; it can differ from the socket shape, such as for unlinked inputs (default 'AUTO' , readonly)

Type :

Literal[Node Socket Structure Type Items]

is_icon_visible

The socket appears as an interactive icon in the node editor (default False, readonly)

Type :

bool

is_inactive

The socket is dimmed because it was found to have no bearing on the output (default False, readonly)

Type :

bool

is_linked

True if the socket is connected (default False, readonly)

Type :

bool

is_multi_input

True if the socket can accept multiple ordered input links (default False, readonly)

Type :

bool

is_output

True if the socket is an output, otherwise input (default False, readonly)

Type :

bool

is_unavailable

True if the socket is unavailable (default False, readonly)

Type :

bool

label

A custom, dynamically set UI label for the socket; it is translatable when translation is turned on in the preferences (default “”, readonly, never None)

Type :

str

link_limit

Max number of links allowed for this socket (in [1, 4095], default 0)

Type :

int

name

Socket name (default “”, never None)

Type :

str

node

Node owning this socket (readonly)

Type :

Node

pin_gizmo

Keep the gizmo on screen even while the node is unselected (default False)

Type :

bool

select

True if the socket is selected (default False, readonly)

Type :

bool

show_expanded

The socket's links are shown unfolded in the user interface (default True)

Type :

bool

type

Data type (default 'VALUE' )

Type :

Literal[Node Socket Type Items]

links

List of node links from or to this socket.

Type :

NodeLinks

Note

Takes O(len(nodetree.links)) time.

(readonly)

bl_system_properties_get ( * , do_create = False )

DEBUG ONLY. Internal access to runtime-defined RNA data storage, intended solely for testing and debugging purposes. Do not access it in regular scripting work, and in particular, do not assume that it contains writable data

Parameters :

do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)

Returns :

The system properties root container, or None if there are no system properties stored in this data yet, and its creation was not requested

Return type :

PropertyGroup

draw ( context , layout , node , text )

Draw socket

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, Layout in the UI (never None)

- node (Node) – Node, Node the socket belongs to (never None)

- text ( str ) – Text, Text label to draw alongside properties (never None)

draw_color ( context , node )

Color of the socket icon

Parameters :

- context (Context) – (never None)

- node (Node) – Node, Node the socket belongs to (never None)

Returns :

Color, (array of 4 items, in [0, 1])

Return type :

bpy_prop_array[float]

classmethod draw_color_simple ( )

Color of the socket icon. Used to draw sockets in places where the socket does not belong to a node, like the node interface panel. Also used to draw node sockets if draw_color is not defined.

Returns :

Color, (array of 4 items, in [0, 1])

Return type :

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

| Node.inputs Node.outputs NodeInputs.new NodeInputs.remove NodeLink.from_socket NodeLink.to_socket NodeLinks.new NodeLinks.new NodeOutputs.new NodeOutputs.remove NodeTreeInterfaceSocket.from_socket NodeTreeInterfaceSocket.init_socket NodeTreeInterfaceSocketBool.from_socket NodeTreeInterfaceSocketBool.init_socket NodeTreeInterfaceSocketBundle.from_socket NodeTreeInterfaceSocketBundle.init_socket NodeTreeInterfaceSocketClosure.from_socket NodeTreeInterfaceSocketClosure.init_socket NodeTreeInterfaceSocketCollection.from_socket NodeTreeInterfaceSocketCollection.init_socket NodeTreeInterfaceSocketColor.from_socket NodeTreeInterfaceSocketColor.init_socket NodeTreeInterfaceSocketFloat.from_socket NodeTreeInterfaceSocketFloat.init_socket NodeTreeInterfaceSocketFloatAngle.from_socket NodeTreeInterfaceSocketFloatAngle.init_socket NodeTreeInterfaceSocketFloatColorTemperature.from_socket NodeTreeInterfaceSocketFloatColorTemperature.init_socket NodeTreeInterfaceSocketFloatDistance.from_socket NodeTreeInterfaceSocketFloatDistance.init_socket NodeTreeInterfaceSocketFloatFactor.from_socket NodeTreeInterfaceSocketFloatFactor.init_socket NodeTreeInterfaceSocketFloatFrequency.from_socket NodeTreeInterfaceSocketFloatFrequency.init_socket NodeTreeInterfaceSocketFloatMass.from_socket NodeTreeInterfaceSocketFloatMass.init_socket NodeTreeInterfaceSocketFloatPercentage.from_socket NodeTreeInterfaceSocketFloatPercentage.init_socket NodeTreeInterfaceSocketFloatTime.from_socket NodeTreeInterfaceSocketFloatTime.init_socket NodeTreeInterfaceSocketFloatTimeAbsolute.from_socket NodeTreeInterfaceSocketFloatTimeAbsolute.init_socket NodeTreeInterfaceSocketFloatUnsigned.from_socket NodeTreeInterfaceSocketFloatUnsigned.init_socket NodeTreeInterfaceSocketFloatWavelength.from_socket NodeTreeInterfaceSocketFloatWavelength.init_socket NodeTreeInterfaceSocketGeometry.from_socket NodeTreeInterfaceSocketGeometry.init_socket NodeTreeInterfaceSocketImage.from_socket NodeTreeInterfaceSocketImage.init_socket NodeTreeInterfaceSocketInt.from_socket NodeTreeInterfaceSocketInt.init_socket NodeTreeInterfaceSocketIntFactor.from_socket NodeTreeInterfaceSocketIntFactor.init_socket NodeTreeInterfaceSocketIntPercentage.from_socket NodeTreeInterfaceSocketIntPercentage.init_socket NodeTreeInterfaceSocketIntUnsigned.from_socket NodeTreeInterfaceSocketIntUnsigned.init_socket NodeTreeInterfaceSocketMaterial.from_socket NodeTreeInterfaceSocketMaterial.init_socket NodeTreeInterfaceSocketMatrix.from_socket NodeTreeInterfaceSocketMatrix.init_socket NodeTreeInterfaceSocketMenu.from_socket NodeTreeInterfaceSocketMenu.init_socket NodeTreeInterfaceSocketObject.from_socket NodeTreeInterfaceSocketObject.init_socket | NodeTreeInterfaceSocketRotation.from_socket NodeTreeInterfaceSocketRotation.init_socket NodeTreeInterfaceSocketShader.from_socket NodeTreeInterfaceSocketShader.init_socket NodeTreeInterfaceSocketString.from_socket NodeTreeInterfaceSocketString.init_socket NodeTreeInterfaceSocketStringFilePath.from_socket NodeTreeInterfaceSocketStringFilePath.init_socket NodeTreeInterfaceSocketTexture.from_socket NodeTreeInterfaceSocketTexture.init_socket NodeTreeInterfaceSocketVector.from_socket NodeTreeInterfaceSocketVector.init_socket NodeTreeInterfaceSocketVector2D.from_socket NodeTreeInterfaceSocketVector2D.init_socket NodeTreeInterfaceSocketVector4D.from_socket NodeTreeInterfaceSocketVector4D.init_socket NodeTreeInterfaceSocketVectorAcceleration.from_socket NodeTreeInterfaceSocketVectorAcceleration.init_socket NodeTreeInterfaceSocketVectorAcceleration2D.from_socket NodeTreeInterfaceSocketVectorAcceleration2D.init_socket NodeTreeInterfaceSocketVectorAcceleration4D.from_socket NodeTreeInterfaceSocketVectorAcceleration4D.init_socket NodeTreeInterfaceSocketVectorDirection.from_socket NodeTreeInterfaceSocketVectorDirection.init_socket NodeTreeInterfaceSocketVectorDirection2D.from_socket NodeTreeInterfaceSocketVectorDirection2D.init_socket NodeTreeInterfaceSocketVectorDirection4D.from_socket NodeTreeInterfaceSocketVectorDirection4D.init_socket NodeTreeInterfaceSocketVectorEuler.from_socket NodeTreeInterfaceSocketVectorEuler.init_socket NodeTreeInterfaceSocketVectorEuler2D.from_socket NodeTreeInterfaceSocketVectorEuler2D.init_socket NodeTreeInterfaceSocketVectorEuler4D.from_socket NodeTreeInterfaceSocketVectorEuler4D.init_socket NodeTreeInterfaceSocketVectorFactor.from_socket NodeTreeInterfaceSocketVectorFactor.init_socket NodeTreeInterfaceSocketVectorFactor2D.from_socket NodeTreeInterfaceSocketVectorFactor2D.init_socket NodeTreeInterfaceSocketVectorFactor4D.from_socket NodeTreeInterfaceSocketVectorFactor4D.init_socket NodeTreeInterfaceSocketVectorPercentage.from_socket NodeTreeInterfaceSocketVectorPercentage.init_socket NodeTreeInterfaceSocketVectorPercentage2D.from_socket NodeTreeInterfaceSocketVectorPercentage2D.init_socket NodeTreeInterfaceSocketVectorPercentage4D.from_socket NodeTreeInterfaceSocketVectorPercentage4D.init_socket NodeTreeInterfaceSocketVectorTranslation.from_socket NodeTreeInterfaceSocketVectorTranslation.init_socket NodeTreeInterfaceSocketVectorTranslation2D.from_socket NodeTreeInterfaceSocketVectorTranslation2D.init_socket NodeTreeInterfaceSocketVectorTranslation4D.from_socket NodeTreeInterfaceSocketVectorTranslation4D.init_socket NodeTreeInterfaceSocketVectorVelocity.from_socket NodeTreeInterfaceSocketVectorVelocity.init_socket NodeTreeInterfaceSocketVectorVelocity2D.from_socket NodeTreeInterfaceSocketVectorVelocity2D.init_socket NodeTreeInterfaceSocketVectorVelocity4D.from_socket NodeTreeInterfaceSocketVectorVelocity4D.init_socket NodeTreeInterfaceSocketVectorXYZ.from_socket NodeTreeInterfaceSocketVectorXYZ.init_socket NodeTreeInterfaceSocketVectorXYZ2D.from_socket NodeTreeInterfaceSocketVectorXYZ2D.init_socket NodeTreeInterfaceSocketVectorXYZ4D.from_socket NodeTreeInterfaceSocketVectorXYZ4D.init_socket UILayout.template_node_link UILayout.template_node_view |

## NodeSocketBool(NodeSocketStandard)

### NodeSocketBool(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketBool ( NodeSocketStandard )

A node socket carrying a boolean value

default_value

(default False)

Type :

bool

links

List of node links from or to this socket.

Type :

NodeLinks

Note

Takes O(len(nodetree.links)) time.

(readonly)

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

| bpy_struct.id_data NodeSocket.name NodeSocket.label NodeSocket.identifier NodeSocket.description NodeSocket.is_output NodeSocket.select NodeSocket.hide NodeSocket.enabled NodeSocket.link_limit NodeSocket.is_linked NodeSocket.is_unavailable NodeSocket.is_multi_input NodeSocket.show_expanded | NodeSocket.is_inactive NodeSocket.is_icon_visible NodeSocket.hide_value NodeSocket.pin_gizmo NodeSocket.node NodeSocket.type NodeSocket.display_shape NodeSocket.inferred_structure_type NodeSocket.bl_idname NodeSocket.bl_label NodeSocket.bl_subtype_label NodeSocket.links NodeSocketStandard.links |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeSocket.bl_system_properties_get NodeSocket.draw NodeSocket.draw_color NodeSocket.draw_color_simple NodeSocket.bl_rna_get_subclass NodeSocket.bl_rna_get_subclass_py NodeSocketStandard.draw NodeSocketStandard.draw_color NodeSocketStandard.draw_color_simple NodeSocketStandard.bl_rna_get_subclass NodeSocketStandard.bl_rna_get_subclass_py |

## NodeSocketBundle(NodeSocketStandard)

### NodeSocketBundle(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketBundle ( NodeSocketStandard )

A node socket whose value is a bundle.

links

The set of links entering or leaving this socket.

Type :

NodeLinks

Note

Runs in O(len(nodetree.links)).

(readonly)

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier string for the RNA type.

- default (bpy.types.Struct | None) – Fallback returned if no match is found.

Returns :

The matching RNA type, or the fallback when nothing matches.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier string for the RNA type.

- default ( type | None ) – Fallback returned if no match is found.

Returns :

The matching class, or the fallback when nothing matches.

Return type :

type

### Inherited Properties

| bpy_struct.id_data NodeSocket.name NodeSocket.label NodeSocket.identifier NodeSocket.description NodeSocket.is_output NodeSocket.select NodeSocket.hide NodeSocket.enabled NodeSocket.link_limit NodeSocket.is_linked NodeSocket.is_unavailable NodeSocket.is_multi_input NodeSocket.show_expanded | NodeSocket.is_inactive NodeSocket.is_icon_visible NodeSocket.hide_value NodeSocket.pin_gizmo NodeSocket.node NodeSocket.type NodeSocket.display_shape NodeSocket.inferred_structure_type NodeSocket.bl_idname NodeSocket.bl_label NodeSocket.bl_subtype_label NodeSocket.links NodeSocketStandard.links |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeSocket.bl_system_properties_get NodeSocket.draw NodeSocket.draw_color NodeSocket.draw_color_simple NodeSocket.bl_rna_get_subclass NodeSocket.bl_rna_get_subclass_py NodeSocketStandard.draw NodeSocketStandard.draw_color NodeSocketStandard.draw_color_simple NodeSocketStandard.bl_rna_get_subclass NodeSocketStandard.bl_rna_get_subclass_py |

## NodeSocketClosure(NodeSocketStandard)

### NodeSocketClosure(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketClosure ( NodeSocketStandard )

A node socket whose value is a closure.

links

The set of links entering or leaving this socket.

Type :

NodeLinks

Note

Runs in O(len(nodetree.links)).

(readonly)

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier string for the RNA type.

- default (bpy.types.Struct | None) – Fallback returned if no match is found.

Returns :

The matching RNA type, or the fallback when nothing matches.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier string for the RNA type.

- default ( type | None ) – Fallback returned if no match is found.

Returns :

The matching class, or the fallback when nothing matches.

Return type :

type

### Inherited Properties

| bpy_struct.id_data NodeSocket.name NodeSocket.label NodeSocket.identifier NodeSocket.description NodeSocket.is_output NodeSocket.select NodeSocket.hide NodeSocket.enabled NodeSocket.link_limit NodeSocket.is_linked NodeSocket.is_unavailable NodeSocket.is_multi_input NodeSocket.show_expanded | NodeSocket.is_inactive NodeSocket.is_icon_visible NodeSocket.hide_value NodeSocket.pin_gizmo NodeSocket.node NodeSocket.type NodeSocket.display_shape NodeSocket.inferred_structure_type NodeSocket.bl_idname NodeSocket.bl_label NodeSocket.bl_subtype_label NodeSocket.links NodeSocketStandard.links |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeSocket.bl_system_properties_get NodeSocket.draw NodeSocket.draw_color NodeSocket.draw_color_simple NodeSocket.bl_rna_get_subclass NodeSocket.bl_rna_get_subclass_py NodeSocketStandard.draw NodeSocketStandard.draw_color NodeSocketStandard.draw_color_simple NodeSocketStandard.bl_rna_get_subclass NodeSocketStandard.bl_rna_get_subclass_py |

## See also

- [Bpy Struct](bpy-struct.md)
