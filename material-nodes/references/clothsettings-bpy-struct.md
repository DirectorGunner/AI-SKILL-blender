# Clothsettings Bpy Struct, Cloudstexture Texture, Colormanageddisplaysettings Bpy Struct, Colormanagedinputcolorspacesettings Bpy Struct ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ClothSettings(bpy_struct); CloudsTexture(Texture); ColorManagedDisplaySettings(bpy_struct); ColorManagedInputColorspaceSettings(bpy_struct); ColorManagedViewSettings(bpy_struct); ColorMapping(bpy_struct).

## ClothSettings(bpy_struct)

### ClothSettings(bpy_struct)

base class — bpy_struct

class bpy.types. ClothSettings ( bpy_struct )

Cloth simulation material parameters

air_damping

Air resistance (in [0, 10], default 1.0)

Type :

float

bending_damping

Damping for bending forces (in [0, 1000], default 0.5)

Type :

float

bending_model

Bending physics method (default 'ANGULAR' )

- ANGULAR
Angular – Cloth model with angular bending springs.

- LINEAR
Linear – Cloth model with linear bending springs (legacy).

Type :

Literal['ANGULAR', 'LINEAR']

bending_stiffness

Material rigidity against bending (in [0, 10000], default 0.5)

Type :

float

bending_stiffness_max

Upper limit for bending rigidity (in [0, 10000], default 0.5)

Type :

float

collider_friction

(in [0, 1], default 0.0)

Type :

float

compression_damping

Damping for compression behavior (in [0, 50], default 5.0)

Type :

float

compression_stiffness

Material rigidity against compression (in [0, 10000], default 15.0)

Type :

float

compression_stiffness_max

Upper limit for compression rigidity (in [0, 10000], default 15.0)

Type :

float

density_strength

Influence of target density (in [0, 1], default 0.0)

Type :

float

density_target

Maximum hair packing density (in [0, 10000], default 0.0)

Type :

float

effector_weights

(readonly)

Type :

EffectorWeights

fluid_density

Fluid mass per unit volume for internal pressure simulation (in [-inf, inf], default 0.0)

Type :

float

goal_default

Default pin strength without a vertex group (in [0, 1], default 0.0)

Type :

float

goal_friction

Pin sliding resistance (in [0, 50], default 0.0)

Type :

float

goal_max

Maximum pin weight value (in [0, 1], default 1.0)

Type :

float

goal_min

Minimum pin weight value (in [0, 1], default 0.0)

Type :

float

goal_spring

Pin stiffness (in [0, 0.999], default 1.0)

Type :

float

gravity

External force vector (array of 3 items, in [-100, 100], default (0.0, 0.0, -9.81))

Type :

mathutils.Vector

internal_compression_stiffness

Internal material compression strength (in [0, 10000], default 15.0)

Type :

float

internal_compression_stiffness_max

Upper limit for internal compression rigidity (in [0, 10000], default 15.0)

Type :

float

internal_friction

(in [0, 1], default 0.0)

Type :

float

internal_spring_max_diversion

Ray divergence angle from vertex normal (in [0, 0.785398], default 0.785398)

Type :

float

internal_spring_max_length

Maximum span of internal springs (0 = unlimited) (in [0, 1000], default 0.0)

Type :

float

internal_spring_normal_check

Require opposite normals for spring connectivity (default True)

Type :

bool

internal_tension_stiffness

Internal material stretching strength (in [0, 10000], default 15.0)

Type :

float

internal_tension_stiffness_max

Upper limit for internal tension rigidity (in [0, 10000], default 15.0)

Type :

float

mass

Weight per vertex (in [0, inf], default 0.3)

Type :

float

pin_stiffness

Pin spring constant (in [0, 50], default 1.0)

Type :

float

pressure_factor

Base pressure that balances internal/external forces (in [0, 10000], default 1.0)

Type :

float

quality

Substeps per frame (higher = better) (in [1, inf], default 5)

Type :

int

rest_shape_key

Shape key for rest length calculation

Type :

ShapeKey

sewing_force_max

Upper limit for stitching (in [0, 10000], default 0.0)

Type :

float

shear_damping

Damping for shearing behavior (in [0, 50], default 5.0)

Type :

float

shear_stiffness

Material rigidity against shearing (in [0, 10000], default 5.0)

Type :

float

shear_stiffness_max

Upper limit for shear scaling (in [0, 10000], default 5.0)

Type :

float

shrink_max

Maximum shrinkage amount (in [-inf, 1], default 0.0)

Type :

float

shrink_min

Shrinking ratio (in [-inf, 1], default 0.0)

Type :

float

target_volume

Equilibrium mesh volume for pressure (0 = no volume change effects) (in [0, 10000], default 0.0)

