# Anim Operators

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

### Anim Operators

bpy.ops.anim. change_frame ( * , frame = 0.0 , snap = False , seq_solo_preview = False , pass_through_on_strip_handles = False )

Adjust the playhead timeline position interactively.

Parameters :

- frame ( float ) – Frame, (in [-1.04857e+06, 1.04857e+06], optional)

- snap ( bool ) – Snap, (optional)

- seq_solo_preview ( bool ) – Strip Preview, (optional)

- pass_through_on_strip_handles ( bool ) – Pass Through on Strip Handles, Permit another operator to act on strip handles (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channel_select_keys ( * , extend = False )

Activate every keyframe in the channel at the cursor.

Parameters :

extend ( bool ) – Extend, Widen the selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channel_view_pick ( * , include_handles = True , use_preview_range = True )

Center the view on the channel beneath the cursor.

Parameters :

- include_handles ( bool ) – Include Handles, Factor keyframe handle extents into viewport bounds (optional)

- use_preview_range ( bool ) – Use Preview Range, Disregard frames beyond the playback window (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_bake ( * , use_scene_range = True , range = (0, 0) , step = 1.0 , remove_outside_range = False , interpolation_type = 'BEZIER' , bake_modifiers = True )

Generate keys matching the present F-Curve shape across chosen channels.

Parameters :

- use_scene_range ( bool ) – Use Scene Range, If enabled, the scene start and end frame will be used to determine the bake range (optional)

- range ( Sequence [ int ] ) – Frame Range, The custom range in which to create new keys. Only used when not using the scene range (array of 2 items, in [-inf, inf], optional)

- step ( float ) – Frame Step, At which interval to add keys (in [0.01, inf], optional)

- remove_outside_range ( bool ) – Remove Outside Range, Removes keys outside the given range, leaving only the newly baked (optional)

- interpolation_type ( Literal [ 'BEZIER' , 'LIN' , 'CONST' ] ) – Interpolation Type, Choose the interpolation type with which new keys will be added (optional)

- BEZIER
Bézier – New keys will be Bézier.

- LIN
Linear – New keys will be linear.

- CONST
Constant – New keys will be constant.

- bake_modifiers ( bool ) – Bake Modifiers, Bake Modifiers into keyframes and delete them after (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_clean_empty ( )

Purge vacant animation containers from displayed data-blocks.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_click ( * , extend = False , extend_range = False , children_only = False )

Manage cursor interactions over timeline channels.

Parameters :

- extend ( bool ) – Extend Select, (optional)

- extend_range ( bool ) – Extend Range, Selection of active channel to clicked channel (optional)

- children_only ( bool ) – Select Children Only, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_collapse ( * , all = True )

Fold closed all expandable animation channels that are active.

Parameters :

all ( bool ) – All, Collapse all channels (not just selected ones) (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_delete ( )

Purge every selected animation channel.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_editable_toggle ( * , mode = 'TOGGLE' , type = 'PROTECT' )

Switch the editability state of active channels.

Parameters :

- mode ( Literal [ 'TOGGLE' , 'DISABLE' , 'ENABLE' , 'INVERT' ] ) – Mode, (optional)

- type ( Literal [ 'PROTECT' , 'MUTE' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_expand ( * , all = True )

Unfold all expandable animation channels that are active.

Parameters :

all ( bool ) – All, Expand all channels (not just selected ones) (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_fcurves_enable ( )

Lift the 'disabled' flag from all F-Curves to restore broken curves to working state.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_group ( * , name = '' )

Collect active F-Curves into a fresh group.

Parameters :

name ( str ) – Name, Name of newly created group (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_move ( * , direction = 'DOWN' )

Reorder active animation channels.

Parameters :

direction ( Literal [ 'TOP' , 'UP' , 'DOWN' , 'BOTTOM' ] ) – Direction, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_rename ( )

Rename the animation channel beneath the cursor.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_select_all ( * , action = 'TOGGLE' )

Change selection state of every animation channel.

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Selection action to execute (optional)

- TOGGLE
Toggle – Change selection for all elements.

- SELECT
Select – Pick all elements.

- DESELECT
Deselect – Unselect all elements.

- INVERT
Invert – Flip selection state for all elements.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_select_box ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , deselect = False , extend = True )

Activate all animation channels within a designated rectangular area.

Parameters :

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- deselect ( bool ) – Deselect, Deselect rather than select items (optional)

- extend ( bool ) – Extend, Extend selection instead of deselecting everything first (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_select_filter ( )

Launch text input mode to narrow the displayed channels to those whose names match the input.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_setting_disable ( * , mode = 'DISABLE' , type = 'PROTECT' )

Deactivate a setting across all active animation channels.

Parameters :

- mode ( Literal [ 'TOGGLE' , 'DISABLE' , 'ENABLE' , 'INVERT' ] ) – Mode, (optional)

- type ( Literal [ 'PROTECT' , 'MUTE' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_setting_enable ( * , mode = 'ENABLE' , type = 'PROTECT' )

Activate a setting across all active animation channels.

Parameters :

- mode ( Literal [ 'TOGGLE' , 'DISABLE' , 'ENABLE' , 'INVERT' ] ) – Mode, (optional)

- type ( Literal [ 'PROTECT' , 'MUTE' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_setting_toggle ( * , mode = 'TOGGLE' , type = 'PROTECT' )

Flip a setting state across all active animation channels.

Parameters :

- mode ( Literal [ 'TOGGLE' , 'DISABLE' , 'ENABLE' , 'INVERT' ] ) – Mode, (optional)

- type ( Literal [ 'PROTECT' , 'MUTE' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_ungroup ( )

Extract picked F-Curves from their current group assignments.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. channels_view_selected ( * , include_handles = True , use_preview_range = True )

Recenter the display on the active channels.

Parameters :

- include_handles ( bool ) – Include Handles, Include handles of keyframes when calculating extents (optional)

- use_preview_range ( bool ) – Use Preview Range, Ignore frames outside of the preview range (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. clear_useless_actions ( * , only_unused = True )

Flag actions with no F-Curves for removal upon next save-and-reload (preserving "action archives").

Parameters :

only_unused ( bool ) – Only Unused, Only unused (Fake User only) actions get considered (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/anim.py:365

bpy.ops.anim. copy_driver_button ( )

Duplicate the driver connected to the active property widget.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. driver_button_add ( )

Assign a driver to the property at the cursor.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. driver_button_edit ( )

Adjust the drivers tied to the property reflected by the active widget.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. driver_button_remove ( * , all = True )

Delete the driver(s) connected to the property(ies) reflected by the active widget.

Parameters :

all ( bool ) – All, Delete drivers for all elements of the array (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. end_frame_set ( )

Set the active frame as the end of the preview or scene timeline.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keyframe_clear_button ( * , all = True )

Erase every keyframe on the active property.

Parameters :

all ( bool ) – All, Clear keyframes from all elements of the array (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keyframe_clear_v3d ( * , confirm = True )

Strip all animation keyframes from active objects.

Parameters :

confirm ( bool ) – Confirm, Prompt for confirmation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keyframe_clear_vse ( * , confirm = True )

Strip all animation keyframes from active clips.

Parameters :

confirm ( bool ) – Confirm, Prompt for confirmation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keyframe_delete ( * , type = 'DEFAULT' )

Remove keyframes at the active timeline frame for properties in the designated Keying Set.

Parameters :

type ( Literal [ 'DEFAULT' ] ) – Keying Set, The Keying Set to use (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keyframe_delete_button ( * , all = True )

Purge the keyframe at the active frame for the highlighted property.

Parameters :

all ( bool ) – All, Delete keyframes from all elements of the array (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keyframe_delete_by_name ( * , type = '' )

Alternate interface for 'Delete Keyframe' suitable for hotkey assignment.

Parameters :

type ( str ) – Keying Set, The Keying Set to use (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keyframe_delete_v3d ( * , confirm = True )

Strip keyframes at the active frame from picked objects and bones.

Parameters :

confirm ( bool ) – Confirm, Prompt for confirmation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keyframe_delete_vse ( * , confirm = True )

Strip keyframes at the active frame from active clips.

Parameters :

confirm ( bool ) – Confirm, Prompt for confirmation (optional)

Returns :

set[Literal[Operator Return Items]]

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keyframe_insert ( * , type = 'DEFAULT' )

Place keyframes at the active frame using the current Keying Set or user settings if none is designated.

Parameters :

type ( Literal [ 'DEFAULT' ] ) – Keying Set, The Keying Set to use (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keyframe_insert_button ( * , all = True )

Embed a keyframe for the active property.

Parameters :

all ( bool ) – All, Insert a keyframe for all element of the array (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keyframe_insert_by_name ( * , type = '' )

Alternate interface for 'Insert Keyframe' suitable for hotkey assignment.

Parameters :

type ( str ) – Keying Set, The Keying Set to use (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keyframe_insert_menu ( * , type = 'DEFAULT' , always_prompt = False )

Embed keyframes for a Keying Set, displaying a list of available sets if unspecified.

Parameters :

- type ( Literal [ 'DEFAULT' ] ) – Keying Set, The Keying Set to use (optional)

- always_prompt ( bool ) – Always Show Menu, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keying_set_active_set ( * , type = 'DEFAULT' )

Switch the active keying set.

Parameters :

type ( Literal [ 'DEFAULT' ] ) – Keying Set, The Keying Set to use (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keying_set_add ( )

Introduce a new (bare) keying set to the active Scene.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keying_set_export ( * , filepath = '' , filter_folder = True , filter_text = True , filter_python = True )

Write Keying Set to a text script.

Parameters :

- filepath ( str ) – filepath, (optional, never None)

- filter_folder ( bool ) – Filter folders, (optional)

- filter_text ( bool ) – Filter text, (optional)

- filter_python ( bool ) – Filter Python, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/anim.py:46

bpy.ops.anim. keying_set_path_add ( )

Contribute an empty route to the active keying set.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keying_set_path_remove ( )

Erase the active Path from the active keying set.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keying_set_remove ( )

Discard the active keying set.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keyingset_button_add ( * , all = True )

Attach the active property to the current keying set.

Parameters :

all ( bool ) – All, Add all elements of the array to a Keying Set (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. keyingset_button_remove ( )

Take away the active property from the current keying set.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. merge_animation ( )

Consolidate motion from active objects into the action of the focused object. No action removal occurs, but some might wind up with no users.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. paste_driver_button ( )

Put the driver from memory onto the active property.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. previewrange_clear ( )

Reset preview frame window.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. previewrange_set ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True )

Dynamically establish a playback range.

Parameters :

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. replace_action ( * , old_session_uid = 0 , new_session_uid = 0 )

Reroute all references from one action to another. Standard action slot policies govern behavior. NLA and Action Constraints are bypassed.

Parameters :

- old_session_uid ( int ) – Old Action, Old Action's session uid to replace (in [-inf, inf], optional)

- new_session_uid ( int ) – Replacement Action, The replacement Action's session uid to remap all selected Action's users to (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. replace_action_new ( * , old_session_uid = 0 )

Reroute all references from one action to a replacement. NLA and Action Constraints are bypassed.

Parameters :

old_session_uid ( int ) – Old Action, Old Action's session uid to replace (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. scene_range_frame ( )

Zoom to the scene's current frame extent, respecting the playback preview range if active.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. separate_slots ( )

Break up each slot of the focused object's action into its own separate action. All owners shift to the generated ones. The original stays vacant and might lose all users.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

set[Literal[Operator Return Items]]

bpy.ops.anim. slot_channels_move_to_new_action ( )

Relocate the active slots into a freshly made action.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. slot_new_for_id ( )

Establish a fresh action slot for this data-block to store animation.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/anim.py:721

bpy.ops.anim. slot_unassign_from_constraint ( )

Detach the action slot from this restriction.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/anim.py:779

bpy.ops.anim. slot_unassign_from_id ( )

Disconnect the action slot, removing animation from this data-block.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/anim.py:758

bpy.ops.anim. slot_unassign_from_nla_strip ( )

Remove the action slot from this NLA clip, effectively disabling animation.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/anim.py:779

bpy.ops.anim. start_frame_set ( )

Set the active frame as the start of the preview or scene timeline.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.anim. update_animated_transform_constraints ( * , use_convert_to_radians = True )

Refresh f-curves/drivers governing Transform limits (for .blend files from 2.70 and prior).

Parameters :

use_convert_to_radians ( bool ) – Convert to Radians, Convert f-curves/drivers affecting rotations to radians.Warning: Use this only once(optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/anim.py:402

bpy.ops.anim. version_bone_hide_property ( )

Transfers F-Curves tied to bone visibility from selected armatures into the object's action. Operates on the primary layer and clip only.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/anim.py:842

bpy.ops.anim. view_curve_in_graph_editor ( * , all = False , isolate = False )

Center the Graph Editor on the property beneath the cursor.

Parameters :

- all ( bool ) – Show All, Center on the full array property instead of the single indexed item under the cursor (optional)

- isolate ( bool ) – Isolate, Conceal all F-Curves except those being centered (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
