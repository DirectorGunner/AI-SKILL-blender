# Rip Vertices, Rip Vertices And Extend, Rip Vertices And Fill, By Attribute ...

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Rip Vertices; Rip Vertices and Extend; Rip Vertices and Fill; By Attribute; Checker Deselect; Select Mirror; Select More/Less; Side of Active; Extrude Manifold; Poly Build; Spin; Grab; Pinch; Metaball Primitives; Smooth Corrective Modifier; Laplacian Deform Modifier; Simple Deform Modifier; Surface Deform Modifier.

## Rip Vertices

### Rip Vertices

Reference

Mode:

Edit Mode

Menu:

Vertex → Rip Vertices

Shortcut:

V

Splits the mesh at two adjacent edges of each chosen vertex.
Vertices then move using the cursor to open a gap.
When positioned, hit LMB or Return to lock in place. Alternatively, press RMB or Esc to cancel (vertices stay separated).

With a single chosen vertex, the mouse position decides the cut direction.
With multiple chosen vertices, linked edge orientation decides direction.

Note

Rip Vertices doesn't support removing whole faces. Use Split Selection instead.

See also

Split Faces by Edges cuts only chosen edges, leaving adjacent unselected edges intact.

### Examples

Single vertex ripping:

| Mouse cursor to the right. | Ripping results in a vertical cut. |
| Mouse cursor below. | Ripping results in a horizontal cut. |

Ripping vertices along connected edges:

| Vertical edges selected. | Ripping cuts vertically regardless of mouse position. |

As a rare case, cutting in several directions works:

| Before ripping. | After ripping. |

Ripping separate "islands" fails and throws an error.

## Rip Vertices and Extend

### Rip Vertices and Extend

Reference

Mode:

Edit Mode

Menu:

Vertex → Rip Vertices and Extend

Shortcut:

Alt - D

This tool copies the outer vertices of chosen edges, then links these copies to their originals. Neighboring faces connect and grow to accept the new vertices, becoming n-gons.

| Before ripping. | After ripping. |

