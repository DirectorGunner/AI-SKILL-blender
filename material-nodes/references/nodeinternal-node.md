# Nodeinternal Node

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### NodeInternal(Node)

base classes — bpy_struct, Node

subclasses —
CompositorNode, FunctionNode, GeometryNode, NodeClosureInput, NodeClosureOutput, NodeCombineBundle, NodeEnableOutput, NodeEvaluateClosure, NodeFrame, NodeGetBundleItem, NodeGroup, NodeGroupInput, NodeGroupOutput, NodeJoinBundle, NodeReroute, NodeSeparateBundle, NodeStoreBundleItem, ShaderNode, TextureNode

class bpy.types. NodeInternal ( Node )

classmethod poll ( node_tree )

When a non-null result comes back, the node type is allowed in the tree

Parameters :

node_tree (NodeTree) – Node Tree

Return type :

bool

poll_instance ( node_tree )

When a non-null result comes back, this node may be placed in the tree

Parameters :

node_tree (NodeTree) – Node Tree

Return type :

bool

update ( )

Run whenever the node graph's topology shifts — nodes or links added or removed

draw_buttons ( context , layout )

Render the node's buttons

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, Layout in the UI (never None)

draw_buttons_ext ( context , layout )

Render the node's buttons within the sidebar

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, Layout in the UI (never None)

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset | bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py |

### References

| GeometryNodeForeachGeometryElementInput.pair_with_output GeometryNodeRepeatInput.pair_with_output | GeometryNodeSimulationInput.pair_with_output NodeClosureInput.pair_with_output |
