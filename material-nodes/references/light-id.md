# Light Id, Linestylealphamodifier Material Linestylealphamodifier, Linestylecolormodifier Material Linestylecolormodifier, Linestylethicknessmodifier Material Linestylethicknessmodifier ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Light(ID); LineStyleAlphaModifier_Material(LineStyleAlphaModifier); LineStyleColorModifier_Material(LineStyleColorModifier); LineStyleThicknessModifier_Material(LineStyleThicknessModifier); MagicTexture(Texture); MarbleTexture(Texture).

## Light(ID)

### Light(ID) 

base classes — bpy_struct, ID

subclasses —
AreaLight, PointLight, SpotLight, SunLight

class bpy.types. Light ( ID ) 

Light data-block for lighting a scene

animation_data 

Animation data for this data-block (readonly)

Type :

AnimData

color 

Light color (array of 3 items, in [0, inf], default (1.0, 1.0, 1.0))

Type :

mathutils.Color

cutoff_distance 

Beyond this distance the light contributes nothing (in [0, inf], default 40.0)

Type :

float

cycles 

Cycles light settings (readonly)

Type :

CyclesLightSettings

diffuse_factor 

Diffuse reflection multiplier (in [0, inf], default 1.0)

Type :

float

exposure 

Raises the light's power exponentially, scaling the intensity by 2^exposure (in [-32, 32], default 0.0)

Type :

float

node_tree 

Node tree for node based lights (readonly)

Type :

NodeTree

normalize 

Divide intensity by the light's area so total output stays the same whatever its size and shape (default True)

Type :

bool

specular_factor 

Specular reflection multiplier (in [0, inf], default 1.0)

Type :

float

temperature 

Light color temperature in Kelvin (in [800, 20000], default 6500.0)

Type :

float

temperature_color 

Color from Temperature (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Color

transmission_factor 

Transmission light multiplier (in [0, inf], default 1.0)

Type :

float

type 

Type of light (default 'POINT' )

Type :

Literal[Light Type Items]

use_custom_distance 

Apply a per-light attenuation distance rather than the global light threshold (default False)

Type :

bool

use_nodes 

Use shader nodes to render the light (default False)

Deprecated since version 5.10: removal planned in version 6.0

Retained only for backward compatibility and otherwise unused. Writing to it does nothing, and reading it yields True every time.

Type :

bool

use_shadow 

(default True)

Type :

bool

use_temperature 

Derive a natural light color from a blackbody temperature (default False)

Type :

bool

volume_factor 

Volume light multiplier (in [0, inf], default 1.0)

Type :

float

area ( * , matrix_world = ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)) ) 

Work out the light's area from its type and shape. With the normalize option on, the light's intensity is divided by this area

Parameters :

matrix_world (mathutils.Matrix) – Object to world space transformation matrix (multi-dimensional array of 4 * 4 items, in [-inf, inf], optional)

Returns :

area, (in [-inf, inf])

Return type :

float

inline_shader_nodes ( ) 

Return this light's inlined shader nodes. The node tree is first flattened, expanding nested groups, repeat zones, and so on.

Returns :

The inlined shader nodes.

Return type :

bpy.types.InlineShaderNodes

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References 

| bpy.context.light BlendData.lights | BlendDataLights.new BlendDataLights.remove |

## LineStyleAlphaModifier_Material(LineStyleAlphaModifier)

### LineStyleAlphaModifier_Material(LineStyleAlphaModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleAlphaModifier

class bpy.types. LineStyleAlphaModifier_Material ( LineStyleAlphaModifier ) 

Adjusts alpha transparency from a chosen material attribute

blend 

How this modifier's output is combined with the underlying base value (default 'MIX' )

Type :

Literal[‘MIX’, ‘ADD’, ‘SUBTRACT’, ‘MULTIPLY’, ‘DIVIDE’, ‘DIFFERENCE’, ‘MINIMUM’, ‘MAXIMUM’]

