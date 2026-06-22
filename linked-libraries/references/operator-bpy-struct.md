# Operator Bpy Struct

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

### Operator(bpy_struct) 

### Basic Operator Example 

A small operator that just prints a message.

Because this operator supplies only an Operator.execute function, it accepts no user input.

That function ought to give back {'FINISHED'} or {'CANCELLED'} ; the latter signals that the operator stopped without altering anything, so no undo step is recorded (the following example covers undo in more detail).

Note

You have to register Operator subclasses before Blender lets you reach them.

`\text
import bpy

class HelloWorldOperator(bpy.types.Operator):
bl_idname = "wm.hello_world"
bl_label = "Minimal Operator"

def execute(self, context):
print("Hello World")
return {'FINISHED'}

### Only needed if you want to add into a dynamic menu.
def menu_func(self, context):
self.layout.operator(HelloWorldOperator.bl_idname, text="Hello World Operator")

### Register and add to the view menu (required to also use F3 search "Hello World Operator" for quick access).
bpy.utils.register_class(HelloWorldOperator)
bpy.types.`VIEW3D_MT`_view.append(menu_func)

### Test call to the newly defined operator.
bpy.ops.wm.hello_world()
`

### Modifying Blender Data & Undo 

Whenever an operator changes Blender data it should switch on the 'UNDO' option. With that set, Blender records an undo step on its own once the operator's execute (or invoke , covered below) finishes and returns {'FINISHED'} .

