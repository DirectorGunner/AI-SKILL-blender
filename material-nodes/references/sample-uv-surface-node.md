# Sample Uv Surface Node, Corners Of Edge Node, Corners Of Face Node, Corners Of Vertex Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Sample UV Surface Node; Corners of Edge Node; Corners of Face Node; Corners of Vertex Node; Edges of Corner Node; Edges of Vertex Node; Face of Corner Node; Offset Corner in Face Node; Vertex of Corner Node; Pack UV Islands Node; UV Tangent Node; UV Unwrap Node; Set Face Set Node; Set Mesh Normal Node; Set Shade Smooth Node; Smooth By Angle Node Group; Warning Node; Distribute Points in Grid.

## Sample UV Surface Node

Sample UV Surface Node

Queries values on a mesh's surface at specific UV coordinates. Internally, it performs a reverse UV lookup from 2D space—finding the corresponding face and its position for each coordinate.

Warning: Overlapping faces in the UV map cause issues. At locations with missing or overlapping faces, the node outputs the default zero value for most data types.

Inputs
Mesh: Geometry containing the mesh with the UV map to sample.
Value: A field to evaluate on the target geometry for later sampling at surface positions.
UV Map: The mesh's UV map to sample, evaluated on the Mesh input. Should not have overlapping faces.
Sample UV: The coordinates to sample within the UV map.

Properties
Data Type: The format for retrieved values.

Outputs
Value: Retrieved and interpolated data from the geometry, mapped per the node settings.
Is Valid: Whether the node successfully found a single face to sample at the coordinate.

## Corners of Edge Node

Corners of Edge Node

Selects a neighboring face corner from an edge and outputs its index.

This node operates across two domains. It calculates Weight for each corner, then for each context item:

- Selects an edge via Edge Index.
- Finds face corners touching the edge.
- Ranks these corners by weight.
- Picks one using Sort Index (0 = lowest weight, 1 = second-lowest).
- Outputs the corner's geometry-wide index.

Warning: Only one corner per face connects through this node. An edge has four neighboring corners total, but Corner Index retrieves only two. Use Offset Corner in Face Node to access the rest.

Inputs
Edge Index: Index of the edge for which to find connected corners. If unconnected, uses the context item index in the Edge domain.
Weights: Corner weights in the geometry. Always evaluated in the Face Corner domain. Corners sort ascending by weight, with ties sorted by index.
Sort Index: Zero-based index for selection from sorted corners. Wraps around if out of range.

Outputs
Corner Index: The geometry-wide index of the selected corner. Pass this to Evaluate at Index Node or Sample Index Node (Face Corner domain). Zero if the edge has no connected corners.
Total: Number of faces connected to the edge.

## Corners of Face Node

Corners of Face Node

Selects a corner from a face and outputs its index.

This node operates across two domains. It calculates Weight for each corner, then for each context item:

- Picks a face via Face Index.
- Finds corners on the face.
- Ranks corners by weight.
- Selects one using Sort Index (0 = lowest weight, 1 = second-lowest).
- Outputs the corner's geometry-wide index.

Inputs
Face Index: Index of the face for which to find corners. If unconnected, uses the context item index in the Face domain.
Weights: Corner weights in the geometry. Always evaluated in the Face Corner domain. Corners sort ascending by weight, with ties sorted by index.
Sort Index: Zero-based index for selection from sorted corners. Wraps around if out of range.

Outputs
Corner Index: The geometry-wide index of the selected corner. Pass this to Evaluate at Index Node or Sample Index Node (Face Corner domain).
Total: Number of corners in the face, equivalent to the edge count.

## Corners of Vertex Node

Corners of Vertex Node

Selects a neighboring face corner from a vertex and outputs its index.

This node operates across two domains. It calculates Weight for each corner, then for each context item:

- Selects a vertex via Vertex Index.
- Finds face corners touching the vertex.
- Ranks corners by weight.
- Picks one using Sort Index (0 = lowest weight, 1 = second-lowest).
- Outputs the corner's geometry-wide index.

