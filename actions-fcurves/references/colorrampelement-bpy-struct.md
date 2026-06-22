# Colorrampelement Bpy Struct, Colorrampelements Bpy Prop Collection, Consoleline Bpy Struct, Constraint Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ColorRampElement(bpy_struct); ColorRampElements(bpy_prop_collection); ConsoleLine(bpy_struct); Constraint(bpy_struct); ConstraintTarget(bpy_struct); ConstraintTargetBone(bpy_struct); CopyLocationConstraint(Constraint); CopyRotationConstraint(Constraint); CopyScaleConstraint(Constraint).

## ColorRampElement(bpy_struct)

### ColorRampElement(bpy_struct)

base class — bpy_struct

class bpy.types. ColorRampElement ( bpy_struct )

A stop that places a color at a specific position along the color ramp

alpha

Choose the alpha of the selected color stop (in [0, inf], default 0.0)

Type :

float

color

Choose the color of the selected color stop (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

position

Choose where the selected color stop sits (in [0, 1], default 0.0)

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

| ColorRamp.elements ColorRampElements.new | ColorRampElements.remove |

## ColorRampElements(bpy_prop_collection)

### ColorRampElements(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. ColorRampElements ( bpy_prop_collection )

A group holding the Color Ramp Elements

new ( position )

Insert a fresh element into the Color Ramp

Parameters :

position ( float ) – Position, Where along the ramp the element goes (in [0, 1])

Returns :

The element that was added

Return type :

ColorRampElement

remove ( element )

Take an element back out of the Color Ramp

Parameters :

element (ColorRampElement) – Element to remove (never None)

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

| ColorRamp.elements | |

## ConsoleLine(bpy_struct)

### ConsoleLine(bpy_struct)

base class — bpy_struct

class bpy.types. ConsoleLine ( bpy_struct )

An input line belonging to the interactive console.

body

The line's text content (default “”, never None)

Type :

str

current_character

(in [-inf, inf], default 0)

Type :

int

type

Kind of console line when shown in the scrollback (default 'OUTPUT' )

Type :

Literal[‘OUTPUT’, ‘INPUT’, ‘INFO’, ‘ERROR’]

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

| SpaceConsole.history | SpaceConsole.scrollback |

## Constraint(bpy_struct)

### Constraint(bpy_struct)

base class — bpy_struct

subclasses —
ActionConstraint, ArmatureConstraint, CameraSolverConstraint, ChildOfConstraint, ClampToConstraint, CopyLocationConstraint, CopyRotationConstraint, CopyScaleConstraint, CopyTransformsConstraint, DampedTrackConstraint, FloorConstraint, FollowPathConstraint, FollowTrackConstraint, GeometryAttributeConstraint, KinematicConstraint, LimitDistanceConstraint, LimitLocationConstraint, LimitRotationConstraint, LimitScaleConstraint, LockedTrackConstraint, MaintainVolumeConstraint, ObjectSolverConstraint, PivotConstraint, ShrinkwrapConstraint, SplineIKConstraint, StretchToConstraint, TrackToConstraint, TransformCacheConstraint, TransformConstraint

class bpy.types. Constraint ( bpy_struct )

A constraint that alters how objects and bones are transformed.

active

Marks this constraint as the one currently being edited (default False)

Type :

bool

enabled

Make use of what this constraint computes (default True)

Type :

bool

error_location

How much positional error remains, in Blender space units, for constraints that act on position (in [-inf, inf], default 0.0, readonly)

Type :

float

error_rotation

How much rotational error remains, in radians, for constraints that act on orientation (in [-inf, inf], default 0.0, readonly)

Type :

float

influence

How strongly the constraint weighs in on the final result (in [0, 1], default 0.0)

Type :

float

is_override_data

Within a local override object, indicates whether the constraint is inherited from the linked reference object or is local to the override (default True, readonly)

Type :

bool

is_valid

Whether the constraint is configured correctly and able to be evaluated (default True, readonly)

Type :

bool

mute

Turn the constraint on or off (default False)

Type :

bool

name

Name of the constraint (default “”, never None)

Type :

str

owner_space

Coordinate space in which the owner is evaluated (default 'WORLD' )

- WORLD
World Space – The constraint is applied relative to the world coordinate system.

- CUSTOM
Custom Space – The constraint is applied in local space of a custom object/bone/vertex group.

- POSE
Pose Space – The constraint is applied in Pose Space, the object transformation is ignored.

- `LOCAL_WITH_PARENT`
Local With Parent – The constraint is applied relative to the rest pose local coordinate system of the bone, thus including the parent-induced transformation.

- LOCAL
Local Space – The constraint is applied relative to the local coordinate system of the object.

Type :

Literal[‘WORLD’, ‘CUSTOM’, ‘POSE’, ‘`LOCAL_WITH_PARENT`’, ‘LOCAL’]

show_expanded

Whether the constraint's panel is unfolded in the UI (default False)

Type :

bool

space_object

Object for Custom Space

Type :

Object

space_subtarget

Armature bone, mesh or lattice vertex group, … (default “”, never None)

Type :

str

target_space

Coordinate space in which the target is evaluated (default 'WORLD' )

- WORLD
World Space – The transformation of the target is evaluated relative to the world coordinate system.

- CUSTOM
Custom Space – The transformation of the target is evaluated relative to a custom object/bone/vertex group.

- POSE
Pose Space – The transformation of the target is only evaluated in the Pose Space, the target armature object transformation is ignored.

- `LOCAL_WITH_PARENT`
Local With Parent – The transformation of the target bone is evaluated relative to its rest pose local coordinate system, thus including the parent-induced transformation.

- LOCAL
Local Space – The transformation of the target is evaluated relative to its local coordinate system.

- `LOCAL_OWNER_ORIENT`
Local Space (Owner Orientation) – The transformation of the target bone is evaluated relative to its local coordinate system, followed by a correction for the difference in target and owner rest pose orientations. When applied as local transform to the owner produces the same global motion as the target if the parents are still in rest pose..

Type :

Literal[‘WORLD’, ‘CUSTOM’, ‘POSE’, ‘`LOCAL_WITH_PARENT`’, ‘LOCAL’, ‘`LOCAL_OWNER_ORIENT`’]

type

(default '`CAMERA_SOLVER`' , readonly)

Type :

Literal[Constraint Type Items]

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

| Object.constraints ObjectConstraints.active ObjectConstraints.copy ObjectConstraints.copy ObjectConstraints.new ObjectConstraints.remove Panel.custom_data | PoseBone.constraints PoseBoneConstraints.active PoseBoneConstraints.copy PoseBoneConstraints.copy PoseBoneConstraints.new PoseBoneConstraints.remove UILayout.template_constraint_header |

## ConstraintTarget(bpy_struct)

### ConstraintTarget(bpy_struct)

base class — bpy_struct

class bpy.types. ConstraintTarget ( bpy_struct )

One of the targets used by a constraint that drives from several at once.

subtarget

Names a vertex group on a mesh or lattice, or a bone on an armature, … (default "", never None)

Type :

str

target

The object pointed at as a target

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

## ConstraintTargetBone(bpy_struct)

### ConstraintTargetBone(bpy_struct)

base class — bpy_struct

class bpy.types. ConstraintTargetBone ( bpy_struct )

A single bone serving as one target for a multi-target constraint.

subtarget

Which bone of the target armature is used (default "", never None)

Type :

str

target

The armature that supplies the bone

Type :

Object

weight

How strongly this bone is mixed in, on a 0-to-1 scale (in [0, 1], default 0.0)

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

| ArmatureConstraint.targets ArmatureConstraintTargets.new | ArmatureConstraintTargets.remove |

## CopyLocationConstraint(Constraint)

### CopyLocationConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. CopyLocationConstraint ( Constraint )

Mirror the target's location onto the owner.

head_tail

Where along the bone the target sits, with 0 at the Head and 1 at the Tail (in [0, 1], default 0.0)

Type :

float

invert_x

Flip the sign of the X location (default False)

Type :

bool

invert_y

Flip the sign of the Y location (default False)

Type :

bool

invert_z

Flip the sign of the Z location (default False)

Type :

bool

subtarget

Names a vertex group on a mesh or lattice, or a bone on an armature, … (default "", never None)

Type :

str

target

The object pointed at as a target

Type :

Object

use_bbone_shape

Trace the curve of the B-Bone segments when working out the Head/Tail position (default False)

Type :

bool

use_offset

Stack the copied location on top of the owner's own location (default False)

Type :

bool

use_x

Pull in the target's X location (default False)

Type :

bool

use_y

Pull in the target's Y location (default False)

Type :

bool

use_z

Pull in the target's Z location (default False)

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

## CopyRotationConstraint(Constraint)

### CopyRotationConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. CopyRotationConstraint ( Constraint )

Mirror the target's rotation onto the owner.

euler_order

Choose the euler rotation order outright (default 'AUTO' )

- AUTO
Default – Euler taken in the default ordering.

- XYZ
XYZ Euler – Euler taken in XYZ order.

- XZY
XZY Euler – Euler taken in XZY order.

- YXZ
YXZ Euler – Euler taken in YXZ order.

- YZX
YZX Euler – Euler taken in YZX order.

- ZXY
ZXY Euler – Euler taken in ZXY order.

- ZYX
ZYX Euler – Euler taken in ZYX order.

Type :

Literal['AUTO', 'XYZ', 'XZY', 'YXZ', 'YZX', 'ZXY', 'ZYX']

invert_x

Flip the sign of the X rotation (default False)

Type :

bool

invert_y

Flip the sign of the Y rotation (default False)

Type :

bool

invert_z

Flip the sign of the Z rotation (default False)

Type :

bool

mix_mode

Choose the way the copied rotation blends with the one already present (default 'REPLACE' )

- REPLACE
Replace – Swap the copied rotation in for the original.

- ADD
Add – Sum the euler components of both rotations.

- BEFORE
Before Original – Put the copied rotation first, treating the target as though it were a parent.

- AFTER
After Original – Put the copied rotation last, treating the target as though it were a child.

- OFFSET
Offset (Legacy) – Mix the rotations the way the old Offset checkbox did. Tends to fall apart once more than one axis rotates..

Type :

Literal['REPLACE', 'ADD', 'BEFORE', 'AFTER', 'OFFSET']

subtarget

Names a vertex group on a mesh or lattice, or a bone on an armature, … (default "", never None)

Type :

str

target

The object pointed at as a target

Type :

Object

use_offset

DEPRECATED: Stack the owner's own rotation onto the copied rotation (default False)

Type :

bool

use_x

Pull in the target's X rotation (default False)

Type :

bool

use_y

Pull in the target's Y rotation (default False)

Type :

bool

use_z

Pull in the target's Z rotation (default False)

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

## CopyScaleConstraint(Constraint)

### CopyScaleConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. CopyScaleConstraint ( Constraint )

Mirror the target's scale onto the owner.

power

Take the target's scale and raise it to the given exponent (in [-inf, inf], default 1.0)

Type :

float

subtarget

Names a vertex group on a mesh or lattice, or a bone on an armature, … (default "", never None)

Type :

str

target

The object pointed at as a target

Type :

Object

use_add

Blend scale by adding rather than multiplying (kept for 2.7 compatibility) (default True)

Type :

bool

use_make_uniform

Spread the copied volume change evenly over the owner's three axes (default False)

Type :

bool

use_offset

Fold the owner's own scale together with the copied scale (default False)

Type :

bool

use_x

Pull in the target's X scale (default False)

Type :

bool

use_y

Pull in the target's Y scale (default False)

Type :

bool

use_z

Pull in the target's Z scale (default False)

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
