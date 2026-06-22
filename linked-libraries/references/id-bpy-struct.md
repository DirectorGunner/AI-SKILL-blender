# Id Bpy Struct, Idmaterials Bpy Prop Collection, Idoverridelibrary Bpy Struct, Image Ul Render Slots Uilist ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ID(bpy_struct); IDMaterials(bpy_prop_collection); IDOverrideLibrary(bpy_struct); `IMAGE_UL`_render_slots(UIList); `IMAGE_UL`_udim_tiles(UIList).

## ID(bpy_struct)

### ID(bpy_struct)

base class — bpy_struct

subclasses —
Action, Annotation, Armature, Brush, CacheFile, Camera, Collection, Curve, Curves, FreestyleLineStyle, GreasePencil, Image, Key, Lattice, Library, Light, LightProbe, Mask, Material, Mesh, MetaBall, MovieClip, NodeTree, Object, PaintCurve, Palette, ParticleSettings, PointCloud, Scene, Screen, Sound, Speaker, Text, Texture, VectorFont, Volume, WindowManager, WorkSpace, World

class bpy.types. ID ( bpy_struct )

The shared base for data-blocks: gives each a unique name, cross-library linking, and reference counting.

asset_data

Additional data for an asset data-block

Type :

AssetMetaData

id_type

Type identifier of this data-block (default 'ACTION' , readonly)

Type :

Literal[Id Type Items]

is_editable

True when the user interface allows editing this data-block; linked ones stay locked unless brought in as editable assets. (default False, readonly)

Type :

bool

is_embedded_data

Rather than standing on its own, this data-block lives inside another ID as sub-data (root node trees or master collections being the usual cases). (default False, readonly)

Type :

bool

is_evaluated

Flags whether the ID is a runtime-only, evaluated copy as opposed to genuine data read from the .blend file. (default False, readonly)

Type :

bool

is_library_indirect

True when this ID block came in through an indirect link. (default False, readonly)

Type :

bool

is_linked_packed

True when the data-block is both linked and packed inside the .blend file. (default False, readonly)

Type :

bool

is_missing

Marks a stand-in left behind for linked data that has gone missing (i.e. [an override of] a link no longer locatable). (default False, readonly)

Type :

bool

is_runtime_data

Indicates the block holds runtime data that the .blend file will not store. Since evaluated IDs always count as runtime, only blocks in the Main database let you toggle this. (default False)

Type :

bool

library

The library file from which this data-block was linked (readonly)

Type :

Library

library_weak_reference

A loose pointer to a data-block in a separate library .blend, letting already-appended data be reused rather than appended afresh (readonly)

Type :

LibraryWeakReference

name

Per-type, per-library unique name for the data-block ID (default "", never None)

Type :

str

name_full

The data-block's unique ID name with its library name folded in where one exists (default "", readonly, never None)

Type :

str

original

The real .blend-file data-block (Main database) behind this evaluated copy (readonly)

Type :

ID

override_library

Library override data (readonly)

Type :

IDOverrideLibrary

preview

This data-block's icon and preview image, which is always None where the data type has no preview support (readonly)

Type :

ImagePreview

session_uid

An identifier unique for the whole session that survives renames and internal reallocation and stays put on file reload (in [-inf, inf], default 0, readonly)

Type :

int

tag

A scratch flag tools may set for whatever they need; its starting value is not defined (default False)

Type :

bool

use_extra_user

Reports whether an extra user has been set, chiefly for internal and debugging use (default False)

Type :

bool

use_fake_user

Save this data-block even if it has no users (default False)

Type :

bool

users

Number of times this data-block is referenced (in [0, inf], default 0, readonly)

Type :

int

bl_system_properties_get ( * , do_create = False )

DEBUG ONLY. A back door into runtime-defined RNA storage meant purely for tests and debugging. Steer clear of it in normal scripts, and never count on the contents being writable.

Parameters :

do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)

Returns :

The root container for system properties, or None when this data holds none yet and you did not ask for them to be created

Return type :

PropertyGroup

rename ( name , * , mode = 'NEVER' )

Renames with smarter behaviour for the case where the chosen name clashes with another ID.

Parameters :

- name ( str ) – New name to rename the ID to, if empty will re-use the current ID name (never None)

- mode ( Literal [ 'NEVER' , 'ALWAYS' , '`SAME_ROOT`' ] ) – How to handle name collision, in case the requested new name is already used by another ID of the same type (optional)

- NEVER
Never Rename – Leave any conflicting ID untouched; instead a numeric suffix is tacked onto the ID being renamed.

- ALWAYS
Always Rename – Rename whichever existing ID conflicts so that the ID being renamed gets exactly the name asked for.

- `SAME_ROOT`
Rename If Same Root – Only displace a conflicting ID when its name root (the part before the numeric suffix) matches the current name of the ID being renamed.

Returns :

The outcome of the rename attempt

- UNCHANGED
Unchanged – No rename happened, for instance because the ID already carries the requested name.

