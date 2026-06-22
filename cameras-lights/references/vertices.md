# Vertices, Line Art, Relations, Tool Settings ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Vertices; Line Art; Relations; Tool Settings; Falloff; Sculpt; Adaptive Resolution; Line Project; Trim Gesture Tools.

## Vertices

### Vertices

Reference

Mode :

Object Mode

Panel :

Properties ‣ Object Properties ‣ Instancing

Instance Vertices allows you to replicate child objects at the location of every vertex of the parent object.

Note

The relative Object Origin position of the parent and child objects determines offset instanced geometry from parent vertex.

Align to Vertex Normal
Rotates all instanced objects according to the corresponding vertex normals of the parent mesh.

To change the axis of direction of the instanced objects, select the child object and change the Tracking Axis.

There are actually two approaches to modeling using instanced vertices. They can be used as an arranging tool, allowing you to model geometrical arrangements of objects (e.g. the columns of a Greek temple, the trees in a garden, the desks in a classroom). The object can be of any object type which Blender supports. The second approach is to use them to model an object starting from a single part of it (e.g. the spikes in a club, the thorns of a sea-urchin, the tiles in a wall, the petals in a flower).

Note

Download Example Blend-File

You can download a file with the examples described on this page. In this blend, the first example, a monkey parented to a circle is on layer 1; while a tentacle parented to an icosphere is on layer 2.

### Usage

### Instanced Vertices as an Arranging Tool

All you need is a base object (e.g. the tree or the column ) and a pattern mesh with its vertices following the pattern you have in mind. In this section, we will use a simple scene for the following part. We will be using a monkey head located at the origin of the coordinate system as our base object and a circle at the same location as our parent mesh.

| A monkey head and a circle. | Instanced monkeys on Vertices. |

First, in Object Mode , select the base object and Shift - LMB to add the circle to the selection (order is very important here), and Ctrl - P or Object ‣ Parent ‣ Object to parent the base object to the circle. Now, the circle is the parent of the monkey; if you move the circle, the monkey will follow it.

With only the circle selected, enable Instancing Vertices ; a monkey head should be placed at every vertex of the circle.

The original monkey head at the center and the parent mesh are still shown in the 3D Viewport but neither will be rendered. If the placement and rotation of your monkey head are odd, you might need to clear its rotation Alt - R , scale Alt - S , location Alt - G , and origin Object ‣ Clear ‣ Origin .

#### Rearranging

If you now select the base object and modify it in either Object or Edit Mode, all changes will also affect the shape of all instanced objects. You can also select the parent mesh to modify the arrangement of the instances; adding vertices will also add more base objects.

Note that the base objects will inherit changes made to the parent mesh in Object Mode, but not in Edit Mode. So scaling the circle up in Object Mode will enlarge the monkey head, while scaling the circle up in Edit Mode will only increase the distance between the base objects.

#### Orientation

The orientation of the base objects can be controlled by enabling Align to Vertex Normal in the Instancing panel. This will rotate all base objects according to the vertex normals of the parent mesh.

To change the orientation of the instanced objects, select the base object and change the Tracking Axis.

| Orientation enabled, orientation +Y. | Negative Y. |
| Positive X. | Positive Z, up X. |

Note

The axes of an object can be made visible in the Properties ‣ Object Properties ‣ Viewport Display panel. To display the vertex normals of the parent mesh, enter Edit Mode and enable this visualization in the Display & Shading ‣ Viewport Overlays ‣ Normals where you can also resize the displayed normals as necessary.

### Instanced Vertices as a Modeling Tool

Very interesting models can be made using Instancing Vertices and a standard primitive. In this example, a simple tentacle was made by extruding a cube a couple of times. The tentacle object was then parented to an icosphere. With Align to Vertex Normal enabled for the parent mesh (the icosphere), the orientation of the base object (the tentacle) was adapted to the vertex normals of the parent mesh (in this case the tentacle was rotated -90° about the X axis in Edit Mode).

| A simple tentacle set to smooth. | Tentacles instanced onto the parent mesh. | Align to Vertex Normal enabled to align instanced geometry. |

As in the previous example, the shape and proportions of the arrangement can now be tweaked.

