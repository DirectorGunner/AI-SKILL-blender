# Graph Operators (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Graph Operators

bpy.ops.graph.bake_keys()

Deposit frames at every timing in between the chosen frames

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.blend_offset(*, factor=0.0)

Move the chose frames towards the worth of the flanking frames as one item

Parameters:

factor (float) – Offset Factor, Regulate which frame to move towards and the degree (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.blend_to_default(*, factor=0.0)

Blend the chose frames to their starting worth from their current placement

Parameters:

factor (float) – Factor, How considerably to blend to the starting worth (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.blend_to_ease(*, factor=0.0)

Blends the chose frames from current status to an accelerate-in or quicken-out trajectory

Parameters:

factor (float) – Blend, Prefer either the real material or accelerate trajectory (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.blend_to_neighbor(*, factor=0.0)

Blend the chose frames to their left or right mate

Parameters:

factor (float) – Blend, The blend degree with zero getting the active timing (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.breakdown(*, factor=0.0)

Shift the chose frames to a middle placement relative to the flanking set

Parameters:

factor (float) – Factor, Prefer either the left or the right set (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.butterworth_smooth(*, cutoff_frequency=3.0, filter_order=4, samples_per_frame=1, blend=1.0, blend_in_out=1)

Make smooth a animation while keeping the general course of the trajectory

Parameters:

- cutoff_frequency (float) – Frequency Cutoff (Hz), Reduced principles provide a sleeker trajectory (in [0, inf], optional)
- filter_order (int) – Filter Order, Taller principles create a stricter frequency border (in [1, 32], optional)
- samples_per_frame (int) – Samples per Frame, Quantity of estimates to reckon per timing, facilitates with subframe material (in [1, 64], optional)
- blend (float) – Blend, How considerably to blend to the sleek trajectory (in [0, inf], optional)
- blend_in_out (int) – Blend In/Out, Straight blend the silky material to the edge frames of the pick (in [0, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.clean(*, threshold=0.001, channels=False)

Shrink trajectories by purging tightly spaced frames

Parameters:

- threshold (float) – Threshold, (in [0, inf], optional)
- channels (bool) – Channels, (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.click_insert(*, frame=1.0, value=1.0, extend=False)

Deposit a fresh frame at the arrow location for the energized trajectory

Parameters:

- frame (float) – Frame Number, Timing to put frame on (in [-inf, inf], optional)
- value (float) – Value, Amount for frame on (in [-inf, inf], optional)
- extend (bool) – Extend, Grow the roster in lieu of wiping everything (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.clickselect(*, wait_to_deselect_others=False, use_select_on_click=False, mouse_x=0, mouse_y=0, extend=False, deselect_all=False, column=False, curves=False)

Highlight frames by engaging them

Parameters:

- wait_to_deselect_others (bool) – Wait to Deselect Others, (optional)
- use_select_on_click (bool) – Act on Click, Rather than marking on button-down, hold up to detect drag. Else mark on release (optional)
- mouse_x (int) – Mouse X, (in [-inf, inf], optional)
- mouse_y (int) – Mouse Y, (in [-inf, inf], optional)
- extend (bool) – Extend Select, Flip frame mark rather than emptying newly chosen frames exclusively (optional)
- deselect_all (bool) – Deselect On Nothing, Wipe all choices when nothing sits at the cursor (optional)
- column (bool) – Column Select, Highlight every frame that sits on the equivalent timing as the one at the cursor (optional)
- curves (bool) – Only Curves, Highlight every frame in the trajectory (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.copy()

Deposit the chose frames into the resident clipboard

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.cursor_set(*, frame=0.0, value=0.0)

Engage to regulate the live timing and worth arrow

Parameters:

- frame (float) – Frame, (in [-1.04857e+06, 1.04857e+06], optional)
- value (float) – Value, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.decimate(*, mode='RATIO', factor=0.333333, remove_error_margin=0.0)

Shrink trajectories by removing frames that change the trajectory form the utmost

Parameters:

- mode (Literal['RATIO', 'ERROR']) – Mode, Which technique to utilize for reduction (optional)

- RATIO
Ratio – Use a portion to convey how numerous frames you wish to purge.

- ERROR
Error Margin – Use an divergence margin to convey how considerably the trajectory is sanctioned to deviate from the initial course.

- factor (float) – Factor, The portion of frames to purge (in [0, 1], optional)
- remove_error_margin (float) – Max Error Margin, How considerably the re-shaped trajectory is sanctioned to deviate from the initial (in [0, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.delete(*, confirm=True)

Pull every chose frame

Parameters:

confirm (bool) – Confirm, Ask for acknowledgment (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.driver_delete_invalid()

Pull every obvious driver judged unserviceable

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.driver_variables_copy()

Deposit the steering components of the energized steering arrangement

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.driver_variables_paste(*, replace=False)

Insert replicated steering components to the energized steering arrangement

Parameters:

replace (bool) – Replace Existing, Swap current steering components, rather than simply tacking to the conclusion of the extant roster (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.duplicate(*, mode='TRANSLATION')

Build a facsimile of every chose frame

Parameters:

mode (Literal[Transform Mode Type Items]) – Mode, (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.duplicate_move(*, `GRAPH_OT`_duplicate={}, `TRANSFORM_OT`_translate={})

Build a facsimile of every chose frame and relocate them

Parameters:

- `GRAPH_OT`_duplicate (dict[str, Any]) – Duplicate Keyframes, Build a facsimile of every chose frame (optional, bpy.ops.graph.duplicate() keyword arguments)
- `TRANSFORM_OT`_translate (dict[str, Any]) – Move, Shift the chose things (optional, bpy.ops.transform.translate() keyword arguments)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.ease(*, factor=0.0, sharpness=2.0)

Position frames on a quicken-in or quicken-out trajectory

Parameters:

- factor (float) – Curve Bend, Establishes if the components should be positioned on a quicken-in or quicken-out trajectory (in [-inf, inf], optional)
- sharpness (float) – Sharpness, Taller amounts construct the shift more sharp (in [0.001, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.easing_type(*, type='AUTO')

Configure acceleration category for the trajectory divisions commencing from the chose frames

Parameters:

type (Literal[Beztriple Interpolation Easing Items]) – Type, (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.equalize_handles(*, side='LEFT', handle_length=5.0, flatten=False)

Make certain the chose frames' grips possess proportional width, voluntarily generating them level. Automatic, Automatic Clamped, or Vector grip types shall be switched to Aligned

Parameters:

- side (Literal['LEFT', 'RIGHT', 'BOTH']) – Side, Face of the frames' Bezier grips to exert upon (optional)

- LEFT
Left – Even the chose frames' left grips.

- RIGHT
Right – Even the chose frames' right grips.

- BOTH
Both – Even each of a frame's grips.

- handle_length (float) – Handle Length, Width to construct the chose frames' Bezier grips (in [0.1, inf], optional)
- flatten (bool) – Flatten, Construct the worths of the chose frames' grips the same as their respective frames (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.euler_filter()

Remedy tremendous shifts and spins in the chose Euler Spinning trajectories developing from spinning principles being clipped when baking matter simulation

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.extrapolation_type(*, type='CONSTANT')

Configure reach technique for the chose trajectories

Parameters:

type (Literal['CONSTANT', 'LINEAR', '`MAKE_CYCLIC`', '`CLEAR_CYCLIC`']) – Type, (optional)

- CONSTANT
Constant Extrapolation – Principles on endpoint frames are maintained.

- LINEAR
Linear Extrapolation – Straight-mark incline of finish divisions are drawn out onward from the endpoint frames.

- `MAKE_CYCLIC`
Make Cyclic (F-Modifier) – Deposit Cycles filter if sole doesn't exist presently.

- `CLEAR_CYCLIC`
Clear Cyclic (F-Modifier) – Purge Cycles filter if not obliged subsequently.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.fmodifier_add(*, type='NULL', only_active=False)

Append filtering consequence to the lively/chose trajectories

Parameters:

- type (Literal[Fmodifier Type Items]) – Type, (optional)
- only_active (bool) – Only Active, Solely put filtering consequence to lively trajectory (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.fmodifier_copy()

Deposit the filtering consequence(s) of the energized trajectory

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.fmodifier_paste(*, only_active=False, replace=False)

Append replicated filtering consequence to the chose trajectories

Parameters:

- only_active (bool) – Only Active, Solely put filtering consequence on lively trajectory (optional)
- replace (bool) – Replace Existing, Swap current filtering consequence, rather than simply tacking to the conclusion of the extant roster (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.frame_jump()

Put the arrow on the midst of chose frames

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.gaussian_smooth(*, factor=1.0, sigma=0.33, filter_width=6)

Make smooth the trajectory with a mathematics filtering instrument

Parameters:

- factor (float) – Factor, How considerably to blend to the starting worth (in [0, inf], optional)
- sigma (float) – Sigma, The outline of the mathematics dispersion, reduced amounts construct it keener (in [0.001, inf], optional)
- filter_width (int) – Filter Width, How distant to every flank the business shall ordinary the frame worths (in [1, 64], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.ghost_curves_clear()

Purge trajectory recordings (Echoes) for lively Graph Editor

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.ghost_curves_create()

Build recording (Echoes) of chose trajectories as foundation assist for lively Graph Editor

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.handle_type(*, type='FREE')

Configure classification of grip for the chose frames

Parameters:

type (Literal[Keyframe Handle Type Items]) – Type, (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.hide(*, unselected=False)

Conceal the chose trajectories from Graph Editor sight

Parameters:

unselected (bool) – Unselected, Conceal unmarked in lieu of chose trajectories (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.interpolation_type(*, type='CONSTANT')

Configure mixing technique for the trajectory divisions commencing from the chose frames

Parameters:

type (Literal[Beztriple Interpolation Mode Items]) – Type, (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.keyframe_insert(*, type='ALL')

Deposit frames for the given divisions

Parameters:

type (Literal['ALL', 'SEL', 'ACTIVE', '`CURSOR_ACTIVE`', '`CURSOR_SEL`']) – Type, (optional)

- ALL
All Channels – Deposit a frame on every obvious and editable trajectory utilizing every trajectory's live worth.

- SEL
Only Selected Channels – Deposit a frame on chose trajectories utilizing every trajectory's live worth.

- ACTIVE
Only Active F-Curve – Deposit a frame on the lively trajectory utilizing the trajectory's live worth.

- `CURSOR_ACTIVE`
Active Channels at Cursor – Deposit a frame for the lively trajectory at the arrow spot.

- `CURSOR_SEL`
Selected Channels at Cursor – Deposit a frame for the chose trajectories at the arrow spot.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.keyframe_jump(*, next=True)

Vault to the preceding or upcoming frame

Parameters:

next (bool) – Next Keyframe, (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.keys_to_samples()

Shift the chose divisions to an unmodifiable roster of estimates to conserve archive house

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.match_slope(*, factor=0.0)

Blend the chose frames to the trajectory of the flanking components

Parameters:

factor (float) – Factor, Characterizes which components to utilize as trajectory and how considerably to blend towards them (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.mirror(*, type='CFRA')

Reverse the chose frames over the chose flip position

Parameters:

type (Literal['CFRA', 'VALUE', 'YAXIS', 'XAXIS', 'MARKER']) – Type, (optional)

- CFRA
By Times Over Current Frame – Reverse timings of the chose frames utilizing the active timing as the flip position.

- VALUE
By Values Over Cursor Value – Reverse worths of the chose frames utilizing the arrow worth (Y/Straight component) as the flip position.

- YAXIS
By Times Over Zero Time – Reverse timings of the chose frames, successfully turning around the order they display in.

- XAXIS
By Values Over Zero Value – Reverse worths of the chose frames (i.e. downward principles become upward, and the other way around).

- MARKER
By Times Over First Selected Marker – Reverse timings of the chose frames utilizing the initial chose sign as the marker.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.paste(*, offset='START', value_offset='NONE', merge='MIX', flipped=False)

Restore frames from the resident clipboard for the chose divisions, getting going on the live timing

Parameters:

- offset (Literal[Keyframe Paste Offset Items]) – Frame Offset, Restore hour distance of components (optional)
- value_offset (Literal[Keyframe Paste Offset Value Items]) – Value Offset, Restore components with a worth distance (optional)
- merge (Literal[Keyframe Paste Merge Items]) – Type, Technique of uniting pasted components and extant (optional)
- flipped (bool) – Flipped, Restore frames from reversed frame designs if they persist (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.previewrange_set()

Fix Examination Extent in light of extent of chose frames

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.push_pull(*, factor=1.0)

Magnify or scale down the worth of the chose components

Parameters:

factor (float) – Factor, Handle how considerably to amplify or scale down the components (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.reveal(*, select=True)

Create before concealed trajectories evident once again in Graph Editor sight

Parameters:

select (bool) – Select, (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.samples_to_keys()

Shift the chose divisions from estimates to frames

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.scale_average(*, factor=1.0)

Grow the chose frame principles by their pooled mid-point

Parameters:

factor (float) – Scale Factor, The grow coefficient used to the trajectory divisions (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.scale_from_neighbor(*, factor=0.0, anchor='LEFT')

Rise or deduct the worth of the chose components in rapport to the flanking component

Parameters:

- factor (float) – Factor, The grow degree to utilize components with (in [-inf, inf], optional)
- anchor (Literal['LEFT', 'RIGHT']) – Reference Key, Which extremity of the division to utilize as a foundation to grow from (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.select_all(*, action='TOGGLE')

Flip mark of every frame

Parameters:

action (Literal['TOGGLE', 'SELECT', 'DESELECT', 'INVERT']) – Action, Choice work to carry out (optional)

- TOGGLE
Toggle – Flip mark for every part.

- SELECT
Select – Mark every part.

- DESELECT
Deselect – Unmark every part.

- INVERT
Invert – Flip which are marked.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.select_box(*, axis_range=False, include_handles=True, tweak=False, use_curve_selection=True, xmin=0, xmax=0, ymin=0, ymax=0, wait_for_input=True, mode='SET')

Highlight every frame in the given zone

Parameters:

- axis_range (bool) – Axis Range, (optional)
- include_handles (bool) – Include Handles, Are grips checked separately alongside the pick requirement, independently from their components. When deactivated, grips are (un)marked in unison with their components (optional)
- tweak (bool) – Tweak, Business has been engaged utilizing a press-drag occurrence (optional)
- use_curve_selection (bool) – Select Curves, Grant marking every frame of a trajectory by marking the computed trajectory (optional)
- xmin (int) – X Min, (in [-inf, inf], optional)
- xmax (int) – X Max, (in [-inf, inf], optional)
- ymin (int) – Y Min, (in [-inf, inf], optional)
- ymax (int) – Y Max, (in [-inf, inf], optional)
- wait_for_input (bool) – Wait for Input, (optional)
- mode (Literal['SET', 'ADD', 'SUB']) – Mode, (optional)

- SET
Set – Set a new selection.

- ADD
Extend – Extend existing selection.

- SUB
Subtract – Subtract existing selection.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.select_circle(*, x=0, y=0, radius=25, wait_for_input=True, mode='SET', include_handles=True, use_curve_selection=True)

Highlight frame points utilizing round marking

Parameters:

- x (int) – X, (in [-inf, inf], optional)
- y (int) – Y, (in [-inf, inf], optional)
- radius (int) – Radius, (in [1, inf], optional)
- wait_for_input (bool) – Wait for Input, (optional)
- mode (Literal['SET', 'ADD', 'SUB']) – Mode, (optional)

- SET
Set – Set a new selection.

- ADD
Extend – Extend existing selection.

- SUB
Subtract – Subtract existing selection.

- include_handles (bool) – Include Handles, Are grips checked separately alongside the pick requirement, independently from their components. When deactivated, grips are (un)marked in unison with their components (optional)
- use_curve_selection (bool) – Select Curves, Grant marking every frame of a trajectory by marking the trajectory itself (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.select_column(*, mode='KEYS')

Highlight every frame on the given timing(s)

Parameters:

mode (Literal['KEYS', 'CFRA', '`MARKERS_COLUMN`', '`MARKERS_BETWEEN`']) – Mode, (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.select_key_handles(*, left_handle_action='SELECT', right_handle_action='SELECT', key_action='KEEP')

For the chose frames, mark/unmark every mix of the component itself and its grips

Parameters:

- left_handle_action (Literal['SELECT', 'DESELECT', 'KEEP']) – Left Handle, Consequence on the left grip (optional)

- SELECT
Select.

- DESELECT
Deselect.

- KEEP
Keep – Leave as is.

- right_handle_action (Literal['SELECT', 'DESELECT', 'KEEP']) – Right Handle, Consequence on the right grip (optional)

- SELECT
Select.

- DESELECT
Deselect.

- KEEP
Keep – Leave as is.

- key_action (Literal['SELECT', 'DESELECT', 'KEEP']) – Key, Consequence on the component itself (optional)

- SELECT
Select.

- DESELECT
Deselect.

- KEEP
Keep – Leave as is.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.select_lasso(*, path=None, use_smooth_stroke=False, smooth_stroke_factor=0.75, smooth_stroke_radius=35, mode='SET', include_handles=True, use_curve_selection=True)

Highlight frame points utilizing noose marking

Parameters:

- path (bpy_prop_collection[OperatorMousePath]) – Path, (optional)
- use_smooth_stroke (bool) – Stabilize Stroke, Mark lags at your cursor and adheres a sleeker course (optional)
- smooth_stroke_factor (float) – Smooth Stroke Factor, Taller amounts provide a sleeker stroke (in [0.5, 0.99], optional)
- smooth_stroke_radius (int) – Smooth Stroke Radius, Least separation from the preceding spot ahead of marking continues (in [10, 200], optional)
- mode (Literal['SET', 'ADD', 'SUB']) – Mode, (optional)

- SET
Set – Set a new selection.

- ADD
Extend – Extend existing selection.

- SUB
Subtract – Subtract existing selection.

- include_handles (bool) – Include Handles, Are grips checked separately alongside the pick requirement, independently from their components. When deactivated, grips are (un)marked in unison with their components (optional)
- use_curve_selection (bool) – Select Curves, Grant marking every frame of a trajectory by marking the trajectory itself (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.select_leftright(*, mode='CHECK', extend=False)

Highlight frames to the left or the right of the live timing

Parameters:

- mode (Literal['CHECK', 'LEFT', 'RIGHT']) – Mode, (optional)
- extend (bool) – Extend Select, (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.select_less()

Unmark frames on margins of mark landmasses

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.graph.select_linked()
