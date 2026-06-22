# Geometry Node, Curves Info Node, Layer Weight Node, Light Path Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Geometry Node; Curves Info Node; Layer Weight Node; Light Path Node; Particle Info Node; Point Info; Tangent Node; Texture Coordinate Node; UV Map Node; Color Attribute Node; Volume Info Node; Wireframe Node; AOV Output Node; Output Nodes; Light Output Node; Material Output Node; World Output Node; Add Shader.

## Geometry Node

### Geometry Node

Access geometric information about the shading point. All vector coordinates use World Space. For volume shaders, only position and incoming vector are available.

### Inputs

None.

### Properties

None.

### Outputs

- **Position** — Shading point location.
- **Normal** — Surface shading normal (includes smooth normals and bump mapping).
- **Tangent** — Surface tangent direction.
- **True Normal** — Flat/geometry normal of the surface.
- **Incoming** — Vector pointing toward the viewer.
- **Parametric** — Surface parametric coordinates. For area lights outputs UV planar coordinates; for point lights outputs spherical coordinates.
- **Backfacing** — 1.0 if viewed from back, 0.0 from front.
- **Pointiness** *(Cycles Only)* — Vertex-based curvature approximation. Light values indicate convex angles; dark values indicate concave. Useful for dirt maps and wear effects.
- **Random per Island** *(Cycles Only)* — Unique random value per connected mesh component (island). Useful for variations on multi-part objects like tree leaves or wood planks. When using Array modifiers, retrieves a random value per instance.

## Curves Info Node

### Curves Info Node

Access Hair information using this node.

### Inputs

None.

### Properties

None.

### Outputs

- **Is Strand** — Outputs 1 when shading a strand, 0 otherwise.
- **Intercept** — Position along strand where ray intersects (1 at tip, 0 at root).
- **Length** — Measurement from root to tip as grayscale (0 to infinity).
- **Thickness** — Strand thickness at ray intersection point.
- **Tangent Normal** — Strand tangent normal.
- **Random** — Per-curve random value (0 to 1). Works with color ramps to randomize strand color.

## Layer Weight Node

### Layer Weight Node

Output a weight for shader layering with Mix Shader nodes.

### Inputs

- **Blend** — Bias output toward 0 or 1 for uneven shader mixing.
- **Normal** — Bump or normal map to affect output.

### Properties

None.

### Outputs

- **Fresnel** — Dielectric Fresnel weight for layering diffuse and glossy (e.g., plastic materials). Like the Fresnel node but in the 0.0–1.0 range for convenience.
- **Facing** — Weight blending from first to second shader as surface orientation shifts from viewer-facing to grazing.

## Light Path Node

### Light Path Node

Identify the incoming ray type for which the shader is executing. Useful for non-physically-based tricks. See Light Paths documentation for ray type meanings.

### Inputs

None.

### Properties

None.

### Outputs

- **Is Camera Ray** — 1.0 for camera rays, 0.0 otherwise.
- **Is Shadow Ray** — 1.0 for shadow rays, 0.0 otherwise.
- **Is Diffuse Ray** — 1.0 for diffuse rays, 0.0 otherwise.
- **Is Glossy Ray** — 1.0 for glossy rays, 0.0 otherwise.
- **Is Singular Ray** *(Cycles Only)* — 1.0 for singular rays, 0.0 otherwise.
- **Is Reflection Ray** *(Cycles Only)* — 1.0 for reflection rays, 0.0 otherwise.
- **Is Transmission Ray** *(Cycles Only)* — 1.0 for transmission rays, 0.0 otherwise.
- **Is Volume Scatter Ray** *(Cycles Only)* — 1.0 for volume scatter rays, 0.0 otherwise.
- **Ray Length** *(Cycles Only)* — Distance the light ray traveled since last bounce or camera.
- **Ray Depth** — Number of surface bounces (reflections/transmissions). Note: Transparent shaders don't count as normal bounces.
- **Diffuse Depth** *(Cycles Only)* — Count of diffuse reflections/transmissions.
- **Glossy Depth** *(Cycles Only)* — Count of glossy reflections/transmissions.
- **Transparent Depth** *(Cycles Only)* — Count of transparent surface passes.
- **Transmission Depth** *(Cycles Only)* — Count of transmissive surface passes. Typical use: avoid render artifacts (black spots from bounce limits) by switching from transmissive to diffuse past a threshold. See Mix Shader.
- **Portal Depth** *(Cycles Only)* — Count of Ray Portal BSDF passes.