To turn all instanced geometry into real objects, select the icosphere and Make Instances Real. To make the icosphere and the tentacle a single object, make sure they are all selected and go to Object ‣ Join , Ctrl - J .

See also

Other duplication methods are listed here.

## Line Art

### Line Art

Reference

Mode :

Object Mode

Panel :

Properties ‣ Object Properties ‣ Line Art

The Line Art panel is used to enable extra display options for customizing Line Art rendering for a specific object.

Line Art panel.

Usage
How the object is loaded into Line Art. This property overrides the parent collection's Line Art usage.

Inherit :

No special loading strategy for Line Art. Loading of the object is controlled by parent collection's Line Art settings.

Include :

Force include the object into Line Art calculation even if its parent collection specifies otherwise.

Intersection Only :

The object will only produce intersection lines in the scene and its own geometry stays invisible.

Occlusion Only :

The object will only cause occlusion to existing feature lines and its geometry stays invisible.

Exclude :

The object will not be loaded into Line Art at all.

No Intersection :

The object will not generate intersection lines on itself or with other objects in scene.

Force Intersection :

Generate intersection lines even with objects that disabled intersection.

Override Crease
Allows the object to have a different crease value than the global one set in the Line Art modifier.

Crease
Override crease value for the object.

Intersection Priority
Assigns an intersection priority value for this object. The intersection line will be included into the object with the higher intersection priority value.

## Relations

### Relations

Reference

Mode :

Object Mode

Panel :

Properties ‣ Object Properties ‣ Relations

Parent
The object to which the selected object is parented to.

Parent Type
The type of parenting used. See parenting for information on the different types.

Use Final Indices Vertex 3 Vertices
Use the final evaluated indices rather than the original mesh indices.

Camera Parent Lock
When the camera is locked to the view, the root parent is transformed rather than the camera. This is useful for camera rigs where you don't want to animate the camera directly.

Parent Vertex/Vertices
Indices of vertices in case of a vertex parenting relation.

Tracking Axis
Axis that points in the "forward" direction. Applies to Instance Vertices when Align to Vertex Normal is enabled.

Up Axis
Axis that points in the "upward" direction. Applies to Instance Vertices when Align to Vertex Normal is enabled.

Pass Index
Defines the index the object will have in the Object Index render pass. See passes and ID mask for more information.

Note

Volume Objects are not supported.

## Tool Settings

### Tool Settings

### Options

Reference

Mode :

Object Mode and Pose Mode

Header :

Sidebar ‣ Tool ‣ Options

### Transform

Affect Only

Origins Ctrl - Period
Repositions the object's origin point directly.
This function operates solely on transformable object data types;
it is not functional for light sources.

When active, the object's coordinate system is rendered.

Use caution with this setting as it adjusts the object-data, potentially
causing linked copies to shift unexpectedly.

Hint

Adjusting origin location and object-data positioning may
alter modifiers, constraints, and animation keyframes.

To temporarily adjust the pivot point,
use the 3D cursor method instead.

Locations
Adjusts the object's origin position relative to another reference point during transformation.
The pivot point and origin cannot occupy the same position.
This action does not change the object's local coordinate values, only its placement in global space.

Examples below contrast scaling and rotating behavior when Location is engaged (center) versus disengaged (right).

Rotation example.

Scaling example.

Parents
Modifies Parent Objects
while keeping their children unmodified.

## Falloff

### Falloff

The Falloff establishes how brush potency reduces with growing range from the focal point. You can arrange a bespoke line or pick
a preset option.

Brush falloff sample.

Curve Preset

Custom
Shows a Curve Resource for establishing a bespoke reduction.
The left boundary of the graph displays the focal point while the proper boundary
shows the border.

Predefined
The preset reduction graphs appear as:

| Smooth | Smoother | Sphere |
| Root | Sharp | Linear |
| Sharper | Inverse Square | Constant |

Falloff Shape
Specifies how the reduction gap is assessed.

Sphere :

Measurement occurs via a 3D shape in 3D planetary area.
If dual spots on the form look near in the 3D space yet distant in the world, applying one won't change the alternate.

Projected :

Measurement happens via a band in 2D display area.
If dual spots on the form appear near in the 3D space, applying
one similarly impacts the alternate, despite far apart distances.

