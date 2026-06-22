# Distortednoisetexture Texture, Dopesheet Bpy Struct, Dynamicpaintsurface Bpy Struct, Effectstrip Strip ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: DistortedNoiseTexture(Texture); DopeSheet(bpy_struct); DynamicPaintSurface(bpy_struct); EffectStrip(Strip); EvaluateClosureNodeViewerPathElem(ViewerPathElem).

## DistortedNoiseTexture(Texture)

### DistortedNoiseTexture(Texture)

base classes — bpy_struct, ID, Texture

class bpy.types. DistortedNoiseTexture ( Texture )

A procedural texture built from distorted noise

distortion

How strongly the noise is distorted (in [0, 10], default 1.0)

Type :

float

nabla

Offset size for the derivative used when working out the normal (in [0.001, 0.1], default 0.025)

Type :

float

noise_basis

Which noise basis drives the turbulence (default '`BLENDER_ORIGINAL`' )

- `BLENDER_ORIGINAL`
Blender Original – Noise algorithm - Blender original: Smooth interpolated noise.

- `ORIGINAL_PERLIN`
Original Perlin – Noise algorithm - Original Perlin: Smooth interpolated noise.

- `IMPROVED_PERLIN`
Improved Perlin – Noise algorithm - Improved Perlin: Smooth interpolated noise.

- `VORONOI_F1`
Voronoi F1 – Noise algorithm - Voronoi F1: Returns distance to the closest feature point.

- `VORONOI_F2`
Voronoi F2 – Noise algorithm - Voronoi F2: Returns distance to the 2nd closest feature point.

- `VORONOI_F3`
Voronoi F3 – Noise algorithm - Voronoi F3: Returns distance to the 3rd closest feature point.

- `VORONOI_F4`
Voronoi F4 – Noise algorithm - Voronoi F4: Returns distance to the 4th closest feature point.

- `VORONOI_F2_F1`
Voronoi F2-F1 – Noise algorithm - Voronoi F1-F2.

- `VORONOI_CRACKLE`
Voronoi Crackle – Noise algorithm - Voronoi Crackle: Voronoi tessellation with sharp edges.

- `CELL_NOISE`
Cell Noise – Noise algorithm - Cell Noise: Square cell tessellation.

Type :

Literal[‘`BLENDER_ORIGINAL`’, ‘`ORIGINAL_PERLIN`’, ‘`IMPROVED_PERLIN`’, ‘`VORONOI_F1`’, ‘`VORONOI_F2`’, ‘`VORONOI_F3`’, ‘`VORONOI_F4`’, ‘`VORONOI_F2_F1`’, ‘`VORONOI_CRACKLE`’, ‘`CELL_NOISE`’]

noise_distortion

Which noise basis is used for the distortion (default '`BLENDER_ORIGINAL`' )

- `BLENDER_ORIGINAL`
Blender Original – Noise algorithm - Blender original: Smooth interpolated noise.

- `ORIGINAL_PERLIN`
Original Perlin – Noise algorithm - Original Perlin: Smooth interpolated noise.

- `IMPROVED_PERLIN`
Improved Perlin – Noise algorithm - Improved Perlin: Smooth interpolated noise.

- `VORONOI_F1`
Voronoi F1 – Noise algorithm - Voronoi F1: Returns distance to the closest feature point.

- `VORONOI_F2`
Voronoi F2 – Noise algorithm - Voronoi F2: Returns distance to the 2nd closest feature point.

- `VORONOI_F3`
Voronoi F3 – Noise algorithm - Voronoi F3: Returns distance to the 3rd closest feature point.

- `VORONOI_F4`
Voronoi F4 – Noise algorithm - Voronoi F4: Returns distance to the 4th closest feature point.

- `VORONOI_F2_F1`
Voronoi F2-F1 – Noise algorithm - Voronoi F1-F2.

- `VORONOI_CRACKLE`
Voronoi Crackle – Noise algorithm - Voronoi Crackle: Voronoi tessellation with sharp edges.

- `CELL_NOISE`
Cell Noise – Noise algorithm - Cell Noise: Square cell tessellation.

Type :

Literal[‘`BLENDER_ORIGINAL`’, ‘`ORIGINAL_PERLIN`’, ‘`IMPROVED_PERLIN`’, ‘`VORONOI_F1`’, ‘`VORONOI_F2`’, ‘`VORONOI_F3`’, ‘`VORONOI_F4`’, ‘`VORONOI_F2_F1`’, ‘`VORONOI_CRACKLE`’, ‘`CELL_NOISE`’]

