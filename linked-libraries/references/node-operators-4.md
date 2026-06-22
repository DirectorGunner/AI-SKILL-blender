# Node Operators (part 4)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

set[Literal[Operator Return Items]]

bpy.ops.node. select_same_type_step ( * , prev = False ) 

Concentrate and display matching node classification, incrementally

Parameters :

prev ( bool ) – Previous, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. separate_bundle_item_add ( * , node_identifier = 0 ) 

Insert element following the selected one

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. separate_bundle_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Reposition an active element

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Movement path (optional)

- node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. separate_bundle_item_remove ( * , node_identifier = 0 ) 

Erase the selected element

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. shader_script_update ( ) 

Modernize shader script node by incorporating fresh sockets and controls from the script

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. simulation_zone_item_add ( * , node_identifier = 0 ) 

Insert element following the selected one

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. simulation_zone_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Reposition an active element

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Movement path (optional)

- node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. simulation_zone_item_remove ( * , node_identifier = 0 ) 

Erase the selected element

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. sockets_sync ( * , node_name = '' ) 

Synchronize sockets to correspond to what is actually utilized

Parameters :

node_name ( str ) – Node Name, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. swap_empty_group ( * , settings = None ) 

Substitute highlighted node with a vacant group

Parameters :

settings ( bpy_prop_collection [ NodeSetting ]) – Settings, Settings to be applied on the newly created node (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:666

bpy.ops.node. swap_group_asset ( * , asset_library_type = 'LOCAL' , asset_library_identifier = '' , relative_asset_identifier = '' ) 

Swap selected nodes with the specified node group asset

Parameters :

- asset_library_type (Literal[Asset Library Type Items]) – Asset Library Type, (optional)

- asset_library_identifier ( str ) – Asset Library Identifier, (optional, never None)

- relative_asset_identifier ( str ) – Relative Asset Identifier, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. swap_node ( * , settings = None , type = '' , visible_output = '' ) 

Exchange the selected nodes for the requested classification

Parameters :

- settings ( bpy_prop_collection [ NodeSetting ]) – Settings, Settings to be applied on the newly created node (optional)

- type ( str ) – Node Type, Node type (optional, never None)

- visible_output ( str ) – Output Name, If provided, all outputs that are named differently will be hidden (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:555

bpy.ops.node. swap_zone ( * , settings = None , offset = (150.0, 0.0) , input_node_type = '' , output_node_type = '' , add_default_geometry_link = False ) 

Undocumented, consider contributing.

Parameters :

- settings ( bpy_prop_collection [ NodeSetting ]) – Settings, Settings to be applied on the newly created node (optional)

- offset ( Sequence [ float ] ) – Offset, Offset of nodes from the cursor when added (array of 2 items, in [-inf, inf], optional)

- input_node_type ( str ) – Input Node, Specifies the input node used by the created zone (optional, never None)

- output_node_type ( str ) – Output Node, Specifies the output node used by the created zone (optional, never None)

- add_default_geometry_link ( bool ) – Add Geometry Link, When enabled, create a link between geometry sockets in this zone (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:847

bpy.ops.node. test_inlining_shader_nodes ( ) 

Produce a fresh inlined shader node tree for use by rendering pipelines

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. toggle_viewer ( ) 

Control the state of highlighted inspection nodes in compositor and geometry node environments

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. translate_attach ( * , `TRANSFORM_OT`_translate = {} , `NODE_OT`_attach = {} ) 

Move nodes and attach to frame

Parameters :

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

- `NODE_OT`_attach ( dict [ str , Any ] ) – Attach Nodes, Attach active node to a frame (optional, bpy.ops.node.attach() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. translate_attach_remove_on_cancel ( * , `TRANSFORM_OT`_translate = {} , `NODE_OT`_attach = {} ) 

Move nodes and attach to frame

Parameters :

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

- `NODE_OT`_attach ( dict [ str , Any ] ) – Attach Nodes, Attach active node to a frame (optional, bpy.ops.node.attach() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. tree_path_parent ( * , parent_tree_index = 0 ) 

Climb up to parent node tree structure

Parameters :

parent_tree_index ( int ) – Parent Index, Parent index in context path (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:1031

bpy.ops.node. view_all ( ) 

Alter the view dimensions to encompass all nodes at once

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. view_selected ( ) 

Alter the view dimensions to encompass selected nodes at once

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. viewer_border ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True ) 

Configure the extents for inspection tasks (Not implemented)

Parameters :

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. viewer_shortcut_get ( * , viewer_index = 0 ) 

Activate an inspection node using numeric keys 1,2,..,9

Parameters :

viewer_index ( int ) – Viewer Index, Index corresponding to the shortcut, e.g. number key 1 corresponds to index 1 etc.. (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:1422

bpy.ops.node. viewer_shortcut_set ( * , viewer_index = 0 ) 

Establish an inspection shortcut for the selected node by pressing ctrl+1,2,..9

Parameters :

viewer_index ( int ) – Viewer Index, Index corresponding to the shortcut, e.g. number key 1 corresponds to index 1 etc.. (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:1362
