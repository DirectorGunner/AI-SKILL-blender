# Simplify, Volumes, World Settings, Light Probes ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Simplify; Volumes; World Settings; Light Probes; Light Probe Plane; Light Probe Volume; Light Settings (EEVEE).

## Simplify

### Simplify

Reference

Menu :

Render ‣ Simplify

Common Settings

Max Subdivision
Subdivision limit for Subdivision Surface modifiers.

Child Particles
Display fraction of all particle and hair children.

Texture Limit
Auto-scales images below selected thresholds. Cuts memory use for large scenes with high-resolution textures.

### Viewport

Reference to Common Settings above.

Volume Resolution
Volume rendering percentage in viewport. Mainly impacts memory rather than processing.

Normals
Skip custom and face corner normal computation for viewport mesh display.

### Render

Reference to Common Settings above.

### Culling

Camera Cull
Removes objects beyond the camera frustum, adjusted by Margin .

Distance Cull
Removes objects past the distance threshold from the active camera. Threshold set via Distance property.

### Grease Pencil

Playback Only
Activate simplification exclusively during animation playback.

Fill
Include fill in Grease Pencil materials.

Modifiers
Display Grease Pencil modifiers.

Shader Effects
Display Grease Pencil visual effects.

Layer Tinting
Display layer tint customization.

Anti-Aliasing
Apply Anti-Aliasing to soften stroke borders. Adjustment via SMAA Threshold.

## Volumes

### Volumes

Reference

Panel :

Render ‣ Volumes

Biased
Standard volume rendering employs null scattering—unbiased, fewer anomalies, potentially noisier. Biased uses ray marching with step and iteration controls.

Note

The following applies to biased ray marching only.

Step distance between volume samples. Cycles computes this based on volume object voxel size and smoke simulations.

Step size increases reduce duration, sacrificing volume precision. For procedural detail-adding volume shaders, per-object, material, or world step adjustment helps.

Step Rate Render Biased
Global step size scaling across all render volumes. Increase to cut time, losing detail.

Viewport Biased
Global step size scaling for viewport volumes. Raise for quicker interaction.

Max Steps Biased
Maximum volume path steps, guarding against extreme durations with large objects or tiny steps.

### Volumes

Volume rendering is used to render various effects that cannot be represented by hard surfaces alone.

- Smoke, fire or clouds are set up using a volume object or fluid simulation, with only a volume shader.

- Meshes can also be used to create such shapes by removing the default surface shader and using a volume shader with the mesh shape defining the volume bounds and textures defining the volume density.

- Mist is created with a volume shader for the world, or with a large mesh object encompassing the scene.

- Absorption in glass is simulated by combining a glass surface shader with refraction and a volume absorption shader for the interior of the object.

### Shading

### Principled Volume

Principled Volume is a physically-based volume shader that can be used to create a wide range of volume materials. It supports scattering, absorption and emission in one easy to use node. Fire can be rendered with blackbody emission.

Smoke and fire rendered with Principled Volume shader.

### Volume Components

For more control, volume shading components can be manually combined into a custom shader setup.

- Volume Absorption will absorb part of the light as it passes through the volume. This can be used to shade for example black smoke or colored glass objects, or mixed with the Volume Scatter node. This node is similar to the transparent BSDF node, it blocks part of the light and lets other light pass straight through.

- Volume Scatter lets light scatter in other directions as it hits particles in the volume. The anisotropy defines in which direction the light is more likely to scatter. A value of 0 will let light scatter evenly in all directions (similar to the diffuse BSDF node), negative values let light scatter mostly backwards, and positive values let light scatter mostly forward. This can be used to shade white smoke or clouds for example.

- Emission will emit light from the volume, for example for fire.

Volume Absorption, Scatter and Emission

### Attributes

When rendering smoke and fire, volume attributes are used to define the shape and shading of the volume. The Principled Volume shader will use them by default, while custom volume shaders can use the Attribute node to get attributes such as density, color and temperature.

### Density

All volume shaders have a density input. The density defines how much of the light will interact with the volume, getting absorbed or scattered, and how much will pass straight through. For effects such as smoke you would specify a density field to indicate where in the volume there is smoke and how much (density bigger than 0), and where there is no smoke (density equals 0).

Volumes in the real world consist of particles, a higher density means there are more particles per unit volume. More particles means there is a higher chance for light to collide with a particle and get absorbed or scattered, rather than passing straight through.

