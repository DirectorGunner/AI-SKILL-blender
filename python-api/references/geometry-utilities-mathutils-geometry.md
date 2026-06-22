# Geometry Utilities Mathutils Geometry, Interpolation Utilities Mathutils Interpolate, Kdtree Utilities Mathutils Kdtree

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Geometry Utilities (mathutils.geometry); Interpolation Utilities (mathutils.interpolate); KDTree Utilities (mathutils.kdtree).

## Geometry Utilities (mathutils.geometry)

### Geometry Utilities (mathutils.geometry)

Blender's module of geometry helpers.

mathutils.geometry. area_tri ( v1 , v2 , v3 , / )

Gives the area of the supplied 2D or 3D triangle.

Parameters :

- v1 (mathutils.Vector) – Point1

- v2 (mathutils.Vector) – Point2

- v3 (mathutils.Vector) – Point3

Returns :

The area of the triangle.

Return type :

float

mathutils.geometry. barycentric_transform ( point , tri_a1 , tri_a2 , tri_a3 , tri_b1 , tri_b2 , tri_b3 , / )

Hand back a point mapped through the transformation that two triangles describe.

Parameters :

- point (mathutils.Vector) – The point to transform.

- tri_a1 (mathutils.Vector) – source triangle vertex.

- tri_a2 (mathutils.Vector) – source triangle vertex.

- tri_a3 (mathutils.Vector) – source triangle vertex.

- tri_b1 (mathutils.Vector) – target triangle vertex.

- tri_b2 (mathutils.Vector) – target triangle vertex.

- tri_b3 (mathutils.Vector) – target triangle vertex.

Returns :

The transformed point

Return type :

mathutils.Vector

mathutils.geometry. box_fit_2d ( points , / )

Gives back the angle that best aligns the points with an axis-aligned rectangle.

Parameters :

points ( Sequence [ Sequence [ float ] ] ) – Sequence of 2D points.

Returns :

The rotation angle in radians for the best axis-aligned bounding box fit.

Return type :

float

mathutils.geometry. box_pack_2d ( boxes , / )

Hands back a tuple holding the packed bounding box's width and height.

Parameters :

boxes ( list [ list [ float ] ] ) – list of boxes, each box is a list where the first 4 items are [X, Y, width, height, …] other items are ignored. The X & Y values in this list are modified to set the packed positions.

Returns :

The width and height of the packed bounding box.

Return type :

tuple[float, float]

mathutils.geometry. closest_point_on_tri ( pt , tri_p1 , tri_p2 , tri_p3 , / )

Accepts 4 vectors: the first is the point, and the remaining 3 lay out the triangle.

Parameters :

- pt (mathutils.Vector) – Point

- tri_p1 (mathutils.Vector) – First point of the triangle

- tri_p2 (mathutils.Vector) – Second point of the triangle

- tri_p3 (mathutils.Vector) – Third point of the triangle

Returns :

The closest point of the triangle.

Return type :

mathutils.Vector

mathutils.geometry. convex_hull_2d ( points , / )

Gives the indices of the points that make up the convex hull, ordered counter-clockwise.

Parameters :

points ( Sequence [ Sequence [ float ] ] ) – Sequence of 2D points.

Returns :

Indices of convex hull vertices in counter-clockwise order.

Return type :

list[int]

mathutils.geometry. delaunay_2d_cdt ( vert_coords , edges , faces , output_type , epsilon , need_ids = True , / )

Builds the Constrained Delaunay Triangulation over a collection of vertices, where the given edges and faces are forced to show up in the result. Depending on the output type, some triangles get consumed or fused with neighbors. The verts that come back may be reordered relative to the input, nudged a little, and merged with nearby ones. Each of the three returned orig lists maps, per vert, edge, and face, to the input element indices that line up positionally with each output element. The edge orig indices begin with the input edges and then run on with the edges that each face implies (n of them for an n-gon). When the need_ids argument is passed as False, the routine skips building the orig arrays, which can shave off some time.

Parameters :

