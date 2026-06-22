# Reducing Noise, Custom Camera, Open Shading Language, Film ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Reducing Noise; Custom Camera; Open Shading Language; Film; Curves.

## Reducing Noise

### Reducing Noise

When rendering a final output, minimizing visual noise is a critical priority. This section explores practical techniques that, while departing from strict physical simulation, prove essential for completing animations within practical timeframes. Examine the examples at full size to appreciate the noise reduction differences.

### Path Tracing

Cycles implements path tracing combined with next event estimation. This approach has limitations for certain phenomena such as caustics, yet provides substantial advantages: it scales efficiently to detailed and large-scale environments since the renderer avoids storing structures like photon maps in memory, and maintains ray coherence for efficient image caching, outperforming strategies such as bidirectional path tracing.

The algorithm inverts the natural light flow: rays originate from the camera, pass through the scene, and terminate at light sources, rather than emanating from lights and reaching the camera. This strategy eliminates wasted rays that miss the camera entirely, but introduces a challenge—it becomes harder to locate certain light paths that contribute significantly to the final image. Light rays distribute either following the surface's BSDF or traveling directly toward known light sources.

See also

For deeper details, consult the Light Paths and Sampling documentation.

### The Source of the Noise

To grasp noise origins, consider this example. When a ray reaches the point marked by the white circle on a red dot, the second image illustrates what the diffuse shader perceives.

Finding the light reflected from this point requires averaging the color across many samples. Observe the glossy reflection on the sphere and the bright light mark on the wall—these high-intensity patches contribute disproportionately to the pixel's lighting.

| The scene. | Irradiance at the shading point. | The detected highlights. |

The light source location is predetermined, yet the glossy highlights it produces behave differently. Path tracing's strategy distributes rays randomly across the hemisphere, hoping to encounter all significant bright regions. If some pixels miss a bright spot while others find it, this inconsistency manifests as noise. Rendering more samples increases the likelihood of covering all important light contributors.

Certain techniques reduce this noise. By softening bright spots—making them larger yet less intense—they become easier to find and produce less noise. While not identical to the original result, the difference often proves negligible when viewed through diffuse or soft glossy reflections. An example follows using Glossy Filter and Light Falloff.

| Using Glossy Filter & Light Falloff. | Irradiance at the shading point. | The detected highlights. |

### Bounces

In nature, light bounces countless times due to its speed. In rendering, additional bounces introduce noise, and the Limited Global Illumination preset in the Light Paths section can help by reducing bounces for different material types. Diffuse surfaces typically manage with fewer bounces, while glossy surfaces demand more, and transmission shaders like glass typically need the most.

| No bounces. | Two bounces at max. | Four bounces at max. |

Equally important is avoiding colors with components at 1.0 or near it; maintain a maximum of 0.8 and increase light brightness instead. In the physical world, surfaces rarely reflect all light, though glass is a notable exception, transmitting most illumination, which is why greater bounce counts apply there. High color values produce noise because light intensity barely diminishes as it reflects between surfaces.

### Caustics and Filter Glossy

Caustics represent a well-known noise challenge, producing Fireflies. These arise when the renderer struggles to detect specular highlights viewed through soft or diffuse reflections. A No Caustics option disables glossy reflections passing through diffuse surfaces entirely. The default behavior in most renderers disables caustics automatically.

| Default settings. | Caustics disabled. | Filter Glossy greater than zero. |

However, No Caustics sacrifices light contribution and overlooks scenarios where sharp glossy reflections appear through soft glossy reflections. A Filter Glossy option cuts noise in these situations, sacrificing some precision. This technique softens sharp reflections by increasing shader Roughness, allowing easier detection.

The images above display three states: defaults, caustics disabled, and Filter Glossy at 1.0.

### Light Falloff

In a vacuum, light follows a 1/(distance^2) falloff law. Yet as distance approaches zero, this expression tends toward infinity, generating extremely bright spots. For indirect lighting, finding such rare, tiny, and brilliant spots becomes statistically unlikely, forming the classic recipe for Fireflies.

| Hard Falloff. | Soft Falloff. |

To mitigate this, the Light Falloff node provides a Smooth factor, reducing the maximum intensity light contributes to nearby surfaces. The images above compare default falloff against smooth set to 1.0.

### Multiple Importance Sampling

