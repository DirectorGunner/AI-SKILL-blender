# Volume To Mesh Modifier, Weld Modifier, Weighted Normal Modifier, Cloth Modifier ...

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Volume to Mesh Modifier; Weld Modifier; Weighted Normal Modifier; Cloth Modifier; Dynamic Paint Modifier; Explode Modifier; Fluid Modifier; Particle System Modifier; Soft Body Modifier; Editing Point Cloud Objects; Point Cloud; Tools; Segments; Surface Primitives; Motion Tracking & Masking; Selecting Mask Elements; Tracking Marker; Object.

## Volume to Mesh Modifier

### Volume to Mesh Modifier

Working in the opposite direction to the Mesh to Volume modifier, this one takes a volume object that already exists and turns one of the grids it holds into a mesh. Only scalar grids, the density grid being a typical case, are eligible for conversion.

Tip

Reach for a collection instance when you want to duplicate and reposition the generated mesh
on its own, apart from the volume object.

### Options

The Volume to Mesh modifier.

Object
The volume object that serves as the source.

Grid Name
Which grid gets converted, named here. It must be a scalar grid.

Resolution Mode
Sets the means by which the output mesh's resolution is governed.

Grid
Ties the output resolution to whatever resolution the converted grid already carries.
A denser grid therefore yields a denser mesh.
For most situations this is the most efficient choice.

Voxel Amount
Sets roughly how fine the generated mesh comes out.
The voxel size scales itself to the overall size of the volume.

Voxel Size
Locks in a fixed resolution that holds steady even as the volume changes.

Threshold
Any voxel whose value exceeds this is treated as interior to the mesh, and the rest as exterior.
Geometry is then built along the dividing line between interior and exterior voxels.
The term "iso value" is sometimes used for it.

Adaptivity
Comparable to decimating the result, trimming resolution in areas that do not require it.

Smooth Shading
Turns smooth shading on for the mesh that gets produced.

### Example

Converting a cloud-shaped volume to a mesh.

## Weld Modifier

### Weld Modifier

Scan the mesh for clusters of vertices sitting within a set threshold of one another, fuse each cluster, and let the geometry wrapped around it collapse inward: that is what the Weld modifier does.

### Options

The Weld modifier.

Mode
Sets the rule for deciding which vertices get merged.

All :

The merge takes in every bit of geometry, loose parts included.

Connected :

The merge covers only attached geometry, so the modifier leaves loose parts un-joined.

Distance
The largest gap two vertices may sit apart and still be merged.

Only Loose Edges Connected Mode
Restricts collapsing to short edges that touch no face.
Handy, for instance, when stitching together the seams used in cloth simulations.

Vertex Group
With the Vertex Group option active, the modifier touches only those vertices carrying a weight greater than zero.

Invert
Flips which vertices the chosen vertex group covers, so the group instead
marks the vertices the modifier will leave un-merged.

The group's weight values are reversed by this setting.

## Weighted Normal Modifier

### Weighted Normal Modifier

A mesh's custom normals are reworked by this modifier through any of several methods you can pick from. One thing it's good for, among others, is making certain faces read as extremely flat under shading. See Normals for the background on normals and custom normals.

### Options

Weighting Mode
The normals around a vertex are blended into a single custom (per face corner) normal,
each contributing by some weight. Weighting Mode sets how those weights are worked out.

Face Area
Weights by the area of the face a normal comes from.
The larger that face, the heavier its normal counts toward the result.

Corner Angle
Weights by the angle each face makes at the vertex.
This is what Blender falls back on by default when blending face normals into a vertex normal.

Face Area and Angle
The weights come from multiplying the face-area weights by the corner-angle ones.

Weight
Sets how hard the weighting leans on face areas and/or corner angles,
rather like turning up the contrast on a photo.

Set it to 50 and every face carries the same weight.
Go above 50 and faces with larger area or wider angles count for still more (more "contrast").
Drop below 50 and those same faces count for less (less "contrast").

Threshold
A rounding threshold for the weights: when two angles or areas differ by less than it,
they come out with the same weight.

Keep Sharp
Holds onto Sharp edges,
though smoothing still occurs where more than one face sits between any two Sharp edges.

Face Influence
Draws on face weights (weak, medium, or strong) handed out by
the Set Strength tool, or
by a Bevel modifier's Set Strength mode.

