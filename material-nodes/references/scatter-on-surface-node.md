# Scatter On Surface Node, Geometry Input Node, Material Index Node, Material Selection Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Scatter on Surface Node; Geometry Input Node; Material Index Node; Material Selection Node; Replace Material Node; Set Material Node; Set Material Index Node; Bake Node; Bounding Box Node; Convex Hull Node; Delete Geometry Node; Displace Geometry Node; Duplicate Elements Node; Merge by Distance Node; Separate Components Node; Separate Geometry Node; Smooth Geometry Node; Sort Elements Node.

## Scatter on Surface Node

Scatter on Surface Node

Distributes points or instances across mesh surfaces using density control, random or Poisson disk sampling, and optional masking. Useful for procedural ground scatter (grass, rocks, debris).

Inputs:
Mesh — Target surface.
Selection — Face/area inclusion. Unselected regions skip distribution.

Density Method — Point-count control:
Density — Per-unit-area field.
Amount — Fixed total count.

Distribution Method Density — Density pattern:
Random — Uniform random placement.
Poisson Disk — Minimum-distance even spacing.

Density Density — Per-area point count.

Amount Amount — Total point count.

Distribution Mask — Limiting field (1.0 allows, 0.0 blocks).

Minimum Distance Poisson Disk — Minimum inter-point spacing.

Keep Surface — Retain original surface in output (vs. instances-only).

Scatter on Instances — Scatter on existing instances rather than a single mesh.

Seed — Random generator initialization.

Instancing:
Input Type — Source:
Data-Block — Object or collection.
Geometry — Input geometry.
Instance Type Data-Block — Object or Collection.
Object / Collection Data-Block — Target object or collection.
Instance Geometry — Geometry input.
Viewport Visibility — Visible instance percentage.
Realize Instances — Convert instances to real geometry.

Pick Instance Data-Block Collection — Random or directed child object selection:
Reset Transform — Restore instance transform before applying scatter.
Instance Seed — Randomization per element.

Transform:
Surface Offset — Normal-direction offset.
Align Rotation — Element orientation alignment.
Alignment Axis — Alignment direction.
Scale — Uniform or per-axis scaling.

Randomize (toggleable in panel header):
Offset — Maximum translation per axis.
Rotation — Maximum rotation per axis.
Scale Axes — Scaling application:
Uniform — Single factor.
Axes — Independent factors.
Scale — Maximum scale factor.
Flipping — Random per-axis mirroring.
Seed — Random number initialization.

Masking:
Image Mask — Scattering density controller via UV-mapped image.
UV Map — UV channel for mask interpretation.

Outputs:
Instances — Scattered instances per method and parameters.

## Geometry Input Node

Geometry Input Node

Provides geometry from external objects, collections, or input connections for use within a node group.

Inputs:
Geometry — Input to the group from connected sockets.

Input Type — Source mode:
Object — Single object.
Collection — All objects within a collection.

Object / Collection — Target object or collection.

Relative Space — Transform relative to local modifier/geometry space instead of world space.

As Instance — Add as instance instead of merging.

Replace Original — When true, replace incoming geometry with the selected source. When false, append the source.

Outputs:
Geometry — Resulting geometry from the selected source or input connection.

## Material Index Node

Material Index Node

Outputs which material slot in the geometry each element belongs to. Currently supports mesh data via the material_index built-in face attribute.

Related: Set Material Index node provides input control.

Inputs: None

Outputs:
Material Index — Integer value (minimum zero).

## Material Selection Node

Material Selection Node

Selects faces using a target material. Output faces select implicitly interpolate to other domains. Example: all vertices connected to a selected face become selected.

Inputs:
Material — Material to match.

Outputs:
Selection — Face selection for the input material.

## Replace Material Node

Replace Material Node

Swaps one material for another. More efficient than Material Selection Node plus Set Material Node for single replacements.

Note: Currently affects mesh data only.

Inputs:
Geometry — Standard geometry input.
Old — Material to be replaced.
New — Replacement material.

