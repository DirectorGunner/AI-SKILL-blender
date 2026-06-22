# Sceneeevee Bpy Struct, Scenegpencil Bpy Struct, Scenerenderview Bpy Struct, Scenestrip Strip ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: SceneEEVEE(bpy_struct); SceneGpencil(bpy_struct); SceneRenderView(bpy_struct); SceneStrip(Strip); Scopes(bpy_struct).

## SceneEEVEE(bpy_struct)

### SceneEEVEE(bpy_struct)

base class — bpy_struct

class bpy.types. SceneEEVEE ( bpy_struct )

Scene display settings for 3D viewport

bokeh_max_size

Largest the depth-of-field bokeh shape may grow; smaller is faster (in [0, 2000], default 100.0)

Type :

float

bokeh_neighbor_max

Upper brightness limit weighed when discarding bokeh sprites by their neighborhood; smaller is faster (in [0, 100000], default 10.0)

Type :

float

bokeh_overblur

Blur each jittered sample to cut down under-sampling artifacts (in [0, 100], default 5.0)

Type :

float

bokeh_threshold

Brightness cutoff above which sprite-based depth of field kicks in (in [0, 100000], default 1.0)

Type :

float

clamp_surface_direct

When non-zero, caps how much lights may contribute to a surface; larger values are scaled back to avoid heavy noise and slow convergence, trading accuracy. Applies to light objects. (in [0, inf], default 0.0)

Type :

float

clamp_surface_indirect

When non-zero, caps indirect lighting on a surface; larger values are scaled back to avoid heavy noise and slow convergence, trading accuracy. Applies to ray-tracing and light-probes. (in [0, inf], default 10.0)

Type :

float

clamp_volume_direct

When non-zero, caps how much lights may contribute within volumes; larger values are scaled back to avoid heavy noise and slow convergence, trading accuracy. Applies to light objects. (in [0, inf], default 0.0)

Type :

float

clamp_volume_indirect

When non-zero, caps indirect lighting within volumes; larger values are scaled back to avoid heavy noise and slow convergence, trading accuracy. Applies to light-probes. (in [0, inf], default 0.0)

Type :

float

direct_light_intensity

Scale applied to the direct lighting contribution (in [0, inf], default 1.0)

Type :

float

fast_gi_bias

Nudge the shading normal to cut down self-intersection artifacts (in [0, 1], default 0.05)

Type :

float

fast_gi_distance

When non-zero, the farthest range at which other surfaces still feed the fast GI approximation (in [0, 100000], default 0.0)

Type :

float

fast_gi_method

Which fast GI approximation is used (default '`GLOBAL_ILLUMINATION`' )

- `AMBIENT_OCCLUSION_ONLY`
Ambient Occlusion – Substitute ambient occlusion for full global illumination.

- `GLOBAL_ILLUMINATION`
Global Illumination – Work out global illumination, accounting for light bouncing off nearby objects.

Type :

Literal[‘`AMBIENT_OCCLUSION_ONLY`’, ‘`GLOBAL_ILLUMINATION`’]

fast_gi_quality

Precision of the fast GI ray marching (in [0, 1], default 0.25)

Type :

float

fast_gi_ray_count

How many GI rays are traced per pixel (in [1, 16], default 2)

Type :

int

fast_gi_resolution

Sets the quality of fast GI lighting; higher resolution costs more memory. (default '2' )

- 1
1:1 – Full resolution.

- 2
1:2 – Render this effect at 50% render resolution.

- 4
1:4 – Render this effect at 25% render resolution.

- 8
1:8 – Render this effect at 12.5% render resolution.

- 16
1:16 – Render this effect at 6.25% render resolution.

Type :

Literal[‘1’, ‘2’, ‘4’, ‘8’, ‘16’]

fast_gi_step_count

How many screen samples are taken per GI ray (in [1, 64], default 8)

Type :

int

fast_gi_thickness_far

Angular thickness given to surfaces while computing fast GI and ambient occlusion; trims energy loss and missing occlusion from distant geometry. (in [0.0174533, 3.14159], default 0.785398)

Type :

float

fast_gi_thickness_near

Geometric thickness given to surfaces while computing fast GI and ambient occlusion; trims light leaking and missing contact occlusion. (in [0, 100000], default 0.25)

Type :

float

gi_cubemap_resolution

Size of each cubemap (default '512' )

Type :

Literal[‘128’, ‘256’, ‘512’, ‘1024’, ‘2048’, ‘4096’]

gi_diffuse_bounces

How many times light is reinjected into the light grids; 0 turns off indirect diffuse light (in [0, inf], default 3)

Type :

int

gi_glossy_clamp

Cap pixel intensity to reduce noise in glossy reflections coming from reflection cubemaps; 0 disables it (in [0, inf], default 0.0)

Type :

float

gi_irradiance_pool_size

Size of the irradiance pool; a larger pool fits more irradiance grids in the scene but may overflow GPU memory and hurt performance (default '16' )

Type :

