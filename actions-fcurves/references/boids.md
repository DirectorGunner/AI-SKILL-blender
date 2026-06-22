# Boids, Fluid, Newtonian, Velocity ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Boids; Fluid; Newtonian; Velocity; Emission; Collisions; Rigid Body Properties; Settings; Collision.

## Boids

### Boids 

Reference

Panel :

Particle System ‣ Physics

Type :

Boids

Boid Physics settings. 

Boid particle configurations operate under limited machine logic, programmable to heed fundamental behavioral guidelines. Ideal for recreating swarms, herds, schools of fauna or aquatic life, plus predator-prey dynamics. They respond to external objects and peer interactions. Boids absorb bounded information; therefore, Boid Brain rule ordering gains tremendous importance. In certain conditions, the system evaluates merely the foremost three parameters.

### Movement 

Reference

Panel :

Particle System ‣ Physics ‣ Movement

Boid Movement settings. 

Boids sidestep Collision-enabled entities, navigate toward mission targets, and escape from "predator" entities per Boid Brain logic. Flight versus ground locomotion shifts behavior characteristics.

Allow Flight

Grants airborne motion capability.

Allow Land

Grants terrestrial movement capability.

Allow Climbing

Activates goal-directed climbing.

Max Air Speed

The peak velocity boids attain during flight.

Min Air Speed

The threshold velocity boids preserve while airborne.

Max Air Acceleration

Governs how swiftly boids shift direction aloft, expressed proportional to peak velocity. Greater values enable sharper, more responsive aerial maneuvers.

Max Air Angular Velocity

Caps the turning rate of boids in flight as a percentage of 180 degrees. Lower magnitudes yield gradual arcs.

Air Personal Space

Airborne boid spacing radius as a percentage of body scale. Elevated values minimize crowding.

Landing Smoothness

Tunes touchdown softness. Higher settings produce gentle landings.

Max Land Speed

The peak velocity boids attain on terrain.

Jump Speed

The velocity magnitude boids achieve when leaving ground.

Max Land Acceleration

Governs how swiftly boids shift direction on terrain as a percentage of peak velocity.

Max Land Angular Velocity

Caps the turning rate of boids on ground as a percentage of 180 degrees. Lower values create fluid, unhurried turns.

Land Personal Space

Ground-based boid spacing radius as a percentage of body scale. Elevated values minimize congregation.

Land Stick Force

Governs the pressure needed to shift grounded boids. Lower magnitudes permit more spontaneous movement when responding to external forces.

Collision Collection

Filters collision engagement to a designated group exclusively. Beneficial for limiting interaction to target objects or surroundings.

### Battle 

Reference

Panel :

Particle System ‣ Physics ‣ Battle

Health

The starting boid vitality upon generation.

Strength

The maximum damage inflicted per second during assault.

Aggression

Determines combat intensity relative to adversary capability.

Accuracy

The assault precision rate.

Range

The maximum strike reach distance.

### Misc 

Reference

Panel :

Particle System ‣ Physics ‣ Misc

Banking

Rotation magnitude surrounding the velocity orientation during turns. A value of 1.0 creates realistic banking.

Pitch

The side-vector rotation component.

Height

Boid magnitude relative to particle scale.

### Relations 

Reference

Panel :

Particle System ‣ Physics ‣ Relations

Target

This list feature permits configuring interactions between the current boids and alternative particle systems.

Target Object

A data ID pointing to an object bearing a particle system.

System

The listed particle system's position on the Object.

Mode

Enemy :

Enemy classification generates competitive interactions.

Friend :

Friend classification promotes system coordination.

Neutral :

Neutral classification produces no alignment or hostility.

### Deflection 

Boids navigate around deflector geometries via Collision rule weighting. This works optimally with convex profiles (concave surface support requires further refinement).

### Force Fields 

Like other physics classifications, Boids responds to external force field influence.

