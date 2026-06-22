# Curve Operators

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

### Curve Operators

**bpy.ops.curve.cyclic_toggle**( * , direction = '`CYCLIC_U`' )

Toggle whether the active spline is open or closed.

Parameters:
- direction ( Literal [ '`CYCLIC_U`' , '`CYCLIC_V`' ] ) – Direction, Axis along which to make the surface cyclic (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.de_select_first**( )

Toggle selection state of the first point on each visible NURBS curve.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.de_select_last**( )

Toggle selection state of the last point on each visible NURBS curve.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.decimate**( * , ratio = 1.0 )

Reduce the number of points on selected curves.

Parameters:
- ratio ( float ) – Ratio, Proportion to retain, from 0 to 1 (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.delete**( * , type = 'VERT' )

Remove selected control points or curve segments.

Parameters:
- type ( Literal [ 'VERT' , 'SEGMENT' ] ) – Type, What to remove (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.dissolve_verts**( )

Remove selected control points while smoothing adjacent handles.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.draw**( * , error_threshold = 0.0 , fit_method = 'REFIT' , corner_angle = 1.22173 , use_cyclic = True , stroke = None , wait_for_input = True )

Create a spline by sketching freehand strokes.

Parameters:
- error_threshold ( float ) – Error, Maximum distance allowed from the drawn path (in object units) (in [0, 10], optional)
- fit_method (Literal[Curve Fit Method Items]) – Fit Method, (optional)
- corner_angle ( float ) – Corner Angle, (in [0, 3.14159], optional)
- use_cyclic ( bool ) – Cyclic, (optional)
- stroke ( bpy_prop_collection [ OperatorStrokeElement ]) – Stroke, (optional)
- wait_for_input ( bool ) – Wait for Input, (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.duplicate**( )

Create a copy of selected control points.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.duplicate_move**( * , `CURVE_OT`_duplicate = {} , `TRANSFORM_OT`_translate = {} )

Duplicate curve points and instantly move them.

Parameters:
- `CURVE_OT`_duplicate ( dict [ str , Any ] ) – Duplicate Curve, Create a copy of selected control points (optional, bpy.ops.curve.duplicate() keyword arguments)
- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Reposition selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.extrude**( * , mode = 'TRANSLATION' )

Extend a spline by pulling out selected control points.

Parameters:
- mode (Literal[Transform Mode Type Items]) – Mode, (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.extrude_move**( * , `CURVE_OT`_extrude = {} , `TRANSFORM_OT`_translate = {} )

Extend curve points and instantly move the new geometry.

Parameters:
- `CURVE_OT`_extrude ( dict [ str , Any ] ) – Extrude, Extend a spline by pulling out selected control points (optional, bpy.ops.curve.extrude() keyword arguments)
- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Reposition selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.handle_type_set**( * , type = 'AUTOMATIC' )

Change how control points influence the curve shape through handle types.

Parameters:
- type ( Literal [ 'AUTOMATIC' , 'VECTOR' , 'ALIGNED' , '`FREE_ALIGN`' , '`TOGGLE_FREE_ALIGN`' ] ) – Type, Spline type (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.hide**( * , unselected = False )

Conceal control points from view.

Parameters:
- unselected ( bool ) – Unselected, Hide unselected rather than selected (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.make_segment**( )

Connect the endpoints of two separate curves together.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.match_texture_space**( )

Align the texture space with the object's bounding box.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.normals_make_consistent**( * , calc_length = False )

Reorient handles so they point in a uniform direction.

Parameters:
- calc_length ( bool ) – Length, Recompute handle magnitudes (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.pen**( * , extend = False , deselect = False , toggle = False , deselect_all = False , select_passthrough = False , extrude_point = False , extrude_handle = 'VECTOR' , delete_point = False , insert_point = False , move_segment = False , select_point = False , move_point = False , close_spline = True , close_spline_method = 'OFF' , toggle_vector = False , cycle_handle_type = False )

Create and modify curves using the Pen tool.

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
- close_spline ( bool ) – Close Spline, Make a spline cyclic by clicking endpoints (optional)
- close_spline_method ( Literal [ 'OFF' , '`ON_PRESS`' , '`ON_CLICK`' ] ) – Close Spline Method, The condition for close spline to activate (optional)

- OFF
None.

- `ON_PRESS`
On Press – Move handles after closing the spline.

- `ON_CLICK`
On Click – Spline closes on release if not dragged.

- toggle_vector ( bool ) – Toggle Vector, Toggle between Vector and Auto handles (optional)
- cycle_handle_type ( bool ) – Cycle Handle Type, Cycle between all four handle types (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.primitive_bezier_circle_add**( * , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Insert a new Bézier-based circular shape.

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

**bpy.ops.curve.primitive_bezier_curve_add**( * , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Insert a new Bézier spline.

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

**bpy.ops.curve.primitive_nurbs_circle_add**( * , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Insert a new NURBS circular shape.

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

**bpy.ops.curve.primitive_nurbs_curve_add**( * , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Insert a new NURBS spline.

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

**bpy.ops.curve.primitive_nurbs_path_add**( * , radius = 1.0 , enter_editmode = False , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) )

Insert a new path curve.

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

**bpy.ops.curve.radius_set**( * , radius = 1.0 )

Control tapering by setting thickness at each point.

Parameters:
- radius ( float ) – Radius, (in [0, inf], optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.reveal**( * , select = True )

Restore hidden control points to visibility.

Parameters:
- select ( bool ) – Select, (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.select_all**( * , action = 'TOGGLE' )

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

**bpy.ops.curve.select_less**( )

Reduce the selection, removing points at its edges.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.select_linked**( )

Select all control points connected to the current selection.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.select_linked_pick**( * , deselect = False )

Select all control points in the same curve as the pointed item.

Parameters:
- deselect ( bool ) – Deselect, Remove linked control points from selection instead (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.select_more**( )

Expand the selection to include adjacent points.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.select_next**( )

Select control points that follow the current selection along the curves.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.select_nth**( * , skip = 1 , nth = 1 , offset = 0 )

Toggle selection on every nth point in a regular pattern.

Parameters:
- skip ( int ) – Deselected, Number of deselected elements in the repetitive sequence (in [1, inf], optional)
- nth ( int ) – Selected, Number of selected elements in the repetitive sequence (in [1, inf], optional)
- offset ( int ) – Offset, Offset from the starting point (in [-inf, inf], optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.select_previous**( )

Select control points that precede the current selection along the curves.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.select_random**( * , ratio = 0.5 , seed = 0 , action = 'SELECT' )

Select a random subset of control points.

Parameters:
- ratio ( float ) – Ratio, Proportion of items to randomly select (in [0, 1], optional)
- seed ( int ) – Random Seed, Initialization value for the random number generator (in [0, inf], optional)
- action ( Literal [ 'SELECT' , 'DESELECT' ] ) – Action, Selection action to execute (optional)

- SELECT
Select – Select all elements.

- DESELECT
Deselect – Deselect all elements.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.select_row**( )

Select a line of control points through the active point. Use again to alternate between U/V directions.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.select_similar**( * , type = 'WEIGHT' , compare = 'EQUAL' , threshold = 0.1 )

Select curve points that share a similar attribute value.

Parameters:
- type ( Literal [ 'TYPE' , 'RADIUS' , 'WEIGHT' , 'DIRECTION' ] ) – Type, (optional)
- compare ( Literal [ 'EQUAL' , 'GREATER' , 'LESS' ] ) – Compare, (optional)
- threshold ( float ) – Threshold, (in [0, inf], optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.separate**( )

Break apart selected control points into their own object.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.shade_flat**( )

Apply flat shading to the surface.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.shade_smooth**( )

Apply smooth shading to the surface.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.shortest_path_pick**( )

Select the shortest path between two chosen points.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.smooth**( )

Reduce the angles at selected control points.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.smooth_radius**( )

Interpolate thickness values across selected points.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.smooth_tilt**( )

Interpolate the tilt angles across selected points.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.smooth_weight**( )

Interpolate the weight values across selected points.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.spin**( * , center = (0.0, 0.0, 0.0) , axis = (0.0, 0.0, 0.0) )

Extend the selected edge row by revolving it around a pivot.

Parameters:
- center (mathutils.Vector) – Center, Center in global view space (array of 3 items, in [-inf, inf], optional)
- axis (mathutils.Vector) – Axis, Axis in global view space (array of 3 items, in [-1, 1], optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.spline_type_set**( * , type = 'POLY' , use_handles = False )

Modify the spline to use a different type.

Parameters:
- type ( Literal [ 'POLY' , 'BEZIER' , 'NURBS' ] ) – Type, Spline type (optional)
- use_handles ( bool ) – Handles, Use handles when converting Bézier curves into polygons (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.spline_weight_set**( * , weight = 1.0 )

Assign softbody influence weights to selected control points.

Parameters:
- weight ( float ) – Weight, (in [0, 1], optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.split**( )

Divide selected control points from unselected ones.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.subdivide**( * , number_cuts = 1 )

Divide selected curve segments into smaller pieces.

Parameters:
- number_cuts ( int ) – Number of Cuts, (in [1, 1000], optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.switch_direction**( )

Reverse the direction of selected curves.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.tilt_clear**( )

Reset the tilt angles of selected control points to zero.

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

**bpy.ops.curve.vertex_add**( * , location = (0.0, 0.0, 0.0) )

Insert a fresh control point and optionally connect it to the last selected endpoint.

Parameters:
- location (mathutils.Vector) – Location, Where to add the new vertex (array of 3 items, in [-inf, inf], optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]
