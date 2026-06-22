# Pitchmodifier Stripmodifier, Pivotconstraint Constraint, Point Bpy Struct, Pointcache Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: PitchModifier(StripModifier); PivotConstraint(Constraint); Point(bpy_struct); PointCache(bpy_struct); PointCacheItem(bpy_struct); PointCaches(bpy_prop_collection); PointerProperty(Property); Pose(bpy_struct).

## PitchModifier(StripModifier)

### PitchModifier(StripModifier)

base classes — bpy_struct, StripModifier

class bpy.types. PitchModifier ( StripModifier )

Adjusts the pitch of an audio strip

cents

A cent is one one-hundredth of a semi-tone. (in [-100, 100], default 0)

Type :

int

mode

Mode of the pitch shift (default 'SEMITONES' )

- SEMITONES
Semitones – Shift pitch using semitones and cents.

- RATIO
Ratio – Shift pitch using a direct ratio.

Type :

Literal[‘SEMITONES’, ‘RATIO’]

preserve_formant

Whether to preserve the vocal formants when shifting the pitch. (default False)

Type :

bool

quality

Quality of the pitch shifting (default 'HIGH' )

- HIGH
High – Prioritize high-quality pitch processing.

- FAST
Fast – Prioritize speed over audio quality.

- CONSISTENT
Consistent – Prioritize consistency for dynamic pitch changes.

Type :

Literal[‘HIGH’, ‘FAST’, ‘CONSISTENT’]

ratio

Factor by which the audio pitch is scaled. (in [0.5, 2], default 0.0)

Type :

float

semitones

Number of semitones to shift the pitch. (in [-12, 12], default 0)

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

| bpy_struct.id_data StripModifier.name StripModifier.type StripModifier.mute StripModifier.enable StripModifier.show_expanded | StripModifier.input_mask_type StripModifier.mask_time StripModifier.input_mask_strip StripModifier.input_mask_id StripModifier.is_active |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values StripModifier.bl_rna_get_subclass StripModifier.bl_rna_get_subclass_py |

## PivotConstraint(Constraint)

### PivotConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. PivotConstraint ( Constraint )

Pivots the rotation about an alternate point

head_tail

Target along length of bone: Head is 0, Tail is 1 (in [0, 1], default 0.0)

Type :

float

offset

Where the pivot sits relative to the target (when one is set), or relative to the owner's location (when Fixed Position is off), or the absolute pivot point itself (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

rotation_range

Range of rotation over which pivoting takes place (default 'NX' )

- `ALWAYS_ACTIVE`
Always – Pivot on every rotation, no matter the direction.

- NX
-X Rotation – Pivot only while rotating into the X-axis negative range.

- NY
-Y Rotation – Pivot only while rotating into the Y-axis negative range.

- NZ
-Z Rotation – Pivot only while rotating into the Z-axis negative range.

- X
X Rotation – Pivot only while rotating into the X-axis positive range.

- Y
Y Rotation – Pivot only while rotating into the Y-axis positive range.

- Z
Z Rotation – Pivot only while rotating into the Z-axis positive range.

Type :

Literal[‘`ALWAYS_ACTIVE`’, ‘NX’, ‘NY’, ‘NZ’, ‘X’, ‘Y’, ‘Z’]

subtarget

(default “”, never None)

Type :

str

target

Target Object, defining the position of the pivot when defined

Type :

Object

use_bbone_shape

Trace the B-Bone segment shape when working out the Head/Tail position (default False)

Type :

bool

use_relative_location

Treat the offset as an absolute point in space rather than relative to the target (default True)

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

## Point(bpy_struct)

### Point(bpy_struct)

base class — bpy_struct

class bpy.types. Point ( bpy_struct )

A single point within a point cloud

co

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

index

Index of this point (in [0, inf], default 0, readonly)

Type :

int

radius

(in [-inf, inf], default 0.0)

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

| PointCloud.points | |

## PointCache(bpy_struct)

### PointCache(bpy_struct)

base class — bpy_struct

class bpy.types. PointCache ( bpy_struct )

The point cache currently active for physics simulations

filepath