Moreover, specialized Boid force fields pair with Boid physics. These effectors function as predators (positive Strength) that boids attempt to evade or objectives (negative Strength) that boids attempt to locate, based on the Boid Brain Avoid and Goal protocols respectively.

### Boid Brain 

Reference

Panel :

Particle System ‣ Physics ‣ Boid Brain

The Boid Brain panel configures how boid particles interact. Behavioral direction comes from a rule sequence. Memory constraints limit information processing. Remaining rules become disregarded once capacity gets exceeded.

Top-to-bottom rule parsing defines hierarchy (earliest rules take precedence). Arrow buttons on the right permit sequence reordering.

Rule Evaluation

Three evaluation paradigms govern rule processing:

Average

All rules receive equal weighting.

Random

Each boid selects a random rule.

Fuzzy

Implements fuzzy decision logic. Top-to-bottom traversal continues until a rule exceeds the Rule Fuzziness activation point. The metric represents rule compliance commitment (1 means strict adherence, 0 means no adherence). Multiple concurrent contradictory rules trigger simultaneous compliance per individual weight.

Note

Boids attempt rule adherence with maximum effort, though some may dominate others contextually. As example: evasion of a predator might overshadow Collision, Separate, and Flock adherence, permitting wall/object penetration despite contrary instructions—essentially a "panic override."

In Air

This rule applies during airborne states.

On Land

This rule applies during non-airborne states.

### Goal Rule 

Navigate toward objective.

Object

Designates the goal target. Absent assignment defaults to negatively-charged Boid force fields as goal markers.

Predict

Anticipates goal displacement.

### Avoid Rule 

Elude "predators".

Object

Designates the avoidance target. Absent assignment defaults to positively-charged Boid force fields as threat identifiers.

Predict

Anticipates threat displacement.

Fear Factor

Escape occurs if danger surpasses this threshold.

### Avoid Collision Rule 

Prevents contact with Deflection-enabled geometries.

Boids

Mutual boid collision avoidance.

Deflectors

Avoidance of deflector geometries.

Look Ahead

The anticipation window in seconds.

### Separate Rule 

Boids increase separation from neighbors.

### Flock Rule 

Boids emulate neighbor motion while maintaining separation.

### Follow Leader Rule 

Boids pursue a leader object rather than another boid.

Distance

The positioning distance trailing the leader.

Line

Encourages linear leader pursuit formation.

Queue Size

The permissible boid count in linear formations.

### Average Speed Rule 

Boids preserve baseline velocity.

Speed

The target speed as a proportion of maximum capability.

Wander

The randomization magnitude applied to velocity orientation.

Level

The Z velocity component permanence degree.

### Fight Rule 

Boids advance toward neighboring boids.

Fight Distance

The maximum assault approach distance.

Flee Distance

The separation threshold during retreat.

In Air

This rule governs airborne behavior.

On Land

This rule governs ground behavior.

### Goal Rule 

Navigate toward designated target.

Object

Identifies the goal reference. Defaults to negatively-charged Boid force fields without specification.

Predict

Estimates target trajectory.

### Avoid Rule 

Retreat from adversaries.

Object

Identifies the avoidance reference. Defaults to positively-charged Boid force fields without specification.

Predict

Estimates adversary trajectory.

Fear Factor

Evasion commences when threat level surpasses this value.

### Avoid Collision Rule 

Prevents Deflection-configured obstacles.

Boids

Prevents boid-boid contact.

Deflectors

Prevents contact with deflector surfaces.

Look Ahead

The temporal forecast window (seconds).

### Separate Rule 

Boids maintain interpersonal distance.

### Flock Rule 

Boids mimic neighboring motion while maintaining interpersonal spacing.

### Follow Leader Rule 

Boids pursue a leader entity instead of another boid.

Distance

The following distance position relative to the leader.

Line

Establishes linear pursuit arrangement.

Queue Size

The maximum linear follower count.

### Average Speed Rule 

Boids keep baseline movement rate.

Speed

The velocity goal expressed as a percentage of capability.

Wander

The arbitrary change magnitude in movement orientation.

