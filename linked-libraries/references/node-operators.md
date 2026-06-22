# Node Operators (part 1)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

### Node Operators 

bpy.ops.node. activate_viewer ( ) 

Turn on chosen monitor node in compositor and geometry nodes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. add_closure_zone ( * , settings = None , use_transform = False , offset = (150.0, 0.0) ) 

Generate a Closure region

Parameters :

- settings ( bpy_prop_collection [ NodeSetting ]) – Settings, Setups to put on the fresh node (optional)

- use_transform ( bool ) – Use Transform, Launch transform tool after putting in the node (optional)

- offset ( Sequence [ float ] ) – Offset, How far to place nodes from the marker when putting them (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:729

bpy.ops.node. add_collection ( * , name = '' , session_uid = 0 ) 

Add a group tracker node to the focal node panel

Parameters :

- name ( str ) – Name, Label of the information to employ (optional, never None)

- session_uid ( int ) – Session UID, Session marker of the information to employ (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. add_color ( * , color = (0.0, 0.0, 0.0, 0.0) , gamma = False , has_alpha = False ) 

Bring a hue node to the focal node panel

Parameters :

- color ( Sequence [ float ] ) – Color, Basis hue (array of 4 items, in [0, inf], optional)

- gamma ( bool ) – Gamma Corrected, The basis hue has gamma modification (optional)

- has_alpha ( bool ) – Has Alpha, The basis hue has an Opacity slot (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. add_empty_group ( * , settings = None , use_transform = False ) 

Bring a node bundle having a bare bundle

Parameters :

- settings ( bpy_prop_collection [ NodeSetting ]) – Settings, Setups to put on the fresh node (optional)

- use_transform ( bool ) – Use Transform, Launch transform tool after putting in the node (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:630

bpy.ops.node. add_foreach_geometry_element_zone ( * , settings = None , use_transform = False , offset = (150.0, 0.0) ) 

Generate a Per Each Form Part region that permits operating nodes once per shape element separately

Parameters :

- settings ( bpy_prop_collection [ NodeSetting ]) – Settings, Setups to put on the fresh node (optional)

- use_transform ( bool ) – Use Transform, Launch transform tool after putting in the node (optional)

- offset ( Sequence [ float ] ) – Offset, How far to place nodes from the marker when putting them (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:729

bpy.ops.node. add_group ( * , name = '' , session_uid = 0 , show_datablock_in_node = True ) 

Bring a pre-built node bundle to the focal node panel

Parameters :

- name ( str ) – Name, Label of the information to employ (optional, never None)

- session_uid ( int ) – Session UID, Session marker of the information to employ (in [-inf, inf], optional)

- show_datablock_in_node ( bool ) – Show the information picker in the node, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. add_group_asset ( * , asset_library_type = 'LOCAL' , asset_library_identifier = '' , relative_asset_identifier = '' ) 

Bring a node group resource to the working node mesh

Parameters :

- asset_library_type (Literal[Asset Library Type Items]) – Asset Library Type, (optional)

- asset_library_identifier ( str ) – Asset Library Identifier, (optional, never None)

- relative_asset_identifier ( str ) – Relative Asset Identifier, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. add_group_input_node ( * , socket_identifier = '' , panel_identifier = 0 ) 

Put a Group Entry node with picked inlets to the focal node panel

Parameters :

- socket_identifier ( str ) – Socket Identifier, Inlet to put in the put group inlet/outlet node (optional, never None)

- panel_identifier ( int ) – Panel Identifier, Panel from which to put inlets to the put group inlet/outlet node (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. add_image ( * , filepath = '' , directory = '' , files = None , hide_props_region = True , check_existing = False , filter_blender = False , filter_backup = False , filter_image = True , filter_movie = True , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 9 , relative_path = True , show_multiview = False , use_multiview = False , display_type = 'DEFAULT' , sort_method = '' , name = '' , session_uid = 0 ) 

Bring a pic/reel record as node to the focal node panel

Parameters :

- filepath ( str ) – File Path, Path to record (optional, never None)

- directory ( str ) – Directory, Folder of the record (optional, never None)

- files ( bpy_prop_collection [ OperatorFileListElement ]) – Files, (optional)

- hide_props_region ( bool ) – Hide Operator Properties, Fold up the panel showing the tool options (optional)

- check_existing ( bool ) – Check Existing, Check and alert on rewriting present records (optional)

- filter_blender ( bool ) – Filter .blend files, (optional)

- filter_backup ( bool ) – Filter backup .blend files, (optional)

- filter_image ( bool ) – Filter pic records, (optional)

- filter_movie ( bool ) – Filter reel records, (optional)

- filter_python ( bool ) – Filter Python records, (optional)

- filter_font ( bool ) – Filter font records, (optional)

- filter_sound ( bool ) – Filter tone records, (optional)

- filter_text ( bool ) – Filter text records, (optional)

- filter_archive ( bool ) – Filter pack records, (optional)

- filter_btx ( bool ) – Filter btx records, (optional)

- filter_alembic ( bool ) – Filter Alembic records, (optional)

- filter_usd ( bool ) – Filter USD records, (optional)

- filter_obj ( bool ) – Filter OBJ records, (optional)

- filter_volume ( bool ) – Filter OpenVDB bulk records, (optional)

- filter_folder ( bool ) – Filter folders, (optional)

- filter_blenlib ( bool ) – Filter Blender IDs, (optional)

- filemode ( int ) – File Browser Mode, The setup for the record panel mode to open a .blend record, a book or a unique record (in [1, 9], optional)

- relative_path ( bool ) – Relative Path, Mark the record relative to the mix record (optional)

- show_multiview ( bool ) – Enable Multi-View, (optional)

- use_multiview ( bool ) – Use Multi-View, (optional)

- display_type ( Literal [ 'DEFAULT' , '`LIST_VERTICAL`' , '`LIST_HORIZONTAL`' , 'THUMBNAIL' ] ) – Display Type, (optional)

- DEFAULT
Default – Mechanically pick display for records.

- `LIST_VERTICAL`
Short List – Show records as brief roll.

- `LIST_HORIZONTAL`
Long List – Show records as a thorough roll.

- THUMBNAIL
Thumbnails – Show records as miniatures.

- sort_method ( Literal [ 'DEFAULT' , '`FILE_SORT_ALPHA`' , '`FILE_SORT_EXTENSION`' , '`FILE_SORT_TIME`' , '`FILE_SORT_SIZE`' , '`ASSET_CATALOG`' ] ) – File sorting mode, (optional)

- DEFAULT
Default – Mechanically pick sort technique for records.

- `FILE_SORT_ALPHA`
Name – Sort the record list by letter.

- `FILE_SORT_EXTENSION`
Extension – Sort the record list by type/suffix.

- `FILE_SORT_TIME`
Modified Date – Sort records by when they changed.

- `FILE_SORT_SIZE`
Size – Sort records by size.

- `ASSET_CATALOG`
Asset Catalog – Sort the tool roll so that tools in the same category stay together. Within one category, tools are sorted by label. The categories are in rank of the leveled group makeup.

- name ( str ) – Name, Label of the information to employ (optional, never None)

- session_uid ( int ) – Session UID, Session marker of the information to employ (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. add_import_node ( * , directory = '' , files = None ) 

Bring an import node to the node mesh

Parameters :

- directory ( str ) – Directory, Folder of the record (optional, never None)

- files ( bpy_prop_collection [ OperatorFileListElement ]) – Files, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. add_mask ( * , name = '' , session_uid = 0 ) 

Bring a marking node to the focal node panel

Parameters :

- name ( str ) – Name, Label of the information to employ (optional, never None)

- session_uid ( int ) – Session UID, Session marker of the information to employ (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. add_material ( * , name = '' , session_uid = 0 ) 

Bring a finish node to the focal node panel

Parameters :

- name ( str ) – Name, Label of the information to employ (optional, never None)

- session_uid ( int ) – Session UID, Session marker of the information to employ (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. add_node ( * , settings = None , use_transform = False , type = '' , visible_output = '' ) 

Bring a node to the working mesh

Parameters :

- settings ( bpy_prop_collection [ NodeSetting ]) – Settings, Setups to put on the fresh node (optional)

- use_transform ( bool ) – Use Transform, Launch transform tool after putting in the node (optional)

- type ( str ) – Node Type, Node variety (optional, never None)

- visible_output ( str ) – Output Name, If given, every outlet named otherwise will be shut (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:490

bpy.ops.node. add_object ( * , name = '' , session_uid = 0 ) 

Bring an object info node to the focal node panel

Parameters :

- name ( str ) – Name, Label of the information to employ (optional, never None)

- session_uid ( int ) – Session UID, Session marker of the information to employ (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. add_repeat_zone ( * , settings = None , use_transform = False , offset = (150.0, 0.0) ) 

Generate a repeat region that permits operating nodes a changing count of times

Parameters :

- settings ( bpy_prop_collection [ NodeSetting ]) – Settings, Setups to put on the fresh node (optional)

- use_transform ( bool ) – Use Transform, Launch transform tool after putting in the node (optional)

- offset ( Sequence [ float ] ) – Offset, How far to place nodes from the marker when putting them (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:729

bpy.ops.node. add_reroute ( * , path = None , cursor = 11 ) 

Bring a path node

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- cursor ( int ) – Cursor, (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. add_simulation_zone ( * , settings = None , use_transform = False , offset = (150.0, 0.0) )

Add simulation region entry and exit nodes to the working mesh

Parameters :

- settings ( bpy_prop_collection [ NodeSetting ]) – Settings, Setups to put on the fresh node (optional)

- use_transform ( bool ) – Use Transform, Launch transform tool after putting in the node (optional)

- offset ( Sequence [ float ] ) – Offset, How far to place nodes from the marker when putting them (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:729

bpy.ops.node. add_zone ( * , settings = None , use_transform = False , offset = (150.0, 0.0) , input_node_type = '' , output_node_type = '' , add_default_geometry_link = False ) 

Undescribed, think about adding to docs.

Parameters :

- settings ( bpy_prop_collection [ NodeSetting ]) – Settings, Setups to put on the fresh node (optional)

- use_transform ( bool ) – Use Transform, Launch transform tool after putting in the node (optional)

- offset ( Sequence [ float ] ) – Offset, How far to place nodes from the marker when putting them (array of 2 items, in [-inf, inf], optional)

- input_node_type ( str ) – Input Node, Says what entry node the made zone employs (optional, never None)

- output_node_type ( str ) – Output Node, Says what exit node the made zone employs (optional, never None)

- add_default_geometry_link ( bool ) – Add Geometry Link, When on, link inlets between shape components in this region (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/node.py:729

bpy.ops.node. attach ( ) 

Fasten working node to a frame

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. backimage_fit ( ) 

Fit the rear image to the view

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. backimage_move ( ) 

Shift node backdrop

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. backimage_sample ( ) 

Employ cursor to harvest rear image

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. backimage_zoom ( * , factor = 1.2 ) 

Blow up/shrink the rear image

Parameters :

factor ( float ) – Factor, (in [0, 10], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. bake_node_item_add ( * , node_identifier = 0 ) 

Append entry below working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. bake_node_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Shift working entry

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Shift route (optional)

- node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. bake_node_item_remove ( * , node_identifier = 0 ) 

Wipe out working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. capture_attribute_item_add ( * , node_identifier = 0 ) 

Append entry below working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. capture_attribute_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Shift working entry

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Shift route (optional)

- node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. capture_attribute_item_remove ( * , node_identifier = 0 ) 

Wipe out working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. clear_viewer_border ( ) 

Clear the marks for monitor work

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. clipboard_copy ( ) 

Grab the marked nodes to the inward clipboard

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. clipboard_paste ( * , offset = (0.0, 0.0) ) 

Put nodes from the inward clipboard to the working node mesh

Parameters :

offset ( Sequence [ float ] ) – Location, The 2D panel spot for the hub of the fresh nodes, or unchanged if not set (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. closure_input_item_add ( * , node_identifier = 0 ) 

Append entry below working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. closure_input_item_move ( * , direction = 'UP' , node_identifier = 0 ) 

Shift working entry

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Shift route (optional)

- node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.node. closure_input_item_remove ( * , node_identifier = 0 ) 

Wipe out working entry

Parameters :

node_identifier ( int ) – Node Identifier, Discretionary label of the node to run on (in [0, inf], optional)

Returns :

Result of the operator call.