- vert_coords (Sequence[mathutils.Vector]) – Vertex coordinates (2d)

- edges ( Sequence [ tuple [ int , int ] ] ) – Edges, as pairs of indices in vert_coords

- faces ( Sequence [ Sequence [ int ] ] ) – Faces, each sublist is a face, as indices in vert_coords (CCW oriented).

- output_type ( int ) – What output looks like. 0 => triangles with convex hull. 1 => triangles inside constraints. 2 => the input constraints, intersected. 3 => like 2 but detect holes and omit them from output. 4 => like 2 but with extra edges to make valid BMesh faces. 5 => like 4 but detect holes and omit them from output.

- epsilon ( float ) – For nearness tests; should not be zero

- need_ids ( bool ) – are the orig output arrays needed?

Returns :

Output tuple, (vert_coords, edges, faces, orig_verts, orig_edges, orig_faces)

Return type :

tuple[list[mathutils.Vector], list[tuple[int, int]], list[list[int]], list[list[int]], list[list[int]], list[list[int]]]

mathutils.geometry. distance_point_to_plane ( pt , plane_co , plane_no , / )

Gives the signed gap between a point and a plane (it goes negative on the side opposite the normal).

Parameters :

- pt (mathutils.Vector) – Point

- plane_co (mathutils.Vector) – A point on the plane

- plane_no (mathutils.Vector) – The direction the plane is facing

Returns :

The signed distance.

Return type :

float

mathutils.geometry. interpolate_bezier ( knot1 , handle1 , handle2 , knot2 , resolution , / )

Interpolate a bezier spline segment.

Parameters :

- knot1 (mathutils.Vector) – First bezier spline point.

- handle1 (mathutils.Vector) – First bezier spline handle.

- handle2 (mathutils.Vector) – Second bezier spline handle.

- knot2 (mathutils.Vector) – Second bezier spline point.

- resolution ( int ) – Number of points to return.

Returns :

The interpolated points.

Return type :

list[mathutils.Vector]

mathutils.geometry. intersect_line_line ( v1 , v2 , v3 , v4 , / )

Gives a tuple holding, on each line, the point that sits closest to the other line.

Parameters :

- v1 (mathutils.Vector) – First point of the first line

- v2 (mathutils.Vector) – Second point of the first line

- v3 (mathutils.Vector) – First point of the second line

- v4 (mathutils.Vector) – Second point of the second line

Returns :

The intersection on each line or None when the lines are parallel.

Return type :

tuple[mathutils.Vector, mathutils.Vector] | None

mathutils.geometry. intersect_line_line_2d ( lineA_p1 , lineA_p2 , lineB_p1 , lineB_p2 , / )

Accepts 2 segments (laid out by 4 vectors) and gives back a vector at their crossing point, or None.

Warning

Despite its name, this function works on segments, and not on lines.

Parameters :

- lineA_p1 (mathutils.Vector) – First point of the first segment

- lineA_p2 (mathutils.Vector) – Second point of the first segment

- lineB_p1 (mathutils.Vector) – First point of the second segment

- lineB_p2 (mathutils.Vector) – Second point of the second segment

Returns :

The point of intersection or None when not found

Return type :

mathutils.Vector | None

mathutils.geometry. intersect_line_plane ( line_a , line_b , plane_co , plane_no , no_flip = False , / )

Work out where a line (given as 2 vectors) meets a plane. Gives back a vector at the crossing, or None.

Parameters :

- line_a (mathutils.Vector) – First point of the line

- line_b (mathutils.Vector) – Second point of the line

- plane_co (mathutils.Vector) – A point on the plane

- plane_no (mathutils.Vector) – The direction the plane is facing

- no_flip ( bool ) – Currently ignored.

Returns :

The point of intersection or None when not found

Return type :

mathutils.Vector | None

mathutils.geometry. intersect_line_sphere ( line_a , line_b , sphere_co , sphere_radius , clip = True , / )

Accepts a line (as 2 points) plus a sphere (a point and a radius) and hands back where they meet.

Parameters :

