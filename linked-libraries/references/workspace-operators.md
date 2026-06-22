# Workspace Operators, Assetbrowser Ul Metadata Tags Uilist, Blenddatalibraries Bpy Prop Collection, Blendimportcontext Bpy Struct ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Workspace Operators; `ASSETBROWSER_UL`_metadata_tags(UIList); BlendDataLibraries(bpy_prop_collection); BlendImportContext(bpy_struct); BlendImportContextItem(bpy_struct); BoneCollection(bpy_struct); `CLIP_UL`_tracking_objects(UIList).

## Workspace Operators

### Workspace Operators 

bpy.ops.workspace. add ( ) 

Make a new workplace by replicating the present one or including one from the client settings

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.workspace. append_activate ( * , idname = '' , filepath = '' ) 

Include a workplace and mark it as the lively one in the present window

Parameters :

- idname ( str ) – Identifier, Name of the workplace to include and mark active (optional, never None)

- filepath ( str ) – Filepath, Route to the repository (optional, never None, blend comparative // tag upheld)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.workspace. delete ( ) 

Eliminate the lively workplace

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.workspace. delete_all_others ( ) 

Eliminate every workplace except this one

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.workspace. duplicate ( ) 

Make a fresh workplace

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.workspace. reorder_to_back ( ) 

Reposition workplace to be final in the set

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.workspace. reorder_to_front ( ) 

Reposition workplace to be opening in the set

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.workspace. scene_pin_toggle ( ) 

Preserve the final selected area for the present workplace and switch to it when this workplace is turned on next

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## `ASSETBROWSER_UL`_metadata_tags(UIList)

UI list showing metadata tags.

base classes — bpy_struct, UIList

class bpy.types. `ASSETBROWSER_UL`_metadata_tags ( UIList )

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

## BlendDataLibraries(bpy_prop_collection)

### BlendDataLibraries(bpy_prop_collection)
base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataLibraries ( bpy_prop_collection )
A collection of libraries.

tag ( value )
Tags the libraries.
Parameters: value ( bool ) – Value

remove ( library , * , do_unlink = True , do_id_user = True , do_ui_user = True )
Removes a library from the current blendfile.
Parameters:
- library (Library) – Library to remove (never None)
- do_unlink ( bool ) – Unlink all usages of this library before deleting it (optional)
- do_id_user ( bool ) – Decrement user counter of all data-blocks used by this library (optional)
- do_ui_user ( bool ) – Make sure interface does not reference this library (optional)

classmethod bl_rna_get_subclass ( id , default = None , / )
Parameters:
- id ( str ) – The RNA type identifier.
- default (bpy.types.Struct | None) – The value to return when not found.
Returns: The RNA type or default when not found.
Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )
Parameters:
- id ( str ) – The RNA type identifier.
- default ( type | None ) – The value to return when not found.
Returns: The class or default when not found.
Return type: type