Materials using emission shaders may leverage Multiple Importance Sampling (Material Settings). Under this approach, rays are directed explicitly toward these materials rather than reaching them through random bouncing. For intense mesh lights, this substantially cuts noise. Conversely, when emission proves dim, this option diverts samples from genuinely bright sources that require directed sampling, lowering efficiency.

Optimal configuration requires experimentation; weak glowing objects may contribute only locally and benefit from disabling Multiple Importance, while mesh lights used as primary light sources usually need it active. Included is an example: emissive spheres contribute minimally, and the render achieves slightly lower noise with Multiple Importance disabled.

| Multiple Importance off. | Multiple Importance on. |

The world background holds its own Multiple Importance option (Settings). This proves most valuable for environment maps containing scattered bright points rather than uniform gradients. The renderer preprocesses to pinpoint these bright areas and sends rays directly toward them. Again, enabling this may redirect samples away from more critical light sources if unwarranted.

### Glass and Transparent Shadows

With caustics suppressed, glass shadows may appear too dim, and with filter glossy, caustics risk becoming overly soft. Construct a glass shader using Glass BSDF for direct rays and Transparent BSDF for indirect rays. Transparent BSDF suits transparent shadows, locating light straight through surfaces and delivering correctly-tinted shadows without caustic artifacts. The Light Path node determines which shader applies.

Optimized glass shader.

Left: render with dark shadows from missing caustics. Right: render using the glass shader optimization.

| Default Glass BSDF. | Optimized Glass Shader. |

### Light Portals

When rendering indoor daylight scenes where light enters mainly through windows or doors, the integrator struggles to locate these openings. Light Portals address this. Scale them to match the opening you wish to illuminate.

### Denoising

Despite the techniques described, some render noise persists regardless of sample count. Implement post-processing denoising to clean this final noise layer. Activate Denoising in the Render tab of the Properties.

An example render by The Pixelary appears below.

| Example render before denoising. | Example render after denoising. |

### Clamp Fireflies

Even with earlier strategies, Fireflies occasionally appear. Individual light ray contributions to each pixel are clamped using the integrator Clamp setting, limiting their maximum intensity.

Overly aggressive clamping removes intentional bright features needed for effects like bloom or glare. To balance these concerns, clamp only indirect bounces, preserving direct highlights without modification.

| No Clamp (0). | With Clamp set to 4. |

## Custom Camera

### Custom Camera

Cycles goes beyond standard camera models (Perspective, Orthographic, and Panoramic) to support user-defined cameras implemented in Open Shading Language (OSL). Custom cameras function as OSL shaders receiving a sensor position as input and outputting the ray's origin, direction, and throughput.

OSL for shading and custom cameras operate independently; custom cameras work even when OSL shading remains disabled.

### Using Custom Cameras

To employ a custom camera, set the lens type to Custom.

This activates selection of a text data-block or external file, mirroring the Script node in shaders.

If the chosen camera shader contains parameters, they display below the Lens panel.

### Writing Camera Shaders

### Inputs

The camera shader's primary input is the sensor position, provided by camera_shader_raster_position() , which returns a point with X and Y values representing image position in the 0-1 range.

To allow random variation in shader sampling, camera_shader_random_sample() returns a vector holding random numbers in X and Y. For aperture sampling specifically, the cam:aperture_position attribute (discussed below) proves better for aligning with Blender's standard aperture options.

### Outputs

Three variables must be output:

- position : a point containing the ray origin.

- direction : a vector containing the normalized ray direction.

- throughput : a color specifying the ray's weighting factor, dimming or tinting camera-visible color.

Both position and direction work in camera coordinates, where the origin sits at the camera position, positive Z points along the view direction, and positive Y indicates up.

A black throughput causes the ray to be skipped, useful for marking invalid rays in panoramic mappings.

### Attributes

Camera shaders lack traditional shader features like closures or geometry attributes. Instead, custom attributes are available via getattribute() :

cam:sensor_size
Camera sensor size in millimeters, set in Camera properties.

cam:image_resolution
Rendered image resolution.

cam:focal_distance
Focal distance in millimeters, set in Depth of Field properties.

cam:aperture_aspect_ratio
Aperture aspect ratio, set in Depth of Field properties.

cam:aperture_size
Aperture size, set in Depth of Field properties.

