# Fluiddomainsettings Bpy Struct (part 2)

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

Type :

bpy_prop_array[float]

time_scale

Tune how quickly the simulation runs (in [0.0001, 10], default 1.0)

Type :

float

timesteps_max

Largest number of solver steps allowed within a single frame (in [1, 100], default 4)

Type :

int

timesteps_min

Smallest number of solver steps allowed within a single frame (in [1, 100], default 1)

Type :

int

use_adaptive_domain

Let the domain's resolution and extent follow the fluid (default False)

Type :

bool

use_adaptive_timesteps

Let Blender choose on its own when several solver steps per frame are needed (default True)

Type :

bool

use_bubble_particles

Create bubble particle system (default False)

Type :

bool

use_collision_border_back

Enable collisions with back domain border (default False)

Type :

bool

use_collision_border_bottom

Enable collisions with bottom domain border (default False)

Type :

bool

use_collision_border_front

Enable collisions with front domain border (default False)

Type :

bool

use_collision_border_left

Enable collisions with left domain border (default False)

Type :

bool

use_collision_border_right

Enable collisions with right domain border (default False)

Type :

bool

use_collision_border_top

Enable collisions with top domain border (default False)

Type :

bool

use_color_ramp

Display a simulation field by mapping its voxel values either through a ramp's colors or through a fixed color code (default False)

Type :

bool

use_diffusion

Turn on the fluid diffusion settings, such as viscosity and surface tension (default False)

Type :

bool

use_dissolve_smoke

Let smoke disappear over time (default False)

Type :

bool

use_dissolve_smoke_log

Fade smoke logarithmically, so it thins out fast at first yet lingers afterward (default True)

Type :

bool

use_flip_particles

Create liquid particle system (default False)

Type :

bool

use_foam_particles

Create foam particle system (default False)

Type :

bool

use_fractions

Use fractional obstacles to refine and smooth the fluid-obstacle boundary (default False)

Type :

bool

use_guide

Enable fluid guiding (default False)

Type :

bool

use_mesh

Enable fluid mesh (using amplification) (default True)

Type :

bool

use_noise

Enable fluid noise (using amplification) (default False)

Type :

bool

use_slice

Perform a single slice of the domain object (default False)

Type :

bool

use_speed_vectors

Stores mesh vertex velocities, which are applied automatically when rendering with motion blur turned on (default False)

Type :

bool

use_spray_particles

Create spray particle system (default False)

Type :

bool

use_tracer_particles

Create tracer particle system (default False)

Type :

bool

use_viscosity

Run highly viscous fluids through a dedicated solver (default False)

Type :

bool

vector_display_type

(default 'NEEDLE' )

- NEEDLE
Needle – Display vectors as needles.

- STREAMLINE
Streamlines – Display vectors as streamlines.

- MAC
MAC Grid – Display vector field as MAC grid.

Type :

Literal[‘NEEDLE’, ‘STREAMLINE’, ‘MAC’]

vector_field

Which vector field the display vectors stand for (default '`FLUID_VELOCITY`' )

- `FLUID_VELOCITY`
Fluid Velocity – Velocity field of the fluid domain.

- `GUIDE_VELOCITY`
Guide Velocity – Guide velocity field of the fluid domain.

- FORCE
Force – Force field of the fluid domain.

Type :

Literal[‘`FLUID_VELOCITY`’, ‘`GUIDE_VELOCITY`’, ‘FORCE’]

vector_scale

Multiplier for scaling the vectors (in [0, 1000], default 1.0)

Type :

float

vector_scale_with_magnitude

Scale vectors with their magnitudes (default False)

Type :

bool

vector_show_mac_x

Show X-component of MAC Grid (default True)

Type :

bool

vector_show_mac_y

Show Y-component of MAC Grid (default True)

Type :

bool

vector_show_mac_z

Show Z-component of MAC Grid (default True)

Type :

bool

velocity_grid

Smoke velocity grid (array of 32 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

velocity_scale

Factor to control the amount of motion blur (in [0, inf], default 1.0)

Type :

float

viscosity_base

Viscosity setting: value that is multiplied by 10 to the power of (exponent*-1) (in [0, 10], default 1.0)

Type :

float

viscosity_exponent

Negative exponent for the viscosity value (to simplify entering small values e.g. 5*10^-6) (in [0, 10], default 6)

Type :

int

viscosity_value

Liquid viscosity; larger values give thicker fluids, and even 0 leaves a trace of viscosity (in [0, 10], default 0.05)

Type :

float

vorticity

How much swirl and turbulence the smoke carries (in [0, 4], default 0.0)

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

| FluidModifier.domain_settings | |
