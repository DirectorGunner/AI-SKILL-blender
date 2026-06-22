# Usage, Light Falloff Node, Shader To Rgb Node, Wavelength Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Usage; Light Falloff Node; Shader To RGB Node; Wavelength Node; Bump Node; Displacement Node; Normal Map Node; Vector Displacement Node; Ambient Occlusion Node; Attribute Node; Bevel Node; Camera Data Node; Fresnel Node.

## Usage

### Usage 

This example transforms an existing monoscopic project into stereo 3D-capable output.

Creature Factory 2 by Andy Goralczyk rendered in stereo 3D (anaglyph). 

### Introduction 

Begin by loading your scene, in this case turntable.blend from the Creature Factory 2 Open Movie Workshop series created by the Blender Institute and Andy Goralczyk.

Turntable Creature Factory 2. 

### Stereoscopy Setup 

Access the Output Properties and activate Stereoscopy for your scene.

Scene render views. 

Note

When Stereoscopy is activated, you gain 3D preview capability in the viewport plus new panel areas throughout the interface.

Viewport with 3D visualization. 

### Camera 

Select the camera object in the Outliner. In the Camera panel's Stereoscopy tab, modify the Convergence Distance to fine-tune stereo 3D parameters.

The viewport instantly reflects alterations in real-time, permitting immediate preview of depth values.

Stereo convergence distance. 

### Viewport 

For initial camera setup, establish the convergence plane in the viewport based on your depth structure. Leave camera view mode and the convergence plane becomes immediately visible in front of the camera.

Toggle this setting and other display choices in the Stereoscopy panel of the 3D Viewport's Sidebar. Camera frustum volumes are also viewable in the following scene.

Viewport plane and volume stereo preview. 

### Stereo 3D Display 

On compatible 3D displays, access the Window menu and invoke the Stereo 3D operator to adjust display mode. Understand that some modes require full-screen and impose substantial processing demands.

Window menu, stereo 3D operator. 

### Viewport Preview 

Test your setup by saving a Viewport Preview before final rendering. The Render Output panel permits selection of the output Views Format.

Available options include individual files per camera, stacked layouts, anaglyph, and others. Select the format matching your display setup.

### Rendering and Image Editor 

Upon reaching the target appearance, proceed with final animation export. Use the Image Editor to examine individual camera views and combined stereo results.

### Image Formats 

Your final output can employ more robust storage formats. This example uses side-by-side cross-eyed stereo 3D storage.

Side-by-side cross-eye format. 

### Final Considerations 

As this tutorial illustrates, stereo 3D rendering involves more than frame pairs. Introduction of stereo considerations early in the pipeline streamlines the overall process. The following information provides deeper coverage of individual workflow components encountered here.

### Window Stereo 3D Display 

Proper stereo image presentation forms a core part of the Stereoscopy pipeline. Blender accommodates display hardware ranging from high-end 3D monitors to affordable glasses-based solutions. Additionally, you can configure a distinct display mode per window.

Alter display mode via the Window menu or create custom shortcuts with the wm.set_stereo_3d operator.

Window menu, stereo 3D operator. 

### Display Mode 

Anaglyph
Produces two distinctly tinted color images, each tailored to one eye. Anaglyph glasses are required. Red-cyan, green-magenta, and yellow-blue variants are available.

Interlace
Merges both eye views into a single interlaced frame. A 3D-compatible display is necessary. Row, Column, and Checkerboard interlacing modes are supported. A Swap Left/Right option adjusts for screen calibration. Best results in full-screen mode.

Time Sequential
Alternates rendering per eye. Also termed Page Flip. Quad Buffer support from the GPU is mandatory and requires full-screen operation.

Side-by-Side
Places left and right eye views side-by-side. Cross-Eye viewing option is available. Full-screen operation is necessary, best paired with the Full Editor option.

Top-Bottom
Stacks left and right eye perspectives vertically. Full-screen and Full Editor operation required.

Note

Full Screen Stereo 3D Modes

For constant stereo 3D viewing, most workflows benefit from full-screen stereo operation. Certain modes function exclusively in full-screen, concealing much of the interface. Two-monitor setups work well: reserve the 3D display for stereo visualization and use the other for standard Blender editing.

### Stereo 3D Camera 