load ( filepath , * , link = False , pack = False , relative = False , set_fake = False , recursive = False , reuse_local_id = False , assets_only = False , clear_asset_data = False , create_liboverrides = False , reuse_liboverrides = False , create_liboverrides_runtime = False )
Returns a context manager that, on entering, exposes 2 library objects; each object has attributes matching bpy.data which are lists of strings to be linked.
Parameters:
- filepath ( str | bytes ) – The path to a blend file.
- link ( bool ) – When False reference to the original file is lost.
- pack ( bool ) – If True, and link is also True, pack linked data-blocks into the current blend-file.
- relative ( bool ) – When True the path is stored relative to the open blend file.
- set_fake ( bool ) – If True, set fake user on appended IDs.
- recursive ( bool ) – If True, also make indirect dependencies of appended libraries local.
- reuse_local_id ( bool ) – If True, try to re-use a previously appended matching ID on new append.
- assets_only ( bool ) – If True, only list data-blocks marked as assets.
- clear_asset_data ( bool ) – If True, clear the asset data on append (it is always kept for linked data).
- create_liboverrides ( bool ) – If True and link is True, liboverrides will be created for linked data.
- reuse_liboverrides ( bool ) – If True and create_liboverride is True, search for an existing liboverride first.
- create_liboverrides_runtime ( bool ) – If True and create_liboverride is True, create (or search for an existing) runtime liboverride.
```python
import bpy

filepath = "//link_library.blend"

# Load a single scene we know the name of.
with bpy.data.libraries.load(filepath) as (data_src, data_dst):
    data_dst.scenes = ["Scene"]

# Load all meshes.
with bpy.data.libraries.load(filepath) as (data_src, data_dst):
    data_dst.meshes = data_src.meshes

# Link all objects starting with "A".
with bpy.data.libraries.load(filepath, link=True) as (data_src, data_dst):
    data_dst.objects = [name for name in data_src.objects if name.startswith("A")]

# Append everything.
with bpy.data.libraries.load(filepath) as (data_src, data_dst):
    for attr in dir(data_dst):
        setattr(data_dst, attr, getattr(data_src, attr))

# The loaded objects can be accessed from `data_dst` outside of the context
# since loading the data replaces the strings for the data-blocks or None
# if the data-block could not be loaded.
with bpy.data.libraries.load(filepath) as (data_src, data_dst):
    data_dst.meshes = data_src.meshes
# Now operate directly on the loaded data.
for mesh in data_dst.meshes:
    if mesh is not None:
        print(mesh.name)
```

write ( filepath , datablocks , * , path_remap = 'NONE' , fake_user = False , compress = False )
Writes data-blocks into a blend file.
Note: indirectly referenced data-blocks will be expanded and written too.
Parameters:
- filepath ( str | bytes ) – The path to write the blend-file.
- datablocks (set[bpy.types.ID]) – set of data-blocks.
- path_remap ( str ) – Optionally remap paths when writing the file:
- NONE No path manipulation (default).
- RELATIVE Remap paths that are already relative to the new location.
- `RELATIVE_ALL` Remap all paths to be relative to the new location.
- ABSOLUTE Make all paths absolute on writing.
- fake_user ( bool ) – When True, data-blocks will be written with fake-user flag enabled.
- compress ( bool ) – When True, write a compressed blend file.
```python
import bpy

filepath = "//new_library.blend"

# Write selected objects and their data to a blend file.
data_blocks = set(bpy.context.selected_objects)
bpy.data.libraries.write(filepath, data_blocks)

# Write all meshes starting with a capital letter and
# set them with fake-user enabled so they aren't lost on re-saving.
data_blocks = {mesh for mesh in bpy.data.meshes if mesh.name[:1].isupper()}
bpy.data.libraries.write(filepath, data_blocks, fake_user=True)

# Write all materials, textures and node groups to a library.
data_blocks = {*bpy.data.materials, *bpy.data.textures, *bpy.data.node_groups}
bpy.data.libraries.write(filepath, data_blocks)
```

### Inherited Properties
| bpy_struct.id_data | |

### Inherited Functions
| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References
| BlendData.libraries | |

## BlendImportContext(bpy_struct)

### BlendImportContext(bpy_struct)

base class — bpy_struct

class bpy.types.BlendImportContext(bpy_struct)

Carries contextual state for an operation involving a blendfile's libraries or linked data. At present it is surfaced only as read-only information for the handlers that run before and after a blend import.

import_items

(default None, readonly)

Type:
BlendImportContextItems[BlendImportContextItem]

options

Flags governing how this blendfile import is carried out (default set(), readonly)

- LINK
Only link data, instead of appending it.

- `MAKE_PATHS_RELATIVE`
Make paths of used library blendfiles relative to current blendfile.

- `USE_PLACEHOLDERS`
Generate a placeholder (empty ID) if not found in any library files.

- `FORCE_INDIRECT`
Force loaded ID to be tagged as indirectly linked (used in reload context only).

- `APPEND_SET_FAKEUSER`
Set fake user on appended IDs.

- `APPEND_RECURSIVE`
Append (make local) also indirect dependencies of appended IDs coming from other libraries. NOTE: All IDs (including indirectly linked ones) coming from the same initial library are always made local.

- `APPEND_LOCAL_ID_REUSE`
Try to re-use previously appended matching IDs when appending them again, instead of creating local duplicates.

