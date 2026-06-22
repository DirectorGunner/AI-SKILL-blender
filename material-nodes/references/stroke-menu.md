# Stroke Menu, Editing Tools, Trace Image To Grease Pencil, Hue Saturation Modifier ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Stroke Menu; Editing Tools; Trace Image to Grease Pencil; Hue/Saturation Modifier; Offset Modifier; Array Modifier; Dot Dash Modifier; Envelope Modifier.

## Stroke Menu

**Subdivide.**

Menu ‣ Stroke ‣ Subdivide. Inserts new control points into selected curve segments via progressive subdivision, enabling smoother transitions, greater detail control, or animation setup.

Number of Cuts — number of divisions for each segment; each cut adds one new control point.

Selected Points — when enabled, limits the effect to selected points within the stroke.

**Subdivide and Smooth.**

Menu ‣ Stroke ‣ Subdivide and Smooth. Subdivides and smooths strokes by inserting points between selected ones.

Number of Cuts — number of subdivisions.

Selected Points — when enabled, limits to selected points within the stroke.

Iterations — procedure repeats.

Factor — smoothness amount on subdivided points.

Smooth Endpoints — smooths stroke endpoints.

Keep Shape — preserves stroke shape.

Position — affects point location.

Radius — affects point thickness.

Opacity — affects point strength (alpha).

**Simplify.**

Menu ‣ Stroke ‣ Simplify. Reduces stroke complexity by strategically removing points; useful for cleaning up strokes, optimizing performance, and preparing for further editing or animation.

Fixed — Menu ‣ Stroke ‣ Simplify – Fixed. Deletes alternated points except start and end.

Steps — procedure repeats.

Adaptive — Menu ‣ Stroke ‣ Simplify – Adaptive. Uses the Ramer-Douglas-Peucker algorithm to remove points while maintaining similar line shape.

Factor — controls recursion depth for simplification.

Sample — Menu ‣ Stroke ‣ Simplify – Sample. Recreates stroke geometry with a predefined distance between points.

Length — distance between points on the recreated stroke; smaller values need more points, larger values fewer.

Merge — Menu ‣ Stroke ‣ Simplify – Merge. Simplifies by merging points closer than a specified distance.

Distance — maximum distance between vertices for merging.

**Outline.**

Menu ‣ Grease Pencil ‣ Outline. Converts selected strokes into closed perimeter shapes, creating new strokes around the stroke boundary with adjustable thickness.

View — projection method:
- View: current viewport perspective.
- Front: X-Z axes (front view).
- Side: Y-Z axes (side view).
- Top: X-Y axes (top view).
- Camera: active camera perspective.

Radius — sets how far the outline extends on either side; larger numbers create thicker boundaries.

Offset Factor — shifts the outline in or out:
- Positive values expand the boundary away.
- Negative values contract it toward the center.
- 0 positions it directly atop the original stroke.

Corner Subdivisions — subdivisions for smoothing corners; higher values create smoother corners but increase complexity.

**Trim.**

Menu ‣ Stroke ‣ Trim. Trims selected stroke to first loop or intersection.

**Join.**

Join — Menu ‣ Stroke ‣ Join ‣ Join; shortcut Ctrl+J. Connects two or more strokes into a single one.

Type:
- Join: connects strokes by connecting points.
- Join and Copy: connects strokes by connecting points in a new stroke.

Leave Gaps — when enabled, does not use geometry to connect strokes.

Join and Copy — Menu ‣ Stroke ‣ Join ‣ Join and Copy; shortcut Shift+Ctrl+J. Identical to Join except the method automatically becomes Join and Copy.

**Move to Layer.**

Menu ‣ Stroke ‣ Move to Layer; shortcut M. Opens a menu to reassign the stroke to a different layer from existing ones or define a fresh layer.

**Assign Material.**

Menu ‣ Stroke ‣ Assign Material. Reassigns the material for the selected stroke, picking from the current Grease Pencil object's material library.

**Set as Active Material.**

Menu ‣ Stroke ‣ Set as Active Material. Makes the active object material match the material of the selected stroke.

**Arrange.**

Menu ‣ Stroke ‣ Arrange. Changes the drawing order of strokes in the 2D layer.

Bring to Front — moves selected points or strokes to the top.

Bring Forward — moves selected points or strokes up one position.

Send Backward — moves selected points or strokes down one position in the drawing order.