noise_scale

Scale factor applied to the noise input (in [0.0001, inf], default 0.25)

Type :

float

users_material

The materials referencing this texture

Type :

tuple[Material, …]

Note

Takes O(len(bpy.data.materials) * len(material.texture_slots)) time.

(readonly)

users_object_modifier

The object modifiers referencing this texture

Type :

tuple[Object, …]

Note

Takes O(len(bpy.data.objects) * len(obj.modifiers)) time.

(readonly)

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference | ID.asset_data ID.override_library ID.preview Texture.type Texture.use_clamp Texture.use_color_ramp Texture.color_ramp Texture.intensity Texture.contrast Texture.saturation Texture.factor_red Texture.factor_green Texture.factor_blue Texture.use_preview_alpha Texture.use_nodes Texture.node_tree Texture.animation_data Texture.users_material Texture.users_object_modifier |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast | bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py Texture.evaluate Texture.bl_rna_get_subclass Texture.bl_rna_get_subclass_py |

## DopeSheet(bpy_struct)

### DopeSheet(bpy_struct)

base class — bpy_struct

class bpy.types. DopeSheet ( bpy_struct )

Controls which channels the animation editors display

filter_collection

Restricts shown objects to members of this collection

Type :

Collection

filter_fcurve_name

Text used to live-filter F-Curves (default “”, never None)

Type :

str

filter_text

Text used for live filtering (default “”, never None)

Type :

str

show_armatures

Surface animation data tied to armatures (default True)

Type :

bool

show_cache_files

Surface animation data tied to cache files (default True)

Type :

bool

show_cameras

Surface animation data tied to cameras (default True)

Type :

bool

show_curves

Surface animation data tied to curves (default True)

Type :

bool

show_datablock_filters

Reveal the toggles that decide which data types contribute channels (default False)

Type :

bool

show_driver_fallback_as_error

Let the Only Show Errors filter flag drivers that leaned on fallback values, even where evaluation still went through (default False)

Type :

bool

show_expanded_summary

Keep the summary collapsed so every other channel is hidden (Dope Sheet editors only) (default True)

Type :

bool

show_gpencil

Surface animation data and frames tied to Grease Pencil (default True)

Type :

bool

show_hair_curves

Surface animation data tied to hair (default True)

Type :

bool

show_hidden

Bring in channels from objects or bones that aren’t currently visible (default False)

Type :

bool

show_lattices

Surface animation data tied to lattices (default True)

Type :

bool

show_lightprobes

Surface animation data tied to light probes (default True)

Type :

bool

show_lights

Surface animation data tied to lights (default True)

Type :

bool

show_linestyles

Surface animation data tied to Line Styles (default True)

Type :

bool

show_materials

Surface animation data tied to materials (default True)

Type :

bool

show_meshes

Surface animation data tied to meshes (default True)

Type :

bool

show_metaballs

Surface animation data tied to metaballs (default True)

Type :

bool

show_missing_nla

Bring in animation data-blocks that lack NLA data (NLA editor only) (default True)

Type :

bool

show_modifiers

Surface animation data for data-blocks linked through modifiers (default True)

Type :

bool

show_movieclips

Surface animation data tied to movie clips (default True)

Type :

bool

show_nodes

Surface animation data tied to nodes (default True)

Type :

bool

show_only_errors

Restrict the view to F-Curves and drivers that are disabled or broken (default False)

Type :

bool

show_only_selected

Restrict channels to those for selected objects and data (default False)

Type :

bool

show_only_slot_of_active_object

Limit the display to the active Object’s slot; otherwise every one of the Action’s Slots appears (default False)

Type :

bool

show_particles

Surface animation data tied to particles (default True)

Type :

bool

show_pointclouds

Surface animation data tied to point clouds (default True)

Type :

bool

show_scenes

Surface animation data tied to scenes (default True)

Type :

bool

show_shapekeys

Surface animation data tied to shape keys (default True)

Type :

bool

show_speakers

Surface animation data tied to speakers (default True)

Type :

bool

show_summary

Add an extra ‘summary’ line to the display (Dope Sheet editors only) (default False)

Type :

bool

show_textures

Surface animation data tied to textures (default True)

Type :

bool

show_transforms

Surface object-level animation data, transforms above all (default True)

Type :

bool

show_volumes

Surface animation data tied to volumes (default True)

Type :

bool

show_worlds

