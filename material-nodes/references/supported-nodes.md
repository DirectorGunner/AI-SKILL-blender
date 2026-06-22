# Supported Nodes, Object Properties, Depth Of Field, Raytracing ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Supported Nodes; Object Properties; Depth of Field; Raytracing; Material Properties; Python Scripting; Render Properties; Freestyle.

## Supported Nodes

Supported Nodes — Node Compatibility

Most nodes originate from Cycles. Some functionality is absent and may or may not appear in EEVEE later.

See also
Shader Nodes.

### EEVEE only Nodes

These nodes only function when EEVEE is the active renderer and are incompatible with Cycles.

### Shader to RGB

EEVEE converts BSDF outputs to color values, enabling custom shading workflows. The Shader to RGB node handles this conversion by evaluating BSDFs similarly to blended materials and inheriting their constraints.

Transparent BSDF operates through the Shader to RGB pathway, granting access to the radiance behind objects according to material classification:

- Dithered material with Raytraced Transmission off samples the nearest light probe.
- Dithered material with Raytraced Transmission on displays other dithered materials without transmission, or falls back to the nearest probe.
- Blended material shows all dithered materials or falls back to the nearest probe.

### Specular BSDF

This node implements the specular workflow pattern found in other rendering systems.

### Other Nodes Support

Unlisted content is supported.

### Shader Nodes

Shader nodes generally behave as they do in Cycles. Consult the Cycles manual section on shading for details.

See also
Materials.

Most BSDFs are supported, though many are approximations lacking full feature parity.

Diffuse BSDF
Roughness is unavailable; only Lambertian diffusion is available.

Glass / Refraction BSDF
GGX and Multiscatter GGX distributions only.
Check Raytracing limitations.

Glossy BSDF
GGX and Multiscatter GGX distributions only.

Subsurface Scattering
Random Walk sampling, IOR, and Anisotropic modes are not available.

Transparent BSDF
Colored and additive transparency work only with blended render modes. When used with Shader to RGB, transparency can expose background radiance depending on material mode and ray-traced transmission settings.

Translucent BSDF
Does not diffuse light through the object; it lights the object with reversed normals.

Principled BSDF
Inherits limitations from Diffuse BSDF, Glossy BSDF, Refraction BSDF, and Subsurface Scattering. Anisotropy is unsupported. The Sheen layer is a crude approximation.

Volume Absorption
See Volume Limitation.

Volume Scatter
The anisotropy parameter is mixed and averaged across overlapping volumetric objects, which is non-physical and differs from Cycles.
Check Volume Limitation.

Principled Volume
Behaves as Volume Scatter; see Volume Limitation.

Holdout
Partially supported; dithered mode may produce wrong results.

Anisotropic BSDF
Unsupported.

Toon BSDF
Unsupported.

Hair BSDF
Unsupported.

Sheen BSDF
Unsupported.

Principled Hair BSDF
Unsupported.

### Input Nodes

Ambient Occlusion
The Only Local option is unavailable.

Geometry
Pointiness is unavailable.

Random per Island
This feature is unavailable.

Attribute
Defaults to the active UV layer. Only density, color, flame, and temperature built-in attributes are supported. UVs and Color Attributes work. Up to 8 Object or Instancer attributes per material (combined), and 512 View Layer attributes per scene.

Bevel
Unsupported.

Curves Info
The Random output employs a different RNG algorithm. Ranges and statistical patterns match, but values differ.

Light Path
EEVEE lacks true ray concepts. To ease Cycles-to-EEVEE workflow transitions, certain outputs are supported in limited cases.

- Is Camera: Supported.
- Is Shadow: Supported.
- Is Diffuse: Set to 1.0 when baking light probe volumes; otherwise 0.0.
- Is Glossy: Set to 1.0 when baking light probe spheres or planes; otherwise 0.0.
- Is Singular: Not supported. Same behavior as Is Glossy.
- Is Reflection: Not supported. Same behavior as Is Glossy.
- Is Transmission: Not supported. Same behavior as Is Glossy.
- Ray Length: Not supported. Defaults to 1.0.
- Ray Depth: Not supported. Defaults to 0.0.
- Diffuse Depth: Partially supported. Set to 1.0 when baking light probe volumes; otherwise 0.0.
- Glossy Depth: Partially supported. Set to 1.0 when baking light probe spheres or planes; otherwise 0.0.
- Transparent Depth: Not supported. Defaults to 0.
- Transmission Depth: Not supported. Same as Glossy Depth.

