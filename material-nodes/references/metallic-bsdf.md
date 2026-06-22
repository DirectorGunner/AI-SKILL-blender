# Metallic Bsdf, Mix Shader, Principled Bsdf, Ray Portal Bsdf ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Metallic BSDF; Mix Shader; Principled BSDF; Ray Portal BSDF; Refraction BSDF; Sheen BSDF; Specular BSDF; Subsurface Scattering; Toon BSDF; Translucent BSDF; Transparent BSDF; Volume Absorption; Volume Coefficients.

## Metallic BSDF

### Metallic BSDF

Recreate metal appearance.

### Inputs

### F82 Tint

- **Base Color** — Material color at normal viewing angle.
- **Edge Tint** — Material color at 82° viewing angle.

### Physical Conductor

- **IOR** — Refractive index per channel (real part of complex IOR, denoted n).
- **Extinction** — Extinction coefficients per channel (imaginary part, denoted k).

### Common

- **Roughness** — Reflection sharpness. 0.0 = perfectly sharp; higher = smoother.
- **Anisotropy** *(Cycles Only)* — Anisotropy amount. Higher = elongated highlights along tangent; negative = perpendicular highlights.
- **Rotation** *(Cycles Only)* — Anisotropy direction rotation (1.0 = full circle). Note: 90° offset vs Glossy BSDF; add 0.25 to correct.
- **Normal** — Shading normal. Defaults to standard when unconnected.
- **Tangent** — Shading tangent. Defaults to standard when unconnected.

### Properties

**Distribution** — Microfacet model.

- **GGX** — GGX distribution.
- **Multiscatter GGX** — Multiple microfacet scattering; more energy-conservative.
- **Beckmann** *(Cycles Only)* — Beckmann distribution.

**Fresnel Type** — Models for material appearance via color or physical IOR.

- **F82 Tint** — Adobe F82-Tint formula for edge color via complex IOR simulation.
- **Physical Conductor** — Complex IOR from real-world metals. Sources: Physically Based database and Refractive Index nk database.

### Outputs

- **BSDF** — Standard shader output.

### Examples

### F82 Tint

| Material | Titanium (Default) | Aluminum | Copper | Gold |
| Base Color | 0.617, 0.576, 0.540 | 0.911, 0.912, 0.917 | 0.972, 0.694, 0.486 | 1.000, 0.735, 0.353 |
| Edge Tint | 0.695, 0.726, 0.770 | 0.848, 0.877, 0.916 | 0.961, 0.969, 0.942 | 0.993, 1.000, 1.000 |

### Physical Conductor

| Material | Titanium (Default) | Aluminum | Copper | Gold |
| IOR | 2.757, 2.512, 2.231 | 1.333, 0.945, 0.582 | 0.235, 0.729, 1.369 | 0.000, 0.470, 1.439 |
| Extinction | 3.867, 3.404, 3.009 | 7.434, 6.340, 5.181 | 5.666, 2.562, 2.227 | 182.6, 2.189, 1.660 |

## Mix Shader

### Mix Shader

Combine two shaders via blending. Useful for layering, where Factor input (e.g., Blend Weight node) controls mixing.

### Inputs

- **Shader** — Shaders to mix. Incoming rays strike either with the specified Factor probability.
- **Factor** — Blend weight. 0 = first shader; 1 = second shader.

### Properties

None.

### Outputs

- **Shader** — Standard shader output.

### Examples

Glossy and diffuse shader mix creates a ceramic material.

## Principled BSDF

### Principled BSDF

A unified node combining multiple layers for versatile material modeling. Based on OpenPBR Surface, compatible with Disney and Standard Surface from other software. Substance Painter textures map directly to inputs.

### Layers

