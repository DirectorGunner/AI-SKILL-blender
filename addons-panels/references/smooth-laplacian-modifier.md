# Smooth Laplacian Modifier, Data Transfer Modifier, Vertex Weight Edit Modifier, Vertex Weight Mix Modifier ...

> Blender Add-ons, Panels, and Properties reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Smooth Laplacian Modifier; Data Transfer Modifier; Vertex Weight Edit Modifier; Vertex Weight Mix Modifier; Selecting Point Cloud Objects; Surface; Surface Structure; Marker.

## Smooth Laplacian Modifier

The Smooth Laplacian modifier reduces noise on a mesh's surface with minimal change to its shape, and can also exaggerate the shape using a negative Factor. It's useful for objects reconstructed from the real world that contain undesirable noise — it removes the noise while preserving desirable geometry and the original model's shape. It's based on a curvature-flow Laplace Beltrami operator in a diffusion equation.
Hint: meshes with many vertices — more than ten thousand (10,000) — may take several minutes to process, so test on small portions of the mesh before running it on the entire model.

Options:
Repeat — repetitions run the smoothing more than once; each repetition recalculates the mesh's flow curvature and so removes more noise per iteration using a small Factor < 1.0. At 0, no smoothing is done.
Note: more repetitions take longer to calculate, so beware of doing so on meshes with a large number of vertices.
Axis — toggle buttons to enable/disable deforming vertices in the X, Y, and/or Z axis directions.
Lambda Factor — controls how far each vertex is displaced along the flow curvature: with a small Factor you remove noise without affecting desirable geometry; with a large Factor you get smoothed shapes at the cost of fine geometry details; with a negative Factor you enhance the shape while preserving desirable geometry; and when the Factor is negative, multiple iterations can magnify the noise.
Lambda Border — since curvature flow can't be calculated on border edges, they're handled separately by a much simpler method, with this property controlling its influence: positive values smooth the vertex positions, while negative values "enhance" them by transforming them in the opposite direction.
Preserve Volume — the smoothing can cause shrinkage, significant at large Factor or Repeat values; use this option to reduce that effect.
Normalized — when enabled, results depend on face sizes; when disabled, geometry spikes may occur.
Vertex Group — a vertex group name to constrain the effect to a group of vertices only, allowing selective, real-time smoothing or enhancing by painting vertex weights.
Invert — invert the influence of the selected vertex group, so the group now represents vertices that will not be deformed by the modifier; the setting reverses the group's weight values.

See also the Smooth Modifier.

## Data Transfer Modifier

### Data Transfer Modifier

Certain categories of data, UV maps, color attributes, custom normals, and the like, get copied from one outside mesh onto the modified mesh by the Data Transfer modifier.

Working through the modified mesh element by element (vertex, edge, or face), the modifier hunts down one or several matching elements over in the source mesh and then interpolates across the values those source elements hold.

Transferring a UV map from a low resolution mesh to a high resolution one
using interpolation.

See also

Transfer Mesh Data Operator

### Usage

- Pick the Source mesh whose data you want to copy.

- Should the source and modified meshes not sit on top of one another in world space,
clear Object Transform (the axes icon beside the source mesh).

- Pick which kind of data to copy (vertex groups, UV maps, and so on).

- To copy just one particular vertex group, UV map, or similar, choose it under Layer Selection .

- If the vertex groups or similar you want to copy aren't yet present on the modified mesh,
hit Generate Data Layers to make them.

### Options

Source
The mesh object that data is copied from.

Object Transform
Decides whether the world space transforms of the source and destination objects are taken into account.
Leave it off and the modifier behaves as if both objects share the same position
along with default rotation and scale.

Mix Mode
Sets how the incoming source data is merged with the data already on the destination mesh.

Replace
Blend between the original and the new value by way of Mix Factor .

Above Threshold
Swaps in the destination value when it sits at or above Mix Factor .
With multi-component data such as colors, the threshold gets weighed against the average of
those components.

With boolean data such as Freestyle Mark , this gives you a logical AND:
set the Mix Factor to 0.5 or above and the destination mesh keeps a mark only on
edges or faces that were marked already and carry a mark in the source mesh too.

Below Threshold
Swaps in the destination value when it sits at or below Mix Factor .
With multi-component data such as colors, the threshold gets weighed against the average of
those components.

With boolean data such as Freestyle Mark , this gives you a logical OR:
set the Mix Factor to 0.5 or above and the destination mesh keeps a mark on
edges or faces that were marked already or carry a mark in the source mesh.