Texture Paint Mode does not present this choice – it constantly applies Projected .

Normal Falloff / Front-Face Falloff
Lowers the mark impact for areas whose direction angles toward the display perimeter
as opposed to the camera.

This characteristic is not accessible in Sculpt Mode.

Angle
The utmost gap among the plane normal and the monitoring bearing for the
decrease to initiate.

## Sculpt

### Sculpt

This documents common hotkey operations and interface-based options in sculpt mode.

### Transform

Move
Change object position.

Rotate
Change mesh orientation.

Scale
Alter mesh size.

Sphere
Shift the mesh to a round shape.

See also

Transform Tools.

### Show & Hide

Reference

Mode:
Sculpt Mode

Menu:
Sculpt

Quick hotkey options regulating visibility per Face Sets.
These lack a menu location and activate via shortcuts.
Extra visibility options are in the Face Sets Menu
and the Pie Menu shortcut Alt - W. (Visibility typically toggles through Face Sets.)

Box Hide
Draw a rectangular region to conceal polygons.

Box Show
Draw a rectangular region to reveal polygons.
Matches the Box Select technique.

Toggle Visibility Shift - H
Conceal all Face Sets except the current one (beneath the cursor).
If Face Sets are already hidden, execute to show all.

Hide Active Face Set H
Conceal the Face Set beneath the cursor. Afterward use Shift - H to show all.

Show All W , Alt - H
Reveal all concealed areas.

Invert Visible
Conceal all shown regions and reveal all concealed areas.

Hide Masked
Conceal all protected points.

Grow/Shrink Visibility PageUp , PageDown
Enlarge or contract the shown zone along the surface.

See also

For broader context see
Visibility, Masking & Face Sets.

### Fairing

These modify surface patches derived from a Face set.

See also

Edit Face Set Tool

Fair Positions
Produces a flat and refined surface patch from the Face set.
Ideal for editing parts when vertex density is too high for alternatives,
or vertex marking must stay unchanged
(As with Multires modification).

Fair Tangency
Produces the most refined surface patch from the Face set
through minimal edge-curve modification.
Perfect for smooth curved layers on intricate topology,
where standard brushing won't give wanted results.

### Trimming

The trimming options add or eliminate surfaces per gesture drawing.
Great for early mesh drafting before advanced
modification with the voxel system.

Line Project
Evens the surfaces along a viewport plane and drawn line.
The affected zone brightens to indicate the region.

Box Trim
Eliminates geometry per rectangular picking.

Lasso Trim
Eliminates geometry per freeform picking.

Box Add
Incorporates geometry per rectangular picking.

Lasso Add
Incorporates geometry per freeform picking.

### Mesh Filters

Alters all visible points at the same time.
Masking, auto-masking and presence will be considered.

To use, drag from left to right
or from right to left for reverse action.

See also

Mesh Filter Tool

Smooth
Refines point spots to either perfect surfaces or eliminate bulk from substantial forms.
Great for voxel system fixes.
Performs like the Smooth brush.

Surface Smooth
Rectifies mesh unevenness by leveling
point spots while keeping object thickness.
Performs like the Surface variety of the
Smooth brush.

Inflate
Moves points uniformly perpendicular to their normals.
Performs like the Inflate brush.

Relax Topology
Tries to build uniform squares without distorting object thickness.
Performs like holding Shift with the
Slide Relax brush.

Relax Face Sets
This erases the stepped look from Face Set creation.
Performs like holding Shift with the
Draw Face Set brush.

Sharpen
Refines and smooths per form angle,
sharpening edges and perfecting flat zones.
Handy for stiff structures and expressive bodies
with creasing and flattening techniques.

Enhance Details
Increases high-range surface characteristics
by maximizing the variance among creases and depressions.
Performs like the inverted choice of the
Smooth brush.

Erase Multires Displacement
Eliminates displacement from
the Multires Modifier,
reversing to standard subdivision outcome.
Good for resetting zones or addressing artifacts
via Shrinkwrap Modifier use.

Reverse strokes will boost displacement specifics,
matching Enhance Details behavior and potentially superior in some scenarios.

Randomize
Arbitrarily moves points following the vertex angle.
Performs like the Randomize Transform.

