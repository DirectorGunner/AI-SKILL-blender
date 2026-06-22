# Remeshing, Metaball Properties, Mesh To Volume Modifier, Screw Modifier ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Remeshing; Metaball Properties; Mesh to Volume Modifier; Screw Modifier; Vertex Weight Proximity Modifier; Normal Edit Modifier; Point Cloud Properties; Active Spline.

## Remeshing

### Remeshing

Blender includes a handful of tools that rebuild a mesh into roughly the same shape but with fewer faces, more faces, or cleaner topology.

Remeshing to clean up messy geometry.

### Remeshing

Reference

Mode :

Object Mode, Sculpt Mode

Panel :

Properties ‣ Data ‣ Remesh

Remeshing regenerates the mesh with uniform topology on its own. Crank the resolution high to densify a simple mesh for sculpting, or drop it low to thin out and tidy overly dense or messy geometry, such as a sculpt or a 3D scan.

Note

- Remeshing only acts on the original mesh data, ignoring modifiers, shape keys, and the like.

- Remeshing is not possible on objects with a Multiresolution Modifier.

The Remesh panel offers two modes:

### Voxel

The Voxel remesher drops the mesh into a virtual 3D grid, finds which grid points sit nearest the outer surface, and lays new vertices there. The upshot is uniform topology with no inner, self-intersecting geometry.

Where it helps:

- Re-resolving or generally tidying a mesh you intend to sculpt. Set the resolution up front and you can keep Dyntopo off, dodging its performance hit.

- Tidying a mesh ahead of 3D printing.

- Producing a stripped-down stand-in mesh for physics simulation.

Because that topology is just a plain grid, though, skip the Voxel remesher for:

- Building topology for a mesh that will deform (an animated character, say). That has to follow the geometry's flow, and since no flawless automatic tool exists yet, it's a manual job. See Retopology.

- Feeding a Subdivision Surface or Multiresolution Modifier. Quad mode wins there.

- Trimming the face count of a mesh whose geometry is otherwise fine. Decimate Geometry suits that better.

Voxel remesh has the following settings:

Voxel Size
How big each voxel (3D grid cell) is. Small values yield a dense, detailed result; large ones a coarse, lightweight one.

Adaptivity
Trims the face count by easing off detail where it isn't needed. Any value above zero turns Fix Poles off and may bring in triangles.

Fix Poles
Trades a little speed to thin out Poles for cleaner topological flow.

Preserve

Volume
Aims to hold the mesh's original volume. (On complex meshes this can slow the operator.)

Attributes
Carries attributes over to the rebuilt mesh, the paint mask, any face sets, color attributes, and the rest.

See also

The Remesh Modifier does the same job non-destructively and brings additional remeshing methods.

### Quad

The Quad remesher runs the Quadriflow algorithm, which can yield nicer output but takes longer. It won't replace the Voxel remesher, since it leaves intersecting geometry uncleaned.

Where it helps:

- Feeding a Subdivision Surface or Multiresolution Modifier.

Where it's a poor fit:

- Prepping a mesh for sculpting or 3D printing; the Voxel remesher fits that better.

- Building final topology for a mesh that will deform (an animated character, say). That has to follow the geometry's flow, and since no flawless automatic tool exists yet, it's a manual job. See Retopology.

- Trimming the face count of a mesh whose geometry is otherwise fine. Decimate Geometry suits that better.

Quadriflow Remesh
Brings up a pop-up for the remesh parameters.

Use Mesh Symmetry
Builds a symmetrical result from the Mesh Symmetry options.

Preserve Sharp
Aims to keep the mesh's sharp features. (On complex meshes this can slow the operator.)

Preserve Mesh Boundary
Aims to hold the mesh's original volume. (On complex meshes this can slow the operator.)

Preserve Attributes
Carries attributes over to the rebuilt mesh, the paint mask, any face sets, color attributes, and the rest.

Smooth Normals
Applies Shade Smooth to the result.

