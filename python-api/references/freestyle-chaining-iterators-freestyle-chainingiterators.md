# Freestyle Chaining Iterators Freestyle Chainingiterators, Freestyle Module Freestyle, Gpu Matrix Utilities Gpu Matrix, Gpu Select Utilities Gpu Select ...

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Freestyle Chaining Iterators (freestyle.chainingiterators); Freestyle Module (freestyle); GPU Matrix Utilities (gpu.matrix); GPU Select Utilities (gpu.select); GPU State Utilities (gpu.state); gpu_extras submodule (gpu_extras.batch); Blender 5.1 Python API Documentation; Gotchas; BVHTree Utilities (mathutils.bvhtree).

## Freestyle Chaining Iterators (freestyle.chainingiterators)

### Freestyle Chaining Iterators (freestyle.chainingiterators) 

The chaining iterators gathered here drive the chaining stage, where feature edges are joined end to end into long strokes according to whichever chaining rules have been picked. Beyond that, the module doubles as a set of worked samples showing how to author chaining iterators in Python.

class freestyle.chainingiterators. ChainPredicateIterator 

Class hierarchy: freestyle.types.Iterator >
freestyle.types.ViewEdgeIterator >
freestyle.types.ChainingIterator >
ChainPredicateIterator

A flexible ViewEdge iterator whose behaviour you steer yourself, assembled out of one unary and one binary predicate. The unary test runs first against every candidate next ViewEdge, retaining only those that meet its constraint. The binary test then compares the current ViewEdge against each survivor of that first pass. Whichever ViewEdge clears both tests becomes the next one in the chain; should no candidate satisfy the pair of predicates, None comes back instead.

__init__ ( upred , bpred , restrict_to_selection = True , restrict_to_unvisited = True , begin = None , orientation = True ) 

__init__ ( brother )

Constructs a ChainPredicateIterator either from a unary predicate, a binary predicate, a seed ViewEdge and its orientation, or via the copy constructor.

Parameters :

- upred (freestyle.types.UnaryPredicate1D) – The unary test the following ViewEdge is required to pass.

- bpred (freestyle.types.BinaryPredicate1D) – The binary test the following ViewEdge has to pass when paired with the ViewEdge currently pointed at.

- restrict_to_selection ( bool ) – Whether chaining is kept confined to the pool of selected ViewEdges or allowed to leave it.

- restrict_to_unvisited ( bool ) – Whether a ViewEdge already used in a chain should be skipped or reused.

- begin (freestyle.types.ViewEdge | None) – The ViewEdge at which iteration kicks off.

- orientation ( bool ) – When true, the search for the next ViewEdge runs among those surrounding the ending ViewVertex of begin; when false, it runs over the ViewEdges around that same ending ViewVertex of begin.

- brother (ChainPredicateIterator) – A ChainPredicateIterator object.

class freestyle.chainingiterators. ChainSilhouetteIterator 

Class hierarchy: freestyle.types.Iterator >
freestyle.types.ViewEdgeIterator >
freestyle.types.ChainingIterator >
ChainSilhouetteIterator

A ViewEdge iterator built to track ViewEdges in the most natural way, for instance continuing along visible ViewEdges that share the same nature. The moment either the nature or the visibility shifts, iteration halts (the pointed ViewEdge is set to 0). Where a ViewEdge counts as both Silhouette and Crease, the silhouette criterion takes priority over the crease one.

__init__ ( restrict_to_selection = True , begin = None , orientation = True ) 

__init__ ( brother )

Constructs a ChainSilhouetteIterator from the seed ViewEdge that iteration begins on plus its orientation, or through the copy constructor.

Parameters :

- restrict_to_selection ( bool ) – Whether chaining is kept confined to the pool of selected ViewEdges or allowed to leave it.

- begin (freestyle.types.ViewEdge | None) – The ViewEdge at which iteration kicks off.

- orientation ( bool ) – When true, the search for the next ViewEdge runs among those surrounding the ending ViewVertex of begin; when false, it runs over the ViewEdges around that same ending ViewVertex of begin.

- brother (ChainSilhouetteIterator) – A ChainSilhouetteIterator object.

class freestyle.chainingiterators. pyChainSilhouetteIterator 

A natural chaining iterator that traces edges sharing the same nature along an object's topology, favouring silhouettes first, then borders, then suggestive contours, and finally every remaining edge type. Each ViewEdge gets chained a single time only.

init ( ) 