### Sample Color

Reference

Mode:
Sculpt Mode

Menu:
Sculpt ‣ Sample Color

Shortcut:
Shift - X , Shift - Ctrl - X

Pulls a hue from the display and implements it on the live
Paint brush.

When launched via menu (avoiding shortcut),
you can position and pull across multiple hues for their blended average.

This facilitates fast hue matching to current paint detail
right on the component.

- Hit Shift - X to pull a hue at the cursor location.

- Hit Shift - Ctrl - X to pull the full viewport hue,
containing illumination, texture effects, and all rendered details.

The acquired hue becomes the main tone of the live Paint brush.

### Set Pivot

Reference

Mode:
Sculpt Mode

Menu:
Sculpt ‣ Set Pivot

Paralleling Object and Edit variations, Sculpt Mode provides a Pivot Point.
This is because standard shift, roll and scale
transforms are allowed in Sculpt Mode too.
The Sculpt Mode pivot differs. It follows the updated component
and can be both hand-set & machine-set.

Origin
Positions the turning point at the base coordinate.

Unmasked
Positions the turning point at the midpoint of unprotected points.

Mask Border
Positions the turning point at the mask perimeter center.
This occurs mechanically during Expand.

Active Vertex
Positions the turning point at the present vertex spot.

Surface Shift - RMB
Positions the turning point at the shown surface beneath the cursor.

Tip

For simple pivot positioning use the Surface assigned hotkey.

See also

For fuller context see Transforming.

### Rebuild BVH

Reference

Mode:
Sculpt Mode

Menu:
Sculpt ‣ Rebuild BVH

Recalculates the BVH leveraged by Dyntopo
to increase performance, which may decline during Dyntopo use.

See also

For fuller context see Adaptive Resolution.

### Dynamic Topology Toggle

Switches Dyntopo.

### Transfer Sculpt Mode

Reference

Mode:
Sculpt Mode

Menu:
Sculpt ‣ Transfer Sculpt Mode

Shortcut:
Alt - Q

Transitions Sculpt Mode from the chosen component to the component beneath the mouse.
See Switching Objects for additional data.

See also

For fuller context see
Working with Multiple Objects.

## Adaptive Resolution

### Adaptive Resolution

For sculpting to yield consistent and repeatable geometry, ample surfaces are necessary.
Rather than beginning with a densely divided mesh, increase geometry in real-time
using either of these adaptive sculpting approaches.

### Voxel Remesher

Voxel-based rebuilding constructs geometry with uniform topology distribution.
Voxel dimensions control resulting resolution.

Ideal for establishing foundational shapes.
Removes overlaps and guarantees watertight models.

Masks, Face Sets, and attribute colors reproject onto remeshed output.
High vertex counts stay feasible based on hardware.

Note

This method needs sealed forms.
Empty all gaps prior to remeshing.
Or avoid holes bigger than the chosen voxel proportion.

Tip

When unclear, use the Alt
to fill all gaps or by using the
Mask Slice and Fill Holes
choice to complete all gaps. If unprotected, only fills all gaps.

Use R to configure the size,
and Ctrl - R to do the remeshing.

See also

Further info at Remesh.

### Dyntopo

Dyntopo (Dynamic topology) mechanically inserts and removes faces under the brush during sculpting.

Unlike Voxel Remesher, this permits elaborate shape work
without density awareness.
Resolution varies per area as needed.
Advanced base topology sculpting shines with this.

Speed and feature availability suffer; performance lags.
Custom characteristics including Color data, UV assignments and Face Sets degrade or vanish.

This capability uses matching shortcuts with voxel method when on.
Use R to configure the density and Ctrl - R to distribute the density (if Constant Detail applies).

Note

Because Dyntopo and the Voxel Remesher exclude and prevent combined use,
both employ the same option for remesh settings.

Approaches like Density,
Snake Hook
and Clay Strips show best with this capability.

See also

Further info at Dyntopo.

### Multiresolution

Multiresolution Modifier enables subdivision-level sculpting.
Operates like
Subdivision Surface Modifier,
allowing sculpting at each subdivision depth.

Note

Clean base geometry is essential.
Rely on quad-only topology
and avoid non-manifold situations, plus vertices with just two connections.
See Quad Remeshing for automated conversion.

