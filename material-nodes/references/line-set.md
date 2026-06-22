# Line Set, Alpha, Material, Strokes ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Line Set; Alpha; Material; Strokes; Thickness; Filter; View Layer Override; Passes.

## Line Set

Line Set — Edge and Feature Selection

Reference
Panel: Properties ‣ View Layer ‣ Freestyle Line Set

A line set selects which detected Freestyle edges render using its attached line style through various selection methods.

Freestyle Line Set panel.

Select By

Image Border
Restrict Freestyle calculation to in-view geometry. Reduces render time but increases continuity problems when geometry moves in/out of view.

### Visibility

Type
Determine visibility usage for feature edge selection.

Visible:
Only unoccluded lines render.

Hidden:
Lines occluded by at least one surface render.

Proof of concept of visible and hidden edges by LightBWK
(blend-file).

Quantitative Invisibility:
Lines occluded by a surface range render.

Start, End
Occluding surface count bounds for line rendering.

QI Range proof of concept demo, Start: 3, End: 7, by LightBWK
(blend-file).

### Edge Types

Edge type selection algorithms identify lines from geometry. Parameter editor use requires minimum one edge type for output, but multiple types combine in one line set. Press X beside types to exclude them from calculation.

Examples of some basic edge types:
Silhouette (green), Crease (black), Border (blue) and Edge Marks (red)
(blend-file by LightBWK).

Type

Silhouette
Outline closed objects by rendering where surface normals transition from camera-facing to away. Works well for organic objects (e.g., Suzanne), poorly for sharp edges (e.g., boxes). Cannot render open meshes like open cylinders and planes.

Crease
Show edges whose adjacent faces form angles sharper than the view map's Crease Angle.

Crease Angle proof of concept for 121° by LightBWK
(blend-file).

Border
Display open mesh edges—edges belonging to one face only. Open cylinders have border edges at top/bottom; planes border all around. Suzanne's eye socket is border.

Edge Mark
Render marked edges. See Edge Marks for details.

Contour
Outline each object, separating from objects behind or the background.

External Contour
Outline all objects, separating from background only, not each other.

Left pair: Contour; Right pair: External Contour.

Material Boundary
Draw where two materials meet on an object.

Suggestive Contour
Draw lines that would form the Silhouette if viewing direction shifted. Depends on view map Kr Derivative Epsilon and Sphere Radius settings.

Ridge & Valley
Mark surface crests and troughs—ridges and valleys where curvature peaks. Depends on Sphere Radius.

### Edge Marks

In Edit Mode, mark "Freestyle Edges" like Seams or Sharp edges. Marked edges render via Edge Mark selection.

Internally, edge marks store as the freestyle_edge attribute.

Marking procedure:

- Select the mesh and enter Edit Mode.
- Choose edges to mark.
- Press Ctrl-E and select Mark Freestyle Edge.

Edge marks help render lines on particular mesh edges.

Marking Freestyle Edges in Edit Mode; the edge marks are highlighted in green.

With Edge Marks enabled, previously-marked lines always render. Black contour lines and blue edge-mark lines display.

| Render without Edge Marks. | Render with Edge Marks enabled. |

Edge mark uses:

- Render marks on nearly-flat planes when other edge types find none.
- Full control of edge rendering. Common for angular shapes.
- Mark the full base mesh for base mesh preview.

Edge mark non-uses:

- Round outer edges (use Contour/External Contour/Silhouette instead).

### Face Marks

Face marks suppress lines in certain mesh areas.

Internally, face marks store as the freestyle_face attribute.

Marking procedure:

- Select a mesh and enter Edit Mode.
- Choose faces to mark.
- Press Ctrl-F and select Face Data ‣ Mark Freestyle Face.

This example marks two cube faces. Right image shows render without face marks.

| Marked faces (Edit Mode). | Render output. |

Line selection via inclusion and face options:

Negation
Include or exclude edges matching face mark conditions.

Condition

One Face:
(De)select edges whose one or both neighbors are marked.

Both Faces:
(De)select edges whose both neighbors are marked.

| Inclusive, One Face. | Inclusive, Both Faces. |
| Exclusive, One Face. | Exclusive, Both Faces. |

### Collection

Include/exclude objects for line calculation per Collection membership.

