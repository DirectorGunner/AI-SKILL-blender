# Numeric Input, Rotate, Scale, Scale Cage ...

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Numeric Input; Rotate; Scale; Scale Cage; Add Curves; Comb Curves; Delete Curves; Grow / Shrink Curves; Pinch Curves; Puff Curves; Selection Paint; Slide Curves; Snake Hook Curves; Common Settings; Blob; Blur; Boundary; Clay.

## Numeric Input

### Numeric Input 

Mouse control is convenient for transforms, but precise adjustments need exact values. After triggering a command, enter a number
to set the transformation strength. Then finalize or undo.
E.g. pressing S 2, Return will multiply the scale by two.

Move G
By default with no additions, movement occurs along the X axis.

Rotation R
Positive angles rotate counterclockwise.

Scale S
Sizing behaves much like moving.
The main difference is that by default, scaling applies to all three dimensions evenly.

You can monitor the numbers in the viewport footer.

Numeric input shown in the footer. 

Tip

Numerical values can also be set in
the sidebar.

### Simple Mode 

Blender supports two "input styles": basic and complex. Basic mode takes whole and decimal numbers.

Decimals Period
Type decimals by pressing Period.

Negate Minus
Reverse the value with Minus.

Reciprocal Slash
Pressing Slash during input flips the number to its opposite,
e.g. 2 / becomes 0.5 (half of 2); 20 / becomes 0.05 (one-twentieth).

Reset Backspace
Hitting Backspace after removing all preceding digits
will first revert the edited value to its starting point, and on a second press,
input ceases and reverts to standard transform with the mouse.

Cycle Components Tab, Ctrl - Tab
For multi-axis values, engage Tab or Ctrl - Tab.
E.g. To move an object a unit along all three directions, type: G 1
and Tab 1 and Tab 1.

Non-number Inputs
Numerical entry combines with
Axis Locking
to restrict movement to one axis or command-specific shortcuts.

### Advanced Mode 

Advanced mode allows you to type formulas and unit notations.

Press = or NumpadAsterisk to start advanced mode,
and Ctrl - = or Ctrl - NumpadAsterisk to switch back to simple mode.

Capabilities include:

