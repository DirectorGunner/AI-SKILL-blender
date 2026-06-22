# Action Id, Actionchannelbag Bpy Struct, Actionchannelbagfcurves Bpy Prop Collection, Actionchannelbaggroups Bpy Prop Collection ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Action(ID); ActionChannelbag(bpy_struct); ActionChannelbagFCurves(bpy_prop_collection); ActionChannelbagGroups(bpy_prop_collection); ActionChannelbags(bpy_prop_collection); ActionConstraint(Constraint); ActionGroup(bpy_struct); ActionKeyframeStrip(ActionStrip).

## Action(ID)

### Action(ID)

base classes — bpy_struct, ID

class bpy.types.Action(ID)

A set of F-Curves for keyframe animation

curve_frame_range

The combined frame range across all F-Curves in this action (array of 2 items, [-inf, inf], default (0.0, 0.0), readonly)

Type: mathutils.Vector

frame_end

The final frame of the manually configured playback range ([-1.04857e+06, 1.04857e+06], default 0.0)

Type: float

frame_range

The intended playback frame span of this action, using manual range if set, otherwise combining all F-Curve ranges; assignment sets the manual range (array of 2 items, [-inf, inf], default (0.0, 0.0))

Type: mathutils.Vector

frame_start

The first frame of the manually configured playback range ([-1.04857e+06, 1.04857e+06], default 0.0)

Type: float

is_action_layered

Returns whether this is a layered Action. Since version 4.4, all actions become layered through automatic upgrading, so this always returns true (default False, readonly)

Type: bool

is_action_legacy

Returns whether this is a legacy Action without layers or slots. Legacy Actions only appear on newly created empty actions, as Blender 4.4+ automatically converts them. This returns true only for unused actions (default False, readonly)

Type: bool

is_empty

False when any Layer, Slot, or legacy F-Curve exists (default False, readonly)

Type: bool

layers

A list of animation layers comprising this Action (default None, readonly)

Type: ActionLayers[ActionLayer]

pose_markers

Markers assigned to this action for identifying key poses (default None, readonly)

Type: ActionPoseMarkers[TimelineMarker]

slots

A list of slots in this Action (default None, readonly)

Type: ActionSlots[ActionSlot]

use_cyclic

This action is intended to cycle over its manually set playback range (enabling does not auto-loop; it is a hint to tools) (default False)

Type: bool

use_frame_range

Manually configure the playback frame range (used by some tools but does not affect evaluation) (default False)

Type: bool

deselect_keys()

Clear selection on all keys of the Action. F-Curve selection remains unaffected.

fcurve_ensure_for_datablock(datablock, data_path, *, index=0, group_name='')

Guarantee that an F-Curve exists for the given property path and index on the given data-block. This action must already be linked to the data-block. The function creates the layer, keyframe strip, and action slot automatically if needed, and assigns the action slot.

Parameters:

- datablock (ID) – The data-block animated by this action, for which to ensure the F-Curve exists. This action must already be assigned to the data-block (never None)

- data_path (str) – Property path for the F-Curve (never None)

- index (int) – Array index ([0, inf], optional)

- group_name (str) – Name of the group to host this F-Curve if it is newly created. Ignored if the F-Curve already exists (optional, never None)

Returns: The found or created F-Curve

Return type: FCurve

flip_with_pose(object)

Reflect the action around the X axis using a pose

Parameters:

object (Object) – The reference armature object to use when flipping (never None)

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns: The RNA type or default when not found.

Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (type | None) – The value to return when not found.

Returns: The class or default when not found.

Return type: type

### Inherited Properties

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| bpy.context.active_action bpy.context.selected_editable_actions bpy.context.selected_visible_actions ActionConstraint.action AnimData.action AnimData.action_tweak_storage BlendData.actions BlendDataActions.new | BlendDataActions.remove GLTF2_filter_action.action NlaStrip.action NlaStrips.new Pose.apply_pose_from_action Pose.backup_create Pose.blend_pose_from_action WindowManager.poselib_previous_action |

## ActionChannelbag(bpy_struct)

### ActionChannelbag(bpy_struct)

base class — bpy_struct

class bpy.types.ActionChannelbag(bpy_struct)

A collection of animation channels, typically tied to an action slot

fcurves

Individual F-Curves that animate the slot (default None, readonly)

Type: ActionChannelbagFCurves[FCurve]

groups

Sets of F-Curves for display in tools like the dopesheet and graph editor (default None, readonly)

Type: ActionChannelbagGroups[ActionGroup]

slot

The Slot for which this Channelbag holds animation data (readonly)

Type: ActionSlot

slot_handle

([-inf, inf], default 0, readonly)

Type: int

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns: The RNA type or default when not found.

Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (type | None) – The value to return when not found.

Returns: The class or default when not found.

Return type: type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| ActionChannelbags.new ActionChannelbags.remove | ActionKeyframeStrip.channelbag ActionKeyframeStrip.channelbags |

## ActionChannelbagFCurves(bpy_prop_collection)

### ActionChannelbagFCurves(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.ActionChannelbagFCurves(bpy_prop_collection)