Send to Back — moves selected points or strokes to the bottom.

**Close.**

Menu ‣ Stroke ‣ Close; shortcut F. Closes or opens strokes by connecting the last and first point.

Type:
- Close All: closes all open selected strokes.
- Open All: opens all closed selected strokes.
- Toggle: closes or opens as required.

Match Point Density — adds points in the new segment to maintain the same density.

**Toggle Cyclic.**

Menu ‣ Stroke ‣ Toggle Cyclic. Toggles between an open and closed stroke (cyclic).

Type:
- Close All: closes all open selected strokes.
- Open All: opens all closed selected strokes.
- Toggle: closes or opens as required.

Match Point Density — adds points in the new segment to maintain the same density.

**Set Caps.**

Menu ‣ Stroke ‣ Set Caps. Toggles stroke ending cap styles.

Rounded — sets start and end points to rounded (default).

Flat — toggles start and end point caps between flat or rounded.

Toggle Start — toggles the start point cap.

Toggle End — toggles the end point cap.

**Switch Direction.**

Menu ‣ Stroke ‣ Switch Direction. Reverses the direction of selected Grease Pencil strokes, making the starting point the endpoint and vice versa. While this does not change the visual appearance, it affects behaviors relying on point order, such as the Build Modifier.

**Set Start Point.**

Menu ‣ Stroke ‣ Set Start Point. Sets the start point for cyclic strokes, determining where the stroke begins and ends when it loops.

**Set Uniform Thickness.**

Menu ‣ Stroke ‣ Set Uniform Thickness. Makes thickness equal across the entire stroke.

Thickness — thickness value for all stroke points.

**Set Uniform Opacity.**

Menu ‣ Stroke ‣ Set Uniform Opacity. Makes opacity equal across the entire stroke.

Opacity — opacity value for all stroke points.

**Scale Thickness.**

Menu ‣ Stroke ‣ Scale Thickness. When enabled, scales stroke thickness during scale transformations.

**Set Curve Type.**

Menu ‣ Stroke ‣ Set Curve Type; shortcut V. Sets the spline type for stroke splines in the selection.

Type — target spline type; see Spline Types for details:
- Bézier: converts the spline to Bézier type. Poly splines convert with vector handles; NURBS or Catmull Rom with automatic handles.
  Note: converting a NURBS spline to Bézier requires at least six points; if the count is not a multiple of three, the spline truncates.
- NURBS: converts to NURBS type.
- Poly: converts to poly type.
- Catmull Rom: converts to Catmull Rom type.

Handles — includes handle information during conversion.

**Set Resolution.**

Menu ‣ Stroke ‣ Set Resolution. Controls the number of points interpolated along each curve segment (between two handles).

**Set Stroke Type.**

Menu ‣ Stroke ‣ Set Stroke Type. Converts selected curves to a different component type.

Type:
- Stroke: retains outlines only; removes any fill.
- Fill: keeps fill areas only; discards the outline.
- Both: activates both outline and fill simultaneously.

**Reset UVs.**

Menu ‣ Stroke ‣ Reset UVs. Resets the UV transformation of selected curves to default values, removing any scaling, rotation, or offset adjustments applied to material coordinates.

**Join Fills.**

Menu ‣ Stroke ‣ Join Fills; shortcut Shift+J. Combines multiple selected fill regions into one; helpful for unifying separate bounded areas.

**Separate Fills.**

Menu ‣ Stroke ‣ Separate Fills; shortcut Alt+P. Divides a unified fill region back into separate fills per boundary curve, enabling independent editing of formerly merged areas.

Individual — creates a separate fill for each individual stroke.

## Editing Tools

Toolbar options for Grease Pencil editing:

Select — select or move geometry.

Select Box — drag a box to select.

Select Circle — paint on geometry to select.

Select Lasso — draw a lasso to select.

Cursor — change the 3D Cursor position.

Move — translation tool.

Rotate — rotation tool.

Scale — scale tool.

Scale Cage — scale by controlling a cage.

Transform — adjust translation, rotation, and scale.

Pen — create and modify Bézier strokes.

Radius (Alt+S) — expand or contract the thickness radius of selected points.

Bend (Shift+W) — curve selected points from the 3D cursor toward the pointer.

Shear (Shift+Ctrl+Alt+S) — skew selected points horizontally or along the vertical axis.

