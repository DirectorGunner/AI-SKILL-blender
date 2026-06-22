# Hinge Constraint, Motor Constraint, Piston Constraint, Point Constraint ...

> Blender Add-ons, Panels, and Properties reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Hinge Constraint; Motor Constraint; Piston Constraint; Point Constraint; Slider Constraint; Dynamics; Rigid Body World; Interior; Cache; Solver; Clear; Constraints; Parenting Objects; Track; Align to Transform Orientation.

## Hinge Constraint

### Hinge Constraint 

Reference

Panel :

Physics ‣ Rigid Body Constraint

Type :

Hinge

The hinge permits single-degree-of-freedom motion between objects. Translation remains fully constrained.
Rotation about the constraint object's Z axis is allowed.
Adjusting the constraint object's position and orientation governs hinge anchor and axis placement.

The Hinge represents the sole single-axis rotation constraint using the Z axis rather than X. Verify axis alignment if hinge behavior diverges from expectations.

Hinge constraint options. 

### Options 

Limits

Z Angle
Enable/disable Z-axis rotation limits.

Lower
Minimum Z-axis rotation.

Upper
Maximum Z-axis rotation.

## Motor Constraint

### Motor Constraint 

Reference

Panel :

Physics ‣ Rigid Body Constraint

Type :

Motor

The motor constraint generates translation and/or rotation between objects.
It drives objects apart or together, creates simple rotation, or combines rotation with translation.
Translation may be blocked while rotation continues—the constraint differs from a screw.

The rotation axis is the constraint object's X axis, contrasting with Hinge's Z axis.
The Motor is vulnerable to confusing perturbations without a matching Hinge constraint—axes must align carefully.
Misalignment causes apparent motor inactivity.

Motor constraint options. 

### Options 

Linear Motor/Angular Motor

Enable
Activates linear or angular motor.

Target Velocity
Linear or angular motor target velocity.

Max Impulse
Maximum linear or angular motor impulse.

## Piston Constraint

### Piston Constraint 

Reference

Panel :

Physics ‣ Rigid Body Constraint

Type :

Piston

A piston permits translation along the constraint object's X axis, and rotation around that axis.
It combines slider and hinge freedoms (neither particularly unconstrained individually).

### Options 

Limits

X Axis
Enable/disable X-axis translation limits.

Lower
Minimum X-axis translation.

Upper
Maximum X-axis translation.

X Angle
Enable/disable X-axis rotation limits.

Lower
Minimum X-axis rotation.

Upper
Maximum X-axis rotation.

## Point Constraint

### Point Constraint 

Reference

Panel :

Physics ‣ Rigid Body Constraint

Type :

Point

Objects link via a point bearing permitting unrestricted rotation around the constraint object location, but blocking translation.
The physics engine enforces coincidence between the constraint-designated points on the two constrained objects.

Point constraint options.

## Slider Constraint

### Slider Constraint 

Reference

Panel :

Physics ‣ Rigid Body Constraint

Type :

Slider

The Slider permits relative translation along the constraint object's X axis, blocking rotation and translation on other axes.

### Options 

Limits

X Axis
Enable/disable X-axis translation limits.

Lower
Minimum X-axis translation.

Upper
Maximum X-axis translation.

## Dynamics

### Dynamics 

Reference

Panel :

Physics ‣ Rigid Body ‣ Dynamics

Rigid Body Dynamics panel. 

Controls rigid body simulation physics.
This panel applies only to Active rigid bodies.

Damping Translation
Linear velocity loss per unit time.

Rotation
Angular velocity loss per unit time.

### Deactivation 

Enable resting rigid bodies to deactivate, improving performance and stability (though occasional glitches may occur).

Start Deactivated
The body initializes deactivated, activating when nearby moving active bodies approach. Proximity checks use bounding boxes.

Linear Velocity
The linear deactivation threshold below which bodies deactivate and stop simulating.

Angular Velocity
The angular deactivation threshold below which bodies deactivate and stop simulating.

## Rigid Body World

### Rigid Body World 

Reference

Panel :

Scene ‣ Rigid Body World

The Rigid Body World groups rigid body objects, holding settings applicable to all.

When rigid body physics gets added, the system creates a group—default name "RigidBodyWorld".
Rigid body objects join this group automatically.
Multiple Rigid Body World Collections exist; allocate bodies via the Collections panel.

Rigid body objects and constraints participate in simulation only when in the collection specified by Rigid Body World's Collection field.

