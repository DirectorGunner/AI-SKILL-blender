# Clamptoconstraint Constraint, Clothcollisionsettings Bpy Struct, Clothsolverresult Bpy Struct, Collectionexport Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ClampToConstraint(Constraint); ClothCollisionSettings(bpy_struct); ClothSolverResult(bpy_struct); CollectionExport(bpy_struct); CollectionExports(bpy_prop_collection); CollectionProperty(Property); CollisionSettings(bpy_struct); ColorBalanceModifier(StripModifier); ColorManagedSequencerColorspaceSettings(bpy_struct); ColorMixStrip(EffectStrip).

## ClampToConstraint(Constraint)

### ClampToConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. ClampToConstraint ( Constraint )

Restrict position to nearest point on target curve

main_axis

Primary movement direction (default '`CLAMPTO_AUTO`' )

Type :

Literal['`CLAMPTO_AUTO`', '`CLAMPTO_X`', '`CLAMPTO_Y`', '`CLAMPTO_Z`']

target

Target Object (Curves only)

Type :

Object

use_cyclic

Treat curve as continuous loop (no edge clamping) (default False)

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

## ClothCollisionSettings(bpy_struct)

### ClothCollisionSettings(bpy_struct)

base class — bpy_struct

class bpy.types. ClothCollisionSettings ( bpy_struct )

Cloth simulation options for object and self collision

collection

Restrict colliders to objects in this Collection

Type :

Collection

collision_quality

Solver iterations (higher = more accurate but slower) (in [1, 32767], default 2)

Type :

int

damping

Velocity reduction on collision (in [0, 1], default 1.0)

Type :

float

distance_min

Minimum gap before collision kicks in (in [0.001, 1], default 0.015)

Type :

float

friction

Sliding resistance on contact (higher = more resistance) (in [0, 80], default 5.0)

Type :

float

impulse_clamp

Impulse limit to stabilize (0 disables) (in [0, 100], default 0.0)

Type :

float

self_distance_min

Minimum gap for self-collision response (in [0.001, 0.1], default 0.015)

Type :

float

self_friction

Self-contact sliding resistance (in [0, 80], default 5.0)

Type :

float

self_impulse_clamp

Self-collision impulse limit (0 disables) (in [0, 100], default 0.0)

Type :

float

use_collision

Enable object collisions (default True)

Type :

bool

use_self_collision

Enable self-intersections (default False)

Type :

bool

vertex_group_object_collisions

Exclude triangles where all vertices belong to this group from object collisions (default "", never None)

Type :

str

vertex_group_self_collisions

Exclude triangles where all vertices belong to this group from self-collisions (default "", never None)

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| ClothModifier.collision_settings | |

## ClothSolverResult(bpy_struct)

### ClothSolverResult(bpy_struct)

base class — bpy_struct

class bpy.types. ClothSolverResult ( bpy_struct )

Cloth solver iteration outcome

avg_error

Average divergence over substeps (in [-inf, inf], default 0.0, readonly)

Type :

float

avg_iterations

Mean iteration count across substeps (in [-inf, inf], default 0.0, readonly)

Type :

float

max_error

Highest divergence in substeps (in [-inf, inf], default 0.0, readonly)

Type :

float

max_iterations

Highest iteration count in substeps (in [-inf, inf], default 0, readonly)

Type :

int

min_error

Lowest divergence in substeps (in [-inf, inf], default 0.0, readonly)

Type :

float

min_iterations

Lowest iteration count in substeps (in [-inf, inf], default 0, readonly)

Type :

int

status

Solver outcome flag (default set(), readonly)

- SUCCESS
Success – Computation was successful.

- `NUMERICAL_ISSUE`
Numerical Issue – The provided data did not satisfy the prerequisites.

- `NO_CONVERGENCE`
No Convergence – Iterative procedure did not converge.

- `INVALID_INPUT`
Invalid Input – The inputs are invalid, or the algorithm has been improperly called.