Surface animation data tied to worlds (default True)

Type :

bool

source

The ID-block that supplies the source data, normally `ID_SCE` (a Scene) (readonly)

Type :

ID

use_datablock_sort

Sort data-blocks alphabetically — mostly the scene’s objects (turn off to speed the viewport up) (default True)

Type :

bool

use_filter_invert

Flip the meaning of the filter search (default False)

Type :

bool

use_multi_word_filter

Match in a fuzzy, multi-word way.
Warning: May be slow

(default False)

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

| SpaceDopeSheetEditor.dopesheet SpaceGraphEditor.dopesheet | SpaceNLA.dopesheet |

## DynamicPaintSurface(bpy_struct)

### DynamicPaintSurface(bpy_struct)

base class — bpy_struct

class bpy.types. DynamicPaintSurface ( bpy_struct )

One layer of a canvas surface

brush_collection

Restrict brush objects to this collection only

Type :

Collection

brush_influence_scale

Tune how much sway brush objects hold over this surface (in [0, 1], default 0.0)

Type :

float

brush_radius_scale

Tune the proximity-brush or particle radius for this surface (in [0, 10], default 0.0)

Type :

float

color_dry_threshold

The wetness at which colors begin drifting toward the background (in [0, 1], default 0.0)

Type :

float

color_spread_speed

The rate at which colors blend together inside wet paint (in [0, 2], default 0.0)

Type :

float

depth_clamp

Cap on depth intersection measured in object space (set 0.0 to switch off) (in [0, 50], default 0.0)

Type :

float

displace_factor

How forcefully displacement hits the mesh (in [-50, 50], default 0.0)

Type :

float

displace_type

(default 'DISPLACE' )

Type :

Literal[‘DISPLACE’, ‘DEPTH’]

dissolve_speed

Roughly how many frames a dissolve should take (in [1, 10000], default 0)

Type :

int

drip_acceleration

How far surface acceleration sways the dripping (in [-200, 200], default 0.0)

Type :

float

drip_velocity

How far surface velocity sways the dripping (in [-200, 200], default 0.0)

Type :

float

dry_speed

Roughly how many frames drying should take (in [1, 10000], default 0)

Type :

int

effect_ui

(default 'SPREAD' )

Type :

Literal[‘SPREAD’, ‘DRIP’, ‘SHRINK’]

effector_weights

(readonly)

Type :

EffectorWeights

frame_end

Last frame of the simulation (in [1, 1048574], default 0)

Type :

int

frame_start

First frame of the simulation (in [1, 1048574], default 0)

Type :

int

frame_substeps

Insert extra frames between scene frames so motion stays smooth (in [0, 20], default 0)

Type :

int

image_fileformat

(default 'PNG' )

Type :

Literal[‘PNG’, ‘OPENEXR’]

image_output_path

