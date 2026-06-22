# Curve Circle Node, Curve Line Node, Spiral Node, Quadratic B Zier Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Curve Circle Node; Curve Line Node; Spiral Node; Quadratic Bézier Node; Quadrilateral Node; Star Node; Curve Handle Positions Node; Curve Length Node; Curve Tangent Node; Curve Tilt Node; Endpoint Selection Node; Handle Type Selection Node; Is Spline Cyclic Node; Spline Length Node; Spline Parameter Node; Spline Resolution Node; Sample Curve Node; Curve of Point Node.

## Curve Circle Node

The Curve Circle node generates a poly spline circle.

Resolution: Edge count.
Radius: Circle radius.
Point 1, Point 2, Point 3: Three circle points. Order determines direction (clockwise/counterclockwise).

Note: Finite resolution means the three points may not lie exactly on the generated curve.

Mode:

Points: Position and radius from three points; center is output. No geometry if points are collinear.
Radius: Circle determined by radius alone.

Curve: Poly spline from inputs.
Center: Circle center (Points mode only).

## Curve Line Node

The Curve Line node generates a poly spline line.

Start: First point position.
End: Second point position (Points mode only).
Direction: Line direction. Length is irrelevant. (Direction mode only).
Length: Line extent. (Direction mode only).

Mode:

Points: Start and end points define the line.
Direction: Start, direction, and length define the line.

Curve: Standard output.

## Spiral Node

Spiral Node

Creates a poly spline following a helical path. Useful for modeling springs, coils, and other twisted forms. By default, the helix twists in a clockwise orientation.

Inputs:
Resolution — Number of points per complete rotation.
Rotations — Count of full rotations in the spiral.
Start Radius, End Radius — Radii at the spiral's beginning and end. Changes linearly across the entire length.
Height — Vertical extent of the helix.
Reverse — Boolean to flip the twist direction from clockwise to counterclockwise.

Outputs:
Curve — The generated poly spline.

## Quadratic Bézier Node

Quadratic Bézier Node

Generates a parabolic poly spline from three control vertices.

Inputs:
Resolution — Number of segments composing the curve.
Start, Middle, End — Three control vectors. The curve begins and concludes at the start and end points, remaining tangent to the lines connecting the middle point to both endpoints.

Outputs:
Curve — The poly spline output.

## Quadrilateral Node

Quadrilateral Node

Generates a four-vertex polygon with multiple configurations.

Inputs:
Width / Bottom Width / Top Width — Horizontal span.
Height — Vertical span.
Bottom Height / Top Height — In Kite mode, vertical distance from center axis to lower or upper vertex.
Offset — In Parallelogram mode, relative horizontal shift between top and bottom edges. In Trapezoid mode, shifts the top edge along the X axis.
Point 1 - 4 — Position vectors for Points mode.

Properties:
Mode
Rectangle — Rectangular outline with specified width and height.
Parallelogram — Rectangle where top and bottom edges differ in horizontal position.
Trapezoid — Four-sided shape with independent widths for top and bottom.
Kite — Symmetric diamond shape defined by width and vertical offsets.
Points — Custom quadrilateral from four directly-supplied vectors.

Outputs:
Curve — The resulting poly spline.

## Star Node

Star Node

Generates a star-shaped poly spline by alternating vertices on two concentric circles.

Inputs:
Points — Vertex count on each circle.
Inner Radius, Outer Radius — Distances of the two circles from center. Inner can exceed outer.
Twist — Rotational offset angle. Rotates inner vertices counterclockwise, positioning them between outer vertices.

Outputs:
Curve — The poly spline.
Outer Points — Boolean field marking every second vertex (those on the outer circle).

## Curve Handle Positions Node

Curve Handle Positions Node

Retrieves both handle positions of each Bézier control point. Use the Set Handle Positions Node to modify them.

Inputs:
Relative — Output positions relative to their control point, rather than in local geometry space.

Outputs:
Left — Left handle position.
Right — Right handle position.

## Curve Length Node

Curve Length Node

Sums the lengths of all splines in the curve.

Inputs:
Curve — Standard geometry input.

Outputs:
Length — Total accumulated length.

## Curve Tangent Node

Curve Tangent Node

Returns the unit-length direction vector at each control point, aligned with curve flow. The Reverse Curve Node governs direction.

Warning: For NURBS and Bézier splines, output corresponds to control points, not evaluated points. A Bézier curve may have 48 evaluated points but only 4 control points (resolution 12). NURBS discrepancies are often larger. Use Resample Curve Node to create a poly spline with aligned densities.

