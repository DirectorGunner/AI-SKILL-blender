# Particlesettingstextureslot Textureslot, Particlesettingstextureslots Bpy Prop Collection, Particlesystem Bpy Struct, Particlesystems Bpy Prop Collection ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ParticleSettingsTextureSlot(TextureSlot); ParticleSettingsTextureSlots(bpy_prop_collection); ParticleSystem(bpy_struct); ParticleSystems(bpy_prop_collection); ParticleTarget(bpy_struct); PathCompare(bpy_struct); PathCompareCollection(bpy_prop_collection).

## ParticleSettingsTextureSlot(TextureSlot)

### ParticleSettingsTextureSlot(TextureSlot)

base classes — bpy_struct, TextureSlot

class bpy.types. ParticleSettingsTextureSlot ( TextureSlot )

A texture slot belonging to a Particle Settings data-block

clump_factor

How much the texture drives the child clump (in [-inf, inf], default 1.0)

Type :

float

damp_factor

How much the texture drives particle damping (in [-inf, inf], default 1.0)

Type :

float

density_factor

How much the texture drives particle density (in [-inf, inf], default 1.0)

Type :

float

field_factor

How much the texture drives the particle force fields (in [-inf, inf], default 1.0)

Type :

float

gravity_factor

How much the texture drives particle gravity (in [-inf, inf], default 1.0)

Type :

float

kink_amp_factor

How much the texture drives the child kink amplitude (in [-inf, inf], default 1.0)

Type :

float

kink_freq_factor

How much the texture drives the child kink frequency (in [-inf, inf], default 1.0)

Type :

float

length_factor

How much the texture drives the child hair length (in [-inf, inf], default 1.0)

Type :

float

life_factor

How much the texture drives the particle lifetime (in [-inf, inf], default 1.0)

Type :

float

mapping

(default 'FLAT' )

- FLAT
Flat – Project the X and Y coordinates straight on.

- CUBE
Cube – Project along the normal vector.

- TUBE
Tube – Project with Z as the central axis.

- SPHERE
Sphere – Project with Z as the central axis.

Type :

Literal[‘FLAT’, ‘CUBE’, ‘TUBE’, ‘SPHERE’]

mapping_x

(default 'X' )

Type :

Literal[‘NONE’, ‘X’, ‘Y’, ‘Z’]

mapping_y

(default 'Y' )

Type :

Literal[‘NONE’, ‘X’, ‘Y’, ‘Z’]

mapping_z

(default 'Z' )

Type :

Literal[‘NONE’, ‘X’, ‘Y’, ‘Z’]

object

Object to use for mapping with Object texture coordinates

Type :

Object

rough_factor

How much the texture drives child roughness (in [-inf, inf], default 1.0)

Type :

float

size_factor

How much the texture drives the physical particle size (in [-inf, inf], default 1.0)

Type :

float

texture_coords

Texture coordinates used to project the texture onto the background (default 'UV' )

- GLOBAL
Global – Drive the texture coordinates from global space.

- OBJECT
Object – Drive them from the linked object’s coordinates.

- UV
UV – Drive them from the UV coordinates.

- ORCO
Generated – Drive them from the object’s original, undeformed coordinates.

- STRAND
Strand / Particle – Drive them from the normalized strand coordinate (1D), or from particle age (X) and trail position (Y).

Type :

Literal[‘GLOBAL’, ‘OBJECT’, ‘UV’, ‘ORCO’, ‘STRAND’]

time_factor

How much the texture drives the particle emission time (in [-inf, inf], default 1.0)

Type :

float

twist_factor

How much the texture drives the child twist (in [-inf, inf], default 1.0)

Type :

float

use_map_clump

Influence the child clumping (default False)

Type :

bool

use_map_damp

Influence the particle velocity damping (default False)

Type :

bool

use_map_density

Influence how dense the particles are (default False)

Type :

bool

use_map_field

Influence the particle force fields (default False)

Type :

bool

use_map_gravity

Influence the particle gravity (default False)

Type :

bool

use_map_kink_amp

Influence the child kink amplitude (default False)

Type :

bool

use_map_kink_freq

Influence the child kink frequency (default False)

Type :

bool

use_map_length

Influence the child hair length (default False)

Type :

bool

use_map_life

Influence how long the particles live (default False)

Type :

bool

use_map_rough

Influence the child roughness (default False)

Type :

bool

use_map_size

Influence the particle size (default False)

Type :

bool

use_map_time

Influence when the particles are emitted (default True)

Type :

bool

use_map_twist

Influence the child twist (default False)

Type :

bool

use_map_velocity

Influence the particle's initial velocity (default False)

Type :

bool

uv_layer

Which UV map feeds the UV texture coordinates (default “”, never None)

Type :

str

velocity_factor