Stereo 3D scene configuration generates a camera pair dynamically for rendering and viewport preview. This behaves like two cameras with shared parameters (focal length, clipping planes, …). The pair is offset and can exhibit independent rotation and perspective shifts.

Stereo 3D camera settings. 

Interocular Distance
The separation between stereo camera pair. Though convergence can be adjusted post-render, distinct interocular distances produce varying outcomes due to differential scene occlusion across viewpoints.

Convergence Plane Distance
The stereo camera convergence point, typically representing the distance between a projector and its screen. Real-time visualization is available in the 3D Viewport.

Spherical Stereo
Renders by rotating the camera around the interocular midpoint for each pixel.

Use Pole Merge
Taper interocular distance toward zero beyond a specific angle cutoff.

Pole Merge Start Angle
The threshold angle where tapering starts.

Pole Merge End Angle
The point angle where interocular distance becomes zero.

### Convergence Mode 

Off-Axis
The camera pair separates by interocular distance and shifts inward to meet at the convergence plane. This represents the ideal configuration, closest to human vision mechanics.

Parallel
Generates two non-converging parallel cameras. This needs post-render alignment and cannot be used directly for viewing. Typical when combining practical footage with CG elements.

Toe-in
Angles cameras rather than shifting frustums. Toe-in remains uncommon in modern visual effects work.

Pivot
The stereo pair can be generated around the main camera with separate cameras per eye (Center Pivot) or with an existing camera as base and generation of (Left or Right). The latter applies when rendering a single eye for a single-view 2D project converted from mono.

### Viewport Stereo 3D 

Activating Views in the Render Layer panel exposes a fresh control area in the 3D Viewport Sidebar. Configure whether the viewport displays stereo 3D output and which camera to show. The panel also permits visibility of individual Cameras, the Plane, and stereo frustums.

Viewport stereo 3D settings. 

Cameras
With Stereo 3D Viewport operation, examine each dynamically-built camera output or their combined result. Multi-View mode displays the merged left-and-right camera result (when both exist) or the currently-selected camera.

Plane
The convergence plane represents the audience viewing surface. Viewport visualization allows depth planning based on script requirements beyond the camera bounds.

Volume
The merged stereo camera frustums help prevent visibility mistakes by identifying where one camera sees content the other doesn't. Boundaries depend on camera clip distances. Retinal rivalry zones (visible to only one camera) are tolerated in the negative space (the region from the convergence plane into the image) but are to be avoided in the positive space (the area from the convergence plane to the camera).

Viewport 3D: convergence plane and volume display. 

### Multi-View and Stereo 3D Image I/O 

Multi-View and Stereo 3D
Multi-view images can be exported in formats aligned with production needs. Default behavior saves each view separately, creating as many files as views rendered. For stereo 3D delivery or interim assessments, stereo 3D-ready images matching display modes are convenient. Available formats correspond to window display options.

Lossy-Formats
Certain stereo 3D formats incur substantial data reduction. Anaglyph strips entire color channels. Top-Bottom compressed removes vertical resolution data. Interlace applies considerable compression. These formats can be re-imported to Blender and treated as stereo 3D when the window display mode aligns with image format.

Lossless Formats
Selected formats retain full information with zero export/import penalties. Individual files (saved as lossless like PNG or OpenEXR) load back with no degradation. For stereo 3D formats, lossless preservation occurs only with Top-Bottom and Side-by-Side modes lacking the Squeezed Frame option.

Multi-View OpenEXR
Multi-view OpenEXR stores multiple camera views in one file while maintaining backward compatibility with standard OpenEXR readers (showing one view). Multi-view native support is exclusive to OpenEXR format.

### Image Editor 

View Menu
Stereo 3D-rendered output displays either combined stereo 3D results or individual camera views in the Image Editor. This applies to Viewer nodes, render results, and opened images.

Stereo 3D and view menu. 

Views Format
Importing images into the Image Editor initially loads them as individual images. For Stereo 3D format images, configure interpretation via Views Format toggle and Multi-View activation with the matching stereo method.

Views formats and stereo 3D. 

### Compositor 

Multi-view handling is seamless in the Compositor. Single-view composition finishes before remaining views are processed. Workflow mirrors single-view operation, with support for multi-view format images, video, and sequences.

Compositor, backdrop and Split Viewer node. 

Render views are defined in the scene's current views configuration, parallel to how composite output resolution is configured at the scene render level, independent of Image node resolution or Render Layers from alternate scenes.

