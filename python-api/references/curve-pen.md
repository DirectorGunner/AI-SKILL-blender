# Curve Pen, Bridge Edge Loops, Extrude Edges, Rotate Edge ...

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Curve Pen; Bridge Edge Loops; Extrude Edges; Rotate Edge; Un-Subdivide; Beautify Faces; Extrude Individual Faces; Fill; Intersect (Knife); Poke Faces; Shade Smooth & Flat; Triangulate Faces; Wireframe; Clean Up; Duplicate; Extrude; Knife Project; Set Attribute.

## Curve Pen

Reference

Mode: Edit Mode
Tool: Toolbar ‣ Curve Pen

Rapidly design and modify curves.

Extrude Point
LMB click to branch a new point from the active one as Vector type. Shift+LMB creates an Auto-type point (converts to Align when dragged).

Delete Point
Ctrl+LMB on a point to remove it.

Insert Point
Ctrl+LMB on a segment inserts a point between two existing ones. Ctrl+LMB and drag adjusts the inserted handles.

Move Segment
LMB drag on the segment between points to adjust handles without moving the points.

Select Point
LMB click to select a single point or handle.

Move Point
LMB drag to reposition points or handles. From an endpoint, click-drag empty space to extrude and reposition simultaneously.

Close Stroke
Click both endpoints to make the stroke cyclic.

Cycle Handle Type
Double LMB on a point to toggle through all handle types.

Hotkeys

Free-Align Toggle
Hold LeftCtrl while dragging a handle to switch between Free and Align. Useful for sharp corners.

Move Entire Point
Hold LeftAlt while dragging a handle to move the whole point.

Snap Handle Angle
Hold LeftShift while dragging to snap the handle to 45-degree multiples (horizontal, vertical, or diagonal).

Tool Settings

Radius: Control the initial radius of newly created points.

## Bridge Edge Loops

Removes the chosen faces and stitches fresh ones across two or more of the selected edge loops.

Note: In Blender, an edge loop is any chain of connected edges—need not be closed. See Select Edge Loops.

Connect Loops option:
- Open Loop: Last loop disconnects from first
- Closed Loop: Last connects back to first
- Loop Pairs: First connects to second, third to fourth, etc.

Merge: Instead of creating faces, merge all loops (or loop pairs if selected) into single loop

Merge Factor: 0 = merge into first loop; 1 = merge into last; intermediate = interpolation

Twist: Offsets target vertex choice for source vertices; makes tube twist along axis

Number of Cuts: Intermediate loop count between existing loop pairs

Interpolation — Intermediate loop calculation when Number of Cuts > 0:
- Linear: Straight-line loops
- Blend Path: Bézier spline loops (disregards neighboring surfaces)
- Blend Surface: Bézier loops along surface normals (surface-aware)

Smoothness: Blend Path/Surface smoothing (1 = full Bézier; 0 ≈ Linear)

Profile Factor: Profile Shape strength (-value shrinks tube middle; +value inflates)

Profile Shape: Tube segment thickness variation between source loops. See Proportional Editing page for option details.

Examples:

Bridging same-vertex-count loops: input → result

Bridging different-vertex-count loops: input → result

Hole connection in surfaces: input → result

Series loop connection in single operation: input → result

Blend Surface interpolation on textured surfaces: input → result

See also: Grid Fill

## Extrude Edges

### Extrude Edges 

Reference

Mode :

Edit Mode

Menu :

Edge ‣ Extrude Edges
Mesh ‣ Extrude ‣ Extrude Edges

Shortcut :

E

Pulls the chosen edges outward into new geometry, ignoring whatever faces sit beside them.

| Edges selected.  | Edges extruded.  |

## Rotate Edge

### Rotate Edge 

Reference

Mode :

Edit Mode

Menu :

Edge ‣ Rotate Edge CW / Rotate Edge CCW

Reworks the two faces flanking each chosen edge, spinning that edge either clockwise (CW)
or counterclockwise (CCW).

| Selected edge.  | Edge rotated CCW.  |

