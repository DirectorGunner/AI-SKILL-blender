# Editing Vertex Paint Colors, Shrinkwrap Modifier, Vertex Weight Angle Modifier, Vertex Weight Proximity Modifier ...

> Blender Add-ons, Panels, and Properties reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Editing Vertex Paint Colors; Shrinkwrap Modifier; Vertex Weight Angle Modifier; Vertex Weight Proximity Modifier; Curve Widget; List View; Curve Display; Control Points; Transform Panel; Active Spline.

## Editing Vertex Paint Colors

**Set Color Attribute.**

Menu ‣ Paint ‣ Set Color Attribute. Establishes the active color on all picked vertices.

**Reset Vertex Color.**

Menu ‣ Paint ‣ Reset Vertex Color. Wipes the Color Attribute from active strokes; if none are chosen, clears all.

**Invert.**

Menu ‣ Paint ‣ Invert. Flips RGB channel values.

**Levels.**

Menu ‣ Paint ‣ Levels. Tweaks the tonal range of Color Attributes.

**Hue/Saturation/Value.**

Menu ‣ Paint ‣ Hue/Saturation/Value. Modulates the color's HSV components.

**Brightness/Contrast.**

Menu ‣ Paint ‣ Brightness/Contrast. Shifts color luminance and contrast range.

**Sample Color.**

Menu ‣ Paint ‣ Sample Color; shortcut Shift+X. Extracts a color from the viewport and binds it to the active Paint brush. When triggered from the menu, drag the cursor across colors to capture their blend, enabling swift color synchronization with drawn details.

Press Shift+X to grab the color at cursor position; it becomes the primary Paint brush hue.

### Editing Vertex Paint Colors

### Smooth Vertex Colors

Reference

Mode :

Vertex Paint Mode

Menu :

Paint ‣ Smooth Vertex Colors

Harmonizes colors throughout the vertex structure.

### Dirty Vertex Colors

Reference

Mode :

Vertex Paint Mode

Menu :

Paint ‣ Dirty Vertex Colors

Create a cavity-based dirt gradient map.

Blur Strength
Softening amount per pass.

Blur Iterations
Recurrence count for softening (higher = more blur).

Highlight Angle
Restricts angle for protruding geometry. Lower values sharpen distinctions but may cause clipping. 90 = flat, 180 = infinitely pointed.

Dirt Angle
Restricts angle for recessed geometry. Higher values sharpen distinctions but may cause clipping. 90 = flat, 0 = infinitely concave.

Dirt Only
Skips clean area computation when enabled.

Normalize
Optimizes contrast by automatically lessening Highlight Angle and raising Dirt Angle. Disabling maintains consistency across distinct meshes.

### Vertex Color from Weight

Reference

Mode :

Vertex Paint Mode

Menu :

Paint ‣ Vertex Color from Weight

Transforms the active weighting map into grayscale pigmentation.

### Invert

Reference

Mode :

Vertex Paint Mode

Menu :

Paint ‣ Invert

Reverses RGB values.

### Levels

Reference

Mode :

Vertex Paint Mode

Menu :

Paint ‣ Levels

Modifies the tonal range of the chosen vertices.

### Hue/Saturation/Value

Reference

Mode :

Vertex Paint Mode

Menu :

Paint ‣ Hue/Saturation/Value

Modifies the HSV spectrum of the chosen vertices.

### Brightness/Contrast

Reference

Mode :

Vertex Paint Mode

Menu :

Paint ‣ Brightness/Contrast

Modifies the luminance and tonal separation of the chosen vertices.

### Set Vertex Colors

Reference

Mode :

Vertex Paint Mode

Menu :

Paint ‣ Set Vertex Colors

Shortcut :

Ctrl - X

Replaces the active Color Attribute with the current paint pigmentation.

Affect Alpha
Apply complete opacity instead of maintaining existing transparency.

### Sample Color

Reference

Mode :

Vertex Paint Mode

Menu :

Paint ‣ Sample Color

Shortcut :

Shift - X , Shift - Ctrl - X

Gathers color from the viewport and sets it as the active Paint brush pigmentation.

When starting from the menu (rather than keyboard), click and drag across varied colors to collect their mean value.

This permits fast alignment of brush color with painting already visible on the mesh.

- Use Shift - X to extract color at the cursor position.

- Use Shift - Ctrl - X to extract the rendered viewport color, including material properties, illumination, and every visible element.

The gathered color becomes the primary Paint brush pigmentation.

## Shrinkwrap Modifier

The Shrinkwrap modifier compresses a Grease Pencil object onto another object's surface by repositioning each point toward the nearest surface location.

