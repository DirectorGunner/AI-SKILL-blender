# Shadernodeteximage Shadernode, Shadernodetexmagic Shadernode, Shadernodetexnoise Shadernode, Shadernodetexsky Shadernode ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ShaderNodeTexImage(ShaderNode); ShaderNodeTexMagic(ShaderNode); ShaderNodeTexNoise(ShaderNode); ShaderNodeTexSky(ShaderNode); ShaderNodeTexVoronoi(ShaderNode).

## ShaderNodeTexImage(ShaderNode)

### ShaderNodeTexImage(ShaderNode)

base classes — bpy_struct, Node, NodeInternal, ShaderNode

class bpy.types. ShaderNodeTexImage ( ShaderNode )

Reads an image file and uses it as a texture.

color_mapping

Color mapping settings (readonly, never None)

Type :

ColorMapping

extension

How the image is extrapolated past its original bounds (default 'REPEAT' )

- REPEAT
Repeat – Cause the image to repeat horizontally and vertically.

- EXTEND
Extend – Extend by repeating edge pixels of the image.

- CLIP
Clip – Clip to image size and set exterior pixels as transparent.

- MIRROR
Mirror – Repeatedly flip the image horizontally and vertically.

Type :

Literal[‘REPEAT’, ‘EXTEND’, ‘CLIP’, ‘MIRROR’]

image

Type :

Image

image_user

Parameters defining which layer, pass and frame of the image is displayed (readonly, never None)

Type :

ImageUser

interpolation

Texture interpolation (default 'Linear' )

- Linear
Linear – Linear interpolation.

- Closest
Closest – No interpolation (sample closest texel).

- Cubic
Cubic – Cubic interpolation.

- Smart
Smart – Bicubic when magnifying, else bilinear (OSL only).

Type :

Literal[‘Linear’, ‘Closest’, ‘Cubic’, ‘Smart’]

projection

Method to project 2D image on object with a 3D texture vector (default 'FLAT' )

- FLAT
Flat – Image is projected flat using the X and Y coordinates of the texture vector.

- BOX
Box – Image is projected using different components for each side of the object space bounding box.

- SPHERE
Sphere – Image is projected spherically using the Z axis as central.

- TUBE
Tube – Image is projected from the tube using the Z axis as central.

Type :

Literal[‘FLAT’, ‘BOX’, ‘SPHERE’, ‘TUBE’]

projection_blend

For box projection, amount of blend to use between sides (in [0, 1], default 0.0)

Type :

float

texture_mapping

Texture coordinate mapping settings (readonly, never None)

Type :

TexMapping

classmethod is_registered_node_type ( )

True if a registered node type

Returns :

Result

Return type :

bool

classmethod input_template ( index )

Input socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index )

Output socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

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

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py ShaderNode.poll ShaderNode.bl_rna_get_subclass ShaderNode.bl_rna_get_subclass_py |

## ShaderNodeTexMagic(ShaderNode)

### ShaderNodeTexMagic(ShaderNode)

base classes — bpy_struct, Node, NodeInternal, ShaderNode

class bpy.types. ShaderNodeTexMagic ( ShaderNode )

Builds a swirling, psychedelic color texture.

color_mapping

Color mapping settings (readonly, never None)

Type :

ColorMapping

texture_mapping

Texture coordinate mapping settings (readonly, never None)

Type :

TexMapping

turbulence_depth

Sets how much fine detail the added turbulent noise carries (in [0, 10], default 0)

Type :

int

classmethod is_registered_node_type ( )

True if a registered node type

Returns :

Result

Return type :

bool

classmethod input_template ( index )

Input socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index )

Output socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

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

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py ShaderNode.poll ShaderNode.bl_rna_get_subclass ShaderNode.bl_rna_get_subclass_py |

## ShaderNodeTexNoise(ShaderNode)

### ShaderNodeTexNoise(ShaderNode)

base classes — bpy_struct, Node, NodeInternal, ShaderNode

class bpy.types. ShaderNodeTexNoise ( ShaderNode )

Builds fractal Perlin noise.

color_mapping

Color mapping settings (readonly, never None)

Type :

ColorMapping

noise_dimensions

Number of dimensions to output noise for (default '1D' )

- 1D
1D – Use the scalar value W as input.

- 2D
2D – Use the 2D vector (X, Y) as input. The Z component is ignored..

- 3D
3D – Use the 3D vector (X, Y, Z) as input.

- 4D
4D – Use the 4D vector (X, Y, Z, W) as input.

Type :

Literal[‘1D’, ‘2D’, ‘3D’, ‘4D’]

noise_type

Type of the Noise texture (default 'MULTIFRACTAL' )

- MULTIFRACTAL
Multifractal – More uneven result (varies with location), more similar to a real terrain.

- `RIDGED_MULTIFRACTAL`
Ridged Multifractal – Create sharp peaks.

- `HYBRID_MULTIFRACTAL`
Hybrid Multifractal – Create peaks and valleys with different roughness values.

- FBM
fBM – The standard fractal Perlin noise.

- `HETERO_TERRAIN`
Hetero Terrain – Similar to Hybrid Multifractal creates a heterogeneous terrain, but with the likeness of river channels.

Type :

Literal[‘MULTIFRACTAL’, ‘`RIDGED_MULTIFRACTAL`’, ‘`HYBRID_MULTIFRACTAL`’, ‘FBM’, ‘`HETERO_TERRAIN`’]

normalize

Normalize outputs to 0.0 to 1.0 range (default False)

Type :

bool

texture_mapping

Texture coordinate mapping settings (readonly, never None)

Type :

TexMapping

classmethod is_registered_node_type ( )

