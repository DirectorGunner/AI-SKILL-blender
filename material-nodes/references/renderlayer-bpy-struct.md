# Renderlayer Bpy Struct, Renderresult Bpy Struct, Rendersettings Bpy Struct, Renderslot Bpy Struct

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: RenderLayer(bpy_struct); RenderResult(bpy_struct); RenderSettings(bpy_struct); RenderSlot(bpy_struct).

## RenderLayer(bpy_struct)

### RenderLayer(bpy_struct) 

base class — bpy_struct

class bpy.types. RenderLayer ( bpy_struct ) 

name 

The name of the view layer (default “”, readonly, never None)

Type :

str

passes 

(default None, readonly)

Type :

RenderPasses[RenderPass]

use_ao 

Compute Ambient Occlusion for this Layer (default False, readonly)

Type :

bool

use_grease_pencil 

Include Grease Pencil when rendering this layer (default False, readonly)

Type :

bool

use_motion_blur 

Compute motion blur for this Layer when the scene has it enabled (default False, readonly)

Type :

bool

use_pass_ambient_occlusion 

Output an Ambient Occlusion pass (default False, readonly)

Type :

bool

use_pass_combined 

Output the complete combined RGBA buffer (default False, readonly)

Type :

bool

use_pass_diffuse_color 

Output a diffuse color pass (default False, readonly)

Type :

bool

use_pass_diffuse_direct 

Output a diffuse direct pass (default False, readonly)

Type :

bool

use_pass_diffuse_indirect 

Output a diffuse indirect pass (default False, readonly)

Type :

bool

use_pass_emit 

Output an emission pass (default False, readonly)

Type :

bool

use_pass_environment 

Output an environment lighting pass (default False, readonly)

Type :

bool

use_pass_glossy_color 

Output a glossy color pass (default False, readonly)

Type :

bool

use_pass_glossy_direct 

Output a glossy direct pass (default False, readonly)

Type :

bool

use_pass_glossy_indirect 

Output a glossy indirect pass (default False, readonly)

Type :

bool

use_pass_material_index 

Output a material index pass (default False, readonly)

Type :

bool

use_pass_mist 

Output a mist factor pass (0.0 to 1.0) (default False, readonly)

Type :

bool

use_pass_normal 

Output a normal pass (default False, readonly)

Type :

bool

use_pass_object_index 

Output an object index pass (default False, readonly)

Type :

bool

use_pass_position 

Output a position pass (default False, readonly)

Type :

bool

use_pass_shadow 

Output a shadow pass (default False, readonly)

Type :

bool

use_pass_subsurface_color 

Output a subsurface color pass (default False, readonly)

Type :

bool

use_pass_subsurface_direct 

Output a subsurface direct pass (default False, readonly)

Type :

bool

use_pass_subsurface_indirect 

Output a subsurface indirect pass (default False, readonly)

Type :

bool

use_pass_transmission_color 

Output a transmission color pass (default False, readonly)

Type :

bool

use_pass_transmission_direct 

Output a transmission direct pass (default False, readonly)

Type :

bool

use_pass_transmission_indirect 

Output a transmission indirect pass (default False, readonly)

Type :

bool

use_pass_uv 

Output a texture UV pass (default False, readonly)

Type :

bool

use_pass_vector 

Output a speed vector pass (default False, readonly)

Type :

bool

use_pass_z 

Output a depth-values pass (default False, readonly)

Type :

bool

use_sky 

Include the Sky when rendering this Layer (default False, readonly)

Type :

bool

use_solid 

Include Solid faces when rendering this Layer (default False, readonly)

Type :

bool

use_strand 

Include Strands when rendering this Layer (default False, readonly)

Type :

bool

use_volumes 

Include volumes when rendering this Layer (default False, readonly)

Type :

bool

load_from_file ( filepath , * , x = 0 , y = 0 ) 

Read pixel data into this renderlayer out of an image file on disk

Parameters :

- filepath ( str ) – File Path, File path to load into this render tile, must be no smaller than the renderlayer (never None)

- x ( int ) – Offset X, Offset the position to copy from if the image is larger than the render layer (in [0, inf], optional)

- y ( int ) – Offset Y, Offset the position to copy from if the image is larger than the render layer (in [0, inf], optional)

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

| RenderResult.layers | |

## RenderResult(bpy_struct)

### RenderResult(bpy_struct) 

base class — bpy_struct

class bpy.types. RenderResult ( bpy_struct ) 

The outcome of a render, covering every layer and pass

layers 

(default None, readonly)

Type :

bpy_prop_collection[RenderLayer]

resolution_x 

(in [-inf, inf], default 0, readonly)

Type :

int

resolution_y 

(in [-inf, inf], default 0, readonly)

Type :

int

views 

(default None, readonly)

Type :

bpy_prop_collection[RenderView]