Level

The degree that vertical movement stays consistent.

### Fight Rule 

Boids approach neighboring boids.

Fight Distance

The maximum engagement approach distance.

Flee Distance

The retreat separation distance.

## Fluid

### Fluid 

Reference

Panel :

Particle System ‣ Physics

Type :

Fluid

Fluid Physics settings. 

Fluid particles share similarities with Newtonian ones yet experience influence from internal mechanisms like pressure, surface interaction, internal friction, linking, and more. Applications range from viscous substances, gels, sandy materials, and misty smoke to countless additional scenarios.

Blender leverages SPH methodology for solving particle fluid mechanics. Smoothed-particle hydrodynamics represents a numerical approach for modeling fluid behavior. Applications span astrophysics, weapons science, volcanic processes, and hydrography. It embodies a coordinate-following, grid-independent Lagrangian formulation, with spatial fidelity tuneable through parameters including density.

### Options 

Fluid physics share configurations with Newtonian Physics. Comprehensive coverage appears on that documentation page.

### Fluid Properties 

Stiffness

The fluid's resistance to compression.

Viscosity

Viscous resistance to deformation. Lower settings model thicker liquids.

Buoyancy

Synthesized upward thrust resulting from density gradients, acting opposite gravity.

### Advanced 

Reference

Panel :

Particle System ‣ Physics ‣ Advanced

Repulsion Factor

Governs how vigorously fluid resists clumping (scaled as a stiffness multiple). Checkbox ties repulsion to stiffness value.

Stiff Viscosity

Introduces viscous opposition when fluid expands. Checkbox couples this to standard viscosity.

Interaction Radius

Sets the range of fluid force exchange. Checkbox couples this to 4 × particle size.

Rest Density

Establishes baseline fluid density. Checkbox couples this to standard density.

### Springs 

Reference

Panel :

Particle System ‣ Physics ‣ Springs

Force

Spring tension coefficient.

Rest Length

The equilibrium distance between spring-connected particles, scaled to particle radius. Checkbox couples this to 2 × particle size.

Viscoelastic Springs

Implements nonlinear spring mechanics rather than traditional Hooke's law.

Elastic Limit

The extension/compression threshold before rest length adaptation initiates.

Plasticity

The threshold of rest length variance following elastic limit breaching.

Initial Rest Length

Uses original particle spacing instead of 2 × particle size as the spring baseline.

Frames

The duration (in frames) from particle genesis during which spring creation continues (0 means perpetual).

## Newtonian

### Newtonian 

Reference

Panel :

Particle System ‣ Physics

Type :

Newtonian

Particles follow classical (Newtonian) mechanics. Particles launch with designated initial velocity and spin vectors, moving under external force direction. Spatial reactivity and force response computation varies per the animator-selected integration algorithm.

Newtonian Physics settings. 

### Forces 

Reference

Panel :

Particle System ‣ Physics ‣ Forces

Brownian

The Brownian motion magnitude. Brownian motion adds stochastic perturbation based on Brownian field noise. Simulates tiny randomized gusting effects nicely.

Drag

Velocity diminishment proportional to speed and scale (suitable for air or aquatic friction simulation).

Damp

Velocity reduction (friction, resistance, energy loss).

### Integration 

Reference

Panel :

Particle System ‣ Physics ‣ Integration

Integrators furnish mathematical frameworks for calculating particle trajectories. Choose per your animation targets per the following direction.

Integration

Euler

Referred to as "Forward Euler". The most basic integrator. Executes fast yet produces less precise results. Without dampening, particles gradually accumulate energy. Bouncing particle energy increases with each bounce as an example. Distinguished from "Backward Euler" (absent here) which dissipates energy gradually. Deploy for brief simulations or highly-dampened scenarios where computation speed outweighs numerical accuracy.

Verlet

Executes swiftly with excellent balance. Energy preservation occurs with minimal computational drift.

Midpoint

