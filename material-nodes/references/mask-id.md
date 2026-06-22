# Mask Id, Materialgpencilstyle Bpy Struct, Materiallineart Bpy Struct

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Mask(ID); MaterialGPencilStyle(bpy_struct); MaterialLineArt(bpy_struct).

## Mask(ID)

### Mask(ID)

base classes — bpy_struct, ID

class bpy.types. Mask ( ID )

A mask data-block that supplies a compositing mask.

active_layer_index

Position of the active layer within the mask's full layer list (in [-inf, inf], default 0)

Type :

int

animation_data

Animation data for this data-block (readonly)

Type :

AnimData

frame_end

Where the mask stops, as read by the sequencer (in [0, 1048574], default 0)

Type :

int

frame_start

Where the mask begins, as read by the sequencer (in [0, 1048574], default 0)

Type :

int

layers

Set of layers that make up this mask (default None, readonly)

Type :

MaskLayers[MaskLayer]

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

| bpy.context.edit_mask BlendData.masks BlendDataMasks.new BlendDataMasks.remove CompositorNodeMask.mask MaskStrip.mask NodeSocketMask.default_value | NodeTreeInterfaceSocketMask.default_value SpaceClipEditor.mask SpaceImageEditor.mask StripModifier.input_mask_id StripsMeta.new_mask StripsTopLevel.new_mask |

## MaterialGPencilStyle(bpy_struct)

### MaterialGPencilStyle(bpy_struct)

base class — bpy_struct

class bpy.types. MaterialGPencilStyle ( bpy_struct )

alignment_mode

Sets how Dots and Boxes line up with the drawing path and object rotation (default 'PATH' )

- PATH
Path – Follow stroke drawing path and object rotation.

- OBJECT
Object – Follow object rotation only.

- FIXED
Fixed – Do not follow drawing path or object rotation and keeps aligned with viewport.

Type :

Literal[‘PATH’, ‘OBJECT’, ‘FIXED’]

alignment_rotation

Extra rotation added to dots and square stroke textures. Takes effect only in texture shading mode. (in [-1.5708, 1.5708], default 0.0)

Type :

float

color

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

fill_color

Color that fills the region enclosed by each stroke (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

fill_image

Type :

Image

fill_style

Choose the style used to fill strokes (default 'SOLID' )

- SOLID
Solid – Fill area with solid color.

- GRADIENT
Gradient – Fill area with gradient color.

- TEXTURE
Texture – Fill area with image texture.

Type :

Literal[‘SOLID’, ‘GRADIENT’, ‘TEXTURE’]

flip

Swap the filling colors (default False)

Type :

bool

ghost

Draw strokes in this color when onion skins are shown (default False)

Type :

bool

gradient_type

Choose the gradient type used to fill strokes (default 'LINEAR' )

- LINEAR
Linear – Fill area with gradient color.

- RADIAL
Radial – Fill area with radial gradient.

Type :

Literal[‘LINEAR’, ‘RADIAL’]

hide

Set color Visibility (default False)

Type :

bool

is_fill_visible

True once the fill opacity is high enough to be seen (default False, readonly)

Type :

bool

is_stroke_visible

True once the stroke opacity is high enough to be seen (default False, readonly)

Type :

bool

lock

Guard the color against further edits and frame changes (default False)

Type :

bool

mix_color

Color blended into the primary fill color (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

mix_factor

Mix Factor (in [0, 1], default 0.0)

Type :

float

mix_stroke_factor

Mix Stroke Factor (in [0, 1], default 0.0)

Type :

float

mode

Choose the line style used for strokes (default 'LINE' )

- LINE
Line – Draw strokes using a continuous line.

- DOTS
Dots – Draw strokes using separated dots.

- BOX
Squares – Draw strokes using separated squares.

Type :

Literal[‘LINE’, ‘DOTS’, ‘BOX’]

pass_index

Index number for the “Color Index” pass (in [0, 32767], default 0)

Type :

int

pixel_size

Texture pixel size factor measured along the stroke (in [1, 5000], default 0.0)

Type :

float

show_fill

Show stroke fills of this material (default False)

Deprecated since version 5.10: removal planned in version 6.0

Unused but kept for compatibility with older versions of Blender.

Type :

bool

show_stroke

Show stroke lines of this material (default False)

Deprecated since version 5.10: removal planned in version 6.0

Unused but kept for compatibility with older versions of Blender.

Type :

bool

stroke_image

Type :

Image

stroke_style

Choose the style used to draw strokes (default 'SOLID' )

- SOLID
Solid – Draw strokes with solid color.

- TEXTURE
Texture – Draw strokes using texture.

Type :

Literal[‘SOLID’, ‘TEXTURE’]

texture_angle

Texture Orientation Angle (in [-inf, inf], default 0.0)

Type :

float

texture_clamp

Clamp the texture to a single instance instead of repeating it (default False)

Type :

bool

texture_offset

Shift Texture in 2d Space (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

texture_scale

Scale Factor for Texture (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

use_fill_holdout

Strip the color beneath this stroke by treating it as a mask (default False)

Type :

bool

use_overlap_strokes

Turn off stencil and let self-intersections overlap with alpha materials (default False)

Type :

bool

use_stroke_holdout

Strip the color beneath this stroke by treating it as a mask (default False)

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

| Material.grease_pencil | |

## MaterialLineArt(bpy_struct)

### MaterialLineArt(bpy_struct)

base class — bpy_struct

class bpy.types. MaterialLineArt ( bpy_struct )

intersection_priority

The intersection line is assigned to whichever object has the higher intersection priority value (in [0, 255], default 0)

Type :

int

mat_occlusion

Faces with this material act as though they carry the set number of layers for occlusion (in [0, 255], default 1)

Type :

int

use_intersection_priority_override

Override the intersection priority value of the object and collection (default False)

Type :

bool

use_material_mask

Filter occluded strokes out using material masks (default False)

Type :

bool

use_material_mask_bits

(array of 8 items, default (False, False, False, False, False, False, False, False))

Type :

bpy_prop_array[bool]

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

| Material.lineart | |

## See also

- [Bpy Struct](bpy-struct.md)
