# Floatattributevalue Bpy Struct, Floatcolorattribute Attribute, Floatcolorattributevalue Bpy Struct, Floatproperty Property ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: FloatAttributeValue(bpy_struct); FloatColorAttribute(Attribute); FloatColorAttributeValue(bpy_struct); FloatProperty(Property); FloatVectorAttribute(Attribute); FloatVectorAttributeValue(bpy_struct); FloatVectorValueReadOnly(bpy_struct); FloorConstraint(Constraint); FluidEffectorSettings(bpy_struct); FluidFlowSettings(bpy_struct).

## FloatAttributeValue(bpy_struct)

### FloatAttributeValue(bpy_struct)

base class — bpy_struct

class bpy.types. FloatAttributeValue ( bpy_struct )

A floating-point value stored within a geometry attribute.

value

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

| FloatAttribute.data | |

## FloatColorAttribute(Attribute)

### FloatColorAttribute(Attribute)

base classes — bpy_struct, Attribute

class bpy.types. FloatColorAttribute ( Attribute )

A geometry attribute holding RGBA colors as 32-bit floating-point values per channel.

data

(default None, readonly)

Type :

bpy_prop_collection[FloatColorAttributeValue]

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

## FloatColorAttributeValue(bpy_struct)

### FloatColorAttributeValue(bpy_struct)

base class — bpy_struct

class bpy.types. FloatColorAttributeValue ( bpy_struct )

A single color entry held within a geometry attribute.

color