Note
Is Glossy does not work with Screen Space Reflections/Refractions but works with reflection planes.

Particle Info
Unsupported.

Texture Coordinate
From Instancer is not supported.

UV Map
From Instancer is not supported.

Wireframe
Pixel size output differs slightly from Cycles; line width may vary due to hardware rasterization.

### Texture Nodes

Most texture nodes are supported except as follows:

IES Texture
Unsupported.

Image Texture
Smart Interpolation always applies Cubic mode. Artifacts occur using Tube or Sphere projection with linear interpolation due to hardware mip-mapping and anisotropic filtering. Tube/Sphere artifacts also appear when texture coordinates lack continuity. Box projection with Clip or Extend modes is unsupported and reverts to Repeat.

Point Density
Unsupported.

Sky Texture
Nishita mode does not support the Sun Disc property.

### Other Nodes

Light Falloff
Unsupported.

## Object Properties

Object Properties — Display Control

### Shading

Reference
Panel: Properties ‣ Object Properties ‣ Shading

### Light Linking

Govern which objects receive light from a given source using Light Linking.

Receiver Collection
Objects in this collection will receive light emitted from the current object.

### Shadow Linking

Control shadow interaction via Light Linking.

Shadow Blocker Collection
Objects in this collection act as shadow blockers for the light emitted from the current object.

### Shadow Terminator

Shadow Terminator mitigates edge artifacts on low-poly or smooth-shaded geometry, especially with bump maps. Artifacts arise when shading normals diverge from geometry, creating visible shadow discontinuities.

Normal Offset
Shift shadow position along the shading normal to suppress artifacts. Offset is in object space and peaks at glancing light angles. Zero disables the bias. Increase if shadow breaks appear, but excessive values risk light leaks. The Geometry Offset controls how many faces the bias touches:

Geometry Offset
Adjust how many faces receive normal offset. Zero affects only grazing faces; 1.0 affects all faces. Higher values help if artifacts persist, though excessive offset distorts shadows, especially with bump mapping.

### Visibility

Reference
Panel: Object Properties ‣ Visibility

### Ray Visibility

Set objects invisible to particular ray types. Example: make emissive mesh invisible to camera rays. For instanced objects, visibility inherits from parents; hidden parent types hide children.

Using these options outperforms shader setups achieving the same result.

Camera
Object appears to the Camera, including viewport perspective in viewport rendering.

Shadow
Object casts shadows; it does not appear inside shadow maps.

### Light Probes

Control whether objects appear in light probe captures. Example: exclude animated objects from static probes. Instanced objects inherit parent visibility.

Volume
Object is visible during light probe volume baking.

Sphere
Object is visible during light probe sphere capture.

Plane
Object is visible during light probe plane capture.

## Depth of Field

Depth of Field — Focus and Blur

EEVEE renders with a pinhole camera model by default, which produces perfectly focused images. To simulate real camera optics, depth of field can be applied via post-process filtering and sample-based methods. Camera optical settings are in the camera properties; quality controls are here.

Note
Depth of field in the 3D Viewport only functions in Camera View.

The post-process method operates in two stages. Stage one uses a blur that works generally but produces poor bokeh on bright highlights. Stage two is sprite-based and enhances bright highlight quality. Sprites are too slow for full-image application; only bright isolated areas receive this treatment. Adjust affected pixels via Sprite Threshold and Neighbor Rejection.

The sample-based method randomizes camera position per sample. More accurate but requires many samples for smooth results. Post-process blur scales down to remove under-sampling artifacts. Some scenes may need extra post-process blur to hide sample patterns; the Overblur option increases blur radius while reducing bokeh sharpness.

Reference
Panel: Render ‣ Depth of Field

Max Size
Maximum depth of field post-process radius in pixels (lower is faster). Zero disables post-process but preserves sample-based method.

Sprite Threshold
Minimum pixel brightness for sprite-based depth of field consideration. Higher values improve performance but reduce highlight quality. Brightness is scene-referred.

