# Ui Operators

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Ui Operators 

bpy.ops.ui. assign_default_button ( ) 

Adopts the property's present value as its new default

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. button_execute ( * , skip_depressed = False ) 

Triggers the button that is currently active

Parameters :

skip_depressed ( bool ) – Skip Depressed, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. button_string_clear ( ) 

Empties the text contents of the active button

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. copy_as_driver_button ( ) 

Builds a fresh driver that reads this property as its input and places it on the internal clipboard. Apply Paste Driver to attach it to a target property, or Paste Driver Variables to extend a driver that already exists

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. copy_data_path_button ( * , full_path = False ) 

Places this property's RNA data path onto the clipboard

Parameters :

full_path ( bool ) – full_path, Copy full data path (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. copy_driver_to_selected_button ( * , all = False ) 

Takes the driver from the active item's property and applies it to the matching property on every selected item that has it

Parameters :

all ( bool ) – All, Copy to selected the drivers of all elements of the array (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. copy_python_command_button ( ) 

Places the Python command behind this button onto the clipboard

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. copy_to_selected_button ( * , all = True ) 

Takes the active item's property value and writes it to the matching property on every selected item that has it

Parameters :

all ( bool ) – All, Copy to selected all elements of the array (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. drop_color ( * , color = (0.0, 0.0, 0.0, 0.0) , gamma = False , has_alpha = False ) 

Drops a color value onto buttons

Parameters :

- color ( Sequence [ float ] ) – Color, Source color (array of 4 items, in [0, inf], optional)

- gamma ( bool ) – Gamma Corrected, The source color is gamma corrected (optional)

- has_alpha ( bool ) – Has Alpha, The source color contains an Alpha component (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. drop_material ( * , session_uid = 0 ) 

Drags a material onto the Material slots shown in Properties

Parameters :

session_uid ( int ) – Session UID, Session UID of the data-block to use by the operator (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. drop_name ( * , string = '' ) 

Drops a name string onto a button

Parameters :

string ( str ) – String, The string value to drop into the button (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. editsource ( ) 

Opens the UI source code for the button currently active

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. eyedropper_bone ( ) 

Picks a bone from the 3D View or Outliner and saves it into a property

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. eyedropper_color ( * , prop_data_path = '' ) 

Picks a color from anywhere in the Blender window and saves it into a property

Parameters :

prop_data_path ( str ) – Data Path, Path of property to be set with the depth (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. eyedropper_colorramp ( ) 

Picks a color band

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. eyedropper_colorramp_point ( ) 

Picks a single point from a color band

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. eyedropper_depth ( * , prop_data_path = '' ) 

Reads a depth value from the 3D view

Parameters :

prop_data_path ( str ) – Data Path, Path of property to be set with the depth (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. eyedropper_driver ( * , mapping_type = '`SINGLE_MANY`' ) 

Chooses a property to serve as a driver target

Parameters :

mapping_type ( Literal [ '`SINGLE_MANY`' , 'DIRECT' , 'MATCH' , '`NONE_ALL`' , '`NONE_SINGLE`' ] ) – Mapping Type, Method used to match target and driven properties (optional)

- `SINGLE_MANY`
All from Target – Drive every component of this property from the single target chosen.

- DIRECT
Single from Target – Drive just this one component using the target chosen.

- MATCH
Match Indices – Set up a driver for each matched pair of elements.

- `NONE_ALL`
Manually Create Later – Set up drivers across all properties but leave the targets unset for now.

- `NONE_SINGLE`
Manually Create Later (Single) – Set up a driver for this property alone, with no target assigned yet.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. eyedropper_grease_pencil_color ( * , mode = 'MATERIAL' , material_mode = 'STROKE' ) 

Picks a color from the Blender Window and builds a Grease Pencil material from it

Parameters :

- mode ( Literal [ 'MATERIAL' , 'PALETTE' , 'BRUSH' ] ) – Mode, (optional)

- material_mode ( Literal [ 'STROKE' , 'FILL' , 'BOTH' ] ) – Material Mode, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. eyedropper_id ( ) 

Picks a data-block from the 3D View and saves it into a property

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. jump_to_target_button ( ) 

Jumps to the object or bone that is targeted

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. list_start_filter ( ) 

Begins typing filter text for whichever list currently has focus

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. override_add_button ( * , all = True ) 

Adds an override operation

Parameters :

all ( bool ) – All, Add overrides for all elements of the array (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. override_idtemplate_clear ( ) 

Removes the chosen local override; where possible its uses are reconnected to the linked data-block, otherwise it is reset and locked from editing

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. override_idtemplate_make ( ) 

Makes a local override of the chosen linked data-block together with everything it depends on

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. override_idtemplate_reset ( ) 

Restores the chosen local override back to the values of its linked reference

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. override_remove_button ( * , all = True ) 

Deletes an override operation

Parameters :

all ( bool ) – All, Reset to default values all elements of the array (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. reloadtranslation ( ) 

Triggers a complete reload of the UI translation

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. reset_default_button ( * , all = True ) 

Returns this property to its default value

Parameters :

all ( bool ) – All, Reset to default values all elements of the array (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. unset_property_button ( ) 

Clears the property so operators fall back to a default or generated value

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. view_drop ( ) 

Performs a drag-and-drop onto a data-set or one of its items

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. view_item_delete ( ) 

Removes the list item that is selected

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. view_item_rename ( ) 

Renames whichever item is active in the data-set view

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. view_item_select ( * , wait_to_deselect_others = False , use_select_on_click = False , mouse_x = 0 , mouse_y = 0 , extend = False , range_select = False ) 

Makes the chosen view item active

Parameters :

- wait_to_deselect_others ( bool ) – Wait to Deselect Others, (optional)

- use_select_on_click ( bool ) – Act on Click, Instead of selecting on mouse press, wait to see if there’s drag event. Otherwise select on mouse release (optional)

- mouse_x ( int ) – Mouse X, (in [-inf, inf], optional)

- mouse_y ( int ) – Mouse Y, (in [-inf, inf], optional)

- extend ( bool ) – extend, Extend Selection (optional)

- range_select ( bool ) – Range Select, Select all between clicked and active items (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. view_scroll ( ) 

Undocumented, consider contributing.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ui. view_start_filter ( ) 

Begins typing filter text for whichever data-set currently has focus

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
