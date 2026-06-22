# Subdivide, Subdivide Edge Ring, Extrude Faces, Extrude Faces Along Normals ...

> Blender Add-ons, Panels, and Properties reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Subdivide; Subdivide Edge-Ring; Extrude Faces; Extrude Faces Along Normals; Face Data; Grid Fill; Inset Faces; Intersect (Boolean); Solidify Faces; Weld Edges into Faces; Convex Hull; Merge; Mirror.

## Subdivide

### Subdivide 

Reference

Mode :

Edit Mode

Menu :

Edge ‣ Subdivide

Boosts mesh resolution by chopping faces or edges into smaller pieces.

What happens depends on the selection, following a handful of rules:

- With just one edge of a triangle or quad selected, that face becomes a quad or N-gon
respectively. Disable Create N-Gons and the face splits into triangles instead.

- With two edges of a face selected:

- On a triangle, a fresh edge joins the two new vertices, breaking the triangle into a triangle
and a quad.

- On a quad whose selected edges are neighbors, the split follows the Quad Corner Type setting
(see below).

- On a quad whose selected edges are opposite, an edge connecting the two new vertices simply
divides it into two quads.

- With three edges of a face selected:

- On a triangle, the whole face is effectively selected, so it splits into four smaller
triangles.

- On a quad, the two opposite edges subdivide as above first; then the "middle" edge subdivides,
treating its new "sub-quad" the way a single-edge case is treated.

- With all four edges of a quad selected, the face splits into four smaller quads.

- With one or more edges of an N-gon selected, those edges subdivide individually while the
face itself stays whole.

### Options 

These options are available in the Adjust Last Operation panel after
running the operator:

Number of Cuts
How many cuts to make per edge. The default of 1 halves each edge; 2 thirds it, and onward.

Smoothness
Nudges the subdivisions to approximate curvature, producing an effect akin to how the
Subdivision Surface Modifier might reshape the mesh.

| Mesh before subdividing.  | Subdivided with no smoothing.  | Subdivided with Smoothness set to 1.  |

Create N-Gons
Uncheck to force the result into triangles or quads rather than n-gons (see examples below).

Quad Corner Type
Governs how quads split when two neighboring edges are selected.

Inner Vertices
The selected edges subdivide; an edge then bridges the two new vertices to form a small triangle;
that edge subdivides as well, and its resulting "inner vertex" links by a further edge to the
vertex opposite the originally selected edges. The outcome is a triangle plus two quads.

Path
The selected edges subdivide, after which new edges connect the new vertices and the existing
outer vertices, giving two triangles and a quad.

Straight Cut
The selected edges subdivide, then an edge across the two new vertices forms a small triangle and
an N-gon. With Create N-Gons off, this behaves like Inner Vertices instead.

Fan
The quad splits into a fan made of one quad and two triangles, all sharing the vertex opposite
the selected edges.

| Inner Vertices corner type.  | Path corner type.  | Straight Cut corner type.  | Fan corner type.  |

Fractal
Throws the vertices in random directions once the mesh has been subdivided.

| Plane before subdivision.  | Regular subdivision.  | Same mesh with fractal added.  |

Along Normal
Confines that vertex movement to the normals rather than random directions.

Along Normal set to 1. 

Random Seed
Swaps the seed feeding the Fractal noise, so each value yields a different outcome.

Same mesh with a different seed value. 

See also

Randomize randomly displaces vertices without
subdividing first.

### Examples 

Some scenarios illustrating edge subdivision appear below.

The sample mesh. 

### One Edge 

| One edge.  | Create N-Gons unchecked.  |

### Two Tri Edges 

| Two tri edges.  | Create N-Gons unchecked.  |

### Two Opposite Quad Edges 

| Two quad edges.  | Create N-Gons unchecked.  |

### Two Adjacent Quad Edges 

| Inner Vertices corner type.  | Create N-Gons unchecked.  |

| Path corner type.  | Create N-Gons unchecked.  |

| Straight Cut corner type.  | Create N-Gons unchecked.  |

| Fan cut type.  | Create N-Gons unchecked.  |

### Three Quad Edges 

| Three edges.  | Create N-Gons unchecked.  |

### Full Triangle 

| Full triangle.  | Create N-Gons unchecked.  |

### Full Quad 

| Full quad.  | Create N-Gons unchecked.  |

### Multiple Cuts 

