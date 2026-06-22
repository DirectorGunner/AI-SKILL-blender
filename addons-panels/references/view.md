# View, Collisions, Field Weights, Settings ...

> Blender Add-ons, Panels, and Properties reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: View; Collisions; Field Weights; Settings; Property Weights; Brush; Collections; Adaptive Domain; Guides; Boid; Charge; Drag; Fluid Flow; Force; Harmonic; Lennard-Jones; Magnetic; Turbulence.

## View

View panel features.

Annotations

Annotation strokes enable/disable via panel header checkbox—standard annotation panel with layer/frame controls.

Difference from other areas: on-demand layer creation (stroke without prior layer) sets default color to pink, heightening contrast.

Data Source
Current annotation storage location.

Clip: Store with active Movie Clip data-block.

Track: Store with active Track data-block.

See Annotation Tools for general information.

## Collisions

### Collisions

Reference

Panel :

Physics ‣ Cloth ‣ Collision

Fabric almost never floats isolated in space—it encounters other scene objects. Proper setup requires several interdependent components:

- The Cloth object must be configured to take part in collision detection.

- Optionally (though recommended) permit cloth to collide with itself.

- Other interacting objects must be visible to the Cloth object via shared layers.

- Other objects must be mesh-type.

- Other objects may move or be deformed by agents (armatures, shape keys).

- Other mesh objects must be enabled to deflect the cloth.

- The .blend file must be saved allowing simulation data storage.

- Execute Bake, computing cloth shape for the specified frame sequence.

- Edit the results or adjust the cloth mesh at individual frames.

- Adjust the surroundings or deforming objects, then re-run from the current frame.

Cloth Collisions panel. 

Quality
General parameter controlling simulation fidelity. Larger values consume more time but ensure fewer tears and penetrations.

### Object Collisions

When cloth needs deflection from another object, that object must activate collision physics (not on the cloth itself).

To permit objects to repel cloth, enable collision physics on the obstacle object.

Note

Non-mesh objects (NURBS surfaces, text) require Convert to mesh format.

Distance
How close another object must approach before the simulator repels the cloth. Smaller values risk errors but run faster; larger values become unrealistic and costly. Balance matters.

Impulse Clamping
Reduces explosions in tight, intricate collisions by constraining post-collision displacement.

Vertex Group
Faces where all vertices belong to this group avoid collision with objects.

Collision Collection
Only objects in this Collection participate in cloth collision. These objects must also have Collision physics active.

### Self-Collisions

Real cloth cannot pass through itself; enabling self-collision enforces this. Computation rises, but realism improves.

Tip

Distant flags skip this; close-ups of capes or shirts should have it on.

Friction
Controls cloth slickness during self-collision. Silk exhibits lower friction than cotton.

Distance
Cloth begins repelling itself at this separation. Smaller values risk errors but accelerate; larger values look wrong or slow. Finding balance is key.

Impulse Clamping
Constrains motion after collision in cramped situations to prevent instability.

Vertex Group
Faces with vertices entirely in this group exclude themselves from self-collision.

See also

Example blend-file:
Cloth self-collisions.

### Troubleshooting

Collision detection issues have several solutions:

- Speed up: raise Object/Self Collision Distance. Fastest but less accurate, cloth appears buoyant.

- Refine: increase Cloth panel Quality. Creates finer solver steps, catching fast-moving contacts better. Boost Collisions Quality for additional refinement iterations.

- Manual edit: fix the cached/baked outcome in Edit Mode if needed.

- Strengthen: raise stiffness if deforming meshes tear the cloth.

## Field Weights

### Field Weights

Reference

Panel :

Physics ‣ Cloth ‣ Field Weights

Cloth, like other physics, reacts to external force effectors.

### Field Weights

Reference

Panel :

Properties ‣ Physics ‣ Fluid ‣ Field Weights

Type :

Domain

These settings determine gravity and Force Field influence on fluid.

Effector Collection
When set, fluid only reacts to force fields in the specified collection.

