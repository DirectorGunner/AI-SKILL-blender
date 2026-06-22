# Nlastrips Bpy Prop Collection, Nlatrack Bpy Struct, Nlatracks Bpy Prop Collection, Node Ast Compositor Assetshelf ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: NlaStrips(bpy_prop_collection); NlaTrack(bpy_struct); NlaTracks(bpy_prop_collection); `NODE_AST`_compositor(AssetShelf); `NODE_FH`_image_node(FileHandler); NodeEnumItem(bpy_struct); NodeIndexSwitchItems(bpy_prop_collection); NodeMenuSwitchItems(bpy_prop_collection); NodesModifierBakeDataBlocks(bpy_prop_collection); NodesModifierDataBlock(bpy_struct); NodesModifierPanel(bpy_struct); ObjectBase(bpy_struct).

## NlaStrips(bpy_prop_collection)

### NlaStrips(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NlaStrips ( bpy_prop_collection )

A set of NLA Strips.

new ( name , start , action )

Append a fresh Action-Clip strip onto the track

Parameters :

- name ( str ) – Name for the NLA Strip (never None)

- start ( int ) – Start Frame, Start frame for this strip (in [-inf, inf])

- action (Action) – Action to assign to this strip (never None)

Returns :

New NLA Strip

Return type :

NlaStrip

remove ( strip )

Delete an NLA Strip

Parameters :

strip (NlaStrip) – NLA Strip to remove (never None)

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

| NlaTrack.strips | |

## NlaTrack(bpy_struct)

### NlaTrack(bpy_struct)

base class — bpy_struct

class bpy.types. NlaTrack ( bpy_struct )

One animation layer that holds Actions pointed at as NLA strips.

active

Whether this NLA Track is the active one (default False, readonly)

Type :

bool

is_override_data

For local override data, indicates whether this NLA track originates from the linked reference or is local to the override (default True, readonly)

Type :

bool

is_solo

Evaluate just this NLA Track on its own (the active Action together with every other NLA Track in the same AnimData block are turned off) (default False)

Type :

bool

lock

Whether this NLA Track is locked (default False)

Type :

bool

mute

Turn off evaluation of this NLA Track (default False)

Type :

bool

name

(default “”, never None)

Type :

str

select

Whether this NLA Track is selected (default False)

Type :

bool

strips

The NLA Strips sitting on this NLA-track (default None, readonly)

Type :

NlaStrips[NlaStrip]

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

| bpy.context.active_nla_track AnimData.nla_tracks NlaTracks.active | NlaTracks.new NlaTracks.new NlaTracks.remove |

## NlaTracks(bpy_prop_collection)

### NlaTracks(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NlaTracks ( bpy_prop_collection )

A set of NLA Tracks.

active

The currently active NLA Track

Type :

NlaTrack

new ( * , prev = None )

Append a fresh NLA Track

Parameters :

prev (NlaTrack) – NLA Track to add the new one after (optional)

Returns :

New NLA Track

Return type :

NlaTrack

remove ( track )

Delete an NLA Track

Parameters :

track (NlaTrack) – NLA Track to remove (never None)

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

| AnimData.nla_tracks | |

## `NODE_AST`_compositor(AssetShelf)

### `NODE_AST`_compositor(AssetShelf)

base classes — bpy_struct, AssetShelf

class bpy.types. `NODE_AST`_compositor ( AssetShelf )

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

| bpy_struct.id_data AssetShelf.bl_idname AssetShelf.bl_space_type AssetShelf.bl_options AssetShelf.bl_activate_operator AssetShelf.bl_drag_operator AssetShelf.bl_default_preview_size AssetShelf.filter_action AssetShelf.filter_armature AssetShelf.filter_brush AssetShelf.filter_camera AssetShelf.filter_cachefile AssetShelf.filter_curve AssetShelf.filter_annotations AssetShelf.filter_grease_pencil AssetShelf.filter_group AssetShelf.filter_curves AssetShelf.filter_image AssetShelf.filter_light AssetShelf.filter_light_probe AssetShelf.filter_linestyle AssetShelf.filter_lattice AssetShelf.filter_material | AssetShelf.filter_metaball AssetShelf.filter_movie_clip AssetShelf.filter_mesh AssetShelf.filter_mask AssetShelf.filter_node_tree AssetShelf.filter_object AssetShelf.filter_particle_settings AssetShelf.filter_palette AssetShelf.filter_paint_curve AssetShelf.filter_pointcloud AssetShelf.filter_scene AssetShelf.filter_speaker AssetShelf.filter_sound AssetShelf.filter_texture AssetShelf.filter_text AssetShelf.filter_font AssetShelf.filter_volume AssetShelf.filter_world AssetShelf.filter_work_space AssetShelf.asset_library_reference AssetShelf.show_names AssetShelf.preview_size AssetShelf.search_filter |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys | bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values AssetShelf.poll AssetShelf.asset_poll AssetShelf.get_active_asset AssetShelf.draw_context_menu AssetShelf.bl_rna_get_subclass AssetShelf.bl_rna_get_subclass_py |

