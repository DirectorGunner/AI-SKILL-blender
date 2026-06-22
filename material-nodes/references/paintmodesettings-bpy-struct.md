# Paintmodesettings Bpy Struct, Particlesettings Id, Pointcloud Id

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: PaintModeSettings(bpy_struct); ParticleSettings(ID); PointCloud(ID).

## PaintModeSettings(bpy_struct)

### PaintModeSettings(bpy_struct) 

base class — bpy_struct

class bpy.types. PaintModeSettings ( bpy_struct ) 

Settings that govern paint mode

canvas_image 

Image that serves as the painting target

Type :

Image

canvas_source 

Where the canvas is taken from (default 'MATERIAL' )

Type :

Literal[‘`COLOR_ATTRIBUTE`’, ‘MATERIAL’, ‘IMAGE’]

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

| ToolSettings.paint_mode | |

## ParticleSettings(ID)

### ParticleSettings(ID)

base classes — bpy_struct, ID

class bpy.types. ParticleSettings ( ID )

A shareable particle settings block that several particle systems can draw on

active_instanceweight

(readonly)

Type :

ParticleDupliWeight

active_instanceweight_index

(in [0, inf], default 0)

Type :

int

active_texture

Active texture slot being displayed

Type :

Texture

active_texture_index

Index of active texture slot (in [0, 17], default 0)

Type :

int

adaptive_angle

Degrees of path curvature needed before another render segment is added (in [0, 45], default 5)

Type :

int

adaptive_pixel

Pixels of path coverage needed before another render segment is added (in [0, 50], default 3)

Type :

int

angular_velocity_factor

Angular velocity amount (in radians per second) (in [-200, 200], default 0.0)

Type :

float

angular_velocity_mode

Which axis drives the change in particle rotation over time (default 'VELOCITY' )

Type :

Literal[‘NONE’, ‘VELOCITY’, ‘HORIZONTAL’, ‘VERTICAL’, ‘`GLOBAL_X`’, ‘`GLOBAL_Y`’, ‘`GLOBAL_Z`’, ‘RAND’]

animation_data

Animation data for this data-block (readonly)

Type :

AnimData

apply_effector_to_children

Apply effectors to children (default False)

Type :

bool

apply_guide_to_children

(default False)

Type :

bool

bending_random

Random stiffness of hairs (in [0, 1], default 0.0)

Type :

float

boids

(readonly)

Type :

BoidSettings

branch_threshold

Threshold of branching (in [0, 1], default 0.0)

Type :

float

brownian_factor

How much random, jittery motion the particles get (in [0, 200], default 0.0)

Type :

float

child_length

Length of child paths (in [0, 1], default 1.0)

Type :

float

child_length_threshold

Share of particles the child path length leaves alone (in [0, 1], default 0.0)

Type :

float

child_parting_factor

Add parting to the children, derived from the parent strands (in [0, 1], default 0.0)

Type :

float

child_parting_max

Maximum root to tip angle (tip distance/root distance for long hair) (in [0, 180], default 0.0)

Type :

float

child_parting_min

Minimum root to tip angle (tip distance/root distance for long hair) (in [0, 180], default 0.0)

Type :

float

child_percent

Number of children per parent (in [0, 100000], default 10)

Type :

int

child_radius

Radius of children around parent (in [0, 100000], default 0.2)

Type :

float

child_roundness

Roundness of children around parent (in [0, 1], default 0.0)

Type :

float

child_size

Scale factor applied to the child particle size (in [0.001, 100000], default 1.0)

Type :

float

child_size_random

Random spread in the size of the child particles (in [0, 1], default 0.0)

Type :

float

child_type

Create child particles (default 'NONE' )

Type :

Literal[‘NONE’, ‘SIMPLE’, ‘INTERPOLATED’]

clump_curve

Curve defining clump tapering (readonly)

Type :

CurveMapping

clump_factor

Amount of clumping (in [-1, 1], default 0.0)

Type :

float

clump_noise_size

Size of clump noise (in [1e-05, 100000], default 1.0)

Type :

float

clump_shape

Shape of clumping (in [-0.999, 0.999], default 0.0)

Type :

float

collision_collection

Limit colliders to this collection

Type :

Collection

color_maximum

Maximum length of the particle color vector (in [0.01, 100], default 1.0)

Type :

float

count

Total number of particles (in [0, inf], default 1000)

Type :

int

courant_target

How far a particle may travel before extra subframes are demanded (the target Courant number); staying within 0.01 to 0.3 is advised (in [0.0001, 10], default 0.2)

Type :

float

create_long_hair_children

Compute children that work well for long hair (default False)

Type :

bool

damping

Amount of damping (in [0, 1], default 0.0)

Type :

float

display_color

Show extra particle data tinted as a color (default 'MATERIAL' )

