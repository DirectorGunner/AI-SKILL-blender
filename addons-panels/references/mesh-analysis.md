# Mesh Analysis, Vertex Groups Panel, Vertex Weights, Select All By Trait ...

> Blender Add-ons, Panels, and Properties reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Mesh Analysis; Vertex Groups Panel; Vertex Weights; Select All by Trait; Select Loops; Select Sharp Edges; Tool Settings; Relax; Rip; Layout Workflow; Metaball Structure; Curve Modifier.

## Mesh Analysis

### Mesh Analysis

Reference

Mode :

Edit Mode

Panel :

Header ‣ Overlays ‣ Mesh Analysis

Use mesh analysis to surface mesh attributes that could matter for particular workflows.

It runs in Edit Mode with Solid Viewport shading. High values come up red, low values blue, and anything beyond the chosen range turns gray. The modes available today are aimed mainly at 3D printing.

### Overhang

Because extrusion printers can only handle so much overhang before it fails, this mode visualizes overhang across an angle range with a selectable axis.

Minimum/Maximum
Low and high bounds of the angle shown.

Axis
The axis and direction the visualized angle is measured against.

Overhang.

### Thickness

Walls below a printer's minimum thickness won't come out, so this check casts rays over a distance range to gauge how thick the geometry is.

Minimum/Maximum
Low and high bounds of the thickness shown.

Samples
How many samples feed the thickness calculation.

Thickness.

### Intersections

Surfaces that cross one another are another frequent printing headache, since a model's inside and outside can no longer be told apart reliably.

This mode has no gradient; an element is either flagged or it isn't.

Intersecting faces.

### Distortion

Distorted geometry is a problem because there's no defined way to triangulate a distorted n-gon.

The measure is non-flatness: faces whose parts angle off in different directions.

Minimum/Maximum
Minimum/Maximum distortion to display.

Distorted Faces.

### Sharp Edges

As with thickness, sharp edges may produce features too thin to print.

Minimum/Maximum
Minimum/Maximum angle to display.

Sharp edges.

### Known Limitations

A couple of caveats apply to mesh analysis:

- At the moment it only shows up with Deform Modifiers.

- On high-poly meshes editing turns sluggish.

## Vertex Groups Panel

### Vertex Groups Panel

Reference

Mode :

All Modes

Panel :

Object Data tab ‣ Vertex Groups

The Vertex Group panel.

You manage vertex groups from the Object Data Properties, in the Vertex Groups panel.

Active Vertex Group
A List view.

Lock
Freezes the group against edits; only renaming or deletion remains.

Add Vertex Group
Makes an empty vertex group.

Remove Vertex Group
Drops the active vertex group.

Vertex Group Specials

Sort by Name
Orders the groups alphabetically.

Sort by Bone Hierarchy

Duplicate Vertex Group
Adds a copy of the active group as a new one. It takes the original's name with "_copy" tacked on, and references the very same vertices at the very same weights as the source.

