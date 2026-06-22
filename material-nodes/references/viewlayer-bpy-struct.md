# Viewlayer Bpy Struct, Volume Id, Volumedisplay Bpy Struct, Voronoitexture Texture ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ViewLayer(bpy_struct); Volume(ID); VolumeDisplay(bpy_struct); VoronoiTexture(Texture); WipeStrip(EffectStrip).

## ViewLayer(bpy_struct)

### ViewLayer(bpy_struct)

base class — bpy_struct

class bpy.types. ViewLayer ( bpy_struct )

View layer

active_aov

Active AOV (readonly)

Type :

AOV

active_aov_index

Index of active AOV (in [0, inf], default 0)

Type :

int

active_layer_collection

The layer collection currently active inside this view layer's tree (never None)

Type :

LayerCollection

active_lightgroup

Active Lightgroup (readonly)

Type :

Lightgroup

active_lightgroup_index

Index of active lightgroup (in [0, inf], default 0)

Type :

int

aovs

(default None, readonly)

Type :

AOVs[AOV]

cycles

Cycles ViewLayer Settings (readonly)

Type :

CyclesRenderLayerSettings

depsgraph

Dependencies in the scene data (readonly)

Type :

Depsgraph

eevee

View layer settings for EEVEE (readonly, never None)

Type :

ViewLayerEEVEE

freestyle_settings

(readonly, never None)

Type :

FreestyleSettings

has_export_collections

True when one or more collections in this view layer carry an exporter (default False, readonly)

Type :

bool

layer_collection

Top of this view layer's collection tree; its 'collection' pointer matches the scene's master collection (readonly, never None)

Type :

LayerCollection

lightgroups

(default None, readonly)

Type :

Lightgroups[Lightgroup]

material_override

Material that replaces every other material across this view layer

Type :

Material

name

View layer name (default "", never None)

Type :

str

objects

Every object contained in this layer (default None, readonly)

Type :

LayerObjects[Object]

pass_alpha_threshold

Z, Index, normal, UV and vector passes register a surface only when its alpha transparency meets or exceeds this cutoff (in [0, 1], default 0.5)

Type :

float

pass_cryptomatte_depth

Number of distinct objects that can be told apart within a single pixel (in [2, 16], default 6)

Type :

int

samples

Per-view-layer override for the render sample count; leave at 0 to fall back to the scene value (in [0, inf], default 0)

Type :

int

use

Turn rendering of this View Layer on or off (default True)

Type :

bool

use_ao

Compute Ambient Occlusion for this Layer (default True)

Type :

bool

use_freestyle

Draw stylized strokes in this Layer (default True)

Type :

bool

use_grease_pencil

Include Grease Pencil when rendering this layer (default True)

Type :

bool

use_motion_blur

Apply motion blur to this Layer when the scene has it enabled (default True)

Type :

bool

use_pass_ambient_occlusion

Output an Ambient Occlusion pass (default False)

Type :

bool

use_pass_combined

Output the complete combined RGBA buffer (default True)

Type :

bool

use_pass_cryptomatte_accurate

Produce a higher-precision cryptomatte pass (default True)

Type :

bool

use_pass_cryptomatte_asset

Output a cryptomatte asset pass that isolates object groups sharing a parent (default False)

Type :

bool

use_pass_cryptomatte_material

Output a cryptomatte material pass for separating materials during compositing (default False)

Type :

bool

use_pass_cryptomatte_object

Output a cryptomatte object pass for separating objects during compositing (default False)

Type :

bool

use_pass_diffuse_color

Output a diffuse color pass (default False)

Type :

bool

use_pass_diffuse_direct

Output a diffuse direct pass (default False)

Type :

bool

use_pass_diffuse_indirect

Output a diffuse indirect pass (default False)

Type :

bool

use_pass_emit

Output an emission pass (default False)

Type :

bool

use_pass_environment

Output an environment lighting pass (default False)

Type :

bool

use_pass_glossy_color

