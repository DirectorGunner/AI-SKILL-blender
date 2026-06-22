# Path Utilities Bpy Path, Bpy Prop Array, Bpy Prop Collection Idprop, Bpy Extras Submodule Bpy Extras Id Map Utils ...

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Path Utilities (bpy.path); bpy_prop_array; bpy_prop_collection_idprop; bpy_extras submodule (bpy_extras.id_map_utils); bpy_extras submodule (bpy_extras.mesh_utils); bpy_extras submodule (bpy_extras.view3d_utils); Asset Library Type Items; Attr Storage Type Items; Attribute Domain Edge Face Items; Attribute Domain Items; Attribute Domain Only Mesh Items; Attribute Domain Only Mesh No Corner Items; Attribute Domain Only Mesh No Edge Items; Attribute Domain Point Edge Face Curve Items; Attribute Domain Point Face Curve Items; Attribute Domain With Auto Items; Attribute Domain Without Corner Items; Attribute Type Items.

## Path Utilities (bpy.path)

### Path Utilities (bpy.path) 

This unit offers utilities similar to os.path, holding support purposes for managing directions in Blender.

bpy.path. abspath ( path , * , start = None , library = None ) 

Delivers the complete route matching the present mix file
utilizing the "//" tag.

Parameters :

- path ( str | bytes ) – The route to transform to complete.

- start ( str | bytes | None ) – Matching to this route,
when unset the present title is utilized.

- library (bpy.types.Library | None) – The archive this route is from. This is merely contained for
benefit, when the archive is not None its route swaps start .

Returns :

The complete route.

Return type :

str

bpy.path. basename ( path ) 

Resembles os.path.basename , but omits a "//" tag.

Use for Windows interoperability.

Parameters :

path ( str | bytes ) – The route to receive the foundation label of.

Returns :

The foundation label of the given route.

Return type :

str

bpy.path. clean_name ( name , * , replace = '_' ) 

Delivers a label with characters swapped that
might generate issues under numerous cases,
for instance composing to a document.

Every sign other than A-Z/a-z, 0-9 is swapped with "_"
or the substitute input if laid out.

Parameters :

- name ( str | bytes ) – The route designation.

- replace ( str ) – The substitute for illegitimate marks.

Returns :

The cleansed designation.

Return type :

str

bpy.path. display_name ( name , * , has_ext = True , title_case = True ) 

Builds a presentation sequence from designation for application in lists and the client interaction.
Meant for application with documentation names and package designations.

Parameters :

- name ( str ) – The designation to be applied for showing the client contact.

- has_ext ( bool ) – Eliminate document finish from designation.

- title_case ( bool ) – Switch uppercase designations to heading structure.

Returns :

The presentation sequence.

Return type :

str

bpy.path. display_name_to_filepath ( name ) 

Executes the opposite of display_name utilizing literal type of marks
which are not permitted in a route.

Parameters :

name ( str ) – The presentation designation to transmute.

Returns :

The route.

Return type :

str

bpy.path. display_name_from_filepath ( name ) 

Yields the route deprived of listing and finish,
guaranteed to be UTF-8 workable.

Parameters :

name ( str ) – The route to transmute.

Returns :

The presentation designation.

Return type :

str

bpy.path. ensure_ext ( filepath , ext , * , case_sensitive = False ) 

Give back the route with the finish attached if it is not currently provided.

Parameters :

- filepath ( str ) – The route.

- ext ( str ) – The finish to inspect, may be a joined finish. Should
begin with a period, for instance .blend or .tar.gz .

- case_sensitive ( bool ) – Verify for fitting situation when matching finishes.

Returns :

The route with the provided finish.

Return type :

str

bpy.path. is_subdir ( path , directory ) 

Returns true if route is in a next listing of listing .
Every routes must be entire.

Parameters :

- path ( str | bytes ) – An entire route.

- directory ( str | bytes ) – The ancestor listing to verify to.

Returns :

Whether or not the route is a next listing.

Return type :

bool

bpy.path. module_names ( path , * , recursive = False , package = '' ) 

