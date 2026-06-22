# Uilist Bpy Struct

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

### UIList(bpy_struct)

### Basic UIList Example

Below is the UIList subclass that drives the material-slots list, annotated heavily so each step is clear.

Pay attention to how the class is named — the convention mirrors the one used for panels and menus.

Note

A UIList subclass has to be registered before Blender will make use of it.

`text
import bpy

class `MATERIAL_UL`_matslots_example(bpy.types.UIList):
### The draw_item function is called for each item of the collection that is visible in the list.
### data is the RNA object containing the collection,
### item is the current drawn item of the collection,
### icon is the "computed" icon for the item (as an integer, because some objects like materials or textures
### have custom icons ID, which are not available as enum items).
### active_data is the RNA object containing the active property for the collection (i.e. integer pointing to the
### active item of the collection).
### active_propname is the name of the active property (use 'getattr(active_data, active_propname)').
### index is index of the current item in the collection.
### flt_flag is the result of the filtering process for this item.
### Note: as index and flt_flag are optional arguments, you do not have to use/declare them here if you don't
### need them.
def draw_item(self, context, layout, data, item, icon, active_data, active_propname):
ob = data
slot = item
ma = slot.material
### You should always start your row layout by a label (icon + text), or a non-embossed text field,
### this will also make the row easily selectable in the list! The later also enables ctrl-click rename.
### We use icon_value of label, as our given icon is an integer value, not an enum ID.
### Note "data" names should never be translated!
if ma:
layout.prop(ma, "name", text="", emboss=False, icon_value=icon)
else:
layout.label(text="", translate=False, icon_value=icon)

### And now we can use this list everywhere in Blender. Here is a small example panel.
class UIListPanelExample1(bpy.types.Panel):
"""Creates a Panel in the Object properties window"""
bl_label = "UIList Example 1 Panel"
bl_idname = "`OBJECT_PT`_ui_list_example_1"
bl_space_type = 'PROPERTIES'
bl_region_type = 'WINDOW'
bl_context = "object"

def draw(self, context):
layout = self.layout

obj = context.object

### `template_list` now takes two new arguments.
### The first one is the identifier of the registered UIList to use (if you want only the default list,
### with no custom draw code, use "`UI_UL`_list").
layout.template_list("`MATERIAL_UL`_matslots_example", "", obj, "material_slots", obj, "active_material_index")

### The second one can usually be left as an empty string.
### It's an additional ID used to distinguish lists in case you use the same list several times in a given area.
layout.template_list("`MATERIAL_UL`_matslots_example", "compact", obj, "material_slots",
obj, "active_material_index", type='COMPACT')

def register():
bpy.utils.register_class(`MATERIAL_UL`_matslots_example)
bpy.utils.register_class(UIListPanelExample1)

def unregister():
bpy.utils.unregister_class(UIListPanelExample1)
bpy.utils.unregister_class(`MATERIAL_UL`_matslots_example)

if __name__ == "__main__":
register()
`

### Advanced UIList Example - Filtering and Reordering

This longer version of the vertex-groups UIList subclass is shown for illustration only — walking every vertex inside a ‘draw’ callback would wreck UI performance, so you would not ship it as-is. Even so, it demonstrates nicely how filtering and reordering callbacks fit together.

`text
import bpy

class `MESH_UL`_vgroups_slow(bpy.types.UIList):
### Constants (flags).
### Be careful not to shadow `FILTER_ITEM`!
`VGROUP_EMPTY` = 1 new_idx`).
### Please note that the default `UI_UL`_list defines helper functions for common tasks (see its doc for more info).
### If you do not make filtering and/or ordering, return empty list(s) (this will be more efficient than
### returning full lists doing nothing!).
vgroups = getattr(data, propname)
helper_funcs = bpy.types.`UI_UL`_list

### Default return values.
flt_flags = []
flt_neworder = []

### Pre-compute of vertex-groups data, unfortunately this is CPU-intensive.
vgroups_empty = self.filter_items_empty_vgroups(context, vgroups)

### Filtering by name.
if self.filter_name:
flt_flags = helper_funcs.filter_items_by_name(self.filter_name, self.bitflag_filter_item, vgroups, "name",
reverse=self.use_filter_name_reverse)
if not flt_flags:
flt_flags = [self.bitflag_filter_item] * len(vgroups)

### Filter by emptiness.
for idx, vg in enumerate(vgroups):
if vgroups_empty[vg.index][0]:
flt_flags[idx] |= self.`VGROUP_EMPTY`
if self.use_filter_empty and self.use_filter_empty_reverse:
flt_flags[idx] &= ~self.bitflag_filter_item
elif self.use_filter_empty and not self.use_filter_empty_reverse:
flt_flags[idx] &= ~self.bitflag_filter_item

### Reorder by name or average weight.
if self.use_order_name:
flt_neworder = helper_funcs.sort_items_by_name(vgroups, "name")
if self.use_filter_orderby_invert:
flt_neworder.reverse()
elif self.use_order_importance:
_sort = [(idx, vgroups_empty[vg.index][1]) for idx, vg in enumerate(vgroups)]
highest_first = not self.use_filter_orderby_invert
flt_neworder = helper_funcs.sort_items_helper(_sort, lambda e: e[1], highest_first)

return flt_flags, flt_neworder

### Minimal code to use above UIList...
class UIListPanelExample2(bpy.types.Panel):
"""Creates a Panel in the Object properties window"""
bl_label = "UIList Example 2 Panel"
bl_idname = "`OBJECT_PT`_ui_list_example_2"
bl_space_type = 'PROPERTIES'
bl_region_type = 'WINDOW'
bl_context = "object"

def draw(self, context):
layout = self.layout
obj = context.object