A set of F-Curves for a specific action slot on a specific strip

new(data_path, *, index=0, group_name='')

Introduce an F-Curve into the channelbag

Parameters:

- data_path (str) – Data Path, F-Curve data path to use (never None)

- index (int) – Index, Array index ([0, inf], optional)

- group_name (str) – Group Name, Name of the Group for this F-Curve, will be created if not present yet (optional, never None)

Returns: Newly created F-Curve

Return type: FCurve

new_from_fcurve(source, *, data_path='')

Duplicate an F-Curve into the channelbag. The original F-Curve is left unchanged

Parameters:

- source (FCurve) – Source F-Curve, The F-Curve to duplicate

- data_path (str) – Data Path, F-Curve data path to use. If not provided, uses the same path as the given F-Curve (optional, never None)

Returns: Newly created F-Curve

Return type: FCurve

ensure(data_path, *, index=0, group_name='')

Retrieve the F-Curve if it exists, or create it if it does not

Parameters:

- data_path (str) – Data Path, F-Curve data path to use (never None)

- index (int) – Index, Array index ([0, inf], optional)

- group_name (str) – Group Name, Name of the Group for this F-Curve, will be created if not present yet. This parameter is ignored if the F-Curve already exists (optional, never None)

Returns: Found or newly created F-Curve

Return type: FCurve

find(data_path, *, index=0)

Scan for an F-Curve. This function performs a linear search across all F-Curves in the channelbag.

Parameters:

- data_path (str) – Data Path, F-Curve data path (never None)

- index (int) – Index, Array index ([0, inf], optional)

Returns: The found F-Curve, or None if not present

Return type: FCurve

remove(fcurve)

Erase F-Curve

Parameters:

fcurve (FCurve) – F-Curve to remove (never None)

clear()

Erase all F-Curves from this channelbag

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns: The RNA type or default when not found.

Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (type | None) – The value to return when not found.

Returns: The class or default when not found.

Return type: type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| ActionChannelbag.fcurves | |

## ActionChannelbagGroups(bpy_prop_collection)

### ActionChannelbagGroups(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.ActionChannelbagGroups(bpy_prop_collection)

A set of curve groups

new(name)

Build a new action group and insert it into the action

Parameters:

name (str) – New name for the action group (never None)

Returns: Newly created action group

Return type: ActionGroup

remove(action_group)

Erase action group

Parameters:

action_group (ActionGroup) – Action group to remove (never None)

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns: The RNA type or default when not found.

Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (type | None) – The value to return when not found.

Returns: The class or default when not found.

Return type: type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| ActionChannelbag.groups | |

## ActionChannelbags(bpy_prop_collection)

### ActionChannelbags(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.ActionChannelbags(bpy_prop_collection)

For every action slot, a set of animation channels intended for that slot

new(slot)

Insert a new channelbag into the strip to hold animation channels for a specified slot

Parameters:

slot (ActionSlot) – Action Slot, The slot that should be animated by this channelbag

Returns: Newly created channelbag

Return type: ActionChannelbag

remove(channelbag)

Erase the channelbag from the strip

Parameters:

channelbag (ActionChannelbag) – The channelbag to remove

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns: The RNA type or default when not found.

Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (type | None) – The value to return when not found.

Returns: The class or default when not found.

Return type: type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| ActionKeyframeStrip.channelbags | |

## ActionConstraint(Constraint)

### ActionConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types.ActionConstraint(Constraint)

Bind an action to the transform channels of a bone

action

The constraining action

Type: Action

action_slot

The slot identifying which subset of the Action applies to this strip; its name is used to locate the slot when a new Action is assigned

Type: ActionSlot

action_slot_handle

A number identifying which subset of the Action applies to this Action Constraint ([-inf, inf], default 0)

Type: int

action_suitable_slots

The set of action slots suitable for this NLA strip (default None, readonly)

Type: bpy_prop_collection[ActionSlot]

eval_time

Blends between Action Start and End frames ([0, 1], default 0.0)

Type: float

frame_end

The final frame of the Action to apply ([-1048574, 1048574], default 0)

Type: int

frame_start

The initial frame of the Action to apply ([-1048574, 1048574], default 0)

Type: int

last_slot_identifier

The identifier of the most recently assigned action slot. The slot identifies which subset of the Action applies to this constraint, and its identifier is used to locate the slot when a new Action is assigned. (default "", never None)

Type: str

max

Ceiling of the target channel range ([-1000, 1000], default 0.0)

Type: float

min

Floor of the target channel range ([-1000, 1000], default 0.0)

Type: float

mix_mode

Method for combining existing transformations with the action channels (default '`AFTER_FULL`')

- REPLACE
Replace – Use the action channels instead of the original transformation.

- `BEFORE_FULL`
Before Original (Full) – Apply the action channels before the original transformation, as if applied to an invisible parent in Full Inherit Scale mode. Non-uniform scale and rotation combinations can create shear.

- BEFORE
Before Original (Aligned) – Apply the action channels before the original transformation, as if applied to an invisible parent in Aligned Inherit Scale mode. Full is applied to location; Split Channels is applied to rotation and scale.

