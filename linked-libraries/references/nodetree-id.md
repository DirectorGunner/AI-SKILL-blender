# Nodetree Id, Nodetreeinterfacesocket Nodetreeinterfaceitem

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: NodeTree(ID); NodeTreeInterfaceSocket(NodeTreeInterfaceItem).

## NodeTree(ID)

### NodeTree(ID) 

### Poll Function 

Through NodeTree.poll, a node tree decides whether it should appear within a
given context — the same role Panel.poll and Menu.poll play for their own
visibility. When the function yields False, that node tree type stays out of
the picker in the node editor.

For shader node trees, a common check inspects the scene's currently active
render engine, exposing only the nodes that target that specific renderer.

`	ext
import bpy

class CyclesNodeTree(bpy.types.NodeTree):
""" This operator is only visible when Cycles is the selected render engine"""
bl_label = "Cycles Node Tree"
bl_icon = 'NONE'

@classmethod
def poll(cls, context):
return context.scene.render.engine == 'CYCLES'

bpy.utils.register_class(CyclesNodeTree)
`

base classes — bpy_struct, ID

subclasses —
CompositorNodeTree, GeometryNodeTree, ShaderNodeTree, TextureNodeTree

class bpy.types. NodeTree ( ID ) 

A tree of connected nodes that drives shading, texturing, and compositing.

animation_data 

Animation data for this data-block (readonly)

Type :

AnimData

annotation 

Annotation data

Type :

Annotation

bl_description 

(default “”, never None)

Type :

str

bl_icon 

Icon shown for the node tree (default 'NODETREE' )

Type :

Literal[Icon Items]

bl_idname 

(default “”, never None)

Type :

str

bl_label 

Label shown for the node tree (default “”, never None)

Type :

str

bl_use_group_interface 

Controls whether certain node-group-related UI elements are shown (default True)

Type :

bool

color_tag 

The node group's color tag, which tints its header (default 'NONE' )

- NONE
None – Default color tag for new nodes and node groups.

- ATTRIBUTE
Attribute.

- COLOR
Color.

- CONVERTER
Converter.

- DISTORT
Distort.

- FILTER
Filter.

- GEOMETRY
Geometry.

- INPUT
Input.

- MATTE
Matte.

- OUTPUT
Output.

- SCRIPT
Script.

- SHADER
Shader.

- TEXTURE
Texture.

- VECTOR
Vector.

- PATTERN
Pattern.

- INTERFACE
Interface.

- GROUP
Group.

Type :

Literal[‘NONE’, ‘ATTRIBUTE’, ‘COLOR’, ‘CONVERTER’, ‘DISTORT’, ‘FILTER’, ‘GEOMETRY’, ‘INPUT’, ‘MATTE’, ‘OUTPUT’, ‘SCRIPT’, ‘SHADER’, ‘TEXTURE’, ‘VECTOR’, ‘PATTERN’, ‘INTERFACE’, ‘GROUP’]

default_group_node_width 

Width given to freshly added group nodes (in [60, 700], default 140)

Type :

int

description 

Text describing the node tree (default “”, never None)

Type :

str

interface 

This node tree's interface declaration (readonly)

Type :

NodeTreeInterface

links 

(default None, readonly)

Type :

NodeLinks[NodeLink]

nodes 

(default None, readonly)

Type :

Nodes[Node]

type 

Node Tree type (deprecated, bl_idname is the actual node tree type identifier) (default 'SHADER' , readonly)

- UNDEFINED
Undefined – Undefined type of nodes (can happen e.g. when a linked node tree goes missing).

- CUSTOM
Custom – Custom nodes.

- SHADER
Shader – Shader nodes.

- TEXTURE
Texture – Texture nodes.

- COMPOSITING
Compositing – Compositing nodes.

- GEOMETRY
Geometry – Geometry nodes.

Type :

Literal[‘UNDEFINED’, ‘CUSTOM’, ‘SHADER’, ‘TEXTURE’, ‘COMPOSITING’, ‘GEOMETRY’]

view_center 

Where the view is currently offset to for this Node Tree (array of 2 items, in [-inf, inf], default (0.0, 0.0), readonly)

Type :

mathutils.Vector

interface_update ( context ) 

Refresh the node group's interface.

Parameters :

context (Context) – (never None)

contains_tree ( sub_tree ) 

Test whether one node tree is nested inside this one, to keep node groups from becoming recursive.

Parameters :

sub_tree (NodeTree) – Node Tree, Node tree for recursive check (never None)

Returns :

contained

Return type :

bool

classmethod poll ( context ) 

Decide whether to display in the editor.

Parameters :

context (Context) – (never None)

Return type :

bool

update ( ) 

React when the editor changes.

classmethod get_from_context ( context ) 

Retrieve a node tree from the current context.

Parameters :

context (Context) – (never None)

Returns :

result_1 , Active node tree from context, NodeTree

result_2 , ID data-block that owns the node tree, ID

result_3 , Original ID data-block selected from the context, ID

Return type :

tuple[NodeTree, ID, ID]