Outputs:
Geometry — Standard geometry output.

## Set Material Node

Set Material Node

Changes material assignment via material_index modification. If the material already exists, the existing index is reused.

Note: Operates on mesh, point cloud, and volume data; other types do not support materials.

Inputs:
Geometry — Standard geometry input.
Material — Material to apply.
Selection — Modify boolean per face. True applies, false preserves. For volumes and point clouds, field input is ignored (single material only).

Outputs:
Geometry — Standard geometry output.

## Set Material Index Node

Set Material Index Node

Sets the material index for geometry.

Related: Material Index node reads this attribute.

Inputs:
Geometry — Standard geometry input.
Selection — Boolean mask for which faces change. True applies, false preserves.
Material Index — New index value.

Outputs:
Geometry — Standard geometry output.

## Bake Node

Bake Node

Saves and retrieves intermediate geometries, baking portions of the node tree for performance gains. Geometry format is internal (non-interoperable except volumes, which use OpenVDB).

Important: Data compatibility between Blender versions is not guaranteed.

Inputs:
Geometry — Default bake item. Additional items via socket dragging into blank sockets or Bake Items panel. Renaming: Ctrl - LMB on socket name or Properties panel.

Bake Items:
Reference: Geometry Node Editor, Sidebar ‣ Node ‣ Bake Items

Bake Items Panel — Input/output socket management:
Bake Items List — Add, remove, rename, sort items.
Socket Type — Data (Sockets) to bake.
Attribute Domain — Field evaluation domain.
Is Attribute — Item is a stored geometry attribute.

Properties:
Note: Some properties edit only in Properties panel (Sidebar ‣ Node ‣ Properties).

Bake Mode — Frame selection:
Animation — Multiple frames. Scene range by default; Custom Range override available.
Still — Current frame only.

Bake — Execute geometry calculation and save.

Pack/Unpack — Consolidate or extract baked data. Unpacking offers options matching Unpack Resources operator.

Delete Geometry Node Bake — Remove bake data.

Bake Target — Storage location:
Inherit from Modifier — Copy modifier setting.
Packed — Embed in .blend file.
Disk — Separate directory.

Custom Path — Manual storage path.

Bake Path — Disk location. Also used for simulation zones.

Custom Range Animation — Override scene range.
Start, End — Frame boundaries.

Outputs:
For each input, a matching output acts as pass-through.
Geometry — Default bake item. Additional items via socket dragging or Bake Items panel. Renaming: Ctrl - LMB on socket name or Properties panel.

## Bounding Box Node

Bounding Box Node

Creates the smallest box mesh encapsulating the input geometry and outputs bounding corner coordinates.

The mesh and Min/Max outputs ignore instances; instead, each instance receives its own bounding box. For instance-inclusive bounds, use Realize Instances Node.

Inputs:
Geometry — Standard geometry input.
Use Radius — When enabled, incorporates the radius attribute during bound computation for curves, point clouds, and Grease Pencil data.

Outputs:
Bounding Box — Encapsulating box mesh.
Min — Box corner at negative X, Y, Z extents.
Max — Box corner at positive X, Y, Z extents.

Examples:
Box encapsulating the monkey mesh via Bounding Box node.

## Convex Hull Node

### Convex Hull Node

Generates a mesh that wraps around and encloses all input geometry points.

When applied to instanced geometry, the algorithm processes each instance separately, producing a distinct convex shape per instance. Use the Realize Instances node to consolidate instance data before computing, if a single hull across all instances is needed.

Limitations: volumes cannot be processed by this operation; input attributes are not carried forward to output. Due to floating-point precision constraints, points lying very close together may merge in the output geometry.

**Inputs**
- Geometry: Standard input.

**Outputs**
- Convex Hull: Enclosing mesh.

## Delete Geometry Node

### Delete Geometry Node

Removes specified geometry elements from the input. Operates analogously to Edit Mode deletion. The domain and mode properties control which element types are removed.

**Inputs**
- Geometry: Standard input.
- Selection: Boolean field marking elements for removal.

