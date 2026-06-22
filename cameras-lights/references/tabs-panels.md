# Tabs Panels, Curve, Shape, Curves ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Tabs & Panels; Curve; Shape; Curves; Knife Topology Tool; Geometry Data.

## Tabs & Panels

### Tabs & Panels

### Tabs
Top: Horizontal Tab header in the Topbar. Bottom: Vertical Tab header shows tab icons in the Properties.

Controlling overlapping sections of the user interface is the job of tabs. Only one Tab's content shows at a time. The Tabs are listed in a Tab header, which can run horizontal or vertical.

### Switching/Cycling
From anywhere in a vertical tab, Ctrl - Wheel switches it. You can also step through tabs with Ctrl - Tab and Shift - Ctrl - Tab, or hold LMB down and slide the mouse across the tab header icons. Pressing NumpadPeriod scrolls to the active tab when it's out of view.

Note that these shortcuts don't cover Workspace tabs; see Workspace controls.

### Panels
Panels in Properties.

Yellow marks a highlighted panel, while red marks a highlighted subpanel.

The panel is the smallest organizational unit in the user interface. Its header, always on screen, shows the panel's title. Subpanels live inside some panels.

### Collapsing and Expanding
A panel sits either expanded, showing its contents, or collapsed, hiding them. A down-arrow (▼) in the header marks an expanded panel, a right-arrow (►) a collapsed one.

- A LMB click on the panel header folds it open or shut.

- A press of A does the same to whichever panel sits under the pointer.

- On a collapsed panel's header, Ctrl - LMB opens it while closing every other.

- On an expanded panel's header, Ctrl - LMB toggles all of its subpanels at once.

- Drag LMB across several headers to fold many of them together.

### Position
Shift a panel within its region by grabbing the grip widget (::::) on the right of its header and dragging.

### Pinning
Now and then you'll want panels from different tabs visible together — keeping a camera's properties in view, say, while other objects are selected. Making panels pinnable is the answer.

Whatever tab is selected, a pinned panel stays in view. Pin one by clicking the pin icon in its header. Panels lacking a pin icon can still be pinned by RMB on the panel header and choosing Pin, or by pressing Shift - LMB.

Note

Not every panel can be pinned. The Sidebar supports it, for instance, while the Properties editor does not.

### Presets
For quickly reapplying common settings, Blender's panels offer a Presets menu ( ). Storing frequently used configurations as presets saves time, since a single click brings them back.

Example Presets menu.

Selector
The roster of presets on hand. Choose one and its stored values land on the matching properties.

Preset Name
The label a newly added preset will carry.

(Add)
Captures the present settings as a new preset, which is then saved and shows up in the list for reuse later.

(Remove)
Wipes out the selected preset.

Stored as Python files in Blender's configuration directory, presets can be hand-edited by advanced users to fine-tune settings or copied across to other systems.

## Curve

This page covers basic curve editing.

Transform:

Reference

Mode :

Edit Mode

Menu :

Curve ‣ Transform

Edit Bézier curves by moving control points and handles.
NURBS curves have only control points.

Move, Rotate, Scale
Like other Blender elements, curve control points and handles can be
moved, rotated, or scaled as described in
Basic Transformations.

To Sphere, Shear, Bend, Push/Pull, Warp, Randomize
Transform tools described in
the Transformations sections.

Move/Scale Texture Space
Like other objects, curves have texture spaces which can be
edited.

Radius:

Reference

Mode :

Edit Mode

Tool :

Toolbar ‣ Radius

Menu :

Curve ‣ Transform ‣ Radius

Shortcut :

Alt - S

Control the extrusion width along the curve path.
Radius is smoothed point-to-point (visible via normals).
Adjust point radius using the Radius transform tool or Sidebar Transform panel.

One control point radius set to zero. 

Mirror:

Reference

Mode :

Edit Mode

Menu :

Curve ‣ Mirror

Shortcut :

Ctrl - M

The Mirror tool works identically to mesh vertex mirroring.

Snap:

Reference

Mode :

Edit Mode

Menu :

Curve ‣ Snap

Shortcut :

Shift - S

Curve component snapping mirrors mesh snapping behavior.
Control points and handles snap, except between components of the same active curve.
2D curves snap with points restricted to local XY axes.