Inputs
Vertex Index: Index of the vertex for which to find corners. If unconnected, uses the context item index in the Point domain.
Weights: Corner weights in the geometry. Always evaluated in the Face Corner domain. Corners sort ascending by weight, with ties sorted by index.
Sort Index: Zero-based index for selection from sorted corners. Wraps around if out of range.

Outputs
Corner Index: The geometry-wide index of the selected corner. Pass this to Evaluate at Index Node or Sample Index Node (Face Corner domain).
Total: Number of adjacent corners, equivalent to the face count.

## Edges of Corner Node

Edges of Corner Node

Gives you the two edges that flank a face corner.

Inputs
Corner Index: Index of the input face corner. By default uses the context index, making it important the node evaluates in the face corner domain.

Outputs
Next Edge Index: Index of the neighboring edge in the direction of increasing face corner indices.
Previous Edge Index: Index of the neighboring edge in the direction of decreasing face corner indices.

## Edges of Vertex Node

Edges of Vertex Node

Selects a neighboring edge from a vertex and outputs its index.

This node operates across two domains. It evaluates a Weight for each edge, then for each context item:

- Picks a vertex via Vertex Index.
- Locates edges connected to the vertex.
- Sorts these edges by weight.
- Picks an edge using Sort Index (0 = lowest weight, 1 = second-lowest).
- Outputs the geometry-wide edge index.

Inputs
Vertex Index: Index of the vertex for which to find edges. If unconnected, uses the context item index in the Point domain.
Weights: Edge weights in the geometry. Always evaluated in the Edge domain. Edges sort ascending by weight, with ties sorted by index.
Sort Index: Zero-based index for selection from sorted edges. Wraps around if out of range.

Outputs
Edge Index: The geometry-wide index of the selected edge. Pass this to Evaluate at Index Node or Sample Index Node (Edge domain). Zero if the vertex has no connected edges.
Total: Number of edges connected to the selected vertex.

Example: Creating Vertical-Aligned Cones on Cube Vertices

This example places a cone at each cube vertex, aligned to the most vertical neighboring edge.

First, each cube edge receives a "verticality score" by subtracting vertex positions for the direction vector, normalizing, and computing the Z-axis dot product. The absolute value gives a 0–1 range (0 = fully horizontal, 1 = fully vertical).

Since edges sort by ascending weight, set weight = 1 − verticality so the most vertical edge ranks first.

Next, in the point domain, calculate cone rotation using Align Rotation to Vector Node, requiring only the direction vector.

The cone's direction is the midpoint of the most vertical neighboring edge minus the vertex position. Edges of Vertex selects that edge (Sort Index = 0), then Evaluate at Index Node retrieves its midpoint.

Finally, Instance on Points Node creates the cones using the calculated rotations.

## Face of Corner Node

Face of Corner Node

Retrieves the face that a face corner belongs to.

Inputs
Corner Index: The geometry-wide index of the corner. If unconnected, uses the context item index, making the Face Corner domain important.

Outputs
Face Index: The geometry-wide index of the containing face.
Index in Face: The face-local index of the corner (0 for first, 1 for next, up to number−1).

## Offset Corner in Face Node

Offset Corner in Face Node

Steps around the face to fetch a different corner belonging to that same face.

This operation is conceptually similar to Offset Point in Curve Node.

Inputs
Corner Index: Index of the input face corner. If unconnected, uses the context item index in the Face Corner domain.
Offset: Number of corners to move around the face, wrapping to the start if needed.

Outputs
Corner Index: Index of the offset face corner.

## Vertex of Corner Node

Vertex of Corner Node

Returns the index of whichever vertex a face corner connects to.

Inputs
Corner Index: Index of the face corner. If unconnected, uses the context item index in the Face Corner domain.

Outputs
Vertex Index: Index of the vertex that the face corner attaches to.

## Pack UV Islands Node

Pack UV Islands Node

Rearranges UV islands for efficient space use. Islands scale, translate, rotate with margins. Procedurally optimizes within Geometry Nodes—atlases, bake prep.

Tip: In contrast to the UV Editor operator, this node runs non-destructively and takes procedural inputs, which makes it a good fit for automated or parametric UV workflows.

