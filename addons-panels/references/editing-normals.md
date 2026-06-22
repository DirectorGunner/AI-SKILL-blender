# Editing Normals, Snap To Symmetry, Split, Symmetrize ...

> Blender Add-ons, Panels, and Properties reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Editing Normals; Snap to Symmetry; Split; Symmetrize; Bend; Push/Pull; Shear; Shrink/Fatten; Skin Resize; Warp; Connect Vertex Pairs; Connect Vertex Path; New Edge/Face from Vertices; Slide Vertices; Smooth Vertices; Vertex Crease; Vertex Groups.

## Editing Normals

### Editing Normals 

Press Alt - N to open the Normals menu as a popover.

Most operators here act on custom split normals — normal vectors tied to face corners rather than
vertices. You can select those corners in several ways:

- In Vertex or Edge selection mode, picking a vertex or edge also picks the nearest corners of the
faces it belongs to.

- In Face mode, picking a face also picks its corners.

- With both Vertex and Face modes on, picking a vertex and then adding a face selects only the
matching face corner.

- Likewise, with both Edge and Face modes on, picking an edge and then adding a face selects only
the two matching face corners.

See also

- The 3D Viewport overlay for visualizing normals.

- The Geometry Data panel of the mesh properties for
clearing custom normals.

- Mesh Data Transfer (operator
or modifier) for copying normals from
another mesh.

- The Normal Edit Modifier and the
Weighted Normal Modifier for calculating or changing normals
based on certain criteria.

### Flip 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Normals ‣ Flip

Reverses the orientation of the selected faces, swapping their "front side" for their "back side"
and vice versa. Custom split normals are untouched.

The 3D Viewport's Face Orientation overlay makes wrongly oriented faces easy to catch.

### Recalculate 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Normals ‣ Recalculate Outside and
Mesh ‣ Normals ‣ Recalculate Inside

Shortcut :

Shift - N and Shift - Ctrl - N

Flips the orientation of selected faces wherever needed so they all face outward (or inward). The
mesh doesn't have to be a closed volume for this to work.

Like Flip, this leaves custom split normals untouched.

### Set from Faces 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Normals ‣ Set from Faces

Sets each selected vertex's custom split normals to the average normal of the selected faces
around it.

Keep Sharp Edges
Tick this and any face corner sitting on a Sharp edge holds onto its original custom normal.

### Rotate 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Normals ‣ Rotate

Shortcut :

R followed by N

Spins the custom split normals of the selected face corners as you move the cursor. LMB confirms,
RMB cancels.

### Point to Target 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Normals ‣ Point to Target

Shortcut :

Alt - L

Aims the custom split normals of the selected face corners at a chosen target. After the menu
item or shortcut, set the target by pressing one of these (also shown in the status bar):

- M for the mouse cursor.

- L for the Pivot Point.

- O for the object origin.

- Ctrl - LMB for the 3D Cursor. This also changes the location of the Cursor.

- Ctrl - RMB for a certain vertex, edge, or face. Make sure not to click a space where there's no geometry,
as doing so will extrude the selection instead.

In addition, the following options are available:

Invert I
Aim the normals away from the target instead.

Align A
Send every normal one way: from the selected vertices' average position toward the target.

Spherize S
Blend each normal between its starting and new orientation. Set the blend amount in the Adjust
Last Operation panel after confirming.

Reset R
Restore the custom normals to their state when the operation began.

Once the normals are set, press LMB or Return to confirm. The options above stay editable
afterward in the Adjust Last Operation panel.

### Merge 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Normals ‣ Merge

Smooth-shades the selected faces and clears the Sharp mark on the selected edges. Then, at each
selected vertex, it averages the custom normals belonging to smooth-shaded faces. (Those
belonging to flat-shaded faces stay as they are.)

To average the custom normals regardless of face selection, use the Average
operator.

### Split 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Normals ‣ Split

Flat-shades the selected faces and marks the selected edges Sharp. Then, at each selected vertex,
it sets every custom normal on a flat-shaded face to that face's normal. (Normals on a
smooth-shaded face are set to the average of those faces' normals.)