See also: Shrinkwrap Constraint and general Shrinkwrap Modifier documentation.

**Options.**

Wrap Method — establishes how the nearest surface point is located for each modified point; some approaches unlock extra settings.

Snap Mode — most approaches permit governance over point motion toward the target. Behavioral variants if Offset ≠ zero:
- On Surface: points always shift; offset travels the projection axis backward.
- Inside: stationary if inside target; offset constricts the allowed region inboard.
- Outside: stationary if outside target; offset pushes the exclusion boundary outward.
- Outside Surface: like On Surface, but offset points outward exclusively.
- Above Surface: like On Surface, but offset follows the target's interpolated normals.

Note: Inside and Outside mimic crude collision via target normal geometry, unreliable near 90° and sharper curvature.

Target — surface destination; the mesh to tighten around.

Offset — gap preserved from the computed target position.

Smooth Factor — intensity of post-wrap smoothing.

Repeat — how often to re-smooth.

**Influence.**

See Influence Filters.

**Wrap Methods.**

Nearest Surface Point — latches onto the nearest spot on the target surface.

Project — shoots points along a user-picked axis until collision; unconnected points sit static.

Limit — threshold for distance between source point and surface; exceeding this prevents projection.

Subdivision Levels — temporarily applies Catmull-Clark subdivision to the object's data prior to wrapping.

Axis — local direction along which projection fires; options layer to form a "composite direction." If blank, face normals guide projection.

Negative/Positive — specifies allowed shrink trajectories along the axis; both enabled tests either way and takes the closer result.

Face Cull — barricades projection across target face "obverse" or "reverse" (determined by face normal).

Invert Cull — when Face Cull is on and Negative is allowed, swaps the Front/Back cull for Negative direction, handy for bilateral projection.

Auxiliary Target — secondary geometry to project against.

Nearest Vertex — jumps to the nearest vertex on the target; contributes no added controls and bypasses Snap Mode.

Target Normal Project — matches Nearest Surface Point's behavior but yields superior blending in exchange for slower performance. Rather than hunting the closest point, seeks the nearest point whose blended normal vector targets/targets-away from the source. Boundary edges in non-closed topology become infinitely-thin cylinder emitters; flat shading does not apply.

The Shrinkwrap modifier draws an object toward another object's surface, relocating each vertex to the nearest point on the target geometry using one of four methods.

It works on meshes, lattices, curves, surfaces, and text.

Wrap Method selects how the nearest surface point is found. Some methods add additional controls.

Snap Mode (available for most methods) determines how the vertex moves to the selected target point. Options differ mainly when Offset is nonzero:

On Surface moves the vertex; offset applies along the line joining original and target positions, toward the original.

Outside Surface matches On Surface but offset goes toward the outside.

Above Surface matches On Surface but offset follows the target's smooth normal.

Inside prevents movement if the vertex already lies within the target. Offset shrinks the allowed interior volume along the projection line.

Outside prevents movement if the vertex is already outside. Offset expands the exterior exclusion zone along the projection line.

Note: Inside and Outside enable crude collision detection, though determining inside vs. outside based on target normals is unreliable near 90-degree and acute angles.

Target specifies the shrink target mesh.

Offset sets how far from the computed target position the vertex stops.

Vertex Group controls displacement per-vertex. Group members displace; others do not (equivalent to weight 0).

Nearest Surface Point selects the closest point anywhere on the target surface.

Project mode shoots vertices along a chosen axis until they contact the target. Vertices missing contact stay in place.

Limit restricts the maximum distance between original and projected position. Exceeding it prevents projection.

Subdivision Levels applies temporary Catmull-Clark subdivision to the modified geometry before wrapping.

Axis selects the projection direction (local). Combinations create median projection axes. If none selected, vertex normal direction is used.

Negative/Positive enables one or both axis directions. Both enabled evaluates both and selects the nearest hit.

Face Cull prevents projection over specified face directions (front or back, determined by normal direction).

Invert Cull, when Face Cull is active and Negative direction is allowed, inverts the Front/Back choice for the Negative direction—useful for two-direction projection.

Auxiliary Target adds a secondary target object for projection.

Nearest Vertex snaps vertices to the closest target vertex. It adds no extra options and does not support Snap Mode.

Target Normal Project, slower but smoother than Nearest Surface Point, seeks the nearest point whose interpolated smooth normal faces or away from the original vertex. Boundary edges are treated as infinitely thin cylinders emitting normals perpendicularly; flat shading is ignored.

## Vertex Weight Angle Modifier

