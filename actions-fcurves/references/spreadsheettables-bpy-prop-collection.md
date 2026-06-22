# Spreadsheettables Bpy Prop Collection, Stretchtoconstraint Constraint, Stringattribute Attribute, Stringattributevalue Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: SpreadsheetTables(bpy_prop_collection); StretchToConstraint(Constraint); StringAttribute(Attribute); StringAttributeValue(bpy_struct); StringProperty(Property); StripColorBalance(StripColorBalanceData); StripColorBalanceData(bpy_struct); StripCrop(bpy_struct); StripModifier(bpy_struct); StripModifiers(bpy_prop_collection).

## SpreadsheetTables(bpy_prop_collection)

### SpreadsheetTables(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. SpreadsheetTables ( bpy_prop_collection )

The active table plus the saved state of tables shown before

active

(readonly)

Type :

SpreadsheetTable

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

| SpaceSpreadsheet.tables | |

## StretchToConstraint(Constraint)

### StretchToConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. StretchToConstraint ( Constraint )

Stretch out to reach the target object

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

head_tail

Position of the target along the bone's length: 0 at Head, 1 at Tail (in [0, 1], default 0.0)

Type :

float

keep_axis

Which rotation type and axis ordering to apply (default '`PLANE_X`' )

- `PLANE_X`
XZ – Rotate about local X first, then Z.

- `PLANE_Z`
ZX – Rotate about local Z first, then X.

- `SWING_Y`
Swing – Apply the smallest single-axis rotation, much like Damped Track.

Type :

Literal[‘`PLANE_X`’, ‘`PLANE_Z`’, ‘`SWING_Y`’]

rest_length

Length while in the rest position (in [0, 1000], default 0.0)

Type :

float

subtarget

Vertex group of an armature bone, mesh, or lattice, … (default “”, never None)

Type :

str

target

The target object

Type :

Object

use_bbone_shape

Trace the shape of B-Bone segments when working out the Head/Tail position (default False)

Type :

bool

use_bulge_max

Apply an upper bound on volume variation (default False)

Type :

bool

use_bulge_min

Apply a lower bound on volume variation (default False)

Type :

bool

volume

Preserve the object's volume while it stretches (default '`VOLUME_XZX`' )

Type :

Literal[‘`VOLUME_XZX`’, ‘`VOLUME_X`’, ‘`VOLUME_Z`’, ‘`NO_VOLUME`’]

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

## StringAttribute(Attribute)

### StringAttribute(Attribute)

base classes — bpy_struct, Attribute

class bpy.types. StringAttribute ( Attribute )

A geometry attribute holding string values

data

(default None, readonly)

Type :

bpy_prop_collection[StringAttributeValue]

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

| bpy_struct.id_data Attribute.name Attribute.data_type Attribute.storage_type | Attribute.domain Attribute.is_internal Attribute.is_required |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Attribute.bl_rna_get_subclass Attribute.bl_rna_get_subclass_py |

## StringAttributeValue(bpy_struct)

### StringAttributeValue(bpy_struct)

base class — bpy_struct

class bpy.types. StringAttributeValue ( bpy_struct )

A string value held inside a geometry attribute

value

(default b””, never None)

Type :

bytes

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

| StringAttribute.data | |

## StringProperty(Property)

### StringProperty(Property)

base classes — bpy_struct, Property

class bpy.types. StringProperty ( Property )

Definition of an RNA property holding a text string.

default

String default value (default “”, readonly, never None)

Type :

str

length_max

Longest allowed string; a value of 0 lifts the limit (in [0, inf], default 0, readonly)

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

| bpy_struct.id_data Property.name Property.identifier Property.description Property.translation_context Property.type Property.subtype Property.srna Property.unit Property.icon Property.is_readonly Property.is_animatable Property.is_overridable Property.is_required Property.is_argument_optional Property.is_never_none Property.is_hidden | Property.is_skip_save Property.is_skip_preset Property.is_output Property.is_registered Property.is_registered_optional Property.is_runtime Property.is_enum_flag Property.is_library_editable Property.is_path_output Property.is_path_supports_blend_relative Property.is_path_supports_templates Property.is_deprecated Property.deprecated_note Property.deprecated_version Property.deprecated_removal_version Property.tags |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Property.bl_rna_get_subclass Property.bl_rna_get_subclass_py |

### References

| Struct.name_property | |

## StripColorBalance(StripColorBalanceData)

### StripColorBalance(StripColorBalanceData)

base classes — bpy_struct, StripColorBalanceData

class bpy.types. StripColorBalance ( StripColorBalanceData )

The color balance controls belonging to a sequence strip.

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

