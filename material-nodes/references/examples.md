# Examples, Physical Properties, Collision, Canvas ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Examples; Physical Properties; Collision; Canvas; Materials; Noise; Diffusion.

## Examples

Examples and workflows.

To begin cloth simulation, first add a plane and delete the default cube. Subdivide the plane several times (approximately eight subdivisions yield good fabric flexibility). Tab into Edit Mode and subdivide.

Activate cloth via the Physics tab: locate Cloth panel and click Cloth. Numerous settings appear; most are initially ignored.

Basic setup is complete. Playback shows modest results—the following sections cover pinning and collision for better dynamics.

Using Simulation to Shape/Sculpt a Mesh

Apply the Cloth Modifier at any frame to freeze the mesh at that point. Re-enable cloth with adjusted start/end frames to continue simulation.

Example: define a flag as a grid and pin its edge to a pole. Simulate 50+ frames until the flag settles. Apply the Cloth Modifier. For flapping animation, re-enable cloth during in-camera frames.

Smoothing of Cloth

Post-simulation, cloth often appears blocky. Apply Smooth and/or Subdivision Surface Modifier via the Modifiers tab. In the Toolbar, find Edit panel and press Smooth.

Cloth on Armature

Pin clothing to bones (e.g., loose tunic to waist).

Workflow:
- Bind-pose armature.
- Model clothing (enclosing, non-penetrating).
- Parent to armature.
- Create pinned-vertex group per cloth object.
- Add vertices + weight (≥1). E.g., belt area, weight 1.
- Physics tab: mark cloth. Stack Cloth below Armature Modifier.
- Cloth Shape: select vertex group.
- Collision on character mesh.
- Unpinned → Cloth; pinned → Armature.

Note: animate from bind pose, moving gradually (multiple frames). Instant/teleport jumps break physics.

Regression blend-file.

Cloth with Animated Vertex Groups

Animated pinned-vertex cloth:
Regression blend-file.

Unsupported: Starting with goal = 0 and increasing (with vertex unpinned) fails; no on-the-fly goal springs.

Cloth with Dynamic Paint

Cloth + Dynamic Paint + animated vertex groups:
Regression blend-file.

Unsupported: Same as above—goal = 0 to 0.5 with unpinned vertex fails.

Using Cloth for Soft Bodies

Soft-body simulation via cloth.

Cloth simulates soft bodies (not its primary function, but functional). Example uses standard Rubber material, default settings, Alt - A playback.

Blend-file: Using Cloth for soft bodies.

Cloth with Wind

Flag with wind force applied.

Cloth wind/self-collision regression blend-file (includes image-above setup):
Cloth flag with wind and self-collisions.

### Examples 

Simple examples demonstrate soft-body physics potential.

### A Bouncing Cube 

### The Process 

Initialize start and end frames as 1 and 150.

Add a plane and scale five times. Go to Physics, add Collision (defaults suffice).

Add a cube (or use default), enter Edit Mode, subdivide three times.
Add a Bevel Modifier to smooth edges; press R twice and move cursor slightly for additional rounding.

The setup now resembles:

The scene, ready for soft body physics. 

Soft body physics activation:
Go to Properties ‣ Physics, select Soft Body.
Uncheck Soft Body Goal; check Soft Body Self Collision.
Under Soft Body Edges, increase Bending to 10.

Playback produces slow-motion bouncing.
For faster playback, bake the physics.

Under Soft Body Cache, set start and end to 1 and 150.
Test with cache step 5 or 10; for final animation, reduce to 1 for complete caching.

The finished setup:

The physics cache settings. 

The physics edges and self collision settings. 

Now bake the simulation, apply materials and textures, and render.

### The Result 

The rendered bouncing cube

## Physical Properties

### Physical Properties

Reference

Panel :

Physics ‣ Cloth ‣ Physical Properties

Vertex Mass
Weight of the cloth material.

