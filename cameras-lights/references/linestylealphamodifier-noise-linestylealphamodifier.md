# Linestylealphamodifier Noise Linestylealphamodifier, Linestylealphamodifier Tangent Linestylealphamodifier, Linestylecolormodifier Alongstroke Linestylecolormodifier, Linestylecolormodifier Creaseangle Linestylecolormodifier ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: LineStyleAlphaModifier_Noise(LineStyleAlphaModifier); LineStyleAlphaModifier_Tangent(LineStyleAlphaModifier); LineStyleColorModifier_AlongStroke(LineStyleColorModifier); LineStyleColorModifier_CreaseAngle(LineStyleColorModifier); LineStyleColorModifier_Curvature_3D(LineStyleColorModifier); LineStyleColorModifier_DistanceFromCamera(LineStyleColorModifier); LineStyleColorModifier_DistanceFromObject(LineStyleColorModifier); LineStyleColorModifier_Noise(LineStyleColorModifier); LineStyleColorModifier_Tangent(LineStyleColorModifier).

## LineStyleAlphaModifier_Noise(LineStyleAlphaModifier)

### LineStyleAlphaModifier_Noise(LineStyleAlphaModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleAlphaModifier

class bpy.types. LineStyleAlphaModifier_Noise ( LineStyleAlphaModifier ) 

Drives alpha transparency from a random noise signal

amplitude 

Amplitude of the noise (in [-inf, inf], default 0.0)

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

period 

Period of the noise (in [-inf, inf], default 0.0)

Type :

float

seed 

Seed for the noise generation (in [1, 32767], default 0)

Type :

int

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

## LineStyleAlphaModifier_Tangent(LineStyleAlphaModifier)

### LineStyleAlphaModifier_Tangent(LineStyleAlphaModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleAlphaModifier

class bpy.types. LineStyleAlphaModifier_Tangent ( LineStyleAlphaModifier ) 

Drives alpha transparency from the orientation the stroke is heading

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

## LineStyleColorModifier_AlongStroke(LineStyleColorModifier)

### LineStyleColorModifier_AlongStroke(LineStyleColorModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleColorModifier

class bpy.types. LineStyleColorModifier_AlongStroke ( LineStyleColorModifier ) 

Varies line color as the stroke progresses

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

type 

Which kind of modifier this is (default '`ALONG_STROKE`' , readonly)

Type :

Literal[Linestyle Color Modifier Type Items]

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

| bpy_struct.id_data | LineStyleColorModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleColorModifier.bl_rna_get_subclass LineStyleColorModifier.bl_rna_get_subclass_py |

## LineStyleColorModifier_CreaseAngle(LineStyleColorModifier)

### LineStyleColorModifier_CreaseAngle(LineStyleColorModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleColorModifier

class bpy.types. LineStyleColorModifier_CreaseAngle ( LineStyleColorModifier ) 

Varies line color according to the crease angle beneath it

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

type 

Which kind of modifier this is (default '`ALONG_STROKE`' , readonly)

Type :

Literal[Linestyle Color Modifier Type Items]

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

| bpy_struct.id_data | LineStyleColorModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleColorModifier.bl_rna_get_subclass LineStyleColorModifier.bl_rna_get_subclass_py |

## LineStyleColorModifier_Curvature_3D(LineStyleColorModifier)

### LineStyleColorModifier_Curvature_3D(LineStyleColorModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleColorModifier

class bpy.types. LineStyleColorModifier_Curvature_3D ( LineStyleColorModifier ) 

Varies line color from the radial curvature measured on 3D mesh surfaces

blend 

How this modifier's output is combined with the underlying base value (default 'MIX' )

Type :

Literal[Ramp Blend Items]

color_ramp 

The color ramp that remaps the line color (readonly)

Type :

ColorRamp

curvature_max 

Maximum Curvature (in [-inf, inf], default 0.0)

Type :

float

curvature_min 

Minimum Curvature (in [-inf, inf], default 0.0)

Type :

float

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

influence 

How strongly this modifier shifts the affected property, weighting its contribution (in [0, 1], default 0.0)

Type :

float

type 

Which kind of modifier this is (default '`ALONG_STROKE`' , readonly)

Type :

Literal[Linestyle Color Modifier Type Items]

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

| bpy_struct.id_data | LineStyleColorModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleColorModifier.bl_rna_get_subclass LineStyleColorModifier.bl_rna_get_subclass_py |

## LineStyleColorModifier_DistanceFromCamera(LineStyleColorModifier)

### LineStyleColorModifier_DistanceFromCamera(LineStyleColorModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleColorModifier

class bpy.types. LineStyleColorModifier_DistanceFromCamera ( LineStyleColorModifier ) 

Varies line color according to how far the geometry sits from the camera

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

Literal[Linestyle Color Modifier Type Items]

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

| bpy_struct.id_data | LineStyleColorModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleColorModifier.bl_rna_get_subclass LineStyleColorModifier.bl_rna_get_subclass_py |

## LineStyleColorModifier_DistanceFromObject(LineStyleColorModifier)

### LineStyleColorModifier_DistanceFromObject(LineStyleColorModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleColorModifier

class bpy.types. LineStyleColorModifier_DistanceFromObject ( LineStyleColorModifier ) 

Varies line color according to how far the geometry sits from an object

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

Literal[Linestyle Color Modifier Type Items]

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

| bpy_struct.id_data | LineStyleColorModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleColorModifier.bl_rna_get_subclass LineStyleColorModifier.bl_rna_get_subclass_py |

## LineStyleColorModifier_Noise(LineStyleColorModifier)

### LineStyleColorModifier_Noise(LineStyleColorModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleColorModifier

class bpy.types. LineStyleColorModifier_Noise ( LineStyleColorModifier ) 

Varies line color from a random noise signal

amplitude 

Amplitude of the noise (in [-inf, inf], default 0.0)

Type :

float

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

period 

Period of the noise (in [-inf, inf], default 0.0)

Type :

float

seed 

Seed for the noise generation (in [1, 32767], default 0)

Type :

int

type 

Which kind of modifier this is (default '`ALONG_STROKE`' , readonly)

Type :

Literal[Linestyle Color Modifier Type Items]

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

| bpy_struct.id_data | LineStyleColorModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleColorModifier.bl_rna_get_subclass LineStyleColorModifier.bl_rna_get_subclass_py |

## LineStyleColorModifier_Tangent(LineStyleColorModifier)

### LineStyleColorModifier_Tangent(LineStyleColorModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleColorModifier

class bpy.types. LineStyleColorModifier_Tangent ( LineStyleColorModifier ) 

Varies line color from the orientation a stroke is heading

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

type 

Which kind of modifier this is (default '`ALONG_STROKE`' , readonly)

Type :

Literal[Linestyle Color Modifier Type Items]

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

| bpy_struct.id_data | LineStyleColorModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleColorModifier.bl_rna_get_subclass LineStyleColorModifier.bl_rna_get_subclass_py |
