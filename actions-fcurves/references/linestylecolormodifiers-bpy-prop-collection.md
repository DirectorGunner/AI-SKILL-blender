# Linestylecolormodifiers Bpy Prop Collection, Linestylegeometrymodifier Linestylemodifier, Linestylegeometrymodifiers Bpy Prop Collection, Linestylemodifier Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: LineStyleColorModifiers(bpy_prop_collection); LineStyleGeometryModifier(LineStyleModifier); LineStyleGeometryModifiers(bpy_prop_collection); LineStyleModifier(bpy_struct); LineStyleTextureSlot(TextureSlot); LineStyleTextureSlots(bpy_prop_collection); LineStyleThicknessModifier(LineStyleModifier); LineStyleThicknessModifiers(bpy_prop_collection); LockedTrackConstraint(Constraint); LoopColors(bpy_prop_collection); MaintainVolumeConstraint(Constraint).

## LineStyleColorModifiers(bpy_prop_collection)

### LineStyleColorModifiers(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. LineStyleColorModifiers ( bpy_prop_collection ) 

The set of color modifiers that adjust a line's colors

new ( name , type ) 

Append a new color modifier onto the line style

Parameters :

- name ( str ) – New name for the color modifier (not unique) (never None)

- type (Literal[Linestyle Color Modifier Type Items]) – Color modifier type to add

Returns :

Newly added color modifier

Return type :

LineStyleColorModifier

remove ( modifier ) 

Delete a color modifier from the line style

Parameters :

modifier (LineStyleColorModifier) – Color modifier to remove (never None)

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

| FreestyleLineStyle.color_modifiers | |

## LineStyleGeometryModifier(LineStyleModifier)

### LineStyleGeometryModifier(LineStyleModifier) 

base classes — bpy_struct, LineStyleModifier

subclasses —
LineStyleGeometryModifier_2DOffset, LineStyleGeometryModifier_2DTransform, LineStyleGeometryModifier_BackboneStretcher, LineStyleGeometryModifier_BezierCurve, LineStyleGeometryModifier_Blueprint, LineStyleGeometryModifier_GuidingLines, LineStyleGeometryModifier_PerlinNoise1D, LineStyleGeometryModifier_PerlinNoise2D, LineStyleGeometryModifier_Polygonalization, LineStyleGeometryModifier_Sampling, LineStyleGeometryModifier_Simplification, LineStyleGeometryModifier_SinusDisplacement, LineStyleGeometryModifier_SpatialNoise, LineStyleGeometryModifier_TipRemover

class bpy.types. LineStyleGeometryModifier ( LineStyleModifier ) 

Parent type from which stroke geometry modifiers derive

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

| FreestyleLineStyle.geometry_modifiers LineStyleGeometryModifiers.new | LineStyleGeometryModifiers.remove |

## LineStyleGeometryModifiers(bpy_prop_collection)

### LineStyleGeometryModifiers(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. LineStyleGeometryModifiers ( bpy_prop_collection ) 

The set of geometry modifiers that adjust a line's geometry

new ( name , type ) 

Append a new geometry modifier onto the line style

Parameters :

- name ( str ) – New name for the geometry modifier (not unique) (never None)

- type (Literal[Linestyle Geometry Modifier Type Items]) – Geometry modifier type to add

Returns :

Newly added geometry modifier

Return type :

LineStyleGeometryModifier

remove ( modifier ) 

Delete a geometry modifier from the line style

Parameters :

modifier (LineStyleGeometryModifier) – Geometry modifier to remove (never None)

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

| FreestyleLineStyle.geometry_modifiers | |

## LineStyleModifier(bpy_struct)

### LineStyleModifier(bpy_struct) 

base class — bpy_struct

subclasses —
LineStyleAlphaModifier, LineStyleColorModifier, LineStyleGeometryModifier, LineStyleThicknessModifier

class bpy.types. LineStyleModifier ( bpy_struct ) 

Parent type from which modifiers derive

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

## LineStyleTextureSlot(TextureSlot)

### LineStyleTextureSlot(TextureSlot) 

base classes — bpy_struct, TextureSlot

class bpy.types. LineStyleTextureSlot ( TextureSlot ) 

A texture slot holding a texture for a LineStyle data-block

alpha_factor 

How much the texture affects alpha (in [-inf, inf], default 1.0)

Type :

float

diffuse_color_factor 

How much the texture affects diffuse color (in [-inf, inf], default 1.0)

Type :

float

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

(default 'X' )

Type :

Literal[‘NONE’, ‘X’, ‘Y’, ‘Z’]

mapping_y 

(default 'Y' )

Type :

Literal[‘NONE’, ‘X’, ‘Y’, ‘Z’]

mapping_z 

(default 'Z' )

Type :

Literal[‘NONE’, ‘X’, ‘Y’, ‘Z’]

texture_coords 

Which texture coordinates map the texture onto the background (default '`ALONG_STROKE`' )

- WINDOW
Window – Use screen coordinates as texture coordinates.

- GLOBAL
Global – Use global coordinates for the texture coordinates.

- `ALONG_STROKE`
Along stroke – Use stroke length for texture coordinates.

- ORCO
Generated – Use the original undeformed coordinates of the object.

Type :

Literal[‘WINDOW’, ‘GLOBAL’, ‘`ALONG_STROKE`’, ‘ORCO’]

use_map_alpha 

Whether the texture acts on the alpha value (default False)

Type :

bool

use_map_color_diffuse 

Whether the texture acts on the stroke's base color (default True)

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

| bpy_struct.id_data TextureSlot.texture TextureSlot.name TextureSlot.offset TextureSlot.scale | TextureSlot.color TextureSlot.blend_type TextureSlot.default_value TextureSlot.output_node |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values TextureSlot.bl_rna_get_subclass TextureSlot.bl_rna_get_subclass_py |

### References 

| FreestyleLineStyle.texture_slots LineStyleTextureSlots.add | LineStyleTextureSlots.create |

## LineStyleTextureSlots(bpy_prop_collection)

### LineStyleTextureSlots(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. LineStyleTextureSlots ( bpy_prop_collection ) 

A collection holding texture slots

classmethod add ( ) 

add

Returns :

The newly initialized mtex

Return type :

LineStyleTextureSlot

classmethod create ( index ) 

create

Parameters :

index ( int ) – Index, Slot index to initialize (in [0, inf])

Returns :

The newly initialized mtex

Return type :

LineStyleTextureSlot

classmethod clear ( index ) 

clear

Parameters :

index ( int ) – Index, Slot index to clear (in [0, inf])

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

| FreestyleLineStyle.texture_slots | |

## LineStyleThicknessModifier(LineStyleModifier)

### LineStyleThicknessModifier(LineStyleModifier) 

base classes — bpy_struct, LineStyleModifier

subclasses —
LineStyleThicknessModifier_AlongStroke, LineStyleThicknessModifier_Calligraphy, LineStyleThicknessModifier_CreaseAngle, LineStyleThicknessModifier_Curvature_3D, LineStyleThicknessModifier_DistanceFromCamera, LineStyleThicknessModifier_DistanceFromObject, LineStyleThicknessModifier_Material, LineStyleThicknessModifier_Noise, LineStyleThicknessModifier_Tangent

class bpy.types. LineStyleThicknessModifier ( LineStyleModifier ) 

Parent type from which line thickness modifiers derive

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

| FreestyleLineStyle.thickness_modifiers LineStyleThicknessModifiers.new | LineStyleThicknessModifiers.remove |

## LineStyleThicknessModifiers(bpy_prop_collection)

### LineStyleThicknessModifiers(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. LineStyleThicknessModifiers ( bpy_prop_collection )

The set of thickness modifiers that alter line width.

new ( name , type )

Attach a new thickness modifier to the line style

Parameters :

- name ( str ) – New name for the thickness modifier (not unique) (never None)

- type (Literal[Linestyle Thickness Modifier Type Items]) – Thickness modifier type to add

Returns :

Newly added thickness modifier

Return type :

LineStyleThicknessModifier

remove ( modifier )

Detach a thickness modifier from the line style

Parameters :

modifier (LineStyleThicknessModifier) – Thickness modifier to remove (never None)

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

| FreestyleLineStyle.thickness_modifiers | |

## LockedTrackConstraint(Constraint)

### LockedTrackConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. LockedTrackConstraint ( Constraint )

Aims along the track axis at the target while keeping the remaining axis locked.

head_tail

Position along the bone's length to target, where Head is 0 and Tail is 1 (in [0, 1], default 0.0)

Type :

float

lock_axis

Which axis is held pointing up (default '`LOCK_X`' )

Type :

Literal[‘`LOCK_X`’, ‘`LOCK_Y`’, ‘`LOCK_Z`’]

subtarget

Armature bone, mesh or lattice vertex group, … (default “”, never None)

Type :

str

target

Target object

Type :

Object

track_axis

Which axis aims at the target object (default '`TRACK_X`' )

Type :

Literal[‘`TRACK_X`’, ‘`TRACK_Y`’, ‘`TRACK_Z`’, ‘`TRACK_NEGATIVE_X`’, ‘`TRACK_NEGATIVE_Y`’, ‘`TRACK_NEGATIVE_Z`’]

use_bbone_shape

Track the B-Bone segment shape when working out the Head/Tail position (default False)

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

| bpy_struct.id_data Constraint.name Constraint.type Constraint.is_override_data Constraint.owner_space Constraint.target_space Constraint.space_object Constraint.space_subtarget | Constraint.mute Constraint.enabled Constraint.show_expanded Constraint.is_valid Constraint.active Constraint.influence Constraint.error_location Constraint.error_rotation |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Constraint.bl_rna_get_subclass Constraint.bl_rna_get_subclass_py |

## LoopColors(bpy_prop_collection)

### LoopColors(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. LoopColors ( bpy_prop_collection )

The group of vertex color layers.

active

The vertex color layer currently active

Type :

MeshLoopColorLayer

active_index

Index of the active vertex color layer (in [0, inf], default 0)

Type :

int

new ( * , name = 'Col' , do_init = True )

Attach a new vertex color layer to the Mesh

Parameters :

- name ( str ) – Vertex color name (optional, never None)

- do_init ( bool ) – Whether new layer’s data should be initialized by copying current active one (optional)

Returns :

The newly created layer

Return type :

MeshLoopColorLayer

remove ( layer )

Delete a vertex color layer

Parameters :

layer (MeshLoopColorLayer) – The layer to remove (never None)

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

| Mesh.vertex_colors | |

## MaintainVolumeConstraint(Constraint)

### MaintainVolumeConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. MaintainVolumeConstraint ( Constraint )

Holds volume steady while scaling occurs along one axis.

free_axis

The axis left free for scaling on the object (default '`SAMEVOL_X`' )

Type :

Literal[‘`SAMEVOL_X`’, ‘`SAMEVOL_Y`’, ‘`SAMEVOL_Z`’]

mode

How the constraint handles scaling on the original non-free axes (default 'STRICT' )

- STRICT
Strict – Volume is strictly preserved, overriding the scaling of non-free axes.

- UNIFORM
Uniform – Volume is preserved when the object is scaled uniformly. Deviations from uniform scale on non-free axes are passed through..

- `SINGLE_AXIS`
Single Axis – Volume is preserved when the object is scaled only on the free axis. Non-free axis scaling is passed through..

Type :

Literal[‘STRICT’, ‘UNIFORM’, ‘`SINGLE_AXIS`’]

volume

Resting volume of the bone (in [0, inf], default 0.0)

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

| bpy_struct.id_data Constraint.name Constraint.type Constraint.is_override_data Constraint.owner_space Constraint.target_space Constraint.space_object Constraint.space_subtarget | Constraint.mute Constraint.enabled Constraint.show_expanded Constraint.is_valid Constraint.active Constraint.influence Constraint.error_location Constraint.error_rotation |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Constraint.bl_rna_get_subclass Constraint.bl_rna_get_subclass_py |
