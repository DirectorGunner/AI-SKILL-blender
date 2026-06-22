# Geometry, Curve Primitives, Empties, Attribute Statistic Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Geometry; Curve Primitives; Empties; Attribute Statistic Node; Blur Attribute Node; Capture Attribute Node; Domain Size Node; Remove Named Attribute Node; Store Named Attribute Node; Baking; Curve Nodes; Curve to Mesh Node; Curve to Points Node; Curves to Grease Pencil Node; Deform Curves on Surface Node; Fill Curve Node; Fillet Curve Node; Interpolate Curves Node.

## Geometry

The Geometry panel converts a curve from a 1D line into 2D ribbon or 3D tube geometry.

Geometry panel. 

Three copies of the same base curve: one without geometry (bright orange line);
one with Offset and Extrude applied (blue ribbon); and one with Offset, Extrude,
and Bevel applied (gray tube). 

Offset
Move control points along their normals.

Extrude
Convert the curve from a line into a ribbon by pushing it to the "sides":
at each point, the curve normal becomes the "up" direction,
and the curve extends to the "left" and "right."

Hint

Adjust the direction and distance of Offset and Extrude per point
by changing its Tilt (tangent-axis rotation) and
Radius (scale factor).

Taper Object
A separate Curve object, consisting of a single, non-cyclic,
2D spline, controlling the scale along the length of each curve spline.

Note

The "taper" name is misleading: it means "to reduce toward the end,"
while the Taper Object can scale anywhere. A better name might be "Scale Curve."

Picture the Taper Object as a profile graph: how far along the curve you sit is read off the X axis, while the scale factor applied there is read off the Y axis:

- Its opening spline point maps onto the geometry's opening spline point, and the closing ones line up the same way.

- Arrange them so the earliest taper point carries the largest X value and the final one the smallest
(if the scaling looks inverted, apply Switch Direction).
The absolute X span is irrelevant—[-10, 10], [-1, 1], or anything else behaves identically.

- Where Y sits at 1.0 the geometry stays as-is; 0.5 shrinks it by half,
whereas 2.0 enlarges it twofold.

Any Z component on these points goes unused; flip the object's Shape to "2D" if you wish.

Taper Radius
Combine the Taper Object scale graph with control point radii.

Note

This isn't limited to tapering and doesn't define a single radius.
A better name might be "Scale Curve Mode."

Override :

The Taper Object (scale curve) replaces the radii (scales) of the curve's control points.

Multiply :

The Taper Object scale is multiplied by control point scales.

Add :

The Taper Object scale is added to control point scales.

| Override mode.  | Multiply mode.  | Add mode.  |

Map Taper
When geometry covers only part of the curve (set via
Factor Start/End), enabling Map Taper aligns
Taper Object endpoints with geometry endpoints instead of curve endpoints.

Bevel:

Apply a Bevel to turn the 1D line (or 2D ribbon with Extrude)
into a 3D tube.

Round:

The tube's cross section is circular (or pill-shaped with Extrude).
Half circles are possible via Fill Mode.

Depth
Cross-section size.

| Small Depth.  | Large Depth.  |

Resolution
Count of cross-section vertices.

| Low Resolution creates blocky mesh.  | High Resolution creates smooth mesh.  |

Fill Caps
Seal tube ends.

Object:

Fully customize cross-section shape using a separate Curve object.

Object
The curve defining the cross section. May be closed (cyclic)
or open.

Important

This curve must lie flat in its local XY plane; other planes produce unexpected results.

Note

If the selected curve has modifiers, they don't apply.
The bevel uses the original curve shape. This is because curves become meshes
when they have modifiers; at that point they can't serve as cross section curves.

Workaround: disable beveling on the path curve, then add geometry nodes:
use an Object Info Node to fetch the cross section curve,
convert it from mesh back to curve via a Mesh to Curve Node,
and finally send both to a Curve to Mesh Node.

Profile:

Customize cross-section shape without a separate Curve object. Unlike the Object option where the curve fully defines the cross section,
the Profile in the Curve Widget defines a quarter which repeats and mirrors.

Black dots show sample points (where mesh vertices form). Increase Resolution for more samples and smoothness.

Preset
Choose predefined profiles instead of building your own.
Support Loops and Steps presets generate based on Resolution
and need reapplication if you change it.

Reverse Path
Mirror the profile along the diagonal.

Toggle Profile Clipping
Restrict control point X and Y coordinates to [0, 1].

Sample Straight Edges
Sample the profile at the middle of perfectly straight segments
(lines between Vector-handle points).
Disabled by default, as sampling at control points usually suffices.

