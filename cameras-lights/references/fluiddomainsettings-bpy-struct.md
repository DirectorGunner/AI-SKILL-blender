# Fluiddomainsettings Bpy Struct (part 1)

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

### FluidDomainSettings(bpy_struct)

base class — bpy_struct

class bpy.types. FluidDomainSettings ( bpy_struct )

Settings that govern a fluid domain.

adapt_margin

Padding kept around the fluid so the domain boundary interferes less (in [2, 24], default 4)

Type :

int

adapt_threshold

Smallest amount of grid value (smoke density, fuel, heat) a cell may hold before that cell counts as empty (in [0, 1], default 0.002)

Type :

float

additional_res

Cap on how many extra cells may be added (in [0, 512], default 0)

Type :

int

alpha

Buoyancy driven by smoke density; raise it to make smoke climb faster (in [-5, 5], default 1.0)

Type :

float

beta

Buoyancy driven by smoke heat; raise it to make smoke climb faster (in [-5, 5], default 1.0)

Type :

float

burning_rate

How fast the reaction burns; raise it to get smaller flames (in [0.01, 4], default 0.75)

Type :

float

cache_data_format

Pick which file format stores cached volumetric data (default 'OPENVDB' )

- UNI
Uni Cache – Uni file format (.uni).

- OPENVDB
OpenVDB – OpenVDB file format (.vdb).

- RAW
Raw Cache – Raw file format (.raw).

Type :

Literal[‘UNI’, ‘OPENVDB’, ‘RAW’]

cache_directory