| Triangle with two cuts.  | Quad with two cuts.  |

## Subdivide Edge-Ring

### Subdivide Edge-Ring 

Reference

Mode :

Edit Mode

Panel :

Edge ‣ Subdivide Edge-Ring

Cuts an edge ring into more loops, with interpolation if you want it.

Note

To Blender, an edge ring is any run of edges lying across a strip of joined faces and running
crosswise to that strip. The strip may close into a loop, but needn't — a "ribbon" counts just as
well as a "ring."

See also Select Edge Rings.

### Options 

Number of Cuts
The number of edge loops to create along the edge ring.

Interpolation
How to place the new edge loops.

Linear
Place the new edge loops in a straight line.

Blend Path
Lays the new loops along a Bézier spline, ignoring the surrounding surface entirely.

Blend Surface
Lays the new loop vertices along Bézier splines while accounting for the normals of the
surrounding surface.

| Before subdividing  | Linear  | Blend Path  | Blend Surface  |

Smoothness
Controls smoothness for the Blend Path and Blend Surface interpolations. At 1 you get full Bézier
splines; at 0 the result is effectively Linear .

Profile Factor
Strength of the Profile Shape . Go negative to pinch the ring's middle inward, positive to bulge
it outward.

Profile Shape
How the ring's thickness varies between its middle and its ends.
See the Proportional Editing page
for a description of each option.

## Extrude Faces

### Extrude Faces 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Extrude Faces ,
Mesh ‣ Extrude ‣ Extrude Faces

Shortcut :

E

This builds new faces around the edge of your selection, then lets you drag the selected faces
along an axis with the cursor. The result is an extrusion — a square turns into a box, a disc into
a cylinder, and so on. Modeling leans on it constantly, for adding limbs to characters, branches
to trees, and the like.

When the faces sit where you want them, press LMB or Return to confirm. RMB or Esc cancels the
move and returns the selected faces to where they began, though the new faces remain.

The extrusion axis defaults to the average of the face normals, but you can override this
Axis Locking by tapping an axis key ( X , Y , or Z ):

- Press once to use the corresponding global axis.

- Press twice to use the average of the faces' local axes.

- Press three times to disable axis locking (allows moving the faces anywhere).

| Selected face.  | During extrude.  | Using the global Z axis.  |

Once extruded, the Adjust Last Operation panel exposes these options:

Flip Normals
Reverses the normals on the new faces, since they can wind up backward depending on which way you
extruded. Check them against the 3D Viewport's Face Orientation overlay.

Dissolve Orthogonal Edges
Turn this on and new faces merge into adjacent existing ones — possibly forming n-gons — wherever
they make up a flat surface together.

Orientation
Determines the extrusion axis to use.

Mirror Editing
This shifts the matching faces on the mesh's other half without extruding them, so it's of little
use here.

Proportional Editing
This drags the surrounding unselected faces along with the extruded ones, so it's of little use
here.

## Extrude Faces Along Normals

### Extrude Faces Along Normals 

Reference

Mode :

Edit Mode

Tool :

Toolbar ‣ Extrude Along Normals

Menu :

Face ‣ Extrude Faces Along Normals ,
Mesh ‣ Extrude ‣ Extrude Faces Along Normals

This works much like Extrude Faces, except every vertex travels along its own normal instead of
all of them following one shared axis. So pushing outward on a convex surface enlarges the faces,
for example.

| Before extrusion  | Regular extrusion  | Extrusion along normals  |

Once extruded, the Adjust Last Operation panel exposes these options:

Flip Normals
Reverses the normals on the new faces, since they can wind up backward depending on which way you
extruded. Check them against the 3D Viewport's Face Orientation overlay.

Dissolve Orthogonal Edges
Turn this on and new faces merge into adjacent existing ones — possibly forming n-gons — wherever
they make up a flat surface together.

Offset
Distance to move the vertices.

Offset Even
Disabled, each vertex moves the same distance. Enabled, each face moves the same distance instead.

You can also flip this mid-extrusion by pressing S or holding Alt . (Those shortcuts show in the
status bar.)

| Before extrusion  | Offset Even off (default)  | Offset Even on  |

Mirror Editing
This shifts the matching vertices on the mesh's other half without extruding any faces, so it's
of little use here.

Proportional Editing
This also drags the surrounding unselected vertices along their normals, so it's of little use
for extrusion.

See also