Sample Even Lengths
By default, each profile segment gets the same sample point count.
Enable to distribute sample points evenly
across the entire profile length.

Factor Start, End
Percentages along the curve length where geometry begins
and finishes. Default: 0 and 1 (full length);
change to 0.5 and 0.75 to cover just the third quarter.

| Curve with Factor Start at 0 and End at 1.  | Factor End changed to 0.6.  |

Mapping Start, End
How Factor Start, End percentages map to curve positions.

Resolution :

Count control points only, ignoring spline segment lengths. A three-point spline with Factor Start at 0.5 always starts at the second point,
regardless of its distances to the first and third points.

Segments :

Approximate the percentage along spline length by assuming
all subdivisions in each segment space evenly.

Spline :

Calculate a precise percentage along spline length.

Examples:

Open 2D Curve:

An open (non-cyclic) curve with beveling becomes a tube.

Closed 2D Curve:

A closed (cyclic) curve with beveling becomes a torus by default.
Set Fill Mode to Both for a 2D curve
to fill top and bottom holes with flat discs, making a rounded-edge cylinder.

This doesn't work with 3D curves.

Taper:

Pick a 2D curve as the Taper Object of another (2D or 3D) curve
to vary geometry radius without adding points.

Tilt:

Use the Tilt tool to spin a control point around
its tangent axis, twisting the curve. The example also uses
a custom profile (cross section).

## Curve Primitives

Hair curves and geometry nodes provide additional options:

Empty Hair:

Creates an empty high-performance curves object and automatically:

- Sets the active object as the Surface.

- Makes the surface object the parent.

- Adds a Geometry Nodes modifier to deform curves on the surface.

Fur:

Apply fur setup to chosen objects.
The setup uses Geometry Nodes with
Hair Node Groups bundled with Blender.

See Quick Fur for more information.

## Empties

An empty is a position marker in space with no geometry. It renders invisibly but serves as a control anchor.

Empty Display Types.

Plain Axes: Six lines extending along each axis (±X, ±Y, ±Z).
Arrows: Three labeled arrows along the positive X, Y, Z axes.
Single Arrow: One arrow pointing along +Z.
Circle: A circle initially in the XZ plane.
Cube: A cube aligned to the coordinate axes.
Sphere: Three circles (one per axis) forming an implied sphere.
Cone: A cone initially pointing along +Y.
Image: Empties can hold images. Use this for reference artwork, blueprints, or figure sheets for modeling.
The image displays regardless of rendering mode.

Access Empty display options via Properties ‣ Object Data ‣ Empty panel.

Offset X, Y: Move the image anchor (1.0 = image width/height).

X=0.5, Y=0.5: Anchor at image center.
X=0.0, Y=0.0: Anchor at bottom-left.
X=1.0, Y=1.0: Anchor at top-right.

Depth:

Default: Standard depth behavior.
Front: Always appear in front.
Back: Always appear behind.

Tip: For a reference image, set Depth to Front and lower Opacity.

Side:

Both: Show front and back.
Front: Show only the front.
Back: Show only the back.

Tip: When using reference photos from both sides, set each empty to display only from the matching viewpoint.

Show in:

Orthographic: Visible in orthographic projection.
Perspective: Visible in perspective projection.

Hint: Disabling this prevents reference images from obstructing your model.

Only Axis Aligned: Display only when the view aligns with the object's local axes.

Opacity: Blend strength between image and background (0–1).

An empty can only be edited in Object Mode, covering transformation and parenting. Other tools appear in the Object section.

Apply Scale Ctrl+A

Empties lack traditional object data, so "apply scale" works differently. Instead, the Display Size property controls the visual size (before scaling). The scale on the most-stretched axis combines with Display Size to maintain correct proportions on that axis.

Display As: Which empty primitive to show in the viewport.
Size: Scales the visual size of the empty (offset, not transform).

Empties serve as deformation handles. Common uses:

Parent object for a group: An empty can parent other objects, allowing centralized control without render impact.

Target for constraints: Use an empty as a constraint anchor. For example, a camera can track a point via a Track To constraint.

Array offset: An empty can drive an Array Modifier, enabling complex transformations through single-object movement.

An example of an empty controlling an array. ‣ An example of an empty driving a Track To constraint. ‣

Other applications:
- Placeholders for missing objects
- Rigging anchors
- Depth-of-field markers
- Reference images

## Attribute Statistic Node

The Attribute Statistic node evaluates a field across a geometry and outputs aggregate metrics.

Geometry: Standard input.
Selection: Boolean field indicating which elements to include. False values exclude the corresponding attribute from calculations.
Attribute: The field to analyze.