Spin:

Reference

Mode :

Edit Mode

Menu :

Curve ‣ Spin

The Spin operator is for one-dimensional surface objects only.
Curves cannot be spun; see Surface editing for full documentation.

Add Duplicate:

Reference

Mode :

Edit Mode

Menu :

Curve ‣ Add Duplicate

Shortcut :

Shift - D

Duplicate chosen control points and implicitly selected curve segments (if any).
Selecting only a handle duplicates the entire point.
The copy becomes active for repositioning.

Split:

Reference

Mode :

Edit Mode

Menu :

Curve ‣ Split

Shortcut :

Y

Separate the chosen portion from the rest, creating an independent segment.
Reposition or alter it separately.

- Selected curve segments become new independent curves.
- Selecting a single control point duplicates it as loose, keeping the original attached.

Separate:

Reference

Mode :

Edit Mode

Menu :

Curve ‣ Separate

Shortcut :

P

Break curve objects made of multiple distinct curves into individual objects.

Note: single-curve objects become new Curve objects with no control points.

Toggle Cyclic:

Reference

Mode :

Edit Mode

Menu :

Curve ‣ Toggle Cyclic

Shortcut :

Alt - C

Switch between open and closed (Cyclic) curves.
Only curves with at least one chosen control point are affected.
Closing segments use start/end handles for Bézier and adjacent points for NURBS.
Auto handles update only if they are Auto type.

Open and Closed curves. 

This action applies only to the original first or the last added control point.
Deleting segments doesn't change this—only the starting and last points matter. This means
Alt - C may join two curves instead of closing one!
Remember: closing a 2D curve creates a renderable flat face.

Open and Closed curves. 

Set Spline Type:

Reference

Mode :

Edit Mode

Menu :

Curve ‣ Set Spline Type

Shortcut :

V

Convert splines between Bézier, NURBS, Poly, and Catmull Rom types.
This is basic conversion—Blender doesn't preserve exact shape or point count.
For instance, converting NURBS to Bézier maps each three-point NURBS group
to one Bézier point with two handles.

Type
Specify the target spline type. See the
Spline Types documentation for details.

Bézier :

Convert to Bézier type.
- Poly splines convert with vector handles.
- NURBS or Catmull Rom splines convert with automatic handles.

Note

NURBS to Bézier conversion requires at least six points.
Non-multiple-of-three point counts result in truncation.

NURBS :

Convert to NURBS type.

Poly :

Convert to poly type.

Handles
Incorporate handle information during conversion.

Show/Hide:

Reference

Mode :

Edit Mode

Menu :

Curve ‣ Show/Hide

Shortcut :

Alt - H , H , Shift - H

Hide or show Edit Mode elements.
Only control points toggle; segments always display unless all connected points hide.

See Show/Hide in Object Mode .
See also the Curve Display panel.

Clean Up:

Decimate Curve:

Reference

Mode :

Edit Mode

Menu :

Curve ‣ Clean Up ‣ Decimate Curve

Lower the point count while attempting to keep the original shape.
Works similarly to the mesh equivalent.

Ratio
Percentage of control points to remove.

Note

Only Bézier curves can be decimated.

Delete:

Reference

Mode :

Edit Mode

Menu :

Curve ‣ Delete

Shortcut :

X , Delete

Delete pop-up menu options:

Vertices
Remove chosen control points without breaking the curve
(adjacent points link directly).
Remember: NURBS order cannot exceed its point count,
so it might decrease when deleting points.
When one point remains, no visible curve exists.
With all points deleted, the curve itself is removed.

Segment
Remove the segment connecting chosen control points and disconnect them.

Dissolve Vertices:

Reference

Mode :

Edit Mode

Menu :

Curve ‣ Delete ‣ Dissolve Vertices

Shortcut :

Ctrl - X

Remove chosen control points, with remaining segments fitted by adjusting handles.

| Before deleting.  | Deleting vertices.  |
| Deleting segment.  | Dissolve vertices.  |

## Shape

Shape panel controls curve appearance.

Shape panel. 

Dimensions
New curves default to 3D, allowing control points anywhere in space.
Set to 2D to restrict points to the curve's local XY plane.