### Average 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Normals ‣ Average

At each selected vertex, sorts the connected face corners into groups split by Sharp edges, then
sets each group's custom normals to a chosen average. The Adjust Last Operation panel offers:

Type

Custom Normal :

Set each group's face-corner custom normals to their average.

Face Area :

Set each group's face-corner custom normals to a weighted average of their face normals, weighted
by face area — bigger faces sway the final normal more.

Corner Angle :

As Face Area , but the weights come from the face-corner angles instead.

Weight
With Type set to Face Area or Corner Angle , the Weight steers which face normals the average
favors. At 50 you get a plain weighted average. At 100 the average rests entirely on the
largest-area faces (or largest-angle corners). At 1 it rests entirely on the smallest-area faces
(or smallest-angle corners).

Threshold
Tolerance value for treating face areas (or corner angles) as equal.

When custom normals are averaged across two vertices: a vertex with two separate groups of faces divided by Sharp edges gets two distinct averages, while a vertex without Sharp edges produces one average.

See also

The Weighted Normal Modifier achieves this without destructive changes.

### Copy Vector

Reference

Mode:

Edit Mode

Menu:

Mesh → Normals → Copy Vector

Transfers a single normal vector to an internal clipboard:

- If a face is selected, that face's normal gets transferred.

- If a vertex is selected, its normal gets transferred, but only when all its custom split normals match.

- If a face corner is selected, its custom split normal gets transferred.

### Paste Vector

Reference

Mode:

Edit Mode

Menu:

Mesh → Normals → Paste Vector

Places the previously copied normal vector onto selected face corners.
The Adjust Last Operation panel includes:

Absolute Coordinates
When enabled, selected face corners receive the pasted normal directly. When disabled, the pasted normal adds as an offset.

### Smooth Vectors

Reference

Mode:

Edit Mode

Menu:

Mesh → Normals → Smooth Vectors

Flattens custom normals at each selected vertex by averaging them with normals from adjacent vertices. The Adjust Last Operation panel offers:

Factor
Smoothing intensity. This sets the blend between original normals and the averaged result.

### Reset Vectors

Reference

Mode:

Edit Mode

Menu:

Mesh → Normals → Reset Vectors

Restores selected face corners' custom normals to defaults.

### Select by Face Strength

Reference

Mode:

Edit Mode

Menu:

Mesh → Normals → Select by Face Strength

Picks faces matching a specific Strength (Weak, Medium, or Strong) and clears the rest.

This value is used by the Weighted Normal Modifier when its Face Influence option is active.

### Set Face Strength

Reference

Mode:

Edit Mode

Menu:

Mesh → Normals → Set Face Strength

Assigns Weak, Medium, or Strong to the Strength property of selected faces.
All faces default to Medium strength.

This value is used by the Weighted Normal Modifier when its Face Influence option is active.

## Snap to Symmetry

### Snap to Symmetry

Reference

Mode:

Edit Mode

Menu:

Mesh → Snap to Symmetry

Snap to Symmetry corrects near-symmetrical meshes to perfect symmetry. Unlike Symmetrize, which cuts one half and mirrors the other, this operator pairs vertices by position and relocates them.

Useful after accidentally moving vertices while Mesh Symmetry was off.

### Options

Direction
The axis and direction of effect, in local object space.
Example: -X to +X affects vertices left of the origin (negative X) and aligns them with those on the right (positive X).

Threshold
Search radius for discovering matching vertices.

Factor
At 1, both vertices in a pair move to the "from" side position. At 0, both go to the "to" side.
Intermediate values interpolate; 0.5 moves both to their average position.

Center
Shifts vertices near the symmetry plane to sit exactly on it (setting their Direction-axis coordinate to zero).

| Before Snap to Symmetry. | After Snap to Symmetry. |

## Split

### Split

Press Alt - M to open the Split menu as a popover.