Mode
How the detail level for the new mesh gets set.

Ratio :

Target a face count as a fraction of the current mesh.

Edge Length :

Target an edge length for the new mesh.

Faces :

Target an absolute face count for the new mesh.

Seed
Random Seed for the solver; change it and the remesher lays out the quads differently.

### Retopology

The automatic remeshers rarely give topology that deforms well, so once you've sculpted a character and want it simplified for animation, you'll usually redo the topology by hand, a process called retopologizing.

The usual approach is to lay a new mesh over the original, then reshape it until it wraps the original fully and matches its form.

- The 3D Viewport's Retopology overlay helps, letting the original show through the new mesh and vice versa, without the far-side geometry distracting you the way X-Ray would.

- The Poly Build tool lets you add, edit, and delete faces quickly.

- Lean on Snapping to seat new vertices on the original mesh.

## Metaball Properties

All metas of the same family in a scene interact collectively. Settings in the Metaball section apply to the active family. When editing individual elements, the Active Element panel displays their per-element controls.

The Metaball panel in Object and Edit Mode contains family-level settings.

Viewport Resolution controls how fine the computed mesh appears in the 3D view, from finest to coarsest detail.

Render Resolution sets the mesh fineness used in final renders, also ranging from finest to coarsest.

As a visualization technique, lowering Resolution and raising Threshold while setting Stiffness just above Threshold reveals the mathematical directing structure underneath. A meta cube with Resolution at 0.410, Threshold at 5.0, and Stiffness at 5.01 clearly shows its underlying cubic core.

Influence Threshold defines the field strength at which the surface appears. Higher values increase the merging influence between metas. Influence can be positive (attraction, stretching toward each other) or negative (repulsion, pushing apart).

Update on Edit provides four visualization modes during transformation:

Always shows the full computed mesh during edits.

Half displays the mesh at half the viewport resolution while transforming.

Fast hides the mesh during manipulation.

Never suppresses mesh visibility entirely (only visible at render time—generally not recommended).

The Active Element panel controls individual meta properties visible in Edit Mode.

Type switches the element's underlying shape.

Stiffness determines the influence range of that specific element, controlling how readily it deforms when approached by other metas. Low values cause deformation from farther away; high values require closer proximity. The stiffness appears as a green ring and can be scaled directly.

The green ring must exceed the Threshold value to be visible.

Radius controls the element's physical size (equivalent to object-mode scaling). The white ring displays the radius and can be scaled.

Negative toggles whether the element attracts or repels neighboring metas.

Positive influence stretches surfaces toward each other as field boundaries overlap. Negative influence creates repulsion.

Note: negative-influenced metas are invisible in the viewport—only their boundary rings appear.

Hide conceals selected metas while disabling them from the field computation. This is useful for temporarily simplifying complex arrangements.

Boundary rings remain always visible in Edit Mode; selection circles appear in Object Mode.

## Mesh to Volume Modifier

This modifier (volume objects only) converts mesh geometry into a new volume density grid. Previous volume grids are discarded; the modifier typically targets an empty volume object.

Object references the mesh that determines volume generation.

Density controls visual density during rendering.

Interior Band Width sets the maximum distance of voxels from the mesh surface included on the inside.

Resolution Mode: Voxel Amount approximates the total voxel count along the mesh's diagonal (changes with mesh size), Voxel Size specifies exact voxel dimensions (better for animation rendering to avoid inter-frame artifacts).

## Screw Modifier

This modifier resembles the Screw tool; it takes a profile object (mesh or curve) and creates a helix.

Angle specifies degrees per single revolution.

Screw defines the height of one helix iteration.

Iterations sets the number of revolutions.

Axis selects the helix build direction.

Axis Object names an object defining the axis direction.

Object Screw derives iteration height from the distance to the Axis Object.

Steps Viewport and Render set the subdivision count per revolution for viewport display and rendering respectively; higher render steps improve quality.

