# Functionnodeslicestring Functionnode, Functionnodestringlength Functionnode, Functionnodestringtovalue Functionnode, Functionnodetransformdirection Functionnode ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: FunctionNodeSliceString(FunctionNode); FunctionNodeStringLength(FunctionNode); FunctionNodeStringToValue(FunctionNode); FunctionNodeTransformDirection(FunctionNode); FunctionNodeTransformPoint(FunctionNode); FunctionNodeTransposeMatrix(FunctionNode); FunctionNodeValueToString(FunctionNode).

## FunctionNodeSliceString(FunctionNode)

### FunctionNodeSliceString(FunctionNode)

base classes — bpy_struct, Node, NodeInternal, FunctionNode

class bpy.types. FunctionNodeSliceString ( FunctionNode )

Pulls a substring out of a longer string.

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py FunctionNode.bl_rna_get_subclass FunctionNode.bl_rna_get_subclass_py |

## FunctionNodeStringLength(FunctionNode)

### FunctionNodeStringLength(FunctionNode)

base classes — bpy_struct, Node, NodeInternal, FunctionNode

class bpy.types. FunctionNodeStringLength ( FunctionNode )

Reports how many characters a string contains.

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py FunctionNode.bl_rna_get_subclass FunctionNode.bl_rna_get_subclass_py |

## FunctionNodeStringToValue(FunctionNode)

### FunctionNodeStringToValue(FunctionNode)

base classes — bpy_struct, Node, NodeInternal, FunctionNode

class bpy.types. FunctionNodeStringToValue ( FunctionNode )

Parses a number out of its string form.

data_type

(default 'FLOAT' )

- FLOAT
Float – Floating-point value.

- INT
Integer – 32-bit integer.

Type :

Literal[‘FLOAT’, ‘INT’]

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py FunctionNode.bl_rna_get_subclass FunctionNode.bl_rna_get_subclass_py |

## FunctionNodeTransformDirection(FunctionNode)

### FunctionNodeTransformDirection(FunctionNode)

base classes — bpy_struct, Node, NodeInternal, FunctionNode

class bpy.types. FunctionNodeTransformDirection ( FunctionNode )

Runs a vector through a transformation matrix while ignoring its translation part.

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py FunctionNode.bl_rna_get_subclass FunctionNode.bl_rna_get_subclass_py |

## FunctionNodeTransformPoint(FunctionNode)

### FunctionNodeTransformPoint(FunctionNode)

base classes — bpy_struct, Node, NodeInternal, FunctionNode

class bpy.types. FunctionNodeTransformPoint ( FunctionNode )

Runs a vector through a transformation matrix.

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py FunctionNode.bl_rna_get_subclass FunctionNode.bl_rna_get_subclass_py |

## FunctionNodeTransposeMatrix(FunctionNode)

### FunctionNodeTransposeMatrix(FunctionNode)

base classes — bpy_struct, Node, NodeInternal, FunctionNode

class bpy.types. FunctionNodeTransposeMatrix ( FunctionNode )

Mirrors a matrix across its diagonal so that rows and columns swap roles.

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py FunctionNode.bl_rna_get_subclass FunctionNode.bl_rna_get_subclass_py |

## FunctionNodeValueToString(FunctionNode)

### FunctionNodeValueToString(FunctionNode)

base classes — bpy_struct, Node, NodeInternal, FunctionNode

class bpy.types. FunctionNodeValueToString ( FunctionNode )

Writes the supplied input value out as a string.

data_type

(default 'FLOAT' )

- FLOAT
Float – Floating-point value.

- INT
Integer – 32-bit integer.

Type :

Literal[‘FLOAT’, ‘INT’]

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py FunctionNode.bl_rna_get_subclass FunctionNode.bl_rna_get_subclass_py |
