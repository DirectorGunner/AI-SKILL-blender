# World Environment, Displacement, Surfaces, Colors ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: World Environment; Displacement; Surfaces; Colors; Blend; Clouds; Distorted Noise; Image or Movie; Magic; Marble; Musgrave; Stucci; Voronoi; Wood; Line Art; Preview; Settings.

## World Environment

### World Environment

Lighting with an HDR image.

The world defines the environment that the scene is in. The surface shader sets the background and environment lighting, either as a fixed color, sky model or HDRI texture. With volume shaders the entire scene can be covered in mist or other volumetric effects.

### Surface

Reference

Panel :

World ‣ Surface

The surface shader defines the light emission from the environment into the scene. The world surface is rendered as if it is very distant from the scene, and as such there is no two-way interacting between objects in the scene and the environment, only light coming in. The only shader accepted is the Background node with a color input and strength factor for the intensity of the light.

### Image Based Lighting

For image based lighting, use the Environment Texture node rather than the Image Texture node for correct mapping. This supports Equirectangular (also known as latitude/longitude) for environment maps, and Mirror Ball mapping for converting photos of mirror balls to environment maps.

### Volume

Reference

Panel :

World ‣ Volume

A volume shader can be applied to the entirely world, filling the entire space.

Currently this is most useful for night time or other dark scenes, as the world surface shader or sun lights will have no effect if a volume shader is used. This is because the world background is assumed to be infinitely far away, which is accurate enough for the sun for example. However, for modeling effects such as fog or atmospheric scattering, it is not a good assumption that the volume fills the entire space, as most of the distance between the sun and the earth is empty space. For such effects it is be better to create a volume object surrounding the scene. The size of this object will determine how much light is scattered or absorbed.

### Viewport Display

Reference

Panel :

World ‣ Viewport Display

Color
The color to render the 3D Viewport background when choosing World Background.

## Displacement

### Displacement

Detail can be added to the shape of a surface with displacement shaders.

To create displacement, connect a Displacement or Vector Displacement node to the displacement input of the Material Output node. Procedural, painted or baked textures can then be connected to these nodes.

Typical displacement node setup.

Three displacement methods exist, with varying accuracy, performance and memory usage. The displacement method can be set per material in the Material Settings.

Bump only, displacement only, and displacement and bump combined.

### Bump Only

The least accurate but most memory efficient method is bump mapping. This method does not actually alter the mesh surface, but merely changes the shading to make it seem so.

Bump maps are often used to add smaller details on a model, for example pores or wrinkles on skin.

For baked bump maps, 8-bit images are commonly used. However, 16 or 32-bit float maps can provide better looking results. When using image textures use Cubic interpolation to avoid stepping artifacts, these are more visible for bump maps than other types of textures.

Important

Because bump mapping is a fake effect, it can cause artifacts if the actual shape of the geometry is too different from the bump mapped shape. If this happens the strength of bump mapping should be reduced or actual displacement should be used.

### Displacement Only

The most accurate and memory intensive displacement method is to apply true displacement to the mesh surface.

It requires the mesh to be finely subdivided, which can be memory intensive. Adaptive Subdivision is the best way to subdivide the mesh, so that exactly the right amount of subdivision is used depending on the distance of the object to the camera.

For baked displacement maps, best results are achieved with 16 or 32-bit float maps, as 8-bit images often can not represent all the necessary detail.

See also

The Displace Modifier can also be used to displace a mesh.

Note

Cycles does not support unique displacement per instance.

### Displacement and Bump

Both methods can be combined to use actual displacement for the bigger displacement and bump for the finer details. This can provide a good balance to reduce memory usage.

Once you subdivide the mesh very finely, it is better to use only actual displacement in Cycles. Keeping bump maps will then only increase memory usage and slow down renders.

## Surfaces

### Surfaces

The surface shader defines the light interaction at the surface of the mesh. One or more BSDF s specify if incoming light is reflected back, refracted into the mesh, or absorbed.

Emission defines how light is emitted from the surface, allowing any surface to become a light source.

### Terminology

BSDF
Stands for Bidirectional Scattering Distribution Function. It defines how light is reflected and refracted at a surface.