### EEVEE Support

EEVEE has no true ray concept, but outputs some ray-path controls for Cycles compatibility:

- **Is Camera** — Supported.
- **Is Shadow** — Supported.
- **Is Diffuse** — Supported.
- **Is Glossy** — Supported.
- **Is Singular** — Not supported (same as Is Glossy).
- **Is Reflection** — Not supported (same as Is Glossy).
- **Is Transmission** — Not supported (same as Is Glossy).
- **Ray Length** — Distance from camera to shading point.
- **Ray Depth** — Current light-cache baking bounce.
- **Diffuse Depth** — Same as Ray Depth during diffuse baking.
- **Glossy Depth** — Same as Ray Depth during specular baking.
- **Transparent Depth** — Not supported (defaults to 0).
- **Transmission Depth** — Not supported (same as Glossy Depth).

Note: Is Glossy doesn't work with Screen Space Reflections/Refractions but works with reflection planes (with or without SSR).

## Particle Info Node

### Particle Info Node

*Cycles Only*

Retrieve particle data for instancing objects in Object or Collection Render mode. Adds variation to materials on instanced objects by accessing parent particle information.

Note: Currently supports parent particles only; child particle info is unavailable.

### Inputs

None.

### Properties

None.

### Outputs

- **Index** — Particle number (0 to particle count).
- **Random** — Per-particle random (0 to 1). Use with color ramps for color randomization.
- **Age** — Particle age in frames.
- **Lifetime** — Total lifespan in frames.
- **Location** — Particle position.
- **Size** — Particle size.
- **Velocity** — Particle velocity.
- **Angular Velocity** — Particle rotation rate.

## Point Info

### Point Info

*Cycles Only*

Access point cloud object data in the material node tree for individual point variation. Useful for applying one material to multiple points with unique properties.

### Inputs

None.

### Properties

None.

### Outputs

- **Location** — Point position.
- **Radius** — Point size.
- **Random** — Per-point random (0 to 1). Use with color ramps for color randomization.

## Tangent Node

### Tangent Node

Generate tangent direction for the Anisotropic BSDF.

### Inputs

None.

### Properties

**Direction Type** — Choose how tangent derives. Use cylindrical projection around X, Y, or Z (radial), or manually created UV Maps for full control.

### Outputs

- **Tangent** — The tangent direction vector.

## Texture Coordinate Node

### Texture Coordinate Node

Output various coordinate systems for procedural textures, image textures, and vector-based texture inputs. Connect typically to texture node Vector inputs to place or manipulate textures in different spaces.

### Inputs

None.

### Properties

**Object** — Specific object for object-space coordinates. Affects only the Object output.

**From Instancer** *(Cycles Only)* — When geometry is instanced from vertices or faces, source texture coordinates from the instancer. Affects Generated and UV outputs only.

Note: From Instancer works with UV output only when the object is instanced (particles or faces).

### Outputs

- **Generated** — Auto-generated coordinates from mesh vertex positions (non-deformed). Range 0.0–1.0 across object bounding box; stays attached to surface under animation. See Texture Spaces.
- **Normal** — Object-space normal for texturing fixed to the object as it transforms. Works on Point and Spot lights, accounting for light rotation.
- **UV** — Active Render UV map coordinates. See UV Mapping. To use non-active UV maps, use UV Map node.
- **Object** — Uses another object (often an empty) as coordinate source. Easily places small images at specific locations or animates texture movement.
- **Camera** — Position in camera space.
- **Window** — Screen location (0.0–1.0 left-to-right, bottom-to-top). Suited for blending objects.
- **Reflection** — Direction of reflection vector as coordinates. Use for reflection maps and environment mapping.

