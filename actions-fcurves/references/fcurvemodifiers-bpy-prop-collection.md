# Fcurvemodifiers Bpy Prop Collection, Fcurvesample Bpy Struct, Fieldsettings Bpy Struct, Filebrowserfsmenuentry Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: FCurveModifiers(bpy_prop_collection); FCurveSample(bpy_struct); FieldSettings(bpy_struct); FileBrowserFSMenuEntry(bpy_struct); FileSelectEntry(bpy_struct); Float2Attribute(Attribute); Float2AttributeValue(bpy_struct); Float4x4Attribute(Attribute); Float4x4AttributeValue(bpy_struct); FloatAttribute(Attribute).

## FCurveModifiers(bpy_prop_collection)

### FCurveModifiers(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. FCurveModifiers ( bpy_prop_collection )

A set of F-Curve Modifiers.

active

The currently active F-Curve Modifier

Type :

FModifier

new ( type )

Add a constraint to this object

Parameters :

type (Literal[Fmodifier Type Items]) – Constraint type to add

Returns :

New fmodifier

Return type :

FModifier

remove ( modifier )

Remove a modifier from this F-Curve

Parameters :

modifier (FModifier) – Removed modifier (never None)

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

| FCurve.modifiers | |

## FCurveSample(bpy_struct)

### FCurveSample(bpy_struct)

base class — bpy_struct

class bpy.types. FCurveSample ( bpy_struct )

One sampled point along an F-Curve.

co