The base layer mixes metal, diffuse, subsurface, and transmission. Most use one, though smooth mixing is possible. Metal is opaque reflection-only. Diffuse is fully opaque; subsurface adds below-surface scattering. Both sit below a specular layer. Transmission includes reflection and refraction. An optional glossy coat sits atop all layers. Sheen (fuzz/dust) sits on top. Light emits from below coat/sheen layers (e.g., emissive displays with coatings).

### Inputs

- **Base Color** — Material color for diffuse, subsurface, metal, transmission.
- **Roughness** — Surface microfacet roughness for specular reflection/transmission. 0.0 = sharp; 1.0 = diffuse.
- **Metallic** — Dielectric/metallic blend. 0.0 = diffuse/transmissive base with specular layer; 1.0 = specular reflection (base color tinted, no diffuse/transmission).
- **IOR** — Index of refraction. 1.0–4.0 typical. 1.5 approximates glass.
- **Alpha** — Surface transparency. 1.0 = fully opaque. Usually linked to Image Texture Alpha output.
- **Normal** — Base layer normals.

### Diffuse

- **Roughness** *(Cycles Only)* — Surface roughness. 0.0 = Lambertian; higher = Oren-Nayar.

### Subsurface

For skin, milk, wax; light scatters below surface for soft appearance.

- **Method** — Subsurface scattering simulation method.
  - **Christensen-Burley** — Approximate physically-based volume scattering. Faster convergence but less accurate than Random Walk.
  - **Random Walk** *(Cycles Only)* — True volumetric scattering. Best for closed meshes; thin/curved objects. Overlapping faces/holes cause problems.
  - **Random Walk (Skin)** *(Cycles Only)* — Optimized for skin. Auto-adjusts radius by color texture; mixes diffuse/specular transmission with custom IOR. Retains surface detail and matches measured skin.
- **Weight** — Diffuse/subsurface blend. Usually 0 or 1.
- **Radius** — Light scattering distance below surface. Higher = softer (light bleeds through). Per-RGB for materials like skin (red scatters deeper).
- **Scale** — Radius scale (0–50 cm).
- **IOR** *(Cycles Only)* — Subsurface component IOR (may differ from global IOR for skin layers).
- **Anisotropy** *(Cycles Only)* — Volumetric scattering directionality. 0 = uniform; higher = forward-scattering. Skin ≈ 0.8.

### Specular

Controls metallic and specular-layer reflection over diffuse/subsurface.

- **Distribution** — Microfacet model.
  - **GGX** — Faster than multiscatter; less physically accurate.
  - **Multiscatter GGX** — Multiple microfacet events; more energy-conserving (prevents excessive darkening).
- **IOR Level** — IOR adjustment to increase/decrease specular intensity. 0.5 = no adjustment; 0 = no reflections; 1 = double at normal incidence. Designed for easy IOR texturing.
- **Tint** — Specular/metallic reflection color tint. Non-metallic: artistic control of normal-incidence color (grazing stays white—physically correct). Metallic: edge tint simulating complex IOR (gold, copper).
- **Anisotropic** *(Cycles Only)* — Specular anisotropy. Higher = elongated highlights along tangent; negative = perpendicular.
- **Anisotropic Rotation** *(Cycles Only)* — Anisotropy direction rotation (1.0 = full circle). Note: 90° offset vs Glossy BSDF; add 0.25 to correct.
- **Tangent** — Anisotropy tangent direction.

### Transmission

For glass and liquids; surface reflects and transmits.

- **Weight** — 0 = fully opaque; 1 = fully transmissive.

### Coat

Clearcoat, lacquer, or car paint simulation.

- **Weight** — Coat layer intensity (reflection and tinting). Usually 0 or 1 for physical accuracy; may texture for variation.
- **Roughness** — Coat layer roughness.
- **IOR** — Coat IOR. Affects reflectivity and tinting falloff.
- **Tint** — Coat color tint via absorption modeling. Saturation increases at shallow angles (light travels farther through medium per IOR).
- **Normal** — Coat layer normals (e.g., smooth coating over rough surface).