RGBA color in scene linear color space (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

color_srgb

RGBA color in sRGB color space (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

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

| FloatColorAttribute.data | |

## FloatProperty(Property)

### FloatProperty(Property)

base classes — bpy_struct, Property

class bpy.types. FloatProperty ( Property )

Definition of an RNA property holding a single-precision floating-point number.

array_dimensions

Length of each dimension of the array (array of 3 items, in [0, inf], default (0, 0, 0), readonly)

Type :

bpy_prop_array[int]

array_length

Maximum length of the array, 0 means unlimited (in [0, inf], default 0, readonly)

Type :

int

default

Default value for this number (in [-inf, inf], default 0.0, readonly)

Type :

float

default_array

Default value for this array (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

hard_max

Maximum value used by buttons (in [-inf, inf], default 0.0, readonly)

Type :

float

hard_min

Minimum value used by buttons (in [-inf, inf], default 0.0, readonly)

Type :

float

is_array

(default False, readonly)

Type :

bool

precision

How many decimal places buttons display. For fields whose unit is 'NONE' or 'TIME' (frame count) and whose step divides evenly by 100, the fraction is dropped automatically once the value is a whole number. (in [0, inf], default 0, readonly)

Type :

int

soft_max

Maximum value used by buttons (in [-inf, inf], default 0.0, readonly)

Type :

float

soft_min

Minimum value used by buttons (in [-inf, inf], default 0.0, readonly)

Type :

float

step

Increment applied by the number buttons; for float fields this is one hundredth of the stated step size (in [0, inf], default 0.0, readonly)

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

| bpy_struct.id_data Property.name Property.identifier Property.description Property.translation_context Property.type Property.subtype Property.srna Property.unit Property.icon Property.is_readonly Property.is_animatable Property.is_overridable Property.is_required Property.is_argument_optional Property.is_never_none Property.is_hidden | Property.is_skip_save Property.is_skip_preset Property.is_output Property.is_registered Property.is_registered_optional Property.is_runtime Property.is_enum_flag Property.is_library_editable Property.is_path_output Property.is_path_supports_blend_relative Property.is_path_supports_templates Property.is_deprecated Property.deprecated_note Property.deprecated_version Property.deprecated_removal_version Property.tags |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Property.bl_rna_get_subclass Property.bl_rna_get_subclass_py |

## FloatVectorAttribute(Attribute)

### FloatVectorAttribute(Attribute)

base classes — bpy_struct, Attribute

class bpy.types. FloatVectorAttribute ( Attribute )

A geometry attribute whose entries are floating-point 3D vectors.

data

(default None, readonly)

Type :

bpy_prop_collection[FloatVectorAttributeValue]

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

## FloatVectorAttributeValue(bpy_struct)

### FloatVectorAttributeValue(bpy_struct)

base class — bpy_struct

class bpy.types. FloatVectorAttributeValue ( bpy_struct )

A single vector entry held within a geometry attribute.

vector

3D vector (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

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

| Curves.position_data | FloatVectorAttribute.data |

## FloatVectorValueReadOnly(bpy_struct)

### FloatVectorValueReadOnly(bpy_struct)

base class — bpy_struct

class bpy.types. FloatVectorValueReadOnly ( bpy_struct )

vector

3D vector (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

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

| Curves.normals | |

## FloorConstraint(Constraint)

### FloorConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. FloorConstraint ( Constraint )

Restrict where an object may move by treating a target as a floor it cannot cross.

floor_location

Side of the target that the object is blocked from passing through (default '`FLOOR_X`' )

Type :

Literal[‘`FLOOR_X`’, ‘`FLOOR_Y`’, ‘`FLOOR_Z`’, ‘`FLOOR_NEGATIVE_X`’, ‘`FLOOR_NEGATIVE_Y`’, ‘`FLOOR_NEGATIVE_Z`’]

offset

Offset of floor from object origin (in [-inf, inf], default 0.0)

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

use_rotation

Use the target’s rotation to determine floor (default False)

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

## FluidEffectorSettings(bpy_struct)

### FluidEffectorSettings(bpy_struct)

base class — bpy_struct

class bpy.types. FluidEffectorSettings ( bpy_struct )

Settings controlling how an object collides with smoke.

effector_type

Switch the role this effector plays in the simulation (default 'COLLISION' )

- COLLISION
Collision – Create collision object.

- GUIDE
Guide – Create guide object.

Type :

Literal[‘COLLISION’, ‘GUIDE’]

guide_mode

Sets the way guiding velocities are built (default 'OVERRIDE' )

- MAXIMUM
Maximize – Compare velocities from previous frame with new velocities from current frame and keep the maximum.

- MINIMUM
Minimize – Compare velocities from previous frame with new velocities from current frame and keep the minimum.

- OVERRIDE
Override – Always write new guide velocities for every frame (each frame only contains current velocities from guiding objects).

- AVERAGED
Averaged – Take average of velocities from previous frame and new velocities from current frame.

Type :

Literal[‘MAXIMUM’, ‘MINIMUM’, ‘OVERRIDE’, ‘AVERAGED’]

subframes

Extra samples taken between frames to sharpen the result for fast-moving effector objects (in [0, 200], default 0)

Type :

int

surface_distance

Extra band around the mesh surface still treated as effector (in [0, 10], default 0.0)

Type :

float

use_effector

Decide at which times the effector takes effect (default True)

Type :

bool

use_plane_init

Treat this object as a planar, unclosed mesh (default False)

Type :

bool

velocity_factor

Multiplier of obstacle velocity (in [-100, 100], default 1.0)

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

| FluidModifier.effector_settings | |

## FluidFlowSettings(bpy_struct)

### FluidFlowSettings(bpy_struct)

base class — bpy_struct

class bpy.types. FluidFlowSettings ( bpy_struct )

Settings that drive a fluid flow.

density

(in [0, 10], default 1.0)

Type :

float

density_vertex_group

Name of the vertex group that sets how fast the surface emits (default “”, never None)

Type :

str

flow_behavior

Switch how the flow acts within the simulation (default 'GEOMETRY' )

- INFLOW
Inflow – Add fluid to simulation.

- OUTFLOW
Outflow – Delete fluid from simulation.

- GEOMETRY
Geometry – Only use given geometry for fluid.

Type :

Literal[‘INFLOW’, ‘OUTFLOW’, ‘GEOMETRY’]

flow_source

Switch the way fluid is emitted (default 'NONE' )

Type :

Literal[‘NONE’]

flow_type

Switch which kind of fluid is added in the simulation (default 'SMOKE' )

- SMOKE
Smoke – Add smoke.

- BOTH
Fire + Smoke – Add fire and smoke.

- FIRE
Fire – Add fire.

- LIQUID
Liquid – Add liquid.

Type :

Literal[‘SMOKE’, ‘BOTH’, ‘FIRE’, ‘LIQUID’]

fuel_amount

(in [0, 10], default 1.0)

Type :

float

noise_texture

Texture that controls emission strength

Type :

Texture

particle_size

Size of a particle measured in simulation cells (in [0.1, inf], default 1.0)

Type :

float

particle_system

Particle systems emitted from the object

Type :

ParticleSystem

smoke_color

Color of smoke (array of 3 items, in [0, inf], default (0.7, 0.7, 0.7))

Type :

mathutils.Color

subframes

Extra samples taken between frames to sharpen the result for fast-moving flows (in [0, 200], default 0)

Type :

int

surface_distance

Distance (measured in domain grid units) above the mesh surface at which fluid is emitted. Larger values push emission further from the surface. When both this value and the emitter are smaller than one domain grid unit, no fluid is produced. (in [0, 10], default 1.0)

Type :

float

temperature

How far the emitted temperature sits above or below the ambient level (in [-10, 10], default 1.0)

Type :

float

texture_map_type

Texture mapping type (default 'AUTO' )

- AUTO
Generated – Generated coordinates centered to flow object.

- UV
UV – Use UV layer for texture coordinates.

Type :

Literal[‘AUTO’, ‘UV’]

texture_offset

Z-offset of texture mapping (in [0, 200], default 0.0)

Type :

float

texture_size

Size of texture mapping (in [0.01, 10], default 1.0)

Type :

float

use_absolute

Hold emitter density to exactly the given value rather than letting it accumulate (default True)

Type :

bool

use_inflow

Decide at which times the fluid flow takes effect (default True)

Type :

bool

use_initial_velocity

Give the fluid a starting velocity at the moment it is emitted (default False)

Type :

bool

use_particle_size

Either set the particle size in simulation cells or fall back to the nearest cell (default True)

Type :

bool

use_plane_init

Treat the object as a planar, unclosed mesh, so fluid is emitted only from the mesh surface according to the surface emission value (default False)

Type :

bool

use_texture

Use a texture to control emission strength (default False)

Type :

bool

uv_layer

UV map name (default “”, never None)

Type :

str

velocity_coord

Extra starting velocity along X, Y and Z, added on top of the source velocity (array of 3 items, in [-1000.1, 1000.1], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

velocity_factor

Multiplier applied to the source velocity handed to the fluid (the source velocity is nonzero only while the object moves) (in [-100, 100], default 1.0)

Type :

float

velocity_normal

How much velocity is added along the surface normal (in [-100, 100], default 0.0)

Type :

float

velocity_random

How much randomized velocity is added (in [0, 10], default 0.0)

Type :

float

volume_density

Governs emission from inside the mesh; larger values emit more from within it (in [0, 1], default 0.0)

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

| FluidModifier.flow_settings | |
