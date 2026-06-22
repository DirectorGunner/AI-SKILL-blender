# Linestylegeometrymodifier Simplification Linestylegeometrymodifier, Linestylegeometrymodifier Sinusdisplacement Linestylegeometrymodifier, Linestylegeometrymodifier Spatialnoise Linestylegeometrymodifier, Linestylegeometrymodifier Tipremover Linestylegeometrymodifier ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: LineStyleGeometryModifier_Simplification(LineStyleGeometryModifier); LineStyleGeometryModifier_SinusDisplacement(LineStyleGeometryModifier); LineStyleGeometryModifier_SpatialNoise(LineStyleGeometryModifier); LineStyleGeometryModifier_TipRemover(LineStyleGeometryModifier); LineStyleThicknessModifier_AlongStroke(LineStyleThicknessModifier); LineStyleThicknessModifier_Calligraphy(LineStyleThicknessModifier); LineStyleThicknessModifier_CreaseAngle(LineStyleThicknessModifier); LineStyleThicknessModifier_Curvature_3D(LineStyleThicknessModifier); LineStyleThicknessModifier_DistanceFromCamera(LineStyleThicknessModifier).

## LineStyleGeometryModifier_Simplification(LineStyleGeometryModifier)

### LineStyleGeometryModifier_Simplification(LineStyleGeometryModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleGeometryModifier

class bpy.types. LineStyleGeometryModifier_Simplification ( LineStyleGeometryModifier ) 

Reduce the complexity of the stroke set

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

tolerance 

Segments closer together than this distance get merged (in [-inf, inf], default 0.0)

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

## LineStyleGeometryModifier_SinusDisplacement(LineStyleGeometryModifier)

### LineStyleGeometryModifier_SinusDisplacement(LineStyleGeometryModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleGeometryModifier

class bpy.types. LineStyleGeometryModifier_SinusDisplacement ( LineStyleGeometryModifier ) 

Apply a sinusoidal displacement to the stroke backbone geometry

amplitude 

Amplitude of the sinus displacement (in [-inf, inf], default 0.0)

Type :

float

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

phase 

Phase of the sinus displacement (in [-inf, inf], default 0.0)

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

wavelength 

Wavelength of the sinus displacement (in [0.0001, inf], default 0.0)

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

## LineStyleGeometryModifier_SpatialNoise(LineStyleGeometryModifier)

### LineStyleGeometryModifier_SpatialNoise(LineStyleGeometryModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleGeometryModifier

class bpy.types. LineStyleGeometryModifier_SpatialNoise ( LineStyleGeometryModifier ) 

Apply spatial noise to the stroke backbone geometry

amplitude 

Amplitude of the spatial noise (in [-inf, inf], default 0.0)

Type :

float

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

octaves 

Octave count, which sets how much spatial-noise detail is present (in [0, inf], default 0)

Type :

int

scale 

Scale of the spatial noise (in [-inf, inf], default 0.0)

Type :

float

smooth 

When enabled, the spatial noise is smoothed (default False)

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

use_pure_random 

When enabled, the spatial noise has no coherence at all (default False)

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

## LineStyleGeometryModifier_TipRemover(LineStyleGeometryModifier)

### LineStyleGeometryModifier_TipRemover(LineStyleGeometryModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleGeometryModifier

class bpy.types. LineStyleGeometryModifier_TipRemover ( LineStyleGeometryModifier ) 

Trim a segment off each end of the stroke backbone

expanded 

Whether the modifier's tab is shown in its unfolded state (default False)

Type :

bool

tip_length 

Length of tips to be removed (in [-inf, inf], default 0.0)

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

## LineStyleThicknessModifier_AlongStroke(LineStyleThicknessModifier)

### LineStyleThicknessModifier_AlongStroke(LineStyleThicknessModifier) 

base classes — bpy_struct, LineStyleModifier, LineStyleThicknessModifier

class bpy.types. LineStyleThicknessModifier_AlongStroke ( LineStyleThicknessModifier ) 

Varies line thickness as the stroke progresses

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

Literal[Linestyle Thickness Modifier Type Items]

use 

Turn this modifier on or off while the stroke is being rendered (default False)

Type :

bool

value_max 

Top output value the mapping can yield (in [-inf, inf], default 0.0)

Type :

float

value_min 

Bottom output value the mapping can yield (in [-inf, inf], default 0.0)

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

## LineStyleThicknessModifier_Calligraphy(LineStyleThicknessModifier)

### LineStyleThicknessModifier_Calligraphy(LineStyleThicknessModifier)

base classes — bpy_struct, LineStyleModifier, LineStyleThicknessModifier

class bpy.types. LineStyleThicknessModifier_Calligraphy ( LineStyleThicknessModifier )

