# Sphfluidsettings Bpy Struct, Splinebezierpoints Bpy Prop Collection, Splineikconstraint Constraint, Splinepoint Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: SPHFluidSettings(bpy_struct); SplineBezierPoints(bpy_prop_collection); SplineIKConstraint(Constraint); SplinePoint(bpy_struct); SplinePoints(bpy_prop_collection); SpreadsheetColumn(bpy_struct); SpreadsheetColumnID(bpy_struct); SpreadsheetRowFilter(bpy_struct); SpreadsheetTable(bpy_struct); SpreadsheetTableID(bpy_struct).

## SPHFluidSettings(bpy_struct)

### SPHFluidSettings(bpy_struct)

base class — bpy_struct

class bpy.types. SPHFluidSettings ( bpy_struct )

Configuration for particle fluid physics

buoyancy

Synthetic buoyancy pushing against gravity, driven by pressure differences within the fluid (in [0, 10], default 0.0)

Type :

float

fluid_radius

Radius over which the fluid interacts (in [0, 20], default 0.0)

Type :

float

linear_viscosity

Viscosity, linear (in [0, 100], default 0.0)

Type :

float

plasticity

Degree to which the spring rest length may shift once the elastic limit is exceeded (in [0, 100], default 0.0)

Type :

float

repulsion

How firmly the fluid resists clustering (a factor of stiffness) (in [0, 100], default 0.0)

Type :

float

rest_density

Density of the fluid at rest (in [0, 10000], default 0.0)

Type :

float

rest_length

Rest length of the springs (a factor of particle radius) (in [0, 2], default 0.0)

Type :

float

solver

Algorithm that computes the internal forces acting on particles (default 'DDR' )

- DDR
Double-Density – An artistic solver with pronounced surface tension (the original).

- CLASSICAL
Classical – A solver that is more physically accurate.

Type :

Literal[‘DDR’, ‘CLASSICAL’]

spring_force

Force of the springs (in [0, 100], default 0.0)

Type :

float

spring_frames

How many frames after a particle's birth springs are created for (0 means always) (in [0, 100], default 0)

Type :

int

stiff_viscosity

Generates viscosity for fluid that is expanding (in [0, 100], default 0.0)

Type :

float

stiffness

Degree to which the fluid resists compression (the speed of sound) (in [0, 1000], default 0.0)

Type :

float

use_factor_density

Compute density as a factor of the default density (varies with particle size) (default False)

Type :

bool

use_factor_radius

Treat the interaction radius as a factor of 4 * particle size (default False)

Type :

bool

use_factor_repulsion

Treat repulsion as a factor of stiffness (default False)

Type :

bool

use_factor_rest_length

Treat the spring rest length as a factor of 2 * particle size (default False)

Type :

bool

use_factor_stiff_viscosity

Treat stiff viscosity as a factor of normal viscosity (default False)

Type :

bool

use_initial_rest_length

Adopt the initial length as the spring rest length in place of 2 * particle size (default False)

Type :

bool

use_viscoelastic_springs

Substitute viscoelastic springs for Hooke's springs (default False)

Type :

bool

yield_ratio

Amount of stretching or compression a spring needs before its rest length changes (in [0, 1], default 0.0)

Type :

float

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| ParticleSettings.fluid | |

## SplineBezierPoints(bpy_prop_collection)

### SplineBezierPoints(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. SplineBezierPoints ( bpy_prop_collection )

Set of Bézier points belonging to a spline

add ( count )

Grow this spline by the requested count of new entries

Parameters :

count ( int ) – Number, Number of points to add to the spline (in [0, inf])

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Spline.bezier_points | |

## SplineIKConstraint(Constraint)

### SplineIKConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. SplineIKConstraint ( Constraint )

Lay 'n' bones out along a curve

bulge

Ratio balancing volume change against stretch (in [0, 100], default 0.0)

Type :

float

bulge_max

Upper bound on the volume stretching factor (in [1, 100], default 0.0)

Type :

float

bulge_min

Lower bound on the volume stretching factor (in [0, 1], default 0.0)

Type :

float

bulge_smooth

How strongly the volume stretching is clamped (in [0, 1], default 0.0)

Type :

float

chain_count

Number of bones taking part in the chain (in [1, 255], default 0)

Type :

int

joint_bindings