Output a glossy color pass (default False)

Type :

bool

use_pass_glossy_direct

Output a glossy direct pass (default False)

Type :

bool

use_pass_glossy_indirect

Output a glossy indirect pass (default False)

Type :

bool

use_pass_grease_pencil

Output the Grease Pencil render result as its own pass (default False)

Type :

bool

use_pass_material_index

Output a material index pass (default False)

Type :

bool

use_pass_mist

Output a mist factor pass (0.0 to 1.0) (default False)

Type :

bool

use_pass_normal

Output a normal pass (default False)

Type :

bool

use_pass_object_index

Output an object index pass (default False)

Type :

bool

use_pass_position

Output a position pass (default False)

Type :

bool

use_pass_shadow

Output a shadow pass (default False)

Type :

bool

use_pass_subsurface_color

Output a subsurface color pass (default False)

Type :

bool

use_pass_subsurface_direct

Output a subsurface direct pass (default False)

Type :

bool

use_pass_subsurface_indirect

Output a subsurface indirect pass (default False)

Type :

bool

use_pass_transmission_color

Output a transmission color pass (default False)

Type :

bool

use_pass_transmission_direct

Output a transmission direct pass (default False)

Type :

bool

use_pass_transmission_indirect

Output a transmission indirect pass (default False)

Type :

bool

use_pass_uv

Output a texture UV pass (default False)

Type :

bool

use_pass_vector

Output a speed vector pass (default False)

Type :

bool

use_pass_z

Output a depth value pass (default False)

Type :

bool

use_sky

Include the Sky when rendering this Layer (default True)

Type :

bool

use_solid

Include Solid faces when rendering this Layer (default True)

Type :

bool

use_strand

Include Strands when rendering this Layer (default True)

Type :

bool

use_volumes

Include volumes when rendering this Layer (default True)

Type :

bool

world_override

World that replaces the scene world across this view layer

Type :

World

bl_system_properties_get ( * , do_create = False )

DEBUG ONLY. Low-level entry point to runtime-defined RNA storage, meant purely for tests and debugging. Steer clear of it in normal scripts, and never assume what it returns is writable.

Parameters :

do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)

Returns :

The root container for system properties, or None when none are stored yet on this data and creation was not asked for

Return type :

PropertyGroup

classmethod update_render_passes ( )

Re-fetch the set of enabled render passes from the render engine

update ( )

Refresh data flagged for update following earlier access to data or operators

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

| bpy.context.view_layer Context.view_layer Depsgraph.view_layer Depsgraph.view_layer_eval ID.override_hierarchy_create IDOverrideLibrary.resync LayerCollection.has_selected_objects Object.hide_get Object.hide_set Object.holdout_get Object.indirect_only_get | Object.select_get Object.select_set Object.visible_get RenderEngine.register_pass RenderEngine.update_render_passes Scene.statistics Scene.view_layers ViewLayers.new ViewLayers.remove Window.view_layer |

## Volume(ID)

### Volume(ID)

base classes — bpy_struct, ID

class bpy.types. Volume ( ID )

Data-block that holds 3D volume grids.

animation_data

Animation data for this data-block (readonly)

Type :

AnimData

display

Volume display settings for 3D viewport (readonly)

Type :

VolumeDisplay

filepath