How much the texture drives the particle's initial velocity (in [-inf, inf], default 1.0)

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

| bpy_struct.id_data TextureSlot.texture TextureSlot.name TextureSlot.offset TextureSlot.scale | TextureSlot.color TextureSlot.blend_type TextureSlot.default_value TextureSlot.output_node |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values TextureSlot.bl_rna_get_subclass TextureSlot.bl_rna_get_subclass_py |

### References

| ParticleSettings.texture_slots ParticleSettingsTextureSlots.add | ParticleSettingsTextureSlots.create |

## ParticleSettingsTextureSlots(bpy_prop_collection)

### ParticleSettingsTextureSlots(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. ParticleSettingsTextureSlots ( bpy_prop_collection )

The set of texture slots

classmethod add ( )

add

Returns :

The newly initialized mtex

Return type :

ParticleSettingsTextureSlot

classmethod create ( index )

create

Parameters :

index ( int ) – Index, Slot index to initialize (in [0, inf])

Returns :

The newly initialized mtex

Return type :

ParticleSettingsTextureSlot

classmethod clear ( index )

clear

Parameters :

index ( int ) – Index, Slot index to clear (in [0, inf])

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

| ParticleSettings.texture_slots | |

## ParticleSystem(bpy_struct)

### ParticleSystem(bpy_struct)

base class — bpy_struct

class bpy.types. ParticleSystem ( bpy_struct )

A particle system attached to an object

active_particle_target

(readonly)

Type :

ParticleTarget

active_particle_target_index

(in [0, inf], default 0)

Type :

int

child_particles

Child particles generated by the particle system (default None, readonly)

Type :

bpy_prop_collection[ChildParticle]

child_seed

Where to start in the random number table for child particles, so a different random result comes out (in [0, inf], default 0)

Type :

int

cloth

Cloth dynamics for hair (readonly, never None)

Type :

ClothModifier

dt_frac

Current size of the simulation time step, expressed as a fraction of a frame (in [0.00990099, 1], default 0.0, readonly)

Type :

float

has_multiple_caches

Whether the particle system holds more than one point cache (default False, readonly)

Type :

bool

invert_vertex_group_clump

Reverse how the clump vertex group acts (default False)

Type :

bool

invert_vertex_group_density

Reverse how the density vertex group acts (default False)

Type :

bool

invert_vertex_group_field

Reverse how the field vertex group acts (default False)

Type :

bool

invert_vertex_group_kink

Reverse how the kink vertex group acts (default False)

Type :

bool

invert_vertex_group_length

Reverse how the length vertex group acts (default False)

Type :

bool

invert_vertex_group_rotation

Reverse how the rotation vertex group acts (default False)

Type :

bool

invert_vertex_group_roughness_1

Reverse how the roughness 1 vertex group acts (default False)

Type :

bool

invert_vertex_group_roughness_2

Reverse how the roughness 2 vertex group acts (default False)

Type :

bool

invert_vertex_group_roughness_end

Reverse how the roughness end vertex group acts (default False)

Type :

bool

invert_vertex_group_size

Reverse how the size vertex group acts (default False)

Type :

bool

invert_vertex_group_tangent

Reverse how the tangent vertex group acts (default False)

Type :

bool

invert_vertex_group_twist

Reverse how the twist vertex group acts (default False)

Type :

bool

invert_vertex_group_velocity

Reverse how the velocity vertex group acts (default False)

Type :

bool

is_editable

Whether the particle system can be edited in particle mode (default False, readonly)

Type :

bool

is_edited

Whether the particle system has already been edited in particle mode (default False, readonly)

Type :

bool

is_global_hair

Whether the hair keys live in global coordinate space (default False, readonly)

Type :

bool

name

Particle system name (default “”, never None)

Type :

str

parent

Use this object's coordinate system rather than the global one

Type :

Object

particles

Particles generated by the particle system (default None, readonly)

Type :

bpy_prop_collection[Particle]

point_cache

(readonly, never None)

Type :

PointCache

reactor_target_object

In reactor systems, the object holding the target particle system

Type :

Object

reactor_target_particle_system

In reactor systems, the index of the particle system on the target object (in [1, 32767], default 0)

Type :

int

seed

Where to start in the random number table, so a different random result comes out (in [0, inf], default 0)

Type :

int

settings

Particle system settings (never None)

Type :

ParticleSettings

targets

Target particle systems (default None, readonly)

Type :

bpy_prop_collection[ParticleTarget]

use_hair_dynamics

Turn on hair dynamics driven by cloth simulation (default False)

Type :

bool

use_keyed_timing

Use key times (default False)

Type :

bool

vertex_group_clump

Channel driving clump, taken from a vertex group (default “”, never None)

Type :

str

vertex_group_density

Channel driving density, taken from a vertex group (default “”, never None)

Type :

str