You can also pick pairs of touching faces; in that case the edge shared by each pair is the
one that turns:

| Two adjacent faces selected.  | Shared edge rotated.  |

## Un-Subdivide

### Un-Subdivide 

Reference

Mode :

Edit Mode

Menu :

Edge ‣ Un-Subdivide

Strips out edges to try to reverse an earlier Subdivide. Expect surprises if you edited the mesh
further after subdividing.

### Options 

Iterations
How many subdivisions to remove.

## Beautify Faces

### Beautify Faces 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Beautify Faces

Reshuffles the chosen faces toward tidier topology.

| Text converted to a mesh.  | Result of Beautify Faces.  |

### Options 

Max Angle
The largest angle permitted between two face normals — so two coplanar faces count as 0°, not
180°. An edge sitting between faces whose angle tops this limit is left alone.

## Extrude Individual Faces

### Extrude Individual Faces 

Reference

Mode :

Edit Mode

Tool :

Toolbar ‣ Extrude Individual

Menu :

Face ‣ Extrude Individual Faces ,
Mesh ‣ Extrude ‣ Extrude Individual Faces

Extrudes every face on its own, in contrast to Extrude Faces, which keeps the faces joined.

| Before.  | After Extrude Faces.  | After Extrude Individual Faces.  |

## Fill

### Fill 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Fill

Shortcut :

Alt - F

Caps a closed ring of selected edges with triangular faces. Holes are handled too:

| Before filling.  | After filling.  |

See also

New Edge/Face from Vertices fills a set of edges
(or vertices) with a single n-gon.

## Intersect (Knife)

### Intersect (Knife) 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Intersect (Knife)

Lays new edges everywhere faces cross one another.

| Before intersect.  | After intersect.  |

See also

Intersect (Boolean) in Union mode doesn't
just create intersection edges, but also removes faces that end up enclosed in a volume.

### Options 

Source

Self Intersect
Cross selected faces against other selected faces.

Selected/Unselected
Cross selected faces against unselected faces.

Separate Mode
Whether faces get disconnected from one another after the edges are made.

All :

Split every face apart at each intersection edge.

Cut :

When Source is Selected/Unselected , detach only the selected faces from the unselected ones.
Otherwise it acts the same as All .

Merge :

Keep every face joined at each intersection edge.

| Separate All: the cylinder and the plane stay separate and are each split in two.  | Separate Cut: the cylinder and the plane stay separate.  | Merge: the cylinder and the plane are connected to each other.  |

Solver
Algorithm used to calculate the intersections.

Float
A lightweight solver — fast, but with no support for overlapping geometry.

Merge Threshold
How close two faces must be to count as touching. Raising it can help when intersections that
ought to register don't, or when stray geometry appears because edges aren't read as overlapping.

Warning

A threshold approaching the size of faces may cause very slow calculation.
In general, keep this value small.

Exact
A heavier solver — slowest of the two, but it gives the best results and fully supports
overlapping geometry.

## Poke Faces

### Poke Faces 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Poke Faces

Breaks each selected face into a triangle fan radiating from a brand-new central vertex. Lift or
drop that vertex to build a pyramid or cone.

| Before poking.  | After poking.  | Adding a Poke Offset.  |

### Options 

Poke Offset
How far to push the freshly made central vertex out along the face normal.

Offset Relative
Ties the Poke Offset to face size — specifically, it scales each face's offset by the mean
distance from that face's center to its corners.

Poke Center
Which rule fixes where the face's center sits:

Weighted Median
Average the corner positions, weighting each by the lengths of its neighboring edges.

Median
Average the corner positions.

Bounds
Use the center of the bounding box.

## Shade Smooth & Flat

### Shade Smooth & Flat 

### Shade Smooth 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Shade Smooth

Tags the chosen faces for smooth shading, so the seams between them blur and grow hard to spot —
ideal for rounded, organic surfaces.

Under the hood, this aims every face-corner normal at a vertex in one shared direction: the
average of the surrounding face normals.

Tip

After using Shade Smooth on a mesh and blurring all its edges, you can use
Mark Sharp to selectively make some edges sharp again.