**Properties**
- Domain: Scope of deletion.
  - Point: Remove vertices, control points, and base points.
  - Edge: Remove mesh edges; other components unaffected.
  - Face: Remove mesh faces; other components unaffected.
  - Spline: Remove entire splines if selected; unchanged otherwise.
  - Instance: Remove top-level instances; realized geometry persists.

- Mode: Deletion granularity (mesh only).
  - All: Remove vertices, edges, and faces together.
  - Only Edges & Faces: Preserve vertices even if selected.
  - Only Faces: Remove only faces.

**Output**
- Geometry: Standard output.

## Displace Geometry Node

### Displace Geometry Node

Shifts geometry components along a direction vector or surface normal, creating deformations. Useful for texture-based detail, wave simulation, or field-driven surface variation.

**Inputs**
- Geometry: Elements to offset.
- Selection: Boolean field; unselected parts remain stationary.
- Strength: Magnitude of displacement per element.
- Offset Method: How direction is computed.
  - Normal: Move along local surface normal.
  - Vector: Move along supplied vector (normalized internally).
- Offset Distance Normal: Distance in Normal mode.
- Offset Vector: Vector input in Vector mode.
- Substeps: Count of iterative steps; fields recomputed at each step for stability.
- Post Substep Process: Closure applied after each substep, receiving geometry, selection, strength, and substep index.

**Outputs**
- Geometry: Displaced result.

## Duplicate Elements Node

### Duplicate Elements Node

Replicates selected geometry elements multiple times. Duplicates occupy identical positions; differentiation requires subsequent positioning operations.

**Inputs**
- Geometry: Standard input.
- Selection: Boolean field for duplication targets.
- Amount: Per-element count; zero means omit the element.

**Properties**
- Domain: Element type to duplicate.
  - Point: Replicate points; other types excluded.
  - Edge: Replicate edges; faces omitted.
  - Faces: Replicate faces independently (no shared edges).
  - Spline: Replicate entire splines.
  - Instances: Replicate top-level instances.

**Outputs**
- Geometry: Standard output.
- Duplicate Index: Attribute field (0 to Amount - 1) marking which iteration each output element represents. Useful with Geometry to Instance for efficient array-like behavior.

## Merge by Distance Node

### Merge by Distance Node

Combines nearby mesh vertices or point cloud points within a specified threshold, also consolidating adjacent geometry. Similar to the Merge operator or Weld Modifier.

**Inputs**
- Geometry: Standard input.
- Selection: Boolean; unselected points are skipped and unaffected.
- Mode: Selection strategy.
  - All: Merge all geometry including isolated parts.
  - Connected: Merge only attached geometry; isolated parts remain separate.
- Distance: Threshold for considering points neighbors.

**Output**
- Geometry: Standard output.

Tip: Selection input improves performance by excluding unneeded points from the expensive neighborhood search.

## Separate Components Node

### Separate Components Node

Splits geometry into distinct outputs by type (mesh, curves, points, volumes, instances).

**Inputs**
- Geometry: Standard input.

**Outputs**
- Mesh: Mesh component.
- Curve: Curve component.
- Point Cloud: Point cloud component.
- Volume: Volume component.
- Instances: All instances, even if containing other geometry types. Use Realize Instances to transfer instance content to corresponding outputs.

## Separate Geometry Node

### Separate Geometry Node

Splits input geometry into two outputs based on a selection criterion.

**Inputs**
- Geometry: Standard input.
- Selection: Boolean field; true values route to Selection output, false to Inverted.

**Properties**
- Domain: Evaluation scope.
  - Point: Applies to base points and control points.
  - Edge: Applies to edges; others unaffected.
  - Faces: Applies to faces; others unaffected.
  - Spline: Applies to splines as units (whole or none); others unaffected.

Note: Components not affected by the chosen domain appear in both outputs.

**Outputs**
- Selection: Chosen geometry.
- Inverted: Remaining geometry.

Tip: Combine with Compare Node for refined separation logic.

## Smooth Geometry Node