Neighbor Rejection
Maximum intensity for sprite neighborhood evaluation. Set this to a brightness level above which visual differences are imperceptible after color management. Lower values improve performance but reduce highlight quality. Brightness is scene-referred.

Jitter Camera
Vary camera position per render sample to boost precision. This may alter actual sample count.

Note
Sample count can increase rapidly.

Hint
Sample count is calculated as:

[sample_count = (ring_count^2 + ring_count) * 3 + 1]

where (ring_count) is the hexaweb pattern ring count. The (ring_count) value ensures the entire pattern includes at least the configured Render Settings sample count.

Over-blur
Scale post-process depth of field radius to suppress artifacts. Higher values blur bokeh shape.

See also
Limitations.

## Raytracing

Raytracing — Indirect Surface Detail

Reference
Panel: Render ‣ Raytracing

Ray-tracing increases indirect surface lighting precision by generating rays from each BSDF and locating intersections individually.

When disabled, pre-filtered light-probes replace it, providing a faster, visually stable option when accuracy is secondary.

See also
Limitations.

Method
Select the intersection discovery technique.

Light Probe:
Use light-probe spheres and planes. Lowest tracing cost but requires manual probe placement.

Screen-Trace:
Trace rays against the screen depth buffer, falling back to light-probes if rays exit view.

Resolution
Ray-tracing resolution. Lower choices are faster, use less memory, but produce softer results.

### Screen Tracing

These settings govern screen-space ray behavior and only appear when Screen-Trace is active.

Precision
Higher values improve screen ray-tracing precision but reduce maximum trace distance. Increased precision raises performance cost.

Thickness
Pixel depth buffer thickness during tracing. Higher values stretch reflections and flicker. Lower values may cause rays to miss surfaces.

### Denoising

Enable denoising to reduce ray-traced output noise, improving stability but over-blurring output.

Spatial Reuse
Reuse neighbor pixel rays. May introduce light leaks across boundaries.

Temporal Accumulation
Re-project and accumulate prior ray tracing results. Removes fireflies but introduces color shift. Useful for viewport temporal stability or faster render convergence.

Bilateral Filter
Apply bilateral filtering to ray-traced output.

### Fast GI Approximation

Fast GI Approximation replaces ray-tracing for high-roughness BSDFs. Produces cleaner output and captures bounce lighting more efficiently than per-ray tracing.

This screen space effect inherits associated limitations.

Threshold
Highest BSDF roughness eligible for ray-tracing. Higher-roughness BSDFs progressively use Fast GI. A value of 1 ray-traces all surfaces, disabling Fast GI.

Method
Select the fast GI computation approach.

Ambient Occlusion:
Compute scene intersections to shadow distant light-probe lighting. Fastest option.

Global Illumination:
Calculate global illumination with light bouncing from surroundings.

Resolution
Fast GI computation resolution. Lower choices are faster, use less memory, but blur more.

Rays
GI rays per pixel at the chosen Resolution. Higher values reduce noise.

Steps
Screen samples per GI ray. Higher values reduce noise and boost quality.

Tip
Higher step counts decrease chances of missing light-bouncing surfaces. This allows Thickness parameters to use lower values without sacrificing light energy.

Precision
Higher values increase GI ray scene intersection precision. Increased precision raises performance cost.

Distance
If nonzero, the ceiling distance at which other surfaces contribute to fast GI. Objects farther away do not contribute.

Thickness Near
Geometric surface thickness for fast GI and ambient occlusion. Reduces light leaking and missing contact shadows. Effectiveness diminishes with distance, following inverse square rules.

Far
Angular surface thickness for fast GI and ambient occlusion. Reduces energy loss and missing occlusion of distant geometry. Higher values cause thin objects to block or reflect excess light.

Bias
Adjust shading normal to mitigate self-intersection artifacts.

## Material Properties

Material Properties — Line Color Control

Reference
Panel: Properties ‣ Material ‣ Freestyle Line

Line Color
Specify line colors per-material basis.

Priority
Order competing line colors at material boundaries.

See also
A Freestyle development blog article details a practical line color priority use case.

## Python Scripting

Python Scripting — Programmable Style Modules

