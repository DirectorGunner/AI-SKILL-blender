# Keyframe Bpy Struct, Keyingset Bpy Struct, Keyingsetinfo Bpy Struct, Keyingsetpath Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Keyframe(bpy_struct); KeyingSet(bpy_struct); KeyingSetInfo(bpy_struct); KeyingSetPath(bpy_struct); KeyingSetPaths(bpy_prop_collection); KeyingSets(bpy_prop_collection); KeyingSetsAll(bpy_prop_collection); KeyMap(bpy_struct).

## Keyframe(bpy_struct)

### Keyframe(bpy_struct)

base class — bpy_struct

class bpy.types. Keyframe ( bpy_struct )

A Bézier curve point, with two handles, that marks a Keyframe on an F-Curve.

amplitude

How much to boost the elastic bounces for ‘elastic’ easing (in [0, inf], default 0.0)

Type :

float

back

How much overshoot to allow for ‘back’ easing (in [-inf, inf], default 0.0)

Type :

float

co

The control point's coordinates (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

co_ui

The control point's coordinates. Note: changing this also moves the handles, as the graph editor transform operator does (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

easing

Which ends of the segment between this keyframe and the next get the easing interpolation (default 'AUTO' )

Type :

Literal[Beztriple Interpolation Easing Items]

handle_left

The left handle's coordinates (before the control point) (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

handle_left_type

The handle types (default 'FREE' )

Type :

Literal[Keyframe Handle Type Items]

handle_right

The right handle's coordinates (after the control point) (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

handle_right_type

The handle types (default 'FREE' )

Type :

Literal[Keyframe Handle Type Items]

interpolation

The interpolation method for the F-Curve segment running from this Keyframe to the next (default 'CONSTANT' )

Type :

Literal[Beztriple Interpolation Mode Items]

period

The time between bounces for elastic easing (in [-inf, inf], default 0.0)

Type :

float

select_control_point

Whether the control point is selected (default False)

Type :

bool

select_left_handle

Whether the left handle is selected (default False)

Type :

bool

select_right_handle

Whether the right handle is selected (default False)

Type :

bool

type

The keyframe's type (a purely visual distinction) (default 'KEYFRAME' )

Type :

Literal[Beztriple Keyframe Type Items]

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

| bpy.context.selected_editable_keyframes FCurve.keyframe_points | FCurveKeyframePoints.insert FCurveKeyframePoints.remove |

## KeyingSet(bpy_struct)

### KeyingSet(bpy_struct)

base class — bpy_struct

class bpy.types. KeyingSet ( bpy_struct )

A group of settings meant to be keyframed at once.

bl_description

A brief description of the keying set (default “”, never None)

Type :

str

bl_idname

When set, the Keying Set is given a custom ID; otherwise it inherits the name of the class that defines it (for instance, with a class named “`BUILTIN_KSI`_location” and no bl_idname set by the script, bl_idname becomes “`BUILTIN_KSI`_location”) (default “”, never None)

Type :

str

bl_label

(default “”, never None)

Type :

str

is_path_absolute

The Keying Set names explicit paths/settings to keyframe (i.e. it does not depend on context info) (default False, readonly)

Type :

bool

paths

The Keying Set Paths that name the settings keyframed together (default None, readonly)

Type :

KeyingSetPaths[KeyingSetPath]

type_info

The callback function definitions for built-in Keying Sets (readonly)

Type :

KeyingSetInfo

use_insertkey_needed

Add keyframes only on the F-Curves that actually need them (default False)

Type :

bool

use_insertkey_override_needed

Override the default so keyframes go only on the F-Curves that need them (default False)

Type :

bool

use_insertkey_override_visual

Override the default so keyframes are taken from ‘visual transforms’ (default False)

Type :

bool

use_insertkey_visual

Take keyframes from ‘visual transforms’ (default False)

Type :

bool

refresh ( )

Refresh the Keying Set so it stays valid in the current context (run it ahead of each use).

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

| KeyingSetInfo.generate KeyingSetInfo.iterator KeyingSets.active KeyingSets.new | KeyingSetsAll.active Scene.keying_sets Scene.keying_sets_all |

## KeyingSetInfo(bpy_struct)

### KeyingSetInfo(bpy_struct)

base class — bpy_struct

class bpy.types. KeyingSetInfo ( bpy_struct )

The callback function definitions for builtin Keying Sets.

bl_description

A brief description of the keying set (default “”, never None)

Type :

str

bl_idname

When set, the Keying Set is given a custom ID; otherwise it inherits the name of the class that defines it (for instance, with a class named “`BUILTIN_KSI`_location” and no bl_idname set by the script, bl_idname becomes “`BUILTIN_KSI`_location”) (default “”, never None)

Type :

str

bl_label

(default “”, never None)

Type :

str

bl_options

The Keying Set options applied while inserting keyframes (default set())

Type :

set[Literal[Keying Flag Items]]

poll ( context )

Check whether the Keying Set is usable.

Return type :

bool

iterator ( context , ks )

Invoke generate() on the structs whose properties are to be keyframed.

generate ( context , ks , data )

Add Paths to the Keying Set so the given data's properties get keyframed.

Parameters :

data (AnyType) – (never None)

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

| KeyingSet.type_info | |

## KeyingSetPath(bpy_struct)

### KeyingSetPath(bpy_struct) 

base class — bpy_struct

class bpy.types. KeyingSetPath ( bpy_struct ) 

Points at a single setting that a Keying Set targets

array_index 

For settings that apply, this selects which individual entry is used (in [-inf, inf], default 0)

Type :

int

data_path 

RNA path identifying the property being keyed (default “”, never None)

Type :

str

group 

