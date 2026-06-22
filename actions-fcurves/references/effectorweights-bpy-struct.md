# Effectorweights Bpy Struct, Enumproperty Property, Enumpropertyitem Bpy Struct, Eqcurvemappingdata Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: EffectorWeights(bpy_struct); EnumProperty(Property); EnumPropertyItem(bpy_struct); EQCurveMappingData(bpy_struct); Event(bpy_struct); FCurve(bpy_struct); FCurveKeyframePoints(bpy_prop_collection).

## EffectorWeights(bpy_struct)

### EffectorWeights(bpy_struct)

base class — bpy_struct

class bpy.types. EffectorWeights ( bpy_struct )

Per-effector weighting used by physics simulation.

all

Master weight applied to every effector (in [-200, 200], default 0.0)

Type :

float

apply_to_hair_growing

Let force fields act while hair is being grown (default False)

Type :

bool

boid

Weight for the boid effector (in [-200, 200], default 0.0)

Type :

float

charge

Weight for the charge effector (in [-200, 200], default 0.0)

Type :

float

collection

Restrict which effectors apply by naming a collection

Type :

Collection

curve_guide

Weight for the curve-guide effector (in [-200, 200], default 0.0)

Type :

float

drag

Weight for the drag effector (in [-200, 200], default 0.0)

Type :

float

force

Weight for the force effector (in [-200, 200], default 0.0)

Type :

float

gravity

Weight applied to global gravity (in [-200, 200], default 0.0)

Type :

float

harmonic

Weight for the harmonic effector (in [-200, 200], default 0.0)

Type :

float

lennardjones

Weight for the Lennard-Jones effector (in [-200, 200], default 0.0)

Type :

float

magnetic

Weight for the magnetic effector (in [-200, 200], default 0.0)

Type :

float

smokeflow

Weight for the fluid-flow effector (in [-200, 200], default 0.0)

Type :

float

texture

Weight for the texture effector (in [-200, 200], default 0.0)

Type :

float

turbulence

Weight for the turbulence effector (in [-200, 200], default 0.0)

Type :

float

vortex

Weight for the vortex effector (in [-200, 200], default 0.0)

Type :

float

wind

Weight for the wind effector (in [-200, 200], default 0.0)

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

| ClothSettings.effector_weights DynamicPaintSurface.effector_weights FluidDomainSettings.effector_weights | ParticleSettings.effector_weights RigidBodyWorld.effector_weights SoftBodySettings.effector_weights |

## EnumProperty(Property)

### EnumProperty(Property)

base classes — bpy_struct, Property

class bpy.types. EnumProperty ( Property )

An RNA enumeration property whose value is selected from a fixed set of predefined options.

default

This enum's default selection (default 'DEFAULT' , readonly)

Type :

Literal[‘DEFAULT’]

default_flag

This enum's default selection (default set(), readonly)

Type :

set[Literal[‘DEFAULT’]]

enum_items

The set of values the property may take (default None, readonly)

Type :

bpy_prop_collection[EnumPropertyItem]

enum_items_static

The set of values the property may take, skipping any optional dynamic generation (default None, readonly)

Type :

bpy_prop_collection[EnumPropertyItem]

enum_items_static_ui

The set of values the property may take, skipping optional dynamic generation, and also carrying UI elements such as separators and section headings (default None, readonly)

Type :

bpy_prop_collection[EnumPropertyItem]

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

## EnumPropertyItem(bpy_struct)

### EnumPropertyItem(bpy_struct)

base class — bpy_struct

class bpy.types. EnumPropertyItem ( bpy_struct )

A single selectable choice belonging to an RNA enum property.

description

What the item is for (default “”, readonly, never None)

Type :

str

icon

The item's icon (default 'NONE' , readonly)

Type :

Literal[Icon Items]

identifier

The item's unique scripting/code name (default “”, readonly, never None)

Type :

str

name

