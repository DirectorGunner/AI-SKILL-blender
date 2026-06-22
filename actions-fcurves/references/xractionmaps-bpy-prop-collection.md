# Xractionmaps Bpy Prop Collection, Xrcomponentpath Bpy Struct, Xrcomponentpaths Bpy Prop Collection, Xreventdata Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: XrActionMaps(bpy_prop_collection); XrComponentPath(bpy_struct); XrComponentPaths(bpy_prop_collection); XrEventData(bpy_struct); XrSessionState(bpy_struct); XrUserPath(bpy_struct); XrUserPaths(bpy_prop_collection).

## XrActionMaps(bpy_prop_collection)

### XrActionMaps(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. XrActionMaps ( bpy_prop_collection ) 

A grouping of XR action maps

classmethod new ( xr_session_state , name , replace_existing ) 

new

Parameters :

- xr_session_state (XrSessionState) – XR Session State, (never None)

- name ( str ) – Name, (never None)

- replace_existing ( bool ) – Replace Existing, Swap out any actionmap that already carries this name

Returns :

Action Map, Added action map

Return type :

XrActionMap

classmethod new_from_actionmap ( xr_session_state , actionmap ) 

new_from_actionmap

Parameters :

- xr_session_state (XrSessionState) – XR Session State, (never None)

- actionmap (XrActionMap) – Action Map, An action map to copy as a template (never None)

Returns :

Action Map, Added action map

Return type :

XrActionMap

classmethod remove ( xr_session_state , actionmap ) 

remove

Parameters :

- xr_session_state (XrSessionState) – XR Session State, (never None)

- actionmap (XrActionMap) – Action Map, Removed action map (never None)

classmethod find ( xr_session_state , name ) 

find

Parameters :

- xr_session_state (XrSessionState) – XR Session State, (never None)

- name ( str ) – Name, (never None)

Returns :

Action Map, The action map with the given name

Return type :

XrActionMap

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

| XrSessionState.actionmaps | |

## XrComponentPath(bpy_struct)

### XrComponentPath(bpy_struct) 

base class — bpy_struct

class bpy.types. XrComponentPath ( bpy_struct ) 

path 

An OpenXR component path (default “”, never None)

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

| XrActionMapBinding.component_paths XrComponentPaths.find | XrComponentPaths.new XrComponentPaths.remove |

## XrComponentPaths(bpy_prop_collection)

### XrComponentPaths(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. XrComponentPaths ( bpy_prop_collection ) 

A grouping of OpenXR component paths

new ( path ) 

new

Parameters :

path ( str ) – Path, OpenXR component path (never None)

Returns :

Component Path, Added component path

Return type :

XrComponentPath

remove ( component_path ) 

remove

Parameters :

component_path (XrComponentPath) – Component Path, (never None)

find ( path ) 

find

Parameters :

path ( str ) – Path, OpenXR component path (never None)

Returns :

Component Path, The component path with the given path

Return type :

XrComponentPath

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

| XrActionMapBinding.component_paths | |

## XrEventData(bpy_struct)

### XrEventData(bpy_struct) 

base class — bpy_struct

class bpy.types. XrEventData ( bpy_struct ) 

XR payload carried by a Window Manager event

action 

The XR action's name (default “”, readonly, never None)

Type :

str

action_set 

The XR action set's name (default “”, readonly, never None)

Type :

str

bimanual 

Whether this is a two-handed interaction (default False, readonly)

Type :

bool

controller_location 

World-space position of the controller aim tied to the action (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

controller_location_other 

Aim position of the other user path during bimanual actions (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

controller_rotation 

World-space orientation of the controller aim tied to the action (array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0), readonly)

Type :

mathutils.Quaternion

controller_rotation_other 

Aim orientation of the other user path during bimanual actions (array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0), readonly)

Type :

mathutils.Quaternion

float_threshold 

Trigger threshold for float or 2D-vector actions (in [-inf, inf], default 0.0, readonly)

Type :

float

state 