Yield a set of instruments which can be brought in from route .

Parameters :

- path ( str ) – a listing to examine.

- recursive ( bool ) – Also yield child unit designations for packages.

- package ( str ) – Discretionary sequence, utilized as the prefix for unit designations (excluding the subsequent ".").

Returns :

a set of sequence groupings (unit_name, unit_file).

Return type :

list[tuple[str, str]]

bpy.path. native_pathsep ( path ) 

Swap the route breaker with the operating system's innate os.sep .

Parameters :

path ( str ) – The route to trade.

Returns :

The route with arrangement innate breakers.

Return type :

str

bpy.path. reduce_dirs ( dirs ) 

Given a grouping of listings, eliminate replicas and
every listings embedded in among the different paths.
(Valuable for rotating route examining).

Parameters :

dirs ( Sequence [ str ] ) – Grouping of listing routes.

Returns :

A distinctive set of routes.

Return type :

list[str]

bpy.path. relpath ( path , * , start = None ) 

Yields the route matching the present mix file utilizing the "//" tag.

Parameters :

- path ( str | bytes ) – An entire route.

- start ( str | bytes | None ) – Matching to this route,
when unset the present title is utilized.

Returns :

The matching route.

Return type :

str

bpy.path. resolve_ncase ( path ) 

Restore a situation-disregarding route on a situation-delicate arrangement,
delivering a sequence with the route if discovered else deliver the initial route.

Parameters :

path ( str ) – The route designation to restore.

Returns :

The restored route.

Return type :

str

## bpy_prop_array

### bpy_prop_array

base classes — bpy_prop

class bpy.types. bpy_prop_array ( bpy_prop )

The built-in class backing array properties.

foreach_get ( seq )

A helper offering quick reads of array data.

foreach_set ( seq )

A helper offering quick writes of array data.

## bpy_prop_collection_idprop

### bpy_prop_collection_idprop

base classes — bpy_prop_collection

class bpy.types. bpy_prop_collection_idprop ( bpy_prop_collection )

The built-in class behind user-defined collections.

add ( )

Appends a brand-new item onto the collection.

Returns :

A newly created item.

Return type :

Any

clear ( )

Empties the collection by stripping out every item.

move ( src_index , dst_index )

Relocates one item to a different slot within the collection.

Parameters :

- src_index ( int ) – Source item index.

- dst_index ( int ) – Destination item index.

remove ( index )

Deletes a single item from the collection.

Parameters :

index ( int ) – Index of the item to be removed.

## bpy_extras submodule (bpy_extras.id_map_utils)

### bpy_extras submodule (bpy_extras.id_map_utils) 

bpy_extras.id_map_utils. get_id_reference_map ( ) 

Hand back a dictionary of direct data-block references for each data-block in the blend file.

Returns :

Each datablock of the .blend file mapped to the set of IDs they directly reference.

Return type :

dict[bpy.types.ID, set[bpy.types.ID]]

bpy_extras.id_map_utils. get_all_referenced_ids ( id , ref_map ) 

Hand back the set of IDs that id references either directly or through other IDs.

Parameters :

- id (bpy.types.ID) – Datablock whose references we're interested in.

- ref_map ( dict [ bpy.types.ID , set [ bpy.types.ID ] ] ) – The global ID reference map, retrieved from get_id_reference_map()

Returns :

Set of datablocks referenced by id .

Return type :

set[bpy.types.ID]

## bpy_extras submodule (bpy_extras.mesh_utils)

### bpy_extras submodule (bpy_extras.mesh_utils) 

bpy_extras.mesh_utils. mesh_linked_uv_islands ( mesh ) 

Hand back lists of polygon indices that UV islands link together.

Parameters :

mesh (bpy.types.Mesh) – the mesh used to group with.

Returns :

list of lists containing polygon indices

Return type :

list[list[int]]

bpy_extras.mesh_utils. mesh_linked_triangles ( mesh ) 

Break the mesh into connected triangles; handy for splitting cubes apart from
other geometry inside a single mesh data-block.

Parameters :

mesh (bpy.types.Mesh) – the mesh used to group with.

