# Extrude Mesh Node, Flip Faces Node, Mesh Boolean Node, Mesh To Curve Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Extrude Mesh Node; Flip Faces Node; Mesh Boolean Node; Mesh to Curve Node; Mesh to Density Grid Node; Mesh to Points Node; Mesh to SDF Grid Node; Mesh to Volume Node; Scale Elements Node; Split Edges Node; Subdivide Mesh Node; Subdivision Surface Node; Triangulate Node; Cone Node; Cube Node; Cylinder Node; Grid Node; Icosphere Node.

## Extrude Mesh Node

### Extrude Mesh Node

Extrude Mesh builds fresh edges or faces from the selected elements, then pushes them outward along an offset.

Similar to mesh edit-mode extrude tools, but with differences: the node never retains back-faces (they are always removed), and attribute propagation rules may differ.

### Inputs

Mesh
Input geometry.

Selection
Boolean: which elements to extrude.

Offset
Displacement vector per extruded element. Default: element normal.

Tip: If all elements move the same direction, connect a Vector Node to improve performance by skipping normal calculation.

Offset Scale
Multiplier for the displacement vector.

Individual Face Mode Only
Extrude each face separately vs. groups of connected faces.

### Properties

Mode

Vertices:
Add a freestanding edge at each selected vertex.

Edges:
Add a quad face at each selected edge. Vertices shared by selected edges are shared in the duplicated edges.

Note: New-face normals may be arbitrary depending on connectivity. When all selected edges have one adjacent face, consistent orientation is possible; with multiple or zero adjacent faces, normals may need manual correction.

Faces:
Extrude contiguous selected-face regions or each face individually (based on Individual input). Connected-face boundaries spawn "side" faces. Interior vertices/edges/faces move but don't duplicate. A fully-selected manifold mesh simply scales outward.

### Output

Mesh
Output geometry.

Top
Boolean: "top" elements in the extrusion. Vertices mode: new vertices; Edges mode: new edges; Faces mode: moved faces.

Side
Boolean: "side" elements. Vertices mode: new edges; Edges and Faces modes: newly-created faces (moved faces excluded in Faces mode).

### Examples

Selection outputs set materials on certain faces. A Random Value Node limits extrusions to random faces.

### Attribute Propagation

Attributes transfer to new elements under specific rules. An attribute never changes domains. The id attribute has no special handling.

Boolean attributes generally propagate with "or" logic: any "true" connection causes the new value to be "true."

### Vertex Mode

New edges use the average of all connected edges.

- New vertices copy from originals.

- New edges average from any connected original edges. Booleans: selected if any connected edge was selected.

### Edge Mode

Vertical connecting edges (shown in yellow) average from the two middle blue edges; darker maroon edges below are unused.

- New vertices copy from originals.

- Vertical connecting edges average from any connected extruded edges. Booleans: selected if any were selected. (Propagation shown in figure.)

- Horizontal duplicate edges copy from originals.

- New faces average from all faces adjacent to selected edges. Booleans: selected if any were.

- New face corners average from corresponding corners in all adjacent faces. Booleans: selected if one was.

### Face Mode

Vertical connecting edges (shown in yellow) average from the two middle blue edges; darker maroon edges between unselected/top faces are unused.

- New vertices copy from originals.

- Vertical connecting edges average from any connected extruded edges, excluding "top" edges. Booleans: selected if any were. (Propagation shown in figure.)

- Horizontal duplicate edges copy from originals.

- New faces copy from corresponding extruded faces.

- New face corners copy from corresponding extruded-face corners.

### Individual Face Mode

Each edge averages from its two neighbors on the extruded face.

- New vertices copy from originals.

- Vertical connecting edges average from the two neighbors on each extruded face. Booleans: selected when at least one neighbor was.

- Horizontal duplicate edges copy from originals.

- New side faces copy from their corresponding selected face.

- New face corners copy from their corresponding selected-face corners.

## Flip Faces Node

### Flip Faces Node

The Flip Faces node reverses vertex and edge order for each selected face. Primary use: inverting face normals. Face-corner domain attributes reverse as well.