Note

Single-View Images

If an Image node references a view absent from the render target, the image is handled as single-view.

Switch View Node
Use the Switch View node when separating views is necessary, combining them before an Output node.

Tip

Performance

During GUI rendering and compositing, all views process before composition. Testing iterations benefit from disabling all but one view in the Scene Views panel, then re-enabling all afterward.

## Light Falloff Node

### Light Falloff Node 

Cycles Only

The Light Falloff node offers control over intensity attenuation with distance. Physically accurate light exhibits quadratic falloff; applying alternative falloff curves enables non-realistic lighting adjustments. Be cautious: Linear or Constant falloff can amplify light with each global illumination pass, potentially causing severe overexposure with multiple bounces.

### Inputs 

Strength
Light magnitude before falloff transformation.

Smooth
Light intensity softening near sources. Values smooth out harsh highlights and reduce GI noise. Zero means no smoothing; larger values increase it. Maximum intensity equals strength divided by smooth.

### Properties 

This node has no properties.

### Outputs 

Quadratic
Quadratic light attenuation; matches physical reality when smooth is 0.0.

Linear
Linear intensity reduction creating slower decay across distance.

Constant
Constant output where distance has no effect.

### Examples 

Todo <2.8 add.

## Shader To RGB Node

### Shader To RGB Node 

EEVEE Only

The Shader to RGB node enables non-photorealistic rendering through additional effects applied to BSDF outputs. For instance, connecting a color ramp to a diffuse BSDF output creates a flexible cartoon renderer.

Using this function departures from PBR, producing unpredictable results when combined with features such as ambient occlusion, contact shadows, soft shadows, and screen space refraction.

Several effects require multiple passes to stabilize; arbitrary modifications to noisy data may prevent smooth convergence.

Warning

When a Shader to RGB node is present, upstream BSDFs become invisible to:

- Screen Space Reflection

- Subsurface Scattering

- Alpha Clip and Alpha Hashed blend modes

Shader to RGB node rendering fails to produce expected results in render passes.

### Inputs 

Shader
Connect any shader—BSDF or Emission—here.

### Properties 

This node has no properties.

### Outputs 

Color
Computed surface color from BSDFs and ambient illumination.

Alpha
Transparency from embedded Transparent BSDFs.

### Examples 

Simple toon shading with Shader to RGB and Freestyle.

## Wavelength Node

### Wavelength Node 

The Wavelength node maps a wavelength magnitude to RGB. Achieves specific colors from the light spectrum.

### Inputs 

Wavelength
The visible-spectrum wavelength in nanometers, spanning 380 to 780.

### Properties 

This node has no properties.

### Outputs 

Color
RGB color output.

### Examples 

Example of Wavelength node.

## Bump Node

### Bump Node 

The Bump node generates perturbed surface normals from height data for bump mapping. Height is sampled at the shading location and adjacent surface points to compute local normal direction.

### Inputs 

Strength
Bump effect magnitude, interpolating between no effect and full effect.

Distance
Scalar multiplier applied to height values, controlling the overall bump scale.

Filter Width
Pixel-sized filter width applied when calculating bump direction. Default 0.1 enables subpixel stability for most textures. Larger filter widths on stepped textures simulate edge bevels.

This input accepts only constant values and does not spatially vary.

Height
Scalar height displacement at the shading location; link textures here.

Normal
Standard normal input.

### Properties 

Invert
Reverses bump direction to displace inward rather than outward.

### Outputs 

Normal
Standard normal output.

Tip

When Height is unconnected, the node passes through its Normal input unchanged, or defaults to geometric normal if unlinked. Feeding a node group input via a no-op Bump node before calculations defaults it to normal.

### Examples 

The setup above applies bump only to diffuse shading, creating the impression of a bumpy base finished with a smooth glossy layer.

## Displacement Node

### Displacement Node 

The Displacement node shifts geometry along surface normals to introduce additional detail. Procedural textures or pre-baked displacement images can serve as input.

Bump Mapping alone is the default in Blender. Genuine displacement physically deforms rendered geometry. For authentic displacement, the Displacement method configuration is required.

Tip

Genuine displacement benefits from fine mesh subdivision to reveal texture detail.

See also

Material Displacement for comprehensive displacement workflow guidance.

### Inputs 

