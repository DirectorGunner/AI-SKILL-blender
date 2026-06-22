# Node Bpy Struct, Nodelink Bpy Struct, Nodelinks Bpy Prop Collection

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Node(bpy_struct); NodeLink(bpy_struct); NodeLinks(bpy_prop_collection).

## Node(bpy_struct)

### Node(bpy_struct)

base class — bpy_struct

subclasses —
NodeCustomGroup, NodeInternal

class bpy.types. Node ( bpy_struct )

A single node living inside a node tree.

bl_description

(default “”, never None)

Type :

str

bl_height_default

(in [0, inf], default 0.0)

Type :

float

bl_height_max

(in [0, inf], default 0.0)

Type :

float

bl_height_min

(in [0, inf], default 0.0)

Type :

float

bl_icon

Which icon represents the node (default 'NODE' )

Type :

Literal[Icon Items]

bl_idname

(default “”, never None)

Type :

str

bl_label

Text shown as the node's label (default “”, never None)

Type :

str

bl_static_type

Older-style unique identifier for the node type, duplicating what bl_idname already provides (default “”, readonly, never None)

Type :

str

bl_width_default

(in [0, inf], default 0.0)

Type :

float

bl_width_max

(in [0, inf], default 0.0)

Type :

float

bl_width_min

(in [0, inf], default 0.0)

Type :

float

color

A user-chosen color for the node's body (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

color_tag

Color tag shown on the node header (default 'NONE' , readonly)

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

dimensions

The node's absolute bounding-box size (array of 2 items, in [-inf, inf], default (0.0, 0.0), readonly)

Type :

mathutils.Vector

height

The node's height (in [-inf, inf], default 0.0)

Type :

float

hide

(default False)

Type :

bool

inputs

(default None, readonly)

Type :

NodeInputs[NodeSocket]

internal_links

Input-to-output wiring used internally while the node is muted (default None, readonly)

Type :

bpy_prop_collection[NodeLink]

label

A custom label for the node, if set (default “”, never None)

Type :

str

location

Where the node sits within its parent frame (array of 2 items, in [-1e+06, 1e+06], default (0.0, 0.0))

Type :

mathutils.Vector

location_absolute

Where the node sits across the whole canvas (array of 2 items, in [-1e+06, 1e+06], default (0.0, 0.0))

Type :

mathutils.Vector

mute

(default False)

Type :

bool

name

The node's unique identifier (default “”, never None)

Type :

str

outputs

(default None, readonly)

Type :

NodeOutputs[NodeSocket]

parent

The node this one is attached to

Type :

Node

select

Whether the node is selected (default False)

Type :

bool

show_options

(default False)

Type :

bool

show_preview

(default False)

Type :

bool

show_texture

Render the node in the viewport's textured shading mode (default False)

Type :

bool

type

Older-style unique identifier for the node type, duplicating what bl_idname already provides (default “”, readonly, never None)

Type :

str

use_custom_color

Apply a custom color to the node (default False)

Type :

bool

warning_propagation

Which message kinds get carried up from this node to the enclosing group node (default 'ALL' )

- ALL
All Messages – Propagate every info, error, and warning message upstream.

- `ERRORS_AND_WARNINGS`
Errors and Warnings – Propagate only error and warning messages upstream.

- ERRORS
Errors – Propagate only error messages upstream.

- NONE
None – Do not propagate any messages upstream.

Type :

Literal[‘ALL’, ‘`ERRORS_AND_WARNINGS`’, ‘ERRORS’, ‘NONE’]

width

The node's width (in [-inf, inf], default 0.0)

Type :

float

bl_system_properties_get ( * , do_create = False )

FOR DEBUGGING ONLY. A back door into the runtime-defined RNA data store, meant purely for tests and debugging. Steer clear of it in ordinary scripts, and never count on the contents being writable

Parameters :

do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)

Returns :

The top-level container of system properties; comes back as None when this data holds none yet and you did not ask for them to be created

Return type :

PropertyGroup