A label meant for people to read (default “”, readonly, never None)

Type :

str

value

The item's numeric value (in [0, inf], default 0, readonly)

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

| EnumProperty.enum_items EnumProperty.enum_items_static EnumProperty.enum_items_static_ui | KeyMap.modal_event_values Struct.property_tags |

## EQCurveMappingData(bpy_struct)

### EQCurveMappingData(bpy_struct)

base class — bpy_struct

class bpy.types. EQCurveMappingData ( bpy_struct )

EQCurveMappingData

curve_mapping

(readonly)

Type :

CurveMapping

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

| SoundEqualizerModifier.graphics | SoundEqualizerModifier.new_graphic |

## Event(bpy_struct)

### Event(bpy_struct)

base class — bpy_struct

class bpy.types. Event ( bpy_struct )

An event handled by the Window Manager.

alt

Set while the Alt/Option key is being pressed (default False, readonly)

Type :

bool

ascii

The lone ASCII character tied to this event (default “”, readonly, never None)

Type :

str

ctrl

Set while the Ctrl key is being pressed (default False, readonly)

Type :

bool

direction

Movement direction, meaningful only for drag events (default 'ANY' , readonly)

Type :

Literal[Event Direction Items]

hyper

Set while the Hyper key is being pressed (default False, readonly)

Type :

bool

is_consecutive

Belongs to a trackpad or NDOF gesture broken up by cursor movement, a button, or a keypress (default False, readonly)

Type :

bool

is_mouse_absolute

Whether the most recent motion event used absolute input (default False, readonly)

Type :

bool

is_repeat

Whether the event came from a key being held down (default False, readonly)

Type :

bool

is_tablet

Whether tablet data accompanies the event (default False, readonly)

Type :

bool

mouse_prev_press_x

Horizontal location of the previous press, relative to the window (in [-inf, inf], default 0, readonly)

Type :

int

mouse_prev_press_y

Vertical location of the previous press, relative to the window (in [-inf, inf], default 0, readonly)

Type :

int

mouse_prev_x

Horizontal pointer location, relative to the window (in [-inf, inf], default 0, readonly)

Type :

int

mouse_prev_y

Vertical pointer location, relative to the window (in [-inf, inf], default 0, readonly)

Type :

int

mouse_region_x

Horizontal pointer location, relative to the region (in [-inf, inf], default 0, readonly)

Type :

int

mouse_region_y

Vertical pointer location, relative to the region (in [-inf, inf], default 0, readonly)

Type :

int

mouse_x

Horizontal pointer location measured against the window (in [-inf, inf], default 0, readonly)

Type :

int

mouse_y

Vertical pointer location measured against the window (in [-inf, inf], default 0, readonly)

Type :

int

ndof_motion

Data carried by an NDOF motion event (readonly)

Type :

NDOFMotionEventData

oskey

Set while the Cmd key is being pressed (default False, readonly)

Type :

bool

pressure

Tablet pressure, falling back to 1.0 when no tablet is in use (in [0, 1], default 1.0, readonly)

Type :

float

shift

Set while the Shift key is being pressed (default False, readonly)

Type :

bool

tilt

Tablet pressure, falling back to zeroes when no tablet is in use (array of 2 items, in [-inf, inf], default (0.0, 0.0), readonly)

Type :

mathutils.Vector

type

(default 'NONE' , readonly)

Type :

Literal[Event Type Items]

type_prev

(default 'NONE' , readonly)

Type :

Literal[Event Type Items]

unicode

The lone unicode character tied to this event (default “”, readonly, never None)

Type :

str

value

The event variety; relevant only for some events (default 'NOTHING' , readonly)

Type :

Literal[Event Value Items]

value_prev

The event variety; relevant only for some events (default 'NOTHING' , readonly)

Type :

Literal[Event Value Items]

xr

Data carried by an XR event (readonly)

Type :

XrEventData

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