load_from_file ( filepath ) 

Read pixel data into this render result out of an image file on disk

Parameters :

filepath ( str ) – File Name, Filename to load into this render tile, must be no smaller than the render result (never None)

stamp_data_add_field ( field , value ) 

Add engine-specific stamp data to the result

Parameters :

- field ( str ) – Field, Name of the stamp field to add (never None)

- value ( str ) – Value, Value of the stamp data (never None)

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

| RenderEngine.begin_result RenderEngine.end_result | RenderEngine.get_result RenderEngine.update_result |

## RenderSettings(bpy_struct)

### RenderSettings(bpy_struct)

base class — bpy_struct

class bpy.types. RenderSettings ( bpy_struct )

Per-Scene data-block holding that scene's render configuration

bake

(readonly, never None)

Type :

BakeSettings

border_max_x

Upper X bound of the render region, expressed in [0, 1] (default 1.0)

Type :

float

border_max_y

Upper Y bound of the render region, expressed in [0, 1] (default 1.0)

Type :

float

border_min_x

Lower X bound of the render region, expressed in [0, 1] (default 0.0)

Type :

float

border_min_y

Lower Y bound of the render region, expressed in [0, 1] (default 0.0)

Type :

float

compositor_denoise_device

Which device runs the compositor's denoise nodes (default 'AUTO' )

- AUTO
Auto – Match whatever device the compositor itself is already using for the denoise node.

- CPU
CPU – Run the denoise node on the CPU.

- GPU
GPU – Run the denoise node on the GPU when one is present, otherwise drop back to the CPU.

Type :

Literal[‘AUTO’, ‘CPU’, ‘GPU’]

compositor_denoise_final_quality

Quality denoise nodes apply when final renders are composited, used whenever a node's quality option is left on Follow Scene (default 'HIGH' )

- HIGH
High – High quality.

- BALANCED
Balanced – A trade-off that sits between speed and quality.

- FAST
Fast – High performance.

Type :

Literal[‘HIGH’, ‘BALANCED’, ‘FAST’]

compositor_denoise_preview_quality

Quality denoise nodes apply for viewport and interactive compositing, used whenever a node's quality option is left on Follow Scene (default 'BALANCED' )

- HIGH
High – High quality.

- BALANCED
Balanced – A trade-off that sits between speed and quality.

- FAST
Fast – High performance.

Type :

Literal[‘HIGH’, ‘BALANCED’, ‘FAST’]

compositor_device

Chooses where the compositing runs (default 'CPU' )

Type :

Literal[‘CPU’, ‘GPU’]

compositor_precision

Numeric precision held by intermediate compositor results (default 'AUTO' )

- AUTO
Auto – Full precision on final renders, half precision the rest of the time.

- FULL
Full – Full precision.

Type :

Literal[‘AUTO’, ‘FULL’]

dither_intensity

Strength of the dithering noise mixed into the rendered image to disrupt banding (in [0, inf], default 1.0)

Type :

float

engine

Which engine performs the render (default '`BLENDER_EEVEE`' )

Type :

Literal[‘`BLENDER_EEVEE`’]

ffmpeg

The scene's FFmpeg-related configuration (readonly)

Type :

FFmpegSettings

file_extension

Extension applied to saved renders (default “”, readonly, never None)

Type :

str

filepath

Output directory and name for animations; the # characters mark where frame numbers sit and how they are padded (default “”, never None, blend relative // prefix supported, Supports template expressions)

Type :

str

film_transparent

Make the world background transparent so the render can be composited over a different backdrop (default False)

Type :

bool

filter_size

Span across which the reconstruction filter blends samples (in [0, 500], default 1.5)

Type :

float

fps

Frame rate in frames per second (in [1, 32767], default 24)

Type :

int

fps_base

Framerate base (in [1e-05, 1e+06], default 1.0)

Type :

float

frame_map_new

Duration, in frames, that the Map Old span is stretched to (in [1, 900], default 100)

Type :

int

frame_map_old

Old mapping value in frames (in [1, 900], default 100)

Type :

int

hair_subdiv

Extra subdivisions applied along the curves (in [0, 3], default 0)

Type :

int

hair_type

Shape used for the curves (default 'STRAND' )

Type :

Literal[‘STRAND’, ‘STRIP’, ‘CYLINDER’]

has_multiple_engines

True when more than a single render engine can be selected (default False, readonly)

Type :

bool

image_settings

(readonly, never None)

Type :

ImageFormatSettings

is_movie_format

True if the chosen format produces a movie (default False, readonly)

Type :

bool

line_thickness

Thickness of lines, measured in pixels (in [0, 10000], default 1.0)

Type :

float

line_thickness_mode

How Freestyle line drawing interprets line thickness (default 'ABSOLUTE' )

- ABSOLUTE
Absolute – Treat the line thickness value as a literal pixel count.