## UV Map Node

### UV Map Node

Output texture coordinates from a specific UV map. Useful when working with multiple UV layouts in one material. Connect typically to texture node Vector inputs for placement and manipulation.

Note: Unlike Texture Coordinate Node (which outputs only the active render UV map), this node accesses any assigned UV map.

### Inputs

None.

### Properties

**From Instancer** *(Cycles Only)* — See Texture Coordinate Node's From Instancer option.

**UV Map** — Name of the UV map to use. Populated from the object's mesh UV maps. If unset, uses the Active Render UV map.

### Outputs

- **UV** — Coordinates from the specified UV map.

## Color Attribute Node

### Color Attribute Node

Access Color Attributes and their alpha values using this node.

### Inputs

None.

### Properties

**Color Attribute** — Select the target Color Attribute from the active object's mesh. If the object has no mesh, a warning appears. Red-highlighted attributes indicate unavailability in the active object's mesh but may exist in other meshes sharing this material.

### Outputs

- **Color** — Standard color output.
- **Alpha** — Alpha value.

## Volume Info Node

### Volume Info Node

Retrieve information about Smoke Domains.

### Inputs

None.

### Properties

None.

### Outputs

- **Color** — Smoke color inside the Fluid Domain (same as vector output; Factor is channel average).
- **Density** — Scalar defining smoke density in the Fluid Domain.
- **Flame** — Scalar defining fire density in the Fluid Domain (all three outputs identical).
- **Temperature** — Volume temperature as scalar. Range 0–1 maps to 0–1000 Kelvin. Use with Blackbody or Principled Volume shaders for physically-based fire. Remap temperature first (Blackbody expects Kelvin values).

### Example

Smoke density visualization. / Fire color calculation using the Blackbody node.

## Wireframe Node

### Wireframe Node

Retrieve object edges as Cycles interprets them. Meshes triangulate before processing, so wireframe topology always appears triangulated.

### Inputs

None.

### Properties

**Pixel Size** — When enabled, edge line width is defined in screen space.

**Size** — Edge line thickness.

### Outputs

- **Factor** — Black-and-white mask with white lines representing edges per object topology.

### Examples

Wireframe node showcasing mesh topology.

## AOV Output Node

### AOV Output Node

Create custom render passes for arbitrary shader node components using Shader AOVs (Arbitrary Output Variables). Define the pass in the Shader AOV panel, then reference it here. This workflow suits debugging or post-processing fine details.

Tip: Use AOV Output in Material and World shader nodes.

### Inputs

- **Color** — Output a color variable (also works for normal values).
- **Value** — Output a single numerical value.

### Properties

**Name** — Name of the render pass. Must match a pass name in the Shader AOV panel.

### Outputs

None.

## Output Nodes

### Output Nodes

Output nodes are the final node in every tree. Although multiple can exist, only one is active (indicated by a colored/darkened header). Output nodes follow Shaders except for Material Output Displacement.

## Light Output Node

### Light Output Node

Define the final shader for a Light object. Control light emission using shader nodes. Currently, light shaders work only with Cycles; other renderers ignore this node.

See Nodes for shader node usage with lights.

### Inputs

- **Surface** — Shader controlling emitted light. Typically an Emission shader defining color and intensity. Only emission-based shading affects lighting; other shader types have no effect.

### Properties

**Target** — Specify which render engine uses the connected shader.

- **All** — Used by all render engines.
- **Cycles** — Used only by Cycles.
- **EEVEE** — Used only by EEVEE.

Multiple Light Output nodes with different targets enable renderer-specific light setups.

### Outputs

None.

## Material Output Node

### Material Output Node

Output surface material information to a surface object.

### Inputs