Alternatively, use Shade Auto Smooth to automatically apply smooth
shading to flattish areas while keeping corners sharp.

### Shade Flat 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Shade Flat

Tags the chosen faces for flat shading, so the seams between them turn crisp and obvious — ideal
for machines, crystals, and such.

Under the hood, this sets each face-corner normal equal to its own face's normal.

See also

Shading

## Triangulate Faces

### Triangulate Faces 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Triangulate Faces

Shortcut :

Ctrl - T

Turns every selected face — quad or n-gon alike — into triangles.
See the Triangulate Modifier.

## Wireframe

### Wireframe 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Wireframe

Converts the chosen faces into a wireframe, swapping their edges for tubes — much like the
Wireframe Modifier.

## Clean Up

### Clean Up 

This set of operators can tidy several kinds of messy geometry on their own.

### Delete Loose 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Clean up ‣ Delete Loose

Removes the selected vertices, edges, and — if you want — faces that connect to nothing.

### Decimate Geometry 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Clean up ‣ Decimate Geometry

Cuts the face count of the selected geometry while keeping shape changes to a minimum.

Ratio
Target ratio for the triangle count. Enter 0.4, for instance, to keep collapsing edges until only
40% of the original triangles remain.

Vertex Group
Steer edge collapsing by the active vertex group. Heavier vertex weights on an edge raise its
odds of being collapsed, even ahead of otherwise "better" (shorter) candidates.

Weight
A multiplier applied to the vertex weights.

Invert
Flips the vertex weights, so lighter-weighted edges collapse first.

Symmetry
Hold the result symmetric across the X , Y , or Z axis.

See also

The Decimate Modifier in Collapse mode
performs the same operation non-destructively.

### Degenerate Dissolve 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Clean up ‣ Degenerate Dissolve

Collapses selected edges below a set length, which also clears out small faces along the way.

Two vertices close together but not joined by an edge won't merge; see Merge By Distance for
that case.

Merge Distance
Any edge below this length gets collapsed away.

### Limited Dissolve 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Clean up ‣ Limited Dissolve

See Limited Dissolve.

### Make Planar Faces 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Clean up ‣ Make Planar Faces

Flattens the selected faces.

Factor
The flattening strength per iteration. Even 1 may fall short of perfectly flat — bump up the
Iterations if so.

Iterations
How many passes the operation runs.

### Split Non-Planar Faces 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Clean up ‣ Split Non-Planar Faces

Splits any selected faces bent past a given limit.

Max Angle
Faces bent by more than this angle get split.

Hint

You can use Rotate Edge if you'd rather have certain
newly created edges point in a different direction.

| Original mesh.  | Result of Split Non-Planar Faces.  |

### Split Concave Faces 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Clean up ‣ Split Concave Faces

Splits any selected concave faces until only convex ones are left.

| Original mesh.  | Result of Split Concave Faces.  |

### Merge by Distance 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Clean up ‣ Merge by Distance

Merges selected vertices that lie within a set distance of one another.

Merge Distance
Vertices nearer to each other than this get fused.

Unselected
Allow merging selected vertices with unselected ones.

Sharp Edges
On a smooth-shaded mesh carrying custom split normals, this adds edge marks where needed so sharp
edges stay sharp through the merge.

See also

The Weld Modifier performs this operation non-destructively.

### Fill Holes 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Clean up ‣ Fill Holes

Drops a face into every hole in the selected geometry.

Sides
The edge-count ceiling: a hole with more edges than this stays open. Use 0 to fill them all.

See also

For filling a large hole that has many edges,
Face Fill or
Grid Fill may be a better option.

## Duplicate

### Duplicate 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Duplicate

Shortcut :

Shift - D

Makes a copy of the selection. Once you click the menu item or press the shortcut, drag the copy
where you want it and press LMB or Return to set it down. Or press RMB or Esc to leave the copy
right on top of the original. (Either way the copy stays selected, so moving it aside afterward is
easy.)

## Extrude