- line_a (mathutils.Vector) – First point of the line

- line_b (mathutils.Vector) – Second point of the line

- sphere_co (mathutils.Vector) – The center of the sphere

- sphere_radius ( float ) – Radius of the sphere

- clip ( bool ) – When False, don't restrict the intersection to the line segment.

Returns :

The intersection points as a pair of vectors (each is None when not found).

Return type :

tuple[mathutils.Vector | None, mathutils.Vector | None]

mathutils.geometry. intersect_line_sphere_2d ( line_a , line_b , sphere_co , sphere_radius , clip = True , / )

Accepts a line (as 2 points) plus a circle (a point and a radius) and hands back where they meet.

Parameters :

- line_a (mathutils.Vector) – First point of the line

- line_b (mathutils.Vector) – Second point of the line

- sphere_co (mathutils.Vector) – The center of the circle

- sphere_radius ( float ) – Radius of the circle

- clip ( bool ) – When False, don't restrict the intersection to the line segment.

Returns :

The intersection points as a pair of vectors (each is None when not found).

Return type :

tuple[mathutils.Vector | None, mathutils.Vector | None]

mathutils.geometry. intersect_plane_plane ( plane_a_co , plane_a_no , plane_b_co , plane_b_no , / )

Give back where two planes cross.

Parameters :

- plane_a_co (mathutils.Vector) – Point on the first plane

- plane_a_no (mathutils.Vector) – Normal of the first plane

- plane_b_co (mathutils.Vector) – Point on the second plane

- plane_b_no (mathutils.Vector) – Normal of the second plane

Returns :

The line of the intersection represented as a point and a vector or None if the intersection can't be calculated

Return type :

tuple[mathutils.Vector, mathutils.Vector] | tuple[None, None]

mathutils.geometry. intersect_point_line ( pt , line_p1 , line_p2 , / )

Accepts a point and a line, returning the nearest point on the line plus how far along it sits from the line's first point. Here 0.0 marks the first point and 1.0 the second; anything outside [0, 1] is extrapolated.

Parameters :

- pt (mathutils.Vector) – Point

- line_p1 (mathutils.Vector) – First point of the line

- line_p2 (mathutils.Vector) – Second point of the line

Returns :

The closest point on the line and its parametric distance from the first point.

Return type :

tuple[mathutils.Vector, float]

mathutils.geometry. intersect_point_line_segment ( pt , seg_p1 , seg_p2 , / )

Accepts a point and a segment, returning the nearest point on that segment together with the distance to it.

Parameters :

- pt (mathutils.Vector) – Point

- seg_p1 (mathutils.Vector) – First point of the segment

- seg_p2 (mathutils.Vector) – Second point of the segment

Returns :

The closest point on the segment and the distance to the segment.

Return type :

tuple[mathutils.Vector, float]

mathutils.geometry. intersect_point_quad_2d ( pt , quad_p1 , quad_p2 , quad_p3 , quad_p4 , / )

Accepts 5 vectors (only their x and y are read): the first is the point, the next 4 lay out the quad. Returns a non-zero value when the point falls inside the quad, otherwise 0. Only convex quads free of singular edges are handled.

Parameters :

- pt (mathutils.Vector) – Point

- quad_p1 (mathutils.Vector) – First point of the quad

- quad_p2 (mathutils.Vector) – Second point of the quad

- quad_p3 (mathutils.Vector) – Third point of the quad

- quad_p4 (mathutils.Vector) – Fourth point of the quad

Returns :

1 if inside with CCW winding, -1 if inside with CW winding, otherwise 0.

Return type :

int

mathutils.geometry. intersect_point_tri ( pt , tri_p1 , tri_p2 , tri_p3 , / )

Accepts 4 vectors: the first is the point, the next 3 lay out the triangle. Drops the point onto the triangle's plane and tests whether it lands inside the triangle.

Parameters :

- pt (mathutils.Vector) – Point

- tri_p1 (mathutils.Vector) – First point of the triangle

- tri_p2 (mathutils.Vector) – Second point of the triangle

