# Grease Pencil Operators (part 3)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

Adjust hue, saturation, and value of vertex colors

Parameters:
- mode ( Literal [ 'STROKE' , 'FILL' , 'BOTH' ] ) – Mode, (optional)
- h ( float ) – Hue, (in [0, 1], optional)
- s ( float ) – Saturation, (in [0, 2], optional)
- v ( float ) – Value, (in [0, 2], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.vertex_color_invert ( * , mode = 'BOTH' )
Reverse RGB color channels

Parameters:
mode ( Literal [ 'STROKE' , 'FILL' , 'BOTH' ] ) – Mode, (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.vertex_color_levels ( * , mode = 'BOTH' , offset = 0.0 , gain = 1.0 )
Rescale vertex color intensity

Parameters:
- mode ( Literal [ 'STROKE' , 'FILL' , 'BOTH' ] ) – Mode, (optional)
- offset ( float ) – Offset, Constant to add to all colors (in [-1, 1], optional)
- gain ( float ) – Gain, Multiplier for all colors (in [0, inf], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.vertex_color_set ( * , mode = 'BOTH' , factor = 1.0 )
Assign the active color to all highlighted vertices

Parameters:
- mode ( Literal [ 'STROKE' , 'FILL' , 'BOTH' ] ) – Mode, (optional)
- factor ( float ) – Factor, Blend ratio (in [0, 1], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.vertex_group_normalize ( )
Scale weights in the active group so the sum is balanced

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.vertex_group_normalize_all ( * , lock_active = True )
Scale all group weights so each vertex sums to 1.0

Parameters:
lock_active ( bool ) – Lock Active, Preserve active group values while rescaling the rest (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.vertex_group_smooth ( * , factor = 0.5 , repeat = 1 )
Blend the weights in the active group

Parameters:
- factor ( float ) – Factor, (in [0, 1], optional)
- repeat ( int ) – Iterations, (in [1, 10000], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.vertexmode_toggle ( * , back = False )
Switch into or out of vertex painting mode for Grease Pencil

Parameters:
back ( bool ) – Return to Previous Mode, Restore the mode before entering vertex painting (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.weight_brush_stroke ( * , stroke = None , mode = 'NORMAL' , brush_toggle = 'None' , pen_flip = False )
Tint vertex weights onto points in the active Grease Pencil object

Parameters:
- stroke ( bpy_prop_collection [ OperatorStrokeElement ]) – Stroke, (optional)
- mode ( Literal [ 'NORMAL' , 'INVERT' ] ) – Stroke Mode, Operation applied during brush motion (optional)
- NORMAL: Apply weight coloring normally
- INVERT: Reverse the weight coloring effect during this stroke
- brush_toggle ( Literal [ 'None' , 'SMOOTH' , 'ERASE' , 'MASK' ] ) – Temporary Brush Toggle Type, Alternate brush active for this stroke only (optional)
- None: Use the current weight tool
- SMOOTH: Temporarily activate smoothing (optional)
- ERASE: Temporarily activate eraser (optional)
- MASK: Temporarily activate masking (optional)
- pen_flip ( bool ) – Pen Flip, Indicates stylus eraser mode engagement (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.weight_invert ( )
Reverse the weight values of the active group

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.weight_sample ( )
Capture the weight value from the point under the cursor

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.weight_toggle_direction ( )
Switch between Add/Subtract modes for weight painting

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.grease_pencil.weightmode_toggle ( * , back = False )
Switch into or out of weight painting mode for Grease Pencil

Parameters:
back ( bool ) – Return to Previous Mode, Restore the mode before entering weight painting (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]