cam:aperture_position
Random position on the aperture, accounting for size, shape, and aspect ratio as configured in Depth of Field properties. Note: this shares random numbers with camera_shader_random_sample() , so avoid using both to prevent correlation.

### Derivatives

Certain features like the Wireframe node require derivatives of ray origin and direction relative to image X and Y. Blender automatically computes these via OSL auto-differentiation. For advanced cases where you compute derivatives more efficiently, define dPdx , dPdy , dDdx , and dDdy outputs. If present, their values override auto-differentiation. Both methods cannot mix—either specify all or none.

### Parameters

Shaders may define additional inputs, exposed in the Camera properties panel under Lens options.

OSL metadata controls their interface presentation:

[[ string help = "This is a parameter" ]]
Description shown in tooltips.

[[ float sensitivity = 0.25 ]]
Increment/decrement amount when dragging or clicking.

[[ int digits = 2 ]]
Display precision for numerical parameters.

[[ float min = -5, float max = 5 ]]
Parameter range limits.

[[ int slider = 1, float slidermin = -4, float slidermax = 4 ]]
Display as a slider with specified range.

[[ string widget = "boolean" ]]
Display an int property as a checkbox (0 or 1).

### An Example

A minimal perspective camera implementation:

shader perspective_camera(
float focal_length = 90.0 [[ float sensitivity = 0.2, float min = 0 ]],
output point position = 0.0,
output vector direction = 0.0,
output color throughput = 1.0) {
vector sensor_size;
getattribute("cam:sensor_size", sensor_size);

point Pcam = camera_shader_raster_position() - point(0.5);
Pcam *= sensor_size / focal_length;
direction = normalize(vector(Pcam.x, Pcam.y, 1.0));
}

Additional examples are available in Text Editor ‣ Templates ‣ Open Shading Language .

### Limitations

Important

Custom cameras are not supported with GPU rendering unless using the OptiX backend.

Certain Cycles features—particularly the Vector pass and Window texture coordinates—need inverse mappings from rays to image coordinates, a capability not yet available with custom cameras.

## Open Shading Language

### Open Shading Language

Open Shading Language (OSL) is a programmable shading framework built for sophisticated rendering systems. It empowers artists and developers to author shaders using C-like script syntax for advanced visual effects beyond standard interfaces.

Blender integrates OSL within Cycles to create custom surface, volume, and displacement shaders. This grants complete authority over shading logic, enabling procedural patterns, tailored illumination models, and geometric material behavior unavailable through prebuilt node systems alone.

Unlike node-based workflows, OSL shaders are written as text in Blender's integrated Text Editor or imported from external .osl or .oso files. After compilation, they appear in the Shader Editor via the Script Node.

Tip

OSL excels at generating procedural textures, custom material models, or prototyping research concepts. It also facilitates shader distribution across compatible applications using the OSL standard.

### Usage

To activate Open Shading Language in Blender:

- Enable OSL Rendering

In the Render Properties, activate Open Shading Language.

- Add a Script Node

In the Shader Editor, insert a Script Node, then configure its properties:

- Set Mode to Internal for a Blender text data-block, or

- Set Mode to External to load shader code from disk (.osl or compiled .oso ).

For internal mode, establish a text data-block in the Text Editor and enter your OSL code.

Blender auto-compiles the OSL source. An .osl file is compiled into .oso bytecode. Error messages appear in the system console.

- Use Shader Outputs

After compilation, the node's outputs mirror the output parameters in the OSL code. These connect anywhere in the material tree.

### Writing Shaders

Consult the OSL Documentation for comprehensive guidance.

A basic example:

shader simple_material(
color Diffuse_Color = color(0.6, 0.8, 0.6),
float Noise_Factor = 0.5,
output closure color BSDF = diffuse(N))
{
color material_color = Diffuse_Color * mix(1.0, noise(P * 10.0), Noise_Factor);
BSDF = material_color * diffuse(N);
}

### Closures

OSL diverges from languages like RSL or GLSL—it lacks a light loop. Scene lights are inaccessible; materials assemble from renderer-implemented closures. This limits flexibility but permits optimizer benefits and ensures all shaders can be importance-sampled.

Cycles closures correspond to shader nodes and their connections; consult the shader nodes documentation for specifics on behavior and parameter meanings.

See also

OSL built-in closures documentation.

