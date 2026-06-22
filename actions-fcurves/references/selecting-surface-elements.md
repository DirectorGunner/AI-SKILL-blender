# Selecting Surface Elements, Transform Modal Map, S Curves, Selecting Tracks ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Selecting Surface Elements; Transform Modal Map; S-Curves; Selecting Tracks; Shape; Effector; Flow; Curve Guide.

## Selecting Surface Elements

### Selecting Surface Elements

On a Surface object, control points are the only thing you can select — there are no edges, faces, or Bézier handles to grab.

See also

Selecting for general information about selecting items in Blender.

### Select All

Reference

Mode :

Edit Mode

Menu :

Select ‣ All

Shortcut :

A

Marks every control point as selected.

### Select None

Reference

Mode :

Edit Mode

Menu :

Select ‣ None

Shortcut :

Alt - A

Clears the selection from all control points.

### Select Invert

Reference

Mode :

Edit Mode

Menu :

Select ‣ Invert

Shortcut :

Ctrl - I

Flips the selection: what was unselected becomes selected and vice versa.

### Box Select

Reference

Mode :

Edit Mode

Menu :

Select ‣ Box Select

Shortcut :

B

See Box Select.

### Circle Select

Reference

Mode :

Edit Mode

Menu :

Select ‣ Circle Select

Shortcut :

C

See Circle Select.

### Lasso Select

Reference

Mode :

Edit Mode

Menu :

Select ‣ Lasso Select

Shortcut :

Ctrl - RMB

See Lasso Select.

### Select Random

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select Random

Throws random control points into the selection. The Adjust Last Operation
panel offers the following options:

Ratio
What fraction of control points should end up selected — 0.5, say, to grab half of all the points
that aren't hidden.

Be aware that whatever is already selected gets ignored: with half the control points already selected,
dropping Ratio to 0.1 neither deselects anything nor selects 10% of what's still unselected.
Instead it always grabs 10% of every visible point and adds those to the selection.

Random Seed
A value that steers exactly which control points end up chosen.

Action

Select :

Throws a random batch of control points into the selection.

Deselect :

Pulls a random batch of control points back out of the selection.

### Checker Deselect

Reference

Mode :

Edit Mode

Menu :

Select ‣ Checker Deselect

Working outward from the active point, this operator removes control points from the selection following a repeating pattern.
Say Deselected is 2 and Selected is 3: the operator
clears the first two points in a row, leaves the next three alone, clears
the following two, and keeps going. It runs this in both the "horizontal" and
"vertical" direction of the grid.

Deselected
How many control points each repetition of the pattern drops from the selection.

Selected
How many control points each repetition of the pattern leaves alone.

Offset
How far to shift away from the starting point.

### Select More/Less

Reference

Mode :

Edit Mode

Menu :

Select ‣ More/Less

Shortcut :

Ctrl - NumpadPlus / Ctrl - NumpadMinus

Grows or shrinks the selection starting from the control points already selected.

More
Pulls the neighbors of the selected control points into the selection.

Less
Drops any control point that has at least one neighbor left unselected.

### Select Linked

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select Linked

Shortcut :

Ctrl - L , L

Hit Ctrl - L to grab every control point "linked to" (sharing the same
surface as) one that's already selected.

Or press L to select the control point beneath the mouse cursor plus every
control point linked to it.

### Select Similar

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select Similar

Shortcut :

Shift - G

Starting from a selected control point, this operator picks up other control points that resemble it in some way.
The Adjust Last Operation panel provides options for this:

Type
Which property gets compared when deciding what counts as similar.

Type :

Has no bearing on Surfaces, since — Curves aside — they offer only a single handle type.

Radius :

Grabs control points whose Radius value comes out similar.
See Transform Panel.

Weight :

Grabs control points whose Weight value comes out similar.
See Transform Panel.

Direction :

Grabs control points whose normal vector points a similar way.

Compare
Which test decides whether an unselected control point counts against the selected ones.

Equal :

Picks control points whose property matches that of a selected point.

Greater :