- `BEFORE_SPLIT`
Before Original (Split Channels) – Apply the action channels before the original transformation, processing location, rotation and scale independently.

- `AFTER_FULL`
After Original (Full) – Apply the action channels after the original transformation, as if applied to an invisible child in Full Inherit Scale mode. Non-uniform scale and rotation combinations can create shear.

- AFTER
After Original (Aligned) – Apply the action channels after the original transformation, as if applied to an invisible child in Aligned Inherit Scale mode. Full is applied to location; Split Channels is applied to rotation and scale.

- `AFTER_SPLIT`
After Original (Split Channels) – Apply the action channels after the original transformation, processing location, rotation and scale independently.

Type: Literal['REPLACE', '`BEFORE_FULL`', 'BEFORE', '`BEFORE_SPLIT`', '`AFTER_FULL`', 'AFTER', '`AFTER_SPLIT`']

subtarget

Bone, mesh, or lattice vertex group name, etc. (default "", never None)

Type: str

target

The target object

Type: Object

transform_channel

Which transformation channel of the target is used to control the Action (default '`ROTATION_X`')

Type: Literal['`LOCATION_X`', '`LOCATION_Y`', '`LOCATION_Z`', '`ROTATION_X`', '`ROTATION_Y`', '`ROTATION_Z`', '`SCALE_X`', '`SCALE_Y`', '`SCALE_Z`']

use_bone_object_action

On bones: apply the object's transformation channels from the action to the constrained bone, rather than the bone's own channels (default False)

Type: bool

use_eval_time

Blend between Action Start and End frames using the Evaluation Time slider instead of the Target object/bone (default False)

Type: bool

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns: The RNA type or default when not found.

Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (type | None) – The value to return when not found.

Returns: The class or default when not found.

Return type: type

### Inherited Properties

| bpy_struct.id_data Constraint.name Constraint.type Constraint.is_override_data Constraint.owner_space Constraint.target_space Constraint.space_object Constraint.space_subtarget | Constraint.mute Constraint.enabled Constraint.show_expanded Constraint.is_valid Constraint.active Constraint.influence Constraint.error_location Constraint.error_rotation |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Constraint.bl_rna_get_subclass Constraint.bl_rna_get_subclass_py |

## ActionGroup(bpy_struct)

### ActionGroup(bpy_struct)

base class — bpy_struct

class bpy.types.ActionGroup(bpy_struct)

Sets of F-Curves

channels

F-Curves belonging to this set (default None, readonly)

Type: bpy_prop_collection[FCurve]

color_set

Custom color palette to apply (default 'DEFAULT')

Type: Literal[Color Sets Items]

colors

A snapshot of colors tied to the group's color palette (readonly, never None)

Type: ThemeBoneColorSet

is_custom_color_set

Color palette is defined by the user rather than a preset theme palette (default False, readonly)

Type: bool

lock

This set is locked (default False)

Type: bool

mute

This set is silenced (default False)

Type: bool

name

(default "", never None)

Type: str

select

This set is picked (default False)

Type: bool

show_expanded

This set displays its curves except in graph editor (default False)

Type: bool

show_expanded_graph

This set displays its curves in graph editor (default False)

Type: bool

use_pin

(default False)

Type: bool

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns: The RNA type or default when not found.

Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (type | None) – The value to return when not found.

Returns: The class or default when not found.

Return type: type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| ActionChannelbag.groups ActionChannelbagGroups.new | ActionChannelbagGroups.remove FCurve.group |

## ActionKeyframeStrip(ActionStrip)

### ActionKeyframeStrip(ActionStrip)

base classes — bpy_struct, ActionStrip

class bpy.types.ActionKeyframeStrip(ActionStrip)

A strip holding F-Curves for each action slot

channelbags

(default None, readonly)

Type: ActionChannelbags[ActionChannelbag]

channelbag(slot, *, ensure=False)

Locate the ActionChannelbag for a specified Slot

Parameters:

- slot (ActionSlot) – Slot, The slot for which to locate the channelbag

- ensure (bool) – Create if necessary, Guarantee the channelbag exists for this slot, creating it if needed (optional)

Returns: Channels

Return type: ActionChannelbag

key_insert(slot, data_path, array_index, value, time)

key_insert

Parameters:

- slot (ActionSlot) – Slot, The slot that identifies which 'thing' should be keyed

- data_path (str) – Data Path, F-Curve data path (never None)

- array_index (int) – Array Index, Index of the animated array element, or -1 if the property is not an array ([-inf, inf])

- value (float) – Value to key, Value of the animated property ([-inf, inf])

- time (float) – Time of the key, Time, in frames, of the key ([-inf, inf])

Returns: Success, Whether the key was successfully inserted

Return type: bool

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns: The RNA type or default when not found.

Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (type | None) – The value to return when not found.

Returns: The class or default when not found.

Return type: type

### Inherited Properties

| bpy_struct.id_data | ActionStrip.type |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ActionStrip.bl_rna_get_subclass ActionStrip.bl_rna_get_subclass_py |