### Settings 

Rigid Body World
Enable/disable rigid body simulation evaluation for participating objects in the specified collection.

Remove Rigid Body World
Eliminate rigid body simulation from the scene.

Collection
The collection housing rigid body objects in this simulation.

Constraints
The collection housing rigid body constraints in this simulation.

Simulation quality and timing:

Speed
Adjusts simulation tempo.

Split Impulse
Enable/disable reduction of extra velocity accumulating on collision.
(Reduces stability slightly; use when necessary.)
Limits collision-separation force, producing nicer results but reduced stability (especially with many stacked objects).

Substeps Per Frame
Simulation steps per frame (higher values increase accuracy at the cost of speed).
Affects accuracy only, not speed.

Solver Iterations
Constraint solver iterations per step (higher values increase accuracy at the cost of speed).
Higher iterations stabilize constraints and stacking.

### Rigid Body Cache 

Reference

Panel :

Scene ‣ Rigid Body World ‣ Cache

The Cache subpanel specifies simulation frame range and enables baking.

Start/End
Simulation's first and last frame.

Bake
Computes and locks the cache. Object Mode required.

Delete Bake
Available after baking; clears the cached result.

Calculate to Frame
Computes physics through the current frame.

Current Cache to Bake
Converts current cache to bake.

Bake All Dynamics
Computes all physics.

Delete All Bakes
Eliminates all cached physics in the current scene.

Update All to Frame
Advances cache through current frame.

Unsaved blend-files store cache in memory; save first or lose the cache.

### Rigid Body Field Weights 

Reference

Panel :

Scene ‣ Rigid Body World ‣ Field Weights

Like other physics systems, rigid body simulation responds to external force fields.

## Interior

### Interior 

By default, soft-body mesh edges behave like springs—stretching under tension, compressing under pressure, returning to "rest" length.

Spring behavior maintains mesh cohesion. Disabling this (and Goal) frees each vertex to move independently, stretching the mesh beyond recognition.

Springs along edges prove insufficient: quad vertices move toward diagonal opposites, collapsing quads.

Diagonal edges everywhere would solve this; instead, enable Stiffness to let Blender create interior diagonal springs automatically—no mesh changes needed.

| Base springs along edges.  | Additional springs when Stiffness is enabled.  |

Bending Stiffness adds rotational resistance, keeping edges at consistent angles.

Both appear in detail below. Configure them in Soft Body Edges panel.

### Stiffness 

Illustrate Stiffness effects by dropping two cubes onto a plane (see Collisions).
The blue cube uses quads; red uses triangles. Both have Goal disabled.

Without Stiffness, the quad cube collapses entirely; the tri cube temporarily deforms then recovers:

| Frame 1.  | Frame 36.  | Frame 401.  |

With Stiffness enabled, the quad cube maintains form via interior springs:

| Frame 1.  | Frame 36.  | Frame 401.  |

### Bending Stiffness 

Bending Stiffness prevents collapse; combine with Stiffness for bending resistance on diagonals.

Cube test using Bending Stiffness alone:

| Frame 1.  | Frame 36.  | Frame 401.  |

Both cubes retain shape. Try with subdivided planes—quad-based and triangulated:

| Two planes falling.  | No bending stiffness.  | High bending stiffness (10).  |

Without Bending Stiffness, faces rotate freely as if hinged. Stiffness (adding diagonals) doesn't prevent this; triangulation similarly doesn't.

With high Bending Stiffness, edges resist rotation; planes behave like planks rather than cloth.

## Cache

### Cache 

Reference

Panel :

Physics ‣ Soft Body ‣ Cache

Soft-body simulations employ unified caching and baking systems.
See Particle Cache and General Baking for references.

## Solver

### Solver 

Reference

Panel :

Physics ‣ Soft Body ‣ Solver

This panel holds the controls that set how exact the soft body simulation comes out.

Step Size Min
The fewest sub-steps run for any one frame. Bump it up when a fast collider slips past the soft body unnoticed.

Max
The most sub-steps run for any one frame.
Ordinarily the Error Limit picks the count for you on the fly, so override it only with cause.

Auto-Step
Pick step sizes from how quickly things are moving.
This hands the solver a way to gauge its workload off scene velocities.

Error Limit
The headline knob for solution quality.
It dictates how tightly collisions are tested, making it the most consequential control here.
Try half the mean edge length as a first guess.
Drop it when jitter, visible errors, or exaggerated reactions show up.
Tracking its own error level is what lets the solver shift to adaptive step sizing.