Returns :

Lists of lists containing triangles.

Return type :

list[list[bpy.types.MeshLoopTriangle]]

bpy_extras.mesh_utils. edge_face_count_dict ( mesh ) 

Parameters :

mesh (bpy.types.Mesh) – The mesh to count edges for.

Returns :

Dictionary of edge keys with their value set to the number of faces using each edge.

Return type :

dict[tuple[int, int], int]

bpy_extras.mesh_utils. edge_face_count ( mesh ) 

Parameters :

mesh (bpy.types.Mesh) – The mesh to count edges for.

Returns :

list of face users for each item in mesh.edges.

Return type :

list[int]

bpy_extras.mesh_utils. edge_loops_from_edges ( mesh , edges = None ) 

Edge loops defined by edges.

Accepts mesh.edges or a list of edges and gives back the edge loops
as lists of vertex indices.
On closed loops the first and last values are equal.

Parameters :

- mesh (bpy.types.Mesh) – The mesh to extract edge loops from.

- edges (list[bpy.types.MeshEdge] | None) – Edges to use, or None to use all edges in the mesh.

Returns :

A list of edge loops, each a list of vertex indices.

Return type :

list[list[int]]

bpy_extras.mesh_utils. ngon_tessellate ( from_data , indices , fix_loops = True , debug_print = True ) 

Accepts a poly-line of indices (an ngon) and gives back a list of face
index lists. Intended for importers that need ngon indices in order to build
faces from existing verts.

Parameters :

- from_data (bpy.types.Mesh | list[Sequence[float]] | tuple[Sequence[float]]) – Either a mesh, or a list/tuple of 3D vectors.

- indices ( list [ int ] ) – a list of indices to use.
This list is the ordered closed poly-line to fill, and can be a subset of the data given.

- fix_loops ( bool ) – If this is enabled poly-lines
that use loops to make multiple
poly-lines are dealt with correctly.

- debug_print ( bool ) – Print debug information to the console.

Returns :

Tessellated faces as a list of triangle index tuples.

Return type :

list[tuple[int, int, int]]

bpy_extras.mesh_utils. triangle_random_points ( num_points , loop_triangles ) 

Produce a list of random points scattered over mesh loop triangles.

Parameters :

- num_points ( int ) – The number of random points to generate on each triangle.

- loop_triangles (Sequence[bpy.types.MeshLoopTriangle]) – Sequence of the triangles to generate points on.

Returns :

List of random points over all triangles.

Return type :

list[mathutils.Vector]

## bpy_extras submodule (bpy_extras.view3d_utils)

### bpy_extras submodule (bpy_extras.view3d_utils) 

bpy_extras.view3d_utils. region_2d_to_vector_3d ( region , rv3d , coord ) 

Give back a direction vector from the viewport at the given 2D region
coordinate.

Parameters :

- region (bpy.types.Region) – region of the 3D viewport, typically bpy.context.region.

- rv3d (bpy.types.RegionView3D) – 3D region data, typically bpy.context.space_data.region_3d.

- coord ( Sequence [ float ] ) – 2D coordinates relative to the region:
(event.mouse_region_x, event.mouse_region_y) for example.

Returns :

normalized 3D vector.

Return type :

mathutils.Vector

bpy_extras.view3d_utils. region_2d_to_origin_3d ( region , rv3d , coord , * , clamp = None ) 

Give back the 3D view origin from region-relative 2D coords.

Note

Orthographic views have a less obvious origin,
the far clip is used to define the viewport near/far extents.
Since far clip can be a very large value,
the result may have numeric precision issues.

To avoid this problem, you can optionally clamp the far clip to a
smaller value based on the data you're operating on.

Parameters :

- region (bpy.types.Region) – region of the 3D viewport, typically bpy.context.region.

- rv3d (bpy.types.RegionView3D) – 3D region data, typically bpy.context.space_data.region_3d.

- coord ( Sequence [ float ] ) – 2D coordinates relative to the region;
(event.mouse_region_x, event.mouse_region_y) for example.