Reflection
BSDFs reflect an incoming ray on the same side of the surface.

Transmission
BSDFs transmit an incoming ray through the surface, leaving on the other side.

Refraction
BSDFs are a type of Transmission , transmitting an incoming ray and changing its direction as it exits on the other side of the surface.

### BSDF Parameters

A major difference from non-physically-based renderers is that direct light reflection from lights and indirect light reflection of other surfaces are not decoupled, but rather handled using a single BSDF . This limits the possibilities a bit, but we believe overall it is helpful in creating consistent-looking renders with fewer parameters to tune.

Roughness
For the glossy BSDF s, the roughness parameter controls the sharpness of the reflection, from 0.0 (perfectly sharp) to 1.0 (very soft).

## Colors

### Colors

The color of a texture can be modified with the Brightness , Contrast , and Saturation buttons. All textures with RGB values, including Images and Environment Maps , may be modified with the RGB sliders.

Clamp
Set negative texture RGB and intensity values to zero, for some uses like displacement this option can be disabled to get the full range.

Multiply R, G, B
Tint the color of a texture by brightening each red, green and blue channel.

Brightness
Change the overall brightness/intensity of the texture.

Contrast
Change the contrast of the texture.

Saturation
Change the saturation of the texture.

### Color Ramp

Activates a color ramp which allows you to remap the colors of a texture to new ones.

## Blend

### Blend

The Blend texture generates a smoothly interpolated progression. This is one of the most frequently used procedural textures. You can use blend textures to blend other textures together (with Stencil ), or to create nice effects (especially with the Mapping: Normal trick).

Note

Remember that if you use a ramp to create a custom blending, you may have to use No RGB , if the Mapping value needs an intensity input.

Blend Texture panels.

### Options

Progression
Profile of blend.

Linear
A linear progression.

Quadratic
A quadratic progression.

Easing
A flowing, nonlinear progression.

Diagonal
A diagonal progression.

Spherical
A progression with the shape of a three-dimensional ball.

Quadratic Sphere
A quadratic progression with the shape of a three-dimensional ball.

Radial
A radial progression: Horizontal / Vertical . The direction of the progression is flipped a quarter turn.

## Clouds

### Clouds

Clouds represent Perlin noise. In addition, each noise-based Blender texture (with the exception of Voronoi and simple noise) has a Noise Basis setting that allows the user to select which algorithm is used to generate the texture. This is often used for Clouds, Fire, Smoke. Well-suited to be used as a Bump map, giving an overall irregularity to the material.

Clouds Texture panels.

### Options

Type
Soft or Hard , changes contrast and sharpness.

Color

Grayscale :

The standard noise, gives a floating-point intensity value.

Color :

The noise gives an RGB value.

Size
The dimension of the Noise table.

Depth
The depth of the Clouds calculation. A higher number results in a long calculation time, but also in finer details.

Nabla
Size of the derivative offset used for calculating surface normals. Smaller values give more precision, larger values are smoother/faster. This is mostly relevant when the texture is used in displacement or bump channels.

## Distorted Noise

### Distorted Noise

Distortion Noise takes the option that you pick from Noise Basis and filters it, to create hybrid pattern. It is often used for grunge but is also very complex and versatile.

Distorted Noise Texture panels.

### Options

Noise Basis
The texture to be distorted.

Distortion
The texture to use to distort another.

Amount
The amount that Distortion Noise affects Basis .

Size
The size of the noise generated.

Nabla
Almost all procedural textures in Blender use derivatives for calculating normals for texture mapping (except Blend and Magic ). This is important for Normal and Displacement Maps. The strength of the effect is controlled with the Nabla number field.

## Image or Movie

### Image or Movie

The term Image Texture simply means that a graphic image, which is a pixel grid composed of R, G, B, and sometimes Alpha values. It is used as the input source to the texture. As with other types of textures, this information can be used in a number of ways, not only as a simple "decal".

Video textures are a some kind of Image textures and based on movie file or sequence of successive numbered separate images. They are added in the same way that image textures are.