Resolution Preview/Render U
The resolution property defines points calculated between each pair of control points.
Curves become smoother or rougher by adjusting resolution.
Preview U sets 3D Viewport resolution; Render U sets render resolution. If Render U is zero (0),
Preview U applies to both 3D Viewport and render.

| Curves with a resolution of 3.  | Curves with a resolution of 12.  |

Twist Method
3D curves have control points outside the local XY plane.
This creates twist affecting curve normals.
Adjust how twist calculates by choosing
Minimum, Tangent, or Z-Up.

| Curves with a twist of Minimum.  | Curves with a twist of Tangent.  |

Smooth
Interactively remove twists from the curve. Useful if a curve has "kinks"
from over-twisting; possible when converting meshes to curves.

Fill Mode
Fill determines display when a curve is beveled (see Beveling details below).
Set to Half for display as half a cylinder.

| Curves with a fill of Half.  | Curves with a fill of Full.  |

Fill Solver
Triangulation algorithm for filling 2D curves.

Sweep Line :

Fast triangulation for well-formed outlines.
Doesn't handle self-intersecting curves.

Delaunay :

Uses Constrained Delaunay Triangulation (CDT).
More robust, supports self-intersecting curves, but slower.

Fill Rule
Fill rule for the Delaunay Fill Solver determining inside regions.

Even-Odd :

Alternate inside/outside based on boundary crossing count.
Overlapping regions may cancel based on crossing count.

Non-Zero :

Inside/outside depends on winding direction.
Overlapping curves with matching winding are filled as union;
opposite winding creates holes.

Curve Deform

Radius
Scale the deformed object by the curve's radius.
Used with curves as paths or the Curve Modifier.

Stretch
Let the mesh object stretch or compress across the entire curve.
Combine with Bounds Clamp for intended behavior.
Used with the Curve Modifier.

Bounds Clamp
Disregard the object and mesh offset along deformation axis.
Helpful with Stretch or negative axes.
Used with the Curve Modifier.

### Shape

Reference

Editor :

Properties

Mode :

Object Mode, Edit Mode

Panel :

Object Data ‣ Shape

Shape panel.

Resolution Preview U/V
How dense the generated surface mesh is in the 3D Viewport. A larger number means more vertices
and a smoother-looking surface.

Render U/V
How dense the generated surface mesh is at render time. Leave a number at 0 and the matching value
from Resolution Preview steps in instead.

| Resolution 1×1. | Resolution 3×3. |

See also

Preview resolution can additionally be dialed in per individual surface within a Surface object.
See the Active Spline panel in the Sidebar.

### Shape 

Reference

Panel :

Particle System ‣ Hair Shape

Parameters here control strand curve geometry during rendering.

Strand Shape
Shape factor determining thickness transition from root to tip.
Negative values create rounded geometry toward the top; zero produces linear geometry; positive values round toward the bottom.

Diameter Root
Scaling factor for strand width at the root.

Tip
Scaling factor for strand width at the end.

Radius Scale
Universal multiplier for Root and Tip values, adjusting overall strand thickness.

Close Tip
Collapses tip thickness to zero, overriding nonzero tip multipliers.

## Curves

This section covers curve editing in the curves object format.

Transform:

Reference

Mode :

Edit Mode

Menu :

Curves ‣ Transform

Edit curves by moving control point locations.

Move, Rotate, Scale
Like other Blender parts, points can be
moved, rotated, or scaled per
Basic Transformations.

To Sphere, Shear, Bend, Push/Pull
Transform methods covered in
the Transformations sections.

Radius:

Reference

Mode :

Edit Mode

Tool :

Toolbar ‣ Radius

Menu :

Curves ‣ Transform ‣ Radius

Shortcut :

Alt - S

Set the extrusion width along the curve path directly.
Radius is smoothed point-to-point (visible via normals).
Set point radius via the Radius transform tool or Sidebar Transform panel.

One control point radius set to zero. 

Mirror:

Reference

Mode :

Edit Mode

Menu :

Curves ‣ Mirror

Shortcut :

Ctrl - M

The Mirror tool works like mesh vertex mirroring.

Snap:

Reference

Mode :

Edit Mode

Menu :

Curves ‣ Snap

Shortcut :

Shift - S

Curve component snapping mirrors mesh snapping.
Points and handles snap, except within the active curve's own components.
2D curves snap with points fixed to local XY axes.