Say three faces meet at a vertex carrying the face weights weak, medium, and strong:
the final result then takes only the normal that belongs to the strong face.

Vertex Group
Name a vertex group and the modifier confines itself to those vertices.
The "arrow" button beside it flips the selection (acting only on the vertices outside the vertex group).

## Cloth Modifier

### Cloth Modifier

Think of the Cloth modifier as a wrapper around a Cloth Physics simulation. One handy routine, for example, is to run the sim on a low-poly mesh and then drop a Subdivision Surface Modifier in after the Cloth modifier, lifting the cloth's visual quality while keeping simulation times from ballooning.

### Options

Being just a wrapper, the modifier keeps its actual settings elsewhere, over on the Physics Properties tab.
The Cloth Physics Properties page covers them in full.

### Example

| Cloth example. | Cloth on carved wooden men (made by motorsep). | Cloth example. |

## Dynamic Paint Modifier

### Dynamic Paint Modifier

Think of the Dynamic Paint modifier as a wrapper around a Dynamic Paint Physics simulation.

### Options

Because this modifier is purely a wrapper, its real controls sit on the Physics Properties tab.
For the full rundown, head to the Dynamic Paint Physics Properties page.

## Explode Modifier

### Explode Modifier

By shifting and spinning its faces so they loosely trail the particles its object throws off, the Explode modifier rearranges the mesh geometry, selling the illusion that the mesh is blowing apart, broken up and flung outward.

Nothing shows up from the modifier unless the object it's on has a particle system, since that system is what powers the explosion.

The granularity of the Explode modifier rides on two things together: how many particles get emitted and how many faces there are. Push either one up and you wind up with more separate fragments.

There's a
demo video
that runs through a cube carrying a particle system and an Explode modifier.
(blend-file).

Note

In the stack, place the Explode modifier below the Particle System one,
so the former can pull the data it needs from the latter.

### Options

The Explode modifier, with a Particle System above it.

Particle UV
When set, the U coordinate in that UV Map gets overwritten
with the age of the particle tied to the matching mesh face
(scaled from 0 for particles not yet born up to 1 for dead ones).

The V coordinate is pinned at a flat 0.5.

You could, for instance, shift a fragment's (face's) color across the explosion
by feeding it a texture whose color gradient runs along the U axis.

Show

Unborn
Reveals faces while their attached particles are still unborn.

Alive
Reveals faces while their attached particles are alive.

Dead
Reveals faces while their attached particles are dead.

Cut Edges
Splits the mesh by where particles emit rather than along the existing faces.
The break this gives tends to read as more random.

Size
Once a particle is alive, its size is used to scale the face it's attached to.

Vertex Group
Vertices placed in this group can be spared from the Explode modifier.
At full weight a vertex isn't touched at all,
whereas a lower weight raises the odds of it being affected.

Vertices at zero weight are treated as though they weren't in the group at all,
and explode as normal.

Invert
Flips which vertices the chosen vertex group covers, so the group instead
marks the vertices the modifier will leave undeformed.

The group's weight values are reversed by this setting.

Protect
Tidies the vertex group edges. According to the weights given to that vertex group, it
either shields those faces entirely from the Explode modifier
(which is what a face weight of 1 produces),
or strips protection from them altogether
(which is what a face weight of 0 produces).

Refresh
Reloads the data held in the Explode modifier.

### Known Limitations

### Dynamic Vertex Weights

The vertex weights this modifier draws on are the initial ones.
Modifiers that change weights on the fly won't sway the explosion, since these values are read just once.

## Fluid Modifier

### Fluid Modifier

Think of the Fluid modifier as a wrapper around a Fluid Physics simulation. A handy routine, for example, is to run the sim on a low-poly mesh and then drop a Subdivision Surface Modifier in after the Fluid modifier, lifting the fluid's visual quality while keeping simulation times from ballooning.

### Options

The modifier serves only as a wrapper, so you'll find its genuine options on the Physics Properties tab.
See the Fluid Physics Properties page for the complete picture.

### Example

Example of a liquid simulation.

## Particle System Modifier

### Particle System Modifier

Think of the Particle System modifier as a wrapper around Particle Systems.

Note

Out of the box, the Particle System modifier pays no attention to the modifier stack.
For it to factor in the other modifiers, switch on Use Modifier Stack
over in the Particle properties.

### Options