Inputs
UV: The UV map to pack. Island topology is determined from this input.
Selection: Faces to include when packing. Only islands containing at least one selected face are affected. UVs on unselected faces stay unchanged.
Margin: Distance between islands in UV space units.
Rotate: Allow island rotation for more efficient packing.
Method: How each island's shape is evaluated.
  Bounding Box: Uses the axis-aligned bounding box. Fastest but less space-efficient.
  Convex Hull: Uses the convex hull. Balances accuracy and performance, won't place islands inside holes.
  Exact Shape: Uses the full island shape including concave regions and holes. Tightest packing but slowest.
Bottom Left: The bottom-left corner of the region for packing.
Top Right: The top-right corner of the region for packing.

Output
UV: Packed UVs with islands repositioned and scaled per node settings.

## UV Tangent Node

UV Tangent Node

Generates tangent vectors from a UV map. Unit-length, on-surface vectors point along increasing U. Uses: normal mapping, anisotropy.

Exact or approximate computation, trading precision vs. performance.

Inputs
Method: Algorithm for tangent computation.
  Exact: MikkTSpace algorithm, consistent with Blender's shading and exports. Aligns with normal map space.
  Fast: Approximate, interpolates across matching UV corners. Similar results, lower cost, less consistent on complex surfaces. Cross with normal for exact alignment.
UV: Map for tangent calculation. Determines orientation across the surface.

Outputs
Tangent: Tangent vector from the UV map. Normalized field on the surface, points along increasing U. Combine with normals and bitangents for tangent space basis.

## UV Unwrap Node

UV Unwrap Node

Generates a UV map from islands based on a selection of seam edges. The node implicitly packs islands afterward, since results may not be generally useful otherwise.

See also: The UV editor's Unwrap operator does the same. This node skips aspect ratio correction—add it yourself with Vector Math Node if needed.

Inputs
Selection: Faces to participate in unwrap. UVs on any other face remain unaffected.
Seam: Edges marking where the mesh is "cut" for unwrapping.
Margin: Distance between UV islands.
Fill Holes: Temporarily plug the mesh's holes ahead of unwrapping, which helps dodge overlaps and keep symmetry intact.
Method:
  Angle Based: Produces a good 2D mesh representation.
  Conformal: Uses LSCM (Least Squares Conformal Mapping). Usually less accurate than Angle Based but works better for simpler objects.

Output
UV: Generated UV coordinates between 0 and 1 for each face corner in selected faces.

Note: To make Blender recognize it as a UV map, use Store Named Attribute Node on the Face Corner domain with 2D Vector data type (no 2D Vector socket exists).

## Set Face Set Node

Set Face Set Node

Controls which face set that faces belong to.

The input node for this data is the Face Set Node.

Note: This node can only be used in the Tool context.

Inputs
Mesh: Standard geometry input.
Selection: Boolean field controlling which faces will have the Face Set value applied.
Face Set: Integer field specifying which face set each selected face should move to. Ignored for faces where Selection is false.

Outputs
Mesh: Standard geometry output.

## Set Mesh Normal Node

Set Mesh Normal Node

Stores a normal vector for each mesh element, controlling shading and influencing operations that use surface normals.

Inputs
Mesh: Standard geometry input.
Remove Custom Sharpness: If enabled, removes any existing custom normals or sharpness data. (Sharpness mode)
Edge Sharpness: Boolean field defining whether an edge is marked sharp. True = sharp edges, false = smooth shading. (Sharpness mode)
Face Sharpness: Boolean field defining whether a face is marked flat. True = flat-shaded faces, false = smooth shading. (Sharpness mode)
Custom Normal: The vector to store as the custom normal. (Free mode, Tangent Space mode)

Properties
Mode: Storage mode for custom normal data.
  Sharpness: Store face or edge sharpness, like "Shade Smooth" and "Shade Flat" operators.
  Free: Keep custom normals as plain vectors expressed in the mesh's local space. Fast, but offers no deformation support.
  Tangent Space: Store normals in a deformation-aware transformation space. Slower but handles mesh changes better.
