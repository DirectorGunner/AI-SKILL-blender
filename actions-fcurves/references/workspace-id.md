# Workspace Id, Workspacetool Bpy Struct, Worldlighting Bpy Struct, Xractionmap Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: WorkSpace(ID); WorkSpaceTool(bpy_struct); WorldLighting(bpy_struct); XrActionMap(bpy_struct); XrActionMapBinding(bpy_struct); XrActionMapBindings(bpy_prop_collection); XrActionMapItem(bpy_struct); XrActionMapItems(bpy_prop_collection).

## WorkSpace(ID)

### WorkSpace(ID) 

base classes — bpy_struct, ID

class bpy.types. WorkSpace ( ID ) 

A data-block that lays out the user's working environment

active_addon 

Index of the active add-on within the Workspace add-ons filter (in [-inf, inf], default 0)

Type :

int

asset_library_reference 

Asset library currently shown in the UI; the Asset Browser tracks its own selection separately from this (default 'ALL' )

- ALL
All Libraries – Show assets from all of the listed asset libraries.

- LOCAL
Current File – Show the assets currently available in this Blender session.

- ESSENTIALS
Essentials – Show the basic building blocks and utilities coming with Blender.

- CUSTOM
Custom – Show assets from the asset libraries configured in the Preferences.

Type :

Literal[‘ALL’, ‘LOCAL’, ‘ESSENTIALS’, ‘CUSTOM’]

object_mode 

Object mode entered automatically when this workspace becomes active (default 'OBJECT' )

Type :

Literal[Workspace Object Mode Items]

owner_ids 

(default None, readonly)

Type :

wmOwnerIDs[wmOwnerID]

screens 

The screen layouts belonging to this workspace (default None, readonly)

Type :

bpy_prop_collection[Screen]

sequencer_scene 

Type :

Scene

tools 

(default None, readonly)

Type :

wmTools[WorkSpaceTool]

use_filter_by_owner 

Restrict what the UI shows according to tags (default False)

Type :

bool

use_pin_scene 

Keep track of the workspace's last scene and return to it each time the workspace is reopened (default False)

Type :

bool

use_scene_time_sync 

Drive the active scene and current time from the active scene strip (default False)

Type :

bool

classmethod status_text_set_internal ( text ) 

Write text to the status bar, usually listing modal-operator shortcuts

Parameters :

text ( str ) – Text, New string for the status bar, None clears the text

status_text_set ( text ) 

Update the status text, or pass None to clear it,
Should text be a callable, it is invoked with (header, context) as its arguments.

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References 

| BlendData.workspaces Context.workspace | Window.workspace |

## WorkSpaceTool(bpy_struct)

### WorkSpaceTool(bpy_struct) 

base class — bpy_struct

class bpy.types. WorkSpaceTool ( bpy_struct ) 

brush_type 

For brush-using tools restricted to one brush kind, the identifier of that brush kind (default 'DEFAULT' , readonly)

Type :

Literal[‘DEFAULT’]

has_datablock 

(default False, readonly)

Type :

bool

idname 

(default “”, never None)

Type :

str

idname_fallback 

(default “”, never None)

Type :

str

index 

(in [-inf, inf], default 0, readonly)

Type :

int

mode 

(default 'DEFAULT' , readonly)

Type :

Literal[‘DEFAULT’]

space_type 

(default 'EMPTY' , readonly)

Type :

Literal[Space Type Items]

use_brushes 

(default False, readonly)

Type :

bool

use_paint_canvas 

Whether the tool operates on a paint canvas (default False, readonly)

Type :

bool

widget 

(default “”, readonly, never None)

Type :

str

setup ( idname , * , cursor = 'DEFAULT' , keymap = '' , gizmo_group = '' , brush_type = '' , data_block = '' , operator = '' , index = 0 , options = set() , idname_fallback = '' , keymap_fallback = '' ) 

Configure the tool's settings

Parameters :

- idname ( str ) – Identifier, (never None)

- cursor (Literal[Window Cursor Items]) – cursor, (optional)

- keymap ( str ) – Key Map, (optional, never None)

- gizmo_group ( str ) – Gizmo Group, (optional, never None)

- brush_type ( str ) – Brush Type, Confine this tool to one kind of brush (optional)

- data_block ( str ) – Data Block, (optional, never None)

- operator ( str ) – Operator, (optional, never None)