Line Set Collection
Object collection name.

Negation
Include or exclude lines from these objects in this line set.

## Alpha

Alpha — Transparency Control

This tab manages stroke transparency.

Line Style: Alpha.

Base Transparency
Stroke alpha for this line style.

### Modifiers

### Common Options

Mix
Blend modifier output with the base property via standard methods (e.g., Mix compositing node).

Influence
Modifier effect magnitude on the current property.

Mapping
Linear progression (0.0 to 1.0) or custom curve.

Note
Linear non-inverted is equivalent to doing nothing, as material values already occupy (0.0 to 1.0). Applies to: Crease Angle, Curvature 3D, Material, Noise, Tangent.

Invert
Reverse the Mapping.

### Types

- Along Stroke
- Crease Angle
- Curvature 3D
- Distance from Camera
- Distance from Object
- Material
- Noise
- Tangent

## Material

Material

This modifier transforms a base property into one derived from the material properties beneath the stroke.

Different material properties yield different result types. Single-component properties (grayscale) can optionally feed into a color ramp for the color modifier to produce RGB output. Multi-component properties (already RGB) will have their mean value applied when used with alpha or thickness modifiers.

When combined with Split by Material in the Stroke tab, material transitions along strokes remain sharp rather than blurred.

Material modifiers demo by T.K.
(blend-file).

Material

This modifier transforms a base property into one derived from the material properties beneath the stroke.

Different material properties yield different result types. Single-component properties (grayscale) can optionally feed into a color ramp for the color modifier to produce RGB output. Multi-component properties (already RGB) will have their mean value applied when used with alpha or thickness modifiers.

When combined with Split by Material in the Stroke tab, material transitions along strokes remain sharp rather than blurred.

Material modifiers demo by T.K.
(blend-file).

Material

This modifier transforms a base property into one derived from the material properties beneath the stroke.

Different material properties yield different result types. Single-component properties (grayscale) can optionally feed into a color ramp for the color modifier to produce RGB output. Multi-component properties (already RGB) will have their mean value applied when used with alpha or thickness modifiers.

When combined with Split by Material in the Stroke tab, material transitions along strokes remain sharp rather than blurred.

Material modifiers demo by T.K.
(blend-file).

## Strokes

Strokes

Strokes represent the final rendered lines. You can adjust them—removing lines shorter or longer than thresholds, merging lines into single strokes, or splitting based on angles, patterns, and other criteria.

Line Style: Strokes.

Caps
Three line ending styles are available:

Butt :
A flat termination at the exact endpoint.

Round :
A semicircle centered on the endpoint.

Square :
A square centered on the endpoint (extends the line slightly beyond its computed edge, similar to Round).

Line caps example.

### Chaining

By default, all lines from a line set connect together. Two chaining approaches exist:

Method

Plain :
Standard chaining; creates simple connected chains.

Sketchy :
Generates chains using multiple overlapping strokes instead of single lines, enabling sketchy effects. Most effective with random-driven modifiers.

Rounds
The number of overlapping strokes in sketchy mode.

Same Object
When enabled, chains only join feature edges from the same object.

Chaining can be disabled to render each line independently, useful when line-style behavior depends on precise line-set representation.

### Splitting

Enable any of the following to subdivide chains:

Min/Max 2D Angle
Separates chains when 2D angles exceed (or fall below) threshold values.

2D Length
Subdivides chains exceeding a specified length.

Material Boundary
Breaks chains crossing material transitions.

### Split Pattern

Uses a dashed pattern for subdivision (see also Dashed Line).

Dash 1, 2, 3
Individual dash segment lengths.

Gap 1, 2, 3
Spacing between dashes.

### Sorting

Lines can be sorted to control stacking order.

Sort Key
Determines the stacking sequence:

Distance from Camera :
Nearer lines render above distant ones.

2D Length :
Longer lines layer atop shorter ones.

Projected X/Y :
Sorts by X or Y position in image space.

Integration Type
Combines with Sort Key to determine the calculation range. Since line distance varies along vertices, this computes a single line value from per-vertex values:

Mean :
The average of vertex values.

Min :
The lowest vertex value.

Max :
The highest vertex value.

First :
The value from the first vertex.

Last :
The value from the last vertex.

Sort Order
Optionally reverse the calculated sort sequence.