- **Surface** — Surface shading.
- **Volume** — Interior shading.
- **Displacement** — Bump mapping or actual subdivided displacement.
- **Thickness** *(EEVEE)* — Approximate inner geometry structure without heavy computation. Used for Subsurface Scattering, Translucent BSDF, Refraction BSDF, and related effects. If unconnected, a default thickness based on the smallest object dimension applies. When connected, it's treated as object-space thickness (scaled by object transform). Zero disables thickness and treats the object as single-interface.

Used for: Subsurface Scattering, Translucent BSDF, Refraction BSDF effects.

Notes: Thickness skips the object interior; refraction won't refract objects within the thickness distance; shadow-casting objects won't cast shadows within the thickness distance.

Tips: For large/compound meshes (vegetation, hair), set thickness to individual part thickness (leaves, grass blades). Bake thickness to textures or custom attributes for accuracy.

See also: Thickness Mode controls thickness behavior.

### Properties

**Target** — Render engine for input shaders. Default: shaders shared between Cycles and EEVEE. Multiple output nodes enable engine-specific setups.

### Outputs

None.

## World Output Node

### World Output Node

Output color to the scene's World. Switch the Shader Editor header to World mode to access this node.

### Inputs

- **Surface** — Environment appearance. Usually connects to a Background shader.
- **Volume** — Volumetric world effects. See Principled Volume, Volume Absorption, Volume Scatter.

Note: Surface and Volume cannot coexist—surfaces sit at infinite distance, so they fully occlude volume.

### Properties

**Target** — Render engine for input shaders. Default: shaders shared between Cycles and EEVEE. Multiple output nodes enable engine-specific setups.

### Outputs

None.

## Add Shader

### Add Shader

Combine two shaders together.

### Inputs

- **Shaders** — Standard shader inputs.

### Properties

None.

### Outputs

- **Shader** — Standard shader output.

### Example

Glossy and diffuse shader mix creates a ceramic material.

## Background

### Background

Add background light emission. Use only with World Output Node.

### Inputs

- **Color** — Emitted light color.
- **Strength** — Emitted light strength.

### Properties

None.

### Outputs

- **Background** — Standard shader output.

## Diffuse BSDF

### Diffuse BSDF

Add Lambertian and Oren-Nayar diffuse reflection.

### Inputs

- **Color** — Surface color (physically: light reflection/transmission probability per wavelength).
- **Roughness** *(Cycles Only)* — Surface roughness. 0.0 gives Lambertian reflection; higher values activate Oren-Nayar.
- **Normal** — Shading normal. Defaults to standard shading normal when unconnected.

### Properties

None.

### Outputs

- **BSDF** — Standard shader output.

### Examples

Lambertian reflection. / Diffuse shader behavior. / Oren-Nayar reflection.

## Emission

### Emission

Add Lambertian emission for materials and light surfaces.

Light units: Point, spot, and area lights use Watts. Sun lights use Watts/m², requiring smaller values (e.g., 1 W/m²)—specifying Watts would be impractical (the sun is ~384.6×10²⁴ W). Mesh emissions also use Watts/m².

### Inputs

- **Color** — Emitted light color.
- **Strength** — Emitted light strength. For point/area lights: Watts. For materials: 1.0 makes the object display its exact Color input (shadeless).

### Properties

None.

### Outputs

- **Emission** — Can connect to Surface or Volume Input of Material Output node.

### Examples

Emission at strength 1.0. / Emission at strength 3.0.

## Glass BSDF

### Glass BSDF

Create glass-like shading by mixing refraction and reflection at grazing angles. Like transparent shaders, only pure white becomes transparent. Glass causes noise from caustics; combine with transparent shaders for shadows to improve results. See referenced details.

### Inputs

- **Color** — Surface color (physically: light transmission probability per wavelength).
- **Roughness** — Refraction sharpness. 0.0 is perfectly sharp; higher values smooth refraction.
- **IOR** — Index of refraction defining ray direction change. 1.0 passes rays straight (like transparent); higher values refract more.
- **Normal** — Shading normal.

### Thin Film *(Cycles Only)*

Simulate thin film interference effects that color specular reflection based on view angle, film thickness, and IOR of both film and material. Common in oil films, soap bubbles, and coatings. Affects transmission as well as reflections.

