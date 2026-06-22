# Paint Operators (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

- merged ( bool ) – Sample Merged, Acquire the exhibition rendering tint (optional)

- palette ( bool ) – Add to Palette, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. texture_paint_toggle ( ) 

Flip tint manner in 3D observation

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vert_select_all ( * , action = 'TOGGLE' ) 

Modify choosing for every vertices

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Choosing activity to execute (optional)

- TOGGLE
Toggle – Flip choosing for every components.

- SELECT
Select – Opt for every components.

- DESELECT
Deselect – Unselect every components.

- INVERT
Invert – Invert choosing of every components.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vert_select_hide ( * , unselected = False ) 

Conceal chosen vertices

Parameters :

unselected ( bool ) – Unselected, Conceal non-chosen preferentially to chosen vertices (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vert_select_less ( * , face_step = True ) 

Unselect Vertices neighboring to persisting choosing

Parameters :

face_step ( bool ) – Face Step, Similarly unselect faces that just interact at a bend (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vert_select_linked ( ) 

Opt for joined vertices

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vert_select_linked_pick ( * , select = True ) 

Opt for joined vertices below the cursor

Parameters :

select ( bool ) – Select, If to opt for or unselect joined vertices below the cursor (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vert_select_loop ( * , select = True , extend = False ) 

Opt for vertex progression below the cursor

Parameters :

- select ( bool ) – Select, Whether bogus, vertices remain deselected (optional)

- extend ( bool ) – Extend, Broaden the choosing (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vert_select_more ( * , face_step = True ) 

Opt for Vertices neighboring to persisting choosing

Parameters :

face_step ( bool ) – Face Step, Similarly opt for faces that just interact at a bend (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vert_select_ungrouped ( * , extend = False ) 

Opt for vertices deprived of a cluster

Parameters :

extend ( bool ) – Extend, Broaden the choosing (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vertex_color_brightness_contrast ( * , brightness = 0.0 , contrast = 0.0 ) 

Regulate vertex tint glow/distinction

Parameters :

- brightness ( float ) – Brightness, (in [-100, 100], optional)

- contrast ( float ) – Contrast, (in [-100, 100], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vertex_color_dirt ( * , blur_strength = 1.0 , blur_iterations = 1 , clean_angle = 3.14159 , dirt_angle = 0.0 , dirt_only = False , normalize = True ) 

Manufacture a grime mapping progression dependent on concavity

Parameters :

- blur_strength ( float ) – Blur Strength, Blur vigor per single iteration (in [0.01, 1], optional)

- blur_iterations ( int ) – Blur Iterations, Quantity of instances to blur the pigments (amplified blurs more) (in [0, 40], optional)

- clean_angle ( float ) – Highlight Angle, Below 90 restricts the span utilized in the shadowy assortment (in [0, 3.14159], optional)

- dirt_angle ( float ) – Dirt Angle, Below 90 restricts the span utilized in the shadowy assortment (in [0, 3.14159], optional)

- dirt_only ( bool ) – Dirt Only, Do not calculate shines for bulging zones (optional)

- normalize ( bool ) – Normalize, Proportion the pigments, magnifying the distinction (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/vertexpaint_dirt.py:179

bpy.ops.paint. vertex_color_from_weight ( ) 

Exchange energetic strain into monocolor vertex pigments

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vertex_color_hsv ( * , h = 0.5 , s = 1.0 , v = 1.0 ) 

Regulate vertex tint Tonal quality/Vividness/Luminosity

Parameters :

- h ( float ) – Hue, (in [0, 1], optional)

- s ( float ) – Saturation, (in [0, 2], optional)

- v ( float ) – Value, (in [0, 2], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vertex_color_invert ( ) 

Reverse RGB quantities

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vertex_color_levels ( * , offset = 0.0 , gain = 1.0 ) 

Regulate profundities of vertex pigments

Parameters :

- offset ( float ) – Offset, Quantity to include to pigments (in [-1, 1], optional)

- gain ( float ) – Gain, Quantity to increase pigments by (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vertex_color_set ( * , use_alpha = True ) 

Populate the energized vertex tint tier with the operative pigment

Parameters :

use_alpha ( bool ) – Affect Alpha, Establish tint wholly opaque rather than reusing persisting opacity (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vertex_color_smooth ( ) 

Smooth pigments throughout vertices

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vertex_paint ( * , stroke = None , mode = 'NORMAL' , brush_toggle = 'None' , pen_flip = False , override_location = False ) 

Tint a movement in the energized tint characteristic tier

Parameters :

- stroke ( bpy_prop_collection [ OperatorStrokeElement ]) – Stroke, (optional)

- mode ( Literal [ 'NORMAL' , 'INVERT' ] ) – Stroke Mode, Activity executed once a tint movement is created (optional)

- NORMAL
Regular – Applies the brush as normal without modification.

- INVERT
Invert – Reverses the brush's action throughout the stroke.

- brush_toggle ( Literal [ 'None' , 'SMOOTH' , 'ERASE' , 'MASK' ] ) – Temporary Brush Toggle Type, Brush to use for duration of stroke (optional)

- None
None – Leaves the brush unchanged.

- SMOOTH
Smooth – Temporarily switches to the smooth variant for this stroke.

- ERASE
Erase – Temporarily switches to the erase variant for this stroke.

- MASK
Mask – Temporarily switches to the mask variant for this stroke.

- pen_flip ( bool ) – Pen Flip, Whether a tablet's eraser mode is being used (optional)

- override_location ( bool ) – Override Location, Override the given "location" array by recalculating object space positions from the provided "mouse_event" positions (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. vertex_paint_toggle ( ) 

Enters or exits vertex painting mode in the 3D viewport

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. visibility_filter ( * , action = 'GROW' , iterations = 1 , auto_iteration_count = True ) 

Modify the visibility of the current mesh based on a filter operation

Parameters :

- action ( Literal [ 'GROW' , 'SHRINK' ] ) – Action, (optional)

- GROW
Grow Visibility – Expand visible regions by one face according to the mesh's topology.

- SHRINK
Shrink Visibility – Reduce visible regions by one face according to the mesh's topology.

- iterations ( int ) – Iterations, Number of times that the filter is going to be applied (in [1, 100], optional)

- auto_iteration_count ( bool ) – Auto Iteration Count, Use an automatic number of iterations based on the number of vertices of the sculpt (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. visibility_invert ( ) 

Toggle the visibility state of all vertices

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. weight_from_bones ( * , type = 'AUTOMATIC' ) 

Distribute weights across vertex groups based on the armature's active bones, using bone-to-vertex proximity

Parameters :

type ( Literal [ 'AUTOMATIC' , 'ENVELOPES' ] ) – Type, Method to use for assigning weights (optional)

- AUTOMATIC
Automatic – Calculates weights from bones automatically.

- ENVELOPES
From Envelopes – Uses bone envelopes with adjustable radius for weight assignment.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. weight_gradient ( * , type = 'LINEAR' , xstart = 0 , xend = 0 , ystart = 0 , yend = 0 , flip = False , cursor = 5 ) 

Apply a graduated weight transition by drawing a line across selected vertices

Parameters :

- type ( Literal [ 'LINEAR' , 'RADIAL' ] ) – Type, (optional)

- xstart ( int ) – X Start, (in [-inf, inf], optional)

- xend ( int ) – X End, (in [-inf, inf], optional)

- ystart ( int ) – Y Start, (in [-inf, inf], optional)

- yend ( int ) – Y End, (in [-inf, inf], optional)

- flip ( bool ) – Flip, (optional)

- cursor ( int ) – Cursor, Mouse cursor style to use during the modal operator (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. weight_paint ( * , stroke = None , mode = 'NORMAL' , brush_toggle = 'None' , pen_flip = False , override_location = False ) 

Paint a stroke into the currently active vertex group to modify weights

Parameters :

- stroke ( bpy_prop_collection [ OperatorStrokeElement ]) – Stroke, (optional)

- mode ( Literal [ 'NORMAL' , 'INVERT' ] ) – Stroke Mode, Action taken when a paint stroke is made (optional)

- NORMAL
Regular – Applies the brush as normal without modification.

- INVERT
Invert – Reverses the brush's action throughout the stroke.

- brush_toggle ( Literal [ 'None' , 'SMOOTH' , 'ERASE' , 'MASK' ] ) – Temporary Brush Toggle Type, Brush to use for duration of stroke (optional)

- None
None – Leaves the brush unchanged.

- SMOOTH
Smooth – Temporarily switches to the smooth variant for this stroke.

- ERASE
Erase – Temporarily switches to the erase variant for this stroke.

- MASK
Mask – Temporarily switches to the mask variant for this stroke.

- pen_flip ( bool ) – Pen Flip, Whether a tablet's eraser mode is being used (optional)

- override_location ( bool ) – Override Location, Override the given "location" array by recalculating object space positions from the provided "mouse_event" positions (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. weight_paint_toggle ( ) 

Enters or exits weight paint mode in the 3D viewport

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. weight_sample ( ) 

Sample a weight value by clicking in the 3D viewport

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. weight_sample_group ( ) 

Pick a vertex group by positioning the cursor over it in the 3D view

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. weight_set ( ) 

Populate the currently active vertex group with a uniform weight value

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