As a wrapper alone, this modifier keeps its working options on the Particle Properties tab.
The Particle Systems Properties page documents them all.

### Converting Particle Systems

Make Instances Real
Spins up a fresh object out of each instanced object or collection.
The Make Instances Real page goes deeper.

Convert to Mesh
Turns path particles into mesh objects.
The Convert page goes deeper.

### Example

Fur made from particles.
</invoke>

## Soft Body Modifier

### Soft Body Modifier

Think of the Soft Body modifier as a wrapper: it holds a Soft Body Physics simulation rather than doing the work itself.

### Options

Because the modifier only acts as a container, you set its real parameters over in the Physics Properties tab.
For the full rundown, head to the Soft Body Physics Properties.

### Example

The wind cone is a soft body, as the suspension.

## Editing Point Cloud Objects

### Editing Point Cloud Objects

Once you switch a point cloud object into Edit Mode, a handful of basic editing operations become available.

Tip

Need geometry-based editing or downstream processing? Point clouds can be turned into mesh objects and back again.

### Transform

Reference

Mode :

Edit Mode

Menu :

Point Cloud ‣ Transform

The familiar Move , Rotate , and Scale operators apply here too, letting you push selected points around within the cloud.

Reach for them whenever a cluster of points needs to be repositioned, lined up, or reshaped by hand.

### Duplicate

Reference

Mode :

Edit Mode

Menu :

Point Cloud ‣ Duplicate

Shortcut :

Shift - D

Makes a copy of the chosen points and lets you drop the copies into a new spot.

Whatever attributes the source points carry, the duplicates carry too.
- Handy for hand-scattering point clusters or copying a specific region you want to tweak further.

### Set Attribute

Reference

Mode :

Edit Mode

Menu :

Point Cloud ‣ Set Attribute

A pop-up appears showing the active attribute's name along with the value it currently holds for the selected points.
From within it you push a fresh value onto the chosen attribute for every selected point at once.

Reach for this when you want a single attribute — size, color, velocity, and the like — set to one consistent value across a batch of points.

### Delete

Reference

Mode :

Edit Mode

Menu :

Point Cloud ‣ Delete

Shortcut :

X or Delete

Drops the chosen points out of the cloud.

### Separate

Reference

Mode :

Edit Mode

Menu :

Point Cloud ‣ Separate

Shortcut :

P

Spins off the currently selected points into a fresh point cloud object of their own.

Handy when you want to carve a large scan or dataset into smaller, more manageable pieces, or to keep distinct regions of points as separate objects.

## Point Cloud

### Point Cloud

A point cloud object exists to hold many individual points positioned in 3D space.
Where a surface mesh would be overkill or simply impractical — visualizing 3D scan data, particle simulations, or sparse datasets — point clouds shine.

By way of Attributes, every point can carry its own data, covering things like position, color, and beyond.
Down the road, the feature set may grow to cover simulation systems such as particles.

Example of a monkey object represented as a point cloud.

## Tools

### Tools

Select
Select or shift the geometry.

Select Box
Grab geometry by dragging out a box.

Select Circle
Grab geometry by dragging out a circle.

Select Lasso
Grab geometry by sketching a lasso around it.

Cursor
Reposition the 3D Cursor.

Move
The translation tool.

Rotate
The rotation tool.

Scale
The scaling tool.

Scale Cage
Resize an object by manipulating its cage.

Transform
A tool for tweaking an object's position, rotation, and scale together.

Annotate
Sketch free-hand annotations.

Annotate Line
Sketch a straight annotation line.

Annotate Polygon
Sketch a polygon annotation.

Annotate Eraser
Wipe out annotations you drew earlier.

Measure
Gauge distances within the scene.

## Segments

### Segments

### Subdivide

Reference

Mode :

Edit Mode

Menu :

Segments ‣ Subdivide

This operator inserts extra, evenly spaced control points into the middle of the selected segments (grid lines).
The added points hand you finer control over how the surface is shaped.

What you select has to be made of complete rows or columns of the control point grid.

Select only part of the surface's control points and it subdivides along one direction; select them all and it subdivides both ways.

Number of Cuts
How many control points get inserted into each segment.

### Switch Direction

Reference

Mode :

Edit Mode

Menu :

Segments ‣ Switch Direction

Flips the order in which the surface's control points are stored internally, which also reverses the face normals.

See also

Face Orientation Overlay

## Surface Primitives

### Surface Primitives