Titled "2nd order Runge-Kutta". Slower than Euler yet substantially more accurate. Constant acceleration (minus drag scenarios) preserves energy. Bouncing particles occasionally exceed starting height infrequently, avoiding systematic climbing. Generally superior for most situations.

RK4

Termed "4th order Runge-Kutta". Comparable to Midpoint yet slower with enhanced precision. Energy remains conserved even with variable acceleration. Reserve for complex situations where Midpoint proves inadequate.

Timestep

The elapsed simulation duration (in seconds) per frame.

Subframes

Computational substeps per frame. Increased counts improve stability and resolution precision for rapidly-moving particles.

The following configurations apply exclusively to Fluid-type physics:

Adaptive

The system independently computes the substep count.

Threshold

A precision allowance establishing how far a particle can relocate before requiring extra substeps. Governs relative distance tolerance.

Minimum frame steps number becomes Subframes + 1. Elevated turbulence may trigger supplementary substeps per Threshold specifications.

### Deflection 

Reference

Panel :

Particle System ‣ Physics ‣ Deflection

Size Deflect

Particle scale factors into deflection computations.

Die on Hit

Particles terminate upon deflector impact.

Collision Collection

When specified, particles collide with grouped entities exclusively.

## Velocity

### Velocity 

Reference

Panel :

Particle System ‣ Velocity

Particle starting velocity depends on system classification. Emitter or Hair systems activate these parameters for particle trajectory initialization.

Normal

The emitter's surface normals (enabling surface normal velocity).

Tangent

Surface tangent provides particle velocity.

Tangent Phase

Modifies the surface tangent orientation.

Object Align

Imparts initial velocity across X, Y, and Z coordinates.

X, Y, Z

Object Velocity

The emitter object's kinetic state (enabling movement-derived velocity).

Randomize

Varies the starting velocity. A texture can restrict value alteration; refer to Controlling Emission, Interaction and Time.

## Emission

### Emission 

Reference

Panel :

Particle System ‣ Emission

Settings for hair particle system generation. 

Number
Governs the strand count; minimize particle count when feasible (especially when planning soft-body animation), but maintain adequate coverage for effective styling.
A few thousand particles generally suffices for typical hairstyles.
Hair density increases subsequently through Children.

Hair Length
Sets strand length.

See also

Emitter particles Emission panel

## Collisions

### Collisions 

Reference

Panel :

Physics ‣ Rigid Body ‣ Collisions

Rigid Body Collisions panel. 

Shape
Determines object collision shape; categories include primitives and mesh-based shapes.

Primitive shapes ( Box , Sphere , Capsule , Cylinder , and Cone )
optimize memory and speed but may not match actual geometry.
Bounding-box dimensions determine size; geometric centers provide mass-center locations.
Enabling Extras Overlay visualizes primitives.

Mesh-based shapes ( Convex Hull and Mesh ) derive from actual geometry, offering better representation.
Object origin defines mass center for these shapes.

Box :

Box-like geometry (cubes), including ground planes.
Bounding-box axes determine per-axis dimensions.

Sphere :

Sphere geometry.
Radius: the bounding box's largest axis.

Capsule :

Points toward the Z axis.

Cylinder :

Points toward the Z axis.
Height from Z axis; radius from the larger of X or Y axes.

Cone :

Points toward the Z axis.
Height from Z axis; radius from the larger of X or Y axes.

Convex Hull :

Mesh-like surface encompassing all vertices (shrink-wrapped geometry).
Convex approximation offering good performance and stability with fewer vertices.

Mesh :

Triangle-only mesh allowing detailed interactions beyond convex hulls.
Enables concave shapes, though slower and less stable.

Compound Parent :

Combines child collision shapes.
Enables concave construction from primitives, typically faster than Mesh shapes and more stable.

Source
Mesh source for collision-shape generation.

Base :

The object's base geometry.

Deform :

Applies shape keys and deform modifiers.

Final :

Includes all deformations and modifiers.

Deforming
Mesh shapes deform during simulation.

### Surface Response 