The Python Scripting mode provides full scriptable line stylization. Styling operations are Python scripts called style modules. A style module receives a view map (detected feature edges) and outputs stylized strokes.

A style module chains five basic operators: selection, chaining, splitting, sorting, and stroke creation. Selection identifies a subset based on predicates. Chaining processes selected edges using predicates and functions to construct chains. Splitting and sorting refine chains. Stroke creation applies stroke shaders to build output strokes.

Python style modules are text data-blocks within blend-files. External modules load in the Text Editor first. A style module stack selector allows choosing from loaded modules.

Blender supplies Python style modules serving as starting references. Consult the Freestyle Python API in the Blender Python API reference for complete style module details.

| By T.K. using the Python Scripting mode (blend-file, CC0). | By T.K. using the Python Scripting mode (blend-file, CC0). |

### Writing Style Modules

A style module stylizes Freestyle line output. Input is a view map (set of feature edges); output is stylized strokes. A style module forms a pipeline of operations transforming input edges into output strokes.

Five operation types exist (with corresponding operator functions):

- Selection Operators.select()
- Chaining Operators.chain(), Operators.bidirectional_chain()
- Splitting Operators.sequential_split(), Operators.recursive_split()
- Sorting Operators.sort()
- Stroke creation Operators.create()

The input view map contains ViewEdge objects. Selection identifies ViewEdges of interest using predicates. Chaining constructs Chains by joining ViewEdges per user predicates and functions. Chains undergo further refinement via splitting and sorting. Finally, stroke creation transforms chains into strokes via stroke shaders.

ViewEdges, Chains, and Strokes constitute one-dimensional (1D) elements. A 1D element is a polyline of connected straight lines. Polyline vertices are called 0D elements.

All operators work on active 1D element sets. Initial active set contains input view map ViewEdges. Operators update the active set.

### Selection

Selection examines every active set element, retaining only those matching a predicate. Operators.select() takes a unary predicate operating on any Interface1D representing a 1D element. Example:

Operators.select(QuantitativeInvisibilityUP1D(0))

This selects visible ViewEdges (quantitative invisibility equals 0). Selection limits styling to a fraction of active 1D elements.

QuantitativeInvisibilityUP1D is a predicate class, and Operators.select() receives an instance. The predicate evaluation invokes the __call__ method. Operators.select() takes a functor taking Interface0D arguments. Freestyle Python API employs functors extensively for predicates and functions.

### Chaining

Chaining operators work on active ViewEdge sets, determining future stroke topology. Chaining implements an iterator traversing the ViewMap graph along ViewEdges. The iterator sets a chaining rule dictating the next ViewEdge at a given vertex. Several iterators ship with Freestyle Python API; custom ones inherit ViewEdgeIterator. Chaining operators take a UnaryPredicate on Interface1D as stopping criteria. Chaining halts when reaching a ViewEdge satisfying this predicate.

Chaining is unidirectional Operators.chain() or bidirectional Operators.bidirectional_chain(). Bidirectional chaining propagates in both directions from the starting edge.

Example bidirectional chaining:

Operators.bidirectional_chain(
ChainSilhouetteIterator(),
NotUP1D(QuantitativeInvisibilityUP1D(0)),
)

This uses ChainSilhouetteIterator for chaining and stops at invisible ViewEdges.

Chaining processes active ViewEdges sequentially. Previously sorted ViewEdges via Operators.sort() can control this order. It starts a chain with the first ViewEdge. Processed ViewEdges are marked (timestamp modification) to avoid reprocessing. When chaining hits a stopping predicate, the chain ends. A new chain begins from the first unmarked ViewEdge. This repeats until all unmarked ViewEdges finish processing. Post-chaining, the active set contains the new Chains.

Python Scripting — Splitting, Sorting, and Stroke Creation (continued)

### Splitting

Splitting refines Chain topology. Operators.sequentialSplit() parses the Chain at arbitrary resolution, evaluating a unary predicate at each point. When satisfied, the chain splits. Sequential splitting results become the new active set.

Operators.sequentialSplit(TrueUP0D(), 2)

This splits the chain every 2 units. An advanced version uses two predicates: one for new chain start, another for end. This produces disjoint or overlapping chains if predicates differ.