- clamp ( float | None ) – Clamp the maximum far-clip value used.
(negative value will move the offset away from the view_location)

Returns :

The origin of the viewpoint in 3D space.

Return type :

mathutils.Vector

bpy_extras.view3d_utils. region_2d_to_location_3d ( region , rv3d , coord , depth_location ) 

Give back a 3D location from region-relative 2D coords, lined up with
depth_location .

Parameters :

- region (bpy.types.Region) – region of the 3D viewport, typically bpy.context.region.

- rv3d (bpy.types.RegionView3D) – 3D region data, typically bpy.context.space_data.region_3d.

- coord ( Sequence [ float ] ) – 2D coordinates relative to the region;
(event.mouse_region_x, event.mouse_region_y) for example.

- depth_location (mathutils.Vector) – the returned vectors depth is aligned with this since
there is no defined depth with a 2D region input.

Returns :

normalized 3D vector.

Return type :

mathutils.Vector

bpy_extras.view3d_utils. location_3d_to_region_2d ( region , rv3d , coord , * , default = None ) 

Give back the region-relative 2D location of a 3D position.

Parameters :

- region (bpy.types.Region) – region of the 3D viewport, typically bpy.context.region.

- rv3d (bpy.types.RegionView3D) – 3D region data, typically bpy.context.space_data.region_3d.

- coord (mathutils.Vector) – 3D world-space location.

- default ( Any ) – Return this value if coord
is behind the origin of a perspective view.

Returns :

2D location

Return type :

mathutils.Vector | Any

## Asset Library Type Items

### Asset Library Type Items 

ALL :

All Libraries.

Pull in assets from every one of the listed asset libraries.

LOCAL :

Current File.

List the assets present in the active Blender session.

ESSENTIALS :

Essentials.

List the core building blocks and utilities that ship with Blender.

CUSTOM :

Custom.

List assets from the asset libraries set up in the Preferences.

## Attr Storage Type Items

### Attr Storage Type Items 

ARRAY :

Array.

Hold one value per element.

SINGLE :

Single.

Hold a single value covering the whole domain.

## Attribute Domain Edge Face Items

### Attribute Domain Edge Face Items 

EDGE :

Edge.

Attribute carried on a mesh edge.

FACE :

Face.

Attribute carried on mesh faces.

## Attribute Domain Items

### Attribute Domain Items 

POINT :

Point.

Attribute carried on a point.

EDGE :

Edge.

Attribute carried on a mesh edge.

FACE :

Face.

Attribute carried on mesh faces.

CORNER :

Face Corner.

Attribute carried on a mesh face corner.

CURVE :

Spline.

Attribute carried on a spline.

INSTANCE :

Instance.

Attribute carried on an instance.

LAYER :

Layer.

Attribute carried on a Grease Pencil layer.

## Attribute Domain Only Mesh Items

### Attribute Domain Only Mesh Items 

POINT :

Point.

Attribute carried on a point.

EDGE :

Edge.

Attribute carried on a mesh edge.

FACE :

Face.

Attribute carried on mesh faces.

CORNER :

Face Corner.

Attribute carried on a mesh face corner.

## Attribute Domain Only Mesh No Corner Items

### Attribute Domain Only Mesh No Corner Items 

POINT :

Point.

Attribute carried on a point.

EDGE :

Edge.

Attribute carried on a mesh edge.

FACE :

Face.

Attribute carried on mesh faces.

## Attribute Domain Only Mesh No Edge Items

### Attribute Domain Only Mesh No Edge Items 

POINT :

Point.

Attribute carried on a point.

FACE :

Face.

Attribute carried on mesh faces.

CORNER :

Face Corner.

Attribute carried on a mesh face corner.

## Attribute Domain Point Edge Face Curve Items

### Attribute Domain Point Edge Face Curve Items 

POINT :

Point.

Attribute carried on a point.

EDGE :

Edge.

Attribute carried on a mesh edge.

FACE :

Face.

Attribute carried on mesh faces.

CURVE :

Spline.

Attribute carried on a spline.

## Attribute Domain Point Face Curve Items