Gravity
Fluid gravity susceptibility.

All
Overall force field influence.

Others control specific field-type impact.

## Settings

### Settings

Reference

Panel :

Physics ‣ Cloth

Presets
Offers preset cloth configurations.

Quality Steps
Controls simulation steps per frame. More steps increase precision but reduce speed.

Speed Multiplier
Modifies the pace of cloth time progression.

### Settings 

Reference

Panel :

Physics ‣ Soft Body

Collision Collection
When specified, soft bodies collide only with collection objects instead of same-layer objects.

## Property Weights

### Property Weights

Reference

Panel :

Physics ‣ Cloth ‣ Property Weights

This panel constrains cloth attributes to a vertex group. Controlled properties span Physical Properties and Shape panels.

Structural Group
Vertex group controlling structural stiffness.

Max Tension
Highest tension stiffness.

Max Compression
Highest compression stiffness.

Shear Group
Vertex group for shear stiffness adjustment.

Max Shearing
Highest shear scaling.

Bending Group
Vertex group for bending stiffness adjustment.

Max Bending
Highest bending stiffness.

Shrinking Group
Vertex group for cloth contraction.

Max Shrinking
Maximum shrink amount; negative = maximum growth.

## Brush

### Brush

Reference

Panel :

Physics ‣ Dynamic Paint

Type :

Brush

A Brush applies paint to the canvas.

Brush main panel. 

This panel defines how the brush alters canvas color surfaces.

Paint Color
Paint hue.

Alpha
Brush transparency/visibility. Wetness also depends on alpha.

Wetness
Freshness of new paint. Visibility in "Paint" surface "wetmap". "Drip" and "Spread" speed depends on wetness.

Absolute Alpha
Constrains brush alpha influence. Without it, brush accumulates each frame, raising alpha and influence. Often preferable to cap brush alpha at its level.

Erase Paint
Dissolves existing paint instead of adding.

### Source

Reference

Type :

Brush

Panel :

Physics ‣ Dynamic Paint ‣ Source

Paint source panel. 

Paint source defines influence/intersection.

Mesh Volume

Brush affects points inside mesh volume.

Source: Mesh Volume. 

Proximity

Uses distance to brush mesh surface closest point. Interior isn't necessarily affected.

Source: Proximity. Brush affects surrounding canvas pixels. 

Mesh Volume + Proximity

Volume-type plus distance-based influence.

Inner Proximity
Applies proximity within volume.

Negate Volume
Inverts brush alpha inside volume.

| Volume + Proximity without extra settings.  | Inner Proximity shows proximity falloff inside volume.  |
| Negate Volume makes the volume interior transparent.  | Inner Proximity + Negate Volume combined.  |

Object Center

Instead of slow proximity-to-brush-mesh calculation, compute only center distance. Faster, usually adequate.

Source: Object Center. 

Particle System

Brush influence stems from selected particle system particles.

Effect Solid Radius
Solid-color paint distance.

Use Particle Radius
Adopts particle panel settings for solid radius. Disables manual Solid Radius.

Smooth Radius
Additional falloff radius beyond Solid Radius.

Zero Smooth Radius paints particles as solid spheres. Zero Solid Radius yields smooth halos.

Source: Particle System. 

### Common Options

Paint Distance
Max distance to mesh surface for paint influence.

Project
Projects brush to canvas from a direction. "Direction-aligned" proximity.

The Project option limits brush canvas effect to normal direction. 

Falloff

Sharp :

Solid paint within distance.

Smooth :

Linear fade-out to maximum distance.

Color Ramp :

Custom falloff behavior.

### Velocity

Reference

Type :

Brush

Panel :

Physics ‣ Dynamic Paint ‣ Velocity

Velocity panel. 

Velocity-based brush options appear here.

A color ramp and settings sit above. The ramp represents velocity: left = zero, right = "Max velocity". Speed is units per frame.

Checkboxes set ramp influence.

Multiply Alpha
Uses ramp alpha per current velocity, multiplying brush alpha.

