# Curves Operators, Export Anim Operators, Gizmogroup Operators, Operators Bpy Ops ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Curves Operators; Export Anim Operators; Gizmogroup Operators; Operators (bpy.ops); Import Anim Operators; Info Operators.

## Curves Operators

### Curves Operators

**bpy.ops.curves.add_bezier**( * , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Add a Bézier curve object to the scene.

Parameters:
- radius ( float ) – Radius, (in [0, inf], optional)
- enter_editmode ( bool ) – Enter Edit Mode, Enter edit mode when adding this object (optional)
- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Position for the new object (array of 3 items, in [-inf, inf], optional)
- rotation (mathutils.Euler) – Rotation, Orientation for the new object (array of 3 items, in [-inf, inf], optional)
- scale (mathutils.Vector) – Scale, Size for the new object (array of 3 items, in [-inf, inf], optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.add_circle**( * , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Add a circular curve to the scene.

Parameters:
- radius ( float ) – Radius, (in [0, inf], optional)
- enter_editmode ( bool ) – Enter Edit Mode, Enter edit mode when adding this object (optional)
- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, The alignment of the new object (optional)

- WORLD
World – Align the new object to the world.

- VIEW
View – Align the new object to the view.

- CURSOR
3D Cursor – Use the 3D cursor orientation for the new object.

- location (mathutils.Vector) – Location, Position for the new object (array of 3 items, in [-inf, inf], optional)
- rotation (mathutils.Euler) – Rotation, Orientation for the new object (array of 3 items, in [-inf, inf], optional)
- scale (mathutils.Vector) – Scale, Size for the new object (array of 3 items, in [-inf, inf], optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.attribute_set**( * , value_float = 0.0 , value_float_vector_2d = (0.0, 0.0) , value_float_vector_3d = (0.0, 0.0, 0.0) , value_int = 0 , value_int_vector_2d = (0, 0) , value_color = (1.0, 1.0, 1.0, 1.0) , value_bool = False )

Assign values to the active attribute on selected geometry.

Parameters:
- value_float ( float ) – Value, (in [-inf, inf], optional)
- value_float_vector_2d ( Sequence [ float ] ) – Value, (array of 2 items, in [-inf, inf], optional)
- value_float_vector_3d ( Sequence [ float ] ) – Value, (array of 3 items, in [-inf, inf], optional)
- value_int ( int ) – Value, (in [-inf, inf], optional)
- value_int_vector_2d ( Sequence [ int ] ) – Value, (array of 2 items, in [-inf, inf], optional)
- value_color ( Sequence [ float ] ) – Value, (array of 4 items, in [-inf, inf], optional)
- value_bool ( bool ) – Value, (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.convert_from_particle_system**( )

Create a curves object from the current particle system state.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.convert_to_particle_system**( )

Set up a hair particle system from curves or refresh an existing one.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.curve_type_set**( * , type = 'POLY' , use_handles = False )

Change the interpolation method of selected curves.

Parameters:
- type (Literal[Curves Type Items]) – Type, Curve type (optional)
- use_handles ( bool ) – Handles, Take handle information into account in the conversion (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.cyclic_toggle**( )

Toggle whether an active curve is open or closed.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.delete**( )

Erase selected control points or curves.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.draw**( * , error_threshold = 0.0 , fit_method = 'REFIT' , corner_angle = 1.22173 , use_cyclic = True , stroke = None , wait_for_input = True , is_curve_2d = False , bezier_as_nurbs = False )

Draw a curve by making freehand strokes.

Parameters:
- error_threshold ( float ) – Error, Maximum distance allowed from the drawn path (in object units) (in [0, 10], optional)
- fit_method (Literal[Curve Fit Method Items]) – Fit Method, (optional)
- corner_angle ( float ) – Corner Angle, (in [0, 3.14159], optional)
- use_cyclic ( bool ) – Cyclic, (optional)
- stroke ( bpy_prop_collection [ OperatorStrokeElement ]) – Stroke, (optional)
- wait_for_input ( bool ) – Wait for Input, (optional)
- is_curve_2d ( bool ) – Curve 2D, (optional)
- bezier_as_nurbs ( bool ) – As NURBS, (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.duplicate**( )

Replicate selected points or curves.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.duplicate_move**( * , `CURVES_OT`_duplicate = {} , `TRANSFORM_OT`_translate = {} )

Clone selected geometry and instantly move the copy.

Parameters:
- `CURVES_OT`_duplicate ( dict [ str , Any ] ) – Duplicate, Replicate selected points or curves (optional, bpy.ops.curves.duplicate() keyword arguments)
- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Reposition selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.extrude**( )

Extend curves by pulling out selected control points.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.extrude_move**( * , `CURVES_OT`_extrude = {} , `TRANSFORM_OT`_translate = {} )

Extend curve geometry and instantly move the result.

Parameters:
- `CURVES_OT`_extrude ( dict [ str , Any ] ) – Extrude, Extend curves by pulling out selected control points (optional, bpy.ops.curves.extrude() keyword arguments)
- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Reposition selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.handle_type_set**( * , type = 'AUTO' )

Set the handle behavior for Bézier curves.

Parameters:
- type ( Literal [ 'AUTO' , 'VECTOR' , 'ALIGN' , '`FREE_ALIGN`' , '`TOGGLE_FREE_ALIGN`' ] ) – Type, (optional)

- AUTO
Auto – The location is automatically calculated to be smooth.

- VECTOR
Vector – The location is calculated to point to the next/previous control point.

- ALIGN
Align – The location is constrained to point in the opposite direction as the other handle.

- `FREE_ALIGN`
Free – The handle can be moved anywhere, and does not influence the point's other handle.

- `TOGGLE_FREE_ALIGN`
Toggle Free/Align – Replace Free handles with Align, and all Align with Free handles.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.pen**( * , extend = False , deselect = False , toggle = False , deselect_all = False , select_passthrough = False , extrude_point = False , extrude_handle = 'VECTOR' , delete_point = False , insert_point = False , move_segment = False , select_point = False , move_point = False , cycle_handle_type = False , size = 0.01 )

Create and modify Bézier curves using the Pen tool.

Parameters:
- extend ( bool ) – Extend, Extend selection instead of deselecting everything first (optional)
- deselect ( bool ) – Deselect, Remove from selection (optional)
- toggle ( bool ) – Toggle Selection, Toggle the selection (optional)
- deselect_all ( bool ) – Deselect On Nothing, Deselect all when nothing under the cursor (optional)
- select_passthrough ( bool ) – Only Select Unselected, Ignore the select action when the element is already selected (optional)
- extrude_point ( bool ) – Extrude Point, Add a point connected to the last selected point (optional)
- extrude_handle ( Literal [ 'AUTO' , 'VECTOR' ] ) – Extrude Handle Type, Type of the extruded handle (optional)
- delete_point ( bool ) – Delete Point, Delete an existing point (optional)
- insert_point ( bool ) – Insert Point, Insert Point into a curve segment (optional)
- move_segment ( bool ) – Move Segment, Move an existing curve segment (optional)
- select_point ( bool ) – Select Point, Select a point or its handles (optional)
- move_point ( bool ) – Move Point, Move a point or its handles (optional)
- cycle_handle_type ( bool ) – Cycle Handle Type, Cycle between all four handle types (optional)
- size ( float ) – Size, Diameter of new points (in [0, inf], optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.sculptmode_toggle**( )

Switch between normal editing and sculpting modes for curves.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.select_all**( * , action = 'TOGGLE' )

Toggle selection on all control points.

Parameters:
- action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Selection action to execute (optional)

- TOGGLE
Toggle – Toggle selection for all elements.

- SELECT
Select – Select all elements.

- DESELECT
Deselect – Deselect all elements.

- INVERT
Invert – Invert selection of all elements.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.select_ends**( * , amount_start = 0 , amount_end = 1 )

Select terminal points of curves.

Parameters:
- amount_start ( int ) – Amount Front, Number of points to select from the front (in [0, inf], optional)
- amount_end ( int ) – Amount Back, Number of points to select from the back (in [0, inf], optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.select_less**( )

Reduce the selection by one layer.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.select_linked**( )

Select all points within curves that have any selected point.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.select_linked_pick**( * , deselect = False )

Select every point within the curve beneath the cursor.

Parameters:
- deselect ( bool ) – Deselect, Remove linked control points from selection instead (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.select_more**( )

Expand the selection outward by one layer.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.select_random**( * , seed = 0 , probability = 0.5 )

Randomly select points or entire curves.

Parameters:
- seed ( int ) – Seed, Origin for randomization (in [-inf, inf], optional)
- probability ( float ) – Probability, Likelihood that any given point or curve will be chosen (in [0, 1], optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.separate**( )

Move selected geometry into a new object.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.set_selection_domain**( * , domain = 'POINT' )

Switch the selection mode between points and full curves.

Parameters:
- domain (Literal[Attribute Curves Domain Items]) – Domain, (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.snap_curves_to_surface**( * , attach_mode = 'NEAREST' )

Position curves so their starting points rest on a surface mesh.

Parameters:
- attach_mode ( Literal [ 'NEAREST' , 'DEFORM' ] ) – Attach Mode, How to find the point on the surface to attach to (optional)

- NEAREST
Nearest – Find the closest point on the surface for the root point of every curve and move the root there.

- DEFORM
Deform – Re-attach curves to a deformed surface using the existing attachment information. This only works when the topology of the surface mesh has not changed.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.split**( )

Divide selected points into separate segments.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.subdivide**( * , number_cuts = 1 )

Break selected curve segments into finer pieces.

Parameters:
- number_cuts ( int ) – Number of Cuts, (in [1, 1000], optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.surface_set**( )

Designate the active object as the surface for curves and parent them to it.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.switch_direction**( )

Invert the orientation of selected curves.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curves.tilt_clear**( )

Reset the tilt angles of selected control points to zero.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

## Export Anim Operators

### Export Anim Operators

**bpy.ops.export_anim.bvh**( * , filepath = '' , check_existing = True , filter_glob = '*.bvh' , global_scale = 1.0 , frame_start = 0 , frame_end = 0 , rotate_mode = 'NATIVE' , root_transform_only = False , sort_children_by_names = False )

Write motion capture data to a BVH file from an armature.

Parameters:
- filepath ( str ) – File Path, Filepath used for exporting the file (optional, never None)
- check_existing ( bool ) – Check Existing, Check and warn on overwriting existing files (optional)
- filter_glob ( str ) – filter_glob, (optional, never None)
- global_scale ( float ) – Scale, Multiply all distances by this factor (in [0.0001, 1e+06], optional)
- frame_start ( int ) – Start Frame, First frame to export (in [-inf, inf], optional)
- frame_end ( int ) – End Frame, Last frame to export (in [-inf, inf], optional)
- rotate_mode ( Literal [ 'NATIVE' , 'XYZ' , 'XZY' , 'YXZ' , 'YZX' , 'ZXY' , 'ZYX' ] ) – Rotation, Rotation conversion (optional)

- NATIVE
Euler (Native) – Use the rotation order defined in the BVH file.

- XYZ
Euler (XYZ) – Convert rotations to euler XYZ.

- XZY
Euler (XZY) – Convert rotations to euler XZY.

- YXZ
Euler (YXZ) – Convert rotations to euler YXZ.

- YZX
Euler (YZX) – Convert rotations to euler YZX.

- ZXY
Euler (ZXY) – Convert rotations to euler ZXY.

- ZYX
Euler (ZYX) – Convert rotations to euler ZYX.

- root_transform_only ( bool ) – Root Translation Only, Only write out translation channels for the root bone (optional)
- sort_children_by_names ( bool ) – Sort Children By Name, Sort the children of each bone alphabetically (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

File: addons_core/io_anim_bvh/__init__.py:286

## Gizmogroup Operators

### Gizmogroup Operators

bpy.ops.gizmogroup.gizmo_select(*, extend=False, deselect=False, toggle=False, deselect_all=False, select_passthrough=False)

Mark the presently pointed gizmo

Parameters:

- extend (bool) – Extend, Grow the roster in lieu of wiping everything (optional)
- deselect (bool) – Deselect, Purge from the roster (optional)
- toggle (bool) – Toggle Selection, Flip the mark (optional)
- deselect_all (bool) – Deselect On Nothing, Wipe all marks when nothing sits at the cursor (optional)
- select_passthrough (bool) – Only Select Unselected, Skip the mark work when the part is picked already (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.gizmogroup.gizmo_tweak()

Move the functioning gizmo

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

## Operators (bpy.ops)

Python Operator Framework

Describes how to invoke bpy.ops functions with context overrides and execution modes

The bpy.ops interface grants Python-based access to operator functions written in C++, Python, or macro recipes. It accepts only named parameter keywords.

Operators do not yield conventional return codes; instead they yield a collection containing one or more elements from:
{'`RUNNING_MODAL`', 'CANCELLED', 'FINISHED', '`PASS_THROUGH`'}.
Standard outcomes are {'FINISHED'} and {'CANCELLED'} (termination without state change or undo history).

If an operator is cancelled without error reports of type {'ERROR'}, it returns {'CANCELLED'} without exception.
When error messages exist, a RuntimeError fires post-execution with all error content, regardless of completion status.

Invoking an operator in an incompatible context raises RuntimeError. The poll() method allows context verification beforehand.

The identifier in the example (mesh.subdivide) is the bl_idname; bpy.ops provides the Python path.

Keyword and Positional Argument Syntax

Operators use keyword arguments for properties and positional arguments for call modifiers.

Two modifiers are supported (in strict order):

`text
bpy.ops.test.operator(execution_context, undo)
`

- execution_context - enum (str type).
- undo - bool

Both are optional but must appear in this sequence.

`text
import bpy

### Invoke operator.
bpy.ops.mesh.subdivide(number_cuts=3, smoothness=0.5)

### Pre-check with poll() to prevent exception.
if bpy.ops.object.mode_set.poll():
bpy.ops.object.mode_set(mode='EDIT')
`

Context Substitution

It is possible to override context bindings that an operator perceives, allowing operation on specified rather than selected or active data, or to execute within a different UI region.

The context replacements are supplied as keyword arguments whose names match bpy.context members.
For instance, to replace bpy.context.active_object, you supply active_object=object to bpy.types.Context.temp_override.

Note: a duplicate of the live context is nearly always preferable as a baseline (else, you must gather all dependencies yourself).

Note: context member names are the data-access names used in Blender; overrides do not extend to Python-specific methods or functions.

`text
### Delete all scene items rather than current selection.
import bpy
from bpy import context
context_override = context.copy()
context_override["selected_objects"] = list(context.scene.objects)
with context.temp_override(**context_override):
bpy.ops.object.delete()
`

Execution Mode Control

When invoking an operator, you may optionally specify the execution mode.

This mode determines the execution context provided to the operator and whether invoke() runs in addition to execute().

`EXEC_DEFAULT` runs only execute() (the standard), but `INVOKE_DEFAULT` will also call invoke() if available.

Execution modes are:

- `INVOKE_DEFAULT`
- `INVOKE_REGION_WIN`
- `INVOKE_REGION_CHANNELS`
- `INVOKE_REGION_PREVIEW`
- `INVOKE_AREA`
- `INVOKE_SCREEN`
- `EXEC_DEFAULT`
- `EXEC_REGION_WIN`
- `EXEC_REGION_CHANNELS`
- `EXEC_REGION_PREVIEW`
- `EXEC_AREA`
- `EXEC_SCREEN`

`text
### Popup for item collection.
import bpy
bpy.ops.object.collection_instance_add('`INVOKE_DEFAULT`')
`

An operator can also target a particular UI zone by passing the window, area, and sometimes a region.

`text
### Expand 3d view in all windows.
import bpy
from bpy import context

for window in context.window_manager.windows:
screen = window.screen
for area in screen.areas:
if area.type == '`VIEW_3D`':
with context.temp_override(window=window, area=area):
bpy.ops.screen.screen_full_area()
break
`

## Import Anim Operators

### Import Anim Operators

bpy.ops.import_anim. bvh ( * , filepath = '' , filter_glob = '*.bvh' , target = 'ARMATURE' , global_scale = 1.0 , frame_start = 1 , use_fps_scale = False , update_scene_fps = False , update_scene_duration = False , use_cyclic = False , rotate_mode = 'NATIVE' , axis_forward = '-Z' , axis_up = 'Y' )

Load a BVH motion capture file

Parameters :

- filepath ( str ) – File Path, Filepath used for importing the file (optional, never None)

- filter_glob ( str ) – filter_glob, (optional, never None)

- target ( Literal [ 'ARMATURE' , 'OBJECT' ] ) – Target, What to import the capture onto (optional)

- global_scale ( float ) – Scale, Multiply the BVH by this scale (in [0.0001, 1e+06], optional)

- frame_start ( int ) – Start Frame, Frame where the animation begins (in [-inf, inf], optional)

- use_fps_scale ( bool ) – Scale FPS, Convert the BVH frame-rate to the current scene's; otherwise each BVH frame maps straight to one Blender frame (optional)

- update_scene_fps ( bool ) – Update Scene FPS, Switch the scene frame-rate to the BVH file's (this makes 'Scale FPS' a no-op, since the scale becomes 1:1) (optional)

- update_scene_duration ( bool ) – Update Scene Duration, Stretch the scene's length out to the BVH duration (it is never shortened) (optional)

- use_cyclic ( bool ) – Loop, Play the animation on a loop (optional)

- rotate_mode ( Literal [ 'QUATERNION' , 'NATIVE' , 'XYZ' , 'XZY' , 'YXZ' , 'YZX' , 'ZXY' , 'ZYX' ] ) – Rotation, How rotations are converted (optional)

- QUATERNION
Quaternion – Turn rotations into quaternions.

- NATIVE
Euler (Native) – Keep the rotation order from the BVH file.

- XYZ
Euler (XYZ) – Turn rotations into euler XYZ.

- XZY
Euler (XZY) – Turn rotations into euler XZY.

- YXZ
Euler (YXZ) – Turn rotations into euler YXZ.

- YZX
Euler (YZX) – Turn rotations into euler YZX.

- ZXY
Euler (ZXY) – Turn rotations into euler ZXY.

- ZYX
Euler (ZYX) – Turn rotations into euler ZYX.

- axis_forward ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – Forward, (optional)

- axis_up ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – Up, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## Info Operators

### Info Operators

bpy.ops.info. report_copy ( )

Copy selected reports to clipboard

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.info. report_delete ( )

Delete selected reports

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.info. report_replay ( )

Replay selected reports

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.info. reports_display_update ( )

Update the display of reports in Blender UI (internal use)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.info. select_all ( * , action = 'SELECT' )

Change selection of all visible reports

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Which selection action to run (optional)

- TOGGLE
Toggle – Flip the selection state of every element.

- SELECT
Select – Select every element.

- DESELECT
Deselect – Deselect every element.

- INVERT
Invert – Swap which elements are selected.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.info. select_box ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , mode = 'SET' )

Toggle box selection

Parameters :

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Start a fresh selection.

- ADD
Extend – Add to the current selection.

- SUB
Subtract – Remove from the current selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.info. select_pick ( * , report_index = 0 , extend = False )

Select reports by index

Parameters :

- report_index ( int ) – Report, Index of the report (in [0, inf], optional)

- extend ( bool ) – Extend, Add this report to the current selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## See also

- [Anim Operators](anim-operators.md)
