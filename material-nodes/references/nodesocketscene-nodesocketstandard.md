# Nodesocketscene Nodesocketstandard, Nodesocketshader Nodesocketstandard, Nodesocketsound Nodesocketstandard, Nodesocketstandard Nodesocket ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: NodeSocketScene(NodeSocketStandard); NodeSocketShader(NodeSocketStandard); NodeSocketSound(NodeSocketStandard); NodeSocketStandard(NodeSocket); NodeSocketString(NodeSocketStandard); NodeSocketStringFilePath(NodeSocketStandard); NodeSocketText(NodeSocketStandard); NodeSocketTexture(NodeSocketStandard).

## NodeSocketScene(NodeSocketStandard)

### NodeSocketScene(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketScene ( NodeSocketStandard )

A node socket whose value is a scene.

default_value

Type :

Scene

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

## NodeSocketShader(NodeSocketStandard)

### NodeSocketShader(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketShader ( NodeSocketStandard )

A node socket whose value is a shader.

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

## NodeSocketSound(NodeSocketStandard)

### NodeSocketSound(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketSound ( NodeSocketStandard )

A node socket whose value is a sound.

default_value

Type :

Sound

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

## NodeSocketStandard(NodeSocket)

### NodeSocketStandard(NodeSocket)

base classes — bpy_struct, NodeSocket

subclasses —
NodeSocketBool, NodeSocketBundle, NodeSocketClosure, NodeSocketCollection, NodeSocketColor, NodeSocketFloat, NodeSocketFloatAngle, NodeSocketFloatColorTemperature, NodeSocketFloatDistance, NodeSocketFloatFactor, NodeSocketFloatFrequency, NodeSocketFloatMass, NodeSocketFloatPercentage, NodeSocketFloatTime, NodeSocketFloatTimeAbsolute, NodeSocketFloatUnsigned, NodeSocketFloatWavelength, NodeSocketFont, NodeSocketGeometry, NodeSocketImage, NodeSocketInt, NodeSocketIntFactor, NodeSocketIntPercentage, NodeSocketIntUnsigned, NodeSocketMask, NodeSocketMaterial, NodeSocketMatrix, NodeSocketMenu, NodeSocketObject, NodeSocketRotation, NodeSocketScene, NodeSocketShader, NodeSocketSound, NodeSocketString, NodeSocketStringFilePath, NodeSocketText, NodeSocketTexture, NodeSocketVector, NodeSocketVector2D, NodeSocketVector4D, NodeSocketVectorAcceleration, NodeSocketVectorAcceleration2D, NodeSocketVectorAcceleration4D, NodeSocketVectorDirection, NodeSocketVectorDirection2D, NodeSocketVectorDirection4D, NodeSocketVectorEuler, NodeSocketVectorEuler2D, NodeSocketVectorEuler4D, NodeSocketVectorFactor, NodeSocketVectorFactor2D, NodeSocketVectorFactor4D, NodeSocketVectorPercentage, NodeSocketVectorPercentage2D, NodeSocketVectorPercentage4D, NodeSocketVectorTranslation, NodeSocketVectorTranslation2D, NodeSocketVectorTranslation4D, NodeSocketVectorVelocity, NodeSocketVectorVelocity2D, NodeSocketVectorVelocity4D, NodeSocketVectorXYZ, NodeSocketVectorXYZ2D, NodeSocketVectorXYZ4D, NodeSocketVirtual

class bpy.types. NodeSocketStandard ( NodeSocket )

links

The set of links entering or leaving this socket.

Type :

NodeLinks

Note

Runs in O(len(nodetree.links)).

(readonly)

draw ( context , layout , node , text )

Render the socket.

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, Layout in the UI (never None)

- node (Node) – Node, Node the socket belongs to (never None)

- text ( str ) – Text, Text label to draw alongside properties (never None)

draw_color ( context , node )

Icon color for the socket.

Parameters :

- context (Context) – (never None)

- node (Node) – Node, Node the socket belongs to (never None)

Returns :

Color, (array of 4 items, in [0, 1])

Return type :

bpy_prop_array[float]

classmethod draw_color_simple ( )

Icon color for the socket.

Returns :

Color, (array of 4 items, in [0, 1])

Return type :

bpy_prop_array[float]

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

| bpy_struct.id_data NodeSocket.name NodeSocket.label NodeSocket.identifier NodeSocket.description NodeSocket.is_output NodeSocket.select NodeSocket.hide NodeSocket.enabled NodeSocket.link_limit NodeSocket.is_linked NodeSocket.is_unavailable NodeSocket.is_multi_input | NodeSocket.show_expanded NodeSocket.is_inactive NodeSocket.is_icon_visible NodeSocket.hide_value NodeSocket.pin_gizmo NodeSocket.node NodeSocket.type NodeSocket.display_shape NodeSocket.inferred_structure_type NodeSocket.bl_idname NodeSocket.bl_label NodeSocket.bl_subtype_label NodeSocket.links |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys | bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeSocket.bl_system_properties_get NodeSocket.draw NodeSocket.draw_color NodeSocket.draw_color_simple NodeSocket.bl_rna_get_subclass NodeSocket.bl_rna_get_subclass_py |

## NodeSocketString(NodeSocketStandard)

### NodeSocketString(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketString ( NodeSocketStandard )

A node socket carrying a string value.

default_value

(default “”, never None)

Type :

str

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

## NodeSocketStringFilePath(NodeSocketStandard)

### NodeSocketStringFilePath(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketStringFilePath ( NodeSocketStandard )

A node socket carrying a string value.

default_value

(default “”, never None, blend relative // prefix supported)

Type :

str

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

## NodeSocketText(NodeSocketStandard)

### NodeSocketText(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketText ( NodeSocketStandard )

A node socket whose value is a text block.

default_value

Type :

Text

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

## NodeSocketTexture(NodeSocketStandard)

### NodeSocketTexture(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketTexture ( NodeSocketStandard )

A node socket whose value is a texture.

default_value

Type :

Texture

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