Domain (Free mode): Where to store free custom normals.
  Point: Per-vertex normals.
  Face: Per-face normals.
  Face Corner: Per-corner normals. Needed to bake mixed sharp and smooth edges into custom vectors.

Outputs
Mesh: Standard geometry output.

## Set Shade Smooth Node

Set Shade Smooth Node

Controls whether mesh faces appear smooth in the viewport and renders. Sets smooth status for edges and faces via sharp_edge and sharp_face attributes. The input node for this data is Is Face Smooth Node.

Inputs
Mesh: Standard geometry input.
Shade Smooth: When true, selected faces render smooth. Otherwise flat shaded.
Selection: Boolean input selecting which faces receive the Shade Smooth value.

Properties
Domain: Choose whether smoothness gets written onto faces or onto edges.

Outputs
Mesh: Standard geometry output.

## Smooth By Angle Node Group

Smooth By Angle Node Group

Set mesh edge sharpness based on the angle between neighboring faces.

Note: This asset is included in the bundled "Essentials" library.

Inputs
Mesh: Standard geometry input.
Angle: Threshold for faces to be considered smooth.
Ignore Sharpness: Smooth all edges, even marked ones.

Outputs
Mesh: Standard geometry output.

## Warning Node

Warning Node

Outputs a custom message in the Geometry Nodes modifier's Warnings panel. Lets node groups communicate expectations, assumptions, and error conditions about inputs—required ranges, missing data, unsupported configs.

Warnings propagate through parent node groups by default, controlled via the Propagation setting on each node.

Inputs
Show: Controls whether the warning displays. When disabled, it suppresses.
Message: Text describing incorrect inputs, required conditions, or other info for users.

Properties
Warning Type: Severity affecting the icon shown.
  Info: Informational, no problem indicated.
  Warning: Potential issue that may cause unexpected results.
  Error: Invalid configuration likely producing incorrect results.

Outputs
Show: Passes the Show input through, forwarding the warning state to other nodes.

## Distribute Points in Grid

Distribute Points in Grid

Generates points within the active region of a voxel grid. Point count and placement use the grid's density values and distribution parameters.

Useful for procedurally scattering geometry in volumetric regions—distributing particles in fog, populating simulation domains, or sampling SDF/density grid areas.

Inputs
Grid: Input grid defining the volume for point distribution. Values determine placement—typically by density or occupancy.
Density (Random): Scaling factor for voxel values, setting expected points per unit volume. Higher = denser.
Seed (Random): Seed for reproducible results. Change to alter the random distribution.
Spacing (Grid): Distance between points in Grid mode. Controls packing tightness.
Threshold (Grid): Minimum voxel density to place a point. Ignores below-threshold voxels.

Properties
Distribution Method: How to scatter points.
  Random: Random placement weighted by voxel density, creating a natural, stochastic pattern.
  Grid: Regular grid pattern. Spacing input sets point distance.

Outputs
Points: Generated points inside the grid's active volume, distributed per method and parameters.

## Distribute Points in Volume

Distribute Points in Volume

Creates points inside volume grids in two modes: random or regular grid. Both work on all float grids.

Inputs
Volume: Standard volume geometry input.
Mode:
  Random: Random placement inside the volume. Local count = Density × voxel value. Distribution destabilizes as the volume deforms.
  Grid: Grid pattern inside the volume. Voxel value determines whether to place a point.
Density (Random): Points per unit volume.
Seed (Random): Random number generator seed.
Spacing (Grid): Distance between grid points.
Threshold (Grid): Minimum cell value for a grid point.

Outputs
Points: Standard point cloud geometry output.

## Distribute Points on Faces

Distribute Points on Faces

Places points on the input surface. Point, corner, and polygon attributes transfer to generated points, including vertex weights and UV maps. A stable ID in the id attribute identifies each point. When the mesh deforms or density changes, values stay consistent. Normal and Rotation outputs also include attributes.

