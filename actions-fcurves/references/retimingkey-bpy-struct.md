# Retimingkey Bpy Struct, Retimingkeys Bpy Prop Collection, Rigidbodyconstraint Bpy Struct, Rigidbodyobject Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: RetimingKey(bpy_struct); RetimingKeys(bpy_prop_collection); RigidBodyConstraint(bpy_struct); RigidBodyObject(bpy_struct); RigidBodyWorld(bpy_struct); SceneObjects(bpy_prop_collection); Screen(ID); ScriptDirectory(bpy_struct).

## RetimingKey(bpy_struct)

### RetimingKey(bpy_struct)

base class — bpy_struct

class bpy.types. RetimingKey ( bpy_struct )

A key tied to a specific frame that you can slide to alter playback speed

timeline_frame

Where the retiming key sits along the timeline (in [-inf, inf], default 0)

Type :

int

remove ( )

Delete this retiming key

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

| ImageStrip.retiming_keys MovieStrip.retiming_keys RetimingKeys.add | SceneStrip.retiming_keys SoundStrip.retiming_keys |

## RetimingKeys(bpy_prop_collection)

### RetimingKeys(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. RetimingKeys ( bpy_prop_collection )

Collection of RetimingKey

add ( * , timeline_frame = 0 )

Add retiming key

Parameters :

timeline_frame ( int ) – Timeline Frame, (in [-1048574, 1048574], optional)

Returns :

New RetimingKey

Return type :

RetimingKey

reset ( )

Clear every retiming key

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

| ImageStrip.retiming_keys MovieStrip.retiming_keys | SceneStrip.retiming_keys SoundStrip.retiming_keys |

## RigidBodyConstraint(bpy_struct)

### RigidBodyConstraint(bpy_struct)

base class — bpy_struct

class bpy.types. RigidBodyConstraint ( bpy_struct )

A constraint acting on Objects taking part in a Rigid Body Simulation

breaking_threshold

Impulse level the constraint has to hit before it breaks (in [0, inf], default 10.0)

Type :

float

disable_collisions

Turn off collisions between the two constrained rigid bodies (default False)

Type :

bool

enabled

Enable this constraint (default False)

Type :

bool

limit_ang_x_lower

Lower bound on rotation about the X axis (in [-6.28319, 6.28319], default -0.785398)

Type :

float

limit_ang_x_upper

Upper bound on rotation about the X axis (in [-6.28319, 6.28319], default 0.785398)

Type :

float

limit_ang_y_lower

Lower bound on rotation about the Y axis (in [-6.28319, 6.28319], default -0.785398)

Type :

float

limit_ang_y_upper

Upper bound on rotation about the Y axis (in [-6.28319, 6.28319], default 0.785398)

Type :

float

limit_ang_z_lower

Lower bound on rotation about the Z axis (in [-6.28319, 6.28319], default -0.785398)

Type :

float

limit_ang_z_upper

Upper bound on rotation about the Z axis (in [-6.28319, 6.28319], default 0.785398)

Type :

float

limit_lin_x_lower

Lower bound on translation along the X axis (in [-inf, inf], default -1.0)

Type :

float

limit_lin_x_upper

Upper bound on translation along the X axis (in [-inf, inf], default 1.0)

Type :

float

limit_lin_y_lower

Lower bound on translation along the Y axis (in [-inf, inf], default -1.0)

Type :

float

limit_lin_y_upper

Upper bound on translation along the Y axis (in [-inf, inf], default 1.0)

Type :

float

limit_lin_z_lower

Lower bound on translation along the Z axis (in [-inf, inf], default -1.0)

Type :

float

limit_lin_z_upper

Upper bound on translation along the Z axis (in [-inf, inf], default 1.0)

Type :

float

motor_ang_max_impulse

Maximum angular motor impulse (in [0, inf], default 1.0)

Type :

float

motor_ang_target_velocity

Target angular motor velocity (in [-inf, inf], default 1.0)

Type :

float

motor_lin_max_impulse

Maximum linear motor impulse (in [0, inf], default 1.0)

Type :

float

motor_lin_target_velocity

Target linear motor velocity (in [-inf, inf], default 1.0)

Type :

float

object1

The first Rigid Body Object held by the constraint

Type :

Object

object2

The second Rigid Body Object held by the constraint

Type :

Object

solver_iterations

How many constraint solver iterations run each simulation step; raising it improves accuracy at the expense of speed (in [1, 1000], default 10)

Type :

int

spring_damping_ang_x

Damping on the X rotational axis (in [0, inf], default 0.5)

Type :

float

spring_damping_ang_y

Damping on the Y rotational axis (in [0, inf], default 0.5)

Type :