curve 

The curve that drives the curve-based mapping (readonly)

Type :

CurveMapping

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

influence 

How strongly this modifier shifts the affected property, weighting its contribution (in [0, 1], default 0.0)

Type :

float

invert 

Flip the direction in which the linear mapping fades out (default False)

Type :

bool

mapping 

Choose which mapping kind applies (default 'LINEAR' )

- LINEAR
Linear – Use linear mapping.

- CURVE
Curve – Use curve mapping.

Type :

Literal[‘LINEAR’, ‘CURVE’]

material_attribute 

Pick which attribute of the material drives the result (default 'LINE' )

Type :

Literal[‘LINE’, ‘`LINE_R`’, ‘`LINE_G`’, ‘`LINE_B`’, ‘`LINE_A`’, ‘DIFF’, ‘`DIFF_R`’, ‘`DIFF_G`’, ‘`DIFF_B`’, ‘SPEC’, ‘`SPEC_R`’, ‘`SPEC_G`’, ‘`SPEC_B`’, ‘`SPEC_HARD`’, ‘ALPHA’]

type 

Which kind of modifier this is (default '`ALONG_STROKE`' , readonly)

Type :

Literal[Linestyle Alpha Modifier Type Items]

use 

Turn this modifier on or off while the stroke is being rendered (default False)

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