traverse ( iter ) 

class freestyle.chainingiterators. pyChainSilhouetteGenericIterator 

A natural chaining iterator that traces edges sharing the same nature along an object's topology, favouring silhouettes first, then borders, then suggestive contours, and finally every remaining edge type.

__init__ ( self , stayInSelection = True , stayInUnvisited = True ) 

Builds a pyChainSilhouetteGenericIterator object.

Parameters :

- stayInSelection ( bool ) – True when leaving the selection is permitted

- stayInUnvisited ( bool ) – Whether one ViewEdge may be chained more than once

init ( ) 

traverse ( iter ) 

class freestyle.chainingiterators. pyExternalContourChainingIterator 

Performs chaining along the external contour

checkViewEdge ( ve , orientation ) 

init ( ) 

traverse ( iter ) 

class freestyle.chainingiterators. pySketchyChainSilhouetteIterator 

A natural chaining iterator with a sketchy, repeated-pass touch: the same ViewEdge is chained several times over to produce a sketch-like look.

__init__ ( self , nRounds = 3 , stayInSelection = True ) 

Builds a pySketchyChainSilhouetteIterator object.

Parameters :

- nRounds ( int ) – How many passes each ViewEdge is chained for.

- stayInSelection ( bool ) – when False, edges beyond the selection are eligible for chaining.

init ( ) 

make_sketchy ( ve ) 

Produces the sketchy look by sending the chain back to run from its start once more. (loops over itself again)

traverse ( iter ) 

class freestyle.chainingiterators. pySketchyChainingIterator 

A chaining iterator meant for the sketchy style: it chains a single ViewEdge repeatedly so that several strokes end up drawn per ViewEdge.

init ( ) 

traverse ( iter ) 

class freestyle.chainingiterators. pyFillOcclusionsRelativeChainingIterator 

A chaining iterator that closes up small occlusions

__init__ ( self , percent ) 

Builds a pyFillOcclusionsRelativeChainingIterator object.

Parameters :

percent ( float ) – How long the occluded section may be, stated as a fraction of the whole chain's length.

init ( ) 

traverse ( iter ) 

class freestyle.chainingiterators. pyFillOcclusionsAbsoluteChainingIterator 

A chaining iterator that closes up small occlusions

__init__ ( self , length ) 

Builds a pyFillOcclusionsAbsoluteChainingIterator object.

Parameters :

length ( int ) – How long, in pixels, the occluded section is allowed to be.

init ( ) 

traverse ( iter ) 

class freestyle.chainingiterators. pyFillOcclusionsAbsoluteAndRelativeChainingIterator 

A chaining iterator that closes up small occlusions no matter what the selection is.

__init__ ( self , percent , l ) 

Builds a pyFillOcclusionsAbsoluteAndRelativeChainingIterator object.

Parameters :

- percent ( float ) – How long the occluded section may be, given as a fraction of the entire chain's length.

- l ( float ) – Absolute length.

init ( ) 

traverse ( iter )

class freestyle.chainingiterators. pyFillQi0AbsoluteAndRelativeChainingIterator 

A chaining iterator that closes up small occlusions irrespective of the selection.

__init__ ( self , percent , l ) 

Builds a pyFillQi0AbsoluteAndRelativeChainingIterator object.

Parameters :

- percent ( float ) – How long the occluded section may be, given as a fraction of the entire chain's length.

- l ( float ) – Absolute length.

init ( ) 

traverse ( iter ) 

class freestyle.chainingiterators. pyNoIdChainSilhouetteIterator 

A natural chaining iterator that traces edges sharing the same nature along an object's topology, favouring silhouettes first, then borders, then suggestive contours, and finally every remaining edge type. The same ViewEdge is never chained twice.

__init__ ( self , stayInSelection = True ) 

Builds a pyNoIdChainSilhouetteIterator object.

Parameters :

stayInSelection ( bool ) – True when leaving the selection is permitted

init ( ) 

traverse ( iter )

## Freestyle Module (freestyle)

### Freestyle Module (freestyle) 

This module supplies the data types for view map components (the 0D and 1D elements), the base classes you subclass to define line stylization rules (predicates, functions, chaining iterators, and stroke shaders), and a handful of helper functions for writing style modules.

## GPU Matrix Utilities (gpu.matrix)

### GPU Matrix Utilities (gpu.matrix)

This module hands you control over the matrix stack.

gpu.matrix. get_model_view_matrix ( )

Hands back a copy of the model-view matrix.