Replace Color
Substitutes brush color with Color Ramp values.

Multiply Depth
Multiplies "depth intersection" effect. Adjust displace and wave per speed.

Do Smudge
Smudging "smears" surface colors as the brush travels. Smudge Strength controls intensity.

Brush still paints normally. Erase can pair with smudge. Zero alpha gives pure smudging.

### Waves

Reference

Type :

Brush

Panel :

Physics ‣ Dynamic Paint ‣ Waves

Brush Waves panel. 

This adjusts brush impact on "Wave" surfaces.

Wave Type
Selects brush wave creation style.

Depth Change :

Brush creates waves when intersection depth changes at a point. Stationary brushes don't activate. Negative "Factor" makes appealing "wake" for moving ships.

Obstacle :

Brush continually affects while intersecting. Waves reflect off this type. Due to algorithm limits, stationary brushes create unnatural "dent".

Force :

Directly impacts wave velocity, not one-to-one with intersection depth, yet depth determines force magnitude.

Reflect Only :

No visible solo effect; only bounces existing waves.

Factor
Strength of brush "depth" effect. Negative values pull water up.

Clamp Waves
Brushes penetrating too deeply break simulations. This limits influence to specific depths.

## Collections

### Collections

Reference

Type :

Domain

Panel :

Properties ‣ Physics ‣ Fluid ‣ Collections

Flow
If set, only Collection objects serve as Flow sources in this domain.

Effector
If set, only Collection objects act as Effector objects in this domain.

## Adaptive Domain

### Adaptive Domain

Reference

Type :

Domain

Panel :

Physics ‣ Fluid ‣ Adaptive Domain

Enabling adaptive domain shrinks the boundary to envelope gas efficiently, reducing computation by omitting empty voxels. The original domain constrains expansion unless Add Resolution increases bounds.

Add Resolution
Voxels to append around domain exterior.

Margin
Empty space around gas in voxels. Fast-moving gas requires larger margins to prevent edge clipping but increases computation.

Threshold
Minimum gas density before a voxel registers as empty and exclusion occurs.

## Guides

### Guides

Reference

Panel :

Physics ‣ Fluid ‣ Guides

Type :

Domain

Fluid guides enforce forces on the sim, analogous to external forces yet preserving physically-accurate flow. The Guides panel tunes global guiding. Enabling guides activates more precise (computationally costly) pressure solving even without baked guides or attached domains. Reserve guide-enabling for intentional use.

See also

Fluid guiding is Primal-Dual Optimization for Fluids.

Weight
Guiding lag degree. Larger "alpha" = greater lag.

Size
Vortex size from guiding. Larger "blur radius" or "beta" = bigger vortices.

Velocity Factor
All guiding velocities multiply by this. Every domain-grid cell scales by this.

Velocity Source
Guiding velocity origin.

Effector :

Domain effectors supply global guiding velocity grid. Once baked, domain resolution is locked.

Domain :

Another fluid domain supplies guiding velocity, possibly at different resolution and type (e.g., Gas domain guiding Liquid domain). Must be pre-baked.

Guide Parent
Selects the guiding domain when Domain is the velocity source.

Bake Guides, Free Guides
With Modular cache and Effector velocity source. Bake Guides writes effector vertex velocities for driving, pre-baking step. Status bar shows progress; Esc pauses. After, Free Guides deletes cache. Pause/resume available.

## Boid

### Boid 

Reference

Panel :

Physics ‣ Force Fields

Type :

Boid

Boid force fields do not alter physics simulations directly. Instead, they work in tandem with Boids Particles to establish predators and objectives for Boid Brain behavioral rules.

UI for a Boid force field.

## Charge

### Charge 

Reference

Panel :

Physics ‣ Force Fields

Type :

Charge

A Charge field operates similarly to a Force field but shifts its behavior (attraction or repulsion) according to particle charge properties (negative or positive), mirroring real charged particle interaction. This field exclusively affects particles carrying their own Charge field setting (without charge, particles remain unresponsive).

