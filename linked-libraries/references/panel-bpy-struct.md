# Panel Bpy Struct, Particle Ul Particle Systems Uilist, Physics Ul Dynapaint Surfaces Uilist, Pointcloud Ul Attributes Uilist ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Panel(bpy_struct); `PARTICLE_UL`_particle_systems(UIList); `PHYSICS_UL`_dynapaint_surfaces(UIList); `POINTCLOUD_UL`_attributes(UIList); `POSE_UL`_selection_set(UIList); PreferencesExperimental(bpy_struct); `RENDER_UL`_renderviews(UIList).

## Panel(bpy_struct)

### Panel(bpy_struct)

### Basic Panel Example

A minimal panel that renders into the object properties area is shown below.

Observe the `CATEGORY_PT_name` value given to Panel.bl_idname — Blender expects panel IDs to follow that naming pattern.

Note

Blender only recognizes Panel subclasses once they have been registered.

`text
import bpy

class HelloWorldPanel(bpy.types.Panel):
bl_idname = "`OBJECT_PT`_hello_world"
bl_label = "Hello World"
bl_space_type = 'PROPERTIES'
bl_region_type = 'WINDOW'
bl_context = "object"

def draw(self, context):
self.layout.label(text="Hello World")

bpy.utils.register_class(HelloWorldPanel)
`

### Simple Object Panel

Here both a Panel.poll and a Panel.draw_header are supplied; despite the modest body, the layout mirrors how Blender's own panels are built.

`text
import bpy

class ObjectSelectPanel(bpy.types.Panel):
bl_idname = "`OBJECT_PT`_select"
bl_label = "Select"
bl_space_type = 'PROPERTIES'
bl_region_type = 'WINDOW'
bl_context = "object"
bl_options = {'`DEFAULT_CLOSED`'}

@classmethod
def poll(cls, context):
return (context.object is not None)

def draw_header(self, context):
layout = self.layout
layout.label(text="My Select Panel")

def draw(self, context):
layout = self.layout

box = layout.box()
box.label(text="Selection Tools")
box.operator("object.select_all").action = 'TOGGLE'
row = box.row()
row.operator("object.select_all").action = 'INVERT'
row.operator("object.select_random")

bpy.utils.register_class(ObjectSelectPanel)
`

### Mix-in Classes

Shared properties together with a common Menu.poll can be factored out into a mix-in parent that several panels inherit from.

`text
import bpy

class View3DPanel:
bl_space_type = '`VIEW_3D`'
bl_region_type = 'UI'
bl_category = "Tool"

@classmethod
def poll(cls, context):
return (context.object is not None)

class PanelOne(View3DPanel, bpy.types.Panel):
bl_idname = "`VIEW3D_PT`_test_1"
bl_label = "Panel One"

def draw(self, context):
self.layout.label(text="Small Class")

class PanelTwo(View3DPanel, bpy.types.Panel):
bl_idname = "`VIEW3D_PT`_test_2"
bl_label = "Panel Two"

def draw(self, context):
self.layout.label(text="Also Small Class")

bpy.utils.register_class(PanelOne)
bpy.utils.register_class(PanelTwo)
`

base class — bpy_struct

class bpy.types. Panel ( bpy_struct )

Holds the UI elements that make up a panel

bl_category

The tab the panel appears under, where that applies (default “”, never None)

Type :

str

bl_context

Which context the panel is attached to. (TODO: explain the possible combinations bl_context/bl_region_type/bl_space_type) (default “”, never None)

Type :

str

bl_description

Tooltip shown for the panel (default “”)

Type :

str

bl_idname

When provided, gives the panel an explicit ID; left unset, the panel inherits the defining class name. So a class named “`OBJECT_PT`_hello” with no script-assigned bl_idname ends up with bl_idname = “`OBJECT_PT`_hello”. (default “”, never None)

Type :

str

bl_label

Text drawn in the panel header beside the collapse triangle (default “”, never None)

Type :

str

bl_options

Per-panel-type option flags (default set())

- `DEFAULT_CLOSED`
Default Closed – Decides whether the panel starts expanded or collapsed when first created.

- `HIDE_HEADER`
Hide Header – When False, a header is drawn carrying the collapse arrow and the label (see bl_label).

- INSTANCED
Instanced Panel – Lets several panels of this kind act as a list backed by data outside the UI. Powers the panels behind the modifier and similar stacks..

- `HEADER_LAYOUT_EXPAND`
Expand Header Layout – Lets header buttons grow or shrink so they span the full layout width.

Type :

set[Literal[‘`DEFAULT_CLOSED`’, ‘`HIDE_HEADER`’, ‘INSTANCED’, ‘`HEADER_LAYOUT_EXPAND`’]]

bl_order

Smaller values place a panel ahead of those with larger ones (in [0, inf], default 0)

Type :

int

bl_owner_id

ID that owns whatever data the panel shows, if there is one (default “”, never None)

Type :

str

bl_parent_id

When provided, turns the panel into a sub-panel (default “”, never None)

Type :

str

bl_region_type

Region in which the panel will appear (default 'WINDOW' )

Type :

Literal[Region Type Items]

bl_space_type

Editor space in which the panel will appear (default 'EMPTY' )

Type :

Literal[Space Type Items]

bl_translation_context