### Extrude 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Extrude

Shortcut :

Alt - E

Which operators this menu offers shifts with the current selection. Many also live in the Vertex,
Edge, and Face menus.

### Extrude Faces 

Available when at least one face is selected.

See Extrude Faces.

### Extrude Faces Along Normals 

Available when at least one face is selected.

See Extrude Faces Along Normals.

### Extrude Individual Faces 

Available when at least one face is selected.

See Extrude Individual Faces.

### Extrude Manifold 

Available when at least one face is selected.

See Extrude Manifold.

### Extrude Edges 

Available when at least one edge is selected.

See Extrude Edges.

### Extrude Vertices 

Available when at least one vertex is selected.

See Extrude Vertices.

### Extrude Repeat 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Extrude ‣ Extrude Repeat

Extrudes the selection over and over along the current view direction, moving away from your
viewpoint. It does best from a top or side view, or any custom orthographic direction.

Steps
How many extrusions to stack.

Offset X, Y, Z
The gap separating one extrusion from the next.

Scale Offset
Multiplication factor for the Offset .

### Spin 

See Spin.

## Knife Project

### Knife Project 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Knife Project

Casts the silhouette of one or more "cookie cutter" objects onto the edited object, cutting fresh
edges where it lands.

Cutter objects have to be Curves or non-manifold meshes — flat shapes, loose edges, and the like.

Tip

Select Non-Manifold will highlight the cutting edges
of mesh objects.

Projection is done along the viewing direction.

### Usage 

- Select the object(s) that should receive the cut and switch to Edit Mode .

- Select the object(s) that should perform the cut by clicking them with Ctrl - LMB in the
3D Viewport or the Outliner.

- Click Mesh ‣ Knife Project in the menu.

Should Blender drop back to Object Mode as you pick the cutter objects, check that
Edit ‣ Lock Object Modes is ticked in the topbar.

### Options 

Cut Through
Drives the cut through the whole mesh, back faces you can't see included.

### Examples 

| Before projecting from a text object.  | Resulting knife projection.  |
| Before projecting from a mesh object.  | Resulting knife projection (extruded after).  |
| Before projecting from a 3D curve object.  | Resulting knife projection (extruded after).  |

### Known Limitations 

Cut several meshes at once in Edit Mode and geometry from one of them won't block separate mesh
objects sitting behind it.

## Set Attribute

### Set Attribute

Reference

Mode:

Edit Mode

Menu:

Mesh → Set Attribute

Opens a dialog showing the active attribute's name and its value for the selected element (vertex/edge/face).
You can then change the value to apply it across all selected elements.

The "active" attribute is the one most recently selected in the Data tab of the Properties Editor.
It may be a UV Map, Color Attribute, or generic Attribute.

See also

Attribute values can be inspected in the Spreadsheet editor.

## Shading

### Shading

### Smooth/Flat Faces

Reference

Mode:

Edit Mode

Menu:

Mesh → Shading → Smooth/Flat Faces

Applies smooth or flat shading to selected faces.

### Smooth/Sharp Edges

Reference

Mode:

Edit Mode

Menu:

Mesh → Shading → Smooth/Sharp Edges

Toggles the Sharp mark on selected edges.

### Smooth/Sharp Vertices

Reference

Mode:

Edit Mode

Menu:

Mesh → Shading → Smooth/Sharp Vertices

Toggles the Sharp mark on all edges connected to at least one selected vertex.

## Randomize

### Randomize

Reference

Mode:

Edit Mode

Menu:

Mesh → Transform → Randomize

Displaces selected vertices in unpredictable directions.

### Options

Amount
Maximum displacement for each vertex.

Uniform
How even the displacement distance should be. At 0, each vertex moves a random distance between 0 and Amount. At 1, all vertices move exactly Amount distance. Displacement direction stays unpredictable regardless.

Normal
How aligned the displacement direction is to each vertex normal.
At 0, direction is fully arbitrary. At 1, direction matches the normal or its opposite.

Random Seed
Different seeds create different random displacements.

See also

Randomize in Object Mode

