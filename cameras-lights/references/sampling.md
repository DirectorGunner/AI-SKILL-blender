# Sampling, Volumes, Scene Settings, World Settings ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Sampling; Volumes; Scene Settings; World Settings; Geometry; Line Style; Along Stroke; Crease Angle; Curvature 3D; Distance from Camera; Distance from Object; Noise; Tangent; 2D Offset; 2D Transform; Backbone Stretcher; Bézier Curve; Blueprint.

## Sampling

Sampling — Antialiasing Control

EEVEE uses Temporal Anti-Aliasing (TAA) to suppress aliasing. Sample count determines aliasing suppression; more samples reduce artifacts at performance cost.

Reference
Panel: Render ‣ Sampling

### Viewport

Samples
Viewport sample count. Zero enables continuous resampling.

Temporal Reprojection
Attenuate noise during viewport movement or animation playback. May produce ghosting.

Jittered Shadows
Enable jittered shadows in the viewport. Final renders always use jittered shadows. Affects transparent shadows as well.

### Render

Samples
Final render sample count.

### Shadows

Rays
Rays per light for shadow computation. Higher values reduce random shadow noise.

Steps
Shadow map samples per shadow ray. Higher step counts yield softer shadows at higher cost.

Volumetric Shadows
Approximate surrounding volume light absorption, making volumes more opaque to light. Highly computationally expensive with limitations.

Steps
Volumetric shadow computation steps.

See also
Volume Limitations.

Resolution
Shadow map resolution percentage.

### Advanced

Light Threshold
Minimum light intensity for contribution. Governs distance cutoff for light influence. Lower values help performance.

See also
Custom Distance overrides this setting.

Sampling

This modifier controls stroke definition and precision for subsequent operations.

Sampling
Smaller values increase precision. Be cautious: excessively small values require substantial rendering time and memory.

### Sampling

Render quality can be modified via the Anti-Aliasing method. Different configurations apply to the 3D Viewport, viewport rendering, and final rendering.

The 3D Viewport setting is a user preference indicating the antialiasing method performing best on the target system. The viewport rendering and final rendering setting is stored per scene.

Reference

Panel :

Render ‣ Sampling
Preferences ‣ Viewport

No Anti-Aliasing
No antialiasing is applied.

Single Pass Anti-Aliasing
The scene receives a single post-process antialiasing pass.

Multisample
The scene is rendered multiple times with slight offsets. Antialiasing is aggregated from the multiple renders. Sample counts are predefined for optimal distribution.

5, 8, 11, 16, 32

Tip

Multisample antialiasing works well for small detail rendering like hair.

Progressive Viewport Rendering

In the 3D Viewport, one sample renders at a time. When viewport and scene remain unchanged, the next sample renders.

## Volumes

Volumes — Volumetric Effects

Reference
Panel: Properties ‣ Render ‣ Volumes

EEVEE simulates volumetric scattering by evaluating volume objects within the view frustum.

This employs several 3D textures with substantial video memory demands. Adjust Resolution and Steps to tune dimensions.

Resolution
Volumetric effect quality. Lower resolution increases memory usage and visual quality.

Steps
Volumetric effect computation steps. Higher counts increase memory usage and quality. Samples distribute along view depth.

Distribution
Interpolate between linear and exponential sample spacing. Higher values concentrate samples nearer the camera.

Max Depth
Maximum surface intersection count for accurate volume intersection. Artifacts appear if exceeded.

### Custom Range

EEVEE auto-computes optimal depth range for volume sampling. Sometimes this produces sub-optimal sampling with elevated noise, particularly with World volume shaders or many overlapping volume objects. Enable custom depth range to constrain computation to a depth interval, boosting precision.

Start
Volumetric effect starting distance.

End
Volumetric effect ending distance.

See also
Limitations.

## Scene Settings

Scene Settings — Global Render Control

### Light Probes

Light Probe Spheres Resolution
Sets the resolution for every light probe sphere in the scene.

## World Settings

World Settings — Environment and Global Light

The world environment can emit light, ranging from solid color to complex textures.

EEVEE stores world lighting in an internal Light Probe, making it less precise than Cycles.

EEVEE classifies world lighting as indirect lighting, whereas Cycles treats it as direct.

### Mist Pass

Reference
Panel: World ‣ Mist Pass

Note
The mist pass must be activated in the View Layer tab of the Properties Editor before these settings appear in the World tab.

