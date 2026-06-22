# Curveprofilepoints Bpy Prop Collection, Curveslice Bpy Struct, Curvesmodifier Stripmodifier, Curvesplines Bpy Prop Collection ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: CurveProfilePoints(bpy_prop_collection); CurveSlice(bpy_struct); CurvesModifier(StripModifier); CurveSplines(bpy_prop_collection); CurvesSculpt(Paint); DampedTrackConstraint(Constraint); DepsgraphUpdate(bpy_struct); DisplaySafeAreas(bpy_struct); Driver(bpy_struct); DriverTarget(bpy_struct); DriverVariable(bpy_struct).

## CurveProfilePoints(bpy_prop_collection)

### CurveProfilePoints(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. CurveProfilePoints ( bpy_prop_collection )

Collection of Profile Points

add ( x , y )

Add point to the profile

Parameters :

- x ( float ) – X Position, X Position for new point (in [-inf, inf])

- y ( float ) – Y Position, Y Position for new point (in [-inf, inf])

Returns :

New point

Return type :

CurveProfilePoint

remove ( point )

Delete point from the profile

Parameters :

point (CurveProfilePoint) – Point to remove (never None)

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

| CurveProfile.points | |

## CurveSlice(bpy_struct)

### CurveSlice(bpy_struct)

base class — bpy_struct

class bpy.types. CurveSlice ( bpy_struct )

One curve drawn from a curves data-block.

first_point_index

Where this curve's first control point lives in the index (in [0, inf], default 0, readonly)

Type :

int

index

Index of this curve (in [0, inf], default 0, readonly)

Type :

int

points

Control points of the curve (default None, readonly)

Type :

bpy_prop_collection[CurvePoint]

points_length

How many control points the curve holds (in [0, inf], default 0, readonly)

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

| Curves.curves | |

## CurvesModifier(StripModifier)

### CurvesModifier(StripModifier)

base classes — bpy_struct, StripModifier

class bpy.types. CurvesModifier ( StripModifier )

An RGB-curves modifier applied to a sequence strip.

curve_mapping

(readonly)

Type :

CurveMapping

open_mask_input_panel

(default False)

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

| bpy_struct.id_data StripModifier.name StripModifier.type StripModifier.mute StripModifier.enable StripModifier.show_expanded | StripModifier.input_mask_type StripModifier.mask_time StripModifier.input_mask_strip StripModifier.input_mask_id StripModifier.is_active |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values StripModifier.bl_rna_get_subclass StripModifier.bl_rna_get_subclass_py |

## CurveSplines(bpy_prop_collection)

### CurveSplines(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. CurveSplines ( bpy_prop_collection )

Collection of curve splines

active

Active curve spline

Type :

Spline

new ( type )

Add a new spline to the curve

Parameters :

type ( Literal [ 'POLY' , 'BEZIER' , 'NURBS' ] ) – type for the new spline

Returns :

The newly created spline

Return type :

Spline

remove ( spline )

Remove a spline from a curve

Parameters :

spline (Spline) – The spline to remove (never None)

clear ( )

Remove all splines from a curve

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

| Curve.splines | |

## CurvesSculpt(Paint)

### CurvesSculpt(Paint)

base classes — bpy_struct, Paint

class bpy.types. CurvesSculpt ( Paint )

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

| ToolSettings.curves_sculpt | |

## DampedTrackConstraint(Constraint)

### DampedTrackConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. DampedTrackConstraint ( Constraint )

Aim at the target along the shortest rotational route.

head_tail

Where along the bone the target sits, with 0 at the Head and 1 at the Tail (in [0, 1], default 0.0)

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

track_axis

Which axis aims at the target object (default '`TRACK_X`' )

Type :

Literal['`TRACK_X`', '`TRACK_Y`', '`TRACK_Z`', '`TRACK_NEGATIVE_X`', '`TRACK_NEGATIVE_Y`', '`TRACK_NEGATIVE_Z`']

use_bbone_shape

Trace the curve of the B-Bone segments when working out the Head/Tail position (default False)

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

## DepsgraphUpdate(bpy_struct)

### DepsgraphUpdate(bpy_struct)

base class — bpy_struct

class bpy.types. DepsgraphUpdate ( bpy_struct )

Details about an ID that received an update

id

The data-block that changed (readonly)

Type :

ID

is_updated_geometry

Marks that the object’s geometry changed (default False, readonly)

Type :

bool

is_updated_shading

Marks that the object’s shading changed (default False, readonly)

Type :

bool

is_updated_transform

Marks that the object’s transform changed (default False, readonly)

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

| Depsgraph.updates | |

## DisplaySafeAreas(bpy_struct)

### DisplaySafeAreas(bpy_struct)

base class — bpy_struct

class bpy.types. DisplaySafeAreas ( bpy_struct )

The safe-area margins applied in the 3D view and the sequencer

action

Margin reserved for general elements (array of 2 items, in [0, 1], default (0.035, 0.035))

Type :

mathutils.Vector

action_center

Margin reserved for general elements under a different aspect ratio (array of 2 items, in [0, 1], default (0.15, 0.05))

Type :

mathutils.Vector

title

