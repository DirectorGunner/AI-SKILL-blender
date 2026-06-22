# Imagepaint Paint, Imagepreview Bpy Struct, Imagestrip Strip, Imagetexture Texture ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ImagePaint(Paint); ImagePreview(bpy_struct); ImageStrip(Strip); ImageTexture(Texture); ImageUser(bpy_struct); InlineShaderNodes.

## ImagePaint(Paint)

### ImagePaint(Paint)

base classes — bpy_struct, Paint

class bpy.types. ImagePaint ( Paint )

Settings that control image and texture painting mode.

canvas

The image serving as the canvas

Type :

Image

clone_alpha

Display opacity for the clone image (in [0, 1], default 0.5)

Type :

float

clone_image

The image used as the clone source

Type :

Image

clone_offset

(array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

dither

How much dithering to apply when painting onto byte images (in [0, 2], default 0.0)

Type :

float

interpolation

Type of texture filtering (default 'LINEAR' )

- LINEAR
Linear – Linear interpolation.

- CLOSEST
Closest – No interpolation (sample closest texel).

Type :

Literal[‘LINEAR’, ‘CLOSEST’]

invert_stencil

Flip the stencil layer (default False)

Type :

bool

missing_materials

The mesh has no materials (default False, readonly)

Type :

bool

missing_stencil

Image Painting lacks a stencil (default False, readonly)

Type :

bool

missing_texture

Image Painting lacks a texture to paint onto (default False, readonly)

Type :

bool

missing_uvs

The mesh has no UV layer (default False, readonly)

Type :

bool

mode

How projection painting operates (default 'MATERIAL' )

- MATERIAL
Material – Detect image slots from the material.

- IMAGE
Single Image – Set image for texture painting directly.

Type :

Literal[‘MATERIAL’, ‘IMAGE’]

normal_angle

Concentrate painting on faces facing the view, up to this angle (in [0, 90], default 80)

Type :

int

screen_grab_size

The capture size for re-projecting the image (array of 2 items, in [512, 16384], default (0, 0))

Type :

bpy_prop_array[int]

seam_bleed

Spread paint past the faces' UVs to cut down on seams (in pixels, slower) (in [-32768, 32767], default 2)

Type :

int

stencil_color

Color of the stencil in the viewport (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

stencil_image

The image used as a stencil

Type :

Image

use_backface_culling

Skip faces that point away from the view (faster) (default True)

Type :

bool

use_clone_layer

Treat another UV map as the clone source, otherwise the 3D cursor serves as the source (default False)

Type :

bool

use_normal_falloff

Concentrate painting on faces facing the view (default True)

Type :

bool

use_occlude

Restrict painting to the faces lying right beneath the brush (slower) (default True)

Type :

bool

use_stencil_layer

Take the mask layer from the UV map buttons (default False)

Type :

bool

detect_data ( )

Verify that the required texpaint data is present.

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

| bpy_struct.id_data Paint.brush Paint.brush_asset_reference Paint.eraser_brush Paint.eraser_brush_asset_reference Paint.palette Paint.show_brush Paint.show_brush_on_surface Paint.show_low_resolution Paint.use_sculpt_delay_updates Paint.show_bvh_nodes Paint.use_symmetry_x Paint.use_symmetry_y | Paint.use_symmetry_z Paint.use_symmetry_feather Paint.cavity_curve Paint.use_cavity Paint.tile_offset Paint.tile_x Paint.tile_y Paint.tile_z Paint.show_strength_curve Paint.show_size_curve Paint.show_jitter_curve Paint.unified_paint_settings |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Paint.bl_rna_get_subclass Paint.bl_rna_get_subclass_py |

### References

| ToolSettings.image_paint | |

## ImagePreview(bpy_struct)

### ImagePreview(bpy_struct)

base class — bpy_struct

class bpy.types. ImagePreview ( bpy_struct )

A preview image alongside its icon.

icon_id

A unique integer that identifies this preview as an icon (zero meaning invalid) (in [-inf, inf], default 0, readonly)

Type :

int

icon_pixels

The icon's pixels, given as bytes (always 32-bit RGBA) (in [-inf, inf], default 0)

Type :

int

icon_pixels_float

The icon's pixel components, given as floats (RGBA concatenated values) (in [-inf, inf], default 0.0)

Type :

float

icon_size

Pixel width and height (array of 2 items, in [-inf, inf], default (0, 0))

Type :

bpy_prop_array[int]

image_pixels

The image's pixels, given as bytes (always 32-bit RGBA) (in [-inf, inf], default 0)

Type :

int

image_pixels_float

The image's pixel components, given as floats (RGBA concatenated values) (in [-inf, inf], default 0.0)

Type :

float

image_size

Pixel width and height (array of 2 items, in [-inf, inf], default (0, 0))

Type :

bpy_prop_array[int]

is_icon_custom

True when a py script has altered this preview icon, so Blender no longer auto-generates it (default False)

Type :

bool

is_image_custom

True when a py script has altered this preview image, so Blender no longer auto-generates it (default False)

Type :

bool

reload ( )

Re-read the preview from where it is sourced.

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

| ID.preview | ID.preview_ensure |

## ImageStrip(Strip)

### ImageStrip(Strip)

base classes — bpy_struct, Strip

class bpy.types. ImageStrip ( Strip )

A sequence strip for bringing in one or more images.

alpha_mode

How alpha data sits within the RGBA pixels (default 'STRAIGHT' )

- STRAIGHT
Straight – The alpha channel leaves the RGB channels in transparent pixels alone.

- PREMUL
Premultiplied – The alpha channel scales the RGB channels in transparent pixels.

Type :

Literal[‘STRAIGHT’, ‘PREMUL’]

animation_offset_end

End offset of the animation (trim end) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_end’.

Type :

int

animation_offset_start

Start offset of the animation (trim start) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_start’.

Type :

int

color_multiply

(in [0, 20], default 1.0)

Type :

float

color_saturation

Dial the saturation of the input's color up or down (in [0, 20], default 1.0)

Type :

float

colorspace_settings

Color space settings for the input (readonly)

Type :

ColorManagedInputColorspaceSettings

content_trim_end

How many frames to skip at the end of the source. The source is trimmed and later frames become holds (in [0, inf], default 0)

Type :

int

content_trim_start

How many frames to skip at the start of the source. The source is trimmed and earlier frames become holds (in [0, inf], default 0)

Type :

int

crop

(readonly)

Type :

StripCrop

directory

(default “”, never None, blend relative // prefix supported)

Type :

str

elements

(default None, readonly)

Type :

StripElements[StripElement]

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

stereo_3d_format

Stereo 3D settings (readonly, never None)

Type :

Stereo3dFormat

strobe

Show only every nth frame (in [1, 30], default 0.0)

Type :

float

transform

(readonly)

Type :

StripTransform

use_deinterlace

Strip the fields out of video movies (default False)

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

Convert the input into float data (default False)

Type :

bool

use_multiview

Use Multiple Views (when available) (default False)

Type :

bool

use_proxy

Give this strip a preview proxy and/or a time-code index (default False)

Type :

bool

use_reverse_frames

Play the frames back in reverse (default False)

Type :

bool

views_format

How to load the image's views (default 'INDIVIDUAL' )

Type :

Literal[Views Format Items]

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

## ImageTexture(Texture)

### ImageTexture(Texture)

base classes — bpy_struct, ID, Texture

class bpy.types. ImageTexture ( Texture )

checker_distance

Gap between checker tiles (in [0, 0.99], default 0.0)

Type :

float

crop_max_x

The largest X value at which to crop the image (in [-10, 10], default 1.0)

Type :

float

crop_max_y

The largest Y value at which to crop the image (in [-10, 10], default 1.0)

Type :

float

crop_min_x

The smallest X value at which to crop the image (in [-10, 10], default 0.0)

Type :

float

crop_min_y

The smallest Y value at which to crop the image (in [-10, 10], default 0.0)

Type :

float

extension

What happens to the image beyond its original bounds (default 'REPEAT' )

- EXTEND
Extend – Carry the image's edge pixels outward.

- CLIP
Clip – Limit to the image size and make pixels outside it transparent.

- `CLIP_CUBE`
Clip Cube – Limit to a cube-shaped region around the image and make pixels outside it transparent.

- REPEAT
Repeat – Tile the image across both horizontally and vertically.

- CHECKER
Checker – Tile the image in a checkerboard arrangement.

Type :

Literal[‘EXTEND’, ‘CLIP’, ‘`CLIP_CUBE`’, ‘REPEAT’, ‘CHECKER’]

filter_size

Scale the filter size used during interpolation (in [0.1, 50], default 1.0)

Type :

float

image

Type :

Image

image_user

Settings picking which layer, pass and frame of the image to show (readonly)

Type :

ImageUser

invert_alpha

Flip every alpha value in the image (default False)

Type :

bool

repeat_x

How many times to repeat along the X direction (in [1, 512], default 1)

Type :

int

repeat_y

How many times to repeat along the Y direction (in [1, 512], default 1)

Type :

int

use_alpha

Make use of the image's alpha channel (default True)

Type :

bool

use_calculate_alpha

Derive an alpha channel from the image's RGB values (default False)

Type :

bool

use_checker_even

Even checker tiles (default False)

Type :

bool

use_checker_odd

Odd checker tiles (default True)

Type :

bool

use_flip_axis

Swap the texture's X and Y axes (default False)

Type :

bool

use_interpolation

Interpolate pixels with the chosen filter (default True)

Type :

bool

use_mirror_x

Mirror the repetition along the X direction (default False)

Type :

bool

use_mirror_y

Mirror the repetition along the Y direction (default False)

Type :

bool

use_normal_map

Treat the image's RGB values as a normal map (default False)

Type :

bool

users_material

The materials that make use of this texture

Type :

tuple[Material, …]

Note

Takes O(len(bpy.data.materials) * len(material.texture_slots)) time.

(readonly)

users_object_modifier

The object modifiers that make use of this texture

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

## ImageUser(bpy_struct)

### ImageUser(bpy_struct)

base class — bpy_struct

class bpy.types. ImageUser ( bpy_struct )

Settings describing how one data-block draws on an Image data-block.

frame_current

The current frame within the image sequence or movie (in [-1048574, 1048574], default 0)

Type :

int

frame_duration

How many of a movie's images to use (in [0, 1048574], default 0)

Type :

int

frame_offset

Shift which frame number is used in the animation (in [-inf, inf], default 0)

Type :

int

frame_start

The movie/sequence's global start frame, taking the first picture as #1 (in [-1048574, 1048574], default 0)

Type :

int

multilayer_layer

The layer within a multilayer image (in [0, 32767], default 0, readonly)

Type :

int

multilayer_pass

The pass within a multilayer image (in [0, 32767], default 0, readonly)

Type :

int

multilayer_view

The view within a multilayer image (in [0, 32767], default 0, readonly)

Type :

int

tile

The tile within a tiled image (in [0, inf], default 0)

Type :

int

use_auto_refresh

Refresh the image every time the frame changes (default False)

Type :

bool

use_cyclic

Loop through the movie's images (default False)

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

| CameraBackgroundImage.image_user Image.filepath_from_user ImageTexture.image_user Object.image_user RenderSlot.clear ShaderNodeTexEnvironment.image_user | ShaderNodeTexImage.image_user SpaceImageEditor.image_user TextureNodeImage.image_user UILayout.template_image UILayout.template_image_layers |

## InlineShaderNodes

### InlineShaderNodes

### Inline Shader Nodes

`\text
import bpy

### The materials should be retrieved from the evaluated object to make sure that
### e.g. edits of Geometry Nodes are applied.
depsgraph = bpy.context.view_layer.depsgraph
ob = bpy.context.active_object
ob_eval = depsgraph.id_eval_get(ob)
material_eval = ob_eval.material_slots[0].material

### Compute the inlined shader nodes.
### Important: Do not loose the reference to this object while accessing the inlined
### node tree. Otherwise there will be a crash due to a dangling pointer.
inline_shader_nodes = material_eval.inline_shader_nodes()

### Get the actual inlined `bpy.types.NodeTree`.
tree = inline_shader_nodes.node_tree

for node in tree.nodes:
print(node.name)
`

class InlineShaderNodes

A shader node tree that has been inlined.

node_tree

The inlined node tree.

Type :

bpy.types.NodeTree

static from_light ( light )

Build an inlined shader node tree out of a light.

Parameters :

light (bpy.types.Light) – The light to online the node tree of.

static from_material ( material )

Build an inlined shader node tree out of a material.

Parameters :

material (bpy.types.Material) – The material to inline the node tree of.

static from_world ( world )

Build an inlined shader node tree out of a world.

Parameters :

world (bpy.types.World) – The world to inline the node tree of.

## See also

- [Bpy Struct](bpy-struct.md)