Data Type:

Float: Single floating-point result.
Vector: Three floating-point values, computed per-component.

Domain: The attribute category on which statistics are calculated.

Mean: The arithmetic average.
Median: The midpoint value.
Sum: The total.
Min: The smallest value.
Max: The largest value.
Range: The difference between max and min.
Standard Deviation: Spread from the mean. Low values cluster tightly; high values scatter widely.
Variance: The square of standard deviation.

## Blur Attribute Node

The Blur Attribute node softens attribute values by mixing them with neighboring geometry parts.

Each step blends a component's value with those of its neighbors, weighted by a factor applied to the neighbors before accumulation.

Blurring functions only on Meshes and Curves with domains having explicit neighbor definitions (vertices, edges, faces of meshes; curve control points). Face corner attributes are not supported, as ideal blending behavior is undefined. All data types work except boolean.

Value: Each element's starting attribute value.
Iterations: How many times to repeat mixing. Each iteration uses previous results independently.
Weight: Multiplier for each element.

Data Type: The data representation used.

Value: The mixed values after blurring.

Input: A subdivided plane with random color. The second Subdivide adds density. Blur Attribute mixes all colors for each face, smoothing the result.

## Capture Attribute Node

This node preserves one or more fields across a geometry, making them available to downstream nodes.

This differs from Store Named Attribute in that capture generates anonymous attributes (no name needed, no name-collision risk), making it ideal for temporary values.

The new attribute only exists in the geometry this node outputs, not in upstream or sibling branches.

Geometry: Standard input.
Capture Items: The fields to keep. Connect new outputs or use the Properties panel list. Rename by Ctrl+LMB clicking in the node or double-clicking in the list.

Domain: Which attribute category to store the data on.

Capture Items List

Reference

Menu: Sidebar ‣ Node ‣ Properties ‣ Capture Items

A list for adding, removing, reordering, and renaming inputs.

Data Type: The data kind of the active input.

Geometry: Standard output.
Attribute: One output per captured field.

Common scenario: Convert a Curve to a Mesh while preserving curve-specific information. The Spline Parameter node works only on curves, not meshes. Capture Attribute solves this by storing the parameter on each control point before conversion. The Curve to Mesh node then propagates these values to mesh vertices. Later, you reconnect to the same Capture Attribute node to retrieve them.

## Domain Size Node

The Domain Size node reports the count of elements in a given geometry domain (e.g., number of edges, number of points).

For domain concepts, refer to the geometry attributes page.

Geometry: Standard input.

Component: Which geometry class to query.

Point Count: How many points exist.
Edge Count: How many edges (meshes only).
Face Count: How many faces (meshes only).
Face Corner Count: How many face corners (meshes only).
Spline Count: How many splines (curves only).
Instance Count: How many root-level instances. Nested instances are not counted.

## Remove Named Attribute Node

The Remove Named Attribute node strips a named attribute from geometry.

All geometry-based attributes propagate automatically when the geometry updates, which can be expensive. This node optimizes by removing unneeded attributes, improving node-tree performance and scene memory.

Most named attributes can be deleted. For some Built-In Attributes, removal causes Blender to use a default. For instance, removing cyclic on curves makes all curves non-cyclic.

Geometry: Standard input.

Pattern Mode: Selection method.

Exact: Delete only the named attribute.
Wildcard: Delete all attributes matching the pattern (single * allowed).

Name: The attribute to delete.

Geometry: Standard output.

## Store Named Attribute Node

The Store Named Attribute node writes a field result onto geometry with a specified name. If the attribute exists, its type and domain update. Built-In Attributes cannot change type or domain.

Compared to Capture Attribute, this stores under a name instead of anonymously. For local reuse, Capture Attribute avoids name collisions.

If geometry contains multiple component types, the attribute is placed on each component supporting the chosen domain.

Geometry: Standard input.

Selection: Boolean field determining which elements receive the stored value. Unselected parts fill with zeros if the attribute is new, otherwise remain unchanged.

Value: The field to store.

Name: The attribute's identifier.

Data Type: The stored data kind.
Domain: The attribute category.

Geometry: Standard output.

## Baking

Baking preserves intermediate geometries for later retrieval.

The internal data format is not an exchange format. OpenVDB is used for volumes (interchangeable across tools).

Two baking methods exist:

- Bake Node – any node-tree section.
- Simulation Zone Baking – animations where one geometry state feeds the next.

Disk writing happens only when Bake is executed.

Important:

- Save the blend file before baking.
- Data format between Blender versions is not guaranteed compatible.

