# Palettecolor Bpy Struct, Palettecolors Bpy Prop Collection, Particle Bpy Struct, Particlebrush Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: PaletteColor(bpy_struct); PaletteColors(bpy_prop_collection); Particle(bpy_struct); ParticleBrush(bpy_struct); ParticleDupliWeight(bpy_struct); ParticleEdit(bpy_struct); ParticleHairKey(bpy_struct); ParticleKey(bpy_struct).

## PaletteColor(bpy_struct)

### PaletteColor(bpy_struct) 

base class — bpy_struct

class bpy.types. PaletteColor ( bpy_struct ) 

color 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

strength 

(in [0, 1], default 0.0)

Type :

float

weight 

(in [0, 1], default 0.0)

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

| Palette.colors PaletteColors.active | PaletteColors.new PaletteColors.remove |

## PaletteColors(bpy_prop_collection)

### PaletteColors(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. PaletteColors ( bpy_prop_collection ) 

The set of colors held by a palette

active 

Type :

PaletteColor

new ( ) 

Append a fresh color to the palette

Returns :

The newly created color

Return type :

PaletteColor

remove ( color ) 

Drop a color from the palette

Parameters :

color (PaletteColor) – The color to remove (never None)

clear ( ) 

Drop every color from the palette

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

| Palette.colors | |

## Particle(bpy_struct)

### Particle(bpy_struct)

base class — bpy_struct

class bpy.types. Particle ( bpy_struct )

A single particle belonging to a particle system

alive_state

(default 'DEAD' )

Type :

Literal[‘DEAD’, ‘UNBORN’, ‘ALIVE’, ‘DYING’]

angular_velocity

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

birth_time

(in [-inf, inf], default 0.0)

Type :

float

die_time

(in [-inf, inf], default 0.0)

Type :

float

hair_keys

(default None, readonly)

Type :

bpy_prop_collection[ParticleHairKey]

is_exist

(default True, readonly)

Type :

bool

is_visible

(default True, readonly)

Type :

bool

lifetime

(in [-inf, inf], default 0.0)

Type :

float

location

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

particle_keys

(default None, readonly)

Type :

bpy_prop_collection[ParticleKey]

prev_angular_velocity

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

prev_location

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

prev_rotation

