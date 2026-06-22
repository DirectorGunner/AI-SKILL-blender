# Nla Operators

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

### Nla Operators 

bpy.ops.nla. action_pushdown ( * , track_index = -1 ) 

Put an action on top of the NLA pile as a new section

Parameters :

track_index ( int ) – Track Index, Index of NLA motion track for this operation (in [-1, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. action_sync_length ( * , active = True ) 

Make the span of the imported action equal to the span used in the section

Parameters :

active ( bool ) – Active Strip Only, Make the span equal only for the focal section (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. action_unlink ( * , force_delete = False ) 

Detach this action from the focal motion slot (and/or escape Tweak Mode)

Parameters :

force_delete ( bool ) – Force Delete, Drop the mark and dump the version kept in this group's NLA pile (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. actionclip_add ( * , action = '' ) 

Add a Motion-Segment section (a section pointing to an action) to the focal track

Parameters :

action ( str ) – Action, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. apply_scale ( ) 

Use the scaling of marked sections on their imported actions

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. bake ( * , frame_start = 1 , frame_end = 250 , step = 1 , only_selected = True , visual_keying = False , clear_constraints = False , clear_parents = False , use_current_action = False , clean_curves = False , bake_types = {'POSE'} , channel_types = {'BBONE', 'LOCATION', 'PROPS', 'ROTATION', 'SCALE'} ) 

Cook every chosen thing's position/scaling/turn shifts into an action

Parameters :

- frame_start ( int ) – Start Frame, Where to begin cooking (in [0, 300000], optional)

- frame_end ( int ) – End Frame, Where to finish cooking (in [1, 300000], optional)

- step ( int ) – Frame Step, How many frames to skip when cooking each step (in [1, 120], optional)

- only_selected ( bool ) – Only Selected Bones, Mark only chosen bone portions (Pose cooking only) (optional)

- visual_keying ( bool ) – Visual Keying, Key based on final shifts (with rules used) (optional)

- clear_constraints ( bool ) – Clear Local Constraints, Strip all rules from cooked object/bones. For sound cooking enable visual marking (optional)

- clear_parents ( bool ) – Clear Parents, Cook shift onto the object then strip parents (objects only) (optional)

- use_current_action ( bool ) – Overwrite Current Action, Cook shifts into the focal action, not a fresh one (for cooking only part of bones in a frame) (optional)

- clean_curves ( bool ) – Clean Curves, After cooking curves, erase unneeded marks (optional)

- bake_types ( set [ Literal [ 'POSE' , 'OBJECT' ] ] ) – Bake Data, What shift types to cook (optional)

- POSE
Pose – Cook bone shifts.

- OBJECT
Object – Cook thing shifts.

- channel_types ( set [ Literal [ 'LOCATION' , 'ROTATION' , 'SCALE' , 'BBONE' , 'PROPS' ] ] ) – Channels, What channels to cook (optional)

- LOCATION
Location – Cook place channels.

- ROTATION
Rotation – Cook turn channels.

- SCALE
Scale – Cook sizing channels.

- BBONE
B-Bone – Cook B-Bone channels.

- PROPS
Custom Properties – Cook special traits.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/anim.py:274

bpy.ops.nla. channels_click ( * , extend = False ) 

Manage clicks to mark NLA tracks

Parameters :

extend ( bool ) – Extend Select, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. clear_scale ( ) 

Zero out scaling of marked sections

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. click_select ( * , wait_to_deselect_others = False , use_select_on_click = False , mouse_x = 0 , mouse_y = 0 , extend = False , deselect_all = False ) 

Manage clicks to mark NLA Sections

Parameters :

- wait_to_deselect_others ( bool ) – Wait to Deselect Others, (optional)

- use_select_on_click ( bool ) – Act on Click, Rather than marking on button, delay to see if there's a drag. Else mark on button lift (optional)

- mouse_x ( int ) – Mouse X, (in [-inf, inf], optional)

- mouse_y ( int ) – Mouse Y, (in [-inf, inf], optional)

- extend ( bool ) – Extend Select, (optional)

- deselect_all ( bool ) – Deselect On Nothing, Unmark everything when nothing beneath the pointer (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. delete ( ) 

Erase marked sections

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. duplicate ( * , linked = False ) 

Make copies of marked NLA-Sections, putting the duplicates on fresh track(s)

Parameters :

linked ( bool ) – Linked, When making copies of sections, form fresh versions of the motions they use (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. duplicate_linked_move ( * , `NLA_OT`_duplicate = {} , `TRANSFORM_OT`_translate = {} ) 

Make linked copies of marked NLA-Sections, putting the copies on fresh track(s)

Parameters :

- `NLA_OT`_duplicate ( dict [ str , Any ] ) – Duplicate Strips, Duplicate selected NLA-Strips, adding the new strips to new track(s) (optional, bpy.ops.nla.duplicate() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Reposition picked items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. duplicate_move ( * , `NLA_OT`_duplicate = {} , `TRANSFORM_OT`_translate = {} ) 

Make copies of marked NLA-Sections, putting the duplicates on fresh track(s)

Parameters :

- `NLA_OT`_duplicate ( dict [ str , Any ] ) – Make Copies, Make copies of marked NLA-Sections, putting the duplicates on fresh track(s) (optional, bpy.ops.nla.duplicate() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Shift, Reposition picked items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. fmodifier_add ( * , type = 'NULL' , only_active = True ) 

Append a frequency-style shift to the focal/marked NLA-Sections

Parameters :

- type (Literal[Fmodifier Type Items]) – Type, (optional)

- only_active ( bool ) – Only Active, Append a frequency modifier of the given sort to the focal section only (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. fmodifier_copy ( ) 

Grab the frequency-style shift(s) of the focal NLA-Section

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. fmodifier_paste ( * , only_active = True , replace = False ) 

Attach grabbed frequency-style shifts to the marked NLA-Sections

Parameters :

- only_active ( bool ) – Only Active, Attach frequency shifts to focal section only (optional)

- replace ( bool ) – Replace Existing, Drop present shifts, rather than adding to the tail of the existing roll (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. make_single_user ( * , confirm = True ) 

Turn shared motions into independent versions for every section

Parameters :

confirm ( bool ) – Confirm, Request endorsement (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. meta_add ( ) 

Enclose the marked sections in a fresh meta-wrapper

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. meta_remove ( ) 

Release the sections held by the marked meta-wrappers

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. move_down ( ) 

Shift marked sections to a lower track if there is room

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. move_up ( ) 

Shift marked sections to a higher track if there is room

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. mute_toggle ( ) 

Hush or restore marked sections

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. previewrange_set ( ) 

Choose Preview Span based on the reaches of marked sections

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. select_all ( * , action = 'TOGGLE' ) 

Toggle or alter the choice of all NLA-Sections

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, What to do with each part (optional)

- TOGGLE
Switch – Flip choice for each part.

- SELECT
Activate – Mark each part.

- DESELECT
Unselect – Remove marks from each part.

- INVERT
Flip – Reverse what is and isn't marked.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. select_box ( * , axis_range = False , tweak = False , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , mode = 'SET' ) 

Grab NLA-Sections by dragging a frame

Parameters :

- axis_range ( bool ) – Axis Range, (optional)

- tweak ( bool ) – Tweak, The tool began via a point-drag occurrence (optional)

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Create a fresh choice.

- ADD
Extend – Grow the active marking.

- SUB
Subtract – Reduce the active marking.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. select_leftright ( * , mode = 'CHECK' , extend = False ) 

Pick sections on the left or the right of the current frame

Parameters :

- mode ( Literal [ 'CHECK' , 'LEFT' , 'RIGHT' ] ) – Mode, (optional)

- extend ( bool ) – Extend Select, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. selected_objects_add ( ) 

Have chosen items show in NLA Editor via motion data

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. snap ( * , type = 'CFRA' ) 

Push section starts to a stated time

Parameters :

type ( Literal [ 'CFRA' , '`NEAREST_FRAME`' , '`NEAREST_SECOND`' , '`NEAREST_MARKER`' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. soundclip_add ( ) 

Append a section for handling when a speaker plays its tone

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. split ( ) 

Tear marked sections at their core positions

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. swap ( ) 

Reverse the alignment of marked sections in tracks

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. tracks_add ( * , above_selected = False ) 

Generate NLA-Tracks above/following the marked tracks

Parameters :

above_selected ( bool ) – Above Selected, Add a fresh NLA Track above every marked one (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. tracks_delete ( ) 

Erase marked NLA-Tracks and their held sections

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. transition_add ( ) 

Link two neighboring marked sections via a shift section

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

set[Literal[Operator Return Items]]

bpy.ops.nla. tweakmode_enter ( * , isolate_action = False , use_upper_stack_evaluation = False ) 

Go into modification behavior for the action in the focal section to edit its shifts

Parameters :

- isolate_action ( bool ) – Isolate Action, Engage 'only' on the NLA Track with the focal section, to edit it without seeing the results of the NLA pile (optional)

- use_upper_stack_evaluation ( bool ) – Evaluate Upper Stack, In modification behavior, view the results of the higher tracks above the edit section (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. tweakmode_exit ( * , isolate_action = False ) 

Leave modification behavior for the action in the focal section

Parameters :

isolate_action ( bool ) – Isolate Action, Disable 'only' on any of the NLA Tracks after leaving change behavior to get things back to normal (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. view_all ( ) 

Reset the viewable region to show the full sections span

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. view_frame ( ) 

Pan the viewport to the current frame

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.nla. view_selected ( ) 

Reset the viewable region to show marked sections span

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