While normals are typically the goal, the node is not called "Flip Normals" for a key reason: it does not directly modify normals. The right-hand rule defines normals from vertex order, so reversing the vertex list inverts the surface direction.

### Inputs

Mesh
Input geometry.

Selection
Boolean: true = flip, false = leave unchanged.

### Output

Mesh
Output geometry.

## Mesh Boolean Node

### Mesh Boolean Node

This node performs set operations on two input geometries: intersection, union, and subtraction. It provides the same functionality as the Boolean modifier.

### Inputs

Mesh 1/2 — Receives standard geometry.

Self Intersection Exact Solver — When present, handles cases where one or both operands contain self-intersections. The tradeoff is slower computation.

Hole Tolerant Exact Solver — Optimizes results for non-manifold surfaces. Higher computational cost applies; use only when the solver produces errors on non-manifold input.

### Properties

Operation

Intersect — Retains only the volume shared by both input geometries.

Union — Combines the two meshes and removes interior faces.

Difference — Removes geometry 2 from geometry 1, keeping everything outside geometry 2.

Solver — Algorithm for computing Boolean results.

Float — Fast but incompatible with overlapping surfaces.

Exact — Slower; handles coplanar or overlapping faces correctly.

Manifold — Fastest option; restricted to manifold meshes and Difference-plane operations.

### Output

Mesh — Standard geometry output.

Intersecting Edges Exact Solver — Boolean attribute; selects edges created at contact between inputs.

## Mesh to Curve Node

### Mesh to Curve Node

Converts mesh geometry into one or more curve splines using two modes:

- Edges — Each connected sequence of edges becomes a poly spline. Intersecting edge chains split into separate splines.
- Faces — Each face becomes a closed spline. Much faster than Edges because it parallelizes and avoids attribute duplication.

Isolated vertices are excluded. Both named and unnamed attributes transfer to output splines. If a radius attribute exists, it applies automatically; alternatively use Set Curve Radius Node.

### Inputs

Mesh — Standard mesh input.

Selection — Boolean field on edges; determines which edges convert to curves. More efficient than pre-deleting parts.

### Properties

Mode — Conversion strategy.

Edges — Poly splines from edge chains.

Faces — Closed splines from faces.

### Outputs

Curve — Generated curve.

## Mesh to Density Grid Node

### Mesh to Density Grid Node

Transforms mesh surface into a volumetric density grid where each voxel holds a scalar for distance to surface (inside vs. outside). Useful for fog volumes, deformable bodies, or volumetric effects.

Output grids feature smooth transitions: high density inside, low outside. Enables continuous blending and field sampling.

### Inputs

Mesh — Surface to voxelize.

Density — Voxel value inside mesh. Convention: 1.0 full, 0.0 empty; any range works.

Voxel Size — Edge length in object units. Smaller = higher detail, more memory. Larger = faster, coarser.

Gradient Width — Transition zone thickness (object units). Controls falloff steepness; wider = softer edge.

### Outputs

Density Grid — Float grid. Interior voxels high, exterior low; smooth ramp controlled by Gradient Width.

## Mesh to Points Node

### Mesh to Points Node

Generates point cloud from mesh surface.

### Inputs

Mesh — Standard input.

Selection — Source for point generation.

Position — Location of new points. Default: Position Node equivalent.

Radius — Radii of points.

### Properties

Mode — Generation source.

Vertices — One point per vertex.

Edges — One point per edge (centered).

Faces — One point per face (center of mass).

Corners — One per corner (at corner vertex location; overlaps by default).

### Outputs

Points — Generated point cloud.

## Mesh to SDF Grid Node

### Mesh to SDF Grid Node

Converts mesh into signed distance field (SDF): each voxel stores shortest distance to surface, signed for inside/outside. Applies to reconstruction, collision, blending, volumetric shape modeling.

Positive = outside, negative = inside, zero = surface.

### Inputs

Mesh — Surface to distance-field.

Voxel Size — Edge dimension. Smaller = finer detail, more memory/compute. Larger = lower precision, faster.

Band Width — Active region width (voxel units). Only voxels near surface store distances; wider band = more overhead.