(EXPERIENCED USERS ONLY) Where the joints sit along the chain, expressed as percentages (array of 32 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

target

The curve driving this relationship

Type :

Object

use_bulge_max

Apply an upper bound on volume variation (default False)

Type :

bool

use_bulge_min

Apply a lower bound on volume variation (default False)

Type :

bool

use_chain_offset

Shift the whole chain with respect to the root joint (default False)

Type :

bool

use_curve_radius

Use the average endpoint radius to tweak the bones' X and Z scaling, layered onto XZ Scale mode (default True)

Type :

bool

use_even_divisions

Disregard the bones' relative lengths when fitting them to the curve (default False)

Type :

bool

use_original_scale

Layer volume preservation on top of the original scaling (default False)

Type :

bool

xz_scale_mode

How scaling of the bones' X and Z axes is decided (default 'NONE' )

- NONE
None – Leave the X and Z axes unscaled.

- `BONE_ORIGINAL`
Bone Original – Keep the bones' original scaling.

- `INVERSE_PRESERVE`
Inverse Scale – The X and Z axis scale becomes the inverse of the Y-Scale.

- `VOLUME_PRESERVE`
Volume Preservation – X and Z axis scale is tuned to keep the bones' volume.

Type :

Literal[‘NONE’, ‘`BONE_ORIGINAL`’, ‘`INVERSE_PRESERVE`’, ‘`VOLUME_PRESERVE`’]

y_scale_mode

How scaling of the bones' Y axis is decided, layered onto the curve's own shape and scaling (default 'NONE' )

- NONE
None – Leave the Y axis unscaled.

- `FIT_CURVE`
Fit Curve – Scale the bones to span the full length of the curve.

- `BONE_ORIGINAL`
Bone Original – Keep the bone's original Y scale.

Type :

Literal[‘NONE’, ‘`FIT_CURVE`’, ‘`BONE_ORIGINAL`’]

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data Constraint.name Constraint.type Constraint.is_override_data Constraint.owner_space Constraint.target_space Constraint.space_object Constraint.space_subtarget | Constraint.mute Constraint.enabled Constraint.show_expanded Constraint.is_valid Constraint.active Constraint.influence Constraint.error_location Constraint.error_rotation |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Constraint.bl_rna_get_subclass Constraint.bl_rna_get_subclass_py |

## SplinePoint(bpy_struct)

### SplinePoint(bpy_struct)

base class — bpy_struct

class bpy.types. SplinePoint ( bpy_struct )

A spline point that carries no handles

co

Coordinates of the point (array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

mathutils.Vector

hide

Whether the point is visible (default False)

Type :

bool

radius

Radius used when beveling (in [0, inf], default 0.0)

Type :

float

select

Whether the point is selected (default False)

Type :

bool

tilt

Tilt as seen in the 3D View (in [-376.991, 376.991], default 0.0)

Type :

float

weight

Weight for NURBS (in [-inf, inf], default 0.0)

Type :

float

weight_softbody

Goal weight for softbody (in [0.01, 100], default 0.0)

Type :

float

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Spline.points | |

## SplinePoints(bpy_prop_collection)

### SplinePoints(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. SplinePoints ( bpy_prop_collection )

Set of points belonging to a spline

add ( count )

Grow this spline by the requested count of new entries

Parameters :

count ( int ) – Number, Number of points to add to the spline (in [0, inf])

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Spline.points | |

## SpreadsheetColumn(bpy_struct)

### SpreadsheetColumn(bpy_struct)

base class — bpy_struct

class bpy.types. SpreadsheetColumn ( bpy_struct )

Data that persists for a column of the spreadsheet

data_type

Type of the data held by the matching column shown in the spreadsheet (default 'BOOLEAN' , readonly)

Type :

Literal[‘INT32’, ‘FLOAT’, ‘BOOLEAN’, ‘INSTANCES’]

id

Key that ties this column back to its origin in the data source (readonly)

Type :

SpreadsheetColumnID

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| SpreadsheetTable.columns | |

## SpreadsheetColumnID(bpy_struct)

### SpreadsheetColumnID(bpy_struct)

base class — bpy_struct

class bpy.types. SpreadsheetColumnID ( bpy_struct )

Information that identifies a spreadsheet column

name

(default “”, never None)

Type :

str

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| SpreadsheetColumn.id | |

## SpreadsheetRowFilter(bpy_struct)

### SpreadsheetRowFilter(bpy_struct)

base class — bpy_struct

class bpy.types. SpreadsheetRowFilter ( bpy_struct )

column_name

(default “”, never None)

Type :

str

enabled

(default False)

Type :

bool

operation

(default 'EQUAL' )

Type :

Literal[‘EQUAL’, ‘GREATER’, ‘LESS’]

show_expanded

(default False)

Type :

bool

threshold

How near two float values must be to count as equal (in [0, inf], default 0.0)

Type :

float

value_boolean

(default False)

Type :

bool

value_color

(array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

value_float

(in [-inf, inf], default 0.0)

Type :

float

value_float2

(array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

bpy_prop_array[float]

value_float3

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

value_int

(in [-inf, inf], default 0)

Type :

int

value_int2

(array of 2 items, in [-inf, inf], default (0, 0))

Type :

bpy_prop_array[int]

value_int3

(array of 3 items, in [-inf, inf], default (0, 0, 0))

Type :

bpy_prop_array[int]

value_int8

(in [-128, 127], default 0)

Type :

int

value_string

(default “”, never None)

Type :

str

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| SpaceSpreadsheet.row_filters | |

## SpreadsheetTable(bpy_struct)

### SpreadsheetTable(bpy_struct)

base class — bpy_struct

class bpy.types. SpreadsheetTable ( bpy_struct )

Data that persists for a table

columns

The table's columns (default None, readonly)

Type :

bpy_prop_collection[SpreadsheetColumn]

id

Key by which the table is recognized (readonly)

Type :

SpreadsheetTableID

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| SpaceSpreadsheet.tables | SpreadsheetTables.active |

## SpreadsheetTableID(bpy_struct)

### SpreadsheetTableID(bpy_struct)

base class — bpy_struct

subclasses —
SpreadsheetTableIDGeometry

class bpy.types. SpreadsheetTableID ( bpy_struct )

Information that identifies a spreadsheet table

type

Which kind of table identifier this is (default 'GEOMETRY' , readonly)

- GEOMETRY
Geometry – The table holds geometry data.

Type :

Literal[‘GEOMETRY’]

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| SpreadsheetTable.id | |
