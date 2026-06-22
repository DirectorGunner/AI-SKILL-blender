# Scene Operators

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

### Scene Operators

bpy.ops.scene. delete ( )

Erase the currently active scene

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. drop_scene_asset ( * , session_uid = 0 )

Load a scene asset and make it the active view

Parameters :

session_uid ( int ) – Session UID, Identifier referencing the data-block the operator will use (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_add_edge_marks_to_keying_set ( )

Add paths for Freestyle Edge Mark attributes on chosen edges to the active keying set

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/freestyle.py:139

bpy.ops.scene. freestyle_add_face_marks_to_keying_set ( )

Add paths for Freestyle Face Mark attributes on chosen polygons to the active keying set

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/freestyle.py:170

bpy.ops.scene. freestyle_alpha_modifier_add ( * , type = '`ALONG_STROKE`' )

Insert an opacity modifier into the line style for the active lineset

Parameters :

type (Literal[Linestyle Alpha Modifier Type Items]) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_color_modifier_add ( * , type = '`ALONG_STROKE`' )

Insert a hue/saturation modifier into the line style for the active lineset

Parameters :

type (Literal[Linestyle Color Modifier Type Items]) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_fill_range_by_selection ( * , type = 'COLOR' , name = '' )

Set Range Min/Max by computing the distance span between chosen mesh objects and the source (either user-specified or the active camera)

Parameters :

- type ( Literal [ 'COLOR' , 'ALPHA' , 'THICKNESS' ] ) – Type, Specifies which modifier category to affect (optional)

- COLOR
Color – Color modifier type.

- ALPHA
Alpha – Alpha modifier type.

- THICKNESS
Thickness – Thickness modifier type.

- name ( str ) – Name, ID of the modifier to work on (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/freestyle.py:45

bpy.ops.scene. freestyle_geometry_modifier_add ( * , type = '2`D_OFFSET`' )

Insert a stroke path modifier into the line style for the active lineset

Parameters :

type (Literal[Linestyle Geometry Modifier Type Items]) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_lineset_add ( )

Append a new line set to the collection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_lineset_copy ( )

Save the active line set to the internal buffer

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_lineset_move ( * , direction = 'UP' )

Shift the active line set up or down in the collection

Parameters :

direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Which way to shift the active line set (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_lineset_paste ( )

Restore the internal buffer content to the active line set

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_lineset_remove ( )

Erase the active line set from the collection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_linestyle_new ( )

Establish a fresh line style that can be assigned to various line sets

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_modifier_copy ( )

Make a second instance of the modifier in the collection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_modifier_move ( * , direction = 'UP' )

Shift the modifier up or down in the collection

Parameters :

direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Which way to shift the selected modifier (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_modifier_remove ( )

Detach the modifier from the collection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_module_add ( )

Append a script to the style stack

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_module_move ( * , direction = 'UP' )

Shift the script up or down within the style stack

Parameters :

direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Which way to shift the selected script (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_module_open ( * , filepath = '' , make_internal = True )

Import and load a script file

Parameters :

- filepath ( str ) – filepath, (optional, never None)

- make_internal ( bool ) – Make internal, Embed the script file after importing (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/freestyle.py:215

bpy.ops.scene. freestyle_module_remove ( )

Erase the script from the stack

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_stroke_material_create ( )

Synthesize a material for Freestyle strokes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. freestyle_thickness_modifier_add ( * , type = '`ALONG_STROKE`' )

Insert a stroke width modifier into the line style for the active lineset

Parameters :

type (Literal[Linestyle Thickness Modifier Type Items]) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. gltf2_action_filter_refresh ( )

Reload the available animation list

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

addons_core/io_scene_gltf2/blender/com/gltf2_blender_ui.py:615

bpy.ops.scene. gpencil_brush_preset_add ( * , name = '' , remove_name = False , remove_active = False )

Record or discard a Grease Pencil brush configuration

Parameters :

- name ( str ) – Name, Configuration ID used to construct the file path (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.scene. gpencil_material_preset_add ( * , name = '' , remove_name = False , remove_active = False )

Record or discard a Grease Pencil material configuration

Parameters :

- name ( str ) – Name, Configuration ID used to construct the file path (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.scene. new ( * , type = 'NEW' )

Establish a fresh scene selected by kind

Parameters :

type ( Literal [ 'NEW' , 'EMPTY' , '`LINK_COPY`' , '`FULL_COPY`' ] ) – Type, (optional)

- NEW
New – Add a new, empty scene with default settings.

- EMPTY
Copy Settings – Add a new, empty scene, and copy settings from the current scene.

- `LINK_COPY`
Linked Copy – Link in the collections from the current scene (shallow copy).

- `FULL_COPY`
Full Copy – Make a full copy of the current scene.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. new_sequencer ( * , type = 'NEW' )

Establish a fresh scene by kind within the sequence editor, assigning it to the active strip

Parameters :

type ( Literal [ 'NEW' , 'EMPTY' , '`LINK_COPY`' , '`FULL_COPY`' ] ) – Type, (optional)

- NEW
New – Add a new, empty scene with default settings.

- EMPTY
Copy Settings – Add a new, empty scene, and copy settings from the current scene.

- `LINK_COPY`
Linked Copy – Link in the collections from the current scene (shallow copy).

- `FULL_COPY`
Full Copy – Make a full copy of the current scene.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. new_sequencer_scene ( * , type = 'NEW' )

Establish a fresh scene intended for sequence editor use

Parameters :

type ( Literal [ 'NEW' , 'EMPTY' , '`LINK_COPY`' , '`FULL_COPY`' ] ) – Type, (optional)

- NEW
New – Add a new, empty scene with default settings.

- EMPTY
Copy Settings – Add a new, empty scene, and copy settings from the current scene.

- `LINK_COPY`
Linked Copy – Link in the collections from the current scene (shallow copy).

- `FULL_COPY`
Full Copy – Make a full copy of the current scene.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. render_view_add ( )

Establish a new output viewport

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. render_view_remove ( )

Discard the chosen output viewport

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. view_layer_add ( * , type = 'NEW' )

Append a layer for controlling visibility and rendering

Parameters :

type ( Literal [ 'NEW' , 'COPY' , 'EMPTY' ] ) – Type, (optional)

- NEW
New – Add a new view layer.

- COPY
Copy Settings – Copy settings of current view layer.

- EMPTY
Blank – Add a new view layer with all collections disabled.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. view_layer_add_aov ( )

Establish a fresh Shader AOV (Arbitrary Output Variable)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. view_layer_add_lightgroup ( * , name = '' )

Append a Light Group

Parameters :

name ( str ) – Name, Identifier for the generated lightgroup (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. view_layer_add_used_lightgroups ( )

Enlist all active Light Groups

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. view_layer_remove ( )

Discard the chosen layer for visibility and rendering

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. view_layer_remove_aov ( )

Discard the current Shader AOV

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. view_layer_remove_lightgroup ( )

Discard the current Lightgroup

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.scene. view_layer_remove_unused_lightgroups ( )

Discard unused Light Groups

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