### Sheen

Small surface fibers; cloth adds soft velvet-like edge reflection. Simulates dust on any material.

- **Weight** — Sheen layer intensity.
- **Roughness** — Sheen reflection roughness.
- **Tint** — Sheen reflection color.

### Emission

Surface light emission.

- **Color** — Emission color.
- **Strength** — Emission intensity. 1.0 makes object display exact Emission Color (shadeless).

### Thin Film *(Cycles Only)*

Thin film interference; specular reflection becomes color-dependent on view angle, film thickness, and IOR of film and material. Common in oils, soaps, coatings; affects transmission too.

- **Thickness** — Film thickness nanometers. 0 = disabled. 100–1000 nm = strongest (visible light range).
- **IOR** — Film IOR (1.0–2.0 typical). 1.33 approximates water. At 1.0 or matching main IOR, effect vanishes (optically blends in).

### Outputs

- **BSDF** — Standard shader output.

Anisotropic rotation runs from 0.0 to 1.0.
Tangent — controls the tangent direction for anisotropy.

Transmission — used to render materials like glass and liquids, where the surface both reflects light and transmits it into the object's interior.
Weight — mix between a fully opaque surface at zero and fully transmissive at one.

Coat — a coat on top of the material, to simulate for example a clearcoat, lacquer, or car paint.
Weight — the coat layer's intensity, both reflection and tinting; typically zero or one for physically-based materials, but it can be textured to vary the amount of coating across the surface.
Roughness — the roughness of the coat layer.
IOR — index of refraction (IOR) of the coat layer, affecting its reflectivity as well as the falloff of coat tinting (from 1.0 to 2.0).
Tint — adds a colored tint to the coat layer by modeling absorption in the layer; saturation increases at shallower angles, as the light travels farther through the medium, depending on the IOR (from white to blue).
Normal — controls the normals of the Coat layer, for example to add a smooth coating on a rough surface.

Sheen — simulates very small fibers on the surface; for cloth this adds a soft velvet-like reflection near edges, and it can also simulate dust on arbitrary materials.
Weight — the intensity of the sheen layer.
Roughness — the roughness of the sheen reflection.
Tint — the color of the sheen reflection (from white to green).

Emission — light emission from the surface.
Color — the color of light emission from the surface.
Strength — the strength of the emitted light; a value of 1.0 makes the object in the image the exact same color as the Emission Color, i.e. "shadeless" (from 0.0 to 10.0).

Thin Film (Cycles Only) — simulates the effect of interference in a thin film sitting on top of the material, coloring the specular reflection in a way that strongly depends on the view angle as well as the film thickness and the index of refraction (IOR) of both the film and the material; commonly seen on e.g. oil films, soap bubbles, or glass coatings, and while its influence is most obvious in specular highlights, it also affects transmission.
Thickness — the film thickness in nanometers; a value of 0 disables the simulation, and the interference effect is strongest roughly between 100 and 1000 nanometers, near the wavelengths of visible light (illustrated from 400 to 800 nanometers).
IOR — index of refraction (IOR) of the thin film; the common range is between 1.0 (vacuum and air) and roughly 2.0, though some materials reach higher, and the default 1.33 is a good approximation for water — note that setting it to 1.0 or to the material's main IOR makes the thin-film effect disappear, since the film optically blends into the air or the material (illustrated from 1.0 to 1.5).

Outputs:
BSDF — standard shader output.

## Ray Portal BSDF

### Ray Portal BSDF

Cycles Only

This node teleports any ray that strikes it to a separate spot in the scene. Artists reach for it when building portal effects and similar specialized rendering tricks.

Its behaviour echoes that of a Transparent BSDF: render passes carry through untouched, and the cap on transparent bounces in the light-path settings still governs it.

Note

- A single portal moves rays only one way. To let them travel back as well, drop a matching portal at the spot they arrive.