Directory that contains fluid cache files (default “”, never None, blend relative // prefix supported)

Type :

str

cache_frame_end

Frame at which the simulation halts (the last frame that is baked) (in [-1048574, 1048574], default 250)

Type :

int

cache_frame_offset

Offset applied when reading the simulation back from cache. Baking ignores it; only loading honors it. (in [-1048574, 1048574], default 0)

Type :

int

cache_frame_pause_data

(in [-inf, inf], default 0)

Type :

int

cache_frame_pause_guide

(in [-inf, inf], default 0)

Type :

int

cache_frame_pause_mesh

(in [-inf, inf], default 0)

Type :

int

cache_frame_pause_noise

(in [-inf, inf], default 0)

Type :

int

cache_frame_pause_particles

(in [-inf, inf], default 0)

Type :

int

cache_frame_start

Frame at which the simulation begins (the first frame that is baked) (in [-1048574, 1048574], default 1)

Type :

int

cache_mesh_format

Pick which file format stores cached surface data (default 'UNI' )

- UNI
Uni Cache – Uni file format (.uni).

- OPENVDB
OpenVDB – OpenVDB file format (.vdb).

- RAW
Raw Cache – Raw file format (.raw).

Type :

Literal[‘UNI’, ‘OPENVDB’, ‘RAW’]

cache_noise_format

Pick which file format stores cached noise data (default 'OPENVDB' )

- UNI
Uni Cache – Uni file format (.uni).

- OPENVDB
OpenVDB – OpenVDB file format (.vdb).

- RAW
Raw Cache – Raw file format (.raw).

Type :

Literal[‘UNI’, ‘OPENVDB’, ‘RAW’]

cache_particle_format

Pick which file format stores cached particle data (default 'OPENVDB' )

- UNI
Uni Cache – Uni file format (.uni).

- OPENVDB
OpenVDB – OpenVDB file format (.vdb).

- RAW
Raw Cache – Raw file format (.raw).

Type :

Literal[‘UNI’, ‘OPENVDB’, ‘RAW’]

cache_resumable

Stores extra data so a paused bake can later be continued. Since it writes more to disk, leaving it off is advisable when baking at high resolutions. (default False)

Type :

bool

cache_type

Choose how the simulation is cached (default 'REPLAY' )

- REPLAY
Replay – Use the timeline to bake the scene.

- MODULAR
Modular – Bake every stage of the simulation separately.

- ALL
All – Bake all simulation settings at once.

Type :

Literal[‘REPLAY’, ‘MODULAR’, ‘ALL’]

cell_size

Cell Size (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

cfl_condition

Cap on how far fluid travels per cell each step; larger CFL numbers cut the step count and shorten compute time (in [0, 10], default 2.0)

Type :

float

clipping

Threshold below which voxels are treated as empty so rendering can be optimized (in [0, 1], default 1e-06)

Type :

float

color_grid

Smoke color grid (array of 32 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

color_ramp

(readonly)

Type :

ColorRamp

color_ramp_field

Simulation field to color map (default 'NONE' )

Type :

Literal[‘NONE’]

color_ramp_field_scale

Multiplier for scaling the selected field to color map (in [0.001, 100000], default 1.0)

Type :

float

delete_in_obstacle

Delete fluid inside obstacles (default False)

Type :

bool

density_grid

Smoke density grid (array of 32 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

display_interpolation

Which interpolation is applied to smoke and fire volumes shown in solid mode (default 'LINEAR' )

- LINEAR
Linear – Good smoothness and speed.

- CUBIC
Cubic – Smoothed high quality interpolation, but slower.

- CLOSEST
Closest – No interpolation.

Type :

Literal[‘LINEAR’, ‘CUBIC’, ‘CLOSEST’]

display_thickness

Thickness of smoke display in the viewport (in [0.001, 1000], default 1.0)

Type :

float

dissolve_speed

Sets how fast smoke fades away; smaller values clear it sooner (in [1, 10000], default 5)

Type :

int

domain_resolution

Smoke Grid Resolution (array of 3 items, in [-inf, inf], default (0, 0, 0), readonly)

Type :

bpy_prop_array[int]

domain_type

Switch the kind of domain the simulation uses (default 'GAS' )

- GAS
Gas – Create domain for gases.

- LIQUID
Liquid – Create domain for liquids.

Type :

Literal[‘GAS’, ‘LIQUID’]

effector_group

Limit effectors to this collection

Type :

Collection

effector_weights

(readonly)

Type :

EffectorWeights

export_manta_script

During bake, write out a Mantaflow script built from the current domain settings. Only useful if you intend to inspect the cache (grids, velocity vectors, particles) inside Mantaflow itself, separate from Blender, once baking finishes. (default False)

Type :

bool

flame_grid

Smoke flame grid (array of 32 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

flame_ignition

Temperature at which the flames first ignite; raising it makes flames rise more quickly (in [0.5, 5], default 1.5)

Type :

float

flame_max_temp

Hottest the flames can get; raising it makes flames rise more quickly (in [1, 10], default 3.0)

Type :

float

flame_smoke

How much smoke the burning fuel gives off (in [0, 8], default 1.0)

Type :

float

flame_smoke_color

Color given to the smoke that rises off burning fuel (array of 3 items, in [0, inf], default (0.7, 0.7, 0.7))

Type :

mathutils.Color

flame_vorticity

Extra swirl added to the flames (in [0, 2], default 0.5)

Type :

float

flip_ratio

PIC/FLIP Ratio. Set it to 1.0 for a fully FLIP-based solve; lower it when you want the simulation to throw smaller splashes. (in [0, 1], default 0.97)

Type :

float

fluid_group

Limit fluid objects to this collection

Type :

Collection

force_collection

Limit forces to this collection

Type :

Collection

fractions_distance

Sets the spacing kept between fluid and obstacle; larger values push fluid further from obstacles while smaller ones let it creep inside them (in [-5, 5], default 0.5)

Type :

float

fractions_threshold

Sets how much fluid an obstacle cell may hold; larger values flag a boundary cell as obstacle more readily and lessen the boundary smoothing (in [0.001, 1], default 0.05)

Type :

float

gravity

Gravity in X, Y and Z direction (array of 3 items, in [-1000.1, 1000.1], default (0.0, 0.0, -9.81))

Type :

mathutils.Vector

gridlines_cell_filter

Cell type to be highlighted (default 'NONE' )

- NONE
None – Highlight the cells regardless of their type.

- FLUID
Fluid – Highlight only the cells of type Fluid.

- OBSTACLE
Obstacle – Highlight only the cells of type Obstacle.

- EMPTY
Empty – Highlight only the cells of type Empty.

- INFLOW
Inflow – Highlight only the cells of type Inflow.

- OUTFLOW
Outflow – Highlight only the cells of type Outflow.

Type :

Literal[‘NONE’, ‘FLUID’, ‘OBSTACLE’, ‘EMPTY’, ‘INFLOW’, ‘OUTFLOW’]

gridlines_color_field

Simulation field to color map onto gridlines (default 'NONE' )

- NONE
None – None.

- FLAGS
Flags – Flag grid of the fluid domain.

- RANGE
Highlight Range – Highlight the voxels with values of the color mapped field within the range.

Type :

Literal[‘NONE’, ‘FLAGS’, ‘RANGE’]

gridlines_lower_bound

Lower bound of the highlighting range (in [-inf, inf], default 0.0)

Type :

float

gridlines_range_color

Color used to highlight the range (array of 4 items, in [0, inf], default (1.0, 0.0, 0.0, 1.0))

Type :

bpy_prop_array[float]

gridlines_upper_bound

Upper bound of the highlighting range (in [-inf, inf], default 1.0)

Type :

float

guide_alpha

Guiding weight; larger values introduce more lag (in [1, 100], default 2.0)

Type :

float

guide_beta

Guiding size; larger values make bigger vortices (in [1, 50], default 5)

Type :

int

guide_parent

Borrow this object's velocities for the guiding effect (the object must carry a fluid modifier and be of the domain type) (in source: object needs to have fluid modifier and be of type domain)

Type :

Object

guide_source

Pick where guiding velocities come from (default 'DOMAIN' )

- DOMAIN
Domain – Use a fluid domain for guiding (domain needs to be baked already so that velocities can be extracted). Guiding domain can be of any type (i.e. gas or liquid)..

- EFFECTOR
Effector – Use guiding (effector) objects to create fluid guiding (guiding objects should be animated and baked once set up completely).

Type :

Literal[‘DOMAIN’, ‘EFFECTOR’]

guide_vel_factor

Guiding velocity factor; larger values yield stronger guiding velocities (in [0, 100], default 2.0)

Type :

float

has_cache_baked_any

(default False)

Type :

bool

has_cache_baked_data

(default False)

Type :

bool

has_cache_baked_guide

(default False)

Type :

bool

has_cache_baked_mesh

(default False)

Type :

bool

has_cache_baked_noise

(default False)

Type :

bool

has_cache_baked_particles

(default False)

Type :

bool

heat_grid

Smoke heat grid (array of 32 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

highres_sampling

Method for sampling the high resolution flow (default 'FULLSAMPLE' )

Type :

Literal[‘FULLSAMPLE’, ‘LINEAR’, ‘NEAREST’]

is_cache_baking_any

(default False)

Type :

bool

is_cache_baking_data

(default False)

Type :

bool

is_cache_baking_guide

(default False)

Type :

bool

is_cache_baking_mesh

(default False)

Type :

bool

is_cache_baking_noise

(default False)

Type :

bool

is_cache_baking_particles

(default False)

Type :

bool

mesh_concave_lower

Lower bound for mesh concavity; high values tend to smooth out and fill in concave regions (in [0, 10], default 0.4)

Type :

float

mesh_concave_upper

Upper bound for mesh concavity; high values tend to smooth out and fill in concave regions (in [0, 10], default 3.5)

Type :

float

mesh_generator

Pick which particle level-set generator runs (default 'IMPROVED' )

- IMPROVED
Final – Use improved particle level set (slower but more precise and with mesh smoothening options).

- UNION
Preview – Use union particle level set (faster but lower quality).

Type :

Literal[‘IMPROVED’, ‘UNION’]

mesh_particle_radius

Factor scaling particle radius; larger values give bigger meshed particles. Re-tune it whenever the mesh scale changes. (in [0, 10], default 2.0)

Type :

float

mesh_scale

Factor by which the meshing simulation is enlarged relative to the domain's base resolution. For the best mesh, tune the mesh particle radius together with this value. (in [1, 100], default 2)

Type :

int

mesh_smoothen_neg

Inward smoothing applied to the mesh (in [0, 100], default 1)

Type :

int

mesh_smoothen_pos

Outward smoothing applied to the mesh (in [0, 100], default 1)

Type :

int

noise_pos_scale

Spatial scale of the noise; larger values make bigger vortices (in [0.0001, 10], default 2.0)

Type :

float

noise_scale

Factor by which the noise simulation is enlarged relative to the domain's base resolution (in [1, 100], default 2)

Type :

int

noise_strength

How strong the noise is (in [0, 10], default 1.0)

Type :

float

noise_time_anim

How fast the noise animates over time (in [0.0001, 10], default 0.1)

Type :

float

openvdb_cache_compress_type

Which compression scheme is applied (default 'ZIP' )

- ZIP
Zip – Effective but slow compression.

- NONE
None – Do not use any compression.

Type :

Literal[‘ZIP’, ‘NONE’]

openvdb_data_depth

Bit depth used for fluid particles and grids; fewer bits make smaller files (default 'NONE' )

Type :

Literal[‘NONE’]

particle_band_width

Width of the narrow particle band; larger values widen the band and add more particles (in [0, 1000], default 3.0)

Type :

float

particle_max

Most particles a cell may contain; guarantees no cell exceeds this count (in [0, 1000], default 16)

Type :

int

particle_min

Fewest particles a cell may contain; guarantees every cell holds at least this count (in [0, 1000], default 8)

Type :

int

particle_number

Particle count factor; larger values produce more particles (in [1, 5], default 2)

Type :

int

particle_radius

Factor scaling particle radius. Raise it if the simulation appears to leak volume, lower it if the simulation appears to gain volume. (in [0, 10], default 1.0)

Type :

float

particle_randomness

How much randomness is applied when sampling particles (in [0, 10], default 0.1)

Type :

float

particle_scale

Factor by which the particle simulation is enlarged relative to the domain's base resolution (in [1, 100], default 1)

Type :

int

resolution_max

Resolution used for the fluid domain. The value maps to the longest side of the domain; the resolution of the remaining sides is derived from it. (in [6, 10000], default 32)

Type :

int

show_gridlines

Show gridlines (default False)

Type :

bool

show_velocity

Visualize vector fields (default False)

Type :

bool

simulation_method

Switch the solver that drives the simulation (default 'FLIP' )

- FLIP
FLIP – Use FLIP as the simulation method (more splashy behavior).

- APIC
APIC – Use APIC as the simulation method (more energetic and stable behavior).

Type :

Literal[‘FLIP’, ‘APIC’]

slice_axis

(default 'AUTO' )

- AUTO
Auto – Adjust slice direction according to the view direction.

- X
X – Slice along the X axis.

- Y
Y – Slice along the Y axis.

- Z
Z – Slice along the Z axis.

Type :

Literal[‘AUTO’, ‘X’, ‘Y’, ‘Z’]

slice_depth

Position of the slice (in [0, 1], default 0.5)

Type :

float

slice_per_voxel

How many slices per voxel should be generated (in [0, 100], default 5.0)

Type :

float

sndparticle_boundary

What happens to particles once they exit the domain (default 'DELETE' )

- DELETE
Delete – Delete secondary particles that are inside obstacles or left the domain.

- PUSHOUT
Push Out – Push secondary particles that left the domain back into the domain.

Type :

Literal[‘DELETE’, ‘PUSHOUT’]

sndparticle_bubble_buoyancy

Strength of the buoyant force lifting bubbles; high values send bubbles mostly upward (in [0, 100], default 0.5)

Type :

float

sndparticle_bubble_drag

Strength of the drag force carrying bubbles with the fluid; high values make bubbles travel mostly with the fluid (in [0, 100], default 0.6)

Type :

float

sndparticle_combined_export

Sets which particle systems get built from the secondary particles (default 'OFF' )

- OFF
Off – Create a separate particle system for every secondary particle type.

- `SPRAY_FOAM`
Spray + Foam – Spray and foam particles are saved in the same particle system.

- `SPRAY_BUBBLES`
Spray + Bubbles – Spray and bubble particles are saved in the same particle system.

- `FOAM_BUBBLES`
Foam + Bubbles – Foam and bubbles particles are saved in the same particle system.

- `SPRAY_FOAM_BUBBLES`
Spray + Foam + Bubbles – Create one particle system that contains all three secondary particle types.

Type :

Literal[‘OFF’, ‘`SPRAY_FOAM`’, ‘`SPRAY_BUBBLES`’, ‘`FOAM_BUBBLES`’, ‘`SPRAY_FOAM_BUBBLES`’]

sndparticle_life_max

Highest possible particle lifetime (in [0, 10000], default 25.0)

Type :

float

sndparticle_life_min

Lowest possible particle lifetime (in [0, 10000], default 10.0)

Type :

float

sndparticle_potential_max_energy

Upper clamp marking the fluid speed past which cells stop emitting more particles; higher values generally mean fewer particles (in [0, 1000], default 5.0)

Type :

float

sndparticle_potential_max_trappedair

Upper clamp for tagging fluid cells where air is trapped; higher values mean fewer tagged cells (in [0, 1000], default 20.0)

Type :

float

sndparticle_potential_max_wavecrest

Upper clamp for tagging fluid cells as wave crests; higher values mean fewer tagged cells (in [0, 1000], default 8.0)

Type :

float

sndparticle_potential_min_energy

Lower clamp marking the fluid speed at which cells begin emitting particles; lower values generally mean more particles (in [0, 1000], default 1.0)

Type :

float

sndparticle_potential_min_trappedair

Lower clamp for tagging fluid cells where air is trapped; lower values mean more tagged cells (in [0, 1000], default 5.0)

Type :

float

sndparticle_potential_min_wavecrest

Lower clamp for tagging fluid cells as wave crests; lower values mean more tagged cells (in [0, 1000], default 2.0)

Type :

float

sndparticle_potential_radius

Radius over which each cell's potential is computed; higher values run slower but give smoother potential grids (in [1, 4], default 2)

Type :

int

sndparticle_sampling_trappedair

Most particles generated per trapped-air cell per frame (in [0, 10000], default 40)

Type :

int

sndparticle_sampling_wavecrest

Most particles generated per wave-crest cell per frame (in [0, 10000], default 200)

Type :

int

sndparticle_update_radius

Radius over which each particle's position update is computed; higher values run slower but make particle motion less chaotic (in [1, 4], default 2)

Type :

int

start_point

Start point (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

surface_tension

Surface tension of the liquid; higher values make it behave more hydrophobically (in [0, 100], default 0.0)

Type :

float

sys_particle_maximum

Cap on how many fluid particles the simulation is permitted to hold (in [0, inf], default 0)

Type :

int

temperature_grid

Smoke temperature grid, range 0 to 1 represents 0 to 1000K (array of 32 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0), readonly)