### BSDF

- diffuse(N)
- oren_nayar(N, roughness)
- diffuse_ramp(N, colors[8])
- phong_ramp(N, exponent, colors[8])
- diffuse_toon(N, size, smooth)
- glossy_toon(N, size, smooth)
- translucent(N)
- reflection(N)
- refraction(N, ior)
- transparent()
- microfacet_ggx(N, roughness)
- microfacet_ggx_aniso(N, T, ax, ay)
- microfacet_ggx_refraction(N, roughness, ior)
- microfacet_beckmann(N, roughness)
- microfacet_beckmann_aniso(N, T, ax, ay)
- microfacet_beckmann_refraction(N, roughness, ior)
- ashikhmin_shirley(N, T, ax, ay)
- ashikhmin_velvet(N, roughness)

### Hair

- hair_reflection(N, roughnessu, roughnessv, T, offset)
- hair_transmission(N, roughnessu, roughnessv, T, offset)
- principled_hair(N, absorption, roughness, radial_roughness, coat, offset, IOR)

### BSSRDF

Models subsurface light scattering.

bssrdf ( method , N , radius , albedo )

Parameters :

- method ( string ) – Algorithm for simulating subsurface scattering.

- burley :
An approximation to physically-based volumetric scattering. Trades accuracy for faster noise reduction in some situations relative to random_walk.

- random_walk_skin :
Delivers accurate results for thin and curved shapes. Uses volumetric scattering within the mesh; works best for closed surfaces. Overlapping faces and mesh holes cause artifacts.

- random_walk :
Similar to random_walk_skin but adjusts Radius based on Color , Anisotropy , and IOR . Attempts to maintain greater surface definition and color compared to random_walk_skin .

- N ( vector ) – Surface normal at the shaded location.

- radius ( vector ) – Average scatter distance below the surface. Larger values yield softer appearance as light penetrates shadows and the object. Specify scatter distance separately for RGB, useful for materials like skin where red light penetrates deeper. X, Y, Z map to R, G, B.

- albedo ( color ) – Surface color, or the likelihood light reflects at each wavelength.

### Volume

- henyey_greenstein(g)
- absorption()

### Other

- emission()
- ambient_occlusion()
- holdout()
- background()

### Attributes

Geometry attributes load via getattribute() . This includes UV maps, color data, and outputs from geometry nodes.

These built-in attributes are also accessible:

geom:generated
Procedurally generated texture coordinates from undeformed geometry.

geom:uv
Primary render UV coordinate.

geom:tangent
Primary tangent vector, in object space.

geom:undisplaced
Position prior to displacement, in object space.

geom:dupli_generated
For instances, generated coordinate from the source object.

geom:dupli_uv
For instances, UV coordinate from the source object.

geom:trianglevertices
Triangle vertex positions.

geom:numpolyvertices
Polygon vertex count (currently always three).

geom:polyvertices
Polygon vertices (always three currently).

geom:name
Object name.

geom:is_smooth
Smooth or flat face shading flag.

geom:is_curve
Curve object indicator.

geom:curve_intercept
0..1 coordinate along curve, root to tip.

geom:curve_thickness
Curve thickness in object space.

geom:curve_length
Curve span in object space.

geom:curve_tangent_normal
Tangent normal along the strand.

geom:is_point
Point cloud indicator.

geom:point_radius
Point cloud point radius.

geom:point_position
Point cloud point center.

geom:point_random
Unique random value per point cloud point.

path:ray_length
Distance traveled since the last intersection.

object:random
Unique random value per object instance.

object:index
Object instance index.

object:location
Object position.

material:index
Material unique index.

particle:index
Particle instance identifier.

particle:age
Particle age in frames.

particle:lifetime
Total particle lifespan in frames.

particle:location
Particle position.

particle:size
Particle size.

particle:velocity
Particle motion direction and speed.

particle:angular_velocity
Rotational velocity of the particle.

### Trace

CPU Only

The trace(point pos, vector dir, ...) function traces rays from OSL shaders. The "shade" parameter currently lacks support, though getmessage("trace", ..) retrieves attributes from struck geometry. Refer to OSL specification documentation for usage details.

This cannot substitute for traditional lighting; its main role is shader "probing" of nearby geometry—for example, applying textures blocked by surrounding objects, exaggerating wear on exposed areas, or creating ambient-occlusion-like effects.

