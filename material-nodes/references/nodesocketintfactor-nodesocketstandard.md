# Nodesocketintfactor Nodesocketstandard, Nodesocketintpercentage Nodesocketstandard, Nodesocketintunsigned Nodesocketstandard, Nodesocketmask Nodesocketstandard ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: NodeSocketIntFactor(NodeSocketStandard); NodeSocketIntPercentage(NodeSocketStandard); NodeSocketIntUnsigned(NodeSocketStandard); NodeSocketMask(NodeSocketStandard); NodeSocketMaterial(NodeSocketStandard); NodeSocketMatrix(NodeSocketStandard); NodeSocketMenu(NodeSocketStandard); NodeSocketObject(NodeSocketStandard); NodeSocketRotation(NodeSocketStandard).

## NodeSocketIntFactor(NodeSocketStandard)

### NodeSocketIntFactor(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketIntFactor ( NodeSocketStandard )

A node socket carrying an integer value.

default_value

(in [0, inf], default 1)

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

## NodeSocketIntPercentage(NodeSocketStandard)

### NodeSocketIntPercentage(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketIntPercentage ( NodeSocketStandard )

A node socket carrying an integer value.

default_value

(in [0, inf], default 100)

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

## NodeSocketIntUnsigned(NodeSocketStandard)

### NodeSocketIntUnsigned(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketIntUnsigned ( NodeSocketStandard )

A node socket carrying an integer value.

default_value

(in [0, inf], default 0)

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

## NodeSocketMask(NodeSocketStandard)

### NodeSocketMask(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketMask ( NodeSocketStandard )

A node socket whose value is a mask.

default_value

Type :

Mask

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

## NodeSocketMaterial(NodeSocketStandard)

### NodeSocketMaterial(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketMaterial ( NodeSocketStandard )

A node socket whose value is a material.

default_value

Type :

Material

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

## NodeSocketMatrix(NodeSocketStandard)

### NodeSocketMatrix(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketMatrix ( NodeSocketStandard )

A node socket carrying a matrix value.

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

## NodeSocketMenu(NodeSocketStandard)

### NodeSocketMenu(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketMenu ( NodeSocketStandard )

A node socket whose value is a menu selection.

default_value

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

## NodeSocketObject(NodeSocketStandard)

### NodeSocketObject(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketObject ( NodeSocketStandard )

A node socket whose value is an object.

default_value

Type :

Object

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

## NodeSocketRotation(NodeSocketStandard)

### NodeSocketRotation(NodeSocketStandard)

base classes — bpy_struct, NodeSocket, NodeSocketStandard

class bpy.types. NodeSocketRotation ( NodeSocketStandard )

A node socket carrying a rotation value.

default_value

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Euler

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