Without it, no undo step gets recorded, which at minimum corrupts the undo stack and puzzles the user (since the operator's edits may be un-undoable, or may be rolled back along with unrelated earlier changes). In plenty of situations this even ends in data corruption and crashes.

Keep in mind that returning {'CANCELLED'} records no undo step. So when something goes wrong after data has already been changed, returning {'FINISHED'} is the safer choice — unless you can completely roll the changes back beforehand.

Note

Hardly any example on this page edits Blender data, which is why leaving the default bl_options value on these operators is safe.

Note

A few involved scenarios go beyond what the automatic exit-time undo step covers — for instance an operator that switches modes, or that fires off other operators which each need their own undo step.

You can issue such a manual undo push with the bpy.ops.ed.undo_push function. Tread carefully, though: it is an advanced feature that calls for some grasp of how Blender's undo system actually works internally.

`\text
import bpy

class DataEditOperator(bpy.types.Operator):
bl_idname = "object.data_edit"
bl_label = "Data Editing Operator"
### The default value is only 'REGISTER', 'UNDO' is mandatory when Blender data is modified
### (and does require 'REGISTER' as well).
bl_options = {'REGISTER', 'UNDO'}

def execute(self, context):
context.object.location.x += 1.0
return {'FINISHED'}

### Only needed if you want to add into a dynamic menu.
def menu_func(self, context):
self.layout.operator(DataEditOperator.bl_idname, text="Blender Data Editing Operator")

### Register.
bpy.utils.register_class(DataEditOperator)
bpy.types.`VIEW3D_MT`_view.append(menu_func)

### Test call to the newly defined operator.
bpy.ops.object.data_edit()
`

### Invoke Function 

Operator.invoke serves to set the operator up from the context at the instant it is called. invoke() usually sets properties that execute() then consumes. Certain operators lack an execute() function, which strips away the ability to replay them from a script or macro.

Calling an operator through bpy.ops makes the execution context follow the argument handed to bpy.ops; the default is execute(). Triggering an operator from a button or menu item instead respects the UILayout.operator_context setting, and most of the time that means invoke(). A key shortcut always runs an operator through invoke(), and there's no way to alter that.

The example below builds an operator that reads mouse input to run a function, and that can be invoked or executed from the Python API alike.

Note as well that this operator declares properties of its own — distinct from ordinary class properties, because Blender registers them with the operator so they can serve as call arguments, be stored for operator undo/redo, and be added to the interface automatically.

`\text
import bpy

class SimpleMouseOperator(bpy.types.Operator):
""" This operator shows the mouse location,
this string is used for the tooltip and API docs
"""
bl_idname = "wm.mouse_position"
bl_label = "Invoke Mouse Operator"

x: bpy.props.IntProperty()
y: bpy.props.IntProperty()

def execute(self, context):
### Rather than printing, use the report function,
### this way the message appears in the header.
self.report({'INFO'}, "Mouse coords are {:d} {:d}".format(self.x, self.y))
return {'FINISHED'}

def invoke(self, context, event):
self.x = event.mouse_x
self.y = event.mouse_y
return self.execute(context)

### Only needed if you want to add into a dynamic menu.
def menu_func(self, context):
self.layout.operator(SimpleMouseOperator.bl_idname, text="Simple Mouse Operator")

### Register and add to the view menu (required to also use F3 search "Simple Mouse Operator" for quick access).
bpy.utils.register_class(SimpleMouseOperator)
bpy.types.`VIEW3D_MT`_view.append(menu_func)

### Test call to the newly defined operator.
### Here we call the operator and invoke it,
### meaning that the settings are taken from the mouse.
bpy.ops.wm.mouse_position('`INVOKE_DEFAULT`')

### Another test call, this time call execute() directly with pre-defined settings.
bpy.ops.wm.mouse_position('`EXEC_DEFAULT`', x=20, y=66)
`

### Calling a File Selector 

Here is how an operator can bring up the file selector.

Observe that the invoke function calls a window manager method and gives back {'`RUNNING_MODAL`'} , so the file selector remains open and the operator doesn't quit the moment invoke finishes.

When the user confirms, the file selector runs the operator and triggers Operator.execute .

Operator.poll is optional and is there to verify whether the operator may run.

`\text
import bpy

class ExportSomeData(bpy.types.Operator):
"""Test exporter which just writes hello world"""
bl_idname = "export.some_data"
bl_label = "Export Some Data"

filepath: bpy.props.StringProperty(subtype="`FILE_PATH`")

@classmethod
def poll(cls, context):
return context.object is not None

def execute(self, context):
file = open(self.filepath, 'w')
file.write("Hello World " + context.object.name)
return {'FINISHED'}

def invoke(self, context, event):
context.window_manager.fileselect_add(self)
return {'`RUNNING_MODAL`'}

### Only needed if you want to add into a dynamic menu.
def menu_func(self, context):
self.layout.operator_context = '`INVOKE_DEFAULT`'
self.layout.operator(ExportSomeData.bl_idname, text="Text Export Operator")

### Register and add to the file selector (required to also use F3 search "Text Export Operator" for quick access).
bpy.utils.register_class(ExportSomeData)
bpy.types.`TOPBAR_MT`_file_export.append(menu_func)

### Test call.
bpy.ops.export.some_data('`INVOKE_DEFAULT`')
`

### Dialog Box 

This operator leans on its Operator.invoke function to raise a popup.

`\text
import bpy

class DialogOperator(bpy.types.Operator):
bl_idname = "object.dialog_operator"
bl_label = "Simple Dialog Operator"

my_float: bpy.props.FloatProperty(name="Some Floating Point")
my_bool: bpy.props.BoolProperty(name="Toggle Option")
my_string: bpy.props.StringProperty(name="String Value")

def execute(self, context):
message = "Popup Values: {:f}, {:d}, '{:s}'".format(
self.my_float, self.my_bool, self.my_string,
)
self.report({'INFO'}, message)
return {'FINISHED'}

def invoke(self, context, event):
wm = context.window_manager
return wm.invoke_props_dialog(self)

### Only needed if you want to add into a dynamic menu.
def menu_func(self, context):
self.layout.operator(DialogOperator.bl_idname, text="Dialog Operator")

### Register and add to the object menu (required to also use F3 search "Dialog Operator" for quick access).
bpy.utils.register_class(DialogOperator)
bpy.types.`VIEW3D_MT`_object.append(menu_func)

### Test call.
bpy.ops.object.dialog_operator('`INVOKE_DEFAULT`')
`

### Custom Drawing 

Out of the box, operator properties lay themselves out automatically. For finer control you can supply your own layout through an Operator.draw function.

It behaves the same way as the Panel and Menu draw functions, and is used for dialogs and file selectors.

`\text
import bpy

class CustomDrawOperator(bpy.types.Operator):
bl_idname = "object.custom_draw"
bl_label = "Simple Modal Operator"

filepath: bpy.props.StringProperty(subtype="`FILE_PATH`")

my_float: bpy.props.FloatProperty(name="Float")
my_bool: bpy.props.BoolProperty(name="Toggle Option")
my_string: bpy.props.StringProperty(name="String Value")

def execute(self, context):
print("Test", self)
return {'FINISHED'}

def invoke(self, context, event):
wm = context.window_manager
return wm.invoke_props_dialog(self)

def draw(self, context):
layout = self.layout
col = layout.column()
col.label(text="Custom Interface!")

row = col.row()
row.prop(self, "my_float")
row.prop(self, "my_bool")

col.prop(self, "my_string")

### Only needed if you want to add into a dynamic menu.
def menu_func(self, context):
self.layout.operator(CustomDrawOperator.bl_idname, text="Custom Draw Operator")

### Register and add to the object menu (required to also use F3 search "Custom Draw Operator" for quick access).
bpy.utils.register_class(CustomDrawOperator)
bpy.types.`VIEW3D_MT`_object.append(menu_func)

### Test call.
bpy.ops.object.custom_draw('`INVOKE_DEFAULT`')
`

### Modal Execution 

This operator supplies an Operator.modal function that keeps getting run to process events until it returns {'FINISHED'} or {'CANCELLED'} .

A modal operator fires each time a fresh event arrives, like a mouse click or a key press; when nothing new comes in, it stays idle. They shine in interactive tools, where the operator can hold its own state and let keys flip options while it runs. Grab, Rotate, Scale, and Fly-Mode are all modal operators.

Operator.invoke kicks the operator into its active state by returning {'`RUNNING_MODAL`'} , which starts the modal loop.

Observe that __init__() and __del__() are declared. They aren't worth much for other operator kinds, but for modal operators they run before Operator.invoke and again once the operator wraps up. The class construction and destruction section has more on this.

`\text
import bpy

class ModalOperator(bpy.types.Operator):
bl_idname = "object.modal_operator"
bl_label = "Simple Modal Operator"
bl_options = {'REGISTER', 'UNDO'}

def __init__(self, *args, **kwargs):
super().__init__(*args, **kwargs)
print("Start")

def __del__(self):
print("End")
super().__del__()

def execute(self, context):
context.object.location.x = self.value / 100.0
return {'FINISHED'}

def modal(self, context, event):
if event.type == 'MOUSEMOVE': # Apply.
self.value = event.mouse_x
self.execute(context)
elif event.type == 'LEFTMOUSE': # Confirm.
return {'FINISHED'}
elif event.type in {'RIGHTMOUSE', 'ESC'}: # Cancel.
### Revert all changes that have been made
context.object.location.x = self.init_loc_x
return {'CANCELLED'}

return {'`RUNNING_MODAL`'}

def invoke(self, context, event):
self.init_loc_x = context.object.location.x
self.value = event.mouse_x
self.execute(context)

context.window_manager.modal_handler_add(self)
return {'`RUNNING_MODAL`'}

### Only needed if you want to add into a dynamic menu.
def menu_func(self, context):
self.layout.operator(ModalOperator.bl_idname, text="Modal Operator")

### Register and add to the object menu (required to also use F3 search "Modal Operator" for quick access).
bpy.utils.register_class(ModalOperator)
bpy.types.`VIEW3D_MT`_object.append(menu_func)

### Test call.
bpy.ops.object.modal_operator('`INVOKE_DEFAULT`')
`

### Enum Search Popup 

When you want an operator to ask the user to pick an entry from a search field, reach for bpy.types.Operator.invoke_search_popup .

`\text
import bpy
from bpy.props import EnumProperty

class SearchEnumOperator(bpy.types.Operator):
bl_idname = "object.search_enum_operator"
bl_label = "Search Enum Operator"
bl_property = "my_search"

my_search: EnumProperty(
name="My Search",
items=(
('FOO', "Foo", ""),
('BAR', "Bar", ""),
('BAZ', "Baz", ""),
),
)

def execute(self, context):
self.report({'INFO'}, "Selected:" + self.my_search)
return {'FINISHED'}

def invoke(self, context, event):
context.window_manager.invoke_search_popup(self)
return {'`RUNNING_MODAL`'}

### Only needed if you want to add into a dynamic menu.
def menu_func(self, context):
self.layout.operator(SearchEnumOperator.bl_idname, text="Search Enum Operator")

### Register and add to the object menu (required to also use F3 search "Search Enum Operator" for quick access).
bpy.utils.register_class(SearchEnumOperator)
bpy.types.`VIEW3D_MT`_object.append(menu_func)

### Test call.
bpy.ops.object.search_enum_operator('`INVOKE_DEFAULT`')
`

base class — bpy_struct

class bpy.types. Operator ( bpy_struct ) 

Storage for an operator while it runs, or kept after it has run

bl_cursor_pending 

Cursor shown while the user is being asked to pick a spot to fire the operator (when bl_options carries `DEPENDS_ON_CURSOR`) (default 'DEFAULT' )

Type :

Literal[Window Cursor Items]

bl_description 

(default “”, never None)

Type :

str

bl_idname 

(default “”, never None)

Type :

str

bl_label 

(default “”, never None)

Type :

str

bl_options 

Options for this operator type (default set())

Type :

set[Literal[Operator Type Flag Items]]

bl_translation_context 

(default “Operator”, never None)

Type :

str

bl_undo_group 

(default “”, never None)

Type :

str

has_reports 

The operator carries a set of reports (warnings and errors) from its most recent run (default False, readonly)

Type :

bool

layout 

(readonly)

Type :

UILayout

macros 

(default None, readonly)

Type :

bpy_prop_collection[Macro]

name 

(default “”, readonly, never None)

Type :

str

options 

Runtime options (readonly, never None)

Type :

OperatorOptions

properties 

(readonly, never None)

Type :

OperatorProperties

bl_property 

The name of the property treated as this operator's primary one. At present it only picks the default property used when an operator is expanded into a menu.

Type :

str

report ( type , message ) 

report

Parameters :

- type (set[Literal[Wm Report Items]]) – Type

- message ( str ) – Report Message, (never None)

is_repeat ( ) 

is_repeat

Returns :

result

Return type :

bool

classmethod poll ( context ) 

Check whether the operator is allowed to run

Parameters :

context (Context) – (never None)

Return type :

bool

execute ( context ) 

Run the operator

Parameters :

context (Context) – (never None)

Returns :

result

Return type :

set[Literal[Operator Return Items]]

check ( context ) 

Re-evaluate the operator settings; return True to request a redraw

Parameters :

context (Context) – (never None)

Returns :

result

Return type :

bool

invoke ( context , event ) 

Invoke the operator

Parameters :

- context (Context) – (never None)

- event (Event) – (never None)

Returns :

result

Return type :

set[Literal[Operator Return Items]]

modal ( context , event ) 

Modal operator function

Parameters :

- context (Context) – (never None)

- event (Event) – (never None)

Returns :

result

Return type :

set[Literal[Operator Return Items]]

draw ( context ) 

Draw function for the operator

Parameters :

context (Context) – (never None)

cancel ( context ) 

Called when the operator is canceled

Parameters :

context (Context) – (never None)

classmethod description ( context , properties ) 

Work out a description string that varies with the parameters

Parameters :

- context (Context) – (never None)

- properties (OperatorProperties) – (never None)

Returns :

result

Return type :

str

as_keywords ( * , ignore = () ) 

Returns :

A copy of the properties as a dictionary.

Return type :

dict[str, Any]

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

classmethod poll_message_set ( message , * args ) 

Define the message displayed in the tool-tip when poll fails.

Should message be callable, any extra user-supplied positional arguments are forwarded to the message function.

Parameters :

- message ( str | Callable [ ... , str | None ] ) – The message or a function that returns the message.

- args ( Any ) – A sequence of arguments to pass to message , if it’s a callable, otherwise argument is not available.

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| bpy.context.active_operator SpaceFileBrowser.active_operator SpaceFileBrowser.operator Window.modal_operators WindowManager.fileselect_add WindowManager.invoke_confirm | WindowManager.invoke_popup WindowManager.invoke_props_dialog WindowManager.invoke_props_popup WindowManager.invoke_search_popup WindowManager.modal_handler_add WindowManager.operators |