## `NODE_FH`_image_node(FileHandler)

### `NODE_FH`_image_node(FileHandler)

base classes — bpy_struct, FileHandler

class bpy.types. `NODE_FH`_image_node ( FileHandler )

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

| bpy_struct.id_data FileHandler.bl_idname FileHandler.bl_import_operator | FileHandler.bl_export_operator FileHandler.bl_label FileHandler.bl_file_extensions |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FileHandler.poll_drop FileHandler.bl_rna_get_subclass FileHandler.bl_rna_get_subclass_py |

## NodeEnumItem(bpy_struct)

### NodeEnumItem(bpy_struct)

base class — bpy_struct

class bpy.types. NodeEnumItem ( bpy_struct )

description

(default “”, never None)

Type :

str

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

| GeometryNodeMenuSwitch.active_item GeometryNodeMenuSwitch.enum_items | NodeMenuSwitchItems.new NodeMenuSwitchItems.remove |

## NodeIndexSwitchItems(bpy_prop_collection)

### NodeIndexSwitchItems(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodeIndexSwitchItems ( bpy_prop_collection )

A set holding the index_switch items for this node.

new ( )

Append a fresh item after the existing ones.

Returns :

Item, New item

Return type :

IndexSwitchItem

remove ( item )

Delete one item.

Parameters :

item (IndexSwitchItem) – Item, The item to remove (never None)

clear ( )

Delete every item at once.

move ( from_index , to_index )

Shift an item to a different slot.

Parameters :

- from_index ( int ) – From Index, Index of the item to move (in [0, inf])

- to_index ( int ) – To Index, Target index for the item (in [0, inf])

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

| GeometryNodeIndexSwitch.index_switch_items | |

## NodeMenuSwitchItems(bpy_prop_collection)

### NodeMenuSwitchItems(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodeMenuSwitchItems ( bpy_prop_collection )

A set of the entries that form an enum.

new ( name )

Append a brand-new enum entry.

Parameters :

name ( str ) – Name, (never None)

Returns :

Item, New item

Return type :

NodeEnumItem

remove ( item )

Delete one item.

Parameters :

item (NodeEnumItem) – Item, The item to remove (never None)

clear ( )

Delete every item at once.

move ( from_index , to_index )

Shift an item to a different slot.

Parameters :

- from_index ( int ) – From Index, Index of the item to move (in [0, inf])

- to_index ( int ) – To Index, Target index for the item (in [0, inf])

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

| GeometryNodeMenuSwitch.enum_items | |

## NodesModifierBakeDataBlocks(bpy_prop_collection)

### NodesModifierBakeDataBlocks(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. NodesModifierBakeDataBlocks ( bpy_prop_collection )

A set of the data-blocks that the baked data may point to.

active_index

(in [-inf, inf], default 0)

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

| NodesModifierBake.data_blocks | |

## NodesModifierDataBlock(bpy_struct)

### NodesModifierDataBlock(bpy_struct)

base class — bpy_struct

class bpy.types. NodesModifierDataBlock ( bpy_struct )

id

Type :

ID

id_name

Name that is mapped to the referenced data-block (default “”, readonly, never None)

Type :

str

id_type

(default 'ACTION' , readonly)

Type :

Literal[Id Type Items]

lib_name

Applies when the data block lives in an external library rather than the current .blend file (default “”, readonly, never None)

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

| NodesModifierBake.data_blocks | |

## NodesModifierPanel(bpy_struct)

### NodesModifierPanel(bpy_struct)

base class — bpy_struct

class bpy.types. NodesModifierPanel ( bpy_struct )

is_open

Tracks whether the panel is unfolded or collapsed (default False)

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

| NodesModifier.panels | |

## ObjectBase(bpy_struct)

### ObjectBase(bpy_struct) 

base class — bpy_struct

class bpy.types. ObjectBase ( bpy_struct ) 

An instance of an object within a View Layer (not currently exposed in the Python API)

hide_viewport 

Hide momentarily in the viewport (default False)

Type :

bool

object 

The object that this base points to (readonly)

Type :

Object

select 

Selection state of this object base (default False)

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