Inputs: None

Outputs:
Tangent — Direction vector per control point.

## Curve Tilt Node

Curve Tilt Node

Outputs the rotation angle around the curve's tangent axis at each control point. Values mirror those editable in curve Edit Mode and are interpolated to evaluated points in Bézier and NURBS splines.

Related: Set Curve Tilt node provides input control.

Inputs: None

Outputs:
Tilt — Rotation in radians.

## Endpoint Selection Node

Endpoint Selection Node

Provides a boolean selection marking the first and last N control points of each spline.

Note: Selection operates on control points; for NURBS and Bézier splines, a single control point may map to many viewport-displayed points.

Tip: Use Capture Attribute Node to preserve this selection after converting to mesh or point cloud.

Inputs:
Start Size — Count of points selected from the beginning.
End Size — Count of points selected from the end.

Outputs:
Selection — Boolean field for start and end regions.

Examples:
Generate first/last point selection for any curve. The shown poly spline in Edit Mode serves as input to Instance on Points Node.

## Handle Type Selection Node

Handle Type Selection Node

Generates a boolean selection based on Bézier handle classifications.

Related: Set Handle Type Node adjusts these values.

Inputs: None

Properties:
Mode — Include left, right, or both handles. When both are active, output is true if either handle matches.
Left — Select left handles.
Right — Select right handles.

Handle Type — Classification to match. Consult Bézier curves documentation for type specifics.

Outputs:
Selection — Boolean field where true indicates handle type match.

## Is Spline Cyclic Node

Is Spline Cyclic Node

Reads whether each spline's start and end points connect, reflecting the built-in cyclic attribute.

Related: Set Spline Cyclic Node applies changes.

Inputs: None

Outputs:
Cyclic — Boolean indicating loop closure per spline.

## Spline Length Node

Spline Length Node

Outputs the total distance per spline, either as a continuous measure or point count. Distinct from Curve Length Node, which accumulates across all splines.

Output operates at spline domain but can be interpolated to control points.

Inputs: None

Outputs:
Length — Per-spline distance.
Point Count — Control vertices per spline.

## Spline Parameter Node

Spline Parameter Node

Reports position along each spline via two metrics: distance traveled and normalized progress.

The Factor is not simply index-over-total because vertices may be unevenly distributed along the curve. The initial value is zero, covering distance to the current point rather than beyond it.

At spline domain, outputs the accumulated curve progress at the start of each spline. Spline order is visible in Spreadsheet Editor.

Warning: For NURBS and Bézier splines, values correspond to control points only. NURBS discrepancies are often pronounced. Resample Curve Node creates uniform point density.

Special case: When length is zero, Factor defaults to index-over-total.

Inputs: None

Outputs:
Factor — At point domain: fraction of spline length. At spline domain: fraction of total curve length.
Length — At point domain: distance along the spline. At spline domain: distance along entire curve.
Index — Zero-indexed position within the current spline, separate from the global Index node.

Examples:
Use parameter to drive radial variation along a curve. Start has radius 0, end has radius 1.

## Spline Resolution Node

Spline Resolution Node

Outputs the count of evaluated vertices per control point for NURBS, Bézier, and Catmull Rom splines.

For poly splines, control and evaluated vertices are one-to-one; resolution has no effect. Bézier segments between vector handles similarly have no extra resolution.

Related: Set Spline Resolution Node provides input control.

Inputs: None

Outputs:
Resolution — Integer resolution per spline.

## Sample Curve Node

Sample Curve Node

Evaluates a point at a specific distance or progress fraction along the curve, interpolating custom attribute values from surrounding evaluated vertices.

When the curve contains multiple splines, the sample location references total accumulated length across all splines in Spreadsheet Editor order.

Inputs:
Curves — Geometry input with curve data.
Value — Custom attribute field to evaluate and output.
Factor — Normalized progress (0–1) mode.
Length — Distance units mode.
Curve Index — Isolate specific splines. Ignored when All Curves is enabled.

Properties:
Data Type — Output attribute type.

Mode — Endpoint location method, paralleling Trim Curve Node behavior.
Factor — Normalize within each spline (0–1).
Length — Distance from spline start.

All Curves — Use total curve length instead of per-spline length.

Outputs:
Value — Sampled attribute value.
Position — Curve location.
Tangent — Unit direction vector.

