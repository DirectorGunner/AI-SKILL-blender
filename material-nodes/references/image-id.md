# Image Id, Image Ast Brush Paint Assetshelf, Image Fh Drop Handler Filehandler, Imageformatsettings Bpy Struct ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Image(ID); `IMAGE_AST`_brush_paint(AssetShelf); `IMAGE_FH`_drop_handler(FileHandler); ImageFormatSettings(bpy_struct); ImagePackedFile(bpy_struct).

## Image(ID)

### Image(ID)

### Image Data

An Image data-block is a thin layer wrapping one or more image or video files (held on disk, packed inside, or generated).

The real payload — pixel data, dimensions, resolution and so on — lives in an imbuf.types.ImBuf image buffer (or in several of them, as happens with UDIM textures, multi-views or animations…).

Because of this, a number of the Image data-block's properties and methods actually read from or write to its image buffer rather than to the data-block.

Warning

A notable catch: image buffers are never shared across separate Image data-blocks, nor are they copied when an image is duplicated.

That means edits to an image buffer stay confined until the buffer is written to disk; duplicating the Image data-block beforehand will not carry the buffer changes over to the new Image.

The script below builds an Image data-block at a chosen size, alters its first pixel, resizes it, then makes a duplicate.

The copy keeps the dimensions and colors the original had when it was first made; every edit to the original's buffer is ‘lost’ in the duplicate.

`\text
import bpy

image_src = bpy.data.images.new('src', 1024, 102)
print(image_src.size)
print(image_src.pixels[0:4])

image_src.scale(1024, 720)
image_src.pixels[0:4] = (0.5, 0.5, 0.5, 0.5)
image_src.update()
print(image_src.size)
print(image_src.pixels[0:4])

image_dest = image_src.copy()
image_dest.update()
print(image_dest.size)
print(image_dest.pixels[0:4])
`

base classes — bpy_struct, ID

class bpy.types. Image ( ID )

An Image data-block that points at an external or packed image.

alpha_mode

How alpha is held in the image file, used to convert in both directions while saving and loading (default 'STRAIGHT' )

- STRAIGHT
Straight – Hold the RGB and alpha channels apart, with alpha used as a mask; also called unassociated alpha. Widely used by image editors and by formats such as PNG..

- PREMUL
Premultiplied – Hold RGB channels with alpha already multiplied in; also called associated alpha. The natural choice for renders, and used by formats such as OpenEXR..

- `CHANNEL_PACKED`
Channel Packed – Pack unrelated images into the RGB and alpha channels so they stay independent. Channel packing is a common memory-saving trick in game engines..

- NONE
None – Disregard the file's alpha channel and treat the image as fully opaque.

Type :

Literal[‘STRAIGHT’, ‘PREMUL’, ‘`CHANNEL_PACKED`’, ‘NONE’]

channels

Count of channels held in the pixel buffer (in [0, inf], default 0, readonly)

Type :

int

colorspace_settings

Color space settings for the input (readonly)

Type :

ColorManagedInputColorspaceSettings

depth

Bit depth of the image (in [0, inf], default 0, readonly)

Type :

int

display_aspect

The display aspect ratio for this image, which has no effect on rendering (array of 2 items, in [0.1, inf], default (1.0, 1.0))

Type :

mathutils.Vector

file_format

The format to use when re-saving this file (default 'TARGA' )

Type :

Literal[Image Type All Items]

filepath

