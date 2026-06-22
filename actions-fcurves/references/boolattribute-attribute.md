# Boolattribute Attribute, Boolattributevalue Bpy Struct, Boolproperty Property, Brightcontrastmodifier Stripmodifier ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: BoolAttribute(Attribute); BoolAttributeValue(bpy_struct); BoolProperty(Property); BrightContrastModifier(StripModifier); BrushCapabilities(bpy_struct); BrushCapabilitiesImagePaint(bpy_struct); BrushCapabilitiesSculpt(bpy_struct); BrushCapabilitiesVertexPaint(bpy_struct); BrushCapabilitiesWeightPaint(bpy_struct); BrushCurvesSculptSettings(bpy_struct); BrushTextureSlot(TextureSlot).

## BoolAttribute(Attribute)

### BoolAttribute(Attribute)

base classes — bpy_struct, Attribute

class bpy.types. BoolAttribute ( Attribute )

A geometry attribute whose values are booleans.

data

(default None, readonly)

Type :

bpy_prop_collection[BoolAttributeValue]

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

| bpy_struct.id_data Attribute.name Attribute.data_type Attribute.storage_type | Attribute.domain Attribute.is_internal Attribute.is_required |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Attribute.bl_rna_get_subclass Attribute.bl_rna_get_subclass_py |

### References

| MeshUVLoopLayer.pin_ensure | |

## BoolAttributeValue(bpy_struct)

### BoolAttributeValue(bpy_struct)

base class — bpy_struct

class bpy.types. BoolAttributeValue ( bpy_struct )

A single boolean entry held inside a geometry attribute.

value

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

| BoolAttribute.data | MeshUVLoopLayer.pin |

## BoolProperty(Property)

### BoolProperty(Property)

base classes — bpy_struct, Property

class bpy.types. BoolProperty ( Property )

The RNA definition describing a boolean property.

array_dimensions

Size along each axis of the array (array of 3 items, in [0, inf], default (0, 0, 0), readonly)

Type :

bpy_prop_array[int]

array_length

Largest size the array may reach; 0 indicates no limit (in [0, inf], default 0, readonly)

Type :

int

default

The value this number falls back to (default False, readonly)

Type :

bool

default_array

The fallback values for this array (array of 3 items, default (False, False, False), readonly)

Type :

bpy_prop_array[bool]

is_array

(default False, readonly)

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

| bpy_struct.id_data Property.name Property.identifier Property.description Property.translation_context Property.type Property.subtype Property.srna Property.unit Property.icon Property.is_readonly Property.is_animatable Property.is_overridable Property.is_required Property.is_argument_optional Property.is_never_none Property.is_hidden | Property.is_skip_save Property.is_skip_preset Property.is_output Property.is_registered Property.is_registered_optional Property.is_runtime Property.is_enum_flag Property.is_library_editable Property.is_path_output Property.is_path_supports_blend_relative Property.is_path_supports_templates Property.is_deprecated Property.deprecated_note Property.deprecated_version Property.deprecated_removal_version Property.tags |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Property.bl_rna_get_subclass Property.bl_rna_get_subclass_py |

## BrightContrastModifier(StripModifier)

### BrightContrastModifier(StripModifier)

base classes — bpy_struct, StripModifier

class bpy.types. BrightContrastModifier ( StripModifier )

Holds bright/contrast modifier settings for a sequence strip.

bright

Tweaks how bright the colors appear (in [-inf, inf], default 0.0)

Type :

float

contrast

Tweaks how far apart the brightness of neighboring pixels sits (in [-100, 100], default 0.0)

Type :

float

open_mask_input_panel

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

| bpy_struct.id_data StripModifier.name StripModifier.type StripModifier.mute StripModifier.enable StripModifier.show_expanded | StripModifier.input_mask_type StripModifier.mask_time StripModifier.input_mask_strip StripModifier.input_mask_id StripModifier.is_active |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values StripModifier.bl_rna_get_subclass StripModifier.bl_rna_get_subclass_py |

## BrushCapabilities(bpy_struct)

### BrushCapabilities(bpy_struct)

base class — bpy_struct

class bpy.types. BrushCapabilities ( bpy_struct )

Read-only flags reporting which operations are available.

has_overlay

(default False, readonly)

Type :

bool

has_random_texture_angle

(default False, readonly)

Type :

bool

has_smooth_stroke

(default False, readonly)

Type :

bool

has_spacing

(default False, readonly)

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

| Brush.brush_capabilities | |

## BrushCapabilitiesImagePaint(bpy_struct)

### BrushCapabilitiesImagePaint(bpy_struct)

base class — bpy_struct

class bpy.types. BrushCapabilitiesImagePaint ( bpy_struct )

Read-only flags reporting which image-paint operations are available.

has_accumulate

(default False, readonly)

Type :

bool

has_color

(default False, readonly)

Type :

bool

has_radius

(default False, readonly)

Type :

bool

has_space_attenuation

(default False, readonly)

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

| Brush.image_paint_capabilities | |

## BrushCapabilitiesSculpt(bpy_struct)

### BrushCapabilitiesSculpt(bpy_struct)

base class — bpy_struct

class bpy.types. BrushCapabilitiesSculpt ( bpy_struct )

Read-only flags reporting which brush operations the active sculpt tool allows.

has_accumulate

(default False, readonly)

Type :

bool

has_auto_smooth

(default False, readonly)

Type :

bool

has_auto_smooth_pressure

(default False, readonly)

Type :

bool

has_color

(default False, readonly)

Type :

bool

has_direction

(default False, readonly)

Type :

bool

has_dyntopo