### Smooth Geometry Node

Averages element positions with neighbors to reduce roughness and create organic appearance while preserving overall form.

**Inputs**
- Geometry: Source.
- Selection: Boolean; unselected elements stay fixed.
- Iterations: Pass count; higher values = stronger smoothing.
- Weight: Blend factor for neighbor influence.

**Outputs**
- Geometry: Smoothed result.

## Sort Elements Node

### Sort Elements Node

Reorders geometry elements via index permutation.

**Inputs**
- Geometry: Standard input.
- Selection: Boolean; sort scope (all if blank).
- Group ID: Cluster ID; elements with matching IDs sort as groups.
- Sort Weight: Values driving reorder.

**Properties**
- Domain: Field evaluation scope.
  - Point: Base/control points.
  - Edge: Mesh edges.
  - Faces: Mesh faces.
  - Spline: Curve splines.
  - Instance: Top-level instances.

**Outputs**
- Geometry: Standard output.

## Split To Instances Node

### Split To Instances Node

Groups geometry elements (e.g., faces) by ID, then converts each group into an instance.

**Inputs**
- Geometry: Standard input.
- Selection: Boolean; included elements.
- Group ID: Integer cluster identifier.

**Properties**
- Domain: Element type and field scope.
  - Point: Base/control points.
  - Edge: Edges.
  - Face: Faces.
  - Spline: Splines.
  - Instance: Top-level instances.
  - Layer: Grease Pencil layers.

Note: Geometry outside the chosen domain is removed (e.g., selecting Edge drops faces and splines).

**Outputs**
- Instances: Grouped geometry.
- Group ID: Cluster index per instance.

Example: 1000x1000 grid of square faces, each assigned a group ID from a Voronoi texture (multiplied by 1000 to exceed 0–1 range), then translated by random Z offset per group.

## Transform Geometry Node

### Transform Geometry Node

Applies translation, rotation, or scaling to entire geometry as a single unit. For per-element movement, use Set Position Node; for instance-level transforms, use dedicated instance nodes.

**Inputs**
- Geometry: Standard input.
- Mode: Specification method.
  - Components: Separate location, rotation, scale inputs.
  - Matrix: Transformation matrix.
- Translation: Offset in local space.
- Rotation: Euler angles in local space.
- Scale: Scale multiplier in local space.
- Transform: Matrix (Matrix mode only).

**Output**
- Geometry: Standard output.

## Active Element Node

### Active Element Node

Outputs the index of the currently active point, edge, face, or layer.

Constraint: Tool context only.

**Inputs**
None.

**Properties**
- Domain: Target element type.

**Outputs**
- Index: Active element position.
- Exists: True if active element is present.

## ID Node

### ID Node

Retrieves the integer stable-random identifier stored per-point on the id attribute. Set this via Set ID Node.

Note: The id attribute does not automatically exist. If absent, this node returns the index.

**Inputs**
None.

**Outputs**
- ID: Integer value.

## Index Node

### Index Node

Returns an integer position for each element in the geometry list, starting at zero. Actual order depends on internal topology logic, visible in the Spreadsheet Editor's leftmost column.

**Inputs**
None.

**Outputs**
- Index: Element position.

Caution: Indices follow internal algorithm ordering and may not be predictable when inputs change. They may also vary across Blender versions as algorithms are updated. For stable references, compute indices locally or avoid topology-changing operations when consistency over time is critical.

## Named Attribute Node

### Named Attribute Node

Reads attribute data from geometry based on field context.

**Inputs**
- Name: Attribute identifier.

**Properties**
- Data Type: Retrieved data type. Attribute Search suggests matching names and types from the geometry.

**Outputs**
- Attribute: Data from geometry.
- Exists: True if attribute is present.

## Position Node

### Position Node

Outputs the location vector for each point. Works across domains via interpolation (e.g., edge position = average of vertices). For instances, outputs origin position; in instance-local contexts, outputs local space position.

**Inputs**
None.

**Outputs**
- Position: Coordinates per element.

## Radius Node

### Radius Node

