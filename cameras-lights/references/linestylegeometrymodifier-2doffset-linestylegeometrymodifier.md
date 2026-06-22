# Linestylegeometrymodifier 2Doffset Linestylegeometrymodifier, Linestylegeometrymodifier 2Dtransform Linestylegeometrymodifier, Linestylegeometrymodifier Backbonestretcher Linestylegeometrymodifier, Linestylegeometrymodifier Beziercurve Linestylegeometrymodifier ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: LineStyleGeometryModifier_2DOffset(LineStyleGeometryModifier); LineStyleGeometryModifier_2DTransform(LineStyleGeometryModifier); LineStyleGeometryModifier_BackboneStretcher(LineStyleGeometryModifier); LineStyleGeometryModifier_BezierCurve(LineStyleGeometryModifier); LineStyleGeometryModifier_Blueprint(LineStyleGeometryModifier); LineStyleGeometryModifier_GuidingLines(LineStyleGeometryModifier); LineStyleGeometryModifier_PerlinNoise1D(LineStyleGeometryModifier); LineStyleGeometryModifier_PerlinNoise2D(LineStyleGeometryModifier); LineStyleGeometryModifier_Polygonalization(LineStyleGeometryModifier); LineStyleGeometryModifier_Sampling(LineStyleGeometryModifier).

## LineStyleGeometryModifier_2DOffset(LineStyleGeometryModifier)

### LineStyleGeometryModifier_2DOffset(LineStyleGeometryModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleGeometryModifier

class bpy.types. LineStyleGeometryModifier_2DOffset ( LineStyleGeometryModifier ) 

Shift the stroke backbone geometry by offsets in two dimensions

end 

Offset measured from the stroke's end point (in [-inf, inf], default 0.0)

Type :

float

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

start 

Offset measured from the stroke's start point (in [-inf, inf], default 0.0)

Type :

float

type 

Which kind of modifier this is (default '2`D_OFFSET`' , readonly)

Type :

Literal[Linestyle Geometry Modifier Type Items]

use 

Turn this modifier on or off while the stroke is being rendered (default False)

Type :

bool

x 

Offset added to the X coordinate of each stroke vertex (in [-inf, inf], default 0.0)

Type :

float

y 

Offset added to the Y coordinate of each stroke vertex (in [-inf, inf], default 0.0)

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

| bpy_struct.id_data | LineStyleGeometryModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleGeometryModifier.bl_rna_get_subclass LineStyleGeometryModifier.bl_rna_get_subclass_py |

## LineStyleGeometryModifier_2DTransform(LineStyleGeometryModifier)

### LineStyleGeometryModifier_2DTransform(LineStyleGeometryModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleGeometryModifier

class bpy.types. LineStyleGeometryModifier_2DTransform ( LineStyleGeometryModifier ) 

Scale and rotate the stroke backbone geometry within two dimensions

angle 

Rotation angle (in [-inf, inf], default 0.0)

Type :

float

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

pivot 

Point around which scaling and rotation are performed (default 'CENTER' )

Type :

Literal[‘CENTER’, ‘START’, ‘END’, ‘PARAM’, ‘ABSOLUTE’]

pivot_u 

Pivot given as the stroke-point parameter u, where 0 <= u <= 1 (in [0, 1], default 0.0)

Type :

float

pivot_x 

X coordinate of the absolute pivot in 2D (in [-inf, inf], default 0.0)

Type :

float

pivot_y 

Y coordinate of the absolute pivot in 2D (in [-inf, inf], default 0.0)

Type :

float

scale_x 

Scaling factor along the X axis (in [-inf, inf], default 0.0)

Type :

float

scale_y 

Scaling factor along the Y axis (in [-inf, inf], default 0.0)

Type :

float

type 

Which kind of modifier this is (default '2`D_OFFSET`' , readonly)

Type :

Literal[Linestyle Geometry Modifier Type Items]

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

| bpy_struct.id_data | LineStyleGeometryModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleGeometryModifier.bl_rna_get_subclass LineStyleGeometryModifier.bl_rna_get_subclass_py |