- `APPEND_ASSET_DATA_CLEAR`
Clear the asset data on append (it is always kept for linked data).

- `SELECT_OBJECTS`
Automatically select imported objects.

- `USE_ACTIVE_COLLECTION`
Use the active Collection of the current View Layer to instantiate imported collections and objects.

- `OBDATA_INSTANCE`
Instantiate object data IDs (i.e. create objects for them if needed).

- `COLLECTION_INSTANCE`
Instantiate collections as empties, instead of linking them into the current view layer.

Type:
set[Literal['LINK', '`MAKE_PATHS_RELATIVE`', '`USE_PLACEHOLDERS`', '`FORCE_INDIRECT`', '`APPEND_SET_FAKEUSER`', '`APPEND_RECURSIVE`', '`APPEND_LOCAL_ID_REUSE`', '`APPEND_ASSET_DATA_CLEAR`', '`SELECT_OBJECTS`', '`USE_ACTIVE_COLLECTION`', '`OBDATA_INSTANCE`', '`COLLECTION_INSTANCE`']]

process_stage

Which phase the import has reached at present (default 'INIT', readonly)

- INIT
Blendfile import context has been initialized and filled with a list of items to import, no data has been linked or appended yet.

- DONE
All data has been imported and is available in the list of "import_items".

Type:
Literal['INIT', 'DONE']

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – The RNA type identifier.
- default (bpy.types.Struct | None) – The value to return when not found.

Returns:
The RNA type or default when not found.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – The RNA type identifier.
- default (type | None) – The value to return when not found.

Returns:
The class or default when not found.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

## BlendImportContextItem(bpy_struct)

### BlendImportContextItem(bpy_struct)

base class — bpy_struct

class bpy.types.BlendImportContextItem(bpy_struct)

Represents one data-block entry held inside a BlendImportContext. For now it is available solely as read-only information passed to the pre- and post-linking handlers.

append_action

Records the way the append operation treated this entry. Populated only when the data was in fact appended (default 'UNSET', readonly)

- UNSET
Not yet defined.

- `KEEP_LINKED`
ID has been kept linked.

- `REUSE_LOCAL`
An existing matching local ID has been re-used.

- `MAKE_LOCAL`
The newly linked ID has been made local.

- `COPY_LOCAL`
The linked ID had other unrelated usages, so it has been duplicated into a local copy.

Type:
Literal['UNSET', '`KEEP_LINKED`', '`REUSE_LOCAL`', '`MAKE_LOCAL`', '`COPY_LOCAL`']

id

The ID that was imported. Stays None until linking or appending occurs. When appended, it can be identical to reusable_local_id (readonly)

Type:
ID

id_type

Which ID category this entry belongs to (default 'ACTION', readonly)

Type:
Literal[Id Type Items]

import_info

Assorted status details describing an entry once its import has finished (default set(), readonly)

- `INDIRECT_USAGE`
That item was added for an indirectly imported ID, as a dependency of another data-block.

- `LIBOVERRIDE_DEPENDENCY`
That item represents an ID also used as liboverride dependency (either directly, as a liboverride reference, or indirectly, as data used by a liboverride reference). It should never be directly made local. Mutually exclusive with `LIBOVERRIDE_DEPENDENCY`.

- `LIBOVERRIDE_DEPENDENCY_ONLY`
That item represents an ID only used as liboverride dependency (either directly or indirectly, see `LIBOVERRIDE_DEPENDENCY` for precisions). It should not be considered during the 'make local' (append) process, and remain purely linked data. Mutually exclusive with `LIBOVERRIDE_DEPENDENCY`.

Type:
set[Literal['`INDIRECT_USAGE`', '`LIBOVERRIDE_DEPENDENCY`', '`LIBOVERRIDE_DEPENDENCY_ONLY`']]

library_override_id

The library override generated for the linked ID. Remains None until one is produced (readonly)

Type:
ID

name

ID name of the item (default "", readonly, never None)

Type:
str

reusable_local_id

A pre-existing local ID eligible for reuse in the append-and-reuse scenario. Stays None until such a match is located (readonly)

Type:
ID

source_libraries