True if a registered node type

Returns :

Result

Return type :

bool

classmethod input_template ( index )

Input socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index )

Output socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

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

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py ShaderNode.poll ShaderNode.bl_rna_get_subclass ShaderNode.bl_rna_get_subclass_py |

## ShaderNodeTexSky(ShaderNode)

### ShaderNodeTexSky(ShaderNode)

base classes — bpy_struct, Node, NodeInternal, ShaderNode

class bpy.types. ShaderNodeTexSky ( ShaderNode )

Builds a procedural sky texture.

aerosol_density

Density of dust, pollution and water droplets.
0 means no aerosols, 1 means urban city aerosols

(in [0, 1000], default 1.0)

Type :

float

air_density

Density of air molecules.
0 means no air, 1 means urban city air

(in [0, 1000], default 1.0)

Type :

float

altitude

Height from sea level (in [0, 100000], default 100.0)

Type :

float

color_mapping

Color mapping settings (readonly, never None)

Type :

ColorMapping

ground_albedo

Ground color that is subtly reflected in the sky (in [0, 1], default 0.0)

Type :

float

ozone_density

Density of ozone layer.
0 means no ozone, 1 means urban city ozone

(in [0, 1000], default 1.0)

Type :

float

sky_type

Which sky model should be used (default 'PREETHAM' )

- `SINGLE_SCATTERING`
Single Scattering – Single scattering sky model.

- `MULTIPLE_SCATTERING`
Multiple Scattering – Multiple scattering sky model (more accurate).

- PREETHAM
Preetham – Preetham 1999 (Legacy).

- `HOSEK_WILKIE`
Hosek / Wilkie – Hosek / Wilkie 2012 (Legacy).

Type :

Literal[‘`SINGLE_SCATTERING`’, ‘`MULTIPLE_SCATTERING`’, ‘PREETHAM’, ‘`HOSEK_WILKIE`’]

sun_direction

Direction from where the sun is shining (array of 3 items, in [-inf, inf], default (0.0, 0.0, 1.0))

Type :

mathutils.Vector

sun_disc

Include the sun itself in the output (default True)

Type :

bool

sun_elevation

Sun angle from horizon (in [-inf, inf], default 0.261799)

Type :

float

sun_intensity

Strength of Sun (in [0, 1000], default 1.0)

Type :

float

sun_rotation

Rotation of sun around zenith (in [-inf, inf], default 0.0)

Type :

float

sun_size

Size of sun disc (in [0, 1.5708], default 0.00951204)

Type :

float

texture_mapping

Texture coordinate mapping settings (readonly, never None)

Type :

TexMapping

turbidity

Atmospheric turbidity (in [1, 10], default 0.0)

Type :

float

classmethod is_registered_node_type ( )

True if a registered node type

Returns :

Result

Return type :

bool

classmethod input_template ( index )

Input socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index )

Output socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

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

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py ShaderNode.poll ShaderNode.bl_rna_get_subclass ShaderNode.bl_rna_get_subclass_py |

## ShaderNodeTexVoronoi(ShaderNode)

### ShaderNodeTexVoronoi(ShaderNode)

base classes — bpy_struct, Node, NodeInternal, ShaderNode

class bpy.types. ShaderNodeTexVoronoi ( ShaderNode )

Produces Worley noise from the distance to scattered random points — a common way to make stone, water, or organic cell patterns.

color_mapping

Color mapping settings (readonly, never None)

Type :

ColorMapping

distance

The distance metric used to compute the texture (default 'EUCLIDEAN' )

- EUCLIDEAN
Euclidean – Euclidean distance.

- MANHATTAN
Manhattan – Manhattan distance.

- CHEBYCHEV
Chebychev – Chebychev distance.

- MINKOWSKI
Minkowski – Minkowski distance.

Type :

Literal[‘EUCLIDEAN’, ‘MANHATTAN’, ‘CHEBYCHEV’, ‘MINKOWSKI’]

feature

The Voronoi feature that the node will compute (default 'F1' )

- F1
F1 – Computes the distance to the closest point as well as its position and color.

- F2
F2 – Computes the distance to the second closest point as well as its position and color.

- `SMOOTH_F1`
Smooth F1 – Smoothed version of F1. Weighted sum of neighbor voronoi cells..

- `DISTANCE_TO_EDGE`
Distance to Edge – Computes the distance to the edge of the voronoi cell.

- `N_SPHERE_RADIUS`
N-Sphere Radius – Computes the radius of the n-sphere inscribed in the voronoi cell.

Type :

Literal[‘F1’, ‘F2’, ‘`SMOOTH_F1`’, ‘`DISTANCE_TO_EDGE`’, ‘`N_SPHERE_RADIUS`’]

normalize

Normalize output Distance to 0.0 to 1.0 range (default False)

Type :

bool

texture_mapping

Texture coordinate mapping settings (readonly, never None)

Type :

TexMapping

voronoi_dimensions

Number of dimensions to output noise for (default '1D' )

- 1D
1D – Use the scalar value W as input.

- 2D
2D – Use the 2D vector (X, Y) as input. The Z component is ignored..

- 3D
3D – Use the 3D vector (X, Y, Z) as input.

- 4D
4D – Use the 4D vector (X, Y, Z, W) as input.

Type :

Literal[‘1D’, ‘2D’, ‘3D’, ‘4D’]

classmethod is_registered_node_type ( )

True if a registered node type

Returns :

Result

Return type :

bool

classmethod input_template ( index )

Input socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index )

Output socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

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

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py ShaderNode.poll ShaderNode.bl_rna_get_subclass ShaderNode.bl_rna_get_subclass_py |