- index ( int ) – Index, (in [-inf, inf], optional)

- options ( set [ Literal [ '`KEYMAP_FALLBACK`' , '`USE_BRUSHES`' ] ] ) – Tool Options, (optional)

- `KEYMAP_FALLBACK`
Fallback.

- `USE_BRUSHES`
Uses Brushes – Allow this tool to use brushes via the asset system.

- idname_fallback ( str ) – Fallback Identifier, (optional, never None)

- keymap_fallback ( str ) – Fallback Key Map, (optional, never None)

operator_properties ( operator ) 

operator_properties

Parameters :

operator ( str ) – (never None)

Returns :

(never None)

Return type :

OperatorProperties

gizmo_group_properties ( group ) 

gizmo_group_properties

Parameters :

group ( str ) – (never None)

Returns :

(never None)

Return type :

GizmoGroupProperties

refresh_from_context ( ) 

refresh_from_context

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

| WorkSpace.tools wmTools.from_space_image_mode wmTools.from_space_node | wmTools.from_space_sequencer wmTools.from_space_view3d_mode |

## WorldLighting(bpy_struct)

### WorldLighting(bpy_struct) 

base class — bpy_struct

class bpy.types. WorldLighting ( bpy_struct ) 

Lighting settings attached to a World data-block

ao_factor 

Blend strength used for ambient occlusion (in [0, inf], default 1.0)

Type :

float

distance 

How far the occlusion rays reach, setting the range over which other faces darken (in [0, inf], default 10.0)

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

| World.light_settings | |

## XrActionMap(bpy_struct)

### XrActionMap(bpy_struct) 

base class — bpy_struct

class bpy.types. XrActionMap ( bpy_struct ) 

actionmap_items 

Entries in the action map that tie an XR event to an operator, pose, or haptic output (default None, readonly)

Type :

XrActionMapItems[XrActionMapItem]

name 

The action map's name (default “”, never None)

Type :

str

selected_item 

(in [-32768, 32767], default 0)

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

| XrActionMaps.find XrActionMaps.new XrActionMaps.new_from_actionmap XrActionMaps.new_from_actionmap XrActionMaps.remove | XrSessionState.action_binding_create XrSessionState.action_create XrSessionState.action_set_create XrSessionState.actionmaps |

## XrActionMapBinding(bpy_struct)

### XrActionMapBinding(bpy_struct) 

base class — bpy_struct

class bpy.types. XrActionMapBinding ( bpy_struct ) 

A binding belonging to an XR action map item

axis0_region 

Which region of the first input axis triggers the action (default 'ANY' )

- ANY
Any – Use any axis region for operator execution.

- POSITIVE
Positive – Use positive axis region only for operator execution.

- NEGATIVE
Negative – Use negative axis region only for operator execution.

Type :

Literal[‘ANY’, ‘POSITIVE’, ‘NEGATIVE’]

axis1_region 

Which region of the second input axis triggers the action (default 'ANY' )

- ANY
Any – Use any axis region for operator execution.

- POSITIVE
Positive – Use positive axis region only for operator execution.

- NEGATIVE
Negative – Use negative axis region only for operator execution.

Type :

Literal[‘ANY’, ‘POSITIVE’, ‘NEGATIVE’]

component_paths 

The OpenXR component paths for this binding (default None, readonly)

Type :

XrComponentPaths[XrComponentPath]

name 

The action map binding's name (default “”, never None)

Type :

str

pose_location 

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

pose_rotation 

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Euler

profile 

The OpenXR interaction-profile path (default “”, never None)

Type :

str

threshold 

Trigger threshold for button or axis actions (in [0, 1], default 0.0)

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

| XrActionMapBindings.find XrActionMapBindings.new XrActionMapBindings.new_from_binding XrActionMapBindings.new_from_binding | XrActionMapBindings.remove XrActionMapItem.bindings XrSessionState.action_binding_create |

## XrActionMapBindings(bpy_prop_collection)

### XrActionMapBindings(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. XrActionMapBindings ( bpy_prop_collection ) 

A grouping of XR action map bindings

new ( name , replace_existing ) 

new

Parameters :

- name ( str ) – Name of the action map binding, (never None)

- replace_existing ( bool ) – Replace Existing, Swap out any binding that already carries this name

Returns :

Binding, Added action map binding

Return type :

XrActionMapBinding

new_from_binding ( binding ) 

