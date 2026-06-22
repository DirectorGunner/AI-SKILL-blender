# Node Operators (part 2)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. closure_output_item_add ( * , node_identifier = 0 ) 

Append entry below working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. closure_output_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Shift working entry

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Shift route (optional)

- node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. closure_output_item_remove ( * , node_identifier = 0 ) 

Wipe out working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. collapse_hide_unused_toggle ( ) 

Toggle packed nodes and shut blank inlets

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:995

bpy.ops.node. combine_bundle_item_add ( * , node_identifier = 0 ) 

Append entry below working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. combine_bundle_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Shift working entry

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Shift route (optional)

- node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. combine_bundle_item_remove ( * , node_identifier = 0 ) 

Wipe out working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. connect_to_output ( * , run_in_geometry_nodes = True ) 

Link working node to the working outlet node of the node mesh

Parameters :

run_in_geometry_nodes ( bool ) – Run in Geometry Nodes Editor, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/connect_to_output.py:251

bpy.ops.node. cryptomatte_layer_add ( ) 

Bring a fresh inlet channel to a Cryptomatte node

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. cryptomatte_layer_remove ( ) 

Drop channel from a Cryptomatte node

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. deactivate_viewer ( ) 

Turn off chosen monitor node in geometry nodes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. default_group_width_set ( ) 

Set the width based on the parent node bundle in the working spot

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. delete ( ) 

Drop marked nodes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. delete_copy_reconnect ( * , `NODE_OT`_clipboard_copy = {} , `NODE_OT`_delete_reconnect = {} ) 

Grab nodes to clipboard, take out and re-join them.

Parameters :

- `NODE_OT`_clipboard_copy ( dict [ str , Any ] ) – Copy to Clipboard, Grab the marked nodes to the inward clipboard (optional, bpy.ops.node.clipboard_copy() keyword arguments)