(default False, readonly)

Type :

bool

has_gravity

(default False, readonly)

Type :

bool

has_hardness

(default False, readonly)

Type :

bool

has_hardness_pressure

(default False, readonly)

Type :

bool

has_height

(default False, readonly)

Type :

bool

has_jitter

(default False, readonly)

Type :

bool

has_normal_radius

(default False, readonly)

Type :

bool

has_normal_weight

(default False, readonly)

Type :

bool

has_persistence

(default False, readonly)

Type :

bool

has_pinch_factor

(default False, readonly)

Type :

bool

has_plane_depth

(default False, readonly)

Type :

bool

has_plane_height

(default False, readonly)

Type :

bool

has_plane_offset

(default False, readonly)

Type :

bool

has_rake_factor

(default False, readonly)

Type :

bool

has_random_texture_angle

(default False, readonly)

Type :

bool

has_sculpt_plane

(default False, readonly)

Type :

bool

has_secondary_color

(default False, readonly)

Type :

bool

has_size_pressure

(default False, readonly)

Type :

bool

has_smooth_stroke

(default False, readonly)

Type :

bool

has_space_attenuation

(default False, readonly)

Type :

bool

has_strength_pressure

(default False, readonly)

Type :

bool

has_tilt

(default False, readonly)

Type :

bool

has_topology_rake

(default False, readonly)

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

| Brush.sculpt_capabilities | |

## BrushCapabilitiesVertexPaint(bpy_struct)

### BrushCapabilitiesVertexPaint(bpy_struct)

base class — bpy_struct

class bpy.types. BrushCapabilitiesVertexPaint ( bpy_struct )

Read-only flags reporting which vertex-paint operations are available.

has_color

(default False, readonly)

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

| Brush.vertex_paint_capabilities | |

## BrushCapabilitiesWeightPaint(bpy_struct)

### BrushCapabilitiesWeightPaint(bpy_struct)

base class — bpy_struct

class bpy.types. BrushCapabilitiesWeightPaint ( bpy_struct )

Read-only flags reporting which weight-paint operations are available.

has_weight

(default False, readonly)

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

| Brush.weight_paint_capabilities | |

## BrushCurvesSculptSettings(bpy_struct)

### BrushCurvesSculptSettings(bpy_struct)

base class — bpy_struct

class bpy.types. BrushCurvesSculptSettings ( bpy_struct )

add_amount

How many curves the Add brush lays down (in [1, inf], default 0)

Type :

int

curve_length

Length given to freshly added curves when their length isn't interpolated from nearby ones (in [0, inf], default 0.0)

Type :

float

curve_parameter_falloff

Falloff running from each curve's tip down to its root (readonly)

Type :

CurveMapping

curve_radius

Radius given to freshly added curves when their radius isn't interpolated from nearby ones (in [0, inf], default 0.01)

Type :

float

density_add_attempts

How many tries the Density brush makes at adding a new curve (in [0, inf], default 0)

Type :

int

density_mode

Whether the brush is adding or removing curves (default 'AUTO' )

- AUTO
Auto – Adds or removes curves based on the smallest spacing among the curves beneath the cursor.

- ADD
Add – Inserts new curves between existing ones, respecting the minimum distance.

- REMOVE
Remove – Strips out curves whose roots sit too close together.

Type :

Literal['AUTO', 'ADD', 'REMOVE']

minimum_distance

Target spacing between curve roots that the Density brush aims for (in [0, inf], default 0.0)

Type :

float

minimum_length

Keep curves from shrinking below this length (in [0, inf], default 0.0)

Type :

float

points_per_curve

How many control points a newly added curve receives (in [2, inf], default 0)

Type :

int

use_length_interpolate

Borrow the length from nearby curves (default False)

Type :

bool

use_point_count_interpolate

Borrow the point count from nearby curves (default False)

Type :

bool

use_radius_interpolate

Borrow the radius from nearby curves (default True)

Type :

bool

use_shape_interpolate

Borrow the shape from nearby curves (default False)

Type :

bool

use_uniform_scale

Resize curves uniformly when growing or shrinking them, rather than trimming or extrapolating (default False)

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

| Brush.curves_sculpt_settings | |

## BrushTextureSlot(TextureSlot)

### BrushTextureSlot(TextureSlot)

base classes — bpy_struct, TextureSlot

class bpy.types. BrushTextureSlot ( TextureSlot )

Texture slot configuration for textures in a Brush data-block

angle

Brush texture orientation (in [0, 6.28319], default 0.0)

Type :

float

has_random_texture_angle

(default False, readonly)

Type :

bool

has_texture_angle

(default False, readonly)

Type :

bool

has_texture_angle_source

(default False, readonly)

Type :

bool

map_mode

(default '`VIEW_PLANE`' )

Type :

Literal['`VIEW_PLANE`', '`AREA_PLANE`', 'TILED', '3D', 'RANDOM', 'STENCIL']

mask_map_mode

(default '`VIEW_PLANE`' )

Type :

Literal['`VIEW_PLANE`', 'TILED', 'RANDOM', 'STENCIL']

random_angle

Brush texture random angle (in [0, 6.28319], default 6.28319)

Type :

float

use_rake

(default False)

Type :

bool

use_random

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

| bpy_struct.id_data TextureSlot.texture TextureSlot.name TextureSlot.offset TextureSlot.scale | TextureSlot.color TextureSlot.blend_type TextureSlot.default_value TextureSlot.output_node |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values TextureSlot.bl_rna_get_subclass TextureSlot.bl_rna_get_subclass_py |

### References

| Brush.mask_texture_slot | Brush.texture_slot |