### Selection

Restrict rendering to chosen chains.

Min/Max 2D Length
Filters by chain length.

Chain Count
Limits rendering to the first N chains.

### Dashed Line

Enable to specify three dash/gap pairs. Dashes define stroke lengths; gaps specify intervals. A zero gap causes its dash to be ignored regardless of its value.

Dashes are treated as separate strokes, allowing line caps and color, alpha, and thickness modifiers to apply.

Dash 1, 2, 3
Individual dash segment lengths.

Gap 1, 2, 3
Spacing between dashes.

## Thickness

Thickness

Configures the width of Freestyle strokes.

Line Style: Thickness.

Base Thickness
The starting thickness value for this line style.

Thickness Position
Specifies where thickness extends relative to the stroke spine. Four options exist:

Center :
Thickness divides equally left and right of the spine.

Inside :
Strokes render within the object boundary.

Outside :
Strokes extend beyond the object boundary.

Relative :
A proportional value between 0.0 (inside) and 1.0 (outside), set in the Thickness Ratio field below.

Note

The Silhouette and Border edge types are the sole categories with boundary-relative definitions, so thickness positioning affects only these. All other edge classifications default to Center.

### Modifiers

### Common Options

Mix
Combines the output with the base property using conventional blending (analogous to the Mix node in compositing).

Influence
Determines the intensity of the modifier's contribution.

### Available Modifiers

The following modifiers are available:

- Along Stroke

- Calligraphy

- Crease Angle

- Curvature 3D

- Distance from Camera

- Distance from Object

- Material

- Noise

- Tangent

## Filter

### Filter

These settings control which element categories appear in the finished output for the current layer.

Include

Environment Cycles , EEVEE
Turn off the Environment render pass in the final output.

Surfaces Cycles , EEVEE
Turn off object material rendering in the final output.

Curves Cycles , EEVEE
Turn off curve strand rendering in the final output.

Volume Cycles , EEVEE
Turn off Volume rendering in the final output.

Grease Pencil Cycles , EEVEE
Show Grease Pencil geometry from the active layer

Use

Motion Blur Cycles , EEVEE
Apply motion blur to the current layer, if active in the Render Settings.

## View Layer Override

### View Layer Override

Reference

Panel :

Properties ‣ View Layer ‣ Override

View Layer overrides enable conditional replacement of select scene-wide configuration for one particular view layer.
This method helps create alternate renderings of identical layouts, for instance with varied surface properties, illumination,
or quality parameters, while preserving initial scene information unchanged.

Overrides take effect exclusively during layer rendering and don't apply globally.

Material Override
Replaces materials throughout the layer with a universal material option.
Typical uses include monochrome renderings or illumination tests where texture and shader detail obstructs the analysis.

Tip

Choose a simple diffuse surface for studying light distribution or geometry without texture or shader distraction.

World Override
Substitutes the scene's world parameters (such as background tone or HDRI environment) for the chosen layer.

This option facilitates testing varied
environmental illumination configurations
or positioning objects against neutral backgrounds for later composition.

Samples
Permits the layer to employ divergent sampling count compared to overall scene configuration.
The Layer Samples parameter
governs this behavior in the Cycles rendering engine. The Samples override activates at all times in EEVEE.

Using fewer samples for utility or background passes cuts time,
while prioritizing higher samples for hero visual passes.

## Passes

### Passes

Reference

Panel :

Properties ‣ View Layer ‣ Passes

A Pass is a type of intermediate rendering information that's extracted as a separate image. Examples include the diffuse colors of the objects in the scene, the light distribution, the depth map, and the normal map.

These images can be accessed using the Render Layers Node in the Compositor and combined in a custom way that replaces the standard one.

### Data

Include

Combined Cycles , EEVEE , Workbench
The render output before any compositing is applied.

Depth Cycles , EEVEE , Workbench
Distance to the nearest visible surface. Can be used with the Defocus Node for a fake Depth of Field effect.

Note

This pass produces noisy results if the render itself uses Depth of Field or motion blur. Use the Mist pass for a cleaner image.

Mist Cycles , EEVEE
Distance to the nearest visible surface, mapped to the 0.0 - 1.0 range. When enabled, settings become available in the World tab.