Shrink/Fatten for moving vertices along their
normal without extruding.

## Face Data

### Face Data 

### Rotate Colors 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Face Data ‣ Rotate Colors

Within each selected face, cycles the active
Color Attribute
clockwise or counterclockwise.

### Reverse Colors 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Face Data ‣ Reverse Colors

Within each selected face, mirrors the active Color Attribute .

### Rotate UVs 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Face Data ‣ Rotate UVs

See Rotate UVs.

### Reverse UVs 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Face Data ‣ Reverse UVs

See Reverse UVs.

### Flip Quad Tessellation 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Face Data ‣ Flip Quad Tessellation

Behind the scenes each quad is split into two triangles. This operator reverses that split's
direction on the selected quads.

See also

Rotate Edge

### Mark/Clear Freestyle Face 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Face Data ‣ Mark/Clear Freestyle Face

Flags or unflags the selected faces as needing special Freestyle treatment.
See Face Marks.

## Grid Fill

### Grid Fill 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Grid Fill

Produces a grid of quads. It accepts two kinds of input:

- A roughly rectangular loop of edges — or just two opposite sides of one — gets a grid filled
inside it.

- A roughly rectangular patch of faces gets a grid generated in its place.

| Input.  | Grid Fill result.  |

Results come out best when each pair of opposite sides carries the same vertex count, though
that's not mandatory.

### Options 

Span
How many columns the grid gets. (Row count follows from this on its own.)

Offset
Picks which vertex serves as the grid's first corner. It's the active vertex by default; use it to
spin the grid's layout around.

Simple Blending
Switches to a plainer interpolation for building the grid — a better choice on flat surfaces, or
anywhere preserving curvature looks wrong.

Tip

Blender may give an error such as "Loops are not connected by wire/boundary edges." The "loops" here
can be confusing as it is Blender terminology for "chains," not "closed loops." As such, this error
really means "The selected edge chains are not connected to each other; please create more edges
to form a closed loop."

See also

Bridge Edge Loops

## Inset Faces

### Inset Faces 

Reference

Mode :

Edit Mode

Tool :

Toolbar ‣ Inset Faces

Menu :

Face ‣ Inset Faces

Shortcut :

I

This rings the selected faces with a border of faces, then lets you set that border's thickness
by dragging the cursor. As the border fattens, the outermost selected faces thin out while the
inner ones hold their size.

You can also change the inset's depth mid-operation by holding Ctrl . As with Extrude Faces Along
Normals, this slides each selected vertex along its normal and may resize every face.

When the inset looks right, press LMB or Return to confirm. RMB or Esc cancels it.

| Faces selected.  | First inset using only Thickness.  | Second inset using only Depth.  |

Several disjoint "patches" of faces can also be inset at once.

### Options 

Inset operator options. 

The shortcuts below work while insetting and also appear in the status bar.

Boundary B
Also build border faces along boundary edges — those belonging to one face rather than two.

Offset Even
Keeps the border an even width along the edges. Switch it off and the width is even at the
corners instead.

| Offset Even enabled (default).  | Offset Even disabled.  |

Offset Relative
Scales each border vertex's Thickness and Depth offset by the mean length of its two neighboring
border edges.

Edge Rail
Snaps the new edges between border faces onto the existing edges between the inset faces.

| Edge Rail disabled.  | Edge Rail enabled.  |

Thickness
How wide the fresh border faces come out.

Depth Ctrl
How far up or down the inset faces shift.

Outset O
Grows the new border outward rather than inward.

Select Outer
Moves the selection onto the freshly made border faces.

Individual I
Insets each face on its own, instead of treating a connected patch as a single unit.

Interpolate
Carries mesh data — UVs, Color Attributes, vertex group weights, and so on — over to the new
border vertices.

## Intersect (Boolean)

### Intersect (Boolean) 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Intersect (Boolean)

Runs Boolean operations between your selected geometry and the unselected geometry.

Selecting a sphere and performing an Intersection, Union, and Difference
with a cube. 

Tip

Hide geometry by pressing H to exclude it from the operation,
then Alt - H afterwards to unhide it again.

See also

The Boolean Modifier can perform these same operations
non-destructively between different mesh objects.

The Adjust Last Operation panel offers the following options:

Boolean Operation

Intersect :

Keep only the volume sitting inside both the selected and unselected geometry.

Union :

Strip out the interior faces between the selected and unselected geometry.

Difference :