(array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

mathutils.Quaternion

prev_velocity

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

rotation

(array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

mathutils.Quaternion

size

(in [-inf, inf], default 0.0)

Type :

float

velocity

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

uv_on_emitter ( modifier )

Look up the UV coordinates of a particle on an evaluated mesh.

Parameters :

modifier (ParticleSystemModifier) – Particle modifier from an evaluated object (never None)

Returns :

uv, (array of 2 items, in [-inf, inf])

Return type :

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

| ParticleHairKey.co_object ParticleHairKey.co_object_set ParticleSystem.mcol_on_emitter | ParticleSystem.particles ParticleSystem.uv_on_emitter |

## ParticleBrush(bpy_struct)

### ParticleBrush(bpy_struct)

base class — bpy_struct

class bpy.types. ParticleBrush ( bpy_struct )

Brush used when editing particles

count

Particle count (in [1, 1000], default 10)

Type :

int

curve

(readonly)

Type :

CurveMapping

length_mode

(default 'GROW' )

- GROW
Grow – Lengthen the hairs.

- SHRINK
Shrink – Shorten the hairs.

Type :

Literal[‘GROW’, ‘SHRINK’]

puff_mode

(default 'ADD' )

- ADD
Add – Increase how puffy the hairs are.

- SUB
Sub – Decrease how puffy the hairs are.

Type :

Literal[‘ADD’, ‘SUB’]

size

Radius of the brush in pixels (in [1, 32767], default 50)

Type :

int

steps

Brush steps (in [1, 32767], default 10)

Type :

int

strength

Brush strength (in [0.001, 1], default 0.5)

Type :

float

use_puff_volume

Extend puffing to the unselected endpoints as well, which helps keep hair volume when the root is puffed (default False)

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

| ParticleEdit.brush | |

## ParticleDupliWeight(bpy_struct)

### ParticleDupliWeight(bpy_struct)

base class — bpy_struct

class bpy.types. ParticleDupliWeight ( bpy_struct )

How heavily a given instance object is weighted within a collection

count

How often this object recurs relative to the other objects (in [0, 32767], default 0)

Type :

int

name

Particle instance object name (default “”, readonly, never None)

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

| ParticleSettings.active_instanceweight | ParticleSettings.instance_weights |

## ParticleEdit(bpy_struct)

### ParticleEdit(bpy_struct)

base class — bpy_struct

class bpy.types. ParticleEdit ( bpy_struct )

Settings that apply while in particle editing mode

brush

(readonly)

Type :

ParticleBrush

default_key_count

Number of keys assigned to newly created particles (in [2, 32767], default 5)

Type :

int

display_step

Number of steps used to draw the path (in [1, 10], default 2)

Type :

int

emitter_distance

How far particles are kept from the emitter (in [-inf, inf], default 0.25)

Type :

float

fade_frames

Number of frames over which to fade (in [1, 100], default 2)

Type :

int

is_editable

Whether a usable edit mode is present (default False, readonly)

Type :

bool

is_hair

Whether hair is being edited (default False, readonly)

Type :

bool

object

The edited object (readonly)

Type :

Object

select_mode

Selection and display mode for particles (default 'PATH' )

- PATH
Path – Path edit mode.

- POINT
Point – Point select mode.

- TIP
Tip – Tip select mode.

Type :

Literal[‘PATH’, ‘POINT’, ‘TIP’]

shape_object

Outer shape to use for tools

Type :

Object

show_particles

Display actual particles (default False)

Type :

bool

tool

(default 'COMB' )

- COMB
Comb – Comb hairs.

- SMOOTH
Smooth – Smooth hairs.

- ADD
Add – Add hairs.

- LENGTH
Length – Make hairs longer or shorter.

- PUFF
Puff – Make hairs stand up.

- CUT
Cut – Cut hairs.

- WEIGHT
Weight – Weight hair particles.

Type :

Literal[‘COMB’, ‘SMOOTH’, ‘ADD’, ‘LENGTH’, ‘PUFF’, ‘CUT’, ‘WEIGHT’]

type

(default 'PARTICLES' )

Type :

Literal[‘PARTICLES’, ‘`SOFT_BODY`’, ‘CLOTH’]

use_auto_velocity

Work out point velocities on their own (default True)

Type :

bool

use_default_interpolate

Derive new particles by interpolating the existing ones (default False)

Type :

bool

use_emitter_deflect

Stop paths from cutting through the emitter (default True)

Type :

bool

use_fade_time

Dim paths and keys the farther they are from the current frame (default False)

Type :

bool

use_preserve_length

Hold path lengths fixed (default True)

Type :

bool

use_preserve_root

Leave the root keys untouched (default True)

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

| ToolSettings.particle_edit | |

## ParticleHairKey(bpy_struct)

### ParticleHairKey(bpy_struct)

base class — bpy_struct

class bpy.types. ParticleHairKey ( bpy_struct )

A particle key belonging to a hair particle system

co

Where the hair key sits in object space (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

co_local

Position of the hair key within its own local frame, measured against the emitting face (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

time

Where the key falls along the hair length, as a relative time (in [0, inf], default 0.0)

Type :

float

weight

Weight for cloth simulation (in [0, 1], default 0.0)

Type :

float

co_object ( object , modifier , particle )

Read back a hairkey position using particle and modifier data

Parameters :

- object (Object) – Object (never None)

- modifier (ParticleSystemModifier) – Particle modifier (never None)

- particle (Particle) – hair particle (never None)

Returns :

Co, Exported hairkey location (array of 3 items, in [-inf, inf])

Return type :

mathutils.Vector

co_object_set ( object , modifier , particle , co )

Write a hairkey position using particle and modifier data

Parameters :

- object (Object) – Object (never None)

- modifier (ParticleSystemModifier) – Particle modifier (never None)

- particle (Particle) – hair particle (never None)

- co (mathutils.Vector) – Co, Specified hairkey location (array of 3 items, in [-inf, inf])

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

| Particle.hair_keys | |

## ParticleKey(bpy_struct)

### ParticleKey(bpy_struct)

base class — bpy_struct

class bpy.types. ParticleKey ( bpy_struct )

Where a particle is keyed at a moment in time

angular_velocity

Key angular velocity (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

location

Key location (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

rotation

Key rotation quaternion (array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

mathutils.Quaternion

time

When the key occurs in the simulation (in [0, inf], default 0.0)

Type :

float

velocity

Key velocity (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

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

| Particle.particle_keys | |