### Metadata

Metadata on parameters governs their interface behavior. Supported entries:

[[ string label = "My Label" ]]
Custom display name in the user interface.

[[ string widget = "null" ]]
Conceals the parameter from the interface.

[[ string widget = "boolean" ]] or [[ string widget = "checkbox" ]]
Shows an integer parameter as a checkbox.

[[ string widget = "filename" ]]
Shows the parameter as a file path picker.

[[ string widget = "mapper", string options = "left:0|right:1" ]]
Shows an integer parameter as an enumerated selector. Options contains label-value pairs separated by | .

[[ string vecsemantics = "POINT" ]]
Treats a vector parameter as position (translation).

[[ string vecsemantics = "NORMAL" ]]
Treats a vector parameter as direction (normal).

[[ string unit = "radians" ]]
Designates a float parameter as an angle, shown in radians.

[[ string unit = "m" ]]
Designates a float parameter as distance, shown in meters.

[[ string unit = "mm" ]]
Designates a float parameter as distance, shown in millimeters.

[[ string unit = "s" ]] or [[ string unit = "sec" ]]
Designates a float parameter as time, shown in seconds.

### Limitations

Important

OSL is not supported with GPU rendering unless using the OptiX backend.

When using OptiX, certain OSL capabilities are unavailable:

- Memory optimizations such as on-demand texture loading and mip-mapping are not present.

- Texture operations require OSL to resolve a constant image file path for each lookup.

- Some noise functions absent. Examples: Cell , Simplex , and Gabor .

- The trace function is non-functional.
Due to this, the Ambient Occlusion and Bevel nodes do not work.

## Film

### Film

Reference

Panel :

Render ‣ Film

Exposure
Adjusts image brightness. Unlike the Exposure in Color management, this option operates on raw image values while Color management exposure applies to the view transform.

### Pixel Filter

Images and screens have finite resolution, necessitating pixel filters to prevent Aliasing. The technique applies slight blurring to soften edges.

Type
Filtering algorithm selection.

Box :

No filtering.

Gaussian :

Smooth filtering.

Blackman-Harris :

Default, balancing smoothness with detail retention.

Width
Lower values produce crisp renders; higher values soften and reduce aliasing.

### Transparent

Render the background as transparent, enabling compositing over alternate backgrounds after rendering.

Transparent Glass
Render refractive surfaces as transparent for compositing glass over alternate backgrounds.

Roughness Threshold
For transparent glass, surfaces with roughness exceeding this limit remain opaque.

Film — Filtering and Background

Filter Size
Limited image and screen resolution necessitate pixel filtering to avoid aliasing artifacts. This is achieved by gentle image softening.

This setting controls softening strength; lower values produce sharp renders, higher values soften and reduce aliasing.

Transparent
Render the background transparent for compositing over a different backdrop post-render.

Overscan
Percentage of render dimensions to add to the internal render buffer. Serious performance impact but resolves perimeter render glitches.

## Curves

### Curves

Reference

Panel :

Render ‣ Curves

Global settings apply to all particle hair systems. Strand resolution is determined by step settings in particle configuration. Each system uses the material specified in its particle settings.

Shape
Determines how curves (such as hair) render. Different techniques optimize for speed or precision based on viewing distance and angle.

Rounded Ribbons :

Render curves as flat ribbons with rounded normals, optimizing speed. Curves subdivide with a set count.

Curve Subdivisions
Subdivision count for cardinal curve calculation (power of 2).

3D Curves :

Render curves as circular 3D forms for precision when viewed up close. Subdivisions adjust automatically to achieve smoothness.

Linear 3D Curves :

Render as 3D circular geometry using linear interpolation between nodes. Faster than 3D curves but less smooth, showing visible transitions at low resolution.

This optimization uses hardware-accelerated curve operations on GPUs. Results differ between CPU and GPU renderings, unsuitable for multi-device rendering or mixed-hardware render farms.

### Viewport Display

These configure curve rendering in Material Preview mode.

Shape

Strand :

Display curves as thin strands, roughly one pixel wide. Diameter parameters are disregarded.

Strip :

Display curves as flat ribbons with rounded normals.

Additional Subdivisions
Subdivisions applied beyond curve resolution from hair system configuration. Higher values refine curve smoothness.