### Mesh Volumes

Meshes used for volume render should be closed and Manifold. That means that there should be no holes in the mesh. Each edge must be connected to exactly two faces such that there are no holes or T-shaped faces where three or more faces are connected to an edge.

Normals must point outside for correct results. The normals are used to determine if a ray enters or exits a volume, and if they point in a wrong direction, or there is a hole in the mesh, then the renderer is unable to decide what is the inside or outside of the volume.

These rules are the same as for rendering glass refraction correctly.

### World Volume

A volume shader can also be applied to the world, filling the entire space.

Currently, this is most useful for night time or other dark scenes, as the world surface shader or sun lights will have no effect if a volume shader is used. This is because the world background is assumed to be infinitely far away, which is accurate enough for the sun for example. However, for modeling effects such as fog or atmospheric scattering, it is not a good assumption that the volume fills the entire space, as most of the distance between the sun and the earth is empty space. For such effects it is be better to create a volume object surrounding the scene. The size of this object will determine how much light is scattered or absorbed.

### Multiple Scattering

Real-world effects such as scattering in clouds or subsurface scattering require many scattering bounces. However, unbiased rendering of such effects can be noisy, so by default the number of bounces is zero in Cycles, and no support is available in EEVEE. The effect you get when rendering with zero volume bounces is what is known as "single scattering", the effect from more bounces is "multiple scattering".

For rendering materials like skin or milk that require multiple scattering, subsurface scattering is more efficient and easier to control. Particularly the random walk method can accurately render such materials.

For materials such as clouds or smoke that do not have a well-defined surface, volume rendering is required. These look best with many scattering bounces, but in practice one might have to limit the number of bounces to keep render times acceptable.

## World Settings

### World Settings

### Mist Pass

Reference

Panel :

World ‣ Mist Pass

Note

Mist pass must activate in the View Layer Properties Editor tab before World tab settings appear.

Mist augments depth perception in renders. Blender creates a depth-mapped render layer (0.0–1.0) for compositor mist synthesis.

Start
Distance from camera where mist begins fading.

Depth
Start-relative mist fade span. Objects beyond Start + Depth disappear into mist.

Falloff
Mist intensity progression curve with distance.

Quadratic :

Light falloff calculation ( 1/{x^2} ), providing smooth 0.0 to 1.0 transition.

Linear :

Steeper start than quadratic ( 1/{x} ).

Inverse Quadratic :

Steepest start ( 1/{√x} ), approaches 1.0 faster.

Tip

Camera ‣ Viewport Display panel contains mist visualization activation.

Mist example
(blend-file).

### Ray Visibility

Reference

Panel :

World ‣ Ray Visibility

Like other objects, Ray Visibility manages which shaders perceive the backdrop.

### Tricks

Scenarios arise where different backgrounds suit direct versus indirect viewing. A Mix node solution: set Blend Factor to Is Camera Ray . First input becomes indirect color, second direct. Useful for high-res background images with low-res lighting.

Similarly, combining Is Camera and Is Glossy rays displays high-res images in reflections too.

Nodes for the trick above.

### Settings

Reference

Panel :

World ‣ Settings

### Surface

Sampling
World material sampling technique. Auto or Manual enable Multiple Importance Sampling while None disables. Multiple Importance Sampling favors lighter texture regions, reducing render noise at artifact risk (Fireflies). Enable with textured small-area lights (like suns) for faster convergence.

Below: Multiple Importance Sample off versus on. Both render 25 seconds (Off: 1,500 samples, On: 1,000).

| Multiple Importance Sample off. | Multiple Importance Sample on. |

Map Resolution
Importance map resolution. Higher resolution captures fine features and samples accurately, consuming more memory, rendering slightly slower. May lower noise with high-res images.

Max Bounces
Backdrop light bounce limit in rendering.

See also

See Reducing Noise for additional reduction guidance.

Shadow Caustics
Flag World Shader as refractive caustic source. Pairs with Cast and Receive caustic object settings for selective refractive caustic acceleration.

### Volume

Sampling Method

Distance :

Dense volumes lit from afar: Distance proves most effective. Typically unused for World volumes.

Equiangular :

Light inside/near volume: equiangular suits better.

Multiple Importance :

Mixed conditions: multiple importance optimal.

Interpolation
Volume interpolation approach.

Linear :

Basic interpolation, suited to thin volumes.

Cubic :