These tools handle splitting meshes by disconnecting faces from one another.
For cutting faces into smaller pieces, consult the Knife Topology Tool or the Connect Vertex Path operator.

### Split Selection

Reference

Mode:

Edit Mode

Menu:

Mesh → Split → Selection

Shortcut:

Y

Severs the mesh along the border of selected faces, allowing them to be repositioned elsewhere.

This operator also disconnects "wires" (edges not belonging to a face). However, applying it to edges that are part of a face duplicates them instead.

Disconnecting inner faces from their surroundings.

See also

The Separate operator disconnects selection and transfers it into a new mesh object.

### Split Faces by Edges

Reference

Mode:

Edit Mode

Menu:

Mesh → Split → Faces by Edges

Splits the mesh along selected edges, allowing vertices to be pulled apart and forming gaps.

Splitting by selected edges.

See also

Rip Vertices also cuts adjoining unselected edges.

### Split Faces & Edges by Vertices

Reference

Mode:

Edit Mode

Menu:

Mesh → Split → Faces & Edges by Vertices

Cuts the mesh at all adjacent edges of each selected vertex. (This differs from Rip Vertices, which cuts only two edges per vertex.)

Vertices can then be separated to create gaps.

Splitting by selected vertices.

## Symmetrize

### Symmetrize

Reference

Mode:

Edit Mode

Menu:

Mesh → Symmetrize

Symmetrize rapidly produces a symmetrical mesh by performing:

- Divides selected geometry along the object's origin using an infinite plane, similar to Bisect.

- Removes geometry on one plane side.

- Duplicates the opposite side's geometry and reverses it.

- Joins vertices that lie on the plane.

See also

- Mesh Symmetry continuously preserves symmetry during editing.

- The Mirror Modifier symmetrizes non-destructively.

- The Mirror operator flips the mesh without dividing or duplicating.

### Options

Direction
The axis and direction of effect, in local object space.
Example: -X to +X deletes geometry right of the origin (positive X) and replaces it with a mirrored copy of geometry on the left (negative X).

Threshold
Vertices within this distance snap to the symmetry plane.

| Mesh before Symmetrize. | Mesh after Symmetrize. |

## Bend

### Bend

Reference

Mode:

Object and Edit Modes

Menu:

Object/Mesh/Curve/Surface → Transform → Bend

Shortcut:

Shift - W

This transform warps part of the selection into a circular arc. Compared to Warp, the 3D Cursor lies on the arc itself instead of at its center.

| Before. | Clamp on. | Clamp off. |

### Usage

- Line the 3D Viewport viewing plane with the plane for bending.

- Set the 3D Cursor at the bend's base. Geometry around it stays put.

- Align the mouse with the geometry to bend, so the line between mouse and cursor lies along the bend direction.

- Press Shift - W and drag to bend the geometry.

- The separation between mouse and cursor determines the bend radius and distortion depth (versus pure rotation).
Press Alt to unlock clamping and bend the entire selection without limit.

- The angle from the original line to the new one determines the bend angle.

- Hit LMB or Return to confirm, or RMB or Esc to cancel.

Note

Unlike most transform tools, Bend ignores transform orientation and pivot point, always using the viewing plane and 3D Cursor instead.

Hint

Repeatedly circling the mouse around the 3D Cursor will apply bending through multiple full rotations.

### Options

Unlike other operators, Bend lacks an Adjust Last Operation panel.

### Example

Multiple consecutive bends.

## Push/Pull

### Push/Pull

Reference

Mode:

Object and Edit Modes

Tool:

Toolbar → Shrink/Fatten → Push/Pull

Menu:

Object/Mesh → Transform → Push/Pull

Shifts selected elements away from or toward the Pivot Point, all by a consistent distance.

With the tool, grab and drag the yellow pin.

From the menu, drag downward to Push or upward to Pull.
(Alternatively, enter a Distance value via keyboard.)
Press LMB or Return to confirm, or RMB or Esc to cancel.

Once confirmed, Adjust Last Operation panel still allows distance changes.

### Options

Distance
How much to push (negative) or pull (positive) selected items.