- `UNCHANGED_COLLISION`
Unchanged Due to Collision – No rename happened: the request would have clashed with another ID, and the auto-adjusted name matched the current name anyway.

- `RENAMED_NO_COLLISION`
Renamed Without Collision – The requested name was applied and no collision arose.

- `RENAMED_COLLISION_ADJUSTED`
Renamed With Collision – The name was applied after being tweaked to sidestep a collision.

- `RENAMED_COLLISION_FORCED`
Renamed Enforced With Collision – The requested name was forced through, with another ID renamed to make room.

Return type :

Literal['UNCHANGED', '`UNCHANGED_COLLISION`', '`RENAMED_NO_COLLISION`', '`RENAMED_COLLISION_ADJUSTED`', '`RENAMED_COLLISION_FORCED`']

evaluated_get ( depsgraph )

Fetch the matching evaluated ID out of the supplied dependency graph. This does not force the graph to be fully evaluated; you simply get back whatever the previous evaluation produced.

Parameters :

depsgraph (Depsgraph) – Dependency graph to perform lookup in (never None)

Returns :

New copy of the ID

Return type :

ID

copy ( )

Duplicate this data-block, where the type permits. The copy lands in the Blend-File Data (Main database), and every pointer to other data-blocks is kept within that same Blend-File Data.

Returns :

New copy of the ID

Return type :

ID

asset_mark ( )

Make the data-block reusable via the Asset Browser, backed by editable metadata such as previews, descriptions, and tags.

asset_clear ( )

Strip all asset metadata and return the asset back to being an ordinary data-block.

asset_generate_preview ( )

Build a preview image, possibly queued onto a background thread.

override_create ( * , remap_local_usages = False )

Produce a local override copy of this linked data-block, for the types that allow it.

Parameters :

remap_local_usages ( bool ) – Whether local usages of the linked ID should be remapped to the new library override of it (optional)

Returns :

New overridden local copy of the ID

Return type :

ID

override_hierarchy_create ( scene , view_layer , * , reference = None , do_fully_editable = False )

Build a local override of this linked data-block, pulling in most of its dependencies too when the block is a Collection or Object.

Parameters :

- scene (Scene) – In which scene the new overrides should be instantiated (never None)

- view_layer (ViewLayer) – In which view layer the new overrides should be instantiated (never None)

- reference (ID) – Another ID (usually an Object or Collection) used as a hint to decide where to instantiate the new overrides (optional)

- do_fully_editable ( bool ) – Make all library overrides generated by this call fully editable by the user (none will be 'system overrides') (optional)

Returns :

New overridden local copy of the root ID

Return type :

ID

user_clear ( )

Drop a data-block's user count to zero so it goes unsaved, and the data is discarded at the next reload.

This function is for advanced use only, misuse can crash Blender since the user
count is used to prevent data being removed when it is used.

`text
### This example shows what _not_ to do, and will crash Blender.
import bpy

### Object which is in the scene.
obj = bpy.data.objects["Cube"]

### Without this, removal would raise an error.
obj.user_clear()

### Runs without an exception but will crash on redraw.
bpy.data.objects.remove(obj)
`

user_remap ( new_id )

Point every reference to this ID in the .blend file at the supplied replacement instead.

Parameters :

new_id (ID) – New ID to use (never None)

make_local ( * , clear_proxy = True , clear_liboverride = False , clear_asset_data = True )

Make this data-block local and hand it back; when the data also has indirect users the returned block may be a fresh copy.

Parameters :

- clear_proxy ( bool ) – Deprecated, has no effect (optional)

- clear_liboverride ( bool ) – Remove potential library override data from the newly made local data (optional)

- clear_asset_data ( bool ) – Remove potential asset metadata so the newly local data-block is not treated as asset data-block and won't show up in asset libraries (optional)

Returns :

This ID, or the new ID if it was copied

Return type :

ID

user_of_id ( id )

Count how many times this data-block points at the given ID.

Parameters :

id (ID) – ID to count usages (never None)

Returns :

Number of usages/references of given id by current data-block (in [0, inf])

Return type :

int

animation_data_create ( )

Attach animation data to this ID; be aware that some ID types do not allow it.

Returns :

New animation data or None

Return type :

AnimData

animation_data_clear ( )

Strip any animation off this ID.

update_tag ( * , refresh = set() )

Flag the ID so its display data refreshes, for instance when bpy.types.Scene.update runs.

Parameters :

refresh ( set [ Literal [ 'OBJECT' , 'DATA' , 'TIME' ] ] ) – Type of updates to perform (optional)

preview_ensure ( )

Guarantee this ID carries preview data, when its type permits previews.

Returns :

The existing or created preview

Return type :

ImagePreview

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