Duplicate:

Reference

Mode :

Edit Mode

Menu :

Curves ‣ Duplicate

Shortcut :

Shift - D

Duplicate chosen points,
plus any implicitly chosen curve sections (if any).
Selecting only a handle duplicates the whole point.
The copy is active for repositioning.

Extrude Curve and Move:

Reference

Mode :

Edit Mode

Menu :

Curves ‣ Extrude Curve and Move

Shortcut :

E

Duplicate chosen points, move them, and reconnect to form a continuous curve.

Set Attribute:

Reference

Mode :

Edit Mode

Menu :

Curves ‣ Set Attribute

Display a pop-up showing the active attribute
with its value for the chosen points
From there, assign a new value across all chosen points.

Useful for setting attribute values consistently.

Set Curve Type:

Reference

Mode :

Edit Mode

Menu :

Curves ‣ Set Curve Type

Shortcut :

V

Convert splines between Bézier, NURBS, Poly, and Catmull Rom types.
Basic conversion—Blender doesn't maintain exact shape or point count.
Converting NURBS to Bézier maps each three-point NURBS group
to one Bézier point with handles.

Type
Specify the target type. See the
Spline Types documentation.

Bézier :

Convert to Bézier type.
- Poly convert with vector handles.
- NURBS or Catmull Rom convert with automatic handles.

Note

NURBS to Bézier conversion requires at least six points.
Non-multiple-of-three counts truncate.

NURBS :

Convert to NURBS type.

Poly :

Convert to poly type.

Catmull Rom :

Convert to Catmull Rom type.

Handles
Include handle information during conversion.

Toggle Cyclic:

Reference

Mode :

Edit Mode

Menu :

Curves ‣ Toggle Cyclic

Shortcut :

Alt - C

Switch between open and closed (Cyclic) curves.
Only curves with at least one chosen point close or open.
Closing segments use start/end handles for Bézier and neighbor points for NURBS.
Auto handles update if they are Auto type.
Open and Closed curves. 

This action applies only to the original first or last added point.
Segment deletion doesn't change this—only starting and last points apply. This means
Alt - C may join two curves instead of closing one!
Remember: closing a 2D curve creates a renderable flat face.

Open and Closed curves. 

Separate:

Reference

Mode :

Edit Mode

Menu :

Curves ‣ Separate

Shortcut :

P

Move chosen curve geometry into their own curve object.

Delete:

Reference

Mode :

Edit Mode

Menu :

Curves ‣ Delete

Shortcut :

X

Remove Control Points or Segments.
Deletion shortens curves or simplifies
segments by removing middle points.

Split:

Reference

Mode :

Edit Mode

Shortcut :

Y

Separate the chosen portion from the rest,
making an independent segment.
Reposition or alter separately.

- Chosen curve segments become independent curves.

- Selecting one point duplicates it as loose, keeping the original attached.

Curves — Strand and Strip Options

Reference
Panel: Render ‣ Curves

Shape

Strand:
Render curves as thin strands approximately one pixel wide. Curve diameter settings are ignored.

Strip:
Render curves as a flat ribbon with rounded normals.

Additional Subdivisions
Extra subdivision passes beyond the curve resolution defined in hair system settings. Higher values smooth curve strands.

## Knife Topology Tool

### Knife Topology Tool 

Reference

Mode :

Edit Mode

Tool :

Toolbar ‣ Knife

Menu :

Mesh ‣ Knife Topology Tool

Shortcut :

K

The Knife tool lets you interactively slice through faces, subdividing them and trailing a chain
of new edges behind the cut.

### Usage 

To begin, grab the tool from the Toolbar or press K . A scalpel cursor signals it's live.

LMB wherever the cut should start — that can be anywhere: on a vertex, edge, or face, or even off
the mesh entirely.

Move toward your next point. A yellow line previews the edges to come and aqua dots mark the new
vertices. LMB confirms and starts the next segment.

When you're finished, press Spacebar or Return to commit the cuts. Esc cancels instead.

Hint

By using Multi-Object Editing, you can cut multiple objects
at the same time.

| Mesh before knife cut.  | Knife cut active.  | After applying knife cut.  |

### Tool Settings 

