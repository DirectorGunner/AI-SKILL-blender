# Keymaps Bpy Prop Collection, Library Id, Macro Bpy Struct, Mask Ul Layers Uilist

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: KeyMaps(bpy_prop_collection); Library(ID); Macro(bpy_struct); `MASK_UL`_layers(UIList).

## KeyMaps(bpy_prop_collection)

### KeyMaps(bpy_prop_collection) 

### Add-on Keymap Registration 

The snippet below demonstrates registering a custom shortcut from an add-on.
Such keymaps live under keyconfigs.addon and get torn down on unregister.

Keep each (keymap, keymap_item) pair around so cleanup is reliable, since the same keymap may be shared by several add-ons.

Note

The Keymap Preferences let users override an add-on's shortcuts.
An add-on's keymaps show up below the editors they apply to, where they
can be tweaked or switched off without touching the add-on's source.

Confine add-on changes to keyconfigs.addon and leave the user's own keymaps alone,
because the add-on's entries are only defaults that a user is free to override.
Editing user keymaps directly works against whatever the user has configured.

Warning

An add-on may extend an already-existing modal keymap, but Python
cannot be used to build a brand-new one. Pass modal=True to point at
an existing modal keymap, for instance the “Knife Tool Modal Map”.

`\text
### In this example keymap registration functions are only split out for clarity,
### so skipping keymap registration in background mode doesn't interfere with other registration logic.

import bpy

### Store (keymap, keymap_item) for cleanup on unregister.
addon_keymaps = []

def register_keymaps():
wm = bpy.context.window_manager
kc = wm.keyconfigs.addon
if kc is None:
return # Can be None in background mode.

### Target the 3D View; name must match Blender's built-in keymap exactly.
km = kc.keymaps.new(name="3D View", space_type='`VIEW_3D`')

### Bind Shift+Alt+K to frame selected objects.
kmi = km.keymap_items.new(
idname="view3d.view_selected",
type='K',
value='PRESS',
shift=True,
alt=True,
)
kmi.properties.use_all_regions = True

addon_keymaps.append((km, kmi))

def unregister_keymaps():
for km, kmi in addon_keymaps:
km.keymap_items.remove(kmi)
addon_keymaps.clear()

def register():
register_keymaps()

def unregister():
unregister_keymaps()

if __name__ == "__main__":
register()
`

base classes — bpy_prop, bpy_prop_collection

class bpy.types. KeyMaps ( bpy_prop_collection ) 

The collection that holds keymaps

new ( name , * , space_type = 'EMPTY' , region_type = 'WINDOW' , modal = False , tool = False ) 

Make sure the keymap is present. The matching one for the given name, space type, and region type is returned, and a new keymap is created only if none already exists.

Parameters :

- name ( str ) – Name, (never None)

- space_type (Literal[Space Type Items]) – Space Type, (optional)

- region_type (Literal[Region Type Items]) – Region Type, (optional)

- modal ( bool ) – Modal, Keymap for modal operators. Modal keymaps are not supported for KeyConfigs.addons . (optional)

- tool ( bool ) – Tool, Keymap for active tools (optional)

Returns :

Key Map, Added key map

Return type :

KeyMap

remove ( keymap ) 

remove

Parameters :

keymap (KeyMap) – Key Map, Removed key map (never None)

clear ( ) 

Remove all keymaps.

find ( name , * , space_type = 'EMPTY' , region_type = 'WINDOW' ) 

find

Parameters :

- name ( str ) – Name, (never None)

- space_type (Literal[Space Type Items]) – Space Type, (optional)

- region_type (Literal[Region Type Items]) – Region Type, (optional)

Returns :

Key Map, Corresponding key map

Return type :

KeyMap

find_match ( keymap ) 

find_match

Parameters :

keymap (KeyMap) – Key Map, The key map for comparison

Returns :

Key Map, Corresponding key map

Return type :

KeyMap

find_modal ( name ) 

find_modal

Parameters :

name ( str ) – Operator Name, (never None)

Returns :

Key Map, Corresponding key map

Return type :

KeyMap

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| KeyConfig.keymaps | |

## Library(ID)

### Library(ID) 

base classes — bpy_struct, ID