- RELATIVE
Relative – Scale the unit line thickness by how the current vertical image resolution compares to 480 pixels.

Type :

Literal[‘ABSOLUTE’, ‘RELATIVE’]

metadata_input

Source the metadata is pulled from (default 'SCENE' )

- SCENE
Scene – Pull metadata out of the current scene.

- STRIPS
Sequencer Strips – Pull metadata from the sequencer's strips.

Type :

Literal[‘SCENE’, ‘STRIPS’]

motion_blur_position

Shifts the shutter's time window, which alters where the motion blur trails fall (default 'CENTER' )

- START
Start on Frame – The shutter begins opening at the current frame.

- CENTER
Center on Frame – The shutter stays open across the current frame.

- END
End on Frame – The shutter finishes closing at the current frame.

Type :

Literal[‘START’, ‘CENTER’, ‘END’]

motion_blur_shutter

Frames of elapsed time spanning shutter open to shutter close (in [0, inf], default 0.5)

Type :

float

motion_blur_shutter_curve

Curve describing how open the shutter is across time (readonly)

Type :

CurveMapping

pixel_aspect_x

Horizontal pixel aspect ratio, for anamorphic or non-square output (in [1, 200], default 1.0)

Type :

float

pixel_aspect_y

Vertical pixel aspect ratio, for anamorphic or non-square output (in [1, 200], default 1.0)

Type :

float

ppm_base

Base unit underlying pixels per meter (in [1e-05, 1e+06], default 0.0254)

Type :

float

ppm_factor

Pixel-density metadata written into formats that support it; the value gets multiplied by the PPM-base, which sets the unit, typically inches or meters (in [1e-05, 1e+06], default 72.0)

Type :

float

preview_pixel_size

Pixel size used by viewport rendering (default 'AUTO' )

- AUTO
Automatic – Pick the pixel size automatically, scaled to the interface scale.

- 1
1× – Render at full resolution.

- 2
2× – Render at 50% resolution.

- 4
4× – Render at 25% resolution.

- 8
8× – Render at 12.5% resolution.

Type :

Literal[‘AUTO’, ‘1’, ‘2’, ‘4’, ‘8’]

resolution_percentage

Scale applied to the render resolution, as a percentage (in [1, 32767], default 100)

Type :

int

resolution_x

Count of horizontal pixels in the rendered image (in [4, 65536], default 1920)

Type :

int

resolution_y

Count of vertical pixels in the rendered image (in [4, 65536], default 1080)

Type :

int

sequencer_gl_preview

Display method the sequencer view uses (default 'SOLID' )

Type :

Literal[Shading Type Items]

simplify_child_particles

Global child particles percentage (in [0, 1], default 1.0)

Type :

float

simplify_child_particles_render

Global child particles percentage during rendering (in [0, 1], default 0.0)

Type :

float

simplify_gpencil

Simplify Grease Pencil drawing (default False)

Type :

bool

simplify_gpencil_antialiasing

Smooth stroke edges with antialiasing (default True)

Type :

bool

simplify_gpencil_modifier

Display modifiers (default True)

Type :

bool

simplify_gpencil_onplay

Apply Grease Pencil simplification only while animation is playing back (default False)

Type :

bool

simplify_gpencil_shader_fx

Display Shader Effects (default True)

Type :

bool

simplify_gpencil_tint

Display layer tint (default True)

Type :

bool

simplify_gpencil_view_fill

Show fill strokes inside the viewport (default True)

Type :

bool

simplify_subdivision

Global maximum subdivision level (in [0, 32767], default 6)

Type :

int

simplify_subdivision_render

Global maximum subdivision level during rendering (in [0, 32767], default 0)

Type :

int

simplify_volumes

Viewport resolution percentage for volume objects (in [0, 1], default 1.0)

Type :

float

stamp_background

Backing color drawn behind stamp text (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.25))

Type :

bpy_prop_array[float]

stamp_font_size

Font size for rendered stamp text (in [8, 64], default 12)

Type :

int

stamp_foreground

Color applied to stamp text (array of 4 items, in [0, 1], default (0.8, 0.8, 0.8, 1.0))

Type :

bpy_prop_array[float]

stamp_note_text

Custom text shown in the stamp note (default “”, never None)

Type :

str

stereo_views

(default None, readonly)

Type :

bpy_prop_collection[SceneRenderView]

threads

Cap on how many CPU cores render at once, on multi-core/CPU machines (in [1, 1024], default 1)

Type :

int

threads_mode

Picks how the render thread count is decided (default 'AUTO' )

- AUTO
Auto-Detect – Derive the thread count automatically from the available CPUs.

- FIXED
Fixed – Set the thread count by hand.

Type :

Literal[‘AUTO’, ‘FIXED’]

use_border

Render only a user-defined region inside the frame size (default False)