These appear only when you launch the tool from the Toolbar, not via K . Find them in the Tool tab
of both the Properties Editor and the Sidebar.

Occlude Geometry
Cut only what's visible on screen. Turn it off to cut clean through the mesh, faces on the back or
hidden behind others included.

Only Selected
Cut through selected geometry alone. Press Shift - K rather than K to start cutting with this
already on.

X-Ray
Keep the cutting path visible even where geometry sits in front of it.

Measurements
The measurements to show along the cutting path: distances, angles, or both.

Angle Snapping
Whether to constrain the cutting lines to multiples of the Snap Increment angle.

None :

No snapping.

Screen :

Snap in screen space (the viewing plane).

Relative :

Snap in a plane on the geometry, relative to an adjacent edge or cutting line.

| Relative snapping at 90°. Blender highlights the reference edge in red and shows the snapping direction in white.  | Doing a few more cuts and applying.  |

Snap Increment
The angle to use for Angle Snapping .

### Controls 

These keyboard shortcuts are shown in the
status bar while cutting.
They're available both when using the tool from the Toolbar and when pressing K .

Cut LMB
Click to drop a new cutting line, or drag to lay cutting lines as the cursor crosses edges.

Close Loop - Double-click LMB
Drops a cutting point at the cursor (as a single click would), then ties it back to the path's
first point, sealing the loop.

Stop RMB
Finishes the current cutting path and opens a new one. The cursor snaps to cuts you've already
made.

Confirm Spacebar or Return
Locks in the cut, converting the cutting paths into real edges.

Cancel Esc
Drops the cut entirely.

Undo Ctrl - Z
Undoes the last cutting line — or, if you'd been dragging, every cutting line from that drag.

Midpoint Snap Shift
Hold it down to pull the cursor onto the midpoint of each edge.

Ignore Snap Ctrl
Hold it down to momentarily switch off snapping to existing vertices, edges, and cutting lines.

Cut Through C
Cut through occluded faces too, not just the visible ones. This mirrors (and inverts) the Occlude
Geometry setting above.

Axis X , Y , or Z
Pins the current cutting line to a global axis. A second press uses the object's local axis; a
third lifts the constraint.

Measure S
Steps through the measurement readouts — distances, angles, or both at once.

X-Ray V
Switches the display of geometry-hidden cuts on or off.

Angle Constraint A
Pins cutting lines to multiples of the Snap Increment angle. Set that angle in the Tool Settings
beforehand (see above), or type it while cutting with Angle Constraint active.

Snapping starts in the Screen plane by default. A second A press snaps in planes on the geometry,
Relative to an automatically picked edge or cutting line; press R to choose a different reference
line.

A third A press switches the snapping off again.

### Known Limitations 

### Duplicate Vertices 

When a cut spawns duplicate vertices, an oversized clipping range is usually the culprit. Try
raising the Clip Start to dodge it. Also see Depth Troubleshooting for details.

## Geometry Data

### Geometry Data

This panel handles the assorted generic data attributes a mesh might carry.

Warning

Clear any of this data and those values are gone for good.

Clear Sculpt Mask Data
Removes the internal sculpt_mask attribute, which drives the Sculpt Masking Feature.

Add/Clear Skin Data
Manages the skin data the Skin Modifier relies on. You may need it when a Skin modifier exists but its skin data doesn't.

Reorder Mesh Spatially
Sorts vertex and face indices by spatial position, so elements near each other in the scene also sit near each other in memory.

The topology and visible geometry stay the same. What improves is performance wherever spatial coherence counts, such as:

- Quicker BVH (Bounding Volume Hierarchy) builds, helping both rendering and the viewport.

- Tighter memory access while sculpting dense, high-poly meshes.

- Possibly smoother handling of heavy geometry in edit and sculpt modes.

Warning

- Because vertex and face indices change, anything depending on stable indices can break, including shape keys, UV maps, or external scripts that reference vertex indices.

- Tread carefully on meshes already tied to rigs or shape keys.

Tip

It pays off most on static, high-resolution meshes for sculpting or rendering, where speed outweighs index stability.

For animated or deformed meshes, leaving the order alone is generally the safer call.

Add/Clear Custom Split Normals Data
Creates Custom Split Normals data when there isn't any.