### Randomize 

Reference

Mode:
Object Mode and Edit Mode

Menu:
Object ‣ Transform ‣ Randomize Transform

Randomize options. 

This tool applies random variations to movement, rotation, and scale on one or several objects.
When used on many objects, each receives its own randomization seed,
yielding distinct outcomes for each.

Random Seed
The seed parameter biases the randomization.
Switching the seed generates a different result.

Transform Delta
Randomize Delta Transform
numbers instead of primary transform.

Randomize Location
Randomize position values.

Location
The furthest distance the objects can drift along each dimension.

Randomize Rotation
Randomize angle values.

Rotation
The furthest angle the objects can turn on each dimension.

Randomize Scale
Randomize resizing values.

Scale Even
Apply the same resizing across all dimensions.

Scale
The most resizing variation across each dimension.

## Move/Scale Texture Space

### Move/Scale Texture Space

Reference

Mode:

Object and Edit Modes

Menu:

Object/Mesh → Transform → Move/Scale Texture Space

Repositions or resizes the Texture Space of the active mesh.

### Move/Scale Texture Space 

Reference

Mode:
Object Mode and Edit Mode

Menu:
Object ‣ Transform ‣ Move/Scale Texture Space

The Move/Scale Texture Space function shifts or resizes the Texture Space
of the item, not the item or component itself.

## To Sphere

### To Sphere

Reference

Mode:

Object and Edit Modes

Menu:

Mesh → Transform → To Sphere

Shortcut:

Shift - Alt - S

To Sphere deforms selected geometry toward a spherical form.

Monkey with increasing sphericity (0%, 25%, 50%, 100%).

### Usage

Select the menu option or shortcut, then drag left or right (or enter a value from 0 to 1) to adjust sphericity.
Finally, press LMB or Return to apply, or RMB or Esc to cancel.

### Options

Factor
A decimal from 0 to 1 controlling how strongly the selection becomes spherical.

Mirror Editing
Whether to affect corresponding geometry on the opposite mesh side.
Mesh Symmetry must be active.

Proportional Editing
See Proportional Editing.

### Examples

Higher-density meshes produce better outcomes:

To Sphere applied to cubes with different subdivision levels.

Results vary with the count and arrangement of selected elements:

To Sphere applied to different selections.

## Blend from Shape

### Blend from Shape

Reference

Mode:

Edit Mode

Menu:

Vertex → Blend from Shape

Shifts selected vertices toward their stored position in a specific Shape Key.
Helpful for refining geometry by borrowing deformations from a shape key.

### Options

Shape
Which shape key to reference.