Folder the textures are written to (default “”, never None, blend relative // prefix supported)

Type :

str

image_resolution

Resolution of the output image (in [16, 4096], default 0)

Type :

int

init_color

The surface’s starting color (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

init_color_type

(default 'NONE' )

Type :

Literal[‘NONE’, ‘COLOR’, ‘TEXTURE’, ‘`VERTEX_COLOR`’]

init_layername

(default “”, never None)

Type :

str

init_texture

Type :

Texture

is_active

Switch this surface between being processed and being skipped (default False)

Type :

bool

is_cache_user

(default False, readonly)

Type :

bool

name

The surface’s name (default “”, never None)

Type :

str

output_name_a

The name this surface’s output is saved under (default “”, never None)

Type :

str

output_name_b

The name this surface’s output is saved under (default “”, never None)

Type :

str

point_cache

(readonly, never None)

Type :

PointCache

shrink_speed

The pace at which the shrink effect travels over the canvas surface (in [0.001, 10], default 0.0)

Type :

float

spread_speed

The pace at which the spread effect travels over the canvas surface (in [0.001, 10], default 0.0)

Type :

float

surface_format

The surface format (default 'VERTEX' )

Type :

Literal[‘VERTEX’, ‘IMAGE’]

surface_type

The surface type (default 'PAINT' )

Type :

Literal[‘PAINT’]

use_antialiasing

Smooth the paint edges with 5× multisampling (default False)

Type :

bool

use_dissolve

Turn on so surface changes fade away as time passes (default False)

Type :

bool

use_dissolve_log

Dissolve on a logarithmic curve (high values fall off quicker than low ones) (default False)

Type :

bool

use_drip

Run the drip effect (wet paint drips toward gravity) (default False)

Type :

bool

use_dry_log

Dry on a logarithmic curve (high values dry quicker than low ones) (default False)

Type :

bool

use_drying

Turn on so the surface’s wetness dries off over time (default False)

Type :

bool

use_incremental_displace

Stack new displacement on top of what’s already there (default False)

Type :

bool

use_output_a

Save out this output layer (default False)

Type :

bool

use_output_b

Save out this output layer (default False)

Type :

bool

use_premultiply

Premultiply the color by alpha (recommended when feeding back into Blender) (default False)

Type :

bool

use_shrink

Run the shrink effect (paint areas contract) (default False)

Type :

bool

use_spread

Run the spread effect (wet paint spreads across the surface) (default False)

Type :

bool

use_wave_open_border

Let waves carry through the mesh edges (default False)

Type :

bool

uv_layer

Name of the UV map (default “”, never None)

Type :

str

wave_damping

Damping applied to the waves (in [0, 1], default 0.0)

Type :

float

wave_smoothness

Cap on how steep the wave slope can get between simulation points (raise it for smoother waves at the cost of detail) (in [0, 10], default 0.0)

Type :

float

wave_speed

How fast the waves propagate (in [0.01, 5], default 0.0)

Type :

float

wave_spring

Spring force pulling the water level back toward zero (in [0, 1], default 0.0)

Type :

float

wave_timescale

Scaling applied to the wave timing (in [0.01, 3], default 0.0)

Type :

float

output_exists ( object , index )

Reports whether a surface output layer of the given name is present

Parameters :

- object (Object) – (never None)

- index ( int ) – Index, (in [0, 1])

Return type :

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

| DynamicPaintCanvasSettings.canvas_surfaces | DynamicPaintSurfaces.active |

## EffectStrip(Strip)

### EffectStrip(Strip)

base classes — bpy_struct, Strip

subclasses —
AddStrip, AdjustmentStrip, AlphaOverStrip, AlphaUnderStrip, ColorMixStrip, ColorStrip, CrossStrip, GammaCrossStrip, GaussianBlurStrip, GlowStrip, MulticamStrip, MultiplyStrip, SpeedControlStrip, SubtractStrip, TextStrip, WipeStrip

class bpy.types. EffectStrip ( Strip )

A sequencer strip that processes an effect onto imagery produced by other strips.

alpha_mode

How alpha is represented within the RGBA pixels (default 'STRAIGHT' )

- STRAIGHT
Straight – In transparent pixels the RGB channels are left untouched by the alpha channel.

- PREMUL
Premultiplied – In transparent pixels the RGB channels are already scaled by the alpha channel.

Type :

Literal[‘STRAIGHT’, ‘PREMUL’]

color_multiply

(in [0, 20], default 1.0)

Type :

float

color_saturation

Scale how saturated the input's colors appear (in [0, 20], default 1.0)

Type :

float

crop

(readonly)

Type :

StripCrop

multiply_alpha

Scale the alpha channel together with the color channels (default False)

Type :

bool

proxy

(readonly)

Type :

StripProxy

strobe

Show only every nth frame (in [1, 30], default 0.0)

Type :

float

transform

(readonly)

Type :

StripTransform

use_deinterlace

Strip interlacing fields out of video footage (default False)

Type :

bool

use_flip_x

Mirror across the X axis (default False)

Type :

bool

use_flip_y

Mirror across the Y axis (default False)

Type :

bool

use_float

Treat the input as float data (default False)

Type :

bool

use_proxy

Apply a preview proxy and/or time-code index to this strip (default False)

Type :

bool

use_reverse_frames

Play the frames back in reverse order (default False)

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

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start | Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py |

## EvaluateClosureNodeViewerPathElem(ViewerPathElem)

### EvaluateClosureNodeViewerPathElem(ViewerPathElem)

base classes — bpy_struct, ViewerPathElem

class bpy.types. EvaluateClosureNodeViewerPathElem ( ViewerPathElem )

evaluate_node_id

(in [-inf, inf], default 0)

Type :

int

source_node_tree

(readonly)

Type :

NodeTree

source_output_node_id

(in [-inf, inf], default 0)

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

| bpy_struct.id_data ViewerPathElem.type | ViewerPathElem.ui_name |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ViewerPathElem.bl_rna_get_subclass ViewerPathElem.bl_rna_get_subclass_py |

## See also

- [Bpy Struct](bpy-struct.md)
