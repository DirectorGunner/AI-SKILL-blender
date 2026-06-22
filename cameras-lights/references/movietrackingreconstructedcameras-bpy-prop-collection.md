# Movietrackingreconstructedcameras Bpy Prop Collection, Multiresmodifier Modifier, Normaleditmodifier Modifier, Objectlightlinking Bpy Struct ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: MovieTrackingReconstructedCameras(bpy_prop_collection); MultiresModifier(Modifier); NormalEditModifier(Modifier); ObjectLightLinking(bpy_struct); ObjectLineArt(bpy_struct); ObjectSolverConstraint(Constraint); ParticleInstanceModifier(Modifier); ParticleSystemModifier(Modifier).

## MovieTrackingReconstructedCameras(bpy_prop_collection)

### MovieTrackingReconstructedCameras(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MovieTrackingReconstructedCameras ( bpy_prop_collection )

Set of solved cameras

find_frame ( * , frame = 1 )

Find a reconstructed camera for a give frame number

Parameters :

frame ( int ) – Frame, Frame number to find camera for (in [0, 1048574], optional)

Returns :

Camera for a given frame

Return type :

MovieReconstructedCamera

matrix_from_frame ( * , frame = 1 )

Return interpolated camera matrix for a given frame

Parameters :

frame ( int ) – Frame, Frame number to find camera for (in [0, 1048574], optional)

Returns :

Matrix, Interpolated camera matrix for a given frame (multi-dimensional array of 4 * 4 items, in [-inf, inf])

Return type :

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

| MovieTrackingReconstruction.cameras | |

## MultiresModifier(Modifier)

### MultiresModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. MultiresModifier ( Modifier )

Modifier that supports several mesh resolution levels at once.

boundary_smooth

Sets the way smoothing is handled along open boundaries (default 'ALL' )

Type :

Literal[Subdivision Boundary Smooth Items]

filepath