| Gizmo.invoke Gizmo.modal KeyMapItems.match_event Operator.invoke Operator.modal | Window.event_simulate WindowManager.invoke_confirm WindowManager.invoke_props_popup WindowManager.piemenu_begin__internal |

## FCurve(bpy_struct)

### FCurve(bpy_struct)

base class — bpy_struct

class bpy.types. FCurve ( bpy_struct )

A function curve that drives a value over a span of time.

array_index

Where applicable, which component of the property the F-Curve drives (in [0, inf], default 0)

Type :

int

auto_smoothing

The method that computes automatic handles (default 'NONE' )

Type :

Literal[Fcurve Auto Smoothing Items]

color

The curve's display color in the Graph Editor (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

color_mode

How the F-Curve's Graph Editor color is chosen (default '`AUTO_RAINBOW`' )

- `AUTO_RAINBOW`
Auto Rainbow – Step through the rainbow so that every curve tends to get its own color.

- `AUTO_RGB`
Auto XYZ to RGB – Apply axis colors to transform and color properties, falling back to auto-rainbow elsewhere.

- `AUTO_YRGB`
Auto WXYZ to YRGB – Apply WXYZ axis colors to quaternion/axis-angle rotations, XYZ axis colors to other transform and color properties, and auto-rainbow for everything else.

- CUSTOM
User Defined – Apply a color you picked yourself for the F-Curve.

Type :

Literal[‘`AUTO_RAINBOW`’, ‘`AUTO_RGB`’, ‘`AUTO_YRGB`’, ‘CUSTOM’]

data_path

RNA path of the property the F-Curve drives (default “”, never None)

Type :

str

driver

The channel's driver, present only on Driver F-Curves (readonly)

Type :

Driver

extrapolation

How the F-Curve value is computed beyond the first and last keyframes (default 'CONSTANT' )

- CONSTANT
Constant – Hold the values of the endpoint keyframes.

- LINEAR
Linear – Continue along the curve's slope as it enters/leaves the endpoint keyframes.

Type :

Literal[‘CONSTANT’, ‘LINEAR’]

group

The Action Group this F-Curve is part of

Type :

ActionGroup

hide

Hide the F-Curve and its keyframes from the Graph Editor graphs (default True)

Type :

bool

is_empty

True when the curve adds no animation, for lack of keyframes or useful modifiers, and is safe to delete (default False, readonly)

Type :

bool

is_valid

False once the F-Curve has failed to evaluate, so it gets skipped during evaluation (default True)

Type :

bool

keyframe_points

The keyframes the user can edit (default None, readonly)

Type :

FCurveKeyframePoints[Keyframe]

lock

Block editing of the F-Curve's settings (default False)

Type :

bool

modifiers

The modifiers that reshape the F-Curve (default None, readonly)

Type :

FCurveModifiers[FModifier]

mute

Turn off evaluation of the F-Curve (default False)

Type :

bool

sampled_points

Animation stored as samples (default None, readonly)

Type :

bpy_prop_collection[FCurveSample]

select

Whether the F-Curve is picked for editing (default False)

Type :

bool

evaluate ( frame )

Evaluate F-Curve

Parameters :

frame ( float ) – Frame, Evaluate F-Curve at given frame (in [-inf, inf])

Returns :

Value, Value of F-Curve specific frame (in [-inf, inf])

Return type :

float

update ( )

Ensure keyframes are sorted in chronological order and handles are set correctly

range ( )

Get the time extents for F-Curve

Returns :

Range, Min/Max values (array of 2 items, in [-inf, inf])

Return type :

mathutils.Vector

update_autoflags ( data )

Refresh the FCurve flags that are derived automatically from the property it drives (for instance, the integer/discrete flags raised when that property is not a float)

Parameters :

data (AnyType) – Data, Data containing the property controlled by given FCurve (never None)

convert_to_samples ( start , end )

Turn this FCurve's keyframes into sample points where needed