Mix
Blend the source value into the destination value, an alpha blend for color attributes being one case. Then interpolate using Mix Factor .

Add
Sum the source and destination values, then blend by way of Mix Factor .

Subtract
Take the source value away from the destination value, then blend by way of Mix Factor .

Multiply
Multiply destination by source, then blend by way of Mix Factor .

Mix Factor
The blend amount between the original destination value and the freshly computed one.
Where Mix Mode is Above Threshold or Below Threshold , it serves as a threshold instead.

Vertex Group
Lets the Mix Factor be tuned on a per-element basis.

Invert
Flip the vertex group weights, turning each into 1 - weight.

Generate Data Layers
Click to lay down any data layers that are missing, such as vertex groups present on the source mesh but
not yet on the modified one. Since the modifier won't do it for you, be sure to hit
this button (or add the missing layers yourself), or the transfer may fail.

Any layers laid down this way are left behind once the modifier is removed.

Data Types
The Custom Normals , Colors , UVs and similar toggle buttons flag which data
gets transferred.

Mapping
Sets the way a matching source element (or elements) is found for each destination element.
The choices are laid out in the Mapping section further down.

Layer Selection
Which source layers get copied across to the destination mesh (every vertex group,
or one specific vertex group, for instance).

Layer Mapping
Sets how the destination layer is matched to a given source layer: by name or by order.

Islands Precision
Governs the computation that keeps a destination face from pulling UV coordinates out of
mismatched source UV islands (regions walled off by seams).
Hold it at 0.0 and there's no island handling at all; raise it and correctness improves
at the expense of more computation.

Small figures around 0.02 usually do the trick, but mapping from
a very high-poly source onto a very low-poly destination may force you to push it up considerably.

### Mapping

### Topology

Pairs the elements purely by index. For this both meshes have to carry the same
count of elements, ordered the same way. It fits best when
the destination mesh is a deformed copy of the source.

See also

Sort Elements, which lets you give both objects
a matching element order.

### One-To-One Mappings

Each of these mappings picks exactly one source element per destination element.

Vertex Data

Nearest Vertex
Takes the closest source vertex.

Nearest Edge Vertex
Takes the closest source vertex lying on the closest source edge (judged by midpoint distance).

Nearest Face Vertex
Takes the closest source vertex lying on the closest source face (judged by midpoint distance).

Edge Data

Nearest Vertices
Takes the source edge whose vertices come closest to those of the destination edge.

Nearest Edge
Takes the source edge whose midpoint comes closest to the destination edge's.

Nearest Face Edge
Takes the closest source edge on the closest face, both judged by midpoint distance.

Face Corner Data
A face corner means a vertex considered in the setting of a face. UV maps are where you meet
it most: every face corner can hold its own UV coordinate, or put another way, a single 3D vertex
may map to several UV vertices, one for each face.

Nearest Corner and Best Matching Normal
Takes the source corner closest to the destination corner that also has the most alike
split normal.

Nearest Corner and Best Matching Face Normal
Takes the source corner closest to the destination corner that also has the most alike
face normal.

Nearest Corner of Nearest Face
Takes the closest source corner on the closest source face.

Face Data

Nearest Face
Takes the closest source face, judged by midpoint distance.

Best Normal-Matching
Shoot a ray out of the destination face's centerpoint along that face's normal
and take whichever source face it strikes.

### Interpolated Mappings

Mappings of this kind can take in several source elements and interpolate across their values.

Vertex Data

Nearest Edge Interpolated
Locate the closest point on the nearest source edge, then let that point drive interpolation between
the edge's two vertex values.

Nearest Face Interpolated
Locate the closest point on the nearest source face, then let that point drive interpolation between
the face's vertex values.

Projected Face Interpolated
Cast the destination vertex along its normal onto a source face,
then use where it lands to interpolate among the face's vertex values.

Edge Data