Merge unifies vertices on the rotation axis using a triangle fan to close endpoints.

Merge Distance sets the proximity threshold for axis-based merging.

Stretch UVs stretches UV coordinates from 0.0 to 1.0 across the helix when present.

Smooth Shading outputs smooth-shaded faces instead of flat.

Calculate Order reorders edges to prevent normal and shading problems (meshes only, not curves).

Flip reverses normal direction.

Profile alignment is critical: orient the profile perpendicular to the cardinal direction rather than to the screw axis itself.

## Vertex Weight Proximity Modifier

### Vertex Weight Proximity Modifier

What this modifier does is set a chosen vertex group's weights from how far the object (or its individual vertices) sits from a second target object (or that object's geometry).

Warning

Weight values get implicitly clamped by this modifier into the usual (0.0 to 1.0) span.
Anything under 0.0 snaps to 0.0, and anything over 1.0 snaps to 1.0.

Note

The reworked weights can be inspected in Weight Paint Mode.
By the same token, you'll need to switch off the Vertex Weight Proximity modifier
to see the vertex group's original weights as you edit them.

### Options

The Vertex Weight Proximity modifier panel.

Vertex Group
The vertex group that gets affected.

Target Object
The object that distances are measured from.

Proximity Mode

Object Distance
Take the gap between the modified mesh object and the target object as the
weight applied to every vertex in the affected vertex group.

Geometry Distance
Measures from each vertex to the target object, or to its geometry.

Vertex
Each vertex's weight comes from how far it lies from the target object's closest vertex.

Edge
Each vertex's weight comes from how far it lies from the target object's closest edge.

Face
Each vertex's weight comes from how far it lies from the target object's closest face.

Note

Turn on more than one and the shortest distance wins.
Where the target object carries no geometry (an empty or camera, say),
the object's own location is used instead.

Lowest
The distance that maps to a weight of 0.0.

Highest
The distance that maps to a weight of 1.0.

Tip

Push Lowest above Highest and the mapping runs the other way.

Normalize Weights
Rescales the vertex group's weights so their relative spacing holds
while the lowest and highest values stretch across the full 0 - 1 range.

### Falloff

Type
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

All three Vertex Weight modifiers hold these settings in common;
see the Vertex Weight Edit modifier page for the rest.

### Example

The example below drives a Wave modifier on the fly through a vertex group
whose values come from distance to a target object:

The blend-file,
`TEST_1` scene.

## Normal Edit Modifier

### Normal Edit Modifier

Custom normals are what the Normal Edit modifier works on, whether editing existing ones or producing new ones. A small set of straightforward parametric methods does the computing, which makes it rather useful for game development and architectural work, and the normals it generates then get blended back together with whatever was already there.

### Options

Normal Edit Modifier.

Radial
Points the normals along the (origin, vertex_coordinates) vector, so they all appear to fan out
from the chosen center point, as though shed from the surface of an ellipsoid.

Directional
Aims every normal so it converges on a chosen target object.

Target
Uses this object's origin as the point of reference while the normals are generated.

Optional in Radial mode, mandatory in Directional one.

Parallel Normals
Runs all the normals parallel to the line joining the two objects' origins,
instead of letting them converge on the target's origin.

Only relevant in Directional mode.

### Mix

Mix Mode
Sets how the freshly generated normals act on the existing ones.

Keep in mind that Multiply here isn't a cross product but a quicker per-component multiplication.

Mix Factor
How much of the generated normals gets folded into the existing ones.

Vertex Group
Gives per-item fine control over the mix factor. The arrow button to the right flips the vertex group's influence.

Max Angle
Bars any newly generated normal from sitting at an angle to its original beyond this threshold.
Useful for heading off drastic shifts, which could even flip the front and back of a face,
and with that bring on shading artifacts.

/ Lock Polygon Normals
Stops polygons from flipping (front and back swapping) where their normal no longer agrees with
the side their corners' custom normals point toward. Can likewise help head off shading trouble.