- Notation ( cm, ", deg, etc.)
.
Reference unit system.

- Fundamental Python operations ( +, *, /, **, etc.)

- Math keywords and routines ( pi, sin, sqrt, etc.)
.
Reference Python's math package.

You can employ the negate and reciprocal shortcuts ( Minus, Slash),
as well as non-number inputs, but you must press Ctrl.

## Rotate

### Rotate 

Reference

Mode:
Object and Edit Modes

Menu:
Object/Mesh/Curve/Surface ‣ Transform ‣ Rotate

Shortcut:
R

Rotation is also called a spin, twist, orbit, pivot, turning, or roll and
entails shifting the orientation of components (corners, edges, surfaces, objects, etc.)
around one or multiple axes or
the Pivot Point.

The turn amount shows in the viewport header.

Rotation display. 

Reference

Blending shortcuts grants better control.
See Transform Control.

### Options 

Angle
The turn amount.

Axis
Used to limit the transformation to one or multiple axes.

Orientation
Realigns the transformation directions to a specified orientation.
Reference Transform Orientations for details.

Proportional Editing
The extruded side will impact nearby components.
See Proportional Editing for complete information.

### Trackball Rotation 

Reference

Mode:
Object and Edit Modes

Shortcut:
R R

An unrestricted turning mode. Hit R R to enable Trackball rotation.

### Rotate

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Rotate geometry following stroke direction.

### Brush Settings

### General

Note

More info at General brush settings
and on Advanced brush settings.

## Scale

### Scale 

Reference

Mode:
Object and Edit Modes

Menu:
Object/Mesh/Curve/Surface ‣ Transform ‣ Scale

Shortcut:
S

Resizing modifies the dimensions of objects. Typing S switches to
Scale mode where the chosen element grows or shrinks based on the mouse placement. The element gets bigger as the mouse shifts away from the Pivot Point and shrinks as
the pointer approaches it. If the mouse swaps from the starting side of
the Pivot Point
to the opposite side, the scale becomes negative and flips the element.

Standard scaling. Left to right: the starting state,
a downsized, an upsized, and a flipped state. 

The scaling amount appears in the viewport header.

Scale display. 

Reference

Mixing shortcuts offers better control.
Reference Transform Control.

### Options 

Scale X, Y, Z
The resize amount on each axis.

Orientation
Realigns the transformation directions to a specified orientation.
Reference Transform Orientations for details.

Proportional Editing
The extruded side will impact nearby components.
See Proportional Editing for complete information.

## Scale Cage

### Scale Cage

Reference

Mode :

Object and Edit Modes

Tool :

Toolbar ‣ Scale ‣ Scale Cage

This tool provides a bounding box interface for scaling objects from a chosen point or axis orientation. Operation involves selecting a scale point and moving it inward or outward to modify the object's overall scale. The scaling center originates at the opposing corner of the selected point on the bounding box. Selection of face corners modifies a single axis; edge selection adjusts two axes; vertex selection affects all three axes.

Scale Cage tool.

### Tool Settings

Orientation
Defines the direction constraint for transformation operations.
See Transform Orientations for further details.

### Options

Scale X, Y, Z
Magnitude of size adjustment along each axis.

Orientation
Defines the direction constraint for transformation operations.
See Transform Orientations for further details.

Proportional Editing
Nearby geometry is influenced by the extruded surface.
See Proportional Editing for full documentation.

## Add Curves

### Add Curves

Used to distribute new curves on the surface mesh. This tool requires the curve to have a surface object set.

The curves follow the surface normals. Using the interpolation options allows the brush to take the characteristics of existing curves.

### Brush Settings

Count
Number of curves added.

Note

Interpolation allows to add hair which are already combed. The new curves are created following the previously created curves which are in the vicinity.

Interpolate – Length
Use the average length of the curves in close proximity.

Interpolate – Radius
Use the average radius of the curves in close proximity. If there is no radius attribute, then the interpolation will skip.

Interpolate – Shape
Use the average shape of the curves in close proximity.

Interpolate – Point Count
Use the average amount of control points of the curves in close proximity.

Curve Length
Length of newly added curves when not interpolated.

Curve Radius
Radius of newly added curves when not interpolated.

Points per Curve
Number of Control Points for the new created curves when the point count is not interpolated.

## Comb Curves

### Comb Curves

Shape the curves by moving their control points while preserving the initial length of every curve segment.

### Brush Settings

Curve Falloff
Falloff that is applied from the tip to the root of each curve.

## Delete Curves

### Delete Curves

Erase current furs. The equipment eliminates the total furs,
when any of their sections fall underneath the implement reduction zone.

## Grow / Shrink Curves

### Grow / Shrink Curves

Change the length of existing curves preserving the amount of control points and resampling the curve to preserve the original shape.

### Brush Settings

Direction
Determines whether to grow or shrink the curves. It can be toggled holding Ctrl while sculpting.

Scale Uniform
Grow or shrink curves by changing their size uniformly instead of using trimming or extrapolation.

Minimum Length
Avoid shrinking curves shorter than this length.

## Pinch Curves

### Pinch Curves

Merges neighboring furs toward the spot at the outline focal point.

The pinch implement can be flipped through pressing Ctrl .

## Puff Curves

### Puff Curves

Makes the furs stand upright. The implement adjusts the fur with the ground outward direction
and guarantees that spots do not approach the base spot.

## Selection Paint

### Selection Paint

Paint curves or control points to use as masks for the other tools. The selection visibility can be controlled by the Selection Opacity option in the Viewport Overlays.

By default the selection sets a new selection. The selection paint can be extended by holding Shift and it can be subtracted by holding Ctrl while painting.

### Brush Settings

Direction
Determines whether to set a new selection or remove from it. It can be toggled holding Ctrl while painting.

## Slide Curves

### Slide Curves

Slides the curves along the surface mesh. This tool requires the curve to have a Surface. Each curve is also rotated by the change in the surface normal.

## Snake Hook Curves

### Snake Hook Curves

Extend existing curves in a specific direction of the brush strokes. A curve can only be extended by its tips (the control point opposite to the root).

Note

No new control points are created for the curves. Instead, existing points are sampled along the new curve shape.

## Common Settings

### Common Settings

Resources on implement parameters for any technique are in these sections:

### Brush

See overall and sophisticated Implement material here.

### Stroke

See the worldwide implement environment for Stroke guidelines.

### Falloff

See the worldwide implement environment for Falloff guidelines.

### Cursor

See the worldwide implement environment for Cursor guidelines.

## Blob

### Blob

Reference

Mode :

Sculpt Mode

Brush :

Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Similar to Draw, but vertices are pushed outwards like an inverted pinching effect. This will lead to a more consistent spherical curvature and thickening of strokes.

### Brush Settings

### General

Magnify
By default at 0.5 to push out the mesh during the stoke. More info at Pinch/Magnify

Note

More info at General brush settings and on Advanced brush settings.

## Blur

### Blur

Reference

Mode :

Sculpt Mode

Brush :

Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

The Blur brush smooths painted colors on the active Color Attribute. It samples the colors under the cursor and blends them together, softening transitions and reducing sharp color differences.

This brush is commonly used to refine painted details, smooth gradients, and remove harsh edges in vertex color painting workflows.

### Brush Settings

### General

Note

More info at General brush settings and on Advanced brush settings.

## Boundary

### Boundary

Reference

Mode :

Sculpt Mode

Brush :

Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Similar to the Pose brush but deforms the open boundaries of a mesh. The tool detects the mesh boundary closest to the active vertex and propagates the deformation using the brush Falloff into the mesh.

The main use cases of this brush are the Bend and Expand geometry, which leads to the best results on evenly distributed quad based topology. Use the Inflate , Grab , Twist , and Smooth deformation modes, to further adjustments and tweaks to the result (which do not depend that much on a clean topology).

Tip

Boundaries to hidden geometry will also be counted as an open boundary.

The boundary origin is displayed via a white line, which indicates the reach of the deformation. The targeted boundary that will be deformed is highlighted in the brush cursor color.

If the Deformation Target is changed, the brush can also be used for cloth sculpting.

Note

Evenly distributed and quad based topology will lead to much better results. Triangles and N-gons are also supported but may lead to unpredictable outcomes.

### Brush Settings

### General

Note

More info at General brush settings and on Advanced brush settings.

### Unique

Deformation
Deformation type that is used by the brush.

Bend :

Rotates the boundary around the local Y axis. Useful for creating folding shapes, like sleeves.

Expand :

Moves/extends the mesh boundary in the local X direction. Useful for extending the boundaries along the surface.

Inflate :

Works similar to the Inflate tool but, the vertices that are inflated are constrained to the mesh boundary.

Grab :

Works similar to the Grab tool but, the vertices that are grabbed are constrained to the mesh boundary.

Twist :

Rotates the active boundary around the local Z axis. Useful for creating folds like on a skirt.

Smooth :

Works similar to the Grab tool but, the vertices that are smoothed are constrained to the mesh boundary.

Boundary Falloff
How the brush Falloff is applied across the boundary.

Constant :

Applies the same deformation in the entire boundary.

Brush Radius :

Applies the deformation only within the brush radius.

Loop :

Applies the brush falloff in a loop pattern along the boundary.

Loop and Invert :

Applies the falloff radius in a loop pattern, inverting the direction back & forth.

Boundary Origin Offset
Offset of the boundary origin in relation to the brush radius.

## Clay

### Clay

Reference

Mode :

Sculpt Mode

Brush :

Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Similar to the Draw brush, but includes settings to adjust the sculpt plane on which the brush acts. That's because it behaves like a combination of the Plane and Draw brushes.

This brush is useful for building and removing volumes and shapes like real clay, because it flattens details as you add/subtract from the surfaces.

If used together with Dyntopo it's easy to continuously build shapes, even in a single stroke.

### Brush Settings

### General

Hardness
Slightly higher by default. This makes the profile of the brush more noticeable. More info at Hardness

Auto-Smooth
Enabled by default for a consistent smoothing effect. With lower brush strength (for example with lower pen pressure) the smoothing effect will be more noticeable and can be used to create and then blend/polish shapes in a single stroke. Enable Pressure to modulate the use of auto-smooth even more with pen inputs. More info at Auto-Smooth

Note

More info at General brush settings and on Advanced brush settings.

## Clay Strips

### Clay Strips

Reference

Mode :

Sculpt Mode

Brush :

Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Similar to the Clay brush, but it uses a square tip shape instead of a round one.

Just like the Clay brush, it's useful for building and removing volumes and shapes like real clay, because it flattens details as you add/subtract from the surfaces.

Clay Strips is very commonly used for aggressive building of volumes and deliberate control over shapes on the surface. This brush alone can be used for a fast rough pass over the entire sculpt, with additional smoothing or polishing often required afterwards. This brush can be very versatile with varying stroke directions, repeated strokes and pen pressure to achieve various results.

If used together with Dyntopo it's easy to continuously build shapes, even in a single stroke.

### Brush Settings

### General

Normal Radius
Higher by default. This ensures that the brush does not change directions to sporadically during a stroke. More info at Normal Radius

Tip Roundness
Very low by default for a square shape for more deliberate shaping. More info at Tip Roundness

Note

More info at General brush settings and on Advanced brush settings.

## Cloth

### Cloth

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Physics-based cloth deformation for geometry under the brush.
Numerous settings control behavior and intensity.

Sculpting with other brushes and tools between cloth operations remains straightforward.

Note

Using smaller brush sizes accelerates computation significantly;
larger sizes can render the interface sluggish.

### Brush Settings

### General

Note

More info at General brush settings
and on Advanced brush settings.

### Unique

Persistent
Prevents accumulation of deformation across successive strokes.
Useful for repeatedly applying distinct forces to a starting shape.

When off, each stroke compounds on previous results.

Set Persistent Base
Resets the reference geometry, allowing additional layered deformations.

Simulation Area
Defines which mesh portion activates during the stroke.
Selection directly impacts performance based on mesh density.

Local
Updates only a fixed-radius region centered on the brush.

Global
Updates all visible mesh geometry.

Dynamic
The active region follows the brush while remaining bounded by a fixed radius.

Simulation Limit
Distance factor relative to brush radius controlling effect extent.

Simulation Falloff
Region receiving deformation falloff application.
Scales as a multiplier of Simulation Limit; shown as a dashed outline.

Pin Simulation Boundary
Locks vertices in the falloff zone, preventing discontinuities
and transitioning smoothly to unaffected areas.

Deformation
The operation type applied to cloth.

Drag:
Pulls cloth toward the cursor,
matching a finger sliding across fabric.

Push:
Drives cloth away from the cursor,
like pressing on cloth with a fingertip.

Pinch Point:
Concentrates cloth into a pointed tip.

Pinch Perpendicular:
Concentrates cloth into a linear edge.

Inflate:
Raises cloth by introducing compressed air underneath.

Grab:
Lifts and repositions cloth as a unit.

Expand:
Stretches the fabric outward.

Snake Hook:
Moves cloth while maintaining surface integrity,
producing natural-looking pleats and folds.
This is achieved by modulating deformation stiffness per step
to reduce simulation influence.

Force Falloff
Brush impact profile.

Radial:
Distributes force as a sphere.

Plane:
Distributes force as a flat plane.

Cloth Mass
Weight of each simulated particle.

Cloth Damping
Propagation rate of forces through cloth.

Soft Body Plasticity
Retention of original configuration,
providing Soft Body characteristics.

Use Collisions
Activates contact with external objects during simulation.
Objects must have Collision Physics enabled to participate.

## Crease

### Crease

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Generates sharp dents via mesh deformation with inward vertex convergence.

Crease also refines and emphasizes existing sharp lines.
Activate pressure responsiveness for Strength to regulate pinching action.

### Brush Settings

### General

Pinch
Applies consistent vertex convergence during strokes.
At 0, acts like the Draw brush.
At 1 combined with zero strength, matches a Pinch brush.

Note

More info at General brush settings
and on Advanced brush settings.

## Draw Face Sets

### Draw Face Sets

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Establish or grow Face Sets via strokes.

Holding Ctrl preserves the Face Set beneath the cursor.
Holding Shift smooths Face Set borders
by adjusting topology so edges follow Face Set outlines.
This eliminates the appearance of irregular transitions.

Note

More information in the
Face Set Introduction.

### Brush Settings

### General

Most general brush options are available,
though defaults require no adjustment—this brush serves a simple purpose.

Note

More info at General brush settings
and on Advanced brush settings.

## Draw Sharp

### Draw Sharp

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Draw variant working from original geometry with sharper falloff.

Suited for high-resolution meshes to produce wrinkled fabric, expressive hair, or angular silhouettes.
For sharper geometry on insufficient density,
consider the Pinch,
Crease or
Multiplane Scrape brushes.

A constraint: this brush doesn't remesh with Dyntopo.
Crease serves as a better alternative in that scenario.

### Brush Settings

### General

Direction
Subtract mode by default for incised grooves. More info at Direction

Note

More info at General brush settings
and on Advanced brush settings.

## Sculpt Brushes

### Sculpt Brushes

Sculpt Mode provides many brush varieties for reshaping, refining,
and enriching mesh surfaces.
Each targets specific operations—volume addition,
surface refinement, edge sharpening, or pattern application.

Every brush type ships with a default configuration,
plus numerous pre-tuned variants for common techniques.
These provide ready-made baselines and illustrate conventional workflows.

Brushes accept extensive customization covering power, shape, pattern use, and stroke mechanics.
Saved brushes can be reused across projects.

## Inflate

### Inflate

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Expand vertices along individual normals. Ideal for curved topology.

Also offered as a Mesh Filter
for concurrent enlargement of unmasked zones.

### Brush Settings

### General

Direction
Selects enlargement or contraction.
Differs from standard Add/Subtract modes.

Note

More info at General brush settings
and on Advanced brush settings.

## Layer

### Layer

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Draw-like behavior with fixed height ceiling; creates flat layers.

Enable the Persistent mode
and use Set Persistent Base regularly,
preventing successive strokes from stacking.

### Brush Settings

### General

Hardness
Set higher by default to make layer profiles more apparent.
More info at Hardness

Note

More info at General brush settings
and on Advanced brush settings.

### Unique

Height
Fixed elevation per stroke. Uses scene units,
so behavior remains independent of zoom or object size.

Persistent
Ensures repeated strokes share the same height, treating sculpting as continuous layering.

Set Persistent Base
Initializes a new reference, enabling subsequent layer creation.

## Mask

### Mask

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Protect areas via grayscale mask overlay.

Note

More information in the
Masking Introduction.

### Brush Settings

### General

Note

More info at General brush settings
and on Advanced brush settings.

### Unique

Mask Tool
Two operation modes:

Draw:
Applies mask.

Smooth:
Holding Shift refines mask edges.

## Scrape Multiplane

### Scrape Multiplane

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Dual-plane scraping for hard surface edges.

### Brush Settings

### General

Note

More info at General brush settings
and on Advanced brush settings.

### Unique

Plane Angle
Angular separation between the two cutting planes. Holding Ctrl reverses direction.

Dynamic Mode
When on, angle adjusts based on underlying surface.
Plane Angle then governs pressure-based change magnitude.
Holding Ctrl fixes angle at zero.

Show Cursor Preview
Renders the cutting geometry and angular relationship during application.

## Erase Multires Displacement

### Erase Multires Displacement

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Clear Multires displacement back to base subdivision.

Helpful for resetting regions or correcting artifacts
from Shrinkwrap Modifier use.

Tip

Most effective after using Apply Base.

### Brush Settings

### General

Note

More info at General brush settings
and on Advanced brush settings.

## Smear Multires Displacement

### Smear Multires Displacement

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Move Multires displacement without modifying base mesh.

Repeated smearing over the same region produces no topology corruption.

Tip

Most effective after using Apply Base.

### Brush Settings

### General

Note

More info at General brush settings
and on Advanced brush settings.

### Unique

Deformation
The kind of offset modification.

Drag:
Draws offset values in stroke direction.

Pinch:
Concentrates offset values toward the center,
producing hard-surface results without topology pinching.

Expand:
Distributes offset values outward, smoothing displacement.

## Nudge

### Nudge

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Move vertices following stroke direction along surface.

### Brush Settings

### General

Note

More info at General brush settings
and on Advanced brush settings.