When the Texture Type Image or Movie is selected, three new panels present themselves allowing to control most aspects of how image textures are applied: Image , Image Sampling , and Image Mapping .

### About Image-Based Texturing

Texture images take up precious memory space, often being loaded into a special video memory bank that is very fast and very expensive, so it is often very small. So, keep the images as small as possible. A 64×64 image takes up only one fourth the memory of a 128×128 image.

For photorealistic rendering of objects in animations, often larger image textures are used, because the object might be zoomed in on in camera moves. In general, you want to use a texture sized proportionally to the number of pixels that it will occupy in the final render. Ultimately, you only have a certain amount of physical RAM to hold an image texture and the model and to provide workspace when rendering your image.

For the most efficient memory usage, image textures should be square, with dimensions as powers of 2, such as 32×32, 64×64, 128×128, 256×256, 1024×1024, 2048×2048, and 4096×4096.

If you can reuse images across different meshes, this greatly reduces memory requirements. You can reuse images if you map those areas of the meshes that "look alike" to a layout that uses the common image.

When using file textures, it is very important that you have Mapped the UVs of the mesh, and they are laid out appropriately.

You do not have to UV map the entire mesh. The sphere above on the left has some faces mapped, but other faces use procedural materials and textures. Only use UV textures for those portions of your mesh where you want very graphic, precise detail. For example, a model of a vase only needs UV texture for the rim where decorative artwork is incorporated. A throw pillow does not need a different image for the back as the front; in fact many throw pillows have a fabric (procedural material) back.

As another example, you should UV map both eyes of a head to the same image (unless you want one bloodshot and the other clear). Mapping both sides of a face to the same image might not be advisable, because the location of freckles and skin defects are not symmetrical. You could of course change the UV map for one side of the face to slightly offset, but it might be noticeable. Ears are another example where images or section of an image can be mapped to similar faces.

### Options

Image
The Image Data-Block Menu.

### Alpha

Use the alpha channel information stored in the image. Where the alpha value in the image is less than 1.0, the object will be partially transparent and things behind it will be visible. Works with image formats that store transparency information.

Calculate
Calculate an alpha based on the RGB values of the Image. Black (0, 0, 0) is transparent, white (1, 1, 1) opaque. Enable this option if the image texture is a mask. Note that mask images can use shades of gray that result in semi-transparency, like ghosts, flames, and smoke/fog.

| Image with Use alpha. The alpha values of the pixels are evaluated. | Image with Calculate alpha only, Use Alpha in the Image panel is disabled. |

Invert
Reverses the alpha value. Use this option if the mask image has white where you want it transparent and vice versa.

### Mapping

Image Mapping panel.

In the Mapping panel, you can control how the image is mapped or projected onto the 3D model.

Flip Axes
Rotates the image 90 degrees counterclockwise when rendered.

Extension
How the image is extrapolated beyond its original bounds.

Extend :

Outside the image the colors of the edges are extended.

Clip :

Clip to image size and set exterior pixels as transparent. Outside the image, an alpha value of 0.0 is returned. This allows you to 'paste' a small logo on a large object.

Clip Cube :

Clips to cubic-shaped area around the images and sets exterior pixels as transparent. The same as Clip, but now the 'Z' coordinate is calculated as well. An alpha value of 0.0 is returned outside a cube-shaped area around the image.

Repeat :

The image is repeated horizontally and vertically.

Repeat X, Y
X/Y repetition multiplier.

Mirror X, Y
Mirror on X/Y axes. These buttons allow you to map the texture as a mirror, or automatic flip of the image, in the corresponding X and/or Y direction.

Checker :

Checkerboards quickly made. You can use the option size on the Mapping panel as well to create the desired number of checkers.

Tiles Even/Odd
Set even/odd tiles.

Distance
Governs the distance between the checkers in parts of the texture size.

#### Crop

Minimum X, Y / Maximum X, Y
The offset and the size of the texture in relation to the texture space. Pixels outside this space are ignored. Use these to crop, or choose a portion of a larger image to use as the texture.

### Sampling

In the Sampling panel you can control how the information is retrieved from the image.

Image Sampling panel.