float

spring_damping_ang_z

Damping on the Z rotational axis (in [0, inf], default 0.5)

Type :

float

spring_damping_x

Damping on the X axis (in [0, inf], default 0.5)

Type :

float

spring_damping_y

Damping on the Y axis (in [0, inf], default 0.5)

Type :

float

spring_damping_z

Damping on the Z axis (in [0, inf], default 0.5)

Type :

float

spring_stiffness_ang_x

Stiffness on the X rotational axis (in [0, inf], default 10.0)

Type :

float

spring_stiffness_ang_y

Stiffness on the Y rotational axis (in [0, inf], default 10.0)

Type :

float

spring_stiffness_ang_z

Stiffness on the Z rotational axis (in [0, inf], default 10.0)

Type :

float

spring_stiffness_x

Stiffness on the X axis (in [0, inf], default 10.0)

Type :

float

spring_stiffness_y

Stiffness on the Y axis (in [0, inf], default 10.0)

Type :

float

spring_stiffness_z

Stiffness on the Z axis (in [0, inf], default 10.0)

Type :

float

spring_type

Selects which spring implementation is applied (default 'SPRING1' )

- SPRING1
Blender 2.7 – The spring implementation that shipped in Blender 2.7. Damping is capped at 1.0.

- SPRING2
Blender 2.8 – The newer implementation introduced in 2.8.

Type :

Literal[‘SPRING1’, ‘SPRING2’]

type

Type of Rigid Body Constraint (default 'POINT' )

Type :

Literal[Rigidbody Constraint Type Items]

use_breaking

Allow the constraint to break once an impulse exceeds the threshold (default False)

Type :

bool

use_limit_ang_x

Limit rotation around X axis (default False)

Type :

bool

use_limit_ang_y

Limit rotation around Y axis (default False)

Type :

bool

use_limit_ang_z

Limit rotation around Z axis (default False)

Type :

bool

use_limit_lin_x

Limit translation on X axis (default False)

Type :

bool

use_limit_lin_y

Limit translation on Y axis (default False)

Type :

bool

use_limit_lin_z

Limit translation on Z axis (default False)

Type :

bool

use_motor_ang

Enable angular motor (default False)

Type :

bool

use_motor_lin

Enable linear motor (default False)

Type :

bool

use_override_solver_iterations

Set a custom solver iteration count just for this constraint (default False)

Type :

bool

use_spring_ang_x

Enable spring on X rotational axis (default False)

Type :

bool

use_spring_ang_y

Enable spring on Y rotational axis (default False)

Type :

bool

use_spring_ang_z

Enable spring on Z rotational axis (default False)

Type :

bool

use_spring_x

Enable spring on X axis (default False)

Type :

bool

use_spring_y

Enable spring on Y axis (default False)

Type :

bool

use_spring_z

Enable spring on Z axis (default False)

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