Type :

Literal[‘NONE’, ‘MATERIAL’, ‘VELOCITY’, ‘ACCELERATION’]

display_method

How particles are displayed in viewport (default 'RENDER' )

Type :

Literal[‘NONE’, ‘RENDER’, ‘DOT’, ‘CIRC’, ‘CROSS’, ‘AXIS’]

display_percentage

Share of particles shown in the 3D view (in [0, 100], default 100)

Type :

int

display_size

Size of particles on viewport (in [0, 1000], default 0.1)

Type :

float

display_step

Number of steps (as a power of 2) used when drawing paths (in [0, 10], default 2)

Type :

int

distribution

How particles are spread across the chosen element (default 'JIT' )

Type :

Literal[‘JIT’, ‘RAND’, ‘GRID’]

drag_factor

Amount of air drag (in [0, 1], default 0.0)

Type :

float

effect_hair

Hair stiffness for effectors (in [0, 1], default 0.0)

Type :

float

effector_amount

How many of the particles act as effectors (0 makes every particle one) (in [0, 10000], default 0)

Type :

int

effector_weights

(readonly)

Type :

EffectorWeights

emit_from

Source the particles are emitted from (default 'FACE' )

Type :

Literal[‘VERT’, ‘FACE’, ‘VOLUME’]

factor_random

Add a random spread to the starting velocity (in [0, 200], default 0.0)

Type :

float

fluid

(readonly)

Type :

SPHFluidSettings

force_field_1

(readonly)

Type :

FieldSettings

force_field_2

(readonly)

Type :

FieldSettings

frame_end

Frame number to stop emitting particles (in [-1.04857e+06, 1.04857e+06], default 200.0)

Type :

float

frame_start

Frame number to start emitting particles (in [-1.04857e+06, 1.04857e+06], default 1.0)

Type :

float

grid_random

Offset the grid locations by a random amount (in [0, 1], default 0.0)

Type :

float

grid_resolution

How finely the particle grid is resolved (in [1, 250], default 10)

Type :

int

hair_length

Length of the hair (in [0, 1000], default 0.0)

Type :

float

hair_step

Number of hair segments (in [2, 32767], default 5)

Type :

int

hexagonal_grid

Lay out the grid hexagonally (default False)

Type :

bool

instance_collection

Display objects from this collection instead of particles

Type :

Collection

instance_object

Display this object instead of particles

Type :

Object

instance_weights

Per-object weighting across the entire instance collection (default None, readonly)

Type :

bpy_prop_collection[ParticleDupliWeight]

integrator

Method used to solve the physics, ordered fastest to most stable and precise: Midpoint, Euler, Verlet, RK4 (default 'MIDPOINT' )

Type :

Literal[‘EULER’, ‘VERLET’, ‘MIDPOINT’, ‘RK4’]

invert_grid

Swap which side counts as object and which does not (default False)

Type :

bool

is_fluid

Whether the particles came from a fluid simulation (default False, readonly)

Type :

bool

jitter_factor

How much jitter the sampling receives (in [0, 2], default 1.0)

Type :

float

keyed_loops

Number of times the keys are looped (in [1, 10000], default 1)

Type :

int

keys_step

(in [0, 32767], default 5)

Type :

int

kink

Type of periodic offset on the path (default 'NO' )

Type :

Literal[‘NO’, ‘CURL’, ‘RADIAL’, ‘WAVE’, ‘BRAID’, ‘SPIRAL’]

kink_amplitude

The amplitude of the offset (in [-100000, 100000], default 0.2)

Type :

float

kink_amplitude_clump

Degree to which clump influences the kink amplitude (in [0, 1], default 1.0)

Type :

float

kink_amplitude_random

Random variation of the amplitude (in [0, 1], default 0.0)

Type :

float

kink_axis

Which axis to use for offset (default 'Z' )

Type :

Literal[Axis Xyz Items]

kink_axis_random

Random variation of the orientation (in [0, 1], default 0.0)

Type :

float

kink_extra_steps

Additional steps to resolve special kink features (in [1, inf], default 4)

Type :

int

kink_flat

How flat the hairs are (in [0, 1], default 0.0)

Type :

float

kink_frequency

The frequency of the offset (1/total length) (in [-100000, 100000], default 2.0)

Type :

float

kink_shape

Bias the offset toward the start or end (in [-0.999, 0.999], default 0.0)

Type :

float

length_random

Add a random spread to the path length (in [0, 1], default 0.0)

Type :

float

lifetime

Life span of the particles (in [1, 1.04857e+06], default 50.0)

Type :

float

lifetime_random

Add a random spread to the particle lifetime (in [0, 1], default 0.0)

Type :

float

line_length_head

Length of the line’s head (in [0, 100000], default 0.0)

Type :

float

line_length_tail

