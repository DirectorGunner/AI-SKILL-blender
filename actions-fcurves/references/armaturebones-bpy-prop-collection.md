# Armaturebones Bpy Prop Collection, Armatureconstraint Constraint, Armatureconstrainttargets Bpy Prop Collection, Armatureeditbones Bpy Prop Collection ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ArmatureBones(bpy_prop_collection); ArmatureConstraint(Constraint); ArmatureConstraintTargets(bpy_prop_collection); ArmatureEditBones(bpy_prop_collection); AssetLibraryCollection(bpy_prop_collection); AssetLibraryReference(bpy_struct); AssetMetaData(bpy_struct); AssetRepresentation(bpy_struct); AssetTag(bpy_struct); AssetTags(bpy_prop_collection); AssetWeakReference(bpy_struct).

## ArmatureBones(bpy_prop_collection)

Collection of bones in an armature.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. ArmatureBones ( bpy_prop_collection )

Container of skeletal bones.

active

Armature's active bone

Type :

Bone

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

| Armature.bones | |

## ArmatureConstraint(Constraint)

Constraint applying skeletal deformation.

base classes — bpy_struct, Constraint

class bpy.types. ArmatureConstraint ( Constraint )

Replicates transformations from the Armature modifier.

targets

Target Bones (default None, readonly)

Type :

ArmatureConstraintTargets[ConstraintTargetBone]

use_bone_envelopes

Multiply weights by envelope for all bones, instead of acting like Vertex Group based blending. The specified weights are still used, and only the listed bones are considered. (default False)

Type :

bool

use_current_location

Use the current bone location for envelopes and choosing B-Bone segments instead of rest position (default False)

Type :

bool

use_deform_preserve_volume

Deform rotation interpolation with quaternions (default False)

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

| bpy_struct.id_data Constraint.name Constraint.type Constraint.is_override_data Constraint.owner_space Constraint.target_space Constraint.space_object Constraint.space_subtarget | Constraint.mute Constraint.enabled Constraint.show_expanded Constraint.is_valid Constraint.active Constraint.influence Constraint.error_location Constraint.error_rotation |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Constraint.bl_rna_get_subclass Constraint.bl_rna_get_subclass_py |

## ArmatureConstraintTargets(bpy_prop_collection)

Collection of target bones for an armature constraint.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. ArmatureConstraintTargets ( bpy_prop_collection )

Container of influencing bones and their weights.

new ( )

Add a new influencing bone.

Returns :

New target bone

Return type :

ConstraintTargetBone

remove ( target )

Remove an influencing bone.

Parameters :

target (ConstraintTargetBone) – Target to remove (never None)

clear ( )

Remove all targets.

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

| ArmatureConstraint.targets | |

## ArmatureEditBones(bpy_prop_collection)

Collection of bones available for editing.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. ArmatureEditBones ( bpy_prop_collection )

Container of bones in edit mode.

active

Armatures active edit bone

Type :

EditBone

new ( name )

Create a new bone.

Parameters :

name ( str ) – New name for the bone (never None)

Returns :

Newly created edit bone

Return type :

EditBone

remove ( bone )

Delete an existing bone from the armature.

Parameters :

bone (EditBone) – EditBone to remove (never None)

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

| Armature.edit_bones | |

## AssetLibraryCollection(bpy_prop_collection)

Registry of local and remote asset libraries.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. AssetLibraryCollection ( bpy_prop_collection )

Container of stored asset libraries.

classmethod new ( * , name = '' , directory = '' )

Register a new asset library.

Parameters :

- name ( str ) – Name, (optional, never None)

- directory ( str ) – Directory, (optional, never None)

Returns :

Newly added asset library

Return type :

UserAssetLibrary

classmethod remove ( library )

Unregister an asset library.

Parameters :

library (UserAssetLibrary) – (never None)

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

| PreferencesFilePaths.asset_libraries | |

## AssetLibraryReference(bpy_struct)

Handle to a library for asset references.

base class — bpy_struct

class bpy.types. AssetLibraryReference ( bpy_struct )

Weak reference to an asset catalog collection.

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