The Vertex Weight Angle Modifier assigns weights to vertex groups based on angle. This tool computes weights according to a chosen angle threshold.

Warning: This modifier caps weight values to 0.0–1.0 range; all values below 0.0 become 0.0, and all above 1.0 become 1.0.

Vertex Group: Target vertex group to modify. Invert: Inverts the group's weight influence, reversing group weight values. Angle: The angle threshold for maximum weights. Axis: The axis (X, Y, Z) along which angle influences weights. Space: Coordinate system for calculations. Minimum: Lowest weight value permitted. Multiply Weights: Multiplies computed weights by existing group values.

Influence: See Influence Filters.

## Vertex Weight Proximity Modifier

The Vertex Weight Proximity Modifier sets weights in a vertex group according to distances between the object (or specific vertices) and another target object (or its surfaces).

Warning: This modifier enforces weight clamping to 0.0–1.0 range; all values fall outside are clipped to the boundary.

Note: This documentation covers Vertex Weight Proximity for Grease Pencil objects. See the general Vertex Weight Proximity Modifier for other object types.

Vertex Group: Target group to affect. Invert: Reverses the weight influence of the vertex group. Target Object: Source object from which distances are measured. Lowest: Distance at which weight becomes 0.0. Highest: Distance at which weight becomes 1.0. Minimum: Threshold weight value. Multiply Weights: Multiplies computed weights with existing values.

Influence: See Influence Filters.

## Curve Widget

### Curve Widget

Curve widget.

This widget edits two flavors of curve:

- Profile curves, which merely lay out a 2D shape.

- Mapping curves, which take an X-axis input value over to a Y-axis output value.

Which flavor you're editing shifts the options a little. One extra rule for mapping curves: they cannot overhang, since every X value has to land on exactly one Y value — profile curves carry no such restriction.

### Control Points
As with every curve in Blender, control points are what define the curve shown in this widget.

Add
LMB-click any stretch of the curve that hasn't got a control point yet.

Move
Drag the point with LMB.

Remove
Pick the point, then click the button down at the bottom right — or just press X.

### Controls
Zoom In
Magnifies for finer detail and tighter control. While zoomed, pan around the curve by clicking and dragging with LMB over an empty spot.

Zoom Out
Pulls back for less detail and a whole-curve view. The clipping region is the limit — you can't zoom past it (see Clipping below).

Reverse Path Profile Curves
Mirror the curve around the diagonal.

Clipping Options Mapping Curves

Use Clipping
Pins curve points within the values you give.

Min X/Y and Max X/Y
Fix the lower and upper bounds the curve points may reach.

Specials

Reset View
Zooms the view fully out.

Extend Options Mapping Curves
Governs how the curve carries on past its first point and beyond its last.

Extend Horizontal
Makes the curve "go flat."

Extend Extrapolated
Keeps the curve heading in its current direction.

| Extend Horizontal. | Extend Extrapolated. |

Reset Curve
Returns the curve to default, clearing every point you added.

Handle Type
The selected control point's handle type, which governs the shape the curve takes through that point.

Auto Handle
Yields a smooth curve with no manual handle setup needed.

Vector Handle
Yields straight lines meeting at a sharp corner.

Free Handle Profile Curves
Exposes Bézier handles you can move freely and apart from one another, which may leave a sharp corner at the point.

Aligned Free Handles Profile Curves
Exposes freely movable Bézier handles tied to face in opposite directions, keeping the curve smooth through the point.

Auto Clamped Handle Mapping Curves
Like Auto Handle, but with overshoot held in check too.

| Vector Handles. | Auto Handles. | Auto Clamped Handles. |

X, Y
The coordinates of the selected control point.

Delete X
Drops the selected control point. The endpoints — first and last — stay put.

Copy/Paste Ctrl - C , Ctrl - V
Hover over a Curve Widget and press Ctrl - C , Ctrl - V to carry the entire curve across to another.

Presets Brush Curve Widgets Only
A set of preset curves you can snap the curve to. What shape each yields turns on whether the property's default curve slopes up or down.

| Smooth | Round | Root |
| Sharp | Linear | Constant |

| Smooth | Round | Root |
| Sharp | Linear | Constant |

## List View

### List View

List view with expanded Filtering Options panel.

Managing lists of items is what this control handles. Besides the main list, a Filtering panel hides at the bottom (off by default) and modification buttons sit on the right.

Select
Pick an item with a LMB click on it.

Rename
Double-click an item to edit its name in a text field. Ctrl - LMB does the same.

Resize
The list view can grow or shrink to show more or fewer items. Park the mouse over the handle (::::), then drag to expand or contract the list.