Cache file path (default “”, never None, blend relative // prefix supported)

Type :

str

frame_end

Frame on which the simulation stops (in [1, 1048574], default 0)

Type :

int

frame_start

Frame on which the simulation starts (in [-1048574, 1048574], default 0)

Type :

int

frame_step

Number of frames between cached frames (in [1, 20], default 0)

Type :

int

index

Index number of cache files (in [-1, 100], default 0)

Type :

int

info

Info on current cache status (default “”, readonly, never None)

Type :

str

is_baked

Whether the cache has been baked (default False, readonly)

Type :

bool

is_baking

Whether the cache is currently baking (default False, readonly)

Type :

bool

is_frame_skip

Whether some frames got skipped while the cache was baked or saved (default False, readonly)

Type :

bool

is_outdated

(default False, readonly)

Type :

bool

name

Cache name (default “”, never None)

Type :

str

point_caches

(default None, readonly)

Type :

PointCaches[PointCacheItem]

use_disk_cache

Write cache files to disk (the .blend file has to be saved first) (default False)

Type :

bool

use_external

Pull the cache from an external location (default False)

Type :

bool

use_library_path

Use this file's path for the disk cache when it is library linked into another file (turn this off for per-scene local bakes) (default True)

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

| ClothModifier.point_cache DynamicPaintSurface.point_cache ParticleSystem.point_cache | RigidBodyWorld.point_cache SoftBodyModifier.point_cache |

## PointCacheItem(bpy_struct)

### PointCacheItem(bpy_struct)

base class — bpy_struct

class bpy.types. PointCacheItem ( bpy_struct )

A point cache entry for physics simulations

filepath

Cache file path (default “”, never None, blend relative // prefix supported)

Type :

str

frame_end

Frame on which the simulation stops (in [1, 1048574], default 0)

Type :

int

frame_start

Frame on which the simulation starts (in [-1048574, 1048574], default 0)

Type :

int

frame_step

Number of frames between cached frames (in [1, 20], default 0)

Type :

int

index

Index number of cache files (in [-1, 100], default 0)

Type :

int

info

Info on current cache status (default “”, readonly, never None)

Type :

str

is_baked

Whether the cache has been baked (default False, readonly)

Type :

bool

is_baking

Whether the cache is currently baking (default False, readonly)

Type :

bool

is_frame_skip

Whether some frames got skipped while the cache was baked or saved (default False, readonly)

Type :

bool

is_outdated

(default False, readonly)

Type :

bool

name

Cache name (default “”, never None)

Type :

str

use_disk_cache

Write cache files to disk (the .blend file has to be saved first) (default False)

Type :

bool

use_external

Pull the cache from an external location (default False)

Type :

bool

use_library_path

Use this file's path for the disk cache when it is library linked into another file (turn this off for per-scene local bakes) (default True)

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

| PointCache.point_caches | |

## PointCaches(bpy_prop_collection)

### PointCaches(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. PointCaches ( bpy_prop_collection )

The set of point caches

active_index

(in [0, inf], default 0)

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

| PointCache.point_caches | |

## PointerProperty(Property)

### PointerProperty(Property)

base classes — bpy_struct, Property

class bpy.types. PointerProperty ( Property )

An RNA property that references another RNA struct.

fixed_type

The fixed pointer type; blank when the type can vary (readonly)

Type :

Struct

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

| bpy_struct.id_data Property.name Property.identifier Property.description Property.translation_context Property.type Property.subtype Property.srna Property.unit Property.icon Property.is_readonly Property.is_animatable Property.is_overridable Property.is_required Property.is_argument_optional Property.is_never_none Property.is_hidden | Property.is_skip_save Property.is_skip_preset Property.is_output Property.is_registered Property.is_registered_optional Property.is_runtime Property.is_enum_flag Property.is_library_editable Property.is_path_output Property.is_path_supports_blend_relative Property.is_path_supports_templates Property.is_deprecated Property.deprecated_note Property.deprecated_version Property.deprecated_removal_version Property.tags |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Property.bl_rna_get_subclass Property.bl_rna_get_subclass_py |

## Pose(bpy_struct)

### Pose(bpy_struct)

base class — bpy_struct

class bpy.types. Pose ( bpy_struct )

A set of pose channels together with the settings that animate bones.

animation_visualization

Animation data attached to this data-block (readonly, never None)

Type :

AnimViz

bones

The armature's pose bones, one per bone (default None, readonly)

Type :

bpy_prop_collection[PoseBone]

ik_param

Configuration passed to the IK solver (readonly)

Type :

IKParam

ik_solver

Which IK solver drives the IK chain (default 'LEGACY' )

- LEGACY
Standard – The original IK solver.

- ITASC
iTaSC – A stateful solver handling multiple constraints.

Type :

Literal[‘LEGACY’, ‘ITASC’]

use_auto_ik

Insert short-lived IK constraints while grabbing bones in Pose Mode (default False)

Type :

bool

use_mirror_relative

Treat transforms as relative when working in X-mirror mode (not supported with Auto IK) (default False)

Type :

bool

use_mirror_x

Mirror edits onto the matching bone across the X-Axis (default False)

Type :

bool

classmethod apply_pose_from_action ( action , * , evaluation_time = 0.0 )

Evaluate the supplied action at a chosen time and set this pose from it. Affects only the selected bones, or every bone when nothing is selected.

Parameters :

- action (Action) – Action, The Action that holds the pose

- evaluation_time ( float ) – Evaluation Time, The time at which the action is sampled to read off the pose (in [-inf, inf], optional)

classmethod blend_pose_from_action ( action , * , blend_factor = 1.0 , evaluation_time = 0.0 )

Evaluate the supplied action at a chosen time and mix it into this pose. Affects only the selected bones, or every bone when nothing is selected.

Parameters :

- action (Action) – Action, The Action that holds the pose

- blend_factor ( float ) – Blend Factor, Degree to which the Action sways the resulting pose (in [0, 1], optional)

- evaluation_time ( float ) – Evaluation Time, The time at which the action is sampled to read off the pose (in [-inf, inf], optional)

classmethod backup_create ( action )

Save the current pose as a backup. Only bones animated in the Action are captured. The backup belongs to the object, which may hold just one at a time; release it with backup_clear() once it is no longer needed.

Parameters :

action (Action) – Action, An Action carrying animation for the bones. Only animated bones go into the backup.

classmethod backup_restore ( )

Reapply the pose backup taken earlier. It may be invoked repeatedly. Refer to Pose.backup_create() for details.

Returns :

True once the backup is reapplied, False when none exists to reapply

Return type :

bool

classmethod backup_clear ( )

Discard a pose backup made earlier. Refer to Pose.backup_create() for details.

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

| Object.pose | |