Projected Edge Interpolated
Track down source edges by projecting from several points spread along the destination edge
(each one cast along the interpolated normals of that destination edge's vertices).
Then interpolate across the values of the source edges turned up this way.

Face Corner Data

Nearest Face Interpolated
Locate the closest point on the nearest source face, then let that point drive interpolation between
the face's corner values.

Projected Face Interpolated
Cast the destination corner along its normal onto a source face,
then use where it lands to interpolate among the face's corner values.

Face Data

Projected Face Interpolated
Find source faces by shooting rays from several points across the destination face along that destination
face's normal. Then interpolate across the values of these source faces.

### Topology Mapping

Note

The panel's name notwithstanding, none of these settings touch the Topology mapping type.

Max Distance
With the checkbox on, any source and destination elements separated by more
than the stated distance are ruled out as matches.

Ray Radius
The radius the ray casting begins from.

With some mapping types the operator fires off a run of ray casts from each destination
element to track down matching source elements. Those casts open at the given radius and
swell steadily until either a match turns up or a ceiling is hit.

Start small and the results get sharper, though performance suffers if it's so
tiny it has to keep growing. Start large and performance is better,
but the matches may come out less than ideal.

As a rule, keep the radius low for dense source meshes and high for simple ones.

## Vertex Weight Edit Modifier

### Vertex Weight Edit Modifier

This modifier's job is to edit the weights a vertex group holds.

Broadly, here is what it runs through for each vertex:

- (Optional) Does the mapping, either through one of the built-in functions or a custom mapping curve.

- Brings the influence factor to bear, optionally alongside the vertex group or texture mask
(0.0 keeps the original weight, 1.0 takes the fully mapped weight).

- Writes the weight back onto the vertex, and may optionally drop the vertex
from the group when its weight falls below a set threshold, or add it when its weight climbs above one.

Important

Weight values get implicitly clamped by this modifier into the usual (0.0 to 1.0) span.
Anything under 0.0 snaps to 0.0, and anything over 1.0 snaps to 1.0.

Note

The reworked weights can be inspected in Weight Paint Mode.
By the same token, you'll need to switch off the Vertex Weight Edit modifier
to see the vertex group's original weights as you edit them.

### Options

The Vertex Weight Edit modifier panel.

Vertex Group
The vertex group that gets affected.

Default Weight
The weight handed by default to every vertex outside the given vertex group.

Group Add
Pulls vertices whose final weight tops Add Threshold into the vertex group.

Group Remove
Drops vertices whose final weight sits under Remove Threshold from the vertex group.

Normalize Weights
Rescales the vertex group's weights so their relative spacing holds
while the lowest and highest values stretch across the full 0 - 1 range.

### Falloff

Falloff Type
The kind of mapping used.

Linear
No mapping applied.

Custom Curve
Lets you shape the mapping yourself with a curve.

Sharp, Smooth, Root and Sphere
The standard mapping functions, running from spikiest through to roundest.

Random
Hands each vertex a random value.

Median Step
Produces binary weights (0.0 or 1.0), splitting at 0.5.

Invert
Turns the falloff inside out.

### Influence

The three Vertex Weight modifiers all share these settings.

Global Influence
The modifier's influence taken as a whole
(0.0 leaves the vertex group's weights as they were, 1.0 is the standard influence).

Important

Influence acts on weights only; setting it to 0.0 won't stop vertices from being
added to or removed from the vertex group.

On top of that, per-vertex fine control is available through either a vertex group or a texture
(the two being mutually exclusive). Their per-vertex values get multiplied by the Global Influence .

For the full reference, see common masking options.

### Example

What follows shows a range of effects produced with the Vertex Weight Edit modifier
(paired with the Vertex Weight Proximity modifier)
to build the weights that drive the Displace modifier.

| Concave-type mapping curve. |
| No mapping curve (linear). |
| Convex-type mapping curve. |

Vertices with a computed weight below 0.1 removed from the vertex group.

The blend-file,
`TEST_2` scene.

## Vertex Weight Mix Modifier

### Vertex Weight Mix Modifier

Drawing on a selection of operations, this modifier folds a second vertex group (or simply a flat value) into the vertex group it acts on.

Important

Weight values get implicitly clamped by this modifier into the usual (0.0 to 1.0) span.
Anything under 0.0 snaps to 0.0, and anything over 1.0 snaps to 1.0.

Note

The reworked weights can be inspected in Weight Paint Mode.
By the same token, you'll need to switch off the Vertex Weight Mix modifier
to see the vertex group's original weights as you edit them.

### Options

The Vertex Weight Mix modifier panel.

Vertex Group A, B

- A : The vertex group that gets affected.

- B : The second vertex group folded into the affected one.
Leave it blank when you only mean to mix in a flat value.

Invert Weights A/B
Flips the vertex group's influence.

Default Weight A, B

- A : The weight handed by default to every vertex outside the given vertex group.

- B : The weight handed by default to every vertex outside the given second vertex group.

Vertex Set
Picks which vertices get affected.

All :

Hits every vertex, paying no mind to what the vertex groups hold.

Vertex Group A :

Hits only the vertices belonging to the affected vertex group.

Vertex Group B :

Hits only the vertices belonging to the second vertex group.

Vertex Group A or B :

Hits only the vertices belonging to at least one of the two vertex groups.

Vertex Group A and B :

Hits only the vertices belonging to both vertex groups.

Important

With All vertices , Vertices from group B or Vertices from one group in play,
some vertices may end up added to the affected vertex group.

Mix Mode
Sets how the affected group's weights are reshaped by the other group's weights.

Replace :

Overwrites the affected weights with the second group's weights.

Add :

Tacks Group B's values onto Group A's.

Subtract :

Takes Group B's values away from Group A's.

Multiply :

Multiplies Group A's values by Group B's.

Divide :

Divides Group A's values by Group B's.

Difference :

Takes the smaller of the two values from the larger.

Average :

Sums the two values and halves the result.

Minimum :

Keeps whichever weight is smaller out of VGroup A's and VGroup B's.

Maximum :

Keeps whichever weight is larger out of VGroup A's and VGroup B's.

Normalize Weights
Rescales the vertex group's weights so their relative spacing holds
while the lowest and highest values stretch across the full 0 - 1 range.

### Influence

These settings are common to all three Vertex Weight modifiers;
the Vertex Weight Edit modifier page has the details.

### Example

What follows uses a texture along with the mapping curve to build the weights that feed
the Wave modifier.

| Using intensity. | Using Red. | Using Saturation. |

| A customized mapping curve. | Custom Mapping disabled. | Custom Mapping enabled. |

The blend-file,
`TEST_4` scene.

## Selecting Point Cloud Objects

### Selecting Point Cloud Objects

Working with point clouds in Edit Mode gives you a set of selection operators, covered here.
With them you can swiftly mark or clear points ahead of further editing or transformation.

### All

Reference

Mode :

Edit Mode

Menu :

Select ‣ All

Shortcut :

A

Marks every point in the cloud as selected.

### Select None

Reference

Mode :

Edit Mode

Menu :

Select ‣ None

Shortcut :

Alt - A

Clears the selection from any points currently selected in the cloud.

### Select Invert

Reference

Mode :

Edit Mode

Menu :

Select ‣ Invert

Shortcut :

Ctrl - I

Flips each point's selection state across the whole cloud:

- Anything that had been selected is now cleared.

- Anything that had been left out is now picked up.

A quick way to grab whatever you didn't already have selected.

### Select Random

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select Random

Picks out a random handful of the cloud's points.

Seed
The starting number fed to the pseudo-random generator.
Change it and a different set of points ends up randomly chosen.

Probability
A figure from 0.0 to 1.0 setting what share of points get picked.
Set it to 0.25, for instance, and about a quarter of the points are selected.

Useful for procedural modeling, scattering, or trying out effects with a randomly spread selection.

## Surface

### Surface

### Transform

Reference

Mode :

Edit Mode

Menu :

Surface ‣ Transform

Tools for shifting control points around.

Move, Rotate, Scale
See Basic Transformations.

To Sphere, Shear, Bend, Push/Pull, Warp, Randomize
See Mesh Transformations.

Move/Scale Texture Space
See Texture Space.

### Mirror

Reference

Mode :

Edit Mode

Menu :

Surface ‣ Mirror

Shortcut :

Ctrl - M

See Mirror.

### Snap

Reference

Mode :

Edit Mode

Menu :

Surface ‣ Snap

Shortcut :

Shift - S

See the Snap menu,
as well as the snapping options.

### Spin

Reference

Mode :

Edit Mode

Menu :

Surface ‣ Spin

Just like its mesh namesake, this operator sweeps the chosen control points
again and again along a circle — one sitting on
the 3D Cursor and lying flat against the plane you're viewing from.
Weights on the freshly made control points are tuned
to trace a circle, and along the extrusion direction the surface gets flagged Cyclic , Bézier , and Endpoint
(see Active Spline).

### Add Duplicate

Reference

Mode :

Edit Mode

Menu :

Surface ‣ Add Duplicate

Shortcut :

Shift - D

Copies the selected control points and builds a brand-new surface from them.
The fresh control points land in Move mode: drag the mouse to set
where they go, then click LMB to lock it in. Otherwise,
hit RMB or Esc to leave them where they started.

Keep in mind that your selection has to form one valid sub grid.
Otherwise the duplication aborts with an error.

### Split

Reference

Mode :

Edit Mode

Menu :

Surface ‣ Split

Shortcut :

Y

Detaches the selected sub grid from the rest of the surface while leaving it inside
the same Surface object. Border control points get copied, so the
original surface and the split-off one each keep their own.

For this to work, the sub grid has to be built from whole rows or whole columns of the surface grid — one or more of them.

### Separate

Reference

Mode :

Edit Mode

Menu :

Surface ‣ Separate

Shortcut :

P

Detaches the selected sub grid from the rest of the surface and relocates it into
a new Surface object. Border control points get copied, so the
original surface and the separated one each keep their own.

Again, the sub grid has to be made up of one or more entire rows or entire columns of the surface grid.

### Toggle Cyclic

Reference

Mode :

Edit Mode

Menu :

Surface ‣ Toggle Cyclic

Shortcut :

Alt - C

A popover appears with Cyclic U and Cyclic V options. Picking one closes (makes cyclic) or opens (makes non-cyclic) the surface along that direction.

When a surface is cyclic, the final row or column of its control point grid loops
back to meet the first. A cylinder runs cyclic in either the U or V direction, whereas
a sphere is cyclic in both.

See also

The Cyclic settings are also in the Active Spline
panel in the Sidebar.

### Set Spline Type

Reference

Mode :

Edit Mode

Menu :

Surface ‣ Set Spline Type

This feature only works for Curves.

### Show/Hide

Reference

Mode :

Edit Mode

Menu :

Surface ‣ Show/Hide

Shortcut :

H , Shift - H , Alt - H

Hides the selected or unselected control points, or brings every hidden
control point back into view.

Out of the box, unhiding control points also adds them to the selection.
Stop that by clearing the Select option in the Adjust Last Operation panel.

### Cleanup

Reference

Mode :

Edit Mode

Menu :

Surface ‣ Clean Up

This feature only works for Curves.

### Delete

Reference

Mode :

Edit Mode

Menu :

Surface ‣ Delete

Shortcut :

X , Delete

Strips out the selected Vertices (control points) or Segments (lines). Either way,
your selection has to be one or more complete rows or columns of the surface grid.

Vertices
Wipes out the selected control points. Fresh grid lines stitch the gap shut so the surface
remains a single piece.

Segments
Wipes out the lines plus the control points caught between the outermost selected control points.
This time the gap stays open, with no bridging.

Dissolve Vertices
This feature only works for Curves.

Before and after deleting a row of control points.

## Surface Structure

### Surface Structure

Both Surfaces and Curves lean on Bézier or NURBS splines to build smooth geometry out of a set of control points. Where they part ways is in the output:
a Curve yields a line, whereas a Surface yields a sheet.

A single Surface object may hold several disconnected surfaces.
Whichever one is selected in Edit Mode goes by the name
"active spline."

### Control Point Grid

You might compare a Surface to a mesh carrying a
Subdivision Surface Modifier,
but the Surface is stricter: its control points have to sit in a rigid grid, where
every "row" marked by a yellow line carries the same number of
control points, and every "column" marked by a pink line does too.
Extending the surface is only possible by
extruding an entire row or column.

From the Active Spline panel you decide,
for each grid direction, whether the surface is cyclic (closed) and whether it
runs on Bézier or NURBS.

### Weights

To fine-tune the shape, change the weight of individual control
points over in the Transform Panel of the Sidebar.

Note that the relevant property goes by the name W ; a separate property labelled Weight
also exists, but that one serves as the Goal Weight for soft body simulations.

A control point with a higher weight pulls the surface towards it.

Note

Give every control point the same weight and they offset one another,
leaving the surface looking exactly as it did. For any effect to show, the
weights have to differ.

Pure shapes such as cylinders and spheres depend on weights to come out right.
The primitives in the Add menu
arrive with these already set.

Control point weights on a spherical Surface.

## Marker

The Marker panel contains numerical marker properties.

Marker schematic showing components.

Enabled
Toggles marker influence on the current frame.

Position X, Y
Screen-coordinate marker position at the frame.

Offset X, Y
Screen-coordinate anchor offset from pattern center.

Pattern Area Width, Height
Screen-coordinate pattern area dimensions.

Search Area X, Y
Screen-coordinate search position relative to marker.

Search Area Width, Height
Screen-coordinate search area dimensions.
