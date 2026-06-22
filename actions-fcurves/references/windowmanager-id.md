# Windowmanager Id, Windows Bpy Prop Collection, Wmownerid Bpy Struct, Wmownerids Bpy Prop Collection ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: WindowManager(ID); Windows(bpy_prop_collection); wmOwnerID(bpy_struct); wmOwnerIDs(bpy_prop_collection); wmTools(bpy_prop_collection).

## WindowManager(ID)

### WindowManager(ID)

base classes — bpy_struct, ID

class bpy.types. WindowManager ( ID )

Data-block holding the open windows and other interface state.

addon_filter

Filter add-ons by category

Type :

str

addon_search

Filter by add-on name, author & category (default "", never None)

Type :

str

addon_support

Display support level (default { 'COMMUNITY' , 'OFFICIAL' })

- OFFICIAL
Official – Officially supported.

- COMMUNITY
Community – Maintained by community developers.

Type :

set[Literal['OFFICIAL', 'COMMUNITY']]

addon_tags

(default None, readonly)

Type :

bpy_prop_collection[ BlExtDummyGroup ]

asset_path_dummy

Full path to the Blender file containing the active asset (default "", readonly, never None)

Type :

str

extension_repo_filter

Filter extensions by repository

Type :

str

extension_search

Filter by extension name, author & category (default "", never None)

Type :

str

extension_show_panel_available

Show the available extensions panel (default True)

Type :

bool

extension_show_panel_installed

Show the installed extensions panel (default True)

Type :

bool

extension_tags

(default None, readonly)

Type :

bpy_prop_collection[ BlExtDummyGroup ]

extension_type

Show extensions by type (default 'ADDON' )

- ALL
All – Show all extension types.

- ADDON
Add-ons – Only show add-ons.

- THEME
Themes – Only show themes.

Type :

Literal['ALL', 'ADDON', 'THEME']

extension_use_filter

Filter Extensions by Tags & Repository (default False)

Type :

bool

extensions_blocked

How many installed extensions are currently blocked (in [-inf, inf], default 0)

Type :

int

extensions_updates

How many extensions have an update available (in [-inf, inf], default 0)

Type :

int

is_interface_locked

When true, a running job holds the interface and application timers should not change data, since doing so could clash with the handler and cause odd results or crashes. (default False, readonly)

Type :

bool

keyconfigs

Registered key configurations (default None, readonly)

Type :

KeyConfigurations[KeyConfig]

operators

Operator registry (default None, readonly)

Type :

bpy_prop_collection[Operator]

poselib_previous_action

Type :

Action

preset_name

Name for new preset (default "New Preset", never None)

Type :

str

windows

Open windows (default None, readonly)

Type :

Windows[Window]

xr_session_settings

(readonly, never None)

Type :

XrSessionSettings

xr_session_state

Live state details about the VR session (readonly)

Type :

XrSessionState

clipboard

Clipboard text storage.

Type :

str

classmethod fileselect_add ( operator )

Opens a file selector with an operator.

Parameters :

operator (Operator) – Operator to call

This method is used from the operators invoke callback
which must then return {'`RUNNING_MODAL`'} .

Accepting the file selector will run the operators execute callback.

The following properties are supported:

filepath : bpy.props.StringProperty(subtype='`FILE_PATH`')
Represents the absolute path to the file.

dirpath : bpy.props.StringProperty(subtype='`DIR_PATH`')
Represents the absolute path to the directory.

filename : bpy.props.StringProperty(subtype='`FILE_NAME`')
Represents the filename without the leading directory.

files : bpy.props.CollectionProperty(type=bpy.types.OperatorFileListElement)
When present in the operator this collection includes all selected files.

filter_glob : bpy.props.StringProperty(default="*.ext")
When present in the operator and it's not empty,
it will be used as a file filter (example value: *.zip;*.py;*.exe ).

check_existing : bpy.props.BoolProperty()
If this property is present and set to True ,
the operator will warn if the provided file-path already exists
by highlighting the filename input field in red.

Warning

After opening the file-browser the user may continue to use Blender,
this means it is possible for the user to change the context in ways
that would cause the operators poll function to fail.

Unless the operator reads all necessary data from the context before the file-selector is opened,
it is recommended for operators to check the poll function from execute
to ensure the context is still valid.

Example from the body of an operators execute function:

`text
if self.options.is_invoke:
### The context may have changed since invoking the file selector.
if not self.poll(context):
self.report({'ERROR'}, "Invalid context")
return {'CANCELLED'}
`

