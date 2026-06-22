# Stripsmeta Bpy Prop Collection, Stripstoplevel Bpy Prop Collection, Striptransform Bpy Struct, Stuccitexture Texture ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: StripsMeta(bpy_prop_collection); StripsTopLevel(bpy_prop_collection); StripTransform(bpy_struct); StucciTexture(Texture); StudioLight(bpy_struct).

## StripsMeta(bpy_prop_collection)

### StripsMeta(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. StripsMeta ( bpy_prop_collection )

A group of Strips.

new_clip ( name , clip , channel , frame_start )

Add a new movie clip strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- clip (MovieClip) – Movie clip to add (never None)

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-1048574, 1048574])

Returns :

New Strip

Return type :

Strip

new_mask ( name , mask , channel , frame_start )

Add a new mask strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- mask (Mask) – Mask to add (never None)

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-1048574, 1048574])

Returns :

New Strip

Return type :

Strip

new_scene ( name , scene , channel , frame_start )

Add a new scene strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- scene (Scene) – Scene to add (never None)

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-1048574, 1048574])

Returns :

New Strip

Return type :

Strip

new_image ( name , filepath , channel , frame_start , * , fit_method = 'ORIGINAL' )

Add a new image strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- filepath ( str ) – Filepath to image (never None)

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-1048574, 1048574])

- fit_method (Literal[Strip Scale Method Items]) – Image Fit Method, (optional)

Returns :

New Strip

Return type :

Strip

new_movie ( name , filepath , channel , frame_start , * , fit_method = 'ORIGINAL' )

Add a new movie strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- filepath ( str ) – Filepath to movie (never None)

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-1048574, 1048574])

- fit_method (Literal[Strip Scale Method Items]) – Image Fit Method, (optional)

Returns :

New Strip

Return type :

Strip

new_sound ( name , filepath , channel , frame_start )

Add a new sound strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- filepath ( str ) – Filepath to movie (never None)

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-1048574, 1048574])

Returns :

New Strip

Return type :

Strip

new_meta ( name , channel , frame_start )

Add a new meta strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-1048574, 1048574])

Returns :

New Strip

Return type :

Strip

new_effect ( name , type , channel , frame_start , * , length = 0 , input1 = None , input2 = None )

Add a new effect strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- type ( Literal [ 'CROSS' , 'ADD' , 'SUBTRACT' , '`ALPHA_OVER`' , '`ALPHA_UNDER`' , '`GAMMA_CROSS`' , 'MULTIPLY' , 'WIPE' , 'GLOW' , 'COLOR' , 'SPEED' , 'MULTICAM' , 'ADJUSTMENT' , '`GAUSSIAN_BLUR`' , 'TEXT' , 'COLORMIX' ] ) – Type, type for the new strip

- CROSS
Crossfade – Fade out of one video, fading into another.

- ADD
Add – Add together color channels from two videos.

- SUBTRACT
Subtract – Subtract one strip’s color from another.

- `ALPHA_OVER`
Alpha Over – Blend alpha on top of another video.

- `ALPHA_UNDER`
Alpha Under – Blend alpha below another video.

- `GAMMA_CROSS`
Gamma Crossfade – Crossfade with color correction.

- MULTIPLY
Multiply – Multiply color channels from two videos.

- WIPE
Wipe – Sweep a transition line across the frame.

- GLOW
Glow – Add blur and brightness to light areas.

- COLOR
Color – Add a simple color strip.

- SPEED
Speed – Timewarp video strips, modifying playback speed.

- MULTICAM
Multicam Selector – Control active camera angles.

- ADJUSTMENT
Adjustment Layer – Apply nondestructive effects.

- `GAUSSIAN_BLUR`
Gaussian Blur – Soften details along axes.

- TEXT
Text – Add a simple text strip.

- COLORMIX
Color Mix – Combine two strips using blend modes.

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-inf, inf])

- length ( int ) – Length of the strip in frames, or the length of each strip if multiple are added (in [-inf, inf], optional)

- input1 (Strip) – First input strip for effect (optional)

- input2 (Strip) – Second input strip for effect (optional)