- Sampling lights across a portal is not efficient, so light coming from the far side tends to look noisy. Small lamps in particular can be extremely grainy, or may never come through.

### Inputs

Color
Tints whatever rays cross the portal.

Position
Where the ray restarts on the far side. Left alone, it stays at the current spot, which equals the Position output of the
Geometry node.

Direction
Which way the ray heads on the far side. Left alone, it keeps the current viewing line, equal to the negated Incoming output of the
Geometry node.

### Properties

This node has no properties.

### Outputs

BSDF
Standard shader output.

### Examples

A typical job for this node is stitching two areas together so you get a gateway into another dimension, or "impossible spaces" whose inside is larger or smaller than the outside suggests.

Wiring it up for a trick like that means reworking the Position and Incoming outputs of the
Geometry node so they set the exit point and heading of the ray as it leaves. A few setups follow:

### Simple Offset

A bare-bones graph that just nudges the exit position. Here the ray moves 0 units on X, 4 on Y, and 5 on Z.

### Portal

Here the Location of Portal Target and Rotation of Portal Target vectors come from a target portal object by way of
Drivers.

### Camera Feed

Beyond tweaking rays, you can swap the position and heading outright, which yields tricks such as a live camera image shown on a surface.

Using the Ray Portal BSDF to reproduce a camera-feed look on a screen.

Node setup for reproducing a camera-feed style effect on a screen.

## Refraction BSDF

### Refraction BSDF

Sharp or microfacet-distributed glossy refraction comes from the Refraction BSDF, meant for matter that lets light pass through. Treat it as a component rather than a standalone shader; on its own it darkens the edges of glossy refraction, so blend it with a glossy node through a Fresnel factor for good results.

### Inputs

Color
Surface tint, or in physics terms, the per-wavelength chance that light is refracted.

Roughness
Sets how crisp the refraction looks: dead sharp at 0.0, and progressively blurrier as the number climbs.

Normal
Shading normal; leaving it unconnected falls back to the geometry's default shading normal.

### Properties

Distribution
Microfacet distribution to use.

GGX :

GGX microfacet distribution.

Beckmann :

Cycles Only
Beckmann microfacet distribution.

### Outputs

BSDF
Standard shader output.

### Examples

Refraction Shader.

## Sheen BSDF

### Sheen BSDF

Cycles Only

The Sheen BSDF adds a reflective response to surfaces carrying fine microscopic structure, such as cloth or a coating of dust. It is built to sit as a layer over another shader, for instance a dielectric or metallic base.

### Inputs

Color
Surface tint, or in physics terms, the per-wavelength chance that light bounces back.

Roughness
Tunes how much colour returns toward the camera: raise it for more colour and a dusty look, lower it for a softer, darker, fuzzier appearance.

Normal
Shading normal; leaving it unconnected falls back to the geometry's default shading normal.

### Properties

Distribution
Sheen shading model.

Ashikhmin :

Classic Ashikhmin velvet, used in Blender versions prior to 4.0

Microfiber :

Microflake-based model of multiple scattering between normal-oriented fibers.

### Outputs

BSDF
Standard shader output.

### Examples

| The Sheen shader example. | The Sheen shader behavior. |

## Specular BSDF

### Specular BSDF

EEVEE Only

The Specular BSDF folds several layers together behind one convenient node.

Think of it as a cousin of the Principled BSDF node that follows the specular workflow rather than the metallic one. It carries far fewer settings and covers fewer features; the two may eventually be folded into a single node.

Under the specular workflow you state the reflection colour seen face-on, along the normal. Because nothing enforces energy conservation, the result need not be physically plausible.

### Inputs

Base Color
Diffuse surface colour. Set it to black for conductors (metals).

Specular
How much specular reflection there is, given as the face-on (along-normal) reflectivity. Conductors (metals) may carry a coloured specular reflection.

Hint