Type :

float

tension_damping

Damping for stretching behavior (in [0, 50], default 5.0)

Type :

float

tension_stiffness

Material rigidity against stretching (in [0, 10000], default 15.0)

Type :

float

tension_stiffness_max

Upper limit for tension rigidity (in [0, 10000], default 15.0)

Type :

float

time_scale

Simulation speed multiplier (in [0, inf], default 1.0)

Type :

float

uniform_pressure_force

Constant pressure applied to the mesh, in pressure units (can be negative) (in [-10000, 10000], default 0.0)

Type :

float

use_dynamic_mesh

Respect base mesh deformations (default False)

Type :

bool

use_internal_springs

Simulate internal volume via springs (default False)

Type :

bool

use_pressure

Simulate enclosed volume pressure (default False)

Type :

bool

use_pressure_volume

Use Target Volume as the start volume (default False)

Type :

bool

use_sewing_springs

Stitch loose edges (default False)

Type :

bool

vertex_group_bending

Vertex group for bending control (default "", never None)

Type :

str

vertex_group_intern

Vertex group for internal spring control (default "", never None)

Type :

str

vertex_group_mass

Vertex Group for pinning (default "", never None)

Type :

str

vertex_group_pressure

Vertex Group for pressure zones. Zero = no pressure, one = full pressure. Vertices with zero weight are excluded from volume (default "", never None)

Type :

str

vertex_group_shear_stiffness

Vertex group for shear control (default "", never None)

Type :

str

vertex_group_shrink

Vertex Group for shrinking (default "", never None)

Type :

str

vertex_group_structural_stiffness

Vertex group for structural control (default "", never None)

Type :

str

voxel_cell_size

Grid resolution for interaction effects (in [0.0001, 10000], default 0.1)

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

| ClothModifier.settings | |

### ClothSettings(bpy_struct)

Type :

str

vertex_group_shear_stiffness

Vertex group for shear control (default "", never None)

Type :

str

vertex_group_shrink

Vertex Group for shrinking (default "", never None)

Type :

str

vertex_group_structural_stiffness

Vertex group for structural control (default "", never None)

Type :

str

voxel_cell_size

Grid resolution for interaction effects (in [0.0001, 10000], default 0.1)

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

| ClothModifier.settings | |

## CloudsTexture(Texture)

### CloudsTexture(Texture)

base classes — bpy_struct, ID, Texture

class bpy.types. CloudsTexture ( Texture )

Noise-based procedural texture

cloud_type

Selects whether the noise output is grayscale or full color (default 'GRAYSCALE' )

Type :

Literal['GRAYSCALE', 'COLOR']

nabla

Offset distance for the derivative when computing the normal (in [0.001, 0.1], default 0.025)

Type :

float

noise_basis

Basis function driving the turbulence (default '`BLENDER_ORIGINAL`' )

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

Literal['`BLENDER_ORIGINAL`', '`ORIGINAL_PERLIN`', '`IMPROVED_PERLIN`', '`VORONOI_F1`', '`VORONOI_F2`', '`VORONOI_F3`', '`VORONOI_F4`', '`VORONOI_F2_F1`', '`VORONOI_CRACKLE`', '`CELL_NOISE`']

noise_depth

How many levels deep the cloud computation runs (in [0, 30], default 2)

Type :

int

noise_scale

Input scaling applied to the noise (in [0.0001, inf], default 0.25)

Type :

float

noise_type

(default '`SOFT_NOISE`' )

- `SOFT_NOISE`
Soft – Generate soft noise (smooth transitions).

- `HARD_NOISE`
Hard – Generate hard noise (sharp transitions).

Type :

Literal['`SOFT_NOISE`', '`HARD_NOISE`']

users_material

Materials referencing this texture

Type :

tuple[Material, …]

Note

Takes O(len(bpy.data.materials) * len(material.texture_slots)) time.

(readonly)

users_object_modifier

Object modifiers referencing this texture

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

## ColorManagedDisplaySettings(bpy_struct)

### ColorManagedDisplaySettings(bpy_struct)

base class — bpy_struct

class bpy.types. ColorManagedDisplaySettings ( bpy_struct )

Color management settings that are particular to a display device

display_device

Name of the display. When viewing, it sets the display device that gets emulated by clamping the gamut and HDR colors; for image and video output, it sets the display space used when writing. (default 'NONE' )

Type :

Literal[‘NONE’]

emulation

Determines how images in the selected display map onto the physical screen (default 'AUTO' )

- OFF
Off – Send the image straight out as OpenColorIO produced it. Generally incorrect, but usable when the system setup and real display device are known to line up with the selected display.