new_from_binding

Parameters :

binding (XrActionMapBinding) – Binding, A binding to copy as a template (never None)

Returns :

Binding, Added action map binding

Return type :

XrActionMapBinding

remove ( binding ) 

remove

Parameters :

binding (XrActionMapBinding) – Binding, (never None)

find ( name ) 

find

Parameters :

name ( str ) – Name, (never None)

Returns :

Binding, The action map binding with the given name

Return type :

XrActionMapBinding

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

| XrActionMapItem.bindings | |

## XrActionMapItem(bpy_struct)

### XrActionMapItem(bpy_struct) 

base class — bpy_struct

class bpy.types. XrActionMapItem ( bpy_struct ) 

bimanual 

The action relies on the states or poses of both user paths (default False)

Type :

bool

bindings 

Bindings on this action map item that tie the action to XR input (default None, readonly)

Type :

XrActionMapBindings[XrActionMapBinding]

haptic_amplitude 

Strength of the haptic vibration, on a 0.0-to-1.0 scale (in [0, 1], default 0.0)

Type :

float

haptic_duration 

Length of the haptic pulse in seconds; 0.0 is the smallest supported value. (in [0, inf], default 0.0)

Type :

float

haptic_frequency 

Vibration frequency in hertz; 0.0 falls back to the OpenXR runtime's default. (in [0, inf], default 0.0)

Type :

float

haptic_match_user_paths 

Send haptics along the same user paths used by both the haptic action and this one (default False)

Type :

bool

haptic_mode 

When the haptics fire (default 'PRESS' )

- PRESS
Press – Apply haptics on button press.

- RELEASE
Release – Apply haptics on button release.

- `PRESS_RELEASE`
Press Release – Apply haptics on button press and release.

- REPEAT
Repeat – Apply haptics repeatedly for the duration of the button press.

Type :

Literal[‘PRESS’, ‘RELEASE’, ‘`PRESS_RELEASE`’, ‘REPEAT’]

haptic_name 

Which haptic action runs when this action fires (default “”, never None)

Type :

str

name 

The action map item's name (default “”, never None)

Type :

str

op 

Identifier of the operator invoked on an action event (default “”, never None)

Type :

str

op_mode 

When the operator runs (default 'PRESS' )

- PRESS
Press – Execute operator on button press (non-modal operators only).

- RELEASE
Release – Execute operator on button release (non-modal operators only).

- MODAL
Modal – Use modal execution (modal operators only).

Type :

Literal[‘PRESS’, ‘RELEASE’, ‘MODAL’]

op_name 

Translated name of the operator invoked on an action event (default “”, readonly, never None)

Type :

str

op_properties 

Property values passed to the operator when it runs (readonly)

Type :

OperatorProperties

pose_is_controller_aim 

Use the action poses as the VR controller aims (default False)

Type :

bool

pose_is_controller_grip 

Use the action poses as the VR controller grips (default False)

Type :

bool

selected_binding 

The binding that is active right now (in [-32768, 32767], default 0)

Type :

int

type 

Kind of action (default 'FLOAT' )

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

user_paths 

The OpenXR user paths for this item (default None, readonly)

Type :

XrUserPaths[XrUserPath]

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

| XrActionMap.actionmap_items XrActionMapItems.find XrActionMapItems.new XrActionMapItems.new_from_item | XrActionMapItems.new_from_item XrActionMapItems.remove XrSessionState.action_binding_create XrSessionState.action_create |

## XrActionMapItems(bpy_prop_collection)

### XrActionMapItems(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. XrActionMapItems ( bpy_prop_collection ) 

A grouping of XR action map items

new ( name , replace_existing ) 

new

Parameters :

- name ( str ) – Name of the action map item, (never None)

- replace_existing ( bool ) – Replace Existing, Swap out any item that already carries this name

Returns :

Item, Added action map item

Return type :

XrActionMapItem

new_from_item ( item ) 

new_from_item

Parameters :

item (XrActionMapItem) – Item, An item to copy as a template (never None)

Returns :

Item, Added action map item

Return type :

XrActionMapItem

remove ( item ) 

remove

Parameters :

item (XrActionMapItem) – Item, (never None)

find ( name ) 

find

Parameters :

name ( str ) – Name, (never None)

Returns :

Item, The action map item with the given name

Return type :

XrActionMapItem

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

| XrActionMap.actionmap_items | |