A translation context supplied only to tell apart labels that would otherwise be identical (default “*”, never None)

Type :

str

bl_ui_units_x

If given, sets the width of a popup panel (in [0, inf], default 0)

Type :

int

custom_data

Panel data (readonly)

Type :

Constraint

is_popover

(default False, readonly)

Type :

bool

layout

Lays out how the panel is arranged in the UI (readonly)

Type :

UILayout

text

Replacement string shown instead of the panel label in the UI (default “”, never None)

Type :

str

use_pin

Keep the panel visible across every tab (default False)

Type :

bool

classmethod poll ( context )

The panel is drawable whenever this method yields a non-null result

Parameters :

context (Context) – (never None)

Return type :

bool

draw ( context )

Render UI elements inside the panel layout

Parameters :

context (Context) – (never None)

draw_header ( context )

Render UI elements inside the panel header layout

Parameters :

context (Context) – (never None)

draw_header_preset ( context )

Render preset UI elements inside the panel header

Parameters :

context (Context) – (never None)

classmethod append ( draw_func )

Add a draw function at the end of this menu;
it receives the same arguments the menu draw function does

classmethod is_extended ( )

classmethod prepend ( draw_func )

Add a draw function at the start of this menu; it receives the same
arguments the menu draw function does

classmethod remove ( draw_func )

Detach a draw function previously added to this menu.

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

## `PARTICLE_UL`_particle_systems(UIList)

### `PARTICLE_UL`_particle_systems(UIList)

base classes — bpy_struct, UIList

class bpy.types. `PARTICLE_UL`_particle_systems ( UIList )

draw_item ( _context , layout , data , item , icon , _active_data , _active_propname , _index , _flt_flag )

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

## `PHYSICS_UL`_dynapaint_surfaces(UIList)

### `PHYSICS_UL`_dynapaint_surfaces(UIList)

base classes — bpy_struct, UIList

class bpy.types. `PHYSICS_UL`_dynapaint_surfaces ( UIList )

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

## `POINTCLOUD_UL`_attributes(UIList)

### `POINTCLOUD_UL`_attributes(UIList)

base classes — bpy_struct, UIList

class bpy.types. `POINTCLOUD_UL`_attributes ( UIList )

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

## `POSE_UL`_selection_set(UIList)

### `POSE_UL`_selection_set(UIList)

base classes — bpy_struct, UIList

class bpy.types. `POSE_UL`_selection_set ( UIList )

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

## PreferencesExperimental(bpy_struct)

### PreferencesExperimental(bpy_struct)

base class — bpy_struct

class bpy.types. PreferencesExperimental ( bpy_struct )

Features still considered experimental

no_data_block_packing

Append data-blocks as a fall-back rather than packing them (default False)

Type :

bool

override_auto_resync

Switch off the automatic resync check and processing for library overrides at file load (useful when repairing broken files). Mirrors the “–disable-liboverride-auto-resync” command line option (default False)

Type :

bool

show_asset_debug_info

Surface extra Asset Browser fields that help with debugging (default False)

Type :

bool

use_all_linked_data_direct

Treat every piece of linked data as directly linked. Works around current BAT (Blender studio pipeline tool) issues/limitations (default False)

Type :

bool

use_asset_indexing

Turn off the asset indexer so each asset library refresh rereads everything from disk (default False)

Type :

bool

use_cycles_debug

Expose Cycles debugging options aimed at developers (default False)

Type :

bool

use_eevee_debug

Expose EEVEE debugging options aimed at developers (default False)

Type :

bool

use_extended_asset_browser

Let the Asset Browser editor and operators handle ordinary data-blocks as assets, not poses alone (default False)

Type :

bool

use_extensions_debug

Additional debugging output & developer tooling for extensions (default False)

Type :

bool

use_geometry_bundle

Allow custom bundles to be stored inside a geometry in Geometry Nodes (default False)

Type :

bool

use_geometry_nodes_lists

Turn on the new list types and their nodes (default False)

Type :

bool

use_new_curves_tools

Turn on extra features for the new curves data block (default False)

Type :

bool

use_paint_debug

Expose paint & sculpt debugging options aimed at developers (default False)

Type :

bool

use_recompute_usercount_on_save_debug

Recount every ID's users before writing a blend-file. Helps sidestep faulty user-count handling that can otherwise discard data when blocks are wrongly seen as unused (default False)

Type :

bool

use_sculpt_texture_paint

Allow texture painting while in Sculpt Mode (default False)

Type :

bool

use_shader_node_previews

Turn on previews inside the shader node editor (default False)

Type :

bool

use_undo_legacy

Fall back to the old undo system (slower than the current default but occasionally steadier) (default False)

Type :

bool

use_viewport_debug

Within the overlays pop-over, surface developer-facing debugging options for the viewport (default False)

Type :

bool

write_legacy_blend_file_format

Save in the format used before Blender 5.0. It is more limited but can interoperate better with tools that have not adopted the new format (default False)

Type :

bool

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

| Preferences.experimental | |

## `RENDER_UL`_renderviews(UIList)

### `RENDER_UL`_renderviews(UIList) 

base classes — bpy_struct, UIList

class bpy.types. `RENDER_UL`_renderviews ( UIList ) 

draw_item ( _context , layout , _data , item , icon , _active_data , _active_propname , index ) 

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