Interpolation
This option interpolates the pixels of an image. This becomes visible when you enlarge the picture. By default, this option is on. Turn this option off to keep the individual pixels visible and if they are correctly anti-aliased. This last feature is useful for regular patterns, such as lines and tiles; they remain 'sharp' even when enlarged considerably. Turn this image off if you are using digital photos to preserve crispness.

| Magnified Picture pattern absent Blending . | Magnified Picture pattern utilizing Blending . |

Span
Boost the filter scope utilized via blending.
When you see dark lines or edges surrounding the patterned thing, notably wherever the picture gets see-through,
switch that rating down starting 1.0 to 0.1 or likewise.

## Magic

### Magic

The Magic Texture node is used to add a psychedelic color texture. It can be used for "Thin Film Interference" if you set Mapping to Reflection and use a relatively high Turbulence . The RGB components are generated independently with a sine formula.

Magic Texture panels.

### Options

Depth
The depth of the calculation. A higher number results in a long calculation time, but also in finer details.

Turbulence
The strength of the pattern.

## Marble

### Marble

The marble texture is used to generate marble, fire, or noise with a structure. Bands are generated based on the sine, saw, or triangular formula and noise turbulence.

Marble Texture panels.

### Options

Marble Type
Three settings for soft to more clearly defined Marble .

Soft, Sharp, Sharper

Noise basis
Shape of wave to produce bands.

Sine, Saw, Triangle

Noise Type
The noise function works with two methods.

Soft, Hard

Size
The dimensions of the noise table.

Depth
The depth of the Marble calculation. A higher value results in greater calculation time, but also in finer details.

Turbulence
The turbulence of the sine bands.

## Musgrave

### Musgrave

The musgrave texture is used to generate organic materials, but it is very flexible. You can do nearly everything with it.

Musgrave Texture panels.

### Options

Type
This procedural texture has five noise types on which the resulting pattern can be based and they are selectable from a select menu at the top of the tab. The five types are:

- Hetero Terrain

- Fractal Brownian Motion (fBm)

- Hybrid Multifractal

- Ridged Multifractal

- Multifractal

These noise types determine the manner in which Blender layers successive copies of the same pattern on top of each other at varying contrasts and scales.

Examples with Basis: Voronoi: F1, Dimension: 0.5, Lacunarity: 0.15, Octave: 2.0.

| Hetero Terrain. | Fractal Brownian Motion. | Hybrid Multifractal. | Ridged Multifractal. | Multifractal. |

The main noise types have four characteristics:

Dimension
Fractal dimension controls the contrast of a layer relative to the previous layer in the texture. The higher the fractal dimension, the higher the contrast between each layer, and thus the more detail shows in the texture.

Lacunarity
Lacunarity controls the scaling of each layer of the Musgrave texture, meaning that each additional layer will have a scale that is the inverse of the value which shows on the button. i.e. Lacunarity = 2 –> Scale = 1/2 original.

Octaves
Octave controls the number of times the original noise pattern is overlaid on itself and scaled/contrasted with the fractal dimension and lacunarity settings.

Intensity
Light intensity. Called Offset for Hetero Terrain .

The Hybrid Multifractal and Ridged Multifractal types have these additional settings:

Offset
Both have a "Fractal Offset" button that serves as a "sea level" adjustment and indicates the base height of the resulting bump map. Bump values below this threshold will be returned as zero.

Gain
Setting which determines the range of values created by the function. The higher the number, the greater the range. This is a fast way to bring out additional details in a texture where extremes are normally clipped off.

## Stucci

### Stucci

Stucci Texture panels.

The Stucci texture is based on noise functions. It is often used for stone, asphalt, or oranges, normally for bump mapping to create grainy surfaces.

### Options

Plastic / Wall In / Wall out
Plastic is the standard Stucci, while the "walls" is where Stucci gets it name. This is a typical wall structure with holes or bumps.

Soft / Hard
There are two methods available for working with Noise.

Size
Dimension of the Noise table.

Turbulence
Depth of the Stucci calculations.

## Voronoi

### Voronoi

The Voronoi texture is used to generate very convincing Metal, especially the "Hammered" effect. Organic shaders (e.g. scales, veins in skin).

