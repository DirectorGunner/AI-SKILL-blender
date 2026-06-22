# Copytransformsconstraint Constraint, Crossstrip Effectstrip, Cryptomatteentry Bpy Struct, Curvemap Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: CopyTransformsConstraint(Constraint); CrossStrip(EffectStrip); CryptomatteEntry(bpy_struct); CurveMap(bpy_struct); CurveMapPoint(bpy_struct); CurveMapPoints(bpy_prop_collection); CurvePaintSettings(bpy_struct); CurvePoint(bpy_struct); CurveProfile(bpy_struct); CurveProfilePoint(bpy_struct).

## CopyTransformsConstraint(Constraint)

### CopyTransformsConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. CopyTransformsConstraint ( Constraint )

Mirror every transform of the target onto the owner.

head_tail

Where along the bone the target sits, with 0 at the Head and 1 at the Tail (in [0, 1], default 0.0)

Type :

float

mix_mode

Choose the way the copied transform blends with the one already present (default 'REPLACE' )

- REPLACE
Replace – Swap the copied transformation in for the original.

- `BEFORE_FULL`
Before Original (Full) – Put the copied transformation first via plain matrix multiplication, as though the target were a parent under Full Inherit Scale. Combining rotation with non-uniform scale here introduces shear..

- BEFORE
Before Original (Aligned) – Put the copied transformation first, as though the target were a parent under Aligned Inherit Scale. In practice that means Full for location and Split Channels for rotation and scale..

- `BEFORE_SPLIT`
Before Original (Split Channels) – Put the copied transformation first while treating location, rotation, and scale on their own, much like chaining three Copy constraints.

- `AFTER_FULL`
After Original (Full) – Put the copied transformation last via plain matrix multiplication, as though the target were a child under Full Inherit Scale. Combining rotation with non-uniform scale here introduces shear..

- AFTER
After Original (Aligned) – Put the copied transformation last, as though the target were a child under Aligned Inherit Scale. In practice that means Full for location and Split Channels for rotation and scale..

- `AFTER_SPLIT`
After Original (Split Channels) – Put the copied transformation last while treating location, rotation, and scale on their own, much like chaining three Copy constraints.

Type :

Literal['REPLACE', '`BEFORE_FULL`', 'BEFORE', '`BEFORE_SPLIT`', '`AFTER_FULL`', 'AFTER', '`AFTER_SPLIT`']

remove_target_shear

Strip shear out of the target transform before it is blended in (default False)

Type :

bool

subtarget

Names a vertex group on a mesh or lattice, or a bone on an armature, … (default "", never None)

Type :

str

target

The object pointed at as a target

Type :

Object

use_bbone_shape

Trace the curve of the B-Bone segments when working out the Head/Tail position (default False)

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

## CrossStrip(EffectStrip)

### CrossStrip(EffectStrip)

base classes — bpy_struct, Strip, EffectStrip

class bpy.types. CrossStrip ( EffectStrip )

Crossfade Strip

input_1

First input for the effect strip (never None)

Type :

Strip

input_2

Second input for the effect strip (never None)

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

## CryptomatteEntry(bpy_struct)

### CryptomatteEntry(bpy_struct)

base class — bpy_struct

class bpy.types. CryptomatteEntry ( bpy_struct )

encoded_hash

(in [-inf, inf], default 0.0, readonly)

Type :

float

name

(default "", readonly, never None)

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

| CompositorNodeCryptomatteV2.entries | |

## CurveMap(bpy_struct)

### CurveMap(bpy_struct)

base class — bpy_struct

class bpy.types. CurveMap ( bpy_struct )

One of the curves within a curve mapping.

points

(default None, readonly)

Type :

CurveMapPoints[CurveMapPoint]

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

| CurveMapping.curves | CurveMapping.evaluate |

## CurveMapPoint(bpy_struct)

### CurveMapPoint(bpy_struct)

base class — bpy_struct

class bpy.types. CurveMapPoint ( bpy_struct )

A single point belonging to a curve in a curve mapping.

handle_type

How the curve interpolates here — Bézier or vector (default 'AUTO' )

Type :

Literal['AUTO', '`AUTO_CLAMPED`', 'VECTOR']

location

The point's X and Y position on the curve (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

select

Whether the curve point is currently selected (default False)

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

| CurveMap.points CurveMapPoints.new | CurveMapPoints.remove |

## CurveMapPoints(bpy_prop_collection)

### CurveMapPoints(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. CurveMapPoints ( bpy_prop_collection )

Collection of Curve Map Points

new ( position , value )

Add point to CurveMap

Parameters :

- position ( float ) – Position, Position to add point (in [-inf, inf])

- value ( float ) – Value, Value of point (in [-inf, inf])

Returns :

New point

Return type :

CurveMapPoint

remove ( point )

Delete point from CurveMap

Parameters :

point (CurveMapPoint) – PointElement to remove (never None)

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

| CurveMap.points | |

## CurvePaintSettings(bpy_struct)

### CurvePaintSettings(bpy_struct)

base class — bpy_struct

class bpy.types. CurvePaintSettings ( bpy_struct )