Type :

bool

use_compositing

Run the render result through compositing when a compositing node group is assigned to the scene (default True)

Type :

bool

use_crop_to_border

Trim the rendered frame down to the render region's size (default False)

Type :

bool

use_file_extension

Append the format's extension to the rendered file name, e.g. filename + .jpg (default True)

Type :

bool

use_freestyle

Render stylized strokes via Freestyle (default False)

Type :

bool

use_high_quality_normals

Trade some performance for higher-quality tangent space (default False)

Type :

bool

use_lock_interface

Freeze the interface during rendering so more memory goes to the renderer (default False)

Type :

bool

use_motion_blur

Apply multi-sampled 3D scene motion blur (default False)

Type :

bool

use_multiview

Use multiple views in the scene (default False)

Type :

bool

use_overwrite

Replace existing files while rendering (default True)

Type :

bool

use_persistent_data

Hold on to render data between runs for faster re-renders and animation renders, trading higher memory use (default False)

Type :

bool

use_placeholder

Write empty placeholder files as frames are rendered, much like Unix 'touch' (default False)

Type :

bool

use_render_cache

Write the render cache out to EXR files, handy for heavy compositing; note this indirectly affects rendered scenes (default False)

Type :

bool

use_sequencer

Send the rendered (and composited) result through the video sequence editor pipeline when sequencer strips are present (default True)

Type :

bool

use_sequencer_override_scene_strip

Take workbench render settings from the sequencer scene rather than from each scene used in the strip (default False)

Type :

bool

use_simplify

Turn on scene simplification for quicker preview renders (default False)

Type :

bool

use_simplify_normals

Skip computing custom normals and face corner normals when meshes are shown in the viewport (default False)

Type :

bool

use_single_layer

Render only the active layer; this applies to interface renders and is ignored from the command line (default False)

Type :

bool

use_spherical_stereo

True when the active render engine can do spherical stereo rendering (default False, readonly)

Type :

bool

use_stamp

Draw the stamp info text into the rendered image (default False)

Type :

bool

use_stamp_camera

Record the active camera's name in the image metadata (default True)

Type :

bool

use_stamp_date

Record the current date in image/video metadata (default True)

Type :

bool

use_stamp_filename

Record the .blend filename in image/video metadata (default True)

Type :

bool

use_stamp_frame

Record the frame number in image metadata (default True)

Type :

bool

use_stamp_frame_range

Record the rendered frame range in image/video metadata (default False)

Type :

bool

use_stamp_hostname

Record the hostname of the rendering machine (default False)

Type :

bool

use_stamp_labels

Show stamp labels, such as “Camera” preceding the camera name (default True)

Type :

bool

use_stamp_lens

Record the active camera's lens in image metadata (default False)

Type :

bool

use_stamp_marker

Record the most recent marker's name in image metadata (default False)

Type :

bool

use_stamp_memory

Record peak memory usage in image metadata (default True)

Type :

bool

use_stamp_note

Record a custom note in image/video metadata (default False)

Type :

bool

use_stamp_render_time

Record the render time in image metadata (default True)

Type :

bool

use_stamp_scene

Record the active scene's name in image/video metadata (default True)

Type :

bool

use_stamp_sequencer_strip

Record the foreground sequence strip's name in image metadata (default False)

Type :

bool

use_stamp_time

Record the rendered frame timecode as HH:MM:SS.FF in image metadata (default True)

Type :

bool

views

(default None, readonly)

Type :

RenderViews[SceneRenderView]

views_format

(default '`STEREO_3D`' )

- `STEREO_3D`
Stereo 3D – One stereo camera rig; configure the stereo options on the camera panel.

- MULTIVIEW
Multi-View – Several cameras configured one by one.

Type :

Literal[‘`STEREO_3D`’, ‘MULTIVIEW’]

frame_path ( * , frame = -2147483648 , preview = False , view = '' )

Give back the full path of the file that a particular frame will be written to

Parameters :

- frame ( int ) – Frame number to use, if unset the current frame will be used (in [-inf, inf], optional)

- preview ( bool ) – Preview, Use preview range (optional)

- view ( str ) – View, The name of the view to use to replace the “%” chars (optional, never None)

Returns :

File Path, The resulting filepath from the scenes render settings (never None)

Return type :

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

| RenderEngine.render | Scene.render |

## RenderSlot(bpy_struct)

### RenderSlot(bpy_struct)

base class — bpy_struct

class bpy.types. RenderSlot ( bpy_struct )

Settings that define a render slot

name

Render slot name (default “”, never None)

Type :

str

clear ( iuser )

Empty out the render slot

Parameters :

iuser (ImageUser) – ImageUser

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

| Image.render_slots RenderSlots.active | RenderSlots.new |

## See also

- [Bpy Struct](bpy-struct.md)
