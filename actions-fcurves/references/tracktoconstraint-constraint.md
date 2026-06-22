# Tracktoconstraint Constraint, Transformcacheconstraint Constraint, Transformconstraint Constraint, Transformorientation Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: TrackToConstraint(Constraint); TransformCacheConstraint(Constraint); TransformConstraint(Constraint); TransformOrientation(bpy_struct); TransformOrientationSlot(bpy_struct); UIPieMenu(bpy_struct); UIPopover(bpy_struct); UIPopupMenu(bpy_struct); UnifiedPaintSettings(bpy_struct).

## TrackToConstraint(Constraint)

### TrackToConstraint(Constraint) 

base classes — bpy_struct, Constraint

class bpy.types. TrackToConstraint ( Constraint ) 

Points the constrained object so it faces the target.

head_tail 

Position along the bone’s length to target: 0 is Head, 1 is Tail (in [0, 1], default 0.0)

Type :

float

subtarget 

Armature bone, mesh or lattice vertex group, … (default “”, never None)

Type :

str

target 

Target object

Type :

Object

track_axis 

Which axis aims at the target object (default '`TRACK_X`' )

Type :

Literal[‘`TRACK_X`’, ‘`TRACK_Y`’, ‘`TRACK_Z`’, ‘`TRACK_NEGATIVE_X`’, ‘`TRACK_NEGATIVE_Y`’, ‘`TRACK_NEGATIVE_Z`’]

up_axis 

Which axis aims upward (default '`UP_X`' )

Type :

Literal[‘`UP_X`’, ‘`UP_Y`’, ‘`UP_Z`’]

use_bbone_shape 

Trace the shape of the B-Bone segments when computing the Head/Tail position (default False)

Type :

bool

use_target_z 

Constrain the Up direction using the target’s Z axis rather than the World Z axis (default False)

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

## TransformCacheConstraint(Constraint)

### TransformCacheConstraint(Constraint) 

base classes — bpy_struct, Constraint

class bpy.types. TransformCacheConstraint ( Constraint ) 

Reads a transform out of an external file.

cache_file 

Type :

CacheFile

object_path 

Path of the object inside the Alembic archive whose transform matrix is read (default “”, never None)

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

| bpy_struct.id_data Constraint.name Constraint.type Constraint.is_override_data Constraint.owner_space Constraint.target_space Constraint.space_object Constraint.space_subtarget | Constraint.mute Constraint.enabled Constraint.show_expanded Constraint.is_valid Constraint.active Constraint.influence Constraint.error_location Constraint.error_rotation |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Constraint.bl_rna_get_subclass Constraint.bl_rna_get_subclass_py |

## TransformConstraint(Constraint)

### TransformConstraint(Constraint) 

base classes — bpy_struct, Constraint

class bpy.types. TransformConstraint ( Constraint ) 

Maps the target’s transformations onto the object.

from_max_x 

Upper end of the X axis source range (in [-inf, inf], default 0.0)

Type :

float

from_max_x_rot 

Upper end of the X axis source range (in [-inf, inf], default 0.0)

Type :

float

from_max_x_scale 

Upper end of the X axis source range (in [-inf, inf], default 0.0)

Type :

float

from_max_y 

Upper end of the Y axis source range (in [-inf, inf], default 0.0)

Type :

float

from_max_y_rot 

Upper end of the Y axis source range (in [-inf, inf], default 0.0)

Type :

float

from_max_y_scale 

Upper end of the Y axis source range (in [-inf, inf], default 0.0)

Type :

float

from_max_z 

Upper end of the Z axis source range (in [-inf, inf], default 0.0)

Type :

float

from_max_z_rot 

Upper end of the Z axis source range (in [-inf, inf], default 0.0)

Type :

float

from_max_z_scale 

Upper end of the Z axis source range (in [-inf, inf], default 0.0)

Type :

float

from_min_x 

Lower end of the X axis source range (in [-inf, inf], default 0.0)

Type :

float

from_min_x_rot 

Lower end of the X axis source range (in [-inf, inf], default 0.0)

Type :

float

from_min_x_scale 

Lower end of the X axis source range (in [-inf, inf], default 0.0)

Type :

float

from_min_y 

Lower end of the Y axis source range (in [-inf, inf], default 0.0)

Type :

float

from_min_y_rot 