Reference

Mode :

Object Mode and Edit Mode

Menu :

Add ‣ Surface

Shortcut :

Shift - A

See also

Once a primitive is in the scene, options such as its radius are open
to change.

These are the primitives on offer in the Add Surface menu:

| NURBS curve primitives. | NURBS surface primitives. |

NURBS Curve
Drops in a basic four-control-point curve bent into an arc.

NURBS Circle
Drops in a closed ring of control points shaped into a circle.

NURBS Surface
Drops in a simple patch built on a 4×4 grid whose center points are nudged slightly upward.

NURBS Cylinder
Drops in an open cylinder formed by extruding a NURBS Circle .

NURBS Sphere
Drops in an ordinary sphere whose control points sit at the corners of a cube.

NURBS Torus
Drops in a doughnut shape made by spinning a circle around an axis.

## Motion Tracking & Masking

### Motion Tracking & Masking

Both masking and tracking are carried out inside the Movie Clip Editor.

The Movie Clip Editor.

See Movie Clip Editor for more information on the Movie Clip Editor.

### Workflows

## Selecting Mask Elements

### Selecting Mask Elements

### All

Reference

Mode :

All modes

Menu :

Select ‣ All

Shortcut :

A

Marks every item as selected.

### None

Reference

Mode :

All modes

Menu :

Select ‣ None

Shortcut :

Alt - A

Clears the selection back to empty.

### Invert

Reference

Mode :

All modes

Menu :

Select ‣ Inverse

Shortcut :

Ctrl - I

Picks up whatever wasn't selected and drops whatever was.

### Box Select

Reference

Mode :

All modes

Menu :

Select ‣ Box Select

Shortcut :

B

See Select Box.

### Circle Select

Reference

Mode :

All modes

Menu :

Select ‣ Circle Select

Shortcut :

C

See Select Circle.

### Lasso Select

Reference

Mode :

All modes

Menu :

Select ‣ Lasso Select

Shortcut :

Ctrl - Alt - LMB

See Select Lasso.

### Select Linked

Reference

Mode :

All modes

Menu :

Select ‣ Select Linked

Shortcut :

Ctrl - L

Grabs every curve point tied to the ones already selected.

## Tracking Marker

Point: move the whole marker with RMB, or by dragging the anchor point (the black dot) with LMB; pressing G also moves the whole marker, and pressing G twice moves the marker while leaving the anchor in place (an anchor outside the pattern area appears as a cross joined to the marker position by a dashed line). S scales the whole marker, while pressing S twice scales only the pattern area; R rotates the Pattern — depending on the pivot point used, either spinning patterns about their own centers or rotating whole markers about, e.g., the median point. To match a marker's perspective transform on a plane, edit the individual corners by hand: each corner deforms independently to define the shape, and dragging a corner with LMB repositions it.
Note: deforming a pattern isn't only useful for planar/affine tracking — since only the pixels inside the pattern are considered, it can help specify a better pattern to track even for simple position tracking.
The Search area can't be rotated, which is intentional: deforming the search area makes no sense.

Plane: the plane's bottom-left corner carries X/Y axes (X is red, Y is green) to help read the plane's orientation in space. You'll likely need to adjust the plane object's corners by hand — slide individual corners with LMB, or use the general transform tools G, R, S. Adjusting the corners keeps the plane following the plane defined by the tracks it was originally created from.

## Object

### Object 

Friction
Surrounding-medium friction. Generally friction dampens motion; higher friction means higher viscosity.
Friction appears when vertices move relative to medium.

Mass
Vertex mass value.
Larger mass slows acceleration (except gravity, which proves mass-independent).
Higher mass increases inertia, making deceleration harder.

Control Point
Paint weights using a vertex group for mass values.

## Asset

### Asset

Operations for managing the Asset status of an object.

### Mark as Asset

See Creating an Asset.

### Clear Asset

See Removing Assets.

### Clear Asset (Set Fake User)

See Removing Assets.

## Editing Modifiers

### Editing Modifiers 

Workflows for controlling an object's Modifier Stack.

### Add Modifier 

Reference

Mode:
Object Mode

Menu:
Object ‣ Modifiers ‣ Add Modifier

Opens a menu showing every available modifier type; picking one will place it at the end of the Modifier Stack.

### Copy Modifiers to Selected Objects 

Reference

Mode:
Object Mode