socket_value_update ( context )

Run an update once properties have changed

Parameters :

context (Context) – (never None)

classmethod is_registered_node_type ( )

True if a registered node type

Returns :

Result

Return type :

bool

classmethod poll ( node_tree )

When a non-null result comes back, this node type may be added to the tree

Parameters :

node_tree (NodeTree) – Node Tree

Return type :

bool

poll_instance ( node_tree )

When a non-null result comes back, the node may be added to the tree

Parameters :

node_tree (NodeTree) – Node Tree

Return type :

bool

update ( )

Run when the node graph topology changes (nodes or links added or removed)

insert_link ( link )

Respond to a link being made to or from the node

Parameters :

link (NodeLink) – Link, Node link that will be inserted (never None)

init ( context )

Set up a freshly created instance of this node

Parameters :

context (Context) – (never None)

copy ( node )

Set up a new instance of this node by copying an existing one

Parameters :

node (Node) – Node, Existing node to copy (never None)

free ( )

Tidy up the node as it is being removed

draw_buttons ( context , layout )

Draw the node's buttons

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, Layout in the UI (never None)

draw_buttons_ext ( context , layout )

Draw the node's buttons in the sidebar

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, Layout in the UI (never None)

draw_label ( )

Produce a label string computed on the fly

Returns :

Label, (never None)

Return type :

str

debug_zone_body_lazy_function_graph ( )

Fetch the internal lazy-function graph for this zone's body

Returns :

Dot Graph, Graph in dot format

Return type :

str

debug_zone_lazy_function_graph ( )

Fetch the internal lazy-function graph for this zone

Returns :

Dot Graph, Graph in dot format

Return type :

str

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