class bpy.types. Library ( ID ) 

External .blend file from which data is linked

archive_libraries 

Archive libraries holding packed IDs, created and owned by this source library (default None, readonly)

Type :

bpy_prop_collection[Library]

archive_parent_library 

The source library that produced this archive of packed IDs (readonly)

Type :

Library

filepath 

Path to the library .blend file (default “”, never None, blend relative // prefix supported)

Type :

str

is_archive 

This library acts as an 'archive' store for packed linked IDs that were originally linked from its 'archive parent' library. (default False, readonly)

Type :

bool

is_editable 

Even though linked, this library's data-blocks may be edited. Used by brush assets along with what they depend on. (default False, readonly)

Type :

bool

needs_liboverride_resync 

True when this library holds library overrides linked into the current blendfile that needed a recursive resync at load time (opening and re-saving that library blendfile is advised) (default False)

Type :

bool

packed_file 

(readonly)

Type :

PackedFile

parent 

(readonly)

Type :

Library

version 

Blender version that wrote the library .blend (array of 3 items, in [0, inf], default (0, 0, 0), readonly)

Type :

bpy_prop_array[int]

users_id 

The ID data-blocks that rely on this library

Type :

tuple[bpy.types.ID, …]

Note

Runs in O(n), with n being the count of every
linkable ID type found in bpy.data .

(readonly)

reload ( ) 

Reload this library and all its linked data-blocks

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References 

| BlendData.libraries BlendDataLibraries.remove BlendImportContextItem.source_library ID.library | Library.archive_libraries Library.archive_parent_library Library.parent |

## Macro(bpy_struct)

### Macro(bpy_struct)

### Example Macro

The snippet below builds a small macro operator that first translates the active object and then spins it.
It shows:

- Defining a macro operator class.

- Registering it and defining sub-operators.

- Setting property values for each step.

`text
import bpy

class `OBJECT_OT`_simple_macro(bpy.types.Macro):
bl_idname = "object.simple_macro"
bl_label = "Simple Transform Macro"
bl_options = {'REGISTER', 'UNDO'}

@classmethod
def poll(cls, context):
return context.active_object is not None

def register():
bpy.utils.register_class(`OBJECT_OT`_simple_macro)

### Define steps after registration and set operator values via .properties
step = `OBJECT_OT`_simple_macro.define("transform.translate")
props = step.properties
props.value = (1.0, 0.0, 0.0)
props.constraint_axis = (True, False, False)

step = `OBJECT_OT`_simple_macro.define("transform.rotate")
props = step.properties
props.value = 0.785398 # 45 degrees in radians
props.orient_axis = 'Z'

def unregister():
bpy.utils.unregister_class(`OBJECT_OT`_simple_macro)

if __name__ == "__main__":
register()

### To run the macro:
bpy.ops.object.simple_macro()
`

base class — bpy_struct

class bpy.types. Macro ( bpy_struct )

Holds a macro operator while it runs, or after it has been registered post-execution.

bl_cursor_pending

Cursor shown while waiting for the user to pick a location that triggers the operator (applies when bl_options has `DEPENDS_ON_CURSOR` set) (default 'DEFAULT' )

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

Flags configuring this operator type (default set())

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

Whether the operator produced any reports — warnings and errors — on its last run (default False, readonly)

Type :

bool

name

(default “”, readonly, never None)

Type :

str

properties

(readonly, never None)

Type :

OperatorProperties

report ( type , message )

report

Parameters :

- type (set[Literal[Wm Report Items]]) – Type

- message ( str ) – Report Message, (never None)

classmethod poll ( context )

Check whether the operator is allowed to run

Parameters :

context (Context) – (never None)

Return type :

bool

draw ( context )

Draw function for the operator

Parameters :

context (Context) – (never None)

classmethod define ( operator )

Append an operator to a registered macro class.

Parameters :

operator ( str ) – Identifier of the operator. This does not have to be defined when this function is called.

Returns :

The operator macro for property access.

Return type :

OperatorMacro

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

| Operator.macros | |

## `MASK_UL`_layers(UIList)

### `MASK_UL`_layers(UIList)

base classes — bpy_struct, UIList

class bpy.types. `MASK_UL`_layers ( UIList )

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
