# Children, Emission, Hair Dynamics, Render ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Children; Emission; Hair Dynamics; Render; Particle Edit Mode; Particle System Panel; Tips; Simulation; Color Management; Subdivision; Light Probe Sphere.

## Children

### Children 

Reference

Panel :

Particle System ‣ Children

Child particles branch from individual parent particles. Establishing a relatively modest parent particle count allows physics computation on parents alone; children then mirror their progenitors. Parent rendering, child visualization, and volume adjustments all bypass physics recalculation.

When children activate, parent particles disappear from render view. Enabling parent rendering in the Render panel toggles Parent Particles display. Parents stay hidden by default because child geometry frequently diverges from parent form.

### Common Options 

Child Type

None
Children do not generate.

Simple
Children originate from parent locations.

Interpolated
Children emerge between Parent particles on mesh faces. They interpolate adjacent parental behavior. Particularly valuable for fur—even distribution becomes achievable. Select children can acquire virtual parent status, affecting neighboring particle behavior.

Display Amount

Particle count visible in the 3D Viewport.

Render Amount

Particle count for rendering output.

Length

Child path extension.

Threshold

The percentage of particles remaining unaffected by child path length adjustments.

Seed

Random number table offset for child particles, enabling variation in randomization outcomes.

### Clumping 

Reference

Panel :

Particle System ‣ Children ‣ Clumping

Use Clump Curve

Substitutes the Curve Widget for numerical parameters.

Clump

Clumping degree along child strand paths. Children may cluster at their endpoint (1.0) or originate unified at their base (-1.0).

Shape

Clump profile: inverse parabolic (0.99) or exponential (-0.99).

Twist

Use Twist Curve

#### Clump Noise 

Generates random clustering along the parental hair.

Clump Noise Size

Specifies the clustering magnitude.

### Roughness 

Reference

Panel :

Particle System ‣ Children ‣ Roughness

Use Roughness Curve

Provides Curve Widget as substitute for numeric input.

Uniform, Size

Varies strand paths according to child position, producing consistent variation for nearby children.

Endpoint, Shape

"Rough End" randomizes path completion (resembling inverse clumping). Shape ranges from <1 (parabolic) to 10.0 (hyperbolic).

Random, Size, Threshold

Follows random vector distribution, creating variance independent of spatial proximity. Threshold permits selective application to designated children only. Beneficial for generating isolated strays behaving differently.

### Kink 

Reference

Panel :

Particle System ‣ Children ‣ Kink

Child particles with Kink. 

From left to right: Curl, Radial, Wave, Braid, Spiral.

Kink manipulates child rotation around progenitor particles. Consult Fig. Child particles with Kink. above for different Kink category examples.

Kink Type

Nothing
Inactive.

Curl
Children spiral around the parent hair.

Radial
Children create wave geometry passing through parent hair.

Wave
Children form unidirectional waves.

Braid
Children weave around the parent hair.

Spiral
Creates spiral formations at hair endpoints.

Radius, Resolution

Establish overall scale dimensions.

Shape

Directs spiral expansion inward or outward.

Note

Alignment Limitations

Vertically oriented hair (along the designated spiral axis, typically Z) may not display spirals. This reflects a projection technique constraint. Tilting or randomizing hair orientation resolves this.

Amplitude

The maximum extent of the offset.

Clump

Magnitude of clump impact on kink amplitude.

Flatness

The degree of hair flatness.

Frequency

The oscillation repetition rate (1/strand length). Increased frequency produces more rotations.

Shape

Determines where rotation begins (rotation offset point).

### Simple 

Size

A multiplier for child particle scaling.

Random Size

Random variation magnitude for child particle dimensions.

Radius

The spreading distance of children around their parents in all spatial directions. Children may scatter higher or lower than their sources.

Roundness

The child distribution shape. A value of 1.0 gives spherical distribution, while 0.0 produces planar distribution.

### Interpolated 

Virtual Parents

The fraction of virtual parents relative to total children.

Long Hair

Optimizes child calculation for extended hair simulations.

### Parting 

Parting

Establishes hair divisions based on parent strand separation.

Min/Max

The minimum/maximum angles spanning from hair root to tip (tip distance/root distance for extended hair).

### Example 

From left to right: Round: 0.0, Round: 1.0, Clump: 1.0, Clump: -1.0, Shape: -0.99.

## Emission

### Emission 

Reference

Panel :

Particle System ‣ Emission