Mirror Editing
Whether to affect corresponding geometry on the opposite mesh side.
Mesh Symmetry must be active.

Proportional Editing
See Proportional Editing.

### Example

Pushing vertices away from the 3D Cursor (middle) versus scaling (right).

## Shear

### Shear

Reference

Mode:

Object and Edit Mode

Tool:

Toolbar → Shear

Menu:

Object/Mesh/Curve/Surface → Transform → Shear

Shortcut:

Shift - Ctrl - Alt - S

Shearing deforms selected geometry by moving upper vertices left and lower ones right (or vice versa) relative to the Pivot Point. Vertices further from the pivot shift more. The outcome: vertical edges become slanted while horizontal ones remain unchanged.

### Usage

### Tool

Set up a pivot point and optionally a transform orientation.
Choose an axis on the gizmo matching the "above"/"below" direction (controlling how much each vertex shears). Then drag the handle matching the "horizontal" direction (where vertices move).

Using the Shear tool.

### Operator

Set a pivot point, then select from the menu or press the shortcut.
Drag left or right to shear, then hit LMB to confirm.

By default, "above," "below," and "horizontal" use the current viewport plane, but options can alter this.

Using the Shear operator with different pivot points.

### Options

Angle
How much to "rotate" vertical edges.

Axis
The axis perpendicular to the shearing plane. For instance, when vertices travel along X and distance is measured from the pivot along Y, set Axis to Z.

Axis Ortho
The axis along which vertices slide. Must differ from Axis.

Orientation
The Transform Orientation from which to select Axis and Axis Ortho.

Mirror Editing
Whether to affect corresponding geometry on the opposite mesh side.
Mesh Symmetry must be active.

Proportional Editing
See Proportional Editing.

## Shrink/Fatten

### Shrink/Fatten

Reference

Mode:

Edit Mode

Tool:

Toolbar → Shrink/Fatten

Menu:

Mesh → Transform → Shrink/Fatten

Shortcut:

Alt - S

Displaces selected vertices "inward" or "outward" along their normals, all uniformly.

After selecting the menu or using the keyboard shortcut, drag downward to shrink or upward to expand.
(Alternatively, enter a numeric distance.) Press LMB or Return to lock in place, or RMB or Esc to abandon.

| Mesh before shrink/fatten. | Shrunk using a negative value. | Fattened using a positive value. |

### Options

Adjust Last Operation panel settings:

Offset
How far each vertex moves.

Offset Even
When off, each vertex shifts the same distance.
When on, each edge shifts the same distance.

This setting toggles before confirming with S or Alt.
(Shortcuts appear in the status bar.)

| Fattening with Offset Even disabled. | Fattening with Offset Even enabled. |

Mirror Editing
Whether to affect corresponding geometry on the opposite mesh side.
Mesh Symmetry must be active.

Proportional Editing
See Proportional Editing.

## Skin Resize

### Skin Resize

Reference

Mode:

Edit Mode

Menu:

Mesh → Transform → Skin Resize

Shortcut:

Ctrl - A

Adjusts X and Y skinning radii of selected vertices for use with the Skin Modifier. (On meshes without this modifier, activation has no effect.)

To adjust only one radius, press X or Y while operating, or modify Scale X/Y in Adjust Last Operation panel.

Radius values can also be fine-tuned in the Transform Panel sidebar.

Note

Deleting the modifier removes the skinning radii.

Simple creature, made with only the Skin and Subdivision Surface modifiers.

## Warp

### Warp

Reference

Mode:

Edit Modes

Menu:

Object/Mesh/Curve/Surface → Transform → Warp

This transform warps part of the selection into a circular arc.
Compared to Bend, the 3D Cursor sits at the arc center rather than on the arc itself.

### Usage

- Orient the 3D Viewport viewing plane toward the warp plane.

- Locate the 3D Cursor at the warp center.

- Click Warp in the menu.

- Adjust options in the Adjust Last Operation panel.

| Before. | Warp Angle 90°. |
| Warp Angle 180°. | Warp Angle 360°. |

