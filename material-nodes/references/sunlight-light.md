# Sunlight Light, Surfacecurve Curve, Texmapping Bpy Struct, Texpaintslot Bpy Struct ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: SunLight(Light); SurfaceCurve(Curve); TexMapping(bpy_struct); TexPaintSlot(bpy_struct); Text(ID); TextCharacterFormat(bpy_struct).

## SunLight(Light)

### SunLight(Light)

base classes — bpy_struct, ID, Light

class bpy.types. SunLight ( Light )

A light emitting parallel rays in a fixed direction.

angle

Angular diameter of the Sun as seen from the Earth (in [0, 3.14159], default 0.00918043)

Type :

float

energy

Sunlight strength in watts per meter squared (W/m²) (in [-inf, inf], default 10.0)

Type :

float

shadow_buffer_clip_start

Near plane of the shadow map; anything closer than this casts no shadow (in [1e-06, inf], default 0.05)

Type :

float

shadow_cascade_count

Number of texture used by the cascaded shadow map (in [1, 4], default 4)

Type :

int

shadow_cascade_exponent

Higher value increase resolution towards the viewpoint (in [0, 1], default 0.8)

Type :

float

shadow_cascade_fade

How smooth is the transition between each cascade (in [0, 1], default 0.1)

Type :

float

shadow_cascade_max_distance

End distance of the cascaded shadow map (only in perspective view) (in [0, inf], default 200.0)

Type :

float

shadow_filter_radius

Blur shadow aliasing using Percentage Closer Filtering (in [0, inf], default 1.0)

Type :

float

shadow_jitter_overblur

Trace shadows per jittered sample so under-sampling artifacts are reduced (in [0, 100], default 10.0)

Type :

float

shadow_maximum_resolution

Smallest a shadow map pixel may get; raising it trades shadow quality for lower memory use. (in [0, inf], default 0.001)

Type :

float

shadow_soft_size

Light size for ray shadow sampling (Raytraced shadows) (in [0, inf], default 0.0)

Type :

float

use_shadow_jitter

Turn on jittered soft shadows for finer shadow precision; off in the viewport unless switched on in render settings, and costly to performance. (default False)

Type :

bool

inline_shader_nodes ( )

Get the inlined shader nodes of this light. This preprocesses the node tree
to remove nested groups, repeat zones and more.

Returns :

The inlined shader nodes.

Return type :

bpy.types.InlineShaderNodes

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data | ID.override_library ID.preview Light.type Light.use_temperature Light.color Light.temperature Light.temperature_color Light.specular_factor Light.diffuse_factor Light.transmission_factor Light.volume_factor Light.use_custom_distance Light.cutoff_distance Light.use_shadow Light.exposure Light.normalize Light.node_tree Light.use_nodes Light.animation_data Light.cycles |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values | ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py Light.area Light.inline_shader_nodes Light.bl_rna_get_subclass Light.bl_rna_get_subclass_py |

## SurfaceCurve(Curve)

### SurfaceCurve(Curve)

base classes — bpy_struct, ID, Curve

class bpy.types. SurfaceCurve ( Curve )

A curve data-block that holds surface data.

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview Curve.shape_keys Curve.splines Curve.path_duration Curve.use_path Curve.use_path_follow Curve.use_path_clamp Curve.use_stretch Curve.use_deform_bounds Curve.use_radius Curve.bevel_mode | Curve.bevel_profile Curve.bevel_resolution Curve.offset Curve.extrude Curve.bevel_depth Curve.resolution_u Curve.resolution_v Curve.render_resolution_u Curve.render_resolution_v Curve.eval_time Curve.bevel_object Curve.taper_object Curve.dimensions Curve.fill_mode Curve.fill_solver Curve.fill_rule Curve.twist_mode Curve.taper_radius_mode Curve.bevel_factor_mapping_start Curve.bevel_factor_mapping_end Curve.twist_smooth Curve.use_fill_caps Curve.use_map_taper Curve.use_auto_texspace Curve.texspace_location Curve.texspace_size Curve.materials Curve.bevel_factor_start Curve.bevel_factor_end Curve.is_editmode Curve.animation_data Curve.cycles |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values | ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py Curve.transform Curve.validate_material_indices Curve.update_gpu_tag Curve.bl_rna_get_subclass Curve.bl_rna_get_subclass_py |

## TexMapping(bpy_struct)

### TexMapping(bpy_struct)

base class — bpy_struct

class bpy.types. TexMapping ( bpy_struct )

Settings that govern how texture coordinates are mapped.

mapping

(default 'FLAT' )

- FLAT
Flat – Map X and Y coordinates directly.

- CUBE
Cube – Map using the normal vector.

- TUBE
Tube – Map with Z as central axis.

- SPHERE
Sphere – Map with Z as central axis.

Type :

Literal[‘FLAT’, ‘CUBE’, ‘TUBE’, ‘SPHERE’]

mapping_x

(default 'NONE' )

Type :

Literal[‘NONE’, ‘X’, ‘Y’, ‘Z’]

mapping_y

(default 'NONE' )

Type :

Literal[‘NONE’, ‘X’, ‘Y’, ‘Z’]

mapping_z

(default 'NONE' )

Type :

Literal[‘NONE’, ‘X’, ‘Y’, ‘Z’]

max