- default (type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Object.rigid_body_constraint | |

## RigidBodyObject(bpy_struct)

### RigidBodyObject(bpy_struct)

base class — bpy_struct

class bpy.types. RigidBodyObject ( bpy_struct )

Configuration for an object taking part in a Rigid Body Simulation

angular_damping

How much angular velocity bleeds away over time (in [0, 1], default 0.1)

Type :

float

collision_collections

Collision collections this rigid body is part of (array of 20 items, default (False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False))

Type :

bpy_prop_array[bool]

collision_margin

Distance band near the surface within which collisions still register; non-zero values give the best results (in [0, 1], default 0.04)

Type :

float

collision_shape

Shape used for the object's collisions in Rigid Body Simulations (default 'BOX' )

Type :

Literal[Rigidbody Object Shape Items]

deactivate_angular_velocity

Angular velocity under which the simulation stops simulating the object (in [0, inf], default 0.5)

Type :

float

deactivate_linear_velocity

Linear velocity under which the simulation stops simulating the object (in [0, inf], default 0.4)

Type :

float

enabled

The rigid body takes an active part in the simulation (default True)

Type :

bool

friction

How strongly the object resists movement (in [0, inf], default 0.5)

Type :

float

kinematic

Let the animation system drive the rigid body (default False)

Type :

bool

linear_damping

How much linear velocity bleeds away over time (in [0, 1], default 0.04)

Type :

float

mass

The object's 'weight', independent of gravity (in [0.001, inf], default 1.0)

Type :

float

mesh_source

Which mesh the collision shape is built from (default 'BASE' )

- BASE
Base – Base mesh.

- DEFORM
Deform – Deformations such as shape keys and deform modifiers.

- FINAL
Final – All modifiers.

Type :

Literal[‘BASE’, ‘DEFORM’, ‘FINAL’]

restitution

How readily the object bounces off another after a collision, where 0 means it stays put and 1 is perfectly elastic (in [0, inf], default 0.0)

Type :

float

type

The object's role within Rigid Body Simulations (default 'ACTIVE' )

Type :

Literal[Rigidbody Object Type Items]

use_deactivation

Let resting rigid bodies deactivate, which helps performance and stability though it can introduce glitches (default True)

Type :

bool

use_deform

The rigid body deforms during simulation (default False)

Type :

bool

use_margin

Apply a custom collision margin; some shapes then show a visible gap around them (default False)

Type :

bool

use_start_deactivated

Begin the simulation with the rigid body deactivated (default False)

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

- default (type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Object.rigid_body | |

## RigidBodyWorld(bpy_struct)

### RigidBodyWorld(bpy_struct)

base class — bpy_struct

class bpy.types. RigidBodyWorld ( bpy_struct )

A self-contained environment plus settings for a rigid body simulation

collection

Collection holding the objects that take part in this simulation

Type :

Collection

constraints

Collection holding the rigid body constraint objects

Type :

Collection

effector_weights

(readonly)

Type :

EffectorWeights

enabled

The simulation will be evaluated (default True)

Type :

bool

point_cache

(readonly, never None)

Type :

PointCache

solver_iterations

How many constraint solver iterations run each simulation step; raising it improves accuracy at the expense of speed (in [1, 1000], default 10)

Type :

int

substeps_per_frame

How many simulation steps run per frame; raising it improves accuracy at the expense of speed (in [1, 32767], default 10)

Type :

int

time_scale

Adjust how fast the simulation runs (in [0, 100], default 1.0)

Type :

float

use_split_impulse

Cut down the extra velocity that accumulates when objects collide; use it sparingly since it slightly lowers simulation stability (default False)

Type :

bool

convex_sweep_test ( object , start , end )

Sweep test convex rigidbody against the current rigidbody world

Parameters :

- object (Object) – Rigidbody object with a convex collision shape (never None)

- start (mathutils.Vector) – (array of 3 items, in [-inf, inf])

- end (mathutils.Vector) – (array of 3 items, in [-inf, inf])

Returns :

object_location , The hit location of this sweep test, mathutils.Vector

hitpoint , The hit location of this sweep test, mathutils.Vector

normal , The face normal at the sweep test hit location, mathutils.Vector

has_hit , If the function has found collision point, value is 1, otherwise 0, int

Return type :

tuple[mathutils.Vector, mathutils.Vector, mathutils.Vector, int]

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

| Scene.rigidbody_world | |

## SceneObjects(bpy_prop_collection)

### SceneObjects(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. SceneObjects ( bpy_prop_collection )

Every object in the scene

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

| Scene.objects | |

## Screen(ID)

### Screen(ID)

base classes — bpy_struct, ID

class bpy.types. Screen ( ID )

A Screen data-block that lays out the areas inside a window

areas

The areas this screen is split into (default None, readonly)

Type :

bpy_prop_collection[Area]

is_animation_playing

Animation playback is active (default False, readonly)

Type :

bool

is_scrubbing

True while the user scrubs through time (default False, readonly)

Type :

bool

is_temporary

(default False, readonly)

Type :

bool

show_fullscreen

One area is maximized and fills this screen (default False, readonly)

Type :

bool

show_statusbar

Show status bar (default True)

Type :

bool

use_follow

Track the current frame across editors (default False)

Type :

bool

use_play_3d_editors

(default False)

Type :

bool

use_play_animation_editors

(default False)

Type :

bool

use_play_clip_editors

(default False)

Type :

bool

use_play_image_editors

(default False)

Type :

bool

use_play_node_editors

(default False)

Type :

bool

use_play_properties_editors

(default False)

Type :

bool

use_play_sequence_editors

(default False)

Type :

bool

use_play_spreadsheet_editors

(default False)

Type :

bool

use_play_top_left_3d_editor

(default False)

Type :

bool

statusbar_info ( )

statusbar_info

Returns :

Status Bar Info, (never None)

Return type :

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| BlendData.screens Context.screen | Window.screen WorkSpace.screens |

## ScriptDirectory(bpy_struct)

### ScriptDirectory(bpy_struct)

base class — bpy_struct

class bpy.types. ScriptDirectory ( bpy_struct )

directory

A secondary scripts location laid out like the default one, with startup, add-ons, modules, and presets sub-directories; a restart is needed for it to take effect (default “”, never None)

Type :

str

name

Label that identifies this Python scripts directory (default “”, never None)

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

| PreferencesFilePaths.script_directories ScriptDirectoryCollection.new | ScriptDirectoryCollection.remove |