| bpy.context.active_node bpy.context.selected_nodes bpy.context.texture_node GeometryNodeForeachGeometryElementInput.paired_output GeometryNodeMenuSwitch.enum_definition GeometryNodeRepeatInput.paired_output GeometryNodeSimulationInput.paired_output Node.copy Node.parent NodeClosureInput.paired_output NodeLink.from_node NodeLink.to_node NodeSocket.draw NodeSocket.draw_color NodeSocket.node NodeSocketStandard.draw NodeSocketStandard.draw_color NodeTree.nodes NodeTreeInterfaceSocket.from_socket NodeTreeInterfaceSocket.init_socket NodeTreeInterfaceSocketBool.from_socket NodeTreeInterfaceSocketBool.init_socket NodeTreeInterfaceSocketBundle.from_socket NodeTreeInterfaceSocketBundle.init_socket NodeTreeInterfaceSocketClosure.from_socket NodeTreeInterfaceSocketClosure.init_socket NodeTreeInterfaceSocketCollection.from_socket NodeTreeInterfaceSocketCollection.init_socket NodeTreeInterfaceSocketColor.from_socket NodeTreeInterfaceSocketColor.init_socket NodeTreeInterfaceSocketFloat.from_socket NodeTreeInterfaceSocketFloat.init_socket NodeTreeInterfaceSocketFloatAngle.from_socket NodeTreeInterfaceSocketFloatAngle.init_socket NodeTreeInterfaceSocketFloatColorTemperature.from_socket NodeTreeInterfaceSocketFloatColorTemperature.init_socket NodeTreeInterfaceSocketFloatDistance.from_socket NodeTreeInterfaceSocketFloatDistance.init_socket NodeTreeInterfaceSocketFloatFactor.from_socket NodeTreeInterfaceSocketFloatFactor.init_socket NodeTreeInterfaceSocketFloatFrequency.from_socket NodeTreeInterfaceSocketFloatFrequency.init_socket NodeTreeInterfaceSocketFloatMass.from_socket NodeTreeInterfaceSocketFloatMass.init_socket NodeTreeInterfaceSocketFloatPercentage.from_socket NodeTreeInterfaceSocketFloatPercentage.init_socket NodeTreeInterfaceSocketFloatTime.from_socket NodeTreeInterfaceSocketFloatTime.init_socket NodeTreeInterfaceSocketFloatTimeAbsolute.from_socket NodeTreeInterfaceSocketFloatTimeAbsolute.init_socket NodeTreeInterfaceSocketFloatUnsigned.from_socket NodeTreeInterfaceSocketFloatUnsigned.init_socket NodeTreeInterfaceSocketFloatWavelength.from_socket NodeTreeInterfaceSocketFloatWavelength.init_socket NodeTreeInterfaceSocketGeometry.from_socket NodeTreeInterfaceSocketGeometry.init_socket NodeTreeInterfaceSocketImage.from_socket NodeTreeInterfaceSocketImage.init_socket NodeTreeInterfaceSocketInt.from_socket NodeTreeInterfaceSocketInt.init_socket NodeTreeInterfaceSocketIntFactor.from_socket NodeTreeInterfaceSocketIntFactor.init_socket NodeTreeInterfaceSocketIntPercentage.from_socket NodeTreeInterfaceSocketIntPercentage.init_socket NodeTreeInterfaceSocketIntUnsigned.from_socket NodeTreeInterfaceSocketIntUnsigned.init_socket NodeTreeInterfaceSocketMaterial.from_socket NodeTreeInterfaceSocketMaterial.init_socket NodeTreeInterfaceSocketMatrix.from_socket NodeTreeInterfaceSocketMatrix.init_socket NodeTreeInterfaceSocketMenu.from_socket NodeTreeInterfaceSocketMenu.init_socket NodeTreeInterfaceSocketObject.from_socket NodeTreeInterfaceSocketObject.init_socket | NodeTreeInterfaceSocketRotation.from_socket NodeTreeInterfaceSocketRotation.init_socket NodeTreeInterfaceSocketShader.from_socket NodeTreeInterfaceSocketShader.init_socket NodeTreeInterfaceSocketString.from_socket NodeTreeInterfaceSocketString.init_socket NodeTreeInterfaceSocketStringFilePath.from_socket NodeTreeInterfaceSocketStringFilePath.init_socket NodeTreeInterfaceSocketTexture.from_socket NodeTreeInterfaceSocketTexture.init_socket NodeTreeInterfaceSocketVector.from_socket NodeTreeInterfaceSocketVector.init_socket NodeTreeInterfaceSocketVector2D.from_socket NodeTreeInterfaceSocketVector2D.init_socket NodeTreeInterfaceSocketVector4D.from_socket NodeTreeInterfaceSocketVector4D.init_socket NodeTreeInterfaceSocketVectorAcceleration.from_socket NodeTreeInterfaceSocketVectorAcceleration.init_socket NodeTreeInterfaceSocketVectorAcceleration2D.from_socket NodeTreeInterfaceSocketVectorAcceleration2D.init_socket NodeTreeInterfaceSocketVectorAcceleration4D.from_socket NodeTreeInterfaceSocketVectorAcceleration4D.init_socket NodeTreeInterfaceSocketVectorDirection.from_socket NodeTreeInterfaceSocketVectorDirection.init_socket NodeTreeInterfaceSocketVectorDirection2D.from_socket NodeTreeInterfaceSocketVectorDirection2D.init_socket NodeTreeInterfaceSocketVectorDirection4D.from_socket NodeTreeInterfaceSocketVectorDirection4D.init_socket NodeTreeInterfaceSocketVectorEuler.from_socket NodeTreeInterfaceSocketVectorEuler.init_socket NodeTreeInterfaceSocketVectorEuler2D.from_socket NodeTreeInterfaceSocketVectorEuler2D.init_socket NodeTreeInterfaceSocketVectorEuler4D.from_socket NodeTreeInterfaceSocketVectorEuler4D.init_socket NodeTreeInterfaceSocketVectorFactor.from_socket NodeTreeInterfaceSocketVectorFactor.init_socket NodeTreeInterfaceSocketVectorFactor2D.from_socket NodeTreeInterfaceSocketVectorFactor2D.init_socket NodeTreeInterfaceSocketVectorFactor4D.from_socket NodeTreeInterfaceSocketVectorFactor4D.init_socket NodeTreeInterfaceSocketVectorPercentage.from_socket NodeTreeInterfaceSocketVectorPercentage.init_socket NodeTreeInterfaceSocketVectorPercentage2D.from_socket NodeTreeInterfaceSocketVectorPercentage2D.init_socket NodeTreeInterfaceSocketVectorPercentage4D.from_socket NodeTreeInterfaceSocketVectorPercentage4D.init_socket NodeTreeInterfaceSocketVectorTranslation.from_socket NodeTreeInterfaceSocketVectorTranslation.init_socket NodeTreeInterfaceSocketVectorTranslation2D.from_socket NodeTreeInterfaceSocketVectorTranslation2D.init_socket NodeTreeInterfaceSocketVectorTranslation4D.from_socket NodeTreeInterfaceSocketVectorTranslation4D.init_socket NodeTreeInterfaceSocketVectorVelocity.from_socket NodeTreeInterfaceSocketVectorVelocity.init_socket NodeTreeInterfaceSocketVectorVelocity2D.from_socket NodeTreeInterfaceSocketVectorVelocity2D.init_socket NodeTreeInterfaceSocketVectorVelocity4D.from_socket NodeTreeInterfaceSocketVectorVelocity4D.init_socket NodeTreeInterfaceSocketVectorXYZ.from_socket NodeTreeInterfaceSocketVectorXYZ.init_socket NodeTreeInterfaceSocketVectorXYZ2D.from_socket NodeTreeInterfaceSocketVectorXYZ2D.init_socket NodeTreeInterfaceSocketVectorXYZ4D.from_socket NodeTreeInterfaceSocketVectorXYZ4D.init_socket Nodes.active Nodes.new Nodes.remove NodesModifierBake.node RenderEngine.update_script_node SpaceNodeEditorPath.append UILayout.template_node_inputs UILayout.template_node_link UILayout.template_node_view |

