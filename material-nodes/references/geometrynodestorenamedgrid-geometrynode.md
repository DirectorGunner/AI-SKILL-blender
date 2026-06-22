# Geometrynodestorenamedgrid Geometrynode, Geometrynodestringjoin Geometrynode, Geometrynodestringtocurves Geometrynode, Geometrynodesubdividecurve Geometrynode ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: GeometryNodeStoreNamedGrid(GeometryNode); GeometryNodeStringJoin(GeometryNode); GeometryNodeStringToCurves(GeometryNode); GeometryNodeSubdivideCurve(GeometryNode); GeometryNodeSubdivideMesh(GeometryNode); GeometryNodeSubdivisionSurface(GeometryNode); GeometryNodeSwitch(GeometryNode).

## GeometryNodeStoreNamedGrid(GeometryNode)

### GeometryNodeStoreNamedGrid(GeometryNode) 

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeStoreNamedGrid ( GeometryNode ) 

Saves grid data into a volume geometry under a chosen name.

data_type 

The value kind held by the grid (default 'FLOAT' )

Type :

Literal[Volume Grid Data Type Items]

classmethod is_registered_node_type ( ) 

Returns whether this node type has been registered.

Returns :

Result

Return type :

bool

classmethod input_template ( index ) 

Template for an input socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index ) 

Template for an output socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The identifier naming the RNA type.

- default (bpy.types.Struct | None) – Value handed back if nothing matches.

Returns :

Either the matching RNA type or the supplied fallback.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The identifier naming the RNA type.

- default ( type | None ) – Value handed back if nothing matches.

Returns :

Either the matching class or the supplied fallback.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py GeometryNode.poll GeometryNode.bl_rna_get_subclass GeometryNode.bl_rna_get_subclass_py |

## GeometryNodeStringJoin(GeometryNode)

### GeometryNodeStringJoin(GeometryNode) 

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeStringJoin ( GeometryNode ) 

Concatenates an arbitrary count of input strings.

classmethod is_registered_node_type ( ) 

Returns whether this node type has been registered.

Returns :

Result

Return type :

bool

classmethod input_template ( index ) 

Template for an input socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index ) 

Template for an output socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The identifier naming the RNA type.

- default (bpy.types.Struct | None) – Value handed back if nothing matches.

Returns :

Either the matching RNA type or the supplied fallback.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The identifier naming the RNA type.

- default ( type | None ) – Value handed back if nothing matches.

Returns :

Either the matching class or the supplied fallback.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py GeometryNode.poll GeometryNode.bl_rna_get_subclass GeometryNode.bl_rna_get_subclass_py |

## GeometryNodeStringToCurves(GeometryNode)

### GeometryNodeStringToCurves(GeometryNode) 

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeStringToCurves ( GeometryNode ) 

Lays out a block of text in a given font, holding each glyph in its own curve instance.

classmethod is_registered_node_type ( ) 

Returns whether this node type has been registered.

Returns :

Result

Return type :

bool

classmethod input_template ( index ) 

Template for an input socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index ) 

Template for an output socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The identifier naming the RNA type.

- default (bpy.types.Struct | None) – Value handed back if nothing matches.

Returns :

Either the matching RNA type or the supplied fallback.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The identifier naming the RNA type.

- default ( type | None ) – Value handed back if nothing matches.

Returns :

Either the matching class or the supplied fallback.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py GeometryNode.poll GeometryNode.bl_rna_get_subclass GeometryNode.bl_rna_get_subclass_py |

## GeometryNodeSubdivideCurve(GeometryNode)

### GeometryNodeSubdivideCurve(GeometryNode) 

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeSubdivideCurve ( GeometryNode ) 

Cuts every curve segment up into a chosen number of pieces.

classmethod is_registered_node_type ( ) 

Returns whether this node type has been registered.

Returns :

Result

Return type :

bool

classmethod input_template ( index ) 

Template for an input socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index ) 

Template for an output socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The identifier naming the RNA type.

- default (bpy.types.Struct | None) – Value handed back if nothing matches.

Returns :

Either the matching RNA type or the supplied fallback.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The identifier naming the RNA type.

- default ( type | None ) – Value handed back if nothing matches.

Returns :

Either the matching class or the supplied fallback.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py GeometryNode.poll GeometryNode.bl_rna_get_subclass GeometryNode.bl_rna_get_subclass_py |

## GeometryNodeSubdivideMesh(GeometryNode)

### GeometryNodeSubdivideMesh(GeometryNode) 

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeSubdivideMesh ( GeometryNode ) 

Splits mesh faces into smaller pieces while preserving the form and volume, positioning the added vertices by linear interpolation.

classmethod is_registered_node_type ( ) 

Returns whether this node type has been registered.

Returns :

Result

Return type :

bool

classmethod input_template ( index ) 

Template for an input socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index ) 

Template for an output socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The identifier naming the RNA type.

- default (bpy.types.Struct | None) – Value handed back if nothing matches.

Returns :

Either the matching RNA type or the supplied fallback.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The identifier naming the RNA type.

- default ( type | None ) – Value handed back if nothing matches.

Returns :

Either the matching class or the supplied fallback.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py GeometryNode.poll GeometryNode.bl_rna_get_subclass GeometryNode.bl_rna_get_subclass_py |

## GeometryNodeSubdivisionSurface(GeometryNode)

### GeometryNodeSubdivisionSurface(GeometryNode) 

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeSubdivisionSurface ( GeometryNode ) 

Refines mesh faces into a smooth surface by applying Catmull-Clark subdivision.

classmethod is_registered_node_type ( ) 

Returns whether this node type has been registered.

Returns :

Result

Return type :

bool

classmethod input_template ( index ) 

Template for an input socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index ) 

Template for an output socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The identifier naming the RNA type.

- default (bpy.types.Struct | None) – Value handed back if nothing matches.

Returns :

Either the matching RNA type or the supplied fallback.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The identifier naming the RNA type.

- default ( type | None ) – Value handed back if nothing matches.

Returns :

Either the matching class or the supplied fallback.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py GeometryNode.poll GeometryNode.bl_rna_get_subclass GeometryNode.bl_rna_get_subclass_py |

## GeometryNodeSwitch(GeometryNode)

### GeometryNodeSwitch(GeometryNode) 

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeSwitch ( GeometryNode ) 

Picks one of a pair of inputs to pass through.

input_type 

(default 'GEOMETRY' )

Type :

Literal[Node Socket Data Type Items]

classmethod is_registered_node_type ( ) 

Returns whether this node type has been registered.

Returns :

Result

Return type :

bool

classmethod input_template ( index ) 

Template for an input socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index ) 

Template for an output socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The identifier naming the RNA type.

- default (bpy.types.Struct | None) – Value handed back if nothing matches.

Returns :

Either the matching RNA type or the supplied fallback.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The identifier naming the RNA type.

- default ( type | None ) – Value handed back if nothing matches.

Returns :

Either the matching class or the supplied fallback.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py GeometryNode.poll GeometryNode.bl_rna_get_subclass GeometryNode.bl_rna_get_subclass_py |