Returns :

A 4x4 view matrix.

Return type :

mathutils.Matrix

gpu.matrix. get_normal_matrix ( )

Hands back a copy of the normal matrix.

Returns :

A 3x3 normal matrix.

Return type :

mathutils.Matrix

gpu.matrix. get_projection_matrix ( )

Hands back a copy of the projection matrix.

Returns :

A 4x4 projection matrix.

Return type :

mathutils.Matrix

gpu.matrix. load_identity ( )

Place an identity matrix onto the stack.

gpu.matrix. load_matrix ( matrix )

Place a matrix onto the stack.

Parameters :

matrix (mathutils.Matrix) – A 4x4 matrix.

gpu.matrix. load_projection_matrix ( matrix )

Place a projection matrix onto the stack.

Parameters :

matrix (mathutils.Matrix) – A 4x4 matrix.

gpu.matrix. multiply_matrix ( matrix )

Multiply against the matrix currently on the stack.

Parameters :

matrix (mathutils.Matrix) – A 4x4 matrix.

gpu.matrix. pop ( )

Drop the most recent model-view matrix off the stack.

gpu.matrix. pop_projection ( )

Drop the most recent projection matrix off the stack.

gpu.matrix. push ( )

Push a new entry onto the model-view matrix stack.

gpu.matrix. push_pop ( )

A context manager that keeps push and pop calls balanced, even when something throws.

Returns :

The context manager.

Return type :

gpu.types.MatrixStackContext

gpu.matrix. push_pop_projection ( )

A context manager that keeps push and pop calls balanced, even when something throws.

Returns :

The context manager.

Return type :

gpu.types.MatrixStackContext

gpu.matrix. push_projection ( )

Push a new entry onto the projection matrix stack.

gpu.matrix. reset ( )

Clear the stack and reset it to identity.

gpu.matrix. scale ( scale )

Scale the matrix currently on the stack.

Parameters :

scale ( Sequence [ float ] ) – Scale the current stack matrix with 2 or 3 floats.

gpu.matrix. scale_uniform ( scale )

Apply a uniform scale to the matrix currently on the stack.

Parameters :

scale ( float ) – Uniform scale factor.

gpu.matrix. translate ( offset )

Translate the matrix currently on the stack.

Parameters :

offset ( Sequence [ float ] ) – Translate the current stack matrix with 2 or 3 floats.

## GPU Select Utilities (gpu.select)

### GPU Select Utilities (gpu.select)

This module opens up access to selection.

gpu.select. load_id ( id )

Assign the selection ID.

Parameters :

id ( int ) – Number (32-bit uint).

## GPU State Utilities (gpu.state)

### GPU State Utilities (gpu.state)

This module opens up access to the gpu state.

gpu.state. active_framebuffer_get ( )

Give back the frame-buffer active in the context.

Returns :

The active framebuffer.

Return type :

gpu.types.GPUFrameBuffer

gpu.state. blend_get ( )

The blending equation in force right now.

Returns :

The current blend mode.

Return type :

str

gpu.state. blend_set ( mode )

Sets the blending equation of the fixed pipeline.

Parameters :

mode ( Literal [ 'NONE' , 'ALPHA' , '`ALPHA_PREMULT`' , 'ADDITIVE' , '`ADDITIVE_PREMULT`' , 'MULTIPLY' , 'SUBTRACT' , 'INVERT' ] ) – The type of blend mode.

- NONE No blending.

- ALPHA Blends the existing color channels by weighting them with the alpha value.

- `ALPHA_PREMULT` Blends the existing color channels by the alpha value, with the incoming colors already multiplied through by it.

- ADDITIVE Sums the existing color channels with their counterparts.

- `ADDITIVE_PREMULT` Sums the existing color channels with their counterparts after those have been pre-multiplied by alpha.

- MULTIPLY Scales the existing color channels by their counterparts.

- SUBTRACT Takes the counterpart channels away from the existing color channels.

- INVERT Swaps the existing color channels for their complementary color.

gpu.state. clip_distances_set ( distances_enabled )

Choose how many gl_ClipDistance planes are active for clipping geometry.

Parameters :

distances_enabled ( int ) – Number of clip distances enabled.

gpu.state. color_mask_set ( r , g , b , a )

Toggle whether each frame buffer color component gets written.

Parameters :

- r ( bool ) – Red component.

- g ( bool ) – Green component.

- b ( bool ) – Blue component.