Note

Unlike most transform tools, Warp disregards transform orientation and pivot point, always using the viewing plane and 3D Cursor instead.

### Options

Warp Angle
The arc's size into which to deform the selection.

Offset Angle
Direction angle for the line from 3D Cursor to selection center.
0° points straight up; higher values proceed clockwise.

Min/Max
Distance from the centerline to the leftmost/rightmost geometry that enters the arc. Geometry beyond these limits rotates but doesn't curve.

Warping with an Offset Angle of 45°, a Min and Max of -0.5 and 0.5,
and a Warp Angle of 90°.

### Example

Text wrapped around logo.

This was produced by building the Blender logo and text as separate objects.
The text was converted to a mesh and then warped around the logo.

## Connect Vertex Pairs

### Connect Vertex Pairs

Reference

Mode:

Edit Mode

Menu:

Vertex → Connect Vertex Pairs

Builds an edge between each pair of selected vertices sharing a face, cutting the face in two.

| Before. | After. |

This tool diverges from Connect Vertex Path by only joining vertices within a single face apart. Selection sequence is irrelevant.

## Connect Vertex Path

### Connect Vertex Path

Reference

Mode:

Edit Mode

Menu:

Vertex → Connect Vertex Path

Shortcut:

J

Bridges vertices in selection order with edges, slicing faces in the process.
Calling a second time closes the loop.

| Before. | First execution. | Second execution. |

Isolated vertices (not in any edges or faces) can also get connected this way.

See also

The Knife Topology Tool offers interactive face splitting. Unlike Connect Vertex Path, it makes cuts aligned with the current viewport.

## New Edge/Face from Vertices

### New Edge/Face from Vertices

Reference

Mode:

Edit Mode

Menu:

Vertex → New Edge/Face from Vertices

Shortcut:

F

Creates a surface between chosen vertices.
With only two vertices chosen, generates an edge instead.

See also

- Face Fill

- Grid Fill

- Bridge Edge Loops

### Use Cases

The operator covers:

### Edge from Vertices

| Before. | After. |

### Face from Vertices

| Before. | After. |

### Face from Edges

| Before. | After. |

### Face from Vertices and Edges

| Before. | After. |

### N-gon from Vertices

Four or more vertices yield a single n-gon.

| Before. | After. |

### N-gon from Edges

A chain of edges also builds an n-gon with greater outline control.
Holes are not supported; use Face Fill instead.

| Before. | After. |

### Patch from Edges

Interior edges trigger creation of multiple surfaces rather than one.

| Before. | After. |

### Face from Single Vertex or Edge

A single boundary vertex or edge on a hole prompt Blender to create a surface using neighboring edges. Just the new edge stays chosen afterward, permitting immediate new surface creation.

Pressing F twice on a vertex.

### Dissolve Existing Faces

Multiple selected surfaces prompt Dissolution, merging them (rather than overlapping).
Works across multiple "islands" simultaneously.

| Before dissolving. | After dissolving. |

## Slide Vertices

### Slide Vertices

Reference

Mode:

Edit Mode

Menu:

Vertex → Slide Vertices

Shortcut:

G twice or Shift - V

Moves each chosen vertex along one of its neighboring edges. After engaging the tool, drag along the target edge direction, then press LMB to apply (or RMB to discard).

These options appear in Adjust Last Operation panel afterward.
Ones with shortcuts also change while dragging – shortcuts and settings display in the status bar.

Factor
Relative shift distance.

Even E
By default, each vertex moves the same percentage along edge length.
Enable Even to move all vertices the same absolute distance.
(Factor stays relative.)

Flipped F
Move each vertex the same absolute distance from its "opposite" endpoint (other edge end). Active only with Even.

Clamp Alt or C
When off, vertices can cross their edge's original limits.

Mirror Editing
Also move matching vertices on the opposite mesh side.
Mesh Symmetry must be active.

Correct UVs
Fix UV coordinates of moved vertices to prevent texture warping.

