# Curve Structure, Draw, Curve Properties, Edge Slide ...

> Blender Add-ons, Panels, and Properties reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Curve Structure; Draw; Curve Properties; Edge Slide; Loop Cut and Slide; Offset Edge Slide; Screw.

## Curve Structure

Splines are the basic parts of curve objects, defining their shapes.
A curve object can hold multiple splines,
like how a mesh object can have multiple separate meshes.
Each spline's shape comes from its Control Points.
Splines exist in types: Poly, Bézier, and NURBS, each with its own curve-definition method,
covered in the Spline Types section.

Splines carry unique properties adjustable in Edit Mode via the
Active Spline panel.

Control Points:

Each spline is assembled out of control points that join together into its shape.
Selecting and dragging those points lets you reshape the spline—
much the same idea as nudging the vertices on a mesh.

See also

Curve Editing

Spline Types:

Poly:

Poly splines are the simplest kind, performing no interpolation from one point across to the next.
Used when converting meshes to curves
for faithful original mesh representation.
Though Poly splines are exact, Bézier or NURBS splines typically work better for smooth curves.

Bézier:

Bézier splines use points and handles to form their shape.
A segment lies between two points, with handles controlling curvature.

Below, the points sit at the pink line centers, with handles extending outward.
Arrows show curve normals, pointing direction and tilt.

Bézier Curve in Edit Mode. 

Bézier curves support four handle varieties, changed with V :

Bézier Curve Handle Types. 

Automatic :

Automatically sets handle length and direction for the smoothest curve.
Shown as yellow. Becomes Aligned when moved.

Vector :

Handles aim directly at neighbor points, allowing straight lines or sharp corners.
Shown as green. Becomes Free when moved.

Aligned :

Handles sit on a straight line, ensuring smooth curves.
Shown as purple.

Free :

Handles move independently, allowing asymmetric curves.
Shown as black.

Note

When a point is active, its handles highlight in red, changing their standard color.
For instance, Vector handles (usually green) appear yellow when active,
which can look like Automatic handles.

To fix this,
adjust the relevant entries under 3D Viewport ‣ Active Spline within Theme Preferences.

NURBS:

NURBS (Non-Uniform Rational B-Splines) describe curves with full mathematical exactness.
Where a Bézier curve merely approximates its target—a Bézier "circle," for instance, only comes close to a real circle—
a NURBS form reproduces the precise shape.

See the Wikipedia page for more.

NURBS points carry a unique weight property setting their influence on the curve.
This weight differs from Goal Weight used in soft body settings.
Adjust weights in the W field of the Transform panel.

Note

When all points share the same weight, their effects balance out.
Weight differences make the curve shift toward or away from specific points.

## Draw

Reference

Mode :

Edit Mode

Tool :

Toolbar ‣ Draw

Free-hand drawing creates curves.

Tool Settings:

Curve Stroke panel. 

Type
Select the curve type to draw with.

Poly :

Bézier Curve with straight segments (auto handles).

Bézier :

Tolerance
Smaller values match the drawing stroke more closely,
while larger values produce more smoothed output.

Method

Refit :

The curve refits incrementally (best output).

Split :

The curve splits until tolerance is met (better performance).

Detect Corners
Notice corners while drawing based on a specified angle;
Angles past the value are marked as corners.
Detected corners use non-aligned handles
for sharper results.

Taper Start, End
Scale the start and end point radius along the curve.

Radius Min
Minimum radius when stylus pressure is lowest (also minimum when tapering).

Max
Radius when stylus pressure is highest (or without a tablet).

Use Pressure
Stylus pressure controls the curve radius.

Depth
Set where and how curves are drawn.

Cursor :

Use the depth under the cursor for drawing.

Surface :

Draw on top of other objects.

Project Onto Selected
Only project onto chosen objects.

Offset
Distance to move the curve from the surface.