Air Viscosity
Air thickness slows falling motion.

Bending Model

Linear :

Traditional cloth with linear bending springs.

Angular :

Contemporary cloth using angular bending springs.

### Stiffness

Tension
Resistance to lengthening.

Compression
Resistance to condensing.

Structural
Overall cloth hardness (linear bending model only).

Shear
Resistance to lateral deformation.

Bending
Wrinkle intensity. Higher = larger folds.

### Damping

Tension
Dampening during lengthening.

Compression
Dampening during condensing.

Structural
Dampening during lengthening (linear bending model only).

Shear
Dampening during lateral deformation.

Bending
Dampening during bending.

### Internal Springs

Springs link surface mesh vertices, affecting only 2D surfaces. For 3D behavior resembling Soft Bodies, enable Internal Springs in the panel header.

Max Spring Creation Length
Upper limit on internal spring length during generation. Connections beyond this separation won't form. Zero = no limit.

Max Creation Diversion
Maximum permitted angle between internal connection and vertex normal direction.

Check Surface Normals
Requires connected points to possess opposite normal orientations.

Tension
Lengthening resistance.

Compression
Condensing resistance.

Vertex Group
A Vertex Group manages Tension and Compression for selected mesh portions and spring intensity.

Max Tension
Highest tension stiffness.

Max Compression
Highest compression stiffness.

### Pressure

Enclosed soft objects (balloons, filled spheres) can be modeled via cloth pressure, treating contents as gas. For incompressible behavior, maximize Pressure Scale without destabilizing. Activate via the Pressure panel header.

Note

Non-manifold meshes work, though pressure leaks through holes, causing drift. Exclude non-manifold portions via Vertex Group.

Pressure
Uniform force always applied. Units are Pressure Scale; negative values simulate inward pressure or collapse.

Custom Volume
Use Target Volume as the starting volume instead of computing from the mesh.

Target Volume
Volume where internal/external pressure equilibrate. Zero disables volume-based pressure adjustment.

Pressure Scale
Background pressure (kPa) balanced at target volume. Higher = stronger resistance to size change.

Fluid Density
Density of interior fluid (kg/liter; use 1 for water), generating hydrostatic gradient (weight). Negative models surrounding buoyancy. No actual fluid motion occurs, so realistic flow dynamics don't manifest, yet the setting helps plausible resting shapes and can add weight to flexible objects, even non-fluids.

Volume isn't preserved without Pressure Scale. Try fluid density × object size × 50 as an initial Pressure Scale to keep volume under 10% change if acceleration stays near standard gravity.

Vertex Group
A Vertex Group specifies mesh portions receiving pressure. Zero weight = no pressure; full weight = max pressure.

Note, faces containing a zero-weight vertex skip Target Volume calculation.

## Collision

### Collision

Reference

Mode :

Object Mode

Panel :

Physics ‣ Collision

Particles, Soft Bodies, and Cloth can hit mesh objects. Boids avoid Collision objects.

- Particle effect scope can be restricted to a group (Field Weights panel).

- Deflection for soft body is tricky; penetration often happens.

- Hair particles disregard deflectors (though animating as soft bodies respects deflection).

Cache recalculation is manual (Delete Bake) when deflection settings change—it doesn't happen automatically.

A collider may be toggled on/off animatably using the control to its right.

### Options

Collision panel. 

### Collision

Field Absorption
A deflector can block effectors. Specify absorption per collision object to reduce force transmission. 100% blocks completely. Stacked objects (10%, 43%, 3%) absorb around 50% (100 × (1 - 0.1) × (1 - 0.43) × (1 - 0.03)).

### Particle

Permeability
Portion of particles crossing the mesh.

Stickiness
Particle adherence strength.

Kill Particles
Destroys particles upon contact.

Damping
Collision-induced damping (velocity-independent).

Randomize
Random damping variation.

Friction
Surface friction during movement.