classmethod modal_handler_add ( operator )

Add a modal handler to the window manager, for the given modal operator (called by invoke() with self, just before returning {'`RUNNING_MODAL`'})

Parameters :

operator (Operator) – Operator to call

Returns :

Whether adding the handler was successful

Return type :

bool

event_timer_add ( time_step , * , window = None )

Add a timer to the given window, to generate periodic 'TIMER' events

Parameters :

- time_step ( float ) – Time Step, Interval in seconds between timer events (in [0, inf])

- window (Window) – Window to attach the timer to, or None (optional)

Return type :

Timer

event_timer_remove ( timer )

event_timer_remove

Parameters :

timer (Timer) – (never None)

classmethod gizmo_group_type_ensure ( identifier )

Activate an existing widget group (when the persistent option isn't set)

Parameters :

identifier ( str ) – Gizmo group type name (never None)

classmethod gizmo_group_type_unlink_delayed ( identifier )

Unlink a widget group (when the persistent option is set)

Parameters :

identifier ( str ) – Gizmo group type name (never None)

progress_begin ( min , max )

Start progress report

Parameters :

- min ( float ) – min, any value in range [0,9999] (in [-inf, inf])

- max ( float ) – max, any value in range [min+1,9998] (in [-inf, inf])

progress_update ( value )

Update the progress feedback

Parameters :

value ( float ) – value, Any value between min and max as set in progress_begin() (in [-inf, inf])

progress_end ( )

Terminate progress report

classmethod invoke_props_popup ( operator , event )

Operator popup invoke (show operator properties and execute it automatically on changes)

Parameters :

- operator (Operator) – Operator to call

- event (Event) – Event

Returns :

result

Return type :

set[Literal[Operator Return Items]]

classmethod invoke_props_dialog ( operator , * , width = 300 , title = '' , confirm_text = '' , cancel_default = False , text_ctxt = '' , translate = True )

Operator dialog (non-autoexec popup) invoke (show operator properties and only execute it on click on OK button)

Parameters :

- operator (Operator) – Operator to call

- width ( int ) – Width of the popup (in [0, inf], optional)

- title ( str ) – Title, Optional text to show as title of the popup (optional, never None)

- confirm_text ( str ) – Confirm Text, Optional text to show instead to the default "OK" confirmation button text (optional, never None)

- cancel_default ( bool ) – cancel_default, (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

Returns :

result

Return type :

set[Literal[Operator Return Items]]

classmethod invoke_search_popup ( operator )

Operator search popup invoke which searches values of the operator's bpy.types.Operator.bl_property (which must be an EnumProperty), executing it on confirmation

Parameters :

operator (Operator) – Operator to call

classmethod invoke_popup ( operator , * , width = 300 )

Operator popup invoke (only shows operator's properties, without executing it)

Parameters :

- operator (Operator) – Operator to call

- width ( int ) – Width of the popup (in [0, inf], optional)

Returns :

result

Return type :

set[Literal[Operator Return Items]]

classmethod invoke_confirm ( operator , event , * , title = '' , message = '' , confirm_text = '' , icon = 'NONE' , text_ctxt = '' , translate = True )

Operator confirmation popup (only to let user confirm the execution, no operator properties shown)

Parameters :

- operator (Operator) – Operator to call

- event (Event) – Event

- title ( str ) – Title, Optional text to show as title of the popup (optional, never None)

- message ( str ) – Message, Optional first line of content text (optional, never None)

- confirm_text ( str ) – Confirm Text, Optional text to show instead to the default "OK" confirmation button text (optional, never None)

- icon ( Literal [ 'NONE' , 'WARNING' , 'QUESTION' , 'ERROR' , 'INFO' ] ) – Icon, Optional icon displayed in the dialog (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

Returns :

result

Return type :

set[Literal[Operator Return Items]]

classmethod popmenu_begin__internal ( title , * , icon = 'NONE' )

popmenu_begin__internal

Parameters :

- title ( str ) – (never None)

- icon (Literal[Icon Items]) – icon, (optional)

Returns :

(never None)

Return type :

UIPopupMenu

classmethod popmenu_end__internal ( menu )

popmenu_end__internal

Parameters :

menu (UIPopupMenu) – (never None)

classmethod popover_begin__internal ( * , ui_units_x = 0 , from_active_button = False )

popover_begin__internal

Parameters :

- ui_units_x ( int ) – ui_units_x, (in [0, inf], optional)

- from_active_button ( bool ) – Use Button, Use the active button for positioning (optional)

Returns :

(never None)

Return type :

UIPopover

classmethod popover_end__internal ( menu , * , keymap = None )

popover_end__internal

Parameters :

- menu (UIPopover) – (never None)

- keymap (KeyMap) – Key Map, Active key map (optional)

classmethod piemenu_begin__internal ( title , * , icon = 'NONE' , event = None )

piemenu_begin__internal

Parameters :

- title ( str ) – (never None)

- icon (Literal[Icon Items]) – icon, (optional)

- event (Event) – (optional, never None)

Returns :

(never None)

Return type :

UIPieMenu

classmethod piemenu_end__internal ( menu )

piemenu_end__internal

Parameters :

menu (UIPieMenu) – (never None)

classmethod operator_properties_last ( operator )

operator_properties_last

Parameters :

operator ( str ) – (never None)

Returns :

(never None)

Return type :

OperatorProperties

print_undo_steps ( )

print_undo_steps

classmethod tag_script_reload ( )

Tag for refreshing the interface after scripts have been reloaded

popover ( draw_func , * , ui_units_x = 0 , keymap = None , from_active_button = False )

popup_menu ( draw_func , * , title = '' , icon = 'NONE' )

Popup menus offer a way to build menus without registering menu classes first.

Because such a menu does not halt the running script, the caller has no way to pause for user input.

`text
import bpy

def draw(self, context):
self.layout.label(text="Hello World")

bpy.context.window_manager.popup_menu(draw, title="Greeting", icon='INFO')
`

popup_menu_pie ( event , draw_func , * , title = '' , icon = 'NONE' )

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

classmethod draw_cursor_add ( callback , args , space_type , region_type )

Register a new draw-cursor handler on this space type.
It runs each time the cursor is drawn for the named region within the space type.
Note: for the time being every argument is positional only.

Parameters :

- callback ( Callable [ ... , Any ] ) – The function invoked while the cursor is being drawn.
It receives the supplied arguments, with the mouse position ( tuple[int, int] ) handed in as the final one.

- args ( tuple [ Any , ... ] ) – The arguments forwarded into the callback.

- space_type ( str ) – The space type the callback draws in; for example `VIEW_3D` . (bpy.types.Space.type)

- region_type ( str ) – The region type the callback draws in; usually WINDOW . (bpy.types.Region.type)

Returns :

A handler you can remove afterward.

Return type :

object

classmethod draw_cursor_remove ( handler )

Take off a draw-cursor handler that was registered earlier.

Parameters :

handler ( object ) – The draw cursor handler that should be removed.

### Inherited Properties

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| BlendData.window_managers | Context.window_manager |

## Windows(bpy_prop_collection)

### Windows(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. Windows ( bpy_prop_collection ) 

A grouping that holds the open windows

find_playing ( * , scrub = False ) 

find_playing

Parameters :

scrub ( bool ) – Scrubbing, Tests whether the window's timeline is being dragged through (optional)

Returns :

Window, Window that is currently playing

Return type :

Window

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

| WindowManager.windows | |

## wmOwnerID(bpy_struct)

### wmOwnerID(bpy_struct) 

base class — bpy_struct

class bpy.types. wmOwnerID ( bpy_struct ) 

name 

(default “”, never None)

Type :

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

| WorkSpace.owner_ids wmOwnerIDs.new | wmOwnerIDs.remove |

## wmOwnerIDs(bpy_prop_collection)

### wmOwnerIDs(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. wmOwnerIDs ( bpy_prop_collection ) 

new ( name ) 

Append a new UI tag

Parameters :

name ( str ) – A name to assign to the new tag (never None)

Return type :

wmOwnerID

remove ( owner_id ) 

Delete a UI tag

Parameters :

owner_id (wmOwnerID) – The tag to delete (never None)

clear ( ) 

Delete every tag

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

| WorkSpace.owner_ids | |

## wmTools(bpy_prop_collection)

### wmTools(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. wmTools ( bpy_prop_collection ) 

from_space_view3d_mode ( mode , * , create = False ) 

Parameters :

create ( bool ) – Create, (optional)

Return type :

WorkSpaceTool

from_space_image_mode ( mode , * , create = False ) 

Parameters :

create ( bool ) – Create, (optional)

Return type :

WorkSpaceTool

from_space_node ( * , create = False ) 

Parameters :

create ( bool ) – Create, (optional)

Return type :

WorkSpaceTool

from_space_sequencer ( mode , * , create = False ) 

Parameters :

create ( bool ) – Create, (optional)

Return type :

WorkSpaceTool

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

| WorkSpace.tools | |