## AssetMetaData(bpy_struct)

Supplementary information about an asset data block.

base class — bpy_struct

class bpy.types. AssetMetaData ( bpy_struct )

Extended metadata for asset identification and organization.

active_tag

Index of the tag set for editing (in [-32768, 32767], default 0)

Type :

int

author

Name of the creator of the asset (default "", never None)

Type :

str

catalog_id

Identifier for the asset's catalog, used by Blender to look up the asset's catalog path. Must be a UUID according to RFC4122. (default "", never None)

Type :

str

catalog_simple_name

Simple name of the asset's catalog, for debugging and data recovery purposes (default "", readonly, never None)

Type :

str

copyright

Copyright notice for this asset. An empty copyright notice does not necessarily indicate that this is copyright-free. Contact the author if any clarification is needed. (default "", never None)

Type :

str

description

A description of the asset to be displayed for the user (default "", never None)

Type :

str

license

The type of license this asset is distributed under. An empty license name does not necessarily indicate that this is free of licensing terms. Contact the author if any clarification is needed. (default "", never None)

Type :

str

tags

Custom tags (name tokens) for the asset, used for filtering and general asset management (default None, readonly)

Type :

AssetTags[AssetTag]

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

| AssetRepresentation.metadata FileSelectEntry.asset_data | ID.asset_data |

## AssetRepresentation(bpy_struct)

A reference to an asset within the system.

base class — bpy_struct

class bpy.types. AssetRepresentation ( bpy_struct )

Public interface to asset system information.

full_library_path

Absolute path to the .blend file containing this asset (default "", readonly, never None)

Type :

str

full_path

Absolute path to the .blend file containing this asset extended with the path of the asset inside the file (default "", readonly, never None)

Type :

str

id_type

The type of the data-block, if the asset represents one ('NONE' otherwise) (default 'ACTION' , readonly)

Type :

Literal[Id Type Items]

local_id

The local data-block this asset represents; only valid if that is a data-block in this file (readonly)

Type :

ID

metadata

Additional information about the asset (readonly)

Type :

AssetMetaData

name

(default "", readonly, never None)

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

| bpy.context.asset bpy.context.selected_assets AssetShelf.asset_poll | AssetShelf.draw_context_menu Context.asset |

## AssetTag(bpy_struct)

A user-defined classification marker.

base class — bpy_struct

class bpy.types. AssetTag ( bpy_struct )

A user-assigned classification.

name

The identifier that makes up this tag (default "", never None)

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

| AssetMetaData.tags AssetTags.new | AssetTags.remove |

## AssetTags(bpy_prop_collection)

Collection of classification markers.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. AssetTags ( bpy_prop_collection )

Set of user-defined classifications on an asset.

new ( name , * , skip_if_exists = False )

Assign a new classification to this asset.

Parameters :

- name ( str ) – Name, (never None)

- skip_if_exists ( bool ) – Skip if Exists, Do not add a new tag if one of the same type already exists (optional)

Returns :

New tag

Return type :

AssetTag

remove ( tag )

Unassign a classification.

Parameters :

tag (AssetTag) – Removed tag (never None)

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

| AssetMetaData.tags | |

## AssetWeakReference(bpy_struct)

Lightweight reference to an asset.

base class — bpy_struct

class bpy.types. AssetWeakReference ( bpy_struct )

A minimal asset identifier.

asset_library_identifier

(default "", readonly, never None)

Type :

str

asset_library_type

(default 'ALL' , readonly)

- ALL
All Libraries – Show assets from all of the listed asset libraries.

- LOCAL
Current File – Show the assets currently available in this Blender session.

- ESSENTIALS
Essentials – Show the basic building blocks and utilities coming with Blender.

- CUSTOM
Custom – Show assets from the asset libraries configured in the Preferences.

Type :

Literal['ALL', 'LOCAL', 'ESSENTIALS', 'CUSTOM']

relative_asset_identifier

(default "", readonly, never None)

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

| AssetShelf.get_active_asset Paint.brush_asset_reference | Paint.eraser_brush_asset_reference |