Height
The offset magnitude along the normal. Connect texture output here.

Midlevel
The neutral displacement threshold. At default 0.5, values below push surfaces inward; values above push outward.

Scale
Amplify or reduce displacement magnitude.

Normal
Standard normal input.

### Properties 

Space
Object Space causes displacement to scale with the object. World Space ignores object scaling.

### Outputs 

Displacement
Displacement data for the Material Output socket.

### Examples 

Typical displacement node setup. 

Bump only, displacement only, and both combined.

## Normal Map Node

### Normal Map Node 

The Normal Map node generates perturbed normals from RGB-encoded normal map textures. Usually chained with an Image Texture node for the color input specifying the map image. For tangent-space maps, UV coordinates must align with the image, and Non-Color mode is required for correct interpretation.

### Inputs 

Strength
The normal mapping intensity.

Strength is set to 0, 0.5, 1, 2 (from left to right). 

Color
RGB data encoding the normal in the designated space.

### Properties 

Space
Three spaces are available for the RGB data: Tangent, Object, and World. Tangent space is most prevalent, supporting transformations and mesh deformations. Object space maps maintain surface alignment through transformations but shift under object scaling. World space maps ignore both.

Convention
Blender defaults to OpenGL, where the green channel's Y points up. DirectX convention (Y pointing down) accommodates maps from external tools.

Base Cycles Only
Surface serving as the normal map base when displacement is combined.

Original Base :

The smooth, unmodified base normal and tangents, coordinating with aligned displacement.

Displaced Base :

The displaced normal and tangents, applying normal mapping on top.

UV Map
The UV set supplying tangent calculation data. Should match the UV used by any linked Image Texture node.

### Outputs 

Normal
Normal output compatible with BSDF inputs.

### Example 

The Normal Map Strength is set to 1.

## Vector Displacement Node

### Vector Displacement Node 

The Vector Displacement node shifts surfaces along arbitrary axes, contrasting the standard Displacement node which moves along the normal only.

Typical application involves importing vector displacement maps from external sculpting tools. Vector maps fully encode high-resolution detail on a smooth base mesh, unlike standard maps.

Bump Mapping is default in Blender. For genuine displacement, geometry physically deforms in the final render. This requires setting the Displacement method appropriately.

Tip

Genuine displacement achieves best results with fine mesh subdivision.

See also

Material Displacement for thorough displacement documentation.

### Inputs 

Vector
Three-axis displacement specification. Connect a texture node here.

Typically pre-baked vector displacement texture output is used. In Object Space, RGB colors are interpreted as XYZ offsets. In Tangent Space, R shifts along tangent, G along normal, and B along bitangent.

Midlevel
The neutral point. Default 0.0 means zero shift; lower values displace inward, higher values outward.

Scale
Multiply or divide displacement magnitude.

### Properties 

Space
Object Space suits static geometry with faster, lower-memory rendering. Tangent Space supports deforming meshes like animated figures, where displacement follows deformation.

### Outputs 

Displacement
Displacement data for the Material Output socket.

### Examples 

Standard and magnified vector displacement on a smooth base mesh.

## Ambient Occlusion Node

### Ambient Occlusion Node 

The Ambient Occlusion node measures hemisphere occlusion above the shading point. Applies include procedural texturing and effects like corner weathering.

In Cycles, this is a costly computation and can extend render duration substantially. For performance-critical projects, Pointiness from the Geometry node or pre-baked AO yield faster results.

Note

Cycles Only

The Ambient Occlusion node fails to give correct output when:

- The object functions as either Caustic caster or Caustic receiver while the scene contains an active Caustic caster, Caustic receiver, and Shadow Caustic Light.

- Open Shading Language is active under the OptiX backend.

See also

The Ambient Occlusion pass provides occlusion data across the full render for compositing work.

### Inputs 

Color
Tint applied to AO output.

Distance
The range for considering objects occluding the shading point.

Normal
The normal used for ambient occlusion computation; geometric normal is used if unconnected.

### Properties 

Samples
Ray-trace sample count for AO. Keep minimal for speed.

Inside
Detect bulges rather than hollows by computing occlusion within mesh.

Only Local Cycles Only
Restrict occlusion to the object itself, excluding other geometry.

### Outputs 

Color
Ambient occlusion with color tint.

AO
Occlusion factor without tint.

### Example 

