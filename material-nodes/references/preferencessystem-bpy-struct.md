# Preferencessystem Bpy Struct

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### PreferencesSystem(bpy_struct)

base class — bpy_struct

class bpy.types. PreferencesSystem ( bpy_struct )

Settings for the graphics driver and operating system

anisotropic_filter

How good the anisotropic filtering is (default '`FILTER_2`' )

Type :

Literal[‘`FILTER_0`’, ‘`FILTER_2`’, ‘`FILTER_4`’, ‘`FILTER_8`’, ‘`FILTER_16`’]

audio_channels

How many audio channels are used (default 'STEREO' )

- MONO
Mono – Use a single mono channel.

- STEREO
Stereo – Use two stereo channels.

- SURROUND4
4 Channels – Use a 4-channel layout.

- SURROUND51
5.1 Surround – Use a 5.1 surround layout.

- SURROUND71
7.1 Surround – Use a 7.1 surround layout.

Type :

Literal[‘MONO’, ‘STEREO’, ‘SURROUND4’, ‘SURROUND51’, ‘SURROUND71’]

audio_device

The device audio is sent to (default 'None' )

- None
None – No device selected, so nothing plays.

Type :

Literal[‘None’]

audio_mixing_buffer

How many samples the audio mixing buffer holds (default '`SAMPLES_2048`' )

- `SAMPLES_256`
256 Samples – Size the mixing buffer at 256 samples.

- `SAMPLES_512`
512 Samples – Size the mixing buffer at 512 samples.

- `SAMPLES_1024`
1024 Samples – Size the mixing buffer at 1024 samples.

- `SAMPLES_2048`
2048 Samples – Size the mixing buffer at 2048 samples.

- `SAMPLES_4096`
4096 Samples – Size the mixing buffer at 4096 samples.

- `SAMPLES_8192`
8192 Samples – Size the mixing buffer at 8192 samples.

- `SAMPLES_16384`
16384 Samples – Size the mixing buffer at 16384 samples.

- `SAMPLES_32768`
32768 Samples – Size the mixing buffer at 32768 samples.

Type :

Literal[‘`SAMPLES_256`’, ‘`SAMPLES_512`’, ‘`SAMPLES_1024`’, ‘`SAMPLES_2048`’, ‘`SAMPLES_4096`’, ‘`SAMPLES_8192`’, ‘`SAMPLES_16384`’, ‘`SAMPLES_32768`’]

audio_sample_format

The format audio samples use (default 'FLOAT' )

- U8
8-bit Unsigned – Samples stored as 8-bit unsigned integers.

- S16
16-bit Signed – Samples stored as 16-bit signed integers.

- S24
24-bit Signed – Samples stored as 24-bit signed integers.

- S32
32-bit Signed – Samples stored as 32-bit signed integers.

- FLOAT
32-bit Float – Samples stored as 32-bit floats.

- DOUBLE
64-bit Float – Samples stored as 64-bit floats.

Type :

Literal[‘U8’, ‘S16’, ‘S24’, ‘S32’, ‘FLOAT’, ‘DOUBLE’]

audio_sample_rate

The rate at which audio is sampled (default '`RATE_48000`' )

- `RATE_44100`
44.1 kHz – Sample at 44100 per second.

- `RATE_48000`
48 kHz – Sample at 48000 per second.

- `RATE_96000`
96 kHz – Sample at 96000 per second.

- `RATE_192000`
192 kHz – Sample at 192000 per second.

Type :

Literal[‘`RATE_44100`’, ‘`RATE_48000`’, ‘`RATE_96000`’, ‘`RATE_192000`’]

dpi

(in [-inf, inf], default 0, readonly)

Type :

int

gl_clip_alpha

Clip alpha that falls below this cutoff in the 3D textured view (in [0, 1], default 0.004)

Type :

float

gl_texture_limit

Cap the texture size to conserve graphics memory (default '`CLAMP_OFF`' )

Type :

Literal[‘`CLAMP_OFF`’, ‘`CLAMP_8192`’, ‘`CLAMP_4096`’, ‘`CLAMP_2048`’, ‘`CLAMP_1024`’, ‘`CLAMP_512`’, ‘`CLAMP_256`’, ‘`CLAMP_128`’]

gpu_backend

Which GPU backend Blender uses (a restart is needed to apply changes) (default 'OPENGL' )

- OPENGL
OpenGL – Run on the OpenGL backend.

- METAL
Metal – Run on the Metal backend.

- VULKAN
Vulkan – Run on the Vulkan backend.

Type :

Literal[‘OPENGL’, ‘METAL’, ‘VULKAN’]

gpu_preferred_device

Which device detection should favor (a restart is needed to apply changes) (default 'AUTO' )

- AUTO
Auto – Detect the best GPU for Blender on its own.

Type :

Literal[‘AUTO’]

gpu_shader_workers

How many threads or subprocesses compile shaders, capped at the CPU's max threads (a restart is needed to apply changes). Raising it speeds compilation but uses more RAM. Set 0 for automatic configuration. (OpenGL only) (in [0, 32], default 0)