Filter
The Show filtering options button (triangle on bottom left) reveals or conceals the filter option panel when clicked.

Search Ctrl - F
Narrows the list down to entries carrying a given term.

Invert
Flips between keeping entries that hold the search term and keeping those that lack it.

Sort by Name
Flips ordering between alphabetical and not.

Reverse
Orders objects ascending or descending — and where alphabetical sorting is on, that direction applies to it as well.

Over on the right of the list view sit the list modification buttons:

(Add)
Drops in a new item.

(Remove)
Takes out the selected item.

(Specials)
A menu of operators for editing list entries.

/ Move
Shifts the selected item one slot up or down.

## Curve Display

Curves display control in Edit Mode via special overlays in the 3D Viewport.

Reference

Mode :

Edit Mode

Panel :

3D Viewport ‣ Header ‣ Curve Edit Mode Overlays

Handles
Control Bézier curve handle visibility during editing.

None :

No handles shown, giving a clear curve view.

Selected :

Show handles only for chosen control points.

All :

Show handles for every control point in the curve.

Normals
Toggle curve normal display.

Normal Size
Length of the axis pointing the normal direction.

Edit Mode overlays control curve display in the 3D Viewport.

Reference

Mode :

Edit Mode

Panel :

3D Viewport ‣ Header ‣ Curve Edit Mode Overlays

Handles
Control Bézier curve handle visibility during editing.

None :

No handles shown, giving a clear curve view.

Selected :

Show handles only for chosen points.

All :

Show handles for every point in the curve.

## Control Points

This section covers control point operations.

Extrude Curve and Move:

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Extrude Curve and Move

Shortcut :

E

Duplicate chosen points, move them, and reconnect them to form a continuous curve.

Make Segment:

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Make Segment

Shortcut :

F

Join two disconnected control points.
Pick standalone points or the endpoints of a curve, then press F .
Connecting points from different curves creates a single curve.

| Before joining.  | After joining.  |

Note: join only curves of the same type (Bézier with Bézier, NURBS with NURBS).
You can close a curve by toggling cyclic.

Tilt:

Reference

Mode :

Edit Mode

Tool :

Toolbar ‣ Tilt

Menu :

Control Points ‣ Tilt

Shortcut :

Ctrl - T

Adjust how curve normals twist around each control point (applies only to 3D curves).
Tilt is smoothed point-to-point (visible via normals).

30 degree Mean Tilt of all control points. 

Clear Tilt:

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Clear Tilt

Shortcut :

Alt - T

Restore tilt to its default orientation (perpendicular to the initial curve plane).
With NURBS, tilt automatically interpolates smoothly. Bézier lets you select the interpolation method.

Set Handle Type:

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Set Handle Type

Shortcut :

V

Handle types define Bézier curve behavior.
For instance, Vector handles produce sharp corners.
See Bézier curves for more details.

Toggle Free/Align
Switch between Free and Aligned handle types.

Recalculate Handles:

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Recalculate Handles

Shortcut :

Shift - N

Adjust selected control point handles to be tangential to the curve.
Produces smoother, more uniform curves.

Length
Make all handles the same length.

Smooth:

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Smooth

For Bézier curves, reduce the distance from selected point(s) to their neighbors,
keeping neighbors fixed. Tangents remain unchanged.

Original, unsmoothed Curve. 

Entire curve smoothed over 20 iterations using Shift - R . 

Only three center control points smoothed over 20 iterations. 

Smooth Curve Tilt:

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Smooth Curve Tilt

Interpolate Tilt values for selected control points.
Produces gradual tilt transitions and reduces abrupt changes.

Smooth Curve Radius:

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Smooth Curve Radius

Interpolate Radius values for selected control points.
Produces gradual radius transitions and reduces abrupt changes.

Smooth Curve Weight:

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Smooth Curve Weight

Interpolate Weight values for selected control points.
Produces gradual weight transitions and reduces abrupt changes.

Hooks:

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Hooks

Shortcut :

Ctrl - H

Add hooks to one or more points for manipulation via other objects.

Make Vertex Parent:

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Make Vertex Parent

Shortcut :

Ctrl - P

Parent other selected objects to one or three control points (similar to mesh objects).

To select an on-screen mesh while editing, Ctrl - P click it.
Pick one or three control points,
then Ctrl - LMB the object and use Ctrl - P to establish parent-child relationship.
Three control points make the child follow
the median point between them. An alternative uses
a Child Of constraint.
See also the Curve modifier.

Control point operations cover these tasks:

Extrude Curve and Move:

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Extrude Curve and Move