- a ( bool ) – Alpha component.

gpu.state. depth_mask_get ( )

The write state of the depth component.

Returns :

True if writing to the depth component is enabled.

Return type :

bool

gpu.state. depth_mask_set ( value )

Enable writing into the depth component.

Parameters :

value ( bool ) – True for writing to the depth component.

gpu.state. depth_test_get ( )

The depth_test equation in force right now.

Returns :

The current depth test mode.

Return type :

str

gpu.state. depth_test_set ( mode )

Sets the depth_test equation.

Parameters :

mode ( Literal [ 'NONE' , 'ALWAYS' , 'LESS' , '`LESS_EQUAL`' , 'EQUAL' , 'GREATER' , '`GREATER_EQUAL`' ] ) – The depth test equation name.

gpu.state. face_culling_set ( culling )

Choose whether none, front-facing, or back-facing facets get culled.

Parameters :

culling ( Literal [ 'NONE' , 'FRONT' , 'BACK' ] ) – The face culling mode.

gpu.state. front_facing_set ( invert )

Sets which winding counts as the front face of a polygon.

Parameters :

invert ( bool ) – True for clockwise polygons as front-facing.

gpu.state. line_width_get ( )

The width currently used for rasterized lines.

Returns :

The current line width.

Return type :

float

gpu.state. line_width_set ( width )

Sets how wide rasterized lines are drawn.

Parameters :

width ( float ) – New width.

gpu.state. point_size_set ( size )

Sets the diameter used for rasterized points.

Parameters :

size ( float ) – New diameter.

gpu.state. program_point_size_set ( enable )

When turned on, the point size comes from the (possibly clipped) shader builtin gl_PointSize.

Parameters :

enable ( bool ) – True for shader builtin gl_PointSize.

gpu.state. scissor_get ( )

Fetch the scissor region of the active framebuffer.
Note: Only valid between ‘scissor_set’ and a framebuffer rebind.

Returns :

The scissor of the active framebuffer as a tuple
(x, y, xsize, ysize).
x, y: lower left corner of the scissor rectangle, in pixels.
xsize, ysize: width and height of the scissor rectangle.

Return type :

tuple[int, int, int, int]

gpu.state. scissor_set ( x , y , xsize , ysize )

Sets the scissor region on the active framebuffer.
Note: The scissor state is not saved upon framebuffer rebind.

Parameters :

- x ( int ) – Lower left corner x coordinate, in pixels.

- y ( int ) – Lower left corner y coordinate, in pixels.

- xsize ( int ) – Width of the scissor rectangle.

- ysize ( int ) – Height of the scissor rectangle.

gpu.state. scissor_test_set ( enable )

Turn scissor testing on or off for the active framebuffer.

Parameters :

enable ( bool ) – True - enable scissor testing.
False - disable scissor testing.

gpu.state. viewport_get ( )

The viewport of the active framebuffer.

Returns :

The viewport as a tuple (x, y, xsize, ysize).

Return type :

tuple[int, int, int, int]

gpu.state. viewport_set ( x , y , xsize , ysize )

Sets the viewport on the active framebuffer.
Note: The viewport state is not saved upon framebuffer rebind.

Parameters :

- x ( int ) – Lower left corner x coordinate, in pixels.

- y ( int ) – Lower left corner y coordinate, in pixels.

- xsize ( int ) – Width of the viewport.

- ysize ( int ) – Height of the viewport.

## gpu_extras submodule (gpu_extras.batch)

### gpu_extras submodule (gpu_extras.batch)

gpu_extras.batch. batch_for_shader ( shader , type , content , * , indices = None )

Give back a batch that is already set up to match the shader.

Parameters :

- shader (gpu.types.GPUShader) – shader for which a compatible format will be computed.

- type ( Literal [ 'POINTS' , 'LINES' , 'TRIS' , '`LINE_STRIP`' , '`TRI_STRIP`' , '`LINES_ADJ`' , '`TRIS_ADJ`' , '`LINE_STRIP_ADJ`' ] ) – The primitive type of batch geometry.

- content ( dict [ str , Buffer | Sequence [ float ] | Sequence [ int ] | Sequence [ Sequence [ float ] ] | Sequence [ Sequence [ int ] ] ] ) – Maps the name of the shader attribute with the data to fill the vertex buffer.
For the dictionary values see documentation for gpu.types.GPUVertBuf.attr_fill data argument.

Returns :

compatible batch

Return type :

gpu.types.GPUBatch