Returns the radius value at each point. Used by Curve to Mesh node for mesh size; in point clouds, controls viewport display size.

**Inputs**
None.

**Outputs**
- Radius: Float per point.

## Selection Node

### Selection Node

Outputs true for geometry marked as selected in Edit Mode, false elsewhere.

Constraint: Tool context only.

**Inputs**
None.

**Outputs**
- Selection: Boolean per element.

Set this via Set Selection Node.

## Geometry Proximity Node

### Geometry Proximity Node

Computes the nearest location on target geometry for each source point.

**Inputs**
- Geometry: Source.
- Group ID: Partitions input into searchable groups.
- Sample Position: Query point.
- Sample Group ID: Search scope.

**Properties**
- Target Element: Search surface.
  - Faces: Face surface.
  - Edges: Edge surface.
  - Points: Vertices (mesh or point cloud; fastest).

**Outputs**
- Position: Nearest location.
- Distance: Float distance.
- Is Valid: Success flag (fails if group is empty).

Tip: Map Range Node often pairs with distance output for falloff.

Example: Different modes (faces, edges, points) shown with subdivided/unsubdivided meshes; sphere-distributed points as target.

## Index of Nearest

### Index of Nearest

Finds the closest element in the same geometry component.

**Inputs**
- Position: Query location (default = Position Node).
- Group ID: Cluster scope.

**Outputs**
- Index: Closest element.
- Has Neighbor: True if group has ≥2 elements.

Differs from Sample Nearest Node: no geometry input required (uses field context). Often combined with Evaluate at Index Node or Sample Index Node.

## Raycast Node

### Raycast Node

Casts rays from source geometry onto target geometry, returning hit locations, normals, distances, and interpolated attributes.

**Inputs**
- Target Geometry: Ray target.
- Attribute: Optional field evaluated on target; interpolated at hit.
- Interpolation: Mapping strategy.
  - Interpolated: Smooth barycentric blending.
  - Nearest: Closest vertex value.
- Source Position: Ray origin (default = Position Node).
- Ray Direction: Ray vector (evaluated on source context).
- Ray Length: Max distance before "no hit."

**Properties**
- Data Type: Output type.

**Outputs**
- Is Hit: True if ray intersects.
- Hit Position: Intersection point.
- Hit Normal: Surface normal at intersection.
- Hit Distance: Distance from origin (or Ray Length if no hit).
- Attribute: Interpolated result.

### Raycast Node

Cast a ray into the scene and report geometry data from the first surface intersection. This node is computationally expensive and can slow renders significantly; consider baking results for speed improvement.

**Cycles:** Treats all geometry as opaque; transparency doesn't discard hits.

**EEVEE:** Subject to standard Screen-Space Effects limitations.

### Inputs

- **Position** — Ray starting point. Defaults to surface position when unconnected.
- **Direction** — Ray direction. Defaults to surface normal when unconnected.
- **Length** — Maximum ray distance before "no hit" conclusion.

### Properties

**Only Local** — Report only hits on the object itself, not other scene objects.

### Outputs

- **Is Hit** — 1 if hit detected, 0 otherwise.
- **Self Hit** — 1 if hit was on the object itself, 0 otherwise.
- **Hit Distance** — Ray distance to impact. Returns ray Length if no hit found.
- **Hit Position** — Impact location. Returns zero vector if no hit found.
- **Hit Normal** — Geometry normal of hit surface. Returns zero vector if no hit found.

## Sample Index Node

The Sample Index node retrieves values from a source geometry at a specific index.
Tip: when the input Geometry is the same as the geometry from the field context, this node is equivalent to the Evaluate at Index Node, which is usually preferable — avoiding the geometry socket makes the whole setup easier to reuse and share in other situations.
Tip: the Point domain is shared across components (Mesh, Point Cloud, Curve); this node simply samples the Value from the first non-empty component, checked in the order Mesh, Point Cloud, Curve. Use the Separate Components Node to sample directly from a specific component.