corner_angle

Anything sharper than this angle counts as a corner (in [0, 3.14159], default 1.22173)

Type :

float

curve_type

Which curve type fresh strokes are drawn as (default 'BEZIER' )

Type :

Literal['POLY', 'BEZIER']

depth_mode

How depth gets projected (default 'CURSOR' )

Type :

Literal['CURSOR', 'SURFACE']

error_threshold

Permit some drift to get a smoother but rougher line (in [1, 100], default 8)

Type :

int

fit_method

Curve fitting method (default 'REFIT' )

Type :

Literal[Curve Fit Method Items]

radius_max

The radius reached at full pressure (or whenever no tablet is in use) (in [0, 100], default 1.0)

Type :

float

radius_min

The smallest radius, hit at the lightest pressure (and the floor while tapering) (in [0, 100], default 0.0)

Type :

float

radius_taper_end

How much the radius tapers from point to point along the curve (in [0, 10], default 0.0)

Type :

float

radius_taper_start

How much the radius tapers from point to point along the curve (in [0, 1], default 0.0)

Type :

float

surface_offset

Lift the stroke off the surface by this amount (in [-10, 10], default 0.0)

Type :

float

surface_plane

Which plane a projected stroke is drawn in (default '`NORMAL_VIEW`' )

- `NORMAL_VIEW`
Normal to Surface – Lay the stroke in a plane that stands at right angles to the surface.

- `NORMAL_SURFACE`
Tangent to Surface – Lay the stroke flat within the surface plane.

- VIEW
View – Lay the stroke in a plane that lines up with the viewport.

Type :

Literal['`NORMAL_VIEW`', '`NORMAL_SURFACE`', 'VIEW']

use_corners_detect

Spot corners and give them non-aligned handles (default True)

Type :

bool

use_offset_absolute

Use a constant offset rather than scaling it by the radius (default False)

Type :

bool

use_pressure_radius

Drive the curve radius from tablet pressure (default False)

Type :

bool

use_project_only_selected

Limit stroke projection to the selected objects (default False)

Type :

bool

use_stroke_endpoints

Take the depth from where the stroke starts (default False)

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

| ToolSettings.curve_paint_settings | |

## CurvePoint(bpy_struct)

### CurvePoint(bpy_struct)

base class — bpy_struct

class bpy.types. CurvePoint ( bpy_struct )

A control point belonging to a curve.

index

Index of this point (in [0, inf], default 0, readonly)

Type :

int

position

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

radius

(in [-inf, inf], default 0.0)

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| CurveSlice.points | Curves.points |

## CurveProfile(bpy_struct)

### CurveProfile(bpy_struct)

base class — bpy_struct

class bpy.types. CurveProfile ( bpy_struct )

The editor used to construct a profile path.

points

Profile control points (default None, readonly)

Type :

CurveProfilePoints[CurveProfilePoint]

preset

(default 'LINE' )

- LINE
Line – The default.

- SUPPORTS
Support Loops – A loop sitting on either side of the profile.

- CORNICE
Cornice Molding.

- CROWN
Crown Molding.

- STEPS
Steps – A run of steps, however many the segments call for.

Type :

Literal['LINE', 'SUPPORTS', 'CORNICE', 'CROWN', 'STEPS']

segments

Segments sampled from control points (default None, readonly)

Type :

bpy_prop_collection[CurveProfilePoint]

use_clip

Constrain the path view so it stays inside a set boundary (default False)

Type :

bool

use_sample_even_lengths

Sample edges with even lengths (default False)

Type :

bool

use_sample_straight_edges

Sample edges with vector handles (default False)

Type :

bool

update ( )

Refresh the internal data, merge any doubles, and clip the points

reset_view ( )

Set the curve profile grid back to match its clipping size

initialize ( totsegments )

Choose how many display segments there are and populate the tables

Parameters :

totsegments ( int ) – The number of segment values to initialize the segments table with (in [1, 1000], never None)

evaluate ( length_portion )

Evaluate the at the given portion of the path length

Parameters :

length_portion ( float ) – Length Portion, Portion of the path length to travel before evaluation (in [0, 1])

Returns :

Location, The location at the given portion of the profile (array of 2 items, in [-100, 100])

Return type :

mathutils.Vector

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

| BevelModifier.custom_profile Curve.bevel_profile | ToolSettings.custom_bevel_profile_preset |

## CurveProfilePoint(bpy_struct)

### CurveProfilePoint(bpy_struct)

base class — bpy_struct

class bpy.types. CurveProfilePoint ( bpy_struct )

A point that helps define a profile path.

handle_type_1

How the path interpolates here (default 'FREE' )

Type :

Literal['AUTO', 'VECTOR', 'FREE', 'ALIGN']

handle_type_2

How the path interpolates here (default 'FREE' )

Type :

Literal['AUTO', 'VECTOR', 'FREE', 'ALIGN']

location

The point's X and Y position on the path (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

select

Whether the path point is currently selected (default False)

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

| CurveProfile.points CurveProfile.segments | CurveProfilePoints.add CurveProfilePoints.remove |