## NodeLink(bpy_struct)

### NodeLink(bpy_struct)

base class — bpy_struct

class bpy.types. NodeLink ( bpy_struct )

A connection joining two nodes inside a node tree

from_node

(readonly)

Type :

Node

from_socket

(readonly)

Type :

NodeSocket

is_hidden

The link stays out of view because its sockets are not shown (default False, readonly)

Type :

bool

is_muted

The link is silenced and may be skipped (default False)

Type :

bool

is_valid

Whether the link is valid (default False)

Type :

bool

multi_input_sort_id

Determines ordering when several links feed one input; the link with the largest ID sits on top. (in [0, inf], default 0, readonly)

Type :

int

to_node

(readonly)

Type :

Node

to_socket

(readonly)

Type :

NodeSocket

swap_multi_input_sort_id ( other )

Trade the positions of two links feeding the same multi-input socket

Parameters :

other (NodeLink) – Other, The other link. Must link to the same multi-input socket. (never None)

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

| Node.insert_link Node.internal_links NodeLink.swap_multi_input_sort_id | NodeLinks.new NodeLinks.remove NodeTree.links |

## NodeLinks(bpy_prop_collection)

### NodeLinks(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodeLinks ( bpy_prop_collection )

A set holding the node links.

new ( input , output , * , verify_limits = True , handle_dynamic_sockets = False )

Create a link inside this node tree.

Parameters :

- input (NodeSocket) – The input socket (never None)

- output (NodeSocket) – The output socket (never None)

- verify_limits ( bool ) – Verify Limits, Remove existing links if connection limit is exceeded (optional)

- handle_dynamic_sockets ( bool ) – Handle Dynamic Sockets, Handle node specific features like virtual sockets (optional)

Returns :

New node link

Return type :

NodeLink

remove ( link )

Delete a link from the node tree.

Parameters :

link (NodeLink) – The node link to remove (never None)

clear ( )

Delete every link in the node tree.

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

| NodeTree.links | |