Varies the stroke width so the result resembles strokes drawn with a calligraphy pen.

blend

Sets the way this modifier's output is combined with the underlying base value (default 'MIX' )

Type :

Literal[‘MIX’, ‘ADD’, ‘SUBTRACT’, ‘MULTIPLY’, ‘DIVIDE’, ‘DIFFERENCE’, ‘MINIMUM’, ‘MAXIMUM’]

expanded

True when the modifier's tab is shown unfolded (default False)

Type :

bool

influence

Weight that scales how strongly the modifier alters the property (in [0, 1], default 0.0)

Type :

float

orientation

Angle defining the principal direction (in [-inf, inf], default 0.0)

Type :

float

thickness_max

Largest width applied along the principal direction (in [0, 10000], default 0.0)

Type :

float

thickness_min

Smallest width applied perpendicular to the principal direction (in [0, 10000], default 0.0)

Type :

float

type

The modifier's kind (default '`ALONG_STROKE`' , readonly)

Type :

Literal[Linestyle Thickness Modifier Type Items]

use

Turn this modifier on or off while strokes are rendered (default False)

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

| bpy_struct.id_data | LineStyleThicknessModifier.name |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleThicknessModifier.bl_rna_get_subclass LineStyleThicknessModifier.bl_rna_get_subclass_py |

## LineStyleThicknessModifier_CreaseAngle(LineStyleThicknessModifier)

### LineStyleThicknessModifier_CreaseAngle(LineStyleThicknessModifier)

base classes — bpy_struct, LineStyleModifier, LineStyleThicknessModifier

class bpy.types. LineStyleThicknessModifier_CreaseAngle ( LineStyleThicknessModifier )

Drives line width from the crease angle formed between two neighboring faces.

angle_max

Upper crease angle at which thickness is altered (in [-inf, inf], default 0.0)

Type :

float

angle_min

Lower crease angle at which thickness is altered (in [-inf, inf], default 0.0)

Type :

float

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

thickness_max

Largest width (in [0, 10000], default 0.0)

Type :

float

thickness_min

Smallest width (in [0, 10000], default 0.0)

Type :

float

type

The modifier's kind (default '`ALONG_STROKE`' , readonly)

Type :

Literal[Linestyle Thickness Modifier Type Items]

use

Turn this modifier on or off while strokes are rendered (default False)

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

| bpy_struct.id_data | LineStyleThicknessModifier.name |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleThicknessModifier.bl_rna_get_subclass LineStyleThicknessModifier.bl_rna_get_subclass_py |

## LineStyleThicknessModifier_Curvature_3D(LineStyleThicknessModifier)

### LineStyleThicknessModifier_Curvature_3D(LineStyleThicknessModifier)

base classes — bpy_struct, LineStyleModifier, LineStyleThicknessModifier

class bpy.types. LineStyleThicknessModifier_Curvature_3D ( LineStyleThicknessModifier )

Derives line width from the radial curvature measured across 3D mesh surfaces.

blend

Sets the way this modifier's output is combined with the underlying base value (default 'MIX' )

Type :

Literal[‘MIX’, ‘ADD’, ‘SUBTRACT’, ‘MULTIPLY’, ‘DIVIDE’, ‘DIFFERENCE’, ‘MINIMUM’, ‘MAXIMUM’]

curvature_max

Upper curvature bound (in [0, 10000], default 0.0)

Type :

float

curvature_min

Lower curvature bound (in [0, 10000], default 0.0)

Type :

float

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

thickness_max

Largest width (in [0, 10000], default 0.0)

Type :

float

thickness_min

Smallest width (in [0, 10000], default 0.0)

Type :

float

type

The modifier's kind (default '`ALONG_STROKE`' , readonly)

Type :

Literal[Linestyle Thickness Modifier Type Items]

use

Turn this modifier on or off while strokes are rendered (default False)

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

| bpy_struct.id_data | LineStyleThicknessModifier.name |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py LineStyleThicknessModifier.bl_rna_get_subclass LineStyleThicknessModifier.bl_rna_get_subclass_py |

## LineStyleThicknessModifier_DistanceFromCamera(LineStyleThicknessModifier)

### LineStyleThicknessModifier_DistanceFromCamera(LineStyleThicknessModifier)

base classes — bpy_struct, LineStyleModifier, LineStyleThicknessModifier

class bpy.types. LineStyleThicknessModifier_DistanceFromCamera ( LineStyleThicknessModifier )

Adjusts line width according to how far the stroke sits from the camera.

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

range_max

Top of the input range over which the mapping operates (in [-inf, inf], default 0.0)

Type :

float

range_min

Bottom of the input range over which the mapping operates (in [-inf, inf], default 0.0)

Type :

float

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
