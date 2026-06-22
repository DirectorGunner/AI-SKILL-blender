# Blenddatasounds Bpy Prop Collection, Blenddataspeakers Bpy Prop Collection, Blenddatatexts Bpy Prop Collection, Blenddatatextures Bpy Prop Collection ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: BlendDataSounds(bpy_prop_collection); BlendDataSpeakers(bpy_prop_collection); BlendDataTexts(bpy_prop_collection); BlendDataTextures(bpy_prop_collection); BlendDataVolumes(bpy_prop_collection); BlendDataWindowManagers(bpy_prop_collection); BlendDataWorkSpaces(bpy_prop_collection); BlendDataWorlds(bpy_prop_collection); BlenderRNA(bpy_struct); BlendImportContextItems(bpy_prop_collection); BlendImportContextLibraries(bpy_prop_collection); BlendImportContextLibrary(bpy_struct); BoidRule(bpy_struct).

## BlendDataSounds(bpy_prop_collection)

### BlendDataSounds(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendDataSounds(bpy_prop_collection)

Houses a collection of audio resources.

load(filepath, *, check_existing=False)

Imports an audio file into Blender's database.

Parameters:
- filepath (str) – file location (cannot be None, blend relative // prefix supported)
- check_existing (bool) – Reuse an existing data-block if already loaded (optional)

Returns:
New text data-block

Return type:
Sound

remove(sound, *, do_unlink=True, do_id_user=True, do_ui_user=True)

Takes out a sound from the blend file.

Parameters:
- sound (Sound) – Sound to remove (cannot be None)
- do_unlink (bool) – Disconnect all linkages before removal (optional)
- do_id_user (bool) – Reduce user counts in all dependent structures (optional)
- do_ui_user (bool) – Eliminate UI references (optional)

tag(value)

Attach metadata.

Parameters:
- value (bool) – Tag value

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – Name of the RNA type.
- default (bpy.types.Struct | None) – Return if absent.

Returns:
The RNA type or return value.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – Name of the RNA type.
- default (type | None) – Return if absent.

Returns:
The class or return value.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendData.sounds | |

## BlendDataSpeakers(bpy_prop_collection)

### BlendDataSpeakers(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendDataSpeakers(bpy_prop_collection)

Manages speaker object data within the database.

new(name)

Generates a speaker object and registers it in the main database.

Parameters:
- name (str) – Speaker identifier (cannot be None)

Returns:
New speaker data-block

Return type:
Speaker

remove(speaker, *, do_unlink=True, do_id_user=True, do_ui_user=True)

Discards a speaker object from the blend file.

Parameters:
- speaker (Speaker) – Speaker to discard (cannot be None)
- do_unlink (bool) – Break all connections before disposal (WARNING: will also delete objects instancing that speaker data) (optional)
- do_id_user (bool) – Update user totals in dependent structures (optional)
- do_ui_user (bool) – Wipe interface references (optional)

tag(value)

Append a tag.

Parameters:
- value (bool) – Tag state

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – RNA class designation.
- default (bpy.types.Struct | None) – Alternate if missing.

Returns:
The RNA type or alternate.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – RNA class designation.
- default (type | None) – Alternate if missing.

Returns:
The class or alternate.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendData.speakers | |

## BlendDataTexts(bpy_prop_collection)

### BlendDataTexts(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendDataTexts(bpy_prop_collection)

Provides access to text block resources in the database.

new(name)

Constructs a text block and adds it to the main database.

Parameters:
- name (str) – Block identifier (cannot be None)

Returns:
New text data-block

Return type:
Text

remove(text, *, do_unlink=True, do_id_user=True, do_ui_user=True)

Removes a text block from the blend file.

Parameters:
- text (Text) – Text block to remove (cannot be None)
- do_unlink (bool) – Disconnect all usages before removal (optional)
- do_id_user (bool) – Reduce counts in linked data-blocks (optional)
- do_ui_user (bool) – Clear UI associations (optional)

load(filepath, *, internal=False)

Reads a text file into Blender's text block storage.

Parameters:
- filepath (str) – file system path (cannot be None, blend relative // prefix supported)
- internal (bool) – Store as internal; Embed file within the blend file (optional)

Returns:
New text data-block

Return type:
Text

tag(value)

Label with a tag.

Parameters:
- value (bool) – Tag flag

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – The RNA type name.
- default (bpy.types.Struct | None) – Fallback when not available.

Returns:
The RNA type or fallback.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – The RNA type name.
- default (type | None) – Fallback when not available.

Returns:
The class or fallback.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendData.texts | |

## BlendDataTextures(bpy_prop_collection)

### BlendDataTextures(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendDataTextures(bpy_prop_collection)

Manages texture data blocks within Blender.

new(name, type)

Instantiates and stores a texture in the main database.

Parameters:
- name (str) – Texture identifier (cannot be None)
- type (Literal[Texture Type Items]) – Texture category; determines the texture subtype to instantiate

Returns:
New texture data-block

Return type:
Texture

remove(texture, *, do_unlink=True, do_id_user=True, do_ui_user=True)

Purges a texture from the blend file.

Parameters:
- texture (Texture) – Texture to purge (cannot be None)
- do_unlink (bool) – Sever all references before removal (optional)
- do_id_user (bool) – Decrement user counts across linked items (optional)
- do_ui_user (bool) – Expunge UI associations (optional)

tag(value)

Stamp with metadata.

Parameters:
- value (bool) – Tag indicator

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – The RNA class identifier.
- default (bpy.types.Struct | None) – Alternate when not found.

Returns:
The RNA type or alternate.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – The RNA class identifier.
- default (type | None) – Alternate when not found.

Returns:
The class or alternate.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendData.textures | |

## BlendDataVolumes(bpy_prop_collection)

### BlendDataVolumes(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendDataVolumes(bpy_prop_collection)

Stores volume data structures in the database.

new(name)

Creates and registers a volume in the main database.

Parameters:
- name (str) – Volume identifier (cannot be None)

Returns:
New volume data-block

Return type:
Volume

remove(volume, *, do_unlink=True, do_id_user=True, do_ui_user=True)

Destroys a volume from the blend file.

Parameters:
- volume (Volume) – Volume to destroy (cannot be None)
- do_unlink (bool) – Sever all connections before destruction (WARNING: will also delete objects instancing that volume data) (optional)
- do_id_user (bool) – Lower user counts in dependent blocks (optional)
- do_ui_user (bool) – Strip UI connections (optional)

tag(value)

Mark with metadata.

Parameters:
- value (bool) – Tag indicator

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – Name of the RNA type.
- default (bpy.types.Struct | None) – Substitute when absent.

Returns:
The RNA type or substitute.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – Name of the RNA type.
- default (type | None) – Substitute when absent.

Returns:
The class or substitute.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendData.volumes | |

## BlendDataWindowManagers(bpy_prop_collection)

### BlendDataWindowManagers(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendDataWindowManagers(bpy_prop_collection)

Provides the collection of window management instances.

tag(value)

Apply a metadata tag.

Parameters:
- value (bool) – Tag setting

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – RNA type identifier.
- default (bpy.types.Struct | None) – Fallback if not found.

Returns:
The RNA type or fallback.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – RNA type identifier.
- default (type | None) – Fallback if not found.

Returns:
The class or fallback.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendData.window_managers | |

## BlendDataWorkSpaces(bpy_prop_collection)

### BlendDataWorkSpaces(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendDataWorkSpaces(bpy_prop_collection)

Provides access to workspace data structures.

tag(value)

Assign metadata.

Parameters:
- value (bool) – Tag status

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – Name of the RNA type.
- default (bpy.types.Struct | None) – Return if not discovered.

Returns:
The RNA type or return value.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – Name of the RNA type.
- default (type | None) – Return if not discovered.

Returns:
The class or return value.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendData.workspaces | |

## BlendDataWorlds(bpy_prop_collection)

### BlendDataWorlds(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendDataWorlds(bpy_prop_collection)

Manages the collection of world environment data.

new(name)

Builds and stores a world in the main database.

Parameters:
- name (str) – World identifier (cannot be None)

Returns:
New world data-block

Return type:
World

remove(world, *, do_unlink=True, do_id_user=True, do_ui_user=True)

Takes away a world from the blend file.

Parameters:
- world (World) – World to take away (cannot be None)
- do_unlink (bool) – Detach references before removal (optional)
- do_id_user (bool) – Lower user totals in all dependent items (optional)
- do_ui_user (bool) – Sever UI associations (optional)

tag(value)

Attach metadata.

Parameters:
- value (bool) – Tag flag

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – Designation of the RNA type.
- default (bpy.types.Struct | None) – Alternative if absent.

Returns:
The RNA type or alternative.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – Designation of the RNA type.
- default (type | None) – Alternative if absent.

Returns:
The class or alternative.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendData.worlds | |

## BlenderRNA(bpy_struct)

### BlenderRNA(bpy_struct)

base class — bpy_struct

class bpy.types.BlenderRNA(bpy_struct)

Defines the structural taxonomy for Blender's type system.

structs

(default None, readonly)

Type:
bpy_prop_collection[Struct]

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – Identifier for the RNA type.
- default (bpy.types.Struct | None) – Fallback result if not found.

Returns:
The RNA type or fallback result.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – Identifier for the RNA type.
- default (type | None) – Fallback result if not found.

Returns:
The class or fallback result.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

## BlendImportContextItems(bpy_prop_collection)

### BlendImportContextItems(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendImportContextItems(bpy_prop_collection)

Groups together the per-entry items of a blendfile import context.

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

## BlendImportContextLibraries(bpy_prop_collection)

### BlendImportContextLibraries(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendImportContextLibraries(bpy_prop_collection)

Groups together the source libraries — that is, the blendfile paths — referenced by an import.

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

| BlendImportContextItem.source_libraries | |

## BlendImportContextLibrary(bpy_struct)

### BlendImportContextLibrary(bpy_struct)

base class — bpy_struct

class bpy.types.BlendImportContextLibrary(bpy_struct)

Points to one library (blendfile) within a BlendImportContext. At present it is surfaced only as read-only data for the handlers running before and after a blend import.

filepath

(default "", readonly, never None)

Type:
str

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

| BlendImportContextItem.source_libraries | |

## BoidRule(bpy_struct)

### BoidRule(bpy_struct)

base class — bpy_struct

subclasses —
BoidRuleAverageSpeed, BoidRuleAvoid, BoidRuleAvoidCollision, BoidRuleFight, BoidRuleFollowLeader, BoidRuleGoal

class bpy.types.BoidRule(bpy_struct)

name

Boid rule name (default "", never None)

Type:
str

type

(default 'GOAL', readonly)

Type:
Literal[Boidrule Type Items]

use_in_air

Apply the rule while the boid is airborne (default False)

Type:
bool

use_on_land

Apply the rule while the boid is grounded (default False)

Type:
bool

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

| BoidSettings.active_boid_state BoidState.active_boid_rule | BoidState.rules |