On border vertices, the outcome resembles Extrude Edges, but existing faces only expand (new faces don't form).

| Before ripping. | After ripping. |

## Rip Vertices and Fill

### Rip Vertices and Fill

Reference

Mode:

Edit Mode

Menu:

Vertex → Rip Vertices and Fill

Shortcut:

Alt - V

This works like Rip Vertices, but fills the gap with fresh surfaces instead of leaving it open.

| Before ripping. | After ripping. |

## By Attribute

### By Attribute

Reference

Mode :

Edit Mode

Menu :

Select ‣ By Attribute

Selects whichever vertices, edges, or faces have the currently active attribute set to True.

The active attribute is the one highlighted in the Properties Editor's Attributes list.

Note

This works only on a Boolean attribute whose domain is Vertex, Edge, or Face.

## Checker Deselect

### Checker Deselect

Reference

Mode :

Edit Mode

Menu :

Select ‣ Checker Deselect

Drops mesh elements from the selection in a recurring pattern that begins at the active element. Which kind gets dropped, vertices, edges, or faces, follows the current selection mode.

When the selection holds several disconnected "islands," only the island with the active element is touched.

### Options

Deselected
How many elements drop out at the front of each pattern cycle.

Selected
How many elements stay in at the tail of each pattern cycle.

Offset
How many elements the first cycle skips over.

### Example

| Initial selection.  | Running with Deselected = 1 and Selected = 1.  | Deselected changed to 2.  |

## Select Mirror

### Select Mirror

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select Mirror

Shortcut :

Shift - Ctrl - M

Flips the selection to the opposite side of the mesh.

### Options

Axis
The local axis around which to mirror. The mesh's origin is used as the centerpoint.

Extend
Add to the selection instead of replacing it.

From left to right: initial selection – mirrored around the X axis – with Extend.

Hold Shift to choose several axes at once. With Extend off, the mirror happens once across all those axes combined; with Extend on, it happens across every possible combination of them.

From left to right: initial selection – mirrored around the X and Z axes – with Extend.

## Select More/Less

### Select More/Less

### Select More

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select More/Less ‣ More

Shortcut :

Ctrl - NumpadPlus

Expands the selection out to the elements along its edge. Concretely, it folds in the neighbors of the current selection, those neighbors being vertices, edges, or faces according to the Selection Mode.

### Options

Face Step
Add whole neighboring faces even if they only share a single vertex.

From left to right: initial selection – Select More – Face Step enabled

### Select Less

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select More/Less ‣ Less

Shortcut :

Ctrl - NumpadMinus

Pulls the selection in from its edge. Concretely, it drops any element that has an unselected neighbor, that neighbor being a vertex, edge, or face according to the Selection Mode.

### Options

Face Step
Deselect elements that share a vertex with an unselected face.

### Select Next Active

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select More/Less ‣ Next Active

Shortcut :

Shift - Ctrl - NumpadPlus

Selects the element that "logically follows" the two most recently selected ones.

| Initial selection.  | Using Next Active once.  | Using Next Active twice.  |

### Select Previous Active

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select More/Less ‣ Previous Active

Shortcut :

Shift - Ctrl - NumpadMinus

Deselects the last selected element and makes the next-to-last one active again.

## Side of Active

### Side of Active

Reference

Mode :

Edit Mode

Menu :

Select ‣ Side of Active

Selects all the vertices that are (for example) to the right of the active vertex.

### Options

Axis Mode
The transform orientation from which to take the Axis .

Axis Sign
Select the vertices whose Axis coordinate is…

Positive Axis
…greater than or equal to that of the active vertex.

Negative Axis
…less than or equal to that of the active vertex.

Aligned Axis
…equal to that of the active vertex.

From left to right: initial selection, Positive, Negative, Aligned.

Axis
The axis along which to compare coordinates.

Threshold
Tolerance for vertices that are slightly outside of the coordinate range.

## Extrude Manifold

Extrude Manifold

Mode: Edit Mode
Toolbar: Extrude Manifold
Menu: Mesh ‣ Extrude ‣ Extrude Manifold

This tool works like Extrude Faces but enables Dissolve Orthogonal Edges by default. This feature automatically splits and removes adjacent faces during inward extrusion.

An example demonstrates the effect of automatic face dissolution when extruding interior surfaces.

## Poly Build

Poly Build

Mode: Edit Mode
Toolbar: Poly Build

Poly Build combines multiple mesh editing operations into one tool, streamlining retopology and quick modeling.

Tool Options

Create Quads
When a new triangle shares an edge with an existing face, this option automatically dissolves that edge, producing a quad instead.

Controls

Adding Geometry — Ctrl - LMB
Creates a vertex at the cursor and forms a triangle using this new vertex and the nearest existing edge. If the nearest edge already has two neighboring faces, instead creates an edge from the new vertex to the nearest existing vertex. Preview appears in blue while holding Ctrl.

Deleting Geometry — Shift - LMB
Dissolves the vertex or removes the face under the cursor. Red highlight shows the target while holding Shift.

Moving Vertices — LMB
Click and drag to reposition a vertex.

Extruding Edges — LMB
Click and drag an edge to extrude it into a quad.

Enabling Snapping and Auto Merge simplifies vertex alignment and combination.

## Spin

Spin

Mode: Edit Mode
Menu: Mesh ‣ Extrude ‣ Spin
Toolbar: Spin

Spin extrudes (or duplicates if the selection is manifold) selected geometry, rotating it around a specific center point and axis. This produces lathe-like objects — circular extrusions centered on the 3D cursor and revolving around an axis perpendicular to your current view.

The viewing angle determines the rotation axis. The 3D cursor position sets the rotation center.

Tool Options

Steps
Number of copies to extrude along the rotation.

Use Duplicates
Keeps the original selected elements as separate, unlinked islands.

Axis
The pivot axis for the spin operation.

Options Panel

Steps
Number of copies along the revolution.

Angle
Sweep angle in degrees (for example, 180 creates a half rotation).

Auto Merge
Automatically joins the first and last duplicates if a full 360-degree rotation produces overlapping geometry.

Flip Normals
Reverses the normal direction of resulting surfaces.

Center X, Y, Z
Spin rotation center; defaults to the cursor position.

Axis X, Y, Z
Rotation axis vector; defaults to the current view axis.

Workflow Example

Create a 2D profile of your desired object. For a hollow object, thicken the outline.

Switch to top view (Numpad7) to work from above.

Place the 3D cursor at the profile's center. Enter Edit Mode, select a center vertex, then snap the cursor to it with Mesh ‣ Snap ‣ Cursor to Selection.

Select all vertices with A and activate Spin from the toolbar. Use the gizmo to rotate.

Angle Variations

Two side-by-side examples show a full 360-degree rotation and a 120-degree partial rotation.

Duplicate Mode

When Use Duplicates is enabled, the original geometry remains separate from the spun copies.

Handling Duplicate Vertices

The spin leaves duplicate vertices along the profile seam. Box select (B) to capture seam vertices, then apply Merge by Distance.

Compare the vertex count before and after merging (shown in the Mesh data panel). The final count should match the original profile count. If not, some vertices were missed and need manual welding.

To merge two vertices: select both with Shift - LMB, press S to scale, hold Ctrl while scaling to zero, then LMB to confirm. Run Mesh ‣ Merge ‣ By Distance or press M and choose By Distance.

Final Step

Recalculate normals by selecting all vertices, pressing Alt - N, and confirming Recalculate Normals Outside.

## Grab

Grab

Mode: Edit Mode
Toolbar: Grab

The Grab tool repositions UVs using a brush interface.

Tool Settings

Size
Controls the brush radius in pixels. Press F to interactively adjust size by dragging and LMB to confirm. Type a number then enter while pressing F to set size numerically.

Strength
Controls the brush effect intensity. Press Shift - F to interactively adjust strength by dragging and LMB to confirm. You can also enter the value numerically while in Shift - F mode.

Falloff
Controls the Strength falloff from the brush center (left curve) to borders (right curve). Adjusting the curve shape makes the brush softer or harder. See the Curve Widget documentation.

Curve Preset

Custom — Manually manipulate control points in the curve widget or choose a preset curve as a starting point.

Smooth — Center, border, and transition strength are evenly distributed.

Smoother — Similar to Smooth with a wider center point before tapering.

Sphere — Strength concentrates at the center with steep border falloff.

Root — Similar to Sphere with a more concentrated center.

Sharp — Strongest at center, exponentially tapering off to a fine point.

Linear — Center is strongest; strength consistently weakens toward borders.

Sharper — Similar to Sharp with a more condensed center.

Inverse Square — Hybrid between Smooth and Sphere.

Constant — Strength remains unified across the entire brush, creating a sharp border edge.

Options

Lock Borders
Locks the UV island boundary from brush effects, preserving island shape.

Sculpt All Islands
Edits all islands, not just the island nearest the brush center at stroke start.

## Pinch

Pinch

Mode: Edit Mode
Toolbar: Pinch

The Pinch tool moves UVs toward the brush center. Invert the effect by pressing Ctrl - LMB.

Tool Settings

Size
Controls the brush radius in pixels. Press F to interactively adjust by dragging and LMB to confirm. Type a number then enter during F to set numerically.

Strength
Controls the brush intensity. Press Shift - F to interactively adjust strength, then LMB to confirm. You can also enter the value numerically while in Shift - F mode.

Falloff
Controls the Strength falloff from brush center to borders. Adjust the curve shape for softer or harder effects. See Curve Widget documentation.

Curve Preset

Custom — Manually adjust curve control points or select a preset curve to start from.

Smooth — Center, border, and transition strength are evenly distributed.

Smoother — Similar to Smooth with a wider center point.

Sphere — Strength concentrates at center with steep border falloff.

Root — Similar to Sphere with more concentrated center.

Sharp — Strongest at center, exponentially tapering to a fine point.

Linear — Center is strongest; strength weakens consistently toward borders.

Sharper — Similar to Sharp with a more condensed center.

Inverse Square — Hybrid between Smooth and Sphere.

Constant — Strength unified across the brush, creating a sharp border edge.

Options

Lock Borders
Locks the UV island boundary from brush effects.

Sculpt All Islands
Edits all islands, not just the island nearest the brush center at stroke start.

### Pinch

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Pull toward center; Ctrl inverts to Magnify.

### Brush Settings

### General

Note

More info at General brush settings
and on Advanced brush settings.

## Metaball Primitives

Five predefined metaball configurations are available from the Add menu.

Ball creates a point-based meta.

Capsule creates a line-segment-based meta.

Plane creates a plane-based meta.

Ellipsoid creates an ellipsoid-volume-based meta.

Cube creates a cubic-volume-based meta.

Each primitive has additional parameters available through the Add menu or during editing. Standard options include radius, viewport alignment, position, and rotation.

## Smooth Corrective Modifier

The Smooth Corrective modifier reduces distortion in highly warped mesh areas, particularly useful after armature deformation where joint compression is difficult to avoid through weight painting alone.

Understanding its workings is essential for effective use.

Rest State serves as a reference to identify distorted regions, using original vertex positions by default.

Smoothing internally corrects distorted areas using multiple relaxation strategies.

Factor controls smoothing intensity. Higher values amplify the effect. Values beyond 0.0–1.0 distort the mesh.

Repeat sets the number of smoothing iterations, equivalent to applying the Smooth tool multiple times.

Scale adds additional enlargement, compensating for volume loss that sometimes occurs, especially with rigged geometry.

Smooth Type selects the relaxation method:

Simple relaxes vertices toward their connected edge neighbors.

Length Weight applies distance-weighted relaxation, preserving shape better in some cases.

Vertex Group restricts the effect to a specific group, enabling selective, real-time smoothing via weight painting.

Only Smooth previews smoothing before correction applies, for comparison.

Pin Boundaries prevents boundary vertices from shifting.

Rest Source determines the reference vertex positions:

Original Coordinates uses the unmodified input positions, requiring the same vertex count in input and output.

Bind Coordinates optionally references a stored state, necessary when prior modifiers (Subdivision Surface, Mirror) add geometry.

## Laplacian Deform Modifier

The Laplacian Deform modifier poses a mesh while maintaining surface detail preservation.

The user marks certain vertices as "anchors," then moves some of them. The modifier keeps unmoved anchors fixed and recalculates all other vertices to preserve the original local geometry—curvature and surface direction based on neighbors.

This works using differential coordinates, which encode local shape information from each vertex and its neighbors.

An Anchors Vertex Group is required; without it the modifier has no effect.

Repeat sets iteration count to refine the solution. More iterations better preserve geometry but take longer. The algorithm seeks optimal rotation of differential coordinates to maintain details.

Anchor Weights specifies the vertex group controlling deformation. Only vertices with weight > 0 participate; their weight values do not affect behavior, only presence.

Invert reverses the group influence.

Bind instructs the modifier to capture the current surface geometry, so moving anchors changes the deformed shape.

Unbind, after binding, allows changing the Anchors Vertex Group. Rebinding is required after group modifications.

Error messages:

"Vertex group X is not valid" appears when the group is deleted or renamed.

"Vertices changed from X to Y" indicates vertex count changes.

"Edges changed from X to Y" indicates edge count changes.

"The system did not find a solution" means the solver failed.

For meshes exceeding 100,000 vertices, nonlinear optimization may fail.

Laplacian Surface Editing, developed by Olga Sorkine et al. in 2004, preserves details during editing operations. Differential coordinates express local shape as the difference between a vertex and the weighted average of its neighbors.

## Simple Deform Modifier

The Simple Deform modifier applies rotation (Twist, Bend) or scaling (Taper, Stretch) deformation to meshes, lattices, curves, surfaces, and text.

Deformation is calculated in local space; the object's local axes may differ from global axes. In the example above, global Z points up while local Z points at 45°.

A Deform axis (X, Y, or Z) specifies the deformation direction. The Limits field restricts influence to a portion of that axis. All distances are measured from the object origin; the vertices furthest from origin along the Deform axis define upper and lower bounds.

An external Deform object (typically an empty) can control the origin and local axis orientation.

Mode selects the deformation type. The examples show all four applied to text with origin at the left edge:

Twist rotates the mesh around the Deform axis. Each vertex is rotated around the origin based on its distance along that axis. For origins inside the object, this produces a twist. Below origin: negative rotation. Above origin: positive rotation. Vertices at the origin plane: no rotation. Rotation is weighted by vertex distance; furthest vertices experience maximum rotation, positive or negative.

Bend bends the mesh over the Deform axis. This is more complex. With Deform axis X or Y applied to a plane, no bending appears—the ambiguity of which perpendicular axis to bend around prevents automatic resolution. Setting Deform and Bending axes as opposite pairs (X with Z, Y with Z, Z with X) resolves this. For example, Deform axis X pairs with Bending axis Z; vertices with identical Z are not bent (at the origin). Bending increases with Z distance. Deform axis Z pairs with Bending axis X; rotation occurs along X coordinate—negative X rotates counterclockwise.

Taper scales linearly along the Deform axis. Scaling is weighted by origin distance; no scaling at the origin plane, maximum at the furthest vertices. This creates tapered shapes when the origin is interior.

Stretch stretches along the Deform axis. For interior origins, stretching resembles pulling rubber. Positive Factor makes the mesh longer in the Deform axis, wider at edges, thinner at origin. Negative Factor compresses, thickening the origin and thinning edges.

Angle (Twist & Bend) or Factor (Taper & Stretch) sets deformation magnitude. Negative values reverse it.

Axis, Origin specifies an object (typically an empty) defining the deformation origin and axis:

Rotation controls the Deform axis (the object's local axis becomes the deformation axis).

Translation controls the origin.

Scaling adjusts the deformation magnitude.

Limits sets the lower and upper deformation bounds on the Deform axis. Upper cannot be less than lower.

Lock (Twist, Taper, Stretch only) controls whether coordinates along the other two axes can change. For example, Stretching along Z can squash X without squashing Y by locking Y.

Vertex Group determines per-vertex influence, read from the Weight Paint map.

## Surface Deform Modifier

The Surface Deform modifier uses an arbitrary mesh surface to control deformation of another, transferring its motion to the target. This is useful for cloth-simulation proxies that drive the motion of more detailed, simulation-unsuitable meshes.

Target specifies the surface to bind (unavailable after binding).

Target Mesh Validity

The target mesh must satisfy constraints; violating them prevents successful binding:

No edges may have more than two adjacent faces.

Faces must be convex (not concave).

No overlapping vertices (doubles).

Faces must not have collinear edges.

Interpolation Falloff controls how much vertices bound to one target face are affected by surrounding faces (unavailable after binding). Low values smooth deformations but may introduce slight artifacts.

Strength sets the overall modifier influence.

Vertex Group enables per-vertex influence control.

Invert reverses the group influence.

Sparse Bind records bind data only for vertices with nonzero group weights at binding time—an optimization that requires rebinding if new vertices are added to the group.

Bind connects the modified mesh's current state to the target mesh's current state. Afterward, target mesh changes deform the modified mesh. Binding is necessary; an unbound modifier has no effect.

Unbind, available after binding, disassociates the modified mesh from the target and reverts the modified mesh to its pre-binding shape.

Note: meshes are bound using global coordinates, but later object transformations are ignored. Objects can be freely moved and rotated after binding without affecting behavior. Only changes to the target's geometry itself matter.

Note: if the mesh deviates significantly from the target surface, artifacts become likely. Reasonably well-matched meshes produce better results.

## Volume Displace Modifier

Volume Displace is available exclusively for Volume Objects.

The Volume Displace modifier shifts existing volume grids based on a 3D texture, using the RGB channels to displace into X, Y, and Z directions respectively.

Texture specifies the evaluated texture at every voxel.

Note: grayscale textures stretch along one axis. Color textures work better.

Strength controls displacement magnitude.

Sample Radius affects quality and performance—smaller values run faster but may clip the volume exterior. Keeping displaced volumes near their original position is important for performance.

Mid Level compensates when the texture causes a directional bias toward one side, allowing the displaced region to return to center.

## Edge Split Modifier

This modifier duplicates edges within a mesh, severing connectivity between faces and affecting normal generation at the split location, producing sharp-appearing edges. Manual shading control is possible by selecting which edges appear smooth or sharp; see Mesh Smoothing for alternatives.

Modern projects often use custom normals for the same result without topology changes; edge-splitting is kept for compatibility.

Edge Angle enabling splits edges when the angle between adjacent faces exceeds the Split Angle threshold; 0 splits all, 180 splits none.

Sharp Edges splits edges marked as sharp.

Non-manifold edges always split regardless of settings.

## Mask Modifier

This modifier hides vertices dynamically using vertex group selection.

Vertex Group mode hides all vertices outside the chosen group.

Armature mode (Pose Mode only) shows vertices in the group matching the active bone name; others hide.

Smooth blends the mask at group weight contours, creating gradual edges instead of sharp cutoffs.

Invert reverses the selection, showing only vertices outside the group.

Threshold hides vertices with weights at or below this value.

## Triangulate Modifier

### Triangulate Modifier

Apply the Triangulate modifier and each face of a mesh, whether a quad or an n-gon, gets cut into triangles. The result is identical to running the Triangulate tool from within Edit Mode.

| Mesh before Triangulate modifier. | Mesh after Triangulate modifier. |

### Options

The Triangulate modifier.

Quad Method

Beauty
Cuts the quads into tidy triangles; this is the slower route.

Fixed
Divides each quad across its 1st and 3rd vertices.

Fixed Alternate
Divides each quad across its 2nd and 4th vertices.

Shortest Diagonal
Cuts each quad along whichever diagonal is shorter.

Longest Diagonal
Cuts each quad along whichever diagonal is longer. For cloth simulations this is the mode to reach for.

N-gon Method

Beauty
Lays out the resulting triangles neatly; this is the slower route.

Clip
Breaks n-gons apart with an ear-clipping algorithm
(the same tessellation used to draw them in the viewport).

Minimum Vertices
The fewest vertices a face needs before it qualifies for triangulation.
Set it to 5, for instance, and quads are left alone
while only n-gons get triangulated.
