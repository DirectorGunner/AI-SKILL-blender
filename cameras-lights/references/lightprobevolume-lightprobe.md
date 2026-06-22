# Lightprobevolume Lightprobe, Linesets Bpy Prop Collection, Linestylealphamodifier Alongstroke Linestylealphamodifier, Linestylealphamodifier Creaseangle Linestylealphamodifier ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: LightProbeVolume(LightProbe); Linesets(bpy_prop_collection); LineStyleAlphaModifier_AlongStroke(LineStyleAlphaModifier); LineStyleAlphaModifier_CreaseAngle(LineStyleAlphaModifier); LineStyleAlphaModifier_Curvature_3D(LineStyleAlphaModifier); LineStyleAlphaModifier_DistanceFromCamera(LineStyleAlphaModifier); LineStyleAlphaModifier_DistanceFromObject(LineStyleAlphaModifier).

## LightProbeVolume(LightProbe)

### LightProbeVolume(LightProbe) 

base classes — bpy_struct, ID, LightProbe

class bpy.types. LightProbeVolume ( LightProbe ) 

Light probe that captures low frequency lighting inside a volume

bake_samples 

How many ray directions to sample during the bake (in [1, inf], default 2048)

Type :

int

capture_distance 

Range around the probe volume taken into account while baking (in [1e-06, inf], default 20.0)

Type :

float

capture_emission 

Include emissive surfaces in the bake for more accurate lighting (default True)

Type :

bool

capture_indirect 

Include bounced light from light sources in the bake for more accurate lighting (default True)

Type :

bool

capture_world 

Bake the actual incoming world light, not merely its visibility, for more accurate lighting, at the cost of correct blending with nearby irradiance volumes (default False)

Type :

bool

clamp_direct 

Limit direct lighting intensity to cut noise (set 0 to turn off) (in [0, inf], default 0.0)

Type :

float

clamp_indirect 

Limit indirect lighting intensity to cut noise (set 0 to turn off) (in [0, inf], default 10.0)

Type :

float

dilation_radius 

Search radius, in grid samples, used to find valid samples to copy into invalid ones (in [1, 5], default 1.0)

Type :

float

dilation_threshold 

Fraction of front-facing surface hits below which a grid sample borrows lighting from its neighbors (in [0, 1], default 0.5)

Type :

float

escape_bias 

How far to look for valid capture positions so lighting artifacts are avoided (in [0, 1], default 0.1)

Type :

float

facing_bias 

Makes irradiance interpolation smoother at the expense of some light bleeding (in [0, inf], default 0.5)

Type :

float

intensity 

Adjust the intensity of the lighting this probe captures (in [0, inf], default 1.0)

Type :

float

normal_bias 

Shift irradiance grid sampling along the surface normal to limit light bleeding (in [0, inf], default 0.3)

Type :

float

resolution_x 

Number of samples along the x axis of the volume (in [1, 256], default 4)

Type :

int

resolution_y 

Number of samples along the y axis of the volume (in [1, 256], default 4)

Type :

int

resolution_z 

Number of samples along the z axis of the volume (in [1, 256], default 4)

Type :

int

surface_bias 

Pushes capture points off surfaces to avoid artifacts (in [0, 1], default 0.05)

Type :

float

surfel_density 

Count of surfels created per local unit of distance (raise it for better quality) (in [1, inf], default 20)

Type :

int

validity_threshold 

Fraction of front-facing surface hits below which a grid sample is left out of the lighting (in [0, 1], default 0.4)

Type :

float

view_bias 

Shift irradiance grid sampling along the view direction to limit light bleeding (in [0, inf], default 0.0)

Type :

float

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

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library | ID.library_weak_reference ID.asset_data ID.override_library ID.preview LightProbe.type LightProbe.clip_start LightProbe.show_clip LightProbe.show_influence LightProbe.influence_distance LightProbe.visibility_buffer_bias LightProbe.visibility_bleed_bias LightProbe.visibility_blur LightProbe.visibility_collection LightProbe.invert_visibility_collection LightProbe.show_data LightProbe.use_data_display LightProbe.data_display_size LightProbe.animation_data |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast | bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py LightProbe.bl_rna_get_subclass LightProbe.bl_rna_get_subclass_py |

