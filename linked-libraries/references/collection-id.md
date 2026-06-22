# Collection Id, Collectionchildren Bpy Prop Collection, Collectionobjects Bpy Prop Collection, Curves Ul Attributes Uilist ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Collection(ID); CollectionChildren(bpy_prop_collection); CollectionObjects(bpy_prop_collection); `CURVES_UL`_attributes(UIList); `DATA_UL`_bone_collections(UIList); FileAssetSelectParams(FileSelectParams); `FILEBROWSER_UL`_dir(UIList).

## Collection(ID)

### Collection(ID)

base classes — bpy_struct, ID

class bpy.types. Collection ( ID )

A data-block grouping Object data-blocks together

active_exporter_index

Which entry in the exporters list is currently active (in [0, inf], default 0)

Type :

int

all_objects

Every object held by this collection together with those in its nested child collections (default None, readonly)

Type :

bpy_prop_collection[Object]

children

The collections nested one level directly beneath this one (default None, readonly)

Type :

CollectionChildren[Collection]

collection_children

Child collections paired with the settings specific to each parent-child relationship (default None, readonly)

Type :

bpy_prop_collection[CollectionChild]

collection_objects

The collection's objects, each carrying the settings tied to that particular parent collection (default None, readonly)

Type :

bpy_prop_collection[CollectionObject]

color_tag

Tag assigning a color to the collection (default '`COLOR_01`' )

Type :

Literal[Collection Color Items]

exporters

The export handlers set up for this collection (default None, readonly)

Type :

CollectionExports[CollectionExport]

hide_render

Turn the collection off everywhere during rendering (default False)

Type :

bool

hide_select

Block the collection from being selected in the viewport (default False)

Type :

bool

hide_viewport

Turn the collection off across all viewports (default False)

Type :

bool

instance_offset