### Attribute Domain Point Face Curve Items 

POINT :

Point.

Attribute carried on a point.

FACE :

Face.

Attribute carried on mesh faces.

CURVE :

Spline.

Attribute carried on a spline.

## Attribute Domain With Auto Items

### Attribute Domain With Auto Items 

AUTO :

Auto.

POINT :

Point.

Attribute carried on a point.

EDGE :

Edge.

Attribute carried on a mesh edge.

FACE :

Face.

Attribute carried on mesh faces.

CORNER :

Face Corner.

Attribute carried on a mesh face corner.

CURVE :

Spline.

Attribute carried on a spline.

INSTANCE :

Instance.

Attribute carried on an instance.

LAYER :

Layer.

Attribute carried on a Grease Pencil layer.

## Attribute Domain Without Corner Items

### Attribute Domain Without Corner Items 

POINT :

Point.

Attribute carried on a point.

EDGE :

Edge.

Attribute carried on a mesh edge.

FACE :

Face.

Attribute carried on mesh faces.

CURVE :

Spline.

Attribute carried on a spline.

INSTANCE :

Instance.

Attribute carried on an instance.

LAYER :

Layer.

Attribute carried on a Grease Pencil layer.

## Attribute Type Items

### Attribute Type Items 

FLOAT :

Float.

Floating-point value.

INT :

Integer.

32-bit integer.

BOOLEAN :

Boolean.

True or false.

`FLOAT_VECTOR` :

Vector.

3D vector holding floating-point components.

`FLOAT_COLOR` :

Color.

RGBA color holding 32-bit floating-point channels.

QUATERNION :

Quaternion.

Quaternion rotation in floating point.

FLOAT4X4 :

4x4 Matrix.

Matrix in floating point.

STRING :

String.

Text string.

INT8 :

8-Bit Integer.

Narrower integer spanning -128 to 127.

`INT16_2D` :

2D 16-Bit Integer Vector.

Signed 16-bit integer vector.

`INT32_2D` :

2D Integer Vector.

Signed 32-bit integer vector.

FLOAT2 :

2D Vector.

2D vector holding floating-point components.

`BYTE_COLOR` :

Byte Color.

RGBA color holding 8-bit positive integer channels.

## Attribute Type With Auto Items

### Attribute Type With Auto Items 

AUTO :

Auto.

FLOAT :

Float.

Floating-point value.

INT :

Integer.

32-bit integer.

BOOLEAN :

Boolean.

True or false.

`FLOAT_VECTOR` :

Vector.

3D vector holding floating-point components.

`FLOAT_COLOR` :

Color.

RGBA color holding 32-bit floating-point channels.

QUATERNION :

Quaternion.

Quaternion rotation in floating point.

FLOAT4X4 :

4x4 Matrix.

Matrix in floating point.

STRING :

String.

Text string.

INT8 :

8-Bit Integer.

Narrower integer spanning -128 to 127.

`INT16_2D` :

2D 16-Bit Integer Vector.

Signed 16-bit integer vector.

`INT32_2D` :

2D Integer Vector.

Signed 32-bit integer vector.

FLOAT2 :

2D Vector.

2D vector holding floating-point components.

`BYTE_COLOR` :

Byte Color.

RGBA color holding 8-bit positive integer channels.

## Bake Margin Type Items

### Bake Margin Type Items 

`ADJACENT_FACES` :

Adjacent Faces.

Borrow pixels from neighboring faces across the UV seams.

EXTEND :

Extend.

Push the border pixels outward.

## Bake Pass Filter Type Items

### Bake Pass Filter Type Items 

NONE :

None.

EMIT :

Emit.

DIRECT :

Direct.

INDIRECT :

Indirect.

COLOR :

Color.

DIFFUSE :

Diffuse.

GLOSSY :

Glossy.

TRANSMISSION :

Transmission.

## Bake Pass Type Items

### Bake Pass Type Items 

COMBINED :

Combined.

AO :

Ambient Occlusion.

SHADOW :

Shadow.

POSITION :

Position.

NORMAL :

Normal.