- `NODE_OT`_delete_reconnect ( dict [ str , Any ] ) – Delete with Reconnect, Take out nodes and re-join nodes as if removal was skipped (optional, bpy.ops.node.delete_reconnect() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. delete_reconnect ( ) 

Take out nodes and re-join nodes as if removal was skipped

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. detach ( ) 

Let go of marked nodes from frames

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. detach_translate_attach ( * , `NODE_OT`_detach = {} , `TRANSFORM_OT`_translate = {} , `NODE_OT`_attach = {} ) 

Let go of nodes, shift and affix to frame

Parameters :

- `NODE_OT`_detach ( dict [ str , Any ] ) – Detach Nodes, Let go of marked nodes from frames (optional, bpy.ops.node.detach() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Shift, Reposition picked items (optional, bpy.ops.transform.translate() keyword arguments)

- `NODE_OT`_attach ( dict [ str , Any ] ) – Attach Nodes, Fasten working node to a frame (optional, bpy.ops.node.attach() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. duplicate ( * , keep_inputs = False , linked = True ) 

Make copies of marked nodes

Parameters :

- keep_inputs ( bool ) – Keep Inputs, Keep the entry routes to copied nodes (optional)

- linked ( bool ) – Linked, Make copies of node but not node meshes, hooking to the prior data (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. duplicate_compositing_modifier_node_group ( ) 

Make a copy of the assigned makeup node bundle.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. duplicate_compositing_node_group ( ) 

Make a copy of the assigned makeup node bundle.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. duplicate_move ( * , `NODE_OT`_duplicate = {} , `NODE_OT`_translate_attach = {} ) 

Make copies of marked nodes and shift them

Parameters :

- `NODE_OT`_duplicate ( dict [ str , Any ] ) – Make Copies, Make copies of marked nodes (optional, bpy.ops.node.duplicate() keyword arguments)

- `NODE_OT`_translate_attach ( dict [ str , Any ] ) – Move and Attach, Shift nodes and affix to frame (optional, bpy.ops.node.translate_attach() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. duplicate_move_keep_inputs ( * , `NODE_OT`_duplicate = {} , `NODE_OT`_translate_attach = {} ) 

Make copies of marked nodes keeping entry routes and shift them

Parameters :

- `NODE_OT`_duplicate ( dict [ str , Any ] ) – Make Copies, Make copies of marked nodes (optional, bpy.ops.node.duplicate() keyword arguments)

- `NODE_OT`_translate_attach ( dict [ str , Any ] ) – Move and Attach, Shift nodes and affix to frame (optional, bpy.ops.node.translate_attach() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. duplicate_move_linked ( * , `NODE_OT`_duplicate = {} , `NODE_OT`_translate_attach = {} ) 

Make copies of marked nodes, but not their node meshes, and shift them

Parameters :

- `NODE_OT`_duplicate ( dict [ str , Any ] ) – Make Copies, Make copies of marked nodes (optional, bpy.ops.node.duplicate() keyword arguments)

- `NODE_OT`_translate_attach ( dict [ str , Any ] ) – Move and Attach, Shift nodes and affix to frame (optional, bpy.ops.node.translate_attach() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. enum_definition_item_add ( * , node_identifier = 0 ) 

Append entry below working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. enum_definition_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Shift working entry

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Shift route (optional)

- node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. enum_definition_item_remove ( * , node_identifier = 0 ) 

Wipe out working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. evaluate_closure_input_item_add ( * , node_identifier = 0 ) 

Append entry below working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. evaluate_closure_input_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Shift working entry

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Shift route (optional)

- node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. evaluate_closure_input_item_remove ( * , node_identifier = 0 ) 

Wipe out working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. evaluate_closure_output_item_add ( * , node_identifier = 0 ) 

Append entry below working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. evaluate_closure_output_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Shift working entry

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Shift route (optional)

- node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. evaluate_closure_output_item_remove ( * , node_identifier = 0 ) 

Wipe out working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. field_to_grid_item_add ( * , node_identifier = 0 ) 

Append entry below working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. field_to_grid_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Shift working entry

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Shift route (optional)

- node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. field_to_grid_item_remove ( * , node_identifier = 0 ) 

Wipe out working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. field_to_list_item_add ( * , node_identifier = 0 ) 

Append entry below working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. field_to_list_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Shift working entry

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Shift route (optional)

- node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. field_to_list_item_remove ( * , node_identifier = 0 ) 

Wipe out working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. file_output_item_add ( * , node_identifier = 0 ) 

Append entry below working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. file_output_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Reposition an active element

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Movement path (optional)

- node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. file_output_item_remove ( * , node_identifier = 0 ) 

Erase the selected element

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. find_node ( ) 

Locate a node via its identifier and focus it on screen

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. foreach_geometry_element_zone_generation_item_add ( * , node_identifier = 0 ) 

Insert element following the selected one

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. foreach_geometry_element_zone_generation_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Reposition an active element

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Movement path (optional)

- node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. foreach_geometry_element_zone_generation_item_remove ( * , node_identifier = 0 ) 

Erase the selected element

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. foreach_geometry_element_zone_input_item_add ( * , node_identifier = 0 ) 

Insert element following the selected one

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. foreach_geometry_element_zone_input_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Reposition an active element

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Movement path (optional)

- node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. foreach_geometry_element_zone_input_item_remove ( * , node_identifier = 0 ) 

Erase the selected element

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. foreach_geometry_element_zone_main_item_add ( * , node_identifier = 0 ) 

Insert element following the selected one

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. foreach_geometry_element_zone_main_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Reposition an active element

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Movement path (optional)

- node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. foreach_geometry_element_zone_main_item_remove ( * , node_identifier = 0 ) 

Erase the selected element

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. format_string_item_add ( * , node_identifier = 0 ) 

Insert element following the selected one

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. format_string_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Reposition an active element

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Movement path (optional)

- node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. format_string_item_remove ( * , node_identifier = 0 ) 

Erase the selected element

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. geometry_nodes_viewer_item_add ( * , node_identifier = 0 ) 

Insert element following the selected one

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. geometry_nodes_viewer_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Reposition an active element

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Movement path (optional)

- node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. geometry_nodes_viewer_item_remove ( * , node_identifier = 0 ) 

Erase the selected element

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. gltf_settings_node_operator ( ) 

Establish a node for glTF asset export

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

addons_core/io_scene_gltf2/blender/com/gltf2_blender_ui.py:35

bpy.ops.node. group_edit ( * , exit = False )