Lower end of the Y axis source range (in [-inf, inf], default 0.0)

Type :

float

from_min_y_scale 

Lower end of the Y axis source range (in [-inf, inf], default 0.0)

Type :

float

from_min_z 

Lower end of the Z axis source range (in [-inf, inf], default 0.0)

Type :

float

from_min_z_rot 

Lower end of the Z axis source range (in [-inf, inf], default 0.0)

Type :

float

from_min_z_scale 

Lower end of the Z axis source range (in [-inf, inf], default 0.0)

Type :

float

from_rotation_mode 

Which kind of rotation channels to read from (default 'AUTO' )

Type :

Literal[Driver Target Rotation Mode Items]

map_from 

Which transformation type is taken from the target (default 'LOCATION' )

Type :

Literal[‘LOCATION’, ‘ROTATION’, ‘SCALE’]

map_to 

Which transformation type is driven on the constrained object (default 'LOCATION' )

Type :

Literal[‘LOCATION’, ‘ROTATION’, ‘SCALE’]

map_to_x_from 

Source axis feeding the constrained object’s X axis (default 'X' )

Type :

Literal[Axis Xyz Items]

map_to_y_from 

Source axis feeding the constrained object’s Y axis (default 'X' )

Type :

Literal[Axis Xyz Items]

map_to_z_from 

Source axis feeding the constrained object’s Z axis (default 'X' )

Type :

Literal[Axis Xyz Items]

mix_mode 

How the new location is blended with the original (default 'ADD' )

- REPLACE
Replace – Replace component values.

- ADD
Add – Add component values together.

Type :

Literal[‘REPLACE’, ‘ADD’]

mix_mode_rot 

How the new rotation is blended with the original (default 'ADD' )

- REPLACE
Replace – Replace component values.

- ADD
Add – Add component values together.

- BEFORE
Before Original – Apply new rotation before original, as if it was on a parent.

- AFTER
After Original – Apply new rotation after original, as if it was on a child.

Type :

Literal[‘REPLACE’, ‘ADD’, ‘BEFORE’, ‘AFTER’]

mix_mode_scale 

How the new scale is blended with the original (default 'REPLACE' )

- REPLACE
Replace – Replace component values.

- MULTIPLY
Multiply – Multiply component values together.

Type :

Literal[‘REPLACE’, ‘MULTIPLY’]

subtarget 

Armature bone, mesh or lattice vertex group, … (default “”, never None)

Type :

str

target 

Target object

Type :

Object

to_euler_order 

Force a particular euler rotation order on the output (default 'AUTO' )

- AUTO
Default – Euler using the default rotation order.

- XYZ
XYZ Euler – Euler using the XYZ rotation order.

- XZY
XZY Euler – Euler using the XZY rotation order.

- YXZ
YXZ Euler – Euler using the YXZ rotation order.

- YZX
YZX Euler – Euler using the YZX rotation order.

- ZXY
ZXY Euler – Euler using the ZXY rotation order.

- ZYX
ZYX Euler – Euler using the ZYX rotation order.

Type :

Literal[‘AUTO’, ‘XYZ’, ‘XZY’, ‘YXZ’, ‘YZX’, ‘ZXY’, ‘ZYX’]

to_max_x 

Upper end of the X axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_max_x_rot 

Upper end of the X axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_max_x_scale 

Upper end of the X axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_max_y 

Upper end of the Y axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_max_y_rot 

Upper end of the Y axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_max_y_scale 

Upper end of the Y axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_max_z 

Upper end of the Z axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_max_z_rot 

Upper end of the Z axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_max_z_scale 

Upper end of the Z axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_min_x 

Lower end of the X axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_min_x_rot 

Lower end of the X axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_min_x_scale 

Lower end of the X axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_min_y 

Lower end of the Y axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_min_y_rot 

Lower end of the Y axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_min_y_scale 

Lower end of the Y axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_min_z 

Lower end of the Z axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_min_z_rot 

Lower end of the Z axis destination range (in [-inf, inf], default 0.0)

Type :

float

to_min_z_scale 

Lower end of the Z axis destination range (in [-inf, inf], default 0.0)

Type :

float

use_motion_extrapolate 

Allow the ranges to extrapolate beyond their limits (default False)

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

## TransformOrientation(bpy_struct)

### TransformOrientation(bpy_struct) 