Randomize
Random friction variation.

### Soft Body and Cloth

This panel notifies all sims that the object deflects/collides with dynamics on shared layers (particles, soft bodies, cloth).

Note

The object's geometry deforms cloth, so the sim requires the "true" mesh shape at that frame—the base shape modified by shape keys or armatures. Place the Collision Modifier after these.
The image shows the Character mesh Modifiers panel (not the cloth object).

Collision stack. 

Damping
Collision damping regulating surface bounce.

- 0.0 - None, soft bodies bounce maximally.

- 1.0 - Full, soft bodies don't bounce.

Thickness
Padding added internally and externally to faces, preventing intersections. The soft body settles away from faces by this distance. Normal (blue arrow) defines inside/outside.

Outer
Outer collision zone extent.

Inner
Inner zone padding distance.

A soft body vertex colliding with a plane. 

Friction
How slippery cloth is during collision. Silk glides more than cotton.

Single Sided
When active, the collider represents a solid boundary, ejecting intersecting cloth along its normal.

Override Normals
When active, cloth collision forces follow collider normals.

Note

Soft body collision is finicky. Fast-moving objects cause penetration. Check Soft Bodies.

### Examples

Deflected particles. 

A Meta object uses Instancing Vertices onto downward-emitting particles deflected by a mesh cube.

### Hints

- Orient mesh normals toward particles for correct deflection. Negative scales have similar effects; recalculate normals after applying scales.

- Hair reacts directly to force fields, so short-range fields may eliminate collision needs.

- Hair avoids its emitting mesh in Particle Edit Mode for basic collision modeling.

## Canvas

### Canvas

Reference

Panel :

Physics ‣ Dynamic Paint

Type :

Canvas

A Canvas accepts paint from Dynamic Paint brushes.

### Settings

Canvas main panel. 

Paint Surface
Dynamic Paint surface list. Surfaces behave as independent paint layers with individual parameters and separate baking.

Is Active
Toggles surface activity. Inactive surfaces skip computation.

Below, configure surface type and quality/timing adjustments.

Format
Each surface has format and type. Format decides how data stores and outputs.

Vertex :

Dynamic Paint operates on mesh vertex data. Results cache and display in viewports. Requires highly subdivided meshes.

Image Sequences :

Dynamic Paint generates UV-wrapped image files at specified resolution as output.

Resolution
Output image dimensions. 256 produces 256×256 output. Doubling resolution quadruples baking time.

Anti-Aliasing
5× multisampling edge smoothing.

Frame Start, End
Surface processing boundaries.

Sub-Steps
Extra frame samples, needed for very fast brushes.

### Surface

Reference

Type :

Canvas

Panel :

Physics ‣ Dynamic Paint ‣ Surface

Canvas advanced panel. 

Surface panel adjusts surface type and settings.

### Surface Type

Each surface has a "type" defining its role.

#### Paint

Paint Surface. 

Paint is the core surface outputting color and wetness. Vertex surface results show as Color Attributes.

Wetmap is grayscale: white = max wetness, black = fully dry. Typically masks rendering. "Paint effects" target wet paint only.

Dry
Disabling drying spreads paint indefinitely.

Color Dry
Defines wetness where paint colors shift toward surface "background". Lower = prevent transparent spreading; higher = better general results.

#### Displace

Displace Surface. 

This outputs intersection depth from brush objects.

Incremental
Adds new displace cumulatively on existing displace.

Max Displace
Intersection depth ceiling; excess clamps.

Displace Factor
Intersection depth multiplier. Adjust strength or use negative for bump painting.

Tip

Rough displace output? Add Smooth Modifier after Dynamic Paint.

#### Waves

Waves Surface. 

This simulates wave motion from brush intersection depth.

Open Borders
Waves cross mesh "edges" instead of reflecting.

Timescale
Adjusts sim speed without outcome shift. Lower = slower; higher = faster.