| Vertices selected. | Sliding vertices. | Slide confirmed. |

See also

Edge Slide

## Smooth Vertices

### Smooth Vertices

Reference

Mode:

Edit Mode

Menu:

Vertex → Smooth Vertices ,
Context Menu → Smooth Vertices

Repositions chosen vertices to smooth the surrounding surface, rendering it rounder.

Adjust Last Operation panel presents:

Smoothing
Smoothing intensity.

Repeat
Number of smoothing passes.

Axes
Limit the effect to specific axes.

| Mesh before smoothing. | Mesh after one smoothing iteration. | Mesh after ten smoothing iterations. |

Tip

Insufficient geometry density leaves meshes blocky after smoothing.
Add subdivisions beforehand.

Alternatively, the Subdivision Surface Modifier subdivides and smooths at once. The method differs, though, producing non-identical results.

See also

The Smooth Modifier applies this effect without modification.

Note

Smooth Faces (also called Shade Smooth elsewhere) differs from this tool. It alters vertex normals for visual smoothness without shifting vertex positions.

## Vertex Crease

### Vertex Crease

Reference

Mode:

Edit Mode

Menu:

Vertex → Vertex Crease

Modifies the Crease value of chosen vertices, which sets corner sharpness when using the Subdivision Surface Modifier.

Crease values also adjust in the Transform Panel sidebar.

## Vertex Groups

### Vertex Groups

### Assign to New Group

Reference

Mode:

Edit Mode

Menu:

Vertex → Vertex Groups → Assign to New Group

Shortcut:

Ctrl - G

Establishes a new Vertex Group and binds chosen vertices to it, with the Weight from the Vertex Groups Panel.

### Assign to Active Group

Reference

Mode:

Edit Mode

Menu:

Vertex → Vertex Groups → Assign to Active Group

Shortcut:

Ctrl - G

Adds chosen vertices to the vertex group selected in the Vertex Groups panel, with its current Weight.

Same as pressing Assign in the panel directly.

### Remove from Active Group

Reference

Mode:

Edit Mode

Menu:

Vertex → Vertex Groups → Remove from Active Group

Shortcut:

Ctrl - G

Excludes chosen vertices from the vertex group selected in the Vertex Groups panel.
Same as pressing Remove in the panel directly.

### Remove from All

Reference

Mode:

Edit Mode

Menu:

Vertex → Vertex Groups → Remove from All

Shortcut:

Ctrl - G

Excludes chosen vertices from all vertex groups.

### Set Active Group

Reference

Mode:

Edit Mode

Menu:

Vertex → Vertex Groups → Set Active Group

Shortcut:

Ctrl - G

Marks a particular vertex group (chosen from the menu) as active.
Same as selecting it in the Vertex Groups panel.

### Remove Active Group

Reference

Mode:

Edit Mode

Menu:

Vertex → Vertex Groups → Remove Active Group

Shortcut:

Ctrl - G

Erases the vertex group selected in the Vertex Groups panel.
Same as pressing the button in the panel.

### Remove All Groups

Reference

Mode:

Edit Mode

Menu:

Vertex → Vertex Groups → Remove All Groups

Shortcut:

Ctrl - G

Clears all mesh vertex groups. Achievable via the Vertex Groups panel button, then Delete All Groups in the popover.

### Vertex Groups 

Reference

Panel :

Particle System ‣ Vertex Groups

The Vertex groups panel permits designating vertex groups for child particle configurations. Checkboxes allow negating each group's influence. The following characteristics become modifiable:

Density

The particle distribution amount.

Length

The strand span.

Clump

The clumping degree. Weighting of 1.0 applies current Clump value; 0.0 eliminates effect.

Kink

The children Kink repetition rate.

Roughness 1

Modifies the Uniform roughness metric.

Roughness 2

Modifies the Random roughness metric.

Roughness End

Modifies the Endpoint roughness metric.

Twist

Vertex group regulating children's Twist magnitude. Authority over twist orientation becomes available. The weight of 0.5 represents neutral, producing no twist.