Inputs
Mesh: Standard geometry input. Must contain faces.
Selection: Which face corners participate in distribution.
Distance Min: Minimum distance between points. Poisson Disk only. Default zero = Random mode behavior.
Density Max: Point density (points per square meter). Multiplies by Density input. Poisson Disk only. Capped by Distance Min—if density exceeds what distance allows, no new points add.
Density: Points per square meter per face. Multiplied by Density Attribute. In Poisson Disk mode, multiplied by Density Max.
Seed: Random seed for generating points.

Properties
Distribution Method:
  Random: Random surface placement. Fastest.
  Poisson Disk: Random with minimum distance constraint.
Legacy Normal: Uses smooth and custom normals by default. Older behavior (true normals only) available in Sidebar.

Outputs
Points: Generated points with named attributes copied from the mesh.
Normal: The normal of the triangle where each point scatters.
Rotation: XYZ Euler rotation built from the normal. Also buildable via Euler to Rotation Node. Z axis is arbitrary (normal has insufficient info for all three axes).

## Points Node

Points Node

Generates a point cloud with positions and radii from fields.

Inputs
Count: Number of points to create.
Position: Position of each point.
Radius: Radius of each point. Since the cloud is created fresh, Position and Radius depend on the index node only. Regular input nodes don't work.

Outputs
Points: Standard geometry output.

## Points to Curves Node

Points to Curves Node

Generates a Curves geometry by converting all points to new curves. Point attributes propagate to Curve Points. Built-in curves attributes in points are ignored.

Tip: Link each point's weight to an attribute value to control order in the curve. Sorting and grouping use Weight and Group ID.

Inputs
Points: The Point Cloud geometry component.
Curve Group ID: Points with the same ID join in one curve. Any value works (negative, zero, infinity). Curves must have at least one point. Order depends on ID value and its order in the Point Cloud.
Weight: For curves with multiple points, Weight defines order via sorting. Minimal values start the curve, maximum end it. Same-weight points keep their original order.

Outputs
Curves: Curves with points joined from the Point Cloud. Other components don't save. Always non-cyclic.

Examples: Create curve arrays with connections by duplicating the Arc primitive, shifting each up by index, converting to Point Cloud, then back to curves. All Point Cloud attributes become curve point attributes.

## Points to SDF Grid

Points to SDF Grid

Generates a Signed Distance Field (SDF) grid from input points. Each voxel stores the shortest signed distance to the nearest point, representing them as smooth, volumetric shapes.

Positive values = outside point influence, negative = inside, zero = surface of the implicit sphere.

Useful for constructing volumetric fields or collision volumes from particles, instances, or procedural clouds.

Inputs
Points: Input points defining the SDF centers.
Radius: Influence radius per point. Each point is a sphere; distance extends this far. Defines how far signed distance reaches.
Voxel Size: Voxel size in object units. Smaller = higher resolution, finer detail, more memory and time.

Outputs
SDF Grid: A scalar float grid of the signed distance field. Each voxel holds the shortest distance to any point's surface—negative inside the spheres, positive outside.

## Points to Vertices Node

Points to Vertices Node

Generates a mesh vertex for each point cloud point in the input geometry.

Inputs
Geometry: Standard geometry input.
Selection: Boolean field determining if each point converts to a vertex.

Outputs
Geometry: Standard geometry output.

## Points to Volume Node

Points to Volume Node

Generates a fog volume sphere around every point. The grid is named "density".

Usually combine with Volume to Mesh Node.

Warning: Point positions should not be extremely large. Billion-scale values give unstable results.

Inputs
Points: Standard geometry input.
Density: Voxel value inside the fog volume.
Resolution Mode: How to specify voxel size.
  Amount: Approximate voxels along the diagonal.
  Size: Voxel side length. Tweaking carefully—small changes affect time significantly.
Voxel Amount (Amount): Approximate voxels along the diagonal.
Voxel Size (Size): Voxel side length.
Radius: Sphere radius generated per point.

Outputs
Volume: Standard geometry output.

## Set Point Radius Node

Set Point Radius Node

Controls how large selected point cloud points display in the viewport.

The input node for this data is Radius Node.

Inputs
Geometry: Standard geometry input.
Radius: Float value for the point radius.
Selection: Boolean input selecting which points receive the radius.

Outputs
Geometry: Standard geometry output.