Tip: Combine with Align Rotation to Vector Node to match curve direction. Layer a second rotation node with Normal to align a second axis.

Normal — Unit surface perpendicular.

Examples:
Recreates Resample Curve Node's Count mode, but outputs a mesh instead. Z component of position can serve as sample factor (0–1 range across the line).

## Curve of Point Node

Curve of Point Node

Retrieves which curve contains a given control point's index.

Conceptually parallel to Face of Corner Node.

Inputs:
Point Index — Control vertex index. By default uses field context, requiring point-domain evaluation.

Outputs:
Curve Index — Owning curve identifier.
Index in Curve — Zero-indexed position within that curve.

## Offset Point in Curve Node

Offset Point in Curve Node

Fetches neighboring control points by stepping relative to an input point along its curve.

Conceptually similar to Offset Corner in Face Node, but point indices do not wrap around unless the curve is cyclic.

Inputs:
Point Index — Input control point. By default uses field context, requiring point-domain evaluation.
Offset — Step count. In cyclic curves, wrapping occurs past boundaries.

Outputs:
Is Valid Offset — Whether the resulting index exists in the original curve. Always true for cyclic curves.
Point Index — Resulting control point index.

## Points of Curve Node

Points of Curve Node

Extracts specific control point indices from a curve using sorting criteria.

Inputs:
Curve Index — Target curve. By default uses field context, requiring curve-domain evaluation.
Weights — Sorting values. Default: by index (lowest first).
Sort Index — Which sorted point to retrieve. Wraps past the maximum.

Outputs:
Point Index — Selected control point index.
Total — Control point count in the curve.

## Set Curve Normal Node

Set Curve Normal Node

Configures the normal calculation strategy for each curve. Normals are computed later as needed; the tilt attribute at each control point provides additional rotation around the tangent.

Internally modifies the normal_mode attribute per curve.

Inputs:
Curve — Standard geometry input.
Selection — Toggle whether to apply changes to each curve.
Mode — Calculation approach:
Minimum Twist — Minimizes tangent-axis rotation across the entire curve.
Z-Up — Perpendiculars to both the Z axis and tangent. Uses X for vertical curves.
Free — Employs a custom_normal attribute as the final normals. Provides an additional Normal input for setting values.

Note: Custom normals are not rotation-invariant; apply after rotations (end of tree or bottom of modifier stack).

Outputs:
Curve — Standard geometry output.

## Set Curve Radius Node

Set Curve Radius Node

Governs the curve radius, used by operations such as Curve to Mesh for profile sizing. Set per control point and interpolated between evaluated vertices.

Related: Radius node reads this attribute.

Inputs:
Curve — Standard geometry input.
Selection — Boolean mask determining which control points receive new values.
Radius — Per-point radius.

Outputs:
Geometry — Standard geometry output.

## Set Curve Tilt Node

Set Curve Tilt Node

Adjusts the tilt angle rotating the normal vector at each control point during evaluation. Retrieved by Normal Node.

The rotation mechanism: Axis Angle around the tangent, equivalent to Vector Rotate Node applied to the untransformed normal using tangent as axis and tilt as angle.

Related: Curve Tilt node reads this attribute.

Inputs:
Curve — Standard geometry input.
Selection — Boolean mask for which control points change.
Tilt — Per-point rotation angle.

Outputs:
Curve — Standard geometry output.

## Set Handle Positions Node

Set Handle Positions Node

Modifies Bézier handle locations to reshape the curve. Consult Bézier curves documentation for details.

Note: Auto and Vector handle types convert to Aligned and Free respectively when positions change.

Note: Left and right handles cannot be modified simultaneously due to alignment constraints.

Inputs:
Curve — Standard geometry input.
Selection — Boolean mask for modifying handles.
Position — Target handle location (global, not relative to control point).
Offset — Optional per-handle translation, evaluated alongside Position without reflecting Position changes.

Properties:
Left / Right — Which handle(s) to adjust. Left is nearer the start.

Outputs:
Curve — Standard geometry output.

Examples:
Align handles to control point position but offset downward in Z. Use Set Spline Type Node to enforce poly spline in Edit Mode for user convenience.

## Set Handle Type Node

Set Handle Type Node

Changes Bézier handle classifications for selected points.

Related: Handle Type Selection Node retrieves these values.

Inputs:
Curve — Bézier curve.
Selection — Points whose handles change.