Speed
Wave travel pace on surface, also corresponding to simulation size. Half speed = surface doubles.

Damping
Wave-strength reduction. Higher = faster disappearance.

Spring
Force pulling water to "zero level".

Smoothness
Max wave-slope steepness between sim points. Eliminates "noise" from sharp-edged objects (cubes). Default catches sharpest spikes; higher values smooth further at detail cost.

Tip

Unstable wave motion near brushes? Lower wave speed, brush "wave factor", or mesh/surface resolution.

#### Weight

Weight Surface. 

Vertex-format-only surface outputting vertex weight groups for other Blender modifiers/tools.

Tip

Prefer "proximity" brushes for weight surfaces for smooth falloff.

### Common Options

Special settings exist per type. Most have Dissolve and Brush:

Dissolve
Smoothly returns the surface to original state over a Time period.

Brush Collection
Defines a specific collection for brush sources.

Influence Scale, Radius Scale
Tweaks brush parameters per surface.

### Cache

Reference

Type :

Canvas

Panel :

Physics ‣ Dynamic Paint ‣ Cache

Canvas cache panel. 

Currently visible for Vertex format only. Adjust and bake point cache here.

### Effects

Reference

Type :

Canvas

Panel :

Physics ‣ Dynamic Paint ‣ Effects

Effects panel. 

For "Paint" surfaces, generates animated canvas movement.

Effects

Spread
Paint expands gradually to adjacent points, filling connected zones.

Drip
Paint flows by Blender force fields, gravity, and velocity with user adjustments.

Shrink
Painted area gradually contracts and vanishes.

Spread and Drip affect "wet paint" only; drying slows motion until stopping.

### Initial Color

Reference

Type :

Canvas

Panel :

Physics ‣ Dynamic Paint ‣ Initial Color

Sets the canvas starting color. (Todo 2.62)

- None

- Color

- UV Texture

- Vertex Color

### Output

Reference

Type :

Canvas

Panel :

Physics ‣ Dynamic Paint ‣ Output

Canvas Output panel. 

Output panel controls how the surface sends results.

### Vertex

For Vertex format, select a mesh data layer (color/weight by surface type) for output. "+"/"-" icons add/remove named layers. Missing layers appear red.

### Image Sequence

For Image Sequence surfaces, specify UV maps, output directory, filename, and format.

## Materials

### Materials

### Smoke Material

Realism in smoke rendering employs the Principled Volume shader.

Smoke Material Example Animation

Materials — Configuration

See also
EEVEE uses the same material node system as Cycles but with feature gaps.
See Shader nodes limitations.

### Thickness

Reference
Panel: Properties ‣ Material ‣ Thickness

Thickness approximates inner structure without heavy calculation. Used for Subsurface Scattering, Translucent BSDF, Refraction BSDF, and related nodes.

When the output node receives no thickness input, object dimensions determine a default value. Connected values represent object space thickness (scaled by object transform). Zero disables thickness approximation and treats geometry as single-sided.

This output is exclusive to EEVEE.

Note
- Thickness excludes the object's interior from computation.
- Refraction does not refract objects within the thickness distance.
- Shadow casting objects do not cast shadows within the thickness distance.

Tip
- For large or composite meshes (e.g., plants), set thickness to individual component thickness (e.g., leaf or grass blade width).
- Bake thickness to textures or attributes for improved accuracy.

See also
Thickness Mode controls thickness interpretation.

### Material Settings

Reference
Panel: Properties ‣ Material ‣ Settings

Pass Index
Index for the Material Index render pass. Applies a material mask readable by the ID Mask Node in the Compositor.

Note
Volume Objects do not support pass index.

### Surface

Backface Culling
Hide back-facing surfaces. Enable whenever possible for performance benefit.

Camera
Apply back face culling in camera view.

Shadow
Apply back face culling during shadow casting.

