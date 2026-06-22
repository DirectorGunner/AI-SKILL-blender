# Sculpt Operators (part 3)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

- location ( Sequence [ int ] ) – Location, Mouse location (array of 2 items, in [-inf, inf], optional)

- trim_mode ( Literal [ 'DIFFERENCE' , 'UNION' , 'JOIN' ] ) – Trim Mode, (optional)

- DIFFERENCE
Difference – Use a difference boolean operation.

- UNION
Union – Use a union boolean operation.

- JOIN
Join – Join the new mesh as separate geometry, without performing any boolean operation.

- use_cursor_depth ( bool ) – Use Cursor for Depth, Use cursor position and span for the size and placement of the trimming boundary (optional)

- trim_orientation ( Literal [ 'VIEW' , 'SURFACE' ] ) – Shape Orientation, (optional)

- VIEW
View – Use the view to orientate the trimming shape.

- SURFACE
Surface – Use the surface normal to orientate the trimming shape.

- trim_extrude_mode ( Literal [ 'PROJECT' , 'FIXED' ] ) – Extrude Mode, (optional)

- PROJECT
Project – Align trim geometry with the perspective of the current view for a tapered shape.

- FIXED
Fixed – Align trim geometry orthogonally for a shape with 90 degree angles.

- trim_solver ( Literal [ 'EXACT' , 'FLOAT' , 'MANIFOLD' ] ) – Solver, (optional)

- EXACT
Exact – Slower solver with the best results for coplanar faces.

- FLOAT
Float – Simple solver with good performance, without support for overlapping geometry.

- MANIFOLD
Manifold – Fastest solver that works only on manifold meshes but gives better results.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. uv_sculpt_grab ( * , use_invert = False )

Capture UVs

Parameters :

use_invert ( bool ) – Invert, Reverse action during the mark (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. uv_sculpt_pinch ( * , use_invert = False )

Compress UVs

Parameters :

use_invert ( bool ) – Invert, Reverse action during the mark (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. uv_sculpt_relax ( * , use_invert = False , relax_method = 'LAPLACIAN' )

Unwind UVs

Parameters :

- use_invert ( bool ) – Invert, Reverse action during the mark (optional)

- relax_method ( Literal [ 'LAPLACIAN' , 'HC' , 'COTAN' ] ) – Relax Method, Formula used for UV unwinding (optional)

- LAPLACIAN
Laplacian – Use Laplacian method for relaxation.

- HC
HC – Use HC method for relaxation.

- COTAN
Geometry – Use Geometry (cotangent) relaxation, making UVs follow the underlying 3D geometry.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]