## Linesets(bpy_prop_collection)

### Linesets(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. Linesets ( bpy_prop_collection ) 

Line sets that pair lines with their style parameters

active 

The line set on display right now (readonly)

Type :

FreestyleLineSet

active_index 

Slot index of the active line set (in [0, inf], default 0)

Type :

int

new ( name ) 

Add a line set into the scene render layer's Freestyle settings

Parameters :

name ( str ) – New name for the line set (not unique) (never None)

Returns :

Newly created line set

Return type :

FreestyleLineSet

remove ( lineset ) 

Take a line set out of the scene render layer's Freestyle settings

Parameters :

lineset (FreestyleLineSet) – Line set to remove (never None)

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

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| FreestyleSettings.linesets | |

## LineStyleAlphaModifier_AlongStroke(LineStyleAlphaModifier)

### LineStyleAlphaModifier_AlongStroke(LineStyleAlphaModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleAlphaModifier

class bpy.types. LineStyleAlphaModifier_AlongStroke ( LineStyleAlphaModifier ) 

Varies alpha transparency as the stroke progresses

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

## LineStyleAlphaModifier_CreaseAngle(LineStyleAlphaModifier)

### LineStyleAlphaModifier_CreaseAngle(LineStyleAlphaModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleAlphaModifier

class bpy.types. LineStyleAlphaModifier_CreaseAngle ( LineStyleAlphaModifier ) 

Drives alpha transparency from the angle formed by two neighboring faces

angle_max 

Upper angle bound for adjusting thickness (in [-inf, inf], default 0.0)

Type :

float

angle_min 

Lower angle bound for adjusting thickness (in [-inf, inf], default 0.0)

Type :

float

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

## LineStyleAlphaModifier_Curvature_3D(LineStyleAlphaModifier)

### LineStyleAlphaModifier_Curvature_3D(LineStyleAlphaModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleAlphaModifier

class bpy.types. LineStyleAlphaModifier_Curvature_3D ( LineStyleAlphaModifier ) 

Drives alpha transparency from the radial curvature measured on 3D mesh surfaces

blend 

How this modifier's output is combined with the underlying base value (default 'MIX' )

Type :

Literal[‘MIX’, ‘ADD’, ‘SUBTRACT’, ‘MULTIPLY’, ‘DIVIDE’, ‘DIFFERENCE’, ‘MINIMUM’, ‘MAXIMUM’]

curvature_max 

Maximum Curvature (in [0, 10000], default 0.0)

Type :

float

curvature_min 

Minimum Curvature (in [0, 10000], default 0.0)

Type :

float

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

## LineStyleAlphaModifier_DistanceFromCamera(LineStyleAlphaModifier)

### LineStyleAlphaModifier_DistanceFromCamera(LineStyleAlphaModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleAlphaModifier

class bpy.types. LineStyleAlphaModifier_DistanceFromCamera ( LineStyleAlphaModifier ) 

Adjusts alpha transparency according to how far the geometry sits from the camera

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

range_max 

Top of the input range over which the mapping operates (in [-inf, inf], default 0.0)

Type :

float

range_min 

Bottom of the input range over which the mapping operates (in [-inf, inf], default 0.0)

Type :

float

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

## LineStyleAlphaModifier_DistanceFromObject(LineStyleAlphaModifier)

### LineStyleAlphaModifier_DistanceFromObject(LineStyleAlphaModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleAlphaModifier

class bpy.types. LineStyleAlphaModifier_DistanceFromObject ( LineStyleAlphaModifier ) 

Adjusts alpha transparency according to how far the geometry sits from an object

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

range_max 

Top of the input range over which the mapping operates (in [-inf, inf], default 0.0)

Type :

float

range_min 

Bottom of the input range over which the mapping operates (in [-inf, inf], default 0.0)

Type :

float

target 

Object that serves as the reference for the distance measurement

Type :

Object

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