The Emitter system operates as its designation suggests: it produces particles across a time window. Particles discharge from the target object beginning at Start through End frames, possessing specified lifespan duration. Rendering defaults to Halos, though configuration allows object-based rendering (based on particle system render settings, see Visualization).

Particle Emission settings. 

The Emission panel buttons manage temporal particle generation patterns:

Number

The aggregate of parent particles deployed in the simulation.

Seed

Blender applies this as the initialization point for random number production throughout the simulation.

Frame Start

The initiation frame for particle release. Negative values initiate simulation before actual rendering commences.

End

The termination frame for particle release.

Lifetime

The duration (in frames) each particle persists.

Lifetime Randomness

Random variation in individual particle lifetimes. Shortest potential lifetime calculates as Lifetime × (1 - Random). Values exceeding 1.0 are prohibited. Illustration: with standard Lifetime of 50 and Random at 0.5, particles exist between 50 frames and \\(50 × (1.0 - 0.5) = 25\\) frames. At Random 0.75, lifespans range from 50 to \\(50 × (1.0 - 0.75) = 12.5\\) frames.

### Source 

Reference

Panel :

Particle System ‣ Emission ‣ Source

Emit From

Defines emission methodology and site, granting granular spatial distribution authority.

Tip

Vertex groups constrain emission; configuration happens in the Vertex Groups panel.

Vertices

Particles originate from mesh vertices.

Faces

Particles originate from mesh surface faces.

Volume

Particles originate from the interior of a closed mesh.

Tip

Mesh must be Manifold for volume emission. Edge Split Modifiers and similar fracture the surface, preventing volume emission from operating as intended.

Use Modifier Stack

Takes Modifiers positioned above the Particle Modifier in the modifier hierarchy into consideration during emission, otherwise using unmodified geometry.

Note

Rendered particles may diverge from viewport particles when modifiers create differing geometry between viewport and render output.

Distribution

These configurations govern how particle emissions disperse across release sites (Faces or Volume).

Jittered

Particles distribute across jittered placements on emitter geometry.

Particles/Face

Emissions per surface face (0 = automated calculation).

Jittering Amount

The degree of distribution randomness applied.

Random

Particles discharge from arbitrary locations within emitter geometry.

Grid

Particles arrange in a 3D lattice; those within geometry stay, others discard.

Invert Grid

Inverts geometry interpretation and spatial interpretation.

Hexagonal

Employs hexagonal lattice configuration instead of rectangular arrays.

Resolution

The lattice granularity.

Random

Applies random translation to grid positions.

Random Order

Emitter indices process in random succession rather than sequentially. Grid distribution excludes this option.

Even Distribution

Particle distribution equilibrates via surface area ratios, yielding smaller elements producing fewer particles while maintaining uniform density.

## Hair Dynamics

### Hair Dynamics 

Reference

Panel :

Particle System ‣ Hair Dynamics

Hair particles gain physics-based behavior through dynamic simulation. Enable hair physics by toggling the checkbox next to Hair Dynamics.

Quality Steps
Simulation quality expressed as steps per frame; higher values improve fidelity at the cost of computation time.

Pin Goal Strength
Spring stiffness governing how strongly vertices return to their target positions.

Warning

When applying motion blur to animations, render one additional frame beyond the final output frame to ensure proper blur calculation.

### Collisions 

Quality
General parameter controlling simulation fineness; greater values produce more precise results with reduced mesh penetration, though computation increases.

Distance
The threshold distance at which other objects trigger hair repulsion away from contact. Smaller distances risk numerical errors but accelerate computation; larger values may produce unrealistic results and slow the simulation.
Optimal results come from balancing speed against fidelity.

Impulse Clamping
Restricts post-collision movement to prevent explosions in geometrically complex collision scenarios.

Collision Collection
Restricts collisions to objects in the specified collection; these objects must have Collision physics enabled.

### Structure 

Reference

Panel :

Particle System ‣ Hair Dynamics ‣ Structure

Vertex Mass
Numerical value controlling hair weight.

Stiffness
Parameter governing strand resistance to bending.

Random
Random variation in hair stiffness.

Damping
Damping coefficient for bending oscillations.

### Volume 

Reference

Panel :

Particle System ‣ Hair Dynamics ‣ Volume

Real-world hair phenomena can be modeled more efficiently through volumetric approaches rather than pure geometric strand representation. This involves constructing a regular three-dimensional grid (similar to fluid simulation grids) and interpolating hair properties across cell boundaries.

Air Drag
Parameter controlling medium density around hair, determining drag magnitude and flow speed.