Type :

int

image_draw_method

How images are drawn on the screen (default 'AUTO' )

- AUTO
Automatic – Let the GPU and image decide the method.

- 2DTEXTURE
2D Texture – Do the display transform on the CPU and show the image as a 2D texture.

- GLSL
GLSL – Do the display transform with GLSL shaders and show the image as a 2D texture.

Type :

Literal[‘AUTO’, ‘2DTEXTURE’, ‘GLSL’]

is_microsoft_store_install

Whether this is the sandboxed Microsoft Store build of Blender (default False, readonly)

Type :

bool

legacy_compute_device_type

Retained only for backwards compatibility (in [-inf, inf], default 0, readonly)

Type :

int

light_ambient

The ambient light color that lights the scene evenly (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

memory_cache_limit

Cap on memory cache use (in megabytes) (in [0, inf], default 4096)

Type :

int

network_connection_limit

Cap how many internet connections online operations open at once. Zero turns the cap off. (in [0, 255], default 0)

Type :

int

network_timeout

Seconds to wait on online operations before a connection may time out. Zero falls back to the system default. (in [0, 255], default 0)

Type :

int

pixel_size

(in [-inf, inf], default 1.0, readonly)

Type :

float

register_all_users

Let this Blender version open blend files for every user. Needs elevated privileges. (default False)

Type :

bool

scrollback

Cap on how many lines the console buffer retains (in [32, 32768], default 256)

Type :

int

sequencer_proxy_setup

Controls when and how proxies get built (default 'AUTOMATIC' )

- MANUAL
Manual – Configure proxies by hand.

- AUTOMATIC
Automatic – Generate proxies at every preview size for newly added movie and image strips.

Type :

Literal[‘MANUAL’, ‘AUTOMATIC’]

shader_compilation_method

Method used to compile shaders in parallel. Subprocess needs much more RAM per worker but can finish faster on some machines. Requires a Blender restart to apply. (OpenGL only) (default 'THREAD' )

- THREAD
Thread – Compile shaders on threads.

- SUBPROCESS
Subprocess – Compile shaders in subprocesses.

Type :

Literal[‘THREAD’, ‘SUBPROCESS’]

solid_lights

Lights that illuminate objects under solid shading (default None, readonly)

Type :

bpy_prop_collection[UserSolidLight]

texture_collection_rate

Seconds between successive runs of the GL texture garbage collector (in [1, 3600], default 60)

Type :

int

texture_time_out

Seconds a GL texture may go untouched before it is freed (use 0 to keep textures allocated)

Type :

int

ui_line_width

Recommended line thickness and point size in pixels for add-ons that draw custom UI, derived from operating system settings and Blender UI scale (in [-inf, inf], default 1.0, readonly)

Type :

float

ui_scale

Scaling factor for drawing custom UI elements so they render correctly across differing DPI. It derives from operating system DPI settings and the Blender display scale. (in [-inf, inf], default 0.0, readonly)

Type :

float

use_edit_mode_smooth_wire

Smooth edit mode edges to cut down on aliasing (requires restart) (default True)

Type :

bool

use_gpu_subdivision

Let the GPU accelerate evaluation of the final subdivision surface modifiers in the stack (default True)

Type :

bool

use_online_access

Permit Blender to reach the internet. Add-ons that respect this setting connect only when it is on. Blender still cannot stop third-party add-ons from ignoring the rule. (default False)

Type :

bool

use_overlay_smooth_wire

Smooth overlay wires to cut down on aliasing (default True)

Type :

bool

use_region_overlap

Draw the tool/property regions on top of the main region (default True)

Type :

bool

use_studio_light_edit

Show the studio light editor's result in the viewport (default False)

Type :

bool

vbo_collection_rate

Seconds between successive runs of the GL vertex buffer object garbage collector (in [1, 3600], default 60)

Type :

int

vbo_time_out

Seconds a GL vertex buffer object may go untouched before it is freed (use 0 to keep the VBO allocated) (in [0, 3600], default 120)

Type :

int

viewport_aa

Anti-aliasing technique used in the 3d viewport (default '8' )

- OFF
No Anti-Aliasing – Render the scene with anti-aliasing turned off.

- FXAA
Single Pass Anti-Aliasing – Render the scene through a one-pass method (FXAA).

- 5
5 Samples – Render the scene at 5 anti-aliasing samples.

- 8
8 Samples – Render the scene at 8 anti-aliasing samples.

- 11
11 Samples – Render the scene at 11 anti-aliasing samples.

- 16
16 Samples – Render the scene at 16 anti-aliasing samples.

- 32
32 Samples – Render the scene at 32 anti-aliasing samples.

Type :

Literal[‘OFF’, ‘FXAA’, ‘5’, ‘8’, ‘11’, ‘16’, ‘32’]

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

| Preferences.system | |

## See also

- [Bpy Struct](bpy-struct.md)