Literal[‘16’, ‘32’, ‘64’, ‘128’, ‘256’, ‘512’, ‘1024’]

gi_visibility_resolution

Size of the shadow map used for each irradiance sample (default '32' )

Type :

Literal[‘8’, ‘16’, ‘32’, ‘64’]

indirect_light_intensity

Scale applied to the indirect lighting contribution (in [0, inf], default 1.0)

Type :

float

light_threshold

Lowest light intensity at which a light still counts toward the lighting (in [0, inf], default 0.01)

Type :

float

motion_blur_depth_scale

Smaller values cut how much background bleeds onto foreground elements (in [0, inf], default 100.0)

Type :

float

motion_blur_max

Farthest a pixel may spread under blur (in [0, 2048], default 32)

Type :

int

motion_blur_steps

Sets motion blur accuracy; more steps mean longer renders (in [1, inf], default 1)

Type :

int

overscan_size

Percentage of the render size added as overscan to the internal render buffers (in [0, 50], default 3.0)

Type :

float

ray_tracing_method

Pick how scene-ray intersections are found (default 'SCREEN' )

- PROBE
Light Probe – Use light probes to locate the scene intersection.

- SCREEN
Screen-Trace – Trace rays against the depth buffer, falling back to light probes for invalid rays..

Type :

Literal[‘PROBE’, ‘SCREEN’]

ray_tracing_options

EEVEE settings for tracing reflections (readonly)

Type :

RaytraceEEVEE

shadow_pool_size

Size of the shadow pool; a larger pool fits more shadows in the scene but may overflow GPU memory (default '512' )

Type :

Literal[‘16’, ‘32’, ‘64’, ‘128’, ‘256’, ‘512’, ‘1024’]

shadow_ray_count

How many shadow rays are traced per light (in [1, 4], default 1)

Type :

int

shadow_resolution_scale

Resolution percentage of shadow maps (in [0, 1], default 1.0)

Type :

float

shadow_step_count

How many shadow map samples are taken per shadow ray (in [1, 16], default 6)

Type :

int

taa_render_samples

Per-pixel sample count used for rendering (in [1, inf], default 64)

Type :

int

taa_samples

Sample count, unlimited when set to 0 (in [0, inf], default 16)

Type :

int

use_bokeh_jittered

Jitter the camera position for accurate blur built from render samples; final render only (default False)

Type :

bool

use_fast_gi

Apply a quicker global illumination technique for high-roughness surfaces (default False)

Type :

bool

use_overscan

Render slightly past the image border internally so screen-space effects don't vanish at the edges (default False)

Type :

bool

use_raytracing

Switch on the ray-tracing module (default False)

Type :

bool

use_shadow_jitter_viewport

Turn on jittered shadows in the viewport. (Final renders always use jittered shadows). (default False)

Type :

bool

use_shadows

Allow lights to cast shadows (default True)

Type :

bool

use_taa_reprojection

Denoise the image via temporal reprojection, which can leave some ghosting (default True)

Type :

bool

use_volume_custom_range

Set custom near and far clip distances for volume computation (default False)

Type :

bool

use_volumetric_shadows

Let volumetric materials cast shadows onto other volumetric materials; this is very costly (default False)

Type :

bool

volumetric_end

Far distance at which the volumetric effect stops (in [1e-06, inf], default 100.0)

Type :

float

volumetric_light_clamp

Cap on light contribution that lowers noise (in [0, inf], default 0.0)

Type :

float

volumetric_ray_depth

Largest number of surface intersections the accurate volume intersection method handles; going over it produces artifacts, and a higher count raises VRAM usage. (in [1, 16], default 16)

Type :

int

volumetric_sample_distribution

Bias more samples toward the camera (in [0, 1], default 0.8)

Type :

float

volumetric_samples

How many steps compute the volumetric effects; a higher step count raises VRAM usage and quality. (in [1, 256], default 64)

Type :

int

volumetric_shadow_samples

How many samples compute volumetric shadowing (in [1, 128], default 16)

Type :

int

volumetric_start

Near distance at which the volumetric effect begins (in [1e-06, inf], default 0.1)

Type :

float

volumetric_tile_size

Sets the quality of the volumetric effects; higher resolution costs more memory. (default '8' )

- 1
1:1 – Full resolution.

- 2
1:2 – Render this effect at 50% render resolution.

- 4
1:4 – Render this effect at 25% render resolution.

- 8
1:8 – Render this effect at 12.5% render resolution.

- 16
1:16 – Render this effect at 6.25% render resolution.

Type :

Literal[‘1’, ‘2’, ‘4’, ‘8’, ‘16’]

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

| Scene.eevee | |

## SceneGpencil(bpy_struct)

### SceneGpencil(bpy_struct)

base class — bpy_struct

class bpy.types. SceneGpencil ( bpy_struct )

Render settings

aa_samples

How many supersampling anti-aliasing samples each pixel gets in the final render (in [1, inf], default 8)

Type :

int

antialias_threshold

