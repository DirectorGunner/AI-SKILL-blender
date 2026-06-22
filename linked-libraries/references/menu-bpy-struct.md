# Menu Bpy Struct, Mesh Ul Attributes Uilist, Mesh Ul Color Attributes Uilist, Mesh Ul Color Attributes Selector Uilist ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Menu(bpy_struct); `MESH_UL`_attributes(UIList); `MESH_UL`_color_attributes(UIList); `MESH_UL`_color_attributes_selector(UIList); `MESH_UL`_uvmaps(UIList); `MESH_UL`_vgroups(UIList).

## Menu(bpy_struct)

### Menu(bpy_struct)

### Basic Menu Example

A minimal menu is shown below. What sets a menu apart from a panel is that it has to be invoked from a header, a panel, or some other menu rather than standing on its own.

The `CATEGORY_MT_name` form in `Menu.bl_idname` follows the standard naming pattern Blender expects for menus.

Note

Before a menu subclass can be referenced inside Blender, it has to be registered first.

Note

For menus, `UILayout.operator_context` defaults to `'EXEC_REGION_WIN'` instead of `'INVOKE_REGION_WIN'` (see Execution Context). Should an operator need to gather its inputs through `Operator.invoke`, you must assign that context yourself. Once a menu is embedded in something like a panel or a header, it picks up whatever execution context those elements use.

```text
import bpy

class BasicMenu(bpy.types.Menu):
bl_idname = "OBJECT_MT_select_test"
bl_label = "Select"

def draw(self, context):
layout = self.layout

layout.operator("object.select_all", text="Select/Deselect All").action = 'TOGGLE'
layout.operator("object.select_all", text="Inverse").action = 'INVERT'
layout.operator("object.select_random", text="Random")

bpy.utils.register_class(BasicMenu)

# Test call to display immediately.
bpy.ops.wm.call_menu(name="OBJECT_MT_select_test")
```

### Submenus

A handful of additional techniques are illustrated by the menu below.

```text
import bpy

class SubMenu(bpy.types.Menu):
bl_idname = "OBJECT_MT_select_submenu"
bl_label = "Select"

def draw(self, context):
layout = self.layout

layout.operator("object.select_all", text="Select/Deselect All").action = 'TOGGLE'
layout.operator("object.select_all", text="Inverse").action = 'INVERT'
layout.operator("object.select_random", text="Random")

# Access this operator as a sub-menu.
layout.operator_menu_enum("object.select_by_type", "type", text="Select All by Type")

layout.separator()

# Expand each operator option into this menu.
layout.operator_enum("object.light_add", "type")

layout.separator()

# Use existing menu.
layout.menu("VIEW3D_MT_transform")

bpy.utils.register_class(SubMenu)

# Test call to display immediately.
bpy.ops.wm.call_menu(name="OBJECT_MT_select_submenu")
```

### Extending Menus

Because add-on menus cannot point at the menus declared in Blender's bundled scripts, the workaround is to attach new entries onto menus that already exist.

Here `menu_draw` behaves the same way `Menu.draw` does.

```text
import bpy

def menu_draw(self, context):
self.layout.operator("wm.save_homefile")

bpy.types.TOPBAR_MT_file.append(menu_draw)
```

### Preset Menus

Rather than being a distinct feature, a preset menu is just a convention: subclass a menu and use it to handle the routine job of managing presets.

Adding a preset menu is demonstrated here.

The object display options drive this particular example, but the same approach works against properties your own scripts declare.

```text
import bpy
from bpy.types import Operator, Menu
from bl_operators.presets import AddPresetBase

class OBJECT_MT_display_presets(Menu):
bl_label = "Object Display Presets"
preset_subdir = "object/display"
preset_operator = "script.execute_preset"
draw = Menu.draw_preset

class AddPresetObjectDisplay(AddPresetBase, Operator):
'''Add a Object Display Preset'''
bl_idname = "camera.object_display_preset_add"
bl_label = "Add Object Display Preset"
preset_menu = "OBJECT_MT_display_presets"

# Variable used for all preset values.
preset_defines = [
"obj = bpy.context.object"
]

# Properties to store in the preset.
preset_values = [
"obj.display_type",
"obj.show_bounds",
"obj.display_bounds_type",
"obj.show_name",
"obj.show_axis",
"obj.show_wire",
]

# Where to store the preset.
preset_subdir = "object/display"

# Display into an existing panel.
def panel_func(self, context):
layout = self.layout

row = layout.row(align=True)
row.menu(OBJECT_MT_display_presets.__name__, text=OBJECT_MT_display_presets.bl_label)
row.operator(AddPresetObjectDisplay.bl_idname, text="", icon='ZOOM_IN')
row.operator(AddPresetObjectDisplay.bl_idname, text="", icon='ZOOM_OUT').remove_active = True

classes = (
OBJECT_MT_display_presets,
AddPresetObjectDisplay,
)

def register():
for cls in classes:
bpy.utils.register_class(cls)
bpy.types.OBJECT_PT_display.prepend(panel_func)

def unregister():
for cls in classes:
bpy.utils.unregister_class(cls)
bpy.types.OBJECT_PT_display.remove(panel_func)

if __name__ == "__main__":
register()
```

### Extending the Button Context Menu

With this approach you can add a custom entry to the right-click menu that pops up whenever the cursor is over a UI button (an operator, a value field, a color, a string, and so on).

For the example to run, select an object first, then right-click on some interface widget — perhaps a color in the material properties — and pick Execute Custom Action.

