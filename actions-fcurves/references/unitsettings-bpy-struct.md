# Unitsettings Bpy Struct, Unknowntype Bpy Struct, Userextensionrepo Bpy Struct, Userextensionrepocollection Bpy Prop Collection ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: UnitSettings(bpy_struct); UnknownType(bpy_struct); UserExtensionRepo(bpy_struct); UserExtensionRepoCollection(bpy_prop_collection); UVLoopLayers(bpy_prop_collection); UVProjector(bpy_struct); UvSculpt(bpy_struct); VertexGroup(bpy_struct); VertexGroupElement(bpy_struct); VertexGroups(bpy_prop_collection); VertexPaint(Paint).

## UnitSettings(bpy_struct)

### UnitSettings(bpy_struct)

base class — bpy_struct

class bpy.types. UnitSettings ( bpy_struct )

length_unit

Which unit length values are shown in (default 'DEFAULT' )

Type :

Literal[‘DEFAULT’]

mass_unit

Which unit mass values are shown in (default 'DEFAULT' )

Type :

Literal[‘DEFAULT’]

scale_length

Conversion factor between Blender units and real dimensions. Picking a tiny or huge unit scale helps keep numerical precision usable when modeling at microscopic or astronomical sizes (in [1e-09, inf], default 0.0)

Type :

float

system

Which measurement system the interface controls follow (default 'NONE' )

Type :

Literal[‘NONE’, ‘METRIC’, ‘IMPERIAL’]

system_rotation

Which unit is applied when showing and editing rotations (default 'DEGREES' )

- DEGREES
Degrees – Use degrees for measuring angles and rotations.

- RADIANS
Radians.

Type :

Literal[‘DEGREES’, ‘RADIANS’]

temperature_unit

Which unit temperature values are shown in (default 'DEFAULT' )

Type :

Literal[‘DEFAULT’]

time_unit

Which unit time values are shown in (default 'DEFAULT' )

Type :

Literal[‘DEFAULT’]

use_separate

Break units into paired components when shown (e.g. 1m 0cm) (default False)

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

| Scene.unit_settings | |

## UnknownType(bpy_struct)

### UnknownType(bpy_struct)

base class — bpy_struct

class bpy.types. UnknownType ( bpy_struct )

Placeholder RNA type that backs pointers to data which is unknown or internal.

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

| ShapeKey.data | |

## UserExtensionRepo(bpy_struct)

### UserExtensionRepo(bpy_struct) 

base class — bpy_struct

class bpy.types. UserExtensionRepo ( bpy_struct ) 

Configuration that describes an extension repository

access_token 

A personal access token that certain repositories might ask for (default "", never None)

Type :

str

custom_directory 

Local folder where the extensions live (default "", never None)

Type :

str

directory 

Local folder where the extensions live (default "", readonly, never None)

Type :

str

enabled 

Turn the repository on (default False)

Type :

bool

module 

A module identifier that must be unique (default "", never None)

Type :

str

name 

A repository name that must be unique (default "", never None)

Type :

str

remote_url 

Remote URL pointing at the extension repository; a local path may be given via the file URI scheme "file://" (default "", never None)

Type :

str

source 

Pick whether the repository sits in a user-managed folder or one supplied by the system (default 'USER' )

- USER
User – Repository managed by the user, stored in user directories.

- SYSTEM
System – Read-only repository provided by the system.

Type :

Literal['USER', 'SYSTEM']

use_access_token 

The repository needs an access token (default False)

Type :

bool

use_cache 

Once installed, downloaded package files get removed (default False)

Type :

bool

use_custom_directory 

Set the extension storage path by hand; with this off, a directory under the user's profile is made instead. (default False)

Type :

bool

use_remote_url 

Keep the repository in sync with a remote URL (default False)

Type :

bool

use_sync_on_startup 

Let Blender look for updates each time it starts (default False)

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

| PreferencesExtensions.repos UserExtensionRepoCollection.new | UserExtensionRepoCollection.remove |

## UserExtensionRepoCollection(bpy_prop_collection)

### UserExtensionRepoCollection(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. UserExtensionRepoCollection ( bpy_prop_collection ) 

A grouping that holds the user's extension repositories

classmethod new ( * , name = '' , module = '' , custom_directory = '' , remote_url = '' , source = 'USER' ) 

Create a fresh repository

Parameters :

- name ( str ) – Name, (optional, never None)

- module ( str ) – Module, (optional, never None)

- custom_directory ( str ) – Custom Directory, (optional, never None)

- remote_url ( str ) – Remote URL, (optional, never None)

- source ( Literal [ 'USER' , 'SYSTEM' ] ) – Source, The way the repository gets managed (optional)

- USER
User – Repository managed by the user, stored in user directories.

- SYSTEM
System – Read-only repository provided by the system.

Returns :

Newly added repository

Return type :

UserExtensionRepo

classmethod remove ( repo ) 

Delete repos

Parameters :

repo (UserExtensionRepo) – Repository to remove (never None)

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

| PreferencesExtensions.repos | |

## UVLoopLayers(bpy_prop_collection)

### UVLoopLayers(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. UVLoopLayers ( bpy_prop_collection ) 

A grouping that holds the UV map layers