| bpy_struct.id_data StripColorBalanceData.correction_method StripColorBalanceData.lift StripColorBalanceData.gamma StripColorBalanceData.gain StripColorBalanceData.slope StripColorBalanceData.offset | StripColorBalanceData.power StripColorBalanceData.invert_lift StripColorBalanceData.invert_gamma StripColorBalanceData.invert_gain StripColorBalanceData.invert_slope StripColorBalanceData.invert_offset StripColorBalanceData.invert_power |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values StripColorBalanceData.bl_rna_get_subclass StripColorBalanceData.bl_rna_get_subclass_py |

## StripColorBalanceData(bpy_struct)

### StripColorBalanceData(bpy_struct)

base class — bpy_struct

subclasses —
StripColorBalance

class bpy.types. StripColorBalanceData ( bpy_struct )

Color balance controls for a sequence strip together with its modifiers.

correction_method

(default '`LIFT_GAMMA_GAIN`' )

- `LIFT_GAMMA_GAIN`
Lift/Gamma/Gain.

- `OFFSET_POWER_SLOPE`
Offset/Power/Slope (ASC-CDL) – ASC-CDL standard color correction.

Type :

Literal[‘`LIFT_GAMMA_GAIN`’, ‘`OFFSET_POWER_SLOPE`’]

gain

Color balance gain (highlights) (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

gamma

Color balance gamma (midtones) (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

invert_gain

Invert the gain color (default False)

Type :

bool

invert_gamma

Invert the gamma color (default False)

Type :

bool

invert_lift

Invert the lift color (default False)

Type :

bool

invert_offset

Invert the offset color (default False)

Type :

bool

invert_power

Invert the power color (default False)

Type :

bool

invert_slope

Invert the slope color (default False)

Type :

bool

lift

Color balance lift (shadows) (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

offset

Correction for entire tonal range (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

power

Correction for midtones (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

slope

Correction for highlights (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

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

| ColorBalanceModifier.color_balance | |

## StripCrop(bpy_struct)

### StripCrop(bpy_struct)

base class — bpy_struct

class bpy.types. StripCrop ( bpy_struct )

The cropping controls belonging to a sequence strip.

max_x

Number of pixels to crop from the right side (in [-inf, inf], default 0)

Type :

int

max_y

Number of pixels to crop from the top (in [-inf, inf], default 0)

Type :

int

min_x

Number of pixels to crop from the left side (in [-inf, inf], default 0)

Type :

int

min_y

Number of pixels to crop from the bottom (in [-inf, inf], default 0)

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

| EffectStrip.crop ImageStrip.crop MaskStrip.crop MetaStrip.crop | MovieClipStrip.crop MovieStrip.crop SceneStrip.crop |

## StripModifier(bpy_struct)

### StripModifier(bpy_struct)

base class — bpy_struct

subclasses —
BrightContrastModifier, ColorBalanceModifier, CurvesModifier, EchoModifier, HueCorrectModifier, MaskStripModifier, PitchModifier, SequencerCompositorModifierData, SequencerTonemapModifierData, SoundEqualizerModifier, WhiteBalanceModifier

class bpy.types. StripModifier ( bpy_struct )

A modifier applied to a sequence strip.

enable

Enable this modifier (default True)

Type :

bool

input_mask_id

Mask ID used as mask input for the modifier

Type :

Mask

input_mask_strip

Strip used as mask input for the modifier

Type :

Strip

input_mask_type

Type of input data used for mask (default 'STRIP' )

- STRIP
Strip – Use sequencer strip as mask input.

- ID
Mask – Use mask ID as mask input.

Type :

Literal[‘STRIP’, ‘ID’]

is_active

This modifier is active (default False)

Type :

bool

mask_time

Time to use for the Mask animation (default 'RELATIVE' )

- RELATIVE
Relative – Shift the mask animation so it begins at the strip’s start.

- ABSOLUTE
Absolute – Keep the mask animation locked to the scene frame.

Type :

Literal[‘RELATIVE’, ‘ABSOLUTE’]

mute

Mute this modifier (default False)

Type :

bool

name

(default “”, never None)

Type :

str

show_expanded

Mute expanded settings for the modifier (default False)

Type :

bool

type

(default '`BRIGHT_CONTRAST`' , readonly)

Type :

Literal[Strip Modifier Type Items]

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| bpy.context.strip_modifier Strip.modifiers StripModifiers.active | StripModifiers.new StripModifiers.remove |

## StripModifiers(bpy_prop_collection)

### StripModifiers(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. StripModifiers ( bpy_prop_collection )

A group of modifiers attached to a strip.

active

The active strip modifier in the list

Type :

StripModifier

new ( name , type )

Add a new modifier

Parameters :

- name ( str ) – New name for the modifier (never None)

- type (Literal[Strip Modifier Type Items]) – Modifier type to add

Returns :

Newly created modifier

Return type :

StripModifier

remove ( modifier )

Remove an existing modifier from the strip

Parameters :

modifier (StripModifier) – Modifier to remove (never None)

clear ( )

Remove all modifiers from the strip

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

| Strip.modifiers | |