To work this figure out for a real material whose index of refraction you know, use this special case of the Fresnel formula:
\(specular = ((ior - 1)/(ior + 1))^2\)

For example:

- water: ior = 1.33, specular = 0.02

- glass: ior = 1.5, specular = 0.04

- diamond: ior = 2.417, specular = 0.17

Roughness
Sets the microfacet roughness of the surface, covering both diffuse and specular reflection.

Hint

Coming from the older Glossy BSDF node, take the square root of the value you had there.

Emissive Color
Colour of the light given off. It is summed onto the BSDF result.

Transparency
A transparency factor, which is just the alpha channel inverted (1 - alpha) as found in an image. Run an Invert node to turn alpha into transparency. It only does anything when the material's blend mode is something other than opaque.

Normal
Drives the normals of the base layers.

Clear Coat
An additional white specular layer laid over the rest, handy for finishes such as car paint.

Clear Coat Roughness:
Roughness of clear coat specular.

Clear Coat Normal
Drives the normals of the Clear Coat layer.

Ambient Occlusion
How much occlusion to lay over indirect lighting, normally fed by a baked ambient occlusion map. The occlusion actually applied is whichever is smaller, this input or the runtime ambient occlusion effect.

### Properties

This node has no properties.

### Outputs

BSDF
Standard shader output.

## Subsurface Scattering

### Subsurface Scattering

This node supplies a basic form of subsurface multiple scattering, which suits skin, wax, marble, milk and the like. With these materials light does not simply reflect off the surface; it sinks in, bounces around inside, and is either absorbed or exits again a short distance away.

You can set the average travel distance of each colour channel on its own. Skin, for instance, lets red travel furthest, which is what gives it those characteristic reddish shadows and its soft look.

### Inputs

Color
Surface tint, or in physics terms, the per-wavelength chance that light bounces back.

Scale
Overall multiplier on the scattering radius.

Radius
Mean depth light reaches under the surface. A larger figure softens the look as light seeps into shadow and across the object. Each of the R, G and B channels gets its own scattering distance, which lets you render things like skin where red travels deeper. The three vector components feed the R, G and B channels in order.

IOR Cycles Only
Index of refraction for Subsurface Scattering .

Anisotropy Cycles Only
Directionality of subsurface scattering. Higher anisotropy scatters deeper into the object.

Roughness Cycles Only
Roughness of the glossy shell wrapping the subsurface volume.

Normal
Shading normal; leaving it unconnected falls back to the geometry's default shading normal.

### Properties

Subsurface Method
Rendering method to simulate subsurface scattering.

Note

EEVEE does not support the Random Walk methods.

Christensen-Burley :

A physically based volume-scattering approximation. It is less accurate than Random Walk, though in certain scenes it clears noise sooner.

Random Walk (Fixed Radius) :

Gives accurate results on thin, curved objects. Because Random Walk does real volumetric scattering inside the mesh, it suits closed meshes best; holes and overlapping faces can trip it up.

Random Walk :

Works much like Random Walk (Fixed Radius) but adjusts the Radius from the Color , Anisotropy , and IOR . That way it aims to hold on to more surface detail and colour than Random Walk (Fixed Radius) does.

### Outputs

BSSRDF
BSSRDF shader output.

### Examples

Random walk subsurface scattering.

## Toon BSDF

### Toon BSDF

Cycles Only

The Toon BSDF builds Diffuse and Glossy materials that carry a stylized, cartoon-style lighting response.

### Inputs

Color
Surface tint, or in physics terms, the per-wavelength chance that light bounces back.

Size
A figure from 0.0 to 1.0 that maps to a reflection angle from 0° to 90°.

Smooth
The angular span over which reflection eases from full down to nothing.

Normal
Shading normal; leaving it unconnected falls back to the geometry's default shading normal.

### Properties

Component
Which material component the toon effect builds on.

Diffuse :

Use shading based on the Diffuse BSDF.