Picks control points whose property is at least as large as the smallest property
found among the selected points.

Less :

Picks control points whose property is no larger than the greatest property
found among the selected points.

Threshold
A leeway that widens the net to control points whose property merely lands near
that of a selected one. Suppose a Weight of 0.6 on the selected control point with
Threshold at 0.1: every control point whose Weight falls anywhere from 0.5 to 0.7
then gets caught by Select Similar.

### Select Control Point Row

Reference

Mode :

Edit Mode

Menu :

Select ‣ Control Point Row

Shortcut :

Shift - Ctrl - R

Grabs the control points sharing the active one's grid line (much like
edge loop selection on meshes).
Run the operator a second time to switch to the grid line going the other way.

## Transform Modal Map

### Transform Modal Map

While a transformation is underway, certain hotkeys let you alter how the operation behaves.

You can check editing the keys of these modal modifiers in
Blender Preferences ‣ Keymap ‣ Transform Modal Map
(at the bottom of the keymap).

### Constraints

If you want a move, rotation, or scale to touch only some axes, you can lock the transformation down to those.

Out of the box those constraint keys are X , Y and Z .
Hold Shift while pressing one to limit the constraint to a plane, or
press MMB to have it picked out automatically.

It's worth noting that pressing the same constraint hotkey again
flips the orientation between Local and Global; a third press turns the constraint off.

### Snapping

Transform operations use the snapping settings set in the scene.
That said, some options can be tweaked mid-transformation.

### Snap Invert

Even with the magnetic icon switched off, snapping can be kicked in partway through a transformation.
By default Ctrl is the hotkey for that.

### Set Snap Base

Blender works out the Snap Base automatically from the Snap Base options.
But that auto-detected point of origin won't always be where the user actually wants it.
So transform operations include a tool for setting a fresh snap origin mid-transformation.
The new Snap Base lines up with the snap point whose target the
Snap Target defines.

By default the hotkey is B .

Note

When Snap to Increment is the only Snap Target enabled,
the targets Vertex , Edge , Face and Edge Center step in instead.

### Add Snap Point

With snapping on as you transform a selection,
press A any time a snap target is highlighted to
flag it. Flag several targets and the selection
snaps to their average location.

Flag a target more than once and it counts for more.

Multiple snapping targets.

### Navigating

A transformation doesn't lock you out of navigation: hold Alt and you can still zoom, pan, or orbit while it runs.

This behavior can be changed through the Transform Navigation with Alt setting
in the Keymap Preferences.

## S-Curves

### S-Curves

The curve underlying a mask spline looks like a Bézier curve but isn't exactly one.
Feathering is what gives a mask its soft edges.
What was needed was a curve that supported feathering and kept the feather glued to the curve as you edited it,
to make animating it easier. The result is called an S-curve.

On top of the handles, each control point also carries points that lay out the feather between
that point and the next one along the spline.
Every feather point lives in UW space,
where U is the position along the spline segment and W (weight) is the distance separating the main spline from the feather points.

S-Curve explained.

The upshot is that you can deform the main spline almost however you like,
and the feather refreshes on its own to match.

Take pure rotation of the spline, for example:
the feather wouldn't budge. Move one point's feather, and
the rest stretch uniformly along that segment,
keeping the overall shape close to what an artist would expect.

### Primitives

Reference

Mode :

Mask Mode

Tool :

Add

Shortcut :

Shift - A

Two primitives are on offer: a Bézier Circle and a Square with vector handles.

## Selecting Tracks

All A
Selects all items.

None Alt - A
Deselects all.

Inverse Ctrl - I
Toggles selection state.

Box Select
Reference
Mode: All modes
Menu: Select ‣ Box Select
Shortcut: B

See Select Box documentation.

Circle Select
Reference
Mode: All modes
Menu: Select ‣ Circle Select
Shortcut: C

See Select Circle documentation.

Lasso Select
Reference
Mode: All modes
Menu: Select ‣ Lasso Select
Shortcut: Ctrl - Alt - RMB