base class — bpy_struct

class bpy.types. TransformOrientation ( bpy_struct ) 

matrix 

(multi-dimensional array of 3 * 3 items, in [-inf, inf], default ((0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0)))

Type :

mathutils.Matrix

name 

Name given to the custom transform orientation (default “”, never None)

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

| TransformOrientationSlot.custom_orientation | |

## TransformOrientationSlot(bpy_struct)

### TransformOrientationSlot(bpy_struct) 

base class — bpy_struct

class bpy.types. TransformOrientationSlot ( bpy_struct ) 

custom_orientation 

(readonly)

Type :

TransformOrientation

type 

Orientation used for transforms (default 'GLOBAL' )

Type :

Literal[Transform Orientation Items]

use 

Take the scene orientation rather than a custom one (default False)

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

| Scene.transform_orientation_slots | |

## UIPieMenu(bpy_struct)

### UIPieMenu(bpy_struct)

base class — bpy_struct

class bpy.types. UIPieMenu ( bpy_struct )

layout

(readonly)

Type :

UILayout

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

| WindowManager.piemenu_begin__internal | WindowManager.piemenu_end__internal |

## UIPopover(bpy_struct)

### UIPopover(bpy_struct)

base class — bpy_struct

class bpy.types. UIPopover ( bpy_struct )

layout

(readonly)

Type :

UILayout

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

| WindowManager.popover_begin__internal | WindowManager.popover_end__internal |

## UIPopupMenu(bpy_struct)

### UIPopupMenu(bpy_struct)

base class — bpy_struct

class bpy.types. UIPopupMenu ( bpy_struct )

layout

(readonly)

Type :

UILayout

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

| WindowManager.popmenu_begin__internal | WindowManager.popmenu_end__internal |

## UnifiedPaintSettings(bpy_struct)

### UnifiedPaintSettings(bpy_struct)

base class — bpy_struct

class bpy.types. UnifiedPaintSettings ( bpy_struct )

Values that take the place of the matching settings on the currently active brush.

color

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

hue_jitter

How much random variation is applied to the hue (in [0, 1], default 0.0)

Type :

float

input_samples

Count of input samples blended together to even out the brush stroke (in [1, 64], default 1)

Type :

int

saturation_jitter

How much random variation is applied to the saturation (in [0, 1], default 0.0)

Type :

float

secondary_color

(array of 3 items, in [0, 1], default (1.0, 1.0, 1.0))

Type :

mathutils.Color

size

Brush diameter (in [1, 10000], default 100)

Type :

int

strength

How strong the brush effect is once applied (in [0, 10], default 0.5)

Type :

float

unprojected_size

Brush diameter expressed in Blender units (in [0.001, inf], default 0.58)

Type :

float

use_color_jitter

Add random variation to the brush color (default False)

Type :

bool

use_locked_size

Whether brush size is gauged against the view or against the scene (default 'VIEW' )

- VIEW
View – Measure brush size relative to the view.

- SCENE
Scene – Measure brush size relative to the scene.

Type :

Literal[‘VIEW’, ‘SCENE’]

use_random_press_hue

Let pen pressure drive the amount of randomness (default False)

Type :

bool

use_random_press_sat

Let pen pressure drive the amount of randomness (default False)

Type :

bool

use_random_press_val

Let pen pressure drive the amount of randomness (default False)

Type :

bool

use_stroke_random_hue

Apply the randomness once per stroke (default False)

Type :

bool

use_stroke_random_sat

Apply the randomness once per stroke (default False)

Type :

bool

use_stroke_random_val

Apply the randomness once per stroke (default False)

Type :

bool

use_unified_color

Share one color across all brushes rather than keeping it per-brush (default True)

Type :

bool

use_unified_input_samples

Share one input-samples value across all brushes rather than keeping it per-brush (default False)

Type :

bool

use_unified_size

Share one size across all brushes rather than keeping it per-brush (default True)

Type :

bool

use_unified_strength

Share one strength across all brushes rather than keeping it per-brush (default False)

Type :

bool

use_unified_weight

Share one weight across all brushes rather than keeping it per-brush (default False)

Type :

bool

value_jitter

How much random variation is applied to the value (in [0, 1], default 0.0)

Type :

float

weight

Weight to write into vertex groups (in [0, 1], default 0.5)

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

| Paint.unified_paint_settings | |