### Diagnostics 

Print Performance to Console
Reports the solver's running status to the console.

Estimate Transforms
Estimate matrix, split to COM , ROT , SCALE .

### Helpers 

The controls below shape a soft body's reaction as it approaches, or bites into, a fellow collider on its layer.

Choke
Once a vertex or edge digs into a collision mesh, this tames its exit speed.

Fuzzy
A collision fuzziness factor; turning it up trades stability for quicker handling.
You end up with a faster yet rougher result.

## Clear

### Clear

Reference

Mode :

Object Mode

Menu :

Object ‣ Clear ‣ Location / Scale / Rotation / Origin

Shortcut :

Alt - G , Alt - S , Alt - R

Resetting transforms clears the transform values. Object location and rotation become 0, and scale becomes 1.

Clear Location Alt - G
Reset the object's position. The selection moves back to (0, 0, 0).

Clear Scale Alt - S
Reset the object's scale. The scale becomes (1, 1, 1).

Clear Rotation Alt - R
Reset the object's rotation. Rotation becomes 0 degrees on each axis.

Clear Origin
Resets the offset of child object origins from their parent. Child objects move to the parent's origin. The parenting relationship remains intact, verifiable via the Outliner confirming the child is still parented.

### Options

Clear Delta
Clears delta transform together with primary transforms. (Displays in the Adjust Last Operation panel.)

## Constraints

### Constraints

Operators for administering an object's Constraints.

### Add Constraint (with Targets)

Reference

Mode :

Object Mode and Pose Mode

Menu :

Object ‣ Constraint ‣ Add Constraint (with Targets)

Applies a constraint to the active object. Select the constraint type from a pop-up; it can be changed later via the Add Constraint (with Targets) Adjust Last Operation panel. If an additional object is selected besides the active one, that object becomes the constraint target (if the constraint accepts targets).

When a bone from a different armature serves as the constraint target, the tool accesses the non-active armature and uses its active bone, assuming that armature is in Pose Mode.

### Copy Constraints to Selected Objects

Reference

Mode :

Object Mode and Pose Mode

Menu :

Object ‣ Constraint ‣ Copy Constraints to Selected Objects

Transfers the active object's Constraints to the remaining selected objects.

### Clear Object Constraints

Reference

Mode :

Object Mode and Pose Mode

Panel :

Object ‣ Constraint ‣ Clear Object Constraints

Eliminates all Constraints on the selected object(s).

## Parenting Objects

### Parenting Objects 

When building intricate structures—such as a chronograph—you might model individual sections as distinct objects.
To coordinate the sections so they move together (as the "watch"), assign one as the parent of the rest.
These child objects inherit its position shifts, rotations, and size changes.

Unlike most living systems, every object or skeleton in Blender has one parent at most.
When you give an object a different parent while one already exists, the previous connection breaks.
The phrase "parents" when plural denotes the succession of ancestry: immediate parent, grandparent, great-grandparent, and so on.

### Make Parent 

Reference

Mode:
Object Mode

Menu:
Object ‣ Parent

Shortcut:
Ctrl - P

To establish parent-child bonds, pick at least two objects
(designate the child objects first, then select the parent object last),
then press Ctrl - P. The Set Parent To dialog appears, presenting
several parenting strategies to pick from.
Confirming an option applies the parent-child relationship.
All chosen objects will have their 'parent' property set to the active object,
becoming 'siblings' to each other.

The Set Parent To popup is context-aware: the number of choices shifts depending on the selection state
when Ctrl - P is triggered.

When the parent moves, rotates, or changes size, child objects typically transform identically.
However, the inverse is not true: modifying child objects leaves the parent unchanged.
The effect flows strictly downward—parent to child, not vice versa.

Tip

You can "relocate" a child back to its parent's location by resetting its origin.

Type
Blender provides numerous parenting approaches, listed here.
Along with linking the chosen objects, some approaches attach a Modifier or Constraint to the child,
with the parent as the destination, or activate a parent behavior like Follow Path.

- Object

- Armature Deform

- Bone

- Curve Deform

- Follow Path

- Path Constraint

- Lattice Deform

- Vertex

- Vertex (Triangle)

Keep Transform
The object's existing world position (its absolute location, rotation, and size in the world) is captured.
The new parent is established, and the Parent Inverse matrix is calculated to ensure
the object maintains its previous world position after parenting.