Copy Vertex Group to Selected
Copies all vertex groups onto other selected objects as long as their indices line up (usually the case for plain deformed copies of the mesh that weren't otherwise edited).

Mirror Vertex Group
Mirrors the weights, flips the group names, or both. See Mirror Vertex Group for more information.

Mirror Vertex Group (Topology)
Runs Mirror Vertex Group with Topology Mirror turned on.

Remove from All Groups
Pulls the selected vertices out of every group, locked ones included, leaving them in none. (Not available for locked groups.)

Clear Active Group
Empties the active group of its vertices, though those vertices may remain in the object's other groups. (Not available for locked groups.)

Delete All Unlocked Groups
Wipes every unlocked group from the object.

Delete All Groups
Wipes every group from the object.

Lock All
Locks all groups.

Unlock All
Unlocks all groups.

Lock Invert All
Flips each group's lock.

### Editing Vertex Groups

Reference

Mode :

Edit Mode

Panel :

Object Data tab ‣ Vertex Groups

Menu :

Vertex ‣ Vertex Groups

Shortcut :

Ctrl - G

Vertex Group panel in Edit or Weight Paint Mode.

Switch into Edit Mode or Weight Paint Mode and vertex weights open up for editing. The same actions live in the 3D Viewport's Vertex ‣ Vertex Groups menu or under Ctrl - G .

Assign
Binds the selected vertices into the active group at the weight set in Weight (see below).

Remove
Drops the selected vertices from the active group, discarding their weights along with them.

Select
Selects every vertex in the group.

Deselect
Deselects every vertex in the group.

Weight
The weight handed to the selected vertices.

Auto Normalize
Keeps all bone-deforming groups summing to 1.0 as you paint or assign weights.

## Vertex Weights

### Vertex Weights

Reference

Mode :

Edit and Weight Paint Modes

Panel :

Sidebar region ‣ Vertex Weights

Vertex Weights panel.

For every vertex it holds, a vertex group records a weight between 0 and 1. A group can span many vertices, and any vertex may appear in many groups.

Sitting in the 3D Viewport's Sidebar, the Vertex Weights panel lists the groups the active vertex belongs to and lets you view and change those weights. It's there in Edit Mode, and in Weight Paint Mode whenever the header has Vertex Selection turned on.

### Vertex Group Categories

Every vertex group is the same thing under the hood, yet by how they're used we can split them in two:

Deform Groups
Sometimes called a "weight group" or "weight map," this kind ties certain vertices to a given bone in the Armature, deciding which stretch of mesh moves as that bone does.

Other Groups
Everything else, put to work with shape keys, modifiers, and so on.

The deform groups are linked: a vertex's deform weights usually have to total 1. That's why the filter buttons atop the panel can narrow the view to just these groups, or hide them.

### Weight Table

The Weight Table lists all weights on the active vertex , the one selected most recently (and shown in white). With no active vertex, or one outside every group, the panel doesn't appear.

### Set the Active Group

Click a vertex group's name to make it active.

Changing the active vertex group.

### Display Weights in Edit Mode

Enable display of weights in Edit Mode.

While in Edit Mode you can paint the active group's weights onto the mesh: pop open the Mesh Edit Mode Overlays popover and tick Vertex Group Weights .

Weights in Edit Mode.

### Change a Weight

To edit a group's weight, click the number and type a fresh value, or drag left and right with LMB . The arrows that surface on hover nudge it by 0.01 at a time.

Changing a weight value.

### Copy a Weight

Paste Weight to Selected pushes the active vertex's weight onto the other selected vertices. Despite the "paste" label, it has nothing to do with the Copy button and never touches the clipboard.

Copying a weight.

### Delete a Weight

Delete Weight drops the active vertex from the group, and its row vanishes from the list.

Deleting a weight.

### Operators

Vertex weight operators.

Normalize
Rescales the active vertex's weights to sum to 1.0 while keeping them in the same proportion to one another.

Copy
Pushes every weight on the active vertex onto the rest of the selected vertices.

Tip

Either tool acts only on the vertex groups passing the current filter.

### Locking

Locked vertex group.

Lock a vertex group and its weights freeze, with the copy and normalize buttons going dim.

Tip

Normalize and Copy gray out only when the current list holds a locked group. So if, say, just the non-deforming groups are locked, flip to the Deform filter and normalize from there.

## Select All by Trait

### Select All by Trait

### Non Manifold

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select All by Trait ‣ Non Manifold

Selects a mesh's non-manifold geometry. Only the Vertex and Edge selection modes offer this entry.

### Options

Extend
Adds to what's selected rather than replacing it.

Wire
Edges attached to no face.

Boundaries
Edges along boundaries and holes.

Multiple Faces
Edges shared by three or more faces.

Non Contiguous
Edges on exactly two faces whose normals oppose each other.

Vertices
Isolated vertices, those on a Wire or Multiple Faces edge, or the lone vertex bridging two faces.

### Loose Geometry

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select All by Trait ‣ Loose Geometry

According to the selection mode, this picks out vertices in no edge, edges in no face, or faces sharing an edge with no other face.

### Interior Faces

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select All by Trait ‣ Interior Faces

Catches faces that may have been created inside the mesh by accident rather than on its surface. To be exact, it grabs faces with "abnormal" neighbors (several neighbors meeting at one edge), plus the "normal" neighbors of those faces.

### Faces by Sides

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select All by Trait ‣ Faces by Sides

Picks every face with a given edge count, which you set in the Adjust Last Operation panel.

### Poles by Count

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select All by Trait ‣ Poles by Count

Hunts down poles, those vertices wired to an odd number of edges, and then selects the poles themselves (vertex mode) or the edges and faces around them (edge/face mode).

| Before selecting poles.  | After selecting poles.  |

### Options

Pole Count
The edge count a vertex must (or must not) hit to register as a pole.

Type
The comparison that decides what counts as a pole:

Less Than :

Vertices with fewer than Pole Count edges.

Equal To :

Vertices with exactly Pole Count edges.

Greater Than :

Vertices with more than Pole Count edges.

Not Equal To :

Vertices whose edge count differs from Pole Count .

Extend
Adds to what's selected rather than replacing it.

Exclude Non Manifold
Leaves out poles sitting in non-manifold geometry.

Hint

Since poles can cause ugly pinching under the Subdivision Surface Modifier, this operator is handy for hunting them down.

### Ungrouped Vertices

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select All by Trait ‣ Ungrouped Vertices

Selects all vertices that are not part of any vertex group.

## Select Loops

### Select Loops

### Select Edge Loops

Reference

Mode :

Edit Mode (Vertex or Edge select mode)

Menu :

Select ‣ Select Loops ‣ Edge Loops

Shortcut :

Alt - LMB or Shift - Alt - LMB

Alt - LMB on an edge sweeps up the edges that run on from it along a topologically straight line. Add Shift - Alt - LMB to extend the current selection instead of replacing it.

That chain of edges is called an edge loop in Blender terms, since it usually closes into a loop around the mesh, though as shown below it needn't.

Selecting edge loops. The clicked edge is highlighted in green.

Hint

Clicking edges to pick edge loops works in Vertex selection mode too.

Note

With Emulate 3 Button Mouse on, Alt - LMB stops working because it stands in for MMB . Double-click LMB instead to pick edge loops.

### All Boundaries

Run edge-loop selection on a boundary edge a second time and the entire boundary is selected.

First and second edge loop selection.

See also Select Boundary Loop.

### Select Face Loops

Reference

Mode :

Edit Mode (Face select mode)

Shortcut :

Alt - LMB or Shift - Alt - LMB

In Face mode, Alt - LMB on an edge selects the row of faces running perpendicular to it. Use Shift - Alt - LMB to add to the previous selection rather than replace it.

That row of faces is called a face loop in Blender terms, since it usually closes into a loop around the mesh, though as shown below it needn't.

Selecting face loops. The clicked edge is highlighted in green.

From Vertex selection mode, Select Edge Rings gets you the same result.

Note

With Emulate 3 Button Mouse on, Alt - LMB stops working because it stands in for MMB . Double-click the edge with LMB instead to pick face loops.

### Select Edge Rings

Reference

Mode :

Edit Mode (Edge select mode)

Menu :

Select ‣ Select Loops ‣ Edge Rings

Shortcut :

Ctrl - Alt - LMB or Shift - Ctrl - Alt - LMB

Ctrl - Alt - LMB on an edge also grabs the parallel edges in the face row perpendicular to it. Use Shift - Ctrl - Alt - LMB to add to the previous selection rather than replace it.

That set of edges is called an edge ring in Blender terms, since it usually closes into a ring around the mesh, though as shown below it needn't.

Selecting edge rings in Edge mode. The clicked edge is highlighted in green.

The shortcut works in Vertex mode too, but yields a face loop selection instead:

Selecting edge rings in Vertex mode.

Hint

To turn an edge ring selection into a face loop, either switch to Vertex mode or switch to Face mode while holding Ctrl (see Expand/Contract Selection).

### Select Loop Inner-Region

Reference

Mode :

Edit Mode (Edge select mode)

Menu :

Select ‣ Select Loops ‣ Select Loop Inner-Region

Selects every face sitting inside a selected, closed loop of edges. It can be run in Vertex and Face modes, but the results may surprise you.

Note that if the selected edges do not form a closed loop, all connected faces will be selected.

### Options

Select Bigger
Select the faces outside the edge loop instead of those inside it.

### Examples

Single edge loop to region.

Multiple edge loops.

Holes are also supported.

### Select Boundary Loop

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select Loops ‣ Select Boundary Loop

Swaps the current face selection for an edge selection tracing the border of each face "island." It's basically the inverse of Select Loop Inner-Region.

You can run it in any selection mode. Run in Face mode, it switches to Edge mode by itself.

Before and after running Select Boundary Loop.

## Select Sharp Edges

### Select Sharp Edges

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select Sharp Edges

Adds edges at sharp corners to the selection.

Note

This tool doesn't handle edges you marked Sharp by hand. To grab those, manually select one Sharp edge first, then run Select ‣ Select Similar ‣ Sharpness to pull in the rest.

### Options

Sharpness
The least angle at which an edge between two faces counts as sharp. Because it's read off the face normals, coplanar faces sit at 0° (not 180°), and the sharper the corner the larger the angle (not the smaller).

## Tool Settings

Edit Mode Tool Options

Transform Options

Correct Face Attributes
Adjusts geometry properties like UVs and color values during transforms.

Keep Connected
When Correct Face Attributes is active, merges attributes linked to the same vertex.

Keeping UVs connected suits organic modeling but not architectural work.

Mirror Transformations

Mirror options enable symmetric transformation of vertices, edges, or faces along a chosen axis. When one element is transformed, its mirrored counterpart (in local space) moves correspondingly, preserving symmetry.

Mirrored vertices must align precisely. Imprecise alignment prevents Mirror from recognizing the pair.

The Mirror Modifier offers an alternative for automatic symmetry handling.

Topology Mirror

This feature identifies mirrored vertices by analyzing mesh relationships rather than relying solely on position. By considering the overall topology, non-symmetrical vertices can be treated as mirrored pairs.

Requires at least one Mirror Axis enabled.

Topology Mirror works best with detailed geometry. Simple meshes (cubes, UV spheres) may yield inconsistent results.

Example Workflow

Create a new scene and delete the default cube. Add a Monkey object.

Press Tab to enter Edit Mode.

Disable Mirror axes and move one vertex slightly.

Enable X Axis Mirror without Topology Mirror. Move the same vertex again — X Axis Mirror won't affect other vertices since they're not perfectly aligned.

Enable Topology Mirror and move the same vertex once more. X Axis Mirror now mirrors the other vertex despite imperfect positioning.

Auto Merge

Mode: Edit Mode
Menu: Sidebar ‣ Tool ‣ Options ‣ Auto Merge

When vertices move closer than the Threshold distance, they automatically merge. This applies to interactive operations only (including Adjust Last Operation tweaks). If multiple vertices occupy the exact target location, the moved vertex merges with one of them.

Split Edges & Faces
Detects edge intersections from transforms, creating vertices at intersection points and splitting the edge and any containing face.

Threshold
Maximum distance between vertices before merging occurs.

UV Options

Live Unwrap
Recalculates UV unwrapping each time a seam property changes on an edge. This differs from the Live Unwrap option in the UV Editor.

## Relax

Relax

Mode: Edit Mode
Toolbar: Relax

The Relax tool distributes UVs more evenly by pulling vertices along UV edges to balance the unwrap.

Relax works similarly to Minimize Stretch (which operates on faces to reduce distortion) but uses a different approach. Sometimes Minimize Stretch performs better, sometimes the unwrap tool, and sometimes Relax. A common workflow uses Unwrap first, then Minimize Stretch, then touches up with Relax. Undo can restore any earlier state.

Tool Settings

Size
Controls the brush radius in pixels. Press F to interactively adjust by dragging and LMB to confirm. Type a number then enter during F to set numerically.

Strength
Controls the brush intensity. Press Shift - F to interactively adjust strength, then LMB to confirm. You can also enter numerically while in Shift - F mode.

Falloff
Controls the Strength falloff from brush center to borders. Adjust the curve shape for softer or harder effects. See Curve Widget documentation.

Curve Preset

Custom — Manually adjust curve control points or select a preset as a starting point.

Smooth — Center, border, and transition strength are evenly distributed.

Smoother — Similar to Smooth with a wider center point before tapering.

Sphere — Strength concentrates at center with steep border falloff.

Root — Similar to Sphere with a more concentrated center.

Sharp — Strongest at center, exponentially tapering to a fine point.

Linear — Center is strongest; strength consistently weakens toward borders.

Sharper — Similar to Sharp with a more condensed center.

Inverse Square — Hybrid between Smooth and Sphere.

Constant — Strength unified across the entire brush, creating a sharp border edge.

Options

Lock Borders
Locks the UV island boundary from brush effects.

Sculpt All Islands
Edits all islands, not just the island nearest the brush center at stroke start.

Method

How edge weighting is determined:

Laplacian — The classic discrete Laplace operator on the UV graph. Each edge has equal weighting, producing triangles resembling a honeycomb or quads in a square grid.

HC — Similar to Laplacian with equal weighting while preserving gradients between dense and sparse mesh regions. Uses the Humphrey's Classes operator (from "Improved Laplacian Smoothing of Noisy Surface Meshes").

Geometry — Edges weight according to the discrete Laplace operator (cotangent formula) on 3D geometry. This brings UV edge lengths closer to 3D edge lengths, resulting in less distortion across boundaries.

## Rip

Rip

Toolbar: Rip

The Rip tool interactively separates selected UV elements (vertices, edges, faces) from connected parts, creating a rip. After separation, elements can move in the mouse direction for interactive repositioning.

This isolates UV islands or unwraps overlapping elements without affecting surrounding geometry.

Two images show before and after states.

Note: The Rip tool is incompatible with Sync Selection. Disable Sync Selection in the UV Editor to use this tool.

See also: UV Rip Move Operator (operator version) and Mesh editing Rip (3D Viewport equivalent).

## Layout Workflow

When unwrapping a complete model at once, the result often appears disorganized. Dense areas like facial structure may compress heavily, while appendages like necks and ears stretch disproportionately. Rather than correcting an unwrap manually, re-unwrapping the model in segments using appropriate projection methods typically yields better results.

Separate the visible head region—excluding eye details, ear protrusions, and neck—and apply Sphere Projection to it. For the ear section, align the viewport directly to its surface and use Project from View. The UV coordinates for already-unwrapped parts remain stored; if the editor shows only current selections, toggle Sync Selection to display all islands.

Unwrap the neck using Cylinder Projection. As an alternative workflow, use Seams to delineate cut boundaries around protruding features, then run Unwrap once to map all sections simultaneously.

After unwrapping separate pieces, individual UV islands often overlap. To remediate this: select a single vertex and press Ctrl-L to select its topologically connected region (or hover and press L, or switch to Island mode). Once selected, scale and reposition the island away from others. Alternatively, use Pack Islands to have the system arrange them automatically.

Consolidate separate islands by translating and scaling them to fit together, then merge them using either Merge or (preferably) Stitch operations.

Once basic unwrapping is done, manual adjustments often improve results. Scaling up a region allocates more texture resolution to it, enabling finer detail. The Minimize Stretch tool helps correct excessive distortion between the 2D UV layout and its corresponding 3D surface.

A single geometry can hold multiple UV layers, each assigning different coordinates to the same vertices. This enables separate maps for color textures and for pre-computed shading information.

UV maps can be transferred between geometries in various ways. For identical topologies with differing vertex locations, use Copy UV Maps. For approximately matching surfaces with different topology, apply Transfer Mesh Data.

## Metaball Structure

A meta object is formally described as a directing structure that generates a static field—either positive or negative, causing neighboring structures to attract or repel.

The implicit surface emerges where this 3D field reaches a specific value. A ball meta, whose directing structure is a point, produces an isotropic field (uniform in all directions), so surfaces of constant field value form concentric spheres around that point.

Metas are mathematical expressions performing logical and arithmetic operations—AND, OR, addition, subtraction. This approach is called Constructive Solid Geometry. CSG uses minimal memory but demands significant computation.

Edit Mode allows changing the underlying structure type from the Active Element panel or the Sidebar Transform panel.

Ball (point structure) produces the simplest meta with no extra settings. The point generates an isotropic field, yielding a spherical surface.

Capsule (line-segment structure) is shaped by the field of a finite line segment, producing a cylinder with hemispherical ends.

Size X sets the line length (and capsule length).

Plane (rectangular structure) is shaped by the field of a rectangular plane, creating a box-like surface with uniform thickness and rounded borders.

Size X/Y specifies the rectangle width and height.

Ellipsoid (ellipsoid-volume structure) is shaped by an ellipsoid's field, yielding an ellipsoid surface.

Size X/Y/Z sets the ellipsoid dimensions.

Cube (cubic-volume structure) is shaped by a cubic volume's field, creating a box with rounded edges.

Size X/Y/Z specifies the cube dimensions.

## Curve Modifier

The Curve modifier bends a mesh, curve, surface, or lattice along a path, deforming it as if following a rail.

The modifier works along a dominant axis (X, Y, or Z, selectable). Moving the object along the dominant direction (default X) travels the object along the curve. Moving perpendicular to it shifts the object toward or away from the path.

Beyond the curve's endpoints, deformation continues based on the direction vector at those ends.

The modifier uses global space, so actual geometry position relative to the curve matters. Position the object origin at its geometry center (use Set Origin to Geometry if needed) and align the object's origin with the curve's origin initially (use snap tools).

If the curve is 3D, Tilt values on control points twist the deformed object. The Radius property scales it. These settings are in the Curve panel under Path/Curve-Deform.

Curve Object specifies the path to follow.

Deformation Axis selects which direction the object travels (X, Y, Z, or their negatives).

Vertex Group restricts the effect to a specific group.

Invert reverses the group effect.