This pass can be used to fade out objects that are farther away. An alternative is using the Volume slot of the World Output shading node.

Position Cycles , EEVEE
Positions in world space.

Normal Cycles , EEVEE
Surface normals in world space.

Vector Cycles , EEVEE
Motion vectors for the Vector Blur Node. The four components consist of 2D vectors giving the screen-space motion based on the next and previous frames.

This pass is disabled when Motion Blur is enabled.

UV Cycles
The UV coordinates within each object's active UV map, represented through the red and green channels of the image. (The blue channel stores a constant value of 1 and does not hold any information.) Can be used with the Map UV Node.

Grease Pencil Cycles , EEVEE , Workbench
Outputs only the visible (non-occluded) strokes and fills from the Grease Pencil engine into a separate image layer.

This pass is useful for compositing workflows where you want to isolate, enhance, or apply effects to Grease Pencil elements separately from the rest of the render.

Note

For most scenes, blending this pass over the rest of the image using an Alpha Over node will reproduce the Combined render result. However, some blending modes in Grease Pencil can modify the chromaticity of the alpha channel. In these cases, compositing the Grease Pencil pass separately can produce different results.

Denoising Data Cycles
Includes Denoising Albedo , Denoising Normal , and the combined image before denoising. Can be used with the Denoise Node as a replacement for automatic denoising.

Indexes

Object Index Cycles
A map where each pixel stores the user-defined ID of the object at that pixel. This map can be converted into a mask for a particular object using the ID Mask Node.

Material Index Cycles
A map where each pixel stores the user-defined ID of the material at that pixel. This map can be converted into a mask for a particular material using the ID Mask Node.

Note

The Depth, Position, Object Index, and Material Index passes are not anti-aliased.

Debug

Render Time Cycles
An estimate for how long in milliseconds each pixel took to render. Note, this pass is not supported on GPU rendering.

Sample Count Cycles
Number of samples calculated for each pixel, divided by the maximum number of samples. Used to analyze adaptive sampling.

Alpha Threshold Cycles
The Depth, Position, Normal, Vector, UV, and Index passes are only affected by surfaces with an opacity equal to or higher than this threshold. With value 0.0, the first surface hit will always write to these passes regardless of opacity. With higher values, surfaces that are mostly transparent will be skipped until an opaque surface is encountered.

### Light

### Cycles

Diffuse

Direct
The intensity and color of light that hit a surface with a Diffuse or Subsurface Scattering BSDF and did not yet bounce off/pass through any other surface (ignoring Transparent ones). The color of the surface itself is not included.

Indirect
The intensity and color of light that hit a surface with a Diffuse or Subsurface Scattering BSDF and already bounced off/passed through another surface before (ignoring Transparent ones). The color of the surface itself is not included.

Color
The colors of Diffuse and Subsurface Scattering BSDFs, modified by any Mix and Add Shader nodes. The intensity and color of light are not included.

Glossy

Direct, Indirect, Color
Same as above, but for glossy BSDFs.

Transmission

Direct, Indirect, Color
Same as above, but for transmissive BSDFs.

The Transparent BSDF is not included; see Light Paths for details. To create a transparent surface that does get included in this pass, use a Glass BSDF with the IOR set to 1.

Volume

Direct, Indirect
Same as above, but for volumetric BSDFs.

Other

Emission
Emission from directly visible surfaces.

Environment
Emission from the directly visible World Environment. When the Film is set to Transparent (meaning the world is excluded from the final render), this pass can be used to get the environment color and composite it back in.

Ambient Occlusion
Ambient occlusion from directly visible surfaces. This is a grayscale pass with values that go from 0 (fully occluded) to 1 (fully exposed), making it suitable for multiplying with a color image in the Compositor (see Mix Color Node).

As an alternative to this pass, it's also possible to use the Ambient Occlusion Node in materials.

Shadow Catcher
Shadows collected by objects with the Mask – Shadow Catcher option enabled. Can be multiplied with existing footage to (for example) have a rendered object cast a shadow on recorded ground.

### EEVEE

Diffuse

Light
The intensity and color of light that hit a surface with a Diffuse or Subsurface Scattering BSDF. The color of the surface itself is not included.

Color
The colors of Diffuse and Subsurface Scattering BSDFs, modified by any Mix and Add Shader nodes. The intensity and color of light are not included.