Action Group name that this path's keyframes get filed under (default “”, never None)

Type :

str

group_method 

Chooses how the Group name for this path is determined (default 'NAMED' )

Type :

Literal[Keyingset Path Grouping Items]

id 

The ID-Block whose keyframes the Keying Set writes to (relevant only for Absolute Keying Sets)

Type :

ID

id_type 

Which kind of ID-block is permitted here (default 'OBJECT' )

Type :

Literal[Id Type Items]

use_entire_array 

For an 'array/vector' property such as Location, Rotation, or Color, key the whole array at once (default False)

Type :

bool

use_insertkey_needed 

Restrict insertion to the F-Curves that actually require a new keyframe (default False)

Type :

bool

use_insertkey_override_needed 

Replace the default so that keyframes go only where the relevant F-Curves call for them (default False)

Type :

bool

use_insertkey_override_visual 

Replace the default so that keyframes capture 'visual transforms' (default False)

Type :

bool

use_insertkey_visual 

Record keyframes from 'visual transforms' (default False)

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

### References 

| KeyingSet.paths KeyingSetPaths.active | KeyingSetPaths.add KeyingSetPaths.remove |

## KeyingSetPaths(bpy_prop_collection)

### KeyingSetPaths(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. KeyingSetPaths ( bpy_prop_collection ) 

The set of paths held by a keying set

active 

The currently active Keying Set used when inserting or deleting keyframes

Type :

KeyingSetPath

active_index 

Index of the Keying Set in use right now (in [-inf, inf], default 0)

Type :

int

add ( target_id , data_path , * , index = -1 , group_method = 'KEYINGSET' , group_name = '' ) 

Register an additional path on the Keying Set

Parameters :

- target_id (ID) – Target ID, ID data-block for the destination

- data_path ( str ) – Data-Path, RNA-Path to destination property (never None)

- index ( int ) – Index, The index of the destination property (i.e. axis of Location/Rotation/etc.), or -1 for the entire array (in [-1, inf], optional)

- group_method (Literal[Keyingset Path Grouping Items]) – Grouping Method, Method used to define which Group-name to use (optional)

- group_name ( str ) – Group Name, Name of Action Group to assign destination to (only if grouping mode is to use this name) (optional, never None)

Returns :

New Path, Path created and added to the Keying Set

Return type :

KeyingSetPath

remove ( path ) 

Take the specified path out of the Keying Set

Parameters :

path (KeyingSetPath) – Path, (never None)

clear ( ) 

Drop every path the Keying Set holds

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

| KeyingSet.paths | |

## KeyingSets(bpy_prop_collection)

### KeyingSets(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. KeyingSets ( bpy_prop_collection ) 

The keying sets belonging to a scene

active 

The currently active Keying Set used when inserting or deleting keyframes

Type :

KeyingSet

active_index 

Index of the Keying Set in use right now (negative values mean 'builtin', positive ones mean 'absolute') (in [-inf, inf], default 0)

Type :

int

new ( * , idname = 'KeyingSet' , name = 'KeyingSet' ) 

Create a fresh Keying Set on the Scene

Parameters :

- idname ( str ) – IDName, Internal identifier of Keying Set (optional, never None)

- name ( str ) – Name, User visible name of Keying Set (optional, never None)

Returns :

Newly created Keying Set

Return type :

KeyingSet

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

| Scene.keying_sets | |

## KeyingSetsAll(bpy_prop_collection)

### KeyingSetsAll(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. KeyingSetsAll ( bpy_prop_collection ) 

Every keying set that can be used

active 

The currently active Keying Set used when inserting or deleting keyframes

Type :

KeyingSet

active_index 

Index of the Keying Set in use right now (negative values mean 'builtin', positive ones mean 'absolute') (in [-inf, inf], default 0)

Type :

int

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

| Scene.keying_sets_all | |

## KeyMap(bpy_struct)

### KeyMap(bpy_struct) 

base class — bpy_struct

class bpy.types. KeyMap ( bpy_struct ) 

Holds an input setup together with its keymaps

bl_owner_id 

Owner used internally (default “”, never None)

Type :

str

is_modal 

Marks the keymap as one that converts modal events for an operator (default False, readonly)

Type :

bool

is_user_modified 

Set when the user has authored this keymap (default False)

Type :

bool

keymap_items 

The entries of the keymap, each tying an operator to an input event (default None, readonly)

Type :

KeyMapItems[KeyMapItem]

modal_event_values 

Exposes the event values available to items of this modal keymap (#KeyMapItem.propvalue), intended for API introspection (default None, readonly)

Type :

bpy_prop_collection[EnumPropertyItem]

name 

The key map's name (default “”, readonly, never None)

Type :

str

region_type 

If set, the region type this keymap belongs to (default 'WINDOW' , readonly)

Type :

Literal[Region Type Items]

show_expanded_children 

Whether children are unfolded in the interface (default False)

Type :

bool

show_expanded_items 

Whether the entry is unfolded in the interface (default False)

Type :

bool

space_type 

If set, the space type this keymap belongs to (default 'EMPTY' , readonly)

Type :

Literal[Space Type Items]

active ( ) 

active

Returns :

Key Map, Active key map

Return type :

KeyMap

restore_to_default ( ) 

restore_to_default

restore_item_to_default ( item ) 

restore_item_to_default

Parameters :

item (KeyMapItem) – Item, (never None)

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

| GizmoGroup.setup_keymap KeyConfig.keymaps KeyConfigurations.find_item_from_operator KeyMap.active KeyMapItems.find_match KeyMaps.find | KeyMaps.find_match KeyMaps.find_match KeyMaps.find_modal KeyMaps.new KeyMaps.remove WindowManager.popover_end__internal |