Margin reserved for text and graphics (array of 2 items, in [0, 1], default (0.1, 0.05))

Type :

mathutils.Vector

title_center

Margin reserved for text and graphics under a different aspect ratio (array of 2 items, in [0, 1], default (0.175, 0.05))

Type :

mathutils.Vector

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

| Scene.safe_areas | |

## Driver(bpy_struct)

### Driver(bpy_struct)

base class — bpy_struct

class bpy.types. Driver ( bpy_struct )

Sets a property’s value by deriving it from an outside value

expression

The expression evaluated for a Scripted Expression (default “”, never None)

Type :

str

is_simple_expression

The scripted expression is simple enough to run without the full Python interpreter (default False, readonly)

Type :

bool

is_valid

A past evaluation of the driver failed, so it ought to be passed over (default True)

Type :

bool

type

Which kind of driver this is (default 'AVERAGE' )

Type :

Literal[‘AVERAGE’, ‘SUM’, ‘SCRIPTED’, ‘MIN’, ‘MAX’]

use_self

Expose a ‘self’ entry in the namespace so drivers can readily point at the data they’re changing — object, bone, and the like (default False)

Type :

bool

variables

The properties feeding values into this driver (default None, readonly)

Type :

ChannelDriverVariables[DriverVariable]

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

| FCurve.driver | |

## DriverTarget(bpy_struct)

### DriverTarget(bpy_struct)

base class — bpy_struct

class bpy.types. DriverTarget ( bpy_struct )

Where a driver variable draws its input values from

bone_target

The PoseBone to treat as the target, by name (default “”, never None)

Type :

str

context_property

Which context-dependent data-block the property is read from (default '`ACTIVE_SCENE`' )

- `ACTIVE_SCENE`
Active Scene – The scene being evaluated right now.

- `ACTIVE_VIEW_LAYER`
Active View Layer – The view layer being evaluated right now.

Type :

Literal[‘`ACTIVE_SCENE`’, ‘`ACTIVE_VIEW_LAYER`’]

data_path

The RNA Path, relative to the ID-block, to the property in use (default “”, never None)

Type :

str

fallback_value

What to fall back on when the data path won’t resolve (in [-inf, inf], default 0.0)

Type :

float

id

The ID-block holding the property in question (set id_type first)

Type :

ID

id_type

Which kind of ID-block is allowed (default 'OBJECT' )

Type :

Literal[Id Type Items]

is_fallback_used

Reports that the latest variable evaluation fell back on the fallback value (default False, readonly)

Type :

bool

rotation_mode

How rotation channel values are worked out (default 'AUTO' )

Type :

Literal[Driver Target Rotation Mode Items]

transform_space

Which space the transforms are taken in (default '`WORLD_SPACE`' )

- `WORLD_SPACE`
World Space – Transforms fold in parenting/restpose and constraints.

- `TRANSFORM_SPACE`
Transform Space – Transforms leave out parenting/restpose and constraints.

- `LOCAL_SPACE`
Local Space – Transforms fold in constraints but leave out parenting/restpose.

Type :

Literal[‘`WORLD_SPACE`’, ‘`TRANSFORM_SPACE`’, ‘`LOCAL_SPACE`’]

transform_type

Which driver variable type this is (default '`LOC_X`' )

Type :

Literal[‘`LOC_X`’, ‘`LOC_Y`’, ‘`LOC_Z`’, ‘`ROT_X`’, ‘`ROT_Y`’, ‘`ROT_Z`’, ‘`ROT_W`’, ‘`SCALE_X`’, ‘`SCALE_Y`’, ‘`SCALE_Z`’, ‘`SCALE_AVG`’]

use_fallback_value

Fall back on the fallback value when the data path won’t resolve, rather than letting the driver fail to evaluate (default False)

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

| DriverVariable.targets | |

## DriverVariable(bpy_struct)

### DriverVariable(bpy_struct)

base class — bpy_struct

class bpy.types. DriverVariable ( bpy_struct )

A variable pulled from some source or target within a driver relationship

is_name_valid

Whether this name works as a driver variable name (default True, readonly)

Type :

bool

name

The name used inside scripted expressions and functions (spaces and dots aren’t permitted, and it has to begin with a letter) (default “”, never None)

Type :

str

targets

Where this variable’s input data comes from for evaluation (default None, readonly)

Type :

bpy_prop_collection[DriverTarget]

type

Which driver variable type this is (default '`SINGLE_PROP`' )

- `SINGLE_PROP`
Single Property – Read the value off some RNA property.

- TRANSFORMS
Transform Channel – The fully resolved transform value of an object or bone.

- `ROTATION_DIFF`
Rotational Difference – The angle separating two bones.

- `LOC_DIFF`
Distance – The gap between a pair of bones or objects.

- `CONTEXT_PROP`
Context Property – Read the value off an RNA property within the active evaluation context.

Type :

Literal[‘`SINGLE_PROP`’, ‘TRANSFORMS’, ‘`ROTATION_DIFF`’, ‘`LOC_DIFF`’, ‘`CONTEXT_PROP`’]

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

| ChannelDriverVariables.new ChannelDriverVariables.remove | Driver.variables |