Where the point sits (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

select

Whether the point is selected (default False)

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

| FCurve.sampled_points | |

## FieldSettings(bpy_struct)

### FieldSettings(bpy_struct)

base class — bpy_struct

class bpy.types. FieldSettings ( bpy_struct )

The force-field settings that belong to an object inside a physics simulation.

apply_to_location

Influence where particles sit (default False)

Type :

bool

apply_to_rotation

Influence the dynamic rotation of particles (default False)

Type :

bool

distance_max

Largest distance over which the field stays active (in [0, inf], default 0.0)

Type :

float

distance_min

Smallest distance before the field begins to fall off (in [0, 1000], default 0.0)

Type :

float

falloff_power

Rate at which strength diminishes with distance from the force field (in [0, 10], default 0.0)

Type :

float

falloff_type

(default 'SPHERE' )

Type :

Literal[‘CONE’, ‘SPHERE’, ‘TUBE’]

flow

Turn effector force into an air-flow velocity (in [-inf, inf], default 0.0)

Type :

float

guide_clump_amount

How much clumping is applied (in [-1, 1], default 0.0)

Type :

float

guide_clump_shape

The profile of the clumping (in [-0.999, 0.999], default 0.0)

Type :

float

guide_free

Span of guide-free time measured back from the end of particle life (in [0, 0.99], default 0.0)

Type :

float

guide_kink_amplitude

Size of the offset (in [0, 10], default 0.0)

Type :

float

guide_kink_axis

Axis along which the offset is applied (default 'X' )

Type :

Literal[Axis Xyz Items]

guide_kink_frequency

How often the offset repeats (1/total length) (in [0, 10], default 0.0)

Type :

float

guide_kink_shape

Bias the offset toward the start or the end (in [-0.999, 0.999], default 0.0)

Type :

float

guide_kink_type

Variety of periodic offset placed on the curve (default 'NONE' )

Type :

Literal[‘NONE’, ‘BRAID’, ‘CURL’, ‘RADIAL’, ‘ROLL’, ‘ROTATION’, ‘WAVE’]

guide_minimum

Distance beyond which particles feel the full effect (in [-inf, inf], default 0.0)

Type :

float

harmonic_damping

How strongly the harmonic force is damped (in [-inf, inf], default 0.0)

Type :

float

inflow

The inward part of the vortex force (in [-inf, inf], default 0.0)

Type :

float

linear_drag

Drag that scales with velocity (in [-inf, inf], default 0.0)

Type :

float

noise

How much noise is added to the force strength (in [0, 10], default 0.0)

Type :

float

quadratic_drag

Drag that scales with velocity squared (in [-inf, inf], default 0.0)

Type :

float

radial_falloff

Power of the radial falloff (true gravitational falloff = 2) (in [0, 10], default 0.0)

Type :

float

radial_max

Largest radial distance over which the field stays active (in [0, 1000], default 0.0)

Type :

float

radial_min

Smallest radial distance before the field begins to fall off (in [0, 1000], default 0.0)

Type :

float

rest_length

Resting length of the harmonic force (in [0, inf], default 0.0)

Type :

float

seed

Random seed driving the noise (in [1, 128], default 0)

Type :

int

shape

Which geometry decides where the effector force comes from (default 'POINT' )

- POINT
Point – The field emanates from the object's center.

- LINE
Line – The field emanates from the object's local Z axis.

- PLANE
Plane – The field emanates from the object's local XY plane.

- SURFACE
Surface – The field emanates from the object's surface.

- POINTS
Every Point – The field emanates from every vertex of the object.

Type :

Literal[‘POINT’, ‘LINE’, ‘PLANE’, ‘SURFACE’, ‘POINTS’]

size

How large the turbulence is (in [0, inf], default 0.0)

Type :

float

source_object

Choose the domain object belonging to the smoke simulation

Type :

Object

strength

How strong the force field is (in [-inf, inf], default 0.0)

Type :

float

texture

Texture that supplies the force

Type :

Texture

texture_mode

The way the texture effect is computed (RGB and Curl require an RGB texture, otherwise Gradient is substituted) (default 'RGB' )

Type :

Literal[‘CURL’, ‘GRADIENT’, ‘RGB’]

texture_nabla

Sets the derivative offset used when computing gradient and curl (in [0.0001, 1], default 0.0)

Type :

float

type

Which kind of field this is (default 'NONE' )

- NONE
None.

- BOID
Boid – Make a force that behaves like a boid's predator or target.

- CHARGE
Charge – A spherical force field driven by particle charge, which only affects other charge force fields.

- GUIDE
Curve Guide – Make a force running along a curve object.

- DRAG
Drag – Make a force that slows motion down.

- `FLUID_FLOW`
Fluid Flow – Make a force derived from fluid-simulation velocities.

- FORCE
Force – A radial field pointing toward the object's center.

- HARMONIC
Harmonic – This force field originates at the zero point of a harmonic oscillator.

- LENNARDJ
Lennard-Jones – A force field built on the Lennard-Jones potential.

- MAGNET
Magnetic – A force field that responds to how fast the particles move.

- TEXTURE
Texture – A force field driven by a texture.

- TURBULENCE
Turbulence – Make turbulence from a noise field.

- VORTEX
Vortex – A spiraling force that twists about the force object's local Z axis.

- WIND
Wind – A steady force directed along the force object's local Z axis.

Type :

Literal[‘NONE’, ‘BOID’, ‘CHARGE’, ‘GUIDE’, ‘DRAG’, ‘`FLUID_FLOW`’, ‘FORCE’, ‘HARMONIC’, ‘LENNARDJ’, ‘MAGNET’, ‘TEXTURE’, ‘TURBULENCE’, ‘VORTEX’, ‘WIND’]

use_2d_force

Confine the force to 2D only (default False)

Type :

bool

use_absorption

Let collision objects soak up the force (default False)

Type :

bool

use_global_coords

Drive turbulence from effector/global coordinates (default False)

Type :

bool

use_gravity_falloff

Scale the force by 1/distance² (default False)

Type :

bool

use_guide_path_add

Contribute a fraction of the whole path based on distance/falloff (default False)

Type :

bool

use_guide_path_weight

Let curve weights shape how strongly particles follow the curve (default False)

Type :

bool

use_max_distance

Cap the distance over which the field stays active (default False)

Type :

bool

use_min_distance

Apply a minimum distance before the field begins to fall off (default False)

Type :

bool

use_multiple_springs

Subject every point to several springs (default False)

Type :

bool

use_object_coords

Drive the texture from object/global coordinates (default False)

Type :

bool

use_radial_max

Cap the radial distance over which the field stays active (default False)

Type :

bool

use_radial_min

Apply a minimum radial distance before the field begins to fall off (default False)

Type :

bool

use_root_coords

Take texture coordinates from where the particle roots sit (default False)

Type :

bool

use_smoke_density

Tune the force strength according to smoke density (default False)

Type :

bool

wind_factor

The degree to which the force weakens when it acts along a surface, such as cloth (in [0, 1], default 0.0)

Type :

float

z_direction

Act in the full Z direction or only its positive/negative half (default 'BOTH' )

Type :

Literal[‘POSITIVE’, ‘NEGATIVE’, ‘BOTH’]

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

| Object.field ParticleSettings.force_field_1 | ParticleSettings.force_field_2 |

## FileBrowserFSMenuEntry(bpy_struct)

### FileBrowserFSMenuEntry(bpy_struct)

base class — bpy_struct

class bpy.types. FileBrowserFSMenuEntry ( bpy_struct )

File Select Parameters

icon

(in [-inf, inf], default 0)

Type :

int

name

(default “”, never None)

Type :

str

path

(default “”, never None)

Type :

str

use_save

Whether the path lives in bookmarks or was produced by the OS (default False, readonly)

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

| SpaceFileBrowser.bookmarks SpaceFileBrowser.recent_folders | SpaceFileBrowser.system_bookmarks SpaceFileBrowser.system_folders |

## FileSelectEntry(bpy_struct)

### FileSelectEntry(bpy_struct)

base class — bpy_struct

class bpy.types. FileSelectEntry ( bpy_struct )

An entry the File Browser can display.

asset_data

Asset data, set only when the file stands in for an asset (readonly)

Type :

AssetMetaData

name

(default “”, readonly, never None)

Type :

str

preview_icon_id

A unique integer that identifies this file's preview as an icon (zero marks it invalid) (in [-inf, inf], default 0, readonly)

Type :

int

relative_path

Path, including the file name, taken relative to the folder the File Browser is currently showing (default “”, readonly, never None)

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

## Float2Attribute(Attribute)

### Float2Attribute(Attribute)

base classes — bpy_struct, Attribute

class bpy.types. Float2Attribute ( Attribute )

A geometry attribute holding floating-point 2D vectors.

data

(default None, readonly)

Type :

bpy_prop_collection[Float2AttributeValue]

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

## Float2AttributeValue(bpy_struct)

### Float2AttributeValue(bpy_struct)

base class — bpy_struct

class bpy.types. Float2AttributeValue ( bpy_struct )

A 2D vector stored within a geometry attribute.

vector

2D vector (array of 2 items, in [-inf, inf], default (0.0, 0.0))

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

| Float2Attribute.data | MeshUVLoopLayer.uv |

## Float4x4Attribute(Attribute)

### Float4x4Attribute(Attribute)

base classes — bpy_struct, Attribute

class bpy.types. Float4x4Attribute ( Attribute )

A geometry attribute holding a 4-by-4 float matrix.

data

(default None, readonly)

Type :

bpy_prop_collection[Float4x4AttributeValue]

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

## Float4x4AttributeValue(bpy_struct)

### Float4x4AttributeValue(bpy_struct)

base class — bpy_struct

class bpy.types. Float4x4AttributeValue ( bpy_struct )

A matrix value stored within a geometry attribute.

value

Matrix (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)))

Type :

mathutils.Matrix

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

| Float4x4Attribute.data | |

## FloatAttribute(Attribute)

### FloatAttribute(Attribute)

base classes — bpy_struct, Attribute

class bpy.types. FloatAttribute ( Attribute )

A geometry attribute holding floating-point values.

data

(default None, readonly)

Type :

bpy_prop_collection[FloatAttributeValue]

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
