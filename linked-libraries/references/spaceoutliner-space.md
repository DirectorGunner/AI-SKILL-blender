# Spaceoutliner Space, Stripelement Bpy Struct, Stripelements Bpy Prop Collection, Texture Ul Texpaintslots Uilist ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: SpaceOutliner(Space); StripElement(bpy_struct); StripElements(bpy_prop_collection); `TEXTURE_UL`_texpaintslots(UIList); `TEXTURE_UL`_texslots(UIList); `UI_UL`_list(UIList).

## SpaceOutliner(Space)

### SpaceOutliner(Space)

base classes — bpy_struct, Space

class bpy.types. SpaceOutliner ( Space )

The space data for the Outliner

display_mode

Which kind of information is shown (default 'SCENES' )

- SCENES
Scenes – Display scenes and their view layers, collections and objects.

- `VIEW_LAYER`
View Layer – Display collections and objects in the view layer.

- SEQUENCE
Video Sequencer – Display data belonging to the Video Sequencer.

- LIBRARIES
Blender File – Display data of current file and linked libraries.

- `DATA_API`
Data API – Display low level Blender data and its properties.

- `LIBRARY_OVERRIDES`
Library Overrides – Display data-blocks with library overrides and list their overridden properties.

- `ORPHAN_DATA`
Unused Data – Display data that is unused and/or will be lost when the file is reloaded.

Type :

Literal[‘SCENES’, ‘`VIEW_LAYER`’, ‘SEQUENCE’, ‘LIBRARIES’, ‘`DATA_API`’, ‘`LIBRARY_OVERRIDES`’, ‘`ORPHAN_DATA`’]

filter_id_type

Which data-block type to show (default 'ACTION' )

Type :

Literal[Id Type Items]

filter_invert

Flip the object state filter (default False)

Type :

bool

filter_state

(default 'ALL' )

- ALL
All – Show all objects in the view layer.

- VISIBLE
Visible – Show visible objects.

- SELECTED
Selected – Show selected objects.

- ACTIVE
Active – Show only the active object.

- SELECTABLE
Selectable – Show only selectable objects.

Type :

Literal[‘ALL’, ‘VISIBLE’, ‘SELECTED’, ‘ACTIVE’, ‘SELECTABLE’]

filter_text

The string used for live search filtering (default “”, never None)

Type :

str

lib_override_view_mode

Pick how library override data is visualized (default 'PROPERTIES' )

- PROPERTIES
Properties – Display all local override data-blocks with their overridden properties and buttons to edit them.

- HIERARCHIES
Hierarchies – Display library override relationships.

Type :

Literal[‘PROPERTIES’, ‘HIERARCHIES’]

show_mode_column

Draw the mode column for toggling and activating modes (default False)

Type :

bool

show_restrict_column_enable

Exclude from view layer (default False)

Type :

bool

show_restrict_column_hide

Temporarily hide in viewport (default False)

Type :

bool

show_restrict_column_holdout

Holdout (default False)

Type :

bool

show_restrict_column_indirect_only

Indirect only (default False)

Type :

bool

show_restrict_column_render

Globally disable in renders (default False)

Type :

bool

show_restrict_column_select

Selectable (default False)

Type :

bool

show_restrict_column_viewport

Globally disable in viewports (default False)

Type :

bool

use_filter_case_sensitive

Match the search string with case sensitivity only (default False)

Type :

bool

use_filter_children

Show children (default True)

Type :

bool

use_filter_collection

Show collections (default True)

Type :

bool

use_filter_complete

Match the search string only when it is complete (default False)

Type :

bool

use_filter_id_type

Limit display to data-blocks of a single type (default False)

Type :

bool

use_filter_lib_override_system

For libraries that have overrides, also show the overridden values that get set or driven automatically (so that, for instance, users of an overridden data-block reference the override rather than the original linked data) (default False)

Type :

bool

use_filter_object

Show objects (default True)

Type :

bool

use_filter_object_armature

Show armature objects (default True)

Type :

bool

use_filter_object_camera

Show camera objects (default True)

Type :

bool

use_filter_object_content

Show what lies inside the object elements (default True)

Type :

bool

use_filter_object_empty

Show empty objects (default True)

Type :

bool

use_filter_object_grease_pencil

Show Grease Pencil objects (default True)

Type :

bool

use_filter_object_light

Show light objects (default True)

Type :

bool

use_filter_object_mesh

Show mesh objects (default True)

Type :

bool

use_filter_object_others