The Bake Geometry node bakes all simulations and bake nodes in chosen objects' modifiers.

Tip: Once baked, frame count displays above zone or node.

Reference

Editor: Geometry Node Editor
Panel: Sidebar ‣ Node ‣ Data-Block References

List baked geometries that reference other data (materials, for example).

This panel lets you update those references post-baking.

Note: Currently only materials are supported.

## Curve Nodes

Nodes working exclusively on curves.

Note: If prior modifiers exist, the curve appears internally as a mesh, and Curve Nodes fail. Convert with Mesh to Curve Node first.

## Curve to Mesh Node

The Curve to Mesh node transforms all splines into mesh geometry. Optionally, a profile curve shapes the output.

Attributes transfer to the result, including built-ins like sharp_face, positioned on the appropriate domain.

Tip: Output mesh edges are marked sharp based on the profile curve. If any profile Bézier splines use Free or Vector handles, matching output edges are shaded sharp.

Curve: Standard input (non-curve components ignored).
Profile Curve: If supplied, extruded along all splines; otherwise a chain of edges results.
Scale: Per-control-point profile scaling.
Fill Caps: For cyclic profiles, seal the ends with n-gons. The mesh is Manifold; new faces connect to existing edges.

Mesh: Standard output.

## Curve to Points Node

The Curve to Points node generates a point cloud from a curve.

Curve: Standard input.
Count: Points to generate (Count mode only).
Length: Segment length (Length mode only).

Mode:

Evaluated: Points from the curve's pre-computed evaluation, using the resolution attribute for NURBS/Bézier. Usually fastest, no extra sampling.
Count: Distribute the specified count evenly across each spline.
Length: Split each spline into segments of specified length. The length rounds down to fit an integer count. Trim Curve Node with a multiple prevents jumping if spline length changes.

Points: Generated point cloud.
Tangent: The curve tangent at sampled position (or direct evaluated normal in Evaluated mode).
Normal: The normal from the evaluated curve at each point, matching Normal Node output at those locations.
Rotation: Euler rotation built from Tangent and Normal, for convenience.

## Curves to Grease Pencil Node

Transform top-level instances of curves into Grease Pencil layers using this node.

Curves: Plain curves or curve instances.
Selection: Curve or instance selection.
Instances as Layers: One layer per instance. Layer names derive from instance geometry. Plain curves yield a single layer named after the input.

Grease Pencil: Standard output.

This example demonstrates converting a curve to a Grease Pencil layer. 

The Set Curve Radius node controls stroke width.

## Deform Curves on Surface Node

The Deform Curves on Surface node shifts and rotates each curve based on its root position change. The root is stored as UV coordinates on the curve and the selected UV Map in the Curves surface settings.

Transformation is calculated from the difference between the original (undeformed) and final (modified) mesh.

This node has implicit inputs beyond the standard one:

- Original and evaluated mesh are pulled from the modifier's surface property, so this works only on curves objects.
- Original and evaluated UV maps come from the object's surface property.
- The rest_position attribute (3D vector) computes rotation tangents matching the original mesh.
- The surface_uv_coordinate attribute (2D vector, curve domain) stores root locations on the surface UV map.

Future updates will make this more flexible.

Parts parallel the Sample UV Surface Node logic.

Warning: After Subdivision Surface, set UV Smooth to None to keep UV attachment points stable.

Curves: Standard input.

Curves: Standard output.

## Fill Curve Node

The Fill Curve node creates a mesh from curves via constrained Delaunay triangulation. Output lies flat on local Z = 0.

Curve: Standard input (curve component).
Group ID: Grouping value. Different IDs treat curves separately.
Mode: Output geometry type (Triangles or N-gons).

Mesh: Filled output.

Single-point splines customize the triangulation.

Default Fill Curve applied to a star. 

Star with one point added for triangulation. 

Star with 300 points for dense triangulation. 

Group ID examples:

Four curves, one Group ID → one mesh island. 

Four curves, different Group IDs → four islands. 

Four curves split into two groups by position → two islands.

## Fillet Curve Node

The Fillet Curve node smooths corners on curve points, similar to bevel on 2D mesh. The rounded sections are always circular arcs.

Curve: Standard input (curve component).
Radius: Circle arc radius per fillet.
Count: For Poly mode, control point count per fillet.
Limit Radius: Cap the radius to prevent overlapping fillets.
Mode: How to add vertices.

Bézier: Two control points per fillet. The aligned handles form the circular shape; segments depend on the spline's resolution.
Poly: Direct control of fillet vertices via an integer field input. Better for poly and NURBS.