Specular

Light, Color
Same as above, but for specular BSDFs.

Volume

Light
Contains Volume objects, as well as any volumes generated by the volume shader nodes (Principled Volume, Volume Absorption, and Volume Scatter), whether they're used in a material or in the World background.

Other

Emission
Radiance from immediately visible matter.

Environment
Radiance from immediately visible World backdrop. Whenever
Film turns See-through (excluding world from final display), this choice supplies environment tone for re-introducing.

Shadow
A pass showing dark for areas lacking direct light and bright for areas receiving illumination.
Frequently employed for placing graphics with shadow into captured video.

Ambient Occlusion
Obstruction illumination from immediately visible matter. This grayscale option spans
from 0 (completely shadowed) to 1 (fully lit), suitable for multiplying picture
in the Compositor (see Mix Color Node).

Another method: use the
Ambient Occlusion Node in shader configuration.

Transparent
Contains Blended matter,
allowing post-processing in the Compositor and subsequent merging with opaque passes.

This pass accepts grayscale see-through values only.
Tinted see-through will appear distinct from the Combined option.

Occlusion Distance
Boundary spacing for item inclusion in the Ambient Occlusion pass.

### Cryptomatte

Cryptomatte delivers an image specification for producing targeted silhouettes by object or material efficiently.
Its purpose parallels the Object Index and Material Index passes,
yet grants several benefits: easier configuration, compatibility with non-Blender composition systems, and multiple-item-per-location capability.
Specifically, it suits see-through, camera zoom, and depth-of-field
in the Cycles platform.

Object
Produce cryptomatte outputs for item segregation.

Material
Produce cryptomatte outputs for surface segregation.

Asset
Produce cryptomatte outputs for item family segregation (same parent).
This option does not tie to Blender's
resource system.

Levels
The cap for identified items per location.
The Render Layers node outputs half this quantity of Cryptomatte pictures,
designated (as example) CryptoObject00 , CryptoObject01 etcetera –
since individual Cryptomatte pictures hold dual item citations per location.

The first picture identifies, for every location, the pair of items producing
the maximum contribution to that location's hue. Following pictures identify the subsequent pairs,
and so forth.

See also

Cryptomatte Node

### Shader AOV

Shader AOVs (Arbitrary Output Variables) comprise user-designed visual data containers for composition purposes. Build a pass in the Shader AOV area,
send to it from a material using the AOV Output Node,
and subsequently retrieve in the Compositor utilizing the socket on the Render Layers node.

Name
The tag for the output channel. Used in both the AOV Output node and the
Render Layers node. The designation can be arbitrary provided it avoids
clashing with other (operational) options.

Data Type
The storage category for the output per location.
Choose Color for hue, direction, or additional vector information.
Pick Value for single-number information.

### Light Groups

Cycles only

A Light Group creates a restricted Combined pass rendering illumination from
designated lights only. These individual passes can then get joined in composition to assemble the final product
with complete illumination. The basic technique involves combining them with
the Mix Color Node, though more intricate assemblies
enable tuning hue and brightness of distinct lights absent re-rendering.

To link a Light item to a new or existing Light Group, locate the panel
Object ‣ Shading ‣ Light Group (specifics).

To link the World backdrop to a Light Group, locate the panel
World ‣ Settings ‣ Light Group (specifics).

Name
The label of the light grouping.

### Light Group Sync

These operations appear via the
Light Group catalog selector.

Add Used Lightgroups
Build Light Groups for any lights mentioning a non-existent group.

Remove Unused Lightgroups
Erase any Light Groups which no lights employ.

### Combining

### Cycles

The individual output stages get assembled to yield the complete result as:

### EEVEE

The stages can get merged to yield the complete result as:

### EEVEE Limitations

- Depth of Field and Motion Blur
stay unrendered in outputs apart from Combined .
You can create them in the Compositor using the Defocus Node
plus the Vector Blur Node.

- See-through materials configured with Blended Render Method get left unrendered in outputs apart from Combined and Transparent .
Switch to the Dithered alternative instead.

- The Shader To RGB Node produces right results
in the Combined option only as EEVEE leaves parts of the BSDF equation unprocessed.

- A cap of 16 Color plus 16 Value AOVs (custom outputs) exists.