Volume file backing this Volume data-block (default "", never None, blend relative // prefix supported)

Type :

str

frame_duration

How many frames of the sequence to play back (in [0, 1048574], default 0)

Type :

int

frame_offset

Shift applied to which frame of the animation is used (in [-inf, inf], default 0)

Type :

int

frame_start

The scene frame the sequence begins on, treating the first file as #1 (in [-1048574, 1048574], default 1)

Type :

int

grids

3D volume grids (default None, readonly)

Type :

VolumeGrids[VolumeGrid]

is_sequence

Whether the cache spans a numbered series of files (default False)

Type :

bool

materials

(default None, readonly)

Type :

IDMaterials[Material]

packed_file

(readonly)

Type :

PackedFile

render

Volume render settings for 3D viewport (readonly)

Type :

VolumeRender

sequence_mode

How the frame sequence is played (default 'CLIP' )

- CLIP
Clip – Conceal any frames that fall outside the chosen range.

- EXTEND
Extend – Hold the first frame before the range and the last frame after it.

- REPEAT
Repeat – Loop the frames in the sequence.

- `PING_PONG`
Ping-Pong – Bounce through the frames, flipping direction each pass.

Type :

Literal['CLIP', 'EXTEND', 'REPEAT', '`PING_PONG`']

velocity_grid

Name of the velocity field, or its base name when the velocity spans several grids (default "", never None)

Type :

str

velocity_scale

Factor controlling how much motion blur is produced (in [0, inf], default 1.0)

Type :

float

velocity_unit

How velocity vectors relate to time: 'frame' treats the delta as 1 frame, 'second' treats it as 1 / FPS (default 'FRAME' )

Type :

Literal[Velocity Unit Items]

velocity_x_grid

Grid name holding the X component of the velocity field when it is stored across separate grids (default "", readonly, never None)

Type :

str

velocity_y_grid

Grid name holding the Y component of the velocity field when it is stored across separate grids (default "", readonly, never None)

Type :

str

velocity_z_grid

Grid name holding the Z component of the velocity field when it is stored across separate grids (default "", readonly, never None)

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| bpy.context.volume BlendData.volumes | BlendDataVolumes.new BlendDataVolumes.remove |

## VolumeDisplay(bpy_struct)

### VolumeDisplay(bpy_struct)

base class — bpy_struct

class bpy.types. VolumeDisplay ( bpy_struct )

Settings for showing a volume object in the 3D viewport.

density

How thick the volume looks when drawn in the viewport (in [1e-05, inf], default 1.0)

Type :

float

interpolation_method

Which interpolation is applied to volumes in solid mode (default 'LINEAR' )

- LINEAR
Linear – A solid balance of smoothness and speed.

- CUBIC
Cubic – Higher-quality smoothed result, at a slower pace.

- CLOSEST
Closest – Skip interpolation entirely.

Type :

Literal['LINEAR', 'CUBIC', 'CLOSEST']

slice_axis

(default 'AUTO' )

- AUTO
Auto – Pick the slice direction from the current view angle.

- X
X – Cut along the X axis.

- Y
Y – Cut along the Y axis.

- Z
Z – Cut along the Z axis.

Type :

Literal['AUTO', 'X', 'Y', 'Z']

slice_depth

Where along the axis the slice sits (in [0, 1], default 0.5)

Type :

float

use_slice

Take a single slice through the domain object (default False)

Type :

bool

wireframe_detail

How much detail the wireframe display shows (default 'COARSE' )

- COARSE
Coarse – Draw one box or point per intermediate tree node.

- FINE
Fine – Draw a box for every leaf node holding 8×8 voxels.

Type :

Literal['COARSE', 'FINE']

wireframe_type

Which wireframe style is drawn (default 'BOXES' )

- NONE
None – Skip drawing the volume in wireframe mode.

- BOUNDS
Bounds – Draw a single bounding box around the whole grid.

- BOXES
Boxes – Draw bounding boxes for the nodes in the volume tree.

- POINTS
Points – Draw points for the nodes in the volume tree.

Type :

Literal['NONE', 'BOUNDS', 'BOXES', 'POINTS']

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

| Volume.display | |

## VoronoiTexture(Texture)

### VoronoiTexture(Texture)

base classes — bpy_struct, ID, Texture

class bpy.types. VoronoiTexture ( Texture )

A procedural voronoi texture.

color_mode

(default 'INTENSITY' )

- INTENSITY
Intensity – Compute intensity only.

- POSITION
Position – Tint cells according to their position.

- `POSITION_OUTLINE`
Position and Outline – Combine position with an outline derived from F2-F1.

- `POSITION_OUTLINE_INTENSITY`
Position, Outline, and Intensity – Scale position and outline by the intensity.

Type :

Literal['INTENSITY', 'POSITION', '`POSITION_OUTLINE`', '`POSITION_OUTLINE_INTENSITY`']

distance_metric

Which algorithm measures distance from sample points to feature points (default 'DISTANCE' )

- DISTANCE
Actual Distance – sqrt(x*x+y*y+z*z).

- `DISTANCE_SQUARED`
Distance Squared – (x*x+y*y+z*z).

- MANHATTAN
Manhattan – The length of the distance in axial directions.

- CHEBYCHEV
Chebychev – The length of the longest Axial journey.

- `MINKOVSKY_HALF`
Minkowski 1/2 – Set Minkowski variable to 0.5.

- `MINKOVSKY_FOUR`
Minkowski 4 – Set Minkowski variable to 4.

- MINKOVSKY
Minkowski – Use the Minkowski function to calculate distance (exponent value determines the shape of the boundaries).

Type :

Literal['DISTANCE', '`DISTANCE_SQUARED`', 'MANHATTAN', 'CHEBYCHEV', '`MINKOVSKY_HALF`', '`MINKOVSKY_FOUR`', 'MINKOVSKY']

minkovsky_exponent

Minkowski exponent (in [0.01, 10], default 2.5)

Type :

float

nabla

Derivative offset size used when computing the normal (in [0.001, 0.1], default 0.025)

Type :

float

noise_intensity

Scales the intensity of the noise (in [0.01, 10], default 1.0)

Type :

float

noise_scale

Scaling for noise input (in [0.0001, inf], default 0.25)

Type :

float

weight_1

Voronoi feature weight 1 (in [-2, 2], default 1.0)

Type :

float

weight_2

Voronoi feature weight 2 (in [-2, 2], default 0.0)

Type :

float

weight_3

Voronoi feature weight 3 (in [-2, 2], default 0.0)

Type :

float

weight_4

Voronoi feature weight 4 (in [-2, 2], default 0.0)

Type :

float

users_material

Materials that use this texture

Type :

tuple[Material, …]

Note

Takes O(len(bpy.data.materials) * len(material.texture_slots)) time.

(readonly)

users_object_modifier

Object modifiers that use this texture

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

## WipeStrip(EffectStrip)

### WipeStrip(EffectStrip) 

base classes — bpy_struct, Strip, EffectStrip

class bpy.types. WipeStrip ( EffectStrip ) 

A sequencer strip that produces a wipe-style transition

angle 

The tilt applied to the transition (in [-1.5708, 1.5708], default 0.0)

Type :

float

blur_width 

How soft the transition edge is, expressed as a fraction of the image dimensions (in [0, 1], default 0.0)

Type :

float

direction 

Selects whether the wipe reveals or conceals (default 'OUT' )

Type :

Literal[‘OUT’, ‘IN’]

input_1 

The strip feeding the effect's first slot (never None)

Type :

Strip

input_2 

The strip feeding the effect's second slot (never None)

Type :

Strip

input_count 

(in [0, inf], default 0, readonly)

Type :

int

transition_type 

(default 'SINGLE' )

Type :

Literal[‘SINGLE’, ‘DOUBLE’, ‘IRIS’, ‘CLOCK’]

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

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset | Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys EffectStrip.use_deinterlace EffectStrip.alpha_mode EffectStrip.use_flip_x EffectStrip.use_flip_y EffectStrip.use_float EffectStrip.use_reverse_frames EffectStrip.color_multiply EffectStrip.multiply_alpha EffectStrip.color_saturation EffectStrip.strobe EffectStrip.transform EffectStrip.crop EffectStrip.use_proxy EffectStrip.proxy |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py EffectStrip.bl_rna_get_subclass EffectStrip.bl_rna_get_subclass_py |

## See also

- [Bpy Struct](bpy-struct.md)
