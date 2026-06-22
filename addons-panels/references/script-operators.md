# Script Operators, Spreadsheet Operators, Surface Operators, Text Editor Operators ...

> Blender Add-ons, Panels, and Properties reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Script Operators; Spreadsheet Operators; Surface Operators; Text Editor Operators; Uilist Operators; View2D Operators; bpy_prop; bpy_prop_collection; bpy_extras submodule (bpy_extras.asset_utils); bpy_extras submodule (bpy_extras.keyconfig_utils).

## Script Operators

### Script Operators

bpy.ops.script. execute_preset ( * , filepath = '' , menu_idname = '' )

Retrieve a configuration

Parameters :

- filepath ( str ) – filepath, (optional, never None)

- menu_idname ( str ) – Menu ID Name, ID name of the menu this was called from (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:285

bpy.ops.script. python_file_run ( * , filepath = '' )

Execute a script file

Parameters :

filepath ( str ) – Path, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.script. reload ( )

Reinitialize all scripts

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## Spreadsheet Operators

### Spreadsheet Operators

bpy.ops.spreadsheet. add_row_filter_rule ( )

Add a filter rule to hide rows from the display

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.spreadsheet. change_spreadsheet_data_source ( * , component_type = 0 , attribute_domain_type = 0 )

Switch the visible data in the spreadsheet view

Parameters :

- component_type ( int ) – Component Type, (in [0, 32767], optional)

- attribute_domain_type ( int ) – Attribute Domain Type, (in [0, 32767], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.spreadsheet. fit_column ( )

Adjust a spreadsheet column to match its content width

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.spreadsheet. remove_row_filter_rule ( * , index = 0 )

Delete a row filter from active rules

Parameters :

index ( int ) – Index, (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.spreadsheet. reorder_columns ( )

Alter column sequence

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.spreadsheet. resize_column ( )

Adjust spreadsheet column size

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.spreadsheet. toggle_pin ( )

Enable or disable pinning mode

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/spreadsheet.py:21

## Surface Operators

### Surface Operators

bpy.ops.surface. primitive_nurbs_surface_circle_add ( * , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Create a NURBS surface in circular form

Parameters :

- radius ( float ) – Radius, (in [0, inf], optional)

- enter_editmode ( bool ) – Enter Edit Mode, Enter edit mode when adding this object (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.surface. primitive_nurbs_surface_curve_add ( * , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Create a NURBS surface from a curve

Parameters :

- radius ( float ) – Radius, (in [0, inf], optional)

- enter_editmode ( bool ) – Enter Edit Mode, Enter edit mode when adding this object (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.surface. primitive_nurbs_surface_cylinder_add ( * , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Create a NURBS surface in cylindrical form

Parameters :

- radius ( float ) – Radius, (in [0, inf], optional)

- enter_editmode ( bool ) – Enter Edit Mode, Enter edit mode when adding this object (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.surface. primitive_nurbs_surface_sphere_add ( * , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Create a NURBS surface in spherical form

Parameters :

- radius ( float ) – Radius, (in [0, inf], optional)

- enter_editmode ( bool ) – Enter Edit Mode, Enter edit mode when adding this object (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.surface. primitive_nurbs_surface_surface_add ( * , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Create a NURBS surface mesh element

Parameters :

- radius ( float ) – Radius, (in [0, inf], optional)

- enter_editmode ( bool ) – Enter Edit Mode, Enter edit mode when adding this object (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.surface. primitive_nurbs_surface_torus_add ( * , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Create a NURBS surface in toroidal form

Parameters :

- radius ( float ) – Radius, (in [0, inf], optional)

- enter_editmode ( bool ) – Enter Edit Mode, Enter edit mode when adding this object (optional)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Location for the newly added object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Rotation for the newly added object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Scale for the newly added object (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## Text Editor Operators

### Text Editor Operators

bpy.ops.text_editor. preset_add ( * , name = '' , remove_name = False , remove_active = False )

Create or destroy a Text Editor Preset

Parameters :

- name ( str ) – Name, Name of the preset, used to make the path name (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

## Uilist Operators

### Uilist Operators 

bpy.ops.uilist. entry_add ( * , list_path = '' , active_index_path = '' ) 

Inserts a new entry just after the currently active item in the list

Parameters :

- list_path ( str ) – list_path, (optional, never None)

- active_index_path ( str ) – active_index_path, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_ui/generic_ui_list.py:208

bpy.ops.uilist. entry_move ( * , list_path = '' , active_index_path = '' , direction = 'UP' ) 

Shifts a list entry upward or downward

Parameters :

- list_path ( str ) – list_path, (optional, never None)

- active_index_path ( str ) – active_index_path, (optional, never None)

- direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, (optional)

- UP
Up – Shift the active entry one slot higher.

- DOWN
Down – Shift the active entry one slot lower.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_ui/generic_ui_list.py:236

bpy.ops.uilist. entry_remove ( * , list_path = '' , active_index_path = '' ) 

Deletes whichever entry is selected from the list

Parameters :

- list_path ( str ) – list_path, (optional, never None)

- active_index_path ( str ) – active_index_path, (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_ui/generic_ui_list.py:191

## View2D Operators

### View2D Operators 

bpy.ops.view2d. edge_pan ( * , inside_padding = 1.0 , outside_padding = 0.0 , speed_ramp = 1.0 , max_speed = 500.0 , delay = 1.0 , zoom_influence = 0.0 ) 

Scrolls the view while the mouse rests against an edge

Parameters :

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

bpy.ops.view2d. ndof ( ) 

Pans and zooms the view with a 3D mouse device

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view2d. pan ( * , deltax = 0 , deltay = 0 ) 

Slides the view

Parameters :

- deltax ( int ) – Delta X, (in [-inf, inf], optional)

- deltay ( int ) – Delta Y, (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view2d. reset ( ) 

Returns the view to its default

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view2d. scroll_down ( * , deltax = 0 , deltay = 0 , page = False ) 

Moves the view downward

Parameters :

- deltax ( int ) – Delta X, (in [-inf, inf], optional)

- deltay ( int ) – Delta Y, (in [-inf, inf], optional)

- page ( bool ) – Page, Scroll down one page (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view2d. scroll_left ( * , deltax = 0 , deltay = 0 ) 

Moves the view leftward

Parameters :

- deltax ( int ) – Delta X, (in [-inf, inf], optional)

- deltay ( int ) – Delta Y, (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view2d. scroll_right ( * , deltax = 0 , deltay = 0 ) 

Moves the view rightward

Parameters :

- deltax ( int ) – Delta X, (in [-inf, inf], optional)

- deltay ( int ) – Delta Y, (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view2d. scroll_up ( * , deltax = 0 , deltay = 0 , page = False ) 

Moves the view upward

Parameters :

- deltax ( int ) – Delta X, (in [-inf, inf], optional)

- deltay ( int ) – Delta Y, (in [-inf, inf], optional)

- page ( bool ) – Page, Scroll up one page (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view2d. scroller_activate ( ) 

Scrolls the view by clicking and dragging the mouse

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view2d. smoothview ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True ) 

Undocumented, consider contributing.

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

bpy.ops.view2d. zoom ( * , deltax = 0.0 , deltay = 0.0 , use_cursor_init = True ) 

Zooms the view in or out

Parameters :

- deltax ( float ) – Delta X, (in [-inf, inf], optional)

- deltay ( float ) – Delta Y, (in [-inf, inf], optional)

- use_cursor_init ( bool ) – Use Mouse Position, Allow the initial mouse position to be used (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view2d. zoom_border ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , zoom_out = False ) 

Zooms the view in to the closest item enclosed by the border

Parameters :

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- zoom_out ( bool ) – Zoom Out, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view2d. zoom_in ( * , zoomfacx = 0.0375 , zoomfacy = 0.0375 ) 

Zooms the view in

Parameters :

- zoomfacx ( float ) – Zoom Factor X, (in [-inf, inf], optional)

- zoomfacy ( float ) – Zoom Factor Y, (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view2d. zoom_out ( * , zoomfacx = -0.0375 , zoomfacy = -0.0375 ) 

Zooms the view out

Parameters :

- zoomfacx ( float ) – Zoom Factor X, (in [-inf, inf], optional)

- zoomfacy ( float ) – Zoom Factor Y, (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## bpy_prop

### bpy_prop

class bpy.types. bpy_prop

The built-in base from which every property class derives.

as_bytes ( )

Hands back this string property encoded as bytes rather than as a Python str.

Returns :

The string as bytes.

Return type :

bytes

path_from_id ( )

Gives the data path that leads from the owning ID down to this property (as a string).

Returns :

The path from bpy.types.bpy_struct.id_data to this property.

Return type :

str

path_from_module ( )

Builds the complete data path to this struct, expressed as a string starting at the bpy module.

Returns :

The full path to the data.

Return type :

str

Raises :

ValueError – if the input data cannot be converted into a full data path.

Note

Even if all input data is correct, this function might
error out because Blender cannot derive a valid path.
The incomplete path will be printed in the error message.

update ( )

Fires the property's update callback.

Note

Assigning a property already triggers this, but on rare occasions
calling it directly is handy.

data

The bpy.types.bpy_struct that this property belongs to.

id_data

The bpy.types.ID object this data-block is from or None, (not available for all data types) (readonly)

Type :

bpy.types.ID

rna_type

Property type information exposed for introspection.

## bpy_prop_collection

### bpy_prop_collection

base classes — bpy_prop

class bpy.types. bpy_prop_collection ( bpy_prop )

The built-in class behind every collection.

find ( key )

Looks up a key inside a collection and hands back its index, or -1 if it isn't present
(mirroring Python's string find method of the same name).

Parameters :

key ( str ) – The identifier for the collection member.

Returns :

index of the key.

Return type :

int

foreach_get ( attr , seq )

Quick reads of a basic-type attribute stored across a collection.

Parameters :

- attr ( str ) – Name of the item attribute to read (for example co , normal or
select ). The attribute must be a basic type (bool, int or float).

For geometry attribute types, see Attribute.data_type.

- seq ( MutableSequence [ bool | int | float ] | buffer ) – Writable sequence or buffer receiving flattened values.
For array attributes, the length must be len(collection) * array_length .

Only works for 'basic type' properties (bool, int and float)!
Multi-dimensional arrays (like array of vectors) will be flattened into seq.

`	ext
import bpy

mesh = bpy.context.object.data
collection = mesh.vertices

### Allocate a flat list for the `co` property (X, Y, Z per vertex).
coords = [0.0] * len(collection) * 3

### Fast access.
collection.foreach_get("co", coords)

### Python equivalent (per-element iteration is much slower).
for i, vert in enumerate(collection):
coords[i * 3], coords[i * 3 + 1], coords[i * 3 + 2] = vert.co
`

foreach_set ( attr , seq )

Quick writes of a basic-type attribute stored across a collection.

Parameters :

- attr ( str ) – Name of the item attribute to write (for example co or
select ). The attribute must be a basic type (bool, int or float).

For geometry attribute types, see Attribute.data_type.

- seq ( Sequence [ bool | int | float ] | buffer ) – Sequence or buffer containing flattened values.
For array attributes, the length must be len(collection) * array_length .

Only works for 'basic type' properties (bool, int and float)!
seq must be uni-dimensional, multi-dimensional arrays (like array of vectors) will be re-created from it.

`	ext
import bpy

mesh = bpy.context.object.data
collection = mesh.vertices

### Flatten all Z coordinates to zero (X, Y, Z per vertex).
coords = [0.0] * len(collection) * 3
collection.foreach_get("co", coords)
for i in range(2, len(coords), 3):
coords[i] = 0.0

### Fast assignment.
collection.foreach_set("co", coords)

### Python equivalent (per-element iteration is much slower).
for i, vert in enumerate(collection):
vert.co = (coords[i * 3], coords[i * 3 + 1], coords[i * 3 + 2])
`

get ( key , default = None )

Hands back the item stored at key, or default when the key isn't present
(mirroring Python's dictionary method of the same name).

Parameters :

- key ( str ) – The identifier for the collection member.

- default ( Any ) – Optional argument for the value to return if
key is not found.

Returns :

The collection member or default.

Return type :

bpy_struct

items ( )

Hands back the member identifiers of this collection
(mirroring Python's dict.items() behavior).

Returns :

(key, value) pairs for each member of this collection.

Return type :

list[tuple[str, bpy.types.bpy_struct]]

keys ( )

Hands back the member identifiers of this collection
(mirroring Python's dict.keys() behavior).

Returns :

the identifiers for each member of this collection.

Return type :

list[str]

values ( )

Hands back the members of this collection
(mirroring Python's dict.values() behavior).

Returns :

The members of this collection.

Return type :

list[bpy.types.bpy_struct | None]

## bpy_extras submodule (bpy_extras.asset_utils)

### bpy_extras submodule (bpy_extras.asset_utils) 

Helpers covering asset-management tasks.

class bpy_extras.asset_utils. AssetBrowserPanel 

Mixin for panels meant to appear only within the asset browser.

classmethod asset_browser_panel_poll ( context ) 

Determine whether the panel ought to appear in the asset browser.

Parameters :

context (bpy.types.Context) – The context.

Returns :

True when the panel should be visible.

Return type :

bool

classmethod poll ( context ) 

Poll for asset browser visibility.

Parameters :

context (bpy.types.Context) – The context.

Returns :

True when the panel should be visible.

Return type :

bool

class bpy_extras.asset_utils. AssetMetaDataPanel 

Mixin for panels that present asset metadata inside the asset browser.

classmethod poll ( context ) 

Poll for asset browser with active asset metadata.

Parameters :

context (bpy.types.Context) – The context.

Returns :

True when the asset browser has active asset data.

Return type :

bool

class bpy_extras.asset_utils. SpaceAssetInfo 

Helper for testing whether a space happens to be an asset browser.

classmethod is_asset_browser ( space_data ) 

Determine whether the supplied space is an asset browser.

Parameters :

space_data (bpy.types.Space) – The space to check.

Returns :

True when the space is an asset browser.

Return type :

bool

classmethod is_asset_browser_poll ( context ) 

Poll whether the active space is an asset browser.

Parameters :

context (bpy.types.Context) – The context.

Returns :

True when the active space is an asset browser.

Return type :

bool

## bpy_extras submodule (bpy_extras.keyconfig_utils)

### bpy_extras submodule (bpy_extras.keyconfig_utils) 

bpy_extras.keyconfig_utils. addon_keymap_register ( keymap_data ) 

Register a batch of keymaps for add-ons from a list of keymaps.

For examples of the format used here, look at 'blender_default.py'.

Parameters :

keymap_data ( list [ tuple [ str , dict [ str , Any ] , dict [ str , Any ] ] ] ) – A list of keymap definitions to register.

bpy_extras.keyconfig_utils. addon_keymap_unregister ( keymap_data ) 

Remove a batch of add-on keymaps.

Parameters :

keymap_data ( list [ tuple [ str , dict [ str , Any ] , dict [ str , Any ] ] ] ) – A list of keymap definitions to unregister.

bpy_extras.keyconfig_utils. keyconfig_test ( kc ) 

Check a key configuration for duplicated key-map item assignments.

Parameters :

kc (bpy.types.KeyConfig) – The key configuration to test.

Returns :

True if any duplicates were found.

Return type :

bool