Light Probe Volume
Apply back face culling during Light Probe Volume baking. Helps reject capture points inside objects to prevent light leaking.

Displacement
Governs how shader node tree displacement output affects rendering.

Bump Only:
Simulate displacement via bump mapping. Shading normals change only; vertex positions remain unaffected.

Displacement Only:
Unsupported; falls back to Displacement and Bump.

Displacement and Bump:
Combines true vertex displacement with bump mapping for fine detail. Vertex position changes.

Note
This is not precomputed and scales with render sample count. Evaluation is faster than geometry nodes or modifiers.

Note
Displacing flat shaded geometry splits adjacent faces. Supply vertex normals as a custom attribute to work around this.

Max Distance
Maximum distance a vertex can displace. Displacements beyond this threshold create visibility artifacts. Edge-of-screen geometry may disappear due to camera culling. Shadow updates may lag.

Transparent shadows
Apply transparency shadows if the material contains Transparent BSDF. Disabled rendering is faster but produces inaccurate shadows.

Render Method
Controls blending behavior and feature compatibility.

Dithered:
Enables grayscale hashed transparency, compatible with render passes and raytracing. Known as deferred rendering.

In Dithered mode, materials render in layers. Each layer can only transmit light from prior layers. If no intersection with lower layers exists, transmissive BSDFs fall back to light probes.

Raytraced Transmission
Use raytracing to compute transmitted color rather than relying solely on light probes. Prevents the surface from contributing to lighting of surfaces without this setting.

Blended:
Permits colored transparency but incompatible with render passes and raytracing. Known as forward rendering.

Sorting Problem

Blended rendering order affects final output since color blending is order-dependent. EEVEE lacks per-pixel or per-triangle sorting and uses only per-object sorting based on origin. Opaque surfaces maintain correct sorting regardless of render method.

Tip
Adjust face order in edit mode via sort element or geometry nodes.

Note
Per-object sorting costs performance; thousands of transparent objects degrade framerate significantly.

Transparency Overlap
Render all transparent fragments when enabled. When disabled, only the frontmost surface renders. Disabling fixes sorting-induced artifacts.
Blended render method only.

Thickness
Choose the model for approximating object geometry.

Sphere:
Approximate as a sphere with diameter equal to the node tree thickness value. Better for rounded objects (e.g., monkey head) and perfect for spheres.

Slab:
Approximate as an infinite slab with defined thickness. Suited to flat or thin objects (e.g., glass panels, grass blades).

From Shadow
Refine thickness using shadow maps from casting lights, taking the minimum value between shadow maps and material node tree thickness. Beneficial for objects where pre-computation is difficult (complex geometry), impossible (procedural displacement), or impractical. Incurs performance cost scaling with render samples.

### Volume

Intersection
Governs which inner mesh portion produces volumetric effects.

Intersection (continued)

Fast:
Each face acts as a medium boundary. Produces correct results for manifold geometry with no internal structure.

Accurate:
Faces act as boundaries only when consecutive faces point in opposite directions. Produces correct results as long as max ray depth is not exceeded. Requires significant additional memory compared to fast mode.

## Noise

### Noise

Reference

Type :

Domain

Panel :

Physics ‣ Fluid ‣ Noise

Injecting noise into gas simulation superimposes fine detail onto the base without changing fluid motion dynamics. This adds complexity to gases (fire, smoke) minus overall motion change.

See also

Fluid noise is Wavelet Turbulence for Fluid Simulation.

Noise enablement signals cache which data to load. With Noise on but no data, the domain appears empty. Toggling doesn't reset cache; switch between base and noise.

Upres Factor
Noise resolution enhancement multiplier, tied to Resolution Divisions.

Strength
Noise magnitude. Higher = turbulent vortices.

Scale
Noise size. Higher = larger vortices.

Time
Noise animation instant, affecting field evaluation. Useful seed for wavelet noise differences between otherwise identical domains.