To Sphere (Shift+Alt+S) — push selected points radially away from the stroke's center.

Interpolate (Ctrl+E) — automatically insert a breakdown keyframe between adjacent normal keyframes.

Gradient — sketch a line to establish a color gradient across the fill of selected strokes.

Annotate — sketch loose annotations by hand.

Annotate Line — sketch straight-line annotations.

Annotate Polygon — sketch multi-sided annotations.

Annotate Eraser — remove previous drawn annotations.

## Trace Image to Grease Pencil

The Trace Image to Grease Pencil tool vectorizes a black-and-white image into Grease Pencil strokes. Non-monochrome images undergo internal conversion (hand conversion typically yields superior results). Opt for lower image resolutions; high resolutions yield excessively dense stroke geometry.

**Usage.**

Place an Image Empty in the scene. Execute Trace Image to Grease Pencil.

**Options.**

Target Object — whether the image empty persists or gets replaced:
- New Object: creates a new Grease Pencil object while preserving the image empty.
- Selected Object: substitutes the image empty with the Grease Pencil object.

Radius — width of the generated strokes.

Color Threshold — luminance cutoff; strokes form above this value.

Turn Policy — resolves ambiguities arising during the image-to-path conversion:
- Black: favors linking black (foreground) areas.
- White: favors linking white (background) areas.
- Left: always turns leftward at intersections.
- Right: always turns rightward at intersections.
- Minority: favors the rarest color locally.
- Majority: favors the most common color locally.
- Random: selects pseudo-randomly.

Mode — specifies whether input is a single image or a sequence:
- Single: the image empty represents one still or one frame from a sequence.
- Sequence: the image empty is a full image sequence.

Start at Current Frame — when active, the trace process starts from the current frame index.

Trace Frame — targets a specific image sequence frame; use zero for all frames.

## Hue/Saturation Modifier

The Hue/Saturation Modifier remaps color output across the object.

**Options.**

Mode — the color remapping affects stroke and/or fill output:
- Stroke & Fill, Stroke, Fill.

Hue — rotates the hue channel; 360° maps to the 0–1 range. Offsets of 0 (-180°) and 1 (+180°) yield identical results.

Saturation — 0 desaturates to monochrome. Values above 1.0 boost chroma intensity.

Value — overall scene luminance; raising/lowering brightens/darkens the image.

**Influence.**

See Influence Filters.

## Offset Modifier

The Offset Modifier repositions, rotates, or rescales strokes measured from the object's local center.

**Options.**

**General.**

Location X, Y, Z — stroke displacement relative to origin.

Rotation X, Y, Z — stroke angular orientation.

Scale X, Y, Z — stroke magnitude scaling.

**Advanced.**

Mode:
- Random: injects random offsets to individual strokes.
- Layer: bases offsets on layer indices.
- Stroke: bases offsets on stroke enumeration.
- Material: bases offsets on material assignment.

Offset X, Y, Z — per-element positional delta.

Rotation X, Y, Z — per-element angular rotation.

Scale X, Y, Z — per-element magnitude change.

Uniform Scale (Random mode) — shares one random Seed across all scale axes, producing isotropic scaling.

Seed (Random mode) — initializer for the pseudo-random sequence.

Layer/Stroke/Material Step (Layer, Stroke, Material mode) — how many contiguous elements to batch and offset.

Offset (Layer, Stroke, Material mode) — shifts the enumeration baseline.

**Influence.**

See Influence Filters.

## Array Modifier

The Array Modifier generates copies of the base object, with each copy offset differently in multiple possible ways. It generates complex repetitive patterns useful for intricate drawings. Multiple Array modifiers may operate simultaneously on a single object to construct elaborate structures.

Note: This documentation covers Array Modifier specific to Grease Pencil. For other object types, consult the general Array Modifier guide.

Count: Total number of copied instances. Material Override: Material index for duplicated strokes (0 applies original materials).

Relative Offset: Factor X, Y, Z translates each copy by the object's bounding box extent times the specified scaling factors for each axis.

Constant Offset: Factor X, Y, Z applies fixed translation components per copy; specify separate values for each axis.

Object Offset: Distance X, Y, Z derives transformation from another object relative to the current one; using an empty object centered near or at the source object is recommended.

