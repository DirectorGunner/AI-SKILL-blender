# Layerobjects Bpy Prop Collection, Layoutpanelstate Bpy Struct, Libraryweakreference Bpy Struct, Limitdistanceconstraint Constraint ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: LayerObjects(bpy_prop_collection); LayoutPanelState(bpy_struct); LibraryWeakReference(bpy_struct); LimitDistanceConstraint(Constraint); LimitLocationConstraint(Constraint); LimitRotationConstraint(Constraint); LimitScaleConstraint(Constraint); LineStyleAlphaModifier(LineStyleModifier); LineStyleAlphaModifiers(bpy_prop_collection); LineStyleColorModifier(LineStyleModifier).

## LayerObjects(bpy_prop_collection)

### LayerObjects(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. LayerObjects ( bpy_prop_collection ) 

Collections of objects

active 

This layer's active object

Type :

Object

selected 

Every selected object on this layer (default None, readonly)

Type :

bpy_prop_collection[Object]

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

| ViewLayer.objects | |

## LayoutPanelState(bpy_struct)

### LayoutPanelState(bpy_struct) 

base class — bpy_struct

class bpy.types. LayoutPanelState ( bpy_struct ) 

is_open 

(default False)

Type :

bool

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

## LibraryWeakReference(bpy_struct)

### LibraryWeakReference(bpy_struct) 

base class — bpy_struct

class bpy.types. LibraryWeakReference ( bpy_struct ) 

A read-only pointer to a linked data-block together with its library file

filepath 