Shift applied from the origin when the collection is instanced (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

lineart_intersection_mask

Mask value carried by intersections this collection produces (array of 8 items, default (False, False, False, False, False, False, False, False))

Type :

bpy_prop_array[bool]

lineart_intersection_priority

When intersection lines overlap, the object whose priority value is greater wins inclusion (in [0, 255], default 0)

Type :

int

lineart_usage

Sets the role this collection plays during Line Art computation (default 'INCLUDE' )

- INCLUDE
Include – Produce feature lines from this collection.

- `OCCLUSION_ONLY`
Occlusion Only – Let the collection contribute occlusion only.

- EXCLUDE
Exclude – Leave this collection out of Line Art entirely.

- `INTERSECTION_ONLY`
Intersection Only – Emit just intersection lines for this collection.

- `NO_INTERSECTION`
No Intersection – Keep the collection but skip generating intersection lines.

- `FORCE_INTERSECTION`
Force Intersection – Emit intersection lines even against objects that turned intersection off.

Type :

Literal[‘INCLUDE’, ‘`OCCLUSION_ONLY`’, ‘EXCLUDE’, ‘`INTERSECTION_ONLY`’, ‘`NO_INTERSECTION`’, ‘`FORCE_INTERSECTION`’]

lineart_use_intersection_mask

Apply a custom intersection mask to the faces belonging to this collection (default False)

Type :

bool

objects

The objects placed directly inside this collection (default None, readonly)

Type :

CollectionObjects[Object]

use_lineart_intersection_priority

Give this collection its own intersection priority value (default False)

Type :

bool

children_recursive

Every descendant collection beneath this one, returned as a list.

Type :

list[Collection]

Note

Runs in O(n), with n counting every descendant collection beneath this one.

(readonly)

users_dupli_group

The collection-instance objects that make use of this collection

Type :

tuple[Object, …]

Note

Runs in O(len(bpy.data.objects)).

(readonly)

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| BlendData.collections BlendDataCollections.new BlendDataCollections.remove BooleanModifier.collection ClothCollisionSettings.collection Collection.children CollectionChildren.link CollectionChildren.unlink Context.collection DopeSheet.filter_collection DynamicPaintSurface.brush_collection EffectorWeights.collection FluidDomainSettings.effector_group FluidDomainSettings.fluid_group FluidDomainSettings.force_collection FreestyleLineSet.collection | GeometryNodeInputCollection.collection GreasePencilLineartModifier.source_collection IDOverrideLibrary.resync LayerCollection.collection LightProbe.visibility_collection NodeSocketCollection.default_value NodeTreeInterfaceSocketCollection.default_value ObjectLightLinking.blocker_collection ObjectLightLinking.receiver_collection Object.instance_collection ParticleSettings.collision_collection ParticleSettings.instance_collection RigidBodyWorld.collection RigidBodyWorld.constraints Scene.collection SoftBodySettings.collision_collection |

## CollectionChildren(bpy_prop_collection)

### CollectionChildren(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. CollectionChildren ( bpy_prop_collection )

A group holding the child collections

link ( child )

Attach the given collection beneath this collection as a child

Parameters :

child (Collection) – Collection to add (never None)

unlink ( child )

Drop the specified child collection out of its parent collection

Parameters :

child (Collection) – Collection to remove

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

| Collection.children | |

## CollectionObjects(bpy_prop_collection)

### CollectionObjects(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. CollectionObjects ( bpy_prop_collection )

A group holding the objects of a collection

link ( object )

Place the given object into a collection

Parameters :

object (Object) – Object to add (never None)

unlink ( object )

Take this object out of a collection

Parameters :

object (Object) – Object to remove

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

| Collection.objects | |

## `CURVES_UL`_attributes(UIList)

### `CURVES_UL`_attributes(UIList)

base classes — bpy_struct, UIList

class bpy.types. `CURVES_UL`_attributes ( UIList )

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

## `DATA_UL`_bone_collections(UIList)

### `DATA_UL`_bone_collections(UIList)

base classes — bpy_struct, UIList

class bpy.types. `DATA_UL`_bone_collections ( UIList )

draw_item ( _context , layout , armature , bcoll , _icon , _active_data , _active_propname , _index )

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

## FileAssetSelectParams(FileSelectParams)

### FileAssetSelectParams(FileSelectParams)

base classes — bpy_struct, FileSelectParams

class bpy.types. FileAssetSelectParams ( FileSelectParams )

The file-selection settings used while the browser is in Asset Browser mode.

asset_library_reference

(default 'ALL' )

- ALL
All Libraries – Pull in assets from every asset library that is listed.

- LOCAL
Current File – Show only the assets present in this Blender session right now.

- ESSENTIALS
Essentials – Show the core building blocks and utilities shipped with Blender.

- CUSTOM
Custom – Show assets from the asset libraries set up in the Preferences.

Type :

Literal[‘ALL’, ‘LOCAL’, ‘ESSENTIALS’, ‘CUSTOM’]

catalog_id

UUID of the catalog currently displayed in the browser (default “”, never None)

Type :

str

filter_asset_id

Controls which asset types appear or stay hidden while an asset library is being browsed (readonly, never None)

Type :

FileAssetSelectIDFilter

import_method

Decides the way the asset gets imported (default 'LINK' )

- `FOLLOW_PREFS`
Follow Preferences – Adopt the import method set in the Preferences for this asset library rather than overriding it here in the Asset Browser.

- LINK
Link – Bring the asset in as a linked data-block.

- APPEND
Append – Bring the asset in as a copied data-block that keeps no tie to the original asset data-block.

- `APPEND_REUSE`
Append (Reuse Data) – Bring the asset in as a copied data-block while sidestepping duplicate copies of nested, usually heavy data. A material asset's textures, say, or an object asset's mesh, need not be duplicated on each import; the asset's instances share that underlying data instead.

- PACK
Pack – Bring the asset in as a linked data-block and pack it into the current file (so it stays intact even if the library data changes, goes missing, and so on).

Type :

Literal[‘`FOLLOW_PREFS`’, ‘LINK’, ‘APPEND’, ‘`APPEND_REUSE`’, ‘PACK’]

instance_collections_on_append

On append, spawn instances for collections rather than dropping them straight into the scene (default False)

Type :

bool

instance_collections_on_link

On link, spawn instances for collections rather than dropping them straight into the scene (default False)

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

| bpy_struct.id_data FileSelectParams.title FileSelectParams.directory FileSelectParams.filename FileSelectParams.use_library_browsing FileSelectParams.display_type FileSelectParams.recursion_level FileSelectParams.show_details_size FileSelectParams.show_details_datetime FileSelectParams.use_filter FileSelectParams.show_hidden FileSelectParams.sort_method FileSelectParams.use_sort_invert FileSelectParams.use_filter_image FileSelectParams.use_filter_blender FileSelectParams.use_filter_backup | FileSelectParams.use_filter_movie FileSelectParams.use_filter_script FileSelectParams.use_filter_font FileSelectParams.use_filter_sound FileSelectParams.use_filter_text FileSelectParams.use_filter_volume FileSelectParams.use_filter_folder FileSelectParams.use_filter_blendid FileSelectParams.use_filter_asset_only FileSelectParams.filter_id FileSelectParams.filter_glob FileSelectParams.filter_search FileSelectParams.display_size FileSelectParams.display_size_discrete FileSelectParams.list_display_size FileSelectParams.list_column_size |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FileSelectParams.bl_rna_get_subclass FileSelectParams.bl_rna_get_subclass_py |

## `FILEBROWSER_UL`_dir(UIList)

### `FILEBROWSER_UL`_dir(UIList)

base classes — bpy_struct, UIList

class bpy.types. `FILEBROWSER_UL`_dir ( UIList )

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