Location of the external file holding displacement data (default “”, never None, blend relative // prefix supported)

Type :

str

is_external

When set, the multires displacements live in a separate file rather than the .blend, which reduces memory use (default False, readonly)

Type :

bool

levels

How many subdivision steps are shown in the viewport (in [0, 255], default 0)

Type :

int

quality

How precisely vertex positions are computed; lower numbers run quicker at the cost of exactness (in [1, 10], default 4)

Type :

int

render_levels

Subdivision level applied when rendering (in [0, 255], default 0)

Type :

int

sculpt_levels

How many subdivision steps apply while in sculpt mode (in [0, 255], default 0)

Type :

int

show_only_control_edges

Avoid drawing or rendering the inner subdivided edges (default True)

Type :

bool

total_levels

How many subdivision steps have displacement data retained for them (in [0, 255], default 0, readonly)

Type :

int

use_creases

Take mesh crease data into account to harden edges and corners (default True)

Type :

bool

use_custom_normals

Carry over any existing custom normals onto the resulting mesh (default False)

Type :

bool

use_sculpt_base_mesh

Have Sculpt Mode tools act on the base mesh while still previewing higher-level displacement (default False)

Type :

bool

uv_smooth

Sets how UVs get smoothed (default '`PRESERVE_BOUNDARIES`' )

Type :

Literal[Subdivision Uv Smooth Items]

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## NormalEditModifier(Modifier)

### NormalEditModifier(Modifier) 

base classes — bpy_struct, Modifier

class bpy.types. NormalEditModifier ( Modifier ) 

A modifier that generates or alters custom normals

invert_vertex_group 

Flip the sway of the vertex group (default False)

Type :

bool

mix_factor 

Proportion of the generated normals to blend over the existing ones (in [0, 1], default 1.0)

Type :

float

mix_limit 

Largest angle allowed between the old and new normals (in [0, 3.14159], default 3.14159)

Type :

float

mix_mode 

The way generated normals combine with the ones already there (default 'COPY' )

- COPY
Copy – Replace the existing normals with the new ones.

- ADD
Add – Write the sum of the new and old normals.

- SUB
Subtract – Write the new normals with the old ones taken away.

- MUL
Multiply – Write the product of old and new normals (not a cross product).

Type :

Literal[‘COPY’, ‘ADD’, ‘SUB’, ‘MUL’]

mode 

The approach used to generate or affect normals (default 'RADIAL' )

- RADIAL
Radial – Derived from an ellipsoid whose shape comes from the boundbox dimensions; a target is optional.

- DIRECTIONAL
Directional – Normals point toward (‘track’) the target object.

Type :

Literal[‘RADIAL’, ‘DIRECTIONAL’]

no_polynors_fix 

Leave polygons unflipped even where their normals disagree with the freshly computed custom vertex normals (default False)

Type :

bool

offset 

Displacement measured from the object's center (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

target 

The target object that drives the normals

Type :

Object

use_direction_parallel 

Apply one shared direction to every normal, running from the origin to the target's center (Directional mode only) (default True)

Type :

bool

vertex_group 

Name of the vertex group that picks out and weights the affected regions (default “”, never None)

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## ObjectLightLinking(bpy_struct)

### ObjectLightLinking(bpy_struct) 

base class — bpy_struct

class bpy.types. ObjectLightLinking ( bpy_struct ) 

blocker_collection 

Collection listing the objects that occlude light coming from this emitter

Type :

Collection

receiver_collection 

Collection that sets the light-linking relationship for this emitter

Type :

Collection

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

| Object.light_linking | |

## ObjectLineArt(bpy_struct)

### ObjectLineArt(bpy_struct) 

base class — bpy_struct

class bpy.types. ObjectLineArt ( bpy_struct ) 

Per-object Line Art settings

crease_threshold 

Any angle below this is handled as a crease (in [0, 3.14159], default 2.44346)

Type :

float

intersection_priority 

When lines cross, the intersection joins whichever object carries the larger intersection priority (in [0, 255], default 0)

Type :

int

usage 

Determines how Line Art treats this object during calculation (default 'INHERIT' )

- INHERIT
Inherit – Adopt the settings of the parent collection.

- INCLUDE
Include – Produce feature lines from this object's data.

- `OCCLUSION_ONLY`
Occlusion Only – Let the object data contribute occlusion alone.

- EXCLUDE
Exclude – Leave this object out of Line Art rendering.

- `INTERSECTION_ONLY`
Intersection Only – Emit intersection lines for this collection and nothing else.

- `NO_INTERSECTION`
No Intersection – Keep this object in but skip generating intersection lines.

- `FORCE_INTERSECTION`
Force Intersection – Produce intersection lines even against objects that have intersection turned off.

Type :

Literal[‘INHERIT’, ‘INCLUDE’, ‘`OCCLUSION_ONLY`’, ‘EXCLUDE’, ‘`INTERSECTION_ONLY`’, ‘`NO_INTERSECTION`’, ‘`FORCE_INTERSECTION`’]

use_crease_override 

Let this object's crease value take precedence over the scene-wide one (default False)

Type :

bool

use_intersection_priority_override 

Let this object's intersection priority take precedence over the collection's (default False)

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

| Object.lineart | |

## ObjectSolverConstraint(Constraint)

### ObjectSolverConstraint(Constraint) 

base classes — bpy_struct, Constraint

class bpy.types. ObjectSolverConstraint ( Constraint ) 

Tie motion to the movement of the reconstructed object

camera 

Camera the motion is parented to (the active scene camera is used when this is empty)

Type :

Object

clip 

Movie Clip that supplies the tracking data

Type :

MovieClip

object 

Movie tracking object to follow (default “”, never None)

Type :

str

set_inverse_pending 

Enable to ask for the inverse matrix to be recomputed (default False)

Type :

bool

use_active_clip 

Adopt the active clip set in the scene (default False)

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

## ParticleInstanceModifier(Modifier)

### ParticleInstanceModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. ParticleInstanceModifier ( Modifier )

A modifier that instances geometry across a particle system

axis

Pole axis for rotation (default 'Z' )

Type :

Literal[Axis Xyz Items]

index_layer_name

Name of the custom data layer holding the index (default “”, never None)

Type :

str

object

Object that has the particle system

Type :

Object

particle_amount

Fraction of particles used for instancing (in [0, 1], default 1.0)

Type :

float

particle_offset

Where, relatively, to start drawing particles for instancing, so several instances do not pile up (in [0, 1], default 0.0)

Type :

float

particle_system

Type :

ParticleSystem

particle_system_index

(in [1, 32767], default 1)

Type :

int

position

Position along path (in [0, 1], default 1.0)

Type :

float

random_position

Randomize position along path (in [0, 1], default 0.0)

Type :

float

random_rotation

Randomize rotation around path (in [0, 1], default 0.0)

Type :

float

rotation

Rotation around path (in [0, 1], default 0.0)

Type :

float

show_alive

Draw instances for particles that are alive (default True)

Type :

bool

show_dead

Draw instances for particles that are dead (default True)

Type :

bool

show_unborn

Draw instances for particles that are not yet born (default True)

Type :

bool

space

Coordinate space used when copying the mesh data (default 'WORLD' )

- LOCAL
Local – Take the offset from the particle object within the instance object.

- WORLD
World – Take the world-space offset within the instance object.

Type :

Literal[‘LOCAL’, ‘WORLD’]

use_children

Build instances from child particles (default False)

Type :

bool

use_normal

Build instances from normal particles (default True)

Type :

bool

use_path

Build instances along the particle paths (default False)

Type :

bool

use_preserve_shape

Leave the object unstretched (default False)

Type :

bool

use_size

Scale instances by particle size (default False)

Type :

bool

value_layer_name

Name of the custom data layer holding the randomized value (default “”, never None)

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## ParticleSystemModifier(Modifier)

### ParticleSystemModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. ParticleSystemModifier ( Modifier )

A modifier that runs a particle system simulation

particle_system

The particle system driven by this modifier (readonly, never None)

Type :

ParticleSystem

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

### References

| Particle.uv_on_emitter ParticleHairKey.co_object ParticleHairKey.co_object_set | ParticleSystem.mcol_on_emitter ParticleSystem.uv_on_emitter |