Returns :

New Strip

Return type :

Strip

remove ( sequence )

Remove a Strip

Parameters :

sequence (Strip) – Strip to remove (never None)

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

| MetaStrip.strips | |

## StripsTopLevel(bpy_prop_collection)

### StripsTopLevel(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. StripsTopLevel ( bpy_prop_collection )

A group of Strips.

new_clip ( name , clip , channel , frame_start )

Add a new movie clip strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- clip (MovieClip) – Movie clip to add (never None)

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-1048574, 1048574])

Returns :

New Strip

Return type :

Strip

new_mask ( name , mask , channel , frame_start )

Add a new mask strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- mask (Mask) – Mask to add (never None)

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-1048574, 1048574])

Returns :

New Strip

Return type :

Strip

new_scene ( name , scene , channel , frame_start )

Add a new scene strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- scene (Scene) – Scene to add (never None)

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-1048574, 1048574])

Returns :

New Strip

Return type :

Strip

new_image ( name , filepath , channel , frame_start , * , fit_method = 'ORIGINAL' )

Add a new image strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- filepath ( str ) – Filepath to image (never None)

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-1048574, 1048574])

- fit_method (Literal[Strip Scale Method Items]) – Image Fit Method, (optional)

Returns :

New Strip

Return type :

Strip

new_movie ( name , filepath , channel , frame_start , * , fit_method = 'ORIGINAL' )

Add a new movie strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- filepath ( str ) – Filepath to movie (never None)

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-1048574, 1048574])

- fit_method (Literal[Strip Scale Method Items]) – Image Fit Method, (optional)

Returns :

New Strip

Return type :

Strip

new_sound ( name , filepath , channel , frame_start )

Add a new sound strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- filepath ( str ) – Filepath to movie (never None)

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-1048574, 1048574])

Returns :

New Strip

Return type :

Strip

new_meta ( name , channel , frame_start )

Add a new meta strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-1048574, 1048574])

Returns :

New Strip

Return type :

Strip

new_effect ( name , type , channel , frame_start , * , length = 0 , input1 = None , input2 = None )

Add a new effect strip

Parameters :

- name ( str ) – Name for the new strip (never None)

- type ( Literal [ 'CROSS' , 'ADD' , 'SUBTRACT' , '`ALPHA_OVER`' , '`ALPHA_UNDER`' , '`GAMMA_CROSS`' , 'MULTIPLY' , 'WIPE' , 'GLOW' , 'COLOR' , 'SPEED' , 'MULTICAM' , 'ADJUSTMENT' , '`GAUSSIAN_BLUR`' , 'TEXT' , 'COLORMIX' ] ) – Type, type for the new strip

- CROSS
Crossfade – Fade out of one video, fading into another.

- ADD
Add – Add together color channels from two videos.

- SUBTRACT
Subtract – Subtract one strip’s color from another.

- `ALPHA_OVER`
Alpha Over – Blend alpha on top of another video.

- `ALPHA_UNDER`
Alpha Under – Blend alpha below another video.

- `GAMMA_CROSS`
Gamma Crossfade – Crossfade with color correction.

- MULTIPLY
Multiply – Multiply color channels from two videos.

- WIPE
Wipe – Sweep a transition line across the frame.

- GLOW
Glow – Add blur and brightness to light areas.

- COLOR
Color – Add a simple color strip.

- SPEED
Speed – Timewarp video strips, modifying playback speed.

- MULTICAM
Multicam Selector – Control active camera angles.

- ADJUSTMENT
Adjustment Layer – Apply nondestructive effects.

- `GAUSSIAN_BLUR`
Gaussian Blur – Soften details along axes.

- TEXT
Text – Add a simple text strip.

- COLORMIX
Color Mix – Combine two strips using blend modes.

- channel ( int ) – Channel, The channel for the new strip (in [1, 128])

- frame_start ( int ) – The start frame for the new strip (in [-inf, inf])

- length ( int ) – Length of the strip in frames, or the length of each strip if multiple are added (in [-inf, inf], optional)

- input1 (Strip) – First input strip for effect (optional)