Properties:
Mode — Affect left, right, or both. When both selected, both update.
Left — Left handle only.
Right — Right handle only.

Handle Type — Target classification. See Bézier curves documentation for details.

Outputs:
Curve — Standard geometry output.

## Set Spline Cyclic Node

Set Spline Cyclic Node

Toggles whether each spline loops back on itself (connects first and last control points).

Related: Is Spline Cyclic Node reads this property.

Inputs:
Curve — Standard geometry input.
Selection — Boolean mask for which splines change. True applies, false preserves existing state.
Cyclic — Loop closure per spline.

Outputs:
Curve — Standard geometry output.

## Set Spline Resolution Node

Set Spline Resolution Node

Configures the evaluated-point count per control point for NURBS, Bézier, and Catmull Rom splines. No effect on poly splines or Bézier segments between vector handles.

Evaluated points appear in the viewport, feed Curve to Mesh Node, and optionally supply Resample Curve Node. Higher settings improve operations like trimming and sampling but reduce speed.

Related: Spline Resolution node reads this attribute.

Inputs:
Curve — Standard geometry input.
Selection — Boolean mask for which splines change.
Resolution — Evaluated points per control point. Higher values increase accuracy at computational cost.

Outputs:
Curve — Standard geometry output.

## Set Spline Type Node

Set Spline Type Node

Converts splines to a target classification.

Inputs:
Curve — Standard geometry input with curve data.
Selection — Splines to convert.

Properties:
Spline Type — Target type. Consult Spline Types documentation.

Bézier — From poly: vector handles. From NURBS/Catmull Rom: auto handles. Requires ≥6 points for NURBS conversion; truncation occurs if point count is not a multiple of three.

NURBS — Target classification.
Poly — Target classification.
Catmull Rom — Target classification.

Outputs:
Curve — Standard geometry output.

## Fields

At heart, a field is a function — a set of instructions that turns any number of inputs into a single output, whose result can then be computed many times with different input data. Fields appear all over geometry nodes to enable calculations that yield different results for every element (mesh vertices, faces, etc.). For example, a field connected to the Set Position node might depend on two inputs, Position and Index, transforming them into a vector with a single instruction.