White AO shader.

## Attribute Node

### Attribute Node

Retrieve attributes from an object or mesh using this node.

### Inputs

None.

### Properties

**Attribute Type** — Choose what kind of attribute data to access.

**Geometry:** The attribute comes from the object's mesh and can vary per-vertex or throughout the volume. Most geometry attributes are available through dedicated input nodes, except:

- **Ocean Foam** — Retrieves scalar values for foam regions when using an Ocean Modifier (name-dependent).

See Stack Exchange for a complete list of available options.

**Object:** Reference custom properties or RNA paths (same as driver variables). Values are defined per-object. The lookup searches the object data-block first, then the mesh data-block if not found. Custom properties take precedence over built-in ones. Properties must be integer, float, boolean, or a vector of 1–4 numeric values; invalid types return 0 on all sockets including Alpha.

Tip: The color attribute reflects the Color field in the object's Viewport Display panel, unless overridden by a custom property.

**Instancer:** Searches the instancer particle system settings, then Geometry Node instance attributes (innermost to outermost), then the instancer object. Falls back to Object mode if the current object is not instanced or the property is missing.

Warning: Currently limited to 4 layers of Geometry Node instancing.

**View Layer:** Searches the current View Layer, Scene, and World using the same lookup logic as Object, returning all zeros (including Alpha) if not found. Attributes here are uniform across the entire Render Layer.

Tip: Access useful built-in properties like: color (or world.color) for World viewport display color, render.resolution_x/y for render dimensions, camera.data.angle_x/y for active camera field of view. See driver Context Properties for an alternative lookup approach.

**Name** — Specify the attribute to retrieve.

### Outputs

- **Color** — RGB value interpolated from the attribute.
- **Vector** — XYZ value interpolated from the attribute.
- **Factor** — Scalar interpolated from the attribute.
- **Alpha** — Alpha channel when available; defaults to 1 if absent.

Warning: Currently only View Layer attributes work in shaders for World or Light Objects.

## Bevel Node

### Bevel Node

*Cycles Only*

Add softened edges to shading using this node. Like bump mapping, it only affects shading, not actual geometry. Realistic specular highlights emerge from slightly rounded edges, mimicking real-world materials.

Bevel is computationally expensive and may reduce render speed by 20% even with high scene complexity. Reserve it for baking or static frame renders where render time is less critical. The Bevel Modifier offers faster alternatives but sometimes fails on complex geometry.

**Limitations:**
- The node produces invalid results when the object is a Caustic caster or receiver while the scene contains active caustic elements (caster, receiver, and Shadow Caustic Light).
- Does not work with Open Shading Language active on OptiX backends.

### Inputs

- **Radius** — Width of the bevel effect on edges.
- **Normal** — Normal to apply bevel atop; combines with Bump Nodes. Defaults to surface normal when disconnected.

### Properties

**Samples** — Number of samples per shader evaluation. More samples improve accuracy but slow rendering. 4 is typical; extra AA samples resolve remaining noise.

### Outputs

- **Normal** — Standard normal output.

### Examples

Minimal node setup for bevel work. / Bevel shader revealing specular highlights on edges.

## Camera Data Node

### Camera Data Node

Retrieve shading point information relative to the camera position. Use this to adjust shading based on distance from camera or build custom fog effects.

### Inputs

None.

### Properties

None.

### Outputs

- **View Vector** — Normalized vector in camera space pointing from camera to shading point.
- **View Z Depth** — Distance (in pixel units) from camera to shading point.
- **View Distance** — Direct distance from camera to shading point.

## Fresnel Node

### Fresnel Node

Calculate how much light reflects off a layer versus passing through. The output weight suits layering shaders via Mix Shader nodes. Reflection amount depends on the angle between surface normal and viewing direction.

Common use: Mix two BSDFs with Fresnel as the blending factor. For glass, mix between glossy refraction and reflection. At grazing angles, more light reflects than refracts, as in the physical world.

Two-layer materials work similarly: place a glossy coating over a diffuse base and mix them with Fresnel. This specifies that refracted light through the coating hits the diffuse layer and bounces.

### Inputs

- **IOR** — Index of refraction of the material being entered.
- **Normal** — Bump or normal map input to affect the output.

### Properties

None.

### Outputs

- **Factor** — Fresnel weight indicating the probability light reflects versus transmitting through.