## LineStyleGeometryModifier_BackboneStretcher(LineStyleGeometryModifier)

### LineStyleGeometryModifier_BackboneStretcher(LineStyleGeometryModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleGeometryModifier

class bpy.types. LineStyleGeometryModifier_BackboneStretcher ( LineStyleGeometryModifier ) 

Extend both ends of the stroke backbone outward

backbone_length 

Amount of backbone stretching (in [-inf, inf], default 0.0)

Type :

float

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

type 

Which kind of modifier this is (default '2`D_OFFSET`' , readonly)

Type :

Literal[Linestyle Geometry Modifier Type Items]

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

| bpy_struct.id_data | LineStyleGeometryModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleGeometryModifier.bl_rna_get_subclass LineStyleGeometryModifier.bl_rna_get_subclass_py |

## LineStyleGeometryModifier_BezierCurve(LineStyleGeometryModifier)

### LineStyleGeometryModifier_BezierCurve(LineStyleGeometryModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleGeometryModifier

class bpy.types. LineStyleGeometryModifier_BezierCurve ( LineStyleGeometryModifier ) 

Swap the stroke backbone for a Bézier-curve fit of the original backbone geometry

error 

Largest separation tolerated from the fitted Bézier curve back to the source backbone geometry (in [-inf, inf], default 0.0)

Type :

float

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

type 

Which kind of modifier this is (default '2`D_OFFSET`' , readonly)

Type :

Literal[Linestyle Geometry Modifier Type Items]

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

| bpy_struct.id_data | LineStyleGeometryModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleGeometryModifier.bl_rna_get_subclass LineStyleGeometryModifier.bl_rna_get_subclass_py |

## LineStyleGeometryModifier_Blueprint(LineStyleGeometryModifier)

### LineStyleGeometryModifier_Blueprint(LineStyleGeometryModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleGeometryModifier

class bpy.types. LineStyleGeometryModifier_Blueprint ( LineStyleGeometryModifier ) 

Generate a blueprint look from circular, elliptic, and square contour strokes

backbone_length 

Amount of backbone stretching (in [-inf, inf], default 0.0)

Type :

float

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

random_backbone 

How much the backbone stretching is randomized (in [0, inf], default 0)

Type :

int

random_center 

How much the center is randomized (in [0, inf], default 0)

Type :

int

random_radius 

How much the radius is randomized (in [0, inf], default 0)

Type :

int

rounds 

Number of rounds in contour strokes (in [1, 1000], default 0)

Type :

int

shape 

Pick the contour-stroke shape used for the blueprint (default 'CIRCLES' )

- CIRCLES
Circles – Draw a blueprint using circular contour strokes.

- ELLIPSES
Ellipses – Draw a blueprint using elliptic contour strokes.

- SQUARES
Squares – Draw a blueprint using square contour strokes.

Type :

Literal[‘CIRCLES’, ‘ELLIPSES’, ‘SQUARES’]

type 

Which kind of modifier this is (default '2`D_OFFSET`' , readonly)

Type :

Literal[Linestyle Geometry Modifier Type Items]

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

| bpy_struct.id_data | LineStyleGeometryModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleGeometryModifier.bl_rna_get_subclass LineStyleGeometryModifier.bl_rna_get_subclass_py |

## LineStyleGeometryModifier_GuidingLines(LineStyleGeometryModifier)

### LineStyleGeometryModifier_GuidingLines(LineStyleGeometryModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleGeometryModifier

class bpy.types. LineStyleGeometryModifier_GuidingLines ( LineStyleGeometryModifier ) 

Reshape the stroke so it follows its principal direction line

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

offset 

How far the principal direction line is shifted in the direction of its normal (in [-inf, inf], default 0.0)

Type :

float

type 

Which kind of modifier this is (default '2`D_OFFSET`' , readonly)

Type :

Literal[Linestyle Geometry Modifier Type Items]

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

| bpy_struct.id_data | LineStyleGeometryModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleGeometryModifier.bl_rna_get_subclass LineStyleGeometryModifier.bl_rna_get_subclass_py |

## LineStyleGeometryModifier_PerlinNoise1D(LineStyleGeometryModifier)