Type :

set[Literal['SUCCESS', '`NUMERICAL_ISSUE`', '`NO_CONVERGENCE`', '`INVALID_INPUT`']]

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

| ClothModifier.solver_result | |

## CollectionExport(bpy_struct)

### CollectionExport(bpy_struct)

base class — bpy_struct

class bpy.types. CollectionExport ( bpy_struct )

export_properties

The property group belonging to the configured exporter (readonly)

Type :

PropertyGroup

filepath

Destination path that exporting writes to (default “”, never None, blend relative // prefix supported)

Type :

str

is_open

Tracks whether the panel is currently expanded (default False)

Type :

bool

name

(default “”, never None)

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Collection.exporters CollectionExports.new | CollectionExports.remove |

## CollectionExports(bpy_prop_collection)

### CollectionExports(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. CollectionExports ( bpy_prop_collection )

A group holding the export handlers

new ( type , * , name = '' )

Create and attach another export handler within the collection

Parameters :

- type ( Literal [ '`IO_FH`_alembic' , '`IO_FH`_usd' , '`IO_FH`_obj' , '`IO_FH`_ply' , '`IO_FH`_stl' , '`IO_FH`_fbx' , '`IO_FH`_gltf2' ] ) – Type, Which kind of export handler to create

- name ( str ) – Name, The label assigned to this freshly made handler (optional, never None)

Returns :

The export handler that was just created

Return type :

CollectionExport

remove ( exporter )

Detach the given export handler so it no longer belongs to the collection

Parameters :

exporter (CollectionExport) – Export Handler to remove

move ( from_index , to_index )

Reorder an export handler within the collection

Parameters :

- from_index ( int ) – From Index, Index to move (in [-inf, inf])

- to_index ( int ) – To Index, Target index (in [-inf, inf])

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

| Collection.exporters | |

## CollectionProperty(Property)

### CollectionProperty(Property)

base classes — bpy_struct, Property

class bpy.types. CollectionProperty ( Property )

An RNA collection property used for lists, arrays, and mappings

fixed_type

The locked pointer type; left empty when the type can vary (readonly)

Type :

Struct

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

| bpy_struct.id_data Property.name Property.identifier Property.description Property.translation_context Property.type Property.subtype Property.srna Property.unit Property.icon Property.is_readonly Property.is_animatable Property.is_overridable Property.is_required Property.is_argument_optional Property.is_never_none Property.is_hidden | Property.is_skip_save Property.is_skip_preset Property.is_output Property.is_registered Property.is_registered_optional Property.is_runtime Property.is_enum_flag Property.is_library_editable Property.is_path_output Property.is_path_supports_blend_relative Property.is_path_supports_templates Property.is_deprecated Property.deprecated_note Property.deprecated_version Property.deprecated_removal_version Property.tags |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Property.bl_rna_get_subclass Property.bl_rna_get_subclass_py |

## CollisionSettings(bpy_struct)

### CollisionSettings(bpy_struct)

base class — bpy_struct

class bpy.types. CollisionSettings ( bpy_struct )

Settings that govern an object's collision behavior in a physics simulation

absorption

Fraction of incoming effector force this object soaks up on collision (expressed as a percentage) (in [0, 1], default 0.0)

Type :

float

cloth_friction

Friction applied during cloth collisions (in [0, 80], default 0.0)

Type :

float

damping

How strongly the collision dampens motion (in [0, 1], default 0.0)

Type :

float

damping_factor

How strongly particle collisions are dampened (in [0, 1], default 0.0)

Type :

float

damping_random

Randomized spread applied to the damping value (in [0, 1], default 0.0)

Type :

float

friction_factor

How much friction particles encounter on collision (in [0, 1], default 0.0)

Type :

float

friction_random

Randomized spread applied to the friction value (in [0, 1], default 0.0)

Type :

float

permeability

Probability that a particle passes straight through the mesh (in [0, 1], default 0.0)

Type :

float

stickiness

How strongly things stick when they collide with the surface (in [0, 10], default 0.0)

Type :

float

thickness_inner

Thickness on the inner side of faces (softbodies only) (in [0.001, 1], default 0.0)

Type :

float

thickness_outer

Thickness on the outer side of faces (in [0.001, 1], default 0.0)

Type :

float

use

Make this object act as a collider for physics systems (default False)

Type :

bool

use_culling

Have cloth collisions respect the collider's normals, which helps recover from penetration (default False)

Type :

bool

use_normal

Direct cloth collision impulses along the collider's normals, which is steadier in certain situations (default False)

Type :

bool

use_particle_kill

Destroy particles that collide (default False)

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

| CollisionModifier.settings | Object.collision |

## ColorBalanceModifier(StripModifier)

### ColorBalanceModifier(StripModifier)

base classes — bpy_struct, StripModifier

class bpy.types. ColorBalanceModifier ( StripModifier )

A strip modifier that performs color balancing on a sequence strip

color_balance

(readonly)

Type :

StripColorBalanceData

color_multiply

Scale the brightness of every pixel (in [0, 20], default 1.0)

Type :

float

open_mask_input_panel

(default False)

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

| bpy_struct.id_data StripModifier.name StripModifier.type StripModifier.mute StripModifier.enable StripModifier.show_expanded | StripModifier.input_mask_type StripModifier.mask_time StripModifier.input_mask_strip StripModifier.input_mask_id StripModifier.is_active |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values StripModifier.bl_rna_get_subclass StripModifier.bl_rna_get_subclass_py |

## ColorManagedSequencerColorspaceSettings(bpy_struct)

### ColorManagedSequencerColorspaceSettings(bpy_struct)

base class — bpy_struct

class bpy.types. ColorManagedSequencerColorspaceSettings ( bpy_struct )

Settings for the input color space

name

The color space in which the sequencer works (default 'NONE' )

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

| Scene.sequencer_colorspace_settings | |

## ColorMixStrip(EffectStrip)

### ColorMixStrip(EffectStrip)

base classes — bpy_struct, Strip, EffectStrip

class bpy.types. ColorMixStrip ( EffectStrip )

Color Mix Strip

blend_effect

How the strip is blended together with the other strips (default 'DARKEN' )

Type :

Literal[‘DARKEN’, ‘MULTIPLY’, ‘BURN’, ‘`LINEAR_BURN`’, ‘LIGHTEN’, ‘SCREEN’, ‘DODGE’, ‘ADD’, ‘OVERLAY’, ‘`SOFT_LIGHT`’, ‘`HARD_LIGHT`’, ‘`VIVID_LIGHT`’, ‘`LINEAR_LIGHT`’, ‘`PIN_LIGHT`’, ‘DIFFERENCE’, ‘EXCLUSION’, ‘SUBTRACT’, ‘HUE’, ‘SATURATION’, ‘COLOR’, ‘VALUE’]

factor

How strongly this strip's colors influence the other strips, as a percentage (in [0, 1], default 0.0)

Type :

float

input_1

The effect strip's first input (never None)

Type :

Strip

input_2

The effect strip's second input (never None)

Type :

Strip

input_count

(in [0, inf], default 0, readonly)

Type :

int

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

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset | Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys EffectStrip.use_deinterlace EffectStrip.alpha_mode EffectStrip.use_flip_x EffectStrip.use_flip_y EffectStrip.use_float EffectStrip.use_reverse_frames EffectStrip.color_multiply EffectStrip.multiply_alpha EffectStrip.color_saturation EffectStrip.strobe EffectStrip.transform EffectStrip.crop EffectStrip.use_proxy EffectStrip.proxy |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py EffectStrip.bl_rna_get_subclass EffectStrip.bl_rna_get_subclass_py |