Mist strengthens depth perception by generating a render layer with a 0.0 to 1.0 depth map usable in the Compositor for mist effects.

Start
Camera distance where mist begins fading.

Depth
Distance from Start over which mist fades. Objects beyond Start + Depth are completely obscured.

Falloff
Curve function governing mist strength progression with distance.

Quadratic:
Uses light falloff calculation (1/x²) for smooth 0.0 to 1.0 transition.

Linear:
Steeper start than quadratic (1/x).

Inverse Quadratic:
Steepest start (1/√x) and approaches 1.0 faster than others.

Tip
Activate visualization in the Camera ‣ Viewport Display panel.

Mist example
(blend-file).

### Settings

Reference
Panel: World ‣ Light Probe

### Light Probe

Resolution
Storage resolution for world light. Equivalent to light probe sphere resolution.

See also
Light Probe Sphere.

### Sun

EEVEE can isolate light from intense sources (e.g., sun from HDRI) and replace with a sun light. Increases illumination quality since light probes alone cannot match this precision.

Threshold
Maximum world contribution recorded in the light probe when nonzero. Excess becomes a sun light. Reduces light bleeding from very bright sources. Zero disables the feature; all lighting stores in light probes.

Angle
Angular diameter of the extracted sun light as viewed from Earth.

Use Shadow
Enable shadow casting on the extracted sun.

See also
Shadow properties match sun light settings exactly.
See Light Properties.

## Geometry

Geometry — Stroke Deformation

This tab controls stroke geometry. It provides only the option to add modifiers.

Modifiers fully apply to stroke geometry (like object modifiers). They process the resulting 2D strokes from the Freestyle line set and displace or deform them in various ways.

Like other modifier stacks, they apply top-to-bottom.

Line Style: Geometry.

### Modifiers

### Types

- 2D Offset
- 2D Transform
- Backbone Stretcher
- Bézier Curve
- Blueprint
- Guiding Lines
- Perlin Noise 1D
- Perlin Noise 2D
- Polygonization
- Sampling
- Simplification
- Sinus Displacement
- Spatial Noise
- Tip Remover

## Line Style

Line Style — Five-Tab Framework

Freestyle line styles define appearance via five primary facets: Stroke, Color, Alpha, Thickness, Geometry, Texture—each on separate tabs. These enable diverse render styles (technical, sketch, cartoon, calligraphy, etc.).

Create unlimited line styles and reuse by selection menu.

Note
Unless noted otherwise, line style lengths are in pixels (relative or absolute per core options).

Line Style Example (blend-file).

### Properties

## Along Stroke

Along Stroke — Length-Based Gradient

The Along Stroke modifier applies a property gradient along each stroke's length, mapping a new value range per stroke.

Along Stroke

This modifier applies a gradient by mapping a base property across the stroke's length. The remapped property varies continuously from start to end.

Along Stroke

This modifier applies a gradient by mapping a base property across the stroke's length. The remapped property varies continuously from start to end.

## Crease Angle

Crease Angle — Edge Sharpness Modifier

This modifier alters properties based on adjacent face angles. Stroke segments not on creases (lacking Crease Angle nature) remain unaffected.

Angle Min, Max
Input value range for the mapping. Out-of-range crease angles clamp to Min/Max angles and corresponding property values.

Crease Angle modifier example by T.K.
(blend-file).

Crease Angle

This modifier responds to the crease angle—the angle separating adjacent faces. Modulator has no effect on stroke segments not lying on creases (edges without crease properties).

Angle Min, Max
The input value range. Crease angles outside this range are clamped to their respective boundary property values.

Crease Angle modifier example by T.K.
(blend-file).

Crease Angle

This modifier responds to the crease angle—the angle separating adjacent faces. Modulator has no effect on stroke segments not lying on creases (edges without crease properties).

Angle Min, Max
The input value range. Crease angles outside this range are clamped to their respective boundary property values.

Crease Angle modifier example by T.K.
(blend-file).

## Curvature 3D

Curvature 3D

A modifier that evaluates surface curvature through radial measurements of the underlying 3D geometry. Curvature, in 2D curve analysis, represents the rate of directional change at any given location. When a curve changes direction rapidly, the curvature value increases proportionally. A straight line exhibits zero curvature. Radial curvature is derived from a 2D cross-section: the intersection of a 3D surface with a plane that contains both the observer position (from the camera) and the surface normal vector at that point.