classmethod valid_socket_type ( idname ) 

Confirm that the given socket type may be used in the node tree.

Parameters :

idname ( str ) – Socket Type, Identifier of the socket type (never None)

Return type :

bool

debug_lazy_function_graph ( ) 

Obtain this node tree's internal lazy-function graph.

Returns :

Dot Graph, Graph in dot format

Return type :

str

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default (bpy.types.Struct | None) – Fallback returned if no match is found.

Returns :

Either the matching RNA type or the supplied fallback when nothing matches.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default (type | None ) – Fallback returned if no match is found.

Returns :

Either the matching class or the supplied fallback when nothing matches.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References 

| BlendData.node_groups BlendDataNodeTrees.new BlendDataNodeTrees.remove CompositorNodeCustomGroup.node_tree CompositorNodeGroup.node_tree EvaluateClosureNodeViewerPathElem.source_node_tree FreestyleLineStyle.node_tree GeometryNodeCustomGroup.node_tree GeometryNodeGroup.node_tree Light.node_tree Material.node_tree Node.poll Node.poll_instance NodeCustomGroup.node_tree NodeGroup.node_tree NodeInternal.poll NodeInternal.poll_instance NodeTree.contains_tree | NodeTree.get_from_context NodeTreePath.node_tree NodesModifier.node_group Scene.compositing_node_group SequencerCompositorModifierData.node_group ShaderNodeCustomGroup.node_tree ShaderNodeGroup.node_tree SpaceNodeEditor.edit_tree SpaceNodeEditor.node_tree SpaceNodeEditor.selected_node_group SpaceNodeEditorPath.append SpaceNodeEditorPath.start Texture.node_tree TextureNodeGroup.node_tree UILayout.template_node_link UILayout.template_node_view World.node_tree |

## NodeTreeInterfaceSocket(NodeTreeInterfaceItem)

### NodeTreeInterfaceSocket(NodeTreeInterfaceItem) 

base classes — bpy_struct, NodeTreeInterfaceItem

subclasses —
NodeTreeInterfaceSocketBool, NodeTreeInterfaceSocketBundle, NodeTreeInterfaceSocketClosure, NodeTreeInterfaceSocketCollection, NodeTreeInterfaceSocketColor, NodeTreeInterfaceSocketFloat, NodeTreeInterfaceSocketFloatAngle, NodeTreeInterfaceSocketFloatColorTemperature, NodeTreeInterfaceSocketFloatDistance, NodeTreeInterfaceSocketFloatFactor, NodeTreeInterfaceSocketFloatFrequency, NodeTreeInterfaceSocketFloatMass, NodeTreeInterfaceSocketFloatPercentage, NodeTreeInterfaceSocketFloatTime, NodeTreeInterfaceSocketFloatTimeAbsolute, NodeTreeInterfaceSocketFloatUnsigned, NodeTreeInterfaceSocketFloatWavelength, NodeTreeInterfaceSocketFont, NodeTreeInterfaceSocketGeometry, NodeTreeInterfaceSocketImage, NodeTreeInterfaceSocketInt, NodeTreeInterfaceSocketIntFactor, NodeTreeInterfaceSocketIntPercentage, NodeTreeInterfaceSocketIntUnsigned, NodeTreeInterfaceSocketMask, NodeTreeInterfaceSocketMaterial, NodeTreeInterfaceSocketMatrix, NodeTreeInterfaceSocketMenu, NodeTreeInterfaceSocketObject, NodeTreeInterfaceSocketRotation, NodeTreeInterfaceSocketScene, NodeTreeInterfaceSocketShader, NodeTreeInterfaceSocketSound, NodeTreeInterfaceSocketString, NodeTreeInterfaceSocketStringFilePath, NodeTreeInterfaceSocketText, NodeTreeInterfaceSocketTexture, NodeTreeInterfaceSocketVector, NodeTreeInterfaceSocketVector2D, NodeTreeInterfaceSocketVector4D, NodeTreeInterfaceSocketVectorAcceleration, NodeTreeInterfaceSocketVectorAcceleration2D, NodeTreeInterfaceSocketVectorAcceleration4D, NodeTreeInterfaceSocketVectorDirection, NodeTreeInterfaceSocketVectorDirection2D, NodeTreeInterfaceSocketVectorDirection4D, NodeTreeInterfaceSocketVectorEuler, NodeTreeInterfaceSocketVectorEuler2D, NodeTreeInterfaceSocketVectorEuler4D, NodeTreeInterfaceSocketVectorFactor, NodeTreeInterfaceSocketVectorFactor2D, NodeTreeInterfaceSocketVectorFactor4D, NodeTreeInterfaceSocketVectorPercentage, NodeTreeInterfaceSocketVectorPercentage2D, NodeTreeInterfaceSocketVectorPercentage4D, NodeTreeInterfaceSocketVectorTranslation, NodeTreeInterfaceSocketVectorTranslation2D, NodeTreeInterfaceSocketVectorTranslation4D, NodeTreeInterfaceSocketVectorVelocity, NodeTreeInterfaceSocketVectorVelocity2D, NodeTreeInterfaceSocketVectorVelocity4D, NodeTreeInterfaceSocketVectorXYZ, NodeTreeInterfaceSocketVectorXYZ2D, NodeTreeInterfaceSocketVectorXYZ4D