See Select Lasso documentation.

Select Grouped
Reference
Mode: All modes
Menu: Select ‣ Select Grouped
Shortcut: Shift - G

Chooses all tracks within a specified category.

Action
Which track group to select.

Keyframed Tracks: All tracks with manual keyframes.

Estimated Tracks: All algorithmically solved tracks.

Tracked Tracks: All tracks with frame-to-frame tracking data.

Locked Tracks: All protected tracks.

Disabled Tracks: All inactive tracks.

Track with Same Color: All tracks matching the active track's color.

Failed Tracks: All tracks failing reconstruction.

Select Stabilization Tracks
Reference
Mode: Tracking mode
Menu: Select ‣ Select Stabilization Tracks

Chooses tracks assigned to translation stabilization.

Select Stabilization Rotation Tracks
Reference
Mode: Tracking mode
Menu: Select ‣ Select Stabilization Rotation Tracks

Chooses tracks assigned to rotation stabilization.

## Shape

### Shape

Reference

Panel :

Physics ‣ Cloth ‣ Shape

Cloth Shape. 

Pin Group
Vertex group for pinning.

Pinning secures cloth by anchoring it to a Vertex Group. Methods include Weight Painting target areas. Per-vertex weight regulates pin intensity.

Stiffness
Anchor position stiffness.

Sewing
An alternative to pinning involves sewing springs—virtual springs pulling one part's vertices toward another part's. Unlike pinning (which locks vertices in place or to objects), sewing allows sliding. A cloak clasp instantiates this: sewing pulls corners about a character's neck with realistic freedom.

Create sewing springs by introducing edges in the mesh not belonging to faces. They join vertices that should draw together—like cloak corners.

Max Sewing Force
Highest force sewing springs can exert. Zero permits unbounded force but risks instability in early frames when ends separate widely.

Shrinking Factor
Cloth reduction factor; negative = growth.

Dynamic Mesh
Enables resting-shape animation via shape keys or modifiers (Armature, deformation modifiers) placed above the Cloth modifier. When active, the resting shape updates each frame, allowing unpinned cloth to squash and stretch with deforming characters yet move under physics control.

Typically cloth preserves the object's initial-frame shape, keeping it constant through the sim. This suits full realism but fails for cartoon characters using squash-and-stretch.

Rest Shape Key
Initiates cloth simulation from a selected Shape Key as the rest state, rather than evaluating shape keys and preceding modifiers normally. Mutually exclusive with Dynamic Mesh.

Lets you start the sim with pre-draped cloth without applying that shape as a plastic deformation that relaxes springs.

Visible only if the mesh contains shape keys.

## Effector

### Effector 

Effector objects direct and shape fluid behavior. To designate a mesh object as an effector, navigate to Properties ‣ Physics and click Fluid, then choose Effector as the fluid Type.

Tip

Force Fields

(such as wind or vortex) integrate with the system like other physics setups. Control over individual force type influence happens through domain object settings.

### Settings 

Reference

Panel :

Physics ‣ Fluid ‣ Settings

Type :

Effector

Effector Type

Collision :

Such objects interact with fluids through contact.

Guide :

These objects' velocity gets transferred during guiding bakes. Guiding effectors must move and possess velocity.

Velocity Factor

Multiplies guiding object velocities by this amount. Useful when coordinating multiple guiding objects with varying speed requirements.

Guide Mode

Specifies how guiding velocities merge into the global domain velocity field.

Maximize :

The guiding object compares its velocity magnitude against the field. When its absolute value exceeds the field's absolute value, its guiding velocity persists.

Minimize :

The guiding object compares its velocity magnitude against the field. When its absolute value falls below the field's absolute value, its guiding velocity persists.

Override :

The most straightforward approach. Guiding objects continuously replace the global guiding velocity field with their current velocity. Previous frame values or velocities from other guiding objects get superseded.

Averaged :

The guiding object writes the mean of its velocity and existing field velocity into the global guiding velocity field.

Sampling Substeps

Specifies how many substeps reduce gaps in fluid collision from quickly moving effectors.