active 

Active UV Map layer

Type :

MeshUVLoopLayer

active_index 

Active UV map index (in [0, inf], default 0)

Type :

int

new ( * , name = 'UVMap' , do_init = True ) 

Attach a UV map layer to the Mesh

Parameters :

- name ( str ) – UV map name (optional, never None)

- do_init ( bool ) – Decide whether the new layer is seeded by copying the current active one, or, when none is active, with a default UVmap (optional)

Returns :

The newly created layer

Return type :

MeshUVLoopLayer

remove ( layer ) 

Delete a UV map layer

Parameters :

layer (MeshUVLoopLayer) – The layer to remove (never None)

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

| Mesh.uv_layers | |

## UVProjector(bpy_struct)

### UVProjector(bpy_struct) 

base class — bpy_struct

class bpy.types. UVProjector ( bpy_struct ) 

A projector consumed by the UV project modifier

object 

Object whose transform serves as the projector

Type :

Object

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

| UVProjectModifier.projectors | |

## UvSculpt(bpy_struct)

### UvSculpt(bpy_struct) 

base class — bpy_struct

class bpy.types. UvSculpt ( bpy_struct ) 

curve_distance_falloff 

(readonly)

Type :

CurveMapping

curve_distance_falloff_preset 

(default 'CUSTOM' )

Type :

Literal[Brush Curve Preset Items]

size 

(in [1, 10000], default 100)

Type :

int

strength 

(in [0, 1], default 1.0)

Type :

float

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

| ToolSettings.uv_sculpt | |

## VertexGroup(bpy_struct)

### VertexGroup(bpy_struct) 

base class — bpy_struct

class bpy.types. VertexGroup ( bpy_struct ) 

A set of vertices serving armature deform and similar uses

index 

The vertex group's index number (in [0, inf], default 0, readonly)

Type :

int

lock_weight 

Hold the group's weights in their current relative proportions (default False)

Type :

bool

name 

Vertex group name (default "", never None)

Type :

str

add ( index , weight , type ) 

Place vertices into the group

Parameters :

- index ( Sequence [ int ] ) – List of indices (array of 1 items, in [-inf, inf])

- weight ( float ) – Vertex weight (in [0, 1])

- type ( Literal [ 'REPLACE' , 'ADD' , 'SUBTRACT' ] ) – Vertex assign mode

- REPLACE
Replace – Replace.

- ADD
Add – Add.

- SUBTRACT
Subtract – Subtract.

remove ( index ) 

Take vertices out of the group

Parameters :

index ( Sequence [ int ] ) – List of indices (array of 1 items, in [-inf, inf])

weight ( index ) 

Read back a vertex's weight in the group

Parameters :

index ( int ) – Index, The index of the vertex (in [0, inf])

Returns :

Vertex weight (in [0, 1])

Return type :

float

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

| Object.vertex_groups VertexGroups.active | VertexGroups.new VertexGroups.remove |

## VertexGroupElement(bpy_struct)

### VertexGroupElement(bpy_struct) 

base class — bpy_struct

class bpy.types. VertexGroupElement ( bpy_struct ) 

The weight a single vertex carries within a vertex group

group 

(in [0, inf], default 0, readonly)

Type :

int

weight 

Vertex Weight (in [0, 1], default 0.0)

Type :

float

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

| LatticePoint.groups | MeshVertex.groups |

## VertexGroups(bpy_prop_collection)

### VertexGroups(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. VertexGroups ( bpy_prop_collection ) 

A grouping that holds vertex groups

active 

Vertex groups of the object

Type :

VertexGroup

active_index 

Active index in vertex group array (in [0, inf], default 0)

Type :

int

new ( * , name = 'Group' ) 

Attach a vertex group to the object

Parameters :

name ( str ) – Vertex group name (optional, never None)

Returns :

New vertex group

Return type :

VertexGroup

remove ( group ) 

Drop a vertex group from the object

Parameters :

group (VertexGroup) – Vertex group to remove (never None)

clear ( ) 

Drop every vertex group from the object

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

| Object.vertex_groups | |

## VertexPaint(Paint)

### VertexPaint(Paint) 

base classes — bpy_struct, Paint

class bpy.types. VertexPaint ( Paint ) 

The settings governing vertex and weight paint mode

use_group_restrict 

Confine painting to the vertices that belong to the group (default False)

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

| bpy_struct.id_data Paint.brush Paint.brush_asset_reference Paint.eraser_brush Paint.eraser_brush_asset_reference Paint.palette Paint.show_brush Paint.show_brush_on_surface Paint.show_low_resolution Paint.use_sculpt_delay_updates Paint.show_bvh_nodes Paint.use_symmetry_x Paint.use_symmetry_y | Paint.use_symmetry_z Paint.use_symmetry_feather Paint.cavity_curve Paint.use_cavity Paint.tile_offset Paint.tile_x Paint.tile_y Paint.tile_z Paint.show_strength_curve Paint.show_size_curve Paint.show_jitter_curve Paint.unified_paint_settings |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Paint.bl_rna_get_subclass Paint.bl_rna_get_subclass_py |

### References 

| ToolSettings.vertex_paint | ToolSettings.weight_paint |