UI for a Charge force field. 

### Example

## Drag

### Drag 

Reference

Panel :

Physics ‣ Force Fields

Type :

Drag

A Drag field impedes particle movement through resistance, progressively slowing them down.

### Options 

UI for a Drag force field. 

Linear

Drag component proportional to velocity magnitude.

Quadratic

Drag component proportional to velocity squared.

## Fluid Flow

### Fluid Flow 

Reference

Panel :

Physics ‣ Force Fields

Type :

Fluid Flow

The Fluid Flow field channels a Fluid simulation air flow into a force effect. It converts smoke simulation air flow velocity into force that affects systems using fields. Set up by adding a Fluid Flow field and specifying a domain object. For instance, fire sparks can realistically drift alongside air turbulence around simulated flames.

### Options 

UI for a Fluid Flow force field. 

Domain Object

Points to a smoke simulation domain object.

Apply Density

Modulates force intensity according to smoke density values.

## Force

### Force 

Reference

Panel :

Physics ‣ Force Fields

Type :

Force

Force field visualization. 

The Force field ranks among the most straightforward field varieties. It delivers a uniform force radiating from (positive strength) or converging toward (negative strength) the object's center point.

### Example

## Harmonic

### Harmonic 

Reference

Panel :

Physics ‣ Force Fields

Type :

Harmonic

In a Harmonic field, the force origin serves as the equilibrium point of an oscillatory system (spring, pendulum). Setting Damping to 1 arrests movement the moment the object arrives at the center. Particularly suited to particle applications, this field type exhibits distinctive characteristics.

### Options 

UI for a Harmonic force field. 

Rest Length

Sets the equilibrium extension of the harmonic force.

Multiple Springs

Activates simultaneous multi-spring effects from all points. Typically, all field particles exert influence on all target particles. With Harmonic, each target particle associates with precisely one field particle. Particles migrate to field particle positions, creating organized geometric structures.

### Example

## Lennard-Jones

### Lennard-Jones 

Reference

Panel :

Physics ‣ Force Fields

Type :

Lennard-Jones

The Lennard-Jones field generates highly localized forces determined by the dimensions of the source and affected particles. When separation falls below combined sizes, strong repulsion activates; at greater distances, attraction dominates. The field maintains particles at an equilibrium spacing. Particles require close proximity for this field to register any effect.

Particles can simultaneously exhibit charge and Lennard-Jones potential—a configuration of interest to nuclear physics practitioners.

UI for a Lennard-Jones force field. 

### Example

## Magnetic

### Magnetic 

Reference

Panel :

Physics ‣ Force Fields

Type :

Magnetic

This field's behavior depends on particle velocity, mimicking the magnetic interaction on magnetized matter.

UI for a Magnetic force field. 

### Example

## Turbulence

### Turbulence 

Reference

Panel :

Physics ‣ Force Fields

Type :

Turbulence

A Turbulence field generates chaotic, randomized 3D noise patterns resembling water jets or submarine geysers.

### Options 

UI for a Turbulence force field. 

Size

Characterizes the noise magnitude scale.

Global

Anchors noise scale and intensity to the world instead of the attached object.

### Example 

Turbulence force field affecting a particle system.

## Vortex

### Vortex 

Reference

Panel :

Physics ‣ Force Fields

Type :

Vortex

Vortex force field visualization. 

The Vortex field imparts a spiraling force that rotates direction around the field object's local Z axis. Valuable for creating swirling drain effects, tornadoes, or particle hair distortions.

### Options 

UI for a Vortex force field. 

Inflow

The inward-drawing component of the vortex mechanism.

### Example

## Wind

### Wind 

Reference

Panel :

Physics ‣ Force Fields

Type :

Wind

Wind force field visualization. 

The Wind field exerts uniform force along the field object's local Z axis direction. Circle spacing in the visualization indicates force magnitude.

UI for a Wind force field. 

### Example

## Force Fields

### Force Fields 