Maximum value for clipping (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

min

Minimum value for clipping (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

rotation

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Euler

scale

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

translation

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

use_max

Whether to use maximum clipping value (default False)

Type :

bool

use_min

Whether to use minimum clipping value (default False)

Type :

bool

vector_type

Type of vector that the mapping transforms (default 'POINT' )

Type :

Literal[Mapping Type Items]

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

| ShaderNodeTexBrick.texture_mapping ShaderNodeTexChecker.texture_mapping ShaderNodeTexEnvironment.texture_mapping ShaderNodeTexGabor.texture_mapping ShaderNodeTexGradient.texture_mapping ShaderNodeTexImage.texture_mapping | ShaderNodeTexMagic.texture_mapping ShaderNodeTexNoise.texture_mapping ShaderNodeTexSky.texture_mapping ShaderNodeTexVoronoi.texture_mapping ShaderNodeTexWave.texture_mapping |

## TexPaintSlot(bpy_struct)

### TexPaintSlot(bpy_struct)

base class — bpy_struct

class bpy.types. TexPaintSlot ( bpy_struct )

A slot holding details for texture painting.

icon_value

Paint slot icon (in [-inf, inf], default 0, readonly)

Type :

int

is_valid

Slot has a valid image and UV map (default False, readonly)

Type :

bool

name

Name of the slot (default “”, readonly, never None)

Type :

str

uv_layer

Name of UV map (default “”, never None)

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Material.texture_paint_slots | |

## Text(ID)

### Text(ID)

base classes — bpy_struct, ID

class bpy.types. Text ( ID )

A data-block that points to an external or packed text file.

current_character

Position of the caret’s character on the active line, doubling as the selection’s starting character when a selection is present (in [0, inf], default 0)

Type :

int

current_line

Current line, and start line of selection if one exists (readonly, never None)

Type :

TextLine

current_line_index

Index of current TextLine in TextLine collection (in [-inf, inf], default 0)

Type :

int

filepath

Filename of the text file (default “”, never None)

Type :

str

indentation

Use tabs or spaces for indentation (default 'TABS' )

- TABS
Tabs – Indent using tabs.

- SPACES
Spaces – Indent using spaces.

Type :

Literal[‘TABS’, ‘SPACES’]

is_dirty

Text file has been edited since last save (default False, readonly)

Type :

bool

is_in_memory

Text file is in memory, without a corresponding file on disk (default False, readonly)

Type :

bool

is_modified

Text file on disk is different than the one in memory (default False, readonly)

Type :

bool

lines

Lines of text (default None, readonly)

Type :

bpy_prop_collection[TextLine]

select_end_character

Position one character past the selection’s end, on the line where the selection finishes (in [0, inf], default 0)

Type :

int

select_end_line

End line of selection (readonly, never None)

Type :

TextLine

select_end_line_index

Index of last TextLine in selection (in [-inf, inf], default 0)

Type :

int

use_module

Run this text as a Python script on loading (default False)

Type :

bool

clear ( )

clear the text block

write ( text )

write text at the cursor location and advance to the end of the text block

Parameters :

text ( str ) – New text for this data-block (never None)

from_string ( text )

Replace text with this string.

Parameters :

text ( str ) – (never None)

as_string ( )

Return the text as a string

Returns :

(never None)

Return type :

str

is_syntax_highlight_supported ( )

Returns True if the editor supports syntax highlighting for the current text data-block

Return type :

bool

select_set ( line_start , char_start , line_end , char_end )

Set selection range by line and character index

Parameters :

- line_start ( int ) – Start Line, (in [-inf, inf])

- char_start ( int ) – Start Character, (in [-inf, inf])

- line_end ( int ) – End Line, (in [-inf, inf])

- char_end ( int ) – End Character, (in [-inf, inf])

cursor_set ( line , * , character = 0 , select = False )

Set cursor by line and (optionally) character index

Parameters :

- line ( int ) – Line, (in [0, inf])

- character ( int ) – Character, (in [0, inf], optional)

- select ( bool ) – Select when moving the cursor (optional)

as_module ( )

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

region_as_string ( * , range = None )

Parameters :

range ( tuple [ tuple [ int , int ] , tuple [ int , int ] ] | None ) – The region of text to be returned, defaulting to the selection when no range is passed.
Each int pair represents a line and column: ((start_line, start_column), (end_line, end_column))
The values match Python’s slicing logic (negative values count backwards from the end, the end value is not inclusive).

Returns :

The specified region as a string.

Return type :

str

region_from_string ( body , / , * , range = None )

Parameters :

- body ( str ) – The text to be inserted.

- range ( tuple [ tuple [ int , int ] , tuple [ int , int ] ] | None ) – The region of text to be returned, defaulting to the selection when no range is passed.
Each int pair represents a line and column: ((start_line, start_column), (end_line, end_column))
The values match Python’s slicing logic (negative values count backwards from the end, the end value is not inclusive).

### Inherited Properties

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| bpy.context.edit_text BlendData.texts BlendDataTexts.load BlendDataTexts.new BlendDataTexts.remove Camera.custom_shader FreestyleModuleSettings.script | NodeFrame.text NodeSocketText.default_value NodeTreeInterfaceSocketText.default_value ShaderNodeScript.script ShaderNodeTexIES.ies SpaceTextEditor.text |

## TextCharacterFormat(bpy_struct)

### TextCharacterFormat(bpy_struct)

base class — bpy_struct

class bpy.types. TextCharacterFormat ( bpy_struct )

Per-character formatting settings for text.

kerning

Spacing between characters (in [-inf, inf], default 0.0)

Type :

float

material_index

Material slot index of this character (in [0, inf], default 0)

Type :

int

use_bold

(default False)

Type :

bool

use_italic

(default False)

Type :

bool

use_small_caps

(default False)

Type :

bool

use_underline

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

| TextCurve.body_format | TextCurve.edit_format |

## See also

- [Bpy Struct](bpy-struct.md)