Name of the image/movie file (default “”, never None, blend relative // prefix supported)

Type :

str

filepath_raw

Name of the image/movie file, without triggering a data refresh (default “”, never None, blend relative // prefix supported)

Type :

str

frame_duration

How many frames the image lasts (1 unless it is a video/sequence) (in [0, inf], default 0, readonly)

Type :

int

generated_color

The color used to fill a generated image (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

generated_height

Height of the generated image (in [1, 65536], default 1024)

Type :

int

generated_type

Kind of generated image (default '`UV_GRID`' )

Type :

Literal[Image Generated Type Items]

generated_width

Width of the generated image (in [1, 65536], default 1024)

Type :

int

has_data

True once the image data has been read into memory (default False, readonly)

Type :

bool

is_dirty

The image carries unsaved changes (default False, readonly)

Type :

bool

is_float

True when this image lives in a floating-point buffer (default False, readonly)

Type :

bool

is_multiview

The image carries more than a single view (default False, readonly)

Type :

bool

is_stereo_3d

The image carries both a left and a right view (default False, readonly)

Type :

bool

packed_file

The image's first packed file (readonly)

Type :

PackedFile

packed_files

The set of packed images (default None, readonly)

Type :

bpy_prop_collection[ImagePackedFile]

pixels

The image buffer's pixels expressed as floating-point values (in [-inf, inf], default 0.0)

Type :

float

render_slots

The image's render slots (default None, readonly)

Type :

RenderSlots[RenderSlot]

resolution

Pixels per meter along X/Y for the image buffer (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

seam_margin

How wide a margin to allow when mending UV seams while painting. Larger values mend seams better for mipmaps at the cost of speed. (in [-32768, 32767], default 8)

Type :

int

size

The image buffer's width and height in pixels, reading zero when the image data will not load (array of 2 items, in [-inf, inf], default (0, 0), readonly)

Type :

bpy_prop_array[int]

source

The origin of the image (default 'FILE' )

- FILE
Single Image – One image file.

- SEQUENCE
Image Sequence – Several image files forming a sequence.

- MOVIE
Movie – A movie file.

- GENERATED
Generated – An image created procedurally.

- VIEWER
Viewer – A compositing node viewer.

- TILED
UDIM Tiles – A tiled UDIM image texture.

Type :

Literal[‘FILE’, ‘SEQUENCE’, ‘MOVIE’, ‘GENERATED’, ‘VIEWER’, ‘TILED’]

stereo_3d_format

Stereo 3D settings (readonly, never None)

Type :

Stereo3dFormat

tiles

The image's tiles (default None, readonly)

Type :

UDIMTiles[UDIMTile]

type

The method used to produce the image (default 'IMAGE' , readonly)

Type :

Literal[‘IMAGE’, ‘MULTILAYER’, ‘`UV_TEST`’, ‘`RENDER_RESULT`’, ‘COMPOSITING’]

use_deinterlace

Deinterlace the movie file as it loads (default False)

Type :

bool

use_generated_float

Produce a floating-point buffer (default False)

Type :

bool

use_half_precision

Drop to 16 bits per channel to cut memory use while rendering (default True)

Type :

bool

use_multiview

Use Multiple Views (when available) (default False)

Type :

bool

use_view_as_render

When showing this image on screen, apply the render part of the display transform (default False)

Type :

bool

views_format

How to load the image's views (default 'INDIVIDUAL' )

Type :

Literal[Views Format Items]

save_render ( filepath , * , scene = None , quality = 0 )

Write the image to a chosen path with a scene's render settings.

Parameters :

- filepath ( str ) – Output path (never None)

- scene (Scene) – Scene to take image parameters from (optional)

- quality ( int ) – Quality, Quality for image formats that support lossy compression, uses default quality if not specified (in [0, 100], optional)

save ( * , filepath = '' , quality = 0 , save_copy = False )

Write the image.

Parameters :

- filepath ( str ) – Output path, uses image data-block filepath if not specified (optional, never None)

- quality ( int ) – Quality, Quality for image formats that support lossy compression, uses default quality if not specified (in [0, 100], optional)

- save_copy ( bool ) – Save Copy, Save the image as a copy, without updating current image’s filepath (optional)

pack ( * , data = b'' , data_len = 0 )

Embed an image as packed data inside the .blend file.

Parameters :

- data ( bytes ) – data, Raw data (bytes, exact content of the embedded file) (optional, never None)

- data_len ( int ) – data_len, length of given data (mandatory if data is provided) (in [0, inf], optional)

unpack ( * , method = '`USE_LOCAL`' )

Write an image packed in the .blend file back out to disk.

Parameters :

method (Literal[Unpack Method Items]) – method, How to unpack (optional)

reload ( )

Re-read the image from where it is sourced.

update ( )

Refresh the display image using the floating-point buffer.

scale ( width , height , * , frame = 0 , tile_index = 0 )

Resize the image's buffer, measured in pixels.

Parameters :

- width ( int ) – Width (in [1, inf])

- height ( int ) – Height (in [1, inf])

- frame ( int ) – Frame, Frame (for image sequences) (in [0, inf], optional)

- tile_index ( int ) – Tile, Tile index (for tiled images) (in [0, inf], optional)

gl_touch ( * , frame = 0 , layer_index = 0 , pass_index = 0 )

Hold off purging the image from the cache for being idle.

Parameters :

- frame ( int ) – Frame, Frame of image sequence or movie (in [0, inf], optional)

- layer_index ( int ) – Layer, Index of layer that should be loaded (in [0, inf], optional)

- pass_index ( int ) – Pass, Index of pass that should be loaded (in [0, inf], optional)

Returns :

Error, OpenGL error value (in [-inf, inf])

Return type :

int

gl_load ( * , frame = 0 , layer_index = 0 , pass_index = 0 )

Bring the image into an OpenGL texture. When it works, image.bindcode holds the OpenGL texture bindcode. Texture reads come back in scene-linear color space with premultiplied or straight alpha to match the image's alpha mode.

Parameters :

- frame ( int ) – Frame, Frame of image sequence or movie (in [0, inf], optional)

- layer_index ( int ) – Layer, Index of layer that should be loaded (in [0, inf], optional)

- pass_index ( int ) – Pass, Index of pass that should be loaded (in [0, inf], optional)

Returns :

Error, OpenGL error value (in [-inf, inf])

Return type :

int

gl_free ( )

Release the image from OpenGL graphics memory.

filepath_from_user ( * , image_user = None )

Give back the absolute path for the image frame that the image user points at.

Parameters :

image_user (ImageUser) – Image user of the image to get filepath for (optional)

Returns :

File Path, The resulting filepath from the image and its user (never None)

Return type :

str

buffers_free ( )

Release the image buffers from memory.

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

| bpy.context.edit_image BlendData.images BlendDataImages.load BlendDataImages.new BlendDataImages.remove CameraBackgroundImage.image CompositorNodeCryptomatteV2.image CompositorNodeImage.image GeometryNodeInputImage.image ImagePaint.canvas ImagePaint.clone_image ImagePaint.stencil_image ImageTexture.image | Material.texture_paint_images MaterialGPencilStyle.fill_image MaterialGPencilStyle.stroke_image MovieTrackingPlaneTrack.image NodeSocketImage.default_value NodeTreeInterfaceSocketImage.default_value PaintModeSettings.canvas_image ShaderNodeTexEnvironment.image ShaderNodeTexImage.image SpaceImageEditor.image TextureNodeImage.image UILayout.template_image_layers |

## `IMAGE_AST`_brush_paint(AssetShelf)

### `IMAGE_AST`_brush_paint(AssetShelf)

base classes — bpy_struct, AssetShelf

class bpy.types. `IMAGE_AST`_brush_paint ( AssetShelf )

classmethod brush_type_poll ( context , asset )

static draw_popup_selector ( layout , context , brush , show_name = True )

static get_shelf_name_from_context ( context )

classmethod has_tool_with_brush_type ( context , brush_type )

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

| bpy_struct.id_data AssetShelf.bl_idname AssetShelf.bl_space_type AssetShelf.bl_options AssetShelf.bl_activate_operator AssetShelf.bl_drag_operator AssetShelf.bl_default_preview_size AssetShelf.filter_action AssetShelf.filter_armature AssetShelf.filter_brush AssetShelf.filter_camera AssetShelf.filter_cachefile AssetShelf.filter_curve AssetShelf.filter_annotations AssetShelf.filter_grease_pencil AssetShelf.filter_group AssetShelf.filter_curves AssetShelf.filter_image AssetShelf.filter_light AssetShelf.filter_light_probe AssetShelf.filter_linestyle AssetShelf.filter_lattice AssetShelf.filter_material | AssetShelf.filter_metaball AssetShelf.filter_movie_clip AssetShelf.filter_mesh AssetShelf.filter_mask AssetShelf.filter_node_tree AssetShelf.filter_object AssetShelf.filter_particle_settings AssetShelf.filter_palette AssetShelf.filter_paint_curve AssetShelf.filter_pointcloud AssetShelf.filter_scene AssetShelf.filter_speaker AssetShelf.filter_sound AssetShelf.filter_texture AssetShelf.filter_text AssetShelf.filter_font AssetShelf.filter_volume AssetShelf.filter_world AssetShelf.filter_work_space AssetShelf.asset_library_reference AssetShelf.show_names AssetShelf.preview_size AssetShelf.search_filter |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys | bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values AssetShelf.poll AssetShelf.asset_poll AssetShelf.get_active_asset AssetShelf.draw_context_menu AssetShelf.bl_rna_get_subclass AssetShelf.bl_rna_get_subclass_py |

## `IMAGE_FH`_drop_handler(FileHandler)

### `IMAGE_FH`_drop_handler(FileHandler)

base classes — bpy_struct, FileHandler

class bpy.types. `IMAGE_FH`_drop_handler ( FileHandler )

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

| bpy_struct.id_data FileHandler.bl_idname FileHandler.bl_import_operator | FileHandler.bl_export_operator FileHandler.bl_label FileHandler.bl_file_extensions |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FileHandler.poll_drop FileHandler.bl_rna_get_subclass FileHandler.bl_rna_get_subclass_py |

## ImageFormatSettings(bpy_struct)

### ImageFormatSettings(bpy_struct)

base class — bpy_struct

class bpy.types. ImageFormatSettings ( bpy_struct )

Settings governing image formats.

cineon_black

Reference blackpoint for log conversion (in [0, 1024], default 0)

Type :

int

cineon_gamma

Gamma for log conversion (in [0, 10], default 0.0)

Type :

float

cineon_white

Reference whitepoint for log conversion (in [0, 1024], default 0)

Type :

int

color_depth

Per-channel bit depth (default '8' )

Type :

Literal[Image Color Depth Items]

color_management

Which color management settings apply when saving the file (default '`FOLLOW_SCENE`' )

Type :

Literal[‘`FOLLOW_SCENE`’, ‘OVERRIDE’]

color_mode

Use BW to save grayscale, RGB for the red/green/blue channels, or RGBA to also include alpha (default 'RGBA' )

Type :

Literal[Image Color Mode Items]

compression

Time spent finding the best compression: 0 = none, with fast output; 100 = maximum lossless compression, with slow output (in [0, 100], default 15)

Type :

int

display_settings

Settings of the device the saved image would appear on (readonly)

Type :

ColorManagedDisplaySettings

exr_codec

OpenEXR compression codec settings (default 'NONE' )

Type :

Literal[Exr Codec Items]

file_format

Format the rendered images are saved as (default 'PNG' )

Type :

Literal[Image Type All Items]

has_linear_colorspace

The file format calls for a linear color space (default False, readonly)

Type :

bool

jpeg2k_codec

JPEG 2000 codec settings (default 'JP2' )

Type :

Literal[‘JP2’, ‘J2K’]

linear_colorspace_settings

Color space settings for the output (readonly)

Type :

ColorManagedInputColorspaceSettings

media_type

Kind of media to save (default 'IMAGE' )

Type :

Literal[‘IMAGE’, ‘`MULTI_LAYER_IMAGE`’, ‘VIDEO’]

quality

Quality level for image formats with lossy compression (in [0, 100], default 90)

Type :

int

stereo_3d_format

Stereo 3D settings (readonly, never None)

Type :

Stereo3dFormat

tiff_codec

TIFF compression mode (default 'DEFLATE' )

Type :

Literal[‘NONE’, ‘DEFLATE’, ‘LZW’, ‘PACKBITS’]

use_cineon_log

Convert into a logarithmic color space (default False)

Type :

bool

use_exr_interleave

Store views, layers and passes interleaved in the legacy way, for compatibility with apps that lack support for the more efficient multi-part OpenEXR files. (default False)

Type :

bool

use_jpeg2k_cinema_48

Use the OpenJPEG Cinema Preset (48fps) (default False)

Type :

bool

use_jpeg2k_cinema_preset

Use the OpenJPEG Cinema Preset (default False)

Type :

bool

use_jpeg2k_ycc

Store luminance-chrominance-chrominance channels rather than RGB colors (default False)

Type :

bool

use_preview

While rendering animations, write JPG preview images into the same directory (default False)

Type :

bool

view_settings

Color management settings applied to the image before it is saved (readonly)

Type :

ColorManagedViewSettings

views_format

Multiview media format (default 'INDIVIDUAL' )

Type :

Literal[Views Format Multiview Items]

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

| CompositorNodeOutputFile.format NodeCompositorFileOutputItem.format BakeSettings.image_settings | RenderSettings.image_settings UILayout.template_image_settings UILayout.template_image_views |

## ImagePackedFile(bpy_struct)

### ImagePackedFile(bpy_struct)

base class — bpy_struct

class bpy.types. ImagePackedFile ( bpy_struct )

filepath

(default “”, never None, blend relative // prefix supported)

Type :

str

packed_file

(readonly)

Type :

PackedFile

tile_number

(in [-inf, inf], default 0, readonly)

Type :

int

view

(in [-inf, inf], default 0, readonly)

Type :

int

save ( )

Write the packed file back to its filepath.

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

| Image.packed_files | |

## See also

- [Bpy Struct](bpy-struct.md)