### Field Weights 

Reference

Panel :

Particle System ‣ Field Weights

The Field Weight panel orchestrates the magnitude of external force field and effector influence on the particle system. Force fields furnish external propulsion that energizes dynamic configurations. The Force Field Page catalogs field type specifications.

Effector Group

Constrains active effectors to a designated group. Only grouped effectors exert system influence.

Gravity

Regulates Global Gravity's system effect magnitude.

All

Normalizes all effector weight magnitudes concurrently.

### Force Fields Settings 

Reference

Panel :

Particle System ‣ Force Fields Settings

The Force Field Settings panel permits individual particles to operate as force fields, affecting rival systems or themselves.

Self Effect

Allows particle force fields to influence sibling particles within the same system.

Effector Amount

Designates how many particles function as force fields. A zero value activates all particles as effectors.

Particle systems can support up to two force fields. None attach by default. Select an effector variety to enable it. The Common Settings section explains configurations.

## Keyed

### Keyed 

Reference

Panel :

Particle System ‣ Physics

Type :

Keyed

Keyed particles traverse paths determined by multiple particle systems. This enables constructing chains building extended strands or flowing animated sequences. Particles lack internal dynamics; interpolation between successive systems each frame governs movement.

Keyed setup demands a minimum of two particle system entries in the Keys register.

### Options 

Keyed Physics settings. 

Loops

Specifies how many times the complete Keys register cycles. Disabled upon Use Timing activation.

Use Timing

This option permits specifying individual timing for separate keys using Time and Duration controls. Without activation, particles traverse all keys over their lifespan. Shorter lifespans accelerate motion. The lifetime divides equally across keys, sometimes producing uneven inter-target speeds.

### Relations 

Reference

Panel :

Particle System ‣ Physics ‣ Relations

Key Targets

The Keys sequence (target particle system list view).

Object

A target object label for the chosen key. If blank, the current particle system gets used.

System

The target object's particle system position.

Time

The frame number marking particle arrival at the selected system site. The Keyed system Start frame offsets this calculation.

Duration

The timespan (in frames) particles remain at the system before advancing to the next.

## Rotation

### Rotation 

Reference

Panel :

Particle System ‣ Rotation

These parameters govern how particles orient at inception and throughout their span. Visualization occurs by switching Display As to Axis in the Viewport Display panel.

Orientation Axis

Aligns the X particle axis to:

None

The universal X direction.

Normal

The emitter's normal orientation.

Normal-Tangent

The emitter's normal direction, additionally orienting the particle's Y axis toward the emitter's active UV map positive V bearing. Permits emitter deformation while preserving particle orientation consistency.

Velocity / Hair

The particle's starting velocity vector/hair emergence orientation.

Global X, Y, Z

Universal coordinate axes.

Object X, Y, Z

The emitter's coordinate axes.

Randomize

The particle starting rotation magnitude (spanning all orientations).

Phase

Starting rotation about the particle X axis, spanning -1 (-180°) through 1 (180°).

Randomize Phase

Random rotation addition to Phase, spanning 0 (0°) to 2 (360°).

Dynamic

Whether particle rotation evolves over duration.

### Angular Velocity 

Reference

Panel :

Particle System ‣ Rotation ‣ Angular Velocity

Permits specifying whether and how particles rotate over their lifetime. Dynamic activation requirement exists for this feature.

Axis

The rotation center. Velocity, Horizontal, or Vertical selections additionally sustain orientation relative to movement direction, even at zero Amount.

None

Rotation deactivates.

Velocity

Rotation occurs about the particle's velocity vector.

Horizontal

Rotation happens around the axis orthogonal to movement and lying in the worldwide XY plane. Vertical-moving particles exhibit no rotation due to lack of distinct axis.

Vertical

Rotation occurs about the axis orthogonal to horizontal rotation and particle velocity. Vertical-moving particles exhibit no rotation.

Global X, Y, Z

Rotation about universal axes.

Random

Rotation about an arbitrary axis.