Glossy :

Use shading based on the Glossy BSDF for specular reflection.

### Outputs

BSDF
Standard shader output.

### Examples

Example of Toon Shader.

## Translucent BSDF

### Translucent BSDF

Lambertian diffuse transmission is what the Translucent BSDF contributes.

### Inputs

Color
Surface tint, or in physics terms, the per-wavelength chance that light passes through.

Normal
Shading normal; leaving it unconnected falls back to the geometry's default shading normal.

### Properties

This node has no properties.

### Outputs

BSDF
Standard shader output.

### Examples

| Translucent shader example. | Translucent shader behavior. |

## Transparent BSDF

### Transparent BSDF

The Transparent BSDF grants transparency with no refraction: light goes straight on as though no surface were present, which makes it handy with alpha maps. It treats light paths somewhat unlike the other BSDFs. Bear in mind that only a pure-white transparent shader is fully see-through.

### Inputs

Color
Surface tint, or in physics terms, the per-wavelength chance that light is either stopped or carries straight on through the surface.

### Properties

This node has no properties.

### Outputs

BSDF
Standard shader output.

### Examples

| Transparent shader (pure white). | Transparent shader behavior. |
| Transparent shader (gray). | |

## Volume Absorption

### Volume Absorption

This node lets a volume soak up light as it travels through. You would typically use it for water and tinted glass.

### Inputs

Color
Colour of the volume.

Density
How strong the absorption effect is.

### Properties

This node has no properties.

### Outputs

Volume
Feed the Volume Shader result to the Volume Input on either the Material or World Output node.

### Examples

Example of Volume Absorption.

## Volume Coefficients

### Volume Coefficients

This node captures three physical effects inside a volume — absorption, scattering and emission — each via its coefficient. The usual approach is to feed it numbers taken from real-world measurements.

### Inputs

### Absorption

Coefficients
Per-channel probability density that light is absorbed over each unit of distance through the medium. This equals \((1-\text{Color}) \times \text{Density}\) in
Volume Absorption.

### Scatter

Coefficients
Per-channel probability density of an out-scattering event over each unit of distance through the medium. This equals \(\text{Color} \times \text{Density}\) in
Volume Scatter.

Anisotropy Henyey-Greenstein Draine
Sets the balance between back- and forward-scattering.

IOR Fournier-Forand
Index of refraction of the scattering particles relative to water. Ordinary ocean water sits between 1.0 and 1.2, while denser, murkier water climbs higher.

Backscatter Fournier-Forand
Share of light thrown back the way it came. Most ocean particles fall between 0.001 (such as very large phytoplankton) and 0.1 (such as very small mineral grains); pure water sits at 0.5. Figures from
Ocean Optics Web Book.

Alpha Draine
A blend control between the Henyey-Greenstein ( \(\alpha = 0\) ) and Cornette & Shanks ( \(\alpha = 1\) ) phase functions.

Diameter Mie
Diameter of the scattering particles in µm.

Note

The inputs above match those in Volume Scatter.

### Emission

Coefficients
Per-channel radiance added onto a ray over each unit of distance. This equals \(\text{Color} \times \text{Strength}\) in Emission.

### Properties

Phase

Note

Same as Phase in Volume Scatter.

Volume scattering phase function.

Henyey-Greenstein :

A simple, widely used phase function, handy for roughly modelling scattering inside biological tissue.

Fournier-Forand :

Cycles Only
Aimed at modelling how light scatters underwater.

Draine :

Cycles Only
Aimed at modelling how interstellar dust scatters.

Rayleigh :

Cycles Only
Covers scattering by particles smaller than light's wavelength, like sunlight scattering through Earth's atmosphere.

Mie :

Cycles Only
Covers scattering by particles larger than light's wavelength, like cloud and fog.

### Outputs

Volume
Feed the Volume Shader result to the Volume Input on either the Material or World Output node.