Cutoff for the edge detection algorithm; higher values may over-blur parts of the image (in [0, inf], default 1.0)

Type :

float

antialias_threshold_render

Cutoff for the edge detection algorithm; higher values may over-blur parts of the image. Applies to the final render only (in [0, inf], default 0.25)

Type :

float

motion_blur_steps

Sets motion blur accuracy; more steps lengthen the render. Used only with Motion Blur on. Set to 0 to switch off Grease Pencil motion blur (in [0, inf], default 8)

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

| Scene.grease_pencil_settings | |

## SceneRenderView(bpy_struct)

### SceneRenderView(bpy_struct)

base class — bpy_struct

class bpy.types. SceneRenderView ( bpy_struct )

A render viewpoint used for 3D stereo and multiview rendering

camera_suffix

Suffix that picks out which cameras to use and is also appended to this view's render images (default “”, never None)

Type :

str

file_suffix

Suffix appended to this view's render images (default “”, never None)

Type :

str

name

Render view name (default “”, never None)

Type :

str

use

Switch this render view on or off (default True)

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

| RenderViews.active RenderViews.new RenderViews.remove | RenderSettings.stereo_views RenderSettings.views |

## SceneStrip(Strip)

### SceneStrip(Strip)

base classes — bpy_struct, Strip

class bpy.types. SceneStrip ( Strip )

A sequence strip that draws on a scene's rendered image

alpha_mode

How alpha is represented within the RGBA pixels (default 'STRAIGHT' )

- STRAIGHT
Straight – In transparent pixels, the RGB channels stay independent of the alpha channel.

- PREMUL
Premultiplied – In transparent pixels, the RGB channels are scaled by the alpha channel.

Type :

Literal[‘STRAIGHT’, ‘PREMUL’]

animation_offset_end

Animation end offset (trim end) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_end’.

Type :

int

animation_offset_start

Animation start offset (trim start) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_start’.

Type :

int

color_multiply

(in [0, 20], default 1.0)

Type :

float

color_saturation

Tune how saturated the input's color is (in [0, 20], default 1.0)

Type :

float

content_trim_end

Frames cut off the end of the underlying source; the source content is trimmed and later frames become holds (in [0, inf], default 0)

Type :

int

content_trim_start

Frames cut off the start of the underlying source; the source content is trimmed and earlier frames become holds (in [0, inf], default 0)

Type :

int

crop

(readonly)

Type :

StripCrop

fps

Frames per second (in [-inf, inf], default 0.0, readonly)

Type :

float

multiply_alpha

Multiply the alpha together with the color channels (default False)

Type :

bool

proxy

(readonly)

Type :

StripProxy

retiming_keys

(default None, readonly)

Type :

RetimingKeys[RetimingKey]

scene

Scene that this strip uses

Type :

Scene

scene_camera

Use a camera other than the scene's active one

Type :

Object

scene_input

Which input the Scene strip draws from (default 'CAMERA' )

- CAMERA
Camera – Take the Scene's 3D camera as the input.

- SEQUENCER
Sequencer – Take the Scene's Sequencer timeline as the input.

Type :

Literal[‘CAMERA’, ‘SEQUENCER’]

strobe

Show only every nth frame (in [1, 30], default 0.0)

Type :

float

transform

(readonly)

Type :

StripTransform

use_annotations

Show Annotations in OpenGL previews (default True)

Type :

bool

use_deinterlace

Strip fields out of video movies (default False)

Type :

bool

use_flip_x

Flip on the X axis (default False)

Type :

bool

use_flip_y

Flip on the Y axis (default False)

Type :

bool

use_float

Convert the input into float data (default False)

Type :

bool

use_proxy

Give this strip a preview proxy and/or a time-code index (default False)

Type :

bool

use_reverse_frames

Reverse frame order (default False)

Type :

bool

volume

Playback volume of the sound (in [0, 100], default 1.0)

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

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start | Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py |

## Scopes(bpy_struct)

### Scopes(bpy_struct)

base class — bpy_struct

class bpy.types. Scopes ( bpy_struct )

Scopes giving a statistical view of an image

accuracy

Share of the source image's original pixel lines that get sampled (in [0, 100], default 0.0)

Type :

float

histogram

Histogram for viewing image statistics (readonly)

Type :

Histogram

use_full_resolution

Sample every single pixel of the image (default False)

Type :

bool

vectorscope_alpha

Opacity of the points (in [0, 1], default 0.0)

Type :

float

vectorscope_mode

(default 'RGB' )

Type :

Literal[‘LUMA’, ‘RGB’]

waveform_alpha

Opacity of the points (in [0, 1], default 0.0)

Type :

float

waveform_mode

(default 'LUMA' )

Type :

Literal[‘LUMA’, ‘PARADE’, ‘YCBCR601’, ‘YCBCR709’, ‘YCBCRJPG’, ‘RGB’]

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

| SpaceImageEditor.scopes | |

## See also

- [Bpy Struct](bpy-struct.md)