The ordered set of libraries searched for this ID; it is pulled from the first file in the sequence that holds it (default None, readonly)

Type:
BlendImportContextLibraries[BlendImportContextLibrary]

source_library

The Library ID identifying the blendfile the ID came from. Remains None until the ID has been linked or appended (readonly)

Type:
Library

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – The RNA type identifier.
- default (bpy.types.Struct | None) – The value to return when not found.

Returns:
The RNA type or default when not found.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – The RNA type identifier.
- default (type | None) – The value to return when not found.

Returns:
The class or default when not found.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendImportContext.import_items | |

## BoneCollection(bpy_struct)

### BoneCollection(bpy_struct)

base class — bpy_struct

class bpy.types.BoneCollection(bpy_struct)

A grouping of bones within an Armature data-block

bones

Bones that belong to this collection. While the armature is in edit mode this list always comes back empty, because collection memberships are only reconciled once edit mode is exited. (default None, readonly)

Type:
bpy_prop_collection[Bone]

child_number

Position of this collection in its parent's child list. Locating it requires scanning every bone collection, so use it sparingly. (in [-inf, inf], default 0)

Type:
int

children

(default None, readonly)

Type:
bpy_prop_collection[BoneCollection]

index

Position of this collection within the armature.collections_all array. Locating it requires scanning every bone collection, so use it sparingly. (in [-inf, inf], default 0, readonly)

Type:
int

is_editable

The collection belongs to a local Armature, or entered the current blend file through a library override (default False, readonly)

Type:
bool

is_expanded

Shows this collection in an unfolded state within the bone collections tree view (default False)

Type:
bool

is_local_override

The collection entered the current blend file through a library override (default False, readonly)

Type:
bool

is_solo

Display this bone collection alone, together with any others also flagged as 'solo' (default False)

Type:
bool

is_visible

The collection's bones become viewable while in pose or object mode (default False)

Type:
bool

is_visible_ancestors

True when every ancestor of this bone collection is flagged visible; root collections are always True (default False, readonly)

Type:
bool

is_visible_effectively

Indicates real viewport visibility for this bone collection. It is True when both this collection and all of its ancestors are visible, or when it is flagged as 'solo'. (default False, readonly)

Type:
bool

name

Unique within the Armature (default "", never None)

Type:
str

parent

Parent bone collection. Reading this requires scanning every bone collection to locate the parent.

Type:
BoneCollection

bones_recursive

A set of all bones assigned to this bone collection and its child collections.

(readonly)

bl_system_properties_get ( * , do_create = False )

DEBUG ONLY. Internal access to runtime-defined RNA data storage, intended solely for testing and debugging purposes. Do not access it in regular scripting work, and in particular, do not assume that it contains writable data

Parameters:
do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)

Returns:
The system properties root container, or None if there are no system properties stored in this data yet, and its creation was not requested

Return type:
PropertyGroup

assign ( bone )

Add the supplied bone to this collection

Parameters:
bone (AnyType) – Bone, PoseBone, or EditBone to assign to this collection

Returns:
Assigned, Whether the bone was actually assigned; will be false if the bone was already member of the collection

Return type:
bool

unassign ( bone )

Take the supplied bone out of this collection

Parameters:
bone (AnyType) – Bone, PoseBone, or EditBone to remove from this collection

Returns:
Unassigned, Whether the bone was actually removed; will be false if the bone was not a member of the collection to begin with

Return type:
bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters:
- id (str) – The RNA type identifier.
- default (bpy.types.Struct | None) – The value to return when not found.

Returns:
The RNA type or default when not found.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters:
- id (str) – The RNA type identifier.
- default (type | None) – The value to return when not found.

Returns:
The class or default when not found.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Armature.collections Armature.collections_all Bone.collections BoneCollection.children BoneCollection.parent | BoneCollections.active BoneCollections.new BoneCollections.new BoneCollections.remove EditBone.collections |

## `CLIP_UL`_tracking_objects(UIList)

### `CLIP_UL`_tracking_objects(UIList)

base classes — bpy_struct, UIList

class bpy.types. `CLIP_UL`_tracking_objects ( UIList )

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