Hint

Refer to the Outliner

An alternative way to observe the parent-child structure and groupings is through the Outliner panel.

### Parent Inverse 

Blender can set a parent without shifting the child object's location.
A hidden matrix called the Parent Inverse matrix manages this,
sitting between the parent's and child's transform data.

When objects are parented using Ctrl - P, the Parent Inverse matrix is recalculated.
The object's local position, rotation, and scale may also shift based on the Set Parent selection. See Object Parent for details.

The Parent Inverse matrix gets cleared by Clear Parent Inverse.

Note

Parenting via the Object Properties panel always resets the Parent Inverse matrix.
This can trigger an unexpected shift in the object's location.
To sidestep this, use Ctrl - P when assigning a new parent.

### Object Parent 

Object Parent represents the most versatile parenting method in Blender.
It takes the chosen objects and makes the active object
the parent of all selections. Each child receives
all position, rotation, and size modifications from the parent. The parent can be any object type.

If the object currently has a parent, it is removed first.
This repositions the object to its own location, rotation, and scale,
free from the previous parent's effect.

Three operators allow parenting. They differ in how they calculate the Parent Inverse matrix
and the object's local Transform.

### Example: Object Parent (Keep Transform) 

Parenting with Keep Transform preserves any modifications that child objects received from
the prior parent.

Imagine a scene with two empty objects called "EmptyA"
and "EmptyB", and a Monkey object. Fig. Scene with no parenting. displays the three without
active parent relationships.

Scene with no parenting. 

Choose the Monkey with LMB and then Shift - LMB
choose "EmptyA" and press Ctrl - P and choose Object
from the Set Parent To menu.
"EmptyA" now serves as the Monkey's parent.
With only "EmptyA" picked, transforming it (rotating/scaling/moving) also transforms
the Monkey correspondingly.

Resize the "EmptyA" object, causing the Monkey to shrink and shift leftward.

The monkey becomes the child of "EmptyA". 

Now pick only the Monkey using LMB and then Shift - LMB
choose "EmptyB" and press Ctrl - P and pick Object from
the Set Parent To dialog.
"EmptyB" is now the Monkey's parent.
Watch the Monkey's scale change when you switch parents.

The monkey becomes the child of "EmptyB". 

This occurs because the Monkey was never directly resized—the change came from being parented to "EmptyA" which was resized.
Switching the Monkey to "EmptyB" removes those indirect changes,
because "EmptyB" has not been modified.

This is frequently the desired result, yet it's also useful to preserve
earlier transformations the child acquired from the original parent when changing parents.
If, instead of switching the Monkey's parent from "EmptyA" to "EmptyB" plainly, you chose parenting type Object and toggle Keep Transform ,
the Monkey would retain its resizing from "EmptyA"
when assigned to "EmptyB".

The Object parent with Keep Transform setting. 

To follow this example, here is the demonstration file:

File: Parent_-_Object_(Keep_Transform)_(Demo_File).blend.

### Bone Parent 

Bone parenting designates a specific bone in an armature as the parent of one or more separate objects.
When the armature is manipulated, the child object shifts
only when the designated bone moves.

Three armature images with four bones each. 

In Fig. Three pictures of armatures with four bones. the 2nd bone controls the child cube.
The cube transforms when the 1st or 2nd bones move.
Modifying the 3rd and 4th bones leaves the cube unaffected.

To employ bone parenting, first select all child objects, then Shift - LMB pick the armature
and move into Pose Mode and
pick the target bone by LMB.
Then press Ctrl - P and pick bone from the Set Parent To menu.

Now adjusting that bone during Pose Mode will also reposition the child objects.

### Relative Parenting 

Bone relative parenting is a per-bone toggle.
This behaves much like bone parenting with a single distinction.

With bone parenting, if you pick a bone with children and
shift to Edit Mode and reposition that bone;
Moving back to Pose Mode on that bone will
cause the child object to snap to the bone's Pose Mode position.

Single armature bone with a child cube parented via bone parenting. 

Picture 1 displays the initial setup. Picture 2 illustrates the state after modifying the bone in Edit Mode,
then returning to Pose Mode. Notice the child object shifts to align with the bone's new Pose Mode location.

Bone relative parenting operates differently;
Moving a parent bone in Edit Mode will not cause the child objects to shift to the bone's fresh Pose Mode position when you return to Pose Mode.

Single bone with bone relative parenting controlling a cube. 