- tri_p3 (mathutils.Vector) – Third point of the triangle

Returns :

Point on the triangle's plane or None if it's outside the triangle

Return type :

mathutils.Vector | None

mathutils.geometry. intersect_point_tri_2d ( pt , tri_p1 , tri_p2 , tri_p3 , / )

Accepts 4 vectors (only their x and y are read): the first is the point, the next 3 lay out the triangle. Returns a non-zero value when the point falls inside the triangle, otherwise 0.

Parameters :

- pt (mathutils.Vector) – Point

- tri_p1 (mathutils.Vector) – First point of the triangle

- tri_p2 (mathutils.Vector) – Second point of the triangle

- tri_p3 (mathutils.Vector) – Third point of the triangle

Returns :

1 if inside with CCW winding, -1 if inside with CW winding, otherwise 0.

Return type :

int

mathutils.geometry. intersect_ray_tri ( v1 , v2 , v3 , ray , orig , clip = True , / )

Hands back where a ray meets a triangle when such a meeting exists, otherwise None.

Parameters :

- v1 (mathutils.Vector) – Point1

- v2 (mathutils.Vector) – Point2

- v3 (mathutils.Vector) – Point3

- ray (mathutils.Vector) – Direction of the ray

- orig (mathutils.Vector) – Origin

- clip ( bool ) – When False, don't restrict the intersection to the area of the triangle, use the infinite plane defined by the triangle.

Returns :

The point of intersection or None if no intersection is found

Return type :

mathutils.Vector | None

mathutils.geometry. intersect_sphere_sphere_2d ( p_a , radius_a , p_b , radius_b , / )

Hands back the 2 points where a pair of circles cross.

Parameters :

- p_a (mathutils.Vector) – Center of the first circle

- radius_a ( float ) – Radius of the first circle

- p_b (mathutils.Vector) – Center of the second circle

- radius_b ( float ) – Radius of the second circle

Returns :

The 2 intersection points or None when there is no intersection.

Return type :

tuple[mathutils.Vector, mathutils.Vector] | tuple[None, None]

mathutils.geometry. intersect_tri_tri_2d ( tri_a1 , tri_a2 , tri_a3 , tri_b1 , tri_b2 , tri_b3 , / )

Test whether two 2D triangles overlap.

Parameters :

- tri_a1 (mathutils.Vector) – First vertex of the first triangle.

- tri_a2 (mathutils.Vector) – Second vertex of the first triangle.

- tri_a3 (mathutils.Vector) – Third vertex of the first triangle.

- tri_b1 (mathutils.Vector) – First vertex of the second triangle.

- tri_b2 (mathutils.Vector) – Second vertex of the second triangle.

- tri_b3 (mathutils.Vector) – Third vertex of the second triangle.

Returns :

True if the triangles intersect.

Return type :

bool

mathutils.geometry. normal ( * vectors )

Hands back the normal of a 3D polygon.

Parameters :

vectors ( Sequence [ Sequence [ float ] ] ) – 3 or more vectors to calculate normals.

Returns :

The normal vector.

Return type :

mathutils.Vector

mathutils.geometry. points_in_planes ( planes , epsilon_coplanar = 1e-4 , epsilon_isect = 1e-6 , / )

Hands back a list of points lying inside every supplied plane, plus a list of the indices of the planes that were used.

Parameters :

- planes (list[mathutils.Vector]) – List of planes (4D vectors).

- epsilon_coplanar ( float ) – Epsilon value for interpreting plane pairs as co-planar.

- epsilon_isect ( float ) – Epsilon value for intersection.

Returns :

Two lists, one containing the 3D coordinates inside the planes, another containing the plane indices used.

Return type :

tuple[list[mathutils.Vector], list[int]]

mathutils.geometry. tessellate_polygon ( polylines , / )

Accepts a list of polylines (each point being a pair or triplet of numbers) and returns the point indices for that polyline filled in with triangles. Degenerate geometry (such as zero-length lines from repeated identical points) isn't handled.

Parameters :