Blend
How much to apply the shape (like the shape key's Value).
0 leaves unchanged; 1 makes vertices exactly match the key.

Add
When off, each vertex interpolates between its current spot and the shape key's absolute position.

When on, Blender finds the difference between the shape key positions and its Relative To shape key, then adds that difference (scaled by Blend) to the vertex.

## Extrude to Cursor or Add

### Extrude to Cursor or Add

Reference

Mode:

Edit Mode

Shortcut:

Ctrl - RMB

Forms a vertex at the cursor position, or extends selected vertices/edges toward the cursor.

Pressing Ctrl - RMB with nothing chosen builds a vertex at the 3D Cursor depth.

With one or more chosen isolated vertices (unconnected to edges/faces), Ctrl - RMB extends each into an edge. New vertices land at the same viewport depth as originals. Selected status flips (originals off, new ones on), enabling repeated chains.

Extruding vertices into edges.

With two or more chosen linked vertices, Ctrl - RMB extends them into faces.

Extruding edges into faces.

Earlier edges rotate for a smoother result. Prefer Shift - Ctrl - RMB to skip rotation.

Tip

When extruding, apply top or side views to stay within a single plane. Top view ensures constant global Z; side view does likewise for another coordinate.

## Extrude Vertices

### Extrude Vertices

Reference

Mode:

Edit Mode

Menu:

Vertex → Extrude Vertices ,
Mesh → Extrude → Extrude Vertices

Shortcut:

E

Pulls each chosen vertex outward as a separate element.

| Vertices selected. | Vertices extruded. |

## Hooks

### Hooks

This mechanism pairs with the Hook Modifier, which "hooks" vertex sets to an external object. Moving that object also moves those vertices.

The reverse – attaching an external object to a vertex – uses Make Vertex Parent.

### Hook to New Object

Reference

Mode:

Edit Mode

Menu:

Vertex → Hooks → Hook to New Object

Shortcut:

Ctrl - H

Generates an Empty at the selected vertices' average position, then installs a Hook modifier tying vertices to the Empty.

If no vertices are chosen, the active Vertex Group gets used instead.

### Hook to Selected Object

Reference

Mode:

Edit Mode

Menu:

Vertex → Hooks → Hook to Selected Object

Shortcut:

Ctrl - H

Installs a Hook modifier linking the chosen vertices to the chosen object (not the active mesh). If no vertices are chosen, the active Vertex Group gets used instead.

To pick another object while in Edit Mode, use the Outliner or Ctrl - LMB in the 3D Viewport.

### Hook to Selected Object Bone

Reference

Mode:

Edit Mode

Menu:

Vertex → Hooks → Hook to Selected Object Bone

Shortcut:

Ctrl - H

Installs a Hook modifier linking the chosen vertices to the chosen bone.
If no vertices are chosen, the active Vertex Group gets used instead.

To choose the bone of another object while in Edit Mode, click it with Ctrl - LMB in the 3D Viewport.

Tip

The Armature Modifier is the more typical way to attach vertices to bones.

### Assign to Hook

Reference

Mode:

Edit Mode

Menu:

Vertex → Hooks → Assign to Hook

Shortcut:

Ctrl - H

Appends the chosen vertices to an existing Hook modifier (selected from a menu) and removes unchosen ones.

Vertices can join multiple hooks.

### Remove Hook

Reference

Mode:

Edit Mode

Menu:

Vertex → Hooks → Remove Hook

Shortcut:

Ctrl - H

Deletes a Hook modifier (selected from a menu) from the mesh.

### Select Hook

Reference

Mode:

Edit Mode

Menu:

Vertex → Hooks → Select Hook

Shortcut:

Ctrl - H

Picks the vertices tied to a chosen Hook modifier (selected from a menu).

### Reset Hook

Reference

Mode:

Edit Mode

Menu:

Vertex → Hooks → Reset Hook

Shortcut:

Ctrl - H

Each Hook modifier stores a rest position for the "parent" object where hooked vertices sit in their original spot. Clicking Reset Hook refreshes this rest position to the parent's current state (vertices return to their original location).

### Recenter Hook

Reference

Mode:

Edit Mode

Menu:

Vertex → Hooks → Recenter Hook

Shortcut:

Ctrl - H

Moves a chosen Hook modifier's center (selected from a menu) to the 3D Cursor. This point calculates the Falloff distance for the modifier.

The center displays in the 3D Viewport as a black dot, linked to the "parent" object with a dashed black line.

## Smooth Vertices (Laplacian)

### Smooth Vertices (Laplacian)

Reference

Mode:

Edit Mode

Menu:

Vertex → Smooth Vertices (Laplacian) ,
Context Menu → Smooth Laplacian

Repositions chosen vertices to smooth the surrounding surface, making it rounder.
See the Smooth Laplacian Modifier for full details.

## Make Vertex Parent

### Make Vertex Parent

Reference

Mode:

Edit Mode

Menu:

Vertex → Make Vertex Parent

Shortcut:

Ctrl - P

Attaches the chosen objects to the chosen vertex or trio of vertices.

With one vertex, objects follow its position.
With three vertices, objects follow the triangle's center and rotate with it. (The triangle doesn't need a physical face.)

In Edit Mode, select child objects via the Outliner or Ctrl - LMB in the 3D Viewport. If Blender reverts to Object Mode, verify Edit → Lock Object Modes is active in the topbar.

See also

- Parenting overview

- Hooks – for the inverse, "hooking" vertices to objects.