Carve the selected geometry out of the unselected, then discard the selected geometry.

Solver
Algorithm used to perform the Boolean operation.

Float :

A lightweight solver — fast, but with no support for overlapping geometry.

Merge Threshold
How close two faces must be to count as touching. Raising it can help when intersections that
ought to register don't, or when stray geometry appears because edges aren't read as overlapping.

Warning

A threshold approaching the size of faces may cause very slow calculation.
In general, keep this value small.

Exact :

A heavier solver — slowest of the two, but it gives the best results and fully supports
overlapping geometry.

Swap
With Difference , this carves the unselected geometry out of the selected geometry rather than the
reverse.

Self Intersection
Handles self-intersection in the participating geometry properly, trading away some performance.

## Solidify Faces

### Solidify Faces 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Solidify Faces

Extrudes the selected faces so they go from an infinitely thin sheet to a solid mesh with real
volume.

Tune the thickness in the Adjust Last Operation panel:

Thickness
How far to offset the new surface. Positive values push inward relative to the face normals;
negative values push outward.

| Mesh before solidifying.  | Solidify with a positive thickness.  | Solidify with a negative thickness.  |

See also

The Solidify Modifier does this non-destructively
and has many more options.

## Weld Edges into Faces

### Weld Edges into Faces 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Weld Edges into Faces

Cuts the selected faces apart along any selected wire edges — edges belonging to no face — that
share their vertices. Those wire edges then become part of the resulting faces.

| Selecting a quad face and a wire edge.  | Welding splits the quad into two triangles.  |

See also

Instead of creating edges and then running this operator, it may be easier to use
Connect Vertex Path or the
Knife Topology Tool to split the faces directly.

## Convex Hull

### Convex Hull 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Convex Hull

Wraps the selected vertices in a convex hull. Original edges and faces lying on that hull may get
reused.

This operator also works as a stand-in for Bridge Edge Loops.

Input mesh, loose vertices, and Convex Hull result for both. 

### Options 

Delete Unused
Clears out vertices, edges, and faces that were selected but didn't end up in the hull. Note that
anything used by other, unselected edges and faces survives.

Use Existing Faces
Reuse existing faces lying on the hull where it can, which lets the hull hold n-gons rather than
only triangles and quads.

Make Holes
Delete the edges and faces that got reused — handy when bridging, to clear faces between the
existing mesh and the hull.

Join Triangles
The hull starts out as pure triangles; this option attempts to fuse them into quads. It carries
all the same controls as the Triangles to Quads operator (angle limit, compare UVs, etc.).

Max Face Angle, Max Shape Angle, Compare
See Triangles to Quads.

## Merge

### Merge 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Merge ,
Context Menu ‣ Merge

Shortcut :

M

Fuses the selected vertices together. The menu lists:

At Center
Fuse every selected vertex into one at their geometric center — the average of their positions,
not the bounding-box center.

At Cursor
Fuse every selected vertex into one sitting at the 3D Cursor.

Collapse
Fuse each island of connected vertices into one at that island's average position.

At First
Fuse every selected vertex into whichever was picked first. Vertex selection mode only.

At Last
Fuse every selected vertex into whichever was picked last. Vertex selection mode only.

By Distance
Fuse each cluster of vertices closer together than a set distance.

Note

At First and At Last hinge on selection order, which is easily lost (for example by switching
selection mode). Run them right after making the selection as a rule.

See also

The Weld Modifier merges vertices by distance non-destructively.

### Options 

After merging, the following options are available in the Adjust Last Operation panel:

Type
The type of merge to perform.

UVs
Corrects the UV coordinates to avoid texture distortion.

Merge By Distance instead has the following options:

Merge Distance
Vertices nearer to each other than this get fused.

Centroid Merge
Set each new vertex at the average position of the vertices fused together. Off, it uses the
position of whichever original vertex sat nearest that average.

Unselected
Allow merging selected vertices with unselected ones.

Sharp Edges
On a smooth-shaded mesh carrying custom split normals, this adds edge marks where needed so sharp
edges stay sharp through the merge.

## Mirror

### Mirror 

### Interactive Mirror 

Reference

Mode :

Object and Edit Modes

Menu :

Object/Mesh/Curves ‣ Mirror ‣ Interactive Mirror

Shortcut :

Ctrl - M

