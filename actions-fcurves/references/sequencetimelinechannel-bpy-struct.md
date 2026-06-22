# Sequencetimelinechannel Bpy Struct, Shapekey Bpy Struct, Shapekeybezierpoint Bpy Struct, Shapekeycurvepoint Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: SequenceTimelineChannel(bpy_struct); ShapeKey(bpy_struct); ShapeKeyBezierPoint(bpy_struct); ShapeKeyCurvePoint(bpy_struct); ShapeKeyPoint(bpy_struct); Short2Attribute(Attribute); Short2AttributeValue(bpy_struct); ShrinkwrapConstraint(Constraint); SimulationZoneViewerPathElem(ViewerPathElem).

## SequenceTimelineChannel(bpy_struct)

### SequenceTimelineChannel(bpy_struct)

base class — bpy_struct

class bpy.types. SequenceTimelineChannel ( bpy_struct )

lock

(default False)

Type :

bool

mute

(default False)

Type :

bool

name

(default “”, never None)

Type :

str

number

The index of this channel (in [-inf, inf], default 0, readonly)

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

| MetaStrip.channels | SequenceEditor.channels |

## ShapeKey(bpy_struct)

### ShapeKey(bpy_struct)

base class — bpy_struct

class bpy.types. ShapeKey ( bpy_struct )

A single shape key stored inside a shape keys data-block.

data

(default None, readonly)

Type :

bpy_prop_collection[UnknownType]

frame

Frame for absolute keys (in [-inf, inf], default 0.0, readonly)

Type :

float

interpolation

Interpolation type for absolute shape keys (default '`KEY_LINEAR`' )

Type :

Literal[‘`KEY_LINEAR`’, ‘`KEY_CARDINAL`’, ‘`KEY_CATMULL_ROM`’, ‘`KEY_BSPLINE`’]

lock_shape

Guard the shape key against unintended sculpting and editing (default False)

Type :

bool

mute

Switch this shape key on or off (default False)

Type :

bool

name

Name of Shape Key (default “”, never None)

Type :

str

points

Fast path to shape-key point data through foreach_get/foreach_set. Warning: Does not support legacy Curve shape keys. (default None, readonly)

Type :

bpy_prop_collection[ShapeKeyPoint]

relative_key

Shape used as a relative key (never None)

Type :

ShapeKey

select

Shape key selection state (default False)

Type :

bool

slider_max

Maximum for slider (in [-10, 10], default 1.0)

Type :

float

slider_min

Minimum for slider (in [-10, 10], default 0.0)

Type :

float

value

Value of shape key at the current frame (in [0, 1], default 0.0)

Type :

float

vertex_group

Vertex weight group, to blend with basis shape (default “”, never None)

Type :

str

normals_vertex_get ( )

Compute local space vertices’ normals for this shape key

Returns :

normals, (in [-1, 1])

Return type :

float

normals_polygon_get ( )

Compute local space faces’ normals for this shape key

Returns :

normals, (in [-1, 1])

Return type :

float

normals_split_get ( )

Compute local space face corners’ normals for this shape key

Returns :

normals, (in [-1, 1])

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

| ClothSettings.rest_shape_key Key.key_blocks Key.reference_key Object.active_shape_key | Object.shape_key_add Object.shape_key_remove Object.shape_keys_selected ShapeKey.relative_key |

## ShapeKeyBezierPoint(bpy_struct)

### ShapeKeyBezierPoint(bpy_struct)

base class — bpy_struct

class bpy.types. ShapeKeyBezierPoint ( bpy_struct )

A single point belonging to a Bézier-curve shape key.

co

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

handle_left

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

handle_right

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

radius

Radius for beveling (in [0, inf], default 0.0)

Type :

float

tilt

Tilt in 3D View (in [-376.991, 376.991], default 0.0)

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

## ShapeKeyCurvePoint(bpy_struct)

### ShapeKeyCurvePoint(bpy_struct)

base class — bpy_struct

class bpy.types. ShapeKeyCurvePoint ( bpy_struct )

A single point belonging to a curve shape key.

co

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

radius

Radius for beveling (in [0, inf], default 0.0)

Type :

float

tilt

Tilt in 3D View (in [-376.991, 376.991], default 0.0)

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

## ShapeKeyPoint(bpy_struct)

### ShapeKeyPoint(bpy_struct)

base class — bpy_struct

class bpy.types. ShapeKeyPoint ( bpy_struct )

A single point within a shape key.

co

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

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

| ShapeKey.points | |

## Short2Attribute(Attribute)

