# Boidruleaveragespeed Boidrule, Boidruleavoid Boidrule, Boidruleavoidcollision Boidrule, Boidrulefight Boidrule ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: BoidRuleAverageSpeed(BoidRule); BoidRuleAvoid(BoidRule); BoidRuleAvoidCollision(BoidRule); BoidRuleFight(BoidRule); BoidRuleFollowLeader(BoidRule); BoidRuleGoal(BoidRule); BoidSettings(bpy_struct); BoidState(bpy_struct).

## BoidRuleAverageSpeed(BoidRule)

### BoidRuleAverageSpeed(BoidRule)

base classes — bpy_struct, BoidRule

class bpy.types.BoidRuleAverageSpeed(BoidRule)

level

Degree to which the z-component of velocity stays fixed (in [0, 1], default 0.0)

Type:
float

speed

Fraction of the maximum speed to use (in [0, 1], default 0.0)

Type:
float

wander

Rate at which the velocity's heading is randomized (in [0, 1], default 0.0)

Type:
float

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

| bpy_struct.id_data BoidRule.name BoidRule.type | BoidRule.use_in_air BoidRule.use_on_land |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values BoidRule.bl_rna_get_subclass BoidRule.bl_rna_get_subclass_py |

## BoidRuleAvoid(BoidRule)

### BoidRuleAvoid(BoidRule)

base classes — bpy_struct, BoidRule

class bpy.types.BoidRuleAvoid(BoidRule)

fear_factor

Steer away from an object once its danger exceeds this level (in [0, 100], default 0.0)

Type:
float

object

Object to avoid

Type:
Object

use_predict

Predict target movement (default False)

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

| bpy_struct.id_data BoidRule.name BoidRule.type | BoidRule.use_in_air BoidRule.use_on_land |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values BoidRule.bl_rna_get_subclass BoidRule.bl_rna_get_subclass_py |

## BoidRuleAvoidCollision(BoidRule)

### BoidRuleAvoidCollision(BoidRule)

base classes — bpy_struct, BoidRule

class bpy.types.BoidRuleAvoidCollision(BoidRule)

look_ahead

How many seconds ahead the boid anticipates (in [0, 100], default 0.0)

Type:
float

use_avoid

Avoid collision with other boids (default False)

Type:
bool

use_avoid_collision

Avoid collision with deflector objects (default False)

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

| bpy_struct.id_data BoidRule.name BoidRule.type | BoidRule.use_in_air BoidRule.use_on_land |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values BoidRule.bl_rna_get_subclass BoidRule.bl_rna_get_subclass_py |

## BoidRuleFight(BoidRule)

### BoidRuleFight(BoidRule)

base classes — bpy_struct, BoidRule

class bpy.types.BoidRuleFight(BoidRule)

distance

Engage boids no farther away than this (in [0, 100], default 0.0)

Type:
float

flee_distance

Retreat until reaching this distance (in [0, 100], default 0.0)

Type:
float

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

| bpy_struct.id_data BoidRule.name BoidRule.type | BoidRule.use_in_air BoidRule.use_on_land |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values BoidRule.bl_rna_get_subclass BoidRule.bl_rna_get_subclass_py |

## BoidRuleFollowLeader(BoidRule)

### BoidRuleFollowLeader(BoidRule)

base classes — bpy_struct, BoidRule

class bpy.types.BoidRuleFollowLeader(BoidRule)

distance

Gap to maintain behind the leader (in [0, 100], default 0.0)

Type:
float

object

Follow this object instead of a boid

Type:
Object

queue_count

Count of boids forming the line (in [0, 100], default 0)

Type:
int

use_line

Follow leader in a line (default False)

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

| bpy_struct.id_data BoidRule.name BoidRule.type | BoidRule.use_in_air BoidRule.use_on_land |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values BoidRule.bl_rna_get_subclass BoidRule.bl_rna_get_subclass_py |

## BoidRuleGoal(BoidRule)

### BoidRuleGoal(BoidRule)

base classes — bpy_struct, BoidRule

class bpy.types.BoidRuleGoal(BoidRule)

object

Goal object

Type:
Object

use_predict