Sculpting at multiple subdivision tiers permits fine control.
Work at any depth: general shapes on early subdivisions,
fine detail at later ones.
Viewport performance stays high while retaining maximum detail.
Return to lower subdivisions anytime for major restructuring.

Example: shape at level 1,
detail at level 4, revert to level 1 to adjust forms further.

Pitfalls include topology distortion
since geometry remains fixed unlike voxel and dyntopo modes.
Base connectivity can't change post-subdivision,
as modifications break subdivision details.

Tip

Consider the topology that you customize and how much it stretches.
If extra density proves necessary you can subdivide again,
yet efficiency and switching pace diminish beyond 5 times.
Additionally try the Slide Relax
brush to move topology to places needing it.

Extra approaches like the Multires Eraser and
Multires Smear aid in rework.

These standard shortcuts cover the capability.

- Step up one multires density Alt - 2

- Step down one multires density Alt - 1

- Set multires density / Build multires option Ctrl - 0 to Ctrl - 5

See also

Further info at Multiresolution Modifier.

## Line Project

### Line Project

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Line Project

This flattens mesh surfaces along a plane formed by the viewport perspective and a user-drawn line. A shaded region shows which mesh portions will be affected.

| Before Line Project. | After Line Project. |

### Usage

Operate using these steps:

- Establish viewport orientation to set depth direction.

- Press LMB and drag the cursor to establish the projection direction.

- Fine-tune the operation via supplementary Control shortcuts.

- Release LMB to finalize.

### Controls

Flip F
Switches which line side the tool projects toward.

Snap Ctrl
Restricts line rotation to 15-degree increments.

Move Ctrl - Spacebar
Repositions the projection line.

### Tool Settings

Limit to Segment
Restricts the affected region to the length of the drawn line. This provides a way to target smaller areas instead of projecting infinitely.

## Trim Gesture Tools

### Trim Gesture Tools

Reference

Mode :

Sculpt Mode

These tools introduce or subtract geometry based on a defined selection region. This approach excels when establishing a preliminary mesh foundation for subsequent voxel remesher sculpting.

| Using Lasso Trim set to Join | The symmetrized mesh. | Sculpting with voxel remeshing. |

Newly added geometry receives a fresh Face Set grouping. When subtracting geometry, the interior surfaces generated along the boundary are assigned a new Face Set instead.

Note

For meshes above 100k vertices, Difference and Union operations using the Exact Solver are not recommended. Since Boolean operations power this tool, processing can require significant time. For higher-resolution geometries, the Line Project tool or Fair Positions mode from Edit Face Set are preferable alternatives.

### Box Trim

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Box Trim

Executes a Boolean operation within a box-defined region.

### Lasso Trim

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Lasso Trim

Executes a Boolean operation within a lasso-defined region.

### Line Trim

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Line Trim

Executes a Boolean operation within a line-defined region.

Note

This tool exclusively supports geometry removal. Only Difference is available.

### Polyline Trim

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Polyline Trim

Executes a Boolean operation within a polyline-defined region.

### Tool Settings

Solver
The computational approach for calculating Boolean intersections.

Exact :

Uses an intricate algorithm providing superior outcomes and complete handling of overlapping topology; however, computation is substantially slower.

Float :

Employs a streamlined algorithm with strong speed characteristics; however, it does not fully support overlapping topology.

Manifold :

Typically the quickest option but restricted to Manifold geometries (with the exception of Difference using planes).

Trim Mode
Determines whether geometry is introduced or subtracted.

Difference :

Subtracts geometry and fills any resulting gaps.

Union :

Introduces geometry and connects intersections with pre-existing geometry.

Join :

Comparable to Union but merges the mesh without Boolean interactions.

Shape Orientation
Determines how the trimming shape gets aligned.

View :

Align the trimming shape toward the viewport.

Surface :

Align the trimming shape along surface normals.

Extrude Mode

Fixed :

Generates new geometry with 90-degree angles perpendicular to depth.

Project :

Generates new geometry following viewport perspective for a tapered appearance.

Use Cursor for Depth
Employs cursor placement and scale for trimming dimensions and positioning. If disabled, the operation spans the object's complete depth from the camera view.