Surface Thickness

Extends the effector region by this distance, expanding its interactive area.

Use Effector

Toggles whether the effector influences the fluid. This property facilitates animations that selectively engage or disengage effector impact.

Is Planar

Marks the effector as either a single-dimension object (such as a plane) or Non-manifold geometry. This declaration ensures accurate fluid simulation on these mesh types.

A manifold mesh can also be flagged as planar. The solver then disregards internal volume and treats the mesh sides as fluid emission boundaries.

## Flow

### Flow 

Flow types manage fluid introduction and removal from a domain. Flow objects require placement within the domain's bounding box for functionality.

To establish a mesh object as a Flow emitter, select Fluid from Properties ‣ Physics and choose Flow as the fluid Type to generate a default flow source.

### Settings 

Reference

Panel :

Physics ‣ Fluid ‣ Settings

Type :

Flow

Flow Type

Smoke :

Produces smoke only.

Fire + Smoke :

Produces both fire and smoke.

Fire :

Produces fire only.
The domain automatically generates accompanying smoke to represent residual combustion byproducts.

Liquid :

Produces liquid.

Flow Behavior

Dictates whether the Flow object contributes ( Inflow ), extracts ( Outflow ), or transforms the mesh into fluid material ( Geometry ).

Inflow :

This object discharges fluid into the simulation, functioning like a water source or fire base.

Outflow :

Fluid that crosses into this object's bounding box gets removed from the domain (comparable to a drain or absorption point). Useful alongside inflow objects to prevent domain saturation. Outflow objects respond to animation, with removal zones tracking their position.

Geometry :

Interior portions of this object within the domain boundary convert to simulation fluid. Multiple fluid objects may coexist. Ensure surface normals face outward or simulation accuracy suffers. Unlike domain objects, fluid objects use their actual mesh topology.

Use Flow Inflow Outflow
Enables or disables fluid transfer. This toggle assists animations where fluid addition or removal needs selective activation.

Sampling Substeps

Counts how many sub-steps diminish gaps in fluid emission from rapidly moving sources.

| Sampling sub-steps: 0.  | Sampling sub-steps: 3.  |

Note

Sub-Steps happen at each simulation step rather than per frame. The adaptive time stepping system regulates simulation step frequency.

Smoke Color

Sets the hue of discharged smoke. When different colors combine, they blend into a unified tint.

Absolute Density

When activated, the emitter generates smoke or fire exclusively when capacity exists within the emitter zone. Otherwise, continuous generation accumulates emissions.

Initial Temperature

Represents the temperature gap between emitted smoke and the domain's baseline temperature. This setting's influence on smoke depends on the domain's Heat Buoyancy configuration.

Density

Specifies the smoke quantity emitted per cycle. Higher values increase output density.

Fuel

Sets the fuel combustion rate per second. Larger values produce bigger flames; smaller values create smaller flames.

| Fuel: 0.5.  | Fuel: 1.0.  |

Vertex Group

When assigned, the designated Vertex Group constrains smoke emission zones.

### Flow Source 

Flow Source

Specifies the mechanism for fluid discharge.

Mesh :

Fluid releases directly from the object's mesh surface.

Is Planar

Marks the effector as either a single-dimension object (such as a plane) or Non-manifold geometry. This declaration guarantees accurate fluid simulation on these configurations.

Surface Emission

Sets the maximum voxel distance from mesh surface where fluid gets released. Since voxel-based calculation applies, results vary with domain resolution.

Volume Emission Fire or Smoke Only :
Specifies the fluid fraction to emit within the emitter mesh, with 0 as none and 1 as complete. Emitting fluid based on volume produces unpredictable outcomes when mesh topology lacks proper connectivity.

Particle System :

Fire or Smoke Only :
Generates smoke or fire from a particle system linked to the flow object.

Particle system selection uses a Data ID reference.

Note that only Emitter-type particle systems produce smoke. Consult Particles for particle system creation guidance.

Set Size