- input2 (Strip) – Second input strip for effect (optional)

Returns :

New Strip

Return type :

Strip

remove ( sequence )

Remove a Strip

Parameters :

sequence (Strip) – Strip to remove (never None)

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

| SequenceEditor.strips | |

## StripTransform(bpy_struct)

### StripTransform(bpy_struct)

base class — bpy_struct

class bpy.types. StripTransform ( bpy_struct )

The transform controls belonging to a sequence strip.

filter

Type of filter to use for image transformation (default 'AUTO' )

- AUTO
Auto – Automatically choose filter based on scaling factor.

- NEAREST
Nearest – Use nearest sample.

- BILINEAR
Bilinear – Interpolate between 2×2 samples.

- `CUBIC_MITCHELL`
Cubic Mitchell – Cubic Mitchell filter on 4×4 samples.

- `CUBIC_BSPLINE`
Cubic B-Spline – Cubic B-Spline filter (blurry but no ringing) on 4×4 samples.

- BOX
Box – Averages source image samples that fall under destination pixel.

Type :

Literal[‘AUTO’, ‘NEAREST’, ‘BILINEAR’, ‘`CUBIC_MITCHELL`’, ‘`CUBIC_BSPLINE`’, ‘BOX’]

offset_x

Move along X axis (in [-inf, inf], default 0.0)

Type :

float

offset_y

Move along Y axis (in [-inf, inf], default 0.0)

Type :

float

origin

Origin of image for transformation (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

bpy_prop_array[float]

rotation

Rotate around image center (in [-inf, inf], default 0.0)

Type :

float

scale_x

Scale along X axis (in [0, inf], default 1.0)

Type :

float

scale_y

Scale along Y axis (in [0, inf], default 1.0)

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

| EffectStrip.transform ImageStrip.transform MaskStrip.transform MetaStrip.transform | MovieClipStrip.transform MovieStrip.transform SceneStrip.transform |

## StucciTexture(Texture)

### StucciTexture(Texture)

base classes — bpy_struct, ID, Texture

class bpy.types. StucciTexture ( Texture )

A procedural texture built from noise.

noise_basis

Noise basis used for turbulence (default '`BLENDER_ORIGINAL`' )

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

Scaling for noise input (in [0.0001, inf], default 0.25)

Type :

float

noise_type

(default '`SOFT_NOISE`' )

- `SOFT_NOISE`
Soft – Generate soft noise (smooth transitions).

- `HARD_NOISE`
Hard – Generate hard noise (sharp transitions).

Type :

Literal[‘`SOFT_NOISE`’, ‘`HARD_NOISE`’]

stucci_type

(default 'PLASTIC' )

- PLASTIC
Plastic – Use standard stucci.

- `WALL_IN`
Wall In – Create Dimples.

- `WALL_OUT`
Wall Out – Create Ridges.

Type :

Literal[‘PLASTIC’, ‘`WALL_IN`’, ‘`WALL_OUT`’]

turbulence

Turbulence of the noise (in [0.0001, inf], default 5.0)

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

## StudioLight(bpy_struct)

### StudioLight(bpy_struct)

base class — bpy_struct

class bpy.types. StudioLight ( bpy_struct )

A studio light.

has_specular_highlight_pass

Studio light image file has separate “diffuse” and “specular” passes (default False, readonly)

Type :

bool

index

(in [-inf, inf], default 0, readonly)

Type :

int

is_user_defined

(default False, readonly)

Type :

bool

light_ambient

Color of the ambient light that uniformly lit the scene (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Color

name

(default “”, readonly, never None)

Type :

str

path

(default “”, readonly, never None)

Type :

str

solid_lights

Lights used to display objects in solid draw mode (default None, readonly)

Type :

bpy_prop_collection[UserSolidLight]

type

(default 'STUDIO' , readonly)

Type :

Literal[‘STUDIO’, ‘WORLD’, ‘MATCAP’]

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

| Preferences.studio_lights StudioLights.load StudioLights.new | StudioLights.remove View3DShading.selected_studio_light |

## See also

- [Bpy Struct](bpy-struct.md)