Randomize: Offset X, Y, Z introduces random translation to copies. Rotation X, Y, Z adds random rotation. Scale X, Y, Z applies random scaling. Uniform Scale: Uses identical random Seed across scale axes for uniform scaling. Seed: Pseudo-random generator value.

Note: Depth Order in Grease Pencil objects influences stroke visibility when using Array; see Depth Order for details.

Influence: See Influence Filters.

The Array modifier creates multiple copies of an input geometry and arranges them in a linear, circular, or custom pattern, with flexible options for count, spacing, and randomization for both precise and organic duplication of geometry.

Options:
Shape — the method used to arrange the duplicates.
- Line: arrange copies along a straight line.
- Circle: arrange copies around a circle.
- Curve: arrange copies along a curve input.
- Transform: position each copy by a transform offset or object transform.
Offset Method (Line) — how copies are spaced along a line.
- Relative: offset each copy relative to the geometry's bounding-box size.
- Offset: offset copies by a fixed world-space distance.
- Endpoint: distribute copies evenly between start and end points.
Offset (Line, Relative) — how far to move each copy relative to its bounding-box size in Relative mode.
Count Method (Circle, Curve) — how the number of duplicates is defined.
- Count: a fixed number of copies.
- Distance: copies based on the distance between them.
Count (Circle, Curve, Count) — the number of copies to generate.
Angular Distance (Circle, Distance) — the angular distance between copies in Circle shape.
Central Axis (Circle) — the axis used as the up direction for circular arrangements.
Circle Segment (Circle) — whether the copies form a full circle or just a partial arc.
- Full: copies evenly spaced around a full 360° circle.
- Arc: copies fan out along a circular arc.
Radius (Circle) — the radius of the circle the copies are distributed along.
Sweep Angle (Circle, Arc) — the total angle (in radians or degrees) the arc spans when Circle Segment is set to Arc.
Per Curve (Curve) — set the number of copies for each curve separately.
Curve Object (Curve) — the reference curve object for the array.
Transform Reference (Transform) — how the transform is applied in Transform shape.
- Input: use the transform given directly in the node inputs.
- Object: use a specified object's transform as the reference.
Translation Inputs (Line, Offset, Endpoint) — the positional offset applied to each copy.
Rotation Inputs (Line) — the rotation offset applied per copy.
Scale Inputs (Line) — the scale factor applied per copy.
Transform Object (Transform, Object) — the object whose transform is used when Transform Reference is set to Object.
Relative Space (Transform, Object) — whether the transform is applied in object or world space.
Realize Instances — convert the generated instances into real geometry; required for certain operations such as merging or boolean operations.

Align Rotation (Circle, Curve):
Forward Axis — the axis defining each instance's facing direction along the circle.
Up Axis — the axis used as the vertical reference for instance orientation.

Randomize:
Offset — maximum random translation offset for each axis, setting the variation in instance position.
Rotation — maximum random rotation for each axis.
Scale Axes — how scaling randomization is applied: Uniform (a single random scale factor on all axes) or Axes (independent random scale factors per axis).
Scale — maximum random scaling factor applied to each instance.
Flipping — randomly mirror instances along one or more axes.
Exclude First / Last — exclude the first (original) or last copy from randomization effects.
Seed — initialize the random number generator; changing it produces a different random arrangement while preserving other settings.

Merge — merge overlapping points or vertices by distance; requires Realize Instances to be enabled.
Distance — the distance threshold within which points are merged.

## Dot Dash Modifier

The Dot Dash Modifier generates dotted-dashed segments from strokes. Offset: Initializes the pattern start position. Segment: Individual stroke within the pattern; use plus/minus to add/remove segments. Dash: Consecutive source points in this segment. Gap: Points skipped after segment. Radius: Scaling factor for new point radius. Opacity: Scaling factor for new point opacity. Material Index: Index for generated segments (−1 uses existing). Use Cyclic: Closes the segment.

Influence Filters: See Influence Filters.

## Envelope Modifier

The Envelope Modifier creates an envelope shape along existing strokes, connecting points with n-point spacing between them.

Mode: Deform replaces the stroke with the envelope. Segments adds boundary lines while keeping the original. Fill adds lines but removes the original.

Spread Length: Point count to skip when creating the envelope's straight-line segments. Thickness: Generated segment thickness. Strength: Generated segment opacity. Material Index: Material for segments. Skip Segments: Generated segments to omit, reducing detail.

Influence Filters: See Influence Filters.