UV :

UV.

ROUGHNESS :

ROUGHNESS.

EMIT :

Emission.

ENVIRONMENT :

Environment.

DIFFUSE :

Diffuse.

GLOSSY :

Glossy.

TRANSMISSION :

Transmission.

## Boidrule Type Items

### Boidrule Type Items 

GOAL :

Goal.

Head toward the assigned object or the loudest assigned signal source.

AVOID :

Avoid.

Move away from the assigned object or the loudest assigned signal source.

`AVOID_COLLISION` :

Avoid Collision.

Steer to dodge upcoming collisions with other boids and deflector objects.

SEPARATE :

Separate.

Avoid passing through other boids.

FLOCK :

Flock.

Head for the center of the neighbors while matching their velocity.

`FOLLOW_LEADER` :

Follow Leader.

Trail behind a boid or an assigned object.

`AVERAGE_SPEED` :

Average Speed.

Hold speed, keep flight level, or wander.

FIGHT :

Fight.

Approach the nearest enemy and strike once within range.

## Brush Automasking Flag Items

### Brush Automasking Flag Items 

use_automasking_topology :

Topology.

Reach only the vertices connected to the active vertex beneath the brush.

use_automasking_face_sets :

Face Sets.

Reach only the vertices sharing face sets with the active vertex.

use_automasking_boundary_edges :

Mesh Boundary Auto-Masking.

Leave non-manifold boundary edges untouched.

use_automasking_boundary_face_sets :

Face Sets Boundary Automasking.

Leave vertices sitting on a face set boundary untouched.

use_automasking_cavity :

Cavity Mask.

Leave vertices on peaks untouched, judged from the surface curvature.

use_automasking_cavity_inverted :

Inverted Cavity Mask.

Leave vertices down in crevices untouched, judged from the surface curvature.

use_automasking_custom_cavity_curve :

Custom Cavity Curve.

Apply a custom curve.

## Brush Curve Preset Items

### Brush Curve Preset Items 

CUSTOM :

Custom.

SMOOTH :

Smooth.

SMOOTHER :

Smoother.

SPHERE :

Sphere.

ROOT :

Root.

SHARP :

Sharp.

LIN :

Linear.

POW4 :

Sharper.

INVSQUARE :

Inverse Square.

CONSTANT :

Constant.

## Brush Curves Sculpt Brush Type Items

### Brush Curves Sculpt Brush Type Items

`SELECTION_PAINT` :

Paint Selection.

ADD :

Add.

DELETE :

Delete.

DENSITY :

Density.

COMB :

Comb.

`SNAKE_HOOK` :

Snake Hook.

`GROW_SHRINK` :

Grow / Shrink.

PINCH :

Pinch.

PUFF :

Puff.

SMOOTH :

Smooth.

SLIDE :

Slide.

## Brush Gpencil Sculpt Types Items

### Brush Gpencil Sculpt Types Items

SMOOTH :

Smooth.

Soften the points along a stroke.

THICKNESS :

Thickness.

Change how thick the strokes are drawn.

STRENGTH :

Strength.

Vary the color intensity of the strokes.

RANDOMIZE :

Randomize.

Add jitter and randomness to strokes.

GRAB :

Grab.

Drag whichever points first sit inside the brush circle.

PUSH :

Push.

Sweep points aside, much like combing them.

TWIST :

Twist.

Spin points about the brush's center.

PINCH :

Pinch.

Draw points inward toward the brush's center.

CLONE :

Clone.

Stamp down copies of strokes held on the internal clipboard.

## Brush Gpencil Types Items

### Brush Gpencil Types Items

DRAW :

Draw.

A brush type meant for laying down strokes.

FILL :

Fill.

A brush type meant for filling in areas.

ERASE :

Erase.

A brush type that removes existing strokes.

TINT :

Tint.

A brush type meant for tinting strokes.

## Brush Gpencil Vertex Types Items

### Brush Gpencil Vertex Types Items

DRAW :

Draw.

Lay color onto the points of a stroke.

BLUR :

Blur.

Even out the colors between neighboring stroke points.