vertex_group_field

Channel driving field, taken from a vertex group (default “”, never None)

Type :

str

vertex_group_kink

Channel driving kink, taken from a vertex group (default “”, never None)

Type :

str

vertex_group_length

Channel driving length, taken from a vertex group (default “”, never None)

Type :

str

vertex_group_rotation

Channel driving rotation, taken from a vertex group (default “”, never None)

Type :

str

vertex_group_roughness_1

Channel driving roughness 1, taken from a vertex group (default “”, never None)

Type :

str

vertex_group_roughness_2

Channel driving roughness 2, taken from a vertex group (default “”, never None)

Type :

str

vertex_group_roughness_end

Channel driving roughness end, taken from a vertex group (default “”, never None)

Type :

str

vertex_group_size

Channel driving size, taken from a vertex group (default “”, never None)

Type :

str

vertex_group_tangent

Channel driving tangent, taken from a vertex group (default “”, never None)

Type :

str

vertex_group_twist

Channel driving twist, taken from a vertex group (default “”, never None)

Type :

str

vertex_group_velocity

Channel driving velocity, taken from a vertex group (default “”, never None)

Type :

str

co_hair ( object , * , particle_no = 0 , step = 0 )

Read back cached hair data

Parameters :

- object (Object) – Object (never None)

- particle_no ( int ) – Particle no, (in [-inf, inf], optional)

- step ( int ) – step no, (in [-inf, inf], optional)

Returns :

Co, Exported hairkey location (array of 3 items, in [-inf, inf])

Return type :

mathutils.Vector

uv_on_emitter ( modifier , particle , * , particle_no = 0 , uv_no = 0 )

Read back the uv for every particle

Parameters :

- modifier (ParticleSystemModifier) – Particle modifier (never None)

- particle (Particle) – Particle (never None)

- particle_no ( int ) – Particle no, (in [-inf, inf], optional)

- uv_no ( int ) – UV no, (in [-inf, inf], optional)

Returns :

uv, (array of 2 items, in [-inf, inf])

Return type :

mathutils.Vector

mcol_on_emitter ( modifier , particle , * , particle_no = 0 , vcol_no = 0 )

Read back the mcol for every particle

Parameters :

- modifier (ParticleSystemModifier) – Particle modifier (never None)

- particle (Particle) – Particle (never None)

- particle_no ( int ) – Particle no, (in [-inf, inf], optional)

- vcol_no ( int ) – vcol no, (in [-inf, inf], optional)

Returns :

mcol, (array of 3 items, in [0, inf])

Return type :

mathutils.Color

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

| bpy.context.particle_system bpy.context.particle_system_editable DepsgraphObjectInstance.particle_system DynamicPaintBrushSettings.particle_system FluidFlowSettings.particle_system | Object.particle_systems ParticleInstanceModifier.particle_system ParticleSystemModifier.particle_system ParticleSystems.active |

## ParticleSystems(bpy_prop_collection)

### ParticleSystems(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. ParticleSystems ( bpy_prop_collection )

The set of particle systems

active

Active particle system being displayed (readonly)

Type :

ParticleSystem

active_index

Index of active particle system slot (in [0, inf], default 0)

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

| Object.particle_systems | |

## ParticleTarget(bpy_struct)

### ParticleTarget(bpy_struct)

base class — bpy_struct

class bpy.types. ParticleTarget ( bpy_struct )

A particle system designated as a target

alliance

(default 'NEUTRAL' )

Type :

Literal[‘FRIEND’, ‘NEUTRAL’, ‘ENEMY’]

duration

(in [0, 1.04857e+06], default 0.0)

Type :

float

is_valid

Whether the keyed-particles target is valid (default False)

Type :

bool

name

Particle target name (default “”, readonly, never None)

Type :

str

object

The object holding the target particle system (left empty if it is the same object)

Type :

Object

system

Index of the particle system on the target object (in [1, inf], default 0)

Type :

int

time

(in [0, 1.04857e+06], default 0.0)

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

| ParticleSystem.active_particle_target | ParticleSystem.targets |

## PathCompare(bpy_struct)

### PathCompare(bpy_struct)

base class — bpy_struct

class bpy.types. PathCompare ( bpy_struct )

A value that paths are tested against

path

(default “”, never None)

Type :

str

use_glob

Allow wildcard globbing (default False)

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

| PathCompareCollection.new PathCompareCollection.remove | Preferences.autoexec_paths |

## PathCompareCollection(bpy_prop_collection)

### PathCompareCollection(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. PathCompareCollection ( bpy_prop_collection )

The set of paths

classmethod new ( )

Add a new path

Return type :

PathCompare

classmethod remove ( pathcmp )

Remove path

Parameters :

pathcmp (PathCompare) – (never None)

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

| Preferences.autoexec_paths | |