| Animation Time: 0.1  | Animation Time: 1.0  |
| Animation Time: 2.5  | Animation Time: 10.0  |

Note

Resolution Divisions and Upres Factor differ. Various combinations yield smoke styles.

| Resolution Divisions: 200, without noise  | Resolution Divisions: 100, Noise scale: 2.  |

Low-division high-Upres sims appear smaller in scale, creating pyroclastic plumes:

Bake Noise, Free Noise
With Modular cache type.

Progress shows in status bar; Esc pauses. After baking, Free Noise deletes cache. Pause/resume supported.

### Noise

Noise Texture panel.

Although this looks great, it is not Perlin Noise! This is a true, randomly generated Noise. This gives a different result every time, for every frame, for every pixel.

### Options

There are no options for this noise.

Often used for
White noise in an animation. This is not well suited if you do not want an animation. For material displacement or bump, use clouds instead.

Result(s)
Intensity.

## Diffusion

### Diffusion

Reference

Type :

Domain

Panel :

Physics ‣ Fluid ‣ Diffusion

Liquid diffusion parameters define physical qualities and environment interaction. Viscosity and Surface Tension are primary factors. Adjusting generates virtual liquids mimicking water, oil, honey, etc. Presets for various substances exist and can be altered in the menu. Diffusion toggles in the panel header.

Viscosity

Viscosity denotes fluid "thickness"—resistance to motion relative to surface area and speed.

Real-world values (dynamic viscosity) are Pascal-seconds (Pa·s) or Poise units (P = 0.1 Pa·s), often centiPoise (cP = 0.001 Pa·s).

Blender employs kinematic viscosity: dynamic viscosity ÷ density, \\(m^{2}/s\\). Example: water at room temp ≈ 1.002 cP or 0.001002 Pa·s; water density ≈ 1000 kg/m³, yielding kinematic ≈ 0.000001002 m²/s (input: 1.002×10⁻⁶).

Examples of fluids with viscosities:

| Fluid | Dynamic viscosity (in cP) | Kinematic viscosity (Blender, in \\(m^{2}/s\\) ) |
| Water (20 °C) | 1.002×10 0 (1.002) | 1.002×10 -6 (0.000001002) |
| Oil SAE 50 | 5.0×10 2 (500) | 5.0×10 -5 (0.00005) |
| Honey (20 °C) | 1.0×10 4 (10,000) | 2.0×10 -3 (0.002) |
| Chocolate Syrup | 3.0×10 4 (30,000) | 3.0×10 -3 (0.003) |
| Ketchup | 1.0×10 5 (100,000) | 1.0×10 -1 (0.1) |
| Melting Glass | 1.0×10 15 | 1.0×10 0 (1.0) |

Tip

Find kinematic viscosity in correct units via Wolfram Alpha, e.g., "kinematic viscosity of alcohol in m^2/s".

Scientific notation simplifies entry: input base and 10's exponent.

Base
Viscosity base (e.g., 1.002 for water (20 °C)).

Exponent
Viscosity 10⁻¹ exponent (e.g., 6 for water).

Note

Viscosity Varies

Blender defaults appear typical and "look right" when animated. Real viscosity—especially sugar-laden (syrup, honey)—hinges on temp and concentration. Oil viscosity shifts with SAE. Room-temp glass is solid; 1500 °C glass flows like water.

Warning

The simulator doesn't fit non-flowing materials. Huge viscosity values won't behave rigidly but may cause instability.

Surface Tension
Surface tension in grid units. Higher = greater tension.

### High Viscosity Solver

High-viscosity solver targets thick liquids (honey, molasses), boosting accuracy for sluggish, dense sims.

Tip

Strength 0 applies some viscosity. Uncheck to fully disable.

Strength
Liquid viscosity. Higher = thicker.

| Strength of 0.2 (at frame 65).  | Strength of 0.4 (at frame 200).  |