Voronoi Texture panels.

### Options

Distance Metric
This procedural texture has seven Distance Metric options. These determine the algorithm to find the distance between cells of the texture. These options are:

- Minkowski

- Minkowski 4

- Minkowski 1/2

- Chebychev

- Manhattan

- Distance Squared

- Actual Distance

The Minkowski setting has a user definable value (the Exponent button) which determines the Minkowski exponent e of the distance function:

( x e + y e + z e ) 1/e

A value of one produces the Manhattan distance metric, a value less than one produces stars (at 0.5, it gives a Minkowski 1/2 ), and higher values produce square cells (at 4.0, it gives a Minkowski 4 , at 10.0, a Chebychev ). So nearly all Distance Settings are basically the same – a variation of Minkowski .

You can get irregularly-shaped rounded cells with the Actual Distance / Distance Squared options.

| Minkowski Exponent: 0.5 (Minkowski 1/2). | Minkowski Exponent: 1 (Manhattan). | Minkowski Exponent: 2 (Actual Distance). |
| Minkowski Exponent: 4 (Minkowski 4). | Minkowski Exponent: 10 (Chebychev). | Distance Squared (more contrast than Actual Distance). |

Feature Weights
These four sliders at the bottom of the Voronoi panel represent the values of the four Worley constants, which are used to calculate the distances between each cell in the texture based on the distance metric. Adjusting these values can have some interesting effects on the end result…

Coloring
Four settings ( Intensity , Position , Position and Outline , and Position, Outline, and Intensity ) that can use four different noise basis as methods to calculate color and intensity of the texture output. This gives the Voronoi texture you create with the "Worley Sliders" a completely different appearance and is the equivalent of the noise basis setting found on the other textures.

## Wood

### Wood

The wood texture is used to generate wood and ring-shaped patterns.

Wood Texture panels.

### Options

Noise Basis
Shape of wave to produce bands.

Sine, Saw, Triangle

Wood Type
Set the bands to either straight or ring-shaped, with or without turbulence.

Bands, Rings, Band Noise, Ring Noise

Noise Type
There are two methods available for the Noise function.

Soft, Hard

Size
Dimension of the Noise table.

Turbulence
Turbulence of the Band Noise and Ring Noise types.

## Line Art

### Line Art

Reference

Panel :

Material ‣ Line Art

Line Art material properties.

Material Mask
Material masks are a way to provide Line Art extra information about faces that caused the occlusion. So edges occluded by those faces can be selected to have different styles.

Masks
The layer to include faces of the current material.

Levels
Faces with this material will behave as if it has set number of layers in occlusion.

Intersection Priority
Assigns an intersection priority value for this material. Note that this priority takes precedent over Object or Collection priority values. The intersection line will be included into the object with the higher intersection priority value.

## Preview

### Preview

The Preview panel gives a quick visualization of the active material applied in a simple scene.

Shape
Preview the material on a Plane, Sphere, Cube, Hair, Shader Ball, Cloth or Fluid object. This shape is also used for previews when linking and appending materials.

Preview World Cycles Only
Use the world from the current scene for lighting in the material preview.

Preview shapes.

## Settings

### Settings

Reference

Panel :

Material ‣ Settings

### Renderer Settings

While shading nodes control the appearance, these settings control the quality and algorithms that each renderer uses to render the material.

- EEVEE specific settings

- Cycles specific settings

### Pass Index

Pass Index
Index number for the Material Index render pass. This can be used to give a mask to a material and then be read with the ID Mask Node in the Compositor.

Note

Volume Objects are not supported.

### Viewport Display

These settings control the 3D Viewport display in solid shading. They provide a faster alternative to full shader nodes, which may be too heavy or distracting for tasks like modeling, layout or sculpting.

Color
Diffuse or metal surface color.

Metallic
Blends between a non-metallic and metallic material model. A value of 1.0 gives a fully specular reflection tinted with the base color, without diffuse reflection or transmission. At 0.0 the material consists of a diffuse or transmissive base layer, with a specular reflection layer on top.

Roughness
Specifies microfacet roughness of the surface for metal and specular reflection.