### Outputs

SDF Grid — Float grid. Each voxel: signed distance to nearest surface point.

## Mesh to Volume Node

### Mesh to Volume Node

Creates fog volume from mesh geometry. Grid labeled "density".

### Inputs

Mesh — Standard input.

Density — Voxel value inside volume.

Resolution Mode — Voxel specification method.

Amount — Approximate diagonal voxel count.

Size — Voxel side length (caution: small tweaks have large performance impact).

Voxel Amount — Approximate diagonal count.

Voxel Size — Edge length.

Interior Band Width — Maximum distance inside mesh included.

### Outputs

Volume — Generated grid.

## Scale Elements Node

### Scale Elements Node

Scales selected faces or edges individually with per-element scale and pivot. Connected faces/edges scale together using average factor and center.

### Inputs

Geometry — Standard input.

Selection — Boolean; targets elements to scale.

Scale — Factor per element.

Center — Pivot per element.

Axis Single Axis Mode Only — Direction vector (auto-normalized).

Scale Mode

Uniform — Same factor all axes.

Single Axis — Single-direction scaling per Axis input.

### Properties

Domain — Element type.

Face — Faces.

Edge — Edges.

### Output

Geometry — Standard output.

### Examples

Effective with Extrude Mesh Node, especially Individual mode where connected faces don't extrude together.

## Split Edges Node

### Split Edges Node

Duplicates edges (like Edge Split Modifier), severing face links at split boundaries.

### Inputs

Mesh — Standard input.

Selection — Boolean; which edges split. Note: topology constraints may result in more or fewer splits than selected.

### Outputs

Mesh — Standard output.

## Subdivide Mesh Node

### Subdivide Mesh Node

Adds faces using linear subdivision interpolation.

### Inputs

Mesh — Standard input.

Level — Subdivision count.

### Outputs

Mesh — Standard output.

## Subdivision Surface Node

### Subdivision Surface Node

Applies Catmull-Clark smoothing to mesh faces.

### Inputs

Mesh — Standard input.

Level — Subdivision count.

Edge Crease — Sharpness via weighted creases.

Vertex Crease — Vertex attractiveness (like edge creases per vertex).

Limit Surface — Positions vertices at infinite-subdivision limit (maximum smoothness).

UV Smooth — UV smoothing behavior.

None — No UV change.

Keep Corners — Islands smooth, boundaries fixed.

Keep Corners, Junctions — Islands smooth, discontinuous corners and tri-region nodes fixed.

Keep Corners, Junctions, Concave — Islands smooth, corners, junctions, darts, concave shapes fixed.

Keep Boundaries — Islands smooth, edges fixed.

All — Full smoothing.

Boundary Smooth — Open boundary treatment.

All — Smooth all boundaries and corners.

Keep Corners — Smooth edges, sharp corners.

### Outputs

Mesh — Standard output.

## Triangulate Node

### Triangulate Node

Converts all quads and n-gons to triangles; equivalent to Triangulate in Edit Mode.

### Inputs

Mesh — Standard input.

Selection — Boolean; which faces triangulate.

Quad Method

Beauty — Good triangles, slower.

Fixed — Diagonal through vertices 1 and 3.

Fixed Alternate — Diagonal through vertices 2 and 4.

Shortest Diagonal — Splits along shortest edge.

Longest Diagonal — Splits along longest edge (preferred for cloth).

N-gon Method

Beauty — Optimal triangles, slower.

Clip — Ear-clipping tessellation (viewport default).

### Outputs

Mesh — Standard output.

### Example

Before/after triangulation comparison.

## Cone Node

### Cone Node

Generates optionally truncated cone mesh.

### Inputs

Vertices — Top/bottom circle vertex count; minimum 3.

Side Segments — Vertical subdivisions; minimum 1.

Fill Segments — Concentric rings; minimum 1.

Radius Top — Top circle size. Zero = single point.

Radius Bottom — Bottom circle size. Zero = single point.

Depth — Height.

Note: Both radii zero produces a line.

### Properties

Fill Type — Circle fill behavior.

None — No fill.

N-Gon — Single face per circle.