Menu:
Object ‣ Modifiers ‣ Copy Modifiers to Selected Objects

Replicates the complete modifier sequence from the active item to every other chosen item.

### Clear Object Modifiers 

Reference

Mode:
Object Mode

Menu:
Object ‣ Modifiers ‣ Clear Object Modifiers

Removes all modifiers from the chosen objects.

## Show/Hide

### Show/Hide 

Reference

Mode:
All Modes

Menu:
Object ‣ Show/Hide

Show Hidden Objects Alt - H
Reveals any concealed objects.

Hide Selected H
Hides all picked objects.

Hide Unselected Shift - H
Hides every object except those picked.

## Snap

### Snap 

Reference

Mode:
Object, Edit, and Pose Mode

Menu:
Object/Object type ‣ Snap

Shortcut:
Shift - S

The Snap menu offers workflows for placing the selection or the
3D Cursor at exact locations.

These operations are regularly employed to arrange objects, position the cursor
for transform operations, or align elements to the grid or neighboring objects.

### Selection to Grid 

Reference

Mode:
Object, Edit, and Pose Mode

Menu:
Object/Object type ‣ Snap ‣ Selection to Grid

Aligns the chosen content to the nearest grid cell.

In Object Mode, each picked object's origin snaps to the nearest grid intersection. In Edit Mode, the chosen vertices, edges, or faces snap
to the nearest grid spot.

This makes rapid alignment to the grid structure straightforward.

### Selection to Cursor 

Reference

Menu:
Object/Object type ‣ Snap ‣ Selection to Cursor

Places the chosen elements at the 3D Cursor's position.

Optionally, the selection can also be reoriented to match the cursor's
rotation.

### Selection to Cursor (Offset) 

Reference

Menu:
Object/Object type ‣ Snap ‣ Selection to Cursor (Offset)

Positions the selection so its center aligns with the 3D Cursor,
while keeping the spacing between chosen elements intact.

Different from Selection to Cursor, the chosen objects don't gather
at the cursor. Rather, the whole selection is offset to place
its center at the cursor.

### Selection to Active 

Reference

Menu:
Object/Object type ‣ Snap ‣ Selection to Active

Repositions the chosen elements to the Active object's origin.

The active object itself stays still. All other chosen objects
are moved to its origin.

### Cursor to Selected 

Reference

Menu:
Object/Object type ‣ Snap ‣ Cursor to Selected

Positions the 3D Cursor at the center of the current selection.

The exact position depends on the active Transform Pivot Point.

Examples:

- With the Bounding Box Center pivot, Cursor to Selected positions the cursor at the center of the
bounding area surrounding the picked objects' origins.

- With the Median Point pivot, Cursor to Selected puts the cursor at the
mean
of the picked object origins.

### Cursor to World Origin 

Reference

Menu:
Object/Object type ‣ Snap ‣ Cursor to World Origin

Moves the 3D Cursor to the world center at (0, 0, 0).

See also

Center Cursor and Frame All, which repositions the 3D Cursor to the world center and refocuses the 3D Viewport.

### Cursor to Grid 

Reference

Menu:
Object/Object type ‣ Snap ‣ Cursor to Grid

Moves the 3D Cursor to the nearest grid overlay cell.

### Cursor to Active 

Reference

Menu:
Object/Object type ‣ Snap ‣ Cursor to Active

Places the 3D Cursor at the origin of the Active object
(the most recently picked object).

## Align Objects

### Align Objects 

Reference

Mode:
Object Mode

Menu:
Object ‣ Transform ‣ Align Objects

The Align operation arranges multiple selected objects into alignment along a specific axis.

### Options 

High Quality
Engages more complex mathematics to determine alignment spots precisely.
When using positive or negative bounding box alignment,
if one or more chosen objects carry rotation modifications
(or delta rotation changes), toggling High Quality ensures their bounding box is computed accurately for all three world axes.

Align Mode
The Align Mode parameter governs which portion of the objects will be lined up:

Centers:
The object centers.

Positive Sides/Negative Sides:
The positive or negative regions (relative to world axes) of their respective bounding areas.

Relative To
The Relative To setting specifies what reference point to align objects to:

Active:
The active object.

Selection:
The mean location of the selection.

3D Cursor:
The 3D Cursor's current position.

Scene Origin:
The world center.

Align X, Y, Z
Selects which world axis to line objects up along.