Refined high-detail interpolation for dense volumes, slower.

Step Size Biased
World volume shader sample spacing. Only active with Render ‣ Volumes ‣ Biased enabled. See Volume Render Settings.

### Light Group

Light Group Cycles only
Add the current World Surface Shader to the chosen Light Group.

Add Light Group
Pressing this generates a Light Group matching the name input field and assigns this World Shader to it if the name lacks an existing group.

## Light Probes

### Light Probes

Light probe objects assist EEVEE as foundational elements.

Three light probe categories exist. Each records lighting at differing resolution and frequency bands. Probes combine to extract light information where ray tracing is impractical (performance or capability grounds).

These objects serve exclusively EEVEE (and Material Preview consequently).

### Types

## Light Probe Plane

### Light Probe Plane

A planar light probe captures incoming light from a single direction across all positions on a flat surface. Only the specular reflection pathway currently provides data.

Planar probes fit smooth flat surfaces well.

Each visible planar probe costs render duration—each requires scene recomputation.

Planar probes operate when ray tracing uses Screen-Trace . They quicken tracing and furnish screen-space ray tracing gaps.

Note

Volumetrics and reflections remain unhandled within Light probe planes.

### Placement

Without Backface Culling, positioning the light probe plane on the planar surface captures its underside.

Elevate the light probe plane above the surface to avoid self-inclusion. Or deactivate light probe visibility in object visibility panel.

### Properties

Reference

Panel :

Object Data ‣ Probe

Distance
A probe only alters lighting inside its influence area. Distance parameter and object scale define this zone.

For planar probes, influence distance measures from the plane. Surfaces aligned with the Reflection Plane get captured reflection contributions.

### Capture

Clipping Offset
Distance below the plane for near clip during capture. Increase to address reflection contact artifacts.

### Viewport Display

Reference

Panel :

Object Data ‣ Viewport Display

Arrow Size
Normal direction arrow scale.

Capture
Show captured reflection on a maximally reflective plane in the viewport.

Influence
Display influence area bounds in viewport.

## Light Probe Volume

### Light Probe Volume

A volumetric probe captures light from all directions across numerous interior positions.

Captured light filters to diffuse only. Capture point positions appear as an overlay when Irradiance Volume selection is active.

Objects outside any Irradiance Volume, or where indirect light hasn't baked, receive world diffuse lighting.

Tip

- Indoor lighting: align grids with room geometry.

- Exclude empty regions and low-variation areas from high resolution allocation.

- Problem zones get fixed via smaller grids nearby.

- Large environments may require many volumes at varying detail levels.

### Properties

Reference

Panel :

Object Data ‣ Probe

Intensity
Recorded lighting intensity. Anything besides 1.0 lacks physical basis. Reserve for artistic tweaking, animation, or adjustment.

Sampling Bias

Normal Bias
Offset irradiance grid samples along surface normal to curtail light seepage. Excessive values impart specular appearance to diffuse surfaces.

View Bias
Offset irradiance grid samples toward the viewer, reducing seepage. Excessive values introduce viewing artifacts. Prefer when the camera is fixed.

Facing Bias
Zero prevents capturing points behind shaded surfaces, yielding non-smooth interpolation at high resolution. Higher bias smooths interpolation but permits some seepage.

Validity & Dilation

During baking, each capture point receives a validity score from back-face strikes during lighting capture. Lone materials with Single Sided for Light Probe Volumes lower the score.

Validity Threshold
Disregard capture points below this validity score during lighting calculation. Suppresses trapped geometry artifacts.

Dilation Threshold
Points below this threshold get data replaced from valid neighbors.

Radius
Neighbor search distance in capture points.

### Bake

Light probe volume data remains static, requiring manual baking. Once baked, data belongs to the object and can move, animate, and transfer between files.

Note

Rendering uses object visibility during baking.

Scene conversion into an accelerated format during baking consumes substantial GPU memory, potentially blocking baking. Approaches to remedy:

- Segment large scenes into smaller zones or variable detail.

- Reduce Surfel Resolution .

- Deactivate light probe visibility on minor-impact objects.

Tip

Debug Value 3, 4, 5 expose the internal representation.

### Resolution

Resolution X, Y, Z
Volumetric probe spatial resolution. The local volume subdivides into a grid of specified dimensions. Each grid cell captures lighting.

Bake Samples
Light direction count during baking. Proportionally extends baking duration to scene size.