polylines ( Sequence [ Sequence [ Sequence [ float ] ] ] ) – Polygons where each polygon is a sequence of 2D or 3D points.

Returns :

A list of triangles.

Return type :

list[tuple[int, int, int]]

mathutils.geometry. volume_tetrahedron ( v1 , v2 , v3 , v4 , / )

Hand back the absolute (unsigned) volume a tetrahedron encloses (the points may be given in any order).

Parameters :

- v1 (mathutils.Vector) – Point1

- v2 (mathutils.Vector) – Point2

- v3 (mathutils.Vector) – Point3

- v4 (mathutils.Vector) – Point4

Returns :

The volume of the tetrahedron.

Return type :

float

## Interpolation Utilities (mathutils.interpolate)

### Interpolation Utilities (mathutils.interpolate) 

Blender's interpolate module.

mathutils.interpolate. poly_3d_calc ( veclist , pt , / ) 

Work out the barycentric weights of a point lying on a polygon.

Parameters :

- veclist ( Sequence [ Sequence [ float ] ] ) – The polygon's vertices, listed as 3D coordinates.

- pt ( Sequence [ float ] ) – The query point, given in 2D or 3D.

Returns :

One weight returned for each vertex listed in veclist .

Return type :

list[float]

## KDTree Utilities (mathutils.kdtree)

### KDTree Utilities (mathutils.kdtree) 

A general-purpose three-dimensional kd-tree for running spatial lookups.

`\text
import mathutils

### Create a KD-tree from a mesh.
from bpy import context
obj = context.object

mesh = obj.data
size = len(mesh.vertices)
kd = mathutils.kdtree.KDTree(size)

for i, v in enumerate(mesh.vertices):
kd.insert(v.co, i)

kd.balance()

### Find the closest point to the center.
co_find = (0.0, 0.0, 0.0)
co, index, dist = kd.find(co_find)
print("Close to center:", co, index, dist)

### 3D cursor relative to the object data.
co_find = obj.matrix_world.inverted() @ context.scene.cursor.location

### Find the closest 10 points to the 3D cursor.
print("Close 10 points")
for (co, index, dist) in kd.find_n(co_find, 10):
print("  ", co, index, dist)

### Find points within a radius of the 3D cursor.
print("Close points within 0.5 distance")
for (co, index, dist) in kd.find_range(co_find, 0.5):
print("  ", co, index, dist)
`

class mathutils.kdtree. KDTree ( size ) 

KDTree(size) -> new kd-tree initialized to hold up to size items.

Parameters :

size ( int ) – Maximum number of items.

Note

KDTree.balance() must have been called before using any of the find methods.

balance ( ) 

Rebuild and balance the tree.

Note

Constructing the whole tree happens here, so don't run it per insert.

find ( co , * , filter = None ) 

Locate the single point closest to co .

Parameters :

- co ( Sequence [ float ] ) – 3D coordinate.

- filter ( Callable [ [ int ] , bool ] | None ) – callable fed an index that returns True to keep that index in the search.

Returns :

Yields the triple (position, index, distance), falling back to (None, None, None) if nothing matches.

Return type :

tuple[ Vector , int, float] | tuple[None, None, None]

find_n ( co , n ) 

Locate the n points nearest to co .

Parameters :

- co ( Sequence [ float ] ) – 3D coordinate.

- n ( int ) – Number of points to find.

Returns :

Yields a list whose entries are (position, index, distance) triples.

Return type :

list[tuple[ Vector , int, float]]

find_range ( co , radius ) 

Gather every point lying no further than radius from co .

Parameters :

- co ( Sequence [ float ] ) – 3D coordinate.

- radius ( float ) – Furthest reach within which points still count.

Returns :

Yields a list whose entries are (position, index, distance) triples.

Return type :

list[tuple[ Vector , int, float]]

insert ( co , index ) 

Add a single point to the KDTree.

Parameters :

- co ( Sequence [ float ] ) – Point 3d position.

- index ( int ) – Identifier tag for the point; zero or positive only.