Shortcut :

E

Duplicate chosen points, move them, and reconnect to form a continuous curve.

Set Handle Type:

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Set Handle Type

Shortcut :

V

Handle types shape Bézier curves.
For instance, Vector handles make sharp corners.
See Bézier curves for more information.

Type
The handle type to switch to.

Auto :

Blender sets the length and direction entirely for the smoothest result.
These become Align when moved.

Vector :

Both handle parts aim at adjacent handles, creating straight lines or sharp corners.
Become Free when moved.

Align :

Both handle parts sit on a straight line,
creating smooth curves without sharp angles.

Free :

Each handle moves on its own.

Toggle Free/Align :

Replace Free with Align, and all Align with Free.

Tilt:

Reference

Mode :

Edit Mode

Tool :

Toolbar ‣ Tilt

Shortcut :

Ctrl - T

Adjust how curve normals rotate around each point.
The tilt is smoothed from point to point (visible via normals).

Clear Tilt:

Reference

Mode :

Edit Mode

Shortcut :

Alt - T

Set tilt back to default (perpendicular to the original curve plane).

## Transform Panel

Edit Mode Transform panel properties:

Reference

Mode :

Edit Mode

Panel :

Sidebar ‣ Transform

When nothing is selected, the panel shows nothing.
With multiple vertices selected, the median is displayed
and "Median" appears in the labels.

Control Point, Vertex
The first set of controls (X, Y, Z) shows the coordinates of the chosen point or handle.
With NURBS curves, a fourth component appears (W),
setting the weight
of the chosen control point or median weight.

Space
Radio buttons choose whether coordinates are local
(relative to object origin) or global.

Global, Local

Weight
Set the "goal weight" for chosen control points,
used when a curve has Soft Body physics,
anchoring the curve to their original positions via the weight.

Radius
Control the extrusion/bevel width along the curve path.
Radius is smoothed point-to-point (visible via normals).

Tilt
Control how curve normals twist around each control point (applies to 3D curves only).
Tilt is smoothed point-to-point (visible via normals).

### Transform Panel

Reference

Editor :

3D Viewport

Mode :

Edit Mode

Panel :

Sidebar ‣ Item ‣ Transform

Whatever control points you've selected have their properties shown in this panel.
Select several at once and it reports the averaged values,
letting you edit them for all the points together.

Control Point

X, Y, Z
Where the control point sits.

W
The control point's weight.
A larger weight tugs the surface more strongly toward that control point.

Space
Whether the coordinates read in object space (Local) or in world space (Global).

Weight
The "goal weight" that Soft Body physics draws on.
Crank this up and the surface grows "stiffer" at that control point — meaning the point
clings to its starting spot and resists deformation.

Radius
Has no effect on Surface objects.

Tilt
Has no effect on Surface objects.

## Active Spline

Edit Mode panel for spline properties:

Reference

Editor :

3D Viewport

Mode :

Edit Mode

Menu :

Sidebar ‣ Item ‣ Active Spline

Controls the currently chosen spline's properties.

Common Options

Cyclic U
Close the active spline.

| Default NURBS curve.  | A NURBS curve with Cyclic applied.  |

Resolution U
Adjust segment resolution by changing subdivision count.

Smooth
Apply Smooth Shading to any 3D geometry.

Poly:

Active Spline panel: Poly Spline. 

Cyclic U
See Common Options.

Smooth
See Common Options.

Bézier:

Active Spline panel: Bézier Spline. 

Cyclic U
See Common Options.

Resolution U
See Common Options.

Interpolation Tilt
Decide how tilt calculates for a segment.

Radius
Decide how radius calculates for a beveled curve.
Effects become clearer after increasing radius.

Smooth
See Common Options.

NURBS:

A defining feature of NURBS is the knot vector .
This sequence of numbers sets how control points influence the curve.
Direct knot vector editing is not possible,
but the Endpoint and Bézier options in the Active Spline panel shape them.
These settings apply only to open NURBS curves.

Active Spline: NURBS Spline. 

Cyclic U
See Common Options.

Bézier U
Make the NURBS curve behave like Bézier.
NURBS control points function as Free handles of Bézier curves.

Endpoint U
Make the curve pass through the end control points.

| Default NURBS curve.  | A NURBS curve with Endpoint enabled.  |

Order U
The order determines how much each control point influences the curve.
Higher order means greater influence over a wider curve section.
Valid range: 2-6, depending on available control points.

| NURBS curves with orders of 4.  | NURBS curves with orders of 2.  |

Resolution U
See Common Options.

Smooth
See Common Options.