- AUTO
Automatic – Show images the way most other applications do, for previewing images and video before export. Best effort is made to emulate the selected display on the real display device.

Type :

Literal[‘OFF’, ‘AUTO’]

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

| CompositorNodeConvertToDisplay.display_settings ImageFormatSettings.display_settings | Scene.display_settings |

## ColorManagedInputColorspaceSettings(bpy_struct)

### ColorManagedInputColorspaceSettings(bpy_struct)

base class — bpy_struct

class bpy.types. ColorManagedInputColorspaceSettings ( bpy_struct )

Settings for the input color space

is_data

Handle the image as non-color data outside color management, as with normal or displacement maps (default False)

Type :

bool

name

The color space recorded in the image file, used to convert to and from it when the image is saved and loaded (default 'NONE' )

Type :

Literal[Color Space Convert Default Items]

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

| Image.colorspace_settings ImageStrip.colorspace_settings MovieClip.colorspace_settings | MovieStrip.colorspace_settings ImageFormatSettings.linear_colorspace_settings |

## ColorManagedViewSettings(bpy_struct)

### ColorManagedViewSettings(bpy_struct)

base class — bpy_struct

class bpy.types. ColorManagedViewSettings ( bpy_struct )

Color management settings governing how images appear on the display

curve_mapping

Curve-based color mapping run before the display transform (readonly)

Type :

CurveMapping

exposure

Exposure in stops applied ahead of the display transform, scaling by 2^exposure (in [-32, 32], default 0.0)

Type :

float

gamma

Extra gamma encoding applied after the display transform, for output needing custom gamma (in [0, 5], default 1.0)

Type :

float

is_hdr

Whether the display and view transform handle high dynamic range colors (default False, readonly)

Type :

bool

look

An extra transform run before the view transform to suit artistic preferences (default 'NONE' )

- NONE
None – Leave the image unaltered artistically.

Type :

Literal[‘NONE’]

support_emulation

Whether the display and view transform can automatically emulate a different display device using the display color spaces feature of OpenColorIO v2 configurations (default False, readonly)

Type :

bool

use_curve_mapping

Apply an RGB curve before the display transform (default False)

Type :

bool

use_white_balance

Run chromatic adaptation starting from a different white point (default False)

Type :

bool

view_transform

The view used when mapping an image into a display space (default 'NONE' )

- NONE
None – Skip any color transform on the display and fall back to the old non-color-managed display method.

Type :

Literal[‘NONE’]

white_balance_temperature

Color temperature of the white point in the scene (in [1800, 100000], default 6500.0)

Type :

float

white_balance_tint

Tint of the white point used by the scene; its default of 10 lines up with daylight (in [-500, 500], default 10.0)

Type :

float

white_balance_whitepoint

The color taken as white; temperature and tint are derived back and forth from it without manual steps (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

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

| CompositorNodeConvertToDisplay.view_settings ImageFormatSettings.view_settings | Scene.view_settings |

## ColorMapping(bpy_struct)

### ColorMapping(bpy_struct)

base class — bpy_struct

class bpy.types. ColorMapping ( bpy_struct )

Settings controlling color mapping

blend_color

The color blended into the texture's output color (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

blend_factor

(in [-inf, inf], default 0.0)

Type :

float

blend_type

Which blend mode is used against the texture's output color (default 'MIX' )

Type :

Literal[‘MIX’, ‘DARKEN’, ‘MULTIPLY’, ‘LIGHTEN’, ‘SCREEN’, ‘ADD’, ‘OVERLAY’, ‘`SOFT_LIGHT`’, ‘`LINEAR_LIGHT`’, ‘DIFFERENCE’, ‘SUBTRACT’, ‘DIVIDE’, ‘HUE’, ‘SATURATION’, ‘COLOR’, ‘VALUE’]

brightness

Tune how bright the texture is (in [0, 2], default 0.0)

Type :

float

color_ramp

(readonly)

Type :

ColorRamp

contrast

Tune the texture's contrast (in [0, 5], default 0.0)

Type :

float

saturation

Tune how saturated the texture's colors are (in [0, 2], default 0.0)

Type :

float

use_color_ramp

Switch color ramp operations on or off (default False)

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

| ShaderNodeTexBrick.color_mapping ShaderNodeTexChecker.color_mapping ShaderNodeTexEnvironment.color_mapping ShaderNodeTexGabor.color_mapping ShaderNodeTexGradient.color_mapping ShaderNodeTexImage.color_mapping | ShaderNodeTexMagic.color_mapping ShaderNodeTexNoise.color_mapping ShaderNodeTexSky.color_mapping ShaderNodeTexVoronoi.color_mapping ShaderNodeTexWave.color_mapping |

## See also

- [Bpy Struct](bpy-struct.md)