Internal Friction
Friction coefficient between individual hair strands.

Voxel Grid Cell Size
Dimension of each cell in the volumetric simulation grid.

Density Target
Upper limit on hair volumetric density.

Density Strength
Magnitude of influence the Density Target exerts on the simulation.

## Render

### Render 

Reference

Panel :

Particle System ‣ Render

Hair renders as Path, Object, or Group. See Particle Visualization for details and Hair Shape settings.

See also

Blender Hair Basics, a comprehensive reference covering all hair particle configuration options.

## Particle Edit Mode

### Particle Edit Mode 

In Particle Edit Mode you alter keyframe points and paths of Hair, Particle, Cloth, and Soft Body simulations. (You can also sculpt and style hair prior to baking.)

Particle Edit Mode shares similarities with vertex editing in the 3D Viewport.

Important

Particle Edit Mode for hair is deprecated; use the new Empty Hair object and associated Sculpt Mode instead.

Important

Cached cloth simulation editing currently does not function; see: blender/blender#77114.

### Usage 

Tip

Only Frames Baked to Memory are Editable!

Check that you're not baking to a Disk Cache if particle editing is unavailable.

### Setup for Hair Particles 

- Create a Hair particle system.

- Apply an initial velocity in the Normal direction.

- Create a simulation.

- Enable the Hair Dynamics checkbox.

Editing hair strands in Particle Edit Mode. 

### Setup for Particle, Cloth, and Soft Body Simulations 

- Use Emitter particles or a cloth/soft body simulation.

- Initialize the simulation: place objects and emitters, define time range (narrow range for experimentation), configure the simulation, preview through playback.

### Bake the Simulation 

Once satisfied with the general simulation, bake from Object Mode. Baking must occur before editing becomes available.

### Edit the Simulation 

Switch to Particle Edit from the Mode menu in the 3D Viewport header to modify particle paths and keyframes. Press T in the 3D Viewport to reveal the Particle Edit toolbox. Navigate to the target frame and apply editing tools.

### Selecting 

Tip

Switch to Point select mode in the 3D Viewport header to view and select keypoints.

- Select single: LMB .

- Add to/remove from selection: Shift - LMB .

- All: A .

- None: Alt - A .

- Invert: Ctrl - I .

- Box select: B .

- Circle Select: C .

- Lasso Select: Ctrl - Alt - LMB .

- Select Linked: Position the cursor over a path and press L to include all its points in selection.

- Unselect Linked: Position the cursor over a path and press Shift - L to exclude all its points from selection.

- Root/Tips: Select ‣ Roots / Tips .

### Select Random 

Selects particles probabilistically.

Percent
Probability of selection per particle.

Random Seed
Seed value for random selection.

Action
Designates selection or deselection mode.

Type
Targets hair or keypoints. Note: these terms refer to path/points rather than particle type.

### Select Modes 

Selection Mode Options. 

Path :

No keypoints display; all particles selected or deselected as groups.

Point :

All keypoints visible and editable.

Tip :

Only the tip (final keypoint) displays and edits; brushes apply to tips only.

### Tools 

Reference

Mode :

Particle Edit Mode

Tool :

Toolbar

### Comb 

Repositions keypoints via proportional editing mechanics.

Deflect Emitter
Hair particles only – prevents keypoint motion through emitter mesh.

Distance
Distance maintained from the Emitter.

### Smooth 

Visually aligns adjacent segments.

### Add 

Creates new particles.

Count
New particles per brush step.

Interpolate
Derives new hair shapes from existing ones.

Steps
Brush step count.

Keys
Keypoint count for new particles.

### Length 

Adjusts segment scaling, elongating with Grow or shortening with Shrink.

Grow/Shrink
Selects effect direction.

### Puff 

Rotates hair around the root keypoint: adds vertical lift with Add or flattens with Sub.

Puff Volume
Applies puff to unselected endpoints, maintaining volume during root adjustment.

### Cut 

Scales segments until the final keypoint reaches brush position.

### Weight 

Particularly valuable for soft-body animation, where weight defines soft-body Goal.
A weight of 1 prevents motion; a weight of 0 allows full soft-body influence.
Soft body goal strength scaling multiplies this value.

### Common Options 

Brush settings appear below type selection:

Radius F
Set the brush radius.

Strength Shift - F
Establish brush effect magnitude (inapplicable to Add).

### Options 

Reference

Mode :

Particle Edit Mode

Panel :

Tool Settings ‣ Options