Operators.recursiveSplit() evaluates a function on 0D elements at given resolution, finding the maximum value point. The Chain splits there and repeats recursively on each segment until stopping conditions are met.

func = Curvature2DAngleF0D()
Operators.recursive_split(func, NotUP1D(HigherLengthUP1D(5)), 5)

This recursively splits Chains at highest 2D curvature points, with 5-unit resolution. Chains under 5 units avoid further splitting.

### Sorting

Operators.sort() arranges active 1D element stacking. It takes a binary predicate as a "smaller than" operator.

Operators.sort(Length2DBP1D())

This sorts Interface1D objects by ascending 2D length. Sorting pairs well with causal density. Causal density evaluates image density during rendering. To remove strokes when local density exceeds limits, control drawing order. Use sorting to draw "important" lines first.

### Stroke Creation

Operators.create() transforms active Chains into Strokes. It takes two arguments: a unary predicate on Interface1D for final chain selection, and a shader list for stroke rendering.

shaders_list = [
SamplingShader(5.0),
ConstantThicknessShader(2),
ConstantColorShader(0.2,0.2,0.2,1),
]
Operators.create(DensityUP1D(8,0.1, IntegrationType.MEAN), shaders_list)

This removes chains exceeding 0.1 mean density via DensityUP1D. Each chain becomes a stroke resampled every 5 units with 2-unit thickness and dark gray color.

### User Control on the Pipeline Definition

Style module writing permits different control types despite fixed module structure. One method: sequence different pipeline structures. Another: define functors passed throughout.

Different structures combine selection, chaining, splitting, and sorting steps. Stroke creation concludes every module.

Predicates, functions, chaining iterators, and stroke shaders inherit base classes and override methods. Reference manual entries for these base classes provide scriptable construct details.

See also
Predicates, functions, chaining iterators, and stroke shaders inherit base classes and override methods. Consult Freestyle python module for complete user-scriptable construct information.

## Render Properties

Render Properties — Freestyle Setup

Reference
Panel: Properties ‣ Render ‣ Freestyle

Activate Freestyle via the checkbox in the Freestyle panel header in the Render tab.

Freestyle Render Properties.

Line Thickness Mode
Establish the base line thickness method:

Absolute:
Line thickness is pixels.

Relative:
Unit line thickness scales to the vertical image resolution ratio to 480 pixels. Example: 1.0 at 480px, 1.5 at 720px, 2.0 at 960px.

Line Thickness
Rendering line thickness (Absolute line thickness mode only).

## Freestyle

Freestyle — View Map Configuration

Reference
Panel: Properties ‣ View Layer ‣ Freestyle

Each view layer has one view map governing edge detection. Freestyle toggles per-View Layer via panel header checkbox.

View Layer: Freestyle panel.

Control Mode
Select how detected edges render and how they appear:

Parameter Editor Mode:
Define Line Sets and line styles through a user interface.

A view map can include multiple Line Sets, each linked to one line style.

Python Scripting Mode:
Lines render via Python scripting—powerful yet complex.

View Map Cache
Reuse a previously computed view map for subsequent renders. Auto-updates when mesh geometry changes.

Offers major performance gains for Freestyle animation when camera-space geometry is static or when repeatedly rendering with stylization-only updates.

Though view layer-specific, cache memory is shared across all layers and scenes. Using Freestyle on multiple layers (possibly across scenes via Compositor) means one cache replaces another, negating gains.

As Render Pass
Freestyle lines do not overlay immediately. Instead, render as a Render Pass compositable with the image via Alpha Over node.

### Edge Detection

Crease Angle
When adjacent faces form an angle smaller than Crease Angle, the edge renders via Crease edge type in a line set. Affects Silhouette edge type selection.

Culling
Discard out-of-view edges. Saves processing and memory but may degrade result quality.

Face Smoothness
Incorporate Smooth Shading into edge calculations.

Sphere Radius
Impact on curvature calculation for Ridge, Valley, and Suggestive Contour edge type selection. Vertex curvature is computed by averaging surface shape within the specified radius. Higher values reduce noise and detail.

Kr Derivative Epsilon
Threshold controlling minimum curvature change rate filtering for Suggestive Contour edge type output. Higher values reduce rendered lines, starting with smoother object areas.