The XR action values for the given type (array of 2 items, in [-inf, inf], default (0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

state_other 

State of the other user path during bimanual actions (array of 2 items, in [-inf, inf], default (0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

type 

The XR action's kind (default 'FLOAT' , readonly)

- FLOAT
Float – Float action, representing either a digital or analog button.

- VECTOR2D
Vector2D – 2D float vector action, representing a thumbstick or trackpad.

- POSE
Pose – 3D pose action, representing a controller’s location and rotation.

- VIBRATION
Vibration – Haptic vibration output action, to be applied with a duration, frequency, and amplitude.

Type :

Literal[‘FLOAT’, ‘VECTOR2D’, ‘POSE’, ‘VIBRATION’]

user_path 

The action's user path. E.g. “/user/hand/left” (default “”, readonly, never None)

Type :

str

user_path_other 

The second user path, used by bimanual actions. E.g. “/user/hand/right” (default “”, readonly, never None)

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

| Event.xr | |

## XrSessionState(bpy_struct)

### XrSessionState(bpy_struct) 

base class — bpy_struct

class bpy.types. XrSessionState ( bpy_struct ) 

Live state details for the current VR session

actionmaps 

(default None, readonly)

Type :

XrActionMaps[XrActionMap]

active_actionmap 

(in [-inf, inf], default 0)

Type :

int

navigation_location 

Positional offset added to the base pose when working out the viewer's location (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

navigation_rotation 

Rotational offset added to the base pose when working out the viewer's rotation (array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

mathutils.Quaternion

navigation_scale 

Scale multiplier used when working out the viewer's scale (in [-inf, inf], default 0.0)

Type :

float

selected_actionmap 

(in [-inf, inf], default 0)

Type :

int

viewer_pose_location 

Most recent world-space location of the viewer pose (midpoint between the eyes) (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

viewer_pose_rotation 

Most recent world-space rotation of the viewer pose (midpoint between the eyes) (array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0), readonly)

Type :

mathutils.Quaternion

viewer_scale 

VR viewer scale, derived from the navigation scale, the view-scale session setting, and the active scene's unit scale (in [-inf, inf], default 0.0, readonly)

Type :

float

classmethod is_running ( context ) 

Check whether the VR session is active

Parameters :

context (Context) – (never None)

Returns :

Result

Return type :

bool

classmethod reset_to_base_pose ( context ) 

Clear the accumulated position and rotation deltas

Parameters :

context (Context) – (never None)

classmethod action_set_create ( context , actionmap ) 

Create a VR action set

Parameters :

- context (Context) – (never None)

- actionmap (XrActionMap) – (never None)

Returns :

Result

Return type :

bool

classmethod action_create ( context , actionmap , actionmap_item ) 

Create a VR action

Parameters :

- context (Context) – (never None)

- actionmap (XrActionMap) – (never None)

- actionmap_item (XrActionMapItem) – (never None)

Returns :

Result

Return type :

bool

classmethod action_binding_create ( context , actionmap , actionmap_item , actionmap_binding ) 

Create a VR action binding

Parameters :

- context (Context) – (never None)

- actionmap (XrActionMap) – (never None)

- actionmap_item (XrActionMapItem) – (never None)

- actionmap_binding (XrActionMapBinding) – (never None)

Returns :

Result

Return type :

bool

classmethod active_action_set_set ( context , action_set ) 

Set the active VR action set

Parameters :

- context (Context) – (never None)

- action_set ( str ) – Action Set, Action set name (never None)

Returns :

Result

Return type :

bool

classmethod controller_pose_actions_set ( context , action_set , grip_action , aim_action ) 

Choose the actions that drive the VR controller poses

Parameters :

- context (Context) – (never None)

- action_set ( str ) – Action Set, Action set name (never None)

- grip_action ( str ) – Grip Action, Name of the action representing the controller grips (never None)

- aim_action ( str ) – Aim Action, Name of the action representing the controller aims (never None)

Returns :

Result

Return type :

bool

classmethod action_state_get ( context , action_set_name , action_name , user_path ) 

Read the current state of a VR action

Parameters :

- context (Context) – (never None)

- action_set_name ( str ) – Action Set, Action set name (never None)

- action_name ( str ) – Action, Action name (never None)

- user_path ( str ) – User Path, OpenXR user path (never None)

Returns :

Action State, Current state of the VR action. Second float value is only set for 2D vector type actions. (array of 2 items, in [-inf, inf], never None)

Return type :

bpy_prop_array[float]

classmethod haptic_action_apply ( context , action_set_name , action_name , user_path , duration , frequency , amplitude ) 

Trigger a VR haptic action

Parameters :

- context (Context) – (never None)

- action_set_name ( str ) – Action Set, Action set name (never None)

- action_name ( str ) – Action, Action name (never None)

- user_path ( str ) – User Path, Optional OpenXR user path. If not set, the action will be applied to all paths. (never None)

- duration ( float ) – Duration, Haptic duration in seconds. 0.0 is the minimum supported duration. (in [0, inf])

- frequency ( float ) – Frequency, Frequency of the haptic vibration in hertz. 0.0 specifies the OpenXR runtime’s default frequency. (in [0, inf])

- amplitude ( float ) – Amplitude, Haptic amplitude, ranging from 0.0 to 1.0 (in [0, 1])

Returns :

Result

Return type :

bool

classmethod haptic_action_stop ( context , action_set_name , action_name , user_path ) 

Halt a VR haptic action

Parameters :

- context (Context) – (never None)

- action_set_name ( str ) – Action Set, Action set name (never None)

- action_name ( str ) – Action, Action name (never None)

- user_path ( str ) – User Path, Optional OpenXR user path. If not set, the action will be stopped for all paths. (never None)

classmethod controller_grip_location_get ( context , index ) 

Read the most recent world-space controller grip location

Parameters :

- context (Context) – (never None)

- index ( int ) – Index, Controller index (in [0, 255])

Returns :

Location, Controller grip location (array of 3 items, in [-inf, inf], never None)

Return type :

mathutils.Vector

classmethod controller_grip_rotation_get ( context , index ) 

Read the most recent world-space controller grip rotation (quaternion)

Parameters :

- context (Context) – (never None)

- index ( int ) – Index, Controller index (in [0, 255])

Returns :

Rotation, Controller grip quaternion rotation (array of 4 items, in [-inf, inf], never None)

Return type :

mathutils.Quaternion

classmethod controller_aim_location_get ( context , index ) 

Read the most recent world-space controller aim location

Parameters :

- context (Context) – (never None)

- index ( int ) – Index, Controller index (in [0, 255])

Returns :

Location, Controller aim location (array of 3 items, in [-inf, inf], never None)

Return type :

mathutils.Vector

classmethod controller_aim_rotation_get ( context , index ) 

Read the most recent world-space controller aim rotation (quaternion)

Parameters :

- context (Context) – (never None)

- index ( int ) – Index, Controller index (in [0, 255])

Returns :

Rotation, Controller aim quaternion rotation (array of 4 items, in [-inf, inf], never None)

Return type :

mathutils.Quaternion

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

| WindowManager.xr_session_state XrActionMaps.find XrActionMaps.new | XrActionMaps.new_from_actionmap XrActionMaps.remove |

## XrUserPath(bpy_struct)

### XrUserPath(bpy_struct) 

base class — bpy_struct

class bpy.types. XrUserPath ( bpy_struct ) 

path 

An OpenXR user path (default “”, never None)

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

| XrActionMapItem.user_paths XrUserPaths.find | XrUserPaths.new XrUserPaths.remove |

## XrUserPaths(bpy_prop_collection)

### XrUserPaths(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. XrUserPaths ( bpy_prop_collection ) 

A grouping of OpenXR user paths

new ( path ) 

new

Parameters :

path ( str ) – Path, OpenXR user path (never None)

Returns :

User Path, Added user path

Return type :

XrUserPath

remove ( user_path ) 

remove

Parameters :

user_path (XrUserPath) – User Path, (never None)

find ( path ) 

find

Parameters :

path ( str ) – Path, OpenXR user path (never None)

Returns :

User Path, The user path with the given path

Return type :

XrUserPath

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

| XrActionMapItem.user_paths | |