| bpy.context.annotation_data_owner bpy.context.id bpy.context.selected_ids bpy.context.texture_user Action.fcurve_ensure_for_datablock ActionSlot.users AssetRepresentation.local_id BlendData.pack_linked_ids_hierarchy BlendData.pack_linked_ids_hierarchy BlendDataObjects.new BlendImportContextItem.id BlendImportContextItem.library_override_id BlendImportContextItem.reusable_local_id Depsgraph.id_eval_get Depsgraph.id_eval_get Depsgraph.ids DepsgraphUpdate.id DopeSheet.source DriverTarget.id ID.copy ID.evaluated_get ID.make_local ID.original ID.override_create ID.override_hierarchy_create ID.override_hierarchy_create | ID.user_of_id ID.user_remap IDOverrideLibrary.hierarchy_root IDOverrideLibrary.reference IDOverrideLibraryPropertyOperation.subitem_local_id IDOverrideLibraryPropertyOperation.subitem_reference_id IDOverrideLibraryPropertyOperations.add IDOverrideLibraryPropertyOperations.add IDViewerPathElem.id Key.user KeyingSetPath.id KeyingSetPaths.add MaskParent.id NodeTree.get_from_context NodeTree.get_from_context NodesModifierDataBlock.id Object.data PropertyGroupItem.id SpaceFileBrowser.activate_asset_by_id SpaceNodeEditor.id SpaceNodeEditor.id_from SpaceProperties.pin_id UILayout.template_action UILayout.template_path_builder UILayout.template_preview UILayout.template_preview |

## IDMaterials(bpy_prop_collection)

### IDMaterials(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. IDMaterials ( bpy_prop_collection )

The list of materials attached to a data-block.

append ( material )

Attach one more material to the data-block.

Parameters :

material (Material) – Material to add

pop ( * , index = -1 )

Take a material off the data-block.

Parameters :

index ( int ) – Index of material to remove (in [-32766, 32766], optional)

Returns :

Material to remove

Return type :

Material

clear ( )

Strip every material off the data-block.

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

| Curve.materials Curves.materials GreasePencil.materials Mesh.materials | MetaBall.materials PointCloud.materials Volume.materials |

## IDOverrideLibrary(bpy_struct)

### IDOverrideLibrary(bpy_struct)

base class — bpy_struct

class bpy.types. IDOverrideLibrary ( bpy_struct )

Bundles together everything an overridden linked ID needs.

hierarchy_root

The override ID that sits at the top of the override hierarchy to which this ID belongs (readonly)

Type :

ID

is_in_hierarchy

Tells whether this override belongs to a library hierarchy or stands alone as a self-contained, independent override (default True)

Type :

bool

is_system_override

Tells whether the override is there purely to serve the hierarchy or is genuinely something the user can edit (default False)

Type :

bool

properties

List of overridden properties (default None, readonly)

Type :

IDOverrideLibraryProperties[IDOverrideLibraryProperty]

reference

The linked ID this override treats as its reference (readonly)

Type :

ID

operations_update ( )

Rebuild the override's list of operations from the differences between this override ID and its reference.

reset ( * , do_hierarchy = True , set_system_override = False )

Bring this override back in line with its linked reference ID.

Parameters :

- do_hierarchy ( bool ) – Reset this override's dependencies too so they line up with their own reference linked IDs (optional)

- set_system_override ( bool ) – Demote every user-editable override into a non-editable system override (optional)

destroy ( * , do_hierarchy = True )

Delete this override ID and send everything that referenced it back to the linked reference ID.

Parameters :

do_hierarchy ( bool ) – Delete this override's dependencies too and point their usages back at their reference linked IDs (optional)

resync ( scene , * , view_layer = None , residual_storage = None , do_hierarchy_enforce = False , do_whole_hierarchy = False )

Re-synchronize the data-block and its sub-hierarchy, or the entire hierarchy when asked.

Parameters :

- scene (Scene) – Scene the operation runs in, used for contextual matters such as keeping the active object active and making sure every overridden object stays instantiated (never None)

- view_layer (ViewLayer) – View layer the operation runs in, used like the scene argument; when omitted the scene's collection stands in for it (optional)

- residual_storage (Collection) – Collection that catches objects no longer instantiated in any other collection (a garbage bin, created on demand when none is supplied) (optional)

- do_hierarchy_enforce ( bool ) – Force the dependency hierarchy among data-blocks back into line with the reference linked hierarchy (WARNING: any ID pointers you deliberately overrode get reset to their defaults) (optional)

- do_whole_hierarchy ( bool ) – Resync the entire hierarchy that contains this data-block, not just its own sub-hierarchy (optional)

Returns :

Success, Whether the resync process was successful or not

Return type :

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

| ID.override_library | |

## `IMAGE_UL`_render_slots(UIList)

### `IMAGE_UL`_render_slots(UIList)

base classes — bpy_struct, UIList

class bpy.types. `IMAGE_UL`_render_slots ( UIList )

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

## `IMAGE_UL`_udim_tiles(UIList)

### `IMAGE_UL`_udim_tiles(UIList)

base classes — bpy_struct, UIList

class bpy.types. `IMAGE_UL`_udim_tiles ( UIList )

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