Parameters :

- start ( int ) – Start Frame, (in [-1048574, 1048574])

- end ( int ) – End Frame, (in [-1048574, 1048574])

convert_to_keyframes ( start , end )

Turn this FCurve's sample points back into keyframes via linear interpolation, where needed

Parameters :

- start ( int ) – Start Frame, (in [-1048574, 1048574])

- end ( int ) – End Frame, (in [-1048574, 1048574])

bake ( start , end , * , step = 1.0 , remove = '`IN_RANGE`' )

Drop keys at regular spacing along the curve as it already stands.

Parameters :

- start ( int ) – Start Frame, Frame at which to start baking (in [-1048574, 1048574])

- end ( int ) – End Frame, Frame at which to end baking (inclusive) (in [-1048574, 1048574])

- step ( float ) – Step, At which interval to add keys (in [0.01, inf], optional)

- remove ( Literal [ 'NONE' , '`IN_RANGE`' , '`OUT_RANGE`' , 'ALL' ] ) – Remove Options, Choose which keys should be automatically removed by the bake (optional)

- NONE
None – Hold on to every key.

- `IN_RANGE`
In Range – Drop every key falling inside the chosen range.

- `OUT_RANGE`
Outside Range – Drop every key falling outside the chosen range.

- ALL
All – Drop every key that already exists.

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

| bpy.context.active_editable_fcurve bpy.context.editable_fcurves bpy.context.selected_editable_fcurves bpy.context.selected_visible_fcurves bpy.context.visible_fcurves Action.fcurve_ensure_for_datablock ActionChannelbag.fcurves ActionChannelbagFCurves.ensure ActionChannelbagFCurves.find ActionChannelbagFCurves.new ActionChannelbagFCurves.new_from_fcurve | ActionChannelbagFCurves.new_from_fcurve ActionChannelbagFCurves.remove ActionGroup.channels AnimData.drivers AnimDataDrivers.find AnimDataDrivers.from_existing AnimDataDrivers.from_existing AnimDataDrivers.new AnimDataDrivers.remove NlaStrip.fcurves NlaStripFCurves.find |

## FCurveKeyframePoints(bpy_prop_collection)

### FCurveKeyframePoints(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. FCurveKeyframePoints ( bpy_prop_collection )

A set of keyframe points.

insert ( frame , value , * , options = set() , keyframe_type = 'KEYFRAME' )

Add a keyframe point to a F-Curve

Parameters :

- frame ( float ) – X Value of this keyframe point (in [-inf, inf])

- value ( float ) – Y Value of this keyframe point (in [-inf, inf])

- options ( set [ Literal [ 'REPLACE' , 'NEEDED' , 'FAST' ] ] ) – Keyframe options (optional)

- REPLACE
Replace – Create no fresh keyframes; only overwrite ones already present.

- NEEDED
Needed – Insert a keyframe only where one is actually required.

- FAST
Fast – Insert keyframes quickly by skipping a curve recalculation on each insert.

- keyframe_type (Literal[Beztriple Keyframe Type Items]) – Type of keyframe to insert (optional)

Returns :

Newly created keyframe

Return type :

Keyframe

add ( count )

Add a keyframe point to a F-Curve

Parameters :

count ( int ) – Number, Number of points to add to the spline (in [0, inf])

remove ( keyframe , * , fast = False )

Remove keyframe from an F-Curve

Parameters :

- keyframe (Keyframe) – Keyframe to remove (never None)

- fast ( bool ) – Fast, Remove keyframes quickly by skipping a curve recalculation each time (optional)

clear ( )

Remove all keyframes from an F-Curve

sort ( )

Ensure all keyframe points are chronologically sorted

deduplicate ( )

Drop any duplicate keys, on the assumption the points are already sorted

handles_recalc ( )

Refresh handles after the keyframe points change, so things like auto-clamping stay correct

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

| FCurve.keyframe_points | |