To enable curvature calculations—and thereby activate this modifier—you must turn on Face Smoothness and apply Smooth Shading to the object.

Curvature Min, Max
The mapping boundaries. When a stroke point falls at or below the Min threshold, it adopts the mapping's start value. Conversely, when it reaches or exceeds Max, it takes the mapping's endpoint.

Curvature 3D modifier demo by T.K.
(blend-file).

Curvature 3D

A modifier that evaluates surface curvature through radial measurements of the underlying 3D geometry. Curvature, in 2D curve analysis, represents the rate of directional change at any given location. When a curve changes direction rapidly, the curvature value increases proportionally. A straight line exhibits zero curvature. Radial curvature is derived from a 2D cross-section: the intersection of a 3D surface with a plane that contains both the observer position (from the camera) and the surface normal vector at that point.

To enable curvature calculations—and thereby activate this modifier—you must turn on Face Smoothness and apply Smooth Shading to the object.

Curvature Min, Max
The mapping boundaries. When a stroke point falls at or below the Min threshold, it adopts the mapping's start value. Conversely, when it reaches or exceeds Max, it takes the mapping's endpoint.

Curvature 3D modifier demo by T.K.
(blend-file).

Curvature 3D

A modifier that evaluates surface curvature through radial measurements of the underlying 3D geometry. Curvature, in 2D curve analysis, represents the rate of directional change at any given location. When a curve changes direction rapidly, the curvature value increases proportionally. A straight line exhibits zero curvature. Radial curvature is derived from a 2D cross-section: the intersection of a 3D surface with a plane that contains both the observer position (from the camera) and the surface normal vector at that point.

To enable curvature calculations—and thereby activate this modifier—you must turn on Face Smoothness and apply Smooth Shading to the object.

Curvature Min, Max
The mapping boundaries. When a stroke point falls at or below the Min threshold, it adopts the mapping's start value. Conversely, when it reaches or exceeds Max, it takes the mapping's endpoint.

Curvature 3D modifier demo by T.K.
(blend-file).

## Distance from Camera

Distance from Camera

This modifier remaps a base property using distance measurements to the active camera as the driving parameter.

Range Min, Max
The mapping boundaries applied to camera-distance values. When a stroke point sits at or within Range Min from the camera or object, the start value applies. When positioned at or beyond Range Max, the endpoint value is used. All measurements follow the scene's unit system, not pixel dimensions.

Fill Range by Selection
Automatically sets min/max bounds by calculating distances from selected mesh vertices to the camera or target.

Distance from Camera

This modifier remaps a base property using distance measurements to the active camera as the driving parameter.

Range Min, Max
The mapping boundaries applied to camera-distance values. When a stroke point sits at or within Range Min from the camera or object, the start value applies. When positioned at or beyond Range Max, the endpoint value is used. All measurements follow the scene's unit system, not pixel dimensions.

Fill Range by Selection
Automatically sets min/max bounds by calculating distances from selected mesh vertices to the camera or target.

Distance from Camera

This modifier remaps a base property using distance measurements to the active camera as the driving parameter.

Range Min, Max
The mapping boundaries applied to camera-distance values. When a stroke point sits at or within Range Min from the camera or object, the start value applies. When positioned at or beyond Range Max, the endpoint value is used. All measurements follow the scene's unit system, not pixel dimensions.

Fill Range by Selection
Automatically sets min/max bounds by calculating distances from selected mesh vertices to the camera or target.

## Distance from Object

Distance from Object

This modifier updates a base property by mapping a distance measurement to a chosen target object or the active camera.

Target
Specifies which object to measure from.

Range Min, Max
The mapping boundaries applied to distance values. When a stroke point lies at or within Range Min from the reference point, the start value applies. When positioned at or beyond Range Max, the endpoint is used. All measurements follow the scene's unit system, not pixel dimensions.

Fill Range by Selection
Automatically sets min/max bounds by calculating distances from selected mesh vertices to the reference point or target.

Distance from Object

This modifier updates a base property by mapping a distance measurement to a chosen target object or the active camera.

Target
Specifies which object to measure from.

Range Min, Max
The mapping boundaries applied to distance values. When a stroke point lies at or within Range Min from the reference point, the start value applies. When positioned at or beyond Range Max, the endpoint is used. All measurements follow the scene's unit system, not pixel dimensions.

Fill Range by Selection
Automatically sets min/max bounds by calculating distances from selected mesh vertices to the reference point or target.

Distance from Object

