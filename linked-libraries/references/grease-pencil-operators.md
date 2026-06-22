# Grease Pencil Operators (part 1)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

Grease Pencil Stroke and Frame Operations

bpy.ops.grease_pencil.active_frame_delete ( * , all = False )
Remove the currently active drawn frame(s)

Parameters:
all ( bool ) – Delete all, Remove active frames across every layer (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.bake_grease_pencil_animation ( * , frame_start = 1 , frame_end = 250 , step = 1 , only_selected = False , frame_target = 1 , project_type = 'KEEP' )
Encode object motion into stroke keyframes

Parameters:
- frame_start ( int ) – Start Frame, Timeline beginning point (in [1, 100000], optional)
- frame_end ( int ) – End Frame, Timeline endpoint (in [1, 100000], optional)
- step ( int ) – Step, Spacing between intermediate frames (in [1, 100], optional)
- only_selected ( bool ) – Only Selected Keyframes, Process only highlighted keyframes (optional)
- frame_target ( int ) – Target Frame, Output keyframe number (in [1, 100000], optional)
- project_type ( Literal [ 'KEEP' , 'FRONT' , 'SIDE' , 'TOP' , 'VIEW' , 'CURSOR' ] ) – Projection Type, (optional)
- KEEP: Leave strokes at their original orientation
- FRONT: Project onto the X-Z plane
- SIDE: Project onto the Y-Z plane
- TOP: Project onto the X-Y plane
- VIEW: Project to align with the current camera viewpoint using cursor placement
- CURSOR: Project based on 3D cursor orientation

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.brush_stroke ( * , stroke = None , mode = 'NORMAL' , brush_toggle = 'None' , pen_flip = False )
Generate a fresh stroke using the current brush

Parameters:
- stroke ( bpy_prop_collection [ OperatorStrokeElement ]) – Stroke, (optional)
- mode ( Literal [ 'NORMAL' , 'INVERT' ] ) – Stroke Mode, Operation applied during brush motion (optional)
- NORMAL: Paint with standard brush behavior
- INVERT: Apply opposite brush effect during this stroke
- brush_toggle ( Literal [ 'None' , 'SMOOTH' , 'ERASE' , 'MASK' ] ) – Temporary Brush Toggle Type, Alternate brush active for this stroke only (optional)
- None: Use the current brush tool
- SMOOTH: Temporarily activate smoothing (optional)
- ERASE: Temporarily activate eraser (optional)
- MASK: Temporarily activate masking (optional)
- pen_flip ( bool ) – Pen Flip, Indicates stylus eraser mode engagement (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.caps_set ( * , type = 'ROUND' )
Modify endpoint styling (curved or straight)

Parameters:
type ( Literal [ 'ROUND' , 'FLAT' , 'START' , 'END' ] ) – Type, (optional)
- ROUND: Apply default rounded endpoints
- FLAT: Apply flat endpoints
- START: Toggle start-point styling
- END: Toggle end-point styling

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.clean_loose ( * , limit = 1 )
Delete isolated or dangling points

Parameters:
limit ( int ) – Limit, Minimum point count to keep a stroke (in [1, inf], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.convert_curve_type ( * , type = 'POLY' , threshold = 0.01 )
Transform curves between spline interpolation modes

Parameters:
- type (Literal[Curves Type Items]) – Type, (optional)
- threshold ( float ) – Threshold, Allowed deviation distance for point reduction (in [0, 100], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.copy ( )
Duplicate selected strokes or points to clipboard

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.cyclical_set ( * , type = 'TOGGLE' , subdivide_cyclic_segment = True )
Toggle closed shape by connecting the final point back to the start

Parameters:
- type ( Literal [ 'CLOSE' , 'OPEN' , 'TOGGLE' ] ) – Type, (optional)
- subdivide_cyclic_segment ( bool ) – Match Point Density, Insert intermediate points along the new segment to maintain spacing (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.delete ( * , mode = 'ALL' )
Erase selected lines or points

Parameters:
mode ( Literal [ 'ALL' , 'STROKES' , 'FILLS' ] ) – Mode, Which category to remove (optional)
- ALL: Discard all selected strokes and fills
- STROKES: Discard strokes only, preserve fills
- FILLS: Discard fills only, preserve strokes

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.delete_breakdown ( )
Purge interpolated frames created between key poses

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.delete_frame ( * , type = '`ACTIVE_FRAME`' )
Discard drawn frame(s)

Parameters:
type ( Literal [ '`ACTIVE_FRAME`' , '`ALL_FRAMES`' ] ) – Type, Frame removal strategy (optional)
- `ACTIVE_FRAME`: Remove the current frame on the active layer only
- `ALL_FRAMES`: Remove current frames across all layers

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.dissolve ( * , type = 'POINTS' )
Discard marked points without severing the stroke into segments

Parameters:
type ( Literal [ 'POINTS' , 'BETWEEN' , 'UNSELECT' ] ) – Type, Point removal strategy (optional)
- POINTS: Erase highlighted points only
- BETWEEN: Erase points lying between highlighted ones
- UNSELECT: Erase every point except highlighted ones

Returns:
Result of the operator call.

Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.duplicate ( )
Create copies of highlighted points

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.duplicate_move ( * , `GREASE_PENCIL_OT`_duplicate = {} , `TRANSFORM_OT`_translate = {} )
Create copies of strokes and reposition them interactively

Parameters:
- `GREASE_PENCIL_OT`_duplicate ( dict [ str , Any ] ) – Duplicate, Replicate the highlighted points (optional, bpy.ops.grease_pencil.duplicate() keyword arguments)
- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Translate selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.erase_box ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True )
Delete points contained within a rectangular region

Parameters:
- xmin ( int ) – X Min, (in [-inf, inf], optional)
- xmax ( int ) – X Max, (in [-inf, inf], optional)
- ymin ( int ) – Y Min, (in [-inf, inf], optional)
- ymax ( int ) – Y Max, (in [-inf, inf], optional)
- wait_for_input ( bool ) – Wait for Input, (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.erase_lasso ( * , path = None , use_smooth_stroke = False , smooth_stroke_factor = 0.75 , smooth_stroke_radius = 35 )
Delete points within a freehand loop

Parameters:
- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)
- use_smooth_stroke ( bool ) – Stabilize Stroke, Track mouse movement with a delayed, smoothed curve (optional)
- smooth_stroke_factor ( float ) – Smooth Stroke Factor, Higher settings yield a more fluid path (in [0.5, 0.99], optional)
- smooth_stroke_radius ( int ) – Smooth Stroke Radius, Minimum distance traveled before registering movement (in [10, 200], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.extrude ( )
Extend out the highlighted points

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.extrude_move ( * , `GREASE_PENCIL_OT`_extrude = {} , `TRANSFORM_OT`_translate = {} )
Extend highlighted points and move them interactively

Parameters:
- `GREASE_PENCIL_OT`_extrude ( dict [ str , Any ] ) – Extrude Stroke Points, Extend out the highlighted points (optional, bpy.ops.grease_pencil.extrude() keyword arguments)
- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Translate selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.fill ( * , invert = False , precision = False )
Colorize enclosed shapes formed by overlapping strokes

Parameters:
- invert ( bool ) – Invert, Detect unfilled regions instead of enclosed ones (optional)
- precision ( bool ) – Precision, Use fine-grained positioning for edge lines (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.frame_clean_duplicate ( * , selected = False )
Purge redundant keyframes that are copies of the preceding one

Parameters:
selected ( bool ) – Selected, Discard only highlighted keyframes (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.frame_duplicate ( * , all = False )
Create a replica of the current drawn frame(s)

Parameters:
all ( bool ) – Duplicate all, Replicate active keyframes across every layer (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.insert_blank_frame ( * , all_layers = False , duration = 0 )
Add an empty frame at the current timeline position

Parameters:
- all_layers ( bool ) – All Layers, Introduce an empty frame across all editable layers (optional)
- duration ( int ) – Duration, (in [0, 1048574], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.interpolate ( * , shift = 0.0 , layers = 'ACTIVE' , exclude_breakdowns = False , use_selection = False , flip = 'AUTO' , smooth_steps = 1 , smooth_factor = 0.0 )
Generate in-between strokes bridging two keyframes

Parameters:
- shift ( float ) – Shift, Balance which frame influences the intermediate strokes more (in [-1, 1], optional)
- layers ( Literal [ 'ACTIVE' , 'ALL' ] ) – Layer, Which layers participate in interpolation (optional)
- exclude_breakdowns ( bool ) – Exclude Breakdowns, Ignore existing breakdown keyframes when determining range (optional)
- use_selection ( bool ) – Use Selection, Interpolate only highlighted strokes (optional)
- flip ( Literal [ 'NONE' , 'FLIP' , 'AUTO' ] ) – Flip Mode, Reverse target strokes to align start/end with source (optional)
- smooth_steps ( int ) – Iterations, How many times to smooth the generated strokes (in [1, 3], optional)
- smooth_factor ( float ) – Smooth, Strength of noise reduction applied to intermediate strokes (in [0, 2], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.interpolate_sequence ( * , step = 1 , layers = 'ACTIVE' , exclude_breakdowns = False , use_selection = False , flip = 'AUTO' , smooth_steps = 1 , smooth_factor = 0.0 , type = 'LINEAR' , easing = '`EASE_IN`' , back = 1.702 , amplitude = 0.15 , period = 0.15 )
Populate frames between keyframes with smoothly eased motion

Parameters:
- step ( int ) – Step, Frame count between each newly created interpolation (in [1, 1048574], optional)
- layers ( Literal [ 'ACTIVE' , 'ALL' ] ) – Layer, Which layers participate in interpolation (optional)
- exclude_breakdowns ( bool ) – Exclude Breakdowns, Ignore existing breakdown keyframes when determining range (optional)
- use_selection ( bool ) – Use Selection, Interpolate only highlighted strokes (optional)
- flip ( Literal [ 'NONE' , 'FLIP' , 'AUTO' ] ) – Flip Mode, Reverse target strokes to align start/end with source (optional)

- smooth_steps ( int ) – Iterations, How many times to smooth the generated strokes (in [1, 3], optional)
- smooth_factor ( float ) – Smooth, Strength of noise reduction applied to intermediate strokes (in [0, 2], optional)
- type ( Literal [ 'LINEAR' , 'CUSTOM' , 'SINE' , 'QUAD' , 'CUBIC' , 'QUART' , 'QUINT' , 'EXPO' , 'CIRC' , 'BACK' , 'BOUNCE' , 'ELASTIC' ] ) – Type, Easing curve used for next interpolation run (optional)
- LINEAR: Direct progression with no smoothing applied
- CUSTOM: User-defined easing from a curve editor
- SINE: Smooth ease (minimal, almost linear with slight arc)
- QUAD: Squared acceleration/deceleration curve
- CUBIC: Cubic acceleration/deceleration curve
- QUART: Fourth-degree polynomial curve
- QUINT: Fifth-degree polynomial curve
- EXPO: Steep acceleration curve (pronounced effect)
- CIRC: High-curvature circular arc (most dramatic effect)
- BACK: Cubic with anticipation and rebound
- BOUNCE: Decaying bounce-like motion similar to impact
- ELASTIC: Decaying sine wave resembling a stretched spring
- easing (Literal[Beztriple Interpolation Easing Items]) – Easing, Which segment endpoints receive easing interpolation (optional)
- back ( float ) – Back, Magnitude of anticipatory overshoot for back easing (in [0, inf], optional)
- amplitude ( float ) – Amplitude, Magnitude multiplier for elastic bounces (in [0, inf], optional)
- period ( float ) – Period, Interval between elastic oscillations (in [-inf, inf], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.join_fills ( )
Merge highlighted strokes to form a single enclosed region with cutouts

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.join_selection ( * , type = 'JOINSTROKES' )
Generate a fresh stroke from selected points or strokes

Parameters:
type ( Literal [ 'JOINSTROKES' , 'SPLITCOPY' , 'SPLIT' ] ) – Type, Combination strategy for the highlighted selection (optional)
- JOINSTROKES: Unite selected strokes into one continuous path
- SPLITCOPY: Copy selected points into a separate stroke
- SPLIT: Isolate selected points as an independent stroke

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_active ( * , layer = 0 )
Designate a Grease Pencil layer as the current working layer

Parameters:
layer ( int ) – Grease Pencil Layer, (in [0, inf], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_add ( * , new_layer_name = 'Layer' )
Create a fresh Grease Pencil layer within the active object

Parameters:
new_layer_name ( str ) – Name, What to call the new layer (optional, never None)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_duplicate ( * , empty_keyframes = False )
Generate a copy of the current Grease Pencil layer

Parameters:
empty_keyframes ( bool ) – Empty Keyframes, Include placeholder keyframes (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_duplicate_object ( * , only_active = True , mode = 'ALL' )
Generate a copy of the current layer on a different object

Parameters:
- only_active ( bool ) – Only Active, Duplicate just the active layer, leave unchecked to copy all (optional)
- mode ( Literal [ 'ALL' , 'ACTIVE' ] ) – Mode, (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_group_add ( * , new_layer_group_name = '' )
Create a fresh Grease Pencil layer group in the active object

Parameters:
new_layer_group_name ( str ) – Name, What to call the new layer group (optional, never None)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_group_color_tag ( * , color_tag = 'COLOR1' )
Modify the appearance mark for a layer group

Parameters:
color_tag ( Literal [ 'NONE' , 'COLOR1' , 'COLOR2' , 'COLOR3' , 'COLOR4' , 'COLOR5' , 'COLOR6' , 'COLOR7' , 'COLOR8' ] ) – Color Tag, (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_group_remove ( * , keep_children = False )
Discard a Grease Pencil layer group in the active object

Parameters:
keep_children ( bool ) – Keep children nodes, Preserve the child layers; delete only the grouping container (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_hide ( * , unselected = False )
Conceal chosen or unchosen Grease Pencil layers

Parameters:
unselected ( bool ) – Unselected, Conceal unchoosen rather than chosen layers (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_isolate ( * , affect_visibility = False )
Restrict editing and display to the current layer alone

Parameters:
affect_visibility ( bool ) – Affect Visibility, Also restrict rendering, not just editing (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_lock_all ( * , lock = True )
Protect every Grease Pencil layer from unintended edits

Parameters:
lock ( bool ) – Lock Value, Toggle protection across all layers (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_mask_add ( * , name = '' )
Introduce a new layer as a masking layer

Parameters:
name ( str ) – Layer, Designate the masking layer (optional, never None)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_mask_remove ( )
Discard the currently active mask

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_mask_reorder ( * , direction = 'UP' )
Shift the current masking layer up or down in the hierarchy

Parameters:
direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_merge ( * , mode = 'ACTIVE' )
Fuse layers together following the chosen strategy

Parameters:
mode ( Literal [ 'ACTIVE' , 'GROUP' , 'ALL' ] ) – Mode, (optional)
- ACTIVE: Combine the current layer with the one immediately below
- GROUP: Combine all layers within the active group
- ALL: Combine every layer into a single one

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_move ( * , direction = 'UP' )
Reposition the current Grease Pencil layer or Group in the stack

Parameters:
direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_remove ( )
Discard the currently active Grease Pencil layer

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.layer_reveal ( )
Display every hidden Grease Pencil layer

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.material_copy_to_object ( * , only_active = True )
Transfer the active Grease Pencil materials to another object

Parameters:
only_active ( bool ) – Only Active, Copy just the active material, uncheck to copy all (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.material_hide ( * , invert = False )
Conceal certain Grease Pencil material(s)

Parameters:
invert ( bool ) – Invert, Conceal inactive materials instead of the active one (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.material_isolate ( * , affect_visibility = False )
Switch whether the active material is the sole one editable and visible

Parameters:
affect_visibility ( bool ) – Affect Visibility, In addition to toggling editability, also toggle rendering (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.material_lock_all ( )
Protect every Grease Pencil material from unintended edits

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.material_lock_unselected ( )
Protect materials unused in highlighted strokes

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.material_lock_unused ( )
Protect and conceal materials with no usage

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.material_reveal ( )
Display all hidden Grease Pencil materials

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.material_select ( * , deselect = False )
Highlight or unhighlight every stroke using the current material

Parameters:
deselect ( bool ) – Deselect, Unhighlight strokes (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.material_unlock_all ( )
Unprotect all Grease Pencil materials for modification

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.move_to_layer ( * , target_layer_name = '' , add_new_layer = False )
Relocate highlighted strokes to a separate layer

Parameters:
- target_layer_name ( str ) – Name, Destination Grease Pencil Layer (optional, never None)
- add_new_layer ( bool ) – New Layer, Move highlighted strokes into a freshly created layer (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.outline ( * , type = 'VIEW' , radius = 0.01 , offset_factor = -1.0 , corner_subdivisions = 2 )
Transform highlighted strokes into their outer boundary

Parameters:
- type ( Literal [ 'VIEW' , 'FRONT' , 'SIDE' , 'TOP' , 'CURSOR' , 'CAMERA' ] ) – Projection Mode, (optional)
- radius ( float ) – Radius, (in [0, 10], optional)
- offset_factor ( float ) – Offset Factor, (in [-1, 1], optional)
- corner_subdivisions ( int ) – Corner Subdivisions, (in [0, 10], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.paintmode_toggle ( * , back = False )
Activate or deactivate drawing mode for Grease Pencil

Parameters:
back ( bool ) – Return to Previous Mode, Restore the mode before entering drawing (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.paste ( * , type = 'ACTIVE' , paste_back = False , keep_world_transform = False )
Insert Grease Pencil points or strokes from clipboard to the current layer

Parameters:
- type ( Literal [ 'ACTIVE' , 'LAYER' ] ) – Type, (optional)
- paste_back ( bool ) – Paste on Back, Position pasted strokes behind all existing ones (optional)
- keep_world_transform ( bool ) – Keep World Transform, Maintain the 3D position of clipboard strokes (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.pen ( * , extend = False , deselect = False , toggle = False , deselect_all = False , select_passthrough = False , extrude_point = False , extrude_handle = 'VECTOR' , delete_point = False , insert_point = False , move_segment = False , select_point = False , move_point = False , cycle_handle_type = False , size = 0.01 )
Draw and modify bezier curves

Parameters:
- extend ( bool ) – Extend, Accumulate selection rather than replacing existing selection (optional)
- deselect ( bool ) – Deselect, Withdraw from selection (optional)
- toggle ( bool ) – Toggle Selection, Reverse the selection status (optional)
- deselect_all ( bool ) – Deselect On Nothing, Clear all selection when the cursor is empty (optional)
- select_passthrough ( bool ) – Only Select Unselected, Skip selection action when element is already highlighted (optional)
- extrude_point ( bool ) – Extrude Point, Create a new point extending from the last selected one (optional)
