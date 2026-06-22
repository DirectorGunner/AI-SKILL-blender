# Lattice Operators, Mask Operators, Mball Operators

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Lattice Operators; Mask Operators; Mball Operators.

## Lattice Operators

### Lattice Operators

bpy.ops.lattice. flip ( * , axis = 'U' )

Mirror all control points without inverting the lattice deform

Parameters :

axis ( Literal [ 'U' , 'V' , 'W' ] ) – Flip Axis, Points get mirrored along this axis (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.lattice. make_regular ( )

Set UVW control points a uniform distance apart

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.lattice. select_all ( * , action = 'TOGGLE' )

Change selection of all UVW control points

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

bpy.ops.lattice. select_less ( )

Deselect vertices at the boundary of each selection region

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.lattice. select_mirror ( * , axis = {'X'} , extend = False )

Select mirrored lattice points

Parameters :

- axis (set[Literal[Axis Flag Xyz Items]]) – Axis, (optional)

- extend ( bool ) – Extend, Grow the current selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.lattice. select_more ( )

Select vertices directly linked to already selected ones

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.lattice. select_random ( * , ratio = 0.5 , seed = 0 , action = 'SELECT' )

Randomly select UVW control points

Parameters :

- ratio ( float ) – Ratio, Fraction of items picked at random (in [0, 1], optional)

- seed ( int ) – Random Seed, Seed feeding the random number generator (in [0, inf], optional)

- action ( Literal [ 'SELECT' , 'DESELECT' ] ) – Action, Which selection action to run (optional)

- SELECT
Select – Select every element.

- DESELECT
Deselect – Deselect every element.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.lattice. select_ungrouped ( * , extend = False )

Select vertices without a group

Parameters :

extend ( bool ) – Extend, Grow the current selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## Mask Operators

### Mask Operators

bpy.ops.mask. add_feather_vertex ( * , location = (0.0, 0.0) )

Add vertex to feather

Parameters :

location (mathutils.Vector) – Location, Vertex position in normalized space (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. add_feather_vertex_slide ( * , `MASK_OT`_add_feather_vertex = {} , `MASK_OT`_slide_point = {} )

Add new vertex to feather and slide it

Parameters :

- `MASK_OT`_add_feather_vertex ( dict [ str , Any ] ) – Add Feather Vertex, Add vertex to feather (optional, bpy.ops.mask.add_feather_vertex() keyword arguments)

- `MASK_OT`_slide_point ( dict [ str , Any ] ) – Slide Point, Slide control points (optional, bpy.ops.mask.slide_point() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. add_vertex ( * , location = (0.0, 0.0) )

Add vertex to active spline

Parameters :

location (mathutils.Vector) – Location, Vertex position in normalized space (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. add_vertex_slide ( * , `MASK_OT`_add_vertex = {} , `MASK_OT`_slide_point = {} )

Add new vertex and slide it

Parameters :

- `MASK_OT`_add_vertex ( dict [ str , Any ] ) – Add Vertex, Add vertex to active spline (optional, bpy.ops.mask.add_vertex() keyword arguments)

- `MASK_OT`_slide_point ( dict [ str , Any ] ) – Slide Point, Slide control points (optional, bpy.ops.mask.slide_point() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. copy_splines ( )

Copy the selected splines to the internal clipboard

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. cyclic_toggle ( )

Toggle cyclic for selected splines

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. delete ( * , confirm = True )

Delete selected control points or splines

Parameters :

confirm ( bool ) – Confirm, Ask for confirmation first (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. duplicate ( )

Duplicate selected control points and segments between them

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. duplicate_move ( * , `MASK_OT`_duplicate = {} , `TRANSFORM_OT`_translate = {} )

Duplicate mask and move

Parameters :

- `MASK_OT`_duplicate ( dict [ str , Any ] ) – Duplicate Mask, Duplicate selected control points and segments between them (optional, bpy.ops.mask.duplicate() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. feather_weight_clear ( )

Reset the feather weight to zero

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. handle_type_set ( * , type = 'AUTO' )

Set type of handles for selected control points

Parameters :

type ( Literal [ 'AUTO' , 'VECTOR' , 'ALIGNED' , '`ALIGNED_DOUBLESIDE`' , 'FREE' ] ) – Type, Spline type (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. hide_view_clear ( * , select = True )

Reveal temporarily hidden mask layers

Parameters :

select ( bool ) – Select, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. hide_view_set ( * , unselected = False )

Temporarily hide mask layers

Parameters :

unselected ( bool ) – Unselected, Hide the unselected layers rather than the selected ones (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. layer_move ( * , direction = 'UP' )

Move the active layer up/down in the list

Parameters :

direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Which way to shift the active layer (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. layer_new ( * , name = '' )

Add new mask layer for masking

Parameters :

name ( str ) – Name, Name for the new mask layer (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. layer_remove ( )

Remove mask layer

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. new ( * , name = '' )

Create new mask

Parameters :

name ( str ) – Name, Name for the new mask (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. normals_make_consistent ( )

Recalculate the direction of selected handles

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. parent_clear ( )

Clear the mask's parenting

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. parent_set ( )

Set the mask's parenting

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. paste_splines ( )

Paste splines from the internal clipboard

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. primitive_circle_add ( * , size = 100.0 , location = (0.0, 0.0) )

Add new circle-shaped spline

Parameters :

- size ( float ) – Size, Size of the new primitive (in [-inf, inf], optional)

- location (mathutils.Vector) – Location, Where the new primitive is placed (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. primitive_square_add ( * , size = 100.0 , location = (0.0, 0.0) )

Add new square-shaped spline

Parameters :

- size ( float ) – Size, Size of the new primitive (in [-inf, inf], optional)

- location (mathutils.Vector) – Location, Where the new primitive is placed (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. select ( * , extend = False , deselect = False , toggle = False , deselect_all = False , select_passthrough = False , location = (0.0, 0.0) )

Select spline points

Parameters :

- extend ( bool ) – Extend, Add to the selection rather than clearing it first (optional)

- deselect ( bool ) – Deselect, Take out of the selection (optional)

- toggle ( bool ) – Toggle Selection, Flip the selection state (optional)

- deselect_all ( bool ) – Deselect On Nothing, Clear the selection when nothing sits under the cursor (optional)

- select_passthrough ( bool ) – Only Select Unselected, Skip the select action when the element is already selected (optional)

- location (mathutils.Vector) – Location, Vertex position in normalized space (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. select_all ( * , action = 'TOGGLE' )

Change selection of all curve points

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

bpy.ops.mask. select_box ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , mode = 'SET' )

Select curve points using box selection

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

bpy.ops.mask. select_circle ( * , x = 0 , y = 0 , radius = 25 , wait_for_input = True , mode = 'SET' )

Select curve points using circle selection

Parameters :

- x ( int ) – X, (in [-inf, inf], optional)

- y ( int ) – Y, (in [-inf, inf], optional)

- radius ( int ) – Radius, (in [1, inf], optional)

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

bpy.ops.mask. select_lasso ( * , path = None , use_smooth_stroke = False , smooth_stroke_factor = 0.75 , smooth_stroke_radius = 35 , mode = 'SET' )

Select curve points using lasso selection

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- use_smooth_stroke ( bool ) – Stabilize Stroke, The selection trails the mouse and follows a smoother route (optional)

- smooth_stroke_factor ( float ) – Smooth Stroke Factor, Larger values produce a smoother stroke (in [0.5, 0.99], optional)

- smooth_stroke_radius ( int ) – Smooth Stroke Radius, Shortest distance from the last point before selection carries on (in [10, 200], optional)

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

bpy.ops.mask. select_less ( )

Deselect spline points at the boundary of each selection region

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. select_linked ( )

Select all curve points linked to already selected ones

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. select_linked_pick ( * , deselect = False )

(De)select all points linked to the curve under the mouse cursor

Parameters :

deselect ( bool ) – Deselect, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. select_more ( )

Select more spline points connected to initial selection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. shape_key_clear ( )

Remove mask shape keyframe for active mask layer at the current frame

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. shape_key_feather_reset ( )

Reset feather weights on all selected points animation values

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. shape_key_insert ( )

Insert mask shape keyframe for active mask layer at the current frame

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. shape_key_rekey ( * , location = True , feather = True )

Recalculate animation data on selected points for frames selected in the dopesheet

Parameters :

- location ( bool ) – Location, (optional)

- feather ( bool ) – Feather, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. slide_point ( * , slide_feather = False , is_new_point = False )

Slide control points

Parameters :

- slide_feather ( bool ) – Slide Feather, Try sliding the feather before the vertex (optional)

- is_new_point ( bool ) – Slide New Point, A freshly created vertex is the one being slid (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. slide_spline_curvature ( )

Slide a point on the spline to define its curvature

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mask. switch_direction ( )

Switch direction of selected splines

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## Mball Operators

### Mball Operators

bpy.ops.mball. delete_metaelems ( * , confirm = True )

Delete selected metaball element(s)

Parameters :

confirm ( bool ) – Confirm, Ask for confirmation first (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mball. duplicate_metaelems ( )

Duplicate selected metaball element(s)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mball. duplicate_move ( * , `MBALL_OT`_duplicate_metaelems = {} , `TRANSFORM_OT`_translate = {} )

Make copies of the selected metaball elements and move them

Parameters :

- `MBALL_OT`_duplicate_metaelems ( dict [ str , Any ] ) – Duplicate Metaball Elements, Duplicate selected metaball element(s) (optional, bpy.ops.mball.duplicate_metaelems() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mball. hide_metaelems ( * , unselected = False )

Hide (un)selected metaball element(s)

Parameters :

unselected ( bool ) – Unselected, Hide the unselected elements rather than the selected ones (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mball. reveal_metaelems ( * , select = True )

Reveal all hidden metaball elements

Parameters :

select ( bool ) – Select, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mball. select_all ( * , action = 'TOGGLE' )

Change selection of all metaball elements

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

bpy.ops.mball. select_random_metaelems ( * , ratio = 0.5 , seed = 0 , action = 'SELECT' )

Randomly select metaball elements

Parameters :

- ratio ( float ) – Ratio, Fraction of items picked at random (in [0, 1], optional)

- seed ( int ) – Random Seed, Seed feeding the random number generator (in [0, inf], optional)

- action ( Literal [ 'SELECT' , 'DESELECT' ] ) – Action, Which selection action to run (optional)

- SELECT
Select – Select every element.

- DESELECT
Deselect – Deselect every element.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.mball. select_similar ( * , type = 'TYPE' , threshold = 0.1 )

Select similar metaballs by property types

Parameters :

- type ( Literal [ 'TYPE' , 'RADIUS' , 'STIFFNESS' , 'ROTATION' ] ) – Type, (optional)

- threshold ( float ) – Threshold, (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