class bpy.types. NodeTreeInterfaceSocket ( NodeTreeInterfaceItem ) 

A socket declared inside a node interface.

attribute_domain 

Domain the geometry nodes modifier targets when it builds an attribute output (default 'POINT' )

Type :

Literal[Attribute Domain Items]

bl_socket_idname 

Name of the socket type (default “”, never None)

Type :

str

default_attribute_name 

Name applied to the attribute by default once a geometry nodes modifier drives the node group (default “”, never None)

Type :

str

default_input 

Source for the value when nothing is wired in. Needs “Hide Value”. (default 'VALUE' )

- VALUE
Default Value – The node socket’s default value.

- INDEX
Index – The index from the context.

- `ID_OR_INDEX`
ID or Index – The “id” attribute if available, otherwise the index.

- NORMAL
Normal – The geometry’s normal direction.

- POSITION
Position – The position from the context.

- `INSTANCE_TRANSFORM`
Instance Transform – Transformation of each instance from the geometry context.

- `HANDLE_LEFT`
Left Handle – The left Bézier control point handle from the context.

- `HANDLE_RIGHT`
Right Handle – The right Bézier control point handle from the context.

Type :

Literal[‘VALUE’, ‘INDEX’, ‘`ID_OR_INDEX`’, ‘NORMAL’, ‘POSITION’, ‘`INSTANCE_TRANSFORM`’, ‘`HANDLE_LEFT`’, ‘`HANDLE_RIGHT`’]

description 

Socket description (default “”, never None)

Type :

str

force_non_field 

Restrict the input to a single value instead of a field.
Deprecated. Will be remove in 5.0.

(default False)

Type :

bool

hide_in_modifier 

Keep the input value out of the geometry nodes modifier interface (default False)

Type :

bool

hide_value 

Conceal the socket's input value even while the socket stays unconnected (default False)

Type :

bool

identifier 

A unique key used when mapping sockets (default “”, readonly, never None)

Type :

str

in_out 

Whether the socket is an input or an output (default 'INPUT' , readonly)

- INPUT
Input – Generate a input node socket.

- OUTPUT
Output – Generate a output node socket.

Type :

Literal[‘INPUT’, ‘OUTPUT’]

is_inspect_output 

Route the link outside the node group so it reaches the root tree's output node (default False)

Type :

bool

is_panel_toggle 

Use this socket as the toggle shown in its panel header (default False)

Type :

bool

layer_selection_field 

Use a Grease Pencil Layer or Layer Group as the selection field (default False)

Type :

bool

menu_expanded 

Render the menu socket as an opened-out drop-down (default False)

Type :

bool

name 

Socket name (default “”, never None)

Type :

str

optional_label 

Mark this socket's label as non-essential for grasping its meaning, which may let the label be omitted in some situations (default False)

Type :

bool

select 

Socket is selected in the interface (default False)

Type :

bool

socket_type 

The socket type produced by this interface item (default 'DEFAULT' )

Type :

Literal[‘DEFAULT’]

structure_type 

The category of higher-order type that may pass through this socket (default 'AUTO' )

Type :

Literal[Node Socket Structure Type Items]

bl_system_properties_get ( * , do_create = False ) 

DEBUG ONLY. A back door into the runtime-built RNA data store, meant purely for tests and debugging. Leave it alone during normal scripting, and never count on its contents being writable.

Parameters :

do_create ( bool ) – Create the system properties when none have been set up yet (optional)

Returns :

The root container holding the system properties; None when this data has none stored yet and creation was not asked for

Return type :

PropertyGroup

draw ( context , layout ) 

Render the socket interface's properties.

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, Layout in the UI (never None)

init_socket ( node , socket , data_path ) 

Set up a node socket instance.

Parameters :

- node (Node) – Node, Node of the socket to initialize (never None)

- socket (NodeSocket) – Socket, Socket to initialize (never None)

- data_path ( str ) – Data Path, Path to specialized socket data (never None)

from_socket ( node , socket ) 

Derive the template parameters from a socket that already exists.

Parameters :

- node (Node) – Node, Node of the original socket (never None)

- socket (NodeSocket) – Socket, Original socket (never None)

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default (bpy.types.Struct | None) – Fallback returned if no match is found.

Returns :

Either the matching RNA type or the supplied fallback when nothing matches.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – Identifier naming the RNA type.

- default ( type | None ) – Fallback returned if no match is found.

Returns :

Either the matching class or the supplied fallback when nothing matches.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data NodeTreeInterfaceItem.item_type NodeTreeInterfaceItem.parent | NodeTreeInterfaceItem.position NodeTreeInterfaceItem.index |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeTreeInterfaceItem.bl_rna_get_subclass NodeTreeInterfaceItem.bl_rna_get_subclass_py |

### References 

| NodeTreeInterface.new_socket | |