Running the operator prints every value out.

```text
import bpy

def dump(obj, text):
for attr in dir(obj):
print("{!r}.{:s} = {!s}".format(obj, attr, getattr(obj, attr)))

class WM_OT_button_context_test(bpy.types.Operator):
"""Right click entry test"""
bl_idname = "wm.button_context_test"
bl_label = "Run Context Test"

@classmethod
def poll(cls, context):
return context.active_object is not None

def execute(self, context):
value = getattr(context, "button_pointer", None)
if value is not None:
dump(value, "button_pointer")

value = getattr(context, "button_prop", None)
if value is not None:
dump(value, "button_prop")

value = getattr(context, "button_operator", None)
if value is not None:
dump(value, "button_operator")

return {'FINISHED'}

def draw_menu(self, context):
layout = self.layout
layout.separator()
layout.operator(WM_OT_button_context_test.bl_idname)

def register():
bpy.utils.register_class(WM_OT_button_context_test)
bpy.types.UI_MT_button_context_menu.append(draw_menu)

def unregister():
bpy.types.UI_MT_button_context_menu.remove(draw_menu)
bpy.utils.unregister_class(WM_OT_button_context_test)

if __name__ == "__main__":
register()
```

base class — bpy_struct

class bpy.types. Menu ( bpy_struct )

Editor menu containing buttons

bl_description

(default "")

Type :

str

bl_idname

When set, this gives the menu an explicit ID; leave it unset and the menu inherits the defining class's name instead (so a class named "`OBJECT_MT`_hello" with no script-assigned bl_idname ends up with bl_idname = "`OBJECT_MT`_hello") (default "", never None)

Type :

str

bl_label

The menu label (default "", never None)

Type :

str

bl_options

Options for this menu type (default set())

- `SEARCH_ON_KEY_PRESS`
Search on Key Press – Open a menu search when a key pressed while the menu is open.

Type :

set[Literal[‘`SEARCH_ON_KEY_PRESS`’]]

bl_owner_id

(default "", never None)

Type :

str

bl_translation_context

(default "*", never None)

Type :

str

layout

Defines the structure of the menu in the UI (readonly)

Type :

UILayout

classmethod poll ( context )

When this method yields a non-null result, the menu is allowed to be drawn

Return type :

bool

draw ( context )

Lay out the menu's interface widgets within its UI layout

classmethod append ( draw_func )

Add a draw function onto the end of this menu; it receives the same arguments the menu's own draw function does

classmethod draw_collapsible ( context , layout )

draw_preset ( _context )

Set the following on your subclass:
- preset_operator (string)
- preset_subdir (string)

Optionally:
- preset_add_operator (string)
- preset_extensions (set of strings)
- preset_operator_defaults (dict of keyword args)

classmethod is_extended ( )

path_menu ( searchpaths , operator , * , props_default = None , prop_filepath = 'filepath' , filter_ext = None , filter_path = None , display_name = None , add_operator = None , add_operator_props = None , translate = True )

Populate a menu from a list of paths.

Parameters :

- searchpaths ( Sequence [ str ] ) – Paths to scan.

- operator ( str ) – The operator id to use with each file.

- prop_filepath ( str ) – Optional operator filepath property (defaults to "filepath").

- props_default ( dict [ str , Any ] | None ) – Properties to assign to each operator.

- filter_ext ( Callable [ [ str ] , bool ] | None ) – Optional callback that takes the file extensions.

Return false to drop the file from the listing.

- display_name ( Callable [ [ str ] , str ] | None ) – Optional callback that takes the full path, returns the name to display.

classmethod prepend ( draw_func )

Add a draw function onto the front of this menu; it receives the same arguments the menu's own draw function does

classmethod remove ( draw_func )

Detach a draw function that was previously attached to this menu.

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

## `MESH_UL`_attributes(UIList)

### `MESH_UL`_attributes(UIList)

base classes — bpy_struct, UIList

class bpy.types. `MESH_UL`_attributes ( UIList )

draw_item ( _context , layout , _data , attribute , _icon , _active_data , _active_propname , _index )

filter_items ( _context , data , property )

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |

## `MESH_UL`_color_attributes(UIList)

### `MESH_UL`_color_attributes(UIList)

base classes — bpy_struct, UIList

class bpy.types. `MESH_UL`_color_attributes ( UIList )

draw_item ( _context , layout , data , attribute , _icon , _active_data , _active_propname , _index )

filter_items ( _context , data , property )

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |

## `MESH_UL`_color_attributes_selector(UIList)

### `MESH_UL`_color_attributes_selector(UIList)

base classes — bpy_struct, UIList

class bpy.types. `MESH_UL`_color_attributes_selector ( UIList )

draw_item ( _context , layout , _data , attribute , _icon , _active_data , _active_propname , _index )

filter_items ( _context , data , property )

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |

## `MESH_UL`_uvmaps(UIList)

### `MESH_UL`_uvmaps(UIList)

base classes — bpy_struct, UIList

class bpy.types. `MESH_UL`_uvmaps ( UIList )

draw_item ( _context , layout , _data , item , icon , _active_data , _active_propname , _index )

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |

## `MESH_UL`_vgroups(UIList)

### `MESH_UL`_vgroups(UIList)

base classes — bpy_struct, UIList

class bpy.types. `MESH_UL`_vgroups ( UIList )

draw_item ( _context , layout , _data , item , icon , _active_data_ , _active_propname , _index )

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |
