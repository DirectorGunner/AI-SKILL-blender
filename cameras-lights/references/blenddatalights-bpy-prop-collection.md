# Blenddatalights Bpy Prop Collection, Blenddatameshes Bpy Prop Collection, Blenddataprobes Bpy Prop Collection, Buildmodifier Modifier ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: BlendDataLights(bpy_prop_collection); BlendDataMeshes(bpy_prop_collection); BlendDataProbes(bpy_prop_collection); BuildModifier(Modifier); CameraSolverConstraint(Constraint); CameraStereoData(bpy_struct); CastModifier(Modifier); ClothModifier(Modifier); CollectionChild(bpy_struct); CollectionLightLinking(bpy_struct); CollectionObject(bpy_struct).

## BlendDataLights(bpy_prop_collection)

Registry of non-photorealistic rendering stroke styles.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataLineStyles ( bpy_prop_collection )

Collection of line styles

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

new ( name ) 

Register a line style in the database

Parameters :

name ( str ) – New name for the data-block (never None)

Returns :

New line style data-block

Return type :

FreestyleLineStyle

remove ( linestyle , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Unregister a line style from the current file

Parameters :

- linestyle (FreestyleLineStyle) – Line style to remove (never None)

- do_unlink ( bool ) – Break all references to this line style before deletion (optional)

- do_id_user ( bool ) – Reduce user count for all data-blocks used (optional)

- do_ui_user ( bool ) – Ensure the interface is updated (optional)

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

| BlendData.linestyles | |

## BlendDataMeshes(bpy_prop_collection)

Registry of implicit surface blob objects.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataMetaBalls ( bpy_prop_collection )

Collection of metaballs

new ( name ) 

Add a metaball to the database

Parameters :

name ( str ) – New name for the data-block (never None)

Returns :

New metaball data-block

Return type :

MetaBall

remove ( metaball , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Remove a metaball from the current file

Parameters :

- metaball (MetaBall) – Metaball to remove (never None)

- do_unlink ( bool ) – Break all references to this metaball before deletion (WARNING: will also delete objects instancing that metaball data) (optional)

- do_id_user ( bool ) – Reduce user count for all data-blocks used (optional)

- do_ui_user ( bool ) – Ensure the interface is updated (optional)

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

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

| BlendData.metaballs | |

## BlendDataProbes(bpy_prop_collection)

### BlendDataProbes(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendDataProbes(bpy_prop_collection)

Stores a collection of light probe instances.

new(name, type)

Creates and adds a light probe to Blender's database.

Parameters:
- name (str) – Probe name (cannot be None)
- type (Literal[Lightprobes Type Items]) – Probe classification; specifies which probe subtype to instantiate

Returns:
New light probe data-block

Return type:
LightProbe

remove(lightprobe, *, do_unlink=True, do_id_user=True, do_ui_user=True)

Destroys a light probe from the blend file.

Parameters:
- lightprobe (LightProbe) – Probe to destroy (cannot be None)
- do_unlink (bool) – Separate all connections before destruction (WARNING: will also delete objects instancing that light probe data) (optional)
- do_id_user (bool) – Update user counts in dependent structures (optional)
- do_ui_user (bool) – Remove interface linkages (optional)

tag(value)

Mark with a tag.

Parameters:
- value (bool) – Tag flag

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – RNA identifier.
- default (bpy.types.Struct | None) – Return if not found.

Returns:
The RNA type or return value.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – RNA identifier.
- default (type | None) – Return if not found.

Returns:
The class or return value.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendData.lightprobes | |

## BuildModifier(Modifier)

### BuildModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. BuildModifier ( Modifier )

Modifier that reveals geometry progressively over time

frame_duration

Total duration in frames for the build sequence (in [1, 1.04857e+06], default 100.0)

Type :

float

frame_start

Frame where the sequence begins (in [-1.04857e+06, 1.04857e+06], default 1.0)

Type :

float

seed

Random seed for variation (in [1, 1048574], default 0)

Type :

int

use_random_order

Shuffle faces or edges during progression (default False)

Type :

bool

use_reverse

Hide geometry instead of revealing it (default False)

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## CameraSolverConstraint(Constraint)

### CameraSolverConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. CameraSolverConstraint ( Constraint )

Constrain motion to reconstructed camera movements

clip

Movie Clip source for tracking info

Type :

MovieClip

use_active_clip

Use the scene's active clip (default False)

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

## CameraStereoData(bpy_struct)

### CameraStereoData(bpy_struct)

base class — bpy_struct

class bpy.types. CameraStereoData ( bpy_struct )

Stereoscopic camera configuration

convergence_distance

Focal point distance (typically projector-to-screen gap) (in [1e-05, inf], default 1.95)

Type :

float

convergence_mode

(default 'OFFAXIS' )

- OFFAXIS
Off-Axis – Off-axis frustums converging in a plane.

- PARALLEL
Parallel – Parallel cameras with no convergence.

- TOE
Toe-in – Rotated cameras, looking at the same point at the convergence distance.

Type :

Literal['OFFAXIS', 'PARALLEL', 'TOE']

interocular_distance

Spacing between eyes; typically 1/30th of the stereo plane (in [0, inf], default 0.065)

Type :

float

pivot

(default 'LEFT' )

Type :

Literal['LEFT', 'RIGHT', 'CENTER']

pole_merge_angle_from

Angle where eye separation begins fading (in [0, 1.5708], default 1.0472)

Type :

float

pole_merge_angle_to

Angle where eye separation fully disappears (in [0, 1.5708], default 1.309)

Type :

float

use_pole_merge

Decrease eye separation at poles (in [-inf, inf], default False)

Type :

bool

use_spherical_stereo

Render via rotating camera around eye center (default False)

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

| Camera.stereo | |

## CastModifier(Modifier)

### CastModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. CastModifier ( Modifier )

Modifier that distorts mesh into other geometries

cast_type

Target geometry (default 'SPHERE' )

Type :

Literal['SPHERE', 'CYLINDER', 'CUBOID']

factor

(in [-inf, inf], default 0.5)

Type :

float

invert_vertex_group

Negate the effect of the vertex group (default False)

Type :

bool

object

Control object; its location determines the effect center

Type :

Object

radius

Deformation range from effect center, 0 = unlimited (in [0, inf], default 0.0)

Type :

float

size

Shape size, 0 = computed automatically (in [0, inf], default 0.0)

Type :

float

use_radius_as_size

Apply radius as shape size (0 = auto) (default True)

Type :

bool

use_transform

Respect object transform for shape control (default False)

Type :

bool

use_x

(default True)

Type :

bool

use_y

(default True)

Type :

bool

use_z

(default True)

Type :

bool

vertex_group

Vertex group name (default "", never None)

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## ClothModifier(Modifier)

### ClothModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. ClothModifier ( Modifier )

Cloth simulation modifier

collision_settings

(readonly, never None)

Type :

ClothCollisionSettings

hair_grid_max

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

hair_grid_min

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

hair_grid_resolution

(array of 3 items, in [-inf, inf], default (0, 0, 0), readonly)

Type :

bpy_prop_array[int]

point_cache

(readonly, never None)

Type :

PointCache

settings

(readonly, never None)

Type :

ClothSettings

solver_result

(readonly)

Type :

ClothSolverResult

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

### References

| bpy.context.cloth | ParticleSystem.cloth |

## CollectionChild(bpy_struct)

### CollectionChild(bpy_struct)

base class — bpy_struct

class bpy.types. CollectionChild ( bpy_struct )

A child collection bundled with the settings tied to it

light_linking

The collection object's light linking configuration (readonly, never None)

Type :

CollectionLightLinking

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

| Collection.collection_children | |

## CollectionLightLinking(bpy_struct)

### CollectionLightLinking(bpy_struct)

base class — bpy_struct

class bpy.types. CollectionLightLinking ( bpy_struct )

Light linking configuration for a collection's objects and child collections

link_state

Whether the object or collection receives light or shadow (default 'INCLUDE' )

Type :

Literal[‘INCLUDE’, ‘EXCLUDE’]

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

| CollectionChild.light_linking | CollectionObject.light_linking |

## CollectionObject(bpy_struct)

### CollectionObject(bpy_struct)

base class — bpy_struct

class bpy.types. CollectionObject ( bpy_struct )

An object within a collection bundled with its collection-specific settings

light_linking

The collection's light linking configuration (readonly, never None)

Type :

CollectionLightLinking

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

| Collection.collection_objects | |