### Offset

Nudges the modified object's origin by an offset before it's used to generate normals.

This matters only in Radial mode where no Target Object is given,
and in Directional mode where Parallel Normals is turned on.

### Usage

You might reach for this modifier to rapidly produce radial normals on low-poly tree foliage, or to
"fix" the shading of toon-style rendering by bending the default normals part-way…

Tip

For richer normal work, you can transfer normals from one mesh onto another;
see the Data Transfer Modifier.
The Weighted Normals modifier is another tool
some shading effects can draw on.

### Example

Editing custom normals to point towards a given direction
(blend-file).

On the left the tree mesh keeps its normals untouched, while on the right a Normal Edit modifier bends them
toward the camera. Games lean on this shading trick a lot to fake scattering through trees and other foliage.

## Point Cloud Properties

### Point Cloud Properties

### Attributes

Each point in a cloud carries data fields, and the Attributes panel is where those fields are listed.
Properties such as a point's location, its size, its color, and its motion are all defined through these attributes.

Browsing, creating, editing, and removing attributes all happen through the List View interface.

### Attribute Types

Point cloud objects ship with a set of common built-in attributes, listed below:

See also

Built-In Attributes covers the broader range of attribute types found across Blender's geometry system.

| Name | Type | Domain | Description |
| position | Vector | Point | Holds the point's 3D coordinates within the object's own local space. |
| radius | Float | Point | Sets how large each point appears (its visual radius) when drawn or rendered. |
| color | Color | Point | The point's display color, applied during viewport drawing or shading. |
| id | Integer | Point | Gives each point a one-of-a-kind identifier, handy for keeping references stable over time. |
| velocity | Vector | Point | Records which way the point is moving and how fast (used for simulations or motion blur, for example). |

Custom Attributes
Particles can be handed a custom attribute to carry a characteristic of your own choosing.

Name
What the attribute is called.

Data Type
Which kind of data the attribute will hold.

Float :

Floating-point value

Integer :

32-bit integer

Vector :

3D vector with floating-point values

Color :

RGBA color with floating-point precision

Byte Color :

RGBA color with 8-bit precision

String :

Text string

Domain
Which kind of element holds the attribute.
For now, Point is the only domain an attribute can live on.

### Custom Properties

Point cloud objects can also receive custom properties of their own.
Rather than living per point, these properties are attached at the object level.

The Custom Properties
documentation walks through how to add and work with them.

## Active Spline

### Active Spline

Reference

Editor :

3D Viewport

Mode :

Edit Mode

Panel :

Sidebar ‣ Item ‣ Active Spline

The properties of whichever surface is currently active live in the Active Spline panel.

Active Spline panel.

Cyclic U/V
Turn this on and the surface's last row/column loops back to the first,
forming a closed loop.

Bézier U/V
Turn this on and, along the row/column direction, the surface is built from a chain of Bézier splines
in place of a NURBS curve.

Endpoint U/V
Sets whether the surface reaches all the way to the edges of its control point grid.

Surface with Endpoint U enabled.

Order U/V
Raising Order widens how far each control point reaches along its
row/column. The surface comes out smoother, but it hugs
the shape of the control grid less tightly.
See NURBS Curves Order.

Surfaces with Order U set to 2 (top) and 4 (bottom).

With Bézier turned on, Order instead sets how many control points each spline gets.

Order in any one direction can't exceed the count of control
points running along that direction.

Resolution U/V
Sets the preview density of the generated surface mesh. Crank it up and you get
more vertices and a smoother-looking surface.

Only the active surface is affected by this. To set the resolution for every surface
in the object, turn to the Resolution Preview U/V setting in the
Shape panel instead.

Should the Render U/V values in the Shape panel be nonzero, they take precedence over these
Resolution U/V values when rendering.

Smooth
Whether smooth shading gets applied
to the generated surface mesh.