Predict target movement (default False)

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

| bpy_struct.id_data BoidRule.name BoidRule.type | BoidRule.use_in_air BoidRule.use_on_land |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values BoidRule.bl_rna_get_subclass BoidRule.bl_rna_get_subclass_py |

## BoidSettings(bpy_struct)

### BoidSettings(bpy_struct)

base class — bpy_struct

class bpy.types.BoidSettings(bpy_struct)

Configuration controlling boid simulation behavior

accuracy

Accuracy of attack (in [0, 1], default 0.0)

Type:
float

active_boid_state

(readonly)

Type:
BoidRule

active_boid_state_index

(in [0, inf], default 0)

Type:
int

aggression

Multiplier on enemy strength that the boid is still willing to fight (in [0, 100], default 0.0)

Type:
float

air_acc_max

Top acceleration while airborne, expressed relative to peak speed (in [0, 1], default 0.0)

Type:
float

air_ave_max

Top angular velocity while airborne, expressed relative to 180 degrees (in [0, 1], default 0.0)

Type:
float

air_personal_space

Personal-space radius in air, given as a percentage of particle size (in [0, 10], default 0.0)

Type:
float

air_speed_max

Top speed while airborne (in [0, 100], default 0.0)

Type:
float

air_speed_min

Lowest speed while airborne, expressed relative to peak speed (in [0, 1], default 0.0)

Type:
float

bank

Degree of roll about the velocity vector during turns (in [0, 2], default 0.0)

Type:
float

health

Starting health value assigned at birth (in [0, 100], default 0.0)

Type:
float

height

Boid height given relative to particle size (in [0, 2], default 0.0)

Type:
float

land_acc_max

Top acceleration while grounded, expressed relative to peak speed (in [0, 1], default 0.0)

Type:
float

land_ave_max

Top angular velocity while grounded, expressed relative to 180 degrees (in [0, 1], default 0.0)

Type:
float

land_jump_speed

Highest speed allowed for a jump (in [0, 100], default 0.0)

Type:
float

land_personal_space

Personal-space radius on land, given as a percentage of particle size (in [0, 10], default 0.0)

Type:
float

land_smooth

Degree of smoothing applied as boids touch down (in [0, 10], default 0.0)

Type:
float

land_speed_max

Top speed while grounded (in [0, 100], default 0.0)

Type:
float

land_stick_force

Minimum force needed before it begins influencing a grounded boid (in [0, 1000], default 0.0)

Type:
float

pitch

Degree of roll about the side vector (in [0, 2], default 0.0)

Type:
float

range

Greatest range over which a boid may launch an attack (in [0, 100], default 0.0)

Type:
float

states

(default None, readonly)

Type:
bpy_prop_collection[BoidState]

strength

Peak damage inflicted per second during an attack (in [0, 100], default 0.0)

Type:
float

use_climb

Allow boids to climb goal objects (default False)

Type:
bool

use_flight

Allow boids to move in air (default False)

Type:
bool

use_land

Allow boids to move on land (default False)

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

| ParticleSettings.boids | |

## BoidState(bpy_struct)

### BoidState(bpy_struct)

base class — bpy_struct

class bpy.types.BoidState(bpy_struct)

A behavioral state used by the boid simulation

active_boid_rule

(readonly)

Type:
BoidRule

active_boid_rule_index

(in [0, inf], default 0)

Type:
int

falloff

(in [0, 10], default 0.0)

Type:
float

name

Boid state name (default "", never None)

Type:
str

rule_fuzzy

(in [0, 1], default 0.0)

Type:
float

rules

(default None, readonly)

Type:
bpy_prop_collection[BoidRule]

ruleset_type

Method by which the listed rules are processed (default 'FUZZY')

- FUZZY
Fuzzy – Rules are gone through top to bottom (only the first rule which effect is above fuzziness threshold is evaluated).

- RANDOM
Random – A random rule is selected for each boid.

- AVERAGE
Average – All rules are averaged.

Type:
Literal['FUZZY', 'RANDOM', 'AVERAGE']

volume

(in [0, 100], default 0.0)

Type:
float

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

| BoidSettings.states | |
