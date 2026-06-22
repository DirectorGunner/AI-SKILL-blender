# Nodesocketfloatpercentage Nodesocketstandard, Nodesocketfloattime Nodesocketstandard, Nodesocketfloattimeabsolute Nodesocketstandard, Nodesocketfloatunsigned Nodesocketstandard ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: NodeSocketFloatPercentage(NodeSocketStandard); NodeSocketFloatTime(NodeSocketStandard); NodeSocketFloatTimeAbsolute(NodeSocketStandard); NodeSocketFloatUnsigned(NodeSocketStandard); NodeSocketFloatWavelength(NodeSocketStandard); NodeSocketFont(NodeSocketStandard); NodeSocketGeometry(NodeSocketStandard); NodeSocketImage(NodeSocketStandard); NodeSocketInt(NodeSocketStandard).

## NodeSocketFloatPercentage(NodeSocketStandard)

### NodeSocketFloatPercentage(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketFloatPercentage ( NodeSocketStandard )

A node socket carrying a floating-point value.

default_value

(in [-inf, inf], default 0.0)

Type :

float

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

## NodeSocketFloatTime(NodeSocketStandard)

### NodeSocketFloatTime(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketFloatTime ( NodeSocketStandard )

A node socket carrying a floating-point value.

default_value

(in [-inf, inf], default 0.0)

Type :

float

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

## NodeSocketFloatTimeAbsolute(NodeSocketStandard)

### NodeSocketFloatTimeAbsolute(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketFloatTimeAbsolute ( NodeSocketStandard )

A node socket carrying a floating-point value.

default_value

(in [-inf, inf], default 0.0)

Type :

float

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

## NodeSocketFloatUnsigned(NodeSocketStandard)

### NodeSocketFloatUnsigned(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketFloatUnsigned ( NodeSocketStandard )

A node socket carrying a floating-point value.

default_value

(in [0, inf], default 0.0)

Type :

float

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

## NodeSocketFloatWavelength(NodeSocketStandard)

### NodeSocketFloatWavelength(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketFloatWavelength ( NodeSocketStandard )

A node socket carrying a floating-point value.

default_value

(in [-inf, inf], default 0.0)

Type :

float

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

## NodeSocketFont(NodeSocketStandard)

### NodeSocketFont(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketFont ( NodeSocketStandard )

A node socket whose value is a font.

default_value

Type :

VectorFont

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

## NodeSocketGeometry(NodeSocketStandard)

### NodeSocketGeometry(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketGeometry ( NodeSocketStandard )

A node socket whose value is geometry.

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

## NodeSocketImage(NodeSocketStandard)

### NodeSocketImage(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketImage ( NodeSocketStandard )

A node socket whose value is an image.

default_value

Type :

Image

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

## NodeSocketInt(NodeSocketStandard)

### NodeSocketInt(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketInt ( NodeSocketStandard )

A node socket carrying an integer value.

default_value

(in [-inf, inf], default 0)

Type :

int

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