Surfel Resolution
Surfel spawning per local unit. Higher yields better quality but severe memory increases.

Tip

Optimal: double the maximum Resolution .

### Capture

Capture Distance
Bake distance around the light probe volume. Zero captures only interior.

Contributions – World
Bake world light for precision versus correct multi-volume blending.

Contributions – Indirect Light
Capture post-source light bounces.

Contributions – Emission
Capture emissive surfaces during baking.

#### Clamping

Direct Light
Clamp direct light entry. 0.0 deactivates. Direct light: single-bounce light or emissive first-bounce light.

Indirect Light
Clamp indirect light entry. 0.0 deactivates. Indirect light: post-first-bounce light from sources or emissive surfaces.

Tip

Tiny non-zero Clamp Indirect captures first-bounce light only.

#### Offset

Baking adjusts capture point placement to lower artifacts. Points shift away from surfaces and relocate from interiors when not too deep.

Surface Offset
Surface distance for point displacement.

Search Distance
Search span for positions near single-sided object back-faces.

Note

Lone materials with Single Sided for Light Probe Volumes move capture point position.

### Viewport Display

Data
Show captured light as diffuse spheres at given size.

Clipping
Show capture clip extent.

Influence
Show influence area. Inner sphere marks falloff start.

## Light Settings (EEVEE)

Light Settings (EEVEE) — Overview

Reference
Panel: Properties ‣ Object Data and Shader Editor ‣ Sidebar ‣ Options

In EEVEE, illumination originates from three sources: the world environment, materials that emit light, and light objects. Light objects provide targeted illumination control and appear as scene elements rather than contributing directly to the rendered output.

For settings shared across rendering engines, see Light settings.

### Shadow

EEVEE employs Virtual Shadow Mapping combined with Shadow Map Raytracing to produce shadow effects. This approach concentrates shadow detail where needed, achieving better accuracy than traditional shadow mapping and includes efficient caching.

Tip
- The error "Shadow buffer full" occurs when shadow memory allocation exceeds system capacity. Remedy: enlarge Shadow Pool Size or reduce Resolution Limit on individual lights. Alternatively, disable shadow casting on less critical light sources.
- Adjust Shadow Map Raytracing behavior through Render Settings.
- Enable Jitter to diminish light leaking artifacts caused by large light sources and Shadow Map Raytracing.

See also
Limitations.

Jitter
Enable jittered soft shadows to enhance shadow precision. Incurs significant performance overhead since the shadow map cannot be cached and recomputes for each render sample.

Note
Viewport display is off by default; check render settings to enable visibility.

Overblur
Apply shadow tracing to individual jittered samples to attenuate under-sampling noise.

Note
Values above zero produce softer shadows but sacrifice physical accuracy.

Filter
Reduce shadow aliasing via PCF with circular kernels. The filter's world-space scale depends on the shadowed pixel's shadow map resolution.

Note
Values larger than 1px raise light leaking risk.

Resolution Limit
Sets the minimum shadow map pixel size. Larger values conserve memory at the expense of shadow quality and also accelerate rendering of complex scenes. Shadows scale to match screen pixel position, enabling sharp precision but requiring substantial memory. This setting caps the detail level captured.

Note
Increasing shadow map coarseness elevates light leaking probability.

Absolute Resolution Limit
Fix resolution at 1 unit from the light source rather than relative to screen pixels. Transforms Resolution Limit to behave as a standard shadow map pixel size.

Hint
This formula calculates Resolution Limit for a target resolution:

[resolution_limit = 2 * sqrt(2) / resolution]

Here (2 * sqrt(2)) denotes the unit cube diagonal and (resolution) denotes target resolution (e.g., 1024px).

Note
This feature is unavailable for Sun Light.

### Influence

These multipliers control light contribution per shader type, intended for creative adjustment. Values differing from 1.0 deviate from physical accuracy.

Diffuse
Multiplier for diffuse reflection intensity.

Glossy
Multiplier for glossy reflection intensity.

Transmission
Multiplier for transmission intensity.

Volume Scatter
Multiplier for volume scattering intensity.

### Custom Distance

When enabled, uses Distance for custom attenuation instead of the global Light Threshold. The distance initializes automatically based on threshold, computed at the light origin using inverse-square falloff.

Distance
Specifies where light contribution decays to zero.

Note
Sun Light does not support this feature.

See also
Global Light Threshold.