- **Thickness** — Film thickness in nanometers. 0 disables simulation. 100–1000 nm is strongest (visible light range).
- **IOR** — Film index of refraction (1.0–2.0 typical range). 1.33 approximates water. At 1.0 or matching main IOR, the film effect vanishes (optically blends in).

### Properties

**Distribution** — Microfacet model.

- **GGX** — GGX distribution.
- **Multiscatter GGX** — Accounts for multiple microfacet scattering. More energy-conservative; prevents excessive darkening.
- **Beckmann** *(Cycles Only)* — Beckmann distribution.

### Outputs

- **BSDF** — Standard shader output.

### Examples

Sharp Glass example. / Sharp Glass behavior. / Rough Glass example. / Rough Glass behavior.

## Glossy BSDF

### Glossy BSDF

Add microfacet-based reflection for metal and mirror-like surfaces.

### Inputs

- **Color** — Surface color (physically: light reflection probability per wavelength).
- **Roughness** — Reflection sharpness. 0.0 is perfectly sharp; higher values smooth reflection.
- **Anisotropy** *(Cycles Only)* — Stretch reflection along surface tangent. 0.0 = isotropic; higher values = elongated highlights perpendicular to tangent; negative values = highlights along tangent. Seen in metallic materials.
- **Rotation** — Rotate anisotropic tangent direction. 0.0 = 0°, 0.25 = 90°, 1.0 = 360°. Can be textured.
- **Normal** — Shading normal. Defaults to standard shading normal when unconnected.
- **Tangent** — Shading tangent. Defaults to standard shading tangent when unconnected.

### Properties

**Distribution** — Microfacet model.

- **GGX** — GGX distribution.
- **Multiscatter GGX** — Accounts for multiple microfacet scattering. More energy-conservative; prevents excessive darkening.
- **Beckmann** *(Cycles Only)* — Beckmann distribution.

### Outputs

- **BSDF** — Standard shader output.

### Examples

Sharp Glossy example. / Sharp Glossy behavior. / Rough Glossy example. / Rough Glossy behavior. / Anisotropic shading at 0°, 90°, and textured tangent rotation. Example blend-file.

## Hair BSDF

### Hair BSDF

*Cycles Only*

Add shading for hair.

### Inputs

- **Color** — Hair color.
- **Offset** — Angular light rotation for reflection/transmission.
- **Roughness U/V** — Roughness along light direction and perpendicular to it.
- **Tangent** — Input tangent.

### Properties

**Component** — Two selectable components (usually both via Mix Node).

- **Reflection** — Light bouncing off hair surface.
- **Transmission** — Light passing through and exiting the opposite side.

With Mix node: 0 = full Reflection, 1 = full Transmission.

### Outputs

- **BSDF** — Standard shader output.

## Principled Hair BSDF

### Principled Hair BSDF

*Cycles Only*

A physically-based, artist-friendly shader for hair and fur rendering.

Tip: Realistic hair requires minimal variance across strands. The shader supports this via Random Color and Random Roughness, remapping specified Melanin/Roughness to ±Randomization% range.

### Inputs

### Common

