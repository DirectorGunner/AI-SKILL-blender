# Node Operators (part 3)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

Engage with node group contents

Parameters :

exit ( bool ) – Exit, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. group_enter_exit ( ) 

Enter or exit a group based on the pointer position

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. group_insert ( ) 

Incorporate currently highlighted nodes into a collective group

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. group_make ( ) 

Establish a group using highlighted nodes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. group_separate ( * , type = 'COPY' ) 

Disconnect currently highlighted nodes from the node group

Parameters :

type ( Literal [ 'COPY' , 'MOVE' ] ) – Type, (optional)

- COPY
Copy – Duplicate to parent node tree, keep group intact.

- MOVE
Move – Shift to parent node tree, remove from group.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. group_ungroup ( ) 

Disassemble the collective group of highlighted nodes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. hide_socket_toggle ( ) 

Control the view state of unconnected node sockets

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. hide_toggle ( ) 

Control compression state of selected nodes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. index_switch_item_add ( * , node_identifier = 0 ) 

Put an element into the index switch construct

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. index_switch_item_remove ( * , index = 0 ) 

Pull out an element from the index switch construct

Parameters :

index ( int ) – Index, Index to remove (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. insert_offset ( ) 

Compute spacing for nodes upon import

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. interface_item_duplicate ( ) 

Copy the highlighted entry to the interface registry

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:1181

bpy.ops.node. interface_item_make_panel_toggle ( ) 

Transform the highlighted boolean socket into a parent panel toggle

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:1260

bpy.ops.node. interface_item_new ( * , item_type = 'INPUT' ) 

Append a new entry to the interface registry

Parameters :

item_type ( Literal [ 'INPUT' , 'OUTPUT' , 'PANEL' ] ) – Item Type, Kind of the item to create (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:1087

bpy.ops.node. interface_item_new_panel_toggle ( ) 

Embed a checkbox within the presently active panel

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:1152

bpy.ops.node. interface_item_remove ( ) 

Clear specified entries from the interface registry

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:1200

bpy.ops.node. interface_item_unlink_panel_toggle ( ) 

Detach the panel toggle to operate independently

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:1308

bpy.ops.node. join ( ) 

Bundle selected nodes beneath a single container

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. join_named ( * , `NODE_OT`_join = {} , `WM_OT`_call_panel = {} ) 

Establish a fresh container around the selected nodes and apply a label right away

Parameters :

- `NODE_OT`_join ( dict [ str , Any ] ) – Join Nodes in Frame, Bundle selected nodes beneath a single container (optional, bpy.ops.node.join() keyword arguments)

- `WM_OT`_call_panel ( dict [ str , Any ] ) – Call Panel, Bring up a predetermined panel (optional, bpy.ops.wm.call_panel() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. join_nodes ( ) 

Consolidate highlighted group entry nodes if feasible

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. link ( * , detach = False , drag_start = (0.0, 0.0) , inside_padding = 2.0 , outside_padding = 0.0 , speed_ramp = 1.0 , max_speed = 26.0 , delay = 0.5 , zoom_influence = 0.5 ) 

Employ cursor gestures to establish a path between two nodes

Parameters :

- detach ( bool ) – Detach, Detach and redirect existing links (optional)

- drag_start ( Sequence [ float ] ) – Drag Start, The position of the mouse cursor at the start of the operation (array of 2 items, in [-6, 6], optional)

- inside_padding ( float ) – Inside Padding, Inside distance in UI units from the edge of the region within which to start panning (in [0, 100], optional)

- outside_padding ( float ) – Outside Padding, Outside distance in UI units from the edge of the region at which to stop panning (in [0, 100], optional)

- speed_ramp ( float ) – Speed Ramp, Width of the zone in UI units where speed increases with distance from the edge (in [0, 100], optional)

- max_speed ( float ) – Max Speed, Maximum speed in UI units per second (in [0, 10000], optional)

- delay ( float ) – Delay, Delay in seconds before maximum speed is reached (in [0, 10], optional)

- zoom_influence ( float ) – Zoom Influence, Influence of the zoom factor on scroll speed (in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. link_drag_operation_test ( * , find_link_operations = False , link_operation_index = -1 ) 

Execute a node link-drag action for verification

Parameters :

- find_link_operations ( bool ) – Find Link Operations, Write link operation names for the context socket the "link_operation_names" property of the node tree (optional)

- link_operation_index ( int ) – Link Operation Index, Link operation to execute on the context socket (in [-1, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. link_make ( * , replace = False ) 

Generate a connection between target output and input sockets

Parameters :

replace ( bool ) – Replace, Replace socket connections with the new links (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. link_viewer ( ) 

Establish connection to inspection terminal node

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. links_cut ( * , path = None , cursor = 15 ) 

Apply cursor gestures to eliminate (sever) some links

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- cursor ( int ) – Cursor, (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. links_detach ( ) 

Strip all links to selected nodes, and try to connect neighbor nodes together

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. links_mute ( * , path = None , cursor = 39 ) 

Employ cursor gestures to deactivate links

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- cursor ( int ) – Cursor, (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. move_detach_links ( * , `NODE_OT`_links_detach = {} , `TRANSFORM_OT`_translate = {} ) 

Shift a node to break links

Parameters :

- `NODE_OT`_links_detach ( dict [ str , Any ] ) – Detach Links, Strip all links to selected nodes, and try to connect neighbor nodes together (optional, bpy.ops.node.links_detach() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. move_detach_links_release ( * , `NODE_OT`_links_detach = {} , `NODE_OT`_translate_attach = {} ) 

Shift a node to break links

Parameters :

- `NODE_OT`_links_detach ( dict [ str , Any ] ) – Detach Links, Strip all links to selected nodes, and try to connect neighbor nodes together (optional, bpy.ops.node.links_detach() keyword arguments)

- `NODE_OT`_translate_attach ( dict [ str , Any ] ) – Move and Attach, Move nodes and attach to frame (optional, bpy.ops.node.translate_attach() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. mute_toggle ( ) 

Control the activation state of selected nodes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. new_compositing_node_group ( * , name = '' ) 

Prepare a fresh compositing node collective and set it up with standard nodes

Parameters :

name ( str ) – Name, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. new_compositor_sequencer_node_group ( * , name = 'Sequencer Compositor Nodes' ) 

Prepare a fresh compositor node collective for sequencer purposes

Parameters :

name ( str ) – Name, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. new_geometry_node_group_assign ( ) 

Prepare a fresh geometry node collective and bind it to the highlighted modifier

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/geometry_nodes.py:345

bpy.ops.node. new_geometry_node_group_tool ( ) 

Prepare a fresh geometry node collective for an instrument

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/geometry_nodes.py:366

bpy.ops.node. new_geometry_nodes_modifier ( ) 

Establish a modifier paired with a fresh geometry node collective

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/geometry_nodes.py:322

bpy.ops.node. new_node_tree ( * , type = '' , name = 'NodeTree' ) 

Prepare a fresh node tree

Parameters :

- type ( str ) – Tree Type, (optional)

- name ( str ) – Name, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. node_color_preset_add ( * , name = '' , remove_name = False , remove_active = False ) 

Insert or withdraw a Node Color Preset

Parameters :

- name ( str ) – Name, Identifier of the preset, utilized to produce the pathname (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.node. node_copy_color ( ) 

Employ the shade of all highlighted nodes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. options_toggle ( ) 

Control the appearance of option elements for selected nodes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. parent_set ( ) 

Bind selected nodes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. preview_toggle ( ) 

Control the appearance of preview view for selected nodes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. read_viewlayers ( ) 

Retrieve all render partitions from all utilized environments

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. render_changed ( ) 

Synthesize present scene, when entry node's section has been modified

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. repeat_zone_item_add ( * , node_identifier = 0 ) 

Insert element following the selected one

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. repeat_zone_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Reposition an active element

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Movement path (optional)

- node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

set[Literal[Operator Return Items]]

bpy.ops.node. repeat_zone_item_remove ( * , node_identifier = 0 ) 

Erase the selected element

Parameters :

node_identifier ( int ) – Node Identifier, Optional identifier of the node to operate on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. resize ( ) 

Modify the measurement of a node

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. select ( * , extend = False , deselect = False , toggle = False , deselect_all = False , select_passthrough = False , location = (0, 0) , socket_select = False , clear_viewer = False ) 

Pick the node underneath the cursor position

Parameters :

- extend ( bool ) – Extend, Extend selection instead of deselecting everything first (optional)

- deselect ( bool ) – Deselect, Remove from selection (optional)

- toggle ( bool ) – Toggle Selection, Toggle the selection (optional)

- deselect_all ( bool ) – Deselect On Nothing, Deselect all when nothing under the cursor (optional)

- select_passthrough ( bool ) – Only Select Unselected, Ignore the select action when the element is already selected (optional)

- location ( Sequence [ int ] ) – Location, Mouse location (array of 2 items, in [-inf, inf], optional)

- socket_select ( bool ) – Socket Select, (optional)

- clear_viewer ( bool ) – Clear Viewer, Deactivate geometry nodes viewer when clicking in empty space (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. select_all ( * , action = 'TOGGLE' ) 

Flip selection state for all nodes

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Choice of pick activity to perform (optional)

- TOGGLE
Toggle – Toggle selection for all elements.

- SELECT
Select – Select all elements.

- DESELECT
Deselect – Deselect all elements.

- INVERT
Invert – Invert selection of all elements.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. select_box ( * , tweak = False , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , mode = 'SET' ) 

Employ rectangular capture to highlight nodes

Parameters :

- tweak ( bool ) – Tweak, Only activate when mouse is not over a node (useful for tweak gesture) (optional)

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Set a new selection.

- ADD
Extend – Extend existing selection.

- SUB
Subtract – Subtract existing selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. select_circle ( * , x = 0 , y = 0 , radius = 25 , wait_for_input = True , mode = 'SET' ) 

Employ spherical capture to highlight nodes

Parameters :

- x ( int ) – X, (in [-inf, inf], optional)

- y ( int ) – Y, (in [-inf, inf], optional)

- radius ( int ) – Radius, (in [1, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Set a new selection.

- ADD
Extend – Extend existing selection.

- SUB
Subtract – Subtract existing selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. select_grouped ( * , extend = False , type = 'TYPE' ) 

Pick nodes exhibiting equivalent qualities

Parameters :

- extend ( bool ) – Extend, Extend selection instead of deselecting everything first (optional)

- type ( Literal [ 'TYPE' , 'COLOR' , 'PREFIX' , 'SUFFIX' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. select_lasso ( * , tweak = False , path = None , use_smooth_stroke = False , smooth_stroke_factor = 0.75 , smooth_stroke_radius = 35 , mode = 'SET' ) 

Pick nodes employing a lasso capture technique

Parameters :

- tweak ( bool ) – Tweak, Only activate when mouse is not over a node (useful for tweak gesture) (optional)

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- use_smooth_stroke ( bool ) – Stabilize Stroke, Selection lags behind mouse and follows a smoother path (optional)

- smooth_stroke_factor ( float ) – Smooth Stroke Factor, Higher values give a smoother stroke (in [0.5, 0.99], optional)

- smooth_stroke_radius ( int ) – Smooth Stroke Radius, Minimum distance from last point before selection continues (in [10, 200], optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Set a new selection.

- ADD
Extend – Extend existing selection.

- SUB
Subtract – Subtract existing selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. select_link_viewer ( * , `NODE_OT`_select = {} , `NODE_OT`_link_viewer = {} ) 

Pick node and establish path to an inspection terminal

Parameters :

- `NODE_OT`_select ( dict [ str , Any ] ) – Select, Pick the node underneath the cursor position (optional, bpy.ops.node.select() keyword arguments)

- `NODE_OT`_link_viewer ( dict [ str , Any ] ) – Link to Viewer Node, Establish connection to inspection terminal node (optional, bpy.ops.node.link_viewer() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. select_linked_from ( ) 

Pick nodes dispatching signals from the selected ones

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. select_linked_to ( ) 

Pick nodes obtaining signals from the selected ones

Returns :

Result of the operator call.

Return type :