This modifier updates a base property by mapping a distance measurement to a chosen target object or the active camera.

Target
Specifies which object to measure from.

Range Min, Max
The mapping boundaries applied to distance values. When a stroke point lies at or within Range Min from the reference point, the start value applies. When positioned at or beyond Range Max, the endpoint is used. All measurements follow the scene's unit system, not pixel dimensions.

Fill Range by Selection
Automatically sets min/max bounds by calculating distances from selected mesh vertices to the reference point or target.

## Noise

Noise

This modifier distributes a property across a stroke using pseudorandom variation.

Amplitude
The peak noise magnitude. Higher values correspond to increased opacity and solidity.

Period
Controls noise oscillation rate. How frequently the property shifts along the stroke. Larger values result in smoother transitions between color values.

Seed
The initialization parameter for the random generator.

Asymmetric Thickness only
Enables unequal thickness distribution at each point. A stroke is internally represented as a spine with distinct left and right thickness values. Most thickness-based modifiers enforce equal left-right values, but this option permits asymmetric assignment for more nuanced visual results.

Effect generated with a noise thickness modifier using asymmetric thickness.

Noise

This modifier distributes a property across a stroke using pseudorandom variation.

Amplitude
The peak noise magnitude. Higher values correspond to increased opacity and solidity.

Period
Controls noise oscillation rate. How frequently the property shifts along the stroke. Larger values result in smoother transitions between color values.

Seed
The initialization parameter for the random generator.

Asymmetric Thickness only
Enables unequal thickness distribution at each point. A stroke is internally represented as a spine with distinct left and right thickness values. Most thickness-based modifiers enforce equal left-right values, but this option permits asymmetric assignment for more nuanced visual results.

Effect generated with a noise thickness modifier using asymmetric thickness.

Noise

This modifier distributes a property across a stroke using pseudorandom variation.

Amplitude
The peak noise magnitude. Higher values correspond to increased opacity and solidity.

Period
Controls noise oscillation rate. How frequently the property shifts along the stroke. Larger values result in smoother transitions between color values.

Seed
The initialization parameter for the random generator.

Asymmetric Thickness only
Enables unequal thickness distribution at each point. A stroke is internally represented as a spine with distinct left and right thickness values. Most thickness-based modifiers enforce equal left-right values, but this option permits asymmetric assignment for more nuanced visual results.

Effect generated with a noise thickness modifier using asymmetric thickness.

## Tangent

Tangent

This modifier applies its effect based on stroke direction as calculated at each stroke vertex.

Tangent

This modifier applies its effect based on stroke direction as calculated at each stroke vertex.

Tangent

This modifier applies its effect based on stroke direction as calculated at each stroke vertex.

## 2D Offset

2D Offset

This modifier shifts the backbone geometry using two-dimensional offsets. It provides two independent parameter sets:

Start, End
Apply offset to the stroke's endpoints along the perpendicular (2D normal) direction. The effect interpolates across the entire stroke—setting only Start to 50 applies 50 pixels of offset at the beginning, 25 pixels at the midpoint, and zero at the end.

X, Y
Add uniform horizontal and/or vertical offset throughout the entire stroke.

## 2D Transform

2D Transform

This modifier applies 2D scaling followed by rotation to the backbone geometry.

Pivot
Selects the rotation and scaling center:

Stroke Center :
The median position of the stroke.

Stroke Start :
The stroke's first point.

Stroke End :
The stroke's final point.

Stroke Point Parameter :
Places the pivot at a proportional position along the stroke (0.0 = start, 1.0 = end).

Absolute 2D Point :
Uses explicit Pivot X and Y coordinates in the final render (measured from the bottom-left corner).

Important

Account for the actual render size: resolution combined with resolution percentage.

Scale X, Y
The scaling magnitudes in each axis.

Rotation Angle
The angular rotation value.

2D Transform modifier
(blend-file).

## Backbone Stretcher

Backbone Stretcher

This modifier extends the stroke by adding length to its endpoints.

Backbone Length
The amount of extension applied to both ends.

## Bézier Curve

Bézier Curve

This modifier converts a stroke into a smooth Bézier spline.

Error
The maximum allowable difference between the resulting Bézier representation and the input stroke path.

Bézier Curve modifier demo by T.K.
(blend-file).

## Blueprint

Blueprint

This modifier generates blueprint-style strokes using basic geometric outlines—circles, ellipses, or squares. Blueprint here describes the initial structural lines sketched to establish silhouettes with elemental shapes.