Triangles — Triangle fan from center.

### Outputs

Mesh — Standard output.

Top — Selection: top faces (or edges if Fill Type=None, or vertex if Radius Top=0).

Side — Selection: side faces.

Bottom — Selection: bottom faces (or edges if Fill Type=None, or vertex if Radius Bottom=0).

UV Map — Default 2D coordinates. Connect to Store Named Attribute Node; UV data requires face-corner storage.

## Cube Node

### Cube Node

Generates cuboid mesh with adjustable dimensions and per-axis subdivisions. Interior remains hollow.

### Inputs

Size — Dimension per axis.

Vertices X, Y, Z — Per-side vertex count (minimum 1).

### Outputs

Mesh — Standard output.

UV Map — Default 2D coordinates. Connect to Store Named Attribute Node; UV data requires face-corner storage after modifier application.

## Cylinder Node

The Cylinder node generates a cylinder mesh. It resembles the Cone node but always uses the same radius for the circles at the top and bottom.

Inputs:
Vertices — number of vertices on the circle at the top and bottom; no geometry is generated below three.
Side Segments — number of edges running vertically along the side; no geometry is generated below one.
Fill Segments — number of concentric rings used to fill the round top and bottom faces; no geometry is generated below one.
Radius — distance of the vertices from the Z axis; if zero, the output is a single line.
Depth — height of the cylinder.

Properties:
Fill Type — how the top and bottom circles are filled with faces when their radius is larger than zero.
- None: do not fill the circles.
- N-Gon: fill the innermost segment of the circles with a single face.
- Triangles: fill the innermost segment of the circles with triangles connected to a new vertex on the Z axis.

Outputs:
Mesh — standard geometry output.
Top — a boolean attribute field selecting the faces on the top of the cylinder; if Fill Type is None, this selects the top edges instead, and if Radius is zero, it selects the top point.
Side — a boolean attribute field selecting the faces on the side of the cylinder.
Bottom — the same as the Top selection output, but on the bottom side of the geometry.
UV Map — a 2D vector giving the default X/Y coordinates of the UV Map for the primitive's shape; connect it to the Store Named Attribute Node to use once the Geometry Nodes Modifier is applied. The UV map must be stored on the face corner in order to be accessed.

## Grid Node

### Grid Node

Generates planar mesh on XY plane.

### Inputs

Size X — X dimension.

Size Y — Y dimension.

Vertices X — X vertex count; minimum 2.

Vertices Y — Y vertex count; minimum 2.

### Outputs

Mesh — Standard output.

UV Map — Default 2D coordinates. Connect to Store Named Attribute Node; UV data requires face-corner storage after modifier application.

## Icosphere Node

### Icosphere Node

Generates spherical mesh from equally-sized triangles.

### Inputs

Radius — Distance from origin.

Subdivisions — Iterations beyond base icosphere. Faces quadruple per subdivision.

### Outputs

Mesh — Standard output.

UV Map — Default 2D coordinates. Connect to Store Named Attribute Node; UV data requires face-corner storage after modifier application.

## Mesh Circle Node

### Mesh Circle Node

Generates optionally-filled circular ring.

### Inputs

Vertices — Ring vertex count; minimum 3.

Radius — Distance from origin.

### Properties

Fill Type — Interior fill.

None — Ring only.

N-Gon — Single face.

Triangles — Fan from origin.

### Outputs

Mesh — Standard output.

## Mesh Line Node

### Mesh Line Node

Generates vertex chain connected by edges.

### Inputs

Count — Vertex count.

Resolution — Edge length. Node distributes vertices between start/end; exact end not guaranteed. Available: mode=End Points, count mode=Resolution.

Start Location — First vertex position.

Offset — Line direction and per-vertex distance. Available: mode=Offset.

End Location — Last vertex position. Available: mode=End Points.

### Properties

Mode — Control scheme.

Offset — Per-vertex vector.

End Points — Start and end positions.

Count Mode — Vertex specification (mode=End Points only).

Count — Total vertices.

Resolution — Inter-vertex distance.

### Outputs

Mesh — Standard output.

## UV Sphere Node