Field Visualization: socket shapes convey which sockets are fields and which are regular data — three possible shapes, each visualizing a socket's "field status":
- Circle: the socket requires a single value and cannot accept a field input; for output sockets, the node always outputs a single value.
- Diamond: the socket can accept a field input or output a field; a constant single value can connect, but then the output will often not vary per element.
- Diamond with Dot: the socket can be a field but is currently a single value — helpful for tracking where single values are calculated rather than a field with many different results, and it makes Socket Inspection show the value instead of field input names.
So a diamond-with-dot socket means the field has the same value for every element (e.g. every point moved up by 5 m), while a plain diamond with a varying input means the value can differ per element (e.g. the position doubled, since each point's offset is its own position). Tip: it's often desirable to extract a single value from a field; while conceptually you can't just flatten a field into a single value, the Sample Index Node or the Attribute Statistic Node can retrieve a single value from a field evaluated on a geometry. A connection between two field-supporting sockets is drawn as a dashed line; mistakenly connecting a non-field socket to a field socket draws a solid red line indicating an error.

Node Types: nodes fall into two categories — data flow nodes that usually pass geometry, and field nodes that operate on data per element. Field nodes can be input nodes that bring geometry data into the tree, or function nodes that operate on that data.
- Data Flow Nodes: nodes with a geometry input and a geometry output are almost always data flow nodes, actually changing the geometry data output from the Geometry Nodes modifier.
- Function Nodes: nodes with diamond socket inputs and outputs are field nodes, resembling the instructions evaluated by data flow nodes — for example the math nodes, and more complex ones like the Geometry Proximity Node.
- Input Nodes: these provide data to the field evaluation process; by themselves they mean nothing and must be evaluated within the context of a data flow node (geometry) to output a value — for example built-in attribute input nodes like Position and ID, and selection nodes like Endpoint Selection. Field inputs may also come from other geometry-processing nodes like Distribute Points on Faces, in the form of Anonymous Attributes.

Field Context: every field node works in the context of the data flow node it connects to — usually a geometry component type and an attribute domain — which determines what data is retrieved from input nodes. A common misunderstanding is that the same field node tree used in multiple places outputs the same data; this isn't necessarily true, because the tree is evaluated for every data flow node, potentially retrieving data from a different or changed geometry. For instance, a Set Position node's input field is evaluated once, traversing backwards to retrieve inputs from the field input nodes; adding a second Set Position node evaluates the same tree twice, and the second node's results differ because its geometry input already carries the changed position from the first node. When you instead need the same field values even after changing the geometry, the Capture Attribute Node evaluates a field and copies the result to an anonymous attribute on the geometry — so with a Capture Attribute node storing a copy of the initial position, evaluating its input field is an entirely separate step, and the later Set Position nodes use the anonymous-attribute copy rather than the actual position.

## Array Node

Array Node

Duplicates input geometry in linear, circular, or custom patterns with configurable count, spacing, and randomization.

Inputs:
Geometry — The shape to replicate.

Shape — Arrangement method:
Line — Straight-line arrangement.
Circle — Radial distribution.
Curve — Distribution along a curve input.
Transform — Position using transform offset or object transform.

Offset Method Line — Spacing strategy:
Relative — Offset by bounding box fraction.
Offset — Fixed world distance.
Endpoint — Even distribution between start and end.

Offset Line Relative — Bounding-box multiplier.

Count Method Circle Curve — Replica specification:
Count — Fixed count.
Distance — Space-based count.

Count Circle Curve Count — Replica quantity.

Angular Distance Circle Distance — Radial spacing angle.

Central Axis Circle — Upward reference direction for circular arrangement.

Circle Segment Circle — Arc or full 360°:
Full — Complete circle, even spacing.
Arc — Partial arc.

Radius Circle — Circle radius.

Sweep Angle Circle Arc — Total arc span (radians or degrees).

Per Curve Curve — Per-curve replica count.

Curve Object Curve — Input curve reference.

Transform Reference Transform — Application method:
Input — Direct node inputs.
Object — Object transform.

Translation Inputs Line Offset Endpoint — Per-copy displacement.

Rotation Inputs Line — Per-copy rotation.

Scale Inputs Line — Per-copy scaling.

Transform Object Transform Object — Reference object for Transform mode.

Relative Space Transform Object — Object or world space application.

Realize Instances — Converts instances to real geometry (required for merging, booleans).

Align Rotation Circle Curve:
Forward Axis — Instance facing direction.
Up Axis — Vertical reference.

Randomize:
Offset — Maximum translation variance per axis.
Rotation — Maximum rotation variance per axis.
Scale Axes — Uniform or per-axis scaling:
Uniform — Single random factor.
Axes — Independent factors per axis.
Scale — Maximum scaling factor.
Flipping — Random mirroring per axis.
Exclude First / Last — Skip randomization for original or final copy.
Seed — Random number initialization. Different seeds yield different patterns with identical other settings.

Merge (requires Realize Instances):
Distance — Merge threshold for overlapping vertices.

Outputs:
Geometry — Combined duplicated and transformed instances.

## Curve to Tube Node

Curve to Tube Node

Generates a mesh tube following an input curve with cylind­rical or custom-profiled cross-section. Useful for cables, pipes, wires, and tubing models.

Inputs:
Curve — Input spline.
Scale — Radius multiplier on the curve's radius attribute.

Profile:
Profile Mode — Shape definition:
Round — Circular cross-section.
Custom — Custom object or geometry profile.
Resolution Round — Circle resolution (also cap resolution).
Profile Input Custom — Profile source:
Object — Single object.
Geometry — Input geometry.
Object / Geometry Custom — Profile specification.
Shade Smooth — Enable smooth shading.

Resample — Curve preprocessing for uniform geometry distribution:
Resample Mode — Method:
Evaluated — Existing evaluated points.
Auto — Automatic sample length.
Count — Fixed sample count.
Length — Fixed distance between samples.
Scale Auto — Auto-mode length multiplier.
Count Count — Sample point count.
Length Length — Sample spacing.

Caps — End-fill strategy:
Caps Type — Approach:
Flat — Single n-gon per end.
Round — Semicircle per end.
Custom — User-provided geometry.
Smooth Flat Round — Smooth tube-to-cap transition.
Caps Input Custom — Cap source:
Object — Single object.
Geometry — Input geometry.
Start / End Custom — Per-end cap objects or geometry.

UV Map:
Name — Map name.
Parameter U/V — UV generation:
Factor — 0–1 normalization along curve and profile.
Length — Real length and circumference.
Index — Point indices.
Consider Curve Radius — Account for radius variation.

Outputs:
Mesh — Tube output including optional caps and UVs.
