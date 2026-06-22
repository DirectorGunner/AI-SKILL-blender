# Palette Operators

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Palette Operators 

bpy.ops.palette. color_add ( ) 

Insert a new color swatch into the current palette

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.palette. color_delete ( ) 

Discard the currently selected color from the palette

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.palette. color_move ( * , type = 'UP' ) 

Shift the currently selected Color higher or lower in the list

Parameters :

type ( Literal [ 'UP' , 'DOWN' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.palette. extract_from_image ( * , threshold = 1 ) 

Scan an Image for all colors and build a Palette from the results

Parameters :

threshold ( int ) – Threshold, (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.palette. join ( * , palette = '' ) 

Combine Palette Swatches

Parameters :

palette ( str ) – Palette, Name of the Palette (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.palette. new ( ) 

Create a fresh palette

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.palette. sort ( * , type = 'HSV' ) 

Organize Palette Colors

Parameters :

type ( Literal [ 'HSV' , 'SVH' , 'VHS' , 'LUMINANCE' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