### Short2Attribute(Attribute)

base classes — bpy_struct, Attribute

class bpy.types. Short2Attribute ( Attribute )

A geometry attribute holding 2D integer vector values.

data

(default None, readonly)

Type :

bpy_prop_collection[Short2AttributeValue]

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

| bpy_struct.id_data Attribute.name Attribute.data_type Attribute.storage_type | Attribute.domain Attribute.is_internal Attribute.is_required |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Attribute.bl_rna_get_subclass Attribute.bl_rna_get_subclass_py |

## Short2AttributeValue(bpy_struct)

### Short2AttributeValue(bpy_struct)

base class — bpy_struct

class bpy.types. Short2AttributeValue ( bpy_struct )

One 2D entry held inside a geometry attribute.

value

2D vector (array of 2 items, in [-32768, 32767], default (0, 0))

Type :

bpy_prop_array[int]

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

| Short2Attribute.data | |

## ShrinkwrapConstraint(Constraint)

### ShrinkwrapConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. ShrinkwrapConstraint ( Constraint )

A constraint that drives a shrinkwrap-style relationship.

cull_face

Prevents vertices from projecting onto a target face that faces toward or away (default 'OFF' )

- OFF
Off – Cull nothing.

- FRONT
Front – Skip projection while positioned ahead of the face.

- BACK
Back – Skip projection while positioned behind the face.

Type :

Literal[‘OFF’, ‘FRONT’, ‘BACK’]

distance

Distance to Target (in [0, inf], default 0.0)

Type :

float

project_axis

Axis constrain to (default '`POS_X`' )

Type :

Literal[Object Axis Items]

project_axis_space

Space for the projection axis (default 'WORLD' )

- WORLD
World Space – Evaluated against the world coordinate frame.

- CUSTOM
Custom Space – Evaluated in the local frame of a chosen object, bone, or vertex group.

- POSE
Pose Space – Evaluated in Pose Space, with the object transform left out.

- `LOCAL_WITH_PARENT`
Local With Parent – Evaluated against the bone's rest-pose local frame, so the parent's transform is folded in.

- LOCAL
Local Space – Evaluated against the object's own local frame.

Type :

Literal[‘WORLD’, ‘CUSTOM’, ‘POSE’, ‘`LOCAL_WITH_PARENT`’, ‘LOCAL’]

project_limit

Cap the distance allowed for projection (zero disables) (in [0, inf], default 0.0)

Type :

float

shrinkwrap_type

Picks which shrinkwrap algorithm finds the target position (default '`NEAREST_SURFACE`' )

- `NEAREST_SURFACE`
Nearest Surface Point – Pull the point onto the closest spot on the target surface.

- PROJECT
Project – Pull the point onto the target surface measured along a chosen axis.

- `NEAREST_VERTEX`
Nearest Vertex – Pull the point onto the target's closest vertex.

- `TARGET_PROJECT`
Target Normal Project – Pull the point onto the target surface following the target's interpolated vertex normals.

Type :

Literal[‘`NEAREST_SURFACE`’, ‘PROJECT’, ‘`NEAREST_VERTEX`’, ‘`TARGET_PROJECT`’]

target

Target Mesh object

Type :

Object

track_axis

Axis that is aligned to the normal (default '`TRACK_X`' )

Type :

Literal[‘`TRACK_X`’, ‘`TRACK_Y`’, ‘`TRACK_Z`’, ‘`TRACK_NEGATIVE_X`’, ‘`TRACK_NEGATIVE_Y`’, ‘`TRACK_NEGATIVE_Z`’]

use_invert_cull

When the projection runs the opposite way, flip the face cull mode (default False)

Type :

bool

use_project_opposite

Project along both the chosen direction and its reverse (default False)

Type :

bool

use_track_normal

Line the chosen axis up with the surface normal (default False)

Type :

bool

wrap_mode

Choose how the object is held to the target surface (default '`ON_SURFACE`' )

Type :

Literal[Modifier Shrinkwrap Mode Items]

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

## SimulationZoneViewerPathElem(ViewerPathElem)

### SimulationZoneViewerPathElem(ViewerPathElem)

base classes — bpy_struct, ViewerPathElem

class bpy.types. SimulationZoneViewerPathElem ( ViewerPathElem )

sim_output_node_id

(in [-inf, inf], default 0)

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

| bpy_struct.id_data ViewerPathElem.type | ViewerPathElem.ui_name |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ViewerPathElem.bl_rna_get_subclass ViewerPathElem.bl_rna_get_subclass_py |