### LineStyleGeometryModifier_PerlinNoise1D(LineStyleGeometryModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleGeometryModifier

class bpy.types. LineStyleGeometryModifier_PerlinNoise1D ( LineStyleGeometryModifier ) 

Apply one-dimensional Perlin noise to the stroke backbone geometry

amplitude 

Amplitude of the Perlin noise (in [-inf, inf], default 0.0)

Type :

float

angle 

Displacement direction (in [-inf, inf], default 0.0)

Type :

float

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

frequency 

Frequency of the Perlin noise (in [-inf, inf], default 0.0)

Type :

float

octaves 

Octave count, which sets how much Perlin-noise detail is present (in [0, inf], default 0)

Type :

int

seed 

Seed for the random number generator; a negative value falls back to using time (in [-inf, inf], default 0)

Type :

int

type 

Which kind of modifier this is (default '2`D_OFFSET`' , readonly)

Type :

Literal[Linestyle Geometry Modifier Type Items]

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

| bpy_struct.id_data | LineStyleGeometryModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleGeometryModifier.bl_rna_get_subclass LineStyleGeometryModifier.bl_rna_get_subclass_py |

## LineStyleGeometryModifier_PerlinNoise2D(LineStyleGeometryModifier)

### LineStyleGeometryModifier_PerlinNoise2D(LineStyleGeometryModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleGeometryModifier

class bpy.types. LineStyleGeometryModifier_PerlinNoise2D ( LineStyleGeometryModifier ) 

Apply two-dimensional Perlin noise to the stroke backbone geometry

amplitude 

Amplitude of the Perlin noise (in [-inf, inf], default 0.0)

Type :

float

angle 

Displacement direction (in [-inf, inf], default 0.0)

Type :

float

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

frequency 

Frequency of the Perlin noise (in [-inf, inf], default 0.0)

Type :

float

octaves 

Octave count, which sets how much Perlin-noise detail is present (in [0, inf], default 0)

Type :

int

seed 

Seed for the random number generator; a negative value falls back to using time (in [-inf, inf], default 0)

Type :

int

type 

Which kind of modifier this is (default '2`D_OFFSET`' , readonly)

Type :

Literal[Linestyle Geometry Modifier Type Items]

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

| bpy_struct.id_data | LineStyleGeometryModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleGeometryModifier.bl_rna_get_subclass LineStyleGeometryModifier.bl_rna_get_subclass_py |

## LineStyleGeometryModifier_Polygonalization(LineStyleGeometryModifier)

### LineStyleGeometryModifier_Polygonalization(LineStyleGeometryModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleGeometryModifier

class bpy.types. LineStyleGeometryModifier_Polygonalization ( LineStyleGeometryModifier ) 

Reshape the stroke geometry to give it a more ‘polygonal’ appearance

error 

Largest gap permitted from the source stroke to the polygonal version that approximates it (in [-inf, inf], default 0.0)

Type :

float

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

type 

Which kind of modifier this is (default '2`D_OFFSET`' , readonly)

Type :

Literal[Linestyle Geometry Modifier Type Items]

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

| bpy_struct.id_data | LineStyleGeometryModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleGeometryModifier.bl_rna_get_subclass LineStyleGeometryModifier.bl_rna_get_subclass_py |

## LineStyleGeometryModifier_Sampling(LineStyleGeometryModifier)

### LineStyleGeometryModifier_Sampling(LineStyleGeometryModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleGeometryModifier

class bpy.types. LineStyleGeometryModifier_Sampling ( LineStyleGeometryModifier ) 

Set a fresh sampling value that controls the resolution of stroke polylines

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

sampling 

Sampling value passed on to any modifiers that follow (in [0, 10000], default 0.0)

Type :

float

type 

Which kind of modifier this is (default '2`D_OFFSET`' , readonly)

Type :

Literal[Linestyle Geometry Modifier Type Items]

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

| bpy_struct.id_data | LineStyleGeometryModifier.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleGeometryModifier.bl_rna_get_subclass LineStyleGeometryModifier.bl_rna_get_subclass_py |
