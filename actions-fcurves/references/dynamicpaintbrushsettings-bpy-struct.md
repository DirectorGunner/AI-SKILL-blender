# Dynamicpaintbrushsettings Bpy Struct, Dynamicpaintcanvassettings Bpy Struct, Dynamicpaintsurfaces Bpy Prop Collection, Echomodifier Stripmodifier ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: DynamicPaintBrushSettings(bpy_struct); DynamicPaintCanvasSettings(bpy_struct); DynamicPaintSurfaces(bpy_prop_collection); EchoModifier(StripModifier); EditBone(bpy_struct).

## DynamicPaintBrushSettings(bpy_struct)

### DynamicPaintBrushSettings(bpy_struct)

base class — bpy_struct

class bpy.types. DynamicPaintBrushSettings ( bpy_struct )

Settings for a brush

invert_proximity

Apply the proximity falloff on the inside of the volume (default False)

Type :

bool

paint_alpha

Alpha of the paint (in [0, 1], default 0.0)

Type :

float

paint_color

The paint’s color (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

paint_distance

Furthest the brush can sit from the mesh surface and still affect paint (in [0, 500], default 0.0)

Type :

float

paint_ramp

Color ramp that shapes the proximity falloff (readonly)

Type :

ColorRamp

paint_source

(default 'VOLUME' )

Type :

Literal[‘`PARTICLE_SYSTEM`’, ‘POINT’, ‘DISTANCE’, ‘`VOLUME_DISTANCE`’, ‘VOLUME’]

paint_wetness

How wet the paint is, shown in the wetmap (a few effects act only on wet paint) (in [0, 1], default 0.0)

Type :

float

particle_system

The particle system used as the painting source

Type :

ParticleSystem

proximity_falloff

Which type of proximity falloff to use (default 'CONSTANT' )

Type :

Literal[‘SMOOTH’, ‘CONSTANT’, ‘RAMP’]

ray_direction

Which way rays are cast for projection (paint lands when the brush object lies that way) (default 'CANVAS' )

Type :

Literal[‘CANVAS’, ‘BRUSH’, ‘`Z_AXIS`’]

smooth_radius

Extra smooth falloff tacked on past the solid radius (in [0, 10], default 0.0)

Type :

float

smudge_strength

How strong the smudge effect is (in [0, 1], default 0.0)

Type :

float

solid_radius

The radius painted at full solid coverage (in [0.01, 10], default 0.0)

Type :

float

use_absolute_alpha

Raise the alpha value only where the paint alpha exceeds what’s already there (default False)

Type :

bool

use_negative_volume

Flip the influence to be negative inside the volume (default False)

Type :

bool

use_paint_erase

Take paint away instead of laying it down (default False)

Type :

bool

use_particle_radius

Take the radius from the particle settings (default False)

Type :

bool

use_proximity_project

Project the brush onto the canvas from a set direction within the brush’s proximity (default False)

Type :

bool

use_proximity_ramp_alpha

Read only the alpha of the color ramp (default False)

Type :

bool

use_smudge

Have this brush smear existing paint as it travels (default False)

Type :

bool

use_velocity_alpha

Scale the brush influence by the alpha of the velocity color ramp (default False)

Type :

bool

use_velocity_color

Swap the brush color for the velocity color ramp (default False)

Type :

bool

use_velocity_depth

Scale the brush intersection depth (displace, waves) by the velocity ramp’s alpha (default False)

Type :

bool

velocity_max

The velocity treated as maximum influence (Blender units per frame) (in [0.0001, 10], default 0.0)

Type :

float

velocity_ramp

Color ramp that shapes the brush velocity effect (readonly)

Type :

ColorRamp

wave_clamp

Cap on how deeply surface intersection feeds the waves (set 0.0 to switch off) (in [0, 50], default 0.0)

Type :

float

wave_factor

Scales how much this brush influences waves (in [-2, 2], default 0.0)

Type :

float

wave_type

(default 'DEPTH' )

Type :

Literal[‘CHANGE’, ‘DEPTH’, ‘FORCE’, ‘REFLECT’]

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

| DynamicPaintModifier.brush_settings | |

## DynamicPaintCanvasSettings(bpy_struct)

### DynamicPaintCanvasSettings(bpy_struct)

base class — bpy_struct

class bpy.types. DynamicPaintCanvasSettings ( bpy_struct )

Settings for a Dynamic Paint canvas

canvas_surfaces

The list of paint surfaces (default None, readonly)

Type :

DynamicPaintSurfaces[DynamicPaintSurface]

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

| DynamicPaintModifier.canvas_settings | |

## DynamicPaintSurfaces(bpy_prop_collection)

### DynamicPaintSurfaces(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. DynamicPaintSurfaces ( bpy_prop_collection )

A set of Dynamic Paint canvas surfaces

active

The Dynamic Paint surface currently on display (readonly)

Type :

DynamicPaintSurface

active_index

(in [0, inf], default 0)

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| DynamicPaintCanvasSettings.canvas_surfaces | |

## EchoModifier(StripModifier)

### EchoModifier(StripModifier)

base classes — bpy_struct, StripModifier

class bpy.types. EchoModifier ( StripModifier )

Tooltip

delay

How long the effect is delayed, in seconds (in [0.05, 5], default 0.0)

Type :

float

feedback

The effect’s feedback level (in [0, 1], default 0.0)

Type :

float

mix

The effect’s wet/dry balance (in [0, 1], default 0.0)

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

| bpy_struct.id_data StripModifier.name StripModifier.type StripModifier.mute StripModifier.enable StripModifier.show_expanded | StripModifier.input_mask_type StripModifier.mask_time StripModifier.input_mask_strip StripModifier.input_mask_id StripModifier.is_active |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values StripModifier.bl_rna_get_subclass StripModifier.bl_rna_get_subclass_py |

## EditBone(bpy_struct)

### EditBone(bpy_struct)

base class — bpy_struct

class bpy.types. EditBone ( bpy_struct )

A bone as it appears while editing an armature data-block

bbone_curveinx

Handle offset on X for where the B-Bone’s curve begins, shaping its curvature (in [-inf, inf], default 0.0)

Type :

float

bbone_curveinz

Handle offset on Z for where the B-Bone’s curve begins, shaping its curvature (in [-inf, inf], default 0.0)

Type :

float

bbone_curveoutx

Handle offset on X for where the B-Bone’s curve ends, shaping its curvature (in [-inf, inf], default 0.0)

Type :

float

bbone_curveoutz

Handle offset on Z for where the B-Bone’s curve ends, shaping its curvature (in [-inf, inf], default 0.0)

Type :

float

bbone_custom_handle_end

The bone acting as the end handle of the B-Bone curve

Type :

EditBone

bbone_custom_handle_start

The bone acting as the start handle of the B-Bone curve

Type :

EditBone

bbone_easein

How long the first Bézier Handle is (B-Bones only) (in [-inf, inf], default 1.0)

Type :

float

bbone_easeout

How long the second Bézier Handle is (B-Bones only) (in [-inf, inf], default 1.0)

Type :

float

bbone_handle_type_end

How the B-Bone’s end handle is worked out (default 'AUTO' )

- AUTO
Automatic – Derive the handle from the connected parent and children.

- ABSOLUTE
Absolute – Derive the handle from the named bone’s position.

- RELATIVE
Relative – Derive the handle from how far the named bone sits from its rest pose.

- TANGENT
Tangent – Derive the handle from the named bone’s orientation, leaving its location out.

Type :

Literal[‘AUTO’, ‘ABSOLUTE’, ‘RELATIVE’, ‘TANGENT’]

bbone_handle_type_start

How the B-Bone’s start handle is worked out (default 'AUTO' )

- AUTO
Automatic – Derive the handle from the connected parent and children.

- ABSOLUTE
Absolute – Derive the handle from the named bone’s position.

- RELATIVE
Relative – Derive the handle from how far the named bone sits from its rest pose.

- TANGENT
Tangent – Derive the handle from the named bone’s orientation, leaving its location out.

Type :

Literal[‘AUTO’, ‘ABSOLUTE’, ‘RELATIVE’, ‘TANGENT’]

bbone_handle_use_ease_end

Scale the B-Bone Ease Out channel by the end handle’s local Y scale. It happens after the Scale Easing option and that option doesn’t alter it. (default False)

Type :

bool

bbone_handle_use_ease_start

Scale the B-Bone Ease In channel by the start handle’s local Y scale. It happens after the Scale Easing option and that option doesn’t alter it. (default False)

Type :

bool

bbone_handle_use_scale_end

Scale the B-Bone Scale Out channels by the end handle’s local scale values. It happens after the Scale Easing option and that option doesn’t alter it. (array of 3 items, default (False, False, False))

Type :

bpy_prop_array[bool]

bbone_handle_use_scale_start

Scale the B-Bone Scale In channels by the start handle’s local scale values. It happens after the Scale Easing option and that option doesn’t alter it. (array of 3 items, default (False, False, False))

Type :

bpy_prop_array[bool]

bbone_mapping_mode

How vertices get assigned to B-Bone segments according to where they sit (default 'STRAIGHT' )

- STRAIGHT
Straight – A quick mapping that suits most cases but disregards the B-Bone’s rest-pose curvature.

- CURVED
Curved – A slower mapping that deforms B-Bones with heavy rest-pose curvature better.

Type :

Literal[‘STRAIGHT’, ‘CURVED’]

bbone_rollin

Roll offset at the B-Bone’s start, shaping the twist (in [-inf, inf], default 0.0)

Type :

float

bbone_rollout

Roll offset at the B-Bone’s end, shaping the twist (in [-inf, inf], default 0.0)

Type :

float

bbone_scalein

Scale factors at the B-Bone’s start, shaping thickness for tapering (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

bbone_scaleout

Scale factors at the B-Bone’s end, shaping thickness for tapering (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

bbone_segments

How many segments the bone is divided into (B-Bones only) (in [1, 32], default 0)

Type :

int

bbone_x

The B-Bone’s X size (in [-inf, inf], default 0.0)

Type :

float

bbone_z

The B-Bone’s Z size (in [-inf, inf], default 0.0)

Type :

float

collections

The Bone Collections this bone belongs to (default None, readonly)

Type :

bpy_prop_collection[BoneCollection]

color

(readonly)

Type :

BoneColor

display_type

(default 'OCTAHEDRAL' )

- `ARMATURE_DEFINED`
Armature Defined – Take the display mode from the armature (default).

- OCTAHEDRAL
Octahedral – Draw bones as octahedral shapes.

- STICK
Stick – Draw bones as plain 2D lines with dots.

- BBONE
B-Bone – Draw bones as boxes that reveal subdivision and B-Splines.

- ENVELOPE
Envelope – Draw bones as extruded spheres that reveal the deformation influence volume.

- WIRE
Wire – Draw bones as thin wires that reveal subdivision and B-Splines.

Type :

Literal[‘`ARMATURE_DEFINED`’, ‘OCTAHEDRAL’, ‘STICK’, ‘BBONE’, ‘ENVELOPE’, ‘WIRE’]

envelope_distance

How far the bone’s deformation reaches (Envelope deform only) (in [0, 1000], default 0.0)

Type :

float

envelope_weight

The bone’s deformation weight (Envelope deform only) (in [0, 1000], default 0.0)

Type :

float

head

Where the head end of the bone sits (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

head_radius

The radius at the bone’s head (Envelope deform only) (in [-inf, inf], default 0.0)

Type :

float

hide

The bone stays hidden while in Edit Mode (default False)

Type :

bool

hide_select

Whether the bone can be selected (default False)

Type :

bool

inherit_scale

How the bone takes on scaling from its parent (default 'FULL' )

- FULL
Full – Take on every effect of the parent’s scaling.

- `FIX_SHEAR`
Fix Shear – Take on the scaling but strip out shear from the child in the rest orientation.

- ALIGNED
Aligned – Spin non-uniform parent scaling into line with the child, sending parent X scale onto the child X axis and so on.

- AVERAGE
Average – Take on a uniform scale standing in for the parent’s overall change in volume.

- NONE
None – Disregard the parent’s scaling entirely.

- `NONE_LEGACY`
None (Legacy) – Disregard parent scaling without compensating for parent shear. Reproduces what turning off the old Inherit Scale checkbox did..

Type :

Literal[‘FULL’, ‘`FIX_SHEAR`’, ‘ALIGNED’, ‘AVERAGE’, ‘NONE’, ‘`NONE_LEGACY`’]

length

How long the bone is. Changing it shifts the tail end. (in [0, inf], default 0.0)

Type :

float

lock

The bone can’t be transformed while in Edit Mode (default False)

Type :

bool

matrix

Matrix pairing the bone’s location and rotation (head position, direction and roll), expressed in armature space (it leaves the bone’s length/size out) (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)))

Type :

mathutils.Matrix

name

(default “”, never None)

Type :

str

parent

The parent edit bone, within the same Armature

Type :

EditBone

roll

How far the bone is rotated about its head-tail axis (in [-inf, inf], default 0.0)

Type :

float

select

(default False)

Type :

bool

select_head

(default False)

Type :

bool

select_tail

(default False)

Type :

bool

show_wire

The bone always draws as wireframe whatever the viewport shading is (handy for unobtrusive custom bone shapes) (default False)

Type :

bool

tail

Where the tail end of the bone sits (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

tail_radius

The radius at the bone’s tail (Envelope deform only) (in [-inf, inf], default 0.0)

Type :

float

use_connect

With a parent present, the bone’s head is pinned to the parent’s tail (default False)

Type :

bool

use_cyclic_offset

With no parent present, the bone picks up cyclic offset effects (Deprecated) (default False)

Type :

bool

use_deform

Let the Bone deform geometry (default False)

Type :

bool

use_endroll_as_inroll

Fold the Start Handle bone’s Roll Out into the Roll In value (default False)

Type :

bool

use_envelope_multiply

While deforming a bone, combine Vertex Group weights with the Envelope influence by multiplying (default False)

Type :

bool

use_inherit_rotation

The bone picks up rotation or scale from its parent bone (default False)

Type :

bool

use_local_location

The bone’s location is set in local space (default False)

Type :

bool

use_relative_parent

The object’s children use a relative transform, the way deform does (default False)

Type :

bool

use_scale_easing

Scale the final easing values by the Scale In/Out Y factors (default False)

Type :

bool

basename

This bone’s name up to its first . character.

(readonly)

center

The point halfway between the head and the tail.

(readonly)

children

A list holding every one of this bone’s children.

Note

Takes O(len(bones)) time.

(readonly)

children_recursive

A list of every descendant of this bone.

Note

Takes O(len(bones)**2) time.

(readonly)

children_recursive_basename

Walks down a chain of children sharing this bone’s base name.
Only straight chains work; where multiple children share matching
base names the fork ends the walk and nothing further is returned.

Note

Takes O(len(bones)**2) time.

(readonly)

parent_recursive

A list of ancestors, beginning with the direct parent.

(readonly)

vector

The direction in which this bone points.
A convenience for (tail - head)

(readonly)

x_axis

A vector running along the bone’s x-axis.

(readonly)

y_axis

A vector running along the bone’s y-axis.

(readonly)

z_axis

A vector running along the bone’s z-axis.

(readonly)

bl_system_properties_get ( * , do_create = False )

DEBUG ONLY. A low-level way into the RNA data storage defined at runtime, meant strictly for tests and debugging. Steer clear of it in ordinary scripts, and never count on its contents being writable

Parameters :

do_create ( bool ) – Create the system properties if none exist so far (optional)

Returns :

The root container for system properties, or None when this data holds none yet and you didn’t ask for them to be created

Return type :

PropertyGroup

align_roll ( vector )

Set the bone’s local-space roll so its Z axis lines up with the supplied vector

Parameters :

vector (mathutils.Vector) – Vector, (array of 3 items, in [-inf, inf])

align_orientation ( other )

Line this bone up with another by shifting its tail and setting its roll;
the other bone’s length plays no part.

parent_index ( parent_test )

Equivalent to ‘bone in other_bone.parent_recursive’
but without building a list along the way.

transform ( matrix , * , scale = True , roll = True )

Transform the bone’s head, tail, roll and envelope
(the envelope only when the matrix carries a scale component).

Parameters :

- matrix (mathutils.Matrix) – 3x3 or 4x4 transformation matrix.

- scale ( bool ) – Scale the bone envelope by the matrix.

- roll ( bool ) – Correct the roll to point in the same relative
direction to the head and tail.

translate ( vec )

A convenience for adding vec to this bone’s head and tail.

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

| bpy.context.active_bone bpy.context.edit_bone bpy.context.editable_bones bpy.context.selected_bones bpy.context.selected_editable_bones bpy.context.visible_bones Armature.edit_bones | ArmatureEditBones.active ArmatureEditBones.new ArmatureEditBones.remove EditBone.bbone_custom_handle_end EditBone.bbone_custom_handle_start EditBone.parent |