- **Color** — Strand RGB color (Direct coloring only). Converted to absorption via the formula (section 4.2 [CBTB16]): σₐ = ln(Color) / (5.969 − 0.215·β_N + 2.532·β_N² − 10.73·β_N³ + 5.574·β_N⁴ + 0.245·β_N⁵)², where β_N is the radial roughness of the hair after randomization (if specified).
- **Melanin** — Pigment quantity. Range [0, 1] = [0%, 100%]. Linear mapping: melanin_qty = -ln(max(1.0 - Melanin, 0.0001)).
- **Melanin Redness** — Pheomelanin/eumelanin ratio. Range [0, 1] = [0%, 100%]. Formula: eumelanin = Melanin×(1.0-MelaninRedness), pheomelanin = Melanin×MelaninRedness. Converted (after randomization, if specified) to absorption concentration via the formula (section 6.1 [EFHLA11], for the range [0, 1]): σₐ = eumelanin × [0.506, 0.841, 1.653] + pheomelanin × [0.343, 0.733, 1.924].
- **Tint** — Hair dye color after melanin pigment. Not randomized. Disable via white. Converted and added to melanin absorption.
- **Absorption Coefficient** — Attenuation coefficient σ.
- **IOR** — Index of refraction. 1.0 = transparent; higher = more refraction. Default 1.55.
- **Offset** — Cuticle scale angle relative to hair shaft. Humans typically have low values.
- **Random Color** — Per-strand melanin variance by RandomFactor. Range [0, 1] = [0%, 100%] of concentration. Formula: randomFactor = 1.0 + 2.0×(Random - 0.5) × RandomColor.
- **Random Roughness** — Per-strand roughness variance by RandomFactor. Range [0, 1]. Same formula as Random Color.
- **Random** — Random number source. Auto-instanced from Hair Info ‣ Random if unconnected.

### Chiang Model

Based on Gaussian distribution with separate roughness along and perpendicular to hair.

- **Roughness** — Smoothing along hair shaft. Low values risk metallic appearance and fireflies; high values risk Lambertian look.
- **Radial Roughness** — Smoothing across hair width. Low = concentrated glint; high = spread light. Mapped to logistic scale (section 4.1 [CBTB16]).
- **Coat** — Shiny fur coat reducing Roughness by this factor on first bounce. Range [0, 1] = [0%, 100%] reduction.

### Huang Model

Based on microfacet reflection/transmission; supports elliptical hair.

- **Aspect Ratio** — Minor/major axis ratio. 0.8–1 Asian; 0.65–0.9 Caucasian; 0.5–0.65 African. Major axis aligns with curve normal (geometry nodes; unsupported in legacy particles).
- **Roughness** — Microfacet roughness for reflection/transmission.
- **Reflection** — First-bounce modulation (always white). Keep 1.0 for physical accuracy.
- **Transmission** — Transmission modulation (picks up pigment color). Keep 1.0 for physical accuracy.
- **Secondary Reflection** — Transmitted-in, back-reflected, transmitted-out component (pigment color). Keep 1.0 for physical accuracy.

### Properties

**Color Parametrization** — Three coloring methods.

- **Direct Coloring** — Choose RGB; shader approximates absorption coefficient.
- **Melanin Concentration** — Define color via pigment quantity/ratio (eumelanin/pheomelanin). Quantity in Melanin; ratio in Melanin Redness. Increasing darkens hair: White (0), Blonde (0.25), Reddish (0.5), Brown (0.75), Black (1). Tint allows dyeing post-pigment.
- **Absorption Coefficient** — Specify attenuation σₐ via Beer-Lambert law. For technical users using literature coefficients without conversion.

### Principled Hair BSDF (continued)

### Outputs

- **BSDF** — Standard shader output.

### References

Implementation of Chiang et al. [CBTB16] and Huang et al. [HHH22].

[CBTB16] (1,2,3) Chiang, M. J., Bitterli, B., Tappan, C. and Burley, B. (2016), A Practical and Controllable Hair and Fur Model for Production Path Tracing. Computer Graphics Forum, 35: 275-283. doi:10.1111/cgf.12830

[EFHLA11] d'Eon, E., Francois, G., Hill, M., Letteri, J. and Aubry, J. (2011), An Energy‐Conserving Hair Reflectance Model. Computer Graphics Forum, 30: 1181-1187. doi:10.1111/j.1467-8659.2011.01976.x

[HHH22] Huang W., Hullin M.B., Hanika J. (2022), A Microfacet-based Hair Scattering Model. Computer Graphics Forum, 41: 79-91. doi:10.1111/cgf.14588

## Holdout

### Holdout

Create a "hole" in the image with zero alpha transparency for compositing work. See Alpha Channel.

### Inputs

None.

### Properties

None.

### Outputs

- **Holdout** — Standard shader output.

### Examples

Checkered region showing zero-alpha area.