Shape
Selects the base geometry: Circles, Ellipses, or Squares.

Rounds
Specifies how many repetitions occur, simulating multiple pen passes (reiterations of the drawing process).

Random Radius, Center
For Circles and Ellipses. Introduces variability into each repetition for the relevant parameter. Multiple rounds without randomness would create identical overlapping drawings.

Backbone Length, Backbone
For Squares. The first augments edge length (further modulated by the second). The second injects randomness into the squares.

The Min 2D Length feature from the Strokes settings proves valuable for filtering out noise from tiny strokes…

## Guiding Lines

Guiding Lines

This modifier reduces a stroke to a direct line between its endpoints.

Offset
Adjusts the start and end coordinates relative to the original path before creating the linear connection.

Shorter strokes yield superior results, as they approximate straight lines more effectively. Pairing this modifier with the Strokes panel's subdivision tools (2D angle or 2D length thresholds) is recommended for optimal outcomes.

Guiding Lines modifier Demo by T.K.
(blend-file).

## Perlin Noise 1D

Perlin Noise 1D

This modifier applies single-dimensional Perlin noise to the stroke. The curvilinear parameter (ranging 0 to 1, determined by a vertex's relative position in the stroke) serves as input to the noise function, creating displacements.

This ensures identical noise outcomes for strokes with matching length and sample interval.

Frequency
Noise density (effectively a scale along the stroke direction).

Amplitude
The magnitude of distortion applied in the Angle direction.

Seed
The random-seed parameter (same seed yields reproducible results within a stroke).

Octaves
The number of noise-detail layers.

Angle
The direction of noise application (0.0 = purely horizontal).

## Perlin Noise 2D

Perlin Noise 2D

This modifier applies Perlin-based noise to the stroke using 2D coordinate information. Vertex positions in 2D space feed into the noise generator, producing spatial displacements.

Frequency
Noise density (effectively a scale along the stroke direction).

Amplitude
The magnitude of distortion applied in the Angle direction.

Seed
The random-seed parameter (same seed yields reproducible results within a stroke).

Octaves
The number of noise-detail layers.

Angle
The direction of noise application (0.0 = purely horizontal).

## Polygonization

Polygonization

This modifier reduces strokes to their simplest form, converting smooth paths into jagged polylines.

Error
The maximum allowed separation between the simplified result and the original (larger values produce more jagged approximations).

## Simplification

Simplification

This modifier merges nearby stroke vertices, functioning similarly to the Decimate operation on meshes.

Tolerance
The proximity threshold for vertex merging. Higher tolerance results in more aggressive vertex removal.

## Sinus Displacement

Sinus Displacement

This modifier imparts sinusoidal waviness to the stroke.

Wavelength
The span of each undulation along the stroke.

Amplitude
The height of undulations across the stroke width.

Phase
Offsets the wave pattern position along the stroke.

Tip

Wave patterns remain visually identical at Phase 0 and any whole multiple of the Wavelength. This property enables seamless video loops featuring wavy lines without visible discontinuities.

Sinus Displacement modifier demo by T.K.
(blend-file).

## Spatial Noise

Spatial Noise

This modifier adds spatial noise by displacing points perpendicular to stroke direction (along the normal) at each vertex.

Amplitude
The displacement strength.

Scale
The noise's lateral extent.

Octaves
The number of detail layers.

Smooth
Apply filtering to reduce noise roughness when toggled on.

Pure Random
When off, each random value influences the next, creating correlated noise; when on, values are independent. Disabling this produces more "cohesive" patterns.

## Tip Remover

Tip Remover

This modifier excises a segment from both endpoints of the stroke.

Tip Length
The length of material to remove from each end.

## Calligraphy

Calligraphy

This modifier emulates broad, flat-edged writing instruments. It generates varying thickness according to stroke angle.

Orientation
The virtual pen angle measured from vertical. An angle of 0.0 aligns with the vertical axis, making vertical strokes the thickest and horizontal strokes the thinnest (aligned vs. perpendicular to the angle setting).

Calligraphy modifier demo by T.K.
(blend-file).

## View Layer

### View Layer

Reference

Panel :

Properties ‣ View Layer ‣ View Layer

View Layer panel.

The Layer Panel displays configuration for the active View Layer.

Use for Rendering
The active layer will generate during rendering.

Render Single Layer
Generate exclusively the active layer.

Note

The shell disregards this option.