Friction
Movement resistance; specifies velocity loss upon collision.

Bounciness
Rebound magnitude after collision (0 to 1, rigid to perfectly elastic).
Determines how much objects bounce following contact.

### Sensitivity 

Collision margins enhance performance and stability.
Shape-dependent behavior: some shapes embed margins; others show visible gaps.

Embedded margin shapes:

- Sphere

- Box

- Capsule

- Cylinder

- Convex Hull: uniform scale required when embedded.

Non-embedded margin shapes:

- Cone

- Active Triangle Mesh

- Passive Triangle Mesh: usually zero.

Margin
Collision proximity threshold where interactions still occur; nonzero values typically perform best.

### Collections 

Rigid body collision allocation uses groups (up to 20).

## Rigid Body Properties

### Rigid Body Properties 

Reference

Panel :

Physics ‣ Rigid Body

Type
The body's simulation role.

Active :

The body is dynamic, directly controlled by simulation.

Passive :

The body remains static, animation-controlled, lacking Dynamics properties.

## Settings

### Settings 

Reference

Panel :

Physics ‣ Rigid Body ‣ Settings

Default rigid body panel. 

Mass
Determines heaviness, weighing independent of gravity.

Tip

Predefined mass presets exist via the Calculate Mass operator.

Dynamic
Toggles rigid body simulation.

Animated
Allows animation system control alongside rigid body simulation.

## Collision

### Collision 

Two collision categories exist: inter-object and internal.
Clarification: collision calculations primarily target soft-body vertices.
Insufficient vertices restrict collision. Secondarily, edges and faces enhance calculations.

### Collisions with Other Objects 

Soft bodies need prerequisites for object collision:

- If Collision Collection is specified, the object must belong to it.

- The collision object must be a mesh.

- Activate Collision in Physics for the collision object.
The object may itself be a soft body.

### Examples 

A soft body cube colliding with a plane functions reasonably (Fig. A soft body cube colliding with a plane.), whereas a soft body plane passes through a cube without interaction (Fig. A soft body plane colliding with a cube, so no interaction at all.).

| A soft body cube colliding with a plane.  | A soft body plane colliding with a cube, so no interaction at all.  |

Why? Default calculation checks only soft-body plane vertices for cube collision.
Activate Collision: Face in Soft Body Edges to check plane-face-to-object collision—more expensive.

Understanding collision calculation enables optimization:

### Calculating Collisions 

Default soft-body simulation operates per-vertex. If soft-body vertices don't collide with the object, no interaction occurs.

The video below shows vertices colliding with a plane.
A vertex entering the zone between Outer and Inner experiences repulsion along the face normal.
Final position depends on acting forces. The example shows balanced gravity and repulsion (first vertex).
The Choke parameter in Soft Body Solver settings controls extraction speed.

See also

Download the blend-file.

Observe vertices traveling at varied speeds.
The rightmost vertices (fifth and sixth) exceed collision-zone passage speed due to default solver precision.
The fourth travels quickly; heavier mass breaches the inner zone. The first three collide correctly.

Configure collision in Soft Body Edges to include edges and faces via Collision Face and Edge options.
Different calculation checks whether edges/faces intersect the collision object; collision zones don't apply.

### Good Collisions 

Problematic collision setups may improve via:

- Soft bodies require more subdivisions than collision objects.
Add loop cuts strategically in high-collision regions.

- Check face normal orientation.

- Collision-object spikes might penetrate the soft body.

- Solver resolution must match soft-body vertex speed.
Lower Error Limit; carefully raise Min Step.

- Outer and Inner should be adequate; opposite-face zones shouldn't overlap, preventing conflicting forces.

- Strong forces demand large zones.

- Set Choke high (maximum if needed) for vertex repulsion difficulties.

- Face collision proves difficult and time-consuming. Avoid if possible.

Often, simplified collision-object meshes perform better, though difficulty arises with animated meshes.

### Self-Collisions 

See Self Collision settings for self-collision details.