Picture 1 illustrates the initial layout. Picture 2 demonstrates conditions after editing the bone in Edit Mode,
then switching back to Pose Mode.
The child retains its original spot and doesn't snap to the bone's fresh location.

Note

Setting parents with Ctrl - P and picking "Bone" or "Bone Relative"
will respectively deactivate or activate the bone's "Relative Parenting" feature.
Since "Relative Parenting" applies to individual bones, altering this affects
all children of that bone simultaneously.

### Vertex Parent 

For meshes, curves, surfaces, and lattices,
you can use a vertex or point as the parent of other objects.
You may parent objects to a solitary vertex or a trio of vertices;
doing so causes child objects to follow when the parent mesh deforms.

### Vertex Parent from Edit Mode 

In Object Mode, select the children and then the parent object.
Press Tab to enter Edit Mode and on the parent select either one vertex
to define a single anchor, or choose three vertices to define a zone
(the three vertices don't have to form a complete face;
any three from the parent work),
then press Ctrl - P and verify.

At this point, when a solitary vertex is chosen,
a line will appear linking the vertex to the child/children. When three
vertices are chosen, a line connects the child/children to the averaged position of
those three vertices (on the parent). As the parent mesh deforms and the parent vertex/vertices shift,
the child/children also shift.

### Vertex Parent from Object Mode 

Vertex parenting can be set from Object Mode;
this works like standard object parenting,
press Ctrl - P in Object Mode and pick Vertex or Vertex (Triangle).

Vertices nearest to each object are selected, which is typically the expected behavior.

| The small cubes can individually snap to triads of neighboring vertices on the icosphere using the "Vertex (Triangle)" option in the set parent menu.  | Reshaping the parent in Edit Mode causes each cube to follow its vertex parent independently.  | Resizing the parent icosphere in Object Mode likewise scales each cube as anticipated.  |

The parent context option lets creators rapidly establish many vertex parent
connections,
avoiding manual setup of each relationship.

Note

It resembles a "reversed" hook effect.

### Make Parent without Inverse 

Reference

Mode:
Object Mode

Menu:
Object ‣ Parent ‣ Make Parent without Inverse

This applies the parent and then resets the Parent Inverse matrix along with the object's local location.
Consequently, the object shifts to the parent's position but retains its rotation and scale.

Keep Transform
The object's existing world position (its absolute location, rotation, and size in the world) is captured.
The new parent relationship is applied, and the object's local transform values are adjusted to keep
its current world position even after the new parent is set.

### Clear Parent 

Reference

Mode:
Object Mode

Menu:
Object ‣ Parent

Shortcut:
Alt - P

Parent relationships can be severed using Alt - P.

Clear Parent
If the parent is among the selection, no change occurs.
If a child or children are chosen, they are separated from the parent,
become independent, and return to their original location, rotation, and proportions.

Clear and Keep Transformation
Separates the children from the parent while maintaining the location, rotation, and size that came from the parent.

Refer to Non-Uniform Scale which may be pertinent.

Clear Parent Inverse
Instead of severing the parent-child structure, this eliminates
the Parent Inverse matrix from the chosen objects. With a null matrix,
the location, rotation, and scale of the children are interpreted
in the parent's coordinate space.

### Known Limitations 

### Non-Uniform Scale 

When a parent has unequal scaling and is rotated relative to its child, shearing can occur.

Although parenting accommodates this, the shear gets lost if the parent is removed since it
cannot be stored as simple location, scale, and rotation values.

If Clear and Keep Transformation causes an unexpected object movement, non-uniform scale is likely the culprit.

## Track

### Track 

Reference

Mode:
Object Mode

Panel:
Object ‣ Track

These functions apply a tracking limitation to the chosen objects;
the target of the limitation will be the active object, which remains unchanged.

- Damped Track Constraint

- Track To Constraint

- Lock Track Constraint

### Clear Track 

Eliminates all Damped Track, Track To, and Lock Track Constraints from the chosen objects.

### Clear and Keep Transformation (Clear Track) 

Removes all Track Constraints from the picked objects, preserving the last position and orientation they achieved.

## Align to Transform Orientation

### Align to Transform Orientation 

Reference

Mode:
Object Mode and Edit Mode

Menu:
Object ‣ Transform ‣ Align to Transform Orientation

Reorients the picked objects so their local space aligns with the active Transform Orientation setting
from the Transform Orientation panel or the Orientation setting
in the Transform Last Operation panels.