Auto-Velocity Emitter
Recompute particle velocities from edited paths; otherwise preserves original velocity regardless of actual displacement.

Mirror X
Enable symmetric editing along the local X axis.

Preserve

Strand Length
Keep keypoint spacing constant during combing or smoothing by adjusting other keypoints.

Root Positions
Lock the first keypoint to prevent hair transplanting.

### Cut Particles to Shape 

Shape Object
A mesh object whose boundary governs the Shape Cut tool.

Cut
A grooming operation that clips hair according to the Shape Object boundary. Avoids tedious manual cutting of protruding sections, especially on highly furred characters.
Works effectively for large areas compared to individual-plane cutting.

| Before.  | After.  |

### Viewport Display 

Path Steps
Number of steps used to render the path; increases smoothness.

Children Hair
Toggles display of child particles, enabling fine-tuning of effects while risking performance impact on high-child-count systems.

Particles Emitter
Overlays particles atop paths.

Fade Time
Fades paths and keys distant from the current frame.

Frames
Fade frame count.

### Editing 

### Moving Keypoints or Particles 

- Press G to move selected keypoints, or employ standard vertex-editing methods.

- Disable Keep Root in the Toolbar to reposition particle roots.

- Apply standard vertex operations: scale, rotate, delete (full particles or individual keypoints).

- Keypoint duplication and extrusion are unavailable, but particle subdivision adds keypoints (Particle ‣ Subdivide).

- Alternatively, reparametrize a particle with Particle ‣ Rekey.

Path Steps settings govern display smoothness. Low settings produce blocky interpolation; high settings yield smooth curves.

### Mirror 

Reference

Mode :

Particle Edit Mode

Menu :

Particle ‣ Mirror

To create X-axis symmetrical haircuts:

- Select all particles: A.

- Mirror with Particle ‣ Mirror.

- Enable X Mirror in Sidebar Region ‣ Tool ‣ Options.

Mirroring can position two particles nearly identically. To save memory and render time, apply Merge by Distance from the Particle menu.

### Unify Length 

Reference

Mode :

Particle Edit Mode

Menu :

Particle ‣ Unify Length

Equalizes selected hair length by averaging.

### Show/Hide 

Reference

Mode :

Particle Edit Mode

Menu :

Particle ‣ Show/Hide

Hide and reveal particles similarly to vertex hiding in the 3D Viewport. Select target keypoints and press H to hide the particle; keypoints hide while the particle persists.

Hidden particles (those with hidden keypoints) do not respond to brush operations. However:

If Mirror Editing is active, particles with hidden keypoints may move when their mirrored counterparts move.

Press Alt - H to reveal all hidden particles.

## Particle System Panel

### Particle System Panel 

Reference

Panel :

Particle System ‣ Particle System

Particle System panel. 

These are the fundamental settings.

Active Particle System
The object's Particle Modifier(s) in list view.

Specials

Copy Active to Selected Objects
Duplicates the active particle system onto all selected objects.

Copy All to Selected Objects
Transfers all particle systems from the active object to all selected objects.

Duplicate Particle Systems
Replicates the particle system within the object.
Checking Duplicate Settings (in Adjust Last Operation) replicates settings too, giving the new system independent parameters.

Remove All Particle Systems
Eliminates all particle systems in the object.

Particle Settings
Data-Block selector for settings.

Type
Fundamental system-type selector.

Emitter
Particles originate from the object.

Hair
Strand-based hair rendering.

Regrow
Regenerates hair each frame, beneficial when animating properties.

Advanced
Unlocks advanced settings matching Emitter mode behavior.

Note

This manual assumes this option is enabled.

Segments
Specifies strand segment count.
Higher values enhance animation quality.

### Workflow 

Standard particle system workflow:

- Create the emitting mesh.

- Initialize one or more Particle Systems from the mesh. Multiple systems typically overlap or merge for the desired combined effect.

- Configure each system's parameters.

- Animate the emitter and other scene meshes.

- Define and refine particle flow and direction.

- For Hair systems: sculpt the emitter's appearance (cut hair length, comb, etc.).

- Perform final rendering and physics simulation, adjusting as needed.

### Creating a Particle System 

Adding a particle system. 

Attach a particle system to an object via the Particles tab in the Properties editor—click the button. An object may host numerous Particle Systems.

Each system maintains separate settings. Systems can share settings, avoiding manual duplication and enabling the same effect across multiple objects.

#### Types of Particle Systems 

Particle System Types. 