The Mirror operator flips the chosen elements about the Pivot Point along an axis of the
Transformation Orientation. It amounts to scaling the selection by -1 along that axis, only it
gives you a quicker, more direct workflow.

Hint

After mirroring a mesh, the face normals tend to get flipped inside out
(see the Face Orientation overlay).
The Flip Normals operator can fix this.

See also

- The Symmetrize operator creates a mirrored
copy of the mesh.

- The Mirror Modifier creates a mirrored copy that's
automatically kept up to date.

### Usage 

- Place the pivot point at the desired mirror location.

- When not mirroring along a global axis, ensure the transform orientation has an axis
pointing along the desired mirror direction (perpendicular to the mirror plane).

- Press Ctrl - M to activate the Mirror operator.

- Choose an axis by dragging with MMB or by pressing X , Y , or Z .
(The chosen axis is shown at the top of the 3D Viewport.) Press an axis key a second
time to toggle between the transform orientation axis and the global axis.

- Press LMB or Return to confirm, or RMB or Esc to cancel.

### Options 

Orientation
The transform orientation to take the Constraint Axis from.

Constraint Axis
Which axis or axes to mirror across. Mirroring across X, for instance, flips the selection
horizontally.

### X/Y/Z Global 

Reference

Mode :

Object and Edit Modes

Menu :

Object/Mesh/Curves ‣ Mirror ‣ X/Y/Z Global

These run a non-interactive mirror along the global X, Y, or Z axis.

### X/Y/Z Local 

Reference

Mode :

Object and Edit Modes

Menu :

Object/Mesh/Curves ‣ Mirror ‣ X/Y/Z Local

These run a non-interactive mirror along the object's local X, Y, or Z axis.

### Examples 

Mirroring along the global X axis around the object origin:

| Mesh before mirroring.  | Mesh after mirroring.  |

Mirroring around the 3D Cursor:

| Mesh before mirroring.  | Mesh after mirroring.  |

### Mirror 

### Interactive Mirror 

Reference

Mode:
Object and Edit Modes, Video Sequencer Preview

Menu:
Object/Mesh/Curves/Strip ‣ Mirror ‣ Interactive Mirror

Shortcut:
Ctrl - M

The Mirror operation flips the picked geometry around a given axis.
This is functionally equal to scaling the selection by -1 in that direction,
though provides a quicker and more user-friendly method.

When mirroring sequencer strips, the axis mirror value changes rather than applying -1 scaling.
Positioning and rotation shift to achieve the same visual outcome as object mirroring.

The operation references the selected Transformation Orientation
and Pivot Point
For complete flexibility, you can:

- Relocate the pivot point to any position for symmetry control.

- Pick a transformation orientation (such as Global, Local, or Normal).

- Designate which axis (X, Y, or Z) to flip across.

Tip

For non-destructive flipping, apply the Mirror Modifier instead.

### Usage 

To perform a flip along a particular axis:

- Hit Ctrl - M, followed by X, Y, or Z to choose the axis.

- Press the same key again to alternate between the selected Transform Orientation and global space.

- Hold MMB and move the mouse to interactively adjust the flip direction.

### Properties 

Orientation
The Transform Orientation governing how the X, Y, and Z directions are positioned.

Constraint Axis
Determines which axis/axes receive the flip.
As an illustration, using the X axis flips the selection side-to-side.

### X/Y/Z Global 

Reference

Mode:
Object and Edit Modes, Video Sequencer Preview

Menu:
Object/Mesh/Curves/Strip ‣ Mirror ‣ X/Y/Z Global

These perform straightforward flips along the world's X, Y, or Z axis without interaction.

X Global
Flips the selection relative to the world X axis.

Y Global
Flips the selection relative to the world Y axis.

Z Global
Flips the selection relative to the world Z axis.

### X/Y/Z Local 

Reference

Mode:
Object and Edit Modes, Video Sequencer Preview

Menu:
Object/Mesh/Curves/Strip ‣ Mirror ‣ X/Y/Z Local

These perform straightforward flips along the object's own X, Y, or Z axis.

X Local
Flips the selection relative to the object's local X axis.

Y Local
Flips the selection relative to the object's local Y axis.

Z Local
Flips the selection relative to the object's local Z axis.

### Examples 

| Before flipping.  | After flipping across the X axis.  |

The following demonstrates flipping around the 3D Cursor with Local orientation:

| Initial state.  | After flipping across the X axis with the 3D Cursor as the pivot point.  |