- default (type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data | LineStyleAlphaModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleAlphaModifier.bl_rna_get_subclass LineStyleAlphaModifier.bl_rna_get_subclass_py |

## LineStyleColorModifier_Material(LineStyleColorModifier)

### LineStyleColorModifier_Material(LineStyleColorModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleColorModifier

class bpy.types. LineStyleColorModifier_Material ( LineStyleColorModifier ) 

Varies line color from a chosen material attribute

blend 

How this modifier's output is combined with the underlying base value (default 'MIX' )

Type :

Literal[Ramp Blend Items]

color_ramp 

The color ramp that remaps the line color (readonly)

Type :

ColorRamp

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

influence 

How strongly this modifier shifts the affected property, weighting its contribution (in [0, 1], default 0.0)

Type :

float

material_attribute 

Pick which attribute of the material drives the result (default 'LINE' )

Type :

Literal[‘LINE’, ‘`LINE_R`’, ‘`LINE_G`’, ‘`LINE_B`’, ‘`LINE_A`’, ‘DIFF’, ‘`DIFF_R`’, ‘`DIFF_G`’, ‘`DIFF_B`’, ‘SPEC’, ‘`SPEC_R`’, ‘`SPEC_G`’, ‘`SPEC_B`’, ‘`SPEC_HARD`’, ‘ALPHA’]

type 

Which kind of modifier this is (default '`ALONG_STROKE`' , readonly)

Type :

Literal[Linestyle Color Modifier Type Items]

use 

Turn this modifier on or off while the stroke is being rendered (default False)

Type :

bool

use_ramp 

Run the BW average through a color ramp to obtain an RGB color (default False)

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

- default (type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data | LineStyleColorModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleColorModifier.bl_rna_get_subclass LineStyleColorModifier.bl_rna_get_subclass_py |

## LineStyleThicknessModifier_Material(LineStyleThicknessModifier)

### LineStyleThicknessModifier_Material(LineStyleThicknessModifier)

base classes — bpy_struct, LineStyleModifier, LineStyleThicknessModifier

class bpy.types. LineStyleThicknessModifier_Material ( LineStyleThicknessModifier )

Drives line width from a selected material attribute.

blend

Sets the way this modifier's output is combined with the underlying base value (default 'MIX' )

Type :

Literal[‘MIX’, ‘ADD’, ‘SUBTRACT’, ‘MULTIPLY’, ‘DIVIDE’, ‘DIFFERENCE’, ‘MINIMUM’, ‘MAXIMUM’]

curve

The curve that drives curve-based mapping (readonly)

Type :

CurveMapping

expanded

True when the modifier's tab is shown unfolded (default False)

Type :

bool

influence

Weight that scales how strongly the modifier alters the property (in [0, 1], default 0.0)

Type :

float

invert

Reverse the direction in which the linear mapping fades out (default False)

Type :

bool

mapping

Choose which mapping mode applies (default 'LINEAR' )

- LINEAR
Linear – Use linear mapping.

- CURVE
Curve – Use curve mapping.

Type :

Literal[‘LINEAR’, ‘CURVE’]

material_attribute

Pick which attribute of the material feeds the modifier (default 'LINE' )

Type :

Literal[‘LINE’, ‘`LINE_R`’, ‘`LINE_G`’, ‘`LINE_B`’, ‘`LINE_A`’, ‘DIFF’, ‘`DIFF_R`’, ‘`DIFF_G`’, ‘`DIFF_B`’, ‘SPEC’, ‘`SPEC_R`’, ‘`SPEC_G`’, ‘`SPEC_B`’, ‘`SPEC_HARD`’, ‘ALPHA’]

type

The modifier's kind (default '`ALONG_STROKE`' , readonly)

Type :

Literal[Linestyle Thickness Modifier Type Items]

use

Turn this modifier on or off while strokes are rendered (default False)

Type :

bool

value_max

Highest value the mapping can output (in [-inf, inf], default 0.0)

Type :

float

value_min

Lowest value the mapping can output (in [-inf, inf], default 0.0)

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

- default (type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | LineStyleThicknessModifier.name |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleThicknessModifier.bl_rna_get_subclass LineStyleThicknessModifier.bl_rna_get_subclass_py |

## MagicTexture(Texture)

### MagicTexture(Texture)

base classes — bpy_struct, ID, Texture

class bpy.types. MagicTexture ( Texture )

A procedurally generated noise texture.

noise_depth

How many iterations deep the noise runs (in [0, 30], default 2)

Type :

int

turbulence

Strength of the noise turbulence (in [0.0001, inf], default 5.0)

Type :

float

users_material

Materials that reference this texture

Type :

tuple[Material, …]

Note

Takes O(len(bpy.data.materials) * len(material.texture_slots)) time.

(readonly)

users_object_modifier

Object modifiers that reference this texture

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

## MarbleTexture(Texture)

### MarbleTexture(Texture)

base classes — bpy_struct, ID, Texture

class bpy.types. MarbleTexture ( Texture )

A procedurally generated noise texture.

marble_type

(default 'SOFT' )

- SOFT
Soft – Use soft marble.

- SHARP
Sharp – Use more clearly defined marble.

- SHARPER
Sharper – Use very clearly defined marble.

Type :

Literal[‘SOFT’, ‘SHARP’, ‘SHARPER’]

nabla

Offset distance for the derivative used when computing the normal (in [0.001, 0.1], default 0.025)

Type :

float

noise_basis

Noise basis driving the turbulence (default '`BLENDER_ORIGINAL`' )

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

noise_basis_2

(default 'SIN' )

- SIN
Sin – Use a sine wave to produce bands.

- SAW
Saw – Use a saw wave to produce bands.

- TRI
Tri – Use a triangle wave to produce bands.

Type :

Literal[‘SIN’, ‘SAW’, ‘TRI’]

noise_depth

How many iterations deep the cloud computation runs (in [0, 30], default 2)

Type :

int

noise_scale

Scale factor applied to the noise input (in [0.0001, inf], default 0.25)

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

turbulence

Strength of the band and ring noise turbulence (in [0.0001, inf], default 5.0)

Type :

float

users_material

Materials that reference this texture

Type :

tuple[Material, …]

Note

Takes O(len(bpy.data.materials) * len(material.texture_slots)) time.

(readonly)

users_object_modifier

Object modifiers that reference this texture

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