After initialization, the Properties panel fills with numerous controls.
Don't panic—two distinct particle system types exist, selectable via Type: Emitter and Hair.

Particle System tab settings vary partially by system type.

## Tips

### Tips 

Monitor the Animated checkbox in Rigid Body properties closely.
A frequent mistake: applying keyframe animation to a Passive object without checking Animated. The object moves, but the physics engine treats the Passive as static, causing unexpected results.

### Animation 

A common technique animates location or rotation of an Active body together with toggling the Animated checkbox.
When Animated disables, the physics engine assumes control using the last known position, rotation, and velocities.

Animating other property strengths—Motor Target Velocity, Hinge limits, etc.—enables varied effects.

Enabling constraints mid-simulation often produces dramatic results as the physics engine reconciles misaligned objects, frequently building sufficient kinetic energy to propel them offscreen.

Bake rigid body dynamics to keyframes via Bake To Keyframes in Object ‣ Rigid Body.

### Simulation Stability 

Increasing steps per second offers the simplest stability improvement.
Excessive steps create problems and reduce stability (over 1000 steps suggests reconsidering the approach).

Higher solver iterations strengthen constraints and improve stacking stability.

Small objects remain unstable; objects should ideally exceed 20 cm diameter.
For smaller objects, setting collision margin to 0 can help (though generally inadvisable).

Fast-moving small objects may interpenetrate. Beyond steps-per-second adjustments, avoid mesh shapes here.
Mesh shapes consist of individual triangles lacking thickness, encouraging interpenetration.
Increase collision margins to add effective thickness.

### Combining Rigid Bodies with Other Simulations 

Since rigid body simulation integrates with the animation system, it influences other simulations just as animation does.

For this to work, the rigid body object requires a Collision Modifier—add it via Physics properties.

### Scaling Rigid Bodies 

Rigid bodies scale during or outside simulation.
Generally this works well, occasionally causing issues.

For non-dynamic scaling, apply the scale first using Apply Scale (Ctrl - A); avoid scaling during simulation if possible.

## Simulation

### Simulation 

Speed
Controls soft-body system internal timing.
Correlates frame rate with simulation tempo.
A free-falling body should travel approximately five meters in one second and reach ten meters-per-second speed.

Adjust scene and simulation scale through this correlation.
For 25 fps rendering, set Speed to 1.3.

## Color Management

### Color Management 

Sound color management is what keeps renders and assets physically accurate while still looking sharp across many displays. It pulls double duty: holding every pipeline stage to a correct reading of color, and leaving room for artistic choices about the look.

## Subdivision

### Subdivision

Reference

Panel :

Render ‣ Subdivision

Control Adaptive Subdivision with these settings.

Dicing Rate Render, Viewport
Micropolygon scaling for final/viewport output.

Offscreen Scale
Dicing scale multiplier for off-camera geometry. Outside-view objects scale upward as distance grows. Lower reduces off-screen quality, higher saves memory.

Max Subdivisions
Subdivision ceiling regardless of dicing requests, preventing excessive Tessellation.

Dicing Camera
Active reference camera for geometry subdivision, preventing crawl artifacts in animated scenes with moving cameras.

## Light Probe Sphere

### Light Probe Sphere

A spherical light probe records incoming light from many angles at one location.

Application targets smooth and semi-rough reflections. Sphere probes transition smoothly toward volumetric lighting for purely diffuse cases.

With raytracing active, they act as missed-ray fallback.

Note

Light probe volumes overshadow sphere probes, minimizing light leakage in shadowed areas and reducing needed setup.

Adjustment occurs in Scene data panel.

World carries an inbuilt sphere probe with adjustable resolution in World data panel.

### Properties

Reference

Panel :

Object Data ‣ Probe

Type
Influence volume shape: Sphere or Box.

Radius / Size
Probes alter nearby surface lighting. Size and scaling define influence extent.

Falloff
Influence fade percentage within the distance.

### Capture

Note

Viewport capture happens upon detected probe or position update. Frame rendering captures at start.

Clipping Start, End
Near and far clip for scene capture.

### Custom Parallax

Reference

Panel :

Object Data ‣ Custom Parallax

Standard: influence volume equals parallax volume. Parallax volume projects captured light, matching surroundings. Custom Parallax enables independent parallax adjustment.

### Viewport Display

Data
Show captured light as a reflective sphere at given size.

Clipping
Show capture clip distance.

Influence
Show influence bounds. Inner sphere marks falloff start.

Parallax
Show Custom Parallax shape.