Hint

Deploy Curve Guide with particles oriented to curve direction via Velocity / Hair Orientation Axis, Dynamic activation, and Velocity Angular Velocity Axis. Particles will consistently point curve-forward. (Standard objects use Follow Curve via Follow Path Constraint or curve legacy Follow, though these methods lack particle compatibility.)

Amount

The rotational speed magnitude about the Axis.

## Texture Influence

### Texture Influence 

Reference

Panel :

Texture ‣ Influence

Texture influence settings. 

Configures how textures modulate particle system properties spatially.

### General 

Time
Modulates particle emission timing.

Lifetime
Modulates particle lifespan.

Density
Modulates particle concentration.

Size
Modulates particle dimensions.

### Physics 

Velocity
Modulates initial particle velocity.

Damp
Modulates particle velocity damping.

Gravity
Modulates gravity effect on particles.

Force Fields
Modulates force field effects on particles.

### Hair 

Length
Modulates child-hair length.

Clump
Modulates child-hair clumping.

Kink
Modulates child-hair kink.

Rough
Modulates child-hair surface roughness.

## Fixed Constraint

### Fixed Constraint 

Reference

Panel :

Physics ‣ Rigid Body Constraint

Type :

Fixed

This constraint binds two objects to move as one unit.
Physics simulation introduces minimal slop, preventing the rigidity achieved by unified meshes.

Fixed constraint options.

## Generic Constraint

### Generic Constraint 

Reference

Panel :

Physics ‣ Rigid Body Constraint

Type :

Generic

The generic constraint provides extensive parameters.

X, Y, and Z axis constraints limit object translation. Clamping min/max to zero replicates Point constraint behavior.

Clamping relative rotation to zero maintains alignment.
Combining absolute rotation and translation clamps mimics Fixed constraint behavior.

Nonzero parameter spreads allow oscillation throughout the simulation.

### Options 

Limits

Angular

X Angle, Y Angle, Z Angle
Enable/disable rotation limits around X, Y, or Z axis.

Lower
Minimum rotation for X, Y, or Z axis.

Upper
Maximum rotation for X, Y, or Z axis.

Linear

X Axis, Y Axis, Z Axis
Enable/disable translation limits on X, Y, or Z axis.

Lower
Minimum translation for X, Y, or Z axis.

Upper
Maximum translation for X, Y, or Z axis.

## Generic Spring Constraint

### Generic Spring Constraint 

Reference

Panel :

Physics ‣ Rigid Body Constraint

Type :

Generic Spring

The generic spring constraint applies spring parameters across X/Y/Z axes, extending Generic constraint capabilities.
Using springs alone causes bouncing between anchor-attached objects—usually excessive freedom.
Most scenarios benefit from enabling translation or rotation constraints alongside springs.

Setting spring damping to 1 prevents forces from realigning anchor points, causing odd behavior. Verify damping levels if springs behave unexpectedly.

### Options 

Generic Spring constraint options. 

Limits

X/Y/Z Axis
Enable/disable translation limits on X, Y, or Z axis.

Lower
Minimum translation for X, Y, or Z axis.

Upper
Maximum translation for X, Y, or Z axis.

X/Y/Z Angle
Enable/disable rotation limits around X, Y, or Z axis.

Lower
Minimum rotation for X, Y, or Z axis.

Upper
Maximum rotation for X, Y, or Z axis.

Springs

X/Y/Z Axis
Enable/disable spring translation on X, Y, or Z axis.

Stiffness
Spring stiffness controlling translation flexibility on X, Y, or Z axis. Higher values reduce compliance.

Damping
Spring damping for translation on X, Y, or Z axis, controlling oscillation magnitude.

X/Y/Z Angle
Enable/disable spring rotation around X, Y, or Z axis.

Stiffness
Spring stiffness controlling rotation flexibility around X, Y, or Z axis. Higher values reduce compliance.

Damping
Spring damping for rotation around X, Y, or Z axis, controlling oscillation magnitude.