Absolute Offset
Use a fixed offset (doesn't scale by curve radius).

Only First
Use the stroke start for the depth only.

Plane
Draw-on orientation plane, active when Only First is enabled.

Normal to Surface :

Align to the surface.

Tangent to Surface :

Align perpendicular to the surface.

View :

Align to the viewport.

Options:

After the tool runs, these appear in the Adjust Last Operation panel.

Error
Error distance in object units. Similar to a subdivision rate.
Smaller values match the drawing stroke; larger values smooth more.

Fit Method

Refit :

Incrementally refit the curve (best output).

Split :

Split until tolerance is met (better performance).

Corner Angle
Angles above this count as corners.

Cyclic
Toggle whether the curve is Cyclic.

Reference

Mode: Edit Mode
Tool: Toolbar ‣ Draw

Draw freehand curves in the viewport.

Tool Settings

Curve Stroke panel.

Type specifies the curve basis.

Poly: A straight-segment Bézier (auto handles).
Bézier: Smoothed curve type.

Tolerance: Lower values match your stroke; higher values smooth it out.

Method determines the fitting approach:

Refit: Incremental refitting yields the best visual match.
Split: Iterative splitting prioritizes interactive responsiveness.

Detect Corners: When the angle exceeds the threshold, corners are recognized and handles are set non-aligned for crispness.

Taper Start, End: Shrink or expand the stroke's thickness at the beginning and endpoints.

Radius Min: The smallest stroke width at minimum pressure (also the taper minimum).
Max: Full stroke width at maximum pressure or no tablet.

Use Pressure: Stylus pressure modulates the radius.

Depth specifies drawing plane and method.

Cursor: Depth under the pointer.
Surface: Drawn atop other objects.

Project Onto Selected: Constrain projection to chosen objects only.

Offset: How far the curve sits from the surface.
Absolute Offset: A fixed distance unscaled by curve radius.
Only First: Depth sample at stroke beginning only.

Plane: Orientation when Only First is on.

Normal to Surface: Aligns to the surface.
Tangent to Surface: Perpendicular to surface direction.
View: Aligned to screen view.

Curve 2D: Project onto the Z axis.

As NURBS: Output NURBS with Bézier knots rather than plain Bézier.

After execution, the Adjust Last Operation panel offers refinement:

Error: Deviation distance in object units (subdivision rate analogue). Lower makes it closer to your input; higher smooths more.

Fit Method:

Refit: Incremental refitting (best results).
Split: Splitting until tolerance is reached (faster).

Corner Angle: Angles above this threshold are corners.

Cyclic: Toggle whether the curve closes on itself.

## Curve Properties

Hair Curves exhibit distinct properties in comparison to standard Curve objects, which are detailed below.

The Attributes panel holds diverse characteristics specific to hair, including strand placement and coloration. You can leverage the List View for attribute administration. For more details, consult the Attribute Reference documentation.

Hair requires an optional attachment surface—a mesh that anchors the curves and acts as a scalp for grooming operations. When you create a Curves object from the Add Menu, the selected object is automatically applied as the surface.

To assign a different surface, press Ctrl+P and choose Object (Attach Curves to Surface) from the Set Parent To popup. This option is also available in the Properties Editor under Curves settings.

The surface mesh attribute that governs curve attachment is named here. This determines which UV coordinate system on the surface each curve is anchored to.

If you modify the UV map on the surface, run Snap to Nearest Surfaces to realign the curves accordingly.

Reference

Editor: 3D Viewport
Mode: Edit Mode
Menu: Sidebar ‣ Item ‣ Curve Data

The Curve Data panel allows you to adjust settings for the active spline during editing. Options here control how the spline evaluates, appears, and is built mathematically.

The Cyclic option connects the final point back to the first, forming a closed loop when enabled or leaving it open when disabled. With the Default NURBS curve and a NURBS curve with Cyclic enabled shown side by side.

NURBS knot generation follows one of several patterns that govern how the spline parameterizes and bends:

Normal: Evenly distributed knots produce smooth curves with uniform influence from all control points.
Endpoint: Clamps the curve so the first and last control points lie on the path.
Bézier: The NURBS behaves like a Bézier, with control points functioning as Free handles.
Endpoint Bézier: Combines endpoint clamping with Bézier-like control.
Custom: You set knot values manually.

The Order setting controls the degree of the NURBS, determining how many control points affect each segment. Higher values create smoother transitions as each point influences a larger section. Lower values make curves sharper. Typical range is 2–6, contingent on control point count.

A NURBS curve with order 4 and a NURBS curve with order 2 illustrate the difference.

Resolution adjusts the number of subdivisions per segment. Increase for smoother results at the cost of computation; decrease for speed but less smoothness.

## Edge Slide

### Edge Slide 

Reference

Mode :

Edit Mode

Menu :

Edge ‣ Edge Slide

Shortcut :

G twice

Shifts whatever edges you've picked sideways, gliding them over the faces next to them.

Hint

Use Select Edge Loops to quickly select a chain of edges
that goes around the mesh.

### Usage 

Pick at least one edge, tap G twice, drag the cursor, then LMB to lock it in
(or RMB to back out).

Out of the box, every vertex on the chosen edges shifts by an identical percentage toward
its neighbor:

| Selected edges.  | Repositioned edges.  |

Switch on Even mode and the vertices instead hold a fixed gap from their neighbor.
Which neighbor each one targets is marked by the red dot:

| Even Mode enabled.  | Even Mode with Flip enabled.  |

### Options 

The Factor reading appears above the 3D Viewport during the operation, with the shortcut keys
listed in the status bar. The settings remain editable in the Adjust Last Operation panel even
once you've committed with LMB .

Factor
How far and which way to slide. Set it to -1 or 1 to push each edge all the way onto
one neighbor.

Even E
Normally a vertex travels a fixed fraction of its edge's length. Turn on Even and every vertex
instead lands at one identical absolute gap from a neighboring vertex. (Factor stays a relative
value regardless.)

Flipped F
While Even runs, picks the vertex's other neighbor instead.

Clamp Alt or C
Stops the edges short of the faces flanking them, so they can't slide past.

Mirror Editing
Slides the equivalent edges across on the mesh's opposite half too.
This requires Mesh Symmetry to be on.

Correct UVs
Adjusts the moved vertices' UVs so the texture doesn't stretch.

See also

Slide Vertices

## Loop Cut and Slide

### Loop Cut and Slide 

Reference

Mode :

Edit Mode

Menu :

Edge ‣ Loop Cut and Slide

Shortcut :

Ctrl - R

This divides a run of faces into two or more parallel loops. By default the fresh edges land
midway, though you're free to nudge them off toward either side.

### Usage 

You drive the tool through two interactive stages:

- Choose the face loop to cut

With the tool running, hover over an edge the cut should pass through — meaning one that runs
crosswise to the cut. A yellow preview line marks where the cut will fall. Press LMB to lock it
and continue, or RMB to abort.

- Slide the new edge loop(s)

Drag the cursor to reposition the freshly added loop. LMB drops the cut where you've placed it,
while RMB drops it dead center.

| Mesh before inserting edge loop.  | Choosing the face loop.  | Sliding the new edge loop.  |

See also

The Edge Slide tool for sliding existing edge loops.

### Options 

The following can be set live during the tool, and again afterward via the Adjust Last
Operation panel.

Number of Cuts Wheel
In the first stage, dial the cut count up or down by scrolling Wheel , typing a figure,
or hitting PageUp / PageDown .

| Preview of multiple edge loops.  | Result of using multiple cuts.  |

Smoothness
Pushes the new edges along their normals to keep the surface's curve. Alt - Wheel changes this
in the first stage, but since you get no preview there, it's usually cleaner to tweak it later
in the Adjust Last Operation panel.

| Added edge loop without smoothing.  | Same edge loop, but with smoothing value.  |

Falloff
Falloff type for Smoothness . Changes the shape of the profile.

Factor
Position of the edge loop relative to the surrounding ones.

Even E
Gives the new loop a uniform gap from one neighboring loop, rather than a gap scaled to the
length of each crosswise edge it cuts. Tap E during the second stage to flip it on or off.

Flipped F
Holds the Even gap against the opposite adjacent edge instead. Tap F during the second
stage to toggle.

| Cut with Even disabled.  | Cut with Even enabled. The red dot shows the side to which an even distance is kept.  | Cut with Even and Flipped enabled.  |

Clamp C
Uncheck this and the new loop is allowed past the boundary edges of the face loop.
Press C , or hold Alt , during the second stage to toggle it.

Mirror Editing
With this checked, sliding the new edges drags any existing edges on the mesh's far side along
too. Mesh Symmetry must be enabled for this.

Correct UVs
Leave this unchecked and the UV-map faces split evenly even when the 3D cut sits off-center.

## Offset Edge Slide

### Offset Edge Slide 

Reference

Mode :

Edit Mode

Menu :

Edge ‣ Offset Edge Slide

Shortcut :

Shift - Ctrl - R

Wraps each selected edge with a pair of fresh flanking edges.

### Usage 

- Select one or more edges.

- Click the menu item or press Shift - Ctrl - R .

- Drag the cursor rightward to widen the gap or leftward to narrow it.
Holding Shift slows the motion down for finer control.

Alternatively, type a number.

- Press LMB or Return to confirm.

| Edges selected.  | Surrounding edges created.  | Cap Endpoint enabled.  |

### Options 

While running, the Factor shows above the 3D Viewport and the shortcuts appear in the status
bar. Once you confirm with LMB , everything stays adjustable in the Adjust Last Operation panel.

Cap Endpoint
Builds triangles wherever an edge chain ends.

Factor
How far across the flanking faces the new edges get placed, as a relative amount.

Even E
Switch this on and the new vertices sit at a fixed absolute gap from the edge chain or its
flanking edges, rather than a proportional one.

Flipped F
Toggles whether the shape follows the edge chain or the flanking edges while Even is on.

| Even enabled.  | Even and Flipped enabled.  |

Clamp Alt or C
Holds the fresh edges back from the faces beside them, blocking any slide past those faces.

Mirror Editing
With this checked, sliding the new edges drags any existing edges on the mesh's far side along
too. Mesh Symmetry must be enabled for this.

Correct UVs
Assigns the new vertices UVs that match where they land on the mesh. Leave it unchecked and the
new vertices simply inherit the UVs of the edges you originally picked.

## Screw

### Screw 

Reference

Mode :

Edit Mode

Menu :

Edge ‣ Screw

This operator sweeps geometry along a helical path — handy for modeling screws, springs,
sea shells and the like.

It overlaps with the Screw Modifier, but several distinctions matter:

| Screw operator | Screw modifier |
| Works in world space. | Works in object space. |
| Extrudes only the selected geometry. | Extrudes all geometry. |
| The centerpoint can be specified manually. | The centerpoint is always the object's origin. |
| One revolution is always 360°. | The angle can be chosen freely. |
| The height offset of each revolution is calculated automatically based on the geometry. | The height offset must be specified manually. |
| Each revolution can also have a radial offset away from/towards the central axis (again determined by the geometry). | The radius stays constant. |

Per the table, both the per-revolution height and radial offset are worked out for you by the
operator. It derives them from the ends of an open profile — a string of joined edges that never
closes into a loop. Extrusion stacks the turns so that one revolution's top vertex meets the
following revolution's bottom vertex.

Sweeping such an open profile is the usual job, but it isn't the only one. Provided the selection
holds exactly one open profile — even a lone stray edge — you may also sweep closed profiles or
geometry that already carries faces.

A few examples follow.

| Wood Screw.  | Spring.  |

### Usage 

Begin by ensuring your mesh contains an open profile. To sweep something else (a circle or two,
say), add an open profile beside it.

With that ready, drop into Edit Mode and select the geometry to sweep, taking care to include
precisely one open profile. Too few or too many and the operator aborts with the error
"You have to select a string of connected vertices too."

Position the 3D Cursor at the point you want the geometry to revolve around. Confirm as well that
your screen's vertical axis lines up with the spin axis. Revolving around the global Z axis is
the typical case: for that, drop the 3D Cursor at the world origin and switch to an orthographic
side view.

You're set to run it now: open the Edge menu — click it in the 3D Viewport header or press
Ctrl - E — and pick Screw .

The step and turn counts can be changed afterward in the Adjust Last Operation panel.

If the open profile was only there to steer the sweep and you don't want its geometry, hover one
of its extruded faces, press L to grab them, and clear them with X or Delete .

### Options 

Screw panel (in Edit Mode). 

Steps
The number of extrusions to be done for each 360° turn.

Turns
The number of turns to create.

Center X, Y, Z
World-space coordinates of the pivot the geometry revolves around. It starts out at the 3D
Cursor's location.

Axis X, Y, Z
The direction vector the geometry spins about. It begins as the screen's vertical axis — so the
global Z in a side view, or the global Y in a top view. Flip the Axis to swap between clockwise
and counterclockwise.

Tip

You can use the Align View to Active
menu item to align the viewport, and thereby the Axis , to a certain item
in the scene.

Keep in mind the Axis governs only the "horizontal" spin around the centerpoint, not any
"vertical" travel. That vertical motion always follows the distance and direction set by the open
profile's endpoints, heading downward in the object's local space.

### Examples 

### Creating a Spring 

Start with a circle for the spring's cross section:

- Open Blender and delete the default Cube.

- Add a circle by pressing Shift - A and selecting Mesh ‣ Circle .

- Set the Location X property of this new object to -3 and its Rotation X property to 90°.

- Enter Edit Mode by pressing Tab .

- Switch to the Front Orthographic view by pressing Numpad1 .

Extrusion profile created. 

Now add a vertical line that sets how far apart the spring's loops sit:

- Deselect all vertices by clicking on an empty space or pressing Alt - A .

- Click Ctrl - RMB twice to create two vertices connected by an edge.

- Select both vertices and press S X 0 Return to ensure they have the same X coordinate.
(This is necessary to keep the spring's radius constant.)

Guide profile created. 

The spring is ready to build:

- Select both the circle and the line by pressing A .

- Click Edge ‣ Screw .

- Adjust the Steps and Turns to your liking.

- Try changing Axis Z to -1 and see that this makes the spring turn the other way.

| Counterclockwise direction.  | Flipped to Clockwise direction.  |

A diagonal Axis yields curious shapes — for instance, hold Axis Z at -1 and set Axis X to 1.
Each loop then tilts 45°, yet the loops still march straight down the guide line's direction
from one to the next.

### Creating a Screw Spindle 

For helices with no gaps between turns, the Screw operator is a natural fit.

- Open Blender and enter Edit Mode for the default cube.

- Delete all vertices by pressing X or Delete .

- Switch to the Front Orthographic view by pressing Numpad1 .

- Click Ctrl - RMB three times to create a profile like the one below.

- Select the two vertices closest to the global Z axis and press S X 0 Return
to ensure they have the same X coordinate.

- Select all three vertices and click Edge ‣ Screw .

- Adjust the Steps and Turns to your liking.

| Profile for a screw spindle.  | Result after running the Screw operator.  |

More elaborate forms work too, such as this spiral "staircase":

| Profile.  | Generated mesh.  |

### Creating a Screw Tip 

So far the profile's first and last vertex have always shared an X coordinate, which holds the
helix at a constant radius. Nothing forces that, though — feed in differing X coordinates and the
helix tapers or flares as it climbs.

| Profile.  | Generated.  |