Length of the line’s tail (in [0, 100000], default 0.0)

Type :

float

lock_boids_to_surface

Hold boids to a surface (default False)

Type :

bool

mass

Mass of the particles (in [1e-08, 100000], default 1.0)

Type :

float

material

Index of material slot used for rendering particles (in [1, 32767], default 1)

Type :

int

material_slot

Material slot used for rendering particles (default 'DEFAULT' )

Type :

Literal[‘DEFAULT’]

normal_factor

Have the surface normal seed the particle's starting velocity (in [-1000, 1000], default 1.0)

Type :

float

object_align_factor

Have the emitter object's orientation seed the particle's starting velocity (array of 3 items, in [-200, 200], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

object_factor

Have the object seed the particle's starting velocity (in [-200, 200], default 0.0)

Type :

float

particle_factor

Have the target particle seed the particle's starting velocity (in [-200, 200], default 0.0)

Type :

float

particle_size

The size of the particles (in [0.001, 100000], default 0.05)

Type :

float

path_end

End time of path (in [-inf, inf], default 1.0)

Type :

float

path_start

Starting time of path (in [-inf, inf], default 0.0)

Type :

float

phase_factor

Rotation about the selected orientation axis (in [-1, 1], default 0.0)

Type :

float

phase_factor_random

Randomize the rotation about the selected orientation axis (in [0, 2], default 0.0)

Type :

float

physics_type

Particle physics type (default 'NEWTON' )

Type :

Literal[‘NO’, ‘NEWTON’, ‘KEYED’, ‘BOIDS’, ‘FLUID’]

radius_scale

Multiplier of diameter properties (in [0, inf], default 0.01)

Type :

float

react_event

Which event on the target particles to respond to (default 'DEATH' )

Type :

Literal[‘DEATH’, ‘COLLIDE’, ‘NEAR’]

reactor_factor

Have the vector pointing away from the target particle's position seed the particle's starting velocity (in [-10, 10], default 0.0)

Type :

float

render_step

Number of steps (as a power of 2) used when rendering paths (in [0, 20], default 3)

Type :

int

render_type

How particles are rendered (default 'HALO' )

Type :

Literal[‘NONE’, ‘HALO’, ‘LINE’, ‘PATH’, ‘OBJECT’, ‘COLLECTION’]

rendered_child_count

Number of children per parent for rendering (in [0, 100000], default 100)

Type :

int

root_radius

Strand diameter width at the root (in [0, inf], default 1.0)

Type :

float

rotation_factor_random

Randomize particle orientation (in [0, 1], default 0.0)

Type :

float

rotation_mode

Axis the particle is oriented to (has no bearing on the Explode modifier output) (default 'VEL' )

Type :

Literal[‘NONE’, ‘NOR’, ‘`NOR_TAN`’, ‘VEL’, ‘`GLOB_X`’, ‘`GLOB_Y`’, ‘`GLOB_Z`’, ‘`OB_X`’, ‘`OB_Y`’, ‘`OB_Z`’]

roughness_1

Amount of location dependent roughness (in [0, 100000], default 0.0)

Type :

float

roughness_1_size

Size of location dependent roughness (in [0.01, 100000], default 1.0)

Type :

float

roughness_2

Amount of random roughness (in [0, 100000], default 0.0)

Type :

float

roughness_2_size

Size of random roughness (in [0.01, 100000], default 1.0)

Type :

float

roughness_2_threshold

Share of particles the random roughness leaves alone (in [0, 1], default 0.0)

Type :

float

roughness_curve

Curve defining roughness (readonly)

Type :

CurveMapping

roughness_end_shape

Shape of endpoint roughness (in [0, 10], default 1.0)

Type :

float

roughness_endpoint

Amount of endpoint roughness (in [0, 100000], default 0.0)

Type :

float

shape

Strand shape parameter (in [-1, 1], default 0.0)

Type :

float

show_guide_hairs

Show guide hairs (default False)

Type :

bool

show_hair_grid

Show hair simulation grid (default False)

Type :

bool

show_health

Display boid health (default False)

Type :

bool

show_number

Show particle number (default False)

Type :

bool

show_size

Show particle size (default False)

Type :

bool

show_unborn

Display particles ahead of their emission (default False)

Type :

bool

show_velocity

Show particle velocity (default False)

Type :

bool

size_random

Add a random spread to the particle size (in [0, 1], default 0.0)

Type :

float

subframes

Subframes simulated for steadier results and finer detail (dt = timestep / (subframes + 1)) (in [0, 1000], default 0)

Type :

int

tangent_factor

Have the surface tangent seed the particle's starting velocity (in [-1000, 1000], default 0.0)

Type :

float

tangent_phase

Rotate the surface tangent (in [-1, 1], default 0.0)

Type :

float

texture_slots

Texture slots defining the mapping and influence of textures (default None, readonly)

Type :

ParticleSettingsTextureSlots[ParticleSettingsTextureSlot]

time_tweak

Scale factor for the physics timestep (1.0 means one frame = 1/25 seconds) (in [0, 100], default 1.0)

Type :

float

timestep

The simulation timestep per frame (seconds per frame) (in [0.0001, 100], default 0.0)

Type :

float

tip_radius

Strand diameter width at the tip (in [0, inf], default 0.0)

Type :

float

trail_count

Number of trail particles (in [1, 100000], default 0)

Type :

int

twist

How many turns the strand makes around its parent (in [-100000, 100000], default 0.0)

Type :

float

twist_curve

Curve defining twist (readonly)

Type :

CurveMapping

type

Particle type (default 'EMITTER' )

Type :

Literal[‘EMITTER’, ‘HAIR’]

use_absolute_path_time

Time the path in absolute frames (default False)

Type :

bool

use_adaptive_subframes

Set the subframe count automatically (default False)

Type :

bool

use_advanced_hair

Grow hair with the full physics solver (default False)

Type :

bool

use_close_tip

Drive the tip radius to zero (default True)

Type :

bool

use_clump_curve

Define clump tapering with a curve (default False)

Type :

bool

use_clump_noise

Scatter random clumps around the parent (default False)

Type :

bool

use_collection_count

Reuse an object several times within the one collection (default False)

Type :

bool

use_collection_pick_random

Draw objects from the collection at random (default False)

Type :

bool

use_dead

Keep showing particles once they have died (default False)

Type :

bool

use_die_on_collision

Make particles die on contact with a deflector object (default False)

Type :

bool

use_dynamic_rotation

Let collisions and effectors drive the particle rotations (default False)

Type :

bool

use_emit_random

Emit from elements in random order (default True)

Type :

bool

use_even_distribution

Spread evenly across faces using face area or edge length (default True)

Type :

bool

use_global_instance

Duplicate using the object's global coordinates (default False)

Type :

bool

use_hair_bspline

Smooth hair interpolation with B-Splines (default False)

Type :

bool

use_modifier_stack

Emit particles from the modified mesh (matching the subdivision surface level between viewport and render keeps results correct) (default False)

Type :

bool

use_multiply_size_mass

Scale mass by particle size (default False)

Type :

bool

use_parent_particles

Render parent particles (default False)

Type :

bool

use_react_multiple

React multiple times (default False)

Type :

bool

use_react_start_end

Eventually spawn particles that never reacted (default False)

Type :

bool

use_regrow_hair

Regrow hair for each frame (default False)

Type :

bool

use_render_adaptive

Display steps of the particle path (default False)

Type :

bool

use_rotation_instance

Duplicate using the object's rotation (the global x-axis lines up with the particle rotation axis) (default False)

Type :

bool

use_rotations

Compute particle rotations (default False)

Type :

bool

use_roughness_curve

Define roughness with a curve (default False)

Type :

bool

use_scale_instance

Duplicate using the object's scale (default True)

Type :

bool

use_self_effect

Let particle effectors act on themselves (default False)

Type :

bool

use_size_deflect

Factor the particle's size into deflection (default False)

Type :

bool

use_strand_primitive

Render with the strand primitive (default False)

Type :

bool

use_twist_curve

Define twist with a curve (default False)

Type :

bool

use_velocity_length

Scale line length by particle speed (default False)

Type :

bool

use_whole_collection

Use the entire collection at once (default False)

Type :

bool

userjit

Emission locations per face (0 = automatic) (in [0, 1000], default 0)

Type :

int

virtual_parents

Relative amount of virtual parents (in [0, 1], default 0.0)

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

- default (type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| bpy.context.particle_settings BlendData.particles BlendDataParticles.new | BlendDataParticles.remove ParticleSystem.settings |

## PointCloud(ID)

### PointCloud(ID)

base classes — bpy_struct, ID

class bpy.types. PointCloud ( ID )

Data-block that stores a point cloud.

animation_data

Animation data attached to this data-block (readonly)

Type :

AnimData

attributes

Attributes defined on the geometry (default None, readonly)

Type :

AttributeGroupPointCloud[Attribute]

color_attributes

Color attributes carried by the geometry (default None, readonly)

Type :

AttributeGroupPointCloud[Attribute]

materials

(default None, readonly)

Type :

IDMaterials[Material]

points

(default None, readonly)

Type :

bpy_prop_collection[Point]

resize ( size )

Change the stored point count.

Parameters :

size ( int ) – Size, New number of points (in [0, inf])

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

| bpy.context.pointcloud BlendData.pointclouds | BlendDataPointClouds.new BlendDataPointClouds.remove |

## See also

- [Bpy Struct](bpy-struct.md)