Inputs:
Geometry — the geometry to retrieve the attribute from.
Value — a field to evaluate on the source Geometry; the values are then retrieved from specific indices for the output.
Index — which index to use when retrieving data from the input Value field; any index can be connected, resulting in a "shuffling" of the values.

Properties:
Data Type — the data type to use for the retrieved values.
Domain — the attribute domain the attribute is transferred from — in other words, the domain used to evaluate the input; for example, it is possible to transfer data from the faces of one geometry to the points of another.
Clamp — clamp the indices to the size of the attribute domain instead of outputting a default value for invalid indices.

Outputs:
Value — the data retrieved from the source Geometry input.

Examples: here the node copies the positions of one object to another, recreating the behavior of the Transfer Attribute node from Blender versions before 3.4; it works best when the geometries have the same number of points and the same Topology.

## Sample Nearest Node

### Sample Nearest Node

Locates the index of the closest geometry element to a given position.

Differs from Geometry Proximity Node: outputs index rather than distance/location.

**Inputs**
- Geometry: Source (point cloud or mesh only).
- Sample Position: Query point.

**Properties**
- Domain: Search scope.

**Outputs**
- Index: Closest element.

Tip: Pair with Sample Index Node to retrieve nearest attribute value (pre-3.4 Transfer Attribute equivalent).

## Box Selection Node

### Box Selection Node

Marks geometry falling within a defined 3D box region.

**Inputs**
- Center: Box center.
- Size: Box extent per axis.

**Outputs**
- Selection: Boolean (true inside/intersecting, false outside).

## Normal Selection Node

### Normal Selection Node

Marks geometry whose surface normals align with a reference direction within an angular tolerance.

**Inputs**
- Direction: Reference vector (ideally normalized).
- Threshold: Max angle for inclusion.

**Outputs**
- Selection: Boolean for aligned elements.

Use case: Select upward faces, walls, or surfaces oriented toward a light/camera.

## Sphere Selection Node

### Sphere Selection Node

Marks geometry inside or touching a spherical region.

**Inputs**
- Center: Sphere center.
- Radius: Sphere size.

**Outputs**
- Selection: Boolean (true inside/on surface, false outside).

Useful for localized effects, falloff regions, or targeted modifications.

## Set Geometry Name Node

### Set Geometry Name Node

Assigns a custom name label to geometry, overriding names from Object Info Node or Grease Pencil to Curves Node. Name appears in Spreadsheet for debugging.

**Inputs**
- Geometry: Standard input.
- Name: New label.

**Outputs**
- Geometry: Standard output.

## Set ID Node

### Set ID Node

Fills the id attribute (creating if absent, default zero). Used by Distribute Points on Faces and referenced by Random Value Node and others.

Read via ID Node.

**Inputs**
- Geometry: Standard input.
- Selection: Boolean (true = modify).
- ID: Value per element (default = index, useful for stable IDs across variable counts).

**Outputs**
- Geometry: Standard output.

## Set Position Node

### Set Position Node

Controls point location, same as position attribute control. For instances, affects origin position.

Read via Position Node.

**Inputs**
- Geometry: Standard input.
- Selection: Boolean (true = move).
- Position: New coordinates (default = current, no-op).
- Offset: Optional per-point translation (evaluated without reflecting Position change).

**Outputs**
- Geometry: Standard output.

## Set Selection Node

### Set Selection Node

Controls which geometry elements are marked as selected.

Read via Selection Node.

Constraint: Tool context only.

**Inputs**
- Geometry: Standard input.
- Selection: Boolean (false = deselect).

**Properties**
- Domain: Domain to mark.

**Outputs**
- Geometry: Standard output.

## Grease Pencil to Curves Node

### Grease Pencil to Curves Node

Converts each Grease Pencil layer into a curve-containing instance.

**Inputs**
- Grease Pencil: Standard input.
- Selection: Boolean marking layers to convert.
- Instances as Layers: If true, create separate curve instances per layer (equivalent to subsequent Realize Instances); off by default for better performance.

**Outputs**
- Curves: Curve geometry.