### UV Sphere Node

Generates quad-dominant sphere (triangles at poles).

### Inputs

Segments — Horizontal resolution; minimum 3.

Rings — Vertical resolution; minimum 2.

Radius — Distance from origin.

### Outputs

Mesh — Standard output.

UV Map — Default 2D coordinates. Connect to Store Named Attribute Node; UV data requires face-corner storage after modifier application.

## Edge Angle Node

### Edge Angle Node

Outputs radian angle between faces meeting at edge. For face/corner/point domains, interpolates from edge values.

Note: Output depends on mesh density. Denser meshes with same curvature produce different angles.

### Inputs

None.

### Outputs

Unsigned Angle — Shortest angle (0 to PI). Flat and non-manifold edges: 0. Back-folded: PI (180°). Computing this is faster than signed angle; use when distinction unnecessary.

Signed Angle — Signed angle. Flat and non-manifold: 0. Concave positive, convex negative.

## Edge Length Node

### Edge Length Node

Outputs distance between each edge's two vertices.

Enables geometric analysis, mesh-based effects, or procedural tasks dependent on edge metrics (adaptive subdivision, weight mapping, trimming).

### Inputs

None.

### Outputs

Length — Float per edge (scene scale units).

## Edge Neighbors Node

### Edge Neighbors Node

Exposes per-edge topology.

### Inputs

None.

### Outputs

Face Count — Face count using edge. One = boundary edge (non-manifold). Zero = loose (unused).

### Examples

Boundary edge detection for curve creation.

## Edge Vertices Node

### Edge Vertices Node

Outputs position and index of each edge's endpoints.

Note: Vertex order is arbitrary; do not assume consistency.

### Inputs

None.

### Outputs

Vertex Index 1/2 — Indices of edge endpoints.

Position 1/2 — Endpoint positions. Convenience; equivalent to Evaluate at Index Node from indices.

## Edges to Face Groups Node

### Edges to Face Groups Node

Partitions faces into regions divided by boundary edges.

### Inputs

Boundary Edges — Edges splitting face regions.

### Outputs

Face Group ID — Integer identifying each region.

## Face Area Node

### Face Area Node

Outputs surface area per face (Blender units squared; meter-squared at default scale).

For non-planar quads/n-gons, output approximates sum of visible triangles. Triangulate Node yields exact values if needed.

### Inputs

None.

### Outputs

Area — Surface area per face.

### Examples

Paired with Attribute Statistic Node for total surface area.

## Face Corner Angle Node

### Face Corner Angle Node

Outputs per-corner geometry: internal angle and bisector direction.

### Inputs

None.

### Outputs

Corner Angle — Internal angle (radians). Right angle ≈ 1.571.

Bisector — Unit vector along bisector between connected edges.

## Face Group Boundaries Node

### Face Group Boundaries Node

Detects edges bounding specified regions.

Used to mark seams for UV unwrapping, etc.

### Inputs

Face Group ID — Region identifier. Contiguous faces with matching value = same region.

### Output

Boundary Edges — Selection of region borders. An edge is a boundary if adjacent to faces with different identifiers.

### Examples

With UV Unwrap Node, converts face regions into UV maps.

## Is Face Planar Node

### Is Face Planar Node

Tests whether all triangles of a quad or n-gon lie on the same plane (identical normal).

Non-planar faces occur when single vertex moves independently. Triangles always planar.

### Inputs

Threshold — Distance tolerance before face deemed non-planar.

### Outputs

Planar — Boolean per face.

### Examples

With Set Material Node, visualizes non-planar faces.

## Face Neighbors Node

### Face Neighbors Node

Exposes per-face topology.

### Inputs

None.

### Outputs

Vertex Count — Face side count (corner count).

Neighboring Face Count — Adjacent face count (at least one shared edge). On regular manifolds (quads/triangles), matches Vertex Count; otherwise can differ.

## Face Set Node

### Face Set Node

Outputs membership of face in face set; also indicates presence of face sets.

Paired data-flow equivalent: Set Face Set Node. Context: Tool only.

### Inputs

None.

### Output