When activated, the Size parameter limits maximum voxel distance for particle-based smoke emission, mirroring Surface Emission behavior for mesh sources. Deactivated, particles fill the nearest voxel entirely.

### Initial Velocity 

When enabled, the fluid inherits the momentum of its source.

Source

Multiplier for inherited velocity. A value of 1 emits fluid at source speed.

Normal

Governs how much velocity fluid receives along a face Normal. Initial velocities always distribute along all face normals regardless of this setting. Thus, closed flow source geometry releases fluid in multiple directions. Achieving single-direction emission requires all normals pointing identically. A plane flow object accomplishes this naturally.

Initial X, Y, Z

Velocity components along X, Y, Z axes in world coordinate space. These augment velocity along the Normal direction.

### Texture 

Reference

Type :

Flow

Panel :

Physics ‣ Fluid ‣ Settings ‣ Texture

When activated, the specified texture and accompanying configuration control smoke or fire emission zones on the mesh. These parameters do not affect Outflow Flow Behavior.

Texture

A Data ID reference for the texture selection.

Mapping

Determines whether Generated UVs or explicit UV mapping governs texture application.

Size

Controls overall texture scaling.

Offset

Displaces the texture along the Z direction.

## Curve Guide

### Curve Guide 

Reference

Panel :

Physics ‣ Force Fields

Type :

Curve Guide

The Curve Guide constrains particles to follow a trajectory defined by a Curve Object. Common applications include transporting a red blood cell along a vein or animating particle movement within a motor. Additionally, this guide can shape specific hair strand paths.

Note

Particle Edit Mode offers an alternative path definition approach.

Curves can animate like soft bodies or any standard method, allowing elaborate animations with minimal computational overhead. Such flexibility maintains fine control while keeping simulation time reasonable.

To orient particles along the curve direction, set their Orientation Axis to Velocity / Hair, enable Dynamic, and configure Angular Velocity Axis to Velocity in the particle system rotation settings. The Follow Path Constraint and curve's legacy Follow mode prove incompatible with this approach.

A Curve Guide affects all particles on the same layer irrespective of their distance to the curve. Stacking multiple guides combines their field effects additively (following classical physics principles). Adjust the Minimum Distance to cap their influence radius.

Particles follow a Curve Guide throughout their existence. Their traversal speed depends on lifetime duration and path length.

Note

The Curve Guide does not influence soft bodies.

### Options 

UI for a Curve Guide force field. 

Free

The fraction of particle lifetime spent outside the curve path.

Falloff Power

Regulates guide strength between Min Distance and Max Distance thresholds. A value of 1 produces linear degradation.

Additive

When used, particle speed evaluation incorporates falloff as well.

Weights

Leverage Curve weights to modulate particle influence progression along the path.

Clumping Amount

Particles converge at the curve end (1) or scatter apart (-1).

Shape

Governs convergence form. A value of +0.99 concentrates particles at the curve terminus. Zero gives linear distribution. A value of -0.99 gathers particles at the curve origin.

Min Distance

Specifies the distance within which the field maintains complete strength. Zero falloff negates this since the field works fully to Max Distance (or infinitely). Circles at curve endpoints indicate this radius in the 3D Viewport.

Max Distance

Sets the upper boundary for field reach, denoted by circles in the viewport.

### Kink 

Warning

The current implementation contains a defect; see Bug Report #46776.

Type

Modifies the shape particles assume.

None :

Braid :

Curl :

Influence extends based on curve-to-emitter separation.

Radial :

A three-dimensional standing oscillation.

Roll :

A one-dimensional standing oscillation.

Rotation :

Wave :

A two-dimensional standing oscillation.

Describing the resulting geometries requires observation. Check the example further below.

Kink options of a curve guide. From left to right: Radial, Wave, Braid, Roll.
Animation. 

Axis

The basis for offset application.

Frequency

The repetition rate of the offset pattern.

Shape

Tunes the offset positioning at the path beginning or terminus.

Amplitude

The maximum extent of the offset displacement.

### Examples 

Curve Guide force field.
