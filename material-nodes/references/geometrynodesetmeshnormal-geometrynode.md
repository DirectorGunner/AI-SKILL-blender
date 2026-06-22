# Geometrynodesetmeshnormal Geometrynode, Geometrynodesetpointradius Geometrynode, Geometrynodesetposition Geometrynode, Geometrynodesetshadesmooth Geometrynode ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: GeometryNodeSetMeshNormal(GeometryNode); GeometryNodeSetPointRadius(GeometryNode); GeometryNodeSetPosition(GeometryNode); GeometryNodeSetShadeSmooth(GeometryNode); GeometryNodeSetSplineCyclic(GeometryNode); GeometryNodeSetSplineResolution(GeometryNode); GeometryNodeSimulationInput(GeometryNode).

## GeometryNodeSetMeshNormal(GeometryNode)

### GeometryNodeSetMeshNormal(GeometryNode) 

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeSetMeshNormal ( GeometryNode ) 

Records a normal vector against each element of a mesh.

domain 

The attribute domain where free custom normals get kept (default 'POINT' )

Type :

Literal[Attribute Domain Only Mesh No Edge Items]

mode 

How custom normal data is held (default 'SHARPNESS' )

- SHARPNESS
Sharpness – Keeps a per-face or per-edge sharpness value, working much like the “Shade Smooth” and “Shade Flat” operators..

- FREE
Free – Holds custom normals as plain vectors expressed in the mesh's local space; these are not guaranteed to refresh on their own when the mesh is later deformed..

- `TANGENT_SPACE`
Tangent Space – Holds normals within a custom transformation space that follows deformation. It runs slower, yet tends to behave better when later operations alter the mesh without dealing with normals directly..

Type :

Literal[‘SHARPNESS’, ‘FREE’, ‘`TANGENT_SPACE`’]

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

## GeometryNodeSetPointRadius(GeometryNode)

### GeometryNodeSetPointRadius(GeometryNode) 

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeSetPointRadius ( GeometryNode ) 

Controls the on-screen size at which point cloud points are drawn.

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

## GeometryNodeSetPosition(GeometryNode)

### GeometryNodeSetPosition(GeometryNode) 

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeSetPosition ( GeometryNode ) 

Places each point at a new location.

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

## GeometryNodeSetShadeSmooth(GeometryNode)

### GeometryNodeSetShadeSmooth(GeometryNode) 

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeSetShadeSmooth ( GeometryNode ) 

Adjusts how smoothly mesh normals blend across faces by editing the “shade smooth” attribute.

domain 

(default 'EDGE' )

Type :

Literal[Attribute Domain Edge Face Items]

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

## GeometryNodeSetSplineCyclic(GeometryNode)

### GeometryNodeSetSplineCyclic(GeometryNode) 

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeSetSplineCyclic ( GeometryNode ) 

Toggles whether a spline closes into a loop by editing the “cyclic” attribute.

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

## GeometryNodeSetSplineResolution(GeometryNode)

### GeometryNodeSetSplineResolution(GeometryNode) 

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeSetSplineResolution ( GeometryNode ) 

Determines the count of evaluated points placed along every curve segment.

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

## GeometryNodeSimulationInput(GeometryNode)

### GeometryNodeSimulationInput(GeometryNode) 

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeSimulationInput ( GeometryNode ) 

Feeds data into the simulation zone.

paired_output 

The zone's output node that this input node is matched to (readonly)

Type :

Node

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

pair_with_output ( output_node ) 

Links a zone input node to its output node.

Parameters :

output_node (NodeInternal) – Output Node, the zone output node to be paired

Returns :

Result, True when the nodes were successfully paired

Return type :

bool

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