Path to the library .blend file (default “”, never None, blend relative // prefix supported)

Type :

str

id_name 

The data-block's full ID name inside the library .blend, with the two-character 'id type' prefix included (default “”, never None)

Type :

str

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

| ID.library_weak_reference | |

## LimitDistanceConstraint(Constraint)

### LimitDistanceConstraint(Constraint) 

base classes — bpy_struct, Constraint

class bpy.types. LimitDistanceConstraint ( Constraint ) 

Limit the distance from target object

distance 

Radius of limiting sphere (in [-inf, inf], default 0.0)

Type :

float

head_tail 

Position along the bone's length, where Head is 0 and Tail is 1 (in [0, 1], default 0.0)

Type :

float

limit_mode 

Which distances relative to the sphere of influence are permitted (default '`LIMITDIST_INSIDE`' )

- `LIMITDIST_INSIDE`
Inside – The object is constrained inside a virtual sphere around the target object, with a radius defined by the limit distance.

- `LIMITDIST_OUTSIDE`
Outside – The object is constrained outside a virtual sphere around the target object, with a radius defined by the limit distance.

- `LIMITDIST_ONSURFACE`
On Surface – The object is constrained on the surface of a virtual sphere around the target object, with a radius defined by the limit distance.

Type :

Literal[‘`LIMITDIST_INSIDE`’, ‘`LIMITDIST_OUTSIDE`’, ‘`LIMITDIST_ONSURFACE`’]

subtarget 

Armature bone, mesh or lattice vertex group, … (default “”, never None)

Type :

str

target 

Target object

Type :

Object

use_bbone_shape 

Trace the B-Bone segment shape when working out the Head/Tail position (default False)

Type :

bool

use_transform_limit 

This constraint affects transforms too (default False)

Type :

bool

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

| bpy_struct.id_data Constraint.name Constraint.type Constraint.is_override_data Constraint.owner_space Constraint.target_space Constraint.space_object Constraint.space_subtarget | Constraint.mute Constraint.enabled Constraint.show_expanded Constraint.is_valid Constraint.active Constraint.influence Constraint.error_location Constraint.error_rotation |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Constraint.bl_rna_get_subclass Constraint.bl_rna_get_subclass_py |

## LimitLocationConstraint(Constraint)

### LimitLocationConstraint(Constraint) 

base classes — bpy_struct, Constraint

class bpy.types. LimitLocationConstraint ( Constraint ) 

Limit the location of the constrained object

max_x 

Highest X value to allow (in [-inf, inf], default 0.0)

Type :

float

max_y 

Highest Y value to allow (in [-inf, inf], default 0.0)

Type :

float

max_z 

Highest Z value to allow (in [-inf, inf], default 0.0)

Type :

float

min_x 

Lowest X value to allow (in [-inf, inf], default 0.0)

Type :

float

min_y 

Lowest Y value to allow (in [-inf, inf], default 0.0)

Type :

float

min_z 

Lowest Z value to allow (in [-inf, inf], default 0.0)

Type :

float

use_max_x 

Use the maximum X value (default False)

Type :

bool

use_max_y 

Use the maximum Y value (default False)

Type :

bool

use_max_z 

Use the maximum Z value (default False)

Type :

bool

use_min_x 

Use the minimum X value (default False)

Type :

bool

use_min_y 

Use the minimum Y value (default False)

Type :

bool

use_min_z 

Use the minimum Z value (default False)

Type :

bool

use_transform_limit 

This constraint affects the transform tools as well (default False)

Type :

bool

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

| bpy_struct.id_data Constraint.name Constraint.type Constraint.is_override_data Constraint.owner_space Constraint.target_space Constraint.space_object Constraint.space_subtarget | Constraint.mute Constraint.enabled Constraint.show_expanded Constraint.is_valid Constraint.active Constraint.influence Constraint.error_location Constraint.error_rotation |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Constraint.bl_rna_get_subclass Constraint.bl_rna_get_subclass_py |

## LimitRotationConstraint(Constraint)

### LimitRotationConstraint(Constraint) 

base classes — bpy_struct, Constraint

class bpy.types. LimitRotationConstraint ( Constraint ) 

Limit the rotation of the constrained object

euler_order 

Set the euler rotation order directly (default 'AUTO' )

- AUTO
Default – Euler using the default rotation order.

- XYZ
XYZ Euler – Euler using the XYZ rotation order.

- XZY
XZY Euler – Euler using the XZY rotation order.

- YXZ
YXZ Euler – Euler using the YXZ rotation order.

- YZX
YZX Euler – Euler using the YZX rotation order.

- ZXY
ZXY Euler – Euler using the ZXY rotation order.

- ZYX
ZYX Euler – Euler using the ZYX rotation order.

Type :

Literal[‘AUTO’, ‘XYZ’, ‘XZY’, ‘YXZ’, ‘YZX’, ‘ZXY’, ‘ZYX’]

max_x 

Upper X angle bound (in [-1000, 1000], default 0.0)

Type :

float

max_y 

Upper Y angle bound (in [-1000, 1000], default 0.0)

Type :

float

max_z 

Upper Z angle bound (in [-1000, 1000], default 0.0)

Type :

float

min_x 

Lower X angle bound (in [-1000, 1000], default 0.0)

Type :

float

min_y 

Lower Y angle bound (in [-1000, 1000], default 0.0)

Type :

float

min_z 

Lower Z angle bound (in [-1000, 1000], default 0.0)

Type :

float

use_legacy_behavior 

Keep the old, partly-broken behavior that fails to account for rotations wrapping around (default False)

Type :

bool

use_limit_x 

Use the minimum X value (default False)

Type :

bool

use_limit_y 

Use the minimum Y value (default False)

Type :

bool

use_limit_z 

Use the minimum Z value (default False)

Type :

bool

use_transform_limit 

This constraint affects the transform tools as well (default False)

Type :

bool

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

| bpy_struct.id_data Constraint.name Constraint.type Constraint.is_override_data Constraint.owner_space Constraint.target_space Constraint.space_object Constraint.space_subtarget | Constraint.mute Constraint.enabled Constraint.show_expanded Constraint.is_valid Constraint.active Constraint.influence Constraint.error_location Constraint.error_rotation |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Constraint.bl_rna_get_subclass Constraint.bl_rna_get_subclass_py |

## LimitScaleConstraint(Constraint)

### LimitScaleConstraint(Constraint) 

base classes — bpy_struct, Constraint

class bpy.types. LimitScaleConstraint ( Constraint ) 

Limit the scaling of the constrained object

max_x 

Highest X value to allow (in [-1000, 1000], default 0.0)

Type :

float

max_y 

Highest Y value to allow (in [-1000, 1000], default 0.0)

Type :

float

max_z 

Highest Z value to allow (in [-1000, 1000], default 0.0)

Type :

float

min_x 

Lowest X value to allow (in [-1000, 1000], default 0.0)

Type :

float

min_y 

Lowest Y value to allow (in [-1000, 1000], default 0.0)

Type :

float

min_z 

Lowest Z value to allow (in [-1000, 1000], default 0.0)

Type :

float

use_max_x 

Use the maximum X value (default False)

Type :

bool

use_max_y 

Use the maximum Y value (default False)

Type :

bool

use_max_z 

Use the maximum Z value (default False)

Type :

bool

use_min_x 

Use the minimum X value (default False)

Type :

bool

use_min_y 

Use the minimum Y value (default False)

Type :

bool

use_min_z 

Use the minimum Z value (default False)

Type :

bool

use_transform_limit 

This constraint affects the transform tools as well (default False)

Type :

bool

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

| bpy_struct.id_data Constraint.name Constraint.type Constraint.is_override_data Constraint.owner_space Constraint.target_space Constraint.space_object Constraint.space_subtarget | Constraint.mute Constraint.enabled Constraint.show_expanded Constraint.is_valid Constraint.active Constraint.influence Constraint.error_location Constraint.error_rotation |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Constraint.bl_rna_get_subclass Constraint.bl_rna_get_subclass_py |

## LineStyleAlphaModifier(LineStyleModifier)

### LineStyleAlphaModifier(LineStyleModifier) 

base classes — bpy_struct, LineStyleModifier

subclasses —
LineStyleAlphaModifier_AlongStroke, LineStyleAlphaModifier_CreaseAngle, LineStyleAlphaModifier_Curvature_3D, LineStyleAlphaModifier_DistanceFromCamera, LineStyleAlphaModifier_DistanceFromObject, LineStyleAlphaModifier_Material, LineStyleAlphaModifier_Noise, LineStyleAlphaModifier_Tangent

class bpy.types. LineStyleAlphaModifier ( LineStyleModifier ) 

The base type from which alpha transparency modifiers derive

name 

Name of the modifier (default “”, never None)

Type :

str

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py |

### References 

| FreestyleLineStyle.alpha_modifiers LineStyleAlphaModifiers.new | LineStyleAlphaModifiers.remove |

## LineStyleAlphaModifiers(bpy_prop_collection)

### LineStyleAlphaModifiers(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. LineStyleAlphaModifiers ( bpy_prop_collection ) 

The set of alpha modifiers that adjust a line's alpha values

new ( name , type ) 

Append a new alpha modifier onto the line style

Parameters :

- name ( str ) – New name for the alpha modifier (not unique) (never None)

- type (Literal[Linestyle Alpha Modifier Type Items]) – Alpha modifier type to add

Returns :

Newly added alpha modifier

Return type :

LineStyleAlphaModifier

remove ( modifier ) 

Delete an alpha modifier from the line style

Parameters :

modifier (LineStyleAlphaModifier) – Alpha modifier to remove (never None)

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

| FreestyleLineStyle.alpha_modifiers | |

## LineStyleColorModifier(LineStyleModifier)

### LineStyleColorModifier(LineStyleModifier) 

base classes — bpy_struct, LineStyleModifier

subclasses —
LineStyleColorModifier_AlongStroke, LineStyleColorModifier_CreaseAngle, LineStyleColorModifier_Curvature_3D, LineStyleColorModifier_DistanceFromCamera, LineStyleColorModifier_DistanceFromObject, LineStyleColorModifier_Material, LineStyleColorModifier_Noise, LineStyleColorModifier_Tangent

class bpy.types. LineStyleColorModifier ( LineStyleModifier ) 

Parent type from which line color modifiers derive

name 

Name of the modifier (default “”, never None)

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values LineStyleModifier.bl_rna_get_subclass LineStyleModifier.bl_rna_get_subclass_py |

### References 

| FreestyleLineStyle.color_modifiers LineStyleColorModifiers.new | LineStyleColorModifiers.remove |