Face Set — Integer per face or 0 if no face sets exist. Edge/point domain: interpolated from faces.

Exists — Boolean; indicates face set presence.

## Is Edge Boundary Node

### Is Edge Boundary Node

Boolean output: true if edge borders open mesh region.

Boundary edges connect to single face. Useful for detecting holes, boundary effects.

### Inputs

None.

### Outputs

Is Edge Boundary — Boolean per edge. True = single adjacent face.

## Is Edge Loose Node

### Is Edge Loose Node

Boolean output: true if edge unconnected to faces.

Loose edges exist independently of surface; useful for detecting stray geometry, guides, supports.

### Inputs

None.

### Outputs

Is Edge Loose — Boolean per edge. True = no adjacent faces.

## Is Edge Manifold Node

### Is Edge Manifold Node

Boolean output: true if edge manifold (shared by exactly two faces with consistent normals).

Manifold edges are continuous surface without gaps or branching. Useful for identifying topology issues or isolating problem edges.

### Inputs

None.

### Outputs

Manifold — Boolean per edge. True = exactly two adjacent faces; false = one, more than two, or none.

## Is Edge Smooth Node

### Is Edge Smooth Node

Outputs true for edges not marked sharp; false for sharp edges.

See Mark Sharp & Clear Sharp.

### Inputs

None.

### Outputs

Smooth — Boolean per edge.

## Is Face Smooth Node

### Is Face Smooth Node

Outputs true for smooth-shaded faces; false for flat-shaded.

### Inputs

None.

### Outputs

Smooth — Boolean per face. Indicates per-corner-normal averaging with adjacent faces.

## Is UV Split Node

### Is UV Split Node

Selection output: true where UV coordinates differ across an edge (UV seam).

Useful for detecting UV boundaries, islands, or procedural UV-dependent operations.

### Inputs

UV Map — Vector attribute (mesh UVs). Checked for discontinuities.

### Outputs

Is UV Split — Boolean per edge. True = UV discontinuity; false = continuous.

## Mesh Island Node

### Mesh Island Node

Outputs per-island topology: separate connected components where edge-linked vertices form islands.

Mirrors Select Linked (edit mode) and Random per Island (Geometry shader).

### Inputs

None.

### Outputs

Island Index — Per-vertex identifier based on lowest vertex index in island.

Island Count — Total island count (single value, uniform).

## Shortest Edge Paths Node

### Shortest Edge Paths Node

Finds paths along edges to target vertices; cost definition customizable. Default: uniform per-edge; typical: edge length.

Output per-vertex; Next Vertex Index encodes path to nearest endpoint. Dijkstra's algorithm.

Tip: Edge length naturally feeds Edge Cost (Edge Vertices Node + Vector Math distance).

See: Edge Paths to Selection Node, Edge Paths to Curves Node for geometry output.

### Inputs

End Vertex — Selection of path endpoints.

Edge Cost — Per-edge weight.

### Outputs

Next Vertex Index — Following vertex on shortest path to nearest endpoint.

Total Cost — Remaining cost to endpoint.

### Examples

Shortest Edge Paths on deformed Icosphere.

Gradient maze: shortest paths to target.

Organic branching on Suzanne.

## Vertex Neighbors Node

### Vertex Neighbors Node

Outputs per-vertex topology: degree (connected edge/face counts).

### Inputs

None.

### Outputs

Vertex Count — Vertices linked by edges (equal to connected edge count).

Face Count — Faces containing this vertex.

## Sample Nearest Surface Node

### Sample Nearest Surface Node

Retrieves attribute values from closest surface points. Non-face attributes interpolate across surface.

Similar to Geometry Proximity Node but returns any attribute, not just position.

Warning: Samples surface; loose points/edges ignored.

### Inputs

Mesh — Source geometry.

Value — Source field for transfer.

Group ID — Face domain; splits input by id.

Sample Position — Sampling origin (default: Position Node equivalent).

Sample Group ID — Selects group for closest-point search.

### Properties

Data Type — Retrieved value type.

### Outputs

Value — Retrieved and interpolated attribute.

Is Valid — Success indicator; fails when group empty.