## Blender 5.1 Python API Documentation

### Blender 5.1 Python API Documentation

This is where the Python scripting reference for Blender lives — Blender being the free and open source 3D creation suite.

Prefer to read it without a connection? Grab the full documentation as zipped HTML files for offline use.

### Documentation

- Quickstart: Just getting started with Blender or with scripting and ready to dip a toe in?

- API Overview: A fuller account of how Python ties into Blender.

- API Reference Usage: Worked examples showing how the reference docs are meant to be read.

- Best Practice: The conventions worth sticking to when you write solid scripts.

- Tips and Tricks: Pointers that smooth the path while you script for Blender.

- Gotchas: A rundown of pitfalls that tend to bite script authors.

- Advanced: Material that everyday use usually won't call for.

- Change Log: A rundown of what has changed since the previous Blender release

- Contribute Documentation: How to pitch in on Blender's Python API documentation.

### Indices

- Index

- Module Index

## Gotchas

### Gotchas

The goal of this page is to steer you through the rougher corners of the Blender API and to warn you off approaches that have a track record of causing instability.

## BVHTree Utilities (mathutils.bvhtree)

### BVHTree Utilities (mathutils.bvhtree)

BVH tree data structures used for casting rays against geometry and running nearness queries on it.

class mathutils.bvhtree. BVHTree

classmethod FromBMesh ( bmesh , * , epsilon = 0.0 )

Build a BVH tree out of BMesh data.

Parameters :

- bmesh ( BMesh ) – BMesh data.

- epsilon ( float ) – Increase the threshold for detecting overlap and raycast hits.

Returns :

BVHTree from BMesh data.

Return type :

BVHTree

classmethod FromObject ( object , depsgraph , * , deform = True , cage = False , epsilon = 0.0 )

Build a BVH tree out of Object data.

Parameters :

- object ( Object ) – Mesh object.

- depsgraph ( Depsgraph ) – Depsgraph to use for evaluating the mesh.

- deform ( bool ) – Use mesh with deformations.

- cage ( bool ) – Use modifiers cage.

- epsilon ( float ) – Increase the threshold for detecting overlap and raycast hits.

Returns :

BVHTree from Object data.

Return type :

BVHTree

classmethod FromPolygons ( vertices , polygons , * , all_triangles = False , epsilon = 0.0 )

BVH tree assembled from geometry handed in through the arguments.

Parameters :

- vertices ( Sequence [ Sequence [ float ] ] ) – float triplets each representing (x, y, z) coordinates.

- polygons ( Sequence [ Sequence [ int ] ] ) – Sequence of polygons, each containing indices to the vertices argument.

- all_triangles ( bool ) – Use when all polygons are triangles for more efficient conversion.

- epsilon ( float ) – Increase the threshold for detecting overlap and raycast hits.

Returns :

BVHTree from polygon data.

Return type :

BVHTree

find_nearest ( origin , distance = 1.84467e+19 , / )

Locate the element nearest a given point (usually a face index).

Parameters :

- origin ( Vector ) – Find nearest element to this point.

- distance ( float ) – Maximum distance threshold.

Returns :

Returns a tuple: (position, normal, index, distance),
Values will all be None if no hit is found.

Return type :

tuple[ Vector | None, Vector | None, int | None, float | None]

find_nearest_range ( origin , distance = 1.84467e+19 , / )

Locate the elements nearest a given point within the distance range (usually face indices).

Parameters :

- origin ( Vector ) – Find nearest elements to this point.

- distance ( float ) – Maximum distance threshold.

Returns :

Returns a list of tuples (position, normal, index, distance)

Return type :

list[tuple[ Vector , Vector , int, float]]

overlap ( other_tree , / )

Locate the overlapping indices shared between two trees.

Parameters :

other_tree (BVHTree) – Other tree to perform overlap test on.

Returns :

Returns a list of unique index pairs, the first index referencing this tree, the second referencing the other_tree .

Return type :

list[tuple[int, int]]

ray_cast ( origin , direction , distance = sys.float_info.max , / )

Shoot a ray at the geometry.

Parameters :

- origin ( Vector ) – Start location of the ray.

- direction ( Vector ) – Direction of the ray (normalized internally).

- distance ( float ) – Maximum distance threshold.

Returns :

Returns a tuple: (position, normal, index, distance),
Values will all be None if no hit is found.

Return type :

tuple[ Vector | None, Vector | None, int | None, float | None]