Curve: Standard output.

A 3D poly spline with rounded corners. 

Fillet combined with curve primitives.

## Interpolate Curves Node

The Interpolate Curves node generates new curves across positions by interpolating between existing ones. Useful for reducing edit effort (fewer guides, faster workflow) while maintaining high density for viewing and rendering.

Guide Curves: Base curves to interpolate.
Guide Up: Optional surface normal. Supplying it improves interpolation quality, grounding it to surface shape.

Tip: In typical child-hair setups, retrieve this normal via Sample UV Surface Node on the same surface plus Normal Node.

Guide Group ID: Splits guides into groups; new curves stay within one group. Prevents curves in different sections (different IDs) from influencing each other.

Points: First root positions of new curves.
Points Up: Optional surface normal.
Point Group ID: The group to interpolate within.
Max Neighbors: Closest guides to consider.

Curves: The guides plus interpolated curves.
Closest Index: Index of the nearest guide for each new curve.

Note: Internally, multiple guides are mixed; this output is only the dominant one.

Closest Weight: Strength of the nearest guide.

## Resample Curve Node

The Resample Curve node converts each input spline to a poly spline. In Count and Length modes, new points are evenly spaced.

Tip: Use a field to vary count/length per spline.

Curve: Standard input.
Selection: Whether to resample each spline (True = resample, False = unchanged).

Mode:

Count: Distribute the specified count evenly.
Length: Split into segments of specified length, rounded down to fit an integer count. Trim Curve Node with a multiple keeps distance exact if spline length changes.
Evaluated: Use the resolution attribute for NURBS/Bézier. Poly unchanged.

Count Count: Points on each new spline.
Length Length: Spacing between points.

Tip: Combine with Trim Curve Node using a length multiple for exact spacing despite spline length variance.

Curve: Standard output.

## Reverse Curve Node

The Reverse Curve node flips the direction of each spline. Shape stays the same.

Tip: When feeding the Profile input of Curve to Mesh Node, this flips the result mesh normals.

Curve: Standard input.
Selection: Whether to reverse each spline (True = reversed, False = unchanged).

Curve: Standard output.

## Subdivide Curve Node

The Subdivide Curve node inserts control points between existing ones. For Bézier and poly, shape is unaltered.

Bézier curves gain finer control while keeping the visual level that Bézier provides. Unlike Resample Curve Node, which converts to poly.

Curve: Standard input.
Cuts: Control points to insert on the segment after each point. As a field, the count at each segment is set by the field value at the previous point.

Curve: Standard output.

## Trim Curve Node

The Trim Curve node shortens splines by removing sections from start and end.

Bézier splines stay Bézier; the first, last, and their handles adjust to preserve shape. NURBS convert to poly.

Warning: Cyclic splines are not supported.

Note: Since normals compute from the final curve, this node may shift normals under Minimum twist method, as it considers the whole curve. Capture Attribute Node can preserve pre-trim normals.

Curve: Standard input (curve component).
Selection: Boolean field indicating which curves to trim.
Start: Where the trimmed spline begins (factor or length).

Note: If Start > End, the result is a single point at Start.

End: Where the trimmed spline ends (factor or length).

Mode:

Factor: Use 0–1 fraction of spline length.
Length: Use distance from spline start (0 to spline length).

Curve: Standard output.

## Arc Node

The Arc node builds a poly spline arc. Two modes: Radius and Points.

Resolution: Edge count on the arc.
Radius: Arc radius (Radius mode).
Start Angle: Arc beginning angle (Radius mode).
Sweep Angle: Arc length (Radius mode).
Connect Center: Link the arc's center point.
Invert Arc: Draw the opposite arc.
Start, Middle, End: Three arc points (Points mode). Order sets direction (clockwise/counterclockwise). Start-to-End is always via Middle; use Invert Arc to flip.
Offset Angle: Arc angle offset (Points mode).

Note: Finite resolution means the middle point may not lie exactly on the arc.

Mode:

Points: Arc determined by three points; center, radius, and normal are output.
Radius: Arc determined by radius, start angle, and sweep angle.

Curve: Poly spline from inputs.
Center: Arc center (Points mode only).
Normal: Plane normal pointing toward +Z (Points mode only).
Radius: Arc radius (Points mode only).

## Bézier Segment Node

The Bézier Segment node builds a 2D Bézier spline from control and handle points.

Resolution: Edge count.
Start, End: Control point positions.
Start Handle, End Handle: Handle positions.

Mode:

Position: Absolute 3D handle positions.
Offset: Positions relative to control points.

Curve: Bézier spline from inputs.