### `template_list` now takes two new arguments.
### The first one is the identifier of the registered UIList to use (if you want only the default list,
### with no custom draw code, use "`UI_UL`_list").
layout.template_list("`MESH_UL`_vgroups_slow", "", obj, "vertex_groups", obj.vertex_groups, "active_index")

def register():
bpy.utils.register_class(`MESH_UL`_vgroups_slow)
bpy.utils.register_class(UIListPanelExample2)

def unregister():
bpy.utils.unregister_class(UIListPanelExample2)
bpy.utils.unregister_class(`MESH_UL`_vgroups_slow)

if __name__ == "__main__":
register()
`

base class — bpy_struct

subclasses —
`ASSETBROWSER_UL`_metadata_tags, `CLIP_UL`_tracking_objects, `CURVES_UL`_attributes, `DATA_UL`_bone_collections, `FILEBROWSER_UL`_dir, `GPENCIL_UL`_annotation_layer, `GPENCIL_UL`_matslots, `GREASE_PENCIL_UL`_attributes, `GREASE_PENCIL_UL`_masks, `IMAGE_UL`_render_slots, `IMAGE_UL`_udim_tiles, `MASK_UL`_layers, `MATERIAL_UL`_matslots, `MESH_UL`_attributes, `MESH_UL`_color_attributes, `MESH_UL`_color_attributes_selector, `MESH_UL`_uvmaps, `MESH_UL`_vgroups, `PARTICLE_UL`_particle_systems, `PHYSICS_UL`_dynapaint_surfaces, `POINTCLOUD_UL`_attributes, `POSE_UL`_selection_set, `RENDER_UL`_renderviews, `SCENE_UL`_gltf2_filter_action, `SCENE_UL`_keying_set_paths, `TEXTURE_UL`_texpaintslots, `TEXTURE_UL`_texslots, `UI_UL`_list, `USERPREF_UL`_asset_libraries, `USERPREF_UL`_extension_repos, `VIEWLAYER_UL`_aov, `VIEWLAYER_UL`_linesets, `VOLUME_UL`_grids, `WORKSPACE_UL`_addons_items

class bpy.types. UIList ( bpy_struct )

UI list containing the elements of a collection

bitflag_filter_item

The value of the reserved bitflag ‘`FILTER_ITEM`’ (in filter_flags values) (in [0, inf], default 0, readonly)

Type :

int

bitflag_item_never_show

Skip the item from displaying in the list (in [0, inf], default 0, readonly)

Type :

int

bl_idname

If this is set, the uilist gets a custom ID, otherwise it takes the name of the class used to define the uilist (for example, if the class name is “`OBJECT_UL`_vgroups”, and bl_idname is not set by the script, then bl_idname = “`OBJECT_UL`_vgroups”) (default “”, never None)

Type :

str

filter_name

Only show items matching this name (use ‘*’ as wildcard) (default “”, never None)

Type :

str

layout_type

(default 'DEFAULT' , readonly)

Type :

Literal[Uilist Layout Type Items]

list_id

Identifier of the list, if any was passed to the “list_id” parameter of “template_list()” (default “”, readonly, never None)

Type :

str

use_filter_invert

Invert filtering (show hidden items, and vice versa) (default False)

Type :

bool

use_filter_show

Show filtering options (default False)

Type :

bool

use_filter_sort_alpha

Sort items by their name (default False)

Type :

bool

use_filter_sort_lock

Lock the order of shown items (user cannot change it) (default False)

Type :

bool

use_filter_sort_reverse

Reverse the order of shown items (default False)

Type :

bool

bl_system_properties_get ( * , do_create = False )

DEBUG ONLY. Internal access to runtime-defined RNA data storage, intended solely for testing and debugging purposes. Do not access it in regular scripting work, and in particular, do not assume that it contains writable data

Parameters :

do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)

Returns :

The system properties root container, or None if there are no system properties stored in this data yet, and its creation was not requested

Return type :

PropertyGroup

draw_item ( context , layout , data , item , icon , active_data , active_property , index , flt_flag )

Draw an item in the list (NOTE: when you define your own draw_item function, you may want to check given ‘item’ is of the right type…)

Parameters :

- layout (UILayout) – Layout to draw the item (never None)

- data (AnyType) – Data from which to take Collection property

- item (AnyType) – Item of the collection property

- icon ( int ) – Icon of the item in the collection (in [0, inf])

- active_data (AnyType) – Data from which to take property for the active element (never None)

- active_property ( str ) – Identifier of property in active_data, for the active element (optional for registration, never None)

- index ( int ) – Index of the item in the collection (in [0, inf])

- flt_flag ( int ) – The filter-flag result for this item (in [0, inf])

draw_filter ( context , layout )

Draw filtering options

Parameters :

layout (UILayout) – Layout to draw the item (never None)

filter_items ( context , data , property )

Filter and/or re-order items of the collection (output filter results in filter_flags, and reorder results in filter_neworder arrays)

Parameters :

- data (AnyType) – Data from which to take Collection property

- property ( str ) – Identifier of property in data, for the collection (never None)

Returns :

filter_flags , An array of filter flags, one for each item in the collection (NOTE: The upper 16 bits, including `FILTER_ITEM`, are reserved, only use the lower 16 bits for custom usages), bpy_prop_array[int]

filter_neworder , An array of indices, one for each item in the collection, mapping the org index to the new one, bpy_prop_array[int]

Return type :

tuple[bpy_prop_array[int], bpy_prop_array[int]]

classmethod append ( draw_func )

Tack a draw function onto the end of this menu; it receives the same arguments as the menu’s own draw function.

classmethod is_extended ( )

classmethod prepend ( draw_func )

Insert a draw function at the front of this menu; it receives the same arguments as the menu’s own draw function.

classmethod remove ( draw_func )

Detach a draw function that was previously added to this menu.

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