Show curves, lattices, light probes, fonts, … (default True)

Type :

bool

use_filter_view_layers

Show every view layer (default True)

Type :

bool

use_sort_alpha

(default True)

Type :

bool

use_sync_select

Keep the outliner selection in sync with the other editors (default False)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

The matching RNA type, or the default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

The matching class, or the default if none is found.

Return type :

type

classmethod draw_handler_add ( callback , args , region_type , draw_type )

Register a fresh draw handler on this kind of space.
Whenever the named region of that space type is redrawn, the handler runs.
Note: for the moment, every argument here is positional-only.

Parameters :

- callback ( Callable [ ... , Any ] ) – A function invoked at region draw time.
It is handed the arguments listed below, and any value it hands back gets thrown away.

- args ( tuple [ Any , ... ] ) – Arguments handed to the callback.

- region_type ( str ) – The region type the callback draws in; usually WINDOW . (bpy.types.Region.type)

- draw_type ( str ) – Usually `POST_PIXEL` for 2D drawing and `POST_VIEW` for 3D drawing. In some cases `PRE_VIEW` can be used. BACKDROP can be used for backdrops in the node editor.

Returns :

A handler reference you can remove afterward.

Return type :

object

classmethod draw_handler_remove ( handler , region_type )

Detach a draw handler that had been registered earlier.

Parameters :

- handler ( object ) – The draw handler to take off.

- region_type ( str ) – The region type that handler was attached to.

### Inherited Properties

| bpy_struct.id_data Space.type | Space.show_locked_time Space.show_region_header |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Space.bl_rna_get_subclass Space.bl_rna_get_subclass_py Space.draw_handler_add Space.draw_handler_remove |

## StripElement(bpy_struct)

### StripElement(bpy_struct)

base class — bpy_struct

class bpy.types. StripElement ( bpy_struct )

The per-frame data of a single sequence strip.

filename

Name of the source file (default “”, never None)

Type :

str

orig_fps

Original frames per second (in [-inf, inf], default 0.0, readonly)

Type :

float

orig_height

Original image height (in [-inf, inf], default 0, readonly)

Type :

int

orig_width

Original image width (in [-inf, inf], default 0, readonly)

Type :

int

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

| ImageStrip.elements MovieStrip.elements | Strip.strip_elem_from_frame StripElements.append |

## StripElements(bpy_prop_collection)

### StripElements(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. StripElements ( bpy_prop_collection )

A group of StripElement entries.

append ( filename )

Push an image from ImageStrip.directory

Parameters :

filename ( str ) – Filepath to image (never None)

Returns :

New StripElement

Return type :

StripElement

pop ( index )

Pop an image off the collection

Parameters :

index ( int ) – Index of image to remove (in [-inf, inf])

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

| ImageStrip.elements | |

## `TEXTURE_UL`_texpaintslots(UIList)

### `TEXTURE_UL`_texpaintslots(UIList)

base classes — bpy_struct, UIList

class bpy.types. `TEXTURE_UL`_texpaintslots ( UIList )

draw_item ( _context , layout , _data , item , _icon , _active_data , _active_propname , _index )

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

## `TEXTURE_UL`_texslots(UIList)

### `TEXTURE_UL`_texslots(UIList)

base classes — bpy_struct, UIList

class bpy.types. `TEXTURE_UL`_texslots ( UIList )

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

## `UI_UL`_list(UIList)

### `UI_UL`_list(UIList) 

base classes — bpy_struct, UIList

class bpy.types. `UI_UL`_list ( UIList ) 

static filter_items_by_name ( pattern , bitflag , items , propname = 'name' , flags = None , reverse = False ) 

Set `FILTER_ITEM` for items which name matches filter_name one (case-insensitive).
pattern is the filtering pattern.
propname is the name of the string property to use for filtering.
flags must be a list of integers the same length as items, or None!
return a list of flags (based on given flags if not None),
or an empty list if no flags were given and no filtering has been done.

classmethod sort_items_by_name ( items , propname = 'name' ) 

Re-order items using their names (case-insensitive).
propname is the name of the string property to use for sorting.
return a list mapping org_idx -> new_idx,
or an empty list if no sorting has been done.

static sort_items_helper ( sort_data , key , reverse = False ) 

Common sorting utility. Returns a neworder list mapping org_idx -> new_idx.
sort_data must be an (unordered) list of tuples [(org_idx, …), (org_idx, …), …].
key must be the same kind of callable you would use for sorted() builtin function.
reverse will reverse the sorting!

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
