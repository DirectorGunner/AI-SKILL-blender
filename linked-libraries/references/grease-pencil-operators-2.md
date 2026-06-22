# Grease Pencil Operators (part 2)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

- extrude_handle ( Literal [ 'AUTO' , 'VECTOR' ] ) – Extrude Handle Type, Behavior for the new handle (optional)
- delete_point ( bool ) – Delete Point, Discard an existing control point (optional)
- insert_point ( bool ) – Insert Point, Embed a point within a curve segment (optional)
- move_segment ( bool ) – Move Segment, Relocate an existing curve segment (optional)
- select_point ( bool ) – Select Point, Highlight a point or its handles (optional)
- move_point ( bool ) – Move Point, Reposition a point or its handles (optional)
- cycle_handle_type ( bool ) – Cycle Handle Type, Rotate through all four handle modes (optional)
- size ( float ) – Size, Diameter of new points (in [0, inf], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.primitive_arc ( * , subdivision = 62 , type = 'ARC' )
Render pre-made Grease Pencil arcs

Parameters:
- subdivision ( int ) – Subdivisions, Segment resolution per curve (in [0, inf], optional)
- type ( Literal [ 'BOX' , 'LINE' , 'POLYLINE' , 'CIRCLE' , 'ARC' , 'CURVE' ] ) – Type, Geometric configuration (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.primitive_box ( * , subdivision = 3 , type = 'BOX' )
Render pre-made Grease Pencil rectangles

Parameters:
- subdivision ( int ) – Subdivisions, Segment resolution per curve (in [0, inf], optional)
- type ( Literal [ 'BOX' , 'LINE' , 'POLYLINE' , 'CIRCLE' , 'ARC' , 'CURVE' ] ) – Type, Geometric configuration (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.primitive_circle ( * , subdivision = 94 , type = 'CIRCLE' )
Render pre-made Grease Pencil circles

Parameters:
- subdivision ( int ) – Subdivisions, Segment resolution per curve (in [0, inf], optional)
- type ( Literal [ 'BOX' , 'LINE' , 'POLYLINE' , 'CIRCLE' , 'ARC' , 'CURVE' ] ) – Type, Geometric configuration (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.primitive_curve ( * , subdivision = 62 , type = 'CURVE' )
Render pre-made Grease Pencil bezier curves

Parameters:
- subdivision ( int ) – Subdivisions, Segment resolution per curve (in [0, inf], optional)
- type ( Literal [ 'BOX' , 'LINE' , 'POLYLINE' , 'CIRCLE' , 'ARC' , 'CURVE' ] ) – Type, Geometric configuration (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.primitive_line ( * , subdivision = 6 , type = 'LINE' )
Render pre-made Grease Pencil line segments

Parameters:
- subdivision ( int ) – Subdivisions, Segment resolution per curve (in [0, inf], optional)
- type ( Literal [ 'BOX' , 'LINE' , 'POLYLINE' , 'CIRCLE' , 'ARC' , 'CURVE' ] ) – Type, Geometric configuration (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.primitive_polyline ( * , subdivision = 6 , type = 'POLYLINE' )
Render pre-made Grease Pencil polyline sequences

Parameters:
- subdivision ( int ) – Subdivisions, Segment resolution per curve (in [0, inf], optional)
- type ( Literal [ 'BOX' , 'LINE' , 'POLYLINE' , 'CIRCLE' , 'ARC' , 'CURVE' ] ) – Type, Geometric configuration (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.relative_layer_mask_add ( * , mode = 'ABOVE' )
Constrain the current layer using an adjacent layer as mask

Parameters:
mode ( Literal [ 'ABOVE' , 'BELOW' ] ) – Mode, Which adjacent layer (higher or lower) serves as the mask (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

File:
startup/bl_operators/grease_pencil.py:39

bpy.ops.grease_pencil.remove_fill_guides ( * , mode = '`ALL_FRAMES`' )
Delete all guide strokes made during the fill process

Parameters:
mode ( Literal [ '`ACTIVE_FRAME`' , '`ALL_FRAMES`' ] ) – Mode, (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.reorder ( * , direction = 'TOP' )
Adjust the stacking order of highlighted strokes

Parameters:
direction ( Literal [ 'TOP' , 'UP' , 'DOWN' , 'BOTTOM' ] ) – Direction, (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.reproject ( * , type = 'VIEW' , keep_original = False , offset = 0.0 )
Flatten strokes onto a target plane as though they were freshly drawn (useful for correcting view changes or repositioning after deformation)

Parameters:
- type ( Literal [ 'FRONT' , 'SIDE' , 'TOP' , 'VIEW' , 'SURFACE' , 'CURSOR' ] ) – Projection Type, (optional)
- FRONT: Map onto the X-Z plane
- SIDE: Map onto the Y-Z plane
- TOP: Map onto the X-Y plane
- VIEW: Map to align with the current camera viewpoint using cursor placement
- SURFACE: Map onto existing scene geometry as if using surface placement
- CURSOR: Map based on 3D cursor orientation
- keep_original ( bool ) – Keep Original, Retain the original strokes and create a repositioned duplicate (optional)
- offset ( float ) – Surface Offset, (in [0, 10], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.reset_uvs ( )
Restore texture coordinates to their default state

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.sculpt_paint ( * , stroke = None , mode = 'NORMAL' , brush_toggle = 'None' , pen_flip = False )
Shape strokes in the active Grease Pencil object

Parameters:
- stroke ( bpy_prop_collection [ OperatorStrokeElement ]) – Stroke, (optional)
- mode ( Literal [ 'NORMAL' , 'INVERT' ] ) – Stroke Mode, Operation applied during brush motion (optional)
- NORMAL: Apply sculpting tool normally
- INVERT: Reverse the sculpting effect during this stroke
- brush_toggle ( Literal [ 'None' , 'SMOOTH' , 'ERASE' , 'MASK' ] ) – Temporary Brush Toggle Type, Alternate brush active for this stroke only (optional)
- None: Use the current sculpting tool
- SMOOTH: Temporarily activate smoothing (optional)
- ERASE: Temporarily activate eraser (optional)
- MASK: Temporarily activate masking (optional)
- pen_flip ( bool ) – Pen Flip, Indicates stylus eraser mode engagement (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.sculptmode_toggle ( * , back = False )
Switch into or out of sculpting mode for Grease Pencil

Parameters:
back ( bool ) – Return to Previous Mode, Restore the mode before entering sculpting (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.select_all ( * , action = 'TOGGLE' )
Highlight or unhighlight all visible strokes

Parameters:
action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Selection operation to perform (optional)
- TOGGLE: Reverse the selection state of every element
- SELECT: Highlight every element
- DESELECT: Unhighlight every element
- INVERT: Reverse the selection state of every element

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.select_alternate ( * , deselect_ends = False )
Highlight every other point in strokes containing selected points

Parameters:
deselect_ends ( bool ) – Deselect Ends, Toggle the first and last point on each stroke (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.select_by_stroke_type ( * , type = 'STROKE' , deselect = False )
Highlight or unhighlight all strokes or fills

Parameters:
- type ( Literal [ 'STROKE' , 'FILL' ] ) – Type, (optional)
- deselect ( bool ) – Deselect, Unhighlight strokes (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.select_ends ( * , amount_start = 0 , amount_end = 1 )
Highlight terminal points of strokes

Parameters:
- amount_start ( int ) – Amount Start, Quantity of points to highlight from the start (in [0, inf], optional)
- amount_end ( int ) – Amount End, Quantity of points to highlight from the end (in [0, inf], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.select_fill ( )
Highlight all curves forming a fill

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.select_less ( )
Contract the selection by one point

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.select_linked ( )
Highlight all points in curves containing any selected point

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.select_more ( )
Expand the selection by one point

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.select_random ( * , ratio = 0.5 , seed = 0 , action = 'SELECT' )
Highlight random points from the current stroke selection

Parameters:
- ratio ( float ) – Ratio, What fraction of items to highlight randomly (in [0, 1], optional)
- seed ( int ) – Random Seed, Initialization value for the randomizer (in [0, inf], optional)
- action ( Literal [ 'SELECT' , 'DESELECT' ] ) – Action, Selection operation to perform (optional)
- SELECT: Highlight selected elements
- DESELECT: Unhighlight selected elements

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.select_similar ( * , mode = 'LAYER' , threshold = 0.1 )
Highlight all strokes matching characteristics of highlighted ones

Parameters:
- mode ( Literal [ 'LAYER' , 'MATERIAL' , '`VERTEX_COLOR`' , 'RADIUS' , 'OPACITY' ] ) – Mode, (optional)
- threshold ( float ) – Threshold, (in [0, inf], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.separate ( * , mode = 'SELECTED' )
Isolate the highlighted geometry into its own Grease Pencil object

Parameters:
mode ( Literal [ 'SELECTED' , 'MATERIAL' , 'LAYER' ] ) – Mode, (optional)
- SELECTED: Isolate highlighted geometry
- MATERIAL: Isolate by material assignment
- LAYER: Isolate by layer membership

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.separate_fills ( * , individual = True )
Detach highlighted strokes from the current fill

Parameters:
individual ( bool ) – Individual, Establish an independent fill for each stroke (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.set_active_material ( )
Assign the currently selected stroke material as the active one

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.set_corner_type ( * , corner_type = 'SHARP' , miter_angle = 0.785398 )
Configure endpoint styling for highlighted points

Parameters:
- corner_type ( Literal [ 'ROUND' , 'FLAT' , 'SHARP' ] ) – Corner Type, (optional)
- miter_angle ( float ) – Miter Cut Angle, All junctions sharper than this angle will be beveled (in [0, 3.14159], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.set_curve_resolution ( * , resolution = 12 )
Configure the interpolation detail for highlighted curves

Parameters:
resolution ( int ) – Resolution, The granularity level to use per curve segment (in [0, 10000], optional)

Returns:
Result of the operator call.
Return type:

set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.set_curve_type ( * , type = 'POLY' , use_handles = False )
Designate the interpolation mode for highlighted curves

Parameters:
- type (Literal[Curves Type Items]) – Type, Spline interpolation mode (optional)
- use_handles ( bool ) – Handles, Account for handle geometry during the conversion (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.set_handle_type ( * , type = 'AUTO' )
Configure handle behavior for Bézier curves

Parameters:
type ( Literal [ 'AUTO' , 'VECTOR' , 'ALIGN' , '`FREE_ALIGN`' , '`TOGGLE_FREE_ALIGN`' ] ) – Type, (optional)
- AUTO: Positioning is computed automatically for smoothness
- VECTOR: Positioning follows the direction toward the adjacent control point
- ALIGN: Handle is mirrored in direction opposite to the other handle
- `FREE_ALIGN`: Handle moves independently without affecting the paired handle
- `TOGGLE_FREE_ALIGN`: Swap free handles with aligned ones and vice versa

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.set_material ( * , slot = 'DEFAULT' )
Establish the working material

Parameters:
slot ( Literal [ 'DEFAULT' ] ) – Material Slot, (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.set_selection_mode ( * , mode = 'POINT' )
Switch the selection paradigm for Grease Pencil strokes

Parameters:
mode (Literal[Grease Pencil Selectmode Items]) – Mode, (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.set_start_point ( )
Choose which point commences the curve

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.set_stroke_type ( * , type = 'STROKE' )
Assign a classification to highlighted strokes (lines, fills, or both)

Parameters:
type ( Literal [ 'STROKE' , 'FILL' , 'BOTH' ] ) – Type, (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.set_uniform_opacity ( * , opacity_stroke = 1.0 , opacity_fill = 0.5 )
Make all stroke points the same opacity value

Parameters:
- opacity_stroke ( float ) – Stroke Opacity, (in [0, 1], optional)
- opacity_fill ( float ) – Fill Opacity, (in [0, 1], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.set_uniform_thickness ( * , thickness = 0.1 )
Make all stroke points the same thickness value

Parameters:
thickness ( float ) – Thickness, Width setting (in [0, 1000], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.snap_cursor_to_selected ( )
Place the cursor at the centroid of highlighted points

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.snap_to_cursor ( * , use_offset = True )
Reposition highlighted points or strokes at the cursor site

Parameters:
use_offset ( bool ) – With Offset, Move the full stroke as a unit instead of just individual points (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.snap_to_grid ( )
Align highlighted points to the nearest grid intersection

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.stroke_material_set ( * , material = '' )
Apply the working material slot to highlighted strokes

Parameters:
material ( str ) – Material, Label of the material (optional, never None)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.stroke_merge_by_distance ( * , threshold = 0.001 , use_unselected = False )
Consolidate points based on proximity

Parameters:
- threshold ( float ) – Threshold, (in [0, 100], optional)
- use_unselected ( bool ) – Unselected, Include the full stroke rather than only highlighted points (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.stroke_reset_vertex_color ( * , mode = 'BOTH' )
Restore default color values for all or certain strokes

Parameters:
mode ( Literal [ 'STROKE' , 'FILL' , 'BOTH' ] ) – Mode, (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.stroke_simplify ( * , factor = 0.01 , length = 0.05 , distance = 0.01 , steps = 1 , mode = 'FIXED' )
Reduce the number of points in highlighted strokes

Parameters:
- factor ( float ) – Factor, (in [0, 100], optional)
- length ( float ) – Length, (in [0, 100], optional)
- distance ( float ) – Distance, (in [0, 100], optional)
- steps ( int ) – Steps, (in [0, 50], optional)
- mode ( Literal [ 'FIXED' , 'ADAPTIVE' , 'SAMPLE' , 'MERGE' ] ) – Mode, Algorithm for point reduction (optional)
- FIXED: Discard alternating points while preserving extremes
- ADAPTIVE: Apply Ramer-Douglas-Peucker to smooth while keeping shape features
- SAMPLE: Re-tessellate with segments of the specified gap
- MERGE: Consolidate points closer than a given threshold

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.stroke_smooth ( * , iterations = 10 , factor = 1.0 , smooth_ends = False , keep_shape = False , smooth_position = True , smooth_radius = True , smooth_opacity = False )
Reduce roughness in highlighted strokes

Parameters:
- iterations ( int ) – Iterations, (in [1, 100], optional)
- factor ( float ) – Factor, (in [0, 1], optional)
- smooth_ends ( bool ) – Smooth Endpoints, (optional)
- keep_shape ( bool ) – Keep Shape, (optional)
- smooth_position ( bool ) – Position, (optional)
- smooth_radius ( bool ) – Radius, (optional)
- smooth_opacity ( bool ) – Opacity, (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.stroke_split ( )
Isolate highlighted points into a separate stroke

Returns:

Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.stroke_subdivide ( * , number_cuts = 1 , only_selected = True )
Insert points halfway between consecutive highlighted points

Parameters:
- number_cuts ( int ) – Number of Cuts, (in [1, 32], optional)
- only_selected ( bool ) – Selected Points, Apply smoothing only to highlighted points (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.stroke_subdivide_smooth ( * , `GREASE_PENCIL_OT`_stroke_subdivide = {} , `GREASE_PENCIL_OT`_stroke_smooth = {} )
Add intermediate points and then blend them

Parameters:
- `GREASE_PENCIL_OT`_stroke_subdivide ( dict [ str , Any ] ) – Subdivide Stroke, Insert points between continuous highlighted points (optional, bpy.ops.grease_pencil.stroke_subdivide() keyword arguments)
- `GREASE_PENCIL_OT`_stroke_smooth ( dict [ str , Any ] ) – Smooth Stroke, Reduce roughness in highlighted strokes (optional, bpy.ops.grease_pencil.stroke_smooth() keyword arguments)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.stroke_switch_direction ( )
Reverse the progression order of points in highlighted strokes

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.stroke_trim ( * , path = None , use_smooth_stroke = False , smooth_stroke_factor = 0.75 , smooth_stroke_radius = 35 )
Erase stroke points lying between crossing segments

Parameters:
- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)
- use_smooth_stroke ( bool ) – Stabilize Stroke, Apply delayed smoothing to the selection trace (optional)
- smooth_stroke_factor ( float ) – Smooth Stroke Factor, Higher settings yield smoother traces (in [0.5, 0.99], optional)
- smooth_stroke_radius ( int ) – Smooth Stroke Radius, Minimum distance traveled before registering movement (in [10, 200], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.texture_gradient ( * , xstart = 0 , xend = 0 , ystart = 0 , yend = 0 , flip = False , cursor = 5 )
Draw a trajectory to apply gradient texture to highlighted strokes

Parameters:
- xstart ( int ) – X Start, (in [-inf, inf], optional)
- xend ( int ) – X End, (in [-inf, inf], optional)
- ystart ( int ) – Y Start, (in [-inf, inf], optional)
- yend ( int ) – Y End, (in [-inf, inf], optional)
- flip ( bool ) – Flip, (optional)
- cursor ( int ) – Cursor, Pointer appearance during modal operation (in [0, inf], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.trace_image ( * , target = 'NEW' , threshold = 0.5 , turnpolicy = 'MINORITY' , mode = 'SINGLE' , use_current_frame = True , frame_number = 0 )
Derive Grease Pencil strokes from raster imagery

Parameters:
- target ( Literal [ 'NEW' , 'SELECTED' ] ) – Target Object, Destination Grease Pencil (optional)
- threshold ( float ) – Color Threshold, Luminance boundary for stroke generation (in [0, 1], optional)
- turnpolicy ( Literal [ 'FOREGROUND' , 'BACKGROUND' , 'LEFT' , 'RIGHT' , 'MINORITY' , 'MAJORITY' , 'RANDOM' ] ) – Turn Policy, Strategy for resolving ambiguities during path decomposition (optional)
- FOREGROUND: Favor linking of foreground regions
- BACKGROUND: Favor linking of background regions
- LEFT: Always turn left
- RIGHT: Always turn right
- MINORITY: Connect the less-common neighboring color
- MAJORITY: Connect the more-common neighboring color
- RANDOM: Select pseudo-randomly
- mode ( Literal [ 'SINGLE' , 'SEQUENCE' ] ) – Mode, Whether to process one or a full sequence (optional)
- SINGLE: Convert the current image frame only
- SEQUENCE: Convert all sequential frames
- use_current_frame ( bool ) – Start At Current Frame, Begin conversion at the active image frame (optional)
- frame_number ( int ) – Trace Frame, Index of the single frame to trace, or zero to trace all (in [0, 9999], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.vertex_brush_stroke ( * , stroke = None , mode = 'NORMAL' , brush_toggle = 'None' , pen_flip = False )
Paint color onto vertex data in the active Grease Pencil object

Parameters:
- stroke ( bpy_prop_collection [ OperatorStrokeElement ]) – Stroke, (optional)
- mode ( Literal [ 'NORMAL' , 'INVERT' ] ) – Stroke Mode, Operation applied during brush motion (optional)
- NORMAL: Apply vertex coloring normally
- INVERT: Reverse the vertex coloring effect during this stroke
- brush_toggle ( Literal [ 'None' , 'SMOOTH' , 'ERASE' , 'MASK' ] ) – Temporary Brush Toggle Type, Alternate brush active for this stroke only (optional)
- None: Use the current vertex coloring tool
- SMOOTH: Temporarily activate smoothing (optional)
- ERASE: Temporarily activate eraser (optional)
- MASK: Temporarily activate masking (optional)
- pen_flip ( bool ) – Pen Flip, Indicates stylus eraser mode engagement (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.vertex_color_brightness_contrast ( * , mode = 'BOTH' , brightness = 0.0 , contrast = 0.0 )
Modify brightness and contrast of vertex tones

Parameters:
- mode ( Literal [ 'STROKE' , 'FILL' , 'BOTH' ] ) – Mode, (optional)
- brightness ( float ) – Brightness, (in [-1, 1], optional)
- contrast ( float ) – Contrast, (in [-1, 1], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.vertex_color_hsv ( * , mode = 'BOTH' , h = 0.5 , s = 1.0 , v = 1.0 )