AVERAGE :

Average.

Blend points toward the mean color found beneath the brush.

SMEAR :

Smear.

Drag and smudge colors across the stroke.

REPLACE :

Replace.

Swap out the color on stroke points that are already colored.

## Brush Gpencil Weight Types Items

### Brush Gpencil Weight Types Items

WEIGHT :

Weight.

Paint weights onto the active vertex group.

BLUR :

Blur.

Soften the weights within the active vertex group.

AVERAGE :

Average.

Even out the weights across the active vertex group.

SMEAR :

Smear.

Drag weights around inside the active vertex group.

## Brush Sculpt Brush Type Items

### Brush Sculpt Brush Type Items

DRAW :

Draw.

`DRAW_SHARP` :

Draw Sharp.

CLAY :

Clay.

`CLAY_STRIPS` :

Clay Strips.

`CLAY_THUMB` :

Clay Thumb.

LAYER :

Layer.

INFLATE :

Inflate.

BLOB :

Blob.

CREASE :

Crease.

SMOOTH :

Smooth.

PLANE :

Plane.

`MULTIPLANE_SCRAPE` :

Multi-plane Scrape.

PINCH :

Pinch.

GRAB :

Grab.

`ELASTIC_DEFORM` :

Elastic Deform.

`SNAKE_HOOK` :

Snake Hook.

THUMB :

Thumb.

POSE :

Pose.

NUDGE :

Nudge.

ROTATE :

Rotate.

TOPOLOGY :

Slide Relax.

BOUNDARY :

Boundary.

CLOTH :

Cloth.

SIMPLIFY :

Simplify.

MASK :

Mask.

`DRAW_FACE_SETS` :

Draw Face Sets.

`DISPLACEMENT_ERASER` :

Multires Displacement Eraser.

`DISPLACEMENT_SMEAR` :

Multires Displacement Smear.

PAINT :

Paint.

SMEAR :

Smear.

BLUR :

Blur.

## Clip Editor Mode Items

### Clip Editor Mode Items

TRACKING :

Tracking.

Reveal the tools for tracking and solving.

MASK :

Mask.

Reveal the tools for editing masks.

## Collection Color Items

### Collection Color Items

NONE :

None.

Leave the collection without any color tag.

`COLOR_01` :

Color 01.

`COLOR_02` :

Color 02.

`COLOR_03` :

Color 03.

`COLOR_04` :

Color 04.

`COLOR_05` :

Color 05.

`COLOR_06` :

Color 06.

`COLOR_07` :

Color 07.

`COLOR_08` :

Color 08.

## Color Attribute Type Items

### Color Attribute Type Items

`FLOAT_COLOR` :

Color.

RGBA color held as 32-bit floating-point values.

`BYTE_COLOR` :

Byte Color.

RGBA color held as 8-bit unsigned integer values.

## Color Sets Items

### Color Sets Items

DEFAULT :

Default Colors.

THEME01 :

01 - Theme Color Set.

THEME02 :

02 - Theme Color Set.

THEME03 :

03 - Theme Color Set.

THEME04 :

04 - Theme Color Set.

THEME05 :

05 - Theme Color Set.

THEME06 :

06 - Theme Color Set.

THEME07 :

07 - Theme Color Set.

THEME08 :

08 - Theme Color Set.

THEME09 :

09 - Theme Color Set.

THEME10 :

10 - Theme Color Set.

THEME11 :

11 - Theme Color Set.

THEME12 :

12 - Theme Color Set.

THEME13 :

13 - Theme Color Set.

THEME14 :

14 - Theme Color Set.

THEME15 :

15 - Theme Color Set.

THEME16 :

16 - Theme Color Set.

THEME17 :

17 - Theme Color Set.

THEME18 :

18 - Theme Color Set.

THEME19 :

19 - Theme Color Set.

THEME20 :

20 - Theme Color Set.

CUSTOM :

Custom Color Set.

## Color Space Convert Default Items

### Color Space Convert Default Items

NONE :

None.

Skip any color conversion at load time, assuming the colors already live in scene linear space.
